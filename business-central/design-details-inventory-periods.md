---
title: "Detalles de diseño: Periodos de inventario | Documentos de Microsoft"
description: "Las transacciones o los ajustes de costo a los que se aplica fecha retroactiva a menudo repercuten en los saldos y los métodos de costo para periodos contables que pueden considerarse cerrados. Esto puede tener un efecto negativo en los informes exactos, especialmente en las corporaciones globales. La característica Periodos inventario se puede usar para evitar dichos problemas mediante la apertura o el cierre de periodos de inventario para limitar el registro en un periodo de tiempo configurado."
services: project-madeira
documentationcenter: 
author: SorenGP
ms.service: dynamics365-business-central
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: 
ms.date: 07/01/2017
ms.author: sgroespe
ms.translationtype: HT
ms.sourcegitcommit: d7fb34e1c9428a64c71ff47be8bcff174649c00d
ms.openlocfilehash: 99aa0cacdbe6933c5ba16443297d1838b8bfd3ac
ms.contentlocale: es-mx
ms.lasthandoff: 03/22/2018

---
# <a name="design-details-inventory-periods"></a>Detalles de diseño: Periodos de inventario
Las transacciones o los ajustes de costo a los que se aplica fecha retroactiva a menudo repercuten en los saldos y los métodos de costo para periodos contables que pueden considerarse cerrados. Esto puede tener un efecto negativo en los informes exactos, especialmente en las corporaciones globales. La característica Periodos inventario se puede usar para evitar dichos problemas mediante la apertura o el cierre de periodos de inventario para limitar el registro en un periodo de tiempo configurado.  

 Un periodo inventario es un periodo de tiempo, definido por una fecha de fin, en el que se registran transacciones de inventario. Cuando cierra un periodo de inventario, no se puede registrar ningún cambio de valor en el periodo cerrado. Esto incluye nuevos registros de valoración, registros previstos o facturados, cambios en los valores existentes y ajustes de costo. No obstante, podrá aplicarse a un movimiento de producto abierto dentro del periodo cerrado. Para obtener más información, consulte [Detalles de diseño: Liquidación de productos](design-details-item-application.md).  

 Para garantizar que todos los movimientos de transacción de un periodo cerrado son finales, se deben cumplir las condiciones siguientes para que se pueda cerrar un periodo de inventario:  

-   Todos los movimientos de producto de en el periodo deben cerrarse (no hay inventario negativo).  
-   Todos los costes de producto en el periodo deben ser ajustados.  
-   Debe ajustarse el costo de todas las órdenes de producción lanzadas y terminadas en el periodo.  

 Cuando cierra un periodo de inventario, se crea un movimiento de periodo de inventario mediante el número del último registro de producto que está dentro de dicho periodo. Además, la hora, la fecha y el código del usuario del usuario que cierra el periodo se registran en el movimiento del periodo de inventario. Usando esta información con el último registro de producto para el periodo anterior, puede ver qué transacciones de inventario se registraron en el periodo del inventario. También se pueden volver a abrir periodos de inventario si necesita aplicar un registro en un periodo cerrado. Cuando se vuelve a abrir un periodo de inventario, se crea un movimiento de periodo de inventario.  

## <a name="see-also"></a>Consulte también  
 [Detalles de diseño: Costo de inventario](design-details-inventory-costing.md) [Administración de costos de inventario](finance-manage-inventory-costs.md) [Finanzas](finance.md)  
 [Trabajar con Financials](ui-work-product.md)
