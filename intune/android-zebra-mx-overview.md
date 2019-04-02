---
title: Usar las extensiones de movilidad de cebra en dispositivos Android en Microsoft Intune - Azure | Microsoft Docs
description: Usar Microsoft Intune para administrar y usar dispositivos de cebra que ejecutan Android con las extensiones de movilidad de cebra (MX). Ver todos los pasos, como instalar la aplicación de Portal de empresa, transferir localmente la aplicación, asigne el rol de administrador de dispositivos, cree un perfil StageNow y mucho más.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa2734247569245794bce7fe1de68c8b20c6091f
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490611"
---
# <a name="use-and-manage-zebra-devices-with-zebra-mobility-extensions-in-microsoft-intune"></a>Usar y administrar dispositivos de cebra con extensiones de movilidad de cebra en Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune incluye un amplio conjunto de características, incluida la administración de aplicaciones y configuración de dispositivo. Estas características integradas y la configuración se usa para administrar dispositivos Android fabricados por Zebra Technologies, también conocido como "dispositivos cebra".

Si desea personalizar o agregar más configuraciones de cebra específicos, también puede usar Zebra **extensiones de movilidad (MX)** en estos dispositivos. 

Esta característica se aplica a:

- Android

La empresa puede usar dispositivos de cebra de venta directa, en la fábrica y mucho más. Por ejemplo, eres minorista y su entorno incluye miles de dispositivos móviles de cebra usados por los socios comerciales. Intune puede ayudar a administrar estos dispositivos como parte de la solución de administración (MDM) de dispositivos móviles.

Con Intune, puede inscribir dispositivos cebra para implementar las aplicaciones de línea de negocio en los dispositivos. Perfiles de "Configuración del dispositivo" le permiten crear perfiles de MX para administrar la configuración específica de cebra.

Este artículo muestra cómo usar las extensiones de movilidad de cebra (MX) en dispositivos de cebra en Microsoft Intune.

## <a name="before-you-begin"></a>Antes de comenzar

