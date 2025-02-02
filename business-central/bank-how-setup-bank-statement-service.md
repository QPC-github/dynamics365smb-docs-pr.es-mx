---
title: Configurar fuentes de bancos de Yodlee
description: Puede convertir la información sobre pagos a cualquier formato de datos que requiera el banco y habilitar la exportación o importación de los archivos de banco.
author: SorenGP
ms.topic: conceptual
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: 'Yodlee, feed, stream, payment process'
ms.search.form: '1280, 1290'
ms.date: 04/01/2021
ms.author: edupont
---
# <a name="set-up-the-envestnet-yodlee-bank-feeds-service" />Configurar el servicio Envestnet Yodlee Bank Feeds

Puede importar estados de cuenta electrónicos de su banco para rellenar rápidamente la página **Diario de conciliación de pagos** para que pueda liquidar pagos y conciliar la cuenta bancaria. Para obtener más información, vea [Liquidación de pagos automáticamente y conciliación de cuentas bancarias](receivables-apply-payments-auto-reconcile-bank-accounts.md).

> [!IMPORTANT]
> Debido a la directiva sobre servicios de pago en Europa (PSD2), después del 14 de septiembre de 2019 ya no podrá importar automáticamente estados de cuenta bancarios del Reino Unido a [!INCLUDE[prod_short](includes/prod_short.md)]. Estamos analizando la posibilidad de ofrecer esta función nuevamente en el futuro.

> [!NOTE]
> El servicio Envestnet Yodlee Bank Feeds solo se admite en la versión en línea de Business Central. Para usar esta funcionalidad localmente, debe obtener una cuenta de marca compartida de Envestnet y agregar código para integrarse con la API de Yodlee.
>
> El servicio Envestnet Yodlee Bank Feeds solo se admite en Estados Unidos y Canadá.
> Solo se admiten los bancos que residan en estos países, aunque los bancos de otros países puedan aparecer en la ventana de selección de banco de Envestnet Yodlee Bank Feeds en [!INCLUDE[prod_short](includes/prod_short.md)].

> [!IMPORTANT]
> Para obtener asistencia técnica con la funcionalidad Envestnet Yodlee, póngase en contacto con el soporte técnico de Microsoft. No se ponga en contacto con Envestnet Yodlee. Para obtener más información, consulte [Configuración de soporte técnico para Dynamics 365 Business Central](/dynamics365/business-central/dev-itpro/technical-support).

El servicio Envestnet Yodlee Bank Feeds está instalado como una extensión de [!INCLUDE[prod_short](includes/prod_short.md)] en línea y está listo para ser activado en los países admitidos. Para obtener más información, consulte [Personalizar [!INCLUDE[prod_short](includes/prod_short.md)] mediante extensiones](ui-extensions.md).

Después de habilitar el servicio de fuentes de banco, debe vincular una cuenta bancaria a la cuenta bancaria de la que proviene la fuente. Vincula las cuentas a cuentas en línea en los siguientes ejemplos:

* No existe una cuenta en [!INCLUDE[prod_short](includes/prod_short.md)] para su cuenta bancaria en línea. Por tanto, cree la cuenta vinculando de la cuenta bancaria en línea.
* Existe una cuenta en [!INCLUDE[prod_short](includes/prod_short.md)] que desea vincular a una cuenta bancaria en línea.
* Una cuenta vinculada debe ser desvinculada porque desea dejar de usar el servicio de fuente de banco de la cuenta.
* Las cuentas en línea se han modificado y desea actualizar la información en las cuentas en [!INCLUDE[prod_short](includes/prod_short.md)].

Cuando se ha habilitado el servicio de fuente de banco, puede definir una cuenta bancaria que importe automáticamente nuevos estados de cuenta en la página **Diario de conciliación de pagos** cada dos horas. Las transacciones para los pagos que ya se hayan registrado como liquidados o conciliados en la página **Diario de conciliación de pagos** no se importarán. Para obtener más información, vea la sección “Para habilitar la importación automática de los estados de cuenta bancarios”.

> [!NOTE]  
> Si usa la guía configuración asistida de la Configuración de la empresa, algunos de los pasos en los procedimientos siguientes se producen automáticamente cuando accede a la configuración de la cuenta bancaria de la empresa. Para obtener más información, vea [Preparación para hacer negocios](ui-get-ready-business.md).

## <a name="to-enable-the-bank-feed-service" />Para activar el servicio de fuente de banco
1. Elija el icono ![Bombilla que abre la función Dígame.](media/ui-search/search_small.png "Dígame qué desea hacer") , escriba **Cuentas bancarias** y luego elija el enlace relacionado.
2. Abra la cuenta bancaria que usará para el servicio de fuente de banco.
3. En la página **Cuenta bancaria**, en el campo **Formato de importación de estados de cuenta bancarios**, seleccione YODLEEBANKFEED.  

