---
title: Glosario de Microsoft Intune
titleSuffix: Microsoft Intune
description: Obtenga información sobre la terminología usada en Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 07/28/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bd7b5613-ee9f-4dc3-990c-ab4c1d40720d
ms.custom: intune-azure
ms.openlocfilehash: 2b59ed38329462ad8d8db604979c8eb725f7973a
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="microsoft-intune-glossary"></a>Glosario de Microsoft Intune
Descubra las definiciones de los términos habituales que se usan en Microsoft Intune.

## <a name="a"></a>A

|||
|-|-|
|Asignación de aplicaciones|Permite a los usuarios [buscar, descargar e instalar](/intune/app-management) las aplicaciones que necesitan. Esto se denominaba anteriormente *implementación de aplicaciones*.|
|Perfil de configuración de aplicaciones <br/><br/>Directiva de configuración de aplicaciones|Disponible para aplicaciones móviles con configuraciones específicas del proveedor. Configura una aplicación [iOS](/intune/app-configuration-policies-use-ios) o [Android](/intune/app-configuration-policies-use-android) con una configuración específica antes de ejecutarla.|
|Supervisión de aplicaciones|Le permite [revisar el estado y la actividad recientes](/intune/apps-monitor) relacionados con la asignación de aplicaciones.|
|Tarea de eliminación de datos de protección de aplicaciones|[Quita los datos de la aplicación](/intune/app-protection-policies) en el dispositivo del usuario.|
|Directiva de protección de aplicaciones|Disponible para aplicaciones móviles que se integran con tecnologías de Enterprise Mobility + Security (EMS). Garantiza que las aplicaciones del usuario son compatibles con las [directivas de protección de datos de la empresa](/intune/app-protection-policies).|
|SDK para aplicaciones|El [SDK para aplicaciones de Microsoft Intune](/intune/app-sdk) permite agregar funcionalidad a las aplicaciones escritas internamente que permite administrarlas mediante directivas de protección de aplicaciones de Intune.|
|Acción de desinstalación de aplicaciones|Le permite [desinstalar aplicaciones](/intune/apps-deploy) en los dispositivos del usuario.|
|Herramienta de ajuste de aplicaciones|[Aplicación de línea de comandos](/intune/apps-prepare-mobile-application-management) que crea un contenedor en torno a una aplicación de línea de negocios, que permite administrarla mediante una directiva de protección de aplicaciones de Intune.|
|Acción de asignación|Opción que se elige al [asignar una aplicación](/intune/apps-deploy). Puede decidir que la instalación de la aplicación sea obligatoria (necesaria), opcional (disponible) o bien puede desinstalar la aplicación.|
|Instalación disponible|Cuando se asigna una aplicación con esta acción, aparece en el portal de empresa y los usuarios pueden [solicitar instalarla](/intune/apps-deploy).|
|Portal de Azure|Nueva consola de Intune [Más información](/intune/what-is-intune).|

## <a name="b"></a>B

|||
|-|-|
|BYOD|[Bring Your Own Device](/intune/device-enrollment). Los usuarios pueden instalar la aplicación de portal de empresa de Intune en sus dispositivos y, luego, inscribirlos para acceder a recursos de la empresa, como el correo electrónico, aplicaciones de empresa, datos de la compañía y soporte técnico.|

## <a name="c"></a>C

|||
|-|-|
|Perfil de certificado|Use este tipo de directiva para [proteger el acceso a los recursos corporativos](/intune/certificates-configure) con certificados cuando se usan perfiles de Wi-Fi, correo electrónico o VPN.|
|Contra reembolso|Los [dispositivos propiedad de la empresa](/intune/device-enrollment) se pueden inscribir de numerosas formas, según cuáles sean las necesidades de la organización y los tipos de dispositivos administrados.|
|Portal de empresa|Aplicación o sitio web que proporciona a los usuarios [acceso a aplicaciones y datos de la empresa](/intune/company-portal-customize).|
|Directiva de cumplimiento|Garantiza que los dispositivos [cumplen ciertas reglas](/intune/device-compliance), como el uso de un PIN para acceder al dispositivo y el cifrado de los datos almacenados en el dispositivo.|
|Aplicaciones conformes y no conformes|Estos valores, que forman parte de un [perfil de restricción de dispositivos](/intune/device-restrictions-configure), permiten definir una lista de las aplicaciones que los usuarios pueden ejecutar o no. Intune, después, le notifica a través de informes si se instala o se ejecuta una aplicación no conforme. En el caso de algunas plataformas, Intune también puede bloquear la instalación de una aplicación no conforme.|
|Acceso condicional|[Permite el acceso al correo electrónico de la empresa, Office 365 y otros servicios](/intune/conditional-access) solo desde dispositivos conformes con las reglas establecidas.|
|Directiva personalizada|[Use estas directivas](/intune/custom-settings-configure) cuando una directiva de configuración general no tiene una configuración integrada que satisfaga sus necesidades. Puede usar una directiva personalizada para crear una configuración usando otros medios, como OMA-URI o Apple Configurator.|

