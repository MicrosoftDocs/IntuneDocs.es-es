---
title: 'Configuración de características de dispositivos iOS en Microsoft Intune: Azure | Microsoft Docs'
description: Consulte todas las opciones de configuración para configurar dispositivos iOS para AirPrint, el diseño de la pantalla principal, las notificaciones de aplicaciones, el dispositivo compartido, el inicio de sesión único y la configuración de filtro de contenido web en Microsoft Intune. Use estas opciones de configuración en un perfil de configuración de dispositivo para configurar dispositivos iOS para que usen estas características de Apple en su organización.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/28/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e3e0ea523d71ff036f1f23c9436c65e105328d8b
ms.sourcegitcommit: 807ab3e35f4d9ffa18655410b7d61e5e772ab348
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2019
ms.locfileid: "73057641"
---
# <a name="ios-and-ipados-device-settings-to-use-common-ios-features-in-intune"></a>Configuración de dispositivos iOS e IPadOS para usar las características comunes de iOS en Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune incluye algunas configuraciones integradas para permitir a los usuarios de iOS usar diferentes características de Apple en sus dispositivos. Por ejemplo, los administradores pueden controlar cómo los usuarios de iOS usan impresoras AirPrint, agregan aplicaciones y carpetas a la base y páginas en la pantalla principal, muestran las notificaciones de aplicación, muestran detalles de etiqueta de recursos en la pantalla de bloqueo, usan la autenticación de inicio de sesión único y autentican usuarios con certificados.

Use estas características para controlar los dispositivos iOS como parte de la solución de administración de dispositivos móviles (MDM).

En este artículo se enumeran estas opciones de configuración y se describe lo que hace cada una de ellas. Para obtener más información sobre estas características, vaya a [Agregar configuración de características de dispositivos iOS o MacOS](../device-features-configure.md).

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración de dispositivo iOS](../device-features-configure.md).

> [!NOTE]
> Esta configuración se aplica a diferentes tipos de inscripción, con algunas opciones de configuración aplicables a todas las opciones de inscripción. Para obtener más información sobre los diferentes tipos de inscripción, consulte [inscripción de iOS](../ios-enroll.md).

## <a name="airprint"></a>AirPrint

### <a name="settings-apply-to-all-enrollment-types"></a>La configuración se aplica a: todos los tipos de inscripción

> [!NOTE]
> Asegúrese de agregar todas las impresoras al mismo perfil. Apple evita que varios perfiles de impresión de destino tengan el mismo dispositivo.

- **Dirección IP**: escriba la dirección IPv4 o IPv6 de la impresora. Si usa nombres de host para identificar impresoras, puede obtener la dirección IP haciendo ping a la impresora en el terminal. En la sección Obtención de la dirección IP y la ruta de acceso (en este artículo) se proporcionan más detalles.
- **Ruta de acceso**: la ruta de acceso suele ser `ipp/print` para las impresoras de la red. En la sección Obtención de la dirección IP y la ruta de acceso (en este artículo) se proporcionan más detalles.
- **Puerto**: escriba el puerto de escucha del destino de AirPrint. Si se deja esta propiedad en blanco, AirPrint usa el puerto predeterminado. Disponible en iOS 11.0 y versiones posteriores.
- **TLS**: elija **Habilitar** para proteger las conexiones AirPrint con Seguridad de la capa de transporte (TLS). Disponible en iOS 11.0 y versiones posteriores.

Para agregar servidores de impresión, puede:

- **Agregar** agrega el servidor AirPrint a la lista. Se pueden agregar muchos servidores de transimpresiones.
- **Importe** un archivo separado por comas (.csv) con esta información. O bien, **exportar** para crear una lista de los servidores de impresión de la que ha agregado.

### <a name="get-server-ip-address-resource-path-and-port"></a>Obtención de la dirección IP del servidor, la ruta de acceso de recursos y el puerto

Para agregar servidores AirPrinter, necesita la dirección IP de la impresora, la ruta de acceso de recursos y el puerto. Los pasos siguientes muestran cómo obtener esta información.

1. En un equipo Mac conectado a la misma red local (subred) que las impresoras AirPrint, abra **Terminal** (en **/Aplicaciones/Utilidades**).
2. En Terminal, escriba `ippfind` y seleccione Entrar.

    Anote la información de la impresora. Por ejemplo, puede devolver algo parecido a `ipp://myprinter.local.:631/ipp/port1`. La primera parte es el nombre de la impresora. La última parte (`ipp/port1`) es la ruta de acceso del recurso.

