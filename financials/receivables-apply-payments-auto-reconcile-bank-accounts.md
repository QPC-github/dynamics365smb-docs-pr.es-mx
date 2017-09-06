---
title: Tareas para conciliar cuentas bancarias y liquidar pagos de los movimientos relacionados | Documentos de Microsoft
description: "Describe las tareas para conciliar las cuentas de banco, cobros y pagos, registrar recibos de efectivo o gastos, y liquidar los pagos automáticamente."
services: project-madeira
documentationcenter: 
author: SorenGP
ms.service: dynamics365-financials
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: payment process, direct payment posting, reconcile payment, expenses, cash receipts
ms.date: 03/29/2017
ms.author: sgroespe
ms.translationtype: Human Translation
ms.sourcegitcommit: 81636fc2e661bd9b07c54da1cd5d0d27e30d01a2
ms.openlocfilehash: f828fce295b15db9e50034a51e1531b29b064c85
ms.contentlocale: es-mx
ms.lasthandoff: 07/07/2017


---
# <a name="apply-payments-automatically-and-reconcile-bank-accounts"></a>Liquidar pagos automáticamente y conciliar cuentas bancarias
Debe conciliar con frecuencia las cuentas bancarias, las de cobros y las de pagos liquidando pagos registrados en el banco en sus facturas sin abonar relacionadas, abonos y otros movimientos pendientes en [!INCLUDE[d365fin](includes/d365fin_long_md.md)].  

Puede realizar esta tarea en la ventana **Diario de conciliación de pagos** importando una fuente o archivo de extracto bancario para registrar rápidamente los pagos. Los pagos se liquidan en los movimientos de cliente o proveedor abiertos en función de las coincidencias entre el texto de pago y la información de movimiento. Puede revisar y cambiar las liquidaciones automáticas entes de registrar el diario. Puede elegir cerrar los movimientos de banco pendientes relacionados con los movimientos liquidados cuando registra el diario. La cuenta bancaria se concilia automáticamente cuando se liquidan todos los pagos.  

Para importar extractos bancarios como fuente de banco, primero debe configurar y habilitar el servicio de fuente de banco de Envestnet Yodlee y, a continuación, vincular sus cuentas bancarias a las cuentas bancarias en línea relacionadas. Para obtener más información, vea [Procedimiento: Configuración del servicio de fuentes de banco de Envestnet Yodlee](bank-how-setup-bank-statement-service.md)  

De forma alternativa, puede usar el servicio de conversión de datos de banco para convertir un archivo de extracto de banco, en cualquier formato, a una secuencia de datos que pueda importar en [!INCLUDE[d365fin](includes/d365fin_long_md.md)]. Para obtener más información, vea [Procedimiento: Configuración del servicio de conversión de datos bancarios](bank-how-setup-bank-data-conversion-service.md).  

En la tabla siguiente se describe una secuencia de tareas, con vínculos a temas que las describen.  

| Para | Vea |
| --- | --- |
| Liquide los pagos en los movimientos pendientes de cliente o proveedor importando un estado de cuenta bancario y concilie la cuenta bancaria cuando se liquiden todos los pagos. |[Conciliar pagos con liquidación automática](receivables-how-reconcile-payments-auto-application.md) |
| Liquide manualmente pagos viendo información detallada sobre datos coincidentes y sugerencias para movimientos pendientes candidatos en los que liquidar pagos. |[Revisar o liquidar pagos después de una liquidación automática](receivables-how-review-apply-payments-auto-application.md) |
| Resuelva los pagos que no se pueden liquidar automáticamente a sus movimientos pendientes relacionados. Por ejemplo, porque los importes son distintos o porque no existe ningún movimiento relacionado. |[Conciliar pagos que no se pueden liquidar automáticamente](receivables-how-reconcile-payments-cannot-apply-auto.md) |
| Vincule el texto sobre pagos con cuentas concretas de cliente, de proveedor o de contabilidad para que siempre se registren recepciones de cobro o gastos periódicos en dichas cuentas cuando no haya documentos a los que aplicarlos. |[Asignación de texto en pagos periódicos a cuentas para conciliación automática](receivables-how-map-text-recurring-payments-accounts-auto-reconcilliation.md) |

## <a name="see-also"></a>Consulte también
[Administrar cobros](receivables-manage-receivables.md)  
[Ventas](sales-manage-sales.md)  
[Trabajar con [!INCLUDE[d365fin](includes/d365fin_md.md)]](ui-work-product.md)