- Asegúrese de que tener la versión más reciente de la aplicación de escritorio StageNow desde Zebra Technologies.
- No olvide consultar [matriz de características de cebra completa MX](http://techdocs.zebra.com/mx/compatibility) (abre el sitio web de cebra) para confirmar los perfiles creados son compatibles con la versión del sistema operativo, versión MX y modelo del dispositivo.
- Ciertos dispositivos, como TC20/25, no admiten todas las características disponibles de MX en StageNow. No olvide consultar [matriz de características de cebra](http://techdocs.zebra.com/mx/tc2x/) (abre el sitio web de cebra) para obtener información de compatibilidad actualizada.

## <a name="step-1-install-the-latest-company-portal-app"></a>Paso 1: Instalar la aplicación de Portal de empresa más reciente

En el dispositivo, vaya a la tienda Google Play y descargue e instale la aplicación de Portal de empresa de Microsoft. Cuando se instala desde Google Play, la aplicación de Portal de empresa obtiene actualizaciones y correcciones automáticamente.

Si Google Play no está disponible, descargue el [Portal de empresa de Microsoft Intune para Android](https://www.microsoft.com/download/details.aspx?id=49140) (abre otro sitio Web de Microsoft), y [transferir localmente](#sideload-the-company-portal-app) (en este artículo). Cuando se instala este modo, la aplicación no recibe las actualizaciones o correcciones automáticamente. Periódicamente, debe actualizar y aplicar revisiones a la aplicación manualmente.

### <a name="sideload-the-company-portal-app"></a>Instalación de prueba de la aplicación Portal de empresa

"Instalación de prueba" es cuando no utilice Google Play para instalar una aplicación. Para transferir localmente la aplicación de Portal de empresa, use StageNow. 

Los pasos siguientes proporcionan una visión general. Para obtener información detallada, consulte la documentación de cebra. [Inscribirse en una MDM usando StageNow](http://techdocs.zebra.com/stagenow/3-1/Profiles/enrollmdm/) (abre el sitio web de cebra) puede ser un buen recurso.

1. En StageNow, cree un perfil para **inscribir en MDM**.
2. En **implementación**, elija descargar el archivo del agente MDM.
3. Establecer el **compatibilidad con aplicaciones** y **descargar configuración** los pasos para **No**.
4. En **descargar MDM**, seleccione **transferencia o copiar archivo**. Agregar el origen y destino del paquete de Portal de empresa Android (APK).
5. En **iniciar MDM**, deje los valores predeterminados como-es. Agregue estos detalles:

    - **Nombre del paquete**: `com.microsoft.windowsintune.companyportal`
    - **Nombre de clase**: `com.microsoft.windowsintune.companyportal.views.SplashActivity`

Seguir el perfil de publicación y usarla con la aplicación StageNow en el dispositivo. Instala la aplicación de Portal de empresa y abierta en el dispositivo.

> [!TIP]
> Para obtener más información sobre StageNow y lo que hace, consulte [almacenamiento provisional de dispositivos StageNow Android](https://www.zebra.com/us/en/products/software/mobile-computers/mobile-app-utilities/stagenow.html) (abre el sitio web de cebra).

## <a name="step-2-confirm-the-company-portal-app-has-device-administrator-role"></a>Paso 2: Confirmar que la aplicación de Portal de empresa tiene el rol de administrador de dispositivos

La aplicación de Portal de empresa requiere que el Administrador de dispositivos para administrar dispositivos Android. Para activar el rol de administrador de dispositivos, algunos dispositivos cebra incluyen una interfaz de usuario (UI) en el dispositivo. Si el dispositivo incluye una interfaz de usuario, la aplicación de Portal de empresa le pide al usuario final que conceda el Administrador de dispositivos durante [inscripción](#step-3-enroll-the-device-in-to-intune) (en este artículo).

Si una interfaz de usuario no está disponible, utilice el **DevAdmin Manager** en StageNow para crear un perfil que concede el Administrador de dispositivos a la aplicación de Portal de empresa manualmente.

Los pasos siguientes proporcionan una visión general. Para obtener información detallada, consulte la documentación de cebra. 
[Establecer el modo de intercambio de la batería como administrador de dispositivos](https://zebratechnologies.force.com/s/article/Set-Battery-Swap-Mode-as-Device-Administrator-using-StageNow-Tool) (abre el sitio Web de cebra) puede ser un buen recurso.

1. En StageNow, cree un perfil y seleccione **modo Xpert**.
2. Agregar **DevAdmin Manager** al perfil.
3. Establecer **acción de administración de dispositivos** a **activar administrador del dispositivo como**.
4. Establecer **el nombre del paquete de administración de dispositivos** a `com.microsoft.windowsintune.companyportal`.
5. Establecer **nombre de la clase de administración de dispositivos** a `com.microsoft.omadm.client.PolicyManagerReceiver`.

Seguir el perfil de publicación y usarla con la aplicación StageNow en el dispositivo. La aplicación de Portal de empresa se concede el rol de administrador de dispositivos.

## <a name="step-3-enroll-the-device-in-to-intune"></a>Paso 3: Inscribir el dispositivo en Intune

Después de completar los dos primeros pasos, la aplicación de Portal de empresa está instalada en el dispositivo. El dispositivo está listo para inscribirse en Intune.

[Inscribir dispositivos Android](android-enroll.md) se enumeran los pasos. Si tiene muchos dispositivos cebra, desear utilizar un [cuenta de administrador de inscripción de dispositivos](device-enrollment-manager-enroll.md).

## <a name="step-4-create-a-device-management-profile-in-stagenow"></a>Paso 4: Crear un perfil de administración de dispositivos en StageNow

Use StageNow para crear un perfil que configura las opciones que desea administrar en el dispositivo. Para obtener información detallada, consulte la documentación de cebra. [Perfiles](http://techdocs.zebra.com/stagenow/3-2/stagingprofiles/) (abre el sitio Web de cebra) puede ser un buen recurso.

Al crear el perfil en StageNow, en el último paso, seleccione **exportar a MDM**. Esto genera un archivo XML. Guarde este archivo. Lo necesitará en un paso posterior.

> [!TIP]
> Se recomienda para probar el perfil antes de implementarla en los dispositivos de su organización. Para probar, en el último paso al crear perfiles con StageNow en el equipo, use el **probar** opciones. A continuación, consumir el archivo generado StageNow con la aplicación StageNow en el dispositivo. 
> 
> La aplicación StageNow en el dispositivo muestra los registros generados cuando se prueba el perfil. [Los registros de uso StageNow en dispositivos de cebra que ejecutan Android en Intune](android-zebra-mx-logs-troubleshoot.md) tiene información sobre el uso de registros StageNow para entender los errores.

> [!NOTE]
> Si hacen referencia a las aplicaciones, paquetes de actualización o actualizar otros archivos en su perfil StageNow, desea que el dispositivo para obtener estas actualizaciones. Para obtener las actualizaciones, el dispositivo debe conectarse al servidor de implementación de StageNow cuando se aplica el perfil. 
> 
> O bien, puede usar las características integradas en Intune para obtener estos cambios, incluyendo: 
> - Características de administración de aplicaciones a [agregar](apps-add.md), [implementar](apps-deploy.md), actualizar, y [monitor](apps-monitor.md) aplicaciones.
> - Administrar [actualizaciones del sistema y aplicación](device-restrictions-android-for-work.md#device-owner-only) en dispositivos que ejecutan Android Enterprise

Después de probar el archivo, el siguiente paso es implementar el perfil en dispositivos con Intune.

> [!NOTE]
> Implementar un perfil para cada dispositivo. Si hay varios perfiles StageNow que desea implementar en los dispositivos, a continuación, exporte los perfiles StageNow y combinar la configuración en un único archivo XML antes de agregarla a Intune. 
> 
> No desea dos configuraciones que configuración la misma propiedad en el mismo archivo XML. El objetivo es evitar conflictos entre la configuración del dispositivo.

## <a name="step-5-create-a-profile-in-intune"></a>Paso 5: Crear un perfil de Intune

En Intune, cree un perfil de configuración de dispositivo:

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Intune**.
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre descriptivo para el nuevo perfil.
    - **Descripción**: escriba una descripción para el perfil Esta configuración es opcional pero recomendada.
    - **Plataforma**: seleccione **Android**.
    - **Tipo de perfil**: seleccione **perfil MX (solo cebra)**.

4. En **perfil MX en el formato .xml**, agregue el archivo de perfil XML [haya exportado desde StageNow](#step-4-create-a-device-management-profile-in-stagenow) (en este artículo).
5. Seleccione **Aceptar** > **Crear** para guardar los cambios. La directiva se crea y se muestra en la lista.

Se crea el perfil, pero todavía no hace nada. Después, [asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

La próxima vez que el dispositivo se registra para las actualizaciones de configuración, el perfil de MX se implementa en el dispositivo. Sincronizar dispositivos con Intune cuando se inscriben los dispositivos y, a continuación, cada 8 horas aproximadamente. También puede [forzar una sincronización en Intune](device-sync.md). O bien, en el dispositivo, abra el **aplicación Portal de empresa** > **configuración** > **sincronización**. 

> [!TIP]
> - Por motivos de seguridad, no verá el texto XML de perfil después de guardarlo. El texto está cifrado, y solo verá asteriscos (`****`). Como referencia, se recomienda para guardar copias de los perfiles de MX antes de agregarlos a Intune.
> 
> - Para actualizar un perfil de una vez que se asigna a dispositivos de cebra, cree un archivo StageNow XML actualizado, edite el perfil de Intune existente y agregar el nuevo archivo StageNow XML. Este nuevo archivo sobrescribe la anterior directiva StageNow en el perfil.

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

[Usar StageNow registros para solucionar problemas de dispositivos de cebra](android-zebra-mx-logs-troubleshoot.md).