3. En Terminal, escriba `ping myprinter.local` y seleccione Entrar.

   Anote la dirección IP. Por ejemplo, puede devolver algo parecido a `PING myprinter.local (10.50.25.21)`.

4. Use los valores de dirección IP y de ruta de acceso del recurso. En este ejemplo, la dirección IP es `10.50.25.21` y la ruta de acceso del recurso es `/ipp/port1`.

## <a name="home-screen-layout"></a>Diseño de la pantalla principal

Esta característica se aplica a:

- iOS 9,3 o posterior

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>La configuración se aplica a: inscripción de dispositivos automatizada (supervisado)

### <a name="dock"></a>Acoplar

Use la configuración **Acoplar**, para agregar hasta seis elementos o carpetas a la base de la pantalla de iOS. Muchos dispositivos admiten menos elementos. Por ejemplo, los dispositivos iPhone admiten hasta cuatro elementos. En este caso, en el dispositivo solo se muestran los primeros cuatro elementos que agrega.

Puede agregar hasta **seis** elementos (aplicaciones y carpetas combinadas) para la base del dispositivo.

- **Agregar**: agregue aplicaciones o carpetas a la base del dispositivo.
- **Tipo**: agregue una **aplicación** o una **carpeta**:

  - **Aplicación**: elija esta opción para agregar aplicaciones a la base en la pantalla. Introduzca:

    - **Nombre de la aplicación**: especifique un nombre para la aplicación. Este nombre se usa como referencia en Azure Portal. *No* se muestra en el dispositivo iOS.
    - **Identificador del paquete de aplicaciones**: escriba el identificador del paquete de la aplicación. Consulte [Identificadores de lote para aplicaciones iOS integradas](bundle-ids-built-in-ios-apps.md) para ver algunos ejemplos.

  - **Carpeta**: elija esta opción para agregar una carpeta a la base en la pantalla.

    Las aplicaciones que agrega a una página en una carpeta se organizan de izquierda a derecha y en el mismo orden que en la lista. Si agrega más aplicaciones de las que pueden caber en una página, se mueven a otra página.

    - **Nombre de la carpeta**: escriba el nombre de la carpeta. Este nombre se muestra en los dispositivos de los usuarios.
    - **Lista de páginas**: **agregue** una página y escriba las propiedades siguientes:

      - **Nombre de la página**: especifique un nombre para la página. Este nombre se usa como referencia en Azure Portal. *No* se muestra en el dispositivo iOS.
      - **Nombre de la aplicación**: especifique un nombre para la aplicación. Este nombre se usa como referencia en Azure Portal. *No* se muestra en el dispositivo iOS.
      - **Identificador del paquete de aplicaciones**: escriba el identificador del paquete de la aplicación. Consulte [Identificadores de lote para aplicaciones iOS integradas](bundle-ids-built-in-ios-apps.md) para ver algunos ejemplos.

      Puede agregar hasta **20** páginas para base del dispositivo.

> [!NOTE]
> Cuando se agregan iconos mediante la configuración de Acoplar, se bloquean los iconos de la pantalla principal y de las páginas, y no se pueden mover. Esto puede deberse al diseño con iOS y las directivas MDM de Apple.

#### <a name="example"></a>Ejemplo

En el ejemplo siguiente, la pantalla de la base muestra solo las aplicaciones Safari, Correo y Bolsa. Se ha seleccionado la aplicación Correo para mostrar sus propiedades:

![Configuración de base de iOS de ejemplo](./media/ios-device-features-settings/FfFiUcP.png)

Cuando asigna la directiva a un iPhone, la base tiene un aspecto similar al de la siguiente imagen:

![Diseño de base de iOS de ejemplo en iPhone](./media/ios-device-features-settings/bAgCe8F.png)

### <a name="pages"></a>Páginas

Agregue las páginas que quiere que aparezcan en la pantalla principal y las aplicaciones que desea que se muestren en cada página. Las aplicaciones que agrega a una página se organizan de izquierda a derecha, en el mismo orden que en la lista. Si agrega más aplicaciones de las que pueden caber en una página, se mueven a otra página.

> [!TIP]
> Para reordenar elementos en cualquier pantalla principal y listas de páginas, puede arrastrarlos y soltarlos.

Puede agregar hasta **40** páginas en un dispositivo.

