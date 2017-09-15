---
title: "Habilitación de BYOD con Microsoft Intune"
description: "Un flujo de trabajo de alto nivel para configurar Intune para habilitar una solución Bring Your Own Device (BYOD) a su organización."
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 07/26/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: vlpetros
ms.suite: ems
ms.openlocfilehash: f4e414f3696c64f8ea450394928aa055ad427afd
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2017
---
# <a name="enable-byod-with-intune"></a>Habilitación de BYOD con Intune

En este tema se proporciona un flujo de trabajo de alto nivel para configurar Intune y habilitar una solución Bring Your Own Device (BYOD) a su organización. En él se organiza la tarea en tres procesos y se proporcionan vínculos a temas de procedimientos.

El flujo de trabajo se divide en los tres procesos siguientes. Puede adaptar los aspectos de cada proceso para cumplir los requisitos de su organización.

-   En **[Inscribir dispositivos y comprobar su cumplimiento](#enroll-devices-and-check-for-compliance)** se describe cómo permitir que los usuarios inscriban sus dispositivos personales en la administración con Intune. Intune administra dispositivos iOS, macOS, Android y Windows. En esta sección también se describe cómo implementar directivas en los dispositivos y garantizar que cumplen los requisitos básicos de seguridad.

- En **[Proporcionar acceso a los recursos de empresa](#provide-access-to-company-resources)** se muestra cómo puede permitir que los usuarios obtengan acceso a los recursos de la empresa de forma fácil y segura. Para ello, debe implementar perfiles de acceso en los dispositivos administrados. En esta sección también se explica cómo administrar con Intune las implementaciones de aplicaciones compradas por volumen.

-   En **[Proteger los datos de la empresa](#protect-company-data)** puede obtener información sobre cómo proporcionar acceso condicional a los recursos de la empresa, evitar la pérdida de datos y quitar datos y aplicaciones de la empresa en dispositivos que ya no se necesitan para trabajar, que se han perdido o que han sido robados.

[![Diagrama del flujo de trabajo de alto nivel para habilitar BYOD con Microsoft Intune](./media/workflow-diagram-for-byod.png)](./media/workflow-diagram-for-byod.png)

<!--- > <sup>You can download this infographic at https://gallery.technet.microsoft.com/Infographic-Management-3644ae41.</sup> --->

## <a name="before-you-begin"></a>Antes de comenzar
Antes de que los usuarios puedan inscribir dispositivos, primero debe preparar el propio servicio de Intune. Para ello, [asigne licencias a los usuarios](licenses-assign.md) y [establezca la entidad de administración de dispositivos móviles](mdm-authority-set.md).

Mientras lo hace, también debe [personalizar el Portal de empresa](company-portal-customize.md). Agregue una marca de empresa y proporcione información de soporte técnico a los usuarios. De este modo se crea una experiencia de soporte técnico y de inscripción de confianza para los usuarios. También puede crear [condiciones de uso](terms-and-conditions-create.md) que los usuarios deben aceptar antes de inscribirse o [restricciones de dispositivo](enrollment-restrictions-set.md) para especificar las plataformas que admite.

## <a name="enroll-devices-and-check-for-compliance"></a>Inscribir dispositivos y comprobar su cumplimiento

Una vez preparado el servicio de Intune, debe cumplir los distintos requisitos de inscripción de los distintos tipos de dispositivos que va a administrar. El proceso de inscripción de dispositivos en la administración es sencillo, pero es ligeramente diferente en función del tipo de dispositivo.

-   **Dispositivos iOS y Mac** Debe [obtener un certificado push MDM de Apple](apple-mdm-push-certificate-get.md) para inscribir dispositivos iPad, iPhone o macOS. Una vez cargado el certificado push MDM en Intune, los usuarios pueden [inscribir dispositivos iOS](/intune-user-help/enroll-your-device-in-intune-ios) mediante la aplicación del portal de empresa y usar el sitio web del portal de empresa para [inscribir dispositivos macOS](/intune-user-help/enroll-your-device-in-intune-macos).

-   **Dispositivos Android** No es necesario que haga nada para preparar el servicio de Intune para la inscripción de dispositivos Android. Los usuarios pueden [inscribir sus dispositivos Android](/intune-user-help/enroll-your-device-in-intune-android) en la administración mediante la aplicación de portal de empresa que está disponible en Google Play.

-   **Equipos y dispositivos Windows Phone** Los dispositivos Windows pueden inscribirse con una configuración adicional. Puede habilitar la inscripción automática para equipos de Windows 10 y dispositivos móviles Windows 10 en Azure Active Directory (AD) Premium para simplificar la experiencia de los usuarios. Si no tiene Azure AD Premium o si necesita admitir Windows 8.1, puede crear [un alias DNS para el servidor de inscripción](windows-enroll.md#simplify-windows-enrollment-without-azure-ad-premium) para facilitar la inscripción.


### <a name="make-sure-that-managed-devices-meet-basic-security-requirements"></a>Asegurarse de que los dispositivos administrados cumplen los requisitos básicos de seguridad

Después de que los usuarios inscriban sus dispositivos en la administración, el departamento de TI debe garantizar que los dispositivos usados para obtener acceso a los datos y aplicaciones de la empresa cumplen los requisitos básicos de seguridad. Estas reglas pueden incluir el uso de un PIN para acceder a los dispositivos y el cifrado de los datos almacenados en ellos. A un conjunto de tales reglas se le denomina una [directiva de cumplimiento](device-compliance.md).

Al [implementar una directiva de cumplimiento](device-compliance-get-started.md) en un usuario, Intune comprueba cada dispositivo administrado por el usuario para ver si cumple los requisitos básicos de seguridad definidos como parte de la directiva BYOD. Una vez evaluado el cumplimiento de la directiva de este dispositivo, notifica su estado a Intune. En algunos casos es posible que se pida a los usuarios que modifiquen algunas opciones, como el PIN o el cifrado del dispositivo. En otros casos, la aplicación del Portal de empresa notifica al usuario todas las opciones que no cumplen la directiva.

## <a name="provide-access-to-company-resources"></a>Proporcionar acceso a los recursos de empresa

A lo primero que la mayoría de los empleados quiere acceder en su dispositivo móvil es a los documentos y el correo electrónico de la empresa. Esperan poder configurarlo sin tener que realizar pasos complejos ni llamar al departamento de soporte técnico. Intune facilita la [creación e implementación de la configuración del correo electrónico](email-settings-configure.md) para las aplicaciones de correo electrónico nativas que están instaladas previamente en los dispositivos móviles.


> [!NOTE]
> Intune admite la configuración de perfil de correo electrónico de Android for Work para las aplicaciones de correo electrónico Gmail y Nine Work que se encuentran en Google Play Store.

Intune también le permite controlar y proteger el acceso a los datos locales de la empresa cuando los usuarios trabajan fuera. Los perfiles de [Wi-Fi](wi-fi-settings-configure.md), [VPN](vpn-settings-configure.md) y de correo electrónico de Intune funcionan de manera conjunta para permitir el acceso a los archivos y recursos que necesitan para trabajar, estén donde estén. También se puede acceder a los servicios y aplicaciones web de la empresa hospedados de forma local y protegerlos de forma segura mediante el proxy de aplicación de Azure Active Directory y el acceso condicional.

### <a name="manage-volume-purchased-apps"></a>Administrar aplicaciones adquiridas por volumen
Con Intune es fácil:
* Importar la información de la licencia por volumen de cualquier tienda de aplicaciones
* Realizar un seguimiento de la cantidad de licencias que se han usado
* Evitar que los usuarios instalen más copias de la aplicación que tiene
* [Entregar aplicaciones de la tienda a los dispositivos administrados](apps-deploy.md)
* Destinar aplicaciones a los dispositivos no administrados mediante el sitio web del portal de empresa

Intune también le permite administrar e implementar las aplicaciones que ha comprado por volumen en el App Store de iOS y en la Tienda Microsoft para Empresas. Esto ayuda a reducir la carga administrativa relacionada con el seguimiento de las aplicaciones adquiridas por volumen.

> [!TIP]
> Puede [configurar el inicio de sesión único (SSO) con Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect). El SSO permite que los usuarios inicien sesión en aplicaciones con el nombre de usuario y la contraseña del dominio que usan de forma local. Asimismo, puede [proporcionar acceso basado en Internet a aplicaciones web hospedadas localmente](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) mediante el Proxy de aplicación de Azure Active Directory.

-   [Administrar aplicaciones adquiridas por volumen para dispositivos iOS](vpp-apps-ios.md). Puede comprar varias licencias para aplicaciones de iOS a través del [Programa de Compras por Volumen de Apple para empresas](http://www.apple.com/business/vpp/). Debe configurar una cuenta de PCV de Apple en el sitio web de Apple y cargar el token de PCV de Apple en Intune. De este modo, puede sincronizar la información de compras por volumen con Intune y hacer el seguimiento del uso de aplicaciones compradas por volumen.

-   [Administración de aplicaciones adquiridas a través de la Tienda Microsoft para Empresas](windows-store-for-business.md). En la [Tienda Microsoft para Empresas](https://www.microsoft.com/business-store), puede buscar y comprar aplicaciones para su organización, tanto sueltas como por volumen. Si conecta la tienda a Intune, puede administrar aplicaciones compradas por volumen desde Azure Portal.

## <a name="protect-company-data"></a>Proteger los datos de la empresa

Intune protege los datos empresariales mediante numerosas capas de tecnología. En la capa de identidad, el acceso condicional protege el acceso a los servicios. El acceso condicional solo permite que los dispositivos administrados y compatibles obtengan acceso a los recursos de la empresa. En la capa de la aplicación cliente, las directivas de protección de aplicaciones ayudan a evitar la pérdida de datos. Las directivas de protección de aplicaciones impiden que los datos se muevan a aplicaciones o ubicaciones de almacenamiento que no están protegidas. Estas directivas también le permiten borrar datos de empresa cuando se pierde o roba un dispositivo.

### <a name="enforce-conditional-access-to-company-resources"></a>Aplicar el acceso condicional a los recursos de la empresa

Puede combinar las directivas de cumplimiento con las [directivas de acceso condicional](device-compliance.md) para comprobar si los dispositivos cumplen los requisitos básicos de seguridad que requiere la directiva BYOD. Si un dispositivo no cumple los requisitos, se aplican las reglas y se deniega el acceso hasta que cumpla los requisitos de la directiva. Esto garantiza que solo los dispositivos administrados y compatibles puedan tener acceso a los datos de la empresa desde servicios como Exchange ([Exchange local](exchange-connector-install.md) o [Exchange Online](conditional-access-exchange-create.md)), SharePoint Online, Skype Empresarial Online, etc.
<!---first link was (https://docs.microsoft.com/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)
third link was (https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune). check with Andre--->

> [!IMPORTANT]
> Las directivas de acceso condicional no funcionarán si no se ha aplicado ninguna directiva de cumplimiento para validar el cumplimiento.

### <a name="prevent-data-loss-of-company-data-with-app-protection-policies"></a>Evitar la pérdida de datos de la empresa con directivas de protección de aplicaciones

Con las directivas de protección de aplicaciones de Intune, puede elegir cómo se accede a los datos (con o sin la inscripción de dispositivos). Esta flexibilidad le permite proteger los datos de empresa de manera que un usuario podrá seguir obteniendo acceso a los datos de la empresa de forma segura aunque no inscriba su dispositivo en Intune.

Puede usar [directivas de protección de aplicaciones de Intune](app-protection-policies.md) para ayudar a proteger los datos de la empresa a los que acceden los dispositivos iOS y Android. Si usa estas directivas de nivel de aplicación, puede controlar la manera en que los empleados usan y comparten los datos de la empresa, aunque Intune no administre el dispositivo en cuestión.

Use [Windows Information Protection (WIP)](app-protection-policies-configure-windows-10.md) para hacer lo mismo en los dispositivos Windows 10 administrados. Estas directivas funcionan sin interferir en la experiencia de los empleados. No requieren cambios en el entorno de red ni en otras aplicaciones.

### <a name="remove-company-data-while-leaving-personal-data-intact"></a>Quitar datos de la empresa mientras se dejan intactos los datos personales

Cuando un dispositivo ya no es necesario para el trabajo, se va a reasignar o se ha perdido, puede quitar los datos y las aplicaciones de la empresa que contenga. Para ello, puede usar las funcionalidades de Intune para eliminar los datos de la empresa o realizar un restablecimiento de fábrica. Los usuarios también pueden restablecer remotamente sus propios dispositivos desde el Portal de empresa de Intune si esos dispositivos están inscritos en Intune.

Un [restablecimiento de fábrica](devices-wipe.md) restaura la configuración predeterminada de fábrica del dispositivo, quita los datos y la configuración del usuario y quita el dispositivo de la administración de Intune. La opción [Eliminar datos de la compañía](devices-wipe.md#remove-company-data) solo quita del dispositivo los datos de la empresa, pero deja intactos los datos personales de los usuarios.

Una vez que se inicia, el dispositivo comienza inmediatamente el proceso de restablecimiento. Una vez finalizado el proceso, se eliminarán todos los datos de la empresa y se quitará el nombre del dispositivo de Intune. con lo que finaliza el ciclo de vida de administración del dispositivo.
