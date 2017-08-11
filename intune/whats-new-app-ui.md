---
title: Actualizaciones de la interfaz de usuario para las aplicaciones de usuario final de Intune
description: "Averigüe qué ha cambiado en la interfaz de usuario para las aplicaciones que funcionan en dispositivos de usuario final con Intune."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b782e382-8deb-48a7-a437-d7c5a17163f1
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 948a7d2e4e0ad80088d864708db5733f08db77c5
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2017
---
# <a name="ui-updates-for-intune-end-user-apps"></a>Actualizaciones de la interfaz de usuario para las aplicaciones de usuario final de Intune
Obtenga más información sobre las actualizaciones que hemos realizado en la interfaz de usuario para las aplicaciones que verán los usuarios finales en esta versión de Microsoft Intune. Esto puede ayudarle con las comunicaciones de usuario y cualquier documentación de actualización personalizada que haya creado para admitir su implementación. También puede ayudarle a comprender cómo solucionar mejor los posibles problemas a los que se enfrenten en caso de que sea necesario llamar al departamento de soporte técnico mediante el Portal de empresa.

## <a name="week-of-july-31-2017"></a>Semana del 31 de julio de 2017

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Se mejoró la experiencia de inicio de sesión en todas las aplicaciones del Portal de empresa para todas las plataformas <!--User Story 1132123-->

Estamos anunciando un cambio que aparecerá en los próximos meses que mejorará la experiencia de inicio de sesión para las aplicaciones del Portal de empresa de Intune para Android, iOS y Windows. La nueva experiencia del usuario aparecerá automáticamente en todas las plataformas de la aplicación Portal de empresa cuando Azure AD haga este cambio. Además, los usuarios ahora pueden iniciar sesión en Portal de empresa desde otro dispositivo con un código generado de un solo uso. Esto resulta útil especialmente en casos en los que los usuarios necesitan iniciar sesión sin credenciales.  

A continuación puede ver la experiencia de inicio de sesión anterior, la nueva experiencia de inicio de sesión con credenciales y la nueva experiencia de inicio de sesión desde otro dispositivo.

__Experiencia de inicio de sesión anterior__

![La página de inicio de sesión de Portal de empresa, con el icono de una persona frente a una representación gráfica de un sitio web. Abajo aparece el botón "Iniciar sesión". Un vínculo en la parte inferior lleva a información de Privacidad y cookies de Microsoft.](./media/cp_ios_aad_signin_before_1704_001.png)

![Después de pulsar Iniciar sesión, el usuario escribe las credenciales en esta página, que pide el correo electrónico y la contraseña de un usuario, además de ofrecer formas de solucionar los errores de contraseña.](./media/cp_ios_aad_signin_before_1704_002.png)

![Después de proporcionar la contraseña, la aplicación Portal de empresa inicia sesión, lo que se indica con una barra de carga.](./media/cp_ios_aad_signin_before_1704_003.png)

__Nueva experiencia de inicio de sesión__

![La página de inicio de sesión de Portal de empresa, con el icono de una persona frente a una representación gráfica de un sitio web. Abajo aparece el botón "Iniciar sesión". Un vínculo en la parte inferior lleva a información de Privacidad y cookies de Microsoft.](./media/cp_ios_aad_signin_after_1704_001.png)

![Se solicita al usuario que proporcione solamente su dirección de correo electrónico en lugar de la dirección de correo electrónico y la contraseña en la misma pantalla.](./media/cp_ios_aad_signin_after_1704_002.png)

![El usuario deberá escribir la contraseña una vez que se acepte la dirección de correo electrónico.](./media/cp_ios_aad_signin_after_1704_003.png)

