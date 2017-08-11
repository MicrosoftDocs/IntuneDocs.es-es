---
title: "Edición anticipada"
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 8/3/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5861c999752bfef05b8a33161d0bf75a6d4daf59
ms.sourcegitcommit: 18cdbdc226f64368de892a8c5cff157c37986c57
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2017
---
# <a name="the-early-edition-for-microsoft-intune---august-2017"></a>La edición anticipada de Microsoft Intune: agosto de 2017

La **edición anticipada** proporciona una lista de características que se incluirán en las próximas versiones de Microsoft Intune. Esta información se proporciona conforme a una base limitada y está sujeta a cambios. No comparta esta información fuera de la compañía. Algunas de las características enumeradas aquí corren el riesgo de no cumplir las fechas límite y pueden retrasarse hasta una versión futura. Otras características se están probando en una prueba piloto (distribución de paquetes piloto) para asegurarse de que están preparadas para el cliente. Si tiene alguna pregunta o problema, póngase en contacto con su contacto del grupo de productos de Microsoft.

Esta página se actualiza periódicamente. Compruebe si hay actualizaciones adicionales.

> [!Note]
>Los siguientes cambios están en fase de desarrollo de Intune. Para más información sobre las nuevas características híbridas, vea nuestra [página sobre novedades de las implementaciones híbridas](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--

## What's coming to Intune on the Azure portal  
## What's coming to Intune apps
## Notices

-->



## <a name="intune-on-the-azure-portal"></a>Intune en el portal de Azure




### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>Nueva acción de dispositivo para forzar la sincronización de los dispositivos con Intune <!-- 711369 -->    
Se ha agregado una nueva acción de dispositivo que fuerza al dispositivo seleccionado a registrarse inmediatamente en Intune. Cuando un dispositivo se registra, recibe de inmediato las acciones o las directivas pendientes que se le han asignado.  Esta acción puede ayudarle a validar y a solucionar problemas de directivas que se le hayan asignado inmediatamente, sin tener que esperar al siguiente registro programado.

### <a name="actions-for-non-compliance----730266--"></a>Acciones en caso de incumplimiento <!--730266-->     
*Acciones en caso de incumplimiento* es una nueva característica de directivas de cumplimiento que le permite realizar acciones en dispositivos no compatibles. Puede especificar una o varias acciones y especificar el período de tiempo en el que se deben producir esas acciones. Por ejemplo, puede notificar a los usuarios de dispositivos no compatibles inmediatamente después de que el dispositivo se convierta en no compatible mediante el correo electrónico, o puede impedir que los dispositivos no compatibles tengan acceso a los recursos corporativos después de un período de gracia de 3 días mediante el acceso condicional.


### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version------1333256--1245463----"></a>Restricción de la inscripción de dispositivos Android e iOS por versión del SO <!--- 1333256,  1245463 --->  
Intune ya permite restringir la inscripción de Android e iOS por número de versión del sistema operativo. En **Intune** > **Restricciones de inscripción** > **Restricción de tipo de dispositivo** > **Predeterminado** > **Restricciones de la plataforma**, el administrador de TI puede establecer una configuración de plataforma para restringir la inscripción entre un valor del sistema operativo mínimo y máximo. Las versiones del sistema operativo Android se deben especificar como Principal.Secundario.Compilación.Revisión, donde Compilación y Revisión son opcionales. Las versiones de iOS deben especificarse como Principal.Secundario.Compilación, donde Compilación es opcional.

>[!NOTE]
>Esta configuración no restringe la inscripción a través de los programas de inscripción de Apple, que incluyen el Programa de inscripción de dispositivos de Apple y Apple School Manager, o Apple Configurator.

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment------1333272--1333275-1245709----"></a>Restricción de la inscripción de dispositivos de propiedad personal macOS, iOS y Android <!--- 1333272,  1333275, 1245709 --->
Intune ya admite la restricción de la inscripción de dispositivos de propiedad personal iOS, Android y macOS mediante los números de serie de los dispositivos. Algunos dispositivos no informan de los números de serie. Póngase en contacto con los fabricantes de los dispositivos para obtener detalles. Al cargar los números de serie en Intune, puede declarar los dispositivos como de propiedad corporativa. Con las restricciones de inscripción puede bloquear los dispositivos de propiedad personal (BYOD), lo que permitiría la inscripción de dispositivos de propiedad corporativa únicamente.

Para importar números de serie al portal de Intune, vaya a **Inscripción de dispositivos** > **Identificadores de dispositivo corporativos** y haga clic en **Agregar**; después, cargue un archivo .CSV. El archivo no debe contener encabezado, y debe tener dos columnas; una para el número de serie y otra para los detalles como los números IMEI.  Para restringir dispositivos de propiedad personal, vaya a **Inscripción de dispositivos** > **Restricciones de inscripción**. En **Restricciones de tipo de dispositivo**, seleccione **Predeterminado** y luego **Configuraciones de plataforma**. Puede **Permitir** o **Bloquear** dispositivos de propiedad personal iOS, Android y macOS. 

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>Forzar a dispositivos iOS supervisados a instalar automáticamente la última actualización de software disponible <!-- 777100 -->   
En el área de trabajo Actualizaciones de software habrá disponible una nueva directiva que permitirá forzar a los dispositivos iOS supervisados a instalar automáticamente la última actualización de software disponible. También se podrá ver un nuevo informe de los dispositivos iOS con versiones anteriores y un resumen de por qué están obsoletos.

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>Nuevo informe que muestra los dispositivos iOS con versiones anteriores de iOS <!-- 1352223 -->
El informe **Dispositivos iOS obsoletos** estará disponible desde el área de trabajo **Actualizaciones de software**. En el informe, puede ver una lista de dispositivos iOS supervisados destinados mediante una directiva de actualización iOS y que tienen actualizaciones disponibles. Para cada dispositivo, puede ver un estado por el que el dispositivo no se ha actualizado automáticamente. 

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices-----822899--1305423--"></a>Nueva configuración para permitir y bloquear aplicaciones en dispositivos Samsung KNOX Standard <!-- 822899,  1305423-->   
Se ha agregado una nueva [configuración de restricción de dispositivos](device-restrictions-android.md) que permite especificar las siguientes listas de aplicaciones:
  - Aplicaciones que los usuarios pueden instalar
  - Aplicaciones que los usuarios no pueden ejecutar
  - Aplicaciones ocultas para el usuario en el dispositivo  

Puede especificar la aplicación por dirección URL, nombre del paquete o desde la lista de aplicaciones que administra.

### <a name="new-settings-for-windows-10-device-restriction-profile"></a>Nueva configuración del perfil de restricción de dispositivos Windows 10
<!--- 978575, 1308849, 1308850 -->
Estamos agregando nuevas configuraciones al perfil de restricción de dispositivos Windows 10 en la categoría de SmartScreen de Windows Defender.

Para obtener información sobre el perfil de restricción de dispositivos Windows 10, vea [Configuración de restricciones de dispositivos Windows 10 y versiones posteriores]( device-restrictions-windows-10.md).

### <a name="new-device-restriction-settings-for-windows-10------1063965---"></a>Nueva configuración de restricciones de dispositivos para Windows 10 <!-- 1063965 -->
Estamos agregando nuevas configuraciones para el [perfil de restricción de dispositivos Windows 10](/intune/device-restrictions-windows-10) en las categorías siguientes:
- SmartScreen de Windows Defender
- Tienda de aplicaciones


### <a name="android-for-work-support-for-lookout----1087312---"></a>Compatibilidad de Android for Work con Lookout <!-- 1087312 -->   
El conector de Intune con Lookout admitirá dispositivos de Android for Work cuando se use la aplicación Lookout for Work. Puede implementar la aplicación Lookout dentro o fuera del contenedor.


### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Intune App Protection y Herramientas de desarrollo de Citrix MDX <!-- 709185 -->
Puede administrar dispositivos y aplicaciones con una combinación de Citrix XenMobile MDX y Microsoft Intune. Esto le permite administrar aplicaciones con la directiva de protección de aplicaciones de Intune mientras usa tecnología mVPN de Citrix.

Puede buscar un repositorio de código que contiene la herramienta de ajuste de aplicaciones de Intune e Intune App SDK para iOS y Android, que se integra con la tecnología mVPN de Citrix MDX.


### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium: nuevo socio de defensa contra amenazas móviles <!-- 954681 -->
Puede controlar el acceso desde dispositivos móviles a recursos corporativos mediante el acceso condicional basado en la evaluación de riesgos efectuada por Zimperium, una solución de defensa contra amenazas móviles integrada en Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Funcionamiento de la integración con Intune
El riesgo se evalúa según la telemetría recopilada de dispositivos con Zimperium. Se pueden configurar directivas de acceso condicional de EMS según la evaluación de riesgos de Zimperium habilitada mediante las directivas de cumplimiento de los dispositivos de Intune, que puede usar para permitir o bloquear el acceso de los dispositivos no compatibles a los recursos corporativos en función de las amenazas detectadas.

### <a name="new-azure-ad-conditional-access-policy-ui-link-from-intune-----1016201---"></a>Nuevo vínculo de interfaz de usuario de la directiva de acceso condicional de Azure AD desde Intune <!-- 1016201 -->
Los administradores de TI pueden establecer directivas condicionales basadas en aplicaciones mediante la nueva interfaz de usuario de directivas de acceso condicional en la carga de trabajo de Azure AD. Las directivas de acceso condicional basadas en aplicaciones que están en la sección de Intune App Protection en Azure permanecen allí por el momento y se aplican en paralelo. También existirá un vínculo cómodo a la nueva interfaz de usuario de la directiva de acceso condicional en Azure AD desde la carga de trabajo de Intune.


### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Compatibilidad de alta disponibilidad de On-premises Exchange Connector <!-- 676614 -->   
Puede tener varios roles de servidor de acceso de cliente (CAS) para el conector de Exchange local. Por ejemplo, si se produce un error en el CAS principal, Exchange Connector recibe una consulta para recurrir a otros CAS. Esta característica garantiza que no se interrumpa el servicio.

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Módulo de administración de System Center Operations Manager para Exchange Connector <!-- 885457 -->   
El módulo de administración de System Center Operations Manager para Exchange Connector está disponible para ayudarle a analizar los registros de Exchange Connector. Este módulo de administración le proporciona distintas maneras de supervisar Intune cuando tenga que resolver problemas.

### <a name="conditional-access-support-for-mac-devices-----720172---"></a>Compatibilidad de acceso condicional para dispositivos Mac <!-- 720172 -->   
Pronto se podrá establecer una directiva de acceso condicional que exija que los dispositivos Mac se inscriban en Intune y cumplan las directivas de cumplimiento de dispositivos. Por ejemplo, los usuarios pueden descargar la aplicación Portal de empresa de Intune para macOS e inscribir los dispositivos Mac en Intune. Intune evalúa si el dispositivo Mac es conforme o no con requisitos como el PIN, el cifrado, la versión del sistema operativo y la integridad del sistema.

### <a name="end-of-support-for-ios-80----1164477---"></a>Fin de la compatibilidad con iOS 8.0 <!---1164477--->
Las aplicaciones administradas y la aplicación Portal de empresa para iOS exigirán iOS 9.0 y versiones posteriores para acceder a recursos de empresa. Los dispositivos que no estén actualizados antes de septiembre de este año ya no podrán acceder a esas aplicaciones ni al Portal de empresa. En diciembre no podrán acceder a la totalidad de los recursos de empresa, incluido el correo electrónico. 

### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>Fin de la compatibilidad con Android 4.3 y anterior <!---1171127, 1326920 --->
Las aplicaciones administradas y la aplicación Portal de empresa para Android exigirán Android 4.4 y versiones posteriores para acceder a recursos de empresa. Los dispositivos que no estén actualizados antes del comienzo de octubre ya no podrán acceder a esas aplicaciones ni al Portal de empresa. En diciembre, todos los dispositivos inscritos serán eliminados, lo que provocará su pérdida de acceso a los recursos de empresa. Si está usando directivas de protección de aplicaciones sin MDM, las aplicaciones no recibirán actualizaciones y la calidad de su experiencia empeorará con el tiempo.


### <a name="platform-support-reminder-windows-phone-81-mainstream-support-will-end-july-11-2017----1327781---"></a>Recordatorio de compatibilidad de plataforma: la compatibilidad estándar de Windows Phone 8.1 finalizará el 11 de julio de 2017 <!-- 1327781 -->  
El 11 de julio de 2017 terminará la compatibilidad estándar de la plataforma Windows Phone 8.1. La compatibilidad de los equipos Windows 8.1 no se verá afectada.

No hay ningún impacto inmediato en ningún dispositivo Windows Phone 8.1 administrado por el servicio Intune. Los dispositivos inscritos siguen funcionando y todas las directivas, configuraciones y aplicaciones seguirán funcionando según lo previsto. Tenga en cuenta que no hay mejoras destinadas a la plataforma Windows Phone 8.1 en el servicio Intune ni para la aplicación Portal de empresa de Windows Phone 8.1.

Se recomienda actualizar los dispositivos Windows Phone 8.1 aptos a Windows 10 Mobile en cuanto se pueda. 




## <a name="intune-apps"></a>Aplicaciones de Intune

### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Modos claro y oscuro disponibles para la aplicación Portal de empresa para Windows 10 <!---676547--->
Los usuarios finales podrán personalizar el modo de color de la aplicación Portal de empresa para Windows 10. El usuario puede realizar el cambio en la sección Configuración de la aplicación Portal de empresa. El cambio aparecerá una vez que el usuario haya reiniciado la aplicación. En Windows 10 versión 1607 y posteriores, el valor predeterminado del modo de la aplicación es la configuración del sistema. En los equipos de escritorio con Windows 10 versión 1511 y anteriores, el valor predeterminado del modo de la aplicación es el claro.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>Permitir que los usuarios finales accedan a la aplicación Portal de empresa para Android sin inscripción <!---1169910--->  
Pronto los usuarios finales no tendrán que inscribir sus dispositivos para acceder a la aplicación Portal de empresa para Android. Los usuarios finales de las organizaciones que usen directivas de protección de aplicaciones dejarán de recibir mensajes para inscribir sus dispositivos cuando abran la aplicación Portal de empresa. Los usuarios finales también podrán instalar aplicaciones desde el Portal de empresa sin inscribir el dispositivo. 

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Mensaje de error mejorado cuando un usuario alcanza el número máximo de dispositivos permitidos para la inscripción <!-- 1270370 -->
En lugar de un mensaje de error genérico, los usuarios finales ven un mensaje de error descriptivo que requiere acción: "Ya ha inscrito el máximo número de dispositivos permitidos por su administrador de TI. Quite un dispositivo inscrito o reciba ayuda de su administrador de TI".

### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Nueva experiencia de sesión iniciada para los usuarios del portal de empresa de Android y para los usuarios de la directiva de protección de aplicaciones <!-- 621669 -->
Los usuarios finales podrán examinar aplicaciones, administrar dispositivos y ver la información de contacto de TI con la aplicación del portal de empresa de Android sin inscribir sus dispositivos Android. Además, si un usuario final ya usa una aplicación protegida mediante las directivas de protección de aplicaciones de Intune e inicia el portal de empresa de Android, el usuario final ya no recibirá una solicitud para inscribir el dispositivo. 

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>Informar a los usuarios finales de la información de dispositivo que puede verse para iOS <!--739894-->
Estamos agregando **Tipo de propiedad** a la pantalla Detalles del dispositivo en la aplicación del portal de empresa para iOS. Esto permite a los usuarios obtener más información sobre privacidad directamente desde esta página de los documentos de usuario final de Intune. También podrán encontrar esta información en la pantalla Acerca de.

### <a name="apps-details-pages-display-new-information-for-android-devices---1287476--"></a>Las páginas de información de aplicaciones muestran información nueva para los dispositivos Android <!--1287476-->
La página de información de aplicaciones de la aplicación de portal de empresa para Android mostrará las categorías de aplicaciones que el administrador de TI ha definido para esa aplicación.

### <a name="intune-mobile-application-management-mam-dialog-boxes-now-have-a-modern-interface----1199015---"></a>Ahora los cuadros de diálogo de administración de aplicaciones móviles (MAM) de Intune tienen una interfaz moderna <!-- 1199015 -->
Se han actualizado los cuadros de diálogo de administración de aplicaciones móviles (MAM) de Intune para tener una apariencia moderna. Los cuadros de diálogo funcionan de la misma manera que con el estilo anterior.

En los dispositivos Android modernos, los cuadros de diálogo de notificación o error que muestra Intune ahora tendrán una apariencia actualizada.

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Nueva configuración de la aplicación de portal de empresa para Android para alternar la optimización de la batería <!--1405990-->
La página **Configuración** de la aplicación de portal de empresa para Android tendrá una nueva opción que permite a los usuarios desactivar fácilmente la optimización de la batería para las aplicaciones de portal de empresa y Microsoft Authenticator. El nombre de la aplicación que se muestra en la configuración varía dependiendo de qué aplicación administre la cuenta profesional. Recomendamos que los usuarios desactiven la optimización de la batería para obtener un rendimiento mejor de las aplicaciones de trabajo que sincronizan el correo electrónico y los datos. 




## <a name="notices"></a>Notificaciones

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple requerirá actualizaciones para la Seguridad de transporte de aplicaciones <!--748318-->   
Apple ha anunciado que, a partir de la primavera de 2017, se aplicarán requisitos específicos para la Seguridad de transporte de aplicaciones (ATS). ATS se usa para aplicar una seguridad más estricta en todas las comunicaciones de aplicaciones a través de HTTPS. Este cambio afecta a los clientes de Intune que usan aplicaciones del portal de empresa de iOS. Visite nuestro [blog de soporte técnico de Intune](https://aka.ms/compportalats) para obtener más información.

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acceso directo a los escenarios de inscripción de Apple <!--951869-->   
Para las cuentas de Intune creadas después de enero de 2017, Intune ha habilitado el acceso directo a los escenarios de inscripción de Apple mediante la carga de trabajo de inscripción de dispositivos en el portal de vista previa de Azure. Anteriormente, la vista previa de inscripción de Apple solo era accesible desde los vínculos al portal clásico de Intune. Las cuentas de Intune creadas antes de enero de 2017 requerirán una migración única antes de que estas características estén disponibles en Azure. Aún no se ha anunciado la programación para la migración, pero la información estará disponible tan pronto como sea posible. Se recomienda encarecidamente crear una cuenta de prueba para probar la nueva experiencia si su cuenta no tiene acceso a la versión preliminar.

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>Plan de cambio: Intune está cambiando la experiencia del portal Partner de Intune<!-- 1050016 -->
Estamos quitando la página Partner de Intune de manage.microsoft.com a partir de la actualización de servicio de mediados de mayo de 2017.  

Si es un administrador de partners, ya no podrá ver y realizar acciones en nombre de sus clientes desde la página Partner de Intune pero, en su lugar, tendrá que iniciar sesión en uno de los dos portales de partners de Microsoft.

Tanto el [Centro de partners de Microsoft](https://partnercenter.microsoft.com/) como el [Centro de administración de partners de Microsoft Office 365](https://portal.office.com/) le permitirá iniciar sesión en las cuentas de cliente que administra. En adelante, como partner, use uno de estos sitios para administrar a sus clientes.



### <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.
