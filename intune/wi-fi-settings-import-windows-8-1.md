---
title: 'Importación de la configuración de Wi-Fi para dispositivos Windows en Microsoft Intune: Azure | Microsoft Docs'
description: Exporte la configuración de Wi-Fi desde un dispositivo Windows como un archivo XML mediante netsh wlan. Después, importe este archivo en Intune para crear un perfil de Wi-Fi para los dispositivos que ejecutan Windows 8.1, Windows 10 y Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/18/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2ce2813702d9b2b3cb91f5531308cbb58b1f9f80
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66050612"
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

1. Cree una carpeta local para los perfiles de Wi-Fi exportados, como **c:\Wi-Fi**.
2. Abra un símbolo del sistema como administrador.
3. Ejecute el comando `netsh wlan show profiles` y anote el nombre del perfil que quiere exportar. En este ejemplo, el nombre de perfil es **WiFiName**.
4. Ejecute el comando `netsh wlan export profile name="ProfileName" folder=c:\Wifi`. Este comando crea un archivo de perfil de Wi-Fi denominado **Wi-Fi-WiFiName.xml** en la carpeta de destino.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importación de la configuración de Wi-Fi en Intune

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba un **nombre** y una **descripción** para el perfil de restricción de dispositivos.

    > [!IMPORTANT]
    > - El nombre **debe** ser el mismo que el del atributo de nombre del archivo XML del perfil de Wi-Fi. De lo contrario, se producirá un error.
    > - Si va a exportar un perfil de Wi-Fi que incluye una clave previamente compartida, **debe** agregar `key=clear` al comando. Por ejemplo, escriba `netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi`
    > - Si se usa una clave previamente compartida con Windows 10, se producirá un error de corrección en Intune. Cuando esto sucede, el perfil de Wi-Fi se asigna correctamente al dispositivo y el perfil funciona según lo previsto.
    > - Si exporta un perfil de Wi-Fi que incluye una clave previamente compartida, asegúrese de que el archivo esté protegido. La clave tiene texto sin formato, por lo que es su responsabilidad protegerla.

4. En **Plataforma**, seleccione **Windows 8.1 y posterior**.
5. En **Tipo de perfil**, seleccione **Importación de Wi-Fi**.
6. Configure las siguientes opciones:
    - **Nombre de la conexión**: escriba un nombre para la conexión Wi-Fi. Este nombre se mostrará a los usuarios finales cuando exploren las redes Wi-Fi disponibles.
    - **XML de perfil**: seleccione el botón Examinar y elija el archivo XML que contiene la configuración del perfil de Wi-Fi que quiere importar.
    - **Contenido de archivo**: muestra el código XML del perfil de configuración seleccionado.
7. Cuando haya terminado, seleccione **Aceptar** > **Crear** para guardar los cambios. El perfil se crea y se muestra en la lista de perfiles.

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero no hacen nada. A continuación, [asigne este perfil](device-profile-assign.md).

## <a name="more-resources"></a>Más recursos

[Introducción a la configuración de Wi-Fi](wi-fi-settings-configure.md), incluidas otras plataformas disponibles.
