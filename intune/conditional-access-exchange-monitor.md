---
title: Supervisar el acceso condicional de Exchange en Microsoft Intune
titlesuffix: ''
description: Supervise el cumplimiento de acceso condicional de Exchange local y Exchange Online a través de Azure Portal de Intune.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5712682d-285b-43fd-9978-3dcfd95ec5f9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 932dfe32c6df5741615d9db9f303aaee7785d3a3
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
ms.locfileid: "29775365"
---
# <a name="monitor-conditional-access-compliance-for-on-premises-exchange-and-exchange-online-in-intune"></a>Supervisión del cumplimiento del acceso condicional en Exchange local y Exchange Online en Intune

A partir de la versión 1704 de Intune, los administradores pueden ver información de los informes relacionados con los registros de dispositivos de Exchange ActiveSync que se sincronizan con Intune mediante la instancia de Exchange Connector local o el conector de Intune de servicio a servicio (conector de Exchange Online). Los informes de cumplimiento de acceso condicional proporcionan un resumen de los dispositivos con diferentes estados de sincronización:

-   **Permitir**

-   **Bloquear**

-   **Cuarentena**

## <a name="to-monitor-conditional-access-compliance"></a>Para supervisar el cumplimiento de acceso condicional

1.  Vaya a [Azure Portal](https://portal.azure.com/) e inicie sesión con sus credenciales de Intune.

2.  Después de iniciar sesión correctamente, verá el **Panel de Azure**.

3.  Elija **Todos los servicios** en el menú de la izquierda y, luego, escriba **Intune** en el filtro del cuadro de texto.

4.  Elija **Intune** y aparecerá el **panel de Intune**.

5.  Elija **Acceso condicional** y luego **Introducción**.

6.  Elija una de las tres áreas (**Permitido**, **Bloqueado** o **Cuarentena**) en el gráfico para ver los informes de cumplimiento de acceso condicional.

    ![Imagen del panel de acceso condicional](./media/CA-reporting-intune-1.png)

Una vez que elija una de las tres áreas, puede ver más detalles sobre los dispositivos que se permiten, se bloquean o se ponen en cuarentena.

También puede desglosar en dispositivos específicos para ver más detalles. Por ejemplo, el dispositivo seleccionado en la siguiente imagen está bloqueado. Intune le ofrece la opción de quitar los datos corporativos del panel de informe de cumplimiento de acceso condicional.

![Imagen de informes de detalles de dispositivo de acceso condicional](./media/CA-reporting-intune-3.png)

En el panel de detalles del dispositivo, puede ver más información:

-   **Información general:** puede ver propiedades del dispositivo como la versión del sistema operativo, el modelo de dispositivo, la propiedad, el número de serie, el fabricante del dispositivo, el número de teléfono y la última vez que se protegió.

-   **Propiedades:** puede establecer la propiedad del dispositivo (personal o corporativo).

-   **Hardware:** proporciona la información que se muestra en la Información general, así como los detalles de almacenamiento (espacio total y espacio libre), el alojamiento del sistema, los detalles de la red, el servicio de red y más detalles de bloqueo de acceso condicional.

-   **Aplicaciones detectadas:** muestra todas las aplicaciones instaladas en el dispositivo. También puede exportar la lista de aplicaciones instaladas en formato .CSV.

-   **Cumplimiento:** muestra detalles de la directiva de cumplimiento de todos los dispositivos.

-   **Configuración del dispositivo:** muestra los detalles de configuración de todos los dispositivos.

-   **Acceso de Exchange:** aquí puede obtener más información sobre el estado del dispositivo después de aplicar las directivas de acceso condicional.