## <a name="d"></a>D

|||
|-|-|
|Implementación|Acto de enviar una aplicación o una directiva a un dispositivo o un usuario que usted administra. Esta acción se denomina ahora *asignar*.|
|Administrador de inscripción de dispositivos|Las organizaciones pueden usar Intune para administrar un gran número de dispositivos móviles con una sola cuenta de usuario. La [cuenta del administrador de inscripción de dispositivos (DEM)](/intune/device-enrollment-program-enroll-ios) es una cuenta especial de Intune con permisos para inscribir hasta 1000 dispositivos.|
|Perfiles de dispositivo|[Estos perfiles](/intune/device-profile-create) le permiten configurar diversos ajustes de seguridad, de características y de acceso en los dispositivos que administra.|

## <a name="e"></a>E

|||
|-|-|
|Perfil de correo electrónico|Esta directiva se puede usar para configurar las [opciones de acceso a correo electrónico](/intune/email-settings-configure) en dispositivos móviles, con lo que se reduce al mínimo la configuración que debe llevar a cabo el usuario final.|
|EMS|Microsoft Enterprise Mobility + Security (anteriormente Enterprise Mobility Suite) protege los datos de la empresa al mismo tiempo que permite que los usuarios [accedan a las aplicaciones y el contenido que necesitan](https://www.microsoft.com/cloud-platform/enterprise-mobility).|
|Usuario final|[Usuarios de dispositivos como teléfonos y equipos](/intune/end-user-educate) que se administran mediante Intune.|
|Inscribir|Microsoft Intune usa la [inscripción](/intune/device-enrollment) para incluir dispositivos en la administración y permitir el acceso a los recursos.|

## <a name="f"></a>F

|||
|-|-|
|FastTrack|[Servicio de Microsoft](https://technet.microsoft.com/library/mt228265.aspx) para usuarios de Intune con 150 licencias en un plan válido. Con este servicio, los especialistas de Microsoft colaboran con los usuarios para ayudarles a empezar a trabajar con Intune.|

## <a name="g"></a>G

|||
|-|-|
|Grupos|Los grupos permiten [reunir de forma lógica usuarios o dispositivos](/intune/groups-get-started). Por ejemplo, puede crear un grupo con todos los equipos Windows. Después, puede asignar perfiles y aplicaciones a estos grupos.|

## <a name="h"></a>H

|||
|-|-|
|Híbrida|Configuración en la que puede administrar dispositivos inscritos con Intune a través de la consola de System Center Configuration Manager.|

## <a name="i"></a>I

|||
|-|-|
|Portal de Azure|Portal de Azure que se usa para la mayoría de las operaciones de administración de Intune.|
|Cliente de software de Intune|Una manera alternativa de [administrar algunos equipos con Windows](/intune-classic/get-started/choose-how-to-manage-devices) para obtener ayuda al decidir qué método quiere usar.|
|editor de software de Intune|Herramienta que se usa para [definir las aplicaciones que se quieren implementar y cargarlas en un espacio de almacenamiento en nube](/intune-classic/deploy-use/add-apps).|
|Tema de|Se usa para ver el [hardware y el software instalado](/intune/device-inventory) de los dispositivos administrados.|

## <a name="k"></a>K

|||
|-|-|
|Modo de quiosco|Este modo, configurado como parte de un [perfil de restricción de dispositivos](/intune/device-restrictions-configure), permite bloquear dispositivos. Por ejemplo, podría configurar un dispositivo comercial de modo que solo ejecute algunas aplicaciones.|

## <a name="m"></a>M

|||
|-|-|
|Explorador administrado|[Aplicación de exploración web](/intune/app-configuration-managed-browser) que se puede asignar en la organización mediante Intune. Una directiva de explorador administrado configura una lista de permitidos o una lista de bloqueados que restringe los sitios web que pueden visitar los usuarios del explorador administrado.|
|Entidad de MDM|La [entidad de MDM](/intune/mdm-authority-set) define el servicio de administración que tiene permiso para administrar un conjunto de dispositivos. Las opciones para la entidad de MDM incluyen Intune y Configuration Manager con Intune.|
|Directiva de configuración de aplicaciones móviles|Disponible para aplicaciones móviles con configuraciones específicas del proveedor. Por ejemplo, una directiva de [iOS](/intune/app-configuration-policies-use-ios) o [Android](/intune/app-configuration-policies-use-android) que se usa para proporcionar la configuración a aplicaciones compatibles cuando se ejecutan, por ejemplo, el nombre de la empresa o la dirección del servidor.|
|Directiva de aprovisionamiento de aplicaciones móviles|Directiva de iOS que ayuda a asegurarse de que los [perfiles de aprovisionamiento](/intune/app-provisioning-profile-ios) de las aplicaciones iOS asignadas no expiran.|
|Administración de aplicaciones móviles|La [administración de aplicaciones móviles (MAM)](/intune/app-lifecycle) permite publicar, insertar, configurar, proteger, supervisar y actualizar aplicaciones móviles para los usuarios.
|Administración de dispositivos móviles|La [administración de dispositivos móviles (MDM)](/intune/device-lifecycle) permite inscribir dispositivos en Intune para poder aprovisionar, configurar y supervisar esos dispositivos, además de administrarlos.



## <a name="o"></a>O

|||
|-|-|
|OMA-DM|Open Mobile Alliance Device Management. Protocolo de administración de dispositivos estándar del sector que usan muchos fabricantes de hardware para habilitar el control de las características de dispositivos móviles y equipos.|
|OMA-URI|Open Mobile Alliance Uniform Resource Identifier. Estos elementos identifican los ajustes de dispositivos individuales que cumplen el estándar OMA-DM. La configuración se puede usar en [perfiles personalizados de Intune](/intune/custom-settings-configure) cuando no haya ninguna configuración integrada que satisfaga sus necesidades.|

## <a name="p"></a>P

|||
|-|-|
|Restablecimiento de la contraseña|Característica de Intune que le permite obligar al usuario final a [restablecer el código de acceso](/intune/device-passcode-reset) en dispositivos compatibles.|

## <a name="r"></a>R

|||
|-|-|
|Bloqueo remoto|Característica de Intune que le permite [bloquear dispositivos compatibles](/intune/device-remote-lock), incluso si no es el propietario del dispositivo.|
|Instalación requerida|Cuando se asigna una aplicación con esta acción, no se requiere [la intervención del usuario](/intune/apps-deploy) para completar la instalación. En algunas plataformas, el usuario final podría tener que aceptar la instalación.|


## <a name="s"></a>S

|||
|-|-|
|La eliminación de datos selectiva|Un [borrado selectivo](/intune/device-company-data-remove) solo quita los datos de la empresa protegidos por la directiva de protección de aplicaciones incluidas las configuraciones y los perfiles de correo electrónico de un dispositivo. El borrado selectivo deja los datos personales del usuario en el dispositivo.|
|Instalación de prueba|Acción de instalar una aplicación de línea de negocio sin tener acceso a ella desde una tienda de aplicaciones.|
|Suscripción|El contrato que especifica que permite tener acceso a un inquilino de Intune.|

## <a name="t"></a>T

|||
|-|-|
|TeamViewer|Aplicación de terceros que funciona con Intune para proporcionar [funcionalidades de asistencia remota](/intune/device-profile-android-teamviewer) para dispositivos Android que gestiona con Intune.|
|Inquilino|Una única instancia del servicio Intune puede tener acceso a una suscripción.|
|términos y condiciones|Tipo de directiva que se asigna en los usuarios con información que estos deben [leer y aceptar](/intune/terms-and-conditions-create) a fin de poder usar el portal de empresa para inscribirse y acceder a su trabajo.|

## <a name="v"></a>V

|||
|-|-|
|Aplicaciones y libros comprados por volumen|Algunas tiendas de aplicaciones permiten comprar varias licencias para una aplicación o reservar las que se quieren usar en la compañía. Intune le ayuda a administrar las aplicaciones y a reservar las que [ha adquirido a través de este tipo de programa](/intune/vpp-apps). Puede importar la información de las licencias del almacén de aplicaciones, realizar el seguimiento del número de licencias que se han utilizado y evitar que los usuarios instalen más copias de la aplicación de las propias.|
|Perfil de VPN|Directiva que asigna la [configuración de VPN](/intune/vpn-settings-configure) en los dispositivos administrados, reduciendo al mínimo la configuración que deben llevar a cabo los usuarios finales.|

## <a name="w"></a>W

|               |                                                                                                                                                                                                 |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Perfil de Wi-Fi | Directiva que asigna la [configuración de red inalámbrica](/intune/wi-fi-settings-configure) en los dispositivos para permitir que los usuarios se conecten a la red de la empresa sin necesidad de que conozcan o configuren las opciones. |

