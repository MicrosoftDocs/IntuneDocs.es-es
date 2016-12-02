---
title: "Acceso al correo electrónico corporativo mediante perfiles de correo electrónico | Microsoft Intune"
description: "Las opciones de configuración de perfil de correo electrónico se pueden usar para configurar el acceso al correo de determinados clientes de correo en dispositivos móviles."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 10f0cd61-e514-4e44-b13e-aeb85a8e53ae
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f0c5920f7cc46e40bf4d1795a68ba1d67840fcfa
ms.openlocfilehash: 6ac7034ba0713c7b6bdd28c7b53b99c247d3aeb3


---

# <a name="configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune"></a>Configurar el acceso al correo electrónico corporativo mediante perfiles de correo electrónico con Microsoft Intune

[!INCLUDE[wit_nextref](../includes/afw_rollout_disclaimer.md)]

Muchas plataformas móviles incluyen un cliente de correo electrónico nativo que se suministra como parte del sistema operativo. Algunos de estos clientes se pueden configurar con perfiles de correo electrónico, como se describe en este tema.

Las opciones de configuración del perfil de correo electrónico se pueden usar para configurar las opciones del acceso al correo de determinados clientes de correo electrónico en dispositivos móviles. En las plataformas compatibles, Microsoft Intune puede configurar los clientes de correo electrónico nativos para permitir que los usuarios puedan tener acceso al correo electrónico corporativo en sus dispositivos personales sin necesidad de configurar nada más.

Si necesita tomar medidas adicionales para la prevención de pérdida de datos, use [Acceso condicional](restrict-access-to-email-and-o365-services-with-microsoft-intune.md), que controla el acceso al buzón del usuario de cualquier cliente de correo electrónico, incluidos los clientes de correo electrónico nativos.

Los usuarios o los administradores de TI también pueden optar por instalar otros clientes de correo electrónico (por ejemplo, Microsoft Outlook para Android o iOS). Puede que estos clientes de correo electrónico no admitan perfiles de correo y no puedan configurarse mediante perfiles de correo electrónico de Intune.  

Puede usar perfiles de correo electrónico para configurar el cliente de correo nativo en los siguientes tipos de dispositivo:
-   Windows Phone 8.1 y versiones posteriores
-   Windows 10 (para el escritorio), Windows 10 Mobile y versiones posteriores
-   iOS 8.0 y versiones posteriores
-   Samsung KNOX Standard (4.0 y posterior)
-   Android for Work

>[!NOTE]
>Intune proporciona dos perfiles de correo electrónico de Android for Work, uno para cada una de las aplicaciones de correo electrónico de Gmail y de Nine Work. Estas aplicaciones están disponibles en Google Play Store y admiten conexiones a Exchange. Para habilitar la conectividad de correo electrónico, implemente una de estas aplicaciones de correo electrónico en los dispositivos de los usuarios y, después, cree e implemente el perfil adecuado.

Además de configurar una cuenta de correo electrónico en el dispositivo, también puede configurar la cantidad de correo electrónico que se sincronizará y, en función del tipo de dispositivo, los tipos de contenido que se sincronizarán.

>[!NOTE]
>
>Si el usuario ha instalado un perfil de correo electrónico antes de la configuración de un perfil mediante Intune, el resultado de la implementación del perfil de correo electrónico de Intune depende de la plataforma del dispositivo:

>**iOS**: se detecta un perfil de correo electrónico existente duplicado basándose en el nombre de host y la dirección de correo electrónico. El perfil de correo electrónico duplicado que ha creado el usuario bloquea la implementación de un perfil de Intune creado por el administrador. Este es un problema común, ya que los usuarios de iOS suelen crear un perfil de correo electrónico y luego inscribirse. El Portal de empresa informa al usuario de que no es compatible debido a su perfil de correo electrónico configurado manualmente y solicita al usuario que quite ese perfil. El usuario debe quitar su perfil de correo electrónico para que el perfil de Intune pueda configurarse. Para evitar el problema, indique a los usuarios que se inscriban antes de instalar un perfil de correo electrónico y que permitan que Intune configure el perfil.

>**Windows**: se detecta un perfil de correo electrónico existente duplicado basándose en el nombre de host y la dirección de correo electrónico. Intune sobrescribe el perfil de correo electrónico existente que ha creado el usuario.

