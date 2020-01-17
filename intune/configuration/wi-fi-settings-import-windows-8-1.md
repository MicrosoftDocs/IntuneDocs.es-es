---
title: 'Importación de la configuración de Wi-Fi para dispositivos Windows en Microsoft Intune: Azure | Microsoft Docs'
description: Exporte la configuración de Wi-Fi desde un dispositivo Windows como un archivo XML mediante netsh wlan. Después, importe este archivo en Intune para crear un perfil de Wi-Fi para los dispositivos que ejecutan Windows 8.1, Windows 10 y Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f79ccdc71ddbfa3f25daef629515fb612de01852
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207016"
---
# <a name="import-wi-fi-settings-for-windows-devices-in-intune"></a>Importar la configuración de Wi-Fi para dispositivos Windows en Intune

Para los dispositivos que ejecutan Windows, puede importar un perfil de configuración de Wi-Fi que se haya exportado previamente a un archivo. **Para los dispositivos Windows 10 y versiones posteriores, también puede [crear un perfil de Wi-Fi](wi-fi-settings-windows.md) directamente en Intune**.

Se aplica a:  
- Windows 8.1 y posterior
- Windows 10 y versiones posteriores
- Windows 10 Desktop o Mobile
- Windows Holographic for Business

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Exportación de la configuración de Wi-Fi de un dispositivo Windows

En Windows, use `netsh wlan` para exportar un perfil de Wi-Fi existente a un archivo XML que Intune pueda leer. La clave se debe exportar como texto sin formato para poder usar el perfil correctamente.

En un equipo de Windows que ya tenga instalado el perfil de Wi-Fi necesario, lleve a cabo los siguientes pasos:

1. Cree una carpeta local para los perfiles Wi-Fi exportados, como **c:\WiFi**.
2. Abra un símbolo del sistema como administrador.
3. Ejecute el comando `netsh wlan show profiles`. Anote el nombre del perfil que desea exportar. En este ejemplo, el nombre de perfil es **WiFiName**.
4. Ejecute el comando `netsh wlan export profile name="ProfileName" folder=c:\Wifi`. Este comando crea un archivo de perfil de Wi-Fi denominado **Wi-Fi-WiFiName.xml** en la carpeta de destino.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importación de la configuración de Wi-Fi en Intune

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.
3. Escriba los valores siguientes:

    - **Nombre**: escriba un nombre descriptivo para el nuevo perfil. El nombre **debe** ser el mismo que el del atributo de nombre del archivo XML del perfil de Wi-Fi. De lo contrario, se producirá un error.
    - **Descripción**: escriba una descripción con información general sobre la configuración y otros detalles importantes.
    - **Plataforma**: seleccione **Windows 8.1 y versiones posteriores**.
    - **Tipo de perfil**: seleccione **Importación de Wi-Fi**.

    > [!IMPORTANT]
    > - Si va a exportar un perfil de Wi-Fi que incluye una clave previamente compartida, **debe** agregar `key=clear` al comando. Por ejemplo, escriba `netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi`
    > - Si se usa una clave precompartida con Windows 10, se produce un error de corrección en Intune. Cuando esto sucede, el perfil de Wi-Fi se asigna correctamente al dispositivo y el perfil funciona según lo previsto.
    > - Si exporta un perfil de Wi-Fi que incluye una clave previamente compartida, asegúrese de que el archivo esté protegido. La clave tiene texto sin formato, por lo que es su responsabilidad protegerla.

4. Escriba los valores siguientes:

    - **Nombre de la conexión**: escriba un nombre para la conexión Wi-Fi. Este nombre se muestra a los usuarios cuando examinan las redes Wi-Fi disponibles.
    - **XML de perfil**: seleccione el botón Examinar y luego el archivo XML que contiene la configuración del perfil de Wi-Fi que quiere importar.
    - **Contenido del archivo**: muestra el código XML del perfil de configuración seleccionado.

5. Haga clic en **Aceptar** para guardar los cambios.
6. Cuando termine, seleccione **Aceptar** > **Crear** para crear el perfil de Intune. Una vez hecho, el perfil aparece en la lista **Dispositivos - Perfiles de configuración**.

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero no hacen nada. Después, [asigne el perfil](../device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

Vea [Introducción a la configuración de Wi-Fi](wi-fi-settings-configure.md), incluidas otras plataformas disponibles.
