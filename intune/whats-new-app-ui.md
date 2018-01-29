---
title: Actualizaciones de la interfaz de usuario para las aplicaciones de usuario final de Intune
description: "Averigüe qué ha cambiado en la interfaz de usuario para las aplicaciones que funcionan en dispositivos de usuario final con Intune."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/18/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b782e382-8deb-48a7-a437-d7c5a17163f1
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1662245fdf9ba557fbc62fbb2e9c0e1aa29888b2
ms.sourcegitcommit: 5877b650d93fc9a5e8f058f845acbdbfdff828b7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2018
---
# <a name="ui-updates-for-intune-end-user-apps"></a>Actualizaciones de la interfaz de usuario para las aplicaciones de usuario final de Intune
Obtenga más información sobre las actualizaciones que hemos realizado en la interfaz de usuario para las aplicaciones que verán los usuarios finales en esta versión de Microsoft Intune. Esto puede ayudarle con las comunicaciones de usuario y cualquier documentación de actualización personalizada que haya creado para admitir su implementación. También puede ayudarle a comprender cómo solucionar mejor los posibles problemas a los que se enfrenten en caso de que sea necesario llamar al departamento de soporte técnico mediante el Portal de empresa.

## <a name="week-of-december-11-2017"></a>Semana del 11 de diciembre de 2017

### <a name="end-user-messaging-for-accounts---1573558-1712-changes-to-be-made-for-other-platforms-for-1801--"></a>Mensajería para las cuentas del usuario final <!--1573558, 1712; changes to be made for other platforms for 1801-->

Los usuarios del sitio web de Portal de empresa no podrán realizar acciones que requieran acceso de escritura a su inquilino. Verán el mensaje de error correspondiente que explica que su cuenta está en mantenimiento. Próximamente se incorporarán modificaciones similares a las aplicaciones de Portal de empresa para Android, iOS, macOS y Windows.

![Mensaje de error que se produce durante el movimiento de cuenta](./media/account-move-rom-iwp-user-1712.png)

## <a name="week-of-november-27-2017"></a>Semana del 27 de noviembre de 2017

### <a name="new-device-categories-step-in-guided-setup-for-the-company-portal-app-for-windows-10----1335292---"></a>Nuevo paso "Categorías de dispositivos" en la configuración guiada de la aplicación Portal de empresa para Windows 10 <!---1335292--->

Si ha habilitado la [asignación de grupos de dispositivos](device-group-mapping.md), la aplicación Portal de empresa para Windows 10 ahora guía a los usuarios a través de la selección de una categoría de dispositivo después de inscribir el dispositivo.

![Categoría de asignación de grupos de dispositivos](./media/w10_cp_category_device_setup_after_1711.png)

## <a name="week-of-november-13-2017"></a>Semana del 13 de noviembre de 2017

### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>Mejoras en el flujo de trabajo de configuración de dispositivos en Portal de empresa para iOS, versión 2.9.0 <!---1417174--->

Hemos mejorado el flujo de trabajo de configuración de dispositivos en la aplicación Portal de empresa para iOS. El lenguaje ahora es más fácil de entender, y también hemos combinado las pantallas que hemos podido. También hemos utilizado el nombre de su empresa en el texto del proceso de configuración para que el lenguaje sea más específico.

> [!NOTE]
> Utilizamos el nombre de empresa que ha establecido en Azure Portal, en **Microsoft Intune** > **Mobile Apps** > **Personalización de marca del Portal de empresa** > **Nombre de la empresa**. Si no ha definido este valor, se usará el nombre del inquilino establecido en **Azure Active Directory** > **Propiedades** > **Nombre**. Si no ha establecido ningún nombre de empresa en Personalización de marca del Portal de empresa y no quiere que se muestre el nombre del inquilino, se recomienda definir el nombre de la empresa en dicha pestaña. Si no quiere que esta cadena aparezca en el encabezado de Portal de empresa, puede anular la selección de la casilla "Mostrar nombre de la empresa junto al logotipo".

