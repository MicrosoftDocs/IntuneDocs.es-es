---
title: Aplicaciones Android con directivas de protección de aplicaciones
titlesuffix: Microsoft Intune
description: Obtenga información sobre las aplicaciones para Android con políticas de protección.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a6816285-8e43-4dc8-bca0-e80ec5ef01e6
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 16cef0b3e72c2e7815aada1c45c0e312b84931ab
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies"></a>Qué esperar cuando la aplicación Android está administrada por directivas de protección de aplicaciones 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Obtenga información sobre las aplicaciones para Android con políticas de protección de aplicaciones. Las directivas de protección de aplicaciones solo se aplican cuando se usan aplicaciones en el ámbito profesional. Por ejemplo, al acceder a una aplicación con una cuenta profesional o a archivos almacenados en la ubicación de OneDrive de su empresa.
##  <a name="accessing-apps"></a>Acceso a aplicaciones

La aplicación Portal de empresa se necesita en todas las aplicaciones para dispositivos Android que tengan directivas de protección de aplicaciones.

Instale Portal de empresa en todos los dispositivos que no estén inscritos en Intune. No se requiere que los usuarios inicien sesión en la aplicación Portal de Empresa para poder usar aplicaciones que tengan directivas de protección de aplicaciones.
La aplicación Portal de empresa le permite compartir datos en una ubicación protegida. Así pues, es un requisito incluso para los dispositivos no inscritos.


##  <a name="using-apps-with-multi-identity-support"></a>Uso de aplicaciones con compatibilidad con varias identidades

Las directivas de protección de aplicaciones solo se aplicarán cuando un usuario intente acceder a datos relacionados con la empresa.  Si el usuario accede a la aplicación para su uso personal, puede que observe distintos comportamientos.

Algunas aplicaciones admiten varias identidades. En este caso, Intune solo aplicará las directivas de protección de aplicaciones cuando un usuario acceda a datos de la empresa.  Por ejemplo, puede que un usuario reciba una solicitud de PIN.  En la **aplicación Outlook**, se genera una solicitud cuando un usuario inicia la aplicación. En la **aplicación OneDrive**, se genera una solicitud cuando un usuario escribe su cuenta profesional.  En Microsoft **Word**, **PowerPoint** y **Excel**, se genera una solicitud cuando un usuario accede a documentos de la empresa en OneDrive.
##  <a name="managing-user-accounts-on-the-device"></a>Administración de cuentas de usuario en el dispositivo

Intune solo admite la implementación de directivas de protección de aplicaciones en una cuenta de usuario por dispositivo.

* Dependiendo de la aplicación que use, el segundo usuario puede o no estar bloqueado en el dispositivo. Sin embargo, en todos los casos, solo el primer usuario que obtenga las directivas de protección de aplicaciones se verá afectado por la directiva.

  * **Microsoft Word**, **Excel** y **PowerPoint** no bloquearán el acceso a cuentas de usuario adicionales. No obstante, las directivas de protección de aplicaciones no se aplicarán a la cuenta de usuario.

  * En **aplicaciones de OneDrive y Outlook**, solo se puede usar una cuenta profesional.  La adición de varias cuentas profesionales está bloqueada en estas aplicaciones.  Sin embargo, puede quitar a un usuario de un dispositivo y agregar otro usuario a este.


* Antes de la implementación de directiva de protección de aplicación, puede que un dispositivo tenga varias cuentas de usuario existentes. En este caso, las directivas de protección de aplicaciones de Intune administrarán la primera cuenta en la que se hayan aplicado las directivas de protección de aplicaciones.


Lea el siguiente escenario de ejemplo para obtener información sobre cómo Intune gestiona varias cuentas de usuario.

El usuario A trabaja para dos empresas: la **empresa X** y la **empresa Y**. El usuario A tiene una cuenta profesional para cada empresa y en ambas se usa Intune para implementar directivas de protección de aplicaciones. La **Compañía X** implementa directivas de protección de aplicaciones **antes que** la **Compañía Y**. La cuenta asociada a la **empresa X** obtendrá la directiva de protección de aplicaciones, pero la cuenta asociada a la empresa Y no lo hará. Si quiere que la cuenta de usuario de la empresa Y se administre mediante las directivas de protección de aplicaciones, deberá quitar la cuenta de usuario de la empresa X.
### <a name="adding-a-second-account"></a>Agregar una segunda cuenta
####  <a name="android"></a>Android
Puede que reciba una solicitud para que quite la cuenta existente y agregue una nueva.  Para quitarla, vaya a **Configuración &gt;General &gt; Administrador de aplicaciones &gt;Portal de empresa. Seleccione "Borrar datos".**

![Captura de pantalla del mensajes de error e instrucciones para quitar la cuenta](./media/android-switch-user.png)

##  <a name="viewing-media-files-with-the-azure-information-protection-app-previously-known-as-rights-management-sharing-app"></a>Ver archivos multimedia con la aplicación Azure Information Protection (anteriormente conocida como aplicación Rights Management sharing)
Para ver archivos de imagen, AV y PDF de la empresa en dispositivos Android, use la [aplicación Azure Information Protection](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer).

Descargue esta aplicación de Google Play Store.  

Se admiten los siguientes tipos de archivos:

* **Audio:** AAC LC, HE-AACv1 (AAC+), HE-AACv2 (AAC+ mejorado), AAC ELD (AAC retraso bajo mejorado), AMR-NB, AMR-WB, FLAC, MP3, MIDI, Ogg Vorbis, PCM/WAVE.
* **Vídeo:** H.263, H.264 AVC, MPEG-4 SP, VP8.
* **Imagen:** jpg, pjpg, png, ppng, bmp, pbmp, gif, pgif, jpeg, pjpeg.
* **Documentos:** PDF, PPDF

------------

|                                                                                 <strong>pfile</strong>                                                                                 |                                                                      <strong>text</strong>                                                                      |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Pfile es un formato de "contenedor" estándar para archivos protegidos. Almacena el contenido cifrado y las licencias de Azure Information Protection en un contenedor. Puede usarse para proteger cualquier tipo de archivo. | Los archivos de texto, incluidos XML, CSV, etc. pueden abrirse para verse en la aplicación incluso cuando están protegidos. Tipos de archivo: txt, ptxt, csv, pcsv, log, plog, xml, pxml. |

---------------
## <a name="next-steps"></a>Pasos siguientes
[What to expect when your iOS app is managed by app protection policies](app-protection-enabled-apps-ios.md) (Qué esperar cuando la aplicación iOS se administra con directivas de protección de aplicaciones)

### <a name="see-also"></a>Vea también
[Creación e implementación de directivas de protección de aplicaciones con Microsoft Intune](app-protection-policies.md)
