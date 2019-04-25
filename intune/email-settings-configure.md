---
title: Configuración del correo electrónico en Microsoft Intune (Azure) | Microsoft Docs
titleSuffix: ''
description: Cree un perfil de correo electrónico en Microsoft Intune e implemente este perfil en dispositivos Windows, iOS y Android Enterprise. Use un perfil de correo electrónico para configurar los valores de correo electrónico comunes, incluidos un servidor de correo electrónico y un método de autenticación para conectarse al correo electrónico corporativo en los dispositivos que administra.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/10/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3e0c59ba8744272dd1038ede854ae49879c66f39
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61513246"
---
# <a name="add-email-settings-to-devices-using-intune"></a>Agregar la configuración de correo electrónico a dispositivos que usan Intune

Microsoft Intune incluye una configuración de correo electrónico diferente que puede implementar en los dispositivos de su organización. Un administrador de TI crea perfiles de correo electrónico con una configuración específica para conectarse a un servidor de correo, como Office 365 y Gmail. Los usuarios finales luego se conectarán a las cuentas de correo electrónico corporativas, las autenticarán y las sincronizarán en sus dispositivos móviles. Al crear e implementar un perfil de correo electrónico, puede confirmar que la configuración es estándar en varios dispositivos. Y ayudará a reducir las llamadas de soporte técnico de los usuarios finales que no conocen la configuración de correo electrónico correcta.

Puede usar perfiles de correo electrónico para configurar las opciones de correo electrónico integradas en los siguientes dispositivos:

- Samsung Knox Standard 4.0 y versiones posteriores
- Android Enterprise
- iOS 8.0 y versiones posteriores
- Windows Phone 8.1 y versiones posteriores
- Windows 10 (escritorio) y Windows 10 Mobile

En este artículo se explica cómo crear un perfil de correo electrónico en Microsoft Intune. También incluye vínculos a las distintas plataformas para consultar configuraciones más específicas.

## <a name="create-a-device-profile"></a>Creación del perfil de un dispositivo

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba un **nombre** y una **descripción** para el perfil de correo electrónico.
4. Elija su **plataforma** en la lista desplegable. Las opciones son:

    - **Android** (solo Android Samsung Knox Standard)
    - **Android Enterprise**
    - **iOS**
    - **Windows Phone 8.1**
    - **Windows 10 y versiones posteriores**

5. En la lista desplegable de tipos de **perfil**, elija **Correo electrónico**.
6. Las opciones que se pueden configurar pueden variar en función de la plataforma de la que se trate. Para una configuración específica, elija la plataforma:

    - [Configuración de Android Samsung Knox Standard](email-settings-android.md)
    - [Configuración de Android Enterprise](email-settings-android-enterprise.md)
    - [Configuración de iOS](email-settings-ios.md)
    - [Configuración de Windows Phone 8.1](email-settings-windows-phone-8-1.md)
    - [Configuración de Windows 10](email-settings-windows-10.md)

Después de escribir la configuración y crear el perfil, el perfil se muestra en la lista de perfiles. A continuación, [asigne este perfil a algunos grupos](device-profile-assign.md).

## <a name="remove-an-email-profile"></a>Eliminación de un perfil de correo electrónico

Los perfiles de correo electrónico se asignan a grupos de dispositivos, no a grupos de usuarios. Hay varias maneras de eliminar un perfil de correo electrónico de un dispositivo, incluso cuando hay un solo perfil de este tipo en el dispositivo:

- **Opción 1**: abra el perfil de correo electrónico (**Configuración del dispositivo** > **Perfiles**) y seleccione **Asignaciones**. En la pestaña **Incluir** se muestran los grupos que están asignados al perfil. Haga clic con el botón derecho en el grupo > **Quitar**. Asegúrese de **Guardar** los cambios.

- **Opción 2**: [borre o retire el dispositivo](devices-wipe.md). Puede usar estas acciones para quitar datos y configuraciones de forma selectiva o por completo.

## <a name="secure-email-access"></a>Protección del acceso al correo electrónico

Puede ayudar a proteger los perfiles de correo electrónico con las siguientes opciones:

- **Certificados**: cuando se crea el perfil de correo electrónico, puede elegir un perfil de certificado creado anteriormente en Intune. Este certificado se conoce como "certificado de identidad". Se autentica con un perfil de certificado de confianza o un certificado raíz para confirmar que el dispositivo de un usuario tiene permiso para conectarse. El certificado de confianza se asigna al equipo que autentica la conexión de correo electrónico. Suele ser el servidor de correo nativo.

  Para más información sobre cómo crear y usar perfiles de certificado en Intune, consulte [Secure resource access with certificate profiles](certificates-configure.md) (Protección del acceso a recursos con perfiles de certificado).

- **Nombre de usuario y contraseña**: el usuario final se autentica en el servidor de correo nativo al proporcionar su nombre de usuario y contraseña. La contraseña no existe en el perfil de correo electrónico. Por lo tanto, el usuario final escribe la contraseña al conectarse al correo electrónico.

## <a name="how-intune-handles-existing-email-accounts"></a>Cómo Intune administra las cuentas de correo electrónico existentes

Si el usuario ya ha configurado una cuenta de correo electrónico, el perfil de correo electrónico se asigna de forma diferente, dependiendo de la plataforma.

- **iOS**: Se detecta un perfil de correo electrónico existente duplicado en función del nombre de host y la dirección de correo electrónico. El perfil de correo electrónico duplicado bloquea la asignación de un perfil de Intune. En este caso, la aplicación de Portal de empresa informa al usuario final de que no es compatible y le pide que quite el perfil configurado manualmente. Para evitar este problema, indique a los usuarios finales que se inscriban *antes* de instalar un perfil de correo electrónico. Esto permite que Intune configure el perfil.

- **Windows:** Se detecta un perfil de correo electrónico existente duplicado en función del nombre de host y la dirección de correo electrónico. Intune sobrescribe el perfil de correo electrónico existente que ha creado el usuario final.

- **Android Samsung Knox Standard**: Se detecta un perfil de correo electrónico existente duplicado en función de la dirección de correo electrónico y se sobrescribe con el perfil de Intune. Android no usa el nombre de host para identificar el perfil. No cree varios perfiles de correo electrónico con la misma dirección de correo electrónico en diferentes hosts. Los perfiles se sobrescriben entre sí.

- **Perfiles de trabajo Android**: Intune proporciona dos perfiles de correo electrónico de trabajo Android, uno para la aplicación de Gmail y otro para la aplicación de Nine Work. Estas aplicaciones están disponibles en Google Play Store e instalan el perfil de trabajo del dispositivo. Estas aplicaciones no crean perfiles duplicados. Ambas aplicaciones admiten conexiones a Exchange. Para usar la conectividad de correo electrónico, implemente una de estas aplicaciones de correo electrónico en los dispositivos de los usuarios. A continuación, cree e implemente el perfil de correo electrónico adecuado. Puede que algunas aplicaciones de correo electrónico, como Nine Work, no sean gratuitas. Revise los detalles de la licencia de la aplicación o póngase en contacto con la empresa de la aplicación si tiene alguna pregunta.

## <a name="changes-to-assigned-email-profiles"></a>Cambios realizados en los perfiles de correo electrónico asignados

Si hace cambios en el perfil de correo electrónico que asignó anteriormente, puede que los usuarios finales vean un mensaje que les pida aprobar la reconfiguración de los ajustes de correo electrónico.

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero todavía no hace nada. A continuación, [asigne el perfil a algunos dispositivos](device-profile-assign.md).
