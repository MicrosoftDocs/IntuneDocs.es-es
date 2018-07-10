---
title: Introducción a las directivas en Microsoft Intune - Azure | Microsoft Docs
description: Cree directivas para ayudar a proteger los datos corporativos y administrar los dispositivos que utilizan los usuarios finales para acceder a recursos de la empresa. Después, asigne las directivas a grupos.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d7fa1b596a1800971919cfc0ab3e94d2d16ec328
ms.sourcegitcommit: afda8a0fc0f615e976b18ddddf81d56d7ae3566e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/20/2018
ms.locfileid: "36271531"
---
# <a name="get-started-with-creating-policies"></a>Introducción a la creación de directivas

Las directivas de Intune son una excelente manera de inscribir dispositivos y garantizar que cumplen con las directivas corporativas. Las directivas de cumplimiento le ayudan a administrar tipos de dispositivo especializados, como los quioscos propiedad de la empresa, y dispositivos sin usuario, tabletas y dispositivos personales (Bring Your Own).

![Panel de cumplimiento con pocos datos](/intune/media/generic-compliance-dashboard.png)

Los dispositivos móviles se pueden administrar con directivas de cumplimiento, incluido:

* Regular el número de dispositivos que un usuario inscribe en Intune
* Administrar la configuración del dispositivo, como el cifrado de nivel de dispositivo, la longitud de la contraseña y el uso de la cámara
* Entregar aplicaciones, perfiles de correo electrónico y perfiles de VPN, y mucho más
* Evaluar los criterios de nivel de dispositivo para las directivas de cumplimiento de seguridad

Las directivas de cumplimiento se crean para cada plataforma, como iOS, Android, Windows y mucho más. Para este ejercicio, use iOS. Están disponibles las siguientes directivas para los dispositivos iOS:

* Configuración de contraseña o PIN
* Cifrado del dispositivo
* Dispositivo con Jailbreak
* Perfil de correo electrónico
* Versión de SO mínima
* Versión de SO máxima

## <a name="create-a-policy"></a>Crear una directiva

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Cumplimiento de dispositivos** > **Directivas** > **Crear directiva**.
4. Escriba un **nombre** y una **descripción** de directiva. 
5. Para la opción **Plataforma**, seleccione **iOS**.
6. En **Configuración**, seleccione **Seguridad del sistema** y después establezca **Requerir una contraseña para desbloquear dispositivos móviles** en **Requerir**. 

    También puede establecer otras reglas, como: 
    - **Longitud mínima de contraseña**
    - **Tipo de contraseña obligatoria**
    - **Número de caracteres no alfanuméricos en la contraseña**
    
    Cuando haya terminado de configurar su directiva, seleccione **Aceptar**.
  
7. Vuelva a **Crear directiva** y seleccione **Crear**. Este paso crea la directiva e incluye la directiva en **Cumplimiento del dispositivo** > **Directivas**.
8. Seleccione la directiva nueva y luego **Asignaciones**. Puede incluir o excluir grupos de seguridad de Azure Active Directory (AD).
Elija Grupos seleccionados para ver los grupos de seguridad de Azure AD existentes. Seleccione los grupos de usuarios a los que quiera aplicar esta directiva y elija **Guardar** para implementar la directiva a los usuarios.

Para ser compatible con la nueva directiva corporativa, tras unos minutos el dispositivo inscrito pide una contraseña actualizada. También puede buscar manualmente la actualización en la **aplicación de Portal de empresa para iOS**. Abra la aplicación de Portal de empresa, seleccione el nombre del dispositivo y, después, seleccione **Sincronizar**.

> [!NOTE]
> Las nuevas directivas aplicadas a un grupo dinámico de dispositivos pueden tardar hasta ocho horas en aplicarse a todos los dispositivos del grupo.

## <a name="next-steps"></a>Pasos siguientes

[Introducción a la inscripción de dispositivos](get-started-enroll.md): obtenga información sobre la inscripción mediante esta experiencia de inscripción completa para un dispositivo iOS.

## <a name="learn-more"></a>Obtener más información

* [Supervisión de las directivas de cumplimiento de dispositivos de Intune](compliance-policy-monitor.md)
* [Formas habituales de usar directivas de acceso condicional con Intune](conditional-access-intune-common-ways-use.md)
