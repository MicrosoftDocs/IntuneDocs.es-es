---
title: "Importar la configuración de Wi-Fi para dispositivos Windows 8.1 y posterior"
titleSuffix: Azure portal
description: "Importación de la configuración de Wi-Fi de Windows a un perfil de Wi-Fi de Intune\"."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 1/25/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5b4b77f9c9c1c957e3332c20e010a5e8e8ec2b56
ms.sourcegitcommit: 93622d740cbd12043eedc25a9699cc4256e23e7e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-import-wi-fi-settings-for-windows-81-and-later-devices-in-microsoft-intune"></a>Importación de la configuración de Wi-Fi para Windows 8.1 y dispositivos posteriores en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

En el caso de los dispositivos que ejecuten Windows 8.1, Windows 10 para escritorio o dispositivos móviles, o Windows Holographic for Business, puede importar un perfil de configuración que se haya exportado anteriormente a un archivo.

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Exportación de la configuración de Wi-Fi de un dispositivo Windows

En Windows, use la utilidad **netsh wlan** para exportar un perfil de Wi-Fi existente a un archivo XML que Intune pueda leer. En un equipo de Windows que ya tenga instalado el perfil de Wi-Fi necesario, siga el procedimiento siguiente.
1. Cree una carpeta local para los perfiles de Wi-Fi exportados, como **c:\Wi-Fi**.
1. Abra un símbolo del sistema como administrador.
1. Ejecute el comando **netsh wlan show profiles** y anote el nombre del perfil que quiere exportar. En este ejemplo, el nombre de perfil es **WiFiName**.
1. Ejecute el comando **netsh wlan export profile name="ProfileName" folder=c:\Wifi**. Se creará un archivo de perfil de Wi-Fi llamado **Wi-Fi-WiFiName.xml** en la carpeta de destino.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importación de la configuración de Wi-Fi en Intune

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Configuración del dispositivo**.
2. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
3. En la hoja de perfiles, haga clic en **Create Profile** (Crear perfil).
4. En la hoja **Create Profile** (Crear perfil), escriba un **nombre** y una **descripción** para el perfil de restricción de dispositivo.

   > [!WARNING]
   > El nombre **debe** ser el mismo que el del atributo de nombre del archivo XML del perfil de Wi-Fi. Si no es así, se producirá un error.

5. En la lista desplegable **Plataforma**, elija **Windows 8.1 y versiones posteriores**.
6. En la lista desplegable de **tipos de perfil**, elija **Importación de Wi-Fi**.
7. En la hoja **Wi-Fi básica**, configure las siguientes opciones:
    - **Nombre de conexión**: escriba el nombre de la conexión Wi-Fi. Este nombre se mostrará a los usuarios finales cuando exploren las redes Wi-Fi disponibles.
    - **XML de perfil**: haga clic en el botón Examinar para seleccionar el archivo XML que contiene la configuración del perfil de Wi-Fi que quiere importar en Intune.
    - **Contenido de archivo**: muestra el código XML del perfil de configuración seleccionado.
8. Cuando haya terminado, vuelva a la hoja **Create Profile** (Crear perfil) y presione **Crear**.

El perfil se crea y aparece en la hoja de la lista de perfiles.
