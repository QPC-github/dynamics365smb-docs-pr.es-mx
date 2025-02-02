---
title: Auditar cambios
description: Puede activar el registro de usuario para tener un historial de los cambios realizados en los datos de las tablas de las que se hace el seguimiento. También puede realizar un seguimiento de actividades con ciertos tipos de registros de actividad.
author: edupont04
ms.topic: get-started-article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: 'user log, user activity, tracking'
ms.search.form: '592, 593, 594, 595, 710, 1366, 1367, 1368, 1369'
ms.date: 03/24/2022
ms.author: edupont
---
# <a name="auditing-changes-in-business-central" />Auditar cambios en Business Central

Un desafío común en muchas aplicaciones de gestión empresarial es evitar cambios no deseados en los datos. Podría ser cualquier cosa, desde un número de teléfono incorrecto de un cliente hasta un registro incorrecto en la contabilidad. Este tema describe las capacidades para averiguar qué cambió, quién lo cambió y cuándo se realizó el cambio.

## <a name="about-the-change-log" />Sobre el Registro de cambios

El registro de cambios permite realizar un seguimiento de todas las modificaciones directas que realiza un usuario a los datos de la base de datos. Especifique cada tabla y campo lo que desea que el sistema registre y, a continuación, active el registro de cambios. El registro de cambios se basa en los cambios realizados en los datos en las tablas que se siguen. En la página **Cambiar entradas del registro**, las entradas se ordenan cronológicamente y se muestran todos los cambios realizados en los valores de los campos, de las tablas que especifique. 

El seguimiento de cambios puede afectar al rendimiento, lo que puede demandarle tiempo, además de aumentar el tamaño de la base de datos, lo que podría costarle dinero. Para reducir esos costos, tenga en cuenta lo siguiente:

- Tenga cuidado al elegir las tablas y las operaciones.
- No agregue asientos contables ni documentos registrados. En su lugar, priorice los campos del sistema como Creado por y Fecha de creación.
- No utilice el tipo de seguimiento Todos los campos. En su lugar, elija Algunos campos y realice un seguimiento solo de los campos más importantes.

También por motivos de rendimiento, el registro de cambios se desactiva durante el proceso de actualización de [!INCLUDE [prod_short](includes/prod_short.md)] a la próxima versión. Además de acelerar el proceso de actualización, esto también ayuda a reducir el desorden en el registro de oportunidades. Tan pronto como se completa la actualización, el registro comienza a rastrear los cambios nuevamente.

> [!Important]
> Los cambios se muestran en **Cambiar entradas de registro** solo después de reiniciar la sesión del usuario, lo que sucede de la siguiente manera:
>
> * La sesión ha caducado y se ha actualizado.
> * El usuario seleccionó otra empresa o área de tareas.
> * El usuario ha cerrado sesión y ha vuelto a iniciar sesión.

### <a name="work-with-the-change-log" />Trabajar con el registro de cambios
El registro de cambios se activa y desactiva en la página **Config. log cambio**. Si un usuario activa o desactiva el registro de cambios, se registra esta actividad, de modo que siempre puede ver qué usuario ha activado o reactivado el registro de cambios.

En la página **Config. log cambio**, si elige la acción **Tablas**, puede especificar de qué tablas que desea realizar el seguimiento de los cambios y de qué cambios desea efectuar el seguimiento. [!INCLUDE[prod_short](includes/prod_short.md)] también realiza el seguimiento de varias tablas del sistema.

