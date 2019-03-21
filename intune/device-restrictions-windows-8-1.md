---
title: Configuración de restricciones de dispositivos de Microsoft Intune para dispositivos que ejecutan Windows 8.1
titleSuffix: ''
description: Descubra las opciones de configuración de Intune que puede usar para controlar la funcionalidad y la configuración de los dispositivos que ejecutan Windows 8.1.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a2b1b9a41c86caa14683a86212bba7570e36d102
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566189"
---
# <a name="microsoft-intune-windows-81-and-later-device-restriction-settings"></a>Configuración de restricciones de Microsoft Intune de dispositivos Windows 8.1 y versiones posteriores

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En este artículo, se muestran las opciones de configuración de restricciones de dispositivos de Microsoft Intune que puede configurar para los dispositivos que ejecutan Windows 8.1 y versiones posteriores.


## <a name="general"></a>General

-   **Envío de datos de diagnóstico**: permite que el dispositivo envíe información de diagnóstico a Microsoft.
-   **Firewall**: requiere que el Firewall de Windows esté activado.
-   **Control de cuentas de usuario**: requiere el uso de Control de cuentas de usuario (UAC) en los dispositivos.

## <a name="password"></a>Contraseña
-   **Tipo de contraseña necesaria**: requiere que el usuario final escriba una contraseña para acceder al dispositivo.
-   **Minimum password length** (Longitud mínima de contraseña): configura la longitud mínima necesaria (de caracteres) para la contraseña.
-   **Número de errores de inicio de sesión antes de borrar el dispositivo**: borra el dispositivo tras el número de intentos de inicio de sesión erróneos especificado.
-   **Máximo de minutos de inactividad hasta que se bloquea la pantalla**: especifique el número de minutos que un dispositivo debe estar inactivo antes de que se exija una contraseña para desbloquearlo.
-   **Caducidad de la contraseña (días)**: especifica el número de días antes de que se deba cambiar la contraseña del dispositivo.
-   **Impedir la reutilización de contraseñas anteriores**: especifica si el usuario puede configurar contraseñas usadas anteriormente.
-   **PIN y contraseña de imagen**: permite el uso de una contraseña de imagen y un PIN. Una contraseña de imagen permite que el usuario inicie sesión mediante gestos en una imagen. Un PIN permite que los usuarios inicien sesión rápidamente con un código de cuatro dígitos.
-   **Cifrado**: requiere el cifrado de los archivos en el dispositivo.<br>Para forzar el cifrado en los dispositivos que ejecutan Windows 8.1, debe instalar la [Actualización de cliente de diciembre de 2014 MDM en Windows](https://support.microsoft.com/kb/3013816) en cada dispositivo.
Si habilita esta configuración para dispositivos Windows 8.1, todos los usuarios del dispositivo deben tener una cuenta de Microsoft.
Para que el cifrado funcione, el dispositivo debe cumplir los requisitos de certificación de hardware de [Microsoft InstantGo](https://blogs.windows.com/windowsexperience/2014/06/19/instantgo-a-better-way-to-sleep/#IBHULcTfI4PokO8X.97).
Al exigir el cifrado en un dispositivo, solo se puede obtener acceso a la clave de recuperación desde la cuenta Microsoft de los usuarios, a la que se obtiene acceso desde su cuenta de OneDrive. No se puede recuperar esta clave en nombre de un usuario.     



## <a name="browser"></a>Explorador
-   **Autofill (Rellenar automáticamente)**: permite a los usuarios cambiar la configuración de Autocompletar en el explorador.
-   **Advertencias de fraude**: habilita o deshabilita advertencias sobre posibles sitios web fraudulentos.
-   **SmartScreen**: habilita o deshabilita advertencias sobre posibles sitios web fraudulentos.
-   **JavaScript**: permite que el explorador ejecute scripts, como los de Java.
-   **Elementos emergentes**: habilita o deshabilita el bloqueador de elementos emergentes del explorador.
-   **Enviar encabezados de no seguimiento**: envía un encabezado de no seguimiento a sitios visitados en Internet Explorer.
-   **Plugins** (Complementos): permite a los usuarios agregar complementos a Internet Explorer.
-   **Entrada de palabra única en el sitio de la intranet**: permite el uso de una sola palabra para dirigir Internet Explorer a un sitio web como, por ejemplo, Bing.
-   **Detección automática del sitio de intranet**: ayuda a configura la seguridad de sitios de intranet en Internet Explorer.
-   **Nivel de seguridad de Internet**: establece el nivel de seguridad de Internet Explorer para sitios de Internet.
-   **Nivel de seguridad de la intranet**: establece el nivel de seguridad de Internet Explorer para sitios de intranet.
-   **Nivel de seguridad de sitios de confianza**: configura el nivel de seguridad para la zona de sitios de confianza.
-   **Nivel de seguridad alto para sitios restringidos**: configura el nivel de seguridad para la zona de sitios restringidos.
-   **Acceso al menú Modo de empresa**: permite a los usuarios tener acceso a las opciones del menú Modo de empresa desde Internet Explorer.
Si selecciona esta opción, también puede especificar una **Ubicación de informes de registro** que contenga una dirección URL a un informe que muestre los sitios web para los que los usuarios hayan activado el acceso en Modo de empresa.
-   **Ubicación de la lista de sitios del modo de empresa**: especifica la ubicación de la lista de sitios web que usan el modo de empresa cuando está activo.

## <a name="cellular"></a>Móvil
-   **Itinerancia de datos**: permite la itinerancia de datos cuando el dispositivo está en una red de telefonía móvil.

## <a name="cloud-and-storage"></a>Nube y almacenamiento
-   **Dirección URL de carpetas de trabajo**: establece la dirección URL de la carpeta de trabajo para permitir que los documentos se sincronicen en todos los dispositivos.
-   **Acceso a la aplicación Correo de Windows sin una cuenta Microsoft**: permite el acceso a la aplicación Windows Mail sin una cuenta Microsoft.    
