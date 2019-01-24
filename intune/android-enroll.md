---
title: Inscribir dispositivos Android en Intune
titlesuffix: Microsoft Intune
description: Obtenga información sobre cómo inscribir dispositivos Android en Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/31/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 3d86afec4e501533ab0048e866969a5bf73c2c57
ms.sourcegitcommit: 911923e9fe0eed52b1c93e400f776956835e582f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2019
ms.locfileid: "54387043"
---
# <a name="enroll-android-devices"></a>Inscripción de dispositivos Android

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Como administrador de Intune, puede administrar los dispositivos Android siguientes:
- Dispositivos Android, incluidos los dispositivos Samsung KNOX estándar.
- Dispositivos Android Enterprise, incluidos:
    - **Dispositivos del perfil de trabajo de Android**: Los dispositivos personales tienen permiso para acceder a datos corporativos. Los administradores pueden administrar las cuentas de trabajo, las aplicaciones y los datos. Los datos personales del dispositivo se mantienen separados de los datos de trabajo y los administradores no tienen control sobre la configuración o los datos personales. 
    - **Dispositivos de Android dedicados**: Dispositivos de propiedad corporativa, de uso único, como señalización digital, impresión de vales o administración de inventario. Los administradores bloquean el uso de un dispositivo para un conjunto limitado de aplicaciones y vínculos web. También impide que los usuarios agreguen otras aplicaciones o lleven a cabo otras acciones en el dispositivo.
    - **Dispositivos Android totalmente administrados**: Dispositivos de propiedad corporativa, de un solo usuario, que se usan exclusivamente para trabajo y no para uso personal. Los administradores pueden administrar todo el dispositivo y aplicar controles de directiva que no están disponibles para perfiles de trabajo. 

## <a name="prerequisite"></a>Requisito previo

Para prepararse para administrar dispositivos móviles, debe establecer la entidad de administración de dispositivos móviles (MDM) en **Microsoft Intune**. Para obtener instrucciones, consulte [Set the MDM authority](mdm-authority-set.md) (Establecimiento de la autoridad de MDM). Este elemento solo se establece una vez, la primera vez que configura Intune para la administración de dispositivos móviles.

## <a name="set-up-android-enrollment"></a>Configuración de la inscripción de Android

De manera predeterminada, Intune permite la inscripción de dispositivos Android y Samsung KNOX Standard. Tras cumplir los requisitos previos, los administradores simplemente deben [indicar a sus usuarios cómo inscribir sus dispositivos](/intune-user-help/enroll-your-device-in-intune-android).

Después de que un usuario se haya inscrito, puede empezar a administrar sus dispositivos en Intune, que incluye la [asignación de directivas de cumplimiento de normas](compliance-policy-create-android.md), la [administración de aplicaciones](app-management.md) y mucho más.

Para más información sobre otras tareas de usuario final, vea estos artículos:

- [Recursos sobre la experiencia del usuario final con Microsoft Intune](end-user-educate.md)
- [Uso de un dispositivo Android con Intune](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

Para bloquear la inscripción de dispositivos Android, o para bloquear solo la de los dispositivos Android de propiedad personal, vea [Set device type restrictions](enrollment-restrictions-set.md) (Establecer restricciones de tipos de dispositivo).

## <a name="set-up-android-enterprise-enrollment"></a>Configurar la inscripción de Android Enterprise

Android Enterprise es un conjunto de características y servicios para dispositivos Android que permite separar las aplicaciones y los datos personales de un perfil de trabajo que contenga aplicaciones y datos laborales. Dispositivos Android Enterprise, incluidos los dispositivos de perfil de trabajo totalmente administrados y los dispositivos dedicados. 

- [Configurar la inscripción de dispositivos de perfil de trabajo Android](android-work-profile-enroll.md)
- [Configuración de inscripciones de dispositivos dedicados de Android](android-kiosk-enroll.md)
- [Configuración de inscripciones de dispositivos Android totalmente administrados](android-fully-managed-enroll.md)

## <a name="end-user-experience-when-enrolling-a-samsung-knox-device"></a>Experiencia del usuario final al inscribir dispositivos de Samsung Knox

Intune es compatible ahora con dispositivos que ejecutan Samsung Knox Standard para la administración de varios usuarios. Esto quiere decir que los usuarios pueden iniciar y cerrar sesión en un dispositivo con sus credenciales de Azure AD. El dispositivo se administra de forma centralizada tanto si se usa como si no. Cuando los usuarios inician sesión, tienen acceso a las aplicaciones y, además, se les aplican las directivas. Cuando los usuarios cierran sesión, se borran todos los datos de la aplicación.

Hay algunas cuestiones que se deben tener en cuenta al inscribir dispositivos de Samsung Knox:
-   Incluso si no hay directivas que requieran un PIN, para poder inscribirse el dispositivo debe tener al menos un PIN de cuatro dígitos. Si carece de él, se le pedirá al usuario que cree uno.
-   No hay interacción del usuario para certificados de unión al área de trabajo (WPJ, Workplace Join Certificates).
-   Se le proporciona al usuario información sobre la inscripción en el servicio y lo que puede hacer la aplicación.
-   Se le proporciona al usuario información sobre la inscripción en Knox y lo que puede hacer Knox.
-   Si se aplica una directiva de cifrado, los usuarios deben establecer una contraseña compleja de seis caracteres como código de acceso al dispositivo.
-   El usuario no recibe ningún aviso adicional sobre la instalación de los certificados insertados por un servicio para el acceso a los recursos de empresa.
- En algunos dispositivos antiguos de Knox se le pedirán al usuario certificados adicionales que se usan para el acceso a los recursos de empresa.
- Si al intentar instalar WPJ en un dispositivo Samsung Mini aparecen los errores **No se encontró el certificado** o **No se puede registrar el dispositivo**, instale las actualizaciones más recientes del firmware de Samsung.

## <a name="next-steps"></a>Pasos siguientes

- [Configurar la inscripción de dispositivos de perfil de trabajo Android](android-work-profile-enroll.md)
- [Configuración de inscripciones de dispositivos dedicados de Android](android-kiosk-enroll.md)
- [Configuración de inscripciones de dispositivos Android totalmente administrados](android-fully-managed-enroll.md)
