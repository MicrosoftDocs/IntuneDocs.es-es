---
title: Configuración de la aplicación Portal de empresa
titleSuffix: Microsoft Intune
description: Aprenda a aplicar personalización de marca específica de la compañía a la aplicación del Portal de empresa de Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/01/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 33f24a3d7b30973855bb303bb97bf703cd4dc5fa
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567275"
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Configuración de la aplicación Portal de empresa de Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

El Portal de empresa de Intune es el lugar donde los usuarios tienen acceso a los datos de la compañía y pueden realizar tareas habituales como, por ejemplo, inscribir dispositivos, instalar aplicaciones y buscar información de ayuda del departamento de TI.        

> [!Tip]        
> Al personalizar el portal de empresa, los valores de configuración se aplicarán tanto al sitio web como a las aplicaciones del portal de empresa. Tenga en cuenta que los usuarios deben tener una licencia de Intune asignada para tener acceso al sitio web Portal de empresa.

Con la personalización del Portal de empresa de Intune, podrá ofrecer una experiencia conocida y útil a los usuarios finales. Para ello, en el portal de Intune, seleccione **Aplicaciones cliente** > **Branding and customization** (Personalización de marca y personalización) y establezca la configuración necesaria. 

> [!Note]       
> Si usa Azure Government, se ofrecen registros de aplicaciones para que el usuario final decida cómo compartirá cuando inicie el proceso para pedir ayuda para un problema. Pero si no usa Azure Government, el Portal de empresa para Windows 10 enviará registros de aplicaciones directamente a Microsoft cuando el usuario inicie el proceso de pedir ayuda para un problema. Si se envían los registros de aplicaciones a Microsoft, será más fácil solucionar los problemas. 

## <a name="company-information-and-privacy-statement"></a>Información de la empresa y declaración de privacidad de la empresa        
El nombre de la empresa se muestra como título del portal de empresa. La declaración de privacidad se muestra cuando el usuario hace clic en el vínculo de privacidad.

Los campos marcados con un asterisco (*) son obligatorios.       


| Nombre de campo | Longitud máxima | Más información |
|---|---|---|
|**Nombre de la empresa**| 40 | Este nombre se muestra como título del Portal de empresa y aparece como texto a lo largo de la experiencia del usuario de Intune. |
| **URL de la declaración de privacidad** |     79     | Puede especificar su propia declaración de privacidad de la empresa, que aparece cuando los usuarios hacen clic en los vínculos de privacidad del portal de empresa. Debe especificar una dirección URL válida en el formato `<https://www.contoso.com>`. |

## <a name="support-information"></a>Información de soporte técnico      
Escriba la información de soporte técnico de la compañía para que los empleados dispongan de un contacto para preguntas relacionadas con Intune.          

|Nombre de campo|Longitud máxima|Más información|
|---|---|---|
|**Nombre de contacto** | 40 | Es el nombre que se muestra en la página **Contacto de TI**. |
|**Número de teléfono** | 20 | Este número de contacto se muestra en la página **Contact IT** (Contactar con TI) para que los empleados puedan ponerse en contacto con usted para cuestiones de soporte técnico. |
|**Dirección de correo electrónico**| 40 | Es la dirección de contacto que se muestra en la página **Contacto de TI**. Debe especificar una dirección de correo electrónico válida en el formato `alias@domainname.com`. |
|**Nombre del sitio web**| 40 | Este nombre es el nombre descriptivo que se muestra para la dirección URL del sitio web de soporte. Si especifica una dirección URL de sitio web de soporte sin nombre descriptivo, se mostrará Ir a sitio web de TI en la página **Contacto de TI** del Portal de empresa. |
|**URL del sitio web**| 150 | Si tiene un sitio web de soporte que desea que utilicen los usuarios finales, especifique la dirección URL aquí. La dirección URL debe tener el formato `https://www.contoso.com`. Si no especifica una dirección URL, no se mostrará ningún sitio web de soporte en la página **Contacto de TI** del portal de empresa. |
| **Información adicional**| 120 | Se muestra en la página **Contacto de TI**. |


## <a name="company-identity-branding-customization"></a>Personalización de la marca de identidad de la empresa      
Puede personalizar su portal de empresa con su logotipo de empresa, nombre de empresa, color de tema y fondo.     

### <a name="theme-color-and-logo-in-the-company-portal"></a>Color de tema y logotipo en el Portal de empresa
Aplique un color de tema al Portal de empresa. Seleccione un color estándar o escriba un código hexadecimal de seis dígitos de un color personalizado.

|Nombre de campo|Más información|
|---|---|
|**Seleccionar un color estándar o escribir un código hexadecimal de seis dígitos**| Elija **Estándar** para seleccionar visualmente un color. Elija **Personalizado** para seleccionar un color específico según un valor de código hexadecimal.|
|**Elegir color de tema**| Seleccione el color del tema que se aplicará al portal de empresa. Puede elegir un color estándar o escribir un código hexadecimal concreto. |
|**Mostrar**| Seleccione si se mostrará **Nombre y logotipo de empresa**, **Company logo only** (Solo logotipo de empresa) o **Company name only** (Solo nombre de empresa). |
|**Cargar el logotipo de empresa**|Puede cargar el logotipo de la empresa para que se muestre en el Portal de empresa. Tenga en cuenta que el color del texto se selecciona automáticamente para proporcionar el nivel más alto de contraste. Para obtener la mejor apariencia, cargue un logotipo con un fondo transparente.<p><ul><li>Tamaño máximo de imagen: 400 px x 400 px</li><li>Tamaño máximo de archivo: 750 KB</li><li>Tipo de archivo: PNG, JPG o JPEG</li></ul>|

