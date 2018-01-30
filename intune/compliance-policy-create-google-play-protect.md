---
title: Habilitar la conformidad de Google Play Protect con Intune
titleSuffix: Azure portal
description: "Obtenga información sobre cómo crear una directiva de cumplimiento para dispositivos Android, a fin de habilitar Google Play Protect."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: E9810BEB-000A-4DFB-B5C7-A22A92082B22
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 13aa627515b74d3c9fe6d091c44dd5147bd786bd
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-create-a-device-compliance-policy-to-enable-google-play-protect"></a>Creación de una directiva de cumplimiento de dispositivos para habilitar Google Play Protect

Puede crear una directiva de cumplimiento para que la plataforma Android pueda comprobar la conformidad con Google Play Protect (GPP).

La directiva de cumplimiento que requiere esta configuración se puede destinar después de un grupo de usuarios o dispositivos Android. Si un dispositivo no tiene esta configuración habilitada, significa que no cumple los requisitos de conformidad.

## <a name="create-a-compliance-policy"></a>Crear una directiva de cumplimiento

1. Inicie sesión en Azure Portal. Elija **More Services** >  (Más servicios) **Supervisión y administración** + **Intune**.
2. Elija **Conformidad de dispositivos** en el grupo **Administrar**. 
3. Elija **Directivas** y después **Crear directiva**.
4. Escriba el **nombre** y la **descripción** de la directiva.
5. Seleccione **Android** como plataforma.
6. Elija **Configuración** > **Estado de dispositivos**.
7. Configure **Google Play Protect**.
8. Una vez configurado Google Play Protect, especifique los ajustes **Seguridad** y **Propiedad de dispositivo**. Cuando termine, elija **Aceptar**.

## <a name="configure-the-google-play-protect-settings"></a>Configuración de Google Play Protect

 - **Google Play Services está configurado**  
   Se requiere que la aplicación Google Play Services esté instalada y habilitada. Google Play Services permite actualizaciones de seguridad y es una dependencia de nivel base para muchas características de seguridad en los dispositivos de Google certificados.
 - **Proveedor de seguridad actualizada**  
   Se requiere que un proveedor de seguridad actualizado pueda proteger un dispositivo frente a vulnerabilidades conocidas.
 - **Examen de amenazas en las aplicaciones**  
   Se requiere que la característica **Verificar aplicaciones** de Android esté habilitada.
    > [!Note]  
    > En la plataforma Android heredada, esta característica es una configuración de cumplimiento. Intune solo puede comprobar si esta configuración está habilitada en el nivel de dispositivo. En los dispositivos con perfiles de trabajo, anteriormente Android for Work, esta configuración puede encontrarse como un ajuste de la directiva de configuración. Esto permite a los administradores habilitar la configuración para un dispositivo.

    Si su empresa utiliza perfiles de trabajo Android, puede habilitar **Examen de amenazas en las aplicaciones** en los dispositivos inscritos. Establezca un perfil de dispositivo y requiera la configuración de seguridad del sistema. Para más información, consulte [Configuración de restricciones de dispositivos Android for Work en Microsoft Intune](device-restrictions-android-for-work.md).

 - **Atestación de dispositivo SafetyNet**  
   Defina el nivel de integridad de atestación de dispositivo SafetyNet que se debe cumplir. Los niveles incluyen **No configurado**, **Comprobar integridad básica** y **Comprobar integridad básica y dispositivos certificados**.




## <a name="next-steps"></a>Pasos siguientes

Para más información sobre cómo trabajar con las directivas de cumplimiento de dispositivos de Intune, consulte la [Introducción a las directivas de cumplimiento de dispositivos de Intune](device-compliance-get-started.md).