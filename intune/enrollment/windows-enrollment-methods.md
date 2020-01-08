---
title: Métodos de inscripción de Intune para dispositivos Windows
titleSuffix: Microsoft Intune
description: Obtenga información sobre las distintas formas de inscripción de dispositivos Windows en Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: ''
ms.openlocfilehash: 060c3c00a228794d3f237a6362b048bf23e1a933
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/31/2019
ms.locfileid: "75547710"
---
# <a name="intune-enrollment-methods-for-windows-devices"></a>Métodos de inscripción de Intune para dispositivos Windows

Para administrar dispositivos en Intune, primero hay que inscribirlos en el servicio Intune. Es posible inscribir tanto dispositivos personales como corporativos para la administración de Intune. 

Hay dos maneras de inscribir dispositivos en Intune:
- Los usuarios pueden inscribir automáticamente sus PC Windows. 
- Los administradores pueden configurar directivas para forzar la inscripción automática sin intervención del usuario.

## <a name="user-self-enrollment-in-intune"></a>Inscripción automática del usuario en Intune

Los usuarios pueden inscribir automáticamente sus dispositivos Windows mediante cualquiera de estos métodos:

- [Bring Your Own Device (BYOD)](https://docs.microsoft.com/intune-user-help/enroll-windows-10-device): los usuarios inscriben sus dispositivos personales al conectarse a una cuenta **profesional o educativa** desde **Configuración** en el dispositivo. Mediante este proceso:
  - Se registra el dispositivo con Azure Active Directory para obtener acceso a recursos corporativos, como el correo electrónico.
  - Se inscribe el dispositivo en Intune como un dispositivo personal (BYOD).
Si un administrador ha configurado la inscripción automática (disponible con suscripciones premium de Azure AD), el usuario solo tiene que escribir sus credenciales una sola vez. En caso contrario, tendrán que inscribirse por separado a través de la inscripción solo MDM y volver a escribir sus credenciales.  
- La **inscripción solo MDM** permite a los usuarios inscribirse en un grupo de trabajo existente, Active Directory o PC unido a Azure Active Directory en Intune. Los usuarios se inscriben desde Configuración en el equipo Windows existente. Este método no se recomienda, ya que no registra el dispositivo en Azure Active Directory. Además, impide el uso de características como el acceso condicional.
- [Unión a Azure Active Directory (Azure AD)](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network): une el dispositivo con Azure Active Directory y permite que los usuarios inicien sesión en Windows con sus credenciales de Azure AD. Si está habilitada la inscripción automática, el dispositivo se inscribe automáticamente en Intune. La ventaja de la inscripción automática es que consiste en un proceso de un solo paso para el usuario. En caso contrario, tendrán que inscribirse por separado a través de la inscripción solo MDM y volver a escribir sus credenciales. Los usuarios se inscriben de esta manera durante la configuración rápida de Windows o desde Configuración. El dispositivo se marca como corporativo en Intune.
- [Autopilot](enrollment-autopilot.md): automatiza la unión a Azure AD e inscribe nuevos dispositivos corporativos en Intune. Este método simplifica la experiencia de configuración rápida y elimina la necesidad de aplicar imágenes de sistema operativo personalizadas en los dispositivos. Cuando los administradores usan Intune para administrar dispositivos Autopilot, pueden administrar directivas, perfiles y aplicaciones (entre otros) después de inscribirlos.  Hay cuatro tipos de implementación de Autopilot: el [modo de implementación automática](https://docs.microsoft.com/windows/deployment/windows-autopilot/self-deploying) (para quioscos multimedia, señalización digital o un dispositivo compartido), el [modo controlado por el usuario](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven) (para usuarios tradicionales), [Preferencial](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove) permite que los asociados o el personal de TI aprovisione de manera previa un equipo con Windows 10 totalmente configurado y listo para el negocio y [Autopilot para dispositivos existentes](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices) que permite implementar fácilmente la versión más reciente de Windows 10 en los dispositivos existentes.

## <a name="administrator-based-enrollment-in-intune"></a>Inscripción basada en administrador en Intune

Los administradores pueden configurar los siguientes métodos de inscripción que no necesitan la interacción del usuario:

- La [Unión a Azure AD híbrido](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy) permite a los administradores configurar la directiva de grupo de Active Directory para inscribir automáticamente los dispositivos que están unidos a Azure AD híbrido. 
- La [Administración conjunta de Configuration Manager](https://docs.microsoft.com/configmgr/comanage/overview) permite a los administradores inscribir los dispositivos administrados por Configuration Manager en Intune para obtener los beneficios de Intune y Configuration Manager. 
- El [Administrador de inscripciones de dispositivos](device-enrollment-manager-enroll.md) (DEM) es una cuenta de servicio especial. Las cuentas de DEM tienen permisos que habilitan a los usuarios autorizados a inscribir y administrar varios dispositivos corporativos. Estos tipos de dispositivos son buenos para aplicaciones de punto de venta o de utilidad, por ejemplo, pero inadecuados para usuarios que necesitan acceso al correo electrónico o a los recursos de empresa. Este método no permite el uso de características como el acceso condicional. 
- La [inscripción masiva](../windows-bulk-enroll.md) permite que un usuario autorizado una grandes cantidades de nuevos dispositivos corporativos a Azure Active Directory e Intune. Es necesario crear un paquete de aprovisionamiento con la aplicación Diseñador de configuración de Windows (WCD). Después, mediante el uso de un medio USB durante la experiencia inicial de configuración rápida de Windows o desde un PC Windows existente, debe instalar el paquete de aprovisionamiento para inscribir automáticamente los dispositivos en Intune. Este método no permite el uso del acceso condicional. 
- La [inscripción de dispositivos Windows IoT Core](https://docs.microsoft.com/windows/iot-core/manage-your-device/intunedeviceenrollment) se logra al usar el panel de Windows IoT Core para preparar el dispositivo y, a continuación, al usar Windows Configuration Designer para crear un paquete de aprovisionamiento. Luego, usando una tarjeta SD durante el arranque inicial, instala el paquete de aprovisionamiento para inscribir automáticamente los dispositivos en Intune.

## <a name="next-steps"></a>Pasos siguientes

[Obtenga información sobre las funcionalidades de los métodos de inscripción de Windows](enrollment-method-capab.md)
