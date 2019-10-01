---
title: Uso de registros de StageNow en dispositivos Android Zebra en Microsoft Intune-Azure | Microsoft Docs
description: Vea problemas y soluciones comunes al usar StageNow en dispositivos Android con Microsoft Intune. También puede obtener información sobre cómo obtener registros y ver ejemplos de cómo leer los registros para comprobar si son correctos o errores.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6110476aace30daa27450326aea3f4abd4fb3ea0
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "71303891"
---
# <a name="troubleshoot-and-see-potential-issues-on-android-zebra-devices-in-microsoft-intune"></a>Solucionar problemas y ver los posibles problemas en los dispositivos Android Zebra en Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En Microsoft Intune, puede usar [las extensiones de movilidad Zebra (mx) para administrar dispositivos Android Zebra](android-zebra-mx-overview.md). Cuando se usan dispositivos Zebra, se crean perfiles en StageNow para administrar la configuración y cargarlos en Intune. Intune usa la aplicación StageNow para aplicar la configuración en los dispositivos. La aplicación StageNow también crea un archivo de registro detallado en el dispositivo que se usa para solucionar problemas.

Esta característica se aplica a:

- Android

Por ejemplo, puede crear un perfil en StageNow para configurar un dispositivo. Al crear el perfil de StageNow, el último paso genera un archivo para probar el perfil. Este archivo se usa con la aplicación StageNow en el dispositivo.

En otro ejemplo, creará un perfil en StageNow y lo probará. En Intune, agregue el perfil StageNow y luego asígnelo a los dispositivos Zebra. Al comprobar el estado del perfil asignado, el perfil muestra un estado de alto nivel.

En ambos casos, puede obtener más detalles del archivo de registro de StageNow, que se guarda en el dispositivo cada vez que se aplica un perfil de StageNow.

Algunos problemas no están relacionados con el contenido del perfil de StageNow y no se reflejan en los registros.

En este artículo se muestra cómo leer los registros de StageNow y se enumeran otros posibles problemas con los dispositivos Zebra que es posible que no se reflejen en los registros.

[Usar y administrar dispositivos Zebra con las extensiones de movilidad Zebra](android-zebra-mx-overview.md) tiene más información sobre esta característica.

## <a name="get-the-logs"></a>Obtener los registros

