---
title: Los registros de uso StageNow en dispositivos Android Zebra en Microsoft Intune - Azure | Microsoft Docs
description: Ver los problemas y resoluciones habituales al usar StageNow en dispositivos Android con Microsoft Intune. También aprenderá cómo obtener los registros y ver ejemplos de cómo leer los registros de aciertos o errores.
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
ms.openlocfilehash: 36476820805c00cefafcd9f64dd2f08a014762c0
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490548"
---
# <a name="troubleshoot-and-see-potential-issues-on-android-zebra-devices-in-microsoft-intune"></a>Solución de problemas y ver los posibles problemas en dispositivos Android Zebra en Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En Microsoft Intune, puede usar [Zebra Mobility extensiones (MX) para administrar dispositivos Android Zebra](android-zebra-mx-overview.md). Cuando se utilizan dispositivos de cebra, creación de perfiles en StageNow para administrar la configuración y cargarlos en Intune. Intune usa la aplicación StageNow para aplicar la configuración en los dispositivos. La aplicación StageNow también crea un archivo de registro detallado en el dispositivo que se usa para solucionar problemas.

Esta característica se aplica a:

- Android

Por ejemplo, crear un perfil en StageNow para configurar un dispositivo. Cuando se crea el perfil StageNow, el último paso genera un archivo para probar el perfil. Consumir este archivo con la aplicación StageNow en el dispositivo.

En otro ejemplo, crear un perfil en StageNow y probarlo. En Intune, agregar el perfil StageNow y, a continuación, asignarla a los dispositivos de cebra. Cuando se comprueba el estado del perfil asignado, el perfil muestra un estado de alto nivel.

En ambos casos, puede obtener más detalles en el archivo de registro StageNow, que se guarda en el dispositivo cada vez que se aplica un perfil StageNow.

Algunos problemas no estén relacionados con el contenido del perfil StageNow y no se reflejan en los registros.

En este artículo se muestra cómo leer los registros de StageNow y se muestra algunos posibles problemas con dispositivos de cebra que pueden no reflejarse en los registros.

[Usar y administrar dispositivos de cebra con extensiones de movilidad de cebra](android-zebra-mx-overview.md) contiene más información sobre esta característica.

## <a name="get-the-logs"></a>Obtención de registros

### <a name="use-the-stagenow-app-on-the-device"></a>Utilice la aplicación StageNow en el dispositivo
Cuando se prueba un perfil directamente mediante StageNow en el equipo, en lugar de usar [Intune para implementar el perfil](android-zebra-mx-overview.md#step-4-create-a-device-management-profile-in-stagenow), la aplicación StageNow en el dispositivo guarda los registros de la prueba. Para obtener el archivo de registro, use el **más (...)**  opción en la aplicación StageNow en el dispositivo.

### <a name="get-logs-using-android-debug-bridge"></a>Obtención de registros con Android Debug Bridge
Para obtener los registros después de que el perfil ya se implementa con Intune, conecte el dispositivo a un equipo con [Android Debug Bridge (adb)](https://developer.android.com/studio/command-line/adb) (abre el sitio web de Android).

En el dispositivo, los registros se guardan en `/sdcard/Android/data/com.microsoft.windowsintune.companyportal/files`

### <a name="get-logs-from-email"></a>Obtener registros de correo electrónico
Para obtener los registros después de que el perfil ya se implementa con Intune, los usuarios finales puede enviar por correo electrónico, los registros mediante una aplicación de correo electrónico en el dispositivo. En el dispositivo de cebra, abra la aplicación de Portal de empresa, y [enviar los registros](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). El uso de la característica de registros de envío también crea un PowerLift incidentes identificador, que puede hacer referencia a si ponerse en contacto con soporte técnico de Microsoft.

## <a name="read-the-logs"></a>Leer los registros

Al examinar los registros, hay un error siempre que vea el `<characteristic-error>` etiqueta. Detalles del error se escriben en el `<parm-error>` etiqueta > `desc` propiedad.

## <a name="error-types"></a>Tipos de errores

Dispositivos de cebra incluyen niveles de información de error diferentes:

- El CSP no es compatible con el dispositivo. Por ejemplo, el dispositivo no es un dispositivo de telefonía móvil y no tiene un administrador de telefonía móvil.
- No coincide la versión del registro MX ni OSX. Cada CSP tiene versiones. Una matriz de soporte técnico completo, vea [documentación de cebra](http://techdocs.zebra.com/mx/) (abre el sitio web de cebra).
- El dispositivo informa de otro problema o error.

## <a name="examples"></a>Ejemplos

Por ejemplo, tiene el perfil de entrada siguiente:

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

En el registro, el XML es idéntico a la entrada. Este resultado coincidente significa que el perfil que se aplicó correctamente en el dispositivo sin errores:

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

El registro muestra un error, ya que contiene un `<characteristic-error>` etiqueta. En este escenario, el perfil ha intentado instalar un paquete de Android (APK) que no existe en la ruta de acceso dada:

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

## <a name="other-potential-issues-with-zebra-devices"></a>Otros posibles problemas con dispositivos de cebra

Esta sección enumeran otros posibles problemas que puede ver al usar dispositivos de cebra con el Administrador de dispositivos. Estos problemas no se notifican en los registros StageNow.

### <a name="android-system-webview-is-out-of-date"></a>Android WebView del sistema no está actualizada

Cuando los dispositivos más antiguos se inicie sesión con la aplicación de Portal de empresa, los usuarios pueden ver un mensaje que el componente WebView del sistema está obsoleto y debe actualiza. Si el dispositivo tiene instalado Google Play, conectarse a internet y compruebe si hay actualizaciones. Si el dispositivo no tiene instalado de Google Play, obtener la versión actualizada del componente y se aplican a los dispositivos. O bien, actualice al dispositivo más reciente del sistema operativo emitido cebra.

### <a name="management-actions-take-a-long-time"></a>Las acciones de administración tardan mucho tiempo

Si Google Play services no están disponibles, algunas tareas tardar hasta 8 horas en Finalizar. [Aplicación de Portal de empresa de las limitaciones de Intune para Android](https://support.microsoft.com/help/3211588/limitations-of-intune-company-portal-app-for-android-in-china) (abre otro sitio web de Microsoft) puede ser un buen recurso.

### <a name="device-spoofing-suspected-shows-in-intune"></a>"Dispositivo de suplantación sospechosa" se muestra en Intune

Este error significa que Intune sospecha que un dispositivo no - cebra Android está informando de su modelo y fabricante, como un dispositivo de cebra.

### <a name="company-portal-app-is-older-than-minimum-required-version"></a>Aplicación de Portal de empresa es anterior a la versión mínima requerida

Intune puede actualizar la versión mínima necesaria de la aplicación de Portal de empresa. Si Google Play no está instalado en el dispositivo, la aplicación de Portal de empresa no se actualizará automáticamente. Si la versión mínima necesaria es más reciente que la versión instalada, la aplicación de Portal de empresa deja de funcionar. Actualización de la aplicación de Portal de empresa más reciente con [instalación de prueba en dispositivos de cebra](android-zebra-mx-overview.md#sideload-the-company-portal-app).

## <a name="next-steps"></a>Pasos siguientes

[Paneles de discusión de cebra](https://developer.zebra.com/community/home/discussions) (abre el sitio web de cebra)

[Usar y administrar dispositivos de cebra con extensiones de movilidad de cebra en Intune](android-zebra-mx-overview.md)
