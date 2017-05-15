---
title: Actualizaciones de la interfaz de usuario para las aplicaciones de usuario final de Intune | Microsoft Docs
description: Conozca lo que ha cambiado en la interfaz de usuario para las aplicaciones que funcionan en dispositivos del usuario final con Intune.
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 04/26/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b782e382-8deb-48a7-a437-d7c5a17163f1
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 5f172290d493717308446c4f9e2313a03ba8f3aa
ms.openlocfilehash: 84c6c9ddeeff3570d0b00364063e43105141de0f
ms.contentlocale: es-es
ms.lasthandoff: 04/27/2017


---
# <a name="ui-updates-for-intune-end-user-apps"></a>Actualizaciones de la interfaz de usuario para las aplicaciones de usuario final de Intune
Obtenga más información sobre las actualizaciones que hemos realizado en la interfaz de usuario para las aplicaciones que verán los usuarios finales en esta versión de Microsoft Intune. Esto puede ayudarle con las comunicaciones de usuario y cualquier documentación de actualización personalizada que haya creado para admitir su implementación. También puede ayudarle a comprender cómo solucionar mejor los posibles problemas a los que se enfrenten en caso de que sea necesario llamar al departamento de soporte técnico mediante el Portal de empresa.

> [!Note]
> Tenga en cuenta que las imágenes siguientes corresponden a la versión preliminar y que el producto anunciado puede diferir de las versiones presentadas.

## <a name="april-2017"></a>Abril de 2017

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Se mejoró la experiencia de inicio de sesión en todas las aplicaciones del Portal de empresa para todas las plataformas <!--User Story 1132123-->

Estamos mejorando la experiencia de inicio de sesión de las aplicaciones del Portal de empresa de Intune para Android, iOS y Windows.  La nueva experiencia del usuario aparecerá automáticamente en todas las plataformas de la aplicación Portal de empresa cuando Azure AD haga este cambio. Además, los usuarios ahora pueden iniciar sesión en el Portal de empresa desde otro dispositivo con un código generado de un solo uso. Esto resulta útil especialmente en casos en los que los usuarios necesitan iniciar sesión sin credenciales.  

A continuación puede ver la experiencia de inicio de sesión anterior, la nueva experiencia de inicio de sesión con credenciales y la nueva experiencia de inicio de sesión desde otro dispositivo.

__Experiencia de inicio de sesión anterior__

![Página de inicio de sesión de Portal de empresa, con un icono de una persona delante de una representación gráfica de un sitio web. Debajo está el botón "Iniciar sesión". Un vínculo en la parte inferior conduce a la información de cookies y privacidad de Microsoft.](./media/cp_ios_aad_signin_before_1704_001.png)

![Después de pulsar el botón Iniciar sesión, el usuario escribe sus credenciales en esta página, que solicita un correo electrónico y una contraseña del usuario, además de ofrecer formas de resolver los errores de contraseña.](./media/cp_ios_aad_signin_before_1704_002.png)

![Después de proporcionar la contraseña, la aplicación Portal de empresa inicia sesión, lo que se indica mediante una barra de carga.](./media/cp_ios_aad_signin_before_1704_003.png)

__Nueva experiencia de inicio de sesión__

![Página de inicio de sesión de Portal de empresa, con un icono de una persona delante de una representación gráfica de un sitio web. Debajo está el botón "Iniciar sesión". Un vínculo en la parte inferior conduce a la información de cookies y privacidad de Microsoft.](./media/cp_ios_aad_signin_after_1704_001.png)

![Se solicita al usuario que proporcione solo su dirección de correo electrónico en lugar de su correo electrónico y contraseña en la misma pantalla.](./media/cp_ios_aad_signin_after_1704_002.png)

![Se pide al usuario la contraseña después de que se haya aceptado su dirección de correo electrónico.](./media/cp_ios_aad_signin_after_1704_003.png)

__Nueva experiencia de inicio de sesión cuando se inicia sesión desde otro dispositivo__

![Página de inicio de sesión de Portal de empresa, con un icono de una persona delante de una representación gráfica de un sitio web. Debajo está el botón "Iniciar sesión". Un vínculo en la parte inferior conduce a la información de cookies y privacidad de Microsoft.](./media/cp_ios_aad_signin_from_another_device_after_1704_001.png)

Pulse el vínculo __Iniciar sesión desde otro dispositivo__.

![Se solicita al usuario que proporcione solo su dirección de correo electrónico en lugar de su correo electrónico y contraseña en la misma pantalla. El vínculo situado bajo el campo de correo electrónico dice "Iniciar sesión desde otro dispositivo".](./media/cp_ios_aad_signin_from_another_device_after_1704_002.png)

![Se proporcionan instrucciones para ir a la página aka.ms/devicelogin con un único código de acceso desde el equipo de trabajo; luego se usa el código para iniciar sesión.](./media/cp_ios_aad_signin_from_another_device_after_1704_003.png)

