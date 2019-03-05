---
title: Habilitar la conformidad de Google Play Protect con Microsoft Intune
titleSuffix: ''
description: Obtenga información sobre cómo crear una directiva de cumplimiento para dispositivos Android, a fin de habilitar Google Play Protect.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: E9810BEB-000A-4DFB-B5C7-A22A92082B22
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6c92115b3e5b5c0f13f60b7483905fef2f73c637
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2019
ms.locfileid: "57230676"
---
# <a name="how-to-create-a-device-compliance-policy-to-enable-google-play-protect"></a>Creación de una directiva de cumplimiento de dispositivos para habilitar Google Play Protect

Puede crear una directiva de cumplimiento para que la plataforma Android pueda comprobar la conformidad con Google Play Protect (GPP).

La directiva de cumplimiento que requiere esta configuración se puede destinar después de un grupo de usuarios o dispositivos Android. Si un dispositivo no tiene esta configuración habilitada, significa que no cumple los requisitos de conformidad.

## <a name="create-a-compliance-policy"></a>Crear una directiva de cumplimiento

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
2. Elija **Conformidad de dispositivos** en el grupo **Administrar**. 
3. Elija **Directivas** y haga clic en **Crear directiva**.
4. Escriba el **nombre** y la **descripción** de la directiva.
5. Seleccione **Android** como plataforma.
6. Elija **Configuración** > **Estado de dispositivos**.
7. Configure **Google Play Protect**.
8. Una vez configurado los valores de Google Play Protect, especifique los ajustes **Seguridad del sistema** y **Propiedades de dispositivo**. Cuando termine, elija **Aceptar**.

## <a name="configure-the-google-play-protect-settings"></a>Configuración de Google Play Protect

 - **Google Play Services está configurado**  
   Se requiere que la aplicación Google Play Services esté instalada y habilitada. Google Play Services permite actualizaciones de seguridad y es una dependencia de nivel base para muchas características de seguridad en los dispositivos de Google certificados.
 - **Proveedor de seguridad actualizada**  
   Se requiere que un proveedor de seguridad actualizado pueda proteger un dispositivo frente a vulnerabilidades conocidas.
 - **Examen de amenazas en las aplicaciones**  
   Se requiere que la característica **Verificar aplicaciones** de Android esté habilitada.
    > [!Note]  
    > En la plataforma Android heredada, esta característica es una configuración de cumplimiento. Intune solo puede comprobar si esta configuración está habilitada en el nivel de dispositivo. En los dispositivos con perfiles de trabajo Android, esta configuración puede encontrarse como un ajuste de la directiva de configuración. Esto permite a los administradores habilitar la configuración para un dispositivo.

    Si su empresa utiliza perfiles de trabajo Android, puede habilitar **Examen de amenazas en las aplicaciones** en los dispositivos inscritos. Establezca un perfil de dispositivo y requiera la configuración de seguridad del sistema. Para obtener más información, consulte [Configuración de las restricciones de dispositivos de perfil de trabajo Android en Microsoft Intune](device-restrictions-android-for-work.md).

 - **Atestación de dispositivo SafetyNet**  
   Defina el nivel de integridad de atestación de dispositivo SafetyNet que se debe cumplir. Los niveles incluyen **No configurado**, **Comprobar integridad básica** y **Comprobar integridad básica y dispositivos certificados**.




## <a name="next-steps"></a>Pasos siguientes

Para más información sobre cómo trabajar con las directivas de cumplimiento de dispositivos de Intune, consulte la [Introducción a las directivas de cumplimiento de dispositivos de Intune](device-compliance-get-started.md).
