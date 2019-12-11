---
title: 'Usar las extensiones de movilidad de Zebra para dispositivos Android en Microsoft Intune: Azure | Microsoft Docs'
description: Use Microsoft Intune para administrar y usar dispositivos de Zebra que ejecutan Android con las extensiones de movilidad (MX) de Zebra. Vea todos los pasos, incluido instalar la aplicación de Portal de empresa, transferir localmente la aplicación, asignar el rol de administrador de dispositivos, crear un perfil StageNow y mucho más.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: jieyan
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 829d8f6b2691f91c14029e4f29e2ef11b070e596
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059615"
---
# <a name="use-and-manage-zebra-devices-with-zebra-mobility-extensions-in-microsoft-intune"></a>Usar y administrar dispositivos Zebra con extensiones de movilidad de Zebra en Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune incluye un amplio conjunto de características, incluidas la administración de aplicaciones y la configuración de los ajustes del dispositivo. Estas características y ajustes integrados administran dispositivos Android fabricados por Zebra Technologies, también conocidos como "dispositivos Zebra".

En dispositivos Android, use perfiles de **extensiones de movilidad (MX)** de Zebra para personalizar o agregar más ajustes específicos de Zebra.

Este artículo muestra cómo usar las extensiones de movilidad (MX) de Zebra en dispositivos Zebra en Microsoft Intune.

Esta característica se aplica a:

- Android

La empresa puede usar dispositivos Zebra para venta minorista, en la fábrica y mucho más. Por ejemplo, es un minorista y su entorno incluye miles de dispositivos móviles Zebra que usan los socios comerciales. Intune puede ayudarle a administrar estos dispositivos como parte de la solución de administración de dispositivos móviles (MDM).

Con Intune, puede inscribir dispositivos Zebra para implementar en los dispositivos las aplicaciones de línea de negocio. Los perfiles de "Configuración de dispositivo" le permiten crear perfiles de MX para administrar los ajustes específicos de Zebra.