>**Samsung KNOX**: se detecta un perfil de correo electrónico existente duplicado basándose en la dirección de correo electrónico y se sobrescribe con el perfil de Intune. Si el usuario configura esa cuenta, se sobrescribe de nuevo mediante el perfil de Intune. Tenga en cuenta que esto puede provocar confusión en el usuario.

>Como Samsung KNOX no usa el nombre de host para identificar el perfil, recomendamos que no cree varios perfiles de correo electrónico para usarlos en la misma dirección de correo electrónico en diferentes hosts, ya que estos se sobrescriben entre sí.

>**Android for Work**: el perfil de Intune solo se aplica a aplicaciones de correo electrónico específicas en el perfil de trabajo del dispositivo y no afecta a la configuración de correo electrónico del perfil de usuario del dispositivo.


## <a name="secure-email-profiles"></a>Proteger los perfiles de correo electrónico
Los perfiles de correo electrónico se pueden proteger mediante un certificado o una contraseña.

### <a name="certificates"></a>Certificados
Cuando se crea el perfil de correo electrónico, puede elegir un perfil de certificado creado previamente en Intune. Esto se conoce como certificado de identidad y sirve para autenticarse con un perfil de certificado de confianza (o un certificado raíz) para establecer que el dispositivo del usuario tenga permiso para conectarse. El certificado de confianza se implementa en el equipo que autentica la conexión de correo electrónico (que suele ser el servidor de correo nativo).

Para más información sobre cómo crear y usar perfiles de certificado en Intune, vea [Secure resource access with certificate profiles](secure-resource-access-with-certificate-profiles.md) (Proteger el acceso a recursos con perfiles de certificado).

### <a name="user-name-and-password"></a>Nombre de usuario y contraseña
El usuario se autentica en el servidor de correo nativo al proporcionar su nombre de usuario y contraseña.

La contraseña no está incluida en el perfil de correo electrónico, por lo que el usuario necesita proporcionarla al conectarse al correo electrónico.

### <a name="create-an-email-profile"></a>Crear un perfil de correo electrónico

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), seleccione **Directiva** &gt; **Agregar directiva**.

2.  Configure uno de los siguientes tipos de directivas:

    -   **Perfil de correo electrónico para Samsung KNOX estándar (4.0 y versiones posteriores)**

    -   **Perfil de correo electrónico (iOS 8.0 y versiones posteriores)**

    -   **Perfil de correo electrónico (Windows Phone 8.1 y versiones posteriores)**

    -   **Perfil de correo electrónico (Windows 10 Escritorio y Windows 10 Mobile y versiones posteriores)**

    -   **Perfil de correo electrónico (Android for Work - Gmail)**

    -   **Perfil de correo electrónico (Android for Work - Nine Work)**

    Solo puede crear e implementar una directiva de perfiles de correo electrónico personalizada. La configuración recomendada no está disponible.

3.  Use la tabla siguiente para que le resulte más fácil configurar las opciones del perfil de correo electrónico:

