---
title: Supervisión de las directivas de protección de aplicaciones
titleSuffix: Microsoft Intune
description: En este tema se describe cómo configurar las directivas de protección de aplicaciones en Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 000b1d04dd3f520b55b1d33545a8803e23bf8965
ms.sourcegitcommit: 0d6f323152ec62f7d383891cce12ea0a4289cd8f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2019
ms.locfileid: "72889587"
---
# <a name="how-to-monitor-app-protection-policies"></a>Supervisión de las directivas de protección de aplicaciones
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Puede supervisar el estado de cumplimiento de las directivas de administración de aplicaciones móviles (MAM) que haya aplicado a los usuarios en el panel de protección de aplicaciones de Intune [Azure Portal](https://portal.azure.com). Además, podrá encontrar información sobre los usuarios afectados por las directivas MAM, el estado de cumplimiento de las directivas MAM y cualquier problema que puedan estar experimentando los usuarios finales.

Hay tres lugares diferentes desde donde se pueden supervisar las directivas de protección de aplicaciones:
- Vista Resumen
- Vista detallada
- Generación de informes

> [!NOTE]
> Para obtener más información, consulte [Creación y asignación de directivas de protección de aplicaciones](app-protection-policies.md).

El período de retención de los datos de protección de la aplicación es de 90 días. Las instancias de aplicación que se han protegido en el servicio MAM en los últimos 90 días se incluyen en el informe de estado de protección de la aplicación. Una *instancia de aplicación* es un usuario único + aplicación + dispositivo. 

## <a name="summary-view"></a>Vista Resumen

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. En el panel **Intune**, seleccione **Aplicaciones cliente**.
4. Para ver la vista de resumen, en la carga de trabajo **Aplicaciones cliente**, en **Supervisar**, elija **Estado de protección de la aplicación**.

   ![Captura de pantalla del icono Resumen en el panel de administración de aplicaciones móviles de Intune](./media/app-protection-policies-monitor/app-protection-user-status-summary.png)

- **Usuarios asignados**: número total de usuarios asignados en la empresa que usan una aplicación que está asociada a una directiva en un contexto profesional, que está protegida y que tiene una licencia, así como los usuarios asignados que están desprotegidos y que non tienen ninguna licencia.
- **Usuarios marcados**: número de usuarios que experimentan problemas con los dispositivos. Los dispositivos liberados (iOS y Android) se notifican en **Usuarios marcados**. Además, aquí se notifican los usuarios con dispositivos marcados por la comprobación de atestación de dispositivo Google SafetyNet (si el administrador de TI la activó). 
- **Usuarios con aplicaciones potencialmente perjudiciales**: el número de usuarios que pueden tener una aplicación perjudicial en su dispositivo Android detectado por Google Play Protect. 
- **Estado de usuario para iOS** y **Estado del usuario para Android**: número de usuarios que han usado una aplicación que tiene una directiva asignada a ellos en un contexto profesional en la plataforma relacionada. Esta información muestra el número de usuarios que administra la directiva, así como el número de usuarios que usan una aplicación que no es el destino de ninguna directiva en un contexto profesional. Considere la posibilidad de agregar estos usuarios a la directiva.
- **Principales aplicaciones iOS protegidas**: según las aplicaciones iOS más usadas, esta información muestra la cantidad de aplicaciones iOS protegidas y no protegidas.
- **Principales aplicaciones Android protegidas**: según las aplicaciones Android más usadas, esta información muestra la cantidad de aplicaciones Android protegidas y no protegidas.
- **Principales aplicaciones iOS configuradas sin inscripción**: según las aplicaciones iOS más usadas para dispositivos no inscritos, esta información muestra la cantidad de aplicaciones iOS configuradas.
- **Principales aplicaciones Android configuradas sin inscripción**: según las aplicaciones Android más usadas para dispositivos no inscritos, esta información muestra la cantidad de aplicaciones Android configuradas.

    > [!NOTE]
    > Si tiene varias directivas por plataforma, se considerará que un usuario está administrado por una directiva cuando tenga al menos una directiva asignada.

## <a name="detailed-view"></a>Vista detallada
Puede obtener la vista detallada del resumen si selecciona los iconos de **Estado del usuario** (según la plataforma del sistema operativo del dispositivo), de **Usuarios con aplicaciones potencialmente perjudiciales** y de **Usuarios marcados**.

### <a name="user-status"></a>Estado del usuario
Puede buscar un solo usuario y examinar su estado de cumplimiento. En el panel **Informes de aplicaciones** se muestra la siguiente información sobre el usuario seleccionado:
- **Icono**: muestra si el estado de la aplicación está actualizado.
- **Nombre de la aplicación**: nombre de la aplicación.
- **Nombre del dispositivo**: dispositivos asociados con la cuenta del usuario.
- **Tipo del dispositivo**: tipo de dispositivo o sistema operativo que el dispositivo ejecuta.
- **Directivas**: directivas asociadas con la aplicación.
- **Estado**:
  - **Protegido**: significa que la directiva se implementó para el usuario y que la aplicación se usó al menos una vez en el contexto de trabajo.
  - **No protegido**: significa que la directiva se implementó para el usuario, pero la aplicación no se ha usado desde entonces en el contexto de trabajo.
- **Última sincronización**: hora de la última sincronización de la aplicación con Intune. 

>[!NOTE]
> La columna **Última sincronización** representa el mismo valor tanto en el informe de estado de usuario de la consola como en el [informe .csv exportable](https://docs.microsoft.com/intune/app-protection-policies-monitor#export-app-protection-activities) de la directiva de protección de aplicaciones. La diferencia es un pequeño retraso en la sincronización entre el valor de los dos informes. 
>
> La hora de Última sincronización hace referencia a la última vez que Intune vio la instancia de la aplicación. Cuando un usuario inicia una aplicación, esta puede comunicarse con el servicio de Intune App Protection en el momento del inicio, en función de cuándo se sincronizara por última vez. Vea [las horas del intervalo de reintentos para la sincronización de la directiva de protección de aplicaciones](https://docs.microsoft.com/en-us/intune/app-protection-policy-delivery). Por lo tanto, si un usuario final no ha usado esa aplicación concreta en el último intervalo de sincronización (que suele ser de 30 minutos para el uso activo) e inicia la aplicación, entonces:
>
> - El informe .csv exportable de la directiva de protección de aplicaciones tiene la hora más reciente, desde 1 minuto (mínimo) a 30 minutos (máximo).
> - El informe de estado de usuario tiene la hora más reciente al instante.
>
> Por ejemplo, imagine un usuario final con licencia y dirigido que inicia una aplicación protegida a las 12:00.
> - Si se trata de un primer inicio de sesión, eso significa que el usuario final ha cerrado la sesión antes y no se había registrado la instancia de la aplicación con Intune. Una vez que el usuario inicia sesión, obtiene un nuevo registro de la instancia de la aplicación y se puede sincronizar inmediatamente (con los mismos retardos enumerados anteriormente para las sincronizaciones futuras). Por lo tanto, la hora de la última sincronización sería 12:00 en el informe de estado de usuario, y 12:01 (o 12:30 a más tardar) en el informe de la directiva de protección de aplicaciones. 
> - Si el usuario acaba de iniciar la aplicación,la hora de la última sincronización notificada depende de cuándo se sincronizó por última vez.


Para ver los informes sobre un usuario, siga estos pasos:

1. Para seleccionar un usuario, elija el icono de resumen **Estado del usuario**.

    ![Captura de pantalla del mosaico Resumen en la Administración de aplicaciones móviles de Intune](./media/app-protection-policies-monitor/MAM-reporting-6.png)

2. En el panel **Informes de aplicaciones**, elija **Seleccionar usuario** para buscar un usuario de Azure Active Directory.

    ![Captura de pantalla de la opción Seleccionar usuario en el panel Informes de aplicaciones](./media/app-protection-policies-monitor/MAM-reporting-2.png)

3. Seleccione el usuario de la lista. Podrá ver los detalles del estado de cumplimiento de ese usuario.

>[!NOTE]
> Si el usuario que ha buscado no tiene la directiva de MAM implementada, aparecerá un mensaje informándole de que el usuario no es objeto de ninguna directiva de MAM.

### <a name="flagged-users"></a>Usuarios marcados
La vista detallada muestra el mensaje de error, la aplicación a la que se obtuvo acceso cuando se produjo el error, la plataforma del sistema operativo del dispositivo afectada y una marca de hora. El error suele ser para dispositivos liberados (iOS) o modificados (Android). Además, aquí se notifican los usuarios con dispositivos marcados por la comprobación de inicio condicional "atestación de dispositivo SafetyNet" con el motivo indicado por Google. Para que se quite un usuario del informe, es necesario que el estado del propio dispositivo haya cambiado, lo que sucede después de la siguiente comprobación de la detección de modificación (o cuando ocurra la comprobación de dispositivo liberado/SafetyNet), que debe informar de un resultado positivo. Si el dispositivo se corrige realmente, la actualización del informe de usuarios marcados se producirá cuando se vuelva a cargar la hoja.

### <a name="users-with-potentially-harmful-apps"></a>Usuarios con aplicaciones potencialmente perjudiciales
La vista detallada muestra:

- El usuario.
- El identificador del paquete de la aplicación.
- Si la aplicación está habilitada para MAM.
- La categoría de la amenaza.
- El correo electrónico.
- El nombre de dispositivo.
- Una marca de hora.

Aquí se notifican los usuarios con dispositivos marcados por la comprobación de inicio condicional **Requerir examen de amenazas en las aplicaciones** con la categoría de amenaza indicada por Google. Si hay aplicaciones enumeradas en este informe que se implementan a través de Intune, póngase en contacto con el desarrollador de la aplicación pertinente o quite la aplicación de la asignación a los usuarios finales. 

## <a name="reporting-view"></a>Generación de informes

Puede encontrar los mismos informes en la parte superior de la hoja **Estado de protección de la aplicación**.

> [!NOTE]
> Intune proporciona campos adicionales con información sobre el dispositivo, como el identificador de registro de aplicación, el fabricante de Android, el modelo, la versión de la revisión de seguridad y el modelo de iOS. En Intune, se accede a estos campos seleccionando **Aplicaciones cliente** > **Estado de protección de aplicaciones** > **Informe de protección de aplicaciones: iOS, Android**. Además, estos parámetros lo ayudan a configurar la lista de **admitidos** correspondiente al fabricante de dispositivo (Android), la lista de **admitidos** del modelo de dispositivo (iOS y Android) y la configuración de versión de la revisión de seguridad mínima de Android. 

Hay informes adicionales disponibles que le ayudarán con el estado de cumplimiento de directivas MAM. Para ver estos informes, seleccione **Aplicaciones cliente** > **Estado protección de la aplicación** > **Informes**. 

En la hoja **Informes** se proporcionan varios informes basados en el usuario y la aplicación, incluidos los siguientes:

- **Informe de usuario**: en este informe, se describe la misma información que puede encontrar en el informe **Estado del usuario** de la sección [Vista detallada](app-protection-policies-monitor.md#detailed-view) anterior.

- **Informe de aplicación**: además de seleccionar la plataforma y la aplicación, en este informe se proporcionan dos estados de protección de aplicación distintos que puede seleccionar antes de generar el informe. Los estados pueden ser **Protegido** o **Desprotegido**.

  - Estado de usuario para la actividad de MAM administrada (**protegido**): este informe resume la actividad de cada aplicación MAM administrada por el usuario. Muestra todas las aplicaciones a las que se dirigen las directivas MAM para cada usuario y el estado de cada aplicación registrada con directivas MAM. El informe también incluye el estado de cada aplicación destinada a una directiva de MAM que no se haya registrado nunca.
  - Estado de usuario para la actividad de MAM sin administrar (**desprotegido**): este informe resume la actividad de las aplicaciones habilitadas por MAM que están sin administrar actualmente por el usuario. Esto puede ocurrir porque:
    - Estas aplicaciones están siendo utilizadas por un usuario o una aplicación que no está destinada actualmente mediante una directiva MAM.
    - Todas las aplicaciones están registradas, pero no reciben ninguna directiva MAM.

    ![Captura de pantalla de la hoja Informes de aplicaciones de un usuario con detalles de tres aplicaciones](./media/app-protection-policies-monitor/MAM-reporting-4.png)

- **Informe de configuración del usuario**: según un usuario seleccionado, en este informe se proporcionan detalles sobre cualquier configuración de aplicación que haya recibido el usuario.
- **Informe de configuración de la aplicación**: según una aplicación y plataforma seleccionada, en este informe se proporcionan detalles sobre qué usuarios han recibido configuraciones para la aplicación seleccionada.
- **Informe de aprendizaje de aplicación para Windows Information Protection**: en este informe se muestran las aplicaciones que intentan cruzar los límites de las directivas.
- **Aprendizaje de sitio web para Windows Information Protection**: en este informe se muestran los sitios web que intentan cruzar los límites de las directivas.

## <a name="table-grouping"></a>Agrupación de tablas

Cuando se muestren los datos del **informe de usuario de protección de aplicaciones**, puede agregar datos de las siguientes maneras:

- **Resultado de la validación:** los datos aparecen agrupados por estado de protección de la aplicación, que puede ser de error, advertencia o correcto.
- **Nombre de la aplicación**: Los datos se agrupan por el nombre real de la aplicación. De nuevo, el estado puede ser de error, advertencia o correcto.

## <a name="export-app-protection-activities"></a>Exportación de actividades de protección de aplicaciones

Puede exportar todas las actividades de directiva de protección de aplicaciones a un archivo .csv único. Esto puede resultar útil para analizar todos los estados de protección de aplicaciones notificados por los usuarios.

Siga estos pasos para generar el informe de protección de aplicaciones:

1. En el panel Administración de aplicaciones móviles de Intune, elija **Informe de protección de la aplicación**.

    ![Captura de pantalla del vínculo de descarga de Protección de aplicaciones](./media/app-protection-policies-monitor/app-protection-report-csv-2.png)

2. Elija **Sí** para guardar el informe y, a continuación, elija **Guardar como**. Seleccione la carpeta donde desee guardar el informe.

    ![Captura de pantalla del cuadro de diálogo de confirmación de Guardar informe](./media/app-protection-policies-monitor/app-protection-report-csv-1.png)

## <a name="see-also"></a>Consulte también
- [Administrar la transferencia de datos entre aplicaciones iOS](data-transfer-between-apps-manage-ios.md)
- [What to expect when your Android app is managed by app protection policies](../fundamentals/end-user-mam-apps-android.md) (Qué esperar cuando la aplicación Android se administra con directivas de protección de aplicaciones)
- [What to expect when your iOS app is managed by app protection policies](../fundamentals/end-user-mam-apps-ios.md) (Qué esperar cuando la aplicación iOS se administra con directivas de protección de aplicaciones)
