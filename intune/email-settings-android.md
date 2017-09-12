---
title: "Configuración del correo electrónico de Intune para dispositivos Android y Android for Work"
titleSuffix: Azure portal
description: "Aprenda sobre la configuración de Intune que puede usar para configurar las conexiones de correo electrónico en los dispositivos Android."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 06/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4d3458cc-fcaa-4648-b13f-bf1f0616c1c5
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 436db2f645a3f2e787cb27a8c110630a8fbb1f38
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2017
---
# <a name="email-profile-settings-for-android--devices-in-microsoft-intune"></a>Configuración del perfil de correo electrónico para dispositivos Android en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Como administrador de Intune, puede crear y asignar configuraciones de correo electrónico a los siguientes dispositivos Android:
- [Android Samsung KNOX Standard](#android-samsung-knox-standard-email-settings)
- [Android for Work](#android-for-work-email-settings)

## <a name="android-samsung-knox-standard-email-settings"></a>Configuración del correo electrónico de Android Samsung KNOX Standard
- **Servidor de correo electrónico**: el nombre de host del servidor de Exchange.
- **Nombre de la cuenta**: el nombre para mostrar de la cuenta de correo electrónico tal y como aparecerá para los usuarios en sus dispositivos.
- **Atributo de nombre de usuario de AAD**: es el atributo de Active Directory (AD) o Azure AD que se usará para generar el nombre de usuario de este perfil de correo electrónico. Seleccione la **dirección SMTP principal**, como user1@contoso.com, o el **nombre principal de usuario**, como user1@contoso.com.
- **Atributo de dirección de correo electrónico de AAD**: cómo se genera la dirección de correo electrónico para el usuario en cada dispositivo. Seleccione **Dirección SMTP primaria** para usar la dirección SMTP primaria para iniciar sesión en Exchange o use **Nombre principal de usuario** para utilizar el nombre principal completo como dirección de correo electrónico.
- **Método de autenticación**: seleccione **Nombre de usuario y contraseña** o **Certificados** como método de autenticación que usa el perfil de correo electrónico.
    - Si seleccionó **Certificado**, seleccione un SCEP cliente o un perfil de certificado PKCS que haya creado anteriormente para autenticar la conexión de Exchange.

### <a name="security-settings"></a>Configuración de seguridad

- **SSL**: use la comunicación de Capa de sockets seguros (SSL) al enviar correos electrónicos, recibir correos electrónicos y comunicarse con el servidor Exchange.
- **S/MIME**: envíe correo electrónico saliente mediante cifrado S/MIME.
    - Si seleccionó **Certificado**, seleccione un SCEP cliente o un perfil de certificado PKCS que haya creado anteriormente para autenticar la conexión de Exchange.

### <a name="synchronization-settings"></a>Configuración de sincronización

- **Cantidad de correo electrónico para sincronizar**: elija el número de días de correo electrónico que quiere sincronizar, o seleccione **Unlimited** (Sin límite) para sincronizar todos el correo electrónico disponible.
- **Programación de sincronización**: seleccione la programación según la cual los dispositivos sincronizarán datos de Exchange Server. También puede seleccionar **Cuando llegan los mensajes**, en cuyo caso los datos se sincronizan tan pronto como llegan, o **Manual**, donde el usuario del dispositivo debe iniciar la sincronización.

### <a name="content-sync-settings"></a>Configuración de la sincronización de contenido

- **Tipo de contenido para sincronizar**: seleccione los tipos de contenido que quiere sincronizar con los dispositivos:
    - **Contactos**
    - **Calendarioio**
    - **Tareas**

## <a name="android-for-work-email-settings"></a>Configuración del correo electrónico de Android for Work

- **Aplicación de correo electrónico**: seleccione **Gmail** o **Nine Work**.
- **Servidor de correo electrónico**: el nombre de host del servidor de Exchange.
- **Atributo de nombre de usuario de AAD**: es el atributo de Active Directory (AD) o Azure AD que se usará para generar el nombre de usuario de este perfil de correo electrónico. Seleccione la **dirección SMTP principal**, como user1@contoso.com, o el **nombre principal de usuario**, como user1@contoso.com.
- **Atributo de dirección de correo electrónico de AAD**: cómo se genera la dirección de correo electrónico para el usuario en cada dispositivo. Seleccione **Nombre principal de usuario** para usar el nombre principal completo como dirección de correo electrónico, o **Nombre de usuario**.
- **Método de autenticación**: seleccione **Nombre de usuario y contraseña** o **Certificados** como método de autenticación que usa el perfil de correo electrónico.
    - Si seleccionó **Certificado**, seleccione un SCEP cliente o un perfil de certificado PKCS que haya creado anteriormente para autenticar la conexión de Exchange.
- **SSL**: use la comunicación de Capa de sockets seguros (SSL) al enviar correos electrónicos, recibir correos electrónicos y comunicarse con el servidor Exchange.
- **Cantidad de correo electrónico para sincronizar**: elija el número de días de correo electrónico que quiere sincronizar, o seleccione **Unlimited** (Sin límite) para sincronizar todos el correo electrónico disponible.
- **Tipo de contenido para sincronizar** (solo Nine Work): seleccione los tipos de contenido que quiere sincronizar con los dispositivos:
    - **Contactos**
    - **Calendarioio**
    - **Tareas**