> [!NOTE]
> Puede monitorear campos específicos para detectar cambios, como campos que contienen datos confidenciales, configurando el monitoreo de campos. Si lo hace, para evitar la redundancia, la tabla que contiene el campo no estará disponible para la configuración del registro de cambios. Para más información, consulte [Supervisión de campos confidenciales](across-log-changes.md#monitoring-sensitive-fields).

Después de haber configurado el registro de cambios, haberlo activado y alguien haya realizado un cambio en los datos, puede ver y filtrar los cambios en la página **Movs. registro cambios**. Si desea eliminar movimientos, puede hacerlo en la página **Eliminar movs. reg. de cambios**, donde puede definir filtros basados en fechas y horas.  

## <a name="about-activity-logs" />Acerca de los registros de actividad

Desde algunas páginas en [!INCLUDE [prod_short](includes/prod_short.md)], puede ver un registro de actividad que muestra el estado y los errores de los archivos que exporta o importa [!INCLUDE [prod_short](includes/prod_short.md)].  

### <a name="work-with-activity-logs" />Trabajar con registros de actividad
La información se muestra en la página **Registro de actividad**, según el contexto desde el que se abra. Por ejemplo, puede abrir la página desde las páginas **Configuración del servicio de intercambio de documentos**, **Documento entrante**, **Factura de venta registrada** y **Nota de crédito de venta registrada**. Puede vaciar la lista de entradas de registro o simplemente borrar la lista de entradas anteriores a siete días.  

## <a name="monitoring-sensitive-fields" />Supervisar campos confidenciales

Mantener los datos confidenciales seguros y privados es una preocupación fundamental para la mayoría de las empresas. Para agregar una capa de seguridad, puede monitorear campos importantes y recibir notificaciones por correo electrónico cuando alguien cambia un valor. Por ejemplo, es posible que desee recibir una notificación si alguien cambia el número IBAN de su empresa.

> [!NOTE]
> El envío de notificaciones por correo electrónico requiere que configure la función de correo electrónico en [!INCLUDE[prod_short](includes/prod_short.md)]. Para obtener más información, consulte [Configurar correo electrónico](admin-how-setup-email.md).

### <a name="setting-up-field-monitoring" />Configuración de supervisión de campos

Puede usar la guía de configuración asistida **Configurar el cambio de campo del monitor** para especificar los campos que desea supervisar en función de los criterios de filtrado, como la clasificación de confidencialidad de datos para los campos. Para obtener más información, consulte [Clasificación de confidencialidad de datos](admin-classifying-data-sensitivity.md). La guía también le permite especificar la persona que recibirá una notificación por correo electrónico cuando se produzca un cambio y la cuenta de correo electrónico que enviará la notificación por correo electrónico. Especifique tanto la notificación del usuario como la cuenta desde la que enviar la notificación. Una vez que termine la guía, puede administrar la configuración para el monitoreo de campo en la página **Configuración de monitoreo de campo**. 

> [!NOTE]
> Cuando especifica la cuenta de correo electrónico desde la cual enviar notificaciones, debe agregar los tipos de cuenta **Microsoft 365** o **SMTP**. Las notificaciones deben enviarse desde una cuenta que no esté asociada con un usuario real. Por lo tanto, no puede elegir el tipo de usuario **Usuario actual**. Si lo hace, no se enviarán notificaciones. 

Con el tiempo, la lista de entradas de la página **Entradas de registro de campos supervisados** crecerá. Para reducir la cantidad de entradas, puede crear una directiva de retención que eliminará las entradas después de un período de tiempo específico. Para obtener más información, consulte [Definir directivas de retención](admin-data-retention-policies.md).

Cuando configura el monitoreo de campo o cambia algo en la configuración, se crean entradas para sus cambios. Puede especificar si mostrar las entradas relacionadas con la configuración de monitoreo, mostrándolas u ocultándolas. 

Puede administrar la configuración para el monitoreo de campo, como enviar una notificación por correo electrónico o simplemente registrar el cambio, para cada campo de la página **Hoja de trabajo de campos monitoreados**. La página también es donde puede agregar o eliminar campos para monitorear.

> [!NOTE]
> Después de agregar uno o más campos y comenzar a monitorear, debe cerrar sesión en [!INCLUDE[prod_short](includes/prod_short.md)] e iniciar sesión nuevamente para aplicar su configuración.

### <a name="work-with-field-monitoring" />Trabajar con la supervisión de campos

Las entradas para todos los valores modificados para los campos supervisados están disponibles en la página **Entradas de registro de campos supervisados**. Por ejemplo, las entradas contienen la siguiente información:

* El campo para el que se cambió el valor.
* Los valores originales y nuevos.
* Quién hizo el cambio y cuándo lo hizo. 

Para investigar más a fondo un cambio, elija un valor para abrir la página donde se realizó. Para ver una lista de todas las entradas, elija **Entradas de cambio de campo**.

### <a name="viewing-field-monitoring-telemetry" />Ver la telemetría de monitoreo de campo

Puede configurar [!INCLUDE[prod_short](includes/prod_short.md)] para enviar la actividad de seguimiento de campo a un recurso de Application Insights en Microsoft Azure. Luego, con Azure Monitor, crea informes y configura alertas sobre los datos recopilados. Para obtener más información, consulte los siguientes artículos en la ayuda para desarrolladores y profesionales de TI de [!INCLUDE[prod_short](includes/prod_short.md)]:

- [Supervisión y análisis de telemetría: habilitación de Application Insights](/dynamics365/business-central/dev-itpro/administration/telemetry-overview#enable)
- [Análisis de la telemetría de monitoreo de campo](/dynamics365/business-central/dev-itpro/administration/telemetry-field-monitoring-trace)

## <a name="defining-retention-policies" />Definición de directivas de retención

Puede crear directivas de retención para eliminar los datos innecesarios de los registros después de un período de tiempo que especifique. Por ejemplo, con el tiempo puede crecer el número de entradas en un registro. Al limpiar las entradas antiguas, puede hacer que sea más fácil centrarse en las entradas más recientes y, probablemente, más relevantes. Para obtener más información, consulte [Definir directivas de retención](admin-data-retention-policies.md).

## <a name="see-also" />Consulte también

[Cambiar la configuración básica](ui-change-basic-settings.md)  
[Ordenar, buscar y filtrar](ui-enter-criteria-filters.md)  
[Búsqueda de páginas e información con Dígame](ui-search.md)  
[Asignar permisos a usuarios y grupos](ui-define-granular-permissions.md)    
[Trabajar con [!INCLUDE[prod_short](includes/prod_short.md)]](ui-work-product.md)  
[Definir directivas de retención](admin-data-retention-policies.md)  

[!INCLUDE[footer-include](includes/footer-banner.md)]
