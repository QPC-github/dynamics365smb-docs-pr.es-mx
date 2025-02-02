---
title: Análisis de datos de informes con Excel y XML
description: Aprenda a usar Excel y XML para analizar un conjunto de datos de informe.
author: jswymer
ms.topic: conceptual
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: 'task, process, report, print, schedule, save, Excel, PDF, Word, dataset'
ms.date: 03/16/2022
ms.author: jswymer
---
# <a name="analyzing-report-data-with-excel-and-xml" />Análisis de datos de informes con Excel y XML

[!INCLUDE[2021_releasewave2](includes/2021_releasewave2.md)]

Como desarrollador o usuario avanzado, es útil inspeccionar los datos que se generan para un conjunto de datos de informe determinado mientras crea nuevos informes o modifica los existentes. Para admitir esta capacidad, puede exportar un conjunto de datos de informe como datos sin procesar a una hoja de cálculo de Excel, o archivo XML, directamente. En Excel, por ejemplo, puede realizar un análisis ad-hoc de los datos y diagnosticar problemas.

## <a name="get-started" />Introducción

Para exportar un conjunto de datos de informe a una hoja de cálculo de Excel o archivo XML, abra el informe en el cliente y luego, en la página de la solicitud, seleccione **Enviar a** > **Documento Microsoft Excel (solo datos)** o **Documento XML**. El archivo se descargará en su dispositivo.

## <a name="more-about-excel-data-only" />Más sobre Excel (solo datos)

La opción **Documento de Microsoft Excel (solo datos)** exporta los resultados del informe y los criterios que se utilizaron para generarlos, pero no incluye el diseño del informe. El archivo de Excel incluirá el conjunto de datos completo, como datos sin procesar, organizados en filas y columnas. Se incluyen todas las columnas de datos del conjunto de datos del informe, independientemente de si se utilizan en el diseño del informe.

Una vez tenga el archivo de Excel, puede comenzar a analizar los datos. Por ejemplo, podría filtrar los datos y utilizar Power Pivot para mostrarlo.

Cada vez que exporta resultados, se crea una nueva hoja de trabajo. Utilizando la opción **Documento de Microsoft Excel (solo datos)**, puede ejecutar el mismo informe y reutilizar los cambios de formato. Por ejemplo, para Power Pivot puede ejecutar el informe nuevamente por otro período de tiempo, copiar los resultados en la hoja de trabajo y luego actualizar la hoja de trabajo. También puede buscar una aplicación de generación de informes en [AppSource](https://appsource.microsoft.com/).

> [!NOTE]
> No puede exportar un informe que tenga más de 1 048 576 filas o 16 384 columnas. Con Business Central local, el número máximo de filas exportadas puede ser incluso menor. Business Central Server incluye una opción de configuración, denominada **Filas de datos máximas permitidas para enviar a Excel**, para disminuir el límite del valor máximo. Para más información, vea [Configuración de Business Central Server](/dynamics365/business-central/dev-itpro/administration/configure-server-instance#General) o comuníquese con su administrador.

## <a name="for-administrators" />Para administradores

- **Documento de Microsoft Excel (solo datos)** se introdujo como característica opcional en 2021 lanzamiento de versiones 1, actualización 18.3. Para dar acceso a los usuarios a esta característica mientras ejecutan el primer lanzamiento de versiones de 2021, habilite la característica **Guardar el conjunto de datos de informe en documento de Microsoft Excel**, en **Administración de características**. Para más información, consulte [Habilitación de las próximas funciones antes de tiempo](/dynamics365/business-central/dev-itpro/administration/feature-management). En el segundo lanzamiento de versiones de 2021, esta característica pasa a ser permanente, por lo que no tendrá que habilitarla.

- Para usar un **Documento de Microsoft Excel (solo datos)**, las cuentas de usuario necesitan el permiso **Permitir la acción Exportar conjunto de datos de informe a Excel**. Puede conceder a los usuarios este permiso asignando el conjunto de permisos **Herramientas de resolución de problemas** o **Exportar informe Excel**. Para obtener más información, consulte [Asignar permisos a usuarios y grupos](ui-define-granular-permissions.md)  

## <a name="for-developers-and-advanced-users" />Para desarrolladores y usuarios avanzados

La opción **Documento de Microsoft Excel (solo datos)** exporta todas las columnas, incluidas las que contienen filtros e instrucciones de formato para otros valores. A continuación se muestran algunos puntos de interés:

- Los datos binarios de un campo, como una imagen, no se exportan.

  En las columnas que contienen datos binarios, los campos incluirán el texto **Datos binarios ({0} bytes)**, donde **{0}** indica el número de bytes.
- A partir de Business Central 2021 lanzamiento de versiones 2, el archivo de Excel también incluye el hoja de cálculo **Metadatos de informe**.

  Esta hoja de cálculo muestra los filtros aplicados al reporte y las propiedades generales del reporte, como el nombre, el id. y los detalles de la extensión. Los filtros se muestran en la columna **Filtro (DataItem::Table::FilterGroupNo::FieldName)**. Los filtros de esta columna incluyen filtros establecidos en la página de solicitud del informe. También incluye filtros definidos en código AL, por ejemplo, por la [propiedad DataItemLink](/dynamics365/business-central/dev-itpro/developer/properties/devenv-dataitemlink-reports-property) y la [propiedad DataItemTableView](/dynamics365/business-central/dev-itpro/developer/properties/devenv-dataitemtableview-property).

Para obtener más información sobre el diseño de informes, consulte [Resumen del informe](/dynamics365/business-central/dev-itpro/developer/devenv-reports).

## <a name="see-also" />Consulte también

[Trabajar con informes](ui-work-report.md)  
[Administrar diseños de informes y documentos](ui-manage-report-layouts.md)  
[Asignar permisos a usuarios y grupos](ui-define-granular-permissions.md)  
[Trabajar con [!INCLUDE[prod_short](includes/prod_short.md)]](ui-work-product.md)

[!INCLUDE[footer-include](includes/footer-banner.md)]
