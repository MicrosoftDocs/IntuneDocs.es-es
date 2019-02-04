---
title: Creación de perfiles de dispositivos iOS o Mac OS con Microsoft Intune - Azure |Microsoft Docs
description: Agregue o cree un perfil de dispositivo para iOS o macOS y después configure los valores de AirPrint, diseño de la pantalla principal, notificaciones de aplicaciones, dispositivo compartido, inicio de sesión único y configuración de filtro de contenido web en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 4542a65afa87668702620a1b50443c9844692a87
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831282"
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>Agregar la configuración de características de dispositivos iOS o Mac OS en Intune

Intune incluye muchas características y configuraciones que ayudan a los administradores a controlar dispositivos iOS y macOS. Por ejemplo, los administradores pueden:

- Permitir a los usuarios acceder a impresoras AirPrint en la red
- Agregar aplicaciones y carpetas a la pantalla principal, incluida la incorporación de nuevas páginas
- Elegir si se muestran las notificaciones de aplicación y cómo se muestran
- Configurar la pantalla de bloqueo para mostrar un mensaje o la etiqueta de recurso, especialmente para los dispositivos compartidos
- Proporcionar a los usuarios una experiencia de inicio de sesión único para compartir las credenciales entre aplicaciones
- Filtrar los sitios web que usan el lenguaje para adultos y permitir o bloquear sitios web específicos

Estas características están disponibles en Intune y el administrador puede configurarlas. Intune usa "perfiles de configuración" para crear y personalizar estas configuraciones para las necesidades de su organización. Después de agregar estas características en un perfil, puede insertar o implementar el perfil en dispositivos iOS y macOS de su organización.

En este artículo se muestra cómo crear un perfil de configuración de dispositivo. También puede ver todas las configuraciones disponibles para dispositivos [iOS](ios-device-features-settings.md) y [macOS](macos-device-features-settings.md).

## <a name="create-a-device-profile"></a>Creación del perfil de un dispositivo

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** > seleccione **Intune**.
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre descriptivo para el nuevo perfil.
    - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
    - **Plataforma**: seleccione la plataforma:
        - **iOS**
        - **macOS**
    - **Tipo de perfil**: seleccione **Características del dispositivo**.
    - **Configuración**: especifique la configuración que desee definir. Para una lista de todas las configuraciones, y lo que hacen, consulte:

        - [iOS](ios-device-features-settings.md)
        - [macOS](macos-device-features-settings.md)

4. Cuando haya terminado, seleccione **Aceptar**y elija **Crear** para guardar los cambios.

El perfil se crea y se muestra en la lista. Asegúrese de [asignar el perfil](device-profile-assign.md) y [supervise su estado](device-profile-monitor.md).

## <a name="next-steps"></a>Pasos siguientes

Una vez creado el perfil, está listo para asignarlo. Después, [asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

Ver todas las configuraciones de características de dispositivo para dispositivos [iOS](ios-device-features-settings.md) y [macOS](macos-device-features-settings.md).