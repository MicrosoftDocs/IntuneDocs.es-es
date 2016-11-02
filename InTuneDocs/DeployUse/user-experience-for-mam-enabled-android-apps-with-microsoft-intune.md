---
title: Aplicaciones Android con directivas MAM | Microsoft Intune
description: "En este tema se describe qué esperar cuando la aplicación está administrada por directivas de administración de aplicaciones móviles."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 10/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 53c8e2ad-f627-425b-9adc-39ca69dbb460
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 389daf0ed39fa2cd4b2e5d6e52cbd6809a568c9e
ms.openlocfilehash: 546b909737b4ea34bd747880fe8ed2d366c6b18a


---

# Qué esperar cuando la aplicación Android está administrada por directivas MAM
En este tema se describe la experiencia del usuario en aplicaciones con directivas MAM. Las directivas de administración de aplicaciones móviles (MAM) solo se aplican cuando se usan aplicaciones en el contexto laboral: por ejemplo, al acceder a aplicaciones con la cuenta profesional o a archivos almacenados en la ubicación empresarial de OneDrive.
##  Acceso a aplicaciones

La aplicación de portal de empresa es necesaria en todas las aplicaciones asociadas a directivas de MAM en los dispositivos Android.

En los dispositivos no inscritos en Intune, la aplicación Portal de empresa debe instalarse en el dispositivo. En cambio, el usuario no tiene que iniciar la aplicación Portal de empresa ni iniciar sesión en ella para poder usar aplicaciones administradas por directivas MAM.
La aplicación Portal de empresa es una manera de que Intune pueda compartir datos en una ubicación protegida, por lo que es un requisito aunque el dispositivo no esté inscrito en Intune.


##  Uso de aplicaciones con compatibilidad con varias identidades

Las directivas MAM solo se aplican en el contexto laboral cuando se usa la aplicación, por lo que es posible que observe distintos comportamientos según el contexto: laboral o personal.

En las aplicaciones que admiten varias identidades, Intune solo aplica las directivas MAM cuando el usuario final está usando la aplicación en el contexto laboral.  Por ejemplo, el usuario final verá una solicitud de PIN al acceder a los datos de trabajo.  En la **aplicación Outlook**, al usuario final se le pide un PIN al iniciar la aplicación. En la **aplicación OneDrive**, esto ocurre cuando el usuario final escribe en la cuenta de trabajo.  En Microsoft **Word**, **PowerPoint* y **Excel**, esto ocurre cuando el usuario final accede a documentos almacenados en la ubicación de OneDrive para la empresa.
##  Administración de cuentas de usuario en el dispositivo

En Intune solo se pueden implementar directivas de MAM en una única cuenta de usuario por dispositivo.

* Dependiendo de la aplicación que use, el segundo usuario puede o no estar bloqueado en el dispositivo. Pero, en todos los casos, solo el primer usuario que obtiene las directivas de MAM se verá afectado por la directiva.

  * **Microsoft Word**, **Excel** y **PowerPoint** no bloquean una segunda cuenta de usuario, pero esa segunda cuenta no se verá afectada por las directivas de MAM.

  * En **aplicaciones de OneDrive y Outlook**, solo se puede usar una cuenta profesional.  La adición de varias cuentas profesionales está bloqueada en estas aplicaciones.  Sin embargo, puede quitar un usuario y agregar un usuario diferente en el dispositivo.


* Si un dispositivo tiene varias cuentas de usuario existentes antes de implementar las directivas de MAM, estas directivas de MAM de Intune solo administrarán la primera cuenta en las que se implementen.


Consulte el siguiente escenario de ejemplo para ahondar aún más en cómo se tratan varias cuentas de usuario.

El usuario A trabaja para dos empresas: la **empresa X** y la **empresa Y**. El usuario A tiene una cuenta profesional en cada empresa y en ambas se usa Intune para implementar directivas de MAM. La **empresa X** implementa directivas de MAM **antes** que la **empresa Y**. La cuenta asociada a la **empresa X** obtendrá la directiva de MAM, pero no la cuenta asociada a la empresa Y. Si quiere que la cuenta de usuario asociada a la empresa Y se administre por medio de las directivas de MAM, deberá quitar la cuenta de usuario asociada a la empresa X.
### Agregar una segunda cuenta
####  Android
Si usa un dispositivo Android, puede que aparezca un mensaje de bloqueo con instrucciones para quitar la cuenta existente y agregar una nueva.  Para quitar la cuenta existente, vaya a **Configuración &gt; General &gt; Administrador de aplicaciones &gt; Portal de empresa y seleccione “Borrar datos”**.

![Captura de pantalla del mensajes de error e instrucciones para quitar la cuenta](../media/AppManagement/Android_SwitchUser.png)

##  Ver archivos multimedia con la aplicación Azure Information Protection (anteriormente conocida como aplicación Rights Management sharing)
Para ver archivos de imagen, AV y PDF de la empresa en dispositivos Android, use la [aplicación Azure Information Protection](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer).

Descargue esta aplicación de Google Play Store.  

Se admiten los siguientes tipos de archivos:

* **Audio:** AAC LC, HE-AACv1 (AAC+), HE-AACv2 (AAC+ mejorado), AAC ELD (AAC retraso bajo mejorado), AMR-NB, AMR-WB, FLAC, MP3, MIDI, Ogg Vorbis, PCM/WAVE.
* **Vídeo:** H.263, H.264 AVC, MPEG-4 SP, VP8.
* **Imagen:** jpg, pjpg, png, ppng, bmp, pbmp, gif, pgif, jpeg, pjpeg.
* **Documentos:** PDF, PPDF

------------
|**Pfile**|**text**|
|----|----|
|Pfile es un formato "contenedor" genérico para archivos protegidos que encapsula el contenido cifrado y las licencias de Azure Information Protection y puede usarse para proteger cualquier tipo de archivo.|Los archivos de texto, incluidos XML, CSV, etc. pueden abrirse para verse en la aplicación incluso cuando están protegidos. Tipos de archivo: txt, ptxt, csv, pcsv, log, plog, xml, pxml.|
---------------
## Pasos siguientes
[Qué esperar cuando la aplicación iOS está administrada por directivas MAM](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)

### Consulte también
[Crear e implementar directivas de administración de aplicaciones móviles con Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Oct16_HO3-->


