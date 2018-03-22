---
title: Importar la configuración de Wi-Fi para dispositivos Windows 8.1 y posterior
titleSuffix: Microsoft Intune
description: Cómo importar la configuración de Wi-Fi de Windows a un perfil de Wi-Fi de Intune.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 890a10ecf4212656c189adaf46bb2839898758c1
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="import-wi-fi-settings-for-windows-81-and-later-devices-in-microsoft-intune"></a>Importación de la configuración de Wi-Fi para Windows 8.1 y dispositivos posteriores en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

En el caso de los dispositivos que ejecuten Windows 8.1, Windows 10 para escritorio o dispositivos móviles, o Windows Holographic for Business, puede importar un perfil de configuración que se haya exportado anteriormente a un archivo.

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Exportación de la configuración de Wi-Fi de un dispositivo Windows

En Windows, use la utilidad **netsh wlan** para exportar un perfil de Wi-Fi existente a un archivo XML que Intune pueda leer. En un equipo de Windows que ya tenga instalado el perfil de Wi-Fi necesario, siga el procedimiento siguiente.
1. Cree una carpeta local para los perfiles de Wi-Fi exportados, como **c:\Wi-Fi**.
1. Abra un símbolo del sistema como administrador.
1. Ejecute el comando **netsh wlan show profiles** y anote el nombre del perfil que quiere exportar. En este ejemplo, el nombre de perfil es **WiFiName**.
1. Ejecute el comando **netsh wlan export profile name="ProfileName" folder=c:\Wifi**. Se creará un archivo de perfil de Wi-Fi llamado **Wi-Fi-WiFiName.xml** en la carpeta de destino.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importación de la configuración de Wi-Fi en Intune

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, elija **Configuración del dispositivo**.
4. En el panel **Configuración del dispositivo**, en la sección **Administrar**, elija **Perfiles**.
5. En el panel Perfiles, haga clic en **Crear perfil**.
6. En el panel **Crear perfil**, escriba un **Nombre** y una **Descripción** para el perfil de restricción de dispositivos.


   > [!WARNING]
   > El nombre **debe** ser el mismo que el del atributo de nombre del archivo XML del perfil de Wi-Fi. Si no es así, se producirá un error.

7. En la lista desplegable **Plataforma**, elija **Windows 8.1 y versiones posteriores**.
8. En la lista desplegable **Tipos de perfil**, elija **Importación de Wi-Fi**.
9. En el panel **Wi-Fi**, configure las siguientes opciones:
    - **Nombre de conexión**: escriba el nombre de la conexión Wi-Fi. Este nombre se mostrará a los usuarios finales cuando exploren las redes Wi-Fi disponibles.
    - **XML de perfil**: haga clic en el botón Examinar para seleccionar el archivo XML que contiene la configuración del perfil de Wi-Fi que quiere importar en Intune.
    - **Contenido de archivo**: muestra el código XML del perfil de configuración seleccionado.
10. Cuando haya terminado, elija **Aceptar**, vuelva al panel **Crear perfil** y seleccione **Crear**.

Se creará el perfil y aparecerá en el panel con la lista de perfiles.
