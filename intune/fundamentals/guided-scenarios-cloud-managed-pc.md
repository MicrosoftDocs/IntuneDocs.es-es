---
title: 'Escenario guiado: Escritorio moderno administrado en la nube'
titleSuffix: Microsoft Intune
description: Obtenga información sobre el escenario guiado para instalar y configurar un Escritorio moderno básico desde el portal de administración de dispositivos de Microsoft 365.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f78f3696827ebd50084f0e4b012c5f94427eeb35
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74164564"
---
# <a name="guided-scenario---cloud-managed-modern-desktop"></a>Escenario guiado: Escritorio moderno administrado en la nube

Escritorio moderno es la plataforma de productividad de vanguardia para el trabajador de la información. Offic 365 ProPlus y Windows 10 son los componentes principales de Escritorio moderno junto con las líneas de base de seguridad más recientes para Windows 10 y Protección contra amenazas avanzada de Microsoft Defender. 

La administración de Escritorio moderno desde la nube aporta la ventaja adicional de las acciones remotas en toda Internet. La administración en la nube emplea las directivas de Administración de dispositivos móviles integradas de Windows y quita las dependencias de la directiva de grupo de Active Directory local. 

Si quiere evaluar un escritorio moderno administrado en la nube en su propia organización, en este escenario guiado se predefinen todas las configuraciones necesarias para una implementación básica. En este escenario guiado, creará un entorno seguro en el que puede probar las funciones de administración de dispositivos de Intune. 

