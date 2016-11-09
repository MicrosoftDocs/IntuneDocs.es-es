---
title: "Guía de evaluación de Intune | Microsoft Intune"
description: "Introducción y requisitos previos sobre cómo configurar una evaluación gratuita de 30 días de Intune"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 08/09/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 619a1d11-3d22-4635-8f70-770eba3e1712
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a4f7a503417938eabb4334757dcf12a63f082fd3
ms.openlocfilehash: 559917b5b3c12534a5aa5d5eb5247d36e4ac1728


---

# <a name="intune-evaluation-guide"></a>Guía de evaluación de Intune
Configurar una evaluación gratuita de 30 días de Intune para administrar los equipos y dispositivos móviles es rápido y sencillo. Con solo unos pocos pasos sencillos en la evaluación, puede agregar hasta 100 usuarios y dispositivos, configurar grupos y directivas de cumplimiento e inscribir y administrar equipos y dispositivos móviles.

En este tema, obtendrá información sobre los conceptos básicos para poner la evaluación de Intune en funcionamiento, así como información general del servicio para que pueda evaluar las características y funciones de Intune.

Vea el siguiente vídeo de demostración de cinco minutos para descubrir lo fácil que es empezar a trabajar con una evaluación gratuita de Microsoft Intune y administrar los dispositivos. La primera parte del vídeo menciona un portal que se ha "retirado" por lo que, aunque usará un portal diferente, los pasos serán esencialmente los mismos. Puede leer más sobre el portal [aquí](https://docs.microsoft.com/intune/deploy-use/account-portal-merged-with-Office-365).

<iframe width="675" height="480" src="https://www.youtube.com/embed/ltcZvm4VOFU" frameborder="0" allowfullscreen></iframe>

## <a name="before-you-begin"></a>Antes de comenzar
Antes de empezar a trabajar con Intune, necesitará lo siguiente:

-   Un dispositivo con un explorador web habilitado para Silverlight que pueda usar para tener acceso a los sitios web en los que creará cuentas de usuario de Intune (el **Centro de administración de Office 365**) y en los que administrará dispositivos, grupos y directivas (la **consola de administración de Intune**).

-   Un segundo dispositivo con un explorador web que usará para probar cómo los usuarios de Intune inscriben y administran sus dispositivos mediante el Portal de empresa. También probará cómo los usuarios encuentran e instalan aplicaciones y piden ayuda a los administradores. Si no tiene un segundo dispositivo, puede usar la opción de "modo de privacidad" en el mismo explorador que usa para la administración de Intune (por ejemplo, en Internet Explorer, puede elegir **Herramientas**&gt;**Exploración de InPrivate**).

-   Si tiene una cuenta de Microsoft Online Services, necesitará las credenciales de administrador para esa cuenta. Si no tiene este tipo de cuenta, o si desea usar este inquilino de Intune solo con fines de evaluación, no necesita estas credenciales de administrador.

-   Si va a administrar dispositivos iOS o Windows Phone 8.1 con la evaluación de Intune, necesitará certificados (o claves) y las cuentas para recuperar dichos certificados (vea la tabla siguiente). Los dispositivos Android no necesitan certificados adicionales.

    |Plataforma|Requisitos de certificado|Más información|
    |------------|----------------------------|--------------------|
    |Windows Phone 8,1 |No es necesario ningún certificado para los usuarios de Windows Phone 8.1 que instalen la aplicación de Portal de empresa desde la Tienda. |Esta guía presupone que los usuarios obtendrán la aplicación de Portal de empresa de la Tienda desde un dispositivo Windows Phone 8.1 o posterior. |
    |Dispositivos Windows 10, Windows RT 8.1 o Windows 8.1|No hay requisitos de certificado para inscribir dispositivos Windows RT y Windows.|[Instalar el cliente de equipos Windows con Microsoft Intune](/Intune/Deploy-Use/install-the-windows-pc-client-with-microsoft-intune).|
    |iOS 7.1 o posterior|Obtenga un certificado del servicio de notificaciones push de Apple.|Solicite un certificado de servicio de notificaciones push de Apple, tal como se describe aquí: [Configurar la administración de dispositivos iOS y Mac con Microsoft Intune](/Intune/Deploy-Use/set-up-ios-and-mac-management-with-microsoft-intune).|

## <a name="steps-to-complete-a-30day-evaluation-of-intune"></a>Pasos para completar una evaluación de 30 días de Intune
- [Paso 1: Iniciar sesión o registrarse para obtener una evaluación de 30 días](get-started-with-a-30-day-trial-of-microsoft-intune-step-1.md). Antes de registrar o iniciar sesión en Intune, debería considerar si iniciar sesión con una cuenta existente o crear una cuenta temporal para usarla solo durante la evaluación de 30 días de Microsoft Intune.
- [Paso 2: Agregar usuarios](get-started-with-a-30-day-trial-of-microsoft-intune-step-2.md). Ahora que ha configurado su cuenta, podrá agregar cuentas de usuario individuales en Intune o agregar usuarios en masa (vea las instrucciones en esta sección). Antes de empezar, es importante que comprenda cómo Intune administra las cuentas de administrador.
- [Paso 3: Crear grupos para organizar los usuarios y los dispositivos](get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md). Los grupos de Intune ofrecen una gran flexibilidad para administrar dispositivos y usuarios. Puede configurar los grupos para que se adapten a las necesidades de su organización (por ejemplo, por ubicación geográfica, departamento o características de hardware) y usarlos para realizar diversas tareas administrativas a escala, desde la configuración de directivas para un conjunto de usuarios hasta la implementación de aplicaciones en un conjunto de dispositivos.
- [Paso 4: Crear directivas y publicar una aplicación](get-started-with-a-30-day-trial-of-microsoft-intune-step-4.md). Las directivas de Intune proporcionan una configuración con la que es más fácil: controlar la configuración de seguridad en dispositivos móviles, mantener la configuración de Firewall de Windows y Endpoint Protection de los equipos e implementar aplicaciones.
- [Paso 5: Inscribir los dispositivos móviles e instalar una aplicación](get-started-with-a-30-day-trial-of-microsoft-intune-step-5.md). Para configurar la administración de dispositivos móviles con Intune, debe establecer la entidad de administración de dispositivos móviles, habilitar la administración de plataformas de dispositivos específicos e inscribir sus dispositivos con la aplicación de Portal de empresa. Posteriormente, puede implementar la aplicación Microsoft Skype que publicó.
- [Paso 6: Otras opciones y extras](get-started-with-a-30-day-trial-of-microsoft-intune-step-6.md). Elija cómo usar las alertas, los informes y otras funciones de Intune para cumplir sus necesidades empresariales.
- [Paso 7: Pasos siguientes](get-started-with-a-30-day-trial-of-microsoft-intune-step-7.md). Prepárese para trasladarse a una suscripción de pago de Intune y aprovechar el “Beneficio del centro FastTrack” para Intune.


### <a name="next-steps"></a>Pasos siguientes
Es el momento de empezar a trabajar con su suscripción de evaluación de 30 días.

>[!div class="step-by-step"]
[**Registrarse en Intune** &rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-1.md)

### <a name="see-also"></a>Consulte también
[Guía de inicio rápido de Intune](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune)



<!--HONumber=Nov16_HO1-->


