---
title: 'Detalles de diseño: gestión de políticas de reorden'
description: Este artículo brinda una descripción general de las políticas de reorden que puede usar en la planificación de suministros.
author: brentholtorf
ms.author: bholtorf
ms.reviewer: andreipa
ms.topic: conceptual
ms.date: 02/24/2023
ms.custom: bap-template
---
# <a name="design-details-handling-reordering-policies" />Detalles de diseño: Gestión de directivas de reorden

Para incluir un artículo en la planificación de suministros, debe especificar una política de reorden para él en la página **Tarjeta de artículo**. Existen las políticas de reorden siguientes:  

* Cdad. fija reordenada  
* Cdad. máxima  
* Pedido  
* Lote a lote  

Las directivas **Cantidad fija reordenada** y **Cdad. máxima** están relacionadas con la planificación de inventario. Estas políticas coexisten con el equilibrio paso a paso del suministro y el seguimiento de pedidos.  

## <a name="the-role-of-the-reorder-point" />Función del punto de reorden

Un punto de reorden representa la demanda durante un plazo de entrega. Cuando el inventario se proyecta por debajo del nivel de inventario definido por el punto de reorden, ha llegado el momento de pedir más cantidad. El inventario disminuirá gradualmente hasta que llegue la reposición. Puede llegar a cero o al nivel de existencias de seguridad. El sistema de planificación sugiere una orden de suministro de programación anticipada en el momento en el que el inventario quede por debajo del punto de reorden.  

Los niveles de inventario pueden moverse significativamente durante el intervalo de tiempo. Por lo tanto, el sistema de planificación monitorea constantemente el inventario disponible.

## <a name="monitoring-the-projected-inventory-level-and-the-reorder-point" />Supervisión del nivel de inventario proyectado y el punto de reorden

El inventario es un tipo de aprovisionamiento, pero para planificación del inventario, el sistema de planificación diferencia entre dos niveles de inventario:  

* Inventario proyectado  
* Inventario disponible proyectado  

### <a name="projected-inventory" />Inventario proyectado

Al comienzo del proceso de planificación, el inventario proyectado es la cantidad bruta de inventario. La cantidad bruta incluye la oferta y la demanda contabilizadas y no contabilizadas en el pasado. Esta cantidad se convierte en un nivel de inventario proyectado que mantienen las cantidades brutas de la oferta y la demanda futuras. La oferta y la demanda futuras se introducen a lo largo de la línea de tiempo, ya sea que se reserven o se asignen de otras formas.  

El sistema de planificación usa el inventario proyectado para supervisar el punto de reorden y para determinar la cantidad de la orden al usar la política de reorden **Cantidad máxima**.  

### <a name="projected-available-inventory" />Inventario disponible proyectado

El inventario disponible proyectado es la parte del inventario que está disponible para satisfacer la demanda en un momento determinado. El sistema de planificación usa el inventario disponible proyectado al supervisar el nivel de inventario de seguridad. El inventario de seguridad siempre debe estar disponible para una demanda inesperada.  

### <a name="time-buckets" />Ciclos

El inventario proyectado es importante para detectar cuándo se está alcanzando o cruzando el punto de reorden y calcular la cantidad correcta de la orden cuando se utiliza la política de reorden **Cantidad máxima**.  

