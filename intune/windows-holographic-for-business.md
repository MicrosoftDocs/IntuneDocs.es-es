---
title: 'Administrar dispositivos de Windows Holographic con Microsoft Intune: Azure | Microsoft Docs'
description: Con Microsoft Intune, puede realizar diferentes tareas en dispositivos con Windows Holographic for Business, incluidas configurar el Portal de empresa, crear una directiva de cumplimiento, personalizar la configuración de OMA-URI, implementar aplicaciones, clasificar los dispositivos en grupos, crear perfiles, restringir dispositivos, habilitar actualizaciones de software, establecer términos y condiciones, configurar opciones de VPN y Wi-Fi y usar Hello para empresas.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 825ceb1eee8f6fdd38f8a203324ce3cad7291918
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2018
ms.locfileid: "43317986"
---
# <a name="customize-devices-running-windows-holographic-with-intune"></a>Personalizar dispositivos que ejecutan Windows Holographic con Intune

Microsoft Intune es compatible con dispositivos que ejecutan Windows Holographic for Business, como [Microsoft HoloLens](https://docs.microsoft.com/en-us/hololens/).

Para administrar dispositivos que ejecutan Windows Holographic con Microsoft Intune, debe crear un perfil de actualización de edición. Este perfil de actualización actualiza los dispositivos de Windows Holographic a Windows Holographic for Business. Para Microsoft HoloLens, puede comprar Commercial Suite para obtener la licencia necesaria para la actualización. Para obtener más información, consulte [Upgrade devices running Windows Holographic to Windows Holographic for Business](holographic-upgrade.md) (Actualizar dispositivos que ejecutan Windows Holographic a Windows Holographic for Business).

Para ayudar a administrar y personalizar los dispositivos con Windows Holographic for Business, puede usar las tareas de este artículo. Por ejemplo, puede administrar actualizaciones de software, configurar opciones de VPN, etc.

## <a name="azure-active-directory"></a>Azure Active Directory

Azure Active Directory (AD) es un excelente recurso para ayudar a administrar y controlar los dispositivos que ejecutan Windows Holographic for Business. Con Intune y Azure AD, puede: 

- **[Configurar dispositivos unidos a Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-setup)**: en Azure Active Directory (AD), puede agregar los dispositivos de Windows 10 de trabajo, incluidos aquellos que ejecutan Windows Holographic for Business. Esta característica permite a Azure AD controlar el dispositivo. Ayuda a confirmar que los usuarios acceden a los recursos de la empresa desde dispositivos que cumplen los estándares de seguridad y cumplimiento.

  [Introducción a la administración de dispositivos en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction) proporciona más detalles.

- **[Inscribir dispositivos Windows de forma masiva](windows-bulk-enroll.md)**: puede unir una gran cantidad de nuevos dispositivos Windows a Azure Active Directory (AD) e Intune. Esta característica se denomina inscripción masiva y usa paquetes de aprovisionamiento. Estos paquetes unen los dispositivos que ejecutan Windows Holographic for Business al inquilino de Azure AD y los inscriben en Intune.

## <a name="company-portal"></a>Portal de empresa
**[Configurar la aplicación Portal de empresa](company-portal-app.md)**

Intune incluye la aplicación Portal de empresa para que los usuarios accedan a los datos de la empresa, inscriban dispositivos, instalen aplicaciones, se pongan en contacto con el departamento de TI y mucho más. Puede personalizar la aplicación Portal de empresa para los dispositivos con Windows Holographic for Business.

En la aplicación Portal de empresa, también puede realizar las acciones siguientes:

- [Quitar un dispositivo de Intune](/intune-user-help/unenroll-your-device-from-intune-windows) mediante la aplicación Configuración o la aplicación Portal de empresa
- [Cambiar el nombre de un dispositivo](/intune-user-help/rename-your-device-cpapp)
- [Instalar aplicaciones](/intune-user-help/install-apps-cpapp-windows) en un dispositivo
- [Sincronizar dispositivos manualmente](/intune-user-help/sync-your-device-manually-windows) desde la aplicación Configuración o la aplicación Portal de empresa


## <a name="compliance-policy"></a>Directiva de cumplimiento
**[Crear una directiva de cumplimiento de dispositivos](compliance-policy-create-windows.md)**

Las directivas de cumplimiento son las reglas y la configuración que deben cumplir los dispositivos para ser conformes. Use estas directivas con el acceso condicional para bloquear el acceso a los recursos de la empresa a los dispositivos no conformes. En Intune, se crean directivas de cumplimiento para permitir o bloquear el acceso a dispositivos que ejecutan Windows Holographic for Business. Por ejemplo, puede crear una directiva que exija la habilitación de Bitlocker.

Vea también **[Introducción a las directivas de cumplimiento de dispositivos de Microsoft Intune](device-compliance-get-started.md)**.

## <a name="deploy-and-manage-apps"></a>Implementación y administración de aplicaciones
**[Agregar aplicaciones a Intune](apps-add.md)**

Con Intune, puede agregar aplicaciones a los dispositivos con Windows Holographic for Business. Hay muchas maneras de implementar aplicaciones, por ejemplo:

- [Agregar aplicaciones de Microsoft Store](store-apps-windows.md)
- [Agregar aplicaciones que cree](lob-apps-windows.md)
- [Asignar aplicaciones a grupos](apps-deploy.md)

Microsoft Intune puede implementar aplicaciones universales de Windows en dispositivos con Microsoft HoloLens que ejecutan Windows Holographic for Business. Puede cargar directamente los paquetes de aplicaciones en Intune en Azure Portal, o bien implementarlos desde Microsoft Store para Empresas. Para obtener más información sobre las áreas relacionadas, vea los artículos siguientes:
- Para implementar aplicaciones de línea de negocio (LOB) mediante Azure Portal de Intune, consulte [Adición de aplicaciones de línea de negocio (LOB) de Windows a Microsoft Intune](lob-apps-windows.md).
- Para implementar aplicaciones con Microsoft Store para Empresas, consulte [Cómo administrar las aplicaciones adquiridas a través de la Microsoft Store para Empresas con Microsoft Intune](windows-store-for-business.md). 
- Para obtener información sobre la administración de aplicaciones con Microsoft Intune, consulte [¿Qué es la administración de aplicaciones de Microsoft Intune?](app-management.md).
- Para más información sobre el desarrollo de aplicaciones para Microsoft HoloLens, consulte [Mixed reality apps for Microsoft HoloLens](https://www.microsoft.com/hololens/apps) (Aplicaciones de realidad mixta para Microsoft HoloLens). 

> [!NOTE]
> Los dispositivos HoloLens que ejecutan Windows 10 Holographic for Business 1607 no son compatibles con las aplicaciones con licencia en línea de Microsoft Store para Empresas. Para más información, consulte [Instalación de aplicaciones en HoloLens](https://docs.microsoft.com/en-us/hololens/hololens-install-apps).

## <a name="device-actions"></a>Acciones de dispositivo
Intune tiene algunas acciones integradas que permiten a los administradores de TI realizar diferentes tareas, en local en el dispositivo o de forma remota con Intune en Azure Portal. Los usuarios también pueden emitir un comando remoto desde el Portal de empresa de Intune para los dispositivos de propiedad privada que están inscritos en Intune.

Cuando se usan dispositivos que ejecutan Windows Holographic for Business, se pueden emplear las siguientes acciones: 

- **[Borrar](devices-wipe.md#wipe)**: la acción **Borrar** quita el dispositivo de Intune y lo restaura a la configuración predeterminada de fábrica. Use esta acción antes de entregar el dispositivo a un nuevo usuario o si se pierde o es robado.

- **[Retirar](devices-wipe.md#retire)**: la acción **Retirar** quita el dispositivo de Intune. También quita los datos de las aplicaciones administradas, la configuración y los perfiles de correo electrónico asignados por Intune. Los datos personales del usuario permanecen en el dispositivo.

- **[Sincronizar dispositivos para obtener las últimas directivas y acciones](device-sync.md)**: la acción **Sincronizar** fuerza al dispositivo a registrarse inmediatamente en Intune. Cuando un dispositivo se registra, recibe de inmediato las acciones o las directivas pendientes que se le han asignado. Esta característica ayuda a validar y a solucionar problemas de directivas que se le han asignado, sin tener que esperar al siguiente registro programado.

**[¿Qué es la administración de dispositivos de Microsoft Intune?](device-management.md)** es un buen recurso para obtener información sobre la administración de dispositivos mediante Azure Portal. 

## <a name="device-categories-and-groups"></a>Categorías de dispositivos y grupos
**[Clasificar dispositivos en grupos](device-group-mapping.md)**

Con Intune, puede crear categorías de dispositivos para agregar automáticamente los dispositivos a grupos en función de las categorías creadas, como Ventas, Contabilidad, Recursos humanos, etc. La idea es facilitar la administración de los dispositivos que ejecutan Windows Holographic for Business.

## <a name="device-configuration-profiles"></a>Perfiles de configuración de dispositivos 
**[Introducción a los perfiles de configuración](device-profiles.md) y [Crear un perfil propio](device-profile-create.md)**

Intune incluye opciones y características que se pueden habilitar o deshabilitar en distintos dispositivos dentro de la organización. Estos valores de configuración y características se administran mediante perfiles. Por ejemplo, puede crear un perfil que habilite Cortana o que use Windows Defender Smart Screen en los dispositivos con Windows Holographic for Business.

En los perfiles, puede usar OMA-URI para personalizar algunas opciones, crear restricciones de dispositivos y configurar una red privada virtual (VPN) y Wi-Fi.

#### <a name="custom-device-settingscustom-settings-windows-holographicmd"></a>[Configuración de dispositivo personalizada](custom-settings-windows-holographic.md)

Para configurar las opciones de OMA-URI (Open Mobile Alliance Uniform Resource Identifier), puede crear un perfil personalizado en Intune. Use las opciones de OMA-URI para controlar diversas características de los dispositivos de Windows Holographic for Business, como habilitar una VPN o comprobar si hay actualizaciones en Microsoft Update.

#### <a name="configure-kiosk-modekiosk-settingsmdwindows-holographic-for-business"></a>[Configuración del modo de pantalla completa](kiosk-settings.md#windows-holographic-for-business)

Mediante las características de PC compartidas o de invitado disponibles en Intune, puede configurar los dispositivos Windows Holographic for Business para que se ejecuten como un quiosco. Estos dispositivos pueden ejecutar una aplicación (modo de pantalla completa con una sola aplicación) o varias (modo de pantalla completa con varias aplicaciones).

#### <a name="device-restrictionsdevice-restrictions-windows-holographicmd"></a>[Restricciones de dispositivos](device-restrictions-windows-holographic.md)

Las restricciones de dispositivos permiten controlar distintas opciones y características de los dispositivos, como la exigencia de una contraseña, la instalación de aplicaciones desde [Microsoft Store](https://www.microsoft.com/store/apps/windows?icid=CNavAppsWindowsApps), la habilitación de Bluetooth, etc. Estas restricciones se crean en un perfil de Intune. Este perfil se puede aplicar a varios dispositivos con Windows Holographic for Business.

#### <a name="configure-vpnvpn-settings-configuremd"></a>[Configurar VPN](vpn-settings-configure.md)

Las redes privadas virtuales (VPN) ofrecen a los usuarios un acceso remoto seguro a la red de la empresa. En Intune, puede crear un perfil de VPN que incluya opciones concretas para los dispositivos que ejecutan Windows Holographic for Business. Por ejemplo, puede crear un perfil de VPN para que todos los dispositivos de Windows Holographic for Business usen Citrix VPN como tipo de conexión.

#### <a name="configure-wi-fiwi-fi-settings-configuremd"></a>[Configurar Wi-Fi](wi-fi-settings-configure.md)

Además, puede crear un perfil de Wi-Fi en Intune para asignar la configuración de red inalámbrica a los dispositivos de Windows Holographic for Business. Cuando se asigna un perfil de Wi-Fi, los usuarios finales obtienen acceso de red corporativo sin ninguna configuración de red. Por ejemplo, puede crear una red Wi-Fi dedicada exclusivamente a los dispositivos de Windows Holographic for Business.

## <a name="software-updates"></a>Actualizaciones de software
**[Administrar actualizaciones de software](windows-update-for-business-configure.md)**

Intune incluye una característica denominada anillos de actualización para dispositivos de Windows 10. Estos anillos de actualización incluyen un grupo de opciones que determinan cómo se instalan las actualizaciones. Por ejemplo, puede crear una ventana de mantenimiento para instalar actualizaciones u optar por reiniciar después de instalar las actualizaciones. Un anillo de actualización se puede aplicar a varios dispositivos con Windows Holographic for Business.

## <a name="terms-and-conditions"></a>términos y condiciones
**[Establecer los términos y condiciones de la empresa para el acceso de los usuarios](terms-and-conditions-create.md)**

Antes de que los usuarios inscriban dispositivos y accedan a las aplicaciones de la empresa, incluido el correo electrónico, puede exigirles que acepten los términos y condiciones de la empresa. En Intune, se define cómo se muestran en el Portal de empresa los términos y condiciones, además de asignarlos a los dispositivos que ejecutan Windows Holographic for Business.

## <a name="windows-hello-for-business"></a>Windows Hello para empresas
**[Usar Windows Hello para empresas](windows-hello.md)**

Hello para empresas es un método alternativo de inicio de sesión que emplea una cuenta de Azure Active Directory para reemplazar a una contraseña, una tarjeta inteligente o una tarjeta inteligente virtual. Con Hello para empresas, los dispositivos de Windows Holographic for Business pueden iniciar sesión con un PIN con una longitud mínima establecida por el usuario.
