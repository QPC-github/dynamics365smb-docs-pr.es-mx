---
title: Información general de los movimientos del grupo dimensiones
description: Este artículo le ofrece una descripción general de cómo se almacenan los movimientos de grupo de dimensiones como movimientos de grupo de dimensiones y cómo se registran.
author: SorenGP
ms.topic: overview
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: dimension
ms.date: 06/14/2021
ms.author: edupont
---
# <a name="dimension-set-entries-overview" />Información general de los movimientos del grupo dimensiones
Este tema describe cómo se almacenan y se registran los movimientos de grupo de dimensiones en [!INCLUDE[prod_short](includes/prod_short.md)].  

## <a name="dimension-sets" />Conjuntos de dimensiones
Un grupo de dimensiones es una combinación única de valores de dimensión. Se almacena como movimientos de grupo de dimensiones en la base de datos. Cada movimiento de grupo de dimensiones representa un valor de dimensión único. El grupo de dimensiones se identifica por medio de un id común del grupo de dimensiones que está asignado a cada movimiento de grupo de dimensiones que pertenece al grupo de dimensiones.  

El siguiente ejemplo muestra un grupo de dimensiones que tiene tres movimientos de grupo de dimensiones. El grupo de dimensiones se identifica por medio de un número de grupo de dimensiones, que es 108.  

|Id. grupo dimensiones|Cód. dimensión|Cód. valor dimensión|Nombre valor dimensión|  
|----------------------|--------------------|--------------------------|--------------------------|  
|108|ÁREA|nº 70|Norte América|  
|108|GRUPONEGOCIO|INICIO|Inicio|  
|108|DPTO|CCIAL|Ccial|  

## <a name="dimension-set-entries" />Movimientos de grupo de dimensiones
Los grupos de dimensiones se almacenan en la tabla **Mov. grupo de dimensiones** como movimientos de grupo de dimensiones con el mismo Id. del grupo de dimensiones.  

![Flujo de movimientos del grupo dimensiones.](media/dimensionentrynav7.png "Flujo de movimientos del grupo dimensiones")  

Cuando crea una nueva línea de diario, cabecera de documentos o línea de documentos, puede especificar una combinación de valores de dimensión. En lugar de explícitamente guardar cada valor de dimensión en la base de datos, un Id. de grupo de dimensiones se asigna a la línea de diario, cabecera de documentos o línea de documentos para especificar el grupo de dimensiones.  

Cuando modifica y cierra la página **Editar movimientos de grupo de dimensiones**, se realiza una comprobación para ver si la combinación de valores de dimensión existe como grupo de dimensiones en la tabla. Si la combinación tiene lugar en la tabla, el Id. correspondiente del grupo de dimensiones se asigna a la línea de diario, cabecera de documentos o línea de documentos. Si no, un nuevo grupo de dimensiones se agrega a la tabla, y el nuevo Id. del grupo de dimensiones se asigna a la línea de diario, cabecera de documento o línea de documento.

## <a name="codeunit-408-dimension-management" />Gestión de dimensiones de codeunit 408
Codeunit 408, gestión de dimensiones, es una biblioteca de funciones que controla tareas comunes relacionadas con las dimensiones, como copiar desde una tabla a otra o desde un documento a otro.

## <a name="performance-improvement" />Mejora del rendimiento
Al almacenar grupos de dimensiones una vez en la base de datos, se preserva el espacio de la base de datos y se mejora el rendimiento total.  

## <a name="see-also" />Consulte también
[Detalles de diseño: Búsqueda de combinaciones de dimensiones](design-details-searching-for-dimension-combinations.md)   
[Detalles de diseño: Estructura de tablas](design-details-table-structure.md)   
[Detalles de diseño: Movimientos de grupo de dimensiones](/dynamics365/business-central/design-details-dimension-set-entries-overview)   


[!INCLUDE[footer-include](includes/footer-banner.md)]
