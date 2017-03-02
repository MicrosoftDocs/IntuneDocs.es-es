---
title: "Importación de la configuración de Wi-Fi para Windows 8.1 y posterior | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: cómo importar la configuración de Wi-Fi de Windows a un perfil de Wi-Fi de Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2c4e9b19-b268-4f6d-9663-7cdbe4e4a8dd
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 2600c8363c677465e29af382fa5ef4a921048fef
ms.lasthandoff: 02/16/2017


---

# <a name="how-to-import-wi-fi-settings-for-windows-81-and-later-devices-in-microsoft-intune"></a>Importación de la configuración de Wi-Fi para Windows 8.1 y dispositivos posteriores en Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

En el caso de los dispositivos que ejecutan Windows 8.1 o Windows 10 para escritorio o móvil, puede importar un perfil de configuración de Wi-Fi que se haya exportado previamente a un archivo.

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Exportación de la configuración de Wi-Fi de un dispositivo Windows

En Windows, use la utilidad **netsh wlan** para exportar un perfil de Wi-Fi existente a un archivo XML que Intune pueda leer. En un equipo de Windows que ya tenga instalado el perfil de Wi-Fi necesario, siga el procedimiento siguiente.
1. Cree una carpeta local para los perfiles de Wi-Fi exportados, como **c:\Wi-Fi**.
1. Abra un símbolo del sistema como administrador.
1. Ejecute el comando **netsh wlan show profiles** y anote el nombre del perfil que quiere exportar. En este ejemplo, el nombre de perfil es **WiFiName**.
1. Ejecute este comando: **netsh wlan export profile name="ProfileName" folder=c:\Wifi**. Se creará un archivo de perfil de Wi-Fi llamado **Wi-Fi-WiFiName.xml** en la carpeta de destino.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importación de la configuración de Wi-Fi en Intune

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
3. En la hoja **Intune**, elija **Configurar dispositivos**.
2. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
3. En la hoja de perfiles, haga clic en **Create Profile** (Crear perfil).
4. En la hoja **Create Profile** (Crear perfil), escriba un **nombre** y una **descripción** para el perfil de restricción de dispositivo.
5. En la lista desplegable **Plataforma**, elija **Windows 8.1 y versiones posteriores**.
6. En la lista desplegable de **tipos de perfil**, elija **Importación de Wi-Fi**.
7. En la hoja **Wi-Fi básica**, configure lo siguiente:
    - **Nombre de conexión**: escriba el nombre de la conexión Wi-Fi. Este nombre se mostrará a los usuarios finales cuando exploren las redes Wi-Fi disponibles.
    - **XML de perfil**: haga clic en el botón Examinar para seleccionar el archivo XML que contiene la configuración del perfil de Wi-Fi que quiere importar en Intune.
    - **Contenido de archivo**: muestra el código XML del perfil de configuración seleccionado.
8. Cuando haya terminado, vuelva a la hoja **Create Profile** (Crear perfil) y presione **Crear**.

El perfil se crea y aparece en la hoja de la lista de perfiles.