### <a name="use-the-stagenow-app-on-the-device"></a>Uso de la aplicación StageNow en el dispositivo
Cuando se prueba un perfil directamente mediante StageNow en el equipo en, en lugar de usar [Intune para implementar el perfil](android-zebra-mx-overview.md#step-4-create-a-device-management-profile-in-stagenow), la aplicación StageNow del dispositivo guarda los registros de la prueba. Para obtener el archivo de registro, use la opción **más (...)** de la aplicación StageNow en el dispositivo.

### <a name="get-logs-using-android-debug-bridge"></a>Obtención de registros mediante Android Debug Bridge
Para obtener los registros después de que el perfil ya esté implementado con Intune, conecte el dispositivo a un equipo con [Android Debug Bridge (ADB)](https://developer.android.com/studio/command-line/adb) (abre el sitio web de Android).

En el dispositivo, los registros se guardan en `/sdcard/Android/data/com.microsoft.windowsintune.companyportal/files`

### <a name="get-logs-from-email"></a>Obtener registros del correo electrónico
Para obtener los registros después de que el perfil ya se haya implementado con Intune, los usuarios finales pueden enviar por correo electrónico los registros con una aplicación de correo electrónico en el dispositivo. En el dispositivo Zebra, abra el Portal de empresa aplicación y [envíe los registros](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). El uso de la característica enviar registros también crea un identificador de incidente de PowerLift, al que puede hacer referencia si se pone en contacto con el soporte técnico de Microsoft.

## <a name="read-the-logs"></a>Leer los registros

Cuando se examinan los registros, hay un error cada vez que se ve la etiqueta `<characteristic-error>`. Los detalles del error se escriben en la etiqueta `<parm-error>` > propiedad `desc`.

## <a name="error-types"></a>Tipos de error

Los dispositivos Zebra incluyen distintos niveles de informes de errores:

- El CSP no es compatible con el dispositivo. Por ejemplo, el dispositivo no es un dispositivo de telefonía móvil y no tiene un administrador de telefonía móvil.
- La versión MX o OSX no coincide. Cada CSP tiene versiones. Para obtener una matriz de compatibilidad completa, consulte [la documentación de Zebra](http://techdocs.zebra.com/mx/) (abre el sitio web de Zebra).
- El dispositivo notifica otro problema o error.

## <a name="examples"></a>Ejemplos

Por ejemplo, tiene el siguiente perfil de entrada:

```xml
<wap-provisioningdoc>
    <characteristic type="Clock">
        <parm name="AutoTime" value="false"/>
        <parm name="TimeZone" value="GMT-5"/>
        <parm name="Date" value="2014-12-03"/>
        <parm name="Time" value="11:11:11"/>
    </characteristic>
</wap-provisioningdoc>
```

En el registro, el código XML es idéntico a la entrada. Esta salida coincidente significa que el perfil se aplicó correctamente al dispositivo sin errores:

```xml
<wap-provisioningdoc>
    <characteristic type="Clock" version="6.0">
        <parm name="AutoTime" value="false"/>
        <parm name="TimeZone" value="GMT-5"/>
        <parm name="Date" value="2014-12-03"/>
        <parm name="Time" value="11:11:11"/>
    </characteristic>
</wap-provisioningdoc>
```

En otro ejemplo, tiene la siguiente entrada:

```xml
<wap-provisioningdoc>
    <characteristic type="XmlMgr" version="4.2" >
        <parm name="ProcessingMode" value="1"/>
    </characteristic>
    <characteristic type="AppMgr" version="4.2" >
        <parm name="Action" value="Install"/>
        <parm name="APK" value="/sdcard/test.apk"/>
    </characteristic>
</wap-provisioningdoc>
```

El registro muestra un error, ya que contiene una etiqueta `<characteristic-error>`. En este escenario, el perfil intentó instalar un paquete de Android (APK) que no existe en la ruta de acceso dada:

```xml
<wap-provisioningdoc>
    <characteristic type="XmlMgr" version="4.2">
        <parm name="ProcessingMode" value="1"/>
    </characteristic>
    <characteristic-error type="AppMgr" version="5.1" desc="missing">
        <parm-error name="Action" value="Install" desc="apk doesnot exist in the path"/>
        <parm name="APK" value="/sdcard/test.apk"/>
    </characteristic-error>
</wap-provisioningdoc>
```

## <a name="other-potential-issues-with-zebra-devices"></a>Otros posibles problemas con los dispositivos Zebra

En esta sección se enumeran otros posibles problemas que pueden aparecer al usar dispositivos Zebra con el administrador de dispositivos. Estos problemas no se incluyen en los registros de StageNow.

### <a name="android-system-webview-is-out-of-date"></a>Android System WebView no está actualizado

Cuando los dispositivos más antiguos inician sesión con la aplicación Portal de empresa, es posible que los usuarios vean un mensaje que indica que el componente WebView del sistema no está actualizado y debe actualizarse. Si el dispositivo tiene Google Play instalado, conéctelo a Internet y compruebe si hay actualizaciones. Si el dispositivo no tiene Google Play instalado, obtenga la versión actualizada del componente y aplíquelo a los dispositivos. O bien, actualice al sistema operativo del dispositivo más reciente emitido por Zebra.

### <a name="management-actions-take-a-long-time"></a>Las acciones de administración tardan mucho tiempo

Si Google Play servicios no están disponibles, algunas tareas tardan hasta 8 horas en completarse. Las [limitaciones de portal de empresa de Intune aplicación para Android](https://support.microsoft.com/help/3211588/limitations-of-intune-company-portal-app-for-android-in-china) (abre otro sitio web de Microsoft) pueden ser un buen recurso.

### <a name="device-spoofing-suspected-shows-in-intune"></a>En Intune, se muestra "suplantación de dispositivos sospechosa".

Este error significa que Intune sospecha que un dispositivo Android no Zebra informa de su modelo y fabricante como un dispositivo Zebra.

### <a name="company-portal-app-is-older-than-minimum-required-version"></a>Portal de empresa aplicación es anterior a la versión mínima requerida

Intune puede actualizar la versión mínima necesaria de la aplicación Portal de empresa. Si Google Play no está instalado en el dispositivo, la aplicación de Portal de empresa no se actualiza automáticamente. Si la versión mínima requerida es más reciente que la versión instalada, la aplicación Portal de empresa deja de funcionar. Actualice a la aplicación de Portal de empresa más reciente mediante la instalación [de prueba en dispositivos Zebra](android-zebra-mx-overview.md#sideload-the-company-portal-app).

## <a name="next-steps"></a>Pasos siguientes

[Paneles de discusión de Zebra](https://developer.zebra.com/community/home/discussions) (abre el sitio web de Zebra)

[Usar y administrar dispositivos Zebra con extensiones de movilidad de Zebra en Intune](android-zebra-mx-overview.md)
