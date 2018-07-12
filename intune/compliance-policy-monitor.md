---
title: Supervisión de las directivas de cumplimiento de dispositivos en Microsoft Intune - Azure | Microsoft Docs
description: Use el panel de cumplimiento de dispositivos para supervisar el cumplimiento general del dispositivo, ver informes y ver el cumplimiento de los dispositivos por directiva y por configuración.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5e9de6f1ac8bca1d65a94294d3b049dfccbe44c7
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905366"
---
# <a name="monitor-intune-device-compliance-policies"></a>Supervisión de las directivas de cumplimiento de dispositivos Intune

Los informes de cumplimiento ayudan a los administradores a analizar el estado de cumplimiento de los dispositivos de su organización, así como a solucionar rápidamente problemas de este tipo que detecten los usuarios de su organización. Puede ver información sobre el estado de cumplimiento general de los dispositivos, y el estado de cumplimiento de configuraciones y directivas concretas, así como profundizar en los dispositivos con el objetivo de ver las directivas y opciones específicas que afectan a los dispositivos.

## <a name="before-you-begin"></a>Antes de comenzar

Siga los pasos de abajo para encontrar el **panel de cumplimiento de dispositivos Intune** en el portal de Azure:

1. En [Azure Portal](https://portal.azure.com), inicie sesión con sus credenciales de Intune.

2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.

3. Seleccione **Cumplimiento del dispositivo** > **Información general**. Se abre el **panel de cumplimiento de dispositivos**.

> [!IMPORTANT]
> Los dispositivos deben inscribirse en Intune para recibir las directivas de cumplimiento de dispositivos.

## <a name="device-compliance-dashboard"></a>Panel de cumplimiento de dispositivos

En el **panel de cumplimiento de dispositivos**, puede supervisar el cumplimiento de diferentes dispositivos, su estado de protección y mucho más. Puede ver los siguientes informes:

- Agregado de cumplimiento general de dispositivos

- Cumplimiento de dispositivos por directiva

- Cumplimiento de dispositivos por configuración

- Estado de protección del dispositivo

- Estado del agente de amenazas

![Imagen en que se muestra el panel de cumplimiento del dispositivo](./media/idc-1.png)

También puede ver la configuración y las directivas de cumplimiento específicas que se aplican a un dispositivo concreto, y el estado final de cumplimiento de cada una de estas opciones del dispositivo.

### <a name="overall-device-compliance-aggregate-report"></a>Informe agregado de cumplimiento general de dispositivos

Se trata de un gráfico de anillos que muestra el estado de cumplimiento agregado de todos los dispositivos inscritos en Intune. Los estados de cumplimiento de dispositivos se mantienen en dos bases de datos: Intune y Azure Active Directory. A continuación, se muestran más detalles sobre los estados de cumplimiento de directivas de dispositivos:

- **Conforme**: el dispositivo aplicó correctamente una o varias configuraciones de directivas de cumplimiento de dispositivos que el administrador seleccionó como destino.

- **No conforme**: el dispositivo no pudo aplicar una o varias configuraciones de directivas de cumplimiento de dispositivos que el administrador seleccionó como destino, o bien el usuario no ha cumplido las directivas que el administrador seleccionó como destino.

- **En período de gracia**: el administrador seleccionó como destino el dispositivo con una o varias configuraciones de directivas de cumplimiento de dispositivos, pero el usuario no ha aplicado las directivas aún, lo que significa que el dispositivo tiene el estado No conforme, pero se encuentra en el período de gracia definido por el administrador.

  - Obtenga más información sobre las acciones disponibles para los dispositivos que no cumplen las directivas.

- **Dispositivo no sincronizado**: el dispositivo no pudo informar del estado de las directivas de cumplimiento de dispositivos por uno de los siguientes motivos:

  - **Desconocido**: el dispositivo está sin conexión o no se pudo comunicar con Intune o Azure AD por otras razones.

  - **Error**: el dispositivo no pudo comunicarse con Intune y Azure AD, y recibe un mensaje de error con el motivo.

> [!IMPORTANT]
> Los dispositivos que están inscritos en Intune, pero no seleccionados como destino de ninguna directiva de cumplimiento de dispositivos, se incluyen en este informe, en el depósito **Conforme**.

#### <a name="drill-down-option"></a>Opción de obtención de detalles

En el **panel de cumplimiento de dispositivos**, seleccione un elemento de cumplimiento de dispositivos para explorar en profundidad los **estados de cumplimiento**, los **alias de correo electrónico del usuario**, los **modelos de dispositivo** y las **ubicaciones** específicas de cada dispositivo objetivo de las directivas de cumplimiento de dispositivos.

![Imagen en que se muestra una exploración en profundidad del panel de cumplimiento de dispositivos](./media/idc-2.png)

Si necesita más información sobre un usuario específico, puede filtrar el informe de gráfico de cumplimiento de dispositivos escribiendo el alias de correo electrónico del usuario.

![Imagen en que se muestra el usuario específico del panel de cumplimiento de dispositivos](./media/idc-3.png)

También puede hacer clic en los diferentes estados de cumplimiento diferentes del gráfico de cumplimiento de dispositivos para ver más detalles de los estados de las directivas de cumplimiento de dispositivos del usuario.

![Imagen en que se muestran diferentes estados del panel de cumplimiento de dispositivos](./media/idc-4.png)

#### <a name="filter"></a>Filtro

Al hacer clic en el **botón Filtrar**, se abre el filtro emergente con las siguientes opciones:

- Modelo

  - Cuadro de texto que acepta cadenas de búsqueda libre

- Plataforma

  - Android

  - iOS

  - macOS

  - Windows

  - Windows Phone

- Estado

  - Conforme

  - No conforme

  - En período de gracia

  - Unknown

  - Error

Al hacer clic en el **botón Actualizar**, se cierra el menú emergente y los resultados se actualizan con los criterios del filtro seleccionado.

##### <a name="device-details"></a>Detalles del dispositivo

Al seleccionar un dispositivo, se abre **Dispositivos** con el dispositivo seleccionado. Así, se proporciona información detallada sobre la configuración de directivas de cumplimiento de dispositivos aplicada a ese dispositivo.

Al seleccionar la propia configuración de directivas de dispositivos, puede ver el que nombre de la directiva de cumplimiento de dispositivos originó dicha configuración de cumplimiento de dispositivos seleccionada como destino por el administrador.

### <a name="devices-without-compliance-policy"></a>Dispositivos sin directiva de cumplimiento
En este informe se identifican los dispositivos que no tienen asignada ninguna directiva de cumplimiento. Con la introducción de la opción de seguridad que marca como "No compatible" todos los dispositivos que no tienen directivas de cumplimiento, es importante poder identificar estos dispositivos. Posteriormente podrá asignarles al menos una directiva de cumplimiento.

> [!NOTE]
> La nueva configuración de seguridad se puede configurar en el portal de Intune. Seleccione **Conformidad de dispositivos** y, en **Configuración**, elija **Configuración de directivas de cumplimiento**. Después, use el botón de alternancia para establecer **Marcar los dispositivos que no tienen asignada una directiva de cumplimiento como** en **Compatible** o **No compatible**. Obtenga más información sobre esta [mejora de la seguridad en el servicio de Intune](https://blogs.technet.microsoft.com/intunesupport/2018/02/09/updated-upcoming-security-enhancements-in-the-intune-service/).

![Imagen en la que se muestra el informe Dispositivos sin directiva de cumplimiento](./media/idc-12.png)

El mosaico **Dispositivos sin directiva de cumplimiento** está disponible en el panel Conformidad de dispositivos. En él se muestran todos los dispositivos que no tienen ninguna directiva de cumplimiento, el usuario del dispositivo, el estado de cumplimiento y el modelo del dispositivo.

> [!NOTE]
> Los usuarios a los que se asigna una directiva de cumplimiento de cualquier tipo no aparecerán en el informe, sea cual sea la plataforma del dispositivo. Por ejemplo, si ha asignado por error una directiva de cumplimiento de Windows a un usuario que tiene un dispositivo Android, el dispositivo no aparecerá en el informe, aunque Intune considerará ese dispositivo como no compatible. Para evitar problemas, le recomendamos que cree directivas para cada plataforma de dispositivo y que las implemente para todos los usuarios.

### <a name="per-policy-device-compliance-report"></a>Informe de cumplimiento de dispositivos por directiva

Este informe proporciona una vista por directiva de cumplimiento y el número total de dispositivos en cada estado de cumplimiento. El título **Cumplimiento de directivas** está disponible en el **panel Cumplimiento de dispositivos**. En él se muestran todas las directivas que ha creado el administrador previamente, las plataformas en las que se aplica la directiva y el número de dispositivos conformes y no conformes.

![Imagen en que se muestra el informe de cumplimiento de dispositivos por directiva](./media/idc-8.png)

Al hacer clic en el mosaico de cumplimiento de directivas, seleccione una de las directivas de cumplimiento de dispositivos para ver el **estado de cumplimiento**, el **alias de correo electrónico del usuario**, el **modelo de dispositivo** y la **ubicación** de cada dispositivo al que se aplique esa directiva de cumplimiento de dispositivos.

## <a name="setting-compliance-report"></a>Informe de configuración de cumplimiento

Este informe permite ver, por configuración de cumplimiento, el número total de dispositivos en cada estado de cumplimiento. El título **Cumplimiento de configuración** está disponible en el **panel Cumplimiento de dispositivos**. En él se muestran todas las opciones de las directivas de cumplimiento de dispositivos creadas por el administrador, las plataformas en las que se han aplicado y el número de dispositivos no conformes.

![Imagen en que se muestra el informe de cumplimiento de dispositivos por configuración](./media/idc-10.png)

Al hacer clic en el mosaico Configuración de cumplimiento, seleccione una de las configuraciones de directivas de cumplimiento de dispositivos para ver el **estado de cumplimiento**, el **alias de correo electrónico del usuario**, el **modelo de dispositivo** y la **ubicación** de cada dispositivo al que se aplique esa configuración de directivas de cumplimiento de dispositivos.

## <a name="view-status-of-device-policies"></a>Ver el estado de las directivas de dispositivo

Puede comprobar los diferentes estados de las directivas de cada plataforma. Por ejemplo, tenemos una directiva de cumplimiento de macOS. Queremos ver los dispositivos afectados por esta directiva y saber si hay conflictos o errores.

Esta característica aparece reflejada en el informe de estado del dispositivo:

1. Seleccione **Cumplimiento de dispositivos** > **Directivas**. Se muestra una lista de directivas (plataforma incluida), si la directiva está asignada y otros detalles.
2. Seleccione una directiva > **Información general**. En esta vista, la asignación de directiva engloba los siguientes estados:

  - Correcto
  - Error
  - Conflicto
  - Pending
  - No disponible

3. Para ver detalles sobre los dispositivos que usan esta directiva, seleccione uno de los estados. Por ejemplo, seleccione **Correcto**. En la siguiente ventana se muestran detalles concretos del dispositivo, como el nombre del dispositivo y el estado de la implementación.

## <a name="how-intune-resolves-policy-conflicts"></a>Cómo Intune resuelve los conflictos de directivas
Pueden producirse conflictos entre directivas de Intune cuando se aplican varias de ellas a un dispositivo. Si las configuraciones de directivas se solapan, Intune resuelve los conflictos siguiendo estas reglas:

- Si las configuraciones en conflicto proceden de una directiva de configuración de Intune y una directiva de cumplimiento, la configuración de la directiva de cumplimiento tiene preferencia sobre la configuración de la directiva de configuración. Esto es así incluso si la configuración de la directiva de configuración es más segura.

- Si ha implementado varias directivas de cumplimiento, Intune usa la más segura de ellas.

