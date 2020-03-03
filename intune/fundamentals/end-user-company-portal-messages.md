---
title: Mensajes de Portal de empresa que los usuarios pueden ver en los dispositivos
titleSuffix: Microsoft Intune
description: Comprenda los distintos mensajes que los usuarios finales pueden ver en Portal de empresa.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/09/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3df993aa-48c5-4799-b68d-c85fe4f7b02c
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: cbc4e1cc8cf7bd578690bf3e34353a60ec67cdab
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514734"
---
# <a name="help-end-users-understand-company-portal-app-messages"></a>Ayudar a que los usuarios finales comprendan los mensajes de la aplicación Portal de empresa

> [!NOTE]
> La siguiente información se aplica solo a dispositivos con Android 6.0 y versiones posteriores y iOS 10 y versiones posteriores.

Comprenda los distintos mensajes de la aplicación que los usuarios finales pueden ver en Portal de empresa. Normalmente, estos mensajes de la aplicación se muestran en distintos puntos del proceso de inscripción. Descubra dónde aparecen, cuál es su significado y qué ocurre si los usuarios deniegan el acceso. Además, aprenderá a explicar mejor los mensajes a los usuarios.

- __¿Permitir que el Portal de empresa realice y administre llamadas telefónicas?__
- __¿Permitir que Portal de empresa tenga acceso a fotos, elementos multimedia y archivos del dispositivo?__

> [!NOTE]
> No vendemos ningún dato recogido por nuestro servicio a terceros por ningún motivo.

## <a name="allow-company-portal-to-make-and-manage-phone-calls"></a>¿Permitir que Portal de empresa realice y administre llamadas telefónicas?

### <a name="where-it-appears"></a>Dónde aparece

El mensaje **¿Permitir que Portal de empresa realice y administre llamadas telefónicas?** aparece cuando los usuarios pulsan **Inscribir** en la aplicación Portal de empresa mientras inscriben su dispositivo.

### <a name="what-it-means"></a>Significado

Al aceptar este aviso, los usuarios permiten que se envíen los números de teléfono y de IMEI del dispositivo al servicio Intune. Aparecerán en la consola de administración en la página __Hardware__.

> [!NOTE]
> **La aplicación Portal de empresa nunca hace ni administra llamadas telefónicas.** Google controla el texto del mensaje y no se puede cambiar.

Para ver la página **Hardware**, debe ir a **Grupos** > **All mobile devices (Todos los dispositivos móviles)** > **Dispositivos**. Seleccione el dispositivo del usuario y vaya a **Ver propiedades** > **Hardware**.

### <a name="what-happens-if-users-deny-access"></a>Qué sucede si los usuarios deniegan el acceso

Si los usuarios deniegan el acceso, pueden seguir usando la aplicación de Portal de empresa e inscribir su dispositivo. Sin embargo, el número de teléfono y el IMEI del dispositivo estarán en blanco en la página de __hardware__ de la consola de administración. La segunda vez que los usuarios inician sesión en la aplicación Portal de empresa después de denegar el acceso, el mensaje muestra una casilla de verificación **Never ask again** (No volver a preguntar) que los usuarios pueden marcar para detener el aviso.

Si los usuarios permiten el acceso, pero luego lo deniegan, el mensaje aparecerá la próxima vez que los usuarios inicien sesión en la aplicación Portal de empresa después de la inscripción.

Si los usuarios más adelante deciden permitir el acceso, pueden ir a **Configuración** > **Aplicaciones** > **Portal de empresa** > **Permisos** > **Teléfono** y activarlo.

### <a name="how-to-explain-this-to-your-users"></a>Cómo explicar esto a los usuarios

Envíe a los usuarios a [Inscribir el dispositivo Android en Intune](/intune-user-help/enroll-device-android-company-portal) para más información.

## <a name="allow-company-portal-to-access-your-contacts"></a>Allow Company Portal to access your contacts? (¿Permitir que el portal de empresa tenga acceso a los contactos?)

### <a name="where-it-appears"></a>Dónde aparece

El mensaje **¿Permitir que el portal de empresa tenga acceso a los contactos?** aparece cuando los usuarios pulsan **Inscribir** en la aplicación Portal de empresa mientras inscriben el dispositivo.

### <a name="what-it-means"></a>Significado

Al aceptar este aviso, los usuarios permiten a Intune crear su cuenta de trabajo y administrar la identidad de Azure Active Directory registrada para el usuario en ese dispositivo.

> [!NOTE]
> **Microsoft nunca accede a los contactos.** Google controla el texto del mensaje y no se puede cambiar.

### <a name="what-happens-if-users-deny-access"></a>Qué sucede si los usuarios deniegan el acceso

Si los usuarios deniegan el acceso, el dispositivo no se inscribirá en Intune ni se podrá administrar. La segunda vez que los usuarios inician sesión en la aplicación Portal de empresa después de denegar el acceso, el mensaje muestra una casilla **No volver a preguntar** que los usuarios pueden seleccionar para detener el aviso.

Si los usuarios permiten el acceso, pero luego lo deniegan, el mensaje aparece la próxima vez que los usuarios inicien sesión en la aplicación Portal de empresa después de la inscripción.

Si los usuarios más adelante deciden permitir el acceso, pueden ir a **Configuración** > **Aplicaciones** > **Portal de empresa** > **Permisos** > **Teléfono** y activarlo.

### <a name="how-to-explain-this-to-your-users"></a>Cómo explicar esto a los usuarios

