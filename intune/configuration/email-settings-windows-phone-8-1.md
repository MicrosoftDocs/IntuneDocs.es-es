---
title: Configuración de correo electrónico de Microsoft Intune para Windows Phone 8.1
titleSuffix: ''
description: Conozca la configuración de Intune que puede usar para configurar las conexiones de correo electrónico en dispositivos que ejecutan Windows Phone 8.1.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e373f0bc511ee7296820bf161da759dedc18b311
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734562"
---
# <a name="email-profile-settings-in-microsoft-intune-for-devices-running-windows-phone-81"></a>Configuración de perfiles de correo electrónico en Microsoft Intune para dispositivos que ejecutan Windows Phone 8.1

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

En este artículo, se muestran las opciones de configuración de perfiles de correo electrónico que puede configurar para los dispositivos que ejecutan Windows Phone 8.1.


- **Apply all settings to Windows Phone 8.1 only** (Aplicar toda la configuración solo a Windows Phone 8.1): esta es una opción que puede configurar en el portal clásico de Intune. En el portal de Azure, esta opción no se puede cambiar. Si se establece en **Configurado**, cualquier configuración solo se aplica a dispositivos Windows Phone 8.1. Si se establece en **No configurado**, esta configuración también se aplica a dispositivos Windows 10 Mobile.
- **Servidor de correo electrónico**: el nombre de host del servidor de Exchange.
- **Nombre de la cuenta**: el nombre para mostrar de la cuenta de correo electrónico tal y como aparecerá para los usuarios en sus dispositivos.
- **Atributo de nombre de usuario de AAD**: es el atributo de Active Directory (AD) o Azure AD que se usa para generar el nombre de usuario de este perfil de correo electrónico. Seleccione la **dirección SMTP principal**, como **user1@contoso.com** , o el **nombre principal de usuario**, como **usuario1** o **user1@contoso.com** .
- **Atributo de dirección de correo electrónico de AAD**: cómo se genera la dirección de correo electrónico para el usuario en cada dispositivo. Seleccione **Dirección SMTP primaria** para usar la dirección SMTP primaria para iniciar sesión en Exchange o **Nombre principal de usuario** para usar el nombre principal completo como dirección de correo electrónico.


## <a name="security-settings"></a>Configuración de seguridad

- **SSL**: use la comunicación de Capa de sockets seguros (SSL) al enviar correos electrónicos, recibir correos electrónicos y comunicarse con el servidor Exchange.



## <a name="synchronization-settings"></a>Configuración de sincronización

- **Cantidad de correo electrónico para sincronizar**: elija el número de días de correo electrónico que quiere sincronizar, o seleccione **Unlimited** (Sin límite) para sincronizar todos el correo electrónico disponible.
- **Programación de sincronización**: seleccione la programación según la cual los dispositivos sincronizarán datos de Exchange Server. También puede seleccionar **Cuando llegan los mensajes** (los datos se sincronizan tan pronto como llegan) o **Manual** (el usuario del dispositivo debe iniciar la sincronización).

## <a name="content-sync-settings"></a>Configuración de la sincronización de contenido

- **Tipo de contenido para sincronizar**: seleccione los tipos de contenido que quiere sincronizar con los dispositivos:
  - **Contactos**
  - **Calendarioio**
  - **Tareas**
