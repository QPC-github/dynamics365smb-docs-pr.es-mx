---
title: "Definición y asignación de costos | Documentos de Microsoft"
description: Las asignaciones de costos mueven los costos e ingresos entre tipos de costo, centros de costo y objetos de costo. Puede definir tantas asignaciones como necesite.
services: project-madeira
documentationcenter: 
author: SorenGP
ms.service: dynamics365-financials
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: 
ms.date: 07/01/2017
ms.author: sgroespe
ms.translationtype: HT
ms.sourcegitcommit: 2c13559bb3dc44cdb61697f5135c5b931e34d2a8
ms.openlocfilehash: 050b0bd997629ca189cfbe035e361de7a252d079
ms.contentlocale: es-mx
ms.lasthandoff: 09/22/2017

---
# <a name="defining-and-allocating-costs"></a>Definición y asignación de costos
Las asignaciones de costos mueven los costos e ingresos entre tipos de costo, centros de costo y objetos de costo. Puede definir tantas asignaciones como necesite. Cada asignación consta de:  

-   Un origen asignación.  
-   Uno o varios destinos de asignación.  

El origen de asignación establece qué costos se deben asignar, y los destinos de asignación determinan dónde se deben asignar los costos. Por ejemplo, un origen de asignación puede ser los costos del tipo de costo Electricidad y Calefacción. Asigna todos los costos de electricidad y calefacción a tres centros de costo: Taller, Producción y Ventas. Estos centros de costo son los destinos de asignación.  

Para cada origen de asignación, puede definir un nivel de asignación, un periodo de validez y una variante como identificador de grupo. Puede utilizar un trabajo por lotes para definir filtros para seleccionar definiciones de asignación y luego ejecutar asignaciones de costo automáticamente.  

Para cada destino de asignación, define una base de asignaciones. La base de la asignaciones puede ser estática o dinámica.  

-   Las bases de asignaciones estáticas se basan en un valor definido, por ejemplo los metros cuadrados o una proporción de asignación establecida, como 5:2:4.  
-   Las bases de asignaciones dinámicas se basan en valores cambiables, como el número de empleados de un centro de costo o los ingresos de ventas de un objeto de costo en un determinado periodo de tiempo.  

En la tabla siguiente se describe una secuencia de tareas, con vínculos a temas que las describen.

|Para|Vea|  
|--------|---------|  
|Configurar el origen de asignación y sus destinos.|[Procedimiento: configurar origen y destinos de asignación](finance-how-to-set-up-allocation-source-and-targets.md)|  
|Configuración de varios filtros para las bases de la asignaciones dinámicas.|[Configuración de filtros para las bases de la asignación dinámica](finance-setting-filters-for-dynamic-allocation-bases.md)|  
|Consulte un ejemplo de cómo definir una asignación estática.|[Ejemplo: definición de asignaciones estáticas basadas en la proporción de asignación](finance-scenario-example-defining-static-allocations-based-on-allocation-ratio.md)|  
|Consulte un ejemplo de cómo definir una asignación dinámica.|[Ejemplo: definición de asignaciones dinámicas basándose en productos vendidos](finance-scenario-example-defining-dynamic-allocations-based-on-items-sold.md)|  

## <a name="see-also"></a>Consulte también  
 [Configuración de contabilidad de costos](finance-set-up-cost-accounting.md)   
 [Transferencia y registro de movimientos de coste](finance-transfer-and-post-cost-entries.md)   
 [Contabilidad para costos](finance-manage-cost-accounting.md)   
 [Terminología en contabilidad de costes](finance-terminology-in-cost-accounting.md)   
 [Acerca de la contabilidad de costos](finance-about-cost-accounting.md)
