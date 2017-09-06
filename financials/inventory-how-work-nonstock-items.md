---
title: Crear y administrar los productos no inventariables | Documentos de Microsoft
description: "Describe cómo comercializar los productos no inventariables o los productos que no se mantienen en el inventario."
documentationcenter: 
author: SorenGP
ms.service: dynamics365-financials
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: non-inventoriable
ms.date: 06/02/2017
ms.author: sgroespe
ms.translationtype: Human Translation
ms.sourcegitcommit: 81636fc2e661bd9b07c54da1cd5d0d27e30d01a2
ms.openlocfilehash: b51c163dc8eafc462a1fd489d498d44eaeafd24a
ms.contentlocale: es-mx
ms.lasthandoff: 07/07/2017


---
# Procedimiento: Trabajar con productos no inventariables
Puede ofrecer varios productos a sus clientes para su comodidad que no desea mantener en el inventario hasta que empiece a venderlos. Cuando desee empezar a mantener esos productos en el inventario, puede convertirlos en fichas de productos normales de dos formas.

* Desde una ficha de producto no inventariable, cree una nueva ficha de producto basada en una plantilla.
* Desde una línea de pedido de ventas del tipo **Producto** con un campo *N.º* vacío, seleccione un producto sin stock. Se crea automáticamente una ficha de producto para el producto no inventariable.

> [!NOTE]  
>   No puede seleccionar un producto sin stock de la ventana **Facturas venta**. Puede seleccionarlo desde la ventana **Cotización de venta**, pero el producto no inventariable no se convertirá en uno normal cuando utilice la función **Realizar orden**.

Un producto no inventariable normalmente tiene el número del proveedor que lo suministra. Para activar la conversión de una ficha de producto no inventariable a una ficha de producto normal, debe configurar cómo se convertirá la numeración del producto del vendedor a la suya.   

## Para crear productos no inventariables
Las fichas de productos no inventariables disponen de mucha menos información que las de productos normales puesto que solo se las utiliza en cotizaciones de ventas y de otras maneras. Por esa razón, se convertirán en fichas de producto normal antes de que pueda registrarles las transacciones de venta.

1. Seleccione el icono ![Buscar página o informe](media/ui-search/search_small.png "icono Buscar página o informe"), escriba **Productos sin stock** y, a continuación, seleccione el vínculo relacionado.
2. Seleccione la acción **Nuevo**.
3. Rellene los campos según sea necesario. [!INCLUDE[tooltip-inline-tip](includes/tooltip-inline-tip_md.md)]

## Para configurar cómo se convierten los números de productos no inventariables a la numeración que usted usa
Para activar la conversión de una ficha de producto no inventariable en una ficha de producto normal, primero debe especificar cómo se convertirá la numeración del producto del proveedor a su formato de número de producto.

1. Seleccione el icono ![Buscar página o informe](media/ui-search/search_small.png "icono Buscar página o informe"), escriba **Config. productos sin stock** y, a continuación, seleccione el vínculo relacionado.
2. Rellene los campos según sea necesario.

## Para convertir un producto no inventariable en un producto normal
1. Seleccione el icono ![Buscar página o informe](media/ui-search/search_small.png "icono Buscar página o informe"), escriba **Productos sin stock** y, a continuación, seleccione el vínculo relacionado.
2. Abra la ficha de un producto no inventariable que desee convertir a uno normal.
3. En la ventana **Ficha prod. no inventariable**, seleccione la acción **Crear producto**.

Se ha creado una nueva ficha de producto con la información del producto no inventariable rellenada previamente y la plantilla de producto correspondiente. Si es necesario, podrá rellenar o editar los campos en la nueva ficha de producto. Para obtener más información, vea [Registrar nuevos productos](inventory-how-register-new-items.md).

## Para vender un producto no inventariable y convertirlo en un producto normal
1. Seleccione el icono ![Buscar página o informe](media/ui-search/search_small.png "icono Buscar página o informe"), escriba **Pedidos de venta** y, a continuación, seleccione el vínculo relacionado.
2. Seleccione la acción **Nuevo**. Rellene los campos de la ficha desplegable **General** para cada pedido. Para obtener más información, vea [Procedimiento: Vender productos](sales-how-sell-products.md).
3. En una nueva línea de venta, en el campo **Tipo**, seleccione **Producto**, pero deje **N.º** campo vacío.
4. Elija la acción **Línea** y, a continuación, elija la acción **Seleccionar artículos sin stock**.

    El producto no inventariable se ha convertido en un producto normal. Se ha creado una nueva ficha de producto con la información del producto no inventariable rellenada previamente y la plantilla de producto correspondiente.
5. En la ventana **Productos no inventariables**, seleccione el producto no inventariable que desea vender y, a continuación, haga clic en **Aceptar**.
6. Cuando la orden de venta esté completa, seleccione la acción **Registrar**.

Si es necesario, podrá rellenar o editar los campos en la nueva ficha de producto. Para obtener más información, vea [Registrar nuevos productos](inventory-how-register-new-items.md).

> [!NOTE]  
>   Un informe de referencia cruzada de un producto se crea automáticamente por el proveedor del producto entre el número del producto del proveedor y su nuevo número de producto.

## Consulte también
[Registro de productos nuevos](inventory-how-register-new-items.md)  
[Inventario](inventory-manage-inventory.md)  
[Trabajar con [!INCLUDE[d365fin](includes/d365fin_md.md)]](ui-work-product.md)