- **Lista de páginas**: **agregue** una página y escriba las propiedades siguientes:

  - **Nombre de la página**: especifique un nombre para la página. Este nombre se usa como referencia en Azure Portal y *no* se muestra en el dispositivo iOS.

  Puede agregar hasta **60** elementos (aplicaciones y carpetas combinadas) en un dispositivo.

  - **Agregar**: agrega aplicaciones o carpetas a una página en el dispositivo.

    - **Tipo**: agregue una **aplicación** o una **carpeta**:

      - **Aplicación**: elija esta opción para agregar aplicaciones a una página en la pantalla. Indique también:

        - **Nombre de la aplicación**: especifique un nombre para la aplicación. Este nombre se usa como referencia en Azure Portal. *No* se muestra en el dispositivo iOS.
        - **Identificador del paquete de aplicaciones**: escriba el identificador del paquete de la aplicación. Consulte [Identificadores de lote para aplicaciones iOS integradas](bundle-ids-built-in-ios-apps.md) para ver algunos ejemplos.

      - **Carpeta**: elija esta opción para agregar una carpeta a la base en la pantalla.

        Las aplicaciones que agrega a una página en una carpeta se organizan de izquierda a derecha y en el mismo orden que en la lista. Si agrega más aplicaciones de las que pueden caber en una página, se mueven a otra página.

        - **Nombre de la carpeta**: escriba un nombre para la carpeta. Este nombre se muestra en los dispositivos de los usuarios.
        - **Agregar**: agrega las páginas a la carpeta. Además, escriba las propiedades siguientes:

          - **Nombre de la página**: especifique un nombre para la página. Este nombre se usa como referencia en Azure Portal. *No* se muestra en el dispositivo iOS.
          - **Nombre de la aplicación**: especifique un nombre para la aplicación. Este nombre se usa como referencia en Azure Portal. *No* se muestra en el dispositivo iOS.
          - **Identificador del paquete de aplicaciones**: escriba el identificador del paquete de la aplicación. Consulte [Identificadores de lote para aplicaciones iOS integradas](bundle-ids-built-in-ios-apps.md) para ver algunos ejemplos.

#### <a name="example"></a>Ejemplo

En el ejemplo siguiente, se agrega una nueva página denominada **Contoso**. La página muestra las aplicaciones Buscar a mis amigos y Ajustes. Se ha seleccionado la aplicación Ajustes para mostrar sus propiedades:

![Ejemplo de configuración de pantalla principal de iOS](./media/ios-device-features-settings/Jc2OxyX.png)

Cuando asigna la directiva a un iPhone, la página tiene un aspecto similar al de la siguiente imagen:

![Dispositivo iOS con la pantalla principal modificada](./media/ios-device-features-settings/Bd37PHa.png)

## <a name="app-notifications"></a>Notificaciones de la aplicación

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>La configuración se aplica a: inscripción de dispositivos automatizada (supervisado)

- **Agregar**: agregue notificaciones para las aplicaciones:

    ![Agregar una notificación de aplicación en el perfil de iOS en Intune](./media/ios-device-features-settings/ios-macos-app-notifications.png)

  - **Identificador de lote de aplicaciones**: escriba el **identificador de lote de aplicaciones** de la aplicación que quiere agregar. Consulte [Identificadores de lote para aplicaciones iOS integradas](bundle-ids-built-in-ios-apps.md) para ver algunos ejemplos.
  - **Nombre de la aplicación**: escriba el nombre de la aplicación que quiera agregar. Este nombre se usa como referencia en Azure Portal. *No* se muestra en el dispositivo.
  - **Publicador**: escriba el publicador de la aplicación que se va a agregar. Este nombre se usa como referencia en Azure Portal. *No* se muestra en el dispositivo.
  - **Notificaciones**: **habilite** o **deshabilite** el envío de notificaciones de la aplicación al dispositivo.
    - **Mostrar en Centro de notificaciones**: **Habilitar** permite que la aplicación muestre notificaciones en el Centro de notificaciones del dispositivo. **Deshabilitar** impide a la aplicación mostrar notificaciones en el centro de notificaciones.
    - **Mostrar en pantalla de bloqueo**: seleccione **Habilitar** para ver las notificaciones de la aplicación en la pantalla de bloqueo del dispositivo. **Deshabilitar** impide a la aplicación mostrar notificaciones en la pantalla de bloqueo.
    - **Tipo de alerta**: cuando el dispositivo está desbloqueado, elija cómo se muestra la notificación. Las opciones son:
      - **Ninguna**: no se muestra ninguna notificación.
      - **Banner**: se muestra brevemente un banner con la notificación.
      - **Modal**: se muestra la notificación y el usuario debe descartarla manualmente antes de continuar usando el dispositivo.
    - **Distintivo en el icono de la aplicación**: seleccione **Habilitar** para agregar un distintivo en el icono de la aplicación. El distintivo significa que la aplicación envió una notificación.
    - **Sonidos**: seleccione **Habilitar** para reproducir un sonido cuando se entrega una notificación.

