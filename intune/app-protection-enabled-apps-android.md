---
title: "Aplicaciones Android con directivas de protección de aplicaciones"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: este tema describe qué esperar cuando la aplicación Android está administrada por directivas de protección de aplicaciones."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a6816285-8e43-4dc8-bca0-e80ec5ef01e6
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: c1704e5e63be434eaacaeec6e575640310ce74b3
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies"></a>Qué esperar cuando la aplicación Android está administrada por directivas de protección de aplicaciones 
[!INCLUDE[azure_preview](./includes/azure_preview.md)]En este tema se describe la experiencia del usuario en aplicaciones con directivas de protección de aplicaciones. Las directivas de protección de aplicaciones solo se aplican cuando se usan aplicaciones en el contexto profesional: por ejemplo, cuando se accede a aplicaciones con la cuenta profesional o cuando se accede a los archivos almacenados en la ubicación empresarial de OneDrive.
##  <a name="accessing-apps"></a>Acceso a aplicaciones

La aplicación Portal de empresa se necesita en todas las aplicaciones que están asociadas a directivas de MAM en los dispositivos Android.

En los dispositivos no inscritos en Intune, la aplicación Portal de empresa debe instalarse en el dispositivo. Sin embargo, el usuario no tiene que iniciar la aplicación Portal de empresa ni iniciar sesión en ella para poder usar aplicaciones administradas mediante directivas de protección de aplicaciones.
La aplicación Portal de empresa es una manera de que Intune pueda compartir datos en una ubicación protegida, por lo que es un requisito aunque el dispositivo no esté inscrito en Intune.


##  <a name="using-apps-with-multi-identity-support"></a>Uso de aplicaciones con compatibilidad con varias identidades

Las directivas de protección de aplicaciones solo se aplican en el contexto profesional cuando se usa la aplicación, por lo que es posible que observe distintos comportamientos de las aplicaciones según el contexto: profesional o personal.

En las aplicaciones que admiten varias identidades, Intune solo aplica las directivas de protección de aplicaciones cuando el usuario final está usando la aplicación en el contexto laboral.  Por ejemplo, el usuario final verá una solicitud de PIN al acceder a los datos de trabajo.  En la **aplicación Outlook**, al usuario final se le pide un PIN al iniciar la aplicación. En la **aplicación OneDrive**, esto ocurre cuando el usuario final escribe en la cuenta de trabajo.  En Microsoft **Word**, **PowerPoint* y **Excel**, esto ocurre cuando el usuario final accede a documentos almacenados en la ubicación de OneDrive para la Empresa.
##  <a name="managing-user-accounts-on-the-device"></a>Administración de cuentas de usuario en el dispositivo

En Intune solo se pueden implementar directivas de protección de aplicaciones en una única cuenta de usuario por dispositivo.

* Dependiendo de la aplicación que use, el segundo usuario puede o no estar bloqueado en el dispositivo. Sin embargo, en todos los casos, solo el primer usuario que obtenga las directivas de protección de aplicaciones se verá afectado por la directiva.

  * **Microsoft Word**, **Excel** y **PowerPoint** no bloquean una segunda cuenta de usuario, pero esa segunda cuenta no se verá afectada por las directivas de protección de aplicaciones.

  * En **aplicaciones de OneDrive y Outlook**, solo se puede usar una cuenta profesional.  La adición de varias cuentas profesionales está bloqueada en estas aplicaciones.  Sin embargo, puede quitar un usuario y agregar un usuario diferente en el dispositivo.


* Si un dispositivo tiene varias cuentas de usuario existentes antes de implementar las directivas de protección de aplicaciones, solo la cuenta en la que estas directivas se implementan primero se administra mediante directivas de protección de aplicaciones de Intune.


Consulte el siguiente escenario de ejemplo para ahondar aún más en cómo se tratan varias cuentas de usuario.

El usuario A trabaja para dos empresas: la **empresa X** y la **empresa Y**. El usuario A tiene una cuenta profesional para cada empresa y en ambas se usa Intune para implementar directivas de protección de aplicaciones. La **Compañía X** implementa directivas de protección de aplicaciones **antes que** la **Compañía Y**. La cuenta asociada a la **Compañía X** obtendrá la directiva de protección de aplicaciones, pero no la cuenta asociada a la Compañía Y. Si quiere que la cuenta de usuario asociada a la Compañía Y se administre por medio de directivas de protección de aplicaciones, deberá quitar la cuenta de usuario asociada a la Compañía X.
### <a name="adding-a-second-account"></a>Agregar una segunda cuenta
####  <a name="android"></a>Android
Si usa un dispositivo Android, puede que aparezca un mensaje de bloqueo con instrucciones para quitar la cuenta existente y agregar una nueva.  Para quitar la cuenta existente, vaya a **Configuración &gt; General &gt; Administrador de aplicaciones &gt; Portal de empresa y seleccione “Borrar datos”**.

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
|**pfile**|**text**|
|----|----|
|Pfile es un formato "contenedor" genérico para archivos protegidos que encapsula el contenido cifrado y las licencias de Azure Information Protection y puede usarse para proteger cualquier tipo de archivo.|Los archivos de texto, incluidos XML, CSV, etc. pueden abrirse para verse en la aplicación incluso cuando están protegidos. Tipos de archivo: txt, ptxt, csv, pcsv, log, plog, xml, pxml.|
---------------
## <a name="next-steps"></a>Pasos siguientes
[Qué esperar cuando la aplicación iOS se administra con directivas de protección de aplicaciones](app-protection-enabled-apps-ios.md)

### <a name="see-also"></a>Consulte también
[Creación e implementación de directivas de protección de aplicaciones con Microsoft Intune](app-protection-policies.md)

