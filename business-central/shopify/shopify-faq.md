---
title: Preguntas frecuentes de detalles técnicos
description: Detalles de implementación relacionados con el Connector for Microsoft Dynamics Shopify.
ms.date: 03/27/2023
ms.topic: article
ms.service: dynamics365-business-central
author: AndreiPanko
ms.author: andreipa
---

# <a name="faq-for-technical-details" />Preguntas frecuentes de detalles técnicos

Este artículo responde a las preguntas más frecuentes sobre el conector de Shopify.

## <a name="what-is-shopify" />¿Qué es Shopify?

Shopify es una aplicación basada en suscripción que permite a cualquier persona configurar una tienda en línea y vender sus productos. La plataforma Shopify ofrece a los minoristas en línea un conjunto de servicios para pagos, marketing, envío y participación del cliente.

## <a name="what-is-the-microsoft-dynamics-365-business-central-shopify-connector" />¿Que es Connector for Microsoft Dynamics Dynamics 365 Business Central Shopify?

Con el conector de Shopify las empresas pueden vincular su tienda (o tiendas) de Shopify con [!INCLUDE[prod_short](../includes/prod_short.md)] para maximizar la productividad de la empresa. Usando el conector de Shopify, pueden gestionar la información de su negocio y acceder a ella, desde su negocio y su tienda en línea de Shopify como una unidad.

### <a name="capabilities" />Capacidades

- Soporte para más de una tienda de Shopify
  - Cada tienda tiene su propia configuración, incluida una colección de productos y ubicaciones utilizadas para calcular el inventario y las listas de precios.  
- Sincronización bidireccional de artículos o productos
  - El conector sincroniza imágenes, variantes de productos, códigos de barras, números de productos de proveedores, textos extendidos y etiquetas.  
  - Exportar atributos de producto a Shopify.  
  - Use grupos de precios de clientes seleccionados y descuentos para definir los precios exportados a Shopify.  
  - Decida si los elementos se pueden crear automáticamente o solo permitir actualizaciones de productos existentes.  
- Sincronización de nivel de inventario
  - Elija algunas o todas las ubicaciones disponibles en [!INCLUDE [prod_short](../includes/prod_short.md)].  
  - Actualice los niveles de inventario en múltiples ubicaciones en Shopify.  
- Sincronización bidireccional de clientes
  - Clientes de mapa inteligente por teléfono y correo electrónico.  
  - Utilice plantillas específicas del país/región al crear clientes, lo que ayuda a garantizar que la configuración de impuestos sea correcta.  
- Importar pedidos desde Shopify
  - Incluir pedidos creados en varios canales, como la tienda en línea o **Shopify POS**.
  - Costos de envío, tarjetas de regalo, propinas, métodos de envío y pago, transacciones y riesgo de fraude.  
  - Durante la importación, puede crear automáticamente clientes en [!INCLUDE [prod_short](../includes/prod_short.md)] o decidir gestionar los clientes en Shopify.  
  - Recibir información de pago desde Shopify Payments.
- Seguimiento de la información de cumplimiento
  - Opcionalmente, elija transferir la información de seguimiento del artículo desde [!INCLUDE [prod_short](../includes/prod_short.md)] a Shopify.  

## <a name="why-did-microsoft-and-shopify-form-this-partnership" />¿Por qué Microsoft y Shopify forman esta asociación?

[!INCLUDE[prod_short](../includes/prod_long.md)] se está asociando con Shopify para ayudar a nuestros clientes a crear una mejor experiencia de compra. Mientas que Shopify ofrece a los comerciantes una solución de comercio fácil de usar, [!INCLUDE[prod_short](../includes/prod_short.md)] ofrece una gestión empresarial integral de los equipos de finanzas, ventas, servicios y operaciones. Utilice la conexión perfecta entre las aplicaciones para sincronizar pedidos, existencias e información del cliente para cumplir con los pedidos más rápido y atender mejor a los clientes.

## <a name="which-microsoft-products-are-the-shopify-connector-available-for" />¿Para qué productos de Microsoft está disponible el conector de Shopify?

Esta función está disponible solo para [!INCLUDE[prod_short](../includes/prod_short.md)] en línea, a partir de la versión 20.1. No está disponible para implementaciones locales. El conector está preinstalado para nuevos entornos. Las organizaciones con entornos existentes pueden descargar e instalar el conector desde AppSource. La organización debe tener una licencia de [!INCLUDE [prod_short](../includes/prod_short.md)] y una licencia de Shopify para usar el conector. Para más información sobre países, idiomas y ediciones de [!INCLUDE[prod_short](../includes/prod_short.md)] permitidos, vaya al [Conector de Shopify en AppSource](https://go.microsoft.com/fwlink/?linkid=2196238).

El conector de Shopify no funciona para [Insertar aplicaciones](/dynamics365/business-central/dev-itpro/deployment/embed-app-overview), cuando la URL del cliente tenga el formato `https://[application name].bc.dynamics.com`.

## <a name="what-support-is-offered-for-the-shopify-connector" />¿Qué apoyo se ofrece para el conector de Shopify?

### <a name="includeprodshortincludesprodshortmd" />[!INCLUDE[prod_short](../includes/prod_short.md)]

Connector for Microsoft Dynamics Shopify está cubierto por el modelo de soporte actual. Obtenga más información en [Soporte técnico](/dynamics365/business-central/dev-itpro/administration//manage-technical-support) (solo en inglés).

Obtenga ayuda de un consultor que conozca el conector de Shopify para [!INCLUDE[prod_short](../includes/prod_short.md)], para cumplir con los requisitos exclusivos y específicos de su empresa. Busque en [Servicios de consultoría](https://aka.ms/BCShopifyConsultant).

### <a name="shopify" />Shopify

Obtenga ayuda con Shopify desde el [Centro de ayuda general de Shopify](https://help.shopify.com/) o desde [Soporte 24/7 para su tienda como comerciante de Shopify](https://help.shopify.com/questions#/).

También puede explorar [Experts Marketplace](https://experts.shopify.com/) para encontrar a los expertos adecuados que ofrecen servicios para los comerciantes de Shopify.

## <a name="currently-unsupported-features-however-were-tracking-them-and-may-consider-adding-them" />Actualmente exiten características no compatibles, pero las estamos siguiendo y podemos considerar agregarlas

- Características B2B, incluidas empresas, listas de precios de empresas y condiciones de pago
- Mercados
  - Múltiples traducciones de datos maestros. Puede elegir un idioma que se utilizará para exportar la información del producto.
  - Precios por país/región. Una lista de precios está disponible para la moneda seleccionada. La conversión a otras monedas está a cargo de Shopify.

## <a name="is-the-shopify-connector-extensible" />¿Es ampliable el conector de Shopify?

Sí, el conector de Shopify es extensible. Consulte GitHub para acceder a la [lista de puntos de extensibilidad](https://github.com/microsoft/ALAppExtensions/tree/main/Apps/W1/Shopify) y explore algunos [ejemplos](https://github.com/microsoft/ALAppExtensions/blob/main/Apps/W1/Shopify/extensibility_examples.md).

## <a name="is-the-shopify-connector-open-for-contribution" />¿Está el conector de Shopify abierto a la contribución?

Sí, esta extensión está abierta a contribuciones de nuestra comunidad. Puede encontrar el [código fuente](https://github.com/microsoft/ALAppExtensions/tree/main/Apps/W1/Shopify) en el repositorio de complementos de aplicaciones de Microsoft AL.

## <a name="see-also" />Consulte también

[Introducción al conector para Shopify](get-started.md)  
