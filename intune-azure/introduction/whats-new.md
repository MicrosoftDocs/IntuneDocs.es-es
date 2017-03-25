---
title: "Novedades de la versión preliminar de Microsoft Intune"
titleSuffix: Intune Azure preview
description: "Descubra las novedades de la versión preliminar de Intune Azure"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: deea78dcea9ade031441bf12b388a862235a8e9c
ms.openlocfilehash: 92bb81440b9374b2b0b433b32fc0a1301998ea80
ms.lasthandoff: 03/15/2017

---

# <a name="whats-new-in-the-microsoft-intune-preview"></a>Novedades de la versión preliminar de Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

A medida que avance la versión preliminar pública y se agreguen más características, proporcionaremos información sobre ellas aquí.

> [!Note]
> Estamos implementando los cambios incluidos en esta página para la versión preliminar de Azure Portal. Sin embargo, pueden que los cambios no estén disponibles inmediatamente debido a la forma en que se ha actualizado el servicio de Intune.  Varios componentes del servicio deben actualizarse de manera secuencial antes de que estén disponibles las nuevas características del Portal. Busque estos cambios cuando se implementen este mes.

## <a name="march-2017"></a>Marzo de 2017

### <a name="support-for-ios-lost-mode---431695--"></a>Compatibilidad con Modo Perdido de iOS <!--431695-->

En iOS 9.3 y dispositivos posteriores, Intune agrega compatibilidad con **Modo Perdido**. Ahora puede bloquear un dispositivo para evitar su uso, así como mostrar un mensaje y llamar al número de teléfono de la pantalla de bloqueo del dispositivo.

El usuario final no podrá desbloquear el dispositivo hasta que un administrador deshabilite Modo Perdido. Cuando está habilitado Modo Perdido, puede usar la acción Buscar dispositivo para mostrar la ubicación geográfica del dispositivo en un mapa con la consola de Intune.

Para obtener más información, consulte [¿Qué es la administración de dispositivos de Microsoft Intune?](/intune-azure/manage-devices/what-is)

### <a name="improvements-to-device-actions-report---677150--"></a>Mejoras en los informes de las acciones del dispositivo <!--677150-->

Hemos realizado mejoras en el informe de las acciones del dispositivo para mejorar el rendimiento. Además, ahora puede filtrar el informe por estado. Por ejemplo, puede filtrar el informe para mostrar únicamente las acciones de dispositivo que se han completado".

### <a name="actions-for-non-compliance---730266--"></a>Acciones en caso de incumplimiento <!--730266-->

**Acciones en caso de incumplimiento** es una nueva característica de directivas de cumplimiento que le permite realizar acciones en dispositivos no compatibles. Puede especificar una o varias acciones y especificar el período de tiempo en el que se deben producir esas acciones. Por ejemplo, puede notificar a los usuarios de dispositivos no compatibles inmediatamente después de que el dispositivo se convierta en no compatible mediante el correo electrónico, o puede impedir que los dispositivos no compatibles tengan acceso a los recursos corporativos después de un período de gracia de 3 días mediante el acceso condicional.

### <a name="custom-app-categories---748805--"></a>Categorías de aplicaciones personalizadas <!--748805-->

Ahora puede crear, editar y asignar categorías a las aplicaciones que agregue a Intune. En estos momentos, las categorías solo pueden especificarse en inglés.
Consulte [How to add an app to Intune](/intune-azure/manage-apps/add-apps) (Cómo agregar una aplicación a Intune).

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>Asignación de aplicaciones LOB a los usuarios con dispositivos no inscritos <!--748823-->

Ahora puede asignar aplicaciones de línea de negocio desde la tienda a usuarios tengan o no inscritos sus dispositivos con Intune. Si el dispositivo de los usuarios no está inscrito con Intune, deben ir al sitio web del Portal de empresa para instalarlo, en lugar de a la aplicación del Portal de empresa.

### <a name="new-compliance-reports---846671--"></a>Nuevos informes de cumplimiento <!--846671-->

Ahora dispone de informes de cumplimiento que proporcionan la posición de cumplimiento de los dispositivos de su empresa y le permiten solucionar rápidamente los problemas relacionados con el cumplimiento detectados por los usuarios. Puede ver información acerca de

- Estado de cumplimiento general de los dispositivos
- Estado de cumplimiento de una configuración individual
- Estado de cumplimiento de una directiva individual

También puede utilizar estos informes para profundizar en un dispositivo individual para ver la configuración específica y las directivas que afectan a dicho dispositivo.

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acceso directo a los escenarios de inscripción de Apple <!--951869-->

Para las cuentas de Intune creadas después de enero de 2017, Intune ha habilitado el acceso directo a los escenarios de inscripción de Apple mediante la carga de trabajo de inscripción de dispositivos en el portal de vista previa de Azure. Anteriormente, la vista previa de inscripción de Apple solo era accesible desde los vínculos al portal clásico de Intune. Las cuentas de Intune creadas antes de enero de 2017 requerirán una migración única antes de que estas características estén disponibles en Azure. Aún no se ha anunciado la programación para la migración, pero la información estará disponible tan pronto como sea posible. Se recomienda encarecidamente crear una cuenta de prueba para probar la nueva experiencia si su cuenta no tiene acceso a la versión preliminar.


