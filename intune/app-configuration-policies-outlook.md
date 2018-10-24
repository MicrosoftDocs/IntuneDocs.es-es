---
title: Configuración de Outlook para dispositivos iOS y Android en Microsoft Intune
description: Cree una directiva de configuración para establecer la configuración de Microsoft Outlook que se ejecutan en dispositivos iOS y Android.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7fc9f34bbd3d14ac4291582247b1e45169c2cccc
ms.sourcegitcommit: d92caead1d96151fea529c155bdd7b554a2ca5ac
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/06/2018
ms.locfileid: "48828938"
---
# <a name="microsoft-outlook-configuration-settings"></a>Opciones de configuración de Microsoft Outlook 

Use una directiva de configuración para establecer la configuración de Microsoft Outlook que se ejecuta en dispositivos iOS y Android. 

Para crear una directiva de configuración de aplicaciones para dispositivos iOS administrados, vea [Agregar directivas de configuración de aplicaciones para dispositivos iOS administrados](app-configuration-policies-use-ios.md). Para crear una directiva de configuración de aplicaciones para dispositivos Android administrados, vea [Agregar directivas de configuración de aplicaciones para dispositivos Android administrados](app-configuration-policies-use-android.md). 

## <a name="configuration-settings"></a>Opciones de configuración

Al agregar una directiva de configuración de Intune, puede establecer una configuración específica para configurar Microsoft Outlook. En el panel **Configuración** puede establecer la configuración de la cuenta de correo electrónico.

### <a name="email-account-settings"></a>Configuración de la cuenta de correo electrónico

Las siguientes opciones de configuración son específicas de Microsoft Outlook.

- **Servidor de correo electrónico**: indique el nombre de host del servidor Exchange.
- **Nombre de la cuenta de correo electrónico**: indique el nombre para mostrar en la cuenta de correo electrónico. Este nombre se muestra en los dispositivos de los usuarios.
- **Atributo de nombre de usuario de AAD**: este nombre es el atributo que Intune obtiene de Azure Active Directory (AAD). Intune genera dinámicamente el nombre de usuario que usa este perfil. Las opciones son:
  - **Nombre principal de usuario**: obtiene el nombre, como `user1` o `user1@contoso.com`.
  - **Dirección SMTP principal**: obtiene el nombre en formato de dirección de correo electrónico, como `user1@contoso.com`.
  - **Nombre de la cuenta sAM**: requiere el dominio, como `domain\user1`.

    Indique también:  
    - **Origen del nombre de dominio de usuario**: elija **AAD** (Azure Active Directory) o **Personalizar**.

      Si quiere obtener los atributos de **AAD**, escriba:
      - **Atributo de nombre de dominio de usuario de AAD**: elija si quiere obtener el atributo **Nombre de dominio completo** o **Nombre de NetBIOS** del usuario

      Si quiere usar los atributos **Personalizados**, escriba:
      - **Nombre de dominio personalizado que quiere usar**: escriba un valor que Intune use como nombre de dominio, como `contoso.com` o `contoso`.

- **Atributo Dirección de correo electrónico de AAD**: elija cómo se genera la dirección de correo electrónico para el usuario. Seleccione **Nombre principal de usuario** (`user1@contoso.com` o `user1`) para usar el nombre principal completo como dirección de correo electrónico o **Dirección SMTP principal** (`user1@contoso.com`) para usar la dirección SMTP principal para iniciar sesión en Exchange.
- **Dominio de la cuenta** (opcional): el dominio de la cuenta.

## <a name="next-steps"></a>Pasos siguientes
[Configuración de las opciones de correo electrónico en Intune](email-settings-configure.md)