|Antes|Después|
|---|---|
|![01](./media/ios_cp_enroll_01_before_1711.png)|![01](./media/ios_cp_enroll_01_after_1711.png)|
|![02](./media/ios_cp_enroll_02_before_1711.png)|*Combinado con el paso anterior*|
|![03](./media/ios_cp_enroll_03_before_1711.png)|![03](./media/ios_cp_enroll_03_after_1711.png)|
|![04](./media/ios_cp_enroll_04_before_1711.png)|![04](./media/ios_cp_enroll_04_after_1711.png)|
|![05](./media/ios_cp_enroll_05_before_1711.png)|![05](./media/ios_cp_enroll_05_after_1711.png)|
|![06](./media/ios_cp_enroll_06_before_1711.png)|![06](./media/ios_cp_enroll_06_after_1711.png)|
|![07](./media/ios_cp_enroll_07_before_1711.png)|![07](./media/ios_cp_enroll_07_after_1711.png)|


## <a name="week-of-november-6-2017"></a>Semana del 6 de noviembre de 2017

### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>Actualizaciones de la aplicación Portal de empresa para Windows 10 <!--1299474-->
La página Configuración de la aplicación de Portal de empresa para Windows 10 se ha actualizado para que las opciones y las acciones de usuario previstas sean más coherentes en relación con el resto de opciones de configuración. También se ha actualizado para que el diseño coincida con el de otras aplicaciones de Windows.

|Antes|Después|
|---|---|
|![01](./media/w10-share-logs.png)|![02](./media/w10-share-logs-after-1711.png)|