El servicio de fuente de banco se activará cuando vincule una cuenta a la cuenta bancaria en línea relacionada. Vea el procedimiento siguiente.  

> [!NOTE]
> Si utiliza la guía de configuración asistida de **Configuración de la empresa**, habilite el servicio seleccionando la casilla de verificación **Usar un servicio de fuente de banco**. Para obtener más información, consulte [Crear nuevas empresas en Business Central](about-new-company.md).

## <a name="to-create-a-new-linked-bank-account" />Para crear una nueva cuenta bancaria vinculada
1. Elija el icono ![Bombilla que abre la función Dígame.](media/ui-search/search_small.png "Dígame qué desea hacer") , escriba **Cuentas bancarias** y luego elija el enlace relacionado.
2. Seleccione la cuenta bancaria correspondiente y, a continuación, seleccione **Crear una nueva cuenta bancaria vinculada**. La página **Vinculación de cuenta bancaria** se abre después de unos segundos.

    > [!NOTE]  
    > Esta página muestra la página web del servicio Envestnet Yodlee Bank Feeds. La terminología y las funciones de la página pueden no coincidir con las instrucciones que ofrece este tema.  
3. En la página **Vinculación de banco en línea**, en el panel **Vínculo de cuenta** use la función Buscar para buscar el banco en el que tiene una o varias cuentas bancarias en línea.
4. Seleccione el nombre del banco. Se abre el panel **Iniciar sesión**.
5. Introduzca el nombre de usuario y la contraseña que usa para conectarse al banco en línea y, a continuación, seleccione el botón **Siguiente**.  
6. El servicio de fuente de banco se prepara para vincular la primera cuenta bancaria en línea en el banco especificado a una nueva cuenta en [!INCLUDE[prod_short](includes/prod_short.md)].

    > [!NOTE]  
    > Si ha configurado más de una cuenta en línea en el banco deberá crear las cuentas adicionales en [!INCLUDE[prod_short](includes/prod_short.md)] para ellas. Consulte los pasos 8 a 10.  

    Después de que se haya completado el proceso, el nombre del banco aparecerá en el panel **Mis cuentas** en la pestaña **Vinculado**. El valor entre corchetes indica la cantidad de cuentas bancarias en línea que están vinculadas.  
7. Elija el botón **Aceptar**.

    Si solo vincula una cuenta bancaria en línea, se abre la página **Ficha banco** y se muestra el nombre de la cuenta bancaria en línea. En este caso, la vinculación de la cuenta bancaria se ha completado. Lo único que tiene que hacer es configurar la cuenta bancaria. Para obtener más información, consulte [Configurar cuentas bancarias](bank-how-setup-bank-accounts.md).

    Si va a vincular más de una cuenta bancaria en línea, la página **Vinculación de banco** abre una ventana y enumera las cuentas bancarias en línea adicionales que todavía no se han vinculado en [!INCLUDE[prod_short](includes/prod_short.md)]. En ese caso, siga el paso siguiente.  
8. En la página **Vinculación de banco**, seleccione la línea para una cuenta bancaria en línea y, a continuación, seleccione la acción **Vincular a nuevo banco**.  

    La página **Ficha banco** se abre para crear una nueva y muestra el nombre de la cuenta bancaria en línea.

    Si ya existe una cuenta bancaria en [!INCLUDE[prod_short](includes/prod_short.md)] al que desea vincular la cuenta bancaria en línea adicional, siga el siguiente paso.  
9. En la página **Vinculación de banco**, seleccione la línea para una cuenta bancaria en línea y, a continuación, seleccione la acción **Vincular a banco existente**.
10. En la página **Lista de bancos**, seleccione la cuenta bancaria que desee vincular y, a continuación, haga clic en **Aceptar**.

## <a name="to-link-a-bank-account-to-an-online-bank-account" />Para vincular una cuenta bancaria a una cuenta bancaria en línea.
1. Elija el icono ![Bombilla que abre la función Dígame.](media/ui-search/search_small.png "Dígame qué desea hacer") , escriba **Cuentas bancarias** y luego elija el enlace relacionado.
2. Seleccione la línea para una cuenta bancaria que no está vinculada a una cuenta en línea y, a continuación, seleccione la acción **Vincular a banco en línea**. La página **Vinculación de banco en línea** se abre rellenada previamente con el nombre del banco en el panel **Vincular cuenta**.
3. Seleccione el nombre del banco. Se abre el panel **Iniciar sesión**.
4. Introduzca el nombre de usuario y la contraseña que usa para conectarse al banco en línea y, a continuación, seleccione el botón **Siguiente**.  

    El servicio de fuentes de banco se prepara para vincular su cuenta bancaria en [!INCLUDE[prod_short](includes/prod_short.md)] a la cuenta bancaria en línea relacionada.  

    Cuando el proceso ha finalizado correctamente, el nombre del banco aparecerá en el panel **Mis cuentas** en la pestaña **Vinculado**. Si el banco tiene más de una cuenta bancaria, solo se vincula la cuenta bancaria seleccionada en el paso 2.  
