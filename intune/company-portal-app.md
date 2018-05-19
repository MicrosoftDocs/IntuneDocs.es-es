---
title: Configuración de la aplicación Portal de empresa
titleSuffix: Microsoft Intune
description: Aprenda a aplicar personalización de marca específica de la compañía a la aplicación del Portal de empresa de Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f5d7a825f70694e9888cf80d96eff12b9169e9ae
ms.sourcegitcommit: b0ad42fe5b5627e5555b2f9e5bb81bb44dbff078
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2018
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Configuración de la aplicación Portal de empresa de Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

El Portal de empresa de Intune es el lugar donde los usuarios tienen acceso a los datos de la compañía y pueden realizar tareas habituales como, por ejemplo, inscribir dispositivos, instalar aplicaciones y buscar información de ayuda del departamento de TI.        

> [!Tip]        
> Al personalizar el portal de empresa, los valores de configuración se aplicarán tanto al sitio web como a las aplicaciones del portal de empresa.       

Con la personalización del portal de empresa, es más fácil ofrecer una experiencia conocida y útil a los usuarios finales. Para ello, desde la carga de trabajo **Mobile apps**, elija **Configuración** > **Personalización de marca del Portal de empresa** y luego configure los valores necesarios.  

> [!Note]       
> Portal de empresa para Windows 10 ahora enviará registros de aplicaciones directamente a Microsoft cuando el usuario inicie el flujo de trabajo para obtener ayuda con un problema. Esto permitirá que sea más fácil solucionar los problemas que se envían a Microsoft.  

## <a name="company-contact-information-and-privacy-statement"></a>Información de contacto y declaración de privacidad de la empresa        
El nombre de la empresa se muestra como título del portal de empresa. La información y los datos de contacto se muestran a los usuarios en la pantalla **Contacto de TI** del Portal de empresa. La declaración de privacidad se muestra cuando el usuario hace clic en el vínculo de privacidad.

Los campos marcados con un asterisco (*) son obligatorios.       


| Nombre de campo | Longitud máxima | Más información |
|---|---|---|
|**Nombre de la empresa**| 40 | Es el nombre que se muestra como título del portal de empresa. |
|**Nombre del contacto del departamento de TI** | 40 | Es el nombre que se muestra en la página **Contacto de TI**. |
|**Número de teléfono del departamento de TI** | 20 | Es el número de contacto que se muestra en la página **Contacto de TI**. |
|**Dirección de correo electrónico del departamento de TI**| 40 | Es la dirección de contacto que se muestra en la página **Contacto de TI**. Debe especificar una dirección de correo electrónico válida en el formato `alias@domainname.com`. |
| **Información adicional**|    120     | Se muestra en la página **Contacto de TI**. |
| **Dirección URL de la declaración de privacidad de la empresa** |     79     | Puede especificar su propia declaración de privacidad de la empresa, que aparece cuando los usuarios hacen clic en los vínculos de privacidad del portal de empresa. Debe especificar una dirección URL válida en el formato `<https://www.contoso.com>`. |

## <a name="support-contacts"></a>Contactos de soporte técnico     
El sitio web de soporte se muestra a los usuarios en el portal de empresa para que puedan tener acceso al soporte en línea.        

|Nombre de campo|Longitud máxima|Más información|
|---|---|---|
|**Dirección URL del sitio web de soporte**|150|Si tiene un sitio web de soporte que desea que utilicen los usuarios finales, especifique la dirección URL aquí. La dirección URL debe tener el formato **https://www.contoso.com**. Si no especifica una dirección URL, no se mostrará ningún sitio web de soporte en la página **Contacto de TI** del portal de empresa.|
|**Nombre del sitio web de soporte técnico**|40|Este nombre es el nombre descriptivo que se muestra para la dirección URL del sitio web de soporte. Si especifica una dirección URL de sitio web de soporte sin nombre descriptivo, se mostrará Ir a sitio web de TI en la página **Contacto de TI** del Portal de empresa.

## <a name="company-branding-customization"></a>Personalización de la marca de empresa       
Puede personalizar su portal de empresa con su logotipo de empresa, nombre de empresa, color de tema y fondo.     

|Nombre del campo|Más información|
|---|---|
|**Color del tema**|Seleccione el color del tema que se aplicará al portal de empresa. Puede elegir en el selector de colores o escribir un código hexadecimal concreto.|
|**Mostrar logotipo de la empresa**|Si habilita esta opción, puede cargar el logotipo de su empresa para que se muestre en el portal de empresa. Puede cargar dos logotipos: uno que se mostrará cuando el fondo del portal de empresa sea de color blanco y otro que se mostrará cuando el fondo del portal de empresa use el color de tema seleccionado. El tipo de archivo del logotipo debe ser .png o .jpg, con una resolución máxima de 400 x 100 píxeles y un tamaño de 750 KB o menos.<br>También puede mostrar el nombre de la empresa que escribió junto al logotipo cargado.|

Después de guardar los cambios, puede elegir **Obtenga una vista previa de la configuración en el portal web de Intune.** para ver el aspecto de las configuraciones.
