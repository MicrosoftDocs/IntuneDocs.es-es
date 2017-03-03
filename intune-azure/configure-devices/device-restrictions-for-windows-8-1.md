---
title: "Configuración de la restricción de dispositivos de Intune para Windows 8.1 | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: conozca la configuración de Intune que puede usar para controlar la configuración y la funcionalidad de dispositivos Windows 8.1."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fe5785e9-8d35-4ad7-95e8-d50f8d87154a
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: fa27874726c016840470c189910f8ea8a1878a43
ms.lasthandoff: 02/16/2017


---

# <a name="windows-81-and-later-device-restriction-settings-in-microsoft-intune"></a>Configuración de restricciones de dispositivos Windows 8.1 y versiones posteriores en Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>General
-     **Aplicar todas las configuraciones a Windows 10**: permite que la configuración de esta directiva se aplique a dispositivos Windows 10, además de a dispositivos Windows 8.1.
-     **Envío de datos de diagnóstico**: permite que el dispositivo envíe información de diagnóstico a Microsoft.
-     **Firewall**: requiere que el Firewall de Windows esté activado.
-     **Control de cuentas de usuario**: requiere el uso de Control de cuentas de usuario (UAC) en los dispositivos.
## <a name="password"></a>Contraseña
-     **Tipo de contraseña necesaria**: requiere que el usuario final escriba una contraseña para acceder al dispositivo.
-     **Minimum password length** (Longitud mínima de contraseña): configura la longitud mínima necesaria (de caracteres) para la contraseña.
-     **Número de errores de inicio de sesión antes de borrar el dispositivo**: borra el dispositivo tras el número de intentos de inicio de sesión erróneos especificado.
-     **Máximo de minutos de inactividad hasta que se bloquea la pantalla**: especifique el número de minutos que un dispositivo debe estar inactivo antes de que se exija una contraseña para desbloquearlo.
-     **Caducidad de la contraseña (días)**: especifica el número de días antes de que se deba cambiar la contraseña del dispositivo.
-     **Impedir la reutilización de contraseñas anteriores**: especifica si el usuario puede configurar contraseñas usadas anteriormente.
-     **PIN y contraseña de imagen**: permite el uso de una contraseña de imagen y un PIN. Una contraseña de imagen permite que el usuario inicie sesión mediante gestos en una imagen. Un PIN permite que los usuarios inicien sesión rápidamente con un código de cuatro dígitos.
-     **Cifrado**: requiere el cifrado de los archivos en el dispositivo.<br>Para forzar el cifrado en los dispositivos que ejecutan Windows 8.1, debe instalar la [Actualización de cliente de diciembre de 2014 MDM en Windows](https://support.microsoft.com/en-us/kb/3013816) en cada dispositivo.
Si habilita esta configuración para dispositivos Windows 8.1, todos los usuarios del dispositivo deben tener una cuenta de Microsoft.
Para que el cifrado funcione, el dispositivo debe cumplir los requisitos de certificación de hardware de [Microsoft InstantGo](https://blogs.windows.com/windowsexperience/2014/06/19/instantgo-a-better-way-to-sleep/#IBHULcTfI4PokO8X.97).
Al exigir el cifrado en un dispositivo, solo se puede obtener acceso a la clave de recuperación desde la cuenta Microsoft de los usuarios, a la que se obtiene acceso desde su cuenta de OneDrive. No se puede recuperar esta clave en nombre de un usuario.     



## <a name="browser"></a>Explorador
-     **Autofill (Rellenar automáticamente)**: permite a los usuarios cambiar la configuración de Autocompletar en el explorador.
-     **Advertencias de fraude**: habilita o deshabilita advertencias sobre posibles sitios web fraudulentos.
-     **SmartScreen**: habilita o deshabilita advertencias sobre posibles sitios web fraudulentos.
-     **JavaScript**: permite que el explorador ejecute scripts, como los de Java.
-     **Elementos emergentes**: habilita o deshabilita el bloqueador de elementos emergentes del explorador.
-     **Enviar encabezados de no seguimiento**: envía un encabezado de no seguimiento a sitios visitados en Internet Explorer.
-     **Plugins** (Complementos): permite a los usuarios agregar complementos a Internet Explorer.
-     **Entrada de palabra única en el sitio de la intranet**: permite el uso de una sola palabra para dirigir Internet Explorer a un sitio web como, por ejemplo, Bing.
-     **Detección automática del sitio de intranet**: ayuda a configura la seguridad de sitios de intranet en Internet Explorer.
-     **Nivel de seguridad de Internet**: establece el nivel de seguridad de Internet Explorer para sitios de Internet.
-     **Nivel de seguridad de la intranet**: establece el nivel de seguridad de Internet Explorer para sitios de intranet.
-     **Nivel de seguridad de sitios de confianza**: configura el nivel de seguridad para la zona de sitios de confianza.
-     **Nivel de seguridad alto para sitios restringidos**: configura el nivel de seguridad para la zona de sitios restringidos.
-     **Acceso al menú Modo de empresa**: permite a los usuarios tener acceso a las opciones del menú Modo de empresa desde Internet Explorer.
Si selecciona esta opción, también puede especificar una **Ubicación de informes de registro** que contenga una dirección URL a un informe que muestre los sitios web para los que los usuarios hayan activado el acceso en Modo de empresa.
-     **Ubicación de la lista de sitios del modo de empresa**: especifica la ubicación de la lista de sitios web que van a usar el modo de empresa cuando esté activo.
## <a name="cellular"></a>Móvil
-     **Itinerancia de datos**: permite la itinerancia de datos cuando el dispositivo está en una red de telefonía móvil.
## <a name="cloud-and-storage"></a>Nube y almacenamiento
-     **Dirección URL de carpetas de trabajo**: establece la dirección URL de la carpeta de trabajo para permitir que los documentos se sincronicen en todos los dispositivos.
-     **Acceso a la aplicación Correo de Windows sin una cuenta Microsoft**: permite el acceso a la aplicación Windows Mail sin una cuenta Microsoft.     

