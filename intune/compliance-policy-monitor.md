---
title: "Supervisión de las directivas de cumplimiento de dispositivos Intune"
titlesuffix: Azure portal
description: Aprenda a supervisar las directivas de cumplimiento de dispositivos
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 2/27/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2f80d46e3e7c25c2b2e7a7c1af9604de1257a21e
ms.sourcegitcommit: a55c009a2ab223f79dc7439539937b284aee0626
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/28/2018
---
# <a name="monitor-intune-device-compliance-policies"></a>Supervisión de las directivas de cumplimiento de dispositivos Intune

Los informes de cumplimiento ayudan a los administradores a analizar el estado de cumplimiento de los dispositivos de su organización, así como a solucionar rápidamente problemas de este tipo que detecten los usuarios de su organización. Puede ver información sobre el estado de cumplimiento general de los dispositivos, y el estado de cumplimiento de configuraciones y directivas concretas, así como profundizar en los dispositivos con el objetivo de ver las directivas y opciones específicas que afectan a los dispositivos.

## <a name="before-you-begin"></a>Antes de comenzar

Siga estos pasos para encontrar el **panel de cumplimiento de dispositivos Intune** en Azure Portal:

1.  Vaya a [Azure Portal](https://portal.azure.com) e inicie sesión con sus credenciales de Intune.

2.  Elija **Más servicios** en el menú izquierdo y, luego, escriba **Intune** en el filtro del cuadro de texto.

3.  Elija **Intune** &gt; **Conformidad de dispositivos** &gt; **Introducción**; se abrirá el **panel de cumplimiento de dispositivos**.

> [!IMPORTANT] 
> Los dispositivos deben inscribirse en Intune para recibir las directivas de cumplimiento de dispositivos.

## <a name="device-compliance-dashboard"></a>Panel de cumplimiento de dispositivos

En el **panel de cumplimiento de dispositivos** puede supervisar los estados de las directivas de cumplimiento de dispositivos, que proporcionan varios informes en diferentes mosaicos que le indican el estado de cumplimiento de los dispositivos de su organización. Puede ver los siguientes informes:

-   Agregado de cumplimiento general de dispositivos

-   Cumplimiento de dispositivos por directiva

-   Cumplimiento de dispositivos por configuración

![Panel de cumplimiento de dispositivos](./media/idc-1.png)

También puede ver la configuración y las directivas de cumplimiento específicas que se aplican a un dispositivo concreto, y el estado final de cumplimiento de cada una de estas opciones del dispositivo.

### <a name="overall-device-compliance-aggregate-report"></a>Informe agregado de cumplimiento general de dispositivos

Se trata de un gráfico de anillos que muestra el estado de cumplimiento agregado de todos los dispositivos inscritos en Intune. Los estados de cumplimiento de dispositivos se mantienen en dos bases de datos: Intune y Azure Active Directory. A continuación, se muestran más detalles sobre los estados de cumplimiento de directivas de dispositivos:

-   **Conforme**: el dispositivo aplicó correctamente una o varias configuraciones de directivas de cumplimiento de dispositivos que el administrador seleccionó como destino.

-   **No conforme**: el dispositivo no pudo aplicar una o varias configuraciones de directivas de cumplimiento de dispositivos que el administrador seleccionó como destino, o bien el usuario no ha cumplido las directivas que el administrador seleccionó como destino.

-   **En período de gracia**: el administrador seleccionó como destino el dispositivo con una o varias configuraciones de directivas de cumplimiento de dispositivos, pero el usuario no ha aplicado las directivas aún, lo que significa que el dispositivo tiene el estado No conforme, pero se encuentra en el período de gracia definido por el administrador.

    -   Obtenga más información sobre las acciones disponibles para los dispositivos que no cumplen las directivas.

-   **Dispositivo no sincronizado**: el dispositivo no pudo informar del estado de las directivas de cumplimiento de dispositivos por uno de los siguientes motivos:

    -   **Desconocido**: el dispositivo está sin conexión o no se pudo comunicar con Intune o Azure AD por otras razones.

    -   **Error**: el dispositivo no pudo comunicarse con Intune y Azure AD, y recibe un mensaje de error con el motivo.

> [!IMPORTANT] 
> Los dispositivos que están inscritos en Intune, pero no seleccionados como destino de ninguna directiva de cumplimiento de dispositivos, se incluyen en este informe, en el depósito **Conforme**.

#### <a name="drill-down-option"></a>Opción de obtención de detalles

En el **panel de cumplimiento de dispositivos**, si hace clic en el mosaico de cumplimiento de dispositivos, puede explorar en profundidad los **estados de cumplimiento**, **alias de correo electrónico del usuario**, **modelos de dispositivo** y **ubicaciones** específicos de cada dispositivo destino de las directivas de cumplimiento de dispositivos.

![Exploración en profundidad del panel de cumplimiento de dispositivos](./media/idc-2.png)

Si necesita más información sobre un usuario específico, puede filtrar el informe de gráfico de cumplimiento de dispositivos escribiendo el alias de correo electrónico del usuario.

![Usuario específico del panel de cumplimiento de dispositivos](./media/idc-3.png)

También puede hacer clic en los diferentes estados de cumplimiento diferentes del gráfico de cumplimiento de dispositivos para ver más detalles de los estados de las directivas de cumplimiento de dispositivos del usuario.

![Estados diferentes del panel de cumplimiento de dispositivos](./media/idc-4.png)

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

    -   Error

Si hace clic en el **botón Actualizar**, se debería cerrar el menú emergente y los resultados se deberían actualizar según los criterios del filtro seleccionado.

##### <a name="device-details"></a>Detalles del dispositivo

Al hacer clic en un dispositivo, se abre la **hoja Dispositivos** con el dispositivo seleccionado. De este modo, obtendrá información detallada sobre la configuración de directivas de cumplimiento de dispositivos aplicada a ese dispositivo.

![Panel de cumplimiento de dispositivos](./media/idc-6.png)

Al hacer clic en la propia configuración de directivas de dispositivos, puede ver el que nombre de la directiva de cumplimiento de dispositivos originó dicha configuración de cumplimiento de dispositivos seleccionada como destino por el administrador.

![Nombre de la configuración de cumplimiento de dispositivos](./media/idc-7.png)

## <a name="policy-compliance-report"></a>Informe de cumplimiento de directivas

Este informe proporciona una vista por directiva de cumplimiento y el número total de dispositivos en cada estado de cumplimiento. El título **Cumplimiento de directivas** está disponible en el **panel Cumplimiento de dispositivos**. En él se muestran todas las directivas que ha creado el administrador previamente, las plataformas en las que se aplica la directiva y el número de dispositivos conformes y no conformes.

![Informe de cumplimiento de dispositivos por directiva](./media/idc-8.png)

Al hacer clic en el mosaico de cumplimiento de directivas, seleccione una de las directivas de cumplimiento de dispositivos para ver el **estado de cumplimiento**, el **alias de correo electrónico del usuario**, el **modelo de dispositivo** y la **ubicación** de cada dispositivo al que se aplique esa directiva de cumplimiento de dispositivos.

![Icono de cumplimiento de directivas](./media/idc-9.png)

## <a name="setting-compliance-report"></a>Informe de configuración de cumplimiento

Este informe permite ver, por configuración de cumplimiento, el número total de dispositivos en cada estado de cumplimiento. El título **Configuración de cumplimiento** está disponible en el **panel de cumplimiento de dispositivos**. En él se muestran todas las opciones de las directivas de cumplimiento de dispositivos creadas por el administrador, las plataformas en las que se han aplicado y el número de dispositivos no conformes.

![Informe de cumplimiento de dispositivos por configuración](./media/idc-10.png)

Al hacer clic en el mosaico Configuración de cumplimiento, seleccione una de las configuraciones de directivas de cumplimiento de dispositivos para ver el **estado de cumplimiento**, el **alias de correo electrónico del usuario**, el **modelo de dispositivo** y la **ubicación** de cada dispositivo al que se aplique esa configuración de directivas de cumplimiento de dispositivos.

![Icono de cumplimiento de configuración](./media/idc-11.png)

## <a name="threat-agent-status-report"></a>Informe de estado del agente de amenazas

Este informe permite ver el estado y el mantenimiento del agente de Windows Defender. Usando un informe de acumulación de estado en **Conformidad de dispositivos**, puede ver los dispositivos que requieren alguna de las siguientes acciones:
- Actualización de la firma
- Reiniciar
- Intervención manual
- Examen completo
- Otros estados del agente que requieren intervención

Un informe detallado para cada categoría de estado muestra los equipos individuales que precisan atención, así como aquellos que se identifican como **Limpiar**.
