---
title: "Supervisión de las directivas de cumplimiento de dispositivos Intune"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: Aprenda a supervisar las directivas de cumplimiento de dispositivos."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 503d1dd2-a647-4aea-bf48-55319a3dd8a7
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: deea78dcea9ade031441bf12b388a862235a8e9c
ms.openlocfilehash: f207edab1b6b30d3680164f24d37e55823eec6d3
ms.lasthandoff: 03/15/2017


---
# <a name="monitor-intune-device-compliance-policies"></a>Supervisión de las directivas de cumplimiento de dispositivos Intune

Los informes de cumplimiento ayudan a los administradores a analizar la posición de cumplimiento de los dispositivos de su organización, así como a solucionar rápidamente problemas de este tipo que detecten los usuarios de su organización. Puede ver información sobre el estado de cumplimiento general de los dispositivos, y el estado de cumplimiento de configuraciones y directivas concretas, así como profundizar en los dispositivos con el objetivo de ver las directivas y opciones específicas que afectan a los dispositivos.

## <a name="before-you-begin"></a>Antes de comenzar

Siga los pasos de abajo para encontrar el **panel de cumplimiento de dispositivos Intune** en Azure Portal:

1.  Vaya a [Azure Portal](https://portal.azure.com) e inicie sesión con sus credenciales de Intune.

2.  Elija **Más servicios** en el menú izquierdo y, luego, escriba **Intune** en el filtro del cuadro de texto.

3.  Elija **Intune** &gt; **Conformidad de dispositivos** &gt; **Introducción**; se abrirá el **panel de cumplimiento de dispositivos**.

> [!IMPORTANT] 
> Los dispositivos deben inscribirse en Intune para recibir las directivas de cumplimiento de dispositivos.

## <a name="device-compliance-dashboard"></a>Panel de cumplimiento de dispositivos

En el **panel de cumplimiento de dispositivos**, donde puede supervisar los estados de las directivas de cumplimiento de dispositivos, proporciona varios informes en diferentes iconos que proporcionan la posición de cumplimiento de dispositivos de su organización. Puede ver los siguientes informes:

-   Agregado de cumplimiento general de dispositivos

-   Cumplimiento de dispositivos por directiva

-   Cumplimiento de dispositivos por configuración

![Panel de cumplimiento de dispositivos](../media/idc-1.png)

También puede ver la configuración y las directivas de cumplimiento específicas que se aplican a un dispositivo concreto, y el estado final de cumplimiento de cada una de estas opciones del dispositivo.

### <a name="overall-device-compliance-aggregate-report"></a>Informe agregado de cumplimiento general de dispositivos

Se trata de un gráfico de anillos que muestra el estado de cumplimiento agregado de todos los dispositivos inscritos en Intune. Los estados de cumplimiento de dispositivos se mantienen en dos bases de datos: Intune y Azure Active Directory. A continuación, se muestran más detalles sobre los estados de cumplimiento de directivas de dispositivos:

-   **Conforme**: el dispositivo aplicó correctamente una o varias configuraciones de directivas de cumplimiento de dispositivos que el administrador seleccionó como destino.

-   **No conforme**: el dispositivo no pudo aplicar una o varias configuraciones de directivas de cumplimiento de dispositivos que el administrador seleccionó como destino, o bien el usuario no ha cumplido las directivas que el administrador seleccionó como destino.

-   **En período de gracia**: el administrador seleccionó como destino el dispositivo con una o varias configuraciones de directivas de cumplimiento de dispositivos, pero el usuario no ha aplicado las directivas aún, lo que significa que el dispositivo tiene el estado No conforme, pero se encuentra en el período de gracia definido por el administrador.

    -   Obtenga más información sobre las acciones para los dispositivos que no cumplen las directivas.

-   **Device not synced** (Dispositivo no sincronizado): el dispositivo no pudo informar del estado de las directivas de cumplimiento de dispositivos por uno de los siguientes motivos:

    -   **Desconocido**: el dispositivo está sin conexión o no se pudo comunicar con Intune o Azure AD por otras razones.

    -   **Error**: el dispositivo no pudo comunicarse con Intune y Azure AD, y recibe un mensaje de error con el motivo.

> [!IMPORTANT] 
> Los dispositivos que están inscritos en Intune, pero no seleccionados como destino de ninguna directiva de cumplimiento de dispositivos, se incluirán en este informe, en el depósito **Conforme**.

#### <a name="drill-down-option"></a>Opción de obtención de detalles

En el **panel de cumplimiento de dispositivos**, si hace clic en el icono de cumplimiento de dispositivos, puede obtener detalles de **estados de cumplimiento**, **alias de correo electrónico del usuario**, **modelos de dispositivo** y **ubicaciones** específicos de cada dispositivo destino de las directivas de cumplimiento de dispositivos.

![Obtención de detalles del panel de cumplimiento de dispositivos](../media/idc-2.png)

Si necesita más información sobre un usuario específico, puede filtrar el informe de gráfico de cumplimiento de dispositivos escribiendo el alias de correo electrónico del usuario.

![Usuario específico del panel de cumplimiento de dispositivos](../media/idc-3.png)

También puede hacer clic en los diferentes estados de cumplimiento diferentes del gráfico de cumplimiento de dispositivos para ver más detalles de los estados de las directivas de cumplimiento de dispositivos del usuario.

![Estados diferentes del panel de cumplimiento de dispositivos](../media/idc-4.png)

#### <a name="filter"></a>Filtro

Si hace clic en **botón Filtrar**, se abre el filtro emergente con las siguientes opciones:

-   Modelo

    -   Cuadro de texto que acepta cadenas de búsqueda libre
<br></br>
-   Plataforma

    -   Android

    -   iOS

    -   Mac OS

    -   Windows

    -   Windows Phone

-   Estado

    -   Conforme

    -   No conforme

    -   En período de gracia

    -   Unknown

    -   Error de:

Si hace clic en el **botón Actualizar**, se debería cerrar el menú emergente y los resultados se deberían actualizar según los criterios del filtro seleccionado.

![Botón de actualización de filtro](../media/idc-5.png)

##### <a name="device-details"></a>Detalles del dispositivo

Al hacer clic en un dispositivo, se abre la **hoja Dispositivos** con el dispositivo seleccionado. De este modo, obtendrá información detallada sobre la configuración de directivas de cumplimiento de dispositivos aplicada a ese dispositivo.

![Panel de cumplimiento de dispositivos](../media/idc-6.png)

Al hacer clic en la propia configuración de directivas de dispositivos, puede ver el que nombre de la directiva de cumplimiento de dispositivos originó dicha configuración de cumplimiento de dispositivos seleccionada como destino por el administrador.

![Nombre de la configuración de cumplimiento de dispositivos](../media/idc-7.png)

### <a name="per-policy-device-compliance-report"></a>Informe de cumplimiento de dispositivos por directiva

Este informe proporciona una vista por directiva de cumplimiento y el número total de dispositivos en cada estado de cumplimiento. El icono de **cumplimiento de directivas** está disponible en el **panel de cumplimiento de dispositivos**, que muestra todas las directivas que creó previamente el administrador, las plataformas en las que se aplica la directiva, y el número de dispositivos conformes y no conformes.

![Informe de cumplimiento de dispositivos por directiva](../media/idc-8.png)

Al hacer clic en el icono de cumplimiento de directivas, seleccione una de las directivas de cumplimiento de dispositivos para ver el **estado de cumplimiento**, el **alias de correo electrónico del usuario**, el **modelo de dispositivo** y la **ubicación** de cada dispositivo destino de esa directiva de cumplimiento de dispositivos.

![Icono de cumplimiento de directivas](../media/idc-9.png)

### <a name="per-setting-device-compliance-report"></a>Informe de cumplimiento de dispositivos por configuración

Este informe permite ver, por configuración de cumplimiento, el número total de dispositivos en cada estado de cumplimiento. El icono de **cumplimiento de configuración** está disponible en el **panel de cumplimiento de dispositivos**, y muestra todas las configuraciones de directivas de cumplimiento de dispositivos de todas las directivas de cumplimiento de dispositivos creadas por el administrador, las plataformas en las que se aplicaron las configuraciones de directivas y el número de dispositivos que no cumplen las directivas.

![Informe de cumplimiento de dispositivos por configuración](../media/idc-10.png)

Al hacer clic en el icono de cumplimiento de configuración, seleccione una de las configuraciones de directivas de cumplimiento de dispositivos para ver el **estado de cumplimiento**, el **alias de correo electrónico del usuario**, el **modelo de dispositivo** y la **ubicación** de cada dispositivo destino de esa directiva de cumplimiento de dispositivos.

![Icono de cumplimiento de configuración](../media/idc-11.png)

