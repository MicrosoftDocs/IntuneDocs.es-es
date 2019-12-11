---
title: Uso de credenciales derivadas para dispositivos móviles en Microsoft Intune - Azure | Microsoft Docs
description: Use credenciales derivadas en dispositivos móviles como método de autenticación para la VPN de Intune, correo electrónico, perfiles de Wi-Fi, aplicaciones, S/MIME y cifrado. Las credenciales derivadas son una implementación de las directrices NIST para la publicación especial 800-157.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/31/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c4d0772f9a0afce0607d0193bfb82ea6bd22709d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "73445330"
---
# <a name="use-derived-credentials-in-microsoft-intune"></a>Uso de credenciales derivadas en Microsoft Intune

*Este artículo se aplica a los dispositivos que ejecutan iOS*

En un entorno en el que se necesitan tarjetas inteligentes para la autenticación o el cifrado y la firma, ahora puede usar Intune para aprovisionar dispositivos móviles con un certificado que se derive de la tarjeta inteligente de un usuario. Ese certificado se denomina *credencial derivada*. Intune [admite varios emisores de credenciales derivadas](#supported-issuers), aunque solo se puede usar un emisor por inquilino a la vez.

Las credenciales derivadas son una implementación de las directrices del National Institute of Standards and Technology (NIST) para las credenciales derivadas de verificación de identidad personal (PIV) como parte de la publicación especial (SP) 800-157.

**Con la implementación de Intune**:

- El administrador de Intune configura su inquilino para que funcione con un emisor de credenciales derivadas compatible. No es necesario aplicar ninguna configuración específica de Intune en el sistema del emisor de las credenciales derivadas.

- El administrador de Intune especifica la **credencial derivada** como *método de autenticación* de los siguientes objetos:

  - Tipos de perfiles comunes, como Wi-Fi, VPN y correo electrónico, que incluye la aplicación de correo electrónico nativa de iOS

  - Autenticación de aplicaciones

  - Firma S/MIME y cifrado

- Los usuarios obtienen una credencial derivada usando su tarjeta inteligente en un equipo para autenticarse en el emisor de las credenciales derivadas. Luego, el emisor emite en el dispositivo móvil un certificado que se deriva de su tarjeta inteligente.

- Una vez que el dispositivo ha recibido la credencial derivada, se usa para la autenticación, así como para la firma S/MIME y el cifrado, cuando las aplicaciones o los recursos obtienen acceso a perfiles que requieren la credencial derivada. 

## <a name="prerequisites"></a>Requisitos previos

Revise la siguiente información antes de configurar su inquilino para usar las credenciales derivadas.

### <a name="supported-platforms"></a>Plataformas compatibles

Intune admite credenciales derivadas en las siguientes plataformas de sistemas operativos:

- iOS/iPadOS

### <a name="supported-issuers"></a>Emisores admitidos

Intune admite un solo emisor de credenciales derivadas por inquilino. Puede configurar Intune para que funcione con los siguientes emisores:

- **DISA Purebred**: https://cyber.mil/pki-pke/purebred/
- **Entrust Datacard**: https://www.entrustdatacard.com/
- **Intercede**: https://www.intercede.com/

Para obtener información importante sobre el uso de los distintos emisores, consulte la guía del emisor en cuestión.<!-- , including the issuers end-user workflow-->. Para obtener más información, vea [Planear las credenciales derivadas](#plan-for-derived-credentials) en este artículo.

> [!IMPORTANT]  
> Si elimina de su inquilino un emisor de credenciales derivadas, las credenciales derivadas que se hayan configurado con ese emisor dejarán de funcionar.
>
> Consulte [Cambiar el emisor de las credenciales derivadas](#change-the-derived-credential-issuer) más adelante en este artículo.

### <a name="company-portal-app"></a>Aplicación de portal de empresa

Planee la implementación de la aplicación Portal de empresa de Intune en los dispositivos que se van a inscribir en una credencial derivada. Los usuarios de dispositivos usan la aplicación Portal de empresa para iniciar el proceso de inscripción de credenciales.

Para los dispositivos iOS, consulte [Adición de aplicaciones de la tienda iOS a Microsoft Intune](../apps/store-apps-ios.md).

## <a name="plan-for-derived-credentials"></a>Planear las credenciales derivadas

Tenga presentes las siguientes consideraciones antes de configurar un emisor de credenciales derivadas.

### <a name="1-review-the-documentation-for-your-chosen-derived-credential-issuer"></a>1) Revisar la documentación del emisor de credenciales derivadas elegido  

Antes de configurar un emisor, revise la documentación correspondiente para comprender cómo suministra su sistema las credenciales derivadas a los dispositivos.

En función del emisor que elija, puede que necesite personal que esté disponible en el momento de la inscripción para que los usuarios puedan llevar a cabo el proceso. También debe revisar las configuraciones actuales de Intune para asegurarse de que no bloquean el acceso necesario para que los dispositivos o los usuarios lleven a cabo la solicitud de credenciales.

Por ejemplo, puede usar el acceso condicional para bloquear el acceso al correo electrónico en los dispositivos no compatibles. Si confía en las notificaciones por correo electrónico para informar al usuario de que debe iniciar el proceso de inscripción de credenciales derivadas, es posible que los usuarios no reciban esas instrucciones hasta que cumplan la directiva.

Del mismo modo, algunos flujos de trabajo de solicitud de credenciales derivadas requieren el uso de la cámara del dispositivo para escanear un código QR que aparece en pantalla. Este código vincula ese dispositivo a la solicitud de autenticación que se efectuó en el emisor de las credenciales derivadas con las credenciales de la tarjeta inteligente del usuario. Si las directivas de la configuración del dispositivo bloquean el uso de la cámara, el usuario no podrá llevar a cabo la solicitud de inscripción de credenciales derivadas.

Información general:

- Solo puede configurar un emisor por inquilino a la vez; ese emisor está disponible para todos los usuarios y los dispositivos compatibles en el inquilino.

- No se notificará a los usuarios de que deben inscribirse en las credenciales derivadas hasta que les aplique una directiva que requiera credenciales derivadas.

- La notificación puede realizarse a través de una notificación de la aplicación del Portal de empresa, por correo electrónico o ambos. Si decide usar notificaciones por correo electrónico y habilita el acceso condicional, es posible que los usuarios no reciban la notificación por correo electrónico si su dispositivo no es compatible.

### <a name="2-review-the-end-user-workflow-for-your-chosen-issuer"></a>2) Revisar el flujo de trabajo del usuario final del emisor elegido

A continuación se indican las consideraciones clave de cada asociado admitido.  Familiarícese con esta información para asegurarse de que las directivas y configuraciones de Intune no impidan que los usuarios y los dispositivos lleven a cabo correctamente la inscripción de una credencial derivada de ese emisor.

#### <a name="disa-purebred"></a>DISA Purebred

Revise el [flujo de trabajo del usuario para DISA Purebred](https://docs.microsoft.com/intune-user-help/enroll-ios-device-disa-purebred). Los principales requisitos de este flujo de trabajo incluyen:

- Los usuarios necesitan tener acceso a un equipo o a un quiosco en el que puedan usar su tarjeta inteligente para autenticarse en el emisor.

- Los dispositivos que se inscriban en una credencial derivada deben instalar la aplicación Portal de empresa de Intune.

- Use Intune para [implementar la aplicación DISA Purebred](#deploy-the-disa-purebred-app) en los dispositivos que se van a inscribir en una credencial derivada. Esta aplicación debe estar implementada a través de Intune para que se administre y pueda trabajar después con la aplicación Portal de empresa de Intune. Esta aplicación la usan los usuarios del dispositivo para llevar a cabo la solicitud de credenciales derivadas.

- La aplicación DISA Purebred requiere una [VPN por aplicación](../configuration/vpn-settings-configure.md) para garantizar que la aplicación pueda acceder a DISA Purebred durante la inscripción de la credencial derivada.

- Los usuarios del dispositivo deben trabajar con un agente activo durante el proceso de inscripción. Durante la inscripción se proporciona al usuario códigos de acceso de un solo uso y de tiempo limitado a medida que avanza en el proceso de inscripción.

Para obtener información sobre cómo obtener y configurar la aplicación DISA Purebred, vea [Implementar la aplicación DISA Purebred](#deploy-the-disa-purebred-app) más adelante en este artículo.

#### <a name="entrust-datacard"></a>Entrust Datacard

Revise el [flujo de trabajo del usuario para Entrust Datacard](https://docs.microsoft.com/intune-user-help/enroll-ios-device-entrust-datacard). Los principales requisitos de este flujo de trabajo incluyen:

- Los usuarios necesitan tener acceso a un equipo o a un quiosco en el que puedan usar su tarjeta inteligente para autenticarse en el emisor.

- Los dispositivos que se inscriban en una credencial derivada deben instalar la aplicación Portal de empresa de Intune.

- Uso de una cámara de dispositivo para escanear un código QR que vincule la solicitud de autenticación a la solicitud de la credencial derivada desde el dispositivo móvil.

#### <a name="intercede"></a>Intercede

Revise el [flujo de trabajo del usuario para Intercede](https://docs.microsoft.com/intune-user-help/enroll-ios-device-intercede). Los principales requisitos de este flujo de trabajo incluyen:

- Los usuarios necesitan tener acceso a un equipo o a un quiosco en el que puedan usar su tarjeta inteligente para autenticarse en el emisor.

- Los dispositivos que se inscriban en una credencial derivada deben instalar la aplicación Portal de empresa de Intune.

- Uso de una cámara de dispositivo para escanear un código QR que vincule la solicitud de autenticación a la solicitud de la credencial derivada desde el dispositivo móvil.

### <a name="3-deploy-a-trusted-root-certificate-to-devices"></a>3) Implementar un certificado raíz de confianza en los dispositivos

Se usa un certificado raíz de confianza con credenciales derivadas para comprobar que la cadena de certificados de las credenciales derivadas es válida y de confianza. Incluso si no se hace referencia directa a él mediante una directiva, se requiere un certificado raíz de confianza. Vea [Configuración de un perfil de certificado para sus dispositivos en Microsoft Intune](certificates-configure.md).

### <a name="4-provide-end-user-instructions-for-how-to-get-the-derived-credential"></a>4) Proporcionar instrucciones al usuario final sobre cómo obtener la credencial derivada

Cree y proporcione orientación a sus usuarios sobre cómo iniciar el proceso de inscripción de credenciales derivadas y dirigirlos al flujo de trabajo de inscripción de credenciales derivadas para el emisor elegido.

Le recomendamos que proporcione una dirección URL que hospede su guía. Esta dirección URL se especifica al configurar el emisor de credenciales derivadas de su inquilino y se pone a disposición desde la aplicación Portal de empresa. Si no especifica su propia dirección URL, Intune proporcionará un vínculo a los detalles genéricos. Esta información detallada no puede cubrir todos los escenarios y es posible que no sea precisa para su entorno.

### <a name="5-deploy-intune-policies-that-require-derived-credentials"></a>5) Implementar directivas de Intune que requieran credenciales derivadas

Cree directivas o edite las directivas existentes para usar las credenciales derivadas. Las credenciales derivadas reemplazan otros métodos de autenticación para la autenticación de aplicaciones, Wi-Fi, VPN, correo electrónico, así como para la firma S/MIME y el cifrado.

Evite requerir el uso de una credencial derivada para obtener acceso a un proceso que usará como parte del proceso para obtener la credencial derivada, ya que puede impedir que los usuarios lleven a cabo la solicitud.

## <a name="set-up-a-derived-credential-issuer"></a>Configurar un emisor de credenciales derivadas

Antes de crear directivas que requieran el uso de una credencial derivada, configure un emisor de credenciales en la consola de Intune. Un emisor de credenciales derivadas es una configuración aplicada a todo el inquilino. Los inquilinos solo admiten un emisor a la vez.

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) y vaya a **Configuración del dispositivo** > **Credenciales derivadas**.

   ![Configurar las credenciales derivadas en la consola](./media/derived-credentials/configure-provider.png)

2. Especifique un **nombre para mostrar** descriptivo para la directiva del emisor de credenciales derivadas.  Este nombre no se mostrará a los usuarios del dispositivo.

3. En **Emisor de credenciales derivadas**, seleccione el emisor de credenciales derivadas que ha elegido para su inquilino:
   - DISA Purebred
   - Entrust Datacard
   - Intercede  

4. Especifique una **dirección URL de ayuda de credenciales derivadas** para proporcionar un vínculo a una ubicación que incluya instrucciones personalizadas para ayudar a los usuarios a obtener las credenciales derivadas para su organización. Las instrucciones deben ser específicas de su organización y del flujo de trabajo necesario para obtener una credencial del emisor elegido. El vínculo aparece en la aplicación Portal de empresa y debe ser accesible desde el dispositivo.

   Si no especifica su propia dirección URL, Intune proporcionará un vínculo a los detalles genéricos que no pueden cubrir todos los escenarios. Puede que esta guía genérica no sea precisa para su entorno.

5. Seleccione una o más opciones para **Tipo de notificación**. Los tipos de notificación son los métodos que se usan para informar a los usuarios sobre los siguientes escenarios:

   - Inscribir un dispositivo con un emisor para obtener una credencial derivada nueva.
   - Obtener una credencial derivada nueva cuando la credencial actual está a punto de vencer.
   - Usar una credencial derivada con una directiva para la autenticación de Wi-Fi, VPN, correo electrónico o aplicación, así como para la firma S/MIME y el cifrado.

6. Cuando esté a punto, seleccione **Guardar** para completar la configuración del emisor de credenciales derivadas.

Después de guardar la configuración, puede hacer cambios en todos los campos excepto en *Emisor de credenciales derivadas*.  Para cambiar el emisor, vea [Cambiar el emisor de credenciales derivadas](#change-the-derived-credential-issuer).

## <a name="deploy-the-disa-purebred-app"></a>Implementar la aplicación DISA Purebred

*Esta sección solo se aplica si se usa DISA Purebred*.

Para usar **DISA Purebred** como emisor de credenciales derivadas para Intune, debe obtener la aplicación DISA Purebred y, después, usar Intune para implementar la aplicación en los dispositivos. Los usuarios del dispositivo usan la aplicación en su dispositivo para solicitar la credencial derivada de DISA Purebred.

Además de implementar la aplicación con Intune, configure una VPN por aplicación de Intune para la aplicación DISA Purebred.

**Lleve a cabo las siguientes tareas**:
  
1. Descargue la [aplicación DISA Purebred](https://cyber.mil/pki-pke/purebred/).
2. Implemente la aplicación DISA Purebred en Intune.  Vea [Incorporación de una aplicación de línea de negocio de iOS a Microsoft Intune](../apps/lob-apps-ios.md).
3. [Cree una VPN por aplicación](../configuration/vpn-settings-configure.md) para la aplicación DISA Purebred.

## <a name="use-derived-credentials-for-authentication-and-smime-signing-and-encryption"></a>Usar credenciales derivadas para la autenticación, la firma S/MIME y el cifrado

Puede especificar **credenciales derivadas** para los tipos de perfil y propósitos siguientes:

- [Aplicaciones](#use-derived-credentials-for-app-authentication)
- [Correo electrónico](../configuration/email-settings-ios.md)
- [VPN](../configuration/vpn-settings-ios.md)
- [Firma S/MIME y cifrado](certificates-s-mime-encryption-sign.md)
- [Wi-Fi](../configuration/wi-fi-settings-ios.md)

  En el caso de los perfiles de Wi-Fi, el *método de autenticación* solo está disponible si el **tipo de EAP** está establecido en uno de los siguientes valores:
  - EAP: TLS
  - EAP-TTLS
  - PEAP

### <a name="use-derived-credentials-for-app-authentication"></a>Usar credenciales derivadas para la autenticación de aplicaciones

Use credenciales derivadas para la autenticación basada en certificados en sitios web y aplicaciones. Para proporcionar una credencial derivada para la autenticación de aplicaciones, siga estos pasos en la consola de Intune:  

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), vaya a **Configuración del dispositivo** > **Perfiles** y seleccione **Crear perfil**.

2. Escriba un nombre descriptivo para el perfil en **Nombre**.

3. Para **Plataforma**, seleccione **iOS**.

4. En **Tipo de perfil**, seleccione **Credencial derivada**.

5. Seleccione **Aceptar** y, a continuación, haga clic en **Crear**.

6. Seleccione **Asignaciones** para elegir los grupos que deben recibir la directiva.
 
Los usuarios reciben la notificación por correo electrónico o de la aplicación en función de la configuración que haya especificado al configurar el emisor de credenciales derivadas. La notificación informa al usuario de que debe iniciar el Portal de empresa para que se puedan procesar las directivas de credenciales derivadas.

## <a name="renew-a-derived-credential"></a>Renovar una credencial derivada

Las credenciales derivadas no se pueden ampliar ni renovar; los usuarios deben usar el flujo de trabajo de solicitud de credenciales para solicitar una credencial derivada nueva para su dispositivo.

Si configura uno o varios métodos para el **tipo de notificación**, Intune notificará automáticamente a los usuarios cuando la credencial derivada actual haya alcanzado el 80% de su ciclo de vida. La notificación dirige a los usuarios al proceso de solicitud de credenciales para obtener una nueva credencial derivada.

Una vez que un dispositivo recibe una nueva credencial derivada, las directivas que usan credenciales derivadas se reimplementan en ese dispositivo.


## <a name="change-the-derived-credential-issuer"></a>Cambiar el emisor de credenciales derivadas

En el nivel de inquilino puede cambiar el emisor de credenciales, aunque solo se admite un emisor por inquilino a la vez.

Después de cambiar el emisor, se solicitará a los usuarios que obtengan una nueva credencial derivada del emisor nuevo. Deben hacerlo antes de poder usar una credencial derivada para la autenticación.

### <a name="change-the-issuer-for-your-tenant"></a>Cambiar el emisor de su inquilino

> [!IMPORTANT]  
> Si elimina un emisor y acto seguido vuelve a configurar ese mismo emisor, deberá actualizar los perfiles y dispositivos para usar las credenciales derivadas de ese emisor. Las credenciales derivadas obtenidas antes de eliminar el emisor ya no son válidas.

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) y vaya a **Configuración del dispositivo** > **Credenciales derivadas**.

2. Seleccione **Eliminar** para quitar el emisor de credenciales derivadas actual.

3. Configure un nuevo emisor.

### <a name="update-profiles-that-use-derived-credentials"></a>Actualizar los perfiles que usan credenciales derivadas

Después de eliminar un emisor y de agregar uno nuevo, edite todos los perfiles que usen credenciales derivadas. Esta regla se aplica incluso si se restaura el emisor anterior. Cualquier edición del perfil desencadenará una actualización, incluida una simple edición en la *descripción* del perfil.

### <a name="update-derived-credentials-on-devices"></a>Actualizar las credenciales derivadas en los dispositivos

Después de eliminar un emisor y de agregar uno nuevo, los usuarios del dispositivo deben solicitar una nueva credencial derivada. Esta regla se aplica incluso si se agrega el mismo emisor que se ha quitado. El proceso para solicitar la nueva credencial derivada es el mismo que para inscribir un dispositivo nuevo o renovar una credencial existente.

## <a name="next-steps"></a>Pasos siguientes

[Creación de perfiles de configuración de dispositivo](../configuration/device-profile-create.md)