## <a name="lock-screen-message"></a>Mensaje de la pantalla de bloqueo

Esta característica se aplica a:

- iOS 9.3 y versiones posteriores

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>La configuración se aplica a: inscripción de dispositivos automatizada (supervisado)

- **Información de etiqueta de activo**: escriba información sobre la etiqueta de activo del dispositivo. Por ejemplo, escriba `Owned by Contoso Corp` o `Serial Number: {{serialnumber}}`.

  El texto que escriba se mostrará en la ventana de inicio de sesión y en la pantalla de bloqueo del dispositivo.

- **Nota al pie de pantalla de bloqueo**: si el dispositivo se pierde o se lo roban, escriba una nota que pueda ayudar a que se lo devuelvan. Puede escribir el texto que quiera. Por ejemplo, escriba algo parecido a `If found, call Contoso at ...`.

  Los tokens de dispositivo también se pueden usar para agregar información específica sobre el dispositivo a estos campos. Por ejemplo, para que se muestre el número de serie, escriba `Serial Number: {{serialnumber}}`. En la pantalla de bloqueo, el texto tendrá un aspecto similar a este: `Serial Number 123456789ABC`. Al especificar variables, no olvide usar llaves: `{{ }}`. En los [tokens de configuración de aplicación](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) podrá ver una lista de las variables que puede usar. También puede usar `deviceName` o cualquier otro valor específico del dispositivo.

  > [!NOTE]
  > Las variables no se validan en la interfaz de usuario y distinguen mayúsculas de minúsculas. Como resultado, es posible que vea perfiles guardados con entradas incorrectas. Por ejemplo, si escribe `{{DeviceID}}` en lugar de `{{deviceid}}`, se muestra la cadena literal en lugar del identificador del dispositivo. Asegúrese de escribir la información correcta.

## <a name="single-sign-on"></a>Inicio de sesión único

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>La configuración se aplica a: inscripción de dispositivos, inscripción de dispositivo automatizada (supervisado)

- **Username attribute from AAD** (Atributo de nombre de usuario de AAD): Intune busca este atributo para cada usuario de Azure AD. Después, Intune rellena el campo correspondiente (como UPN) antes de generar el código XML que se instala en el dispositivo. Las opciones son:

  - **Nombre principal de usuario**: se analiza el UPN de la manera siguiente:

    ![Atributo de nombre de usuario](./media/ios-device-features-settings/User-name-attribute.png)

    También puede sobrescribir el dominio kerberos con el texto que escriba en el cuadro de texto **Dominio kerberos**.

    Por ejemplo, Contoso tiene varias regiones, incluidas Europa, Asia y Norteamérica. Contoso desea que los usuarios de Asia usen el inicio de sesión único y la aplicación requiere UPN con el formato `username@asia.contoso.com`. Si selecciona **Nombre principal de usuario**, el dominio kerberos de cada usuario se toma de Azure AD, que es `contoso.com`. Por tato, para los usuarios de Asia, seleccione **Nombre principal de usuario** y escriba `asia.contoso.com`. El UPN del usuario final se convierte en `username@asia.contoso.com` y no en `username@contoso.com`.

  - **Identificador de dispositivo de Intune**: Intune selecciona de forma automática el identificador de dispositivo de Intune.

    De forma predeterminada, las aplicaciones solo tienen que usar el identificador de dispositivo. Pero si la aplicación usa el dominio kerberos y el identificador de dispositivo, puede escribir dicho dominio en el cuadro de texto Dominio kerberos.

    > [!NOTE]
    > Si usa el identificador de dispositivo, mantenga vacío el dominio kerberos de forma predeterminada.

  - **Id. de dispositivo de Azure AD**

