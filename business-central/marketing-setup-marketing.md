---
title: Configurar la información de Marketing y gestión de contactos
description: 'Puede configurar la administración de marketing y de contacto de Business Central para optimizar las relaciones con los clientes potenciales o actuales, y mejorar las campañas y las promociones.'
author: SorenGP
ms.topic: conceptual
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: 'relationship, prospect, client, customer, campaign, promo'
ms.search.forms: '5172, 5173, 5170, 5094, 429'
ms.date: 04/01/2021
ms.author: edupont
---
# <a name="setting-up-relationship-management" />Configurar la gestión de relaciones

Antes de empezar a trabajar con sus contactos e intereses de marketing, hay algunas decisiones y pasos que debe tomar para configurar la manera en que el área de marketing administra ciertos aspectos de sus contactos. Por ejemplo, puede decidir si sincronizar la ficha de contacto con la ficha de cliente, proveedor o cuenta bancaria, cómo se definirán las series numéricas o qué saludo estándar se usará al escribir a sus contactos.

La gestión de contactos y el establecimiento de una estrategia para identificar, atraer y conservar a los clientes le ayudará a optimizar su negocio y a incrementar la satisfacción del cliente. Asimismo, el uso de un sistema adecuado de gestión de contactos será de gran ayuda en los procesos de creación y mantenimiento de relaciones con los clientes. La comunicación es la clave en estas relaciones. Para lograr el éxito, las empresas deben ser capaces de establecer la comunicación adecuada con sus clientes, proveedores y socios comerciales potenciales y existentes. El establecimiento de una estrategia sobre cómo utilizará la empresa la información de contactos es un paso fundamental. Esta información estará accesible para muchos grupos diferentes de su empresa, por lo que un sistema adecuado incrementará la productividad de todos los usuarios.

Puede configurar la gestión de marketing y de contactos desde la página **Configuración de marketing**. Para abrir la página **Configuración de marketing**, elija el icono ![Bombilla que abre la función Dígame.](media/ui-search/search_small.png "Dígame qué desea hacer") , escriba **Configuración de marketing** y luego elija el enlace relacionado.

## <a name="automatically-copying-specific-information-from-contact-companies-to-contact-persons" />Copiar automáticamente información específica desde las empresas de contacto a las personas de contacto
Parte de la información de contacto de las empresas es la misma que la de las personas que trabajan allí, como la dirección. En la sección **Herencia** de la página **Configuración de marketing**, puede configurar la aplicación para que copie automáticamente campos específicos de la ficha de empresa de contacto a la ficha de persona de contacto cada vez que cree una persona de contacto de una empresa de contacto. Por ejemplo, puede seleccionar copiar el código de vendedor, los detalles de dirección (dirección, colonia 2, municipio/ciudad, código postal y provincia), los detalles de comunicación (número de fax, respuesta de télex y número de teléfono) y más.

Al modificar uno de estos campos en la ficha Empresa de contacto, la aplicación modificará de forma automática el campo de la ficha Persona de contacto, a menos que ese campo se haya modificado manualmente.

Para obtener más información, consulte [Crear contactos](marketing-create-contact-companies.md).

## <a name="use-predefined-defaults-on-new-contacts" />Usar valores predeterminados predefinidos en contactos nuevos
Puede hacer que la aplicación asigne de forma automática ciertos códigos de idioma, territorio, vendedor y país/región como valores predeterminados para cada nuevo contacto. También se puede especificar un ciclo de ventas predeterminado que la aplicación asignará de forma automática a cada nueva oportunidad creada.

La herencia de campos sobrescribe los valores predeterminados en la configuración. Por ejemplo, si el idioma predeterminado es el inglés, pero el de la empresa contacto es el alemán, la aplicación asignará automáticamente el alemán como idioma para las personas de contacto almacenadas de esa empresa.

<!--You can also setup a default salutation that application automatically assigns to your contacts. You can use these salutations in your interaction template attachments (for example, Microsoft Word documents). When setting up a default salutation, you can enter a salutation text and a salutation format. For example, if the salutation text is Dear, and the salutation format is Salutation Text + Title + Name, application will automatically enter Dear Mr. John Smith as a salutation for a contact called John Smith.-->

## <a name="automatically-recording-interactions" />Interacciones registradas automáticamente
[!INCLUDE[prod_short](includes/prod_short.md)] puede registrar automáticamente los documentos de compras y ventas como interacciones (por ejemplo, los pedidos, facturas, recibos, etc.), así como los correos electrónicos, las llamadas telefónicas y las hojas de portada.

Para obtener más información, vea [Registro automático de interacciones con contactos](marketing-auto-record-interactions.md)

## <a name="synchronizing-contacts-with-customers-and-more" />Sincronizar contactos con clientes, etc.
Para poder sincronizar la ficha del contacto con la del cliente, proveedor y banco, debe seleccionar un código de relación de negocio para clientes, proveedores y bancos. Por ejemplo, solo se puede enlazar un contacto con un cliente existente si seleccionó un código de relación de negocio para los clientes en la página **Configuración de marketing**.

Para obtener más información, consulte [Procedimiento: Sincronizar contactos con clientes, proveedores y cuentas bancarias](marketing-create-contact-companies.md#synchronizing-contacts-with-customers-vendors-employees-and-bank-accounts).  

## <a name="assigning-a-number-series-to-contacts-and-opportunities" />Asignar una serie numérica a contactos y oportunidades
Puede configurar números de serie para contactos y oportunidades. Si ha configurado una serie de números para los contactos, cuando cree un contacto y seleccione <kbd>Enter</kbd>en el campo N.º de la ficha de contacto y la aplicación introduce automáticamente el siguiente número de contacto disponible.

Para obtener más información acerca de las series numéricas, consulte [Crear series numéricas](ui-create-number-series.md).

## <a name="searching-for-duplicate-contacts-when-contacts-are-created" />Buscar contactos duplicados al crear contactos
Puede elegir que la aplicación busque duplicados de forma automática cada vez que cree una empresa de contacto o buscarlos de forma manual después de crearlos. También puede hacer que la aplicación actualice las cadenas de búsqueda de forma automática cada vez que se crea un contacto o se modifica su información. Puede elegir el porcentaje de acierto búsqueda, es decir, el porcentaje de cadenas idénticas que dos contactos deben tener para que la aplicación los considere duplicados.

## <a name="see-also" />Consulte también
[Gestionar contactos](marketing-contacts.md)  
[Trabajar con [!INCLUDE[prod_short](includes/prod_short.md)]](ui-work-product.md)  


[!INCLUDE[footer-include](includes/footer-banner.md)]
