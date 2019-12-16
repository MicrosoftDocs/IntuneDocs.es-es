---
title: Requerir la autenticación multifactor para la inscripción de dispositivos de Intune
titleSuffix: Microsoft Intune
description: Cómo requerir la autenticación multifactor en Azure AD para la inscripción de dispositivos de Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 94280c73-c05c-4e72-b0dd-a7cb997782f9
ROBOTS: ''
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: db04b93deffd2476a97b952fd1c6942fa79e1f05
ms.sourcegitcommit: e75718ee6cf93c0e6c915f2776b785fe8db9f7e0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74955395"
---
# <a name="require-multi-factor-authentication-for-intune-device-enrollments"></a>Requerir la autenticación multifactor para las inscripciones de dispositivos de Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune puede usar la autenticación multifactor (MFA) en Azure Active Directory (AD) en la inscripción de dispositivos para ayudar a proteger los recursos corporativos.

MFA funciona pidiendo dos o más de los métodos de verificación siguientes:

- Algo que usted sabe (generalmente una contraseña o PIN).
- Algo que usted tiene (un dispositivo de confianza que no se puede duplicar fácilmente, como un teléfono).
- Algo que le defina (datos biométricos, como una huella digital).

MFA se admite en iOS, Android, Windows 8.1 o versiones posteriores, Windows Phone 8.1 y Windows 10 Mobile o versiones posteriores.

Al habilitar MFA, los usuarios finales deben proporcionar dos tipos de credenciales para inscribir un dispositivo.

## <a name="configure-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>Configurar Intune para requerir Multi-Factor Authentication en la inscripción de dispositivos

Para requerir MFA cuando se inscribe un dispositivo, siga estos pasos:

>[!Important]
>Para implementar esta directiva, es necesario disponer de Azure Active Directory Premium P1 o una suscripción de mayor nivel asignada a los usuarios.

>[!Important]
>No configure **reglas de acceso basadas en dispositivos** para la inscripción a Microsoft Intune.

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), seleccione **Dispositivos** > **Acceso condicional**. El nodo de acceso condicional al que se accede desde *Intune* es el mismo nodo al que se accede desde *Azure AD*.
2. Pulse **Nueva directiva**.
3. En **Directiva nueva**, escriba un nombre descriptivo para la directiva.
4. En la sección **Asignaciones**, seleccione **Usuarios y grupos**. 
5. En **Usuarios y grupos**, elija **Seleccionar usuarios o grupos** y marque **Usuarios y grupos**. Después, seleccione los usuarios o grupos que recibirán esta directiva y seleccione **Listo**.
6. En la sección **Asignaciones**, elija **Aplicaciones en la nube**.
7. En la pestaña **Incluir** de **Aplicaciones en la nube**, elija **Seleccionar aplicaciones**, **Seleccionar** > **Inscripción a Microsoft Intune** y, luego, **Listo**. Al elegir la **inscripción a Microsoft Intune**, la autenticación MFA de acceso condicional se aplica solo a la inscripción del dispositivo (solicitud única de MFA).
8. En la sección **Asignaciones**, en **Condiciones** no es necesario configurar ninguna opción para MFA.
9. En la sección **Controles de acceso**, elija **Conceder**.
10. En **Conceder**, seleccione **Conceder acceso** y, luego, **Requerir autenticación multifactor**. No seleccione **Requerir que el dispositivo esté marcado como compatible**, puesto que el cumplimiento normativo de un dispositivo no puede evaluarse hasta que esté inscrito. Luego, elija **Seleccionar**.
11. En **Directiva nueva**, elija **Habilitar directiva** > **Activado** y después elija **Crear**.



## <a name="next-steps"></a>Pasos siguientes

Cuando los usuarios finales inscriban sus dispositivos, deberán autenticarse con un segundo método de identificación, como un PIN, un teléfono o datos biométricos.