- **Dominio kerberos**: escriba la parte del dominio de la dirección URL. Por ejemplo, escriba `contoso.com`.
- **URL prefixes that will use Single Sign On** (Prefijos de dirección URL que usarán el inicio de sesión único): **agregue** cualquier dirección URL de la organización que exija la autenticación de inicio de sesión único.

  Por ejemplo, cuando un usuario se conecta a alguno de estos sitios, el dispositivo iOS usa las credenciales de inicio de sesión único. El usuario no tiene que escribir otras credenciales. Si la autenticación multifactor está habilitada, los usuarios tienen que escribir la segunda autenticación.

  > [!NOTE]
  > Estas direcciones URL deben tener el formato FQDN correcto. Apple exige que tengan el formato `http://<yourURL.domain>`.

  Los patrones de coincidencia de la dirección URL deben comenzar por `http://` o `https://`. Se ejecuta una coincidencia de cadena simple, así que el prefijo de dirección URL `http://www.contoso.com/` no coincide con `http://www.contoso.com:80/`. Con iOS 10.0 o versiones posteriores, se puede usar un único carácter comodín \* para especificar todos los valores coincidentes. Por ejemplo, `http://*.contoso.com/` coincide con `http://store.contoso.com/` y con `http://www.contoso.com`.

  Los patrones `http://.com` y `https://.com` coinciden con todas las direcciones URL HTTP y HTTPS, respectivamente.

- **Apps that will use Single Sign On** (Aplicaciones que usarán el inicio de sesión único): **agregue** las aplicaciones de los dispositivos de los usuarios finales que pueden usar el inicio de sesión único.

  La matriz `AppIdentifierMatches` debe incluir cadenas que coincidan con los identificadores del lote de aplicaciones. Estas cadenas pueden ser coincidencias exactas, como `com.contoso.myapp`, o pueden especificar una coincidencia de prefijo en el identificador de lote mediante el carácter comodín \*. El carácter comodín debe aparecer después de un carácter de punto (.) y solo puede hacerlo una vez, al final de la cadena, como `com.contoso.*`. Cuando se incluye un carácter comodín, se concede acceso a la cuenta a cualquier aplicación cuyo identificador de lote empiece por el prefijo.

  Use **Nombre de la aplicación** para especificar un nombre descriptivo que ayude a identificar el identificador de lote.

- **Certificado de renovación de credenciales**: si usa certificados para la autenticación (no contraseñas), seleccione el certificado SCEP o PFX existente como certificado de autenticación. Normalmente, se trata del mismo certificado implementado para el usuario para otros perfiles como VPN, Wi-Fi o correo electrónico.

## <a name="web-content-filter"></a>Filtro de contenido web

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>La configuración se aplica a: inscripción de dispositivos automatizada (supervisado)

- **Tipo de filtro**: seleccione esta opción para permitir sitios web específicos. Las opciones son:

  - **Configurar direcciones URL**: use el filtro web integrado de Apple que busca términos para adultos, incluido lenguaje obsceno y sexualmente explícito. Esta característica evalúa cada página web cuando se carga e identifica y bloquea contenido inadecuado. También puede agregar direcciones URL que no desea que el filtro compruebe. O bien, puede bloquear direcciones URL específicas, independientemente de la configuración del filtro de Apple.

    - **URL permitidas**: **agregue** las URL que quiera permitir. Estas direcciones URL no son capturadas por el filtro web de Apple.

        > [!NOTE]
        > Las direcciones URL que especifique son las direcciones URL que no desea que el filtro web de Apple evalúe. Estas direcciones URL no son una lista de sitios web permitidos. Para crear una lista de sitios web permitidos, establezca **Tipo de filtro** en **Solo sitios web específicos**.

    - **URL bloqueadas**: **agregue** las direcciones URL que quiera impedir que se abran, independientemente de la configuración del filtro web de Apple.

  - **Solo sitios web específicos** (solo para el explorador web Safari): estas direcciones URL se agregan a los marcadores del explorador Safari. El usuario **solo** tiene permiso para visitar estos sitios; no pueden abrir otros sitios. Use esta opción solo si conoce la lista exacta de direcciones URL a las que pueden acceder los usuarios.

    - **URL**: escriba la dirección URL del sitio web que quiere permitir. Por ejemplo, escriba `https://www.contoso.com`.
    - **Ruta de acceso del marcador**: Apple cambió esta configuración. Todos los marcadores van a la carpeta **sitios aprobados** . Los marcadores no entran en la ruta de acceso del marcador que especifique.
    - **Título**: escriba un título descriptivo para el marcador.

    Si no especifica ninguna dirección URL, los usuarios finales no pueden acceder a ningún sitio web, excepto `microsoft.com`, `microsoft.net` y `apple.com`. Intune permite automáticamente estas direcciones URL.

