---
title: Configurar una página de estado de inscripción
titleSuffix: Microsoft Intune
description: Dé la bienvenida a los usuarios que inscriben dispositivos Windows 10.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/17/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c6604c35cebdad4341f27a51db1a4c735f9a9818
ms.sourcegitcommit: 6bd5867c41fb5288fde114dbfcc127dd206f7148
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="set-up-an-enrollment-status-page"></a>Configurar una página de estado de inscripción
 
[!INCLUDE [azure_portal](./includes/azure_portal.md)]
 
Durante la configuración del dispositivo, la página de estado de inscripción muestra información sobre el estado de instalación en el dispositivo del usuario final. Algunas aplicaciones, perfiles y certificados podrían no estar completamente instalados en el momento en el que se inscribe un usuario. La página de estado puede ayudar a los usuarios a comprender el estado de su dispositivo durante y después de la inscripción. Puede activar la página de estado para todos los usuarios, así como impedir que los usuarios utilicen el dispositivo hasta que no se hayan instalado todas las aplicaciones y los perfiles asignados.
 
Para activar la página de estado de inscripción para todos los usuarios finales, siga estos pasos.
 
1.  En [Intune](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Página de estado de inscripción (vista previa)**.
2.  En la hoja **Página de estado de inscripción**, elija **Predeterminado** > **Configuración**.
3.  Para **Show app and profile installation progress** (Mostrar progreso de instalación de la aplicación y el perfil), elija **Sí**.
4.  Elija las demás opciones de configuración que desee activar y seleccione **Guardar**.
 
## <a name="enrollment-status-page-tracking-information"></a>Información de seguimiento de la página de estado de inscripción

La página de estado realiza un seguimiento de la información sobre la preparación del dispositivo, la configuración del dispositivo y la configuración de la cuenta.

### <a name="device-preparation"></a>Preparación del dispositivo

Para la preparación del dispositivo, la página de estado de inscripción realiza un seguimiento de las atestaciones de las claves del Módulo de plataforma segura (TPM) (cuando proceda), el progreso de la unión con Azure Active Directory y la inscripción en Intune.

### <a name="device-setup"></a>Configuración del dispositivo

Para la configuración del dispositivo, la página de estado de inscripción realiza un seguimiento de los siguientes elementos si están asignados a todos los dispositivos:
- Directivas de seguridad
    - Un proveedor de servicios de configuración (CSP) para todas las inscripciones.
    - El seguimiento de los CSP reales configurados por Intune no se realiza aquí.
- Aplicaciones
    - Aplicaciones MSI de línea de negocio (LoB) por equipo.
    - Aplicaciones de almacén de LoB con contexto de instalación = Dispositivo.
    - Aplicaciones de almacén de LoB y almacén sin conexión con contexto de instalación = Dispositivo.
- Aún no se realiza un seguimiento de los perfiles de conectividad (VPN y Wi-Fi), por lo que siempre aparecerá "0 de 0".
- Aún no se realiza un seguimiento de los certificados, por lo que siempre aparecerá "0 de 0".

### <a name="account-setup"></a>Configuración de la cuenta
Para la configuración de la cuenta, la página de estado de inscripción realiza el seguimiento de los siguientes elementos:
- Directivas de seguridad
    - Un CSP para todas las inscripciones.
    - El seguimiento de los CSP reales configurados por Intune no se realiza aquí.
- Aplicaciones
    - Aplicaciones de MSI de LoB por usuario que están asignadas a todos los dispositivos, a todos los usuarios a un grupo de usuarios del que es miembro el usuario que está inscribiendo el dispositivo.
    - Aplicaciones de MSI de LoB por equipo que están asignadas a todos los usuarios o a un grupo de usuarios del que es miembro el usuario que está inscribiendo el dispositivo.
    - Aplicaciones de almacén de LoB que están asignadas a todos los dispositivos, a todos los usuarios o a un grupo de usuarios del que es miembro el usuario que está inscribiendo el dispositivo con contexto de instalación = Usuario.
    - Aplicaciones de tienda en línea que están asignadas a todos los dispositivos, a todos los usuarios o a un grupo de usuarios del que es miembro el usuario que está inscribiendo el dispositivo con contexto de instalación = Usuario.
    - Aplicaciones de almacén sin conexión que están asignadas a todos los dispositivos, a todos los usuarios o a un grupo de usuarios del que es miembro el usuario que está inscribiendo el dispositivo con contexto de instalación = Usuario.
- Perfiles de conectividad
    - Perfiles de VPN o Wi-Fi que están asignados a todos los usuarios o a un grupo de usuarios del que es miembro el usuario que está inscribiendo el dispositivo.
- Certificados
    - Perfiles de certificado que están asignados a todos los usuarios o a un grupo de usuarios del que es miembro el usuario que está inscribiendo el dispositivo.

## <a name="next-steps"></a>Pasos siguientes
Tras configurar las páginas de inscripción de Windows, descubra cómo administrar dispositivos Windows. Para obtener más información, consulte [¿Qué es la administración de dispositivos de Microsoft Intune?](https://docs.microsoft.com/intune/device-management)