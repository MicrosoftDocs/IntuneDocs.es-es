---
title: ¿Qué información puede ver la empresa cuando el usuario inscribe el dispositivo?
description: Explica lo que el personal de TI puede y no puede ver en su dispositivo administrado.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 12655728-a1af-4d89-97bc-925fe36c0dc4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.collection: M365-identity-device-management
ms.openlocfilehash: 91ea3aab5cd04624bfa036615b8d7710573bcae1
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "55846985"
---
# <a name="what-information-can-my-organization-see-when-i-enroll-my-device"></a>¿Qué información puede ver mi organización cuando inscribo mi dispositivo?

Su organización no puede ver su información personal cuando inscribe un dispositivo a Microsoft Intune. Cuando inscribe un dispositivo, da permiso a su organización para que pueda ver cierta información del dispositivo, como el modelo y el número de serie. Su organización usa esta información para proteger los datos corporativos del dispositivo.

**Contenido que no puede ver nunca su organización:**

- Historial de llamadas y exploración web
- Mensajes de texto y de correo electrónico
- Contactos
- Calendario
-   Contraseñas
- Imágenes, ni siquiera lo que hay en la aplicación de fotos ni en el álbum de cámara
- Archivos

**Contenido que puede ver siempre su organización:**

- Modelo del dispositivo, como Google Pixel
- Fabricante del dispositivo (por ejemplo, Microsoft)
- Sistema operativo y versión (por ejemplo, iOS 12.0.1)
- Nombres de las aplicaciones (por ejemplo, Microsoft Word): en los dispositivos personales, su organización solo puede ver el inventario de aplicaciones administradas. En los dispositivos de propiedad corporativa, su organización puede ver todo el inventario de aplicaciones.
- Propietario del dispositivo
- Nombre del dispositivo
- Número de serie del dispositivo
- IMEI

**Contenido que su organización podría ver:**

-  Número de teléfono: en el caso de los dispositivos propiedad de la **empresa**, puede ver su número de teléfono completo. En el caso de los dispositivos **personales**, su organización solo puede ver los últimos cuatro dígitos de su número de teléfono. Puede ver el **Tipo de propiedad** de cada dispositivo abriendo la página **Detalles del dispositivo** correspondiente.
- Espacio de almacenamiento del dispositivo: si no puede instalar una aplicación necesaria, su organización podría consultar el espacio de almacenamiento del dispositivo para averiguar si el espacio es insuficiente.  
-  Ubicación: la organización nunca puede ver la ubicación del dispositivo, a menos que necesite recuperar un dispositivo iOS perdido supervisado. Visite la [documentación de Apple iOS](https://go.microsoft.com/fwlink/?linkid=853816) para más información sobre los dispositivos supervisados.  
- Inventario de aplicaciones: si en la organización se usa Mobile Threat Defense, se podrá ver información adicional sobre las aplicaciones instaladas en el dispositivo iOS. Obtenga más información sobre [Mobile Threat Defense](you-are-prompted-to-install-mtd-ios.md).
- Información de la red: parte de la información sobre las conexiones de red de los dispositivos Android puede estar disponible para el soporte técnico de su organización. Por ejemplo, si su organización exige que los dispositivos permanezcan dentro de cierto edificio, el dispositivo podría identificar la red donde está conectado. 
