---
title: Quitar un dispositivo iOS de Intune | Microsoft Docs
description: Describe cómo anular la inscripción de un dispositivo iOS de Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 28914db1-3e62-45f5-9632-b0d2a808a44d
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: bd5384945158f3d0ef3035eaf9bc2f8375d8b153
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75859022"
---
# <a name="remove-your-ios-device-from-intune"></a>Quitar un dispositivo iOS de Intune

Una vez quitado el dispositivo iOS de Intune, este ya no podrá acceder a los recursos de la empresa ni será administrado por Intune.


## <a name="removing-the-device-from-my-devices"></a>Quitar el dispositivo de Mis dispositivos

Para quitar el dispositivo de Intune, siga estos pasos o vea este vídeo:


1. En la aplicación Portal de empresa, pulse **Dispositivos** y seleccione el dispositivo cuya inscripción desee anular. Si solo tiene un dispositivo, cuando pulse **Dispositivos** irá directamente a la pantalla de detalles del dispositivo.

2. Junto a **CAMBIAR NOMBRE**, pulse el botón de puntos suspensivos y luego seleccione **Quitar dispositivo** > **Quitar**.  

    |![Captura de la pantalla Dispositivos de la aplicación Portal de empresa en la que se muestran las opciones disponibles después de que el usuario haya hecho clic en Quitar. Muestra los botones "Quitar dispositivo", "Restablecimiento de fábrica" y "Cancelar".](/intune-user-help/media/cp_ios_unenroll_after_1804_001.png)|

    |![Captura de la pantalla Dispositivos de la aplicación Portal de empresa en la que se muestran las opciones disponibles después de que el usuario haya hecho clic en el botón Quitar dispositivo. Muestra el botón "Quitar" resaltado en rojo y los botones "Más información" y "Cancelar" resaltados en azul.](/intune-user-help/media/cp_ios_unenroll_after_1804_002.png)|


    Cuando se anula la inscripción de un dispositivo de Intune, ocurre lo siguiente:

    - El dispositivo deja de aparecer en el portal de empresa.

    - No se podrán instalar aplicaciones desde el Portal de empresa.

    - Dejará de aplicarse cualquier configuración que se haya modificado en el dispositivo cuando se agregó, por ejemplo, la opción para deshabilitar la cámara o exigir una determinada longitud de contraseña.

    - Es posible que deje de tener acceso en su dispositivo a algunos recursos de la empresa, como recursos compartidos de archivos o sitios web internos.

    - No se podrán utilizar las aplicaciones y los datos de la empresa.

    - No se podrá conectar a la red de su empresa mediante Wi-Fi o una red privada virtual (VPN).

    - Los perfiles de correo electrónico de empresa se quitan del dispositivo.

    - Los dispositivos que están configurados para el correo electrónico no aparecerán en el sitio web o en la aplicación Portal de empresa.

    - Las aplicaciones se desinstalarán. Se quitarán los datos de la aplicación de empresa.

## <a name="removing-data-collected-by-the-company-portal-app"></a>Eliminación de datos recopilados por la aplicación Portal de empresa

El Portal de empresa almacena los datos locales en tres ubicaciones del dispositivo.

- **Registros de información**: los datos estándar recopilados por Microsoft acerca de la actividad de la aplicación (por ejemplo, cuánto tiempo estuvo abierta la aplicación o si se ha bloqueado) se borran automáticamente cuando el dispositivo se quita del Portal de empresa.

- **Análisis de Apple**: datos estándar recopilados por Apple sobre el bloqueo de la aplicación. La única manera de quitar esta información es restablecer el dispositivo a la configuración de fábrica. Esto borrará toda la información personal en el dispositivo. Para ello, abra **Ajustes** > **General** > **Restablecer** > **Borrar contenidos y ajustes**.

- **Cadena de claves**: el dispositivo almacena en la cadena de claves las contraseñas y otra información que se usa para inicios de sesión. Las aplicaciones de Microsoft comparten la información de inicio de sesión con todas las aplicaciones desarrolladas por Microsoft que haya en el dispositivo, como Microsoft Outlook y Microsoft Authenticator. Al igual que con el análisis de Apple, la única manera de quitar esta información es restablecer el dispositivo a la configuración de fábrica. Esto borrará toda la información personal en el dispositivo. Para ello, abra **Ajustes** > **General** > **Restablecer** > **Borrar contenidos y ajustes**.


¿Aún necesita ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
