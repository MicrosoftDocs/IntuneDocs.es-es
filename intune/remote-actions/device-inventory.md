---
title: Ver los detalles de un dispositivo con Microsoft Intune - Azure | Microsoft Docs
description: Vea los detalles del dispositivo, incluidos los sistemas operativos, el espacio de almacenamiento, el fabricante y el modelo. Obtenga una lista de las aplicaciones instaladas, compruebe las directivas de cumplimiento y configure TeamViewer con Microsoft Intune en Azure. El procedimiento es similar a ver el inventario de los dispositivos que administra.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ce3f73834ffdc2648dae345f8fa2a8233d2bb8c9
ms.sourcegitcommit: e7052114324b80d0503b107c934bb90b8eb29704
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75756020"
---
# <a name="see-device-details-in-intune"></a>Ver detalles del dispositivo en Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

La característica **Dispositivos** proporciona detalles adicionales sobre los dispositivos que administra, incluido el hardware, y sobre las aplicaciones instaladas.

En este artículo se explica cómo se pueden ver todos los dispositivos y sus propiedades en el portal de Azure.

## <a name="view-the-device-details"></a>Ver los detalles del dispositivo

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Seleccione **Dispositivos** > **Todos los dispositivos** > seleccione uno de los dispositivos que aparecen para que se muestren los detalles correspondientes:

   - En **Información general** se indica el nombre del dispositivo y algunas propiedades clave del dispositivo., como, por ejemplo, si se trata de un dispositivo Bring Your Own Device (BYOD), hora de entrada, etc. Puede realizar lo siguiente en el dispositivo:
      - [Retirar](devices-wipe.md#retire)
      - [Borrar](devices-wipe.md#wipe)
      - [Bloqueo remoto](device-remote-lock.md)
      - [Sincronización del dispositivo](device-sync.md)
      - [Restablecer el código de acceso](device-passcode-reset.md)
      - [Reiniciar](device-restart.md) (solo para Windows)
      - [Comienzo de cero](device-fresh-start.md) (solo para Windows)
      - Iniciar una sesión de asistencia remota
   - Use **Propiedades** para asignar una [categoría de dispositivo que cree](../enrollment/device-group-mapping.md) y cambie la propiedad del dispositivo a un dispositivo personal o a un dispositivo de empresa.
   - **Hardware** incluye muchos detalles sobre el dispositivo, como el identificador del dispositivo, el sistema operativo y la versión, el espacio de almacenamiento y más detalles.
   - **Aplicaciones detectadas**: muestra todas las aplicaciones que Intune encuentra instaladas en el dispositivo, así como las versiones de las aplicaciones. Para más información, consulte [Aplicaciones descubiertas de Intune](../apps/app-discovered-apps.md).
   - En **Conformidad de dispositivos** figuran todas las directivas de cumplimiento asignadas y se indica si el dispositivo es compatible o no.
   - En **Configuración del dispositivo** se muestran todas las directivas de configuración de dispositivos asignadas al dispositivo. También se indica si la directiva se ha aplicado correctamente o no.

## <a name="hardware-device-details"></a>Estado del dispositivo de hardware
En función del operador que usen los dispositivos, puede que no se recopilen todos los detalles.

> [!Note]  
> El inventario de hardware y de software se actualiza cada 7 días en el servicio de Intune.

|Detalle|Descripción|Plataforma| 
|--------------|----------------------|----|  
|Nombre|Nombre del dispositivo.|Windows, iOS|
|Nombre de administración|Nombre de dispositivo usado solo en la consola. Si se cambia, el nombre del dispositivo permanece inalterado.|Windows, iOS|
|UDID|Identificador de dispositivo único del dispositivo.|Windows, iOS|
|Identificador de dispositivo de Intune|GUID que identifica el dispositivo de forma única.|Windows, iOS|
|Número de serie|Número de serie del dispositivo del fabricante.|Windows, iOS|
|Dispositivo compartido|Si se establece en **Sí**, el dispositivo se comparte con más de un usuario.|Windows, iOS|
|Inscripción de usuario aprobada|Si se establece en **Sí**, el dispositivo dispondrá de una inscripción de usuario aprobada que permite a los administradores administrar determinadas opciones de seguridad en el dispositivo.|Windows, iOS|
|Sistema operativo|Sistema operativo usado en el dispositivo.|Windows, iOS|
|Versión del sistema operativo|La versión del sistema operativo en el dispositivo.|Windows, iOS|
|Idioma del sistema operativo|Idioma configurado en el sistema operativo del dispositivo.|Windows, iOS|
|Número de compilación|Número de compilación del sistema operativo.|Android|
|Nivel de revisión de seguridad|Nivel de revisión de seguridad del dispositivo.|Android|
|Espacio de almacenamiento total|Espacio de almacenamiento total del dispositivo (en gigabytes).|Windows, iOS|
|Espacio de almacenamiento libre|Espacio de almacenamiento sin usar en el dispositivo (en gigabytes).|Windows, iOS|
|IMEI|Identidad de equipo móvil internacional del dispositivo.|Windows, iOS, Android|
|MEID|Identificador de equipo móvil del dispositivo.|Windows, iOS, Android|
|Fabricante|Fabricante del dispositivo.|Windows, iOS, Android|
|Modelo|Modelo del dispositivo.|Windows, iOS, Android|
|Número de teléfono|Número de teléfono asignado al perfil.|Windows, iOS, Android*|
|Operador del suscriptor|Operador de red inalámbrica del dispositivo.|Windows, iOS, Android|
|Tecnología de datos móviles|Sistema de radio usado en el dispositivo.|Windows, iOS, Android|
|MAC Wi-Fi|Dirección de Media Access Control del dispositivo.|Windows, iOS, Android|
|ICCID|Identificador de tarjeta de circuitos integrados, que es el número de identificación único de una tarjeta SIM.|Windows, iOS, Android|
|Fecha de inscripción|Fecha y hora en que el dispositivo se inscribió en Intune.|Windows, iOS, Android|
|Último contacto|Fecha y hora en que el dispositivo se conectó a Intune por última vez.|Windows, iOS, Android|
|Código de omisión del bloqueo de activación|Código que se puede usar para omitir el bloqueo de activación.|iOS|
|Registrado en Azure AD|Si se establece en **Sí**, el dispositivo se registra en Azure Directory.|Windows, iOS, Android|
|Registrado en Intune|Si se establece en **Sí**, el dispositivo se registra en Intune.|Windows, iOS, Android|
|Cumplimiento|Estado de cumplimiento del dispositivo.|Windows, iOS, Android|
|EAS activada|Si se establece en **Sí**, el dispositivo se sincroniza con un buzón de Exchange.|Windows, iOS, Android|
|Id. de activación de EAS|Identificador de Exchange ActiveSync del dispositivo.|Windows, iOS, Android|
|Supervisado|Si se establece en **Sí**, los administradores han mejorado el control sobre el dispositivo.|Windows, iOS, Android|
|Cifrado|Si se establece en **Sí**, los datos almacenados en el dispositivo se cifran.|Windows, iOS, Android|

\* No está disponible en Android con el administrador de directivas de Google, como los dispositivos totalmente administrados y dedicados

> [!Note]  
> El número de teléfono no está inventariado en dispositivos Android Enterprise dedicados o totalmente administrados.

## <a name="next-steps"></a>Pasos siguientes
Vea qué más puede hacer para [administrar sus dispositivos](device-management.md) con Intune.