5. Elija el botón **Aceptar**.

En la página **Lista de bancos**, se activa la casilla **Vinculado**.

## <a name="to-edit-the-credentials-for-an-online-bank-account" />Para editar las credenciales de una cuenta bancaria en línea
1. Elija el icono ![Bombilla que abre la función Dígame](media/ui-search/search_small.png "Dígame qué desea hacer"), escriba **Bancos** y luego elija el enlace relacionado.  
2. Elija la línea para una cuenta bancaria que está vinculada a una cuenta en línea y, a continuación, seleccione la acción **Editar información de cuenta de banco en línea**.
3. Actualice las credenciales.

## <a name="to-unlink-a-bank-account" />Para desvincular una cuenta bancaria
1. Elija el icono ![Bombilla que abre la función Dígame.](media/ui-search/search_small.png "Dígame qué desea hacer") , escriba **Cuentas bancarias** y luego elija el enlace relacionado.  
2. Seleccione la línea para una cuenta bancaria vinculada que desee desvincular de su cuenta en línea relacionada y, a continuación, seleccione la acción **Desvincular un banco en línea**.

> [!NOTE]  
> Si selecciona **Sí** en el cuadro de diálogo de confirmación, el vínculo a la cuenta bancaria en línea se elimina y se eliminan los detalles de inicio de sesión. Para vincular nuevamente la cuenta bancaria a una cuenta bancaria en línea, debe volver a iniciar sesión en el banco. Para obtener más información, vea la sección "Para vincular una cuenta bancaria a una cuenta bancaria en línea".

## <a name="to-update-bank-account-linking" />Para actualizar la vinculación de la cuenta bancaria
1. Elija el icono ![Bombilla que abre la función Dígame.](media/ui-search/search_small.png "Dígame qué desea hacer") , escriba **Cuentas bancarias** y luego elija el enlace relacionado.
2. Seleccione la cuenta bancaria correspondiente y, a continuación, seleccione la acción **Actualizar vinculación de banco**.

Si surgen problemas para alguna de las cuentas bancarias vinculadas en la página **Lista de bancos**, se abre la página **Vinculación de banco** y se especifican qué cuentas bancarias tienen problemas. Los problemas se solucionan mejor desvinculando la cuenta y reconstruyendo el vínculo. Para obtener más información, vea la sección "Para vincular una cuenta bancaria a una cuenta bancaria en línea".

## <a name="to-enable-automatic-import-of-bank-statements" />Para activar la importación automática de los extractos de cuenta
1. Elija el icono ![Bombilla que abre la función Dígame.](media/ui-search/search_small.png "Dígame qué desea hacer") , escriba **Cuentas bancarias** y luego elija el enlace relacionado.
2. Seleccione la línea para una cuenta bancaria vinculada y, a continuación, seleccione la acción **Configuración de la importación automática de estados de cuenta bancarios**.
3. En la página **Configuración de la importación automática de estados de cuenta bancarios**, en el campo **N.º de días incluidos**, especifique hasta qué fecha en el pasado desea obtener nuevas transacciones bancarias.

    > [!NOTE]  
    > Se recomienda establecer este valor a 7 días o más.  
4. Seleccione la casilla de verificación **Habilitado**.  

Cada hora, la página **Diario de conciliación de pagos** mostrará cualquier nuevo pago que se realice en la cuenta bancaria en línea.

> [!NOTE]  
> Las transacciones para los pagos que ya se hayan registrado como liquidados o conciliados en la página **Diario de conciliación de pagos** no se importarán.

## <a name="see-also" />Consulte también
[Configurar banca](bank-setup-banking.md)  
[Conciliar bancos](bank-manage-bank-accounts.md)  
[Liquidación de pagos automáticamente y conciliación de cuentas bancarias](receivables-apply-payments-auto-reconcile-bank-accounts.md)  
[Personalizar [!INCLUDE[prod_short](includes/prod_short.md)] usando extensiones](ui-extensions.md)  
[Trabajar con [!INCLUDE[prod_short](includes/prod_short.md)]](ui-work-product.md)


[!INCLUDE[footer-include](includes/footer-banner.md)]
