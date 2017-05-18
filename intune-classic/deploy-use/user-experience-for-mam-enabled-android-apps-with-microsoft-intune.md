---
title: "Aplicaciones Android con directivas de protección de aplicaciones | Microsoft Docs"
description: "En este tema se describe qué esperar cuando la aplicación está administrada por directivas de protección de aplicaciones."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 53c8e2ad-f627-425b-9adc-39ca69dbb460
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 665d3347636d5ec0c698ffb93b768028c9d59ce3
ms.openlocfilehash: 64a31832012aba65c4ad5b1c3dc67fa4aa748246
ms.lasthandoff: 03/07/2017


---

# <a name="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies"></a>Qué esperar cuando la aplicación Android está administrada por directivas de protección de aplicaciones

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

En este tema se describe la experiencia del usuario en aplicaciones con directivas de protección de aplicaciones. Las directivas de protección de aplicaciones solo se aplican cuando se usan aplicaciones en el contexto laboral: por ejemplo, cuando el usuario obtiene acceso a las aplicaciones con la cuenta profesional o a archivos que están almacenados en la ubicación empresarial de OneDrive.
##  <a name="access-apps"></a>Acceso a las aplicaciones

La aplicación Portal de empresa se necesita en todas las aplicaciones que están asociadas a directivas de protección de aplicaciones en los dispositivos Android.

En el caso de los dispositivos que no están inscritos en Intune, la aplicación Portal de empresa debe instalarse en el dispositivo. En cambio, el usuario no tiene que iniciar la aplicación Portal de empresa ni iniciar sesión en ella para poder usar aplicaciones administradas por directivas de protección de aplicaciones.

La aplicación Portal de empresa es una manera de que Intune pueda compartir datos en una ubicación protegida. Por lo tanto, la aplicación Portal de empresa es un requisito para todas las aplicaciones asociadas con las directivas de protección de aplicaciones, incluso si el dispositivo no está inscrito en Intune.


##  <a name="use-apps-with-multi-identity-support"></a>Uso de aplicaciones con compatibilidad con varias identidades

Las directivas de protección de aplicaciones solo se aplican en el contexto laboral. Por lo tanto, la aplicación podría comportarse de manera distinta si el contexto es laboral o personal.

Por ejemplo, el usuario obtiene una solicitud de PIN al obtener acceso a los datos de trabajo. En la **aplicación Outlook**, al usuario se le pide un PIN al iniciar la aplicación. En la **aplicación OneDrive**, al usuario se le pide el PIN cuando escribe la cuenta profesional. En Microsoft **Word**, **PowerPoint** y **Excel**, al usuario se le pide el PIN cuando obtiene acceso a documentos que se encuentran almacenados en la ubicación OneDrive para la Empresa.

##  <a name="manage-user-accounts-on-the-device"></a>Administración de cuentas de usuario en el dispositivo

Intune solo admite la implementación de directivas de protección de aplicaciones en una cuenta de usuario por dispositivo.

* Dependiendo de la aplicación que use, el segundo usuario puede estar bloqueado en el dispositivo. Sin embargo, en todos los casos, solo el primer usuario que obtenga las directivas de protección de aplicaciones se verá afectado por la directiva.

  * **Microsoft Word**, **Excel** y **PowerPoint** no bloquean una segunda cuenta de usuario, pero esa segunda cuenta no se verá afectada por las directivas de protección de aplicaciones.

  * En **aplicaciones de Outlook** y **OneDrive**, solo se puede usar una cuenta profesional.  No puede agregar varias cuentas profesionales para estas aplicaciones.  Sin embargo, puede quitar un usuario y agregar un usuario diferente en el dispositivo.


* Si un dispositivo tiene varias cuentas de usuario existentes antes de implementar las directivas de protección de aplicaciones, solo la cuenta en la que estas directivas se implementan primero se administra mediante directivas de protección de aplicaciones de Intune.


Consulte el siguiente escenario de ejemplo para profundizar aún más en cómo se tratan varias cuentas de usuario.

El usuario A trabaja para dos empresas: la **empresa X** y la **empresa Y**. El usuario A tiene una cuenta profesional para cada empresa y en ambas se usa Intune para implementar directivas de protección de aplicaciones. La **Compañía X** implementa directivas de protección de aplicaciones **antes que** la **Compañía Y**. La cuenta que está asociada a la **empresa X** obtiene la directiva de protección de aplicaciones, pero no la cuenta asociada a la empresa Y. Si quiere que la cuenta de usuario asociada a la empresa Y se administre por medio de las directivas de protección de aplicaciones, deberá quitar la cuenta de usuario asociada a la empresa X.
### <a name="add-a-second-account"></a>Incorporación de una segunda cuenta
####  <a name="android"></a>Android
Si usa un dispositivo Android, podría aparecer un mensaje de bloqueo con instrucciones para quitar la cuenta existente y agregar una nueva.  Para quitar la cuenta existente, vaya a **Configuración &gt;General &gt; Administrador de aplicaciones &gt;Portal de empresa**. Luego, elija **Borrar datos**.

![Captura de pantalla del mensajes de error e instrucciones para quitar la cuenta](../media/AppManagement/Android_SwitchUser.png)

##  <a name="view-media-files-with-the-azure-information-protection-app"></a>Visualización de archivos multimedia con la aplicación de Azure Information Protection
Para ver archivos de imagen, AV y PDF de la empresa en dispositivos Android, use la [aplicación Azure Information Protection](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer) (conocida anteriormente como la aplicación Rights Management sharing).

Descargue esta aplicación de Google Play Store.  

Se admiten los siguientes tipos de archivos:

* **Audio:** AAC LC, HE-AACv1 (AAC+), HE-AACv2 (AAC+ mejorado), AAC ELD (AAC retraso bajo mejorado), AMR-NB, AMR-WB, FLAC, MP3, MIDI, Ogg Vorbis, PCM/WAVE
* **Vídeo:** H.263, H.264 AVC, MPEG-4 SP, VP8
* **Imagen:** .jpg, .pjpg, .png, .ppng, .bmp, .pbmp, .gif, .pgif, .jpeg, .pjpeg
* **Documentos:** PDF, PPDF


|**pfile**|**text**|
|----|----|
|Pfile es un formato "contenedor" genérico para archivos protegidos que encapsula el contenido cifrado y las licencias de Azure Information Protection. Puede usarse para proteger cualquier tipo de archivo.|Los archivos de texto, incluidos XML, CSV, etc. pueden abrirse para verse en la aplicación incluso cuando están protegidos. Tipos de archivo: .txt, .ptxt, .csv, .pcsv, .log, .plog, .xml, .pxml.|

## <a name="next-steps"></a>Pasos siguientes
[Qué esperar cuando la aplicación iOS se administra con directivas de protección de aplicaciones](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)

### <a name="see-also"></a>Consulte también
[Crear e implementar directivas de administración de aplicaciones móviles con Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)

