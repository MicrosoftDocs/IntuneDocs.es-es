---
title: Administrar dispositivos con Intune
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: Información sobre cómo ver los dispositivos que administra con Intune y realizar diversas operaciones en ellos."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/13/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: 25a46754f6c7e44b3f4fef7e8eef015cf559e31f
ms.lasthandoff: 04/19/2017


---

# <a name="what-is-microsoft-intune-device-management"></a>¿Qué es la administración de dispositivos de Microsoft Intune?


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

La carga de trabajo de **Dispositivos**ofrece información sobre los dispositivos que administra y permite realizar tareas remotas en esos dispositivos. Para acceder a la carga de trabajo:

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Dispositivos**.

Ahora, elija una de las opciones siguientes:

- **Overview** (Información general): obtenga información sobre los dispositivos que ha inscrito y los sistemas operativos en los que se ejecuta cada dispositivo.
- **Administrar**: elija **Todos los dispositivos** para ver una lista de todos los dispositivos administrados.
    Seleccione uno de los dispositivos de la lista para abrir la hoja *nombre de dispositivo*> **Overview** (Información general) donde puede seleccionar una de estas opciones:
    - **Overview** (Información general): consulte las limitaciones generales sobre el dispositivo, como la información sobre su nombre, el propietario, si se trata de un dispositivo BYOD, cuándo se registró por última vez, y mucho más.

    - **Hardware**: consulte información más detallada sobre el dispositivo, como el espacio libre de almacenamiento, el modelo, el fabricante y mucho más.
    ![Inventario de hardware de dispositivo administrado](./media/hardware-inventory.png)
    - **Aplicaciones detectadas**: muestra una lista de todas las aplicaciones instaladas en el dispositivo que encuentra Intune.
    ![Nodo de aplicaciones detectadas](./media/detected-applications.png)
- **Monitor** (Supervisar): elija **Acciones de dispositivo** para ver una lista de acciones de dispositivo que se han realizado en los dispositivos administrados y el estado actual de tales acciones.
![Supervisión de acciones de dispositivo](./media/monitor-device-actions.png)
- **Ayuda y soporte técnico**: muestra vínculos a la documentación de solución de problemas y asistencia técnica.

## <a name="available-device-actions"></a>Acciones de dispositivo disponibles

Además, puede realizar las siguientes acciones remotas en el dispositivo (no todas las acciones se admiten en todas las plataformas de dispositivo):

### <a name="remove-company-data"></a>**Eliminar datos de la compañía**
Quita solo los datos de empresa administrados por Intune. No se quitan datos personales del dispositivo. Intune ya no administra el dispositivo y este dejará de poder acceder a recursos corporativos (no aplicable a dispositivos Windows unidos a Azure Active Directory).

### <a name="factory-reset"></a>**Restablecimiento de la configuración de fábrica**
Devuelve el dispositivo a su configuración predeterminada. Intune ya no administrará el dispositivo y se quitan tanto los datos de la compañía como los personales. No se puede deshacer esta acción.

### <a name="remote-lock"></a>**Bloqueo remoto**
Bloquea el dispositivo. El propietario del dispositivo debe usar su contraseña para desbloquearlo. Solo puede bloquear de forma remota un dispositivo que tenga definidos un PIN o una contraseña.

### <a name="reset-passcode"></a>**Restablecer el código de acceso**
Genera una contraseña para el dispositivo que se muestra en la hoja <*nombre del dispositivo*> **Información general**.

### <a name="bypass-activation-lock"></a>**Omitir bloqueo de activación**
Esta acción quita el bloqueo de activación de un dispositivo iOS sin la contraseña y el identificador de Apple. Cuando se omite el bloqueo de activación, el dispositivo activa de nuevo el bloqueo de activación cuando se inicia la aplicación Buscar mi iPhone. Omita el bloqueo de activación solo si tiene acceso físico al dispositivo.

### <a name="fresh-start"></a>**Fresh Start**

Quita todas las aplicaciones que se instalaron en un equipo Windows 10 que ejecuta Creators Update y, luego, actualiza automáticamente el equipo a la versión más reciente de Windows.
Esto puede servir para ayudar a quitar las aplicaciones de OEM preinstaladas que a menudo se entregan con los nuevos equipos. Puede configurar si se conservan los datos de usuario cuando se lleva a cabo esta acción de dispositivo. En este caso, se quitan las aplicaciones y la configuración, pero se conserva el contenido de la carpeta de inicio de los usuarios.


### <a name="lost-mode"></a>**Modo Perdido**
Si un dispositivo iOS se ha robado o perdido, puede habilitar Modo Perdido. Esto le permite especificar un mensaje y un número de teléfono que se mostrarán en la pantalla de bloqueo del dispositivo. Para ello:
1.    En la hoja de propiedades de un dispositivo iOS, elija **Más** > **Modo Perdido**.
2.    En la hoja **Modo Perdido**, habilite Modo Perdido, escriba el mensaje que se mostrará y un número de teléfono de contacto (opcional).
3.    Haga clic en **Aceptar**.
Al habilitar Modo Perdido, se bloquea el uso del dispositivo al completo. El usuario final no puede acceder al dispositivo hasta que deshabilite Modo Perdido. Mientras Modo Perdido esté habilitado, puede utilizar la acción **Buscar dispositivo** para averiguar dónde está el dispositivo.
Para usar el Modo Perdido, el dispositivo debe ser un dispositivo iOS de la empresa, inscrito mediante DEP, que esté en modo supervisado.

### <a name="locate-device"></a>**Buscar dispositivo**
Use esta acción remota para mostrar la ubicación de un dispositivo iOS perdido o robado en un mapa. El dispositivo debe ser un dispositivo iOS de la empresa, inscrito mediante DEP, que esté en modo supervisado. Antes de realizar esta acción, el dispositivo debe tener habilitado Modo Perdido.
1.    En la hoja de propiedades de un dispositivo iOS, elija **Más** > **Buscar dispositivo**.
2.    Cuando se haya localizado el dispositivo, se muestra su ubicación en la hoja **Buscar dispositivo**.
    ![Hoja Buscar dispositivo](./media/locate-device.png)

>[!NOTE]
>Por motivos de privacidad, se limita la distancia con la que puede hacer zoom en el mapa.

### <a name="restart"></a>**Reiniciar**
Hace que el dispositivo se reinicie. Como al propietario del dispositivo no se le informa automáticamente del reinicio, podría perder trabajo.


## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>Información de seguridad y privacidad de las acciones Modo Perdido y Buscar dispositivo
- No se envía ningún dato relacionado con la ubicación del dispositivo a Intune hasta que active esta acción.
- Cuando se usa la acción Buscar dispositivo, las coordenadas de latitud y longitud del dispositivo se envían a Intune y se muestran en Azure Portal.
- Los datos se almacenan durante 24 horas y, más adelante, se eliminan. No se puede quitar manualmente la información de ubicación.
- Los datos de ubicación permanecen cifrados mientras están almacenados y transmitiéndose.
- Al configurar Modo Perdido, se recomienda que el mensaje que escriba y que se muestra en la pantalla de bloqueo incluya información para que se puede determinar la ubicación del dispositivo.

