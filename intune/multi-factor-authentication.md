---
title: "Autenticación multifactor para la inscripciones de dispositivos de Intune"
titlesuffix: Azure portal
description: "Cómo requerir Multi-factor Authentication en Azure AD para la inscripción de dispositivos."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 94280c73-c05c-4e72-b0dd-a7cb997782f9
ROBOTS: 
ms.custom: intune-azure
ms.openlocfilehash: a3aabe77257fd7e6964dd7bd83035c8a491a58b4
ms.sourcegitcommit: 94d3d86f8ae9f82a9872384bbaae53580036a4ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2017
---
# <a name="multi-factor-authentication-for-intune-device-enrollments"></a>Autenticación multifactor para inscripciones de dispositivos de Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

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
>No configure **reglas de acceso basadas en dispositivos** para la inscripción a Microsoft Intune.

1. Inicie sesión en [Microsoft Azure Portal](https://portal.azure.com) con sus credenciales.
2. En el portal, elija **Azure Active Directory**.
2. En **Azure Active Directory**, seleccione **Administrar** > **Aplicaciones empresariales**.
3. En **Aplicaciones empresariales**, elija **Administrar** > **Todas las aplicaciones**. Verá una lista de todas las aplicaciones de Azure que administre.
3. En la lista, seleccione **Inscripción a Microsoft Intune**.
4. En **Inscripción a Microsoft Intune**, elija **Seguridad** > **Acceso condicional**.
5. Pulse **Nueva directiva**.
6. En **Directiva nueva**, escriba un nombre descriptivo para la directiva.
7. En la sección **Asignaciones**, seleccione **Usuarios y grupos**.
8. En **Usuarios y grupos**, elija los usuarios o los grupos a los que se aplicará esta directiva y, luego, seleccione **Listo**.
9. En la sección **Asignaciones**, elija **Aplicaciones en la nube**.
10. En la pestaña **Incluir** de **Aplicaciones en la nube**, elija **Seleccionar aplicaciones**, **Seleccionar** > **Inscripción a Microsoft Intune** y, luego, **Listo**.
11. En la sección **Asignaciones**, seleccione **Condiciones**.
12. En **Condiciones**, no es necesario configurar ninguna configuración para MFA.
13. En la sección **Controles de acceso**, elija **Conceder**.
14. En **Conceder**, seleccione **Conceder acceso** y, luego, **Requerir autenticación multifactor**.
    No seleccione **Requerir que el dispositivo esté marcado como compatible**, puesto que el cumplimiento normativo de un dispositivo no puede evaluarse hasta que esté inscrito.
15. Elija **Seleccionar**.
16. En **Directiva nueva**, elija **Habilitar directiva** > **Activado** y después elija **Crear**.



## <a name="next-steps"></a>Pasos siguientes

Cuando los usuarios finales inscriban sus dispositivos, deberán autenticarse con un segundo método de identificación, como un PIN, un teléfono o datos biométricos.
