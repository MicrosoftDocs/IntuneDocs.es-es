---
title: Configuración de Outlook para dispositivos iOS y Android en Microsoft Intune
description: Cree una directiva de configuración para establecer la configuración de Microsoft Outlook que se ejecutan en dispositivos iOS y Android.
keywords: ''
author: Erikre
ms.author: erikre
ms.reviewer: smithre4
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 691029cc7b9fd8880c5440a84b95bbf2462920d6
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180330"
---
# <a name="microsoft-outlook-configuration-settings"></a>Opciones de configuración de Microsoft Outlook 

Use una directiva de configuración para establecer la configuración de Microsoft Outlook que se ejecuta en dispositivos iOS y Android. 

Para crear una directiva de configuración de aplicaciones para dispositivos iOS administrados, vea [Agregar directivas de configuración de aplicaciones para dispositivos iOS administrados](app-configuration-policies-use-ios.md). Para crear una directiva de configuración de aplicaciones para dispositivos Android administrados, vea [Agregar directivas de configuración de aplicaciones para dispositivos Android administrados](app-configuration-policies-use-android.md). 

## <a name="configuration-settings"></a>Opciones de configuración

Al agregar una directiva de configuración de Intune, puede establecer una configuración específica para configurar Microsoft Outlook. En el panel **Configuración** puede establecer la configuración de la cuenta de correo electrónico.

### <a name="basic-authentication-email-account-settings"></a>Configuración de la cuenta de correo electrónico de autenticación básica
Outlook para iOS y Android ofrece a los administradores de Exchange la posibilidad de "insertar" configuraciones de cuenta en sus usuarios locales que usan autenticación básica con el protocolo ActiveSync. Para más información, consulte [Programa de instalación de cuenta en Outlook para iOS y Android mediante la autenticación básica](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/account-setup). Para habilitar la configuración del programa de instalación de la cuenta, puede configurar las siguientes opciones:

- **Servidor de correo electrónico**: escriba el nombre de host del servidor de Exchange local (por ejemplo, mail.contoso.com).
- **Nombre de la cuenta de correo electrónico**: indique el nombre para mostrar en la cuenta de correo electrónico. Este nombre se muestra en los dispositivos de los usuarios.
- **Atributo de nombre de usuario de AAD**: este nombre es el atributo que Intune obtiene de Azure Active Directory (Azure AD). Intune genera dinámicamente el nombre de usuario que usa este perfil. Existen varias opciones:
  - **Nombre principal de usuario**: obtiene el nombre, como `user1` o `user1@contoso.com`.
  - **Dirección SMTP principal**: obtiene el nombre en formato de dirección de correo electrónico, como `user1@contoso.com`.
- **Atributo Dirección de correo electrónico de AAD**: elija cómo se genera la dirección de correo electrónico para el usuario. Seleccione **Nombre principal de usuario** (`user1@contoso.com` o `user1`) para usar el nombre principal completo como dirección de correo electrónico o **Dirección SMTP principal** (`user1@contoso.com`) para usar la dirección SMTP principal para iniciar sesión en Exchange. La recomendación es seleccionar **Dirección SMTP principal**.
- **Dominio de la cuenta** (opcional): el dominio de la cuenta.

## <a name="next-steps"></a>Pasos siguientes
[Configuración de las opciones de correo electrónico en Intune](email-settings-configure.md)