## <a name="single-sign-on-app-extension"></a>Extensión de aplicación de inicio de sesión único

Esta característica se aplica a:

- iOS 13.0 y versiones posteriores
- iPados 13,0 y versiones posteriores

### <a name="settings-apply-to-all-enrollment-types"></a>La configuración se aplica a: todos los tipos de inscripción

- **Tipo de extensión de aplicación de SSO**: elija el tipo de extensión de aplicación SSO de credenciales. Las opciones son:

  - **No configurado**: no se usan las extensiones de aplicación. Para deshabilitar una extensión de aplicación, puede cambiar el tipo de extensión de aplicación de SSO de **Kerberos** o **credencial** a **no configurado**.
  - **Credential**: Use una extensión de aplicación de credenciales genérica y personalizable para realizar el inicio de sesión único. Asegúrese de que conoce el identificador de la extensión de la aplicación SSO de su organización.
  - **Kerberos**: Use la extensión integrada de Kerberos de Apple, que se incluye en iOS 13,0 (y versiones más recientes) y en ipados 13,0 (y versiones más recientes). Esta opción es una versión específica de Kerberos de la extensión de la aplicación de **credenciales** .

  > [!TIP]
  > Con el tipo de **credencial** , se agregan sus propios valores de configuración para pasar a través de la extensión. En su lugar, considere la posibilidad de usar las opciones de configuración integradas proporcionadas por Apple en el tipo de **Kerberos** .

