---
title: Inscriba el dispositivo iOS proporcionado por la organización en la administración. | Microsoft Docs
description: En este artículo se describe cómo inscribir un dispositivo iOS en Intune comprado o proporcionado por la organización.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f4e7d87e-56d1-43e4-8e88-2f62cf0999e2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: japoehlm
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: c592b558ace0a2a39059de9f64531f1e078c539d
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "55847767"
---
# <a name="enroll-your-organization-provided-ios-device-in-management"></a>Inscripción de dispositivos iOS proporcionados por la organización en la administración

Obtenga información sobre cómo administrar un dispositivo iOS nuevo en Intune.  

Los dispositivos iOS proporcionados por su empresa o centro educativo a menudo están preconfigurados antes de recibirlos. La organización enviará estas opciones configuradas previamente al dispositivo después de encenderlo e iniciar sesión por primera vez. Una vez configurado el dispositivo, recibirá acceso a los recursos profesionales o educativos.  

Para comenzar con la configuración, encienda el dispositivo e inicie sesión con sus credenciales profesionales o educativas. A continuación, en este artículo se describirán los pasos y las pantallas que verá en el asistente de configuración. 

## <a name="what-is-apple-dep"></a>¿Qué es DEP de Apple?
Es posible que la organización haya comprado los dispositivos a través de lo que se denomina *Programa de inscripción de dispositivos de Apple* (DEP). DEP de Apple permite a las organizaciones comprar una gran cantidad de dispositivos iOS o macOS. De este modo, pueden configurar y administrar esos dispositivos con su proveedor de administración de dispositivos móviles preferido, como Intune. Si es un administrador y quiere obtener más información sobre DEP de Apple, vea [Inscripción automática de dispositivos iOS con el Programa de inscripción de dispositivos de Apple](https://docs.microsoft.com/intune/device-enrollment-program-enroll-ios).  

## <a name="set-up-your-ios-device"></a>Configuración de un dispositivo iOS  
Si usa un dispositivo iOS propio, que la organización no le haya proporcionado, siga los pasos para los [dispositivos personales y Bring Your Own Device](enroll-your-device-in-intune-ios.md).  

1. Encienda el dispositivo iOS. 
2. Una vez seleccionado el **idioma**, conecte el dispositivo a la red Wi-Fi.
3. En la pantalla de **configuración del dispositivo iOS**, elija lo que quiera hacer: 
 
   - **Set Up as New device** (Configurar como un nuevo dispositivo)
   - **Restore from iCloud Backup** (Restaurar desde la copia de seguridad de iCloud)
   - **Restore from iTunes Backup** (Restaurar desde la copia de seguridad de iTunes)

4. Una vez que se haya conectado a la red Wi-Fi, aparecerá la pantalla **Configuración**, donde se le indicará que **[su empresa] configurará automáticamente su dispositivo.**

   **La configuración permite que [su empresa] administre este dispositivo de forma inalámbrica. Un administrador puede ayudarle a configurar las cuentas de red y correo electrónico, instalar y configurar aplicaciones y administrar la configuración de manera remota. Un administrador puede deshabilitar características, instalar y quitar aplicaciones, supervisar y restringir el tráfico de Internet y borrar de manera remota este dispositivo.**
 
   **Configuración proporcionada por: Equipo de iOS de [su empresa] [dirección]**

5. Inicie sesión con su identificador de Apple. El inicio de sesión le permite instalar la aplicación de Portal de empresa e instalar el perfil de administración con el que su empresa le proporcionará acceso a los recursos, como el correo electrónico y las aplicaciones. 
6. Acepte los **términos y condiciones** y decida si desea enviar información de diagnóstico a Apple.
7. Cuando haya concluido la inscripción, puede que el dispositivo le pida que lleve a cabo más acciones, Algunos de estos pasos pueden consistir en escribir la contraseña de acceso al correo electrónico o en configurar un código de acceso.

¿Sigue necesitando ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
