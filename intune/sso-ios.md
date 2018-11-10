---
title: 'Agregar el inicio de sesión único para dispositivos iOS en Microsoft Intune: Azure | Microsoft Docs'
description: En Microsoft Intune, puede crear, configurar o habilitar dispositivos iOS de modo que usen el inicio de sesión único (SSO) en lugar de una contraseña para la autenticación en los recursos y los datos de la organización. Para usar el SSO, cree un perfil de configuración de dispositivo y especifique el UPN, el identificador del dispositivo, las aplicaciones y un certificado para autenticar al usuario y el dispositivo.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d1add113222c2aa7eaea10679c329e877b1a136f
ms.sourcegitcommit: 437eaf364c3b8a38d294397310c770ea4d8a8015
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2018
ms.locfileid: "49992016"
---
# <a name="use-single-sign-on-ios-device-in-microsoft-intune"></a>Usar el inicio de sesión único para dispositivos iOS en Microsoft Intune

La mayoría de las aplicaciones de línea de negocio (LOB) necesita cierto nivel de autenticación de usuario para ofrecer seguridad. En muchos casos, esta autenticación exige que el usuario escriba las mismas credenciales varias veces, lo que puede resultarle frustrante. Para mejorar la experiencia del usuario, los desarrolladores pueden crear aplicaciones que usen el inicio de sesión único (SSO), con lo que se reduce el número de veces que un usuario debe escribir las credenciales.

En este artículo se muestra cómo activar el inicio de sesión único para dispositivos iOS mediante un perfil de configuración de dispositivo en Microsoft Intune.

## <a name="before-you-begin"></a>Antes de comenzar

Asegúrese de que dispone de una aplicación programada para buscar el almacén de credenciales del usuario en la carga de inicio de sesión único en el dispositivo iOS.

## <a name="create-the-sso-profile"></a>Creación del perfil de SSO

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba los valores siguientes:

    - **Nombre**: escriba un nombre para el perfil, como `ios sso profile`.
    - **Descripción**: escriba una descripción con términos clave que le ayuden a encontrar el perfil en la lista.
    - **Plataforma**: elija **iOS**.
    - **Tipo de perfil**: elija **Características del dispositivo**.

4. Seleccione **Inicio de sesión único**.

    ![Panel Inicio de sesión único](./media/sso-blade.png)

5. Escriba los valores siguientes: 

    - **Username attribute from AAD** (Atributo de nombre de usuario de AAD): Intune busca este atributo para cada usuario de Azure AD. Después, Intune rellena el campo correspondiente (como UPN) antes de generar la carga XML que se instala en el dispositivo. Las opciones son:
    
        - **Nombre principal de usuario**: se analiza el UPN de la manera siguiente:

            ![Atributo de nombre de usuario](media/User-name-attribute.png)

            También puede sobrescribir el dominio kerberos con el texto que escriba en el cuadro de texto **Dominio kerberos**.

            Por ejemplo, Contoso podría tener varias subregiones como Europa, Asia y Norteamérica. Podría querer que los usuarios de Asia usaran la carga de SSO y que la aplicación exigiera el UPN con el formato `username@asia.contoso.com`. En este caso, si selecciona **Nombre principal de usuario**, de forma predeterminada, el dominio kerberos de cada usuario se toma de Azure AD, que puede ser *contoso.com*. Así, especialmente para los usuarios de Asia, puede crear esta carga y sobrescribir el dominio kerberos con el valor *asia.contoso.com*. Ahora el UPN del usuario final se convierte en username@asia.contoso.com y no en username@contoso.com.

        - **Identificador de dispositivo de Intune**: Intune selecciona automáticamente el identificador de dispositivo de Intune. 

            De forma predeterminada, las aplicaciones solo tienen que usar el identificador de dispositivo. Pero si la aplicación usa el dominio kerberos *y* el identificador de dispositivo, puede escribir el dominio kerberos en el cuadro de texto **Dominio kerberos**.

            > [!NOTE]
            > Si usa el identificador de dispositivo, mantenga vacío el dominio kerberos de forma predeterminada.

    - **Dominio kerberos**: parte de dominio de la dirección URL.
    
    - **URL prefixes that will use Single Sign On** (Prefijos de dirección URL que usarán el inicio de sesión único): **agregue** cualquier dirección URL de la organización que exija la autenticación de inicio de sesión único. 

        Por ejemplo, cuando un usuario se conecta a alguno de estos sitios, el dispositivo iOS usa las credenciales de inicio de sesión único. El usuario no tiene que escribir otras credenciales. Pero si tiene habilitada la autenticación multifactor, los usuarios tienen que escribir la segunda autenticación.

        > [!NOTE]
        > Estas direcciones URL deben tener el formato FQDN correcto. Apple exige que las direcciones URL tengan el formato `http://<yourURL.domain>`.

        Los patrones de coincidencia de la dirección URL deben comenzar por `http://` o `https://`. Se realiza una coincidencia de cadena simple, así que el prefijo de URL `http://www.contoso.com/` no coincide con `http://www.contoso.com:80/`. Pero con iOS 10.0 o versiones posteriores, se puede usar un único carácter comodín \* para especificar todos los valores coincidentes. Por ejemplo, `http://*.contoso.com/` coincide con `http://store.contoso.com/` y con `http://www.contoso.com`.

        Los patrones `http://.com` y `https://.com` coinciden con todas las direcciones URL HTTP y HTTPS, respectivamente.
    
    - **Apps that will use Single Sign On** (Aplicaciones que usarán el inicio de sesión único): **agregue** las aplicaciones de los dispositivos de los usuarios finales que pueden usar el inicio de sesión único. 

        La matriz `AppIdentifierMatches` debe contener cadenas que coincidan con los identificadores del lote de aplicaciones. Estas cadenas pueden ser coincidencias exactas (como `com.contoso.myapp`) o pueden especificar una coincidencia de prefijo en el identificador de lote mediante el carácter comodín \*. El carácter comodín debe aparecer después de un carácter de punto (.) y solo puede hacerlo una vez, al final de la cadena (por ejemplo: `com.contoso.*`). Cuando se incluye un carácter comodín, se concede acceso a la cuenta a cualquier aplicación cuyo identificador de lote empiece por el prefijo.

        Use **Nombre de la aplicación** para especificar un nombre descriptivo que ayude a identificar el identificador de lote.
    
    - **Certificado de renovación de credenciales**: si usa certificados para la autenticación (no contraseñas), seleccione el certificado SCEP o PFX implementado para el usuario como certificado de autenticación. Normalmente se trata del mismo certificado implementado para el usuario para otros perfiles como VPN, Wi-Fi o correo electrónico.

6. Seleccione **Aceptar** > **Aceptar** > **Crear** para guardar los cambios y crear el perfil. Una vez que lo haya creado, se mostrará en la lista **Configuración del dispositivo - Perfiles**. 

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre la configuración de características de dispositivos, vea [Configuración de características de dispositivos en Microsoft Intune](device-features-configure.md).

[Asigne este perfil](device-profile-assign.md) a los dispositivos iOS.