Después de cargar el logotipo, en el área de vista previa se mostrará el logotipo de con el color del tema. Si decide mostrar el nombre de la empresa, se mostrará en blanco o negro en el Portal de empresa y se seleccionará automáticamente para proporcionar el nivel más alto de contraste según el color del tema. En el área de vista previa de la pantalla no se mostrará el nombre de la empresa. 

### <a name="logo-to-use-on-white-or-light-backgrounds"></a>Logotipo para usar en fondos claros o blancos
Elija un logotipo que encaje mejor en fondos blancos o claros.

|Nombre de campo|Más información|
|---|---|
|**Cargar el logotipo**| Esta opción está disponible si ha elegido mostrar el logotipo de la empresa. Para obtener la mejor apariencia, cargue un logotipo con un fondo transparente.<p><ul><li>Tamaño máximo de imagen: 400 px x 400 px</li><li>Tamaño máximo de archivo: 750 KB</li><li>Tipo de archivo: PNG, JPG o JPEG</li></ul>|

### <a name="brand-image-for-company-portal"></a>Imagen de marca del Portal de empresa

Muestra una imagen de marca que refleja la marca de la empresa. Después de guardar los cambios, puede elegir **Preview your settings** (Vista previa de la configuración) en el portal web de Intune, en la parte superior de la hoja para ver qué aspecto tendrá la configuración. Tenga en cuenta que solo podrá obtener una vista previa de la imagen de marca en un dispositivo iOS y no el portal web de Intune. 

|Nombre de campo|Más información|
|---|---|
|**Upload your brand image** (Cargar imagen de marca)| Esta opción permite mostrar una imagen de marca. En el Portal de empresa de iOS, muestra una imagen de fondo en la página de perfil del usuario.<p><ul><li>Ancho de imagen recomendado: Menor que 1125 px, pero no inferior a 640 px</li><li>Tamaño máximo de imagen: 1,3 MB</li><li>Tipo de archivo: PNG, JPG o JPEG</li></ul>|

La imagen de marca adecuada puede mejorar la confianza del usuario en el Portal de empresa, ya que presenta un fuerte sentido de marca de la empresa. Estas son algunas sugerencias que puede tener en cuenta para adquirir, elegir y optimizar la imagen para el Portal de empresa. 

- Póngase en contacto con el departamento de marketing o imágenes de la empresa. Es posible que ya tengan un conjunto aprobado de imágenes de marca. Es posible que también le ayuden a optimizar las imágenes según sea necesario. 

- Considere tanto la composición horizontal como la vertical. La imagen debe tener suficiente espacio de fondo rodeando el punto focal. La imagen puede recortarse de forma diferente según el tamaño, la orientación y la plataforma del dispositivo. 

- Evite usar una imagen estándar genérica. La imagen debe reflejar la marca de la empresa y resultar familiar a los usuarios. Si no tiene una, es mejor no usar ninguna que usar una imagen genérica que no aporte ningún significado para el usuario. 

- Quite los metadatos que sean innecesarios. El archivo de imagen puede incluir metadatos, como el perfil de la cámara, la ubicación geográfica, el título, la leyenda, etc. Use una herramienta de optimización de imágenes para eliminar esta información y mantener la calidad al tiempo que cumple los límites de tamaño de archivo. 

Después de agregar o cambiar una imagen de marca en Intune, es posible que el usuario final no vea el cambio en los dispositivos iOS hasta que el Portal de empresa haya reconocido el cambio durante el inicio y se haya reiniciado luego para mostrar la imagen de marca. 

### <a name="brand-image-examples"></a>Ejemplos de imagen de marca

En la siguiente imagen se muestra un ejemplo de imagen de personalización de marca de iPad:

![Captura de pantalla de la imagen de personalización de marca de iPhone de ejemplo](media/company-portal-app/company-portal-app-03.png)

En la siguiente imagen se muestra un ejemplo de imagen de personalización de marca de iPhone:

![Captura de pantalla de la imagen de personalización de marca de iPad de ejemplo](media/company-portal-app/company-portal-app-02.png)

## <a name="windows-company-portal-keyboard-shortcuts"></a>Métodos abreviados de teclado del Portal de empresa de Windows

Los usuarios finales pueden desencadenar acciones de navegación, aplicación y dispositivo en el Portal de empresa de Windows mediante métodos abreviados de teclado (aceleradores).

Los siguientes métodos abreviados de teclado están disponibles en la aplicación del Portal de empresa de Windows.

| Área | Descripción | Método abreviado de teclado |
|:------------------:|:--------------:|:-----------------:|
| Menú de navegación | Navegación | Alt+M |
|  | Inicio | Alt+H |
|  | Todas las aplicaciones | Alt+A |
|  | Aplicaciones instaladas | Alt+I |
|  | Enviar comentarios | Alt+F |
|  | Mi perfil | Alt+U |
|  | Configuración | Alt+T |
| Página principal, icono de dispositivo | Cambiar nombre | F2 |
|  | Quitar | Ctrl+D o Eliminar |
|  | Comprobar acceso | Ctrl+M o F9 |
| Detalles del dispositivo | Cambiar nombre | F2 |
|  | Quitar | Ctrl+D o Eliminar |
|  | Comprobar acceso | Ctrl+M o F9 |
| Detalles de la aplicación | Instalar | Ctrl+I |

Los usuarios finales también podrán ver los accesos directos disponibles en la aplicación Portal de empresa de Windows.

![Captura de pantalla de los accesos directos disponibles en el Portal de empresa de Windows](media/company-portal-app/company-portal-app-01.png)

## <a name="next-steps"></a>Pasos siguientes

- [Adición manual de la aplicación Portal de empresa para Windows 10 con Microsoft Intune](store-apps-company-portal-app.md)
