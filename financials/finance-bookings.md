---
title: Facturar las reservas en Dynamics 365 | Documentos de Microsoft
description: "Obtenga información sobre cómo realizar la facturación masiva desde Microsoft Bookings en Dynamics 365 for Financials."
author: edupont04
ms.service: dynamics365-financials
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: invoicing, bookings
ms.date: 06/14/2017
ms.author: edupont
ms.translationtype: Human Translation
ms.sourcegitcommit: 81636fc2e661bd9b07c54da1cd5d0d27e30d01a2
ms.openlocfilehash: 1f1a1645ba27a3b42d67c11f7472c283ca44dbd1
ms.contentlocale: es-mx
ms.lasthandoff: 07/07/2017


---
# <a name="bulk-invoicing-for-microsoft-bookings-in-included365finincludesd365finmdmd"></a>Facturación masiva para Microsoft Bookings en [!INCLUDE[d365fin](includes/d365fin_md.md)]
Si su empresa utiliza la aplicación Bookings en Office 365, puede hacer la facturación masiva para citas. La página **Bookings sin facturar** de [!INCLUDE[d365fin](includes/d365fin_md.md)] ofrece una lista de las reservas completadas de la empresa. En esta página puede seleccionar rápidamente citas que desea facturar y para crear borradores de factura de los servicios prestados.  

## <a name="connect-to-bookings"></a>Conectarse a Bookings
Para conectarse [!INCLUDE[d365fin](includes/d365fin_md.md)] con Bookings, debe especificar su empresa de Bookings, lo que desea sincronizar con Bookings, la frecuencia con que se realizará la sincronización y las plantillas que se usarán. Puede configurar esta información en la página **Configuración de sincronización de Bookings**, que puede iniciar desde la página **Configuración de la sincronización de Exchange**, que puede encontrar mediante [Buscar](ui-search.md).  

Por ejemplo, si desea sincronizar clientes entre Bookings y [!INCLUDE[d365fin](includes/d365fin_md.md)], debe especificar la plantilla predeterminada que se usa para agregar a los clientes nuevos en [!INCLUDE[d365fin](includes/d365fin_md.md)] basándose en los clientes en su empresa de Bookings.  

## <a name="invoice-appointments"></a>Citas de factura
Cuando sea el momento enviar facturas de las reservas completadas, vaya a la página **Bookings sin facturar**. Dependiendo de la frecuencia con que se sincroniza la información, la lista es larga o corta. Puede crear facturas para todas las reservas de la lista o una reserva cada vez. Puede seleccionar una o varias entradas de la lista y facturar solo esas.  

La compatibilidad para facturar citas desde Bookings es más simple que el flujo de trabajo completo para trabajar con ofertas de ventas, pedidos de ventas y facturas de ventas. Para obtener más información, vea [Procedimiento: Facturar ventas](sales-how-invoice-sales.md). Puede elegir vender sus servicios utilizando [!INCLUDE[d365fin](includes/d365fin_md.md)] o elegir usar Bookings, en función de sus necesidades empresariales.  

## <a name="see-also"></a>Consulte también
[Finanzas](finance.md)  
[Facturación de ventas](sales-how-invoice-sales.md)  
[Configuración de ventas](sales-setup-sales.md)  
[Microsoft Bookings](https://products.office.com/en-us/business/scheduling-and-booking-app)  
