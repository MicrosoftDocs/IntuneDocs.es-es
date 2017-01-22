---
title: Glosario de Intune | Microsoft Docs
description: "Obtenga información sobre la terminología de Microsoft Intune"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/17/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 86d00901-fac7-4471-aac2-f1d13a4879b6
translationtype: Human Translation
ms.sourcegitcommit: f268cf29461447306d0f5c3ca06d541d9a03a49d
ms.openlocfilehash: b9a51cb2123bc9b6e73c0bf72ef5393252e8d37d


---

# <a name="microsoft-intune-glossary"></a>Glosario de Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="a"></a>A

|||
|-|-|
|SDK para aplicaciones|El [SDK de aplicaciones de Microsoft Intune](/intune/develop/intune-app-sdk) permite agregar funcionalidad a las aplicaciones escritas internamente que permite administrarlas mediante directivas de administración de aplicaciones móviles de Intune.|
|Herramienta de ajuste de aplicaciones|[Aplicación de línea de comandos](/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune) que crea un contenedor en torno a una aplicación de línea de negocios, que permite administrarla mediante una directiva de administración de aplicaciones móviles de Intune.|
|Instalación disponible|Cuando se implementa una aplicación con esta acción, aparece en el portal de empresa y los usuarios pueden [solicitar instalarla](/intune/deploy-use/deploy-apps).|
|Portal de Azure|Nueva consola de Intune que se presentará próximamente. En este momento, puede usar Azure Portal para crear [directivas de MAM de Intune](/intune/deploy-use/azure-portal-for-microsoft-intune-mam-policies) para dispositivos.|

## <a name="b"></a>B
|||
|-|-|
|BYOD|[Bring Your Own Device](/intune/get-started/choose-how-to-enroll-devices1). Los usuarios pueden instalar la aplicación de portal de empresa de Intune en sus dispositivos y, luego, inscribirlos para acceder a recursos de la empresa, como el correo electrónico, aplicaciones de empresa, datos de la compañía y soporte técnico.|