### <a name="search-improvements-to-the-company-portal-apps-and-website---1418189--"></a>Mejoras de búsqueda en el sitio web y las aplicaciones del Portal de empresa <!--1418189-->
Ahora, las aplicaciones del Portal de empresa realizan búsquedas en categorías de aplicaciones, nombres y descripciones. Los resultados se ordenan en orden decreciente de relevancia. Estas actualizaciones también están disponibles en el [sitio web del Portal de empresa](https://portal.manage.microsoft.com).

Seguimos ajustando el modo de seguimiento de la relevancia, por lo que le agradeceríamos que nos hiciera saber si resulta útil mediante el vínculo "Comentarios" situado en la parte inferior del sitio web del Portal de empresa.

## <a name="week-of-october-16-2017"></a>Semana del 16 de octubre de 2017

### <a name="search-improvements-to-the-company-portal-website---1331697--"></a>Mejoras de búsqueda en el sitio web del Portal de empresa <!--1331697-->
Estamos mejorando nuestras capacidades de búsqueda de aplicaciones, empezando por el [sitio web del Portal de empresa](https://portal.manage.microsoft.com). Las búsquedas ahora se efectuarán en categorías de aplicaciones, además de en los campos Nombre y Descripción. Los resultados se ordenarán, de forma predeterminada, en orden decreciente de relevancia. 

Los usuarios de dispositivos iOS también recibirán este cambio, ya que el sitio web del Portal de empresa también se usa como parte de la aplicación del Portal de empresa para iOS. Las aplicaciones del Portal de empresa para Android y Windows recibirán actualizaciones similares en los próximos meses.

Seguimos ajustando el modo de seguimiento de la relevancia, por lo que le agradeceríamos que nos hiciera saber si resulta útil mediante el vínculo "Comentarios" situado en la parte inferior del sitio web del Portal de empresa.


### <a name="ios-company-portal-displays-large-icons----1454593---"></a>En el portal de empresa de iOS se muestran iconos de gran tamaño <!-- 1454593 -->
Con esta versión se soluciona un problema conocido en relación con el modo en que el portal de empresa de iOS muestra los iconos en el icono de la aplicación. Si carga iconos de aplicación de 120x120 píxeles o más, ahora se muestran en el [sitio web del portal de empresa](https://portal.manage.microsoft.com) y las páginas de aplicaciones del Portal de empresa de iOS al tamaño completo del icono de aplicaciones.


## <a name="week-of-october-2-2017"></a>Semana del 2 de octubre de 2017

#### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>Mejoras en el flujo de trabajo de configuración de dispositivos en el Portal de empresa <!--1490692-->
Hemos mejorado el flujo de trabajo de configuración de dispositivos en la aplicación Portal de empresa para Android. El lenguaje es más fácil de usar y es específico de su empresa. Además, hemos combinado pantallas siempre que hemos podido. 

|Antes|Después|
|---|---|
|![01](./media/android_cp_enroll_01_post_1709.png)|![01](./media/android_cp_enroll_01_1709_new.png)|
|![01a](./media/android_cp_enroll_01_before_1710.png)| *Combinado con el paso anterior* |
|![02](./media/android_cp_enroll_02_before_1710.png)|![02](./media/android_cp_enroll_02_after_1710.png)|
|![03](./media/android_cp_enroll_03_before_1710.png)|![03](./media/android_cp_enroll_03_after_1710.png)|

Se han mejorado los pasos adicionales en los dispositivos de Android for Work.

|Antes|Después|
|---|---|
|![04](./media/android_work_cp_enroll_01_before_1710.png)|![04](./media/android_work_cp_enroll_01_after_1710.png)|
|![05](./media/android_work_cp_enroll_02_before_1710.png)| *Combinado con el paso anterior* |
|![06](./media/android_work_cp_enroll_03_before_1710.png)|![06](./media/android_work_cp_enroll_03_after_1710.png)|
|![07](./media/android_work_cp_enroll_04_before_1710.png)|![07](./media/android_work_cp_enroll_04_after_1710.png)|
|![08](./media/android_work_cp_enroll_05_before_1710.png)| *Combinado con el paso anterior* |


También hemos actualizado la pantalla de activación de correo electrónico de acceso condicional.

|Antes|Después|
|---|---|
|![06](./media/android_conditional_access_email_before_1710.png)|![06](./media/android_conditional_access_email_after_1710.png)

## <a name="week-of-september-11-2017"></a>Semana del 11 de septiembre de 2017

### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Expresión más fácil de entender para la aplicación de Portal de empresa para Android <!---1396349--->  

El proceso de inscripción para la aplicación de Portal de empresa para Android se ha simplificado con nuevo texto para que resulte más sencillo para los usuarios finales. Si tiene documentación de inscripción personalizada, deberá actualizarla para que se muestre en las nuevas pantallas. Puede encontrar imágenes de muestra a continuación:

|Antes|Después|
|---|---|
|![01](./media/android_cp_enroll_01_before_1709.png)|![01](./media/android_cp_enroll_01_post_1709.png)|
|![02](./media/android_cp_enroll_02_before_1709.png)|![02](./media/android_cp_enroll_02_post_1709.png)|
|![03](./media/android_cp_enroll_03_before_1709.png)|![03](./media/android_cp_enroll_03_post_1709.png)|
|![04](./media/android_cp_enroll_04_before_1709.png)|![04](./media/android_cp_enroll_04_post_1709.png)|
|![05](./media/android_cp_enroll_05_before_1709.png)|![05](./media/android_cp_enroll_05_post_1709.png)|


## <a name="august-2017"></a>Agosto de 2017

### <a name="ios-11-mail-app-will-support-oauth----1196951---"></a>Compatibilidad de la aplicación Mail de iOS 11 con OAuth <!---1196951--->

El acceso condicional con Intune es compatible con una autenticación más segura en dispositivos iOS con OAuth. Para lograr esta mayor seguridad en la autenticación, ahora habrá un flujo diferente en la aplicación Portal de empresa para iOS. Cuando los usuarios finales intenten iniciar sesión en una nueva cuenta de Exchange con la aplicación Mail, verán un mensaje de vista web. Tras la inscripción en Intune, los usuarios verán un mensaje para permitir que la aplicación nativa Mail acceda a un certificado. La mayoría de los usuarios finales no podrá ver correos electrónicos en cuarentena. Las cuentas de correo electrónico existentes continuarán usando el protocolo de autenticación básico, de modo que estos usuarios seguirán recibiendo correos electrónicos en cuarentena. Esta experiencia de inicio de sesión para los usuarios finales es similar a la de las aplicaciones móviles de Office.

![Seleccione el tipo de cuenta en la aplicación de correo electrónico nativa.](./media/ios-11-ca-email-after-1708-01.png)

![Después de seleccionar Exchange, el dispositivo iOS solicitará el nombre de la cuenta y la dirección de correo electrónico.](./media/ios-11-ca-email-after-1708-02.png)

![Proporcione la dirección de correo electrónico y el nombre de la cuenta.](./media/ios-11-ca-email-after-1708-03.png)

![Se le dirigirá a la página de inicio de sesión de Microsoft externa.](./media/ios-11-ca-email-after-1708-04.png)

![Proporcione la contraseña en la página de Microsoft.](./media/ios-11-ca-email-after-1708-05.png)

![Microsoft solicitará al usuario que inscriba el dispositivo en el sistema de administración.](./media/ios-11-ca-email-after-1708-06.png)

![Se solicitará al usuario que inscriba su dispositivo en el sitio web Portal de empresa.](./media/ios-11-ca-email-after-1708-07.png)



### <a name="intune-mobile-application-management-mam-dialog-boxes-will-have-a-modern-interface----1199015---"></a>Ahora los cuadros de diálogo de administración de aplicaciones móviles (MAM) de Intune tendrán una interfaz moderna <!-- 1199015 -->

Se actualizarán los cuadros de diálogo de administración de aplicaciones móviles (MAM) de Intune para tener un aspecto moderno. Los cuadros de diálogo funcionarán de la misma manera que con el estilo anterior.

**Experiencia anterior**

![interfaz antigua](./media/NewUI_Old_AttachFileHandler.jpg)

**Experiencia moderna**

![interfaz moderna](./media/NewUI_Modern_AttachFileHandler.jpg)


### <a name="updates-to-the-device-details-page-on-the-company-portal-app-for-windows-10----1287448---"></a>Actualizaciones en la página "Detalles del dispositivo" en la aplicación Portal de empresa para Windows 10 <!---1287448--->

La etiqueta __Categoría__ de la aplicación Portal de empresa para Windows 10 pasará de estar debajo del título a formar parte de una propiedad de la página __Detalles del dispositivo__.

![La pantalla "Detalles del dispositivo" de la aplicación Portal de empresa para Windows ahora muestra el campo "Categorías" como una propiedad, en lugar de hacerlo debajo del título.](./media/cp_win10_category_tag_move_after_1708.png)

## <a name="july-2017"></a>Julio de 2017

### <a name="apps-details-pages-will-display-new-information-for-android-devices---1287476--"></a>Las páginas de información de aplicaciones mostrarán información nueva para los dispositivos Android <!--1287476-->

La página de información de aplicaciones de la aplicación Portal de empresa para Android mostrará las categorías de aplicaciones que el administrador de TI haya definido para esa aplicación.

![Página de detalles de aplicaciones nueva](./media/cp_android_appdetails_after_1708.png)

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Se mejoró la experiencia de inicio de sesión en todas las aplicaciones del Portal de empresa para todas las plataformas <!--User Story 1132123-->

Estamos anunciando un cambio que aparecerá en los próximos meses que mejorará la experiencia de inicio de sesión para las aplicaciones del Portal de empresa de Intune para Android, iOS y Windows. La nueva experiencia del usuario aparecerá automáticamente en todas las plataformas de la aplicación Portal de empresa cuando Azure AD haga este cambio. Además, los usuarios ahora pueden iniciar sesión en Portal de empresa desde otro dispositivo con un código generado de un solo uso. Esto resulta útil especialmente en casos en los que los usuarios necesitan iniciar sesión sin credenciales.  

A continuación puede ver la experiencia de inicio de sesión anterior, la nueva experiencia de inicio de sesión con credenciales y la nueva experiencia de inicio de sesión desde otro dispositivo.

__Experiencia de inicio de sesión anterior__

![La página de inicio de sesión de Portal de empresa, con el icono de una persona frente a una representación gráfica de un sitio web. Abajo aparece el botón "Iniciar sesión". Un vínculo en la parte inferior lleva a información de Privacidad y cookies de Microsoft.](./media/cp_ios_aad_signin_before_1704_001.png)

![Después de pulsar Iniciar sesión, el usuario escribe las credenciales en esta página, que pide el correo electrónico y la contraseña de un usuario, además de ofrecer formas de solucionar los errores de contraseña.](./media/cp_ios_aad_signin_before_1704_002.png)

![Después de proporcionar la contraseña, la aplicación Portal de empresa inicia sesión, lo que se indica con una barra de carga.](./media/cp_ios_aad_signin_before_1704_003.png)

__Nueva experiencia de inicio de sesión__

![Página de inicio de sesión de Portal de empresa, con un icono de una persona delante de una representación gráfica de un sitio web. Abajo aparece el botón "Iniciar sesión". Un vínculo en la parte inferior conduce a la información de cookies y privacidad de Microsoft.](./media/cp_ios_aad_signin_after_1704_001.png)

![Se solicita al usuario que proporcione solo su dirección de correo electrónico en lugar de su correo electrónico y contraseña en la misma pantalla.](./media/cp_ios_aad_signin_after_1704_002.png)

![El usuario deberá escribir la contraseña una vez que se acepte la dirección de correo electrónico.](./media/cp_ios_aad_signin_after_1704_003.png)

![Después del proceso de autenticación, la aplicación Portal de empresa inicia sesión, lo que se indica con una barra de carga.](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

__Nueva experiencia de inicio de sesión cuando se inicia sesión desde otro dispositivo__

![La página de inicio de sesión de Portal de empresa, con el icono de una persona frente a una representación gráfica de un sitio web. Abajo aparece el botón "Iniciar sesión". Un vínculo en la parte inferior lleva a información de Privacidad y cookies de Microsoft.](./media/cp_ios_aad_signin_from_another_device_after_1704_001.png)

Pulse el vínculo __Iniciar sesión desde otro dispositivo__.

![Se proporcionan instrucciones para ir a la página aka.ms/devicelogin con un código de acceso único desde el equipo de trabajo y, luego, use el código para iniciar sesión.](./media/cp_ios_aad_signin_from_another_device_after_1704_003.png)

Inicie un explorador y vaya a [https://aka.ms/devicelogin](https://aka.ms/devicelogin).

![Imagen del explorador del usuario en su equipo de trabajo en lugar de su aplicación Portal de empresa. La página "Inicio de sesión del dispositivo" que aparece solicita al usuario el código que recibió en la aplicación Portal de empresa.](./media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

Escriba el código que vio en la aplicación Portal de empresa. Cuando seleccione __Continuar__, podrá autenticarse con cualquier método que admita su empresa, como una tarjeta inteligente.

![El usuario ha agregado a su código único en el campo y el sitio "Inicio de sesión del dispositivo" ha solicitado la confirmación de que Portal de empresa de Intune era la aplicación correcta para recibir la autorización para iniciar sesión.](./media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

![Una página de confirmación que establece que el usuario inició sesión en la aplicación Portal de empresa en el dispositivo y que se puede cerrar esta página.](./media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

La aplicación Portal de empresa comenzará a iniciar sesión.

![Después del proceso de autenticación, la aplicación Portal de empresa inicia sesión, lo que se indica con una barra de carga.](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

## <a name="june-2017"></a>Junio de 2017

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
La aplicación del Portal de empresa para Windows 10 incluirá la experiencia de un tutorial de Intune guiado para dispositivos que no se han identificado ni inscrito. La nueva experiencia proporciona instrucciones paso a paso que llevan al usuario por el registro en Azure Active Directory (que es necesario para las características de acceso condicional) y la inscripción en MDM (que es necesaria para las características de administración de dispositivos). La experiencia guiada será accesible desde la página principal del Portal de empresa. Los usuarios pueden seguir utilizando la aplicación si no completan el registro y la inscripción, pero experimentarán una funcionalidad limitada.

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

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios---1230777--"></a>Mejoras de los iconos de aplicación en la aplicación Portal de empresa de Intune para iOS <!--1230777-->
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

Managed Browser está recibiendo iconos actualizados para las versiones de iOS y Android de la aplicación. El nuevo icono contendrá la notificación de Intune actualizada para que sea más coherente con otras aplicaciones de Enterprise Mobility + Security (EM+S).

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_manbro_before_042017.png" alt="The previous version of the Managed Browser app icon." width="200" height="366" align="center">
          </td>
          <td>
             <img src="/intune/media/cp_manbro_after_042017.png" alt="The updated version of the Managed Browser app icon." width="200" height="366" align="center">
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
            <img src="/intune/media/cp_android_connecting_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Connecting' underneath it." width="200" height="366" align="center">
          </td>
          <td>
             <img src="/intune/media/cp_android_signing_in_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Signing in' underneath it." width="200" height="366" align="center">
           </td>
           <td>
              <img src="/intune/media/cp_android_checking_security_reqs_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Checking for security requirements' underneath it." width="200" height="366" align="center">
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

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622-announced-1702--"></a>Nueva experiencia de usuario para la aplicación Portal de empresa para Android <!--621622, announced 1702-->
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
            <img src="/intune/media/cp_android_contactit_after.png" alt="The Company Portal app for Android displaying an updated version of the Contact IT tab. The tab shows available contact information for IT, including phone number, email address, IT website, and IT contact information." width="200" height="366" align="center">
          </td>
      </tr>
   </table>
</body>
</html>

## <a name="january-2017"></a>Enero de 2017

### <a name="modernizing-the-company-portal-website---753980-announced-1701--"></a>Renovación del sitio web del Portal de empresa <!--753980, announced 1701-->
A partir de febrero, el sitio web del portal de empresa admitirá aplicaciones destinadas a aquellos usuarios que no tienen dispositivos administrados. El sitio web se asemejará a otros productos y servicios de Microsoft gracias a una nueva combinación de colores de contraste, ilustraciones dinámicas y un "menú hamburguesa", ![Pequeña imagen del menú hamburguesa que se ha agregado en la esquina superior izquierda del sitio web del Portal de empresa](./media/CP_hamburger_menu.png) que contendrá los detalles de contacto del departamento de soporte técnico e información sobre los dispositivos administrados existentes. La página de inicio se reorganizará para destacar las aplicaciones que están disponibles para los usuarios, con carruseles para aplicaciones destacadas y actualizadas recientemente.

![A la izquierda, una imagen de la versión actual del sitio web Portal de empresa con su versión anterior de Aplicaciones, Mis dispositivos, y las vistas Destacadas y Categorías. A la derecha, una imagen de la versión actualizada del sitio web Portal de empresa con un carrusel de aplicaciones actualizado, la lista de aplicaciones publicadas recientemente y la vista Categorías actualizada.](./media/CP_Website_BeforeAfter_Feb2016.png)

## <a name="coming-soon-in-the-ui"></a>Próximamente en la interfaz de usuario
Estos son los planes para mejorar la experiencia del usuario mediante la actualización de nuestra interfaz de usuario.

> [!Note]
> Tenga en cuenta que las imágenes siguientes pueden corresponder a versiones preliminares y que el producto anunciado puede diferir de las versiones presentadas.

### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866--"></a>Actualización de la experiencia del usuario en la aplicación del Portal de empresa para iOS <!--1412866-->

Lanzaremos una actualización importante de la experiencia de usuario para la aplicación del Portal de empresa para iOS. La actualización contará con un cambio de diseño visual completo, que incluye una apariencia y aspecto modernizados con mayor facilidad de uso y accesibilidad. Se mantendrán todas las funcionalidades del Portal de empresa de iOS actuales.

Ofrecemos una versión preliminar de la aplicación del Portal de empresa actualizada para iOS a través del programa TestFlight de Apple para que la use y nos envíe sus comentarios. Regístrese en https://aka.ms/intune_ios_cp_testflight para obtener acceso a TestFlight.

![imágenes de avance para la nueva aplicación del Portal de empresa de iOS](./media/ios-cp-app-redesign-1801-teaser.png)

### <a name="ui-updates-to-the-company-portal-website---1313244-part-2--"></a>Actualizaciones de la interfaz de usuario en el sitio web del portal de empresa <!--1313244 part 2-->

__Actualizaciones de aplicaciones destacadas__ Hemos agregado una página dedicada al sitio donde los usuarios pueden buscar aplicaciones que ha decidido presentar, y hemos realizado algunos ajustes a la interfaz de usuario de la sección Destacado en la página principal.

![Los iconos de colores que muestran las aplicaciones. Son cuadrados grandes de colores debajo de cada aplicación, donde el color se extrae del color principal del logotipo de la aplicación. La sección "Aplicaciones destacadas" aparece en la parte superior de la aplicación de portal de empresa.](./media/cp_win10_colorful_tiles_after_1708.png)



### <a name="see-also"></a>Vea también
* [Blog de Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guía básica de Cloud Platform](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novedades de Intune](https://docs.microsoft.com/intune/whats-new)
