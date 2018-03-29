---
title: Configurar Microsoft Intune para el inicio de sesión único para dispositivos iOS
titlesuffix: ''
description: Obtenga información sobre cómo configurar Microsoft Intune para el inicio de sesión único para dispositivos iOS.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f19320df9a9728cdd77e608fc0ad219272a731f
ms.sourcegitcommit: e6319ff186d969da34bd19c9730ba003d6cce353
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2018
---
# <a name="configure-microsoft-intune-for-ios-device-single-sign-on"></a>Configurar Microsoft Intune para el inicio de sesión único para dispositivos iOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La mayoría de las aplicaciones de línea de negocio (LOB) necesita cierto nivel de autenticación de usuario para ofrecer seguridad. En muchos casos, esto exige que el usuario escriba las mismas credenciales varias veces, lo que puede resultarle frustrante. Para mejorar la experiencia del usuario, los desarrolladores pueden crear aplicaciones que usen el inicio de sesión único, con lo que se reduce el número de veces que un usuario debe proporcionar las credenciales.

Para aprovechar el inicio de sesión único para dispositivos iOS, debe cumplir las siguientes condiciones:

- Una aplicación programada para buscar el almacén de credenciales del usuario en la carga de inicio de sesión único en el dispositivo iOS.
- Intune configurado para el inicio de sesión único para dispositivos iOS.

## <a name="to-configure-intune-for-ios-device-single-sign-on"></a>Para configurar Intune para el inicio de sesión único para dispositivos iOS


1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, elija **Configuración del dispositivo**.
4. En el panel **Configuración del dispositivo**, en la sección **Administrar**, elija **Perfiles**.
5. En el panel Perfiles, elija **Crear perfil**.
6. Proporcione un nombre y una descripción, y configure los siguientes valores:
   - **Plataforma**: elija **iOS**.
   - **Tipo de perfil**: elija **Características del dispositivo**.
7. En el panel **Características del dispositivo**, elija **Inicio de sesión único**.

   ![Panel Inicio de sesión único](./media/sso-blade.png)

8. Use la siguiente tabla de resumen como ayuda para rellenar los campos del panel **Inicio de sesión único**. Para obtener detalles, vea las secciones a continuación de la tabla.

   |Campo  |Notas|
   |---------|---------|
   |**Atributo de nombre de usuario de AAD**|Atributo en el que Intune busca cada usuario en AAD y rellena el campo correspondiente (como UPN) antes de generar la carga XML que se instala en el dispositivo.|
   |**Dominio Kerberos**|Parte de dominio de la dirección URL.|
   |**Prefijos de dirección URL que usarán el inicio de sesión único**|Cualquier dirección URL de la organización que exija la autenticación de inicio de sesión único.|
   |**Aplicaciones que usarán el inicio de sesión único**|Aplicaciones del dispositivo del usuario final que usan la carga de inicio de sesión único.|
   |**Certificado de renovación de credenciales**|Si usa certificados para la autenticación, seleccione el certificado SCEP o PFX implementado para el usuario como certificado de autenticación.|

En las secciones siguientes se proporcionan más detalles sobre cada uno de los campos de la hoja Inicio de sesión único.

### <a name="username-attribute-from-aad-and-realm"></a>Atributo de nombre de usuario de AAD y Dominio kerberos

- Si se selecciona **Nombre principal del usuario** en este campo, se analiza de la siguiente forma:

   ![Atributo de nombre de usuario](media/User-name-attribute.png)

   También tiene la opción de sobrescribir el dominio kerberos con el texto que escriba en el cuadro de texto **Dominio kerberos**.

   Por ejemplo, Contoso podría tener varias subregiones como Europa, Asia y Norteamérica. Podría querer que los usuarios de Asia usaran la carga de SSO y que la aplicación exigiera el UPN con el formato *username@asia.contoso.com*. En este caso, si selecciona **Nombre principal del usuario**, de forma predeterminada, el dominio kerberos de cada usuario se toma de AAD, que puede ser simplemente *contoso.com*. Así, especialmente para los usuarios de Asia, puede crear esta carga y sobrescribir el dominio kerberos con el valor *asia.contoso.com*. Ahora el UPN del usuario final se convierte en *username@asia.contoso.com* y no en *username@contoso.com*.

- Si selecciona **Id. de dispositivo**, Intune selecciona automáticamente el identificador de dispositivo de Intune.

   De forma predeterminada, las aplicaciones solo tienen que usar el identificador de dispositivo. Pero si la aplicación usa el dominio kerberos además del identificador de dispositivo, puede escribir el dominio kerberos en el cuadro de texto **Dominio kerberos**.

   > [!NOTE]
   > Si usa el identificador de dispositivo, mantenga vacío el dominio kerberos de forma predeterminada.

### <a name="url-prefixes-that-will-use-single-sign-on"></a>Prefijos de dirección URL que usarán el inicio de sesión único

Escriba aquí cualquier dirección URL que exista en la organización que exija la autenticación de usuario.

Por ejemplo, cuando un usuario se conecta a alguno de estos sitios, el dispositivo iOS usa las credenciales de inicio de sesión único y el usuario no tiene que escribir otras credenciales. Pero si tiene habilitada la autenticación multifactor, los usuarios tienen que escribir la segunda autenticación.

> [!NOTE]
> Estas direcciones URL deben tener el formato FQDN correcto. Apple exige que tengan el formato `http://<yourURL.domain>`.

Los patrones de coincidencia de la dirección URL deben comenzar por `http://` o `https://`. Se realiza una coincidencia de cadena simple, así que el prefijo de URL `http://www.contoso.com/` no coincide con `http://www.contoso.com:80/`. Pero con iOS 9.0 o posterior, se puede usar un único carácter comodín \* para especificar todos los valores coincidentes. Por ejemplo, `http://*.contoso.com/` coincide con `http://store.contoso.com/` y con `http://www.contoso.com`.
Los patrones `http://.com` y `https://.com` coinciden con todas las direcciones URL HTTP y HTTPS, respectivamente.

### <a name="apps-that-will-use-single-sign-on"></a>Aplicaciones que usarán el inicio de sesión único

Indique qué aplicaciones del dispositivo de un usuario final pueden usar la carga de inicio de sesión único.

La matriz `AppIdentifierMatches` debe contener cadenas que coincidan con los identificadores del lote de aplicaciones. Estas cadenas pueden ser coincidencias exactas (por ejemplo, `com.contoso.myapp`) o pueden especificar una coincidencia de prefijo en el identificador del lote mediante el carácter comodín \*. El carácter comodín debe aparecer después de un carácter de punto (.) y solo puede hacerlo una vez, al final de la cadena (por ejemplo: `com.contoso.*`). Cuando se incluye un carácter comodín, se concede acceso a la cuenta a cualquier aplicación cuyo identificador de lote empiece por el prefijo.

El campo **Nombre de la aplicación** se usa para agregar un nombre descriptivo que ayude a identificar el identificador de lote.

### <a name="credential-renewal-certificate"></a>Certificado de renovación de credenciales

Si autentica a los usuarios finales con certificados (no contraseñas), use este campo para seleccionar el certificado SCEP o PFX implementado para el usuario como certificado de autenticación. Normalmente se trata del mismo certificado implementado para el usuario para otros perfiles como VPN, Wi-Fi o Correo electrónico.

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre la configuración de características de dispositivos, vea [Configuración de características de dispositivos en Microsoft Intune](device-features-configure.md).
