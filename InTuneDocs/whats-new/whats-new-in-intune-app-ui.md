---
title: Actualizaciones de la interfaz de usuario para las aplicaciones de usuario final de Intune | Microsoft Docs
description: "Averigüe qué ha cambiado en la interfaz de usuario para las aplicaciones que funcionan en dispositivos de usuario final con Intune."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 04/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b782e382-8deb-48a7-a437-d7c5a17163f1
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 62dcb40ad5a7921c514a9d41da14b991e39f3bcd
ms.openlocfilehash: f4a48b889702147abe20fd513fdb0f774020a54a
ms.lasthandoff: 04/20/2017


---
# <a name="ui-updates-for-intune-end-user-apps"></a>Actualizaciones de la interfaz de usuario para las aplicaciones de usuario final de Intune
Obtenga más información sobre las actualizaciones que hemos realizado en la interfaz de usuario para las aplicaciones que verán los usuarios finales en esta versión de Microsoft Intune. Esto puede ayudarle con las comunicaciones de usuario y cualquier documentación de actualización personalizada que haya creado para admitir su implementación. También puede ayudarle a comprender cómo solucionar mejor los posibles problemas a los que se enfrenten en caso de que sea necesario llamar al departamento de soporte técnico mediante el Portal de empresa.

> [!Note]
> Tenga en cuenta que las imágenes siguientes corresponden a la versión preliminar y que el producto anunciado puede diferir de las versiones presentadas.

## <a name="april-2017"></a>Abril de 2017

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Se mejoró la experiencia de inicio de sesión en todas las aplicaciones del Portal de empresa para todas las plataformas <!--User Story 1132123-->

Estamos mejorando la experiencia de inicio de sesión de las aplicaciones del Portal de empresa de Intune para Android, iOS y Windows.  La nueva experiencia del usuario aparecerá automáticamente en todas las plataformas de la aplicación Portal de empresa cuando Azure AD haga este cambio. Además, los usuarios ahora pueden iniciar sesión en Portal de empresa desde otro dispositivo con un código generado de un solo uso. Esto resulta útil especialmente en casos en los que los usuarios necesitan iniciar sesión sin credenciales.  

A continuación puede ver la experiencia de inicio de sesión anterior, la nueva experiencia de inicio de sesión con credenciales y la nueva experiencia de inicio de sesión desde otro dispositivo.

__Experiencia de inicio de sesión anterior__

![La página de inicio de sesión de Portal de empresa, con el icono de una persona frente a una representación gráfica de un sitio web. Abajo aparece el botón "Iniciar sesión". Un vínculo en la parte inferior lleva a información de Privacidad y cookies de Microsoft.](./media/cp_ios_aad_signin_before_1704_001.png)

![Después de pulsar Iniciar sesión, el usuario escribe las credenciales en esta página, que pide el correo electrónico y la contraseña de un usuario, además de ofrecer formas de solucionar los errores de contraseña.](./media/cp_ios_aad_signin_before_1704_002.png)

![Después de proporcionar la contraseña, la aplicación Portal de empresa inicia sesión, lo que se indica con una barra de carga.](./media/cp_ios_aad_signin_before_1704_003.png)

__Nueva experiencia de inicio de sesión__

![La página de inicio de sesión de Portal de empresa, con el icono de una persona frente a una representación gráfica de un sitio web. Abajo aparece el botón "Iniciar sesión". Un vínculo en la parte inferior lleva a información de Privacidad y cookies de Microsoft.](./media/cp_ios_aad_signin_after_1704_001.png)

![Se solicita al usuario que proporcione solamente su dirección de correo electrónico en lugar de la dirección de correo electrónico y la contraseña en la misma pantalla.](./media/cp_ios_aad_signin_after_1704_002.png)

![El usuario deberá escribir la contraseña una vez que se acepte la dirección de correo electrónico.](./media/cp_ios_aad_signin_after_1704_003.png)

__Nueva experiencia de inicio de sesión cuando se inicia sesión desde otro dispositivo__

![La página de inicio de sesión de Portal de empresa, con el icono de una persona frente a una representación gráfica de un sitio web. Abajo aparece el botón "Iniciar sesión". Un vínculo en la parte inferior lleva a información de Privacidad y cookies de Microsoft.](./media/cp_ios_aad_signin_from_another_device_after_1704_001.png)

Pulse el vínculo __Iniciar sesión desde otro dispositivo__.

![Se solicita al usuario que proporcione solamente su dirección de correo electrónico en lugar de la dirección de correo electrónico y la contraseña en la misma pantalla. El vínculo bajo el campo de correo electrónico indica "Iniciar sesión desde otro dispositivo".](./media/cp_ios_aad_signin_from_another_device_after_1704_002.png)

![Se proporcionan instrucciones para ir a la página aka.ms/devicelogin con un código de acceso único desde el equipo de trabajo y, luego, use el código para iniciar sesión.](./media/cp_ios_aad_signin_from_another_device_after_1704_003.png)

