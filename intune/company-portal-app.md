---
title: Configuración de la aplicación Portal de empresa
titleSuffix: Microsoft Intune
description: Aprenda a aplicar personalización de marca específica de la compañía a la aplicación del Portal de empresa de Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bd388131445715a4037cc0480c194d338212dbb0
ms.sourcegitcommit: e814cfbbefe818be3254ef6f859a7bf5f5b99123
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2018
ms.locfileid: "43329980"
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Configuración de la aplicación Portal de empresa de Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

El Portal de empresa de Intune es el lugar donde los usuarios tienen acceso a los datos de la compañía y pueden realizar tareas habituales como, por ejemplo, inscribir dispositivos, instalar aplicaciones y buscar información de ayuda del departamento de TI.        

> [!Tip]        
> Al personalizar el portal de empresa, los valores de configuración se aplicarán tanto al sitio web como a las aplicaciones del portal de empresa.       

Con la personalización del portal de empresa, es más fácil ofrecer una experiencia conocida y útil a los usuarios finales. Para ello, desde la carga de trabajo **Aplicaciones cliente**, elija **Configuración** > **Personalización de marca del Portal de empresa** y luego configure los valores necesarios.  

> [!Note]       
> El Portal de empresa para Windows 10 ahora enviará registros de aplicaciones directamente a Microsoft cuando el usuario inicie el flujo de trabajo para obtener ayuda con un problema. Esto permitirá que sea más fácil solucionar los problemas que se envían a Microsoft.  

## <a name="company-information-and-privacy-statement"></a>Información de la empresa y declaración de privacidad de la empresa        
El nombre de la empresa se muestra como título del portal de empresa. La declaración de privacidad se muestra cuando el usuario hace clic en el vínculo de privacidad.

Los campos marcados con un asterisco (*) son obligatorios.       


| Nombre de campo | Longitud máxima | Más información |
|---|---|---|
|**Nombre de la empresa**| 40 | Este nombre se muestra como título del Portal de empresa y aparece como texto a lo largo de la experiencia del usuario de Intune. |
| **URL de la declaración de privacidad** |     79     | Puede especificar su propia declaración de privacidad de la empresa, que aparece cuando los usuarios hacen clic en los vínculos de privacidad del portal de empresa. Debe especificar una dirección URL válida en el formato `<https://www.contoso.com>`. |

## <a name="support-information"></a>Información de soporte técnico      
Escriba la información de soporte técnico de su empresa para que los empleados dispongan de un contacto para preguntas relacionadas con Intune.       

|Nombre de campo|Longitud máxima|Más información|
|---|---|---|
|**Nombre de contacto** | 40 | Es el nombre que se muestra en la página **Contacto de TI**. |
|**Número de teléfono** | 20 | Este número de contacto se muestra en la página **Contact IT** (Contactar con TI) para que los empleados puedan ponerse en contacto con usted para cuestiones de soporte técnico. |
|**Dirección de correo electrónico**| 40 | Es la dirección de contacto que se muestra en la página **Contacto de TI**. Debe especificar una dirección de correo electrónico válida en el formato `alias@domainname.com`. |
|**Nombre del sitio web**| 40 | Este nombre es el nombre descriptivo que se muestra para la dirección URL del sitio web de soporte. Si especifica una dirección URL de sitio web de soporte sin nombre descriptivo, se mostrará Ir a sitio web de TI en la página **Contacto de TI** del Portal de empresa. |
|**URL del sitio web**| 150 | Si tiene un sitio web de soporte que desea que utilicen los usuarios finales, especifique la dirección URL aquí. La dirección URL debe tener el formato `https://www.contoso.com`. Si no especifica una dirección URL, no se mostrará ningún sitio web de soporte en la página **Contacto de TI** del portal de empresa. |
| **Información adicional**| 120 | Se muestra en la página **Contacto de TI**. |


## <a name="company-branding-customization"></a>Personalización de la marca de empresa       
Puede personalizar su portal de empresa con su logotipo de empresa, nombre de empresa, color de tema y fondo.     

### <a name="theme-color"></a>Color del tema
Aplique un color de tema al Portal de empresa. Seleccione un color estándar o escriba un código hexadecimal de seis dígitos de un color personalizado.

|Nombre de campo|Más información|
|---|---|
|**Tipo de color**| Seleccione el color del tema que se aplicará al portal de empresa. Puede elegir un color estándar o escribir un código hexadecimal concreto. |
|**Elegir color** o **Código de color hexadecimal**| Seleccione el color del tema que se aplicará al portal de empresa. Puede elegir un color estándar o escribir un código hexadecimal concreto. Estas opciones se proporcionan en función del **Tipo de color** que seleccione.  |

### <a name="company-logo"></a>Logotipo de la empresa
Cargue el logotipo de la empresa para que esté visible en toda la experiencia de usuario de Intune.

|Nombre de campo|Más información|
|---|---|
|**Mostrar logotipo de la empresa**|Si habilita esta opción, puede cargar el logotipo de su empresa para que se muestre en el portal de empresa. Puede cargar dos logotipos: uno que se mostrará cuando el fondo del portal de empresa sea de color blanco y otro que se mostrará cuando el fondo del portal de empresa use el color de tema seleccionado. |
|**Upload a logo to use on theme color backgrounds** (Cargar un logotipo para usarlo en fondos de color de tema)| Esta opción está disponible si ha elegido mostrar el logotipo de la empresa. El logotipo debe ser un archivo .png o .jpg, con una resolución máxima de 400 x 400 píxeles y un tamaño de 750 KB o menos. |
|**Upload logo to use on light backgrounds** (Cargar un logotipo para usarlo en fondos de color claro)| Esta opción está disponible si ha elegido mostrar el logotipo de la empresa. El logotipo debe ser un archivo .png o .jpg, con una resolución máxima de 400 x 400 píxeles y un tamaño de 750 KB o menos. |
|**Show company name next to logo** (Mostrar el nombre de la empresa junto al logotipo)| Seleccione esta opción para mostrar el nombre de la empresa que escribió junto al logotipo cargado. |

Después de guardar los cambios, puede elegir **Preview your settings in the Intune Web Portal** (Vista previa de la configuración en el portal web de Intune).
