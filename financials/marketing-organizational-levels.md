---
title: "Configurar los niveles de organización para las personas de contacto | Documentos de Microsoft"
description: "Puede definir un nivel de organización y asignarlo a su contacto para indicar la posición que tiene en su empresa, por ejemplo alta gestión."
services: project-madeira
documentationcenter: 
author: jswymer
ms.service: dynamics365-financials
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: relationship, client, prospect
ms.date: 06/06/2017
ms.author: jswymer
ms.translationtype: Human Translation
ms.sourcegitcommit: 81636fc2e661bd9b07c54da1cd5d0d27e30d01a2
ms.openlocfilehash: 927c27998bfaeb8d7247158cde1d1eb958a6911f
ms.contentlocale: es-mx
ms.lasthandoff: 07/07/2017


---
# <a name="how-to-set-up-organizational-levels-for-contact-persons"></a>Configurar niveles de organización en personas de contacto
Puede usar niveles de organización en sus contactos para especificar su posición en la empresa, por ejemplo, alta gestión. Puede usar esta información al introducir información sobre sus contactos.

El uso de niveles de organización en contactos es un proceso que consta de dos pasos. Primero, debe definir el código de nivel de organización. Solo debe realizar este paso una vez para cada nivel de organización. Una vez tenga código de nivel de organización, puede comenzar a asignar el código a personas de contacto.

## <a name="to-define-an-organizational-level-code"></a>para definir un código de nivel de organización
El código de nivel de organización define el tipo o la categoría de nivel de organización, por ejemplo DIRGEN o DIRFIN. Puede tener varios códigos de nivel de organización. Para definir el nivel de organización, use la ventana **Niveles de organización**.

1. Seleccione el icono ![Buscar página o informe](media/ui-search/search_small.png "icono Buscar página o informe"), escriba **Niveles de organización** y, a continuación, seleccione el vínculo relacionado.
2. Seleccione la acción **Nuevo** e introduzca un código y una descripción. El código admite un máximo de 11 caracteres y puede ser cualquier combinación de números y letras.

## <a name="to-assign-organizational-levels-to-a-contact-person"></a>para asignar niveles de organización a una persona de contacto
Solo puede asignar niveles de organización a personas de contacto, no a empresas de contacto. Sólo puede asignar un nivel organización a cada contacto.

1. Abra el contacto.
2. En el campo **Niveles de organización**, seleccione el código que desea asignar.

Después de asignar niveles organización a sus contactos, puede utilizar esta información para crear segmentos.

Después de asignar responsabilidades de cargo a sus contactos puede usar esa información para seleccionar contactos para sus segmentos. Para obtener más información, vea [Procedimiento: Agregar contactos a segmentos](marketing-add-contact-segment.md).

## <a name="see-also"></a>Consulte también
[Crear empresas de contacto](marketing-create-contact-companies.md)  
[Crear personas de contacto](marketing-create-contact-persons.md)  
[Trabajar con [!INCLUDE[d365fin](includes/d365fin_md.md)]](ui-work-product.md)  