Abra un explorador y vaya a [http://aka.ms/devicelogin](https://aka.ms/devicelogin).

![Una imagen del explorador del usuario en su equipo de trabajo en lugar de su aplicación Portal de empresa. La página "Inicio de sesión del dispositivo" que aparece solicita al usuario el código que recibió en la aplicación Portal de empresa.](./media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

Escriba el código que vio en la aplicación Portal de empresa. Cuando seleccione __Continuar__, podrá autenticarse con cualquier método que admita su empresa, como una tarjeta inteligente.

![El usuario ingresó su código único en el campo y el sitio "Inicio de sesión del dispositivo" solicitó la confirmación con respecto a que Portal de empresa de Intune era la aplicación correcta para recibir autorización para iniciar sesión.](./media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

![Una página de confirmación que establece que el usuario inició sesión en la aplicación Portal de empresa en el dispositivo y que se puede cerrar esta página.](./media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

La aplicación Portal de empresa comenzará a iniciar sesión.

![Después del proceso de autenticación, la aplicación Portal de empresa inicia sesión, lo que se indica con una barra de carga.](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Nuevos iconos para Managed Browser y el Portal de empresa <!--918433, 918431-->

Managed Browser está recibiendo iconos actualizados para las versiones de iOS y Android de la aplicación. El nuevo icono contendrá el distintivo de Intune actualizado para que sea más coherente con otras aplicaciones de Enterprise Mobility + Security (EM+S).

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_manbro_before_042017.png" alt="The previous version of the Managed Browser app icon." width=200 height=366 align=center>
          </td>
          <td>
             <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_manbro_after_042017.png" alt="The updated version of the Managed Browser app icon." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

El Portal de empresa también está recibiendo iconos actualizados para las versiones de Windows, iOS y Android de la aplicación con el objetivo de mejorar la coherencia con otras aplicaciones de EM+S. Estos iconos se lanzarán gradualmente en las plataformas desde abril hasta finales de mayo.

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Indicador de progreso de inicio de sesión en Portal de empresa de Android <!--953374-->

Una actualización de la aplicación Portal de empresa de Android muestra un indicador de progreso de inicio de sesión cuando el usuario inicia o reanuda la aplicación. El indicador avanza por nuevos estados en el siguiente orden: "Conectando...", "Iniciando sesión..." y "Checking for security requirements..." (Comprobando requisitos de seguridad) antes de permitir que el usuario acceda a la aplicación.

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_signing_in_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Connecting' underneath it." width=200 height=366 align=center>
          </td>
          <td>
             <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_checking_security_reqs_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Signing in' underneath it." width=200 height=366 align=center>
           </td>
           <td>
              <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_connecting_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Checking for security requirements' underneath it." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

## <a name="february-2017"></a>Febrero de 2017

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622-announced-1702--"></a>Nueva experiencia del usuario en la aplicación del portal de empresa para Android <!--621622, announced 1702-->
A partir de marzo, la aplicación del portal de empresa para Android seguirá las [directrices de Material Design](https://material.io/guidelines/material-design/introduction.html) para crear una apariencia más moderna. Esta experiencia del usuario mejorada incluye:

* __Colores__: los encabezados de pestaña pueden colorearse según la paleta de colores personalizada.

![A la izquierda, una imagen de la aplicación del portal de empresa para Android antes de la actualización. A la derecha, una imagen de la aplicación del portal de empresa para Android después de la actualización. Ambas imágenes muestran la pestaña Dispositivos como la pestaña seleccionada de las tres pestañas disponibles: Aplicaciones, Dispositivos y Contactar con TI.](./media/CP_Android_DevicesTab_BeforeAfter.png)

* __Interfaz__: los botones __Aplicaciones destacadas__ y __Todas las aplicaciones__ se han actualizado en la pestaña __Aplicaciones__. El botón __Buscar__ ahora es un botón de acción flotante.

![A la izquierda, una imagen de la aplicación del portal de empresa para Android antes de la actualización. A la derecha, una imagen de la aplicación del portal de empresa para Android después de la actualización. Ambas imágenes muestran la pestaña Aplicaciones como la pestaña seleccionada de las tres pestañas disponibles: Aplicaciones, Dispositivos y Contactar con TI.](./media/CP_Android_AppsTab_BeforeAfter.png)

* __Navegación__: Todas las aplicaciones muestra una vista con las pestañas __Destacadas__, __Todas__ y __Categorías__ para navegar más fácilmente. __Contactar con TI__ se ha simplificado para mejorar la legibilidad.

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_contactit_after.png" alt="The Company Portal app for Android displaying an updated version of the Contact IT tab. The tab shows available contact information for IT, including phone number, email address, IT website, and IT contact information." width=200 height=366 align=center>
          </td>
      </tr>
   </table>
</body>
</html>

## <a name="january-2017"></a>Enero de 2017

### <a name="modernizing-the-company-portal-website---753980-announced-1701--"></a>Renovación del sitio web del portal de empresa<!--753980, announced 1701-->
A partir de febrero, el sitio web del portal de empresa admitirá aplicaciones destinadas a aquellos usuarios que no tienen dispositivos administrados. El sitio web se asemejará a otros productos y servicios de Microsoft gracias a una nueva combinación de colores de contraste, ilustraciones dinámicas y un “menú hamburguesa”, ![Pequeña imagen del menú hamburguesa que se ha agregado en la esquina superior izquierda del sitio web del portal de empresa](./media/CP_hamburger_menu.png) que contendrá los detalles de contacto del departamento de soporte técnico e información sobre los dispositivos administrados existentes. La página de inicio se reorganizará para destacar las aplicaciones que están disponibles para los usuarios, con carruseles para aplicaciones destacadas y actualizadas recientemente.

![A la izquierda, una imagen de la versión actual del sitio web Portal de empresa con su versión anterior de Aplicaciones, Mis dispositivos, y las vistas Destacadas y Categorías. A la derecha, una imagen de la versión actualizada del sitio web Portal de empresa con un carrusel de aplicaciones actualizado, la lista de aplicaciones publicadas recientemente y la vista Categorías actualizada.](./media/CP_Website_BeforeAfter_Feb2016.png)


### <a name="see-also"></a>Consulte también
* [Blog de Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guía básica de Cloud Platform](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novedades en la vista previa de Azure](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [Archivo de novedades](whats-new-archive.md)

