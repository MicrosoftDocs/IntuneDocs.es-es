---
title: Configurar una página de estado de inscripción
titleSuffix: Microsoft Intune
description: Configure una página de saludo para los usuarios que inscriban dispositivos Windows 10.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: f01009a0cb35f4270bdb1e768ee781172c8bfa2f
ms.sourcegitcommit: 17f58d35a6bdff3e179662f3731fc74d39144470
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/28/2019
ms.locfileid: "55105194"
---
# <a name="set-up-an-enrollment-status-page"></a>Configurar una página de estado de inscripción
 
[!INCLUDE [azure_portal](./includes/azure_portal.md)]
 
Durante la configuración del dispositivo mediante Intune, la página Estado de inscripción muestra información sobre la instalación en el dispositivo. Es posible que algunas aplicaciones, perfiles y certificados no estén instalados cuando un usuario complete el proceso de inscripción rápida e inicie sesión en el dispositivo. Una página de estado de inscripción permite que los usuarios comprendan el estado de su dispositivo durante la instalación del dispositivo. Puede crear varios perfiles de la página de estado de inscripción y aplicarlos a diferentes grupos. Los perfiles se pueden establecer en:
- Mostrar progreso de la instalación.
- Bloquear el uso hasta que finalice la instalación.
- Especificar lo que puede hacer un usuario si se produce un error en la configuración del dispositivo.

También puede establecer el orden de prioridad para cada perfil para tener en cuenta las asignaciones de perfil en conflicto con el mismo usuario o dispositivo.

 
## <a name="turn-on-default-enrollment-status-page-for-all-users"></a>Activar la página de estado de inscripción predeterminada para todos los usuarios

Para activar la página de estado de inscripción, siga estos pasos.
 