El nivel de inventario proyectado se calcula al principio del periodo de planificación. Es un nivel bruto que no tiene en cuenta las reservas u otras asignaciones. Para supervisar este nivel de inventario durante la secuencia de planificación, el sistema de planificación supervisa los cambios agregados durante un periodo de tiempo. Ese período se denomina *cubo de tiempo*. Para obtener más información sobre los períodos de tiempo, vaya a [Períodos de tiempo](#time-buckets). El sistema de planificación garantiza que el intervalo de tiempo sea de al menos un día. Un día es la unidad mínima de tiempo para eventos de demanda o suministro.  

### <a name="determining-the-projected-inventory-level" />Determinación del nivel de inventario proyectado

En la secuencia siguiente se describe cómo el sistema de planificación determina el nivel de inventario proyectado:  

* Cuando un evento de suministro se ha planificado totalmente, aumenta el inventario proyectado en la fecha de vencimiento del evento.  
* Cuando se ha satisfecho completamente un evento de demanda, el inventario proyectado no se reducirá inmediatamente. En su lugar, registra un aviso de disminución, que es un registro interno que lleva la fecha y la cantidad de la adición al inventario proyectado.  
* Cuando se planifica un evento de suministro posterior y se agrega a la escala de tiempo, el sistema investiga los recordatorios de disminución publicados uno por uno hasta la fecha planificada del suministro. Durante este proceso, se podría alcanzar o pasar el nivel del punto de reorden del aviso de aumento interno.  
* Si se introduce una nueva orden de suministro, comprueba si se hace antes del aprovisionamiento actual. Si lo es, el nuevo aprovisionamiento se convierte en el aprovisionamiento actual y el procedimiento de contrapartida se reinicia.  

La siguiente imagen muestra este principio.  

![Determinación del nivel de inventario proyectado.](media/nav_app_supply_planning_2_projected_inventory.png "Determinación del nivel de inventario proyectado")  

1. El suministro **Sa** de 4 (fijos) cierra la demanda **Da** de 3.  
2. CloseDemand: crear un aviso de disminución de -3 (no se mostrará).  
3. El suministro **Sa** está cerrado con un exceso de 1 (no hay más demanda).  

     El nivel de inventario proyectado aumenta en +4, mientras que el inventario **disponible** proyectado es -1.  

4. El siguiente suministro **Sb** de 2 (otro pedido) ya se ha colocado en la escala de tiempo.  
5. El sistema de planificación comprueba si hay un aviso de disminución antes de **Sb** (en este ejemplo no lo hay, por lo que no se realiza ninguna acción).  
6. El sistema de planificaión cierra el suministro **Sb** (no hay más demanda); A: mediante la reducción a 0 (cancelar) o B: dejándolo como está.  

     El nivel de inventario proyectado aumenta (A: +0 => +4 o B: +2 = +6).  

7. El sistema de planificación realiza una comprobación final. ¿Hay algún recordatorio de disminución? Sí, hay uno con fecha de **Da**.  
8. El sistema de planificación agrega el aviso de disminución del aviso -3 en el nivel de inventario proyectado, A: +4 -3 = 1 o B: +6 -3 = +3.  
9. Para A, el sistema de planificación crea un pedido con programación anticipada en la fecha **Da**. Para B, el punto de reorden se alcanza y no se crea ninguna orden nueva.

## <a name="the-role-of-the-time-bucket" />El rol del ciclo

El propósito del ciclo es recopilar los eventos de demanda dentro del intervalo de tiempo para crear una orden de suministro conjunto.  

En el caso de directivas de reorden que utilizan un punto de reorden se puede definir un ciclo. Los intervalos de tiempo ayudan a garantizar que se acumulen las demandas dentro del mismo período de tiempo. Luego, el sistema verifica el efecto en el inventario proyectado y si se pasó el punto de reorden.

Si sobrepasa el punto de reorden, el sistema programa de forma anticipada una nueva orden de suministro desde el final del ciclo. Los ciclos comienzan en la fecha inicial de planificación.  

El concepto por ciclos refleja el proceso manual de comprobación del nivel de inventario de un modo frecuente en vez de hacerlo por cada transacción. Usted define la frecuencia (el ciclo). Por ejemplo, podría recopilar todas las exigencias de producto de un proveedor para hacer un pedido semanal.  

![Ejemplo de ciclo en la planificación.](media/nav_app_supply_planning_2_reorder_cycle.png "Ejemplo de ciclo en la planificación")  

Los ciclos se usan a menudo para evitar un efecto de cascada. Por ejemplo, una fila equilibrada de demanda y aprovisionamiento donde se cancela una demanda temprana, o se crea una nueva. El resultado podría ser que se programe cada orden de suministro (sin incluir el último).

## <a name="stay-below-the-overflow-level" />Mantenerse por debajo del nivel de desbordamiento

Cuando se usan las políticas de reorden **Cantidad máxima** y **Cantidad fija reordenada**, el sistema de planificación se centra en el inventario proyectado únicamente en el ciclo indicado. Podría sugerir una oferta adicional cuando la demanda negativa o los cambios positivos en la oferta ocurren fuera del intervalo de tiempo. Para el suministro adicional, el sistema de planificación calcula la cantidad en la que debe reducir el suministro. Esta cantidad se denomina “nivel de desbordamiento.” El desbordamiento disponible se comunica como una línea de planificación con una acción de **Cambiar cantidad. (salida)** o **Cancelar** y el mensaje de advertencia siguiente:  

* Atención: El inventario proyectado [xx] es superior al nivel de desbordamiento [xx] en la fecha de vencimiento [xx].*  

![Nivel de desbordamiento de inventario.](media/supplyplanning_2_overflow1_new.png "Nivel de desbordamiento de inventario")  

### <a name="calculating-the-overflow-level" />Cálculo del nivel de desbordamiento

El nivel de desbordamiento se calcula de diferentes modos según la política de reorden.  

#### <a name="maximum-qty" />Cdad. máxima

Nivel de desbordamiento = inventario máximo  

> [!NOTE]  
> Si usa una cantidad mínima de pedido, se agrega de la siguiente manera:
>
> nivel de desbordamiento = inventario máximo + cantidad mínima de pedido.  

#### <a name="fixed-reorder-qty" />Cdad. fija reordenada

nivel de desbordamiento = cantidad de reorden + punto de reorden  

> [!NOTE]  
> Si la cantidad mínima de pedido es mayor que el punto de reorden, se reemplaza de la siguiente manera:
>
> nivel de desbordamiento = cantidad de reorden + cantidad mínima de pedido  

#### <a name="order-multiple" />Múltiplos de pedido

Si existe un múltiplo de pedido, ajusta el nivel de desbordamiento para las políticas de reorden Cantidad máxima y Cantidad fija reordenada.  

### <a name="creating-the-planning-line-with-an-overflow-warning" />Crear la línea de planificación con advertencia de desbordamiento

Se crea una línea de planificación cuando un suministro existente provoca que el inventario proyectado sea superior al nivel de desbordamiento al final de un ciclo. Para advertir del posible suministro extra, la línea de planificación tiene un mensaje de advertencia, el campo **Aceptar mensaje acción** no está seleccionado y el mensaje de acción es **Cancelar** o **Cambiar cdad**.  

#### <a name="calculating-the-planning-line-quantity" />Cálculo de la cantidad en la línea de planificación

La cantidad de una línea de planificación se calcula de la manera siguiente:

Cantidad de planificación de línea = cantidad de suministro actual – (inventario proyectado – nivel de desbordamiento)  

> [!NOTE]  
> Para sAs con todas las líneas de advertencia, se omite la cantidad de pedido máximo y mínimo y múltiplo de pedido.  

#### <a name="defining-the-action-message-type" />Definir el tipo de mensaje de acción

* Si la cantidad de la línea de planificación es superior a 0, el mensaje de acción es **Cambiar cdad**.  
* Si la cantidad de la línea de planificación es igual o menor que 0, el mensaje de acción es **Cancelar**.  

#### <a name="composing-the-warning-message" />Composición del mensaje de advertencia

Si hay desbordamiento, la página **Elementos planificación sin seguimiento** muestra un mensaje de advertencia con la siguiente información:  

* Nivel de inventario proyectado que ha activado la advertencia  
* Nivel de desbordamiento calculado  
* Fecha de vencimiento del evento de suministro  

Ejemplo: "El inventario proyectado 120 es superior al nivel de desbordamiento 60 el 01-28-23".  

### <a name="example-scenario" />Ejemplo de escenario

En este ejemplo, un cliente cambia un pedido de venta de 70 a 40 piezas entre dos ejecuciones de planificación. La característica de desbordamiento reduce la compra que se ha sugerido para la cantidad de venta inicial.  

#### <a name="item-setup" />Configuración de producto

|Política reorden|Cdad. máxima|  
|-----------------------|------------------|  
|Cantidad máxima pedido|100|  
|Punto de reorden|50|  
|Inventario|80|  

#### <a name="situation-before-sales-decrease" />Situación antes de la disminución de venta

|Evento|Cambiar cdad.|Inventario proyectado|  
|-----------|-----------------|-------------------------|  
|Día uno|Ninguno|80|  
|Ventas|-70|10|  
|Final del ciclo|Ninguno|10|  
|Sugerir nuevo pedido de compra|+90|100|  

#### <a name="situation-after-sales-decrease" />Situación después de la disminución de venta

|Cambiar|Cambiar cdad.|Inventario proyectado|  
|------------|-----------------|-------------------------|  
|Día uno|Ninguno|80|  
|Ventas|-40|nº 40|  
|Compra|+90|130|  
|Final del ciclo|Ninguno|130|  
|Sugerir disminución de compra<br><br> pedido a partir de 90 a 60|-30|100|  

#### <a name="resulting-planning-lines" />Líneas de planificación resultantes

El sistema crea una línea de planificación de advertencia para reducir la compra con 30 de 90 a 60 para mantener el inventario proyectado en 100 según el nivel de desbordamiento.  

![Planificar de acuerdo con el nivel de desbordamiento.](media/nav_app_supply_planning_2_overflow2.png "Planificar de acuerdo con el nivel de desbordamiento")  

> [!NOTE]  
> Sin la característica de desbordamiento, no se crea ninguna advertencia si el nivel de inventario proyectado está por encima del máximo, lo que podría producir un suministro extra de 30.

## <a name="handling-projected-negative-inventory" />Gestión de inventario negativo proyectado

El punto de reorden expresa la demanda prevista durante el plazo del producto. El inventario proyectado debe ser lo suficientemente grande como para satisfacer la demanda hasta que se reciba el nuevo pedido. Mientras tanto, el stock de seguridad debe satisfacer las fluctuaciones en la demanda hasta un nivel de servicio objetivo.  

El sistema de planificación considera una emergencia si una demanda futura no puede ser atendida desde el inventario proyectado. O, expresado de otra forma, que el inventario proyectado sea negativo. El sistema sugiere que cree una nueva orden de suministro para cubrir la parte no satisfecha de la demanda. El tamaño de la nueva orden de suministro no considerará el inventario máximo ni la cantidad de reorden ni los siguientes modificadores de orden:

* Cantidad máxima pedido
* Cantidad mínima pedido
* Múltiplos de pedido 

En su lugar, refleja la deficiencia exacta.  

La línea de planificación de este tipo de orden de suministro mostrará un icono de advertencia de **emergencia** y se proporciona información adicional sobre la situación.  

En la ilustración siguiente, el aprovisionamiento D representa un pedido de emergencia que ajustar para inventario negativo.  

![Sugerencia de planificación de emergencia para evitar un inventario negativo.](media/nav_app_supply_planning_2_negative_inventory.png "Sugerencia de planificación de emergencia para evitar un inventario negativo")  

1. El suministro **A**, inventario proyectado inicial, está por debajo del punto de reorden.  
2. Se ha creado un nuevo aprovisionamiento programación de forma anticipada (**C**).  

     (Cantidad = Inventario máximo – Nivel de inventario proyectado)  
3. El suministro **A** está cerrado por la demanda **B**, que no se cubre por completo.  

     (La demanda **B** podría intentar programar el aprovisionamiento C, pero el ciclo lo impide).  
4. Se crea un nuevo suministro (**D**) para cubrir la cantidad restante de la demanda **B**.  
5. La demanda **B** está cerrada (creando un aviso al inventario proyectado).  
6. Se cierra el nuevo suministro **D**.  
7. El inventario proyectado se comprueba. No se ha cruzado el punto de reorden.  
8. El suministro **C** está cerrado (no hay más demanda).  
9. Revision final. No hay avisos pendientes en el nivel de inventario.  

En la sección siguiente se describen las características de las cuatro directivas de reorden admitidas.

## <a name="reordering-policies" />Políticas de reorden

Las directivas de reorden definen cuánto se debe pedir cuando se debe reponer el producto. Hay cuatro directivas de reorden.  

### <a name="fixed-reorder-quantity" />Cantidad fija reordenada

La política Cantidad fija reordenada se utiliza normalmente para la planificación de inventario de artículos con las siguientes características:

* Costo de inventario bajo
* Bajo riesgo de obsolescencia
* Bajo número de productos

Normalmente, esta directiva se usa con relación a un punto de reorden que refleja la demanda anticipada durante el plazo del producto.  

#### <a name="calculated-per-time-bucket" />Calculado por ciclo

Si alcanza o cruza el punto de reorden en un intervalo de tiempo (ciclo de pedido), el sistema sugiere dos acciones:

* Crear una nueva orden de suministro para la cantidad de reorden
* Reenviar programar el pedido desde la primera fecha después del final del período de tiempo  

El punto de reorden por ciclos reduce el número de sugerencias de suministro. Refleja un proceso de verificación manual del contenido real de los contenedores en su almacén.  

#### <a name="creates-only-necessary-supply" />Crea solo el aprovisionamiento necesario

Antes de sugerir una nueva orden de suministro para cumplir con un punto de reorden, el sistema de planificación verifica el siguiente suministro:

* Si el suministro ya está pedido
* Si espera recibir el suministro dentro del plazo de entrega del artículo

El sistema no sugerirá una nueva orden de suministro si un suministro llevará el inventario proyectado hasta el punto de reorden dentro del plazo de entrega.  

Los órdenes de suministro que se crean específicamente para satisfacer un punto de reorden se excluyen del equilibrado de suministro normal y no cambiarán. Si desea eliminar gradualmente un artículo que tiene un punto de reorden, revise manualmente sus órdenes de suministros pendientes o cambie la política de reorden a **Lote por lote**. El sistema reducirá o cancelará el suministro extra.  

#### <a name="combines-with-order-modifiers" />Combina con modificadores de pedido

Los modificadores de pedido Cantidad mínima pedido, Cantidad máxima pedida y Múltiplos de pedido no deben desempeñar un rol significativo cuando se usa la directiva Cantidad fija reordenada. Sin embargo, el sistema de planificación los tiene en cuenta:

* Reduzca la cantidad a la cantidad máxima de pedido especificada (y cree dos o más suministros para alcanzar la cantidad total de pedido)
* Aumentar el pedido a la cantidad mínima de pedido especificada
* Redondee la cantidad del pedido para cumplir con un múltiplo de pedido específico  

#### <a name="combines-with-calendars" />Combina con calendarios

Antes de sugerir una nueva orden de suministro para cumplir con un punto de reorden, el sistema de planificación verifica si la orden está programada para un día no laborable. Utiliza los calendarios que especifique en el campo **Código de calendario base** en las páginas **Información de la empresa** y **Tarjeta de ubicación**.  

Si la fecha programada es un día no laborable, el sistema de planificación mueve el pedido al próximo día laborable. Al mover la fecha, se puede dar lugar a una orden que cumpla con el punto de reorden, pero que no cumpla una demanda específica. Para este tipo de demandas sin saldar, el sistema de planificación crea un suministro extra.  

#### <a name="shouldnt-be-used-with-forecasts" />No debe usarse con previsiones

Dado que la demanda prevista aparece expresada ya en el nivel del punto de reorden, no es necesario incluir una previsión en la planificación. Si es necesario basar el plan en una previsión, utilice la directiva de **lote por lote**.  

#### <a name="must-not-be-used-with-reservations" />No se debe usar con reservas

Si ha reservado una cantidad, por ejemplo una cantidad en inventario, para una demanda lejana, podría alterar la base de la planificación. Aunque el nivel de inventario estimado es aceptable en relación con el punto de reorden, las cantidades pueden no estar disponibles. El sistema podría intentar compensar creando órdenes de excepción. Sin embargo, recomendamos que el campo **Reservar** se establezca en **Nunca** en los artículos que se planifican mediante un punto de reorden.

### <a name="maximum-quantity" />Cantidad máxima

La directiva de cantidad máxima es una forma de mantener el inventario mediante un punto de reorden.  

También se aplica a esta directiva todo lo relacionado con la directiva de cantidad de reorden fija. La única diferencia es la cantidad del suministro sugerido. Al usar la directiva de cantidad máxima, la cantidad de la reorden se definirá dinámicamente según el nivel de inventario proyectado. Por lo tanto, generalmente difiere de un pedido a otro.  

#### <a name="calculate-per-time-bucket" />Calculado por ciclo

Cuando alcanza o cruza el punto de reorden, el sistema determina la cantidad de la orden al final de un intervalo de tiempo. Mide la diferencia entre el nivel de inventario proyectado actual y el inventario máximo especificado para determinar la cantidad del pedido. A continuación, el sistema comprueba:

* Si el suministro ya está pedido
* Si espera recibir el suministro dentro del plazo de entrega del artículo

Si es así, el sistema reduce la cantidad de la nueva orden de suministro por las cantidades ya ordenadas.  

Si no especifica una cantidad máxima de inventario, el sistema de planificación garantiza que el inventario proyectado alcance la cantidad de reorden.

#### <a name="combine-with-order-modifiers" />Combinar con modificadores de pedido

Dependiendo de su configuración, podría ser mejor combinar la política de cantidad máxima con modificadores de pedidos: 

* Para garantizar una cantidad de pedido mínima
* Redondear la cantidad a un número entero de unidades de medida de compra
* Dividir la cantidad en lotes, como lo define la cantidad de pedido máximo  

### <a name="combine-with-calendars" />Combinar con calendarios

Antes de sugerir una nueva orden de suministro para cumplir con un punto de reorden, el sistema de planificación verifica si la orden está programada para un día no laborable. Utiliza los calendarios que especifique en el campo **Código de calendario base** en las páginas **Información de la empresa** y **Tarjeta de ubicación**.  

Si la fecha programada es un día no laborable, el sistema de planificación mueve el pedido al próximo día laborable. Al mover la fecha, se puede dar lugar a una orden que cumpla con el punto de reorden, pero que no cumpla una demanda específica. Para este tipo de demandas sin saldar, el sistema de planificación crea un suministro extra.

### <a name="order" />Sentido

En un entorno de fabricación contra pedido, el producto se compra o se produce para cubrir una demanda concreta. Normalmente, la política de reorden de Orden se utiliza para artículos con las siguientes características

* La demanda es poco frecuente
* El tiempo de entrega es insignificante
* Los atributos obligatorios varían  

[!INCLUDE [prod_short](includes/prod_short.md)] crea un vínculo de orden contra orden, que actúa de conexión preliminar entre el suministro (una orden de suministro o inventario) y la demanda que se va a cumplir. Puede aplicar el enlace de pedido a pedido durante la planificación de las siguientes maneras:  

* Al usar la directiva de fabricación Fab-contra-pedido para crear órdenes de producción multinivel o de tipo de proyecto (que producen los componentes necesarios en la misma orden de producción)  
* Al usar la planificación de pedido de venta para crear una orden de producción a partir de un pedido de venta  

> [!TIP]
> Si los atributos de los artículos no varían, podría ser mejor usar una política de reorden de lote por lote. Como resultado, el programa usa un inventario no planificado y solo acumulará las órdenes de venta con la misma fecha de envío o dentro de un ciclo definido.  

#### <a name="order-to-order-links-and-past-due-dates" />Conexiones de pedido contra pedido y fechas vencidas

A diferencia de la mayoría de conjuntos de suministro-demanda, el sistema ha planificado completamente los pedidos vinculados con fechas de vencimiento anteriores a la fecha inicial de planificación. El motivo empresarial de esta excepción es que los conjuntos de demanda-suministro específicos se deben sincronizar. Para obtener más información acerca de la zona congelada aplicable a la mayoría de los tipos de aprovisionamiento-demanda, vaya a [Procesar los pedidos antes de la fecha de inicio de planificación](design-details-balancing-demand-and-supply.md#process-orders-before-the-planning-start-date).

### <a name="lot-for-lot" />Lote a lote

La política Lote por lote es la más flexible porque el sistema solo reacciona a la demanda real. Actúa sobre la demanda anticipada de los pedidos abiertos y previstos y luego liquida la cantidad del pedido en función de la demanda. La directiva está pensada para los productos donde el inventario se puede aceptar pero se debe evitar.  

De alguna manera, la política Lote por lote es similar a la política Pedido. Puede aceptar cantidades en el inventario y agrupa la oferta y la demanda en los intervalos de tiempo que defina.

El intervalo de tiempo se especifica en el campo **Cubo de tiempo** en la página **Tarjeta de artículo**. El tamaño mínimo del período de tiempo es un día, porque es la unidad de medida de tiempo más pequeña en eventos de oferta y demanda en [!INCLUDE [prod_short](includes/prod_short.md)].  

El ciclo también establece límites con respecto a cuándo se debe reprogramar una orden de suministro para cubrir una demanda determinada. El aprovisionamiento dentro del ciclo se vuelve a programar dentro o fuera para cubrir la demanda. El suministro anterior generará un inventario adicional y debe cancelarlo. Para el suministro posterior, cree una nueva orden de suministro.  

Con esta política, puede especificar un stock de seguridad para compensar los cambios en la oferta o para satisfacer una demanda repentina. La política de lote por lote también puede incluir un periodo de tolerancia y una cantidad de tolerancia para reducir la programación de pedidos.  

Junto con el campo **Periodo de reprogramación**, el campo **Periodo de acumulación de lotes** contribuye para definir el ciclo de reorden. Desde la fecha de la primera demanda, todas las demandas se acumulan en el siguiente periodo de acumulación de lotes en una orden de suministro en la fecha de la primera demanda. La demanda que está fuera del periodo de acumulación del lote no queda cubierta por las órdenes de suministro.

Debido a que la cantidad de la orden de suministro se basa en la demanda real, puede tener sentido usar los modificadores de orden:

* Redondee la cantidad del pedido para cumplir con un múltiplo de pedido (o unidad de medida de compra)
* Aumentar el pedido a una cantidad mínima de pedido especificada
* Reduzca la cantidad a la cantidad máxima de pedido especificada (y, por tanto, cree dos o más suministros para alcanzar la cantidad total necesaria)

## <a name="see-also" />Consulte también

[Detalles de diseño: Parámetros de la planificación](design-details-planning-parameters.md)  
[Detalles de diseño: Tabla de asignación de planificación](design-details-planning-assignment-table.md)  
[Detalles de diseño: Conceptos centrales del sistema de planificación](design-details-central-concepts-of-the-planning-system.md)  
[Detalles de diseño: Equilibrio de aprovisionamiento y demanda](design-details-balancing-demand-and-supply.md)  
[Detalles de diseño: Planificación de aprovisionamiento](design-details-supply-planning.md)

[!INCLUDE[footer-include](includes/footer-banner.md)]