Inicie un explorador y vaya a [https://aka.ms/devicelogin](https://aka.ms/devicelogin).

![Imagen del explorador del usuario en su equipo de trabajo en lugar de su aplicación Portal de empresa. La página "Inicio de sesión del dispositivo" mostrada solicita al usuario el código que se recibe en la aplicación Portal de empresa.](./media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

Escriba el código que vio en la aplicación Portal de empresa. Cuando seleccione __Continuar__, podrá autenticarse utilizando cualquier método que admita la empresa, como una tarjeta inteligente.

![El usuario ha agregado a su código único en el campo y el sitio "Inicio de sesión del dispositivo" ha solicitado la confirmación de que Portal de empresa de Intune era la aplicación correcta para recibir la autorización para iniciar sesión.](./media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

![Página de confirmación que indica que el usuario ya ha iniciado sesión ahora en la aplicación Portal de empresa en el dispositivo y que se puede cerrar esta página.](./media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

La aplicación Portal de empresa comenzará a iniciar sesión.

![Después de pasar por el proceso de autenticación, la aplicación Portal de empresa inicia sesión, lo que se indica mediante una barra de carga.](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Nuevos iconos para Managed Browser y Portal de empresa <!--918433, 918431-->

Managed Browser recibirá iconos actualizados para la versión de la aplicación de Android y la de iOS. El nuevo icono contendrá la notificación de Intune actualizada para que sea más coherente con otras aplicaciones de Enterprise Mobility + Security (EM+S).

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

Portal de empresa también recibirá iconos actualizados para las versiones de Windows, iOS y Android de la aplicación a fin de mejorar la coherencia con otras aplicaciones de EM+S. Estos iconos se lanzarán gradualmente en las distintas plataformas desde abril hasta finales de mayo.

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Indicador de progreso de inicio de sesión en Portal de empresa para Android <!--953374-->

Una actualización de la aplicación Portal de empresa para Android muestra un indicador de progreso de inicio de sesión cuando el usuario inicia o reanuda la aplicación. El indicador avanza por los nuevos estados, desde "Conectando..." e "Iniciando sesión..." hasta "Comprobando los requisitos de seguridad...", antes de permitir que el usuario acceda a la aplicación.

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

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Mejora del estado de instalación de la aplicación para la aplicación Portal de empresa de Windows 10 <!--676495-->
La aplicación Portal de empresa de Windows 10 ahora proporcionará la barra de progreso de instalación de la aplicación para todas las instalaciones de aplicaciones modernas iniciadas desde el Portal de empresa.

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_win10_install_status_before_1704.png" alt="An image of the previous version of the loading screen, where the status simply said 'installing.'" width=200 height=366 align=center>
          </td>
          <td>
             <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_win10_install_status_after_1704.png" alt="An image of the updated version of the loading screen, which now shows an install progress bar." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

## <a name="february-2017"></a>Febrero de 2017

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622-announced-1702--"></a>Nueva experiencia de usuario para la aplicación Portal de empresa para Android <!--621622, announced 1702-->
A partir de marzo, la aplicación Portal de empresa para Android seguirá las [directrices de Material Design](https://material.io/guidelines/material-design/introduction.html) para crear una apariencia más moderna. Esta experiencia del usuario mejorada incluye:

* __Colores__: los encabezados de pestaña pueden colorearse según la paleta de colores personalizada.

![A la izquierda, una imagen de la aplicación Portal de empresa para Android antes de la actualización. A la derecha, una imagen de la aplicación Portal de empresa para Android después de la actualización. Ambas imágenes muestran la pestaña Dispositivos como la pestaña seleccionada desde las tres pestañas disponibles Aplicaciones, Dispositivos y Contactar con TI.](./media/CP_Android_DevicesTab_BeforeAfter.png)

* __Interfaz__: los botones __Aplicaciones destacadas__ y __Todas las aplicaciones__ se han actualizado en la pestaña __Aplicaciones__. El botón __Buscar__ ahora es un botón de acción flotante.

![A la izquierda, una imagen de la aplicación Portal de empresa para Android antes de la actualización. A la derecha, una imagen de la aplicación Portal de empresa para Android después de la actualización. Ambas imágenes muestran la pestaña Aplicaciones como la pestaña seleccionada desde las tres pestañas disponibles Aplicaciones, Dispositivos y Contactar con TI.](./media/CP_Android_AppsTab_BeforeAfter.png)

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

### <a name="modernizing-the-company-portal-website---753980-announced-1701--"></a>Renovación del sitio web del Portal de empresa <!--753980, announced 1701-->
A partir de febrero, el sitio web del Portal de empresa admitirá aplicaciones destinadas a aquellos usuarios que no tienen dispositivos administrados. El sitio web se asemejará a otros productos y servicios de Microsoft gracias a una nueva combinación de colores de contraste, ilustraciones dinámicas y un "menú hamburguesa", ![Pequeña imagen del menú hamburguesa que se ha agregado en la esquina superior izquierda del sitio web del Portal de empresa](./media/CP_hamburger_menu.png) que contendrá los detalles de contacto del departamento de soporte técnico e información sobre los dispositivos administrados existentes. La página de inicio se reorganizará para destacar las aplicaciones que están disponibles para los usuarios, con carruseles para aplicaciones destacadas y actualizadas recientemente.

![A la izquierda, una imagen de la versión actual del sitio web del Portal de empresa con su versión anterior de Aplicaciones, Mis dispositivos y las vistas Destacadas y Categorías. A la derecha, ver una imagen de la versión actualizada del sitio web del Portal de empresa con un carrusel de aplicaciones actualizadas, la lista de aplicaciones publicadas recientemente y la vista de categorías actualizadas.](./media/CP_Website_BeforeAfter_Feb2016.png)


### <a name="see-also"></a>Consulte también
* [Blog de Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guía básica de la plataforma en la nube](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novedades de la versión preliminar de Azure](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [Archivo de novedades](whats-new-archive.md)

