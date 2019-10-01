---
title: Configuración de restricciones de dispositivos de Microsoft Intune para Windows Phone 8.1
titleSuffix: ''
description: Descubra las opciones de configuración de Intune que puede usar para controlar la funcionalidad y la configuración de los dispositivos que ejecutan Windows Phone 8.1.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3bcfad3937b4ab6f533cd7ac915a964f2551be45
ms.sourcegitcommit: 1d4aec7b79c70d35ec3fc29df6ff9c6a1403412e
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/25/2019
ms.locfileid: "71302299"
---
# <a name="microsoft-intune-windows-phone-81-device-restriction-settings"></a>Configuración de restricciones de dispositivos Windows Phone 8.1 de Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En este artículo, se muestran las opciones de configuración de restricciones de dispositivos de Microsoft Intune que puede configurar para los dispositivos que ejecutan Windows Phone 8.1.


## <a name="general"></a>General

- **Cámara**: permite o bloquea la cámara del dispositivo.
- **Copiar y pegar**: permite o bloquea la funcionalidad de copiar y pegar en los dispositivos.
- **Almacenamiento extraíble**: permite que el dispositivo use almacenamiento extraíble, como tarjetas SD.
- **Geolocalización**: permite que el dispositivo use información de ubicación.
- **Cuenta Microsoft**: permite o impide que el usuario vincule una cuenta de Microsoft al dispositivo.
- **Captura de pantalla**: permite que el usuario capture el contenido de la pantalla como un archivo de imagen.
- **Envío de datos de diagnóstico**: permite que el dispositivo envíe información de diagnóstico a Microsoft.
- **Sincronización de cuentas de correo electrónico personalizadas**: permite que el dispositivo se conecte a cuentas de correo electrónico que no son de Microsoft.

## <a name="password"></a>Contraseña

- **Contraseña**: exige que el usuario final escriba una contraseña para acceder al dispositivo.
  - **Tipo de contraseña necesaria**: especifica el tipo de contraseña que es necesaria, como solo numérica o alfanumérica.
  - **Minimum password length** (Longitud mínima de contraseña): especifica el número mínimo de caracteres que son necesarios en la contraseña.
  - **Contraseñas sencillas**: especifica que pueden usarse contraseñas sencillas como "0000" y "1234".
  - **Número de errores de inicio de sesión antes de borrar el dispositivo**: especifica el número de veces que puede escribirse una contraseña incorrecta antes de que se borre el dispositivo.
  - **Máximo de minutos de inactividad hasta que se bloquea la pantalla**: especifique la cantidad de tiempo que un dispositivo debe permanecer inactivo antes de que la pantalla se bloquee automáticamente.
  - **Caducidad de la contraseña (días)** : especifica el número de días antes de que se deba cambiar la contraseña del dispositivo.
  - **Impedir la reutilización de contraseñas anteriores** -especifica cuántas contraseñas usadas anteriormente se pueden recordar.
- **Cifrado**: requiere que se cifren los datos en los dispositivos móviles compatibles.

## <a name="app-store"></a>Tienda de aplicaciones

- **Tienda de aplicaciones**: permite a los usuarios conectarse a la tienda de aplicaciones desde el dispositivo.

## <a name="restricted-apps"></a>Aplicaciones restringidas

En la lista de aplicaciones restringidas, puede configurar una de las listas siguientes:

**Aplicaciones bloqueadas**: aplicaciones (no administradas por Intune) que los usuarios no pueden instalar ni ejecutar.
**Aplicaciones permitidas**: aplicaciones que los usuarios pueden instalar. Las aplicaciones que se administran mediante Intune están permitidas automáticamente.

Para configurar la lista, haga clic en **Agregar** y especifique un nombre de su elección. Opcionalmente, puede indicar el editor de la aplicación y la dirección URL de la aplicación en la tienda de aplicaciones.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Especificación de la dirección URL para una aplicación de la tienda

Para especificar la dirección URL de una aplicación en la lista de aplicaciones permitidas y bloqueadas, use el siguiente formato:

Desde la página de la [Tienda de Windows Phone](https://www.microsoft.com/store/apps/windows-phone), busque la aplicación que quiere usar.

Abra la página de la aplicación y copie la dirección URL en el Portapapeles. Ya puede usarla como dirección URL en una la lista de aplicaciones permitidas o bloqueadas.

Ejemplo: busque la aplicación Skype en la tienda. La dirección URL usada es `http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51`.



### <a name="additional-options"></a>Opciones adicionales

También puede hacer clic en **Importar** para rellenar la lista a partir de un archivo .csv con el formato <*dirección URL de aplicación*>, <*nombre de aplicación*>, <*editor de aplicación*> o en **Exportar** para crear un archivo .csv que contenga la lista de aplicaciones restringidas en el mismo formato.


## <a name="browser"></a>Explorador

- **Explorador web**: permite o bloquea el explorador web integrado en los dispositivos.

## <a name="cellular-and-connectivity"></a>Red de telefonía móvil y conectividad

- **Wi-Fi**: habilita o deshabilita la funcionalidad Wi-Fi del dispositivo.
- **Tethering Wi-Fi**: permite el uso de tethering Wi-Fi en el dispositivo.
- **Conectar automáticamente a zonas Wi-Fi**: permite que el dispositivo se conecte automáticamente a zonas Wi-Fi gratuitas y acepte automáticamente las condiciones de uso.
- **Informes de zona Wi-Fi**: envía información sobre las conexiones Wi-Fi para ayudar al usuario a detectar conexiones cercanas.
- **NFC**: habilita o deshabilita operaciones que usan transmisión de datos en proximidad en dispositivos compatibles.
- **Bluetooth**: habilita o deshabilita la funcionalidad Bluetooth del dispositivo.
