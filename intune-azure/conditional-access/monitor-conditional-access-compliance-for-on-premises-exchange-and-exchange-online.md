---
title: "Supervisión del cumplimiento de acceso condicional de Exchange local y Exchange Online"
titleSuffix: Intune Azure preview
description: "Supervisión del cumplimiento de acceso condicional de Exchange local y Exchange Online a través de Azure Portal en Intune"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5712682d-285b-43fd-9978-3dcfd95ec5f9
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: c8715f96f532ee6bacda231e1147d03226ecbb48
ms.openlocfilehash: 9d5521de8709bf232dedfeeb1874f8db1898f2d0
ms.lasthandoff: 04/26/2017


---

# <a name="monitor-conditional-access-compliance-for-on-premises-exchange-and-exchange-online-in-intune-azure-preview"></a>Supervisión del cumplimiento de acceso condicional de Exchange local y Exchange Online a través de la versión preliminar de Azure en Intune

A partir de la versión 1704 de Intune, los administradores pueden ver información de los informes relacionados con los registros de dispositivos de Exchange ActiveSync que se sincronizan con Intune mediante la instancia de Exchange Connector local o el conector de Intune de servicio a servicio (conector de Exchange Online). Los informes de cumplimiento de acceso condicional proporcionan un resumen de los dispositivos con diferentes estados de sincronización:

-   **Permitir**

-   **Bloquear**

-   **Cuarentena**

## <a name="to-monitor-conditional-access-compliance"></a>Para supervisar el cumplimiento de acceso condicional

1.  Vaya a [Azure Portal](https://portal.azure.com/) e inicie sesión con sus credenciales de Intune.

2.  Después de iniciar sesión correctamente, verá el **Panel de Azure**.

3.  Elija **Más servicios** en el menú izquierdo y, luego, escriba **Intune** en el filtro del cuadro de texto.

4.  Elija **Intune** y aparecerá el **panel de Intune**.

5.  Elija **Acceso condicional** y luego **Introducción**.

6.  Elija una de las tres áreas (**Bloqueado**, **En cuarentena** o **Permitido**) en el gráfico para ver los informes de cumplimiento de acceso condicional.

    ![Panel de acceso condicional](../media/CA-reporting-intune-1.png)

Una vez que elija una de las tres áreas, puede ver más detalles acerca de los dispositivos que se permiten, se bloquean o se ponen en cuarentena.

También puede desglosar en dispositivos específicos para ver más detalles. Por ejemplo, el dispositivo seleccionado en la imagen siguiente está bloqueado. Intune le ofrece la opción de quitar los datos corporativos de la hoja de informe de cumplimiento de acceso condicional.

![Informes de detalles de dispositivo de acceso condicional](../media/CA-reporting-intune-3.png)

En la hoja de detalles del dispositivo, puede ver más información:

-   **Información general:** puede ver propiedades del dispositivo como la versión del SO, el modelo de dispositivo, la propiedad, el número de serie, el fabricante del dispositivo, el número de teléfono y la última vez que se protegió.

-   **Propiedades:** puede establecer la propiedad del dispositivo (personal o corporativo).

-   **Hardware:** proporciona la información que se muestra en la Información general, así como los detalles de almacenamiento (espacio total y espacio libre), el alojamiento del sistema, los detalles de la red, el servicio de red y más detalles de bloqueo de acceso condicional.

-   **Aplicaciones detectadas:** muestra todas las aplicaciones instaladas en el dispositivo. También puede exportar la lista de aplicaciones instaladas en formato .CSV.

-   **Cumplimiento:** muestra detalles de la directiva de cumplimiento de todos los dispositivos.

-   **Configuración del dispositivo:** muestra los detalles de configuración de todos los dispositivos.

-   **Acceso de Exchange:** aquí puede obtener más información sobre el estado del dispositivo después de aplicar las directivas de acceso condicional.

