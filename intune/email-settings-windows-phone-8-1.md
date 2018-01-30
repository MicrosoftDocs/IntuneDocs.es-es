---
title: "Configuración de correo electrónico de Intune para Windows Phone 8.1"
titleSuffix: Azure portal
description: "Conozca la configuración de Intune que puede usar para configurar las conexiones de correo electrónico en los dispositivos Windows Phone 8.1."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 352d6bd9-ec8c-439e-be3a-ad3daf307df2
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 14b39932bb6bf2ee32fea8e51603fc055436dbe9
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="email-profile-settings-for-windows-phone-81-devices-in-microsoft-intune"></a>Configuración del perfil de correo electrónico para dispositivos Windows Phone 8.1 en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


- **Apply all settings to Windows Phone 8.1 only** (Aplicar toda la configuración solo a Windows Phone 8.1): esta es una opción que puede configurar en el portal clásico de Intune. En el portal de Azure, esta opción no se puede cambiar. Si se establece en **Configured** (Configurado), cualquier configuración solo se aplicará a dispositivos Windows Phone 8.1. Si establece en **Not Configured** (No configurado), esta configuración también se aplicará a dispositivos Windows 10 Mobile.
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
