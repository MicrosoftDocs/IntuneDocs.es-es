---
# required metadata

title: Guía de evaluación de Intune | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 619a1d11-3d22-4635-8f70-770eba3e1712

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Guía de evaluación de Intune
Configurar una evaluación gratuita de 30 días de Intune para administrar los equipos y dispositivos móviles es rápido y sencillo. Con solo unos pocos pasos sencillos en la evaluación, puede agregar hasta 100 usuarios y dispositivos, configurar grupos y directivas de cumplimiento e inscribir y administrar equipos y dispositivos móviles.

En este tema, obtendrá información sobre los conceptos básicos para poner la evaluación de Intune en funcionamiento, así como información general del servicio para que pueda evaluar las características y funciones de Intune.

Vea este vídeo de demo de cinco minutos para descubrir lo fácil que es empezar a trabajar con una evaluación gratuita de Microsoft Intune y administrar los dispositivos:

<iframe width="675" height="480" src="https://www.youtube.com/embed/ltcZvm4VOFU" frameborder="0" allowfullscreen></iframe>

## Antes de comenzar
Antes de empezar a trabajar con Intune, necesitará lo siguiente:

-   Un dispositivo con un explorador web habilitado para Silverlight que pueda usar para tener acceso a los sitios web en los que creará cuentas de usuario de Intune (el **Centro de administración de Office 365**) y en los que administrará dispositivos, grupos y directivas (la **consola de administración de Intune**).).

-   Un segundo dispositivo con un explorador web que usará para probar cómo los usuarios de Intune inscriben y administran sus dispositivos mediante el Portal de empresa. También probará cómo los usuarios encuentran e instalan aplicaciones y piden ayuda a los administradores. Si no tiene un segundo dispositivo, puede usar la opción de “modo de privacidad” en el mismo explorador que usa para la administración de Intune (por ejemplo, en Internet Explorer, puede elegir **Herramientas** &gt; **Exploración de InPrivate**).).

-   Si tiene una cuenta de Microsoft Online Services, necesitará las credenciales de administrador para esa cuenta. Si no tiene este tipo de cuenta, o si desea usar este inquilino de Intune solo con fines de evaluación, no necesita estas credenciales de administrador.

-   Si va a administrar dispositivos iOS o Windows Phone con la evaluación de Intune, necesitará certificados (o claves) y las cuentas para recuperar dichos certificados (vea la tabla siguiente). Los dispositivos Android no necesitan certificados adicionales.

    |Plataforma|Requisitos de certificado|Más información|
    |------------|----------------------------|--------------------|
    |Windows Phone 8.1 y Windows Phone 8 |No es necesario ningún certificado para los usuarios de Windows Phone 8.1 que instalen la aplicación de Portal de empresa desde la Tienda. Se requiere un certificado Symantec en Windows Phone 8.0 o usar Intune para implementar la aplicación de Portal de empresa en dispositivos Windows Phone 8.1.|Esta guía presupone que los usuarios obtendrán la aplicación de Portal de empresa de la Tienda desde un dispositivo Windows Phone 8.1 o posterior. Para más información sobre el soporte técnico de Windows Phone 8.0, vea [Set up Windows Phone management with Microsoft Intune (Configurar la administración de Windows Phone con Microsoft Intune)](/Intune/DeployUse/set-up-windows-phone-management-with-microsoft-intune)..|
    |Dispositivos Windows 10, Windows RT 8.1, Windows RT o Windows 8.1|No hay requisitos de certificado para inscribir dispositivos Windows RT y Windows.|[Instalar al cliente de equipos Windows con Microsoft Intune](/Intune/DeployUse/install-the-windows-pc-client-with-microsoft-intune).|
    |iOS 7.1 o posterior|Obtenga un certificado del servicio de notificaciones push de Apple.|Solicite un certificado de servicio de notificaciones push de Apple, tal como se describe aquí: [Set up iOS and Mac management with Microsoft Intune (Configurar la administración de iOS y Mac con Microsoft Intune)](/Intune/DeployUse/set-up-ios-and-mac-management-with-microsoft-intune)..|

## Pasos para completar una evaluación de 30 días de Intune
- [Paso 1: Iniciar sesión o registrarse para obtener una evaluación de 30 días](get-started-with-a-30-day-trial-of-microsoft-intune-step-1.md). Antes de registrar o iniciar sesión en Intune, debería considerar si iniciar sesión con una cuenta existente o crear una cuenta temporal para usarla solo durante la evaluación de 30 días de Microsoft Intune.
- [Paso 2: Agregar usuarios](get-started-with-a-30-day-trial-of-microsoft-intune-step-2.md). Ahora que ha configurado su cuenta, podrá agregar cuentas de usuario individuales en Intune o agregar usuarios en masa (vea las instrucciones en esta sección). Antes de empezar, es importante que comprenda cómo Intune administra las cuentas de administrador.
- [Paso 3: Crear grupos para organizar los usuarios y los dispositivos](get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md). Los grupos de Intune ofrecen una gran flexibilidad para administrar dispositivos y usuarios. Puede configurar los grupos para que se adapten a las necesidades de su organización (por ejemplo, por ubicación geográfica, departamento o características de hardware) y usarlos para realizar diversas tareas administrativas a escala, desde la configuración de directivas para un conjunto de usuarios hasta la implementación de aplicaciones en un conjunto de dispositivos.
- [Paso 4: Crear directivas y publicar una aplicación](get-started-with-a-30-day-trial-of-microsoft-intune-step-4.md). Las directivas de Intune proporcionan una configuración con la que es más fácil: controlar la configuración de seguridad en dispositivos móviles, mantener la configuración de Firewall de Windows y Endpoint Protection de los equipos e implementar aplicaciones.
- [Paso 5: Inscribir los dispositivos móviles e instalar una aplicación](get-started-with-a-30-day-trial-of-microsoft-intune-step-5.md). Para configurar la administración de dispositivos móviles con Intune, debe establecer la entidad de administración de dispositivos móviles, habilitar la administración de plataformas de dispositivos específicos e inscribir sus dispositivos con la aplicación de Portal de empresa. Posteriormente, puede implementar la aplicación Microsoft Skype que publicó.
- [Paso 6: Otras opciones y extras](get-started-with-a-30-day-trial-of-microsoft-intune-step-6.md). Elija cómo usar las alertas, los informes y otras funciones de Intune para cumplir sus necesidades empresariales.
- [Paso 7: Pasos siguientes](get-started-with-a-30-day-trial-of-microsoft-intune-step-7.md). Prepárese para trasladarse a una suscripción de pago de Intune y aprovechar el “Beneficio del centro FastTrack” para Intune.


### Pasos siguientes
Es el momento de empezar a trabajar con su suscripción de evaluación de 30 días.

>[!div class="step-by-step"]
[**Registrarse en Intune** &rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-1.md)

### Consulte también
[Guía de inicio rápido de Intune](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune)


<!--HONumber=May16_HO1-->


