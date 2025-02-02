---
title: Configuración de registro de transacciones entre empresas
description: Aprenda a configurar una asociación entre empresas.
author: brentholtorf
ms.author: bholtorf
ms.reviewer: bnielse
ms.topic: how-to
ms.date: 01/31/2023
ms.custom: bap-template
ms.search.keywords: 'IC, group, consolidation, affiliate, subsidiary'
ms.search.form: '605, 620, 602, 603, 601, 600, 652, 653, 606, 607, 609, 608, 621'
---
# <a name="set-up-intercompany-transactions" />Configurar transacciones entre empresas vinculadas

Las asociaciones entre empresas facilitan el manejo de los procesos contables cuando dos o más filiales de una empresa hacen negocios entre sí con frecuencia. Los socios pueden intercambiar transacciones, como ventas y compras, y gestionarlas de forma manual o automática. Por ejemplo, cuando un socio envía una línea de diario de ventas a otro socio, se crea una línea de diario de compras para el socio receptor.

El catálogo de cuentas de empresas vinculadas puede ser, por ejemplo, una versión del catálogo de cuentas del socio de sincronización. Cada socio asigna sus cuentas al catálogo de cuentas de empresas vinculadas. Cada socio también asigna sus dimensiones y valores de dimensión a las dimensiones de empresas vinculadas.

> [!NOTE]
> En el primer lanzamiento de versiones de 2023, presentamos una página mejorada de **Configuración de empresas vinculadas**. La nueva página facilita la configuración de una asociación entre empresas al consolidar todas las tareas de configuración en una sola página. Si es nuevo en [!INCLUDE [prod_short](includes/prod_short.md)], ya está usando la nueva experiencia. Si ya es un cliente, su administrador puede activar el conmutador de la característica **Aceptar automáticamente transacciones de diario general entre empresas** en la página **Gestión de funciones**.
>
> Las tareas de este artículo asumen que el interruptor de la característica está activado. Si ya configuró una asociación entre empresas, puede continuar usándola.

## <a name="before-you-start" />Antes de comenzar

Antes de comenzar a configurar su asociación entre empresas, hay algunas decisiones que tomar.

