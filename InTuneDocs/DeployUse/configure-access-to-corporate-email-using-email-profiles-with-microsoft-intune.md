---
title: "Acceso al correo electrónico corporativo mediante perfiles de correo electrónico | Microsoft Intune"
description: "Las opciones de configuración de perfil de correo electrónico se pueden usar para configurar el acceso al correo de determinados clientes de correo en dispositivos móviles."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/021/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 10f0cd61-e514-4e44-b13e-aeb85a8e53ae
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb0aeac2f94dfde50d9398b09c6b21c7ae40624
ms.openlocfilehash: cddc1a68b14520774555416dcd496a06a0f89385


---

# Configurar el acceso al correo electrónico corporativo mediante perfiles de correo electrónico con Microsoft Intune
Muchas plataformas móviles incluyen un cliente de correo electrónico *nativo* que se suministra como parte del sistema operativo.  Algunos de estos clientes se pueden configurar con perfiles de correo electrónico, cosa que veremos en este tema.

Si necesita una mayor prevención de pérdida de datos, elija [Acceso condicional](restrict-access-to-email-and-o365-services-with-microsoft-intune.md), que controla el acceso al buzón del usuario de cualquier cliente de correo, incluidos los clientes de correo nativos.

Las opciones de configuración de perfil de correo electrónico se pueden usar para configurar el acceso al correo de determinados clientes de correo en dispositivos móviles. La mayoría de las plataformas móviles incluye un cliente de correo electrónico *nativo* que se suministra como parte del sistema operativo.  En las plataformas compatibles, Microsoft Intune puede configurar los clientes de correo electrónico nativos de forma que los usuarios puedan tener acceso al correo electrónico corporativo en los dispositivos personales sin necesidad de configurar nada.  

Los usuarios o los administradores de TI también pueden optar por instalar otros clientes de correo electrónico, como Microsoft Outlook para Android o iOS.  Puede que estos clientes no admitan perfiles de correo electrónico y no sean configurables mediante perfiles de correo electrónico de Microsoft Intune.  

Puede usar perfiles de correo electrónico para configurar el cliente de correo nativo en los siguientes tipos de dispositivo:
-   Windows Phone 8 y versiones posteriores
-   Windows 10 Escritorio, Windows 10 Mobile y versiones posteriores
-   iOS 7.1 y versiones posteriores
-   Samsung KNOX Standard (4.0 y posterior)


Además de configurar una cuenta de correo electrónico en el dispositivo, también puede configurar opciones de sincronización como, por ejemplo, la cantidad de correo electrónico que se sincronizará y, en función el tipo de dispositivo, los tipos de contenido que se sincronizarán.
>[!NOTE]
>
>Si el usuario ha instalado un perfil de correo electrónico antes del aprovisionamiento de un perfil mediante Intune, el resultado de la implementación del perfil de correo electrónico de Intune depende de la plataforma del dispositivo:

>-**iOS:** Intune detecta un perfil de correo electrónico existente duplicado sobre la base del nombre de host y la dirección de correo electrónico. El perfil de correo electrónico duplicado que ha creado el usuario bloquea la implementación de un perfil de Intune creado por el administrador. Este es un problema común, ya que los usuarios de iOS suelen crear un perfil de correo y luego inscribirse. El portal de empresa informará al usuario de que no son compatibles debido a su perfil de correo configurado manualmente y le pedirá que quite ese perfil. El usuario debe quitar su perfil de correo para que se pueda implementar el perfil de Intune. Para evitar el problema, indique a los usuarios que se inscriban antes de instalar un perfil de correo y que permitan que Intune implemente el perfil.

>-**Windows:** Intune detecta un perfil de correo electrónico existente duplicado sobre la base del nombre de host y la dirección de correo electrónico. Intune sobrescribe el perfil de correo electrónico existente que ha creado el usuario.

>-**Samsung KNOX:** Intune identifica una cuenta de correo electrónico duplicada sobre la base de la dirección de correo electrónico y la sobrescribe con el perfil de Intune. Si el usuario configura esa cuenta, el perfil de Intune la vuelve a sobrescribir. Tenga en cuenta que esto puede confundir al usuario cuya configuración de cuenta se sobrescribe.

>Dado que Samsung KNOX no usa el nombre de host para identificar el perfil, recomendamos que no cree varios perfiles de correo electrónico para implementar en la misma dirección de correo electrónico en diferentes hosts, ya que estos se sobrescriben entre sí.
    

## Proteger los perfiles de correo electrónico
Los perfiles de correo electrónico se pueden proteger con uno de estos dos métodos:

### Certificados
Cuando se crea el perfil de correo electrónico, puede elegir un perfil de certificado creado previamente en Intune. Esto se conoce como certificado de identidad y sirve para autenticarse con un perfil de certificado de confianza (o un certificado raíz) para establecer que el dispositivo del usuario tiene permiso para conectarse. El certificado de confianza se implementa en el equipo que autentica la conexión de correo electrónico (que suele ser el servidor de correo nativo).

Para más información sobre cómo crear y usar perfiles de certificado en Intune, vea [Secure resource access with certificate profiles](secure-resource-access-with-certificate-profiles.md) (Proteger el acceso a recursos con perfiles de certificado).

### Nombre de usuario y contraseña
El usuario se autentica en el servidor de correo nativo proporcionando su nombre de usuario y contraseña.

La contraseña no está incluida en el perfil de correo electrónico, por lo que el usuario deberá proporcionarla al conectarse al correo electrónico.

### Crear un perfil de correo electrónico

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), haga clic en **Directiva** &gt; **Agregar directiva**.

