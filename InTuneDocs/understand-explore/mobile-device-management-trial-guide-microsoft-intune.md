---
title: "Evalúe la administración de dispositivos móviles en Microsoft Intune | Microsoft Docs"
description: "Evaluar MDM en la versión de prueba gratuita de Intune."
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 11/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47806f69-303d-41d9-9b0e-9b9445ea24ac
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 4133c64d283682f0be37cd6ac69164ef872a5026


---

# <a name="evaluate-mobile-device-management-in-microsoft-intune"></a>Evalúe la administración de dispositivos móviles en Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Esta guía de evaluación mostrará móvil cómo funciona la administración de dispositivos móviles en Intune. Podrá:
- Inscribir un dispositivo para que lo administre Intune.
- Crear grupos para organizar usuarios y dispositivos.
- Crear e implementar algunas directivas de administración de dispositivos en los grupos.
- Publicar una aplicación para que los usuarios con dispositivos inscritos puedan instalarla en su dispositivo.
<!--- - Monitor the device? View a report of compliant devices?--->
<!--- - Remove the device from management--->

## <a name="assumptions"></a>Suposiciones
Esta guía presupone que está utilizando la versión de prueba solo con fines de evaluación y va a comenzar con un entorno limpio al suscribirse.

Para facilitar la introducción a la versión de prueba, estamos configurando un entorno muy simple que usa solo Intune y presupone que será la entidad de administración de dispositivos móviles. Sin embargo, a lo largo de la guía se indicará contenido técnico más profundo si desea explorar más adelante.

Puede hacer todo en el contenido de la versión de prueba que pueda hacer en una versión de suscripción; la única diferencia es que está limitado a 100 cuentas de usuario en la versión de prueba.