- **Identificador de extensión** (solo credencial): escriba el identificador de paquete que identifica la extensión de la aplicación de SSO, como `com.apple.extensiblesso`.
- **Identificador de equipo** (solo credencial): escriba el identificador de equipo de la extensión de la aplicación de SSO. Un identificador de equipo es una cadena alfanumérica de 10 caracteres (números y letras) que genera Apple, como `ABCDE12345`. No es necesario el identificador del equipo.

  [Busque el identificador de su equipo](https://help.apple.com/developer-account/#/dev55c3c710c) (abre el sitio web de Apple) para obtener más información.

- **Territorio**: escriba el nombre del dominio Kerberos. El nombre de dominio Kerberos debe escribirse en mayúsculas, como `CONTOSO.COM`. Normalmente, el nombre de dominio Kerberos es el mismo que el nombre de dominio DNS, pero en mayúsculas.

- **Dominios**: escriba los nombres de dominio o de host de los sitios que pueden autenticarse a través de SSO. Por ejemplo, si el sitio web es `mysite.contoso.com`, `mysite` es el nombre de host y `contoso.com` es el nombre de dominio. Cuando los usuarios se conectan a cualquiera de estos sitios, la extensión de la aplicación controla el desafío de autenticación. Esta autenticación permite a los usuarios usar el ID. de la persona, Touch ID o pincode/PASSCODE de Apple para iniciar sesión.

  - Todos los dominios de la extensión de aplicación de inicio de sesión único perfiles de Intune deben ser únicos. No se puede repetir un dominio en ningún perfil de extensión de aplicación de inicio de sesión, aunque se usen distintos tipos de extensiones de aplicación de SSO.
  - Estos dominios no distinguen mayúsculas de minúsculas.

- **Configuración adicional** (solo credencial): escriba datos adicionales específicos de la extensión para pasarlos a la extensión de la aplicación de SSO:
  - **Clave de configuración**: escriba el nombre del elemento que desea agregar, como `user name`.
  - **Tipo de valor**: escriba el tipo de datos. Las opciones son:

    - String
    - Booleano: en **valor de configuración**, escriba `True` o `False`.
    - Entero: en **valor de configuración**, escriba un número.
    
  - **Valor de configuración**: escriba los datos.

  - **Agregar**: Seleccione esta configuración para agregar las claves de configuración.

- **Uso de cadena de claves** (solo Kerberos): elija **bloquear** para impedir que se guarden y almacenen contraseñas en la cadena de claves. **No configurado** (valor predeterminado) permite guardar y almacenar contraseñas en la cadena de claves.
- **Identificador de la esfera, Touch ID o PASSCODE** (solo Kerberos): **requerir** obliga a los usuarios a escribir su identificador de la esfera, Touch ID o el código de acceso de Apple para iniciar sesión en los dominios que ha agregado. **No configurado** (valor predeterminado) no requiere que los usuarios utilicen la biometría o el código de acceso para iniciar sesión.
- **Dominio Kerberos predeterminado** (solo Kerberos): elija **Habilitar** para establecer el valor de **dominio** Kerberos que especificó como dominio predeterminado. **No configurado** (valor predeterminado) no establece un dominio Kerberos predeterminado.

  > [!TIP]
  > - **Habilite** esta opción si va a configurar varias extensiones de aplicación SSO de Kerberos en su organización.
  > - **Habilite** esta opción si usa varios dominios. Establece el valor de **dominio Kerberos** que escribió como el dominio Kerberos predeterminado.
  > - Si solo tiene un dominio Kerberos, déjelo como **no configurado** (valor predeterminado).

- **Nombre principal** (solo Kerberos): escriba el nombre de usuario de la entidad de seguridad de Kerberos. No es necesario incluir el nombre de dominio Kerberos. Por ejemplo, en `user@contoso.com`, `user` es el nombre principal y `contoso.com` es el nombre de dominio Kerberos.
- **Código de sitio de Active Directory** (solo Kerberos): escriba el nombre del sitio Active Directory que debe usar la extensión de Kerberos. Es posible que no necesite cambiar este valor, ya que la extensión de Kerberos puede encontrar automáticamente el código del sitio Active Directory.
- **Nombre de caché** (solo Kerberos): escriba el nombre de los servicios de seguridad genéricos (GSS) de la memoria caché de Kerberos. Lo más probable es que no tenga que establecer este valor.
- **Identificadores de lote de aplicaciones** (solo Kerberos): **agregue** los identificadores de lote de aplicaciones que deben usar el inicio de sesión único en los dispositivos. A estas aplicaciones se les concede acceso al vale de concesión de vales de Kerberos, el vale de autenticación y autenticar a los usuarios en los servicios a los que están autorizados para obtener acceso.
- **Asignación de dominio Kerberos** (solo Kerberos): **agregue** los sufijos DNS de dominio que deben asignarse a su dominio Kerberos. Use esta opción cuando los nombres DNS de los hosts no coincidan con el nombre de dominio Kerberos. Lo más probable es que no tenga que crear esta asignación personalizada de dominio a dominio Kerberos.

## <a name="wallpaper"></a>Fondo de pantalla

Puede experimentar un comportamiento inesperado cuando un perfil sin imagen se asigna a dispositivos con una imagen existente. Por ejemplo, crea un perfil sin una imagen. Este perfil se asigna a dispositivos que ya tienen una imagen. En este escenario, la imagen puede cambiar a la predeterminada del dispositivo, o bien la imagen original puede permanecer en el dispositivo. Este comportamiento se controla y limita por medio de la plataforma MDM de Apple.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>La configuración se aplica a: inscripción de dispositivos automatizada (supervisado)

- **Ubicación de presentación del fondo de pantalla**: elija una ubicación en el dispositivo para mostrar la imagen. Las opciones son:
  - **Sin configurar**: no se agrega una imagen personalizada al dispositivo. El dispositivo usa la configuración predeterminada del sistema operativo.
  - **Pantalla de bloqueo**: agrega la imagen a la pantalla de bloqueo.
  - **Pantalla de inicio**: agrega la imagen a la pantalla de inicio.
  - **Pantalla de bloqueo y pantalla de inicio**: usa la misma imagen en la pantalla de bloqueo y en la pantalla de inicio.
- **Imagen de fondo de pantalla**: cargue una imagen .png, .jpg o .jpeg existente que quiera usar. Asegúrese de que el tamaño del archivo es inferior a 750 KB. También puede **quitar** una imagen que ha agregado.

> [!TIP]
> Para mostrar diferentes imágenes en la pantalla de bloqueo y en la pantalla de inicio, cree un perfil con la imagen de la pantalla de bloqueo. Cree otro perfil con la imagen de la pantalla de inicio. Asigne ambos perfiles a los grupos de usuarios o dispositivos de iOS.

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](../device-profile-assign.md) y [supervise el estado](../device-profile-monitor.md).

También puede crear perfiles de característica de dispositivo para dispositivos [macOS](macos-device-features-settings.md).