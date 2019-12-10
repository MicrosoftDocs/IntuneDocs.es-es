---
title: Configuración de S/MIME con Outlook para iOS en Microsoft Intune
description: Uso de S/MIME con Outlook para iOS en Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lance
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1b2f483415d050486ae9979899d9308154a9b131
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2019
ms.locfileid: "74411364"
---
# <a name="configure-smime-with-outlook-for-ios"></a>Configuración de S/MIME con Outlook para iOS

Las extensiones seguras y multipropósito de correo Internet (S/MIME) ofrecen una capa de seguridad adicional para el correo electrónico que se envía a y desde una cuenta de Exchange ActiveSync (EAS). [Microsoft Outlook](https://aka.ms/omsmime) puede usar S/MIME para permitir que los usuarios cifren mensajes salientes y datos adjuntos, lo que garantiza que solo el destinatario previsto pueda leer el contenido del mensaje y acceder a este al usar cuentas de Office 365. Los usuarios también pueden firmar digitalmente un mensaje, lo que permite a los destinatarios comprobar la identidad del remitente y confirmar que el mensaje no se ha alterado. Esta funcionalidad es posible mediante el uso de certificados. Para más información, consulte [Uso de S/MIME](https://docs.microsoft.com/previous-versions/tn-archive/aa995740(v=exchg.65)?redirectedfrom=MSDN).

> [!NOTE]
> En este tema se describe cómo implementar certificados raíz de confianza mediante el [Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431). El Administrador de puntos de conexión de Microsoft es una plataforma de administración de puntos de conexión única e integrada para la administración de todos los puntos de conexión. Este Centro de administración del Administrador de puntos de conexión de Microsoft integra ConfigMgr y Microsoft Intune.

## <a name="about-message-encryption"></a>Sobre el cifrado de mensajes
Los usuarios pueden enviar un mensaje cifrado a las personas de dentro y fuera de su organización si tienen la parte pública de los certificados de cifrado. Las claves privadas asociadas a los certificados de cifrado siempre deben estar protegidas por el destinatario del mensaje cifrado. El destinatario usa la clave privada del certificado de cifrado para descifrar el mensaje.

Solo los destinatarios que tienen el certificado correspondiente al que cifró el mensaje pueden leer los mensajes cifrados. Si intenta enviar un mensaje cifrado a destinatarios cuyo certificado de cifrado no está disponible, la aplicación le pedirá que quite estos destinatarios para poder enviar el correo electrónico.

## <a name="about-digital-signatures"></a>Sobre las firmas digitales
Un mensaje firmado digitalmente garantiza al destinatario que el mensaje no se ha alterado y que la identidad del remitente es auténtica. Los destinatarios solo pueden comprobar la firma digital si usan un cliente de correo electrónico que admite S/MIME.

## <a name="prerequisites"></a>Requisitos previos
- Outlook para iOS solo admite S/MIME en cuentas de Office 365.
- S/MIME se debe configurar para Office 365. Para más información, consulte [Configuración de S/MIME en Office 365](https://techcommunity.microsoft.com/t5/Exchange-Team-Blog/How-to-Configure-S-MIME-in-Office-365/ba-p/584516).
- Debe tener una entidad de certificación que pueda emitir certificados que se puedan usar para la firma y el cifrado.
- Implemente certificados raíz de confianza mediante el Administrador de puntos de conexión. Para más información, consulte [Creación de perfiles de certificado de confianza](~/protect/certificates-configure.md#create-trusted-certificate-profiles).
- Los certificados de cifrado se deben importar en el Administrador de puntos de conexión. Para más información, consulte [Configuración y uso de certificados PKCS importados con Intune](~/protect/certificates-imported-pfx-configure.md).
- Instale y configure el conector PFX para Microsoft Intune. Para más información, consulte [Descarga, instalación y configuración del conector de certificado PFX para Microsoft Intune](~/protect/certificates-imported-pfx-configure.md#download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune).
- Los dispositivos deben estar inscritos en MDM para recibir certificados S/MIME y raíz de confianza de manera automática del Administrador de puntos de conexión.

> [!IMPORTANT]
> Debe descargar e instalar el conector PFX actualizado (versión 6.1911.11.0 o posterior) de Microsoft Intune para usar certificados de cifrado S/MIME con Outlook para iOS.

## <a name="smime-support-in-outlook-for-ios"></a>Compatibilidad con S/MIME en Outlook para iOS
Outlook para iOS admite la firma S/MIME y el cifrado de mensajes mediante certificados. Muchos clientes tienen certificados de firma y cifrado independientes, en lugar de un único certificado que admita tanto la firma como el cifrado. Los certificados de firma suelen ser únicos en los dispositivos inscritos de un usuario, mientras que los certificados de cifrado se comparten entre los dispositivos de un mismo usuario. Lo normal es que los usuarios hayan usado S/MIME durante años y distintos certificados de cifrado a lo largo del tiempo a medida que se renuevan los certificados. Los historiales de certificados de cifrado, incluidas sus claves privadas, deben estar presentes en el dispositivo del usuario para que se pueda leer el correo electrónico que se haya cifrado con cualquiera de esos certificados en el pasado. También es posible tener un solo certificado que admita la firma y el cifrado.

Outlook para iOS admite dos maneras de entregar certificados en los dispositivos para que se puedan usar con S/MIME:

- Los **usuarios** pueden enviarse por correo electrónico certificados S/MIME e instalarlos a partir de datos adjuntos en Outlook para iOS en sus dispositivos móviles.
- Los **administradores** pueden importar historiales de certificados de cifrado de cualquier entidad de certificación al Administrador de puntos de conexión. Después, el Administrador de puntos de conexión entregará automáticamente esos certificados a cualquier dispositivo que inscriba el usuario. Por lo general, se usa el Protocolo de inscripción de certificados simple (SCEP) en los certificados de firma. Con SCEP, la clave privada se genera y se almacena en el dispositivo inscrito y se entrega un certificado único a cada dispositivo que inscriba un usuario, que se puede usar para el no rechazo. Los administradores importan historiales de certificados de cifrado de sus usuarios al Administrador de puntos de conexión, quien entrega luego todos los certificados de cifrado del usuario a cualquier dispositivo que inscriban. Por último, el Administrador de puntos de conexión admite credenciales derivadas para clientes que necesitan compatibilidad con el estándar NIST 800-157. En iOS, el Portal de empresa se usa para recuperar certificados de firma y cifrado de Intune.

## <a name="configuring-outlook-for-ios-smime-in-endpoint-manager"></a>Configuración de S/MIME de Outlook para iOS en el Administrador de puntos de conexión
Para configurar S/MIME de Outlook para iOS en el Administrador de puntos de conexión, incluida la entrega automática de certificados S/MIME que puede usar Outlook para iOS, siga estos pasos:

### <a name="add-the-microsoft-outlook-app"></a>Adición de la aplicación Microsoft Outlook
1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Agregue la aplicación Microsoft Outlook para iOS de la App Store al Administrador de puntos de conexión o sincronice Outlook para iOS desde el Programa de Compras por Volumen de Apple. Para más información, consulte [Incorporación de aplicaciones de la tienda iOS a Microsoft Intune](~/apps/store-apps-ios.md) o [Administración de aplicaciones de iOS y macOS compradas a través del Programa de Compras por Volumen de Apple con Microsoft Intune](~/apps/vpp-apps-ios.md).

### <a name="create-the-outlook-for-ios-smime-configuration-policy"></a>Creación de la directiva de configuración de S/MIME de Outlook para iOS

Los pasos siguientes le permiten crear y configurar la directiva de S/MIME de Outlook para iOS en el Administrador de puntos de conexión. Esta configuración proporciona la entrega automatizada de los certificados de firma y cifrado.

1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), seleccione **Aplicaciones** > **Directivas de configuración de aplicaciones** > **Agregar**.<br>
Se mostrará el panel **Agregar directiva de configuración**.
2. Rellene los campos **Nombre** y **Descripción** de la directiva de configuración.
3. En **Tipo de inscripción del dispositivo**, seleccione **Dispositivos administrados**.
4. En **Plataforma**, seleccione **iOS/iPadOS**.
5. Haga clic en **Seleccionar la aplicación requerida** para buscar y asociar la aplicación Microsoft Outlook para iOS que agregó anteriormente. 
6. Haga clic en **Opciones de configuración** para agregar las opciones de configuración. 
    - Seleccione **Usar diseñador de configuraciones** junto a **Formato de opciones de configuración** y acepte los valores predeterminados. Para más información, vea [Opciones de configuración de Microsoft Outlook](~/apps/app-configuration-policies-outlook.md).
7. Haga clic en **S/MIME** para mostrar **Configuración de S/MIME de Outlook**.

    ![Captura de pantalla de la configuración de S/MIME de Outlook para iOS](./media/app-configuration-policies-outlook-smime/app-configuration-policies-outlook-smime-01.png)

8. Establezca **Habilitar S/MIME** en **Sí**.
9. Establezca **Implementar certificados S/MIME desde Intune** en **Sí**.
10. En **Certificados de firma** junto a **Tipo de perfil de certificado**, elija una de las siguientes opciones:
    - **SCEP**: crea un certificado, único para el dispositivo y el usuario, que Microsoft Outlook puede usar para la firma. Para ver información relacionada, consulte [Configuración de la infraestructura para admitir SCEP con Intune](~/protect/certificates-scep-configure.md) y [Creación de un perfil de certificado SCEP](~/protect/certificates-profile-scep.md#create-a-scep-certificate-profile). 
    - **Certificados PKCS importados**: usa un certificado que es único para el usuario, pero que puede compartirse entre dispositivos y que el administrador ha importado al Administrador de puntos de conexión en nombre del usuario. El certificado se entrega a cualquier dispositivo que inscribe un usuario. El Administrador de puntos de conexión seleccionará automáticamente el certificado importado que admite la firma para entregarlo al dispositivo que corresponde al usuario inscrito.
    - **Credenciales derivadas**: utiliza un certificado que ya está en el dispositivo y que se puede usar para la firma. El certificado debe recuperarse en el dispositivo mediante los flujos de credenciales derivadas de Intune.
11. En **Certificados de cifrado** junto a **Tipo de perfil de certificado**, elija una de las siguientes opciones:
    - **Certificados PKCS importados**: el administrador entrega al Administrador de puntos de conexión todos los certificados de cifrado que se han importado en los dispositivos que inscribe el usuario; el Administrador de puntos de conexión seleccionará automáticamente los certificados importados que admitan cifrado para entregarlos al dispositivo correspondiente al usuario inscrito.
    - **Credenciales derivadas**: utiliza un certificado que ya está en el dispositivo y que se puede usar para la firma. El certificado debe recuperarse en el dispositivo mediante los flujos de credenciales derivadas de Intune.
12. Junto a **Notificaciones del usuario final**, elija notificar a los usuarios finales; para ello, seleccione **Portal de empresa** o **Correo electrónico** para recuperar los certificados S/MIME de Outlook para iOS.

    En iOS, los usuarios deben usar la aplicación Portal de empresa para recuperar sus certificados S/MIME. El Administrador de puntos de conexión informará al usuario de que necesita iniciar el Portal de empresa para recuperar sus certificados S/MIME a través de la sección Notificaciones de dicho portal, una notificación push o un correo electrónico. Al hacer clic en una de las notificaciones, el usuario irá a una página de aterrizaje que le informa del progreso de la recuperación de los certificados. Una vez que se recuperan los certificados, el usuario puede usar S/MIME desde Microsoft Outlook para iOS para firmar y cifrar el correo electrónico.
    
    Las notificaciones del usuario final incluyen las siguientes opciones:
       - **Portal de empresa**: si se selecciona, los usuarios recibirán una notificación push en su dispositivo, que los llevará a la página de aterrizaje del Portal de empresa donde se recuperarán los certificados S/MIME.
        - **Correo electrónico**: envía un correo electrónico al usuario final para informarle de que necesita iniciar el Portal de empresa para recuperar sus certificados S/MIME. Si el usuario está en su dispositivo iOS inscrito cuando hace clic en el correo electrónico, se le redirigirá al Portal de empresa para recuperar su certificado.
    
13. Seleccione **Asignaciones** para asignar la directiva de configuración de aplicaciones a los grupos de Azure AD. Para más información, consulte [Asignación de aplicaciones a grupos con Microsoft Intune](~/apps/apps-deploy.md).

## <a name="next-steps"></a>Pasos siguientes

- Para obtener más información, vea [Directivas de configuración de aplicaciones para Microsoft Intune](app-configuration-policies-overview.md).
