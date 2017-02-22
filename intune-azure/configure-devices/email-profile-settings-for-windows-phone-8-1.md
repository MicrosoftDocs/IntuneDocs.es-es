---
title: "Configuración del correo electrónico de Intune para Windows Phone 8.1 | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: aprenda cómo usar la configuración de Intune para configurar conexiones de correo electrónico en dispositivos Windows Phone 8.1."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 352d6bd9-ec8c-439e-be3a-ad3daf307df2
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f16c9dfb41cb2cfe07ce473a131dac767dee9c74
ms.openlocfilehash: e8d8a7b7a7c752269e36e0e40f136f6fb002a19f


---

# <a name="email-profile-settings-for-windows-phone-81-devices-in-intune-azure-preview"></a>Configuración del perfil de correo electrónico para dispositivos Windows Phone 8.1 en la versión preliminar de Intune Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


- **Apply all settings to Windows Phone 8.1 only** (Aplicar toda la configuración solo a Windows Phone 8.1): esta es una opción que puede configurar en el portal de Intune clásico. En el portal de Azure, esta opción no se puede cambiar. Si se establece en **Configured** (Configurado), cualquier configuración solo se aplicará a dispositivos Windows Phone 8.1. Si establece en **Not Configured** (No configurado), esta configuración también se aplicará a dispositivos Windows 10 Mobile.
- **Servidor de correo electrónico**: el nombre de host del servidor de Exchange.
- **Nombre de la cuenta**: el nombre para mostrar de la cuenta de correo electrónico tal y como aparecerá para los usuarios en sus dispositivos.
- **Atributo de nombre de usuario de AAD**: es el atributo de Active Directory (AD) o Azure AD que se usará para generar el nombre de usuario de este perfil de correo electrónico. Seleccione la **dirección SMTP principal**, como **user1@contoso.com**, o el **nombre principal de usuario**, como **usuario1** o **user1@contoso.com**.
- **Atributo de dirección de correo electrónico de AAD**: cómo se genera la dirección de correo electrónico para el usuario en cada dispositivo. Seleccione **Dirección SMTP primaria** para usar la dirección SMTP primaria para iniciar sesión en Exchange o **Nombre principal de usuario** para usar el nombre principal completo como dirección de correo electrónico.


## <a name="security-settings"></a>Configuración de seguridad

- **SSL**: use la comunicación de Capa de sockets seguros (SSL) al enviar correos electrónicos, recibir correos electrónicos y comunicarse con el servidor Exchange.



## <a name="synchronization-settings"></a>Configuración de sincronización

- **Cantidad de correo electrónico para sincronizar**: elija el número de días de correo electrónico que quiere sincronizar, o seleccione **Unlimited** (Sin límite) para sincronizar todos el correo electrónico disponible.
- **Programación de sincronización**: seleccione la programación por la que los dispositivos sincronizarán datos de Exchange Server. También puede seleccionar **Cuando llegan los mensajes** (los datos se sincronizan tan pronto como llegan) o **Manual** (el usuario del dispositivo debe iniciar la sincronización).

## <a name="content-sync-settings"></a>Configuración de la sincronización de contenido

- **Tipo de contenido para sincronizar**: seleccione los tipos de contenido que quiere sincronizar con los dispositivos:
    - **Contactos**
    - **Calendarioio**
    - **Tareas**



<!--HONumber=Feb17_HO1-->