![Después del proceso de autenticación, la aplicación Portal de empresa inicia sesión, lo que se indica con una barra de carga.](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

__Nueva experiencia de inicio de sesión cuando se inicia sesión desde otro dispositivo__

![La página de inicio de sesión de Portal de empresa, con el icono de una persona frente a una representación gráfica de un sitio web. Abajo aparece el botón "Iniciar sesión". Un vínculo en la parte inferior lleva a información de Privacidad y cookies de Microsoft.](./media/cp_ios_aad_signin_from_another_device_after_1704_001.png)

Pulse el vínculo __Iniciar sesión desde otro dispositivo__.

![Se proporcionan instrucciones para ir a la página aka.ms/devicelogin con un código de acceso único desde el equipo de trabajo y, luego, use el código para iniciar sesión.](./media/cp_ios_aad_signin_from_another_device_after_1704_003.png)

Inicie un explorador y vaya a [https://aka.ms/devicelogin](https://aka.ms/devicelogin).

![Imagen del explorador del usuario en su equipo de trabajo en lugar de su aplicación Portal de empresa. La página "Inicio de sesión del dispositivo" que aparece solicita al usuario el código que recibió en la aplicación Portal de empresa.](./media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

Escriba el código que vio en la aplicación Portal de empresa. Cuando seleccione __Continuar__, podrá autenticarse con cualquier método que admita su empresa, como una tarjeta inteligente.

![El usuario ingresó su código único en el campo y el sitio "Inicio de sesión del dispositivo" solicitó la confirmación con respecto a que Portal de empresa de Intune era la aplicación correcta para recibir autorización para iniciar sesión.](./media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

![Una página de confirmación que establece que el usuario inició sesión en la aplicación Portal de empresa en el dispositivo y que se puede cerrar esta página.](./media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

La aplicación Portal de empresa comenzará a iniciar sesión.

![Después del proceso de autenticación, la aplicación Portal de empresa inicia sesión, lo que se indica con una barra de carga.](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

## <a name="week-of-june-12-2017"></a>Semana del 12 de junio de 2017

### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>La aplicación portal de empresa para Android ahora tiene una nueva experiencia de usuario final para las directivas de protección de aplicaciones <!--1305217-->
Basándonos en los comentarios de los clientes, hemos modificado la aplicación del portal de empresa para Android para mostrar un botón **Acceso al contenido de la empresa**. El objetivo es impedir que los usuarios finales pasen innecesariamente por todo el proceso de inscripción cuando solo necesitan tener acceso a las aplicaciones que admiten las directivas de protección de aplicaciones, una característica de la administración de aplicaciones móviles de Intune.

El usuario pulsará el botón **Acceso al contenido de la empresa** en lugar de comenzar a inscribir el dispositivo.

![Una imagen de la aplicación de portal de empresa de Android que muestra en texto grande "Acceso al contenido de la empresa" en el centro, en lugar de ofrecer opciones de inscripción inmediatas como es el caso estándar](./media/and_access_company_content_after_1706.png)

Después, al usuario se le redirige al sitio web del portal de empresa para autorizar la aplicación para su uso en el dispositivo, donde el sitio web del portal de empresa comprueba sus credenciales.

![Una imagen del sitio web del portal de empresa, que confirma el inicio de sesión.](./media/and_iwp_sign_in_auth_page_after_1706.png)

El dispositivo todavía puede inscribirse en la administración completa al pulsar el menú de **acción**.

![Una imagen de la aplicación de portal de empresa para Android que muestra el menú desde la esquina superior derecha de la pantalla con una opción para seguir inscribiendo el dispositivo.](./media/and_sign_in_menu_after_app_protection_policy_enrolled_after_1706.png)

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Mejoras en la sincronización de aplicaciones con Windows 10 Creators Update <!--676505-->

La aplicación Portal de empresa de Intune para Windows 10 ahora iniciará automáticamente una sincronización de las solicitudes de instalación de aplicaciones para dispositivos con Windows 10 Creators Update (versión 1703). De esta forma, se reducirá el problema de estancamiento de las instalaciones de aplicaciones durante el estado "Pending Sync" (Sincronización pendiente). Además, los usuarios podrán iniciar manualmente la sincronización desde dentro de la aplicación.

![Una imagen de la aplicación de portal de empresa de Windows 10, donde la descarga de Microsoft Word está en un estado pendiente desde la tienda de aplicaciones del portal de empresa.](./media/w10_download_pending_after_1706.png)

![Una imagen de la aplicación de portal de empresa de Windows 10, con el nuevo estado de sincronización automático que muestra un mensaje de estado indicando que el dispositivo está sincronizándose e intentando descargar la aplicación.](./media/w10_download_pending_syncing_after_1706.png)

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Nueva experiencia guiada del Portal de empresa de Windows 10<!---1058938--->
La aplicación del Portal de empresa para Windows 10 incluirá la experiencia de un tutorial de Intune guiado para dispositivos que no se han identificado ni inscrito. La nueva experiencia proporciona instrucciones paso a paso que llevan al usuario por el registro en Azure Active Directory (que es necesario para las características de acceso condicional) y la inscripción en MDM (que es necesaria para las características de administración de dispositivos). La experiencia guiada será accesible desde la página principal del Portal de empresa. Los usuarios pueden seguir usando la aplicación aunque no completen el registro y la inscripción, pero experimentarán una funcionalidad limitada.

Esta actualización solo es visible en dispositivos que ejecuten la Actualización de aniversario de Windows 10 (compilación 1607) o superior.

![Una imagen de la página de aterrizaje de la aplicación de portal de empresa de Windows 10, con un mensaje de estado en el medio de la lista "dispositivos" que indica al usuario que el dispositivo en el que se encuentra no se ha configurado todavía para el uso corporativo y que el usuario debe seleccionar para comenzar la instalación.](./media/win10_guided_enroll_select_setup_after_1706.png)

![Una imagen de la página de instalación de la aplicación de portal de empresa de Windows 10, que advierte al usuario de que necesita agregar una cuenta corporativa a este dispositivo, después, puede inscribirlo en la administración.](./media/win10_guided_enroll_we_help_setup_after_1706.png)

![Una imagen de la adición de una cuenta corporativa a esta página de dispositivo de la aplicación de portal de empresa de Windows 10 que indica al usuario que necesitará ir a la aplicación Configuración y seleccionar "Conectar" para completar la inscripción. Después de hacer esto, la pantalla le indica que necesitará volver a la aplicación de portal de empresa para completar la inscripción.](./media/win10_guided_enroll_leaving_for_iwp_after_1706.png)

![Una imagen de la inscripción en la pantalla de administración de la aplicación de portal de empresa de Windows 10, que muestra un mensaje de estado completado que indica que el dispositivo del usuario ahora está inscrito y que debe pulsar el botón "Siguiente" para continuar.](./media/win10_guided_enroll_youre_now_enrolled_after_1706.png)

![Una imagen de la pantalla de finalización de la aplicación de portal de empresa de Windows 10, que permite que el usuario conozca que está todo configurado y que el dispositivo está inscrito con una cuenta corporativa que se ha agregado correctamente a este.](./media/win10_guided_enroll_youre_all_set_after_1706.png)

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>Nueva acción de menú para quitar fácilmente Portal de empresa de Intune <!--1164569-->
Según los comentarios de los usuarios, se agregó una nueva acción de menú en la aplicación Portal de empresa de Intune para Android con el fin de iniciar su eliminación del dispositivo. Esta acción quita el dispositivo de la administración de Intune, por lo que el usuario puede quitar la aplicación del dispositivo.

![Una imagen de la aplicación de Portal de empresa de Android con el menú de acciones abierto en la esquina superior derecha. La nueva opción "quitar portal de empresa" está disponible como la tercera opción, debajo de "mi perfil" y "configuración" y sobre "términos y condiciones", "ayuda y comentarios" e "información".](./media/android_remove_cp_menu_action_after_1705.png)

![Una imagen del cuadro de diálogo de confirmación, disponible después de seleccionar la nueva opción "quitar portal de empresa" del menú de acciones. El cuadro de diálogo informa al usuario que "al quitar portal de empresa, el dispositivo ya no estará administrado por el administrador de TI y podrá quitar el acceso a los datos, las aplicaciones y el correo electrónico de la empresa". Luego se le pide al usuario que seleccione "Sí" para confirmar que desea quitar la aplicación Portal de empresa.](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="week-of-june-5-2017"></a>Semana del 5 de junio de 2017

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>Mejoras de los iconos de aplicación en la aplicación Portal de empresa de Intune para iOS
Se actualizó el diseño de los iconos de aplicación en la página principal para reflejar el color de personalización de marca que estableció para Portal de empresa de Intune.

**Antes**

![Una imagen de la aplicación Portal de empresa para iOS anterior a la actualización, que mostraba imágenes de relleno preestablecidas para "Todas las aplicaciones", "Aplicaciones destacadas" y "categorías".](./media/cp_ios_homepage_before_1705.png)

**Después**

![Una imagen de la aplicación Portal de empresa para iOS posterior a la actualización, que ahora refleja la capacidad de seleccionar los colores que corresponden a su organización.](./media/cp_ios_homepage_after_1705.png)

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>Ahora el selector de cuenta está disponible en la aplicación Portal de empresa de Intune para iOS
Si los usuarios usaron su cuenta profesional o educativa para iniciar sesión en otras aplicaciones Microsoft en un dispositivo iOS, pueden ver el nuevo selector de cuenta cuando inician sesión por primera vez en Portal de empresa.

![Una imagen del selector de cuenta, que muestra a un usuario de prueba, "Robin Swanson", cuando elige entre una de sus dos direcciones de correo electrónico. Hay un botón debajo de ambas direcciones que permite que el usuario inicie sesión con otra cuenta.](./media/cp_ios_multi-account-selector-after-1705.png)

## <a name="april-2017"></a>Abril de 2017

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Nuevos iconos para Managed Browser y el Portal de empresa <!--918433, 918431-->

Managed Browser está recibiendo iconos actualizados para las versiones de iOS y Android de la aplicación. El nuevo icono contendrá el distintivo de Intune actualizado para que sea más coherente con otras aplicaciones de Enterprise Mobility + Security (EM+S).

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_manbro_before_042017.png" alt="The previous version of the Managed Browser app icon." width=200 height=366 align=center>
          </td>
          <td>
             <img src="/intune/media/cp_manbro_after_042017.png" alt="The updated version of the Managed Browser app icon." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

El Portal de empresa también está recibiendo iconos actualizados para las versiones de Windows, iOS y Android de la aplicación con el objetivo de mejorar la coherencia con otras aplicaciones de EM+S. Estos iconos se lanzarán gradualmente en las plataformas desde abril hasta finales de mayo.

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Indicador de progreso de inicio de sesión en Portal de empresa de Android <!--953374-->

Una actualización de la aplicación Portal de empresa de Android muestra un indicador de progreso de inicio de sesión cuando el usuario inicia o reanuda la aplicación. El indicador avanza por los nuevos estados, desde "Conectando..." e "Iniciando sesión..." hasta "Comprobando los requisitos de seguridad...", antes de permitir que el usuario acceda a la aplicación.

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_android_connecting_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Connecting' underneath it." width=200 height=366 align=center>
          </td>
          <td>
             <img src="/intune/media/cp_android_signing_in_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Signing in' underneath it." width=200 height=366 align=center>
           </td>
           <td>
              <img src="/intune/media/cp_android_checking_security_reqs_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Checking for security requirements' underneath it." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Mejora del estado de instalación de la aplicación para la aplicación Portal de empresa de Windows 10 <!--676495-->
La aplicación Portal de empresa para Windows 10 ahora proporciona una barra de progreso de la instalación en la página de detalles de la aplicación. Esto se admite para aplicaciones modernas en dispositivos que ejecutan la Actualización de aniversario de Windows 10 o superior.

__Antes__ ![Una imagen de la versión anterior de la pantalla de carga, donde el estado dice simplemente "instalando".](./media/cp_win10_install_status_before_1704.png)

__Después__ ![Una imagen de la versión actualizada de la pantalla de carga, que ahora muestra una barra de progreso de la instalación.](./media/cp_win10_install_status_after_1704.png)

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
            <img src="/intune/media/cp_android_contactit_after.png" alt="The Company Portal app for Android displaying an updated version of the Contact IT tab. The tab shows available contact information for IT, including phone number, email address, IT website, and IT contact information." width=200 height=366 align=center>
          </td>
      </tr>
   </table>
</body>
</html>

## <a name="january-2017"></a>Enero de 2017

### <a name="modernizing-the-company-portal-website---753980-announced-1701--"></a>Renovación del sitio web del portal de empresa<!--753980, announced 1701-->
A partir de febrero, el sitio web del portal de empresa admitirá aplicaciones destinadas a aquellos usuarios que no tienen dispositivos administrados. El sitio web se asemejará a otros productos y servicios de Microsoft gracias a una nueva combinación de colores de contraste, ilustraciones dinámicas y un “menú hamburguesa”, ![Pequeña imagen del menú hamburguesa que se ha agregado en la esquina superior izquierda del sitio web del portal de empresa](./media/CP_hamburger_menu.png) que contendrá los detalles de contacto del departamento de soporte técnico e información sobre los dispositivos administrados existentes. La página de inicio se reorganizará para destacar las aplicaciones que están disponibles para los usuarios, con carruseles para aplicaciones destacadas y actualizadas recientemente.

![A la izquierda, una imagen de la versión actual del sitio web Portal de empresa con su versión anterior de Aplicaciones, Mis dispositivos, y las vistas Destacadas y Categorías. A la derecha, una imagen de la versión actualizada del sitio web Portal de empresa con un carrusel de aplicaciones actualizado, la lista de aplicaciones publicadas recientemente y la vista Categorías actualizada.](./media/CP_Website_BeforeAfter_Feb2016.png)

## <a name="coming-soon-in-the-ui"></a>Próximamente en la interfaz de usuario
Estos son los planes para mejorar la experiencia del usuario mediante la actualización de nuestra interfaz de usuario.

> [!Note]
> Tenga en cuenta que las imágenes siguientes pueden corresponder a versiones preliminares y que el producto anunciado puede diferir de las versiones presentadas.

### <a name="ui-updates-to-the-company-portal-website---1313244-part-2--"></a>Actualizaciones de la interfaz de usuario en el sitio web del portal de empresa <!--1313244 part 2-->

__Actualizaciones de aplicaciones destacadas__ Hemos agregado una página dedicada al sitio donde los usuarios pueden buscar aplicaciones que ha decidido presentar, y hemos realizado algunos ajustes a la interfaz de usuario de la sección Destacado en la página principal.

![Los iconos de colores que muestran las aplicaciones. Son cuadrados grandes de colores debajo de cada aplicación, donde el color se extrae del color principal del logotipo de la aplicación. La sección "Aplicaciones destacadas" aparece en la parte superior de la aplicación de portal de empresa.](./media/cp_win10_colorful_tiles_after_1708.png)

### <a name="see-also"></a>Consulte también
* [Blog de Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guía básica de Cloud Platform](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novedades de Intune](https://docs.microsoft.com/intune/whats-new)
