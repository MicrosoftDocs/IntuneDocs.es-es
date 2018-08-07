---
title: 'Importación de la configuración de Wi-Fi para dispositivos Windows en Microsoft Intune: Azure | Microsoft Docs'
description: Exporte la configuración de Wi-Fi desde un dispositivo Windows como un archivo XML mediante netsh wlan. Después, importe este archivo en Intune para crear un perfil de Wi-Fi para los dispositivos que ejecutan Windows 8.1, Windows 10 y Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6ce5cdd9509ed3407491714ccfa853613eb43973
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321142"
---
# <a name="import-wi-fi-settings-for-windows-devices-in-intune"></a>Importar la configuración de Wi-Fi para dispositivos Windows en Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Para los dispositivos que ejecutan Windows, puede importar un perfil de configuración de Wi-Fi que se haya exportado previamente a un archivo. **Para los dispositivos Windows 10 y versiones posteriores, puede [crear un perfil de Wi-Fi](wi-fi-settings-windows.md) directamente en Intune**.

Se aplica a:  
- Windows 8.1 y posterior
- Windows 10 y versiones posteriores
- Windows 10 Desktop o Mobile
- Windows Holographic for Business

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Exportación de la configuración de Wi-Fi de un dispositivo Windows

En Windows, use **netsh wlan** para exportar un perfil de Wi-Fi existente a un archivo XML que Intune pueda leer. La clave se debe exportar como texto sin formato para poder usar el perfil correctamente.

En un equipo de Windows que ya tenga instalado el perfil de Wi-Fi necesario, lleve a cabo los siguientes pasos:

1. Cree una carpeta local para los perfiles de Wi-Fi exportados, como **c:\Wi-Fi**.
2. Abra un símbolo del sistema como administrador.
3. Ejecute el comando `netsh wlan show profiles` y anote el nombre del perfil que quiere exportar. En este ejemplo, el nombre de perfil es **WiFiName**.
4. Ejecute el comando `netsh wlan export profile name="ProfileName" folder=c:\Wifi`. Esto crea un archivo de perfil de Wi-Fi denominado **Wi-Fi-WiFiName.xml** en la carpeta de destino.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importación de la configuración de Wi-Fi en Intune

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
4. Escriba un **nombre** y una **descripción** para el perfil de restricción de dispositivos.

    > [!IMPORTANT]
    > - El nombre **debe** ser el mismo que el del atributo de nombre del archivo XML del perfil de Wi-Fi. De lo contrario, se producirá un error.
    > - Si va a exportar un perfil de Wi-Fi que incluye una clave previamente compartida, **debe** agregar `key=clear` al comando. Por ejemplo, escriba `netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi`
    > - Si se usa una clave previamente compartida con Windows 10, se producirá un error de corrección en Intune. Cuando esto sucede, el perfil de Wi-Fi se asigna correctamente al dispositivo y el perfil funciona según lo previsto.
    > - Si exporta un perfil de Wi-Fi que incluye una clave previamente compartida, asegúrese de que el archivo esté protegido. La clave tiene texto sin formato, por lo que es su responsabilidad protegerla.

5. En **Plataforma**, seleccione **Windows 8.1 y posterior**.
6. En **Tipo de perfil**, seleccione **Importación de Wi-Fi**.
7. Configure las siguientes opciones:
  - **Nombre de la conexión**: escriba un nombre para la conexión Wi-Fi. Este nombre se mostrará a los usuarios finales cuando exploren las redes Wi-Fi disponibles.
  - **XML de perfil**: seleccione el botón Examinar para seleccionar el archivo XML que contiene la configuración del perfil de Wi-Fi que quiere importar en Intune.
  - **Contenido de archivo**: muestra el código XML del perfil de configuración seleccionado.
8. Cuando haya terminado, elija **Aceptar** y **Crear** para crear el perfil.

El perfil se crea y aparece en la lista de perfiles.
