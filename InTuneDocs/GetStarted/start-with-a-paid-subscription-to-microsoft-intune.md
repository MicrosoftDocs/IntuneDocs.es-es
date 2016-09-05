---
title: "Guía de inicio rápido de Intune | Microsoft Intune"
description: "Condiciones y requisitos previos para comenzar a usar su suscripción de Intune"
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d158503c-1276-422b-ab81-5f66c1cd7e7a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6d1c7c670341692d4ea0c823e4a9a96746b83067
ms.openlocfilehash: 735889feb1c3234c0c063048601715a3f8aa4719


---


# Guía de inicio rápido de Intune
Esta guía de inicio rápido le guiará por los pasos necesarios para configurar una suscripción de pago de Microsoft Intune a fin de administrar de manera rápida y sencilla los dispositivos móviles y los equipos con Windows que se usan en la organización. Puede seguir cada paso en orden u omitir los pasos que no se apliquen a su entorno específico o a sus necesidades empresariales.

>[!NOTE]
>Este artículo se centra en la configuración de Intune como servicio independiente. Si actualmente usa Microsoft System Center Configuration Manager para administrar equipos y servidores, también puede [ampliar Configuration Manager para administrar dispositivos móviles](https://technet.microsoft.com/library/jj884158.aspx). Para ello, debe conectar Intune con Configuration Manager en una implementación híbrida de administración de dispositivos móviles (MDM).

En esta guía de inicio rápido se comparten muchos de los pasos incluidos en la [Guía de evaluación de Intune](/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune). Sin embargo, deberá tener en cuenta varios requisitos adicionales cuando haya terminado la evaluación y esté listo para empezar a administrar los dispositivos móviles:

-   Sincronice las cuentas locales de Active Directory con Intune y Azure Active Directory.

-   Actualice el dominio público y los registros del servicio DNS con el registrador de dominios.

-   Personalice las características de Intune para su uso en producción.

>[!TIP]
>Puede usar el *beneficio del Centro FastTrack* si adquiere al menos 150 licencias de Microsoft Intune en un plan que pueda optar a ello. Se trata de un servicio donde los especialistas en Microsoft trabajan con usted para preparar su entorno para Intune. Consulte [Descripción del servicio Microsoft Intune](https://technet.microsoft.com/library/mt228265.aspx).


## Antes de comenzar
Use esta guía cuando empiece con una suscripción de pago y esté listo para implementar Intune y realizar cambios en su infraestructura de red. Estas tareas pueden abarcar desde simplemente agregar o actualizar los registros DNS internos y externos hasta sincronizar sus cuentas de usuario de Active Directory en Azure Active Directory. Cualquiera que sea la combinación de características de administración de dispositivos móviles de Intune que decida, deberá planear cuidadosamente la interacción de Intune con sus servicios y componentes de red. En concreto, debe revisar:

-   **Cómo administrará la identidad de usuario**: para la mayoría de organizaciones de tamaño medio y grande, la forma más conveniente de administrar la identidad de usuario con Intune es conectar los servicios de directorio existentes a Intune a través de Azure Active Directory. Esto es especialmente cierto si ya usa otros servicios de nube de Microsoft, como Office 365 o Exchange Online. La sincronización de las cuentas de usuario con [Microsoft Azure Active Directory Connect](https://www.microsoft.com/download/details.aspx?id=47594) es una manera rápida y sencilla de conectar la instancia de Active Directory local a Azure Active Directory y configurar una experiencia de autenticación de inicio de sesión único para los usuarios.

-   **Cómo se verá afectado DNS**: si quiere usar su propio nombre de dominio en lugar del dominio onmicrosoft.com predeterminado que obtiene al registrarse por primera vez en Intune, necesitará algunas actualizaciones de registros DNS públicos. Las actualizaciones de registros DNS son necesarias para que los dispositivos móviles puedan localizar el servicio Intune y garantizar que el servicio de administración de la suscripción funciona correctamente para administrar todos los dispositivos que se usan en organización.

## Asegúrese de que dispone de los siguientes elementos
¿Listo para comenzar? Para empezar a usar la suscripción de pago de Intune necesita los siguientes elementos:

### Un dispositivo con un explorador web habilitado para Silverlight
Le servirá para tener acceso a la consola de administración de Intune, donde podrá administrar dispositivos, aplicaciones y directivas. También necesita un explorador web para tener acceso al Portal de empresa de Intune basado en web cuando no pueda tener acceso a la aplicación Portal de empresa desde un dispositivo móvil. Para facilitar las cosas, puede usar la opción de "modo de privacidad" en el mismo explorador que usa para la administración de Intune. Por ejemplo, en Internet Explorer, puede hacer clic en **Herramientas** &gt; **Exploración de InPrivate**.

>[!TIP]
>Debido a este requisito, no se admite el explorador de Microsoft Edge para tener acceso a la consola de administración de Intune.


### Certificados para dispositivos móviles
Si va a administrar dispositivos iOS o Windows Phone con Intune, necesitará certificados y cuentas para recuperar dichos certificados. No necesitará certificados adicionales para administrar dispositivos Android.

- No es necesario ningún certificado para los usuarios de **Windows Phone 8.1** que instalen la aplicación Portal de empresa desde la Tienda. No obstante, se requiere un [certificado de firma de código de Symantec](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do) para **Windows Phone 8.0** o para usar Intune a fin de implementar la aplicación Portal de empresa en dispositivos Windows Phone 8.1.

>[!NOTE]
>En esta guía de inicio rápido se da por supuesto que los usuarios obtendrán la aplicación Portal de empresa de la Tienda desde un dispositivo Windows Phone 8.1 o posterior. Para más información sobre el soporte técnico de Windows Phone 8.0, consulte [Configurar la administración de dispositivos para Windows Phone 8.0](/Intune/deploy-use/set-up-windows-phone-8.0-management-with-microsoft-intune).

- No hay ningún requisito de certificado para **PC con Windows** o **dispositivos con Windows RT** cuando se realiza la inscripción de los PC con Windows como dispositivos o cuando se [instala el cliente de PC con Windows para Microsoft Intune](/intune/deploy-use/install-the-windows-pc-client-with-microsoft-intune).

- En el caso de dispositivos **iOS** o **Mac OS X**, deberá pedir un certificado del Servicio de notificaciones push de Apple, tal como se describe en el paso 3 de [Configurar la administración de dispositivos iOS y Mac](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).

## Pasos siguientes
Es el momento de empezar a usar la Guía de inicio rápido de Intune.

>[!div class="step-by-step"]
[**Iniciar sesión en Intune** &rarr;](start-with-a-paid-subscription-to-microsoft-intune-step-1.md)



<!--HONumber=Aug16_HO4-->


