---
title: Configuración del correo electrónico de Microsoft Intune
titleSuffix: ''
description: Aprenda a configurar Microsoft Intune para crear conexiones al correo electrónico corporativo en los dispositivos que administra.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f51854bfb198ca65cc5fc82bad0e3b3befbb173a
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-configure-email-settings-in-microsoft-intune"></a>Configuración del correo electrónico en Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Se pueden usar perfiles de correo electrónico para configurar dispositivos administrados con los valores necesarios para conectarse al correo electrónico de la empresa y sincronizarlo. Esto ayuda a garantizar que la configuración es estándar en todos los dispositivos y también ayuda a reducir las llamadas al soporte técnico por usuarios finales que no conocen la configuración correcta del correo electrónico.

El cliente de correo integrado se admite en la mayoría de las plataformas. Actualmente no se admiten la mayoría de aplicaciones de correo electrónico de terceros.

Puede usar perfiles de correo electrónico para configurar el cliente de correo nativo en los siguientes tipos de dispositivo:

- Samsung Knox Standard 4.0 y versiones posteriores
- Android for Work
- iOS 8.0 y versiones posteriores
- Windows Phone 8.1 y versiones posteriores
- Windows 10 (escritorio) y Windows 10 Mobile

Use la información de este artículo para conocer los aspectos básicos de la configuración de un perfil de correo electrónico. Luego, siga leyendo los temas correspondientes a cada plataforma para descubrir las peculiaridades de cada dispositivo.

## <a name="create-a-device-profile-containing-email-settings"></a>Creación de un perfil de dispositivo que contenga la configuración de correo electrónico

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, elija **Configuración del dispositivo**.
2. En el panel **Configuración del dispositivo**, en la sección **Administrar**, elija **Perfiles**.
3. En el panel Perfiles, elija **Crear perfil**.
4. En el panel **Crear perfil**, escriba un **Nombre** y una **Descripción** para el perfil de correo electrónico.
5. En la lista desplegable **Plataforma**, seleccione la plataforma del dispositivo a la que quiere aplicar configuración de correo electrónico. Actualmente, puede elegir una de las siguientes plataformas para la configuración del dispositivo de correo electrónico:
    - **Android** (solo Android Samsung Knox Standard)
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 y versiones posteriores**
    - **Windows 10 y versiones posteriores**
6. En la lista desplegable de **tipos de perfil**, elija **Correo electrónico**.
7. Dependiendo de la plataforma que haya elegido, las opciones que pueda configurar serán diferentes. Vaya a uno de los siguientes temas para conocer más detalles sobre la configuración para cada plataforma:
    - [Configuración de Android for Work y Samsung Knox Standard](email-settings-android.md)
    - [Configuración de iOS](email-settings-ios.md)
    - [Configuración de Windows Phone 8.1](email-settings-windows-phone-8-1.md)
    - [Configuración de Windows 10](email-settings-windows-10.md)
8. Cuando haya terminado, vuelva al panel **Crear perfil** y pulse **Crear**.

El perfil se creará y aparecerá en la hoja de la lista de perfiles.
Si desea continuar y asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).

## <a name="further-information"></a>Más información

### <a name="remove-an-email-profile"></a>Eliminación de un perfil de correo electrónico

Si desea quitar un perfil de correo electrónico de un dispositivo, edite la asignación y quite los grupos de los que sea miembro el dispositivo. No se puede quitar de esta manera un perfil de correo electrónico si es el único de un dispositivo.

### <a name="securing-email-access"></a>Protección del acceso al correo electrónico

Los perfiles de correo electrónico se pueden proteger con uno de estos dos métodos:

1. **Certificados**: cuando se crea el perfil de correo electrónico, puede elegir un perfil de certificado creado anteriormente en Intune. Esto se conoce como certificado de identidad y sirve para autenticarse con un perfil de certificado de confianza (o un certificado raíz) para establecer que el dispositivo del usuario tenga permiso para conectarse. El certificado de confianza se asigna al equipo que autentica la conexión de correo electrónico, que suele ser el servidor de correo nativo.
Para más información sobre cómo crear y usar perfiles de certificado en Intune, consulte [Secure resource access with certificate profiles](certificates-configure.md) (Protección del acceso a recursos con perfiles de certificado).
2. **Nombre de usuario y contraseña**: el usuario se autentica en el servidor de correo nativo al proporcionar su nombre de usuario y contraseña.
La contraseña no está incluida en el perfil de correo electrónico, por lo que el usuario necesita proporcionarla al conectarse al correo electrónico.


### <a name="how-intune-handles-existing-email-accounts"></a>Cómo Intune administra las cuentas de correo electrónico existentes

Si el usuario ya ha configurado una cuenta de correo electrónico, el resultado de la asignación del perfil de correo electrónico de Intune depende de la plataforma del dispositivo:

- **iOS**: se detecta un perfil de correo electrónico existente duplicado en función del nombre de host y la dirección de correo electrónico. El perfil de correo electrónico duplicado bloquea la asignación de un perfil de Intune. En este caso, el Portal de empresa informa al usuario de que no es compatible y le pide que quite el perfil configurado manualmente. Para evitar este problema, indique a los usuarios que se inscriban antes de instalar un perfil de correo electrónico. Esto permite que Intune configure el perfil.
- **Windows**: se detecta un perfil de correo electrónico existente duplicado en función del nombre de host y la dirección de correo electrónico. Intune sobrescribe el perfil de correo electrónico existente que ha creado el usuario.
- **Android Samsung Knox Standard**: se detecta un perfil de correo electrónico duplicado existente según la dirección de correo electrónico y se sobrescribe con el perfil de Intune.
Como Android no usa el nombre de host para identificar el perfil, se recomienda que no creen varios perfiles de correo electrónico para usarlos en la misma dirección de correo electrónico en diferentes hosts, ya que estos se sobrescriben entre sí.
- **Android for Work**: Intune proporciona dos perfiles de correo electrónico de Android for Work, uno para cada una de las aplicaciones de correo electrónico de Gmail y de Nine Work. Estas aplicaciones están disponibles en Google Play Store e instalan el perfil de trabajo del dispositivo para que no se generen perfiles duplicados. Ambas aplicaciones admiten conexiones a Exchange. Para habilitar la conectividad de correo electrónico, implemente una de estas aplicaciones de correo en los dispositivos de los usuarios y, después, cree e implemente el perfil de correo electrónico adecuado. Es posible que aplicaciones de correo electrónico como Nine Work no sean gratuitas. Revise los detalles de la licencia de la aplicación o póngase en contacto con la empresa de la aplicación si tiene alguna pregunta.

### <a name="update-an-email-profile"></a>Actualización de un perfil de correo electrónico

Si hace cambios en el perfil de correo electrónico que asignó anteriormente, es posible que los usuarios finales vean un mensaje que les pida aprobar la reconfiguración de los ajustes de correo electrónico.
