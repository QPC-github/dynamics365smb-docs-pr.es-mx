---
title: "Actividades de almacén | de Microsoft"
description: "Una vez recibidos los bienes, antes de que se envíen, se llevan a cabo una serie de actividades internas de almacén para garantizar un flujo eficaz por todo el almacén y para organizar y mantener las existencias de la empresa."
services: project-madeira
documentationcenter: 
author: SorenGP
ms.service: dynamics365-financials
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: 
ms.date: 08/15/2017
ms.author: sgroespe
ms.translationtype: HT
ms.sourcegitcommit: 2c13559bb3dc44cdb61697f5135c5b931e34d2a8
ms.openlocfilehash: c1ea1c4a5ea4b917243d60981ec35050895f82a7
ms.contentlocale: es-mx
ms.lasthandoff: 09/22/2017

---
# <a name="warehouse-management"></a>Gestión almacén
Una vez recibidos los bienes, antes de que se envíen, se llevan a cabo una serie de actividades internas de almacén para garantizar un flujo eficaz por todo el almacén y para organizar y mantener las existencias de la empresa.

Entre las actividades de almacén habituales se encuentran la ubicación de productos, los movimientos de productos dentro de un mismo almacén o entre distintos almacenes y el picking de productos para las fases de ensamblado, producción o envío. Los productos de ensamblaje para la venta o el inventario también se pueden considerar actividades del almacén, pero éstos se cubren en otra parte. Para obtener más información, consulte [Gestión de ensamblado](assembly-assemble-items.md).  

En almacenes de grandes dimensiones, las distintas tareas de manipulación pueden distribuirse entre distintos departamentos y la integración puede gestionarse mediante un flujo de trabajo dirigido. En instalaciones más sencillas, el flujo no está tan formalizado y las actividades de almacén se llevan a cabo con las llamadas ubicaciones y picking de inventario. Para obtener más información sobre configuraciones de almacén básicas y avanzadas, consulte [Detalles de diseño: Vista general de almacén](design-details-warehouse-overview.md).

Antes de poder realizar actividades de almacén, debe configurar el sistema para la complejidad relevante del procesamiento del almacén. Para obtener más información, consulte [Configuración de la administración de almacén](warehouse-setup-warehouse.md).

 En la tabla siguiente se describe una secuencia de tareas, con vínculos a temas que las describen.   

|**Para**|**Vea**|  
|------------|-------------|  
|Registre la recepción de productos en las ubicaciones del almacén, ya sea solo con una orden de compra, en configuraciones de ubicación sencillas o con un recibo de almacén, en caso de procesamiento semi o totalmente automatizado del almacén en la ubicación.|[Cómo recibir productos](warehouse-how-receive-items.md)|
|Evite los procesos de ubicación y picking para acelerar un elemento directamente desde la recepción o producción hasta el envío.|[Procedimiento: haga tránsito directo de artículos](warehouse-how-to-cross-dock-items.md)|    
|Ubicar los productos recibidos de compras, devoluciones de ventas, transferencias o salidas de producción de acuerdo con lo configurado en el proceso del almacén.|[Configurando los artículos componentes](warehouse-put-away-items.md)|
|Mover productos de una ubicación a otra en el almacén.|[Mover artículos](warehouse-move-items.md)|
|Realizar el picking de los productos para su envío, transferencia o consumo en producción o ensamblado, de acuerdo con lo configurado en el proceso del almacén.|[Realización de picking de artículos](warehouse-pick-items.md)|
|Registre el envío de productos desde las ubicaciones del almacén, ya sea solo con un pedido de ventas, en configuraciones de ubicación sencillas o con un envío de almacén, en caso de proceso semi o totalmente automatizado del almacén en la ubicación.|[Procedimiento: enviar productos](warehouse-how-ship-items.md)|  

## <a name="see-also"></a>Consulte también  
 [Grupos contables inventario](inventory-manage-inventory.md)  
 [Configuración de la gestión del almacén](warehouse-setup-warehouse.md)     
 [Gestión de ensamblaje](assembly-assemble-items.md)    
[Detalles de diseño: Gestión de almacén](design-details-warehouse-management.md)  
 [Trabajar con [!INCLUDE[d365fin](includes/d365fin_md.md)]](ui-work-product.md)  
