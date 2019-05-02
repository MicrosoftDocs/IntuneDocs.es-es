---
title: Supervisión de las directivas de cumplimiento de dispositivos en Microsoft Intune - Azure | Microsoft Docs
description: Use el panel de cumplimiento de dispositivos para supervisar el cumplimiento general del dispositivo, ver informes y ver el cumplimiento de los dispositivos por directiva y por configuración.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 654d5b86a8a2df8eaddc8ea626b55390d2d32920
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61509077"
---
# <a name="monitor-intune-device-compliance-policies"></a>Supervisión de las directivas de cumplimiento de dispositivos Intune

Los informes de cumplimiento ayudan a revisar el cumplimiento de los dispositivos y solucionar problemas relacionados con el cumplimiento en la organización. Con estos informes, puede ver información sobre:

- Los estados de cumplimiento general de los dispositivos
- El estado de cumplimiento de una configuración individual
- El estado de cumplimiento de una directiva individual
- Explorar en profundidad los dispositivos individuales para ver los valores específicos y las directivas que afectan a los dispositivos

## <a name="open-the-compliance-dashboard"></a>Apertura del panel de cumplimiento

Abra el **panel de Cumplimiento de dispositivos de Intune**:

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.

2. Seleccione **Cumplimiento del dispositivo** > **Información general**. Se abre el **panel de cumplimiento de dispositivos**.

> [!IMPORTANT]
> Los dispositivos deben inscribirse en Intune para recibir las directivas de cumplimiento de dispositivos.

## <a name="dashboard-overview"></a>Visión general del panel

Cuando el panel se abre, se obtiene una visión general con todos los informes de cumplimiento. En estos informes, puede ver y comprobar lo siguiente:

- Cumplimiento general del dispositivo
- Cumplimiento de dispositivos por directiva
- Cumplimiento de dispositivos por configuración
- Estado de protección del dispositivo
- Estado del agente de amenazas

![Imagen del panel en la que se muestra el panel de cumplimiento de dispositivos y los distintos informes](./media/compliance-policy-monitor/idc-1.png)

Al profundizar en este informe, también se pueden ver las directivas de cumplimiento específicas y las configuraciones que se aplican a un dispositivo concreto, incluido el estado de cumplimiento de cada configuración.

### <a name="device-compliance-status-report"></a>Informe de estado de cumplimiento del dispositivo

En el gráfico se muestran los estados de cumplimiento para todos los dispositivos inscritos en Intune. Los estados de cumplimiento de dispositivos se mantienen en dos bases de datos diferentes: Intune y Azure Active Directory. 