|Nombre de la configuración | Más información|
| ----------- | --------------- |
    |**Nombre**|Nombre único del perfil de correo electrónico.|
    |**Descripción**|Una descripción que le ayudará a identificar este perfil.|
    |**Host**|El nombre de host del servidor de la compañía que hospeda el servicio de correo electrónico nativo.|
    |**Nombre de cuenta**|Nombre para mostrar de la cuenta de correo electrónico tal y como aparecerá para los usuarios en sus dispositivos.|
    |**Nombre de usuario**|Es el atributo de Active Directory (AD) o Azure AD que se usará para generar el nombre de usuario de este perfil de correo electrónico. Seleccione la dirección SMTP principal, como *user1@contoso.com*, o el nombre principal de usuario, como *usuario1* o *user1@contoso.com*.|
    |**Dirección de correo electrónico**|Modo en que se genera la dirección de correo electrónico para el usuario en cada dispositivo. Seleccione **Dirección SMTP primaria** para usar la dirección SMTP primaria para iniciar sesión en Exchange o **Nombre principal de usuario** para usar el nombre principal completo como dirección de correo electrónico.|
    |**Método de autenticación** (Android for Work, Samsung KNOX e iOS)|Seleccione **Nombre de usuario y contraseña** o **Certificados** como método de autenticación que usa el perfil de correo electrónico.|
    |**Seleccionar un certificado de cliente para la autenticación de cliente (certificado de identidad)** (Android for Work, Samsung KNOX e iOS)|Seleccione el certificado SCEP de cliente que creó previamente y que se utilizará para autenticar la conexión de Exchange. Para más información sobre cómo usar perfiles de certificado en Intune, vea [Secure resource access with certificate profiles](secure-resource-access-with-certificate-profiles.md) (Proteger el acceso a recursos con perfiles de certificado). Esta opción solo se muestra cuando el método de autenticación es **Certificados**.|
    |**Usar S/MIME** (Samsung KNOX e iOS)|Enviar correo electrónico saliente mediante cifrado S/MIME.|
    |**Certificado de firma** (Samsung KNOX e iOS)|Seleccione el certificado de firma que se utilizará para firmar el correo electrónico saliente. Esta opción se muestra solo cuando se selecciona **Usar S/MIME**.|
    |**Número de días de correo electrónico para sincronizar**|El número de días de correo electrónico que quiere sincronizar o seleccione **Sin límite** para sincronizar todo el correo electrónico disponible.|
    |**Programación de sincronización** (Android for Work, Samsung KNOX, Windows Phone 8 y versiones posteriores, Windows 10)|Seleccione la programación por la que los dispositivos sincronizarán los datos del servidor Exchange. También puede seleccionar **Cuando llegan los mensajes** (los datos se sincronizan tan pronto como llegan) o **Manual** (el usuario del dispositivo debe iniciar la sincronización).|
    |**Usar SSL**|Usa la comunicación de Capa de sockets seguros (SSL) al enviar correos electrónicos, recibir correos electrónicos y comunicarse con el servidor Exchange. En dispositivos que ejecutan Samsung KNOX 4.0 o versiones posteriores, es necesario exportar el certificado SSL de Exchange Server e implementarlo como un perfil de certificado de confianza de Android en Intune. En Intune no se puede tener acceso a este certificado si se ha instalado en el servidor Exchange por otros medios.|
    |**Tipo de contenido que se va a sincronizar** (todas las plataformas excepto Gmail de Android for Work)|Seleccione los tipos de contenido que quiere sincronizar con los dispositivos.|
    |**Permitir el envío de correo electrónico desde aplicaciones de terceros** (solo iOS)|Permitir que el usuario seleccione este perfil como la cuenta predeterminada para enviar correo electrónico y permitir que aplicaciones de terceros abran el correo electrónico en la aplicación de correo electrónico nativa, por ejemplo, para adjuntar archivos a un correo electrónico.|

> [!IMPORTANT]
>
> Si ha implementado un perfil de correo electrónico y, luego, quiere cambiar los valores de **Host** o **Dirección de correo electrónico**, deberá eliminar el perfil de correo electrónico existente y crear otro con los valores necesarios.

4.  Cuando haya terminado haga clic en **Guardar directiva**.

La nueva directiva se muestra en el nodo **Directivas de configuración** del área de trabajo **Directiva** .

## <a name="deploy-the-policy"></a>Implementar la directiva

1.  En el área de trabajo **Directiva**, seleccione la directiva que quiera implementar y, después, elija **Administrar la implementación**.

2.  En el cuadro de diálogo **Administrar la implementación** :

    -   **Para implementar la directiva**: seleccione uno o más grupos en los que quiera implementarla y, luego, elija **Agregar** &gt; **Aceptar**.

    -   **Para cerrar el cuadro de diálogo sin implementarla:** seleccione **Cancelar**.

En el área de trabajo **Directiva** de la página **General** , un resumen de estado y las alertas identifican los problemas de la directiva que requieren su atención. Además, aparece un resumen de estado en el área de trabajo Panel.

> [!NOTE]
> - En el caso de Android for Work, asegúrese de que también implementa las aplicaciones Gmail o Nine Work, además del perfil de correo electrónico adecuado.
> - Si desea quitar un perfil de correo electrónico de un dispositivo, edite la implementación y quite los grupos de los que sea miembro el dispositivo.



<!--HONumber=Nov16_HO3-->