## <a name="february-2017"></a>Febrero de 2017

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>Capacidad para restringir la inscripción de dispositivos móviles <!--747600, 795782-->
Intune está agregando nuevas restricciones de inscripción que controlan qué plataformas de dispositivos móviles pueden inscribir. Intune separa las plataformas de dispositivos móviles como iOS, Mac OS, Android, Windows y Windows Mobile.

* La restricción la inscripción de dispositivos móviles no restringe la inscripción del cliente de PC.  
* Solo para iOS y Android, hay una opción adicional para bloquear la inscripción de dispositivos de propiedad personal.

Intune marca todos los dispositivos nuevos como personal a menos que el administrador de TI tome la medida de marcarlos como propiedad de la empresa, como se explica en [este artículo](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices).

### <a name="view-all-actions-on-managed-devices---677150--"></a>Ver todas las acciones en los dispositivos administrados <!--677150-->
Un nuevo informe __Acciones de dispositivo__ muestra quién ha realizado acciones remotas como el restablecimiento de fábrica en dispositivos y, además, muestra el estado de esa acción. Vea [¿Qué es la administración de dispositivos?](https://docs.microsoft.com/intune-azure/manage-devices/what-is).

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Los dispositivos no administrados puedan acceder a aplicaciones asignadas <!--664691-->
Como parte de los cambios de diseño en el sitio web del portal de empresa, los usuarios de iOS y Android podrán instalar aplicaciones asignadas a ellos como "disponibles sin inscripción" en sus dispositivos no administrados. Con sus credenciales de Intune, los usuarios podrán iniciar sesión en el sitio web del portal de empresa y ver la lista de aplicaciones asignadas. Los paquetes de aplicación de las aplicaciones "disponibles sin inscripción" se encuentran disponibles para descargar a través del sitio web del portal de empresa. Las aplicaciones que requieren la inscripción para la instalación no se ven afectadas por este cambio, ya que se les pedirá a los usuarios que inscriban su dispositivo si quieren instalar esas aplicaciones.

### <a name="custom-app-categories---748805--"></a>Categorías de aplicaciones personalizadas <!--748805-->
Ahora puede crear, editar y asignar categorías a las aplicaciones que agregue a Intune. En estos momentos, las categorías solo pueden especificarse en inglés.
Consulte [How to add an app to Intune](/intune-azure/manage-apps/add-apps) (Cómo agregar una aplicación a Intune).

### <a name="display-device-categories---814654--"></a>Mostrar categorías de dispositivos <!--814654-->
Ahora puede ver la categoría del dispositivo como una columna en la lista de dispositivos. También puede editar la categoría desde la sección de propiedades de la hoja de propiedades del dispositivo. Consulte [How to add an app to Intune](/intune-azure/manage-apps/add-apps) (Cómo agregar una aplicación a Intune).

### <a name="configure-windows-update-for-business-settings---776716--"></a>Configuración de Windows Update para empresas <!--776716-->

Windows como servicio es la nueva forma de proporcionar actualizaciones para Windows 10. A partir de Windows 10, todas las nuevas actualizaciones de calidad y características contienen las actualizaciones anteriores. Es decir, siempre que haya instalado la más reciente, sabrá que sus dispositivos Windows 10 están completamente actualizados. A diferencia de las versiones anteriores de Windows, ahora debe instalar la actualización completa en lugar de una parte.

Gracias a Windows Update para empresas, puede simplificar la administración de actualizaciones, ya que no tendrá que aprobar actualizaciones individuales para grupos de dispositivos. Todavía puede administrar los riesgos en sus entornos configurando una estrategia de implementación de actualizaciones; Windows Update se asegurará de que las actualizaciones se instalen en el momento oportuno. Microsoft Intune ofrece la posibilidad de configurar las actualizaciones en los dispositivos y de aplazar su instalación. Intune no almacena las actualizaciones, sino únicamente la asignación de las directivas de actualización. Los dispositivos acceden a Windows Update directamente para instalar las actualizaciones. Use Intune para configurar y administrar los **anillos de actualización de Windows 10**. Un anillo de actualización contiene un grupo de opciones que configuran cuándo y cómo se instalan las actualizaciones de Windows 10. Para obtener más información, consulte [Configuración de Windows Update para empresas](/intune-azure/configure-devices/how-to-configure-windows-update-for-business).

## <a name="january-2017"></a>Enero de 2017

### <a name="assign-line-of-business-apps-whether-or-not-devices-are-enrolled---748823--"></a>Asignar aplicaciones de línea de negocio en dispositivos inscritos y no inscritos <!--748823-->
Ahora puede asignar aplicaciones de línea de negocio desde la tienda a usuarios tengan o no inscritos sus dispositivos con Intune. Si el dispositivo de los usuarios no está inscrito con Intune, deben ir al sitio web del portal de empresa para instalarlo, en lugar de a la aplicación de portal de empresa. [¿Qué es la administración de aplicaciones?](/intune-azure/manage-apps/what-is-app-management)

### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them"></a>Resolver el problema en el que los dispositivos iOS están inactivos o la consola de administración no puede comunicarse con ellos
Cuando los dispositivos de los usuarios pierden el contacto con Intune, puede proporcionarles nuevos pasos de solución de problemas para ayudarles a volver a obtener acceso a los recursos de la empresa. Vea [Los dispositivos están inactivos o la consola de administración no puede comunicarse con ellos](/intune-azure/enroll-devices/troubleshoot-device-enrollment#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them).

## <a name="december-2016-initial-release"></a>Diciembre de 2016 (versión inicial)

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Integración de la administración de gastos de telecomunicaciones en la versión preliminar pública del portal de Azure<!--747605-->
Ahora estamos comenzando a realizar la integración de la versión preliminar con los servicios de administración de gastos de telecomunicaciones (TEM) dentro del portal de Azure. Puede usar Intune para exigir límites sobre el uso de datos nacionales y móviles. Comenzaremos estas integraciones con [Saaswedo](http://www.saaswedo.com). Para habilitar esta característica en su inquilino de prueba, [póngase en contacto con el soporte técnico de Microsoft](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

- Implementación y administración de aplicaciones de la tienda en dispositivos iOS, Android y Windows
- Implementación y administración de aplicaciones de línea de negocio (LOB) en dispositivos iOS, Android y Windows
- Implementación y administración de aplicaciones compradas por volumen en dispositivos iOS y Windows
- Implementación y administración de aplicaciones web para dispositivos Android, iOS y Windows
- Perfiles de configuración de aplicaciones administrados por iOS
- Configuración de directivas de protección de aplicaciones e implementación de aplicaciones de línea de negocio en dispositivos no inscritos en Intune
- Perfiles de VPN, VPN por aplicación, Wi-Fi, correo electrónico y perfiles de certificado
- Directivas de cumplimiento
- Acceso condicional para Azure AD
- Acceso condicional para Exchange local
- Inscripción de dispositivos
- Control de acceso basado en roles

## <a name="deprecated-features-in-the-azure-portal"></a>Características en desuso en el portal de Azure

### <a name="support-for-row-by-row-review-of-hardware-identifiers"></a>Compatibilidad con la revisión fila a fila de identificadores de hardware
El portal de Azure no admite la revisión fila a fila de identificadores de hardware para números IMEI y números de serie de Apple. En la consola de Intune clásica, puede importar detalles de un archivo de valores separados por comas (.csv) y sobrescribir los detalles existentes para identificadores de hardware individuales. El portal de Azure presenta una única opción optimizada que sobrescribe automáticamente los detalles de todos los identificadores de hardware u omite nuevos detalles de identificadores existentes.

#### <a name="how-this-affects-you"></a>Cómo afecta esto
En el portal de Azure, no podrá decidir, fila a fila, qué dispositivos de identidad de equipo móvil internacional (IMEI) se actualizarán. La consola de Intune clásica seguirá admitiendo esta funcionalidad.

#### <a name="how-to-get-ready-for-this-change"></a>Cómo prepararse para este cambio
Vamos a proporcionar esta información de antemano; así, en caso de que le afecte, pueda informar a sus administradores de soporte técnico de este cambio. Este cambio coincidirá con el paso al portal de Azure, previsto para la primera mitad de 2017.


### <a name="support-for-default-corporate-device-enrollment-profiles-in-apple-dep"></a>Compatibilidad con perfiles de Inscripción de dispositivos corporativos en DEP de Apple
El portal de Azure no admite el perfil de inscripción de dispositivos corporativos "predeterminado" para los números de serie de dispositivo del Programa de inscripción de dispositivos de Apple (DEP). Esta funcionalidad, disponible en la consola de Intune clásica, está en desuso para evitar que se asignen perfiles involuntariamente. En el portal de Azure, los números de serie sincronizados desde una cuenta de DEP de Apple inicialmente no tendrán asignado ningún perfil de inscripción de dispositivos corporativos.

#### <a name="how-this-affects-you"></a>Cómo afecta esto
En el portal de Azure, no podrá establecer una directiva de perfil predeterminada en todos los dispositivos Apple. La consola de Intune clásica seguirá admitiendo esta funcionalidad.

#### <a name="how-to-get-ready-for-this-change"></a>Cómo prepararse para este cambio
Vamos a proporcionar esta información de antemano; así, en caso de que le afecte, pueda informar a sus administradores de soporte técnico de este cambio. Este cambio coincidirá con el movimiento al portal de Azure, previsto para la primera mitad de 2017.