2.  Configure uno de los siguientes tipos de directivas:

    -   **Perfil de correo electrónico para Samsung KNOX estándar (4.0 y versiones posteriores)**

    -   **Perfil de correo electrónico (iOS 7.1 y versiones posteriores)**

    -   **Perfil de correo electrónico (Windows Phone 8 y versiones posteriores)**

    -   **Perfil de correo electrónico (Windows 10 para escritorios y Windows 10 Mobile y versiones posteriores)**

    Solo puede crear e implementar una directiva de perfiles de correo electrónico personalizada. La configuración recomendada no está disponible.

3.  Tenga esta tabla como referencia para configurar las opciones del perfil de correo electrónico:
    |Nombre de la configuración|Más información|
    |----------------|-----------------------------------------------------------------------------|
    |**Nombre**|Nombre único del perfil de correo electrónico.|
    |**Descripción**|Descripción que le ayudará a identificar este perfil.|
    |**Host**|Nombre de host del servidor de la empresa que hospeda el servicio de correo electrónico nativo.|
    |**Nombre de cuenta**|Nombre para mostrar de la cuenta de correo electrónico tal y como aparecerá para los usuarios en sus dispositivos.|
    |**Nombre de usuario**|Modo en el que se obtendrá el nombre de usuario de la cuenta de correo electrónico. Seleccione **Nombre de usuario** si es un servidor de Exchange local o **Nombre principal de usuario** si es Office 365.|
    |**Dirección de correo electrónico**|Modo en que se genera la dirección de correo electrónico para el usuario en cada dispositivo. Seleccione **Dirección SMTP primaria** para usar la dirección SMTP primaria para iniciar sesión en Exchange o **Nombre principal de usuario** para usar el nombre principal completo como dirección de correo electrónico.|
    |**Método de autenticación** (Samsung KNOX e iOS)|Seleccione **Nombre de usuario y contraseña** o **Certificados** como método de autenticación que usa el perfil de correo electrónico.|
    |**Seleccionar un certificado de cliente para la autenticación del cliente (certificado de identidad)** (Samsung KNOX and iOS)|Seleccione el certificado SCEP de cliente que creó previamente y que se utilizará para autenticar la conexión de Exchange. Para más información sobre cómo usar perfiles de certificado en Intune, vea [Secure resource access with certificate profiles](secure-resource-access-with-certificate-profiles.md) (Proteger el acceso a recursos con perfiles de certificado).<br /><br />Esta opción solo se muestra cuando el método de autenticación es **Certificados**.|
    |**Usar S/MIME** (Samsung KNOX e iOS)|Enviar correo electrónico saliente mediante cifrado S/MIME.|
    |**Certificado de firma** (Samsung KNOX e iOS)|Seleccione el certificado de firma que se utilizará para firmar el correo electrónico saliente.<br /><br />Esta opción se muestra solo cuando se selecciona **Usar S/MIME**.|
    |**Número de días de correo electrónico para sincronizar**|Número de días de correo electrónico que quiere sincronizar (o bien seleccione **Sin límite** para sincronizar todo el correo electrónico disponible).|
    |**Programación de sincronización** (Samsung KNOX, Windows Phone 8 y versiones posteriores, Windows 10)|Seleccione la programación por la que los dispositivos sincronizarán los datos de Exchange Server. También puede seleccionar **Cuando llegan los mensajes** (los datos se sincronizan tan pronto como llegan) o **Manual** (el usuario del dispositivo debe iniciar la sincronización).|
    |**Usar SSL**|Use la comunicación de Capa de sockets seguros (SSL) al enviar correos electrónicos, recibir correos electrónicos y comunicarse con Exchange Server.<br /><br />En dispositivos que ejecutan Samsung KNOX 4.0 o posterior, es necesario exportar el certificado SSL de Exchange Server e implementarlo como perfil de certificado de confianza de Android en Intune. En Intune no se puede tener acceso a este certificado si se ha instalado en el servidor de Exchange Server por otros medios.|
    |**Tipo de contenido para sincronizar**|Seleccione los tipos de contenido que quiere sincronizar con los dispositivos.|
    |**Permitir el envío de correo electrónico desde aplicaciones de terceros** (solo iOS)|Permitir que un usuario seleccione este perfil como la cuenta predeterminada para enviar correo electrónico y permitir que aplicaciones de terceros abran el correo electrónico en la aplicación de correo electrónico nativa, por ejemplo, para adjuntar archivos a un correo electrónico.|

    > [!IMPORTANT]
    > Si ha implementado un perfil de correo electrónico y, luego, quiere cambiar los valores de **Host** o **Dirección de correo electrónico**, deberá eliminar el perfil de correo electrónico existente y crear otro con los valores necesarios.

4.  Cuando haya terminado haga clic en **Guardar directiva**.

La nueva directiva se muestra en el nodo **Directivas de configuración** del área de trabajo **Directiva** .

## Implementar la directiva

1.  En el área de trabajo **Directiva** , seleccione la directiva que quiera implementar y, a continuación, haga clic en **Administrar implementación**.

2.  En el cuadro de diálogo **Administrar la implementación** :

    -   **Para implementar la directiva**: seleccione uno o más grupos en los que quiera implementar la directiva y haga clic en **Agregar** &gt; **Aceptar**.

    -   **Para cerrar el cuadro de diálogo sin implementarla**: haga clic en **Cancelar**.

En el área de trabajo **Directiva** de la página **General** , un resumen de estado y las alertas identifican los problemas de la directiva que requieren su atención. Además, aparece un resumen de estado en el área de trabajo Panel.

> [!NOTE]
> Si desea quitar un perfil de correo electrónico de un dispositivo, edite la implementación y quite los grupos de los que sea miembro el dispositivo.



<!--HONumber=Aug16_HO1-->


