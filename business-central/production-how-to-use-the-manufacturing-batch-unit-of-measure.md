---
title: Utilizar la unidad de medida de lote de fabricación
description: Este tema ofrece una descripción general de cómo trabajar con unidades de medida de lotes de fabricación en Business Central.
author: SorenGP
ms.topic: conceptual
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: null
ms.date: 06/25/2021
ms.author: edupont
---
# <a name="work-with-manufacturing-batch-units-of-measure" />Trabajar con unidades de medida de lote de fabricación
Si un producto se almacena en una unidad de medida pero se fabrica en otra, se crea una orden de producción que utiliza una unidad de medida de la sección de fabricación para calcular la cantidad correcta de componentes durante el trabajo por lotes **Actualizar orden producción**. Un ejemplo del cálculo de una unidad de medida de la sección de fabricación es el caso en que un producto fabricado se almacena por piezas pero se produce en toneladas.  

## <a name="to-create-a-production-bom-using-a-batch-unit-of-measure" />Para crear una lista de materiales de producción con una unidad de medida de sección
1.  La unidad de medida de la sección de fabricación se configura como unidad de medida alternativa en la página **Unidades medida producto** del producto que se va a fabricar. La unidad de medida de sección no sustituye a la unidad de medida base del producto.  
2.  Cree una L.M. producción para el producto configurado con la unidad de medida de sección de fabricación. Para obtener más información, consulte [Crear L.M. de producción](production-how-to-create-production-boms.md).  
3.  En el campo **Cód. unidad medida**, seleccione la unidad de medida de sección de fabricación.  
4.  Por cada línea de la lista de materiales de producción, en el campo **Cantidad por**, especifique la cantidad de este producto de componente, necesaria para crear esta unidad de medida de sección.  
5.  Abra la **Ficha de producto** del producto relacionado.  

    En la ficha desplegable **Reposición** y, en el campo **Nº L.M. producción**, seleccione la L.M. de producción creada anteriormente.  
6.  Cree una cabecera de orden de producción utilizando el producto configurado con la unidad de medida de la sección de fabricación. Para obtener más información, consulte [Crear órdenes de producción](production-how-to-create-production-orders.md).  
7.  Elija la acción **Actualizar** y, a continuación, seleccione el botón **Aceptar**.  

En la ficha desplegable **Líneas**, elija la acción **Línea** y, a continuación, seleccione la acción **Componentes** para ver el resultado. La aplicación calcula la cantidad correcta de los componentes necesarios para satisfacer la lista de materiales de producción en función de la unidad de medida de la sección de fabricación.  

## <a name="to-calculate-a-manufacturing-batch-unit-of-measure-on-a-production-order" />Para calcular una unidad de medida de sección de fabricación de una orden de producción
1.  Cree una cabecera de orden de producción utilizando el producto configurado con la unidad de medida de la sección de fabricación.  
2.  En el campo **Nº producto** de la línea de la orden de producción, escriba el mismo número de producto que se usa en la cabecera.  
3.  En el campo **Cantidad**, escriba la misma cantidad que se usa en la cabecera.  
4.  En el campo **Cód. unidad medida**, seleccione el código de la unidad de medida de sección de fabricación.  
5.  Seleccione la acción **Actualizar**.
6.  En la ficha desplegable **Calcular**, borre el la casilla de verificación **Líneas**.  
7.  Elija el botón **Aceptar**.  
8.  En la ficha desplegable **Líneas**, elija la acción **Línea** y, a continuación, seleccione la acción **Componentes** para ver el resultado. Se calcula la cantidad correcta de los componentes necesarios para satisfacer la lista de materiales de producción en función de la unidad de medida de sección de fabricación.  

## <a name="see-also" />Consulte también
[Creación de rutas](production-how-to-create-routings.md)  
[Crear LM de producción](production-how-to-create-production-boms.md)     
[Configuración de fabricación](production-configure-production-processes.md)  
[Fabricación](production-manage-manufacturing.md)    
[Planificación](production-planning.md)   
[Inventario](inventory-manage-inventory.md)  
[Compras](purchasing-manage-purchasing.md)  
[Trabajar con [!INCLUDE[prod_short](includes/prod_short.md)]](ui-work-product.md)  


[!INCLUDE[footer-include](includes/footer-banner.md)]
