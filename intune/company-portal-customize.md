---
title: Personalizar el portal de empresa
description: "El Portal de empresa de Intune permite a los usuarios realizar tareas comunes como inscribir dispositivos, instalar aplicaciones y encontrar información del departamento de TI."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb4a9f01-f857-4563-ab6f-5d0d7dfa659d
ms.reviewer: angerobe
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: e54f1a2ab0e62ab3ffcbf6fa1ae6f974c5f18717
ms.contentlocale: es-es
ms.lasthandoff: 06/08/2017


---

# <a name="customize-the-company-portal"></a>Personalizar el portal de empresa

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

En este tema se explica a los administradores cómo pueden personalizar la aplicación del Portal de empresa de Intune y el sitio web del Portal de empresa.

El portal de empresa de Intune es el lugar donde los usuarios tienen acceso a los datos de la empresa y pueden realizar tareas habituales como, por ejemplo, inscribir dispositivos, instalar aplicaciones y buscar información de ayuda del departamento de TI.

El Portal de empresa de Microsoft Intune proporciona a los usuarios acceso a aplicaciones y datos de la empresa. El Portal de empresa está disponible en dos formas:

-   **Aplicación del Portal de empresa**: una aplicación que está disponible en dispositivos administrados con Intune. Obtenga más información sobre las aplicaciones de Portal de empresa para [Android](/intune-user-help/using-your-android-device-with-intune), [iOS](/intune-user-help/using-your-iOS-or-macOS-device-with-intune) y [Windows](/intune-user-help/using-your-windows-device-with-intune).


- **El sitio web del Portal de empresa**: un sitio web que permite a los usuarios finales realizar la mayor parte de las tareas que pueden hacer desde la aplicación del Portal de empresa. La dirección URL del Portal de empresa de Intune es [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com). Obtenga más información sobre este sitio web en [Usar el sitio web del Portal de empresa de Intune](/intune-user-help/using-the-intune-company-portal-website).

> [!TIP]
> Al personalizar el portal de empresa, los valores de configuración se aplicarán tanto al sitio web como a las aplicaciones del portal de empresa.

Estas son algunas de las tareas que los usuarios pueden hacer en el Portal de empresa:

-   Inscribir dispositivos
-   Ver el estado de sus dispositivos
-   Restablecer su dispositivo
-   Restablecer su contraseña
-   Bloquear de forma remota su dispositivo
-   Descargar el software implementado por la organización
-   Ponerse en contacto con el departamento de TI para obtener ayuda

## <a name="customize-company-portal-settings"></a>Personalizar la configuración del Portal de empresa
Con la personalización del portal de empresa, es más fácil ofrecer una experiencia conocida y útil a los usuarios finales. Inicie sesión en la [consola de administrador de Microsoft Intune](https://manage.microsoft.com) como administrador de inquilinos o de servicios, elija **Administración** &gt; **Portal de empresa** y configure el Portal de empresa.

## <a name="company-contact-information-and-privacy-statement"></a>Información de contacto y declaración de privacidad de la empresa
El nombre de la empresa se muestra como título del portal de empresa. La información y los datos de contacto se muestran a los usuarios en la pantalla Contacto de TI del portal de empresa. La declaración de privacidad se muestra cuando el usuario hace clic en el vínculo de privacidad.

|Nombre de campo|Longitud máxima|Más información|
    |----------|------------------------|----------------|
    |Nombre de la empresa|40|Es el nombre que se muestra como título del portal de empresa.|
    |Nombre del contacto del departamento de TI|40|Es el nombre que se muestra en la página **Contacto de TI**.|
    |Número de teléfono del departamento de TI|20|Es el número de contacto que se muestra en la página **Contacto de TI**.|
    |Dirección de correo electrónico del departamento de TI|40|Es la dirección de contacto que se muestra en la página **Contacto de TI**. Debe especificar una dirección de correo electrónico válida en el formato **alias@domainname.com**.|
    |Información adicional|120|Se muestra en la página **Contacto de TI**.|
    |Dirección URL de la declaración de privacidad de la empresa|79|Puede especificar su propia declaración de privacidad de la empresa, que aparece cuando los usuarios hacen clic en los vínculos de privacidad del portal de empresa. Debe escribir una dirección URL válida con el formato https://www.contoso.com.|

## <a name="support-contacts"></a>Contactos de soporte técnico
El sitio web de soporte se muestra a los usuarios en el portal de empresa para que puedan tener acceso al soporte en línea.

|Nombre del campo|Longitud máxima|Más información|
    |----------|------------------------|----------------|
    |Dirección URL del sitio web de soporte:|150|Si tiene un sitio web de soporte que desea que utilicen los usuarios finales, especifique la dirección URL aquí. La dirección URL debe tener el formato https://www.contoso.com. Si no especifica una dirección URL, no se mostrará ningún sitio web de soporte en la página **Contacto de TI** del portal de empresa.|
    |Nombre del sitio web|40|Este nombre es el nombre descriptivo que se muestra para la dirección URL del sitio web de soporte. Si solo especifica una dirección URL de sitio web de soporte sin nombre descriptivo, se mostrará **Ir a sitio web de TI** en la página **Contacto de TI** del portal de empresa.|

## <a name="company-branding-customization"></a>Personalización de la marca de empresa
Puede personalizar su portal de empresa con su logotipo de empresa, nombre de empresa, color de tema y fondo.

|Nombre del campo|Más información|
    |----------|----------------|
    |Color del tema|Seleccione el color del tema que se aplicará al portal de empresa.|
    |Incluir el logotipo de la empresa|Si habilita esta opción, puede cargar el logotipo de su empresa para que se muestre en el portal de empresa. Puede cargar dos logotipos: uno que se mostrará cuando el fondo del portal de empresa sea de color blanco y otro que se mostrará cuando el fondo del portal de empresa use el color de tema seleccionado. El tipo de archivo del logotipo debe ser .png o .jpg, con una resolución máxima de 400 x 100 píxeles y un tamaño de 750 KB o menos.|
    |Elegir un fondo para la aplicación de portal de empresa para Windows 8|Esta opción de configuración solo afecta al fondo de la aplicación de portal de empresa de Windows 8.|


Después de guardar los cambios puede usar los vínculos que aparecen en la parte inferior de la página del **Portal de empresa** de la consola de administración para ver el sitio web del portal de empresa. Estos vínculos no se pueden cambiar. Cuando un usuario inicia sesión, estos vínculos muestran las suscripciones en el portal de empresa.