## <a name="c"></a>C
|||
|-|-|
|Perfil de certificado|Use este tipo de directiva para [proteger el acceso a los recursos corporativos](/intune/deploy-use/secure-resource-access-with-certificate-profiles) con certificados cuando se usan perfiles de Wi-Fi, correo electrónico o VPN.|
|Espacio de almacenamiento en nube|Lugar donde [se almacenan](/intune/deploy-use/add-apps#cloud-storage-space) las aplicaciones o los datos sobre las aplicaciones creadas.|
|Contra reembolso|Los [dispositivos propiedad de la empresa](/intune/get-started/choose-how-to-enroll-devices1) se pueden inscribir de diversas formas, según cuáles sean las necesidades de la organización y los tipos de dispositivos administrados.|
|Portal de empresa|Aplicación o sitio web que proporciona a los usuarios [acceso a aplicaciones y datos de la empresa](/intune/get-started/microsoft-intune-company-portal).|
|Directiva de cumplimiento|Garantiza que los dispositivos usados para acceder a las aplicaciones y a los datos de la empresa [cumplan ciertas reglas](/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune), como el uso de un PIN para acceder al dispositivo y el cifrado de los datos almacenados en el dispositivo.|
|Aplicaciones conformes y no conformes|Estos valores, que forman parte de una [directiva de configuración general](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies), permiten definir una lista de las aplicaciones que los usuarios pueden ejecutar o no. Después, Intune informará a través de informes si se instala o se ejecuta una aplicación no conforme. En el caso de algunas plataformas, Intune también puede bloquear la instalación de una aplicación no conforme.|
|Acceso condicional|[Permite el acceso al correo electrónico de la empresa, Office 365 y otros servicios](/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune) solo desde dispositivos conformes con las reglas establecidas.|
|Directiva personalizada|[Use estas directivas](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) cuando una directiva de configuración general no tiene una configuración integrada que satisfaga sus necesidades. Puede usar una directiva personalizada para crear una configuración usando otros medios, como OMA-URI o Apple Configurator.|

## <a name="d"></a>D
|||
|-|-|
|Implementación|Acto de enviar una aplicación o una directiva a un dispositivo o un usuario que usted administra.|
|Acción de implementación|Opción que se elige al [implementar una aplicación](/intune/deploy-use/deploy-apps-in-microsoft-intune). Puede decidir que la instalación de la aplicación sea obligatoria, opcional o puede desinstalar la aplicación.|
|Administrador de inscripción de dispositivos|Las organizaciones pueden usar Intune para administrar un gran número de dispositivos móviles con una sola cuenta de usuario. La cuenta del [administrador de inscripción de dispositivos (DEM)](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) es una cuenta especial de Intune con permisos para inscribir hasta 1000 dispositivos.|
|Asignación de grupos de dispositivos|Ayuda a [agregar automáticamente dispositivos a grupos](/intune/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune) en función de una categoría de dispositivo (por ejemplo, "Personal" o "Ventas") que usted o el usuario final pueden asignar al dispositivo.|

## <a name="e"></a>E
|||
|-|-|
|Perfil de correo electrónico|Esta directiva se puede usar para configurar las [opciones de acceso a correo electrónico](/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune) para clientes de correo electrónico específicos en dispositivos móviles reduciendo al mínimo la configuración que debe llevar a cabo el usuario final.|
|EMS|Microsoft Enterprise Mobility + Security (anteriormente Enterprise Mobility Suite) protege los datos de la empresa al mismo tiempo que permite que los usuarios [accedan a las aplicaciones y el contenido que necesitan](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility).|
|Usuario final|[Usuarios de dispositivos como teléfonos y equipos](/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune) que se administran mediante Intune.|
|Inscribir|Microsoft Intune usa la [inscripción](/intune/deploy-use/enroll-devices-in-microsoft-intune) para incluir dispositivos en la administración y permitir el acceso a los recursos.|

## <a name="f"></a>F
|||
|-|-|
|FastTrack|[Servicio de Microsoft](https://technet.microsoft.com/library/mt228265.aspx) para usuarios de Intune con 150 licencias en un plan válido. Con este servicio, los especialistas de Microsoft colaborarán con usted para ayudarle a empezar a trabajar con Intune.|

## <a name="g"></a>G
|||
|-|-|
|Grupos|Los grupos permiten [reunir de forma lógica usuarios o dispositivos](/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune). Por ejemplo, puede crear un grupo con todos los equipos Windows. Después, puede implementar aplicaciones y directivas en los grupos.|

## <a name="h"></a>H
|||
|-|-|
|Híbrido|Configuración en la que puede administrar dispositivos inscritos con Intune [a través de la consola de System Center Configuration Manager](/intune/get-started/integration-with-cloud-services).|

## <a name="i"></a>I
|||
|-|-|
|Consola de administración de Intune|Consola actual que se usa para la mayoría de las operaciones de administración de Intune.|
|Cliente de software de Intune|Manera alternativa de [administrar algunos equipos Windows](/intune/deploy-use/manage-windows-pcs-with-microsoft-intune). Consulte [Elegir cómo administrar dispositivos](/intune/get-started/choose-how-to-manage-devices) para decidir qué método usar.|
|editor de software de Intune|Herramienta que se usa para [definir las aplicaciones que se quieren implementar y cargarlas en un espacio de almacenamiento en nube](/intune/deploy-use/add-apps).|
|Tema de|Se usa para ver el [hardware y el software instalado](/intune/deploy-use/understand-your-devices-with-inventory-in-microsoft-intune) de los dispositivos administrados.|

## <a name="k"></a>K
|||
|-|-|
|Modo de quiosco|Este modo, configurado como parte de una [directiva de configuración general](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies), permite bloquear dispositivos. Por ejemplo, podría configurar un dispositivo comercial de modo que solo ejecute una aplicación.|

## <a name="m"></a>M
|||
|-|-|
|Explorador administrado|[Aplicación de exploración web](/intune/deploy-use/manage-internet-access-using-managed-browser-policies) que se puede implementar en la organización mediante Microsoft Intune. Una directiva de explorador administrado configura una lista de permitidos o una lista de bloqueados que restringe los sitios web que pueden visitar los usuarios del explorador administrado.|
|Administración de aplicaciones móviles|La [administración de aplicaciones móviles (MAM)](/intune/deploy-use/overview-of-app-lifecycle-in-microsoft-intune) permite publicar, insertar, configurar, proteger, supervisar y actualizar aplicaciones móviles para los usuarios.
|Administración de dispositivos móviles|La [administración de dispositivos móviles (MDM)](/intune/deploy-use/overview-of-device-lifecycle-in-microsoft-intune) permite inscribir dispositivos en Intune para poder aprovisionar, configurar y supervisar esos dispositivos, además de llevar a cabo acciones en ellos.
|Entidad de MDM|La [entidad de MDM](/intune/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune) define el servicio de administración que tiene permiso para administrar un conjunto de dispositivos. Las opciones para la entidad de MDM incluyen Intune y Configuration Manager con Intune.|
|Directiva de aprovisionamiento de aplicaciones móviles|Directiva de iOS que ayuda a asegurarse de que los [perfiles de aprovisionamiento](/intune/deploy-use/ios-mobile-app-provisioning-profiles) de las aplicaciones iOS implementadas no expiran.|
|Directiva de configuración de aplicaciones móviles|Directiva de iOS que se usa para [proporcionar la configuración a aplicaciones iOS compatibles](/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune) cuando se ejecutan, por ejemplo, el nombre de la empresa o la dirección del servidor.|

## <a name="o"></a>O
|||
|-|-|
|OMA-DM|Open Mobile Alliance Device Management. Protocolo de administración de dispositivos estándar del sector que usan muchos fabricantes de hardware para habilitar el control de las características de dispositivos móviles y equipos.|
|OMA-URI|Open Mobile Alliance Uniform Resource Identifier. Identifica los ajustes de dispositivos individuales que cumplen el estándar OMA-DM. Puede usar un conjunto de estos en [directivas personalizadas de Intune](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) cuando no haya ninguna configuración integrada que satisfaga sus necesidades.|

## <a name="p"></a>P
|||
|-|-|
|Directiva|[Paquete de información](/intune/deploy-use/microsoft-intune-policy-reference) que se envía de Intune a un dispositivo. Por ejemplo, podría implementar en el dispositivo una configuración de seguridad o información de conformidad de dispositivos.|
|Restablecimiento de la contraseña|Característica de Intune que le permite obligar al usuario final a [restablecer el código de acceso](/intune/deploy-use/use-remote-lock-and-passcode-reset-in-microsoft-intune) en dispositivos compatibles.|

## <a name="r"></a>R
|||
|-|-|
|Bloqueo remoto|Característica de Intune que le permite [bloquear dispositivos compatibles](/intune/deploy-use/use-remote-lock-and-passcode-reset-in-microsoft-intune), incluso si no es el propietario del dispositivo.|
|Reports|Intune ofrece diversos [informes integrados](/intune/deploy-use/understand-microsoft-intune-operations-by-using-reports) que le proporcionan información sobre los dispositivos que administra.|
|Instalación requerida|Al implementar una aplicación con esta acción, se instala en el dispositivo [sin intervención del usuario](/intune/deploy-use/deploy-apps) (aunque en algunas plataformas, el usuario final podría tener que aceptar la instalación).|
|Requisitos|[Operación de implementación de aplicación](/en-us/intune/deploy-use/add-apps) que permite seleccionar los requisitos que se deben cumplir en un dispositivo antes de instalar la aplicación. Por ejemplo, puede especificar la versión del sistema operativo de iOS que debe estar instalada para que se pueda instalar la aplicación.|

## <a name="s"></a>S
|||
|-|-|
|La eliminación de datos selectiva|El [borrado selectivo](/intune/deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune) solo quita los datos de la empresa, incluidos los datos de administración de aplicaciones móviles (MAM) si procede, las configuraciones y los perfiles de correo electrónico de un dispositivo. El borrado selectivo deja los datos personales del usuario en el dispositivo.|
|Suscripción|El contrato que especifica que permite tener acceso a un inquilino de Intune.|

## <a name="t"></a>T
|||
|-|-|
|TeamViewer|Aplicación de terceros que funciona con Intune para proporcionar [funcionalidades de asistencia remota](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#request-and-provide-remote-assistance-for-windows-pcs) para equipos Windows administrados con el cliente de software de Intune.|
|Inquilino|Una única instancia del servicio Intune puede tener acceso a una suscripción.|
|términos y condiciones|Tipo de directiva que se implementa en los usuarios con información que estos deben [leer y aceptar](/intune/deploy-use/terms-and-condition-policy-settings-in-microsoft-intune) a fin de poder usar el portal de empresa para inscribirse y acceder a su trabajo.|

## <a name="v"></a>V
|||
|-|-|
|Aplicación comprada por volumen|Algunas tiendas de aplicaciones permiten comprar varias licencias de una aplicación que se quiere ejecutar en la compañía. Intune ayuda a administrar las aplicaciones que [se compran a través de este tipo de programa](/intune/deploy-use/manage-volume-purchased-apps-in-microsoft-intune). Para ello, importa la información de licencia desde la tienda de aplicaciones, realiza el seguimiento de la cantidad de licencias usadas y le impide instalar más copias de la aplicación de las que posee.|
|Perfil de VPN|Directiva que implementa la [configuración de VPN](/intune/deploy-use/vpn-connections-in-microsoft-intune) en los dispositivos administrados, reduciendo al mínimo la configuración que deben llevar a cabo los usuarios finales.|

## <a name="w"></a>W
|||
|-|-|
|Perfil de Wi-Fi|Directiva que implementa la [configuración de red inalámbrica](/intune/deploy-use/wi-fi-connections-in-microsoft-intune) en los dispositivos para permitir que los usuarios se conecten a la red de la empresa sin necesidad de que conozcan o configuren las opciones.



<!--HONumber=Dec16_HO3-->


