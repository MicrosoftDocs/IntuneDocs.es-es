---
title: "La edición anticipada | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 12/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 18d47678b0fbdbd98502f2d3b469b202b567b2e7
ms.openlocfilehash: 3c7edc236878232c6f4c0ae993733c967946e765


---

# <a name="the-early-edition-for-microsoft-intune---january"></a>La edición anticipada de Microsoft Intune: enero

La **edición anticipada** proporciona una lista de características que se incluirán en las próximas versiones de Microsoft Intune. Esta información se proporciona conforme al NDA en una base extremadamente limitada y está vinculada a cambios. Algunas de las características enumeradas aquí corren el riesgo de no cumplir las fechas límite y pueden retrasarse hasta una versión futura. Otras características se están probando en una prueba piloto (distribución de paquetes piloto) para asegurarse de que están preparadas para el cliente. Póngase en contacto con su persona conocida de Intune/PM si tiene alguna pregunta o problema.

Esta página se actualiza periódicamente. Compruebe si hay actualizaciones adicionales.

> [!Note]
> Los siguientes cambios están en fase de desarrollo de Intune. Todas estas características finalmente se admitirán para las implementaciones de clientes híbridos (Configuration Manager con Intune). Para más información sobre las nuevas características híbridas, vea nuestra [página sobre novedades de las implementaciones híbridas](https://docs.microsoft.com/en-us/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nuevas funcionalidades

### <a name="actions-for-non-compliance---730266--"></a>Acciones en caso de incumplimiento <!--730266-->
_Acciones en caso de incumplimiento_ es una nueva característica de directivas de cumplimiento que le permite realizar acciones en dispositivos no compatibles. Puede especificar una o varias acciones y especificar el período de tiempo en el que se deben producir esas acciones. Por ejemplo, puede notificar a los usuarios de dispositivos no compatibles inmediatamente después de que el dispositivo se convierta en no compatible mediante el correo electrónico, o puede impedir que los dispositivos no compatibles tengan acceso a los recursos corporativos después de un período de gracia de 3 días mediante el acceso condicional.

### <a name="in-console-reports-for-mam-without-enrollment---677961--"></a>Informes en la consola para MAM sin inscripción <!--677961-->
Se han agregado nuevos informes de protección de aplicaciones para los dispositivos inscritos y no inscritos. Obtenga más información sobre cómo puede [supervisar directivas de administración de aplicaciones móviles con Microsoft Intune aquí](https://docs.microsoft.com/en-us/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune).

### <a name="conditional-access-for-mam-with-sharepoint-online---679339--"></a>Acceso condicional para MAM con SharePoint Online<!--679339-->
Puede impedir que las aplicaciones que no son compatibles con las directivas de administración de aplicaciones móviles (MAM) de Intune accedan a SharePoint Online.  Puede comenzar a usar la administración de aplicaciones móviles de Intune mediante el portal de Azure. Busque la sección __Acceso condicional__ en la hoja __Configuración__ que incluirá la opción para SharePoint Online. Esta característica se distribuirá aparte del resto de la versión del servicio. <!--Find out more about this new feature [here](https://docs.microsoft.com/intune/deploy-use/mam-ca-for-sharepoint-online).-->

### <a name="android-711-support---694397--"></a>Compatibilidad con Android 7.1.1 <!--694397-->
Ahora, Intune admite y administra completamente Android 7.1.1.

## <a name="notices"></a>Notificaciones

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Restablecer la administración de dispositivos de escritorio Windows predeterminada mediante la configuración de Windows <!--663050-->
El comportamiento predeterminado para inscribir equipos de escritorio de Windows 10 está cambiando. Las nuevas inscripciones seguirán el típico flujo de inscripción del agente MDM en lugar del agente de PC.

El sitio web de portal de empresa proporcionará a los usuarios de escritorio de Windows 10 las instrucciones de inscripción que les guiarán a través del proceso de agregar equipos de escritorio de Windows 10 como dispositivos móviles. Esto no afectará a los PC inscritos en estos momentos, y su organización todavía puede administrar equipos de escritorio de Windows 10 con el agente de PC [si lo prefiere](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune).

### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>Los vínculos de portal de empresa para iOS se abren dentro de la aplicación <!--665954-->
Los vínculos dentro de la aplicación de portal de empresa para iOS, incluidos los de documentación y aplicaciones, se abrirán directamente en la aplicación de portal de empresa con una vista desde la aplicación de Safari. Esta actualización se enviará por separado desde la actualización del servicio en enero.

### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Mejorar la asistencia de la administración de aplicaciones móviles para el borrado selectivo <!--581242-->
A los usuarios finales se les proporcionarán instrucciones adicionales sobre cómo recuperar el acceso a los datos profesionales o educativos si estos se quitaron automáticamente debido a la directiva "Intervalo sin conexión antes de que se borren los datos de la aplicación".<!--, or the removal of the Intune Company Portal on Android.-->

### <a name="new-documentation-for-app-protection-policies---583398--"></a>Nueva documentación para las directivas de protección de aplicaciones <!--583398-->
Hemos actualizado nuestra documentación para administradores y desarrolladores de aplicaciones que quieran habilitar directivas de protección de aplicaciones (conocidas como directivas de MAM) en sus aplicaciones iOS y Android con la herramienta de ajuste de aplicaciones de Intune o con el SDK para aplicaciones de Intune.

Se han actualizado los siguientes artículos:

* [Decidir cómo preparar las aplicaciones para la administración de aplicaciones móviles mediante Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)
* [Preparar aplicaciones iOS para la administración de aplicaciones móviles con la Herramienta de ajuste de aplicaciones de Intune](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)
* [Introducción al SDK para aplicaciones de Microsoft Intune](https://docs.microsoft.com/intune/develop/intune-app-sdk-get-started)
* [Guía para desarrolladores sobre el SDK de aplicaciones de Intune para iOS](https://docs.microsoft.com/intune/develop/intune-app-sdk-ios)

Se han agregado los siguientes artículos nuevos a la biblioteca de documentos:

* [Complemento Cordova del SDK para aplicaciones de Intune](https://docs.microsoft.com/intune/develop/intune-app-sdk-cordova)
* [Componente Xamarin del SDK para aplicaciones de Intune](https://docs.microsoft.com/intune/develop/intune-app-sdk-xamarin)

### <a name="progress-bar-when-launching-the-company-portal-on-ios---665978--"></a>Barra de progreso cuando se inicia el portal de empresa en iOS <!--665978-->
El portal de empresa para iOS presenta una barra de progreso en la pantalla de inicio para proporcionar información al usuario sobre los procesos de carga que se producen. Habrá una implementación por fases de la barra de progreso para reemplazar el control de número. Esto significa que algunos usuarios verán la nueva barra de progreso y otros seguirán viendo el control de número.

## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Versión preliminar pública de la nueva experiencia de administración de Intune en Azure <!--736542-->

A principios de 2017 migraremos nuestra experiencia de administración completa a Azure, lo que permitirá una administración eficaz e integrada de los flujos de trabajo principales de EMS en una moderna plataforma de servicios que es extensible mediante las API Graph.

Nuevos inquilinos de prueba comenzarán a ver la versión preliminar pública de la nueva experiencia de administración en el portal de Azure de este mes. Durante el estado de versión preliminar, se proporcionarán funcionalidades y paridad con la consola de Intune existente de manera iterativa.

La experiencia de administración del portal de Azure usará la nueva funcionalidad de agrupación y selección de destino ya anunciada; cuando se migre su inquilino existente a la nueva experiencia de agrupación también se migrará a la versión preliminar la nueva experiencia de administración en el inquilino. Mientras tanto, si quiere probar o examinar alguna de las nuevas características hasta que se migre su inquilino, regístrese para obtener una nueva cuenta de prueba de Intune o revise la [nueva documentación](https://docs.microsoft.com/en-us/intune-azure/introduction/what-is-microsoft-intune).

Si tiene alguna pregunta sobre la programación de la migración de su inquilino, póngase en contacto con nuestro equipo de migración en [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

### <a name="january-2017"></a>Enero de 2017

#### <a name="custom-app-categories---748805--"></a>Categorías de aplicaciones personalizadas <!--748805-->
Ahora puede crear, editar y asignar categorías a las aplicaciones que agregue a Intune. En estos momentos, las categorías solo pueden especificarse en inglés.

#### <a name="assign-line-of-business-apps-whether-or-not-devices-are-enrolled---748803--"></a>Asignar aplicaciones de línea de negocio en dispositivos inscritos y no inscritos <!--748803-->
Ahora puede asignar aplicaciones de línea de negocio desde la tienda a usuarios tengan o no inscritos sus dispositivos con Intune. Si el dispositivo de los usuarios no está inscrito con Intune, deben ir al sitio web del portal de empresa para instalarlo, en lugar de a la aplicación de portal de empresa.

### <a name="december-2016"></a>Diciembre de 2016

#### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Integración de la administración de gastos de telecomunicaciones en la versión preliminar pública del portal de Azure<!--747605-->
Ahora estamos comenzando a realizar la integración de la versión preliminar con los servicios de administración de gastos de telecomunicaciones (TEM) dentro del portal de Azure. Puede usar Intune para exigir límites sobre el uso de datos nacionales y móviles. Comenzaremos estas integraciones con [Saaswedo](http://www.saaswedo.com). Para habilitar esta característica en su inquilino de prueba, [póngase en contacto con el soporte técnico de Microsoft](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

### <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new-in-microsoft-intune.md) para obtener más información sobre los desarrollos recientes.



<!--HONumber=Dec16_HO4-->


