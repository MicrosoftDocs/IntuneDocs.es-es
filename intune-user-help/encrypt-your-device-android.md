---
title: "Cómo proteger el dispositivo Android con cifrado | Microsoft Docs"
description: Proteger su dispositivo Android
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 11/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d4430e92-04cc-48e9-a77a-81b95a90b6b3
searchScope:
- User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 54f592c8ece9180ed6ce8a722f09ff168f06435d
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-protect-your-android-device-using-encryption"></a>Cómo proteger el dispositivo Android mediante el cifrado

Cuando cifra un dispositivo, está ajustando la información en una capa de código de protección que evita que los usuarios sin autorización tengan acceso a él. Para asegurarnos de que su información está protegida, la organización le pide que cifre su dispositivo Android antes de poder acceder a archivos, correos electrónicos o datos de la empresa.

> [!Note]
> No es posible cifrar ciertos dispositivos Android, como algunos de Huawei y los de Vivo y OPPO. Descubra más [aquí](your-device-appears-encrypted-but-cp-says-otherwise-android.md).

Si anula la inscripción del dispositivo, este permanecerá cifrado.

1.  Asegúrese de que se ha establecido un PIN o una contraseña de bloqueo de pantalla para el dispositivo.

2.  En **Configuración**, elija **Seguridad** > **Cifrar dispositivo**.
    (En algunos teléfonos, tendrá que elegir **Almacenamiento** > **Cifrado de almacenamiento** o **Almacenamiento** > **Pantalla de bloqueo y seguridad** > **Otras opciones de seguridad** para poder encontrar la opción "Cifrar").

3.  Siga las instrucciones en pantalla. Durante el cifrado, el dispositivo podría reiniciarse varias veces.

### <a name="what-to-do-if-you-have-issues"></a>Qué hacer si tiene problemas
**Problema:** con el dispositivo ya cifrado, ocurre una de las siguientes cosas:

- El botón de cifrado está deshabilitado.
- Ve un mensaje en el que se indica que aún es necesario realizar el cifrado.
- Obtiene errores al intentar usar la aplicación Portal de empresa.

**Opciones que puede probar**

- Asegúrese de que el dispositivo está cargado y conectado.
- Asegúrese de que ha establecido un PIN o una contraseña en el dispositivo.
- Si ya ha configurado un PIN o una contraseña en el dispositivo, intente los pasos siguientes que podría requerir el equipo de soporte técnico de su empresa para hacer que el dispositivo sea más seguro. Los nombres de menú que verá pueden diferir ligeramente de los incluidos en los pasos, en función del tipo de dispositivo Android que tenga.

    1. Vaya a **Configuración** > **Pantalla de bloqueo y seguridad** > **Bloqueo de pantalla**. Confirme su PIN o contraseña actual.

    2. En la pantalla **Elige un bloqueo**, elija el tipo de bloqueo de pantalla que quiere usar. 

    3. Después de elegir el bloqueo de pantalla, vuelva a **Pantalla de bloqueo y seguridad** y seleccione **Inicio seguro**. 
    
    4. En la pantalla **Inicio seguro**, pulse **Solicitar PIN para iniciar el dispositivo** y **Continuar**.

    5. Elija un PIN (puede escribir el mismo que haya especificado anteriormente) y pulse **Confirma el número PIN**.

    6. Abra la aplicación de Portal de empresa, seleccione el dispositivo y pulse **Comprobar cumplimiento**.

¿Sigue necesitando ayuda? Póngase en contacto con el equipo de soporte técnico de su empresa (visite el [sitio web del Portal de empresa](https://portal.manage.microsoft.com#HelpDeskDialog) para obtener la información de contacto), o escriba al <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with encryption on my Android device&body=Describe the issue you're experiencing here.">equipo de Microsoft Android</a>.
