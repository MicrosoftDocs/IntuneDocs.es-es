---
title: "Configuración del correo electrónico de Intune | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: aprenda a configurar Intune para crear conexiones al correo electrónico corporativo en los dispositivos que administra."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 484bd9b0-fbf1-4f4f-940c-6b12fa07e228
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 66c189ed45b8b5226e36ef4769c0872c428646bb
ms.lasthandoff: 02/16/2017


---

# <a name="how-to-configure-email-settings-in-microsoft-intune"></a>Configuración del correo electrónico en Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Se puede usar la configuración del perfil de correo electrónico para configurar dispositivos administrados con los valores necesarios para conectarse al correo electrónico de la empresa y sincronizarlo. Esto ayuda a garantizar que la configuración es estándar en todos los dispositivos y también ayuda a reducir las llamadas al soporte técnico por usuarios finales que no conocen la configuración correcta del correo electrónico.

El cliente de correo integrado se admite en la mayoría de las plataformas. Actualmente no se admiten la mayoría de aplicaciones de correo electrónico de terceros.

Puede usar perfiles de correo electrónico para configurar el cliente de correo nativo en los siguientes tipos de dispositivo:

- Android 4.0 y versiones posteriores
- iOS 8.0 y versiones posteriores
- Windows Phone 8.1 y versiones posteriores
- Windows 10 (escritorio) y Windows 10 Mobile

Use la información de este tema para conocer los aspectos básicos de la configuración de un perfil de correo electrónico. Luego, siga leyendo los temas correspondientes a cada plataforma para saber las peculiaridades de cada dispositivo.

## <a name="create-a-device-profile-containing-email-settings"></a>Creación de un perfil de dispositivo que contenga la configuración de correo electrónico

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
3. En la hoja **Intune**, elija **Configurar dispositivos**.
2. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
3. En la hoja de perfiles, elija **Create Profile** (Crear perfil).
4. En la hoja **Create Profile** (Crear perfil), escriba un **nombre** y una **descripción** para el perfil de correo electrónico.
5. En la lista desplegable **Plataforma**, seleccione la plataforma del dispositivo a la que quiere aplicar configuración de correo electrónico. Actualmente, puede elegir una de las siguientes plataformas para la configuración del dispositivo de correo electrónico:
    - **Android**
    - **iOS**
    - **Windows Phone 8.1**
    - **Windows 10 y versiones posteriores**
6. En la lista desplegable de **tipos de perfil**, elija **Correo electrónico**.
7. Dependiendo de la plataforma que eligió, las opciones que pueda configurar serán diferentes. Vaya a uno de los siguientes temas para conocer más detalles sobre la configuración para cada plataforma:
    - [Configuración de Android](email-profile-settings-for-android.md)
    - [Configuración de iOS](email-profile-settings-for-ios.md)
    - [Configuración de Windows Phone 8.1](email-profile-settings-for-windows-phone-8-1.md)
    - [Configuración de Windows 10](email-profile-settings-for-windows-10.md)
8. Cuando haya terminado, vuelva a la hoja **Create Profile** (Crear perfil) y presione **Crear**.

El perfil se crea y aparece en la hoja de la lista de perfiles.
Si desea continuar y asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](how-to-assign-device-profiles.md).

## <a name="further-information"></a>Más información

### <a name="remove-an-email-profile"></a>Eliminación de un perfil de correo electrónico

Si desea quitar un perfil de correo electrónico de un dispositivo, edite la asignación y quite los grupos de los que sea miembro el dispositivo. Tenga en cuenta que un perfil de correo electrónico no se puede quitar de esta manera, si es el único perfil de correo electrónico en un dispositivo.

### <a name="securing-email-access"></a>Protección del acceso al correo electrónico

Los perfiles de correo electrónico se pueden proteger con uno de estos dos métodos:

1. **Certificados**: cuando se crea el perfil de correo electrónico, puede elegir un perfil de certificado creado anteriormente en Intune. Esto se conoce como certificado de identidad y sirve para autenticarse con un perfil de certificado de confianza (o un certificado raíz) para establecer que el dispositivo del usuario tenga permiso para conectarse. El certificado de confianza se implementa en el equipo que autentica la conexión de correo electrónico (que suele ser el servidor de correo nativo).
Para más información sobre cómo crear y usar perfiles de certificado en Intune, consulte [Secure resource access with certificate profiles](/intune-azure/configure-devices/how-to-configure-certificates) (Protección del acceso a recursos con perfiles de certificado).
2. **Nombre de usuario y contraseña**: el usuario se autentica en el servidor de correo nativo al proporcionar su nombre de usuario y contraseña.
La contraseña no está incluida en el perfil de correo electrónico, por lo que el usuario necesita proporcionarla al conectarse al correo electrónico.


### <a name="how-intune-handles-existing-email-accounts"></a>Cómo Intune administra las cuentas de correo electrónico existentes

Si el usuario ya ha configurado una cuenta de correo electrónico, el resultado de la asignación del perfil de correo electrónico de Intune depende de la plataforma del dispositivo:

- **iOS**: se detecta un perfil de correo electrónico existente duplicado en función del nombre de host y la dirección de correo electrónico. El perfil de correo electrónico duplicado bloquea la asignación de un perfil de Intune. En este caso, el Portal de empresa informa al usuario de que no es compatible y le pide que quite el perfil configurado manualmente. Para evitar este problema, indique a los usuarios que se inscriban antes de instalar un perfil de correo electrónico. Esto permite que Intune configure el perfil.
- **Windows**: se detecta un perfil de correo electrónico existente duplicado en función del nombre de host y la dirección de correo electrónico. Intune sobrescribe el perfil de correo electrónico existente que ha creado el usuario.
- **Android**: se detecta un perfil de correo electrónico existente duplicado en función de la dirección de correo electrónico y se sobrescribe con el perfil de Intune.
Como Android no usa el nombre de host para identificar el perfil, se recomienda que no creen varios perfiles de correo electrónico para usarlos en la misma dirección de correo electrónico en diferentes hosts, ya que estos se sobrescriben entre sí.

