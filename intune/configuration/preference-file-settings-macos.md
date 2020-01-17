---
title: 'Adición de una configuración de archivo de preferencia para dispositivos macOS en Microsoft Intune: Azure | Microsoft Docs'
titleSuffix: ''
description: Agregue un archivo XML o plist que incluya información clave sobre la aplicación. Use un perfil de configuración de dispositivo de archivo de preferencias para cambiar la información de clave en el archivo de lista de propiedades y asignarlo a los dispositivos macOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d226a5b8ee448b7b168a03fe6b8a1c63bc1be432
ms.sourcegitcommit: 8f56220e7cafc5bc43135940575a9acb5afde730
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2020
ms.locfileid: "75827792"
---
# <a name="add-a-property-list-file-to-macos-devices-using-microsoft-intune"></a>Agregue un archivo de lista de propiedades a los dispositivos macOS mediante Microsoft Intune

Con Microsoft Intune, puede Agregar un archivo de lista de propiedades (. plist) para dispositivos macOS o aplicaciones en dispositivos macOS.

Esta característica se aplica a:

- dispositivos macOS con 10.7 y versiones más recientes

Los archivos de lista de propiedades suelen incluir información acerca de las aplicaciones macOS. Para obtener más información, consulte [acerca de los archivos de lista de propiedades de información](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html) (sitio web de Apple) y configuración de [carga personalizada](https://support.apple.com/guide/mdm/custom-mdm9abbdbe7/1/web/1).

En este artículo se enumeran y describen los distintos valores de archivo de lista de propiedades que puede Agregar a los dispositivos macOS. Como parte de la solución de administración de dispositivos móviles (MDM), use esta configuración para agregar el identificador de lote de aplicaciones (`com.company.application`) y agregar su archivo. plist.

Estos valores se agregan a un perfil de configuración de dispositivo en Intune y luego se asignan o implementan en los dispositivos macOS.

## <a name="before-you-begin"></a>Antes de comenzar

[Cree el perfil](device-profile-create.md).

## <a name="what-you-need-to-know"></a>Aspectos que debe saber

- Esta configuración no se valida. Asegúrese de probar los cambios antes de asignar el perfil a los dispositivos.
- Si no está seguro de cómo especificar una clave de aplicación, cambie la configuración dentro de la aplicación. Después, revise el archivo de preferencias de la aplicación con [Xcode](https://developer.apple.com/xcode/) para ver cómo está configurada la configuración. Apple recomienda quitar la configuración no administrable con Xcode antes de importar el archivo.
- Solo algunas aplicaciones funcionan con preferencias administradas y es posible que no le permitan administrar todas las configuraciones.
- Asegúrese de cargar los archivos de lista de propiedades que tienen como destino la configuración de canal de dispositivo, no la configuración de canal de usuario. Los archivos de lista de propiedades tienen como destino todo el dispositivo.

## <a name="preference-file"></a>Archivo de preferencia

- **Nombre de dominio de preferencia**: los archivos de lista de propiedades se usan normalmente para exploradores Web (Microsoft Edge), [protección contra amenazas avanzada de Microsoft defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac)y aplicaciones personalizadas. Al crear un dominio de preferencias, también se crea un identificador de paquete. Escriba el identificador de paquete, como `com.company.application`. Por ejemplo, escriba `com.Contoso.applicationName`, `com.Microsoft.Edge` o `com.microsoft.wdav`.
- **Archivo de lista de propiedades**: seleccione el archivo de lista de propiedades asociado a la aplicación. Asegúrese de que es un archivo `.plist` o `.xml`. Por ejemplo, cargue un archivo `YourApp-Manifest.plist` o `YourApp-Manifest.xml`.
- **Contenido del archivo**: se muestra la información de clave en el archivo de lista de propiedades. Si necesita cambiar la información de la clave, abra el archivo de lista en otro editor y, a continuación, vuelva a cargar el archivo en Intune.

Asegúrese de que el archivo tiene el formato correcto. El archivo solo debe tener pares clave-valor y no debe ajustarse en las etiquetas `<dict>`, `<plist>`o `<xml>`. Por ejemplo, el archivo de lista de propiedades debe ser similar al siguiente:

```xml
<key>SomeKey</key>
<string>someString</string>
<key>AnotherKey</key>
<false/>
...
```

Seleccione **Aceptar** > **Crear** para guardar los cambios. El perfil se crea y se muestra en la lista de perfiles.

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero todavía no hace nada. Después, [asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

Para obtener más información sobre los archivos de preferencias de Microsoft Edge, consulte [configuración de las directivas de Microsoft Edge en MacOS](https://docs.microsoft.com/deployedge/configure-microsoft-edge-on-mac).