> [!IMPORTANT]
> Intune sigue el programa de inserción en el repositorio del dispositivo para todas las evaluaciones de cumplimiento del dispositivo. [Obtenga más información sobre el programa de inserción en el repositorio del dispositivo](https://docs.microsoft.com/intune/device-profile-troubleshoot#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned).

Descripciones de los estados de directiva de cumplimiento de dispositivos:

- **Conforme**: el dispositivo aplicó correctamente una o varias configuraciones de directivas de cumplimiento de dispositivos.

- **En período de gracia:** el dispositivo se selecciona como destino con una o varias configuraciones de directivas de cumplimiento de dispositivos. Pero el usuario todavía no ha aplicado las directivas. Esto significa que el dispositivo es no conforme, pero se encuentra en el período de gracia definido por el administrador.

  - Obtenga más información sobre las [acciones disponibles para los dispositivos que no cumplen las directivas](actions-for-noncompliance.md).

- **Sin evaluar**: un estado inicial para los dispositivos recién inscritos. Otros posibles motivos de este estado incluyen:

  - Dispositivos que no tienen asignada una directiva de cumplimiento y no tienen un desencadenador para comprobar su cumplimiento
  - Dispositivos que no se han registrado desde la última vez que se actualizó la directiva de cumplimiento
  - Dispositivos no asociados a un usuario específico
  - Dispositivos inscritos con una cuenta del administrador de inscripciones de dispositivos (DEM)

- **No conforme:** el dispositivo no pudo aplicar una o varias configuraciones de directivas de cumplimiento de dispositivos. O bien, el usuario no ha cumplido las directivas.

- **No se sincroniza el dispositivo:** el dispositivo no pudo informar del estado de las directivas de cumplimiento de dispositivos por uno de los siguientes motivos:

  - **Desconocido**: el dispositivo está sin conexión o no se pudo comunicar con Intune o Azure AD por otras razones.

  - **Error**: el dispositivo no pudo comunicarse con Intune y Azure AD, y recibió un mensaje de error con el motivo.

> [!IMPORTANT]
> Los dispositivos que están inscritos en Intune, pero no seleccionados como destino de ninguna directiva de cumplimiento de dispositivos, se incluyen en este informe, en el depósito **Conforme**.

#### <a name="drill-down-for-more-details"></a>Exploración en profundidad para obtener más detalles

En el gráfico **Estado de cumplimiento del dispositivo**, seleccione un estado. Por ejemplo, seleccione el estado **No conforme**:

![Selección del estado No conforme](./media/compliance-policy-monitor/select-not-compliant-status.png)

Muestra más detalles sobre los dispositivos que tienen ese estado, incluida la plataforma del sistema operativo, la fecha de la última inserción en el repositorio y mucho más. 

![Imagen del panel en la que se muestran más detalles sobre el dispositivo en ese estado específico](./media/compliance-policy-monitor/drill-down-details.png)

Si quiere ver todos los dispositivos de un usuario específico, también puede filtrar el informe de gráfico escribiendo el correo electrónico del usuario.

#### <a name="filter-and-columns"></a>Filtrar y columnas

![Haga clic en Filtrar y Columnas para cambiar los resultados en el gráfico](./media/compliance-policy-monitor/filter-columns.png)

Cuando se hace clic en el botón **Filtrar**, se abre el menú emergente de filtro con más opciones, como el estado de cumplimiento, los dispositivos con Jailbreak y más. **Aplique** el filtro para actualizar los resultados.

Use la propiedad **Columnas** para agregar o quitar columnas del resultado del gráfico. Por ejemplo, **Nombre principal de usuario** puede mostrar la dirección de correo electrónico registrada en el dispositivo. **Aplique** las columnas para actualizar los resultados.

#### <a name="device-details"></a>Detalles del dispositivo

En el gráfico, seleccione un dispositivo específico y, después, seleccione **Conformidad de dispositivos**:

![Selección de un dispositivo específico y, después, de Conformidad de dispositivos para ver las directivas de cumplimiento aplicadas](./media/compliance-policy-monitor/see-policies-applied-specific-device.png)

Proporciona información detallada sobre la configuración de directivas de cumplimiento de dispositivos aplicada a ese dispositivo. Al seleccionar la directiva específica, se muestran todas las configuraciones de la directiva.

### <a name="devices-without-compliance-policy"></a>Dispositivos sin directiva de cumplimiento
En **Conformidad de dispositivos** > **Información general**, el informe también identifica los dispositivos que no tienen asignada ninguna directiva de cumplimiento:

![Visualización de los dispositivos sin directivas de cumplimiento](./media/compliance-policy-monitor/devices-without-policies.png)

Al hacer clic en el icono, se muestran todos los dispositivos sin una directiva de cumplimiento. También se muestra el usuario del dispositivo, el estado de implementación de la directiva y el modelo del dispositivo.

#### <a name="what-you-need-to-know"></a>Aspectos que debe saber

- Con la opción de seguridad **Marcar los dispositivos que no tienen asignada una directiva de cumplimiento como**, es importante identificar los dispositivos sin una directiva de cumplimiento. Posteriormente podrá asignarles al menos una directiva de cumplimiento.

  La opción de seguridad se puede configurar en el portal de Intune. Seleccione **Conformidad de dispositivos** > **Configuración de directivas de cumplimiento**. Después, establezca **Marcar los dispositivos que no tienen asignada una directiva de cumplimiento como** en **Compatible** o **No compatible**. 

  Obtenga más información sobre esta [mejora de la seguridad en el servicio de Intune](https://blogs.technet.microsoft.com/intunesupport/2018/02/09/updated-upcoming-security-enhancements-in-the-intune-service/).

- Los usuarios a los que se asigna una directiva de cumplimiento de cualquier tipo no se muestran en el informe, con independencia de la plataforma del dispositivo. Por ejemplo, si ha asignado una directiva de cumplimiento de Windows a un usuario que tiene un dispositivo Android, el dispositivo no se muestra en el informe. Pero Intune considera ese dispositivo Android como no conforme. Para evitar problemas, le recomendamos que cree directivas para cada plataforma de dispositivo y que las implemente para todos los usuarios.

### <a name="per-policy-device-compliance-report"></a>Informe de cumplimiento de dispositivos por directiva

En el informe **Conformidad de dispositivos** > **Cumplimiento de directivas** se muestran las directivas y cuántos dispositivos son compatibles y no compatibles. 

![Visualización de una lista de la directiva y la diferencia entre dispositivos conformes y no conformes para esa directiva](./media/compliance-policy-monitor/idc-8.png)

Cuando se selecciona una directiva específica, puede ver el **estado de cumplimiento**, **alias de correo electrónico del usuario**, **modelo del dispositivo** y **ubicación** de cada dispositivo seleccionado como destino por esa directiva de cumplimiento.

## <a name="setting-compliance-report"></a>Informe de configuración de cumplimiento

En el informe **Conformidad de dispositivos** > **Configuración de cumplimiento** se muestra, por configuración de cumplimiento, el número total de dispositivos en cada estado de cumplimiento. Muestra toda la configuración de directivas de cumplimiento de todas las directivas de cumplimiento, las plataformas a las que se aplica la configuración de directivas y el número de dispositivos no conformes.

![Visualización de una lista de todas las configuraciones de las distintas directivas](./media/compliance-policy-monitor/idc-10.png)

Cuando se selecciona una configuración específica, puede ver el **estado de cumplimiento**, **alias de correo electrónico del usuario**, **modelo del dispositivo** y **ubicación** de cada dispositivo seleccionado como destino por esa configuración.

> [!NOTE]
> Los dispositivos Windows 10 que están unidos a Azure AD pueden mostrar la cuenta del sistema como un usuario no compatible. Este es el comportamiento esperado y no afecta al cumplimiento general del dispositivo. 

## <a name="view-status-of-device-policies"></a>Ver el estado de las directivas de dispositivo

Puede comprobar los diferentes estados de las directivas de cada plataforma. Por ejemplo, tenemos una directiva de cumplimiento de macOS. Queremos ver los dispositivos afectados por esta directiva y saber si hay conflictos o errores.

Esta característica aparece reflejada en el informe de estado del dispositivo:

1. Seleccione **Cumplimiento de dispositivos** > **Directivas**. Se muestra una lista de directivas (plataforma incluida), si la directiva está asignada y otros detalles.
2. Seleccione una directiva > **Información general**. En esta vista, la asignación de directiva engloba los siguientes estados:

    - Correcto: se aplica la directiva.
    - Error: no se ha podido aplicar la directiva. El mensaje se suele mostrar con un código de error vinculado a una explicación. 
    - Conflicto: se aplican dos configuraciones al mismo dispositivo, e Intune no puede solucionar el conflicto. Un administrador debe encargarse de revisar.
    - Pendiente: el dispositivo no se ha registrado aún con Intune para recibir la directiva. 
    - No aplicable: el dispositivo no puede recibir la directiva. Por ejemplo, la directiva actualiza una configuración específica de iOS 11.1, pero el dispositivo usa iOS 10. 

3. Para ver detalles sobre los dispositivos que usan esta directiva, seleccione uno de los estados. Por ejemplo, seleccione **Correcto**. En la siguiente ventana se muestran detalles concretos del dispositivo, como el nombre del dispositivo y el estado de la implementación.

## <a name="how-intune-resolves-policy-conflicts"></a>Cómo Intune resuelve los conflictos de directivas
Pueden producirse conflictos entre directivas de Intune cuando se aplican varias de ellas a un dispositivo. Si las configuraciones de directivas se solapan, Intune resuelve los conflictos siguiendo estas reglas:

- Si las configuraciones en conflicto proceden de una directiva de configuración de Intune y una directiva de cumplimiento, la configuración de la directiva de cumplimiento tiene preferencia sobre la configuración de la directiva de configuración. Esto es así incluso si la configuración de la directiva de configuración es más segura.

- Si ha implementado varias directivas de cumplimiento, Intune usa la más segura de ellas.