1. En [Intune](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Página de estado de inscripción (vista previa)**.
2. En la hoja **Página de estado de inscripción**, elija **Predeterminado** > **Configuración**.
3. Para **Show app and profile installation progress** (Mostrar progreso de instalación de la aplicación y el perfil), elija **Sí**.
4. Elija las demás opciones de configuración que desee activar y seleccione **Guardar**.

## <a name="create-enrollment-status-page-profile-and-assign-to-a-group"></a>Creación de un perfil de página de estado de inscripción y asignación a un grupo

1. En [Intune](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Página de estado de la inscripción (versión preliminar)** > **Crear perfil**.
2. Proporcione un **Nombre** y una **Descripción**.
3. Elija **Crear**.
4. Elija el nuevo perfil en la lista **Página de estado de inscripción**.
5. Elija **Asignaciones** > **Seleccionar grupos** > elija los grupos que quiera que adopten este perfil > **Seleccionar** > **Guardar**.
6. Elija **Configuración** > elija la configuración que quiera aplicar a este perfil > **Guardar**.

## <a name="set-the-enrollment-status-page-priority"></a>Establecimiento de la prioridad de la página de estado de inscripción

Un dispositivo o un usuario podrían estar en varios grupos y tener varios perfiles de página de estado de inscripción. Para resolver estos conflictos, puede establecer las prioridades para cada perfil. Si alguien tiene más de un perfil de página de estado de inscripción, se aplicará solamente el perfil con la prioridad más alta.

1. En [Intune](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Página de estado de inscripción (vista previa)**.
2. Mantenga el mouse sobre el perfil en la lista.
3. Use los tres puntos verticales para arrastrar el perfil a la posición que quiera en la lista.

## <a name="block-access-to-a-device-until-a-specific-application-is-installed"></a>Bloqueo del acceso a un dispositivo a menos que haya instalada una aplicación específica

Puede especificar qué aplicaciones deben estar instaladas antes de que el usuario pueda acceder al escritorio.

1. En Intune, elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Página de estado de inscripción (vista previa)**.
2. Elija un perfil > **Configuración**.
3. Elija **Sí** en **Show app and profile installation progress** (Mostrar progreso de instalación de la aplicación y el perfil).
4. Elija **Sí** en **Block device use until all apps and profiles are installed** (Bloquear dispositivo hasta que todas estas aplicaciones y perfiles estén instalados).
5. Elija **Seleccionado** en **Block device use until these required apps are installed if they are assigned to the user/device** (Bloquear dispositivo hasta que las aplicaciones necesarias estén instaladas si están asignadas al usuario o dispositivo).
 6. Elija **Seleccionar aplicaciones** > elija las aplicaciones > **Seleccionar** > **Guardar**.

## <a name="enrollment-status-page-tracking-information"></a>Información de seguimiento de la página de estado de inscripción

La página de estado realiza un seguimiento de la información sobre la preparación del dispositivo, la configuración del dispositivo y la configuración de la cuenta.

### <a name="device-preparation"></a>Preparación del dispositivo

Para la preparación del dispositivo, la página de estado de inscripción realiza un seguimiento de las atestaciones de las claves del Módulo de plataforma segura (TPM) (cuando proceda), el progreso de la unión con Azure Active Directory y la inscripción en Intune.

### <a name="device-setup"></a>Configuración del dispositivo

Para la configuración del dispositivo, la página de estado de inscripción realiza un seguimiento de estos elementos si están asignados a todos los dispositivos:
- Directivas de seguridad
    - Un proveedor de servicios de configuración (CSP) para todas las inscripciones.
    - El seguimiento de los CSP reales configurados por Intune no se realiza aquí.
- Aplicaciones
    - Aplicaciones MSI de línea de negocio (LoB) por equipo.
    - Aplicaciones de almacén de LoB con contexto de instalación = Dispositivo.
    - Aplicaciones de almacén de LoB y almacén sin conexión con contexto de instalación = Dispositivo.
- Perfiles de conectividad
    - Perfiles de Wi-Fi o VPN que están asignados a **Todos los dispositivos** o a un grupo de dispositivos en el que el dispositivo de inscripción es un miembro, pero solo para dispositivos Autopilot
- Perfiles de certificado que están asignados a **Todos los dispositivos** o a un grupo de dispositivos en el que el dispositivo de inscripción es un miembro, pero solo para dispositivos Autopilot

### <a name="account-setup"></a>Configuración de la cuenta
Para la configuración de la cuenta, la página de estado de inscripción realiza el seguimiento de los siguientes elementos:
- Directivas de seguridad
    - Un CSP para todas las inscripciones.
    - El seguimiento de los CSP reales configurados por Intune no se realiza aquí.
- Aplicaciones
    - Aplicaciones de MSI de LoB por usuario que están asignadas a todos los dispositivos, a todos los usuarios a un grupo de usuarios del que es miembro el usuario que está inscribiendo el dispositivo.
    - Aplicaciones de MSI de LoB por equipo que están asignadas a todos los usuarios o a un grupo de usuarios del que es miembro el usuario que está inscribiendo el dispositivo.
    - Aplicaciones LoB de la tienda, aplicaciones de la tienda en línea y aplicaciones de la tienda sin conexión que se asignan a cualquiera de los siguientes:
        - Todos los dispositivos
        - Todos los usuarios
        - Un grupo de usuarios en el que el usuario que inscribe el dispositivo es un miembro con el contexto de instalación establecido en Usuario.
- Perfiles de conectividad
    - Perfiles de VPN o Wi-Fi que están asignados a todos los usuarios o a un grupo de usuarios del que es miembro el usuario que está inscribiendo el dispositivo.
- Certificados
    - Perfiles de certificado que están asignados a todos los usuarios o a un grupo de usuarios del que es miembro el usuario que está inscribiendo el dispositivo.

## <a name="next-steps"></a>Pasos siguientes
Tras configurar las páginas de inscripción de Windows, descubra cómo administrar dispositivos Windows. Para obtener más información, consulte [¿Qué es la administración de dispositivos de Microsoft Intune?](https://docs.microsoft.com/intune/device-management)
