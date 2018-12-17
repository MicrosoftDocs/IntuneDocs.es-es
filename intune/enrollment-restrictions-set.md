---
title: Establecer restricciones de inscripción en Microsoft Intune
titlesuffix: ''
description: Restrinja las inscripciones por plataforma y establezca un límite de inscripciones de dispositivos en Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: e6f816ae0eb025addfaa0c5f7ec7d16005f6b040
ms.sourcegitcommit: 5058dbfb0e224207dd4e7ca49712c6ad3434c83c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112959"
---
# <a name="set-enrollment-restrictions"></a>Establecer restricciones de inscripción

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Como administrador de Intune, puede crear y administrar las restricciones de inscripción que definen el número y los tipos de dispositivos que se pueden inscribir en la administración con Intune. Puede crear varias restricciones y aplicarlas a diferentes grupos de usuarios. Puede establecer el [orden de prioridad](#change-enrollment-restriction-priority) para las distintas restricciones.

>[!NOTE]
>Las restricciones de inscripción no son características de seguridad. Los dispositivos en peligro pueden falsificar su carácter. Estas restricciones son un obstáculo al mejor esfuerzo para los usuarios no malintencionados.

Las restricciones de inscripción específicas que se pueden crear son:

- Número máximo de dispositivos inscritos.
- Plataformas de dispositivo que se pueden inscribir:
  - Android
  - Perfil de trabajo Android
  - iOS
  - macOS
  - Windows
- Versión del sistema operativo de la plataforma para iOS, Android, perfil de trabajo Android y Windows (solo se pueden usar las versiones de Windows 10; déjelo en blanco si se admite Windows 8.1).
  - Versión mínima.
  - Versión máxima.
- Restricción de los dispositivos de propiedad personal (solo iOS, Android, perfil de trabajo Android, macOS y Windows).

## <a name="default-restrictions"></a>Restricciones predeterminadas

Las restricciones predeterminadas se proporcionan automáticamente para las restricciones de inscripción de tipo de dispositivo y límite de dispositivo. Puede cambiar las opciones para los valores predeterminados. Las restricciones predeterminadas se aplican a todos los usuarios e inscripciones sin usuario. Puede invalidar estos valores predeterminados mediante la creación de nuevas restricciones con prioridades más altas.

## <a name="create-a-restriction"></a>Crear una restricción

1. Inicie sesión en Azure Portal.
2. Seleccione **Más servicios**, busque **Intune** y, después, seleccione **Intune**.
3. Seleccione **Inscripción de dispositivos** > **Restricciones de inscripción**.
4. Seleccione **Crear restricción**.
5. Asigne un nombre y una descripción a la restricción.
6. Elija un **tipo de restricción** y, después, seleccione **Crear**.
7. Para las restricciones de límite de dispositivo, seleccione **Límite de dispositivos** para establecer el número máximo de dispositivos que puede inscribir un usuario.
8. Para las restricciones de tipo de dispositivo, seleccione **Plataformas** y **Configuraciones de plataforma** para permitir o bloquear varias versiones y plataformas.
9. Seleccione **Asignaciones** > **+ Seleccionar grupos**.
10. En **Seleccionar grupos**, seleccione uno o más grupos y, después, elija **Seleccionar**. La restricción se aplica únicamente a los grupos a los que está asignada. Si no asigna una restricción al menos a un grupo, no tendrá ningún efecto.
11. Seleccione **Guardar**.
12. La nueva restricción se crea con una prioridad justo por encima del valor predeterminado. También puede [cambiar la prioridad](#change-enrollment-restriction-priority).

## <a name="set-device-type-restrictions"></a>Establecer restricciones de tipo de dispositivo

Puede cambiar la configuración de una restricción de tipo de dispositivo mediante los pasos siguientes. Estas restricciones no afectan a los dispositivos que ya se han inscrito. Los dispositivos inscritos con el [agente de PC de Intune](manage-windows-pcs-with-microsoft-intune.md) no se puede bloquear con esta característica.

1. Inicie sesión en Azure Portal.
2. Seleccione **Más servicios**, busque **Intune** y, después, seleccione **Intune**.
3. Seleccione **Inscripción de dispositivos** > **Restricciones de inscripción**.
4. En **Restricciones de tipo de dispositivo** > elija la restricción que quiera establecer > **Propiedades** > **Seleccionar plataformas**. Pulse **Permitir** o **Bloquear** para cada plataforma de la lista.
    ![Captura de pantalla para permitir o bloquear una plataforma](media/enrollment-restrictions-set/platform-allow-block.png)
5. Elija **Aceptar**.
6. Elija **Configurar plataformas**.
    ![Captura de pantalla para configurar plataformas](media/enrollment-restrictions-set/configure-platforms.png)
7. Seleccione las **versiones** mínima y máxima de las plataformas enumeradas. Entre los formatos de las versiones admitidas se incluyen los siguientes:
    - El perfil de trabajo Android admite major.minor.rev.build.
    - iOS admite major.minor.rev. Las versiones de sistema operativo no son relevantes en dispositivos Apple que se inscriban en el Programa de inscripción de dispositivos, Apple School Manager ni la aplicación Apple Configurator.
    - Windows admite major.minor.rev.build únicamente para Windows 10.
8. Elija si quiere **Permitir** o **Bloquear** los dispositivos de **propiedad personal** para las plataformas de la lista.
9. Elija **Aceptar**.

### <a name="blocking-personal-android-devices"></a>Bloquear dispositivos Android personales
- Si bloquea los dispositivos Android de propiedad personal de la inscripción, los dispositivos de perfil de trabajo Android de propiedad personal todavía pueden inscribirse.
- De forma predeterminada, la configuración de los dispositivos de perfil de trabajo Android es igual que la configuración de los dispositivos Android. Dejará de ser así después de modificar la configuración del perfil de trabajo Android.
- Si bloquea la inscripción del perfil de trabajo Android personal, tan solo los dispositivos Android corporativos podrán inscribirse como perfil de trabajo Android.

### <a name="blocking-personal-windows-devices"></a>Bloquear dispositivos Windows personales
Si impide la inscripción de dispositivos Windows de uso personal, Intune realiza comprobaciones para asegurarse de que se ha autorizado cada nueva solicitud de inscripción de Windows como una inscripción corporativa. Las inscripciones no autorizadas se bloquearán.

Los métodos siguientes se consideran como autorizados como una inscripción corporativa de Windows:
 - El usuario que se inscribe usa una [cuenta de administrador de inscripción de dispositivos]( device-enrollment-manager-enroll.md).
- El dispositivo se inscribe a través de [Windows AutoPilot](enrollment-autopilot.md).
- El dispositivo está registrado con Windows Autopilot, pero no es la única opción de inscripción de MDM que encontrará en la configuración de Windows.
- El número IMEI del dispositivo aparece en **Inscripción del dispositivo** > **[Identificadores de dispositivo corporativos](corporate-identifiers-add.md)**. (No se admite para Windows Phone 8.1).
- El dispositivo se inscribe a través de un [paquete de aprovisionamiento en masa](windows-bulk-enroll.md).
- El dispositivo se inscribe a través de la [inscripción automática de SCCM para la administración conjunta](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview#how-to-configure-co-management.md).
 
Intune marca las inscripciones siguientes como corporativas, pero dado que no ofrecen control por dispositivo del administrador de Intune, se bloquearán:
 - [Inscripción automática de MDM](windows-enroll.md#enable-windows-10-automatic-enrollment) con [combinación de Azure Active Directory durante la instalación de Windows](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx)\*.
- [Inscripción automática de MDM](windows-enroll.md#enable-windows-10-automatic-enrollment) con [combinación de Azure Active Directory desde la instalación de Windows](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)*.
 
También se bloquearán los siguientes métodos de inscripción personal:
- [Inscripción automática de MDM](windows-enroll.md#enable-windows-10-automatic-enrollment) con [incorporación de cuenta profesional desde la instalación de Windows](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network)\*.
- Opción de [solo inscripción de MDM]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device) desde la instalación de Windows.

\* Estos no se bloquearán si se han registrado con Autopilot.

## <a name="set-device-limit-restrictions"></a>Establecer restricciones de límite de dispositivos

Para cambiar la configuración de una restricción de límite de dispositivos, siga estos pasos:

1. Inicie sesión en Azure Portal.
2. Seleccione **Más servicios**, busque **Intune** y, después, seleccione **Intune**.
3. Seleccione **Inscripción de dispositivos** > **Restricciones de inscripción**.
4. En **Restricciones de límite de dispositivo**, elija la restricción que quiera establecer.
5. Seleccione **Límite de dispositivos** y, después, en la lista desplegable, seleccione el número máximo de dispositivos que puede inscribir un usuario.
    ![Hoja de restricciones de límite de dispositivos con las restricciones de límite de dispositivos](./media/device-restrictions-limit.png)
6. Seleccione **Guardar**.


Durante las inscripciones de BYOD, los usuarios recibirán una notificación en la que se les informará cuando hayan alcanzado el límite de dispositivos inscritos. Por ejemplo, en iOS, tiene un aspecto similar al siguiente:

![Notificación del límite en un dispositivo iOS](./media/enrollment-restrictions-ios-set-limit-notification.png)

## <a name="change-enrollment-restriction-priority"></a>Cambiar la prioridad de las restricciones de inscripción

La prioridad se usa cuando un usuario existe en varios grupos a los que se asignan restricciones. Los usuarios solo están sujetos a la restricción de prioridad más alta asignada a un grupo al que pertenecen. Por ejemplo, Juan está en el grupo A asignado a restricciones de prioridad 5, así como en el grupo B asignado a restricciones de prioridad 2. Juan solo está sujeto a las restricciones de prioridad 2.

Cuando se crea una restricción, se agrega a la lista justo encima de la predeterminada.

La inscripción de dispositivos incluye restricciones predeterminadas para el tipo y límite de dispositivo. Estas dos restricciones se aplican a todos los usuarios a menos que se reemplacen por restricciones de prioridad más alta.

Puede cambiar la prioridad de cualquier restricción que no sea la predeterminada.

1. Inicie sesión en Azure Portal.
2. Seleccione **Más servicios**, busque **Intune** y, después, seleccione **Intune**.
3. Seleccione **Inscripción de dispositivos** > **Restricciones de inscripción**.
4. Mantenga el puntero sobre la restricción en la lista de prioridades.
5. Con los tres puntos verticales, arrastre la prioridad a la posición deseada en la lista.
