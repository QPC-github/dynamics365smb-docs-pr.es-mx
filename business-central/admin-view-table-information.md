---
title: Ver información de tabla
description: Descubra cómo puede ver información sobre las tablas de bases de datos en Business Central.
author: jswymer
ms.topic: conceptual
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.form: 8700
ms.date: 08/23/2022
ms.author: jswymer
---

# <a name="viewing-table-information" />Visualización de información de tabla

La página **Información de la tabla 8700** proporciona información sobre el número de registros en todo el sistema y tablas de negocios en [!INCLUDE[prod_short](includes/prod_short.md)] y cuántos datos contiene cada tabla.

Esta información es útil para solucionar problemas de rendimiento, porque le permite ver la distribución del tamaño de los datos en las tablas.

## <a name="viewing-table-information" />Visualización de información de tabla

Para abrir esta página, seleccione el icono ![Buscar página o informe.](media/ui-search/search_small.png "Icono de Buscar por página o informe") , escriba **Información de tabla** y luego elija el enlace relacionado.

La siguiente tabla describe la información proporcionada para cada tabla:

|Columna|Description|
|------|-----------|
|Nombre de la empresa|El nombre de la empresa, si existe, a la que pertenece la tabla.|
|Nombre de la tabla|El nombre de la tabla.|
|Tabla n.º|El id. de la tabla.|
|N.º de registros|El número total de registros almacenados en la tabla.|
|Tamaño del registro|El tamaño de registro promedio en KB/registro. El valor se calcula utilizando la siguiente fórmula: 1024 (Tamaño)/(N.º de registros). |
|Tamaño (KB)|La cantidad de espacio que ocupa la tabla en la base de datos. Este valor es la suma de valores de los campos Tamaño de datos y Tamaño del índice.|
|Tamaño de datos (KB)|Cantidad de espacio que ocupan los datos de la tabla en la base de datos.|
|Tamaño de índice (KB)|Cantidad de espacio que los índices de tabla (claves) ocupan en la base de datos.|
|Compresión|El tipo de compresión, **Fila**, **Página** o **Ninguna** que se aplica a la tabla en la base de datos. Para obtener más información, consulte [Compresión de datos](/sql/relational-databases/data-compression/data-compression?).|

> [!NOTE]
> Si elimina datos en una tabla, [!INCLUDE[prod_short](includes/prod_short.md)] inicia varios procesos detrás de escena para asegurarse de que todo esté limpio en su base de datos. Los valores en la página Información de la tabla no se actualizarán hasta que se completen esos procesos, lo que puede demorar un tiempo. La cantidad de tiempo que tendrá que esperar puede variar, según el tamaño de su base de datos.

## <a name="see-also" />Consulte también

[Inspección de páginas](across-inspect-page.md)  
[Artículos de rendimiento para desarrolladores](/dynamics365/business-central/dev-itpro/performance/performance-developer)  


[!INCLUDE[footer-include](includes/footer-banner.md)]
