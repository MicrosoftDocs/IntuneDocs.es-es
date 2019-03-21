---
title: Configuración de correo electrónico para dispositivos Windows 10 en Microsoft Intune - Azure | Microsoft Docs
description: Cree un perfil de correo electrónico de configuración de dispositivos que use servidores de Exchange y recupere los atributos de Azure Active Directory. También puede habilitar SSL y sincronizar el correo electrónico y los programas en dispositivos Windows 10 con Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/29/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3e2b3708b6b0c75a1384a7cdbdb524dff3f0627d
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565441"
---
# <a name="email-profile-settings-for-devices-running-windows-10---intune"></a>Configuración del perfil de correo electrónico para dispositivos que ejecuten Windows 10 Intune

Use la configuración del perfil de correo electrónico para configurar la aplicación Correo en los dispositivos que ejecutan Windows 10.

- **Servidor de correo electrónico**: indique el nombre de host del servidor Exchange.
- **Nombre de la cuenta**: indique el nombre para mostrar en la cuenta de correo electrónico. Este nombre se muestra en los dispositivos de los usuarios.
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

## <a name="security-settings"></a>Configuración de seguridad

- **SSL**: use la comunicación de Capa de sockets seguros (SSL) al enviar correos electrónicos, recibir correos electrónicos y comunicarse con el servidor Exchange.

## <a name="synchronization-settings"></a>Configuración de sincronización

- **Cantidad de correo electrónico para sincronizar**: elija el número de días de correo electrónico que quiere sincronizar. También puede seleccionar **Ilimitado** para sincronizar todo el correo electrónico disponible.
- **Programación de la sincronización**: seleccione la programación para que los dispositivos sincronicen datos del servidor de Exchange También puede seleccionar **Cuando llegan los mensajes** (los datos se sincronizan tan pronto como llegan) o **Manual** (el usuario del dispositivo debe iniciar la sincronización).

## <a name="content-sync-settings"></a>Configuración de la sincronización de contenido

- **Tipo de contenido para sincronizar**: seleccione los tipos de contenido que quiere sincronizar con los dispositivos:
  - **Contactos**
  - **Calendarioio**
  - **Tareas**

## <a name="next-steps"></a>Pasos siguientes
[Configuración de las opciones de correo electrónico en Intune](email-settings-configure.md)
