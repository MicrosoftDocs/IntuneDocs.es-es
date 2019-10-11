---
title: Establecer restricciones de inscripción en Microsoft Intune
titleSuffix: ''
description: Restrinja las inscripciones por plataforma y establezca un límite de inscripciones de dispositivos en Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/17/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bdeb88f3a69db160dca61bf3038c5a7d0235f2b2
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722467"
---
# <a name="set-enrollment-restrictions"></a>Establecer restricciones de inscripción

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Como Administrador del servicio Intune, puede crear y administrar las restricciones de inscripción que definen los dispositivos que se pueden inscribir en la administración con Intune, que incluyen:
- Número de dispositivos
- Sistemas operativos y versiones. Puede crear varias restricciones y aplicarlas a diferentes grupos de usuarios. Puede establecer el [orden de prioridad](#change-enrollment-restriction-priority) para las distintas restricciones.

>[!NOTE]
>Las restricciones de inscripción no son características de seguridad. Los dispositivos en peligro pueden falsificar su carácter. Estas restricciones son un obstáculo al mejor esfuerzo para los usuarios no malintencionados.

Las restricciones de inscripción específicas que se pueden crear son:

- Número máximo de dispositivos inscritos.
- Plataformas de dispositivo que se pueden inscribir:
  - Administrador de dispositivos Android
  - Perfil de trabajo de Android Enterprise
  - iOS
  - macOS
  - Windows
  - Windows Mobile
- Versión del sistema operativo de la plataforma para iOS, el administrador de dispositivos Android, el perfil de trabajo de Android Enterprise, Windows y Windows Mobile. (solo se pueden usar las versiones de Windows 10; déjelo en blanco si se admite Windows 8.1).
  - Versión mínima.
  - Versión máxima.
- Restrinja los dispositivos de propiedad personal (solo iOS, del administrador de dispositivos Android, del perfil de trabajo de Android Enterprise, macOS, Windows y Windows Mobile).

## <a name="default-restrictions"></a>Restricciones predeterminadas

Las restricciones predeterminadas se proporcionan automáticamente para las restricciones de inscripción de tipo de dispositivo y límite de dispositivo. Puede cambiar las opciones para los valores predeterminados. Las restricciones predeterminadas se aplican a todos los usuarios e inscripciones sin usuario. Puede invalidar estos valores predeterminados mediante la creación de nuevas restricciones con prioridades más altas.

## <a name="create-a-device-type-restriction"></a>Creación de una restricción de tipo de dispositivo

1. Inicie sesión en Azure Portal.
2. Seleccione **Más servicios**, busque **Intune** y, después, seleccione **Intune**.
3. Seleccione **Inscripción de dispositivos** > **Restricciones de inscripción** > **Crear restricción** > **Restricción de tipo de dispositivo**.
    ![Captura de pantalla de la creación de una restricción de tipo de dispositivo](./media/enrollment-restrictions-set/create-device-type-restriction.png)
4. En la página **Datos básicos**, asigne un **Nombre** y, opcionalmente, una **descripción** a la restricción.
5. Elija **Siguiente** para ir a la página **Configuración de plataforma**.
6. En **Plataforma**, elija **Permitir** para las plataformas en las que quiera que esta restricción se permita.
    ![Captura de pantalla de la elección de configuración de plataforma](./media/enrollment-restrictions-set/choose-platform-settings.png)
7. En **Versiones**, elija las versiones mínima y máxima que quiera que admita la plataforma permitida. Las restricciones de versión solo se aplican a los dispositivos inscritos en el Portal de empresa.
     Entre los formatos de las versiones admitidas se incluyen los siguientes:
    - El administrador de dispositivos Android y el perfil de trabajo de Android Enterprise admiten major.minor.rev.build.
    - iOS admite major.minor.rev. Las versiones de sistema operativo no son relevantes en dispositivos Apple que se inscriban en el Programa de inscripción de dispositivos, Apple School Manager ni la aplicación Apple Configurator.
    - Windows admite major.minor.rev.build únicamente para Windows 10.
    > [!Note]
    > Windows 10 no proporciona el número de compilación durante la inscripción; por lo tanto, si, por ejemplo, escribe 10.0.17134.100 y el dispositivo coincide con 10.0.17134.174, durante la inscripción este se bloqueará.

8. En **Propiedad personal**, elija **Permitir** para las plataformas que quiera permitir como dispositivos de 	propiedad personal.
9. Elija **Siguiente** para ir a la página **Asignaciones**.
10. Elija **Seleccionar grupos para incluir** y luego use el cuadro de búsqueda para buscar los grupos que quiere incluir en esta restricción. La restricción se aplica únicamente a los grupos a los que está asignada. Si no asigna una restricción al menos a un grupo, no tendrá ningún efecto. Luego, elija **Seleccionar**. 
    ![Captura de pantalla de la elección de configuración de plataforma](./media/enrollment-restrictions-set/select-groups.png)
11. Elija **Siguiente** para ir a la página **Revisar y crear**.
12. Haga clic en **Crear** para crear la restricción.
13. La nueva restricción se crea con una prioridad justo por encima del valor predeterminado. También puede [cambiar la prioridad](#change-enrollment-restriction-priority).


## <a name="create-a-device-limit-restriction"></a>Creación de una restricción de límite de dispositivos

1. Inicie sesión en Azure Portal.
2. Seleccione **Más servicios**, busque **Intune** y, después, seleccione **Intune**.
3. Seleccione **Inscripción de dispositivos** > **Restricciones de inscripción** > **Crear restricción** > **Restricción de límite de dispositivos**.
    ![Captura de pantalla de la creación de una restricción de límite de dispositivos](./media/enrollment-restrictions-set/create-device-limit-restriction.png)
4. En la página **Datos básicos**, asigne un **Nombre** y, opcionalmente, una **descripción** a la restricción.
5. Elija **Siguiente** para ir a la página **Límite de dispositivo**.
6. Como **Límite de dispositivo**, seleccione el número máximo de dispositivos que un usuario puede inscribir.
    ![Captura de pantalla de la elección de límite de dispositivo](./media/enrollment-restrictions-set/choose-device-limit.png)
7. Elija **Siguiente** para ir a la página **Asignaciones**.
8. Elija **Seleccionar grupos para incluir** y luego use el cuadro de búsqueda para buscar los grupos que quiere incluir en esta restricción. La restricción se aplica únicamente a los grupos a los que está asignada. Si no asigna una restricción al menos a un grupo, no tendrá ningún efecto. Luego, elija **Seleccionar**. 
    ![Captura de pantalla de selección de grupos](./media/enrollment-restrictions-set/select-groups-device-limit.png)
11. Elija **Siguiente** para ir a la página **Revisar y crear**.
12. Haga clic en **Crear** para crear la restricción.
13. La nueva restricción se crea con una prioridad justo por encima del valor predeterminado. También puede [cambiar la prioridad](#change-enrollment-restriction-priority).

Durante las inscripciones de BYOD, los usuarios recibirán una notificación en la que se les informará cuando hayan alcanzado el límite de dispositivos inscritos. Por ejemplo, en iOS:

![Notificación del límite en un dispositivo iOS](./media/enrollment-restrictions-set/enrollment-restrictions-ios-set-limit-notification.png)

> [!IMPORTANT]
> No se aplican restricciones de límite de dispositivos para los siguientes tipos de inscripción de Windows:
> - Inscripciones con administración conjunta
> - Inscripciones de GPO
> - Inscripciones unidas a Azure Active Directory
> - Inscripciones masivas unidas a Azure Active Directory
> - Inscripciones de AutoPilot
> - Inscripciones del administrador de inscripción de dispositivos
>
> No se aplican restricciones de límite de dispositivos para estos tipos de inscripción porque se consideran escenarios de dispositivos compartidos.
> Puede establecer límites estrictos para estos tipos de inscripción [en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/devices/device-management-azure-portal#configure-device-settings).


## <a name="change-enrollment-restrictions"></a>Cambio de restricciones de inscripción

Para cambiar la configuración de una restricción de inscripción, siga estos pasos. Estas restricciones no afectan a los dispositivos que ya se han inscrito. Los dispositivos inscritos con el [agente de PC de Intune](../fundamentals/manage-windows-pcs-with-microsoft-intune.md) no se puede bloquear con esta característica.

1. Inicie sesión en Azure Portal.
2. Seleccione **Más servicios**, busque **Intune** y, después, seleccione **Intune**.
3. En **Inscripción de dispositivos** > **Restricciones de inscripción** > elija la restricción que quiere cambiar > **Propiedades**.
4. Elija **Editar** junto a la configuración que quiere cambiar.
5. En la página **Editar**, realice los cambios que quiera y siga en la página **Revisar y guardar**, elija luego **Guardar**.


## <a name="blocking-personal-android-devices"></a>Bloquear dispositivos Android personales
- Si bloquea la inscripción de dispositivos del administrador de dispositivos Android de propiedad personal, aún pueden inscribirse los dispositivos del perfil de trabajo de Android Enterprise de propiedad personal.
- De forma predeterminada, la configuración de los dispositivos de perfil de trabajo de Android Enterprise es igual que la configuración de los dispositivos del administrador de dispositivos Android. Después de cambiar la configuración del perfil de trabajo de Android Enterprise o del administrador de dispositivos Android, ya no es así.
- Si bloquea la inscripción del perfil de trabajo personal de Android Enterprise, tan solo los dispositivos Android de propiedad corporativa podrán inscribirse como perfil de trabajo de Android Enterprise.

## <a name="blocking-personal-windows-devices"></a>Bloquear dispositivos Windows personales
Si impide la inscripción de dispositivos Windows de uso personal, Intune realiza comprobaciones para asegurarse de que se ha autorizado cada nueva solicitud de inscripción de Windows como una inscripción corporativa. Las inscripciones no autorizadas se bloquearán.

Los métodos siguientes se consideran como autorizados como una inscripción corporativa de Windows:
- El usuario que se inscribe usa una [cuenta de administrador de inscripción de dispositivos]( device-enrollment-manager-enroll.md).
- El dispositivo se inscribe a través de [Windows AutoPilot](enrollment-autopilot.md).
- El dispositivo está registrado con Windows Autopilot, pero no es la única opción de inscripción de MDM que encontrará en la configuración de Windows.
- El número IMEI del dispositivo aparece en **Inscripción del dispositivo** >  **[Identificadores de dispositivo corporativos](corporate-identifiers-add.md)** . (No se admite para Windows Phone 8.1).
- El dispositivo se inscribe a través de un [paquete de aprovisionamiento en masa](windows-bulk-enroll.md).
- El dispositivo se inscribe a través de GPO, o la [inscripción automática de SCCM para la administración conjunta](https://docs.microsoft.com/sccm/comanage/quickstart-paths#bkmk_path1).
 
Intune marcó como corporativas las inscripciones siguientes. Pero se bloquearán porque no ofrecen control por dispositivo del administrador de Intune:
- [Inscripción automática de MDM](windows-enroll.md#enable-windows-10-automatic-enrollment) con [combinación de Azure Active Directory durante la instalación de Windows](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx)\*.
- [Inscripción automática de MDM](windows-enroll.md#enable-windows-10-automatic-enrollment) con [combinación de Azure Active Directory desde la instalación de Windows](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)*.
 
También se bloquearán los siguientes métodos de inscripción personal:
- [Inscripción automática de MDM](windows-enroll.md#enable-windows-10-automatic-enrollment) con [incorporación de cuenta profesional desde la instalación de Windows](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network)\*.
- Opción de [solo inscripción de MDM]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device) desde la instalación de Windows.

\* Estos no se bloquearán si se han registrado con Autopilot.


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
