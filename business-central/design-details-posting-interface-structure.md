---
title: "Detalles de diseño: Estructura de interfaz de registro | Documentos de Microsoft"
description: Este tema proporciona un resumen de los procedimientos globales en la estructura de la interfaz de registro.
services: project-madeira
documentationcenter: 
author: SorenGP
ms.service: dynamics365-business-central
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: posting, interface, design
ms.date: 07/01/2017
ms.author: sgroespe
ms.translationtype: HT
ms.sourcegitcommit: d7fb34e1c9428a64c71ff47be8bcff174649c00d
ms.openlocfilehash: 4d5aede731958f6f07b361cf2b4f2351bb5ad06a
ms.contentlocale: es-mx
ms.lasthandoff: 03/22/2018

---
# <a name="design-details-posting-interface-structure"></a>Detalles de diseño: estructura de interfaz de registro
En la estructura de interfaz de registro de [!INCLUDE[d365fin](includes/d365fin_md.md)] existen varios procedimientos globales que utilizan la misma estructura:  
  
* RunWithCheck y RunWithoutCheck llaman al código de procedimiento - interfaz de registro genérica para la línea de diario general.  
* CustPostApplyCustLedgEntry: registrar aplicación de cliente, llamada desde la unidad de código 226 Mov. cliente-Liquidar movimientos registrados.  
* VendPostApplyVendLedgEntry: registrar liquidación de proveedor, llamada desde la unidad de código 227 Mov. proveedor-Liquidar movimientos registrados.  
* UnapplyCustLedgEntry: registrar desliquidación de liquidación de cliente, llamada desde la unidad de código 226 Mov. cliente-Liquidar movimientos registrados.  
* UnapplyVendLedgEntry: registrar desliquidación de liquidación de proveedor, llamada desde la unidad de código 227 Mov. proveedor-Liquidar movimientos registrados.  
  
## <a name="see-also"></a>Consulte también  
[Detalles de diseño: estructura de motor de registro](design-details-posting-engine-structure.md)