## <a name="prerequisites"></a>Requisitos previos
- [Establecer la entidad de MDM en Intune](~/fundamentals/mdm-authority-set.md#set-mdm-authority-to-intune): la configuración de la entidad de administración de dispositivos móviles (MDM) determina cómo se administran los dispositivos. Como administrador de TI, debe establecer una entidad de MDM antes de que los usuarios puedan inscribir dispositivos para la administración.
- M365 E3 como mínimo (o M365 E5 para mayor seguridad)
- Dispositivo Windows 10 1903 (registrado con Windows Autopilot para la experiencia óptima del usuario final)
- Permisos de administrador de Intune necesarios para completar este escenario guiado:
  - Configuración del dispositivo, Leer, Crear, Eliminar, Asignar y Actualizar
  - Programas de inscripción Leer dispositivo, Leer perfil, Crear perfil, Asignar perfil, Eliminar perfil
  - Aplicaciones móviles, Leer, Crear, Eliminar, Asignar y Actualizar
  - Organización Leer y Actualizar
  - Líneas de base de seguridad, Leer, Crear, Eliminar, Asignar y Actualizar
  - Conjuntos de directivas Leer, Crear, Eliminar, Asignar y Actualizar

## <a name="step-1---introduction"></a>Paso 1: Introducción

Con este escenario guiado, configurará un usuario de prueba, inscribirá un dispositivo en Intune y lo implementará con la configuración recomendada de Intune, así como con Windows 10 y Office ProPlus. El dispositivo también se configurará para Protección contra amenazas avanzada de Microsoft Defender, si elige [habilitar esta protección en Intune](~/protect/advanced-threat-protection.md#enable-microsoft-defender-atp-in-intune). El usuario que configure y el dispositivo que inscriba se agregarán a un nuevo grupo de seguridad y se configurarán con la configuración recomendada para la seguridad y la productividad. 

### <a name="what-you-will-need-to-continue"></a>Qué se necesita para continuar

En este escenario guiado debe proporcionar el dispositivo de prueba y el usuario de prueba. Asegúrese de completar las tareas siguientes:
- Configurar una cuenta de usuario de prueba en Azure Active Directory.
- Crear un dispositivo de prueba que ejecute Windows 10 versión, 1903 o posterior.
- (Opcional) [Registrar el dispositivo de prueba con Windows Autopilot](~/enrollment/enrollment-autopilot.md#add-devices).
- (Opcional) Habilitar la [personalización de marca en la página de inicio de sesión Azure Active Directory de la organización](https://go.microsoft.com/fwlink/?linkid=2102455).

## <a name="step-2---user"></a>Paso 2: Usuario

Elija un usuario para configurar en el dispositivo. Será el usuario primario del dispositivo.

Si quiere agregar más usuarios o dispositivos a esta configuración, simplemente agréguelos a los grupos de seguridad de AAD generados por el asistente. A diferencia de otros escenarios guiados, no es necesario ejecutar el asistente más de una vez, ya que la configuración no se puede personalizar. Simplemente agregue más usuarios y dispositivos a los grupos de AAD creados. Después de completar el asistente, podrá ver el grupo generado con las directivas recomendadas implementadas. 

## <a name="step-3---device"></a>Paso 3: Dispositivo

Asegúrese de que el dispositivo ejecuta Windows 10, versión 1903 o posterior.  El usuario principal tendrá que configurar el dispositivo cuando lo reciba. Hay dos opciones de configuración disponibles para el usuario. 

### <a name="option-a--windows-autopilot"></a>Opción A: Windows Autopilot
Windows Autopilot automatiza la configuración de dispositivos nuevos para que los usuarios puedan configurarlos de forma rápida, sin necesidad de ayuda de TI. Si el dispositivo ya está registrado en Windows Autopilot, selecciónelo por su número de serie. Para más información sobre el uso de Windows Autopilot, vea [Registro del dispositivo con Windows Autopilot (opcional)](~/fundamentals/guided-scenarios-cloud-managed-pc.md#register-device-with-windows-autopilot-optional).

### <a name="option-b--manual-device-enrollment"></a>Opción B: Inscripción manual de dispositivos
Los usuarios instalarán e inscribirán de forma manual los dispositivos nuevos en la administración de dispositivos móviles. Después de completar este escenario, restablezca el dispositivo y proporcione al usuario principal las instrucciones de inscripción para los dispositivos Windows. Para más información, vea [Unión de un dispositivo Windows 10 a Azure AD durante la experiencia de primera ejecución](https://docs.microsoft.com/azure/active-directory/devices/azuread-joined-devices-frx#joining-a-device).

## <a name="step-4---review--create"></a>Paso 4: Revisión y creación

El último paso permite revisar un resumen de los valores que ha configurado. Una vez que haya revisado las opciones, haga clic en **Implementar** para completar el escenario guiado. Una vez completado el escenario guiado, se mostrará una tabla de recursos. Puede editar estos recursos más adelante, pero una vez que salga de la vista de resumen, la tabla no se guardará.

> [!IMPORTANT]
> Cuando el escenario guiado se complete, se mostrará un resumen. Puede modificar los recursos enumerados en el resumen más adelante, pero la tabla en la que se muestran estos recursos no se guardará.

### <a name="verification"></a>Comprobación
1. Compruebe que al usuario seleccionado se le ha asignado el ámbito de usuario de MDM.
    - Asegúrese de que [Ámbito de usuario de MDM](~/enrollment/windows-enroll.md#enable-windows-10-automatic-enrollment) está:
        - Establecido en **Todo** para la aplicación **Microsoft Intune** o bien,
        - Establecido en **Algunos**. Además, agregue el grupo de usuarios creado por este escenario guiado.
2. Compruebe que el usuario seleccionado puede unir dispositivos a Azure Active Directory.
    - Asegúrese de que la unión a AAD está:
        - Establecida en **Todos** o bien,
        - Establecida en **Algunos**. Además, agregue el grupo de usuarios creado por este escenario guiado.
3. Siga los pasos adecuados en el dispositivo para unirlo a Azure AD en función de lo siguiente:
    - Con Autopilot. Para más información, vea [Modo controlado por el usuario de Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven).
    - Sin Autopilot: Para más información, vea [Unión de un dispositivo Windows 10 a Azure AD durante la experiencia de primera ejecución](https://docs.microsoft.com/azure/active-directory/devices/azuread-joined-devices-frx#joining-a-device).

### <a name="what-happens-when-i-click-deploy"></a>¿Qué ocurre cuando hago clic en Implementar?
El usuario y el dispositivo se agregarán a grupos de seguridad nuevos. También se configurarán con los valores recomendados por Intune para la seguridad y la productividad en el ámbito educativo o laboral. Después de que el usuario una el dispositivo a Azure AD, se agregarán más aplicaciones y configuraciones al dispositivo. Para obtener más información sobre estas configuraciones adicionales, vea [Inicio rápido: Inscripción de dispositivos Windows 10](~/enrollment/quickstart-enroll-windows-device.md).

## <a name="additional-information"></a>Información adicional

### <a name="register-device-with-windows-autopilot-optional"></a>Registro de dispositivos con Windows Autopilot (opcional)

Opcionalmente, puede optar por usar un dispositivo Autopilot registrado. Para Autopilot, este escenario guiado asignará un perfil de implementación de Autopilot y un perfil de página de estado de inscripción. El perfil de implementación de Autopilot se configurará de la siguiente manera:
- Modo controlado por el usuario: es decir, requerir que el usuario final escriba el nombre de usuario y la contraseña durante la configuración de Windows.
- Unión a Azure AD.
- Personalizar la configuración de Windows:
  - Ocultar la pantalla de términos de licencia de software de Microsoft
  - Ocultar la configuración de privacidad 
  - Crear el perfil local del usuario sin privilegios de administrador local
  - Ocultar las opciones de cambio de cuenta en la página de inicio de sesión corporativa

La página Estado de inscripción se configurará para que solo se habilite para dispositivos Autopilot y no se bloqueará mientras espera a que se instalen todas las aplicaciones.

El escenario guiado también asignará el usuario al dispositivo Autopilot seleccionado para una experiencia de instalación personalizada.

#### <a name="post-requisites"></a>Requisitos posteriores
Una vez que el usuario une el dispositivo a Azure Active Directory, se aplicarán las configuraciones siguientes al dispositivo:
1. Office 365 ProPlus se instalará de forma automática en el equipo administrado en la nube. Incluye las aplicaciones con las que está familiarizado, como Access, Excel, OneNote, Outlook, PowerPoint, Publisher, Skype Empresarial y Word. Puede usar estas aplicaciones para conectarse a servicios de Office 365, como SharePoint Online, Exchange Online y Skype Empresarial Online. Office 365 ProPlus se actualiza periódicamente con nuevas características, a diferencia de las versiones de Office que no son de suscripción. Para obtener una lista de las características nuevas, vea Novedades de Office 365.
2. Las líneas de base de seguridad de Windows se instalarán en el equipo administrado en la nube. Si ha configurado Protección contra amenazas avanzada de Microsoft Defender, el escenario guiado también configurará las opciones de línea de base de Defender. Protección contra amenazas avanzada de Microsoft Defender proporciona una nueva capa de protección posterior a la infracción en la pila de seguridad de Windows 10. Con una combinación de tecnología cliente integrada en Windows 10 y un sólido servicio en la nube, ayudará a detectar las amenazas que han superado otras medidas de defensa. 

## <a name="next-steps"></a>Pasos siguientes

- Si usa Protección contra amenazas avanzada de Microsoft Defender, cree una [directiva de cumplimiento de Intune](~/protect/advanced-threat-protection.md#create-and-assign-the-compliance-policy) para requerir que el análisis de amenazas de Defender satisfaga los requisitos de cumplimiento.
- Cree una [directiva de acceso condicional basada en dispositivos](~/protect/advanced-threat-protection.md#create-a-conditional-access-policy) para bloquear el acceso si el dispositivo no satisface los requisitos de cumplimiento de Intune.