|Decisión  |Descripción  |
|---------|---------|
|¿Qué catálogo de cuentas debe ser la base para el catálogo de cuentas de empresas vinculadas?     | Todas las empresas de la sociedad deben utilizar el mismo catálogo de cuentas de empresas vinculadas. Puede basar su catálogo de cuentas de empresas vinculadas en el catálogo de cuentas de una de las empresas de la sociedad o crear un nuevo catálogo de cuentas de empresas vinculadas. Las cuentas que se van a utilizar en la asociación se asignan de ambas maneras, de modo que cada socio envía y recibe transacciones en las cuentas correctas. Obtenga más información sobre cómo configurar el catálogo de cuentas de empresas vinculadas en [Configurar los catálogos de cuentas de empresas vinculadas](#set-up-the-intercompany-charts-of-accounts).         |
|¿Qué dimensiones deben ser la base para las dimensiones de empresas vinculadas?     | Si utiliza dimensiones de empresas vinculadas, deben ser las mismas para todas las empresas de la asociación. Después de especificar sus dimensiones de empresas vinculadas, asigne sus valores de dimensión. Obtenga más información sobre la asignación de valores de dimensión en [Configurar dimensiones de empresas vinculadas](#set-up-intercompany-dimensions).        |
|¿Qué socios son clientes o proveedores, o ambos?     |  Obtenga más información sobre cómo configurar las empresas de clientes y proveedores en una asociación entre empresas vinculadas en [Configurar socios entre empresas como clientes y proveedores](#set-up-intercompany-partners-as-customers-and-vendors).       |
|¿Quiere especificar cuentas bancarias para usar en la asociación?| Puede acelerar el proceso de registro de transacciones de pago especificando la cuenta bancaria que se utilizará para cada empresa de socio. Obtenga más información en [Especificar las cuentas bancarias que se usarán para los socios de empresas vinculadas](#specify-the-bank-accounts-to-use-for-intercompany-partners). |
|¿Cómo desea identificar a las empresas en la asociación?     | Todas las partes deben acordar un código de identificación de socio de empresas vinculadas para cada empresa. Asignará el código a las tarjetas de cliente y proveedor, para identificar transacciones relacionadas. Obtenga más información sobre los identificadores en [Crear serie numérica](ui-create-number-series.md).        |
|¿Cómo desea manejar los números de producto?"     | Si las líneas de empresas vinculadas contienen productos, puede utilizar sus propios números de producto o configurar los números de producto de sus socios para cada producto que corresponda, ya sea en el campo **N.º de producto de proveedor** o en el campo **N.º de producto común** en la ficha del producto. También puede usar la acción **Referencia del producto** para asignar los números de sus productos a las descripciones de los productos de sus socios de empresas vinculadas. Para obtener más información sobre las referencias de productos, vaya a [Usar referencias de productos](inventory-how-use-item-cross-refs.md).        |
|¿Están involucrados los recursos?     | Si las transacciones de ventas entre empresas vinculadas van a incluir recursos, debe rellenar el campo **N.º cuenta de contabilidad de compras de IC** en la tarjeta de recurso de cada recurso. El campo contiene el número de la cuenta contable de empresas vinculadas que la cuenta de este recurso contabilizará en la empresa asociada. Para obtener más información sobre rcursos, vaya a [Configurar recursos](projects-how-setup-resources.md).<br><br>**NOTA**<br>Las transacciones de compra entre empresas que incluyen recursos, activos fijos y cargos por artículos no son totalmente compatibles. En la empresa de socio, el campo **Tipo de línea** estará en blanco en las líneas del documento de compra que incluyan estas entidades. Debe actualizar el campo manualmente.        |

## <a name="overview-of-the-steps-to-get-started" />Resumen de los pasos para empezar

Utilice la página **Configuración de empresas vinculadas** para configurar los siguientes componentes de las transacciones de empresas vinculadas:

* La configuración de empresas vinculadas de su empresa.
* La empresa que será el socio de sincronización.
* El catálogo de cuentas de empresas vinculadas que todos los socios usan para intercambiar transacciones.
* Las asignaciones entre cuentas del catálogo de cuentas y el catálogo de cuentas de empresas vinculadas para las transacciones entrantes y salientes de cada socio.
* Las dimensiones y valores de dimensión de empresas vinculadas a usar, y cómo se asignan a las dimensiones para cada socio.
* Las empresas que son los socios de empresas vinculadas.
* Las empresas que son proveedores o clientes, o ambos.

## <a name="set-up-a-synchronization-partner" />Configurar un socio de sincronización

Todos los socios deben usar el mismo catálogo de cuentas de empresas vinculadas y, si es necesario, las mismas dimensiones de empresas vinculadas. Puede ahorrar tiempo al configurar la asociación utilizando el catálogo de cuentas y las dimensiones de uno de los socios como línea de base para el catálogo de cuentas y las dimensiones de empresas vinculadas. La empresa que utiliza como referencia se denomina *socio de sincronización*. Por lo general, el socio de sincronización es la empresa central, pero no tiene por qué serlo.

En la página **Configuración de empresas vinculadas**, cada socio especifica el socio de sincronización en el campo **Socio de sincronización** . Posteriormente, el catálogo de cuentas de empresas vinculadas y las dimensiones de empresas vinculadas se especifican automáticamente para ellos, en función de la configuración del socio de sincronización. A continuación, los socios utilizan las páginas **Asignación de catálogo de cuentas de empresas vinculadas** y **Asignación de dimensiones de empresas vinculadas** para asignar su catálogo de cuentas y dimensiones al catálogo de cuentas y a las dimensiones de empresas vinculadas, y viceversa. 

Cuando esté listo para sincronizar datos con su socio de sincronización, elija la acción **Configuración de sincronización** .

> [!NOTE]
> Es importante asignar cuentas y dimensiones en ambas direcciones. Es decir, tanto al catálogo de cuentas y las dimensiones de empresas vinculadas, como de ellos a sus propias cuentas y dimensiones.

## <a name="set-up-the-intercompany-charts-of-accounts" />Configurar los planes de cuentas de las empresas vinculadas

Todos los socios deben utilizar el mismo catálogo de cuentas de empresas vinculadas y asignarle las cuentas de su propio catálogo de cuentas. Si el catálogo de cuentas de su empresa define el catálogo de cuentas de empresas vinculadas para las empresas de su socio, siga los pasos de esta sección.

Si usa un archivo XML que contiene el catálogo de cuentas de empresas vinculadas, siga los pasos de la sección [Importar o exportar un catálogo de cuentas de empresas vinculadas](intercompany-how-setup.md#import-or-export-an-intercompany-chart-of-accounts).  

1. Elija el icono ![Bombilla que abre la función Dígame.](media/ui-search/search_small.png "Dígame qué desea hacer") icono, escriba **Configuración de empresas vinculadas** y luego elija el enlace relacionado.
2. Elija la acción **Catálogo de cuentas de empresas vinculadas**.
3. Para agregar cuentas, haga una de las opciones siguientes de la página **Catálogo de cuentas de empresas vinculadas**:
    * Elija **Nuevo** y luego introduzca cada cuenta en una línea de la página.  
    * Si su plan de cuentas de empresas vinculadas va a ser idéntico o similar al suyo habitual, puede rellenar la página automáticamente mediante la acción **Copiar de Plan de cuentas**. Puede editar las líneas nuevas si es necesario.
    * Si configuró un catálogo de cuentas de empresas vinculadas para un socio de sincronización, utilice la acción **Configuración de sincronización** para copiar esas cuentas.

    > [!TIP]
    > Si copia el catálogo de cuentas de empresas vinculadas de un socio de sincronización, puede usar la acción **Configuración de sincronización** para actualizar sus cuentas de empresas vinculadas con cualquier cambio que el socio realice en las suyas.

El próximo paso es asignar su catálogo de cuentas al catálogo de cuentas de empresas vinculadas. Obtenga más información en [Asignar el catálogo de cuentas de empresas vinculadas al catálogo de cuentas de la empresa propia](#map-the-intercompany-chart-of-accounts-to-your-companys-chart-of-accounts).

### <a name="import-or-export-an-intercompany-chart-of-accounts" />Importar o exportar el catálogo de cuentas de empresas vinculadas

La empresa de sincronización puede compartir su catálogo de cuentas con socios exportándolo a un archivo. Los socios pueden importar el archivo para obtener el catálogo de cuentas.

1. Elija el icono ![Bombilla que abre la función Dígame.](media/ui-search/search_small.png "Dígame qué desea hacer") icono, escriba **Configuración de empresas vinculadas** y luego elija el enlace relacionado.
2. Elija la acción **Catálogo de cuentas de empresas vinculadas**.
3. En la página **Catálogo de cuentas de empresas vinculadas**, seleccione la acción **Importar/Exportar** y, a continuación, **Importar** o **Exportar**.
4. Elija el archivo para importar o exportar.  

La página **Catálogo de cuentas de empresas vinculadas** se rellena con las líneas de cuentas de contabilidad general nuevas o modificadas, según el catálogo de cuentas de empresas vinculadas del archivo. Las líneas existentes, no relacionadas en la página permanecen sin cambios.

## <a name="map-the-intercompany-chart-of-accounts-to-your-companys-chart-of-accounts" />Asignar el catálogo de cuentas de empresas vinculadas al catálogo de cuentas de la empresa propia

Cuando haya definido o importado el catálogo de cuentas de empresas vinculadas, asigne cada cuenta de empresas vinculadas a una de sus cuentas. En la página **Catálogo de cuentas de empresas vinculadas**, puede especificar cómo se asignan las cuentas de contabilidad general de empresas vinculadas de las transacciones entrantes a las cuentas de contabilidad general del catálogo de cuentas de su empresa.

Si las cuentas de empresas vinculadas y sus cuentas tienen los mismos números, puede asignar las cuentas automáticamente.

1. Elija el icono ![Bombilla que abre la función Dígame.](media/ui-search/search_small.png "Dígame qué desea hacer") icono, escriba **Configuración de empresas vinculadas** y luego elija el enlace relacionado.  
2. Elija la acción **Catálogo de cuentas de empresas vinculadas**.

    > [!TIP]
    > Para acceder a las acciones de la página, es posible que deba expandir la página a la vista de diseño amplia.

3. En la página **Catálogo de cuentas de empresas vinculadas**, seleccione la acción **Asignación de catálogo de cuentas**.
4. Puede asignar las cuentas de forma automática o manual.

    * Para crear manualmente la asignación, en los paneles **Catálogo de cuentas de empresas vinculadas** y **Catálogo de cuentas de C/G**, seleccione una cuenta y, a continuación, elija una cuenta en el campo **N.º de contabilidad general.** y **N.º de empresa vinculada.** .
    * Para asignar automáticamente cuentas que tienen los mismos números, seleccione las líneas que desea asignar, elija la acción **Asignar a cuenta con igual n.º** y, luego, elija el catálogo de cuentas que se va a actualizar.

    > [!TIP]
    > Si desea asignar muchas o quizás todas las cuentas, elija una línea, elija :::image type="icon" source="media/show-more-options-icon.png" border="false"::: y luego elija **Seleccionar más**.

## <a name="set-up-intercompany-dimensions" />Configurar dimensiones de empresas vinculadas

Si los socios van a intercambiar transacciones con dimensiones relacionadas con ellos, debe estar de acuerdo en las dimensiones que todos usarán. Por ejemplo, la empresa de sincronización puede crear una versión simplificada de sus dimensiones, exportarlas a un archivo XML y luego distribuir el archivo a cada socio. Cada socio puede importar el archivo XML en la página **Dimensiones de empresas vinculadas** y luego asignar las dimensiones de empresas vinculadas a sus dimensiones. Más información en [Asignar dimensiones de empresas vinculadas a las dimensiones de su empresa](#map-intercompany-dimensions-to-your-companys-dimensions).

> [!NOTE]
> Cada empresa debe asignar sus dimensiones a las dimensiones de empresas vinculadas para documentos salientes y documentos entrantes. La asignación de cuentas en ambas direcciones es importante y ayuda a mantener la coherencia entre las empresas.

Si los socios utilizarán las dimensiones de empresas vinculadas del socio de sincronización, siga los pasos de esta sección. Si quiere compartir usando un archivo XML que contiene las dimensiones de empresas vinculadas, siga los pasos de [Importar o exportar dimensiones de empresas vinculadas](#import-or-export-intercompany-dimensions).

1. Elija el icono ![Bombilla que abre la función Dígame.](media/ui-search/search_small.png "Dígame qué desea hacer") icono, escriba **Configuración de empresas vinculadas** y luego elija el enlace relacionado.  
2. Seleccione la acción **Dimensiones de empresas vinculadas**.
3. Para agregar dimensiones, haga algo de lo siguiente en la página **Dimensiones de empresas vinculadas**:
    * Elija **Nuevo** y luego introduzca cada dimensión en una línea.  
    * Si sus dimensiones de empresas vinculadas van a ser idénticas o similares a sus dimensiones regulares, puede rellenar la página automáticamente mediante la acción **Copiar de dimensiones**. Luego, puede editar las líneas nuevas si es necesario.
    * Si ha especificado unas dimensiones de empresas vinculadas especificadas para un socio de sincronización, utilice la acción **Configuración de sincronización** para copiar esas dimensiones.

    > [!TIP]
    > Si copia las dimensiones de empresas vinculadas de un socio de sincronización, puede usar la acción **Configuración de sincronización** para actualizarlas dimensiones de las empresas vinculadas con cualquier cambio que el socio realice en las suyas.  

### <a name="import-or-export-intercompany-dimensions" />Importar o exportar dimensiones de empresas vinculadas

La empresa de sincronización puede compartir sus dimensiones con socios exportándolas a un archivo. Los socios pueden importar el archivo para obtener las dimensiones.

1. Elija el icono ![Bombilla que abre la función Dígame.](media/ui-search/search_small.png "Dígame qué desea hacer") icono, escriba **Configuración de empresas vinculadas** y luego elija el enlace relacionado.
2. Seleccione la acción **Dimensiones de empresas vinculadas**.  
3. En la página **Dimensiones de empresas vinculadas**, seleccione la acción **Importar/Exportar** y, a continuación, **Importar** o **Exportar**.
4. Elija el archivo para importar o exportar.

El siguiente paso es asignar las dimensiones con las cimensiones de empresas vinculadas. Más información en [Asignar dimensiones de empresas vinculadas a las dimensiones de su empresa](#map-intercompany-dimensions-to-your-companys-dimensions).

### <a name="map-intercompany-dimensions-to-your-companys-dimensions" />Asignar dimensiones de empresas vinculadas a las dimensiones de su empresa

Una vez especifique las dimensiones que usará, asigne cada una de las dimensiones de empresas vinculadas a una de las dimensiones de su empresa y a la inversa. Utilice la página **Asignación de dimensiones entre empresas vinculadas** para especificar la asignación. Luego, repita el proceso para los valores de dimensión.

* Especifique cómo se asignan las dimensiones de empresas vinculadas en las transacciones entrantes a las dimensiones de la lista de dimensiones de su empresa.
* Especifique cómo se transformarán sus dimensiones en dimensiones de empresas vinculadas, en *transacciones salientes*.

Si alguna de las dimensiones de empresas vinculadas tiene el mismo código que las dimensiones correspondientes de su empresa, puede dejar que el programa realice automáticamente las asignaciones de dimensión.  

En los siguientes pasos, primero asigna dimensiones de empresas vinculadas a dimensiones para documentos entrantes en el panel **Dimensiones de empresas vinculadas**. Luego, asigna dimensiones a dimensiones de empresas vinculadas para documentos salientes en el panel **Dimensiones de la empresa actual**.

1. Elija el icono ![Bombilla que abre la función Dígame.](media/ui-search/search_small.png "Dígame qué desea hacer") icono, escriba **Configuración de empresas vinculadas** y luego elija el enlace relacionado.
2. Seleccione la acción **Dimensiones de empresas vinculadas**.
3. En la página **Dimensiones de empresas vinculadas**, seleccione la acción **Asignación de dimensiones**.
4. Puede asignar las dimensiones de forma automática o manual.

    * Para crear manualmente la asignación, en los paneles **Dimensiones de empresas vinculadas** y **Dimensiones de la empresa actual** , elija una dimensión y luego elija una dimensión en los campos **Código de dimensión** y **Código de dimensión de empresas vinculadas**.
    * Para asignar automáticamente cuentas que tienen los mismos números, seleccione las líneas que desea asignar, elija la acción **Asignar dimensiones con el mismo código** y luego elija las dimensiones a actualizar. 

    > [!TIP]
    > Si desea asignar muchas o quizás todas las dimensiones, elija una línea, elija :::image type="icon" source="media/show-more-options-icon.png" border="false"::: y luego elija **Seleccionar más**.

5. Seleccione la acción **Asignación de valores de dimensiones**.
6. En la página **Asignación de valores de dimensión de empresas vinculadas** , los pasos para crear la asignación son similares a los que acaba de hacer para las dimensiones.

## <a name="set-up-intercompany-general-journal-templates-and-batches" />Configurar libros y lotes de diario general de empresas vinculadas

Debe configurar un libro de diario general y un lote de diario general para usar de forma predeterminada para las transacciones de empresas vinculadas. La plantilla y el lote son especialmente importantes si acepta automáticamente transacciones entre empresas de sus socios. Para obtener más información sobre la aceptación automática de transacciones, vaya a [Aceptación automática de transacciones de socios de empresas vinculadas](#auto-accept-transactions-from-intercompany-partners).   

* Los diarios generales se utilizan para registrar en cuentas contables y otras cuentas, como bancarias, de clientes y de proveedores. Registrar con un diario general siempre crea movimientos en cuentas contables.  Utilice la página **Diario general de empresas vinculadas** para configurar el lote de diario general que se utilizará. La configuración que es específica para las transacciones entre empresas son las cuentas que especifica en los campos **Tipo de cuenta de empresa vinculada** y **Número de cuenta de empresa vinculada**.
* Los libros de diario le ofrecen una página de diario diseñada para un propósito específico. Es decir, los campos de los libros de diario serán exactamente los necesarios para una parte determinada del programa. Utilice la página **Libros de diario general** para configurar un libro para usar en transacciones de empresas vinculadas.

Para obtener más información sobre los libros y los lotes de diarios generales, vaya a [Usar libros y lotes de diarios](ui-work-general-journals.md#use-journal-templates-and-batches).

## <a name="set-up-a-company-for-intercompany-transactions" />Establecer una empresa para transacciones entre empresas vinculadas

En los siguientes pasos, se asume que un socio de sincronización está configurado con el catálogo de cuentas y las dimensiones en los que basará el catálogo de cuentas y las dimensiones de empresas vinculadas. Puede configurarlos usted mismo, pero normalmente es más rápido comenzar si utiliza un socio de sincronización y, además, el mantenimiento es más fácil. Obtenga más información sobre el socio de sincronización, vaya a [Configurar un socio de sincronización](#set-up-a-synchronization-partner).

> [!TIP]
> Es una buena idea completar los campos de la ficha desplegable **General** en la página **Configuración de empresas vinculadas** para cada socio antes de que usted agregue a sus socios. Cuando agrega empresas asociadas que están en el mismo suscriptor, [!INCLUDE [prod_short](includes/prod_short.md)] obtiene su código de empresa vinculada y el nombre de la empresa de su configuración en la ficha desplegable General. El campo **Nombre de la empresa** verificará que su código IC sea único.

> [!NOTE]
> Si utilizará un socio de sincronización, deje el campo **Socio de sincronización** en blanco cuando configure esa empresa para la asociación.

1. Elija el icono ![Bombilla que abre la función Dígame.](media/ui-search/search_small.png "Dígame qué desea hacer") icono, escriba **Configuración de empresas vinculadas** y luego elija el enlace relacionado.  
2. En la página **Configuración de empresas vinculadas**, rellene el resto de los campos de la ficha desplegable **General**. [!INCLUDE[tooltip-inline-tip](includes/tooltip-inline-tip_md.md)]

> [!NOTE]
> En [!INCLUDE[prod_short](includes/prod_short.md)] en línea, no puede utilizar ubicaciones de archivos para transferir transacciones a sus socios porque [!INCLUDE[prod_short](includes/prod_short.md)] no tiene acceso a su red local. Por tanto, si elige **Ubicación del archivo** en el campo **Tipo de transferencia**, el campo **Ruta de la carpeta** no está disponible. En su lugar, el archivo se descargará a la carpeta **Descargas** de su equipo. Luego envía el archivo a alguien de la empresa asociada, por ejemplo, por correo electrónico. Para un proceso más directo, le recomendamos que elija **Correo electrónico**.

El siguiente paso es configurar las empresas de socios.

## <a name="set-up-intercompany-partners" />Configurar socios de empresas vinculadas

Cada socio debe agregar todas las demás empresas de la asociación como si fueran un socio.

1. Elija el icono ![Bombilla que abre la función Dígame.](media/ui-search/search_small.png "Dígame qué desea hacer") icono, escriba **Configuración de empresas vinculadas** y luego elija el enlace relacionado.
2. En la ficha desplegable **Socios de empresas vinculadas** , elija **Agregar**.
3. En la página **Socio de empresas vinculadas**, rellene los campos. [!INCLUDE[tooltip-inline-tip](includes/tooltip-inline-tip_md.md)]
4. Repita los pasos 2 y 3 para todas las empresas de la asociación.

> [!NOTE]
> Para la contabilización de empresas vinculadas, si activa la alternancia **Aceptar automáticamente transacciones** en la página **Socio de empresas vinculadas**, [!INCLUDE[prod_short](includes/prod_short.md)] suprime los mensajes de advertencia sobre facturas de compra que duplican el pedido de compra original. Es importante contar con un proceso de empresa para gestionar los duplicados. Por ejemplo, eliminando dichos pedidos de compra cuando se recibe la factura de compra del socio de empresas vinculadas.

### <a name="set-up-intercompany-partners-as-customers-and-vendors" />Configurar socios de empresas vinculadas como empresas y proveedores

1. Elija el icono ![Bombilla que abre la función Dígame.](media/ui-search/search_small.png "Dígame qué desea hacer") icono, escriba **Configuración de empresas vinculadas** y luego elija el enlace relacionado.
2. En la ficha desplegable **Socios de empresas vinculadas** , abra la página de la tarjeta del socio.
3. Según lo que desee hacer, elija el cliente o socio en los campos **N.º de cliente.** o **N.º de proveedor**.

    > [!NOTE]
    > Si no se ha creado el cliente o proveedor, puede elegir **+Nuevo** en el menú desplegable para configurarlos. Para obtener más información sobre cómo crear clientes y proveedores, vaya a [Registrar nuevos clientes](sales-how-register-new-customers.md) y [Registrar nuevos proveedores](purchasing-how-register-new-vendors.md).

    > [!TIP]
    > También puede especificar un cliente o proveedor como socio de empresas vinculadas, rellenando el campo **Código socio IC** en las páginas **Tarjeta de cliente** y **Tarjeta de proveedor**.

### <a name="set-up-default-intercompany-partner-general-ledger-accounts" />Configurar cuentas de contabilidad de socios de empresas vinculadas predeterminadas

Cuando crea una línea de venta o de compra de empresas vinculadas para enviarla como transacción saliente, indique una cuenta del catálogo de cuentas de empresas vinculadas como cuenta predeterminada en la que se registre el importe de la empresa asociada. En la página **Tarjeta de cuenta contable**, para las cuentas que utiliza regularmente en líneas de ventas o compras salientes de empresas intervinculadas, puede especificar una cuenta genérica de empresa vinculada asociada. Por ejemplo, para su cuenta de clientes, puede introducir las cuentas de proveedores correspondientes desde el plan de cuentas de empresas vinculadas. Las cuentas de clientes y proveedores se utilizan como cuenta de compensación para el socio de empresas vinculadas cuando registra transacciones en los diarios generales de empresas vinculadas.  

Ahora, cuando introduzca una cuenta contable en el campo **Cta. contrapartida** en una línea de empresas vinculadas con **Socio de empresas vinculadas** en el campo **Tipo de cuenta** el campo **Cuentas genéricas de empresas vinculadas asociadas** se rellenará automáticamente.  

1. Elija el icono ![Bombilla que abre la función Dígame.](media/ui-search/search_small.png "Dígame qué desea hacer") , escriba **Catálogo de cuentas** y, luego, elija el vínculo relacionado.  
2. Abra la cuenta contable que se utiliza para transacciones entre empresas vinculadas y, en el campo **Cuentas contables predeterminadas de empresas vinculadas asociadas**, introduzca la cuenta de contabilidad general entre empresas vinculadas que su socio contabilizará cuando registre en la cuenta de contabilidad en la línea.
3. Repita el paso 2 para cada cuenta que introduzca a menudo en el campo **Cta. contrapartida** en un diario o documento de empresas vinculadas.

### <a name="auto-accept-transactions-from-intercompany-partners" />Aceptación automática de transacciones de socios de empresas vinculadas

Para agilizar el proceso de transacciones de empresas vinculadas, puede especificar si quiere que esta empresa cree automáticamente líneas de diario en función de las contabilizaciones de un socio de empresas vinculadas desde la página **Diario general de empresas vinculadas**. Para crear automáticamente transacciones entrantes y salientes, debe activar las siguientes opciones para cada socio:

* En la página **Configuración de empresas vinculadas**, active la opción **Enviar automáticamente transacciones** para el socio de sincronización. A continuación, especifique dónde crear las transacciones de diario de empresas vinculadas recibidas completando los campos **Plantilla Jnl. general de iC predeterminada** y **Lote Jnl. general de iC predeterminado**.

    > [!TIP]
    > Si el campo **Libro predeterminado de diario general de empresas vinculadas** está en blanco, debe configurar un libro de diario general para usar en sus diarios generales de empresas vinculadas. Para obtener más información sobre los libros y los lotes, vaya a [Configurar libros y lotes de diario general de empresas vinculadas](#set-up-intercompany-general-journal-templates-and-batches)    

* En la página **Socio de empresas vinculadas**, active la opción **Aceptar automáticamente transacciones** .

Las líneas de diario se crean automáticamente, pero no se contabilizan.

> [!NOTE]
> Si su organización usó características de empresas vinculadas en [!INCLUDE [prod_short](includes/prod_short.md)] antes del lanzamiento de versiones 1 de 2022, para aceptar transacciones automáticamente, su administrador debe activar el conmutador de característica **Aceptar automáticamente transacciones del diario general de empresas vinculadas** en la página **Administración de características**.

### <a name="specify-the-bank-accounts-to-use-for-intercompany-partners" />Especificar las cuentas bancarias que se usarán para los socios de empresas vinculadas

Para facilitar los pagos rápidos, especifique una o más cuentas bancarias para usar con socios de empresas vinculadas. Cuando un socio utiliza un diario general de empresas vinculadas para realizar un pago, puede especificar la cuenta bancaria en la línea. La cuenta bancaria se utiliza como cuenta de contrapartida en la empresa receptora, lo que minimiza la necesidad de introducir transacciones manualmente.

* Para especificar la cuenta bancaria a utilizar, en la página **Socios de empresas vinculadas** elija la acción **Cuentas bancarias**. En la **Tarjeta de cuenta bancaria interempresas**, introduzca la información de la cuenta.

## <a name="troubleshoot-your-intercompany-setup" />Solucionar problemas de configuración entre empresas

En la página **Configuración de empresas vinculadas**, el panel **Diagnósticos de configuración de empresas vinculadas** contiene mosaicos que indican si ha configurado todos los componentes necesarios para intercambiar transacciones entre empresas. Los mosaicos también están disponibles en el área de tareas de Business Manager. Elige los mosaicos para descubrir qué falta. Para obtener una descripción general de los componentes necesarios, vaya a [Descripción general de los pasos para comenzar](#overview-of-the-steps-to-get-started).

## <a name="see-also" />Consulte también

[Gestión de transacciones entre empresas vinculadas](intercompany-manage.md)  
[Finanzas](finance.md)  
[Configurar las finanzas](finance-setup-finance.md)  
[Trabajar con diarios generales](ui-work-general-journals.md)  
[Trabajar con [!INCLUDE[prod_short](includes/prod_short.md)]](ui-work-product.md)

[!INCLUDE[footer-include](includes/footer-banner.md)]