Envíe a los usuarios a [Inscribir el dispositivo Android en Intune](/intune-user-help/enroll-device-android-company-portal) para más información.  

## <a name="allow-company-portal-to-access-photos-media-and-files-on-your-device"></a>¿Permitir que Portal de empresa tenga acceso a fotos, elementos multimedia y archivos del dispositivo?

### <a name="where-it-appears"></a>Dónde aparece

El mensaje **¿Permitir que Portal de empresa tenga acceso a fotos, elementos multimedia y archivos del dispositivo?** aparece cuando los usuarios pulsan **Enviar datos** para enviar registros a su administrador de TI.

### <a name="what-it-means"></a>Significado

Al aceptar este aviso, los usuarios permiten que su dispositivo escriba registros de datos en la tarjeta SD de este. Esto también permite que esos registros se trasladen mediante un cable USB.   

> [!NOTE]
> **La aplicación Portal de empresa nunca tiene acceso a las fotos, elementos multimedia ni archivos de los usuarios.** Google controla el texto del mensaje y no se puede cambiar.

### <a name="what-happens-if-users-deny-access"></a>Qué sucede si los usuarios deniegan el acceso

Si los usuarios deniegan el acceso, podrán enviar registros de datos por correo electrónico, pero los registros no se copiarán en la tarjeta SD del dispositivo.

La segunda vez que los usuarios inician sesión en la aplicación Portal de empresa después de denegar el acceso, el mensaje muestra una casilla **No volver a preguntar** que los usuarios pueden seleccionar para que el mensaje no se vuelva a mostrar. Si los usuarios permiten el acceso, pero luego lo deniegan, el mensaje aparece la próxima vez que los usuarios intenten enviar registros. No obstante, si los usuarios más adelante deciden permitir el acceso, pueden ir a **Configuración** > **Aplicaciones** > **Portal de empresa** > **Permisos** > **Almacenamiento** y activar el permiso.


### <a name="how-to-explain-this-to-your-users"></a>Cómo explicar esto a los usuarios

Envíe a sus usuarios a [Enviar registros al administrador de TI mediante correo electrónico](/intune-user-help/send-logs-to-your-it-admin-by-email-android). 

## <a name="your-company-support-needs-to-give-you-access-to-company-resources"></a>El servicio de soporte técnico de su empresa debe concederle acceso a sus recursos

### <a name="where-it-appears"></a>Dónde aparece

Si no ha agregado la aplicación Portal de empresa a las listas **Aplicaciones permitidas** o **Aplicaciones exentas** y un usuario intenta iniciar sesión, se producirá un error en el inicio de sesión. Se mostrará este mensaje:

> **El servicio de soporte técnico de su empresa debe concederle acceso a sus recursos**  
> Su empresa está usando directivas de Windows Information Protection para proteger su dispositivo. El servicio de soporte técnico de su empresa tendrá que asegurarse de que permite que Portal de empresa pueda acceder a esos recursos.

### <a name="what-it-means"></a>Significado

Agregue Portal de empresa a las listas **Aplicaciones permitidas** o **Aplicaciones exentas** en la directiva de protección de aplicaciones de Windows Information Protection (WIP). Para obtener más información, consulte [Creación e implementación de una directiva de protección de aplicaciones de Windows Information Protection (WIP) con Intune](../apps/windows-information-protection-policy-create.md).

## <a name="approve-a-iosipados-company-app-line-of-business-app-on-your-iosipados-device"></a>Aprobación de una aplicación de empresa iOS/iPadOS (aplicación de línea de negocio) en un dispositivo iOS/iPadOS 

### <a name="where-it-appears"></a>Dónde aparece

De manera predeterminada, su dispositivo no confía en las aplicaciones iOS que desarrolla su organización que no están disponibles en App Store. Cuando instala ese tipo de aplicaciones con Portal de empresa de Intune e inicia la aplicación, se muestra este mensaje:

![Mensaje de la aplicación iOS: Desarrollador empresarial no confiable](./media/end-user-company-portal-messages/end-user-company-portal-messages-01.png)

### <a name="what-it-means"></a>Significado

Este mensaje significa que tendrá que modificar la configuración del dispositivo iOS/iPadOS para aprobar e instalar una aplicación desarrollada por la empresa en el dispositivo iOS/iPadOS.

Cuando instala ese tipo de aplicaciones con Portal de empresa de Intune e inicia la aplicación, siga estos pasos para aprobar la aplicación después de descargarla:

1. Después de iniciar una aplicación de empresa instalada (aplicación de línea de negocio), verá el mensaje "Desarrollador empresarial no confiable". <br>
   Presione **Cancelar**.
2. Vaya a **Configuración** > **General** > **Administración de dispositivos**.

   ![UI de dispositivo iOS: Administración de dispositivos](./media/end-user-company-portal-messages/end-user-company-portal-messages-02.png)

3. Seleccione **Perfil de administración** > **Aplicación de empresa**.
4. Seleccione el nombre del desarrollador.
5. Presione **Confiar en _nombre del desarrollador_**.
6. Para confirmar la aplicación, seleccione **Confiar** en el mensaje emergente de instalación de la aplicación.

   ![UI de dispositivo iOS: Mensaje de aplicación de confianza](./media/end-user-company-portal-messages/end-user-company-portal-messages-03.png)

    Debería ser capaz de iniciar y usar la aplicación de empresa.


## <a name="see-also"></a>Vea también
[Qué decirles a los usuarios finales sobre el uso de Intune](end-user-educate.md)
