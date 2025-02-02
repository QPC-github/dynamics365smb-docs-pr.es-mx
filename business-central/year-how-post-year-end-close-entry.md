---
title: Registrar el movimiento de cierre del ejercicio
description: 'Describe cómo abrir el diario especificado en el proceso Cerrar resultados y, a continuación, revisar y registrar el movimiento de cierre de fin de año.'
author: edupont04
ms.topic: conceptual
ms.search.keywords: 'year closing, close accounting period, close fiscal year, bank account detailed trial balance'
ms.search.form: 100
ms.date: 06/25/2021
ms.author: edupont
---
# <a name="posting-the-year-end-closing-entry" />Registrar el movimiento de cierre del ejercicio

Después de usar el proceso **Asiento regularización** para generar los movimientos de cierre de fin de año, debe abrir el diario especificado en el proceso y revisar y registrar los movimientos.  

> [!TIP]
> Dependiendo de los procesos de trabajo de su organización, puede optar por cerrar o no los períodos contables y los ejercicios en [!INCLUDE [prod_short](includes/prod_short.md)]. El siguiente procedimiento asume que ha cerrado el ejercicio utilizando la opción *Periodos contables*, ha generado una entrada de cierre de año mediante el trabajo por lotes **Cerrar balance de ingresos** y ahora está listo para contabilizar el movimiento de cierre de fin de año junto con los movimientos de cuenta de desplazamiento de capital. Su organización puede optar por trabajar de manera diferente, como contabilizar la entrada de cierre de fin de año como parte del cierre del ejercicio.

## <a name="to-post-the-year-end-closing-entry" />Para registrar el movimiento de cierre del ejercicio

1. Elija el icono ![Bombilla que abre la función Dígame.](media/ui-search/search_small.png "Dígame qué desea hacer") , escriba **Diario general**, y luego elija el enlace relacionado.
2. En la página **Diario general**, en el campo **Nombre de sección**, seleccione la sección que contiene los movimientos de cierre.
3. Revise los movimientos.
4. Para registrar el diario, elija la acción **Registrar**.

> [!NOTE]  
> Si se detecta algún error, se muestra un mensaje de error. Si el registro es correcto, se eliminan los movimientos registrados del diario. Una vez registrados, los movimientos se registran en cada una de las cuentas de regularización, de forma que sus saldos pasan a ser cero y el resultado del año se transfiere al balance.

## <a name="see-also" />Consulte también

[Cerrar periodos contables](year-close-account-periods.md)  
[Cierre de libros](year-close-books.md)  
[Asiento regularización](year-close-income-statement.md)  
[Trabajar con [!INCLUDE[prod_short](includes/prod_short.md)]](ui-work-product.md)


[!INCLUDE[footer-include](includes/footer-banner.md)]
