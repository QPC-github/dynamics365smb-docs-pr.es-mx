---
title: 'Detalles de diseño: Valuación de Inventarios | Documentos de Microsoft'
description: La valuación de inventarios es la determinación del costo de un artículo de inventario.
author: SorenGP
ms.topic: conceptual
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: null
ms.date: 06/08/2021
ms.author: edupont
---
# <a name="design-details-inventory-valuation" />Detalles de diseño: Valuación de Inventarios
La valuación de inventarios es la determinación del costo que se asigna a un producto de inventario, tal como expresa la ecuación siguiente.  

Inventario final = inventario inicial + compras netas – costo de bienes vendidos  

El cálculo de valuación de inventarios usa el campo **Importe costo (real)** de los movimientos de valuación del producto. Los movimientos se clasifican según el tipo de movimiento correspondiente a los componentes de costo, el costo directo, el costo indirecto, la desviación, la revalorización y el redondeo. Para obtener más información, consulte [Detalles de diseño: Componentes de costo](design-details-cost-components.md).  

Las entradas se aplican una respecto a otra, por liquidación fija o según el supuesto de flujo de costo general definido por el método de costo. Se puede aplicar un movimiento de salida de inventario a varios movimientos de entrada con distintas fechas de registro y, posiblemente, distintos costos. Para obtener más información, consulte [Detalles de diseño: Liquidación de productos](design-details-item-application.md). Por lo tanto, el cálculo del valor de inventario para una fecha determinada se basa en la suma de movimientos de valoración positivos y negativos.  

## <a name="inventory-valuation-report" />Informe de valuación de inventarios
Para calcular el valor de inventario en el informe **Valuación de Inventarios**, se comienza con el cálculo del valor del inventario del producto en una fecha inicial determinada. Después suma el valor de las entradas de inventario y resta el valor de las salidas de inventario hasta una fecha final determinada. El resultado final es el valor de inventario en la fecha final. El informe calcula estos valores mediante la suma de los valores del campo **Importe costo (real)** en los movimientos de valoración, usando las fechas de registro como filtros.  

El informe impreso siempre muestra los importes reales, es decir, el costo de los movimientos que se han registrado como facturados. Si activa el campo Incluir costo esperado de la ficha desplegable Opciones, el informe impreso también incluirá el costo esperado de los movimientos que se hayan registrado como recibidos o enviados.  

> [!IMPORTANT]  
>  Los valores del informe **Valuación de Inventarios** se concilian con la cuenta de inventario en la contabilidad, lo que significa que los movimientos de valuación en cuestión se han registrado en la contabilidad.  

> [!IMPORTANT]  
>  Las cantidades en las columnas **Valor** del informe se basan en la fecha de registro de las transacciones para un producto.  

## <a name="inventory-valuation---wip-report" />Valuación de inventario - informe WIP
Una empresa de fabricación debe determinar el valor de tres tipos de inventario:  

* Inventario de materias primas  
* Inventario WIP  
* Inventario de productos terminados  

El valor del inventario WIP del trabajo en curso se determina mediante la ecuación siguiente:  

* Inventario WIP final = Inventario WIP inicial + costos de fabricación – costo de productos fabricados  

En cuanto al inventario comprado, las entradas de valor proporcionan la base de valuación del inventario. El cálculo se realiza con los valores del campo **Importe costo (real)** de los movimientos de valoración de producto y de capacidad asociados con una orden de producción.  

El propósito de la valuación de inventarios del trabajo en curso es determinar el valor de los productos cuya fabricación aún no se ha completado en una fecha determinada. Por lo tanto, el valor de inventario del trabajo en curso se basa en los movimientos de valoración relacionados con los movimientos de consumo y de capacidad. Los movimientos de consumo se deben facturar totalmente en la fecha de la evaluación. Por tanto, el informe **Valuación de Inventarios - WIP** muestra los costos que representan el valor de inventario del trabajo en curso en dos categorías: consumo y capacidad.  

## <a name="see-also" />Consulte también
[Detalles de diseño: Conciliación con contabilidad](design-details-reconciliation-with-the-general-ledger.md)   
[Detalles de diseño: Revalorización](design-details-revaluation.md)   
[Detalles de diseño: Registro de órdenes de producción](design-details-production-order-posting.md)
[Gestión de costos de inventario](finance-manage-inventory-costs.md)  
[Finanzas](finance.md)  
[Trabajar con [!INCLUDE[prod_short](includes/prod_short.md)]](ui-work-product.md)


[!INCLUDE[footer-include](includes/footer-banner.md)]