## <a name="whats-not-covered"></a>Qué no está cubierto
|Si está interesado en |Lea este |
|------------------------|----------|
|MDM en un entorno que no es de prueba | [Introducción](https://docs.microsoft.com/en-us/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune) |
|MDM con Intune y System Center Configuration Manager | [Administración de dispositivos móviles híbrida](https://docs.microsoft.com/en-us/sccm/mdm/understand/hybrid-mobile-device-management) |

Dado que las anteriores guías le ayudan a configurar Intune en entornos de producción, son más largas y tienen muchos más puntos de decisión en los que debe trabajar en comparación con la guía de evaluación.

Para familiarizarse rápidamente con Intune, le sugerimos que comience por la guía de evaluación y, a continuación, se dirija a las demás guías.

## <a name="prerequisites-for-this-evaluation"></a>Requisitos previos para esta evaluación
- Internet Explorer 10 o posterior
- Un dispositivo que usará para probar cómo los usuarios de Intune inscriben y administran sus dispositivos mediante el Portal de empresa. Vamos a usar un iPad y un teléfono Android para esta guía.
- Para administrar el iPad o cualquier otro dispositivo iOS, necesitará un [certificado de Apple Push Notification Service](https://docs.microsoft.com/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).
- Una [suscripción de prueba de Intune](sign-up-for-30-day-trial-microsoft-intune.md)

## <a name="set-your-mdm-authority"></a>Configurar entidad de MDM
El primer paso que debe seguir para administrar dispositivos móviles con Intune es establecer su **autoridad de administración de dispositivos móviles (MDM)**.

Si usa Intune de forma independiente, como presupone esta versión de prueba, o si usa Intune como parte de una suscripción de Enterprise Mobility + Security (EMS), debe establecer Intune como entidad de administración de dispositivos móviles. Es decir, designe Intune para que sea el servicio que se utiliza para administrar dispositivos móviles en su organización.

Los clientes que desean usar Intune con System Center Configuration Manager para administrar dispositivos móviles deben decidir si usar Intune o Configuration Manager como su entidad de administración de dispositivos móviles. Esto es una decisión importante que tomar en un entorno de producción porque actualmente es muy difícil de cambiar la configuración una vez que la elige, pero eso está fuera del ámbito de esta guía de evaluación. Para obtener más información acerca de las implicaciones de establecer Intune o Configuration Manager como entidad MDM, consulte [Elegir entre la administración de dispositivos móviles híbrida y de Intune independiente](https://docs.microsoft.com/en-us/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management).

Estableceremos Intune como entidad de MDM para la versión de prueba; esto no afectará a su entorno de producción a menos que decida utilizar la versión de prueba para el entorno de producción.

1. En la [consola de administración de Intune](https://manage.microsoft.com/), elija **Administración** &gt; **Administración de dispositivos móviles**.
2. En la lista **Tareas**, elija **Configurar entidad de MDM**. Se abre el cuadro de diálogo **Establecer entidad de administración de dispositivos móviles** . <!---screen shot--->
3. Intune solicita confirmación de que desea que Intune sea su entidad de MDM. Seleccione la casilla y elija **Sí** si quiere usar Intune para administrar dispositivos móviles.

## <a name="enroll-your-test-devices-into-intune"></a>Inscribir dispositivos de prueba en Intune

En esta guía, inscribiremos un teléfono Android y un iPad de Apple, pero se proporcionarán vínculos para [obtener más información acerca de la inscripción de dispositivos en Intune](#Learn-more-about-device-enrollment) al final de esta sección.
### <a name="android"></a>Android
Instale la aplicación **Portal de empresa de Intune** de Microsoft Corporation, disponible en [Google Play](http://go.microsoft.com/fwlink/p/?LinkId=386612), e inicie sesión con las [credenciales de usuario creadas](sign-up-for-30-day-trial-microsoft-intune.md#add-users) cuando se registró en la versión de prueba gratuita.

### <a name="ios"></a>iOS
Antes de que los usuarios puedan inscribir sus dispositivos iOS, debe configurar Intune para administrar estos dispositivos.

1. **Obtener una solicitud de firma de certificado**<br/>
Inicie sesión en Intune con su cuenta de administración y vaya a **Administración** > **Administración de dispositivos móviles** > **iOS y Mac OS X** > **Cargar un certificado APN** y, a continuación, elija **Descargar la solicitud de certificados de APNs**. Guarde la solicitud de firma de certificado (.csr) en el equipo local. Se utiliza el archivo .csr para solicitar un certificado de relación de confianza desde el portal de certificados push de Apple. <!--- screen shot--->
2.    **Obtener un certificado de servicio de notificaciones de inserción de Apple**<BR/>
Vaya al [Portal de certificados push de Apple](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&rv=2) e inicie sesión con el Id. de Apple de empresa para crear el certificado de APNs mediante el archivo .csr. Después de elegir **Cargar** en el portal de certificados push de Apple, recibirá un archivo .json que no se puede usar para APNs. Complete la descarga, vuelva al portal de certificados push de Apple para Certificados para servidores de terceros y elija **Descargar**.

 Descargue el certificado de APNs (.pem) y guarde el archivo localmente. Este Id. de Apple debe usarse en el futuro para renovar el certificado de APNs.
3.    **Agregar el certificado de APN a Intune**<BR/>
En la consola de administración de Microsoft Intune, vaya a **Administración** > ** Administración de dispositivos móviles** > **iOS y Mac OS X** > **Cargar un certificado de APNs** y luego elija **Cargar el certificado de APNs**. Vaya al archivo de certificado (.pem), elija **Abrir** y luego escriba su Id. de Apple. Con el certificado de APNs. Intune puede inscribir y administrar dispositivos iOS insertando la directiva en los dispositivos móviles inscritos.
4.    **Indique a los usuarios cómo inscribir sus dispositivos para acceder a recursos de la empresa.**<br/>
Para instrucciones sobre la inscripción del usuario final, consulte [Inscribir un dispositivo iOS en Intune](https://docs.microsoft.com/en-us/Intune/enduser/enroll-your-device-in-intune-ios) o [Inscribir un dispositivo Mac OS X en Intune](https://docs.microsoft.com/en-us/Intune/enduser/enroll-your-device-in-intune-mac-os-x). El proceso de inscripción indica a los usuarios lo que pueden esperar y qué pueden o no ver los administradores de TI en sus dispositivos.


### <a name="learn-more-about-device-enrollment"></a>Obtenga información acerca de la inscripción de dispositivos

Intune admite las siguientes plataformas de dispositivo:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

Los requisitos para habilitar la administración de dispositivos dependen de las plataformas que desea administrar.
- Los dispositivos móviles **Android** permiten a los usuarios [inscribirse mediante la aplicación Portal de empresa](/intune/deploy-use/set-up-android-management-with-microsoft-intune) disponible en Google Play. No se requiere ninguna configuración adicional en Intune.
- [Requisitos de configuración para **iOS y Mac OS X**](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)
- [Requisitos de configuración para **Windows Phone**](/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune).

<!--- ## Verify enrollment--->
<!--- START HERE

### iOS and Mac OS X
Install the **Microsoft Intune Company Portal** app from Microsoft Corporation available in the App Store and sign in with Intune user credentials added above. View **Enrolled devices** to add your device.



### Windows Phone 8.1
Users install the **Company Portal** app from Microsoft Corporation, available in the Windows Phone store, and sign in with the Intune user credentials added above.  View **Enrolled devices** to add your device.

## Install the previously deployed app
Open the Company Portal on the mobile device, choose **Apps**, and then install **Microsoft Skype**.--->



## <a name="next-steps"></a>Pasos siguientes
[Creación de grupos para organizar usuarios y dispositivos](get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md)



<!--HONumber=Jan17_HO1-->