> [!NOTE]
> De forma predeterminada, las API de Zebra MX no se bloquean en los dispositivos. Antes de que un dispositivo se inscriba en Intune, es posible que el dispositivo esté en peligro de manera malintencionada. Cuando el dispositivo se encuentra en un estado limpio, le sugerimos que bloquee las API MX mediante el administrador de acceso (AccessMgr). Por ejemplo, puede elegir que solo el Portal de empresa aplicación y las aplicaciones en las que confía tengan permiso para llamar a las API MX.
>
> Para obtener más información, consulte [bloquear el dispositivo en el](https://developer.zebra.com/community/home/blog/2017/04/11/locking-down-your-device) sitio web de Zebra.

## <a name="before-you-begin"></a>Antes de comenzar

- Asegúrese de que tiene la versión más reciente de la aplicación de escritorio StageNow de Zebra Technologies.
- No olvide consultar la [matriz de características de MX completa de Zebra](http://techdocs.zebra.com/mx/compatibility) (abre el sitio web de Zebra) para confirmar que los perfiles creados son compatibles con la versión del sistema operativo, versión de MX y modelo del dispositivo.
- Ciertos dispositivos, como TC20/25, no admiten todas las características disponibles de MX en StageNow. No olvide consultar la [matriz de características de Zebra](http://techdocs.zebra.com/mx/tc2x/) (abre el sitio web de Zebra) para obtener información de compatibilidad actualizada.

## <a name="step-1-install-the-latest-company-portal-app"></a>Paso 1: instalar la aplicación Portal de empresa más reciente.

En el dispositivo, abra el almacén de Google Play. Descargue e instale la aplicación Portal de empresa de Intune de Microsoft. Cuando se instala desde Google Play, la aplicación del Portal de empresa obtiene actualizaciones y correcciones automáticamente.

Si Google Play no está disponible, descargue el [Portal de empresa de Microsoft Intune para Android](https://www.microsoft.com/download/details.aspx?id=49140) (abre otro sitio web de Microsoft), y [transfiéralo localmente](#sideload-the-company-portal-app) (en este artículo). Cuando se instala este modo, la aplicación no recibe las actualizaciones o correcciones automáticamente. Asegúrese de actualizar y aplicar revisiones periódicamente a la aplicación de forma manual.

### <a name="sideload-the-company-portal-app"></a>Instalación de prueba de la aplicación Portal de empresa

"Transferir localmente" es cuando no usa Google Play para instalar una aplicación. Para transferir localmente la aplicación Portal de empresa use StageNow. 

Los pasos siguientes proporcionan una visión general. Para obtener información detallada, consulte la documentación de Zebra. [Enroll in an MDM using StageNow](http://techdocs.zebra.com/stagenow/3-1/Profiles/enrollmdm/) (Inscribirse en una MDM mediante StageNow; abre el sitio web de Zebra) puede ser un buen recurso.

1. En StageNow, cree un perfil para **inscribir en MDM**.
2. En **Implementación**, elija descargar el archivo del agente MDM.
3. Establezca los pasos **Compatibilidad con aplicaciones** y **Descargar configuración** para **No**.
4. En **Descargar MDM**, seleccione **Transferencia o Copiar archivo**. Agregue el origen y destino del paquete de Portal de empresa Android (APK).
5. En **Iniciar MDM**, deje los valores predeterminados como-estn. Agregue estos detalles:

    - **Nombre del paquete**: `com.microsoft.windowsintune.companyportal`
    - **Nombre de clase**: `com.microsoft.windowsintune.companyportal.views.SplashActivity`

Vaya a publicar en el perfil de publicación y personalícelo con StageNow en el dispositivo. La aplicación Portal de empresa se instala y se abre en el dispositivo.

> [!TIP]
> Para obtener más información sobre StageNow y lo que hace, consulte [StageNow Android device staging](https://www.zebra.com/us/en/products/software/mobile-computers/mobile-app-utilities/stagenow.html) (Almacenamiento provisional de dispositivos Android Stage Now) (abre el sitio web de Zebra).

## <a name="step-2-confirm-the-company-portal-app-has-device-administrator-role"></a>Paso 2: confirmar que la aplicación Portal de empresa tiene un rol de administrador de dispositivos.

La aplicación de Portal de empresa requiere un administrador de dispositivos para administrar dispositivos Android. Para activar el rol de administrador de dispositivos, algunos dispositivos Zebra incluyen una interfaz de usuario (IU) en el dispositivo. Si el dispositivo incluye una interfaz de usuario, la aplicación de Portal de empresa le pide al usuario final que proporcione un administrador de dispositivos durante la [inscripción](#step-3-enroll-the-device-in-to-intune) (en este artículo).

Si no hay disponible una interfaz de usuario, use el **administrador DevAdmin** en StageNow para crear un perfil que proporcione manualmente un administrador de dispositivos a la aplicación de Portal de empresa.

Los pasos siguientes proporcionan una visión general. Para obtener información detallada, consulte la documentación de Zebra. 
[Establecer el modo de intercambio de la batería como administrador de dispositivos](https://zebratechnologies.force.com/s/article/Set-Battery-Swap-Mode-as-Device-Administrator-using-StageNow-Tool) (abre el sitio Web de Zebra) puede ser un buen recurso.

1. En StageNow, cree un perfil y seleccione **modo Xpert**.
2. Agregue **Administrador de DevAdmin** al perfil.
3. Establezca la **acción de administración de dispositivos** en **activar como administrador del dispositivo**.
4. Establezca **Nombre del paquete de administración de dispositivos** en `com.microsoft.windowsintune.companyportal`.
5. Establezca **Nombre de la clase de administración de dispositivos** en `com.microsoft.omadm.client.PolicyManagerReceiver`.

Vaya a publicar en el perfil de publicación y personalícelo con StageNow en el dispositivo. La aplicación Portal de empresa tiene un rol de administrador de dispositivos.

## <a name="step-3-enroll-the-device-in-to-intune"></a>Paso 3: Inscribir el dispositivo en Intune

Después de completar los dos primeros pasos, la aplicación Portal de empresa está instalada en el dispositivo. Ya puede inscribir el dispositivo en Intune.

[Inscribir dispositivos Android](../enrollment/android-enroll.md) se enumeran los pasos. Si tiene muchos dispositivos Zebra, puede que quiera usar una [cuenta de administrador de inscripciones de dispositivos (DEM)](../enrollment/device-enrollment-manager-enroll.md). Usar una cuenta DEM también quita la opción para anular la inscripción desde la aplicación de Portal de empresa, para que los usuarios no puedan anular la inscripción del dispositivo tan fácilmente.

## <a name="step-4-create-a-device-management-profile-in-stagenow"></a>Paso 4: Crear un perfil de administración de dispositivos en StageNow

Use StageNow para crear un perfil que configure las opciones que quiere administrar en el dispositivo. Para obtener información detallada, consulte la documentación de Zebra. [Perfiles](http://techdocs.zebra.com/stagenow/3-2/stagingprofiles/) (abre el sitio web de Zebra) puede ser un buen recurso.

Al crear el perfil en StageNow, en el último paso, seleccione **Export to MDM** (Exportar a MDM). Este paso genera un archivo XML. Guarde este archivo. Lo necesitará en un paso posterior.

- Se recomienda que pruebe el perfil antes de implementarlo en los dispositivos de su organización. Para ello, en el último paso al crear perfiles con StageNow en el equipo, use las opciones **Probar**. A continuación, consuma el archivo generado por StageNow con la aplicación StageNow en el dispositivo.

  La aplicación StageNow en el dispositivo muestra los registros generados cuando se prueba el perfil. En [Use StageNow logs on Zebra devices running Android in Intune](android-zebra-mx-logs-troubleshoot.md) (Usar los registros de StageNow en dispositivos Zebra que ejecutan Android en Intune) hay información sobre el uso de los registros StageNow para entender los errores.

- Si hace referencia a las aplicaciones, actualiza paquetes o actualizar otros archivos en su perfil de StageNow, querrá que el dispositivo obtenga estas actualizaciones. Para ello, el dispositivo debe conectarse al servidor de implementación de StageNow cuando se aplica el perfil. 

  O bien, puede usar las características integradas en Intune para obtener estos cambios, incluyendo:

  - Características de administración de aplicaciones para [agregar](../apps/apps-add.md), [implementar](../apps/apps-deploy.md), actualizar, y [supervisar](../apps/apps-monitor.md) aplicaciones.
  - Administrar [actualizaciones del sistema y de aplicaciones](device-restrictions-android-for-work.md#device-owner-only) en dispositivos que ejecutan Android Enterprise.

Después de probar el archivo, el siguiente paso es implementar el perfil en dispositivos con Intune.

- Puede implementar uno o varios perfiles MX en un dispositivo.
- También puede exportar varios perfiles de StageNow y combinarlos en un solo archivo XML. Después, cargue el archivo XML en Intune para implementarlo en los dispositivos.

  > [!WARNING]
  > Si hay varios perfiles MX destinados al mismo grupo y configura la misma propiedad, habrá conflictos en el dispositivo.
  >
  > Si la misma propiedad se configura varias veces en un único perfil MX, prevalece la última configuración.

## <a name="step-5-create-a-profile-in-intune"></a>Paso 5: crear un perfil en Intune

En Intune, cree un perfil de configuración de dispositivo:

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.
3. Escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre descriptivo para el nuevo perfil.
    - **Descripción**: escriba una descripción para el perfil Esta configuración es opcional pero recomendada.
    - **Plataforma**: seleccione **Android**.
    - **Tipo de perfil**: seleccione **perfil de MX (solo Zebra)** .

4. En **Perfil de MX en formato .xml**, agregue el archivo de perfil XML que [exportó desde StageNow](#step-4-create-a-device-management-profile-in-stagenow) (en este artículo).
5. Seleccione **Aceptar** > **Crear** para guardar los cambios. La directiva se crea y se muestra en la lista.

    > [!TIP]
    > Por motivos de seguridad, no verá el texto XML de perfil después de guardarlo. El texto está cifrado, y solo verá asteriscos (`****`). Como referencia, se recomienda que guarde copias de los perfiles de MX antes de agregarlos a Intune.

Se crea el perfil, pero todavía no hace nada. Después, [asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

La próxima vez que el dispositivo se registre para buscar actualizaciones de configuración, el perfil de MX se implementará en el dispositivo. Los dispositivos se sincronizan con Intune cuando se inscriben los dispositivos y, después, cada 8 horas aproximadamente. También puede [forzar una sincronización en Intune](../remote-actions/device-sync.md). O bien, en el dispositivo, abrir la **aplicación de Portal de empresa** > **Configuración** > **Sincronizar**. 

## <a name="update-a-zebra-mx-configuration-after-its-assigned"></a>Actualizar una configuración de Zebra MX después de asignarla

Para actualizar la configuración específica de MX de un dispositivo Zebra, puede: 

- Cree un archivo StageNow XML actualizado, edite el perfil de Intune MX existente y cargue el nuevo archivo XML de StageNow. Este nuevo archivo sobrescribe la directiva anterior en el perfil y reemplaza la configuración anterior.
- Cree un nuevo archivo XML de StageNow que configure diferentes opciones, cree un nuevo perfil de Intune MX, cargue el nuevo archivo XML de StageNow y asígnelo al mismo grupo. Se implementan varios perfiles. Si el nuevo perfil configura valores que ya existen en los perfiles existentes, se producirán conflictos.

## <a name="next-steps"></a>Pasos siguientes

- [Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).
- [Use StageNow logs to troubleshoot Zebra devices](android-zebra-mx-logs-troubleshoot.md) (Usar registros de StageNow para solucionar problemas de dispositivos Zebra).
