---
title: Revertir registro de salida | Documentos de Microsoft
description: "En ciertas ocasiones es necesario revertir el registro de la salida. Por ejemplo, si se ha cometido un error en la introducción de los datos y se ha registrado una cantidad de salida incorrecta en una orden de producción."
services: project-madeira
documentationcenter: 
author: SorenGP
ms.service: dynamics365-financials
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: 
ms.date: 09/06/2017
ms.author: sgroespe
ms.translationtype: HT
ms.sourcegitcommit: 2c13559bb3dc44cdb61697f5135c5b931e34d2a8
ms.openlocfilehash: 7ac453ff87d78e6be0567ba93b58c0f8938f4052
ms.contentlocale: es-mx
ms.lasthandoff: 09/22/2017

---
# <a name="how-to-reverse-output-posting"></a>Procedimiento: Revierta un registro de salida
En ciertas ocasiones es necesario revertir el registro de la salida. Por ejemplo, si se ha cometido un error en la introducción de los datos y se ha registrado una cantidad de salida incorrecta en una orden de producción.  

## <a name="to-reverse-an-output-posting"></a>Para revertir un registro de salida  
1.  Seleccione el icono ![Buscar página o informe](media/ui-search/search_small.png "icono Buscar página o informe"), escriba **Diario de salida** y, a continuación, seleccione el vínculo relacionado. Seleccione el lote.  
2. Rellene los campos según sea necesario. Para obtener más información, vea [Procedimiento: Registro de salida y tiempos de ejecución por lotes](production-how-to-post-output-quantity.md).
3.  En el campo **Liq. por nº orden**, seleccione el movimiento de contabilidad de productos asociado. De esta forma se reserva la capacidad y los movimientos de producto.  
4. Registre la reversión registrando el diario.  

Los movimientos del diario de salida se registran como un ajuste positivo.  

## <a name="see-also"></a>Consulte también  
 [Fabricación](production-manage-manufacturing.md)    
 [Configuración de fabricación](production-configure-production-processes.md)  
 [Planificación](production-planning.md)      
 [Grupos contables inventario](inventory-manage-inventory.md)  
 [Compras](purchasing-manage-purchasing.md)  
 [Trabajar con [!INCLUDE[d365fin](includes/d365fin_md.md)]](ui-work-product.md)  
