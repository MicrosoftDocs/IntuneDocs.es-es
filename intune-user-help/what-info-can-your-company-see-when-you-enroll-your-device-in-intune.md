---
title: ¿Qué información puede ver la empresa cuando el usuario inscribe el dispositivo?
description: Explica lo que el personal de TI puede y no puede ver en su dispositivo administrado.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/18/2018
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
ms.openlocfilehash: bdf08ccac21407bc2572f1133b2fe8d45548342f
ms.sourcegitcommit: cac71802b2782700f0d52ea114089d73620cd1ed
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50679260"
---
# <a name="what-information-can-my-company-see-when-i-enroll-my-device"></a>¿Qué información puede ver mi empresa cuando inscribo mi dispositivo?

Su empresa no puede ver su información personal cuando inscribe un dispositivo con Microsoft Intune. Cuando inscribe un dispositivo, da permiso a su empresa para ver algunos fragmentos de información del dispositivo, como el modelo de dispositivo y el número de serie. Su empresa usa esta información para ayudar a proteger los datos corporativos en el dispositivo.

**Contenido que su empresa no puede ver nunca:**

- Historial de llamadas y exploración web
- Mensajes de texto y de correo electrónico
- Contactos
- Calendario
-   Contraseñas
- Imágenes, ni siquiera lo que hay en la aplicación de fotos ni en el álbum de cámara

**Contenido que su empresa puede ver siempre:**

- Modelo del dispositivo, como Google Pixel
- Fabricante, como Microsoft
- Sistema operativo, como iOS
- Nombres de aplicaciones, como Microsoft Word
- Propietario del dispositivo
- Nombre del dispositivo
- Número de serie

**Contenido que su empresa es posible que vea:**

-  Número de teléfono: en el caso de los dispositivos propiedad de la **empresa**, se puede ver el número de teléfono completo. En el caso de los dispositivos **personales**, únicamente son visibles para la empresa los últimos cuatro dígitos del número de teléfono. Puede ver el **Tipo de propiedad** de cada dispositivo abriendo la página **Detalles del dispositivo** correspondiente.
-  Ubicación: su empresa nunca puede ver la ubicación de su dispositivo, excepto si tiene un dispositivo iOS que está supervisado y se ha perdido. [¿Cómo puedo saberlo?](https://go.microsoft.com/fwlink/?linkid=853816)
- Inventario de aplicaciones: si su empresa usa Mobile Threat Defense, se podrá consultar información adicional sobre las aplicaciones instaladas en el dispositivo iOS. Obtenga más información sobre [Mobile Threat Defense](you-are-prompted-to-install-mtd-ios.md).
- Información de la red: parte de la información sobre las conexiones de red de los dispositivos Android puede estar disponible para el soporte técnico de su empresa. Por ejemplo, si la empresa requiere que los dispositivos permanezcan dentro de cierto edificio, el dispositivo podría identificar la red donde está conectado. 
