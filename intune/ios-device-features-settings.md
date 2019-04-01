---
title: 'Configuración de características de dispositivos iOS en Microsoft Intune: Azure | Microsoft Docs'
description: Consulte todas las opciones de configuración para configurar dispositivos iOS para AirPrint, el diseño de la pantalla principal, las notificaciones de aplicaciones, el dispositivo compartido, el inicio de sesión único y la configuración de filtro de contenido web en Microsoft Intune. Use estas opciones configuración en un perfil de configuración de dispositivo para configurar dispositivos iOS para usar estas características diferentes de Apple en su organización.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/13/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 34f0869b46323606d69891c3761bfbc154f3b6a3
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566631"
---
# <a name="ios-device-settings-to-use-common-ios-features-in-intune"></a>configuración de dispositivos iOS para usar las características comunes de iOS en Intune

Intune incluye algunas configuraciones integradas para permitir a los usuarios de iOS usar diferentes características de Apple en sus dispositivos. Por ejemplo, los administradores pueden controlar cómo los usuarios de iOS usan impresoras AirPrint, agregan aplicaciones y carpetas a la base y páginas en la pantalla principal, muestran las notificaciones de aplicación, muestran detalles de etiqueta de recursos en la pantalla de bloqueo, usan la autenticación de inicio de sesión único y autentican usuarios con certificados.

Use estas características para controlar los dispositivos iOS como parte de la solución de administración (MDM) de dispositivos móviles.

En este artículo se enumeran estas opciones de configuración y se describe lo que hace cada una de ellas.

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración de dispositivo iOS](device-features-configure.md#create-a-device-profile).

## <a name="airprint-settings"></a>Configuración de AirPrint

Esta característica permite a los usuarios de iOS imprimir en impresoras AirPrint conocidas.

1. En **Configuración**, seleccione **AirPrint**. Especifique las siguientes propiedades del servidor AirPrint:

    - **Dirección IP**: escriba la dirección IPv4 o IPv6 de la impresora. Si usa nombres de host para identificar impresoras, puede obtener la dirección IP haciendo ping a la impresora en el terminal. En la sección Obtención de la dirección IP y la ruta de acceso (en este artículo) se proporcionan más detalles.
    - **Ruta de acceso**: la ruta de acceso suele ser `ipp/print` para las impresoras de la red. En la sección Obtención de la dirección IP y la ruta de acceso (en este artículo) se proporcionan más detalles.
    - **Puerto**: escriba el puerto de escucha del destino de AirPrint. Si se deja esta propiedad en blanco, AirPrint usa el puerto predeterminado. Disponible en iOS 11.0 y versiones posteriores.
    - **TLS**: elija **Habilitar** para proteger las conexiones AirPrint con Seguridad de la capa de transporte (TLS). Disponible en iOS 11.0 y versiones posteriores.

2. Seleccione **Agregar**. El servidor AirPrint se agrega a la lista. Puede agregar varios servidores AirPrint.

    También puede **importar** un archivo separado por comas (.csv) con esta información. Después de crear la lista, también puede **exportar** la lista de servidores AirPrint.

3. Cuando termine, seleccione **Aceptar** para guardar la lista.

Para agregar servidores AirPrinter, necesita la dirección IP de la impresora, la ruta de acceso de recursos y el puerto. Los pasos siguientes muestran cómo obtener esta información.

1. En un equipo Mac conectado a la misma red local (subred) que las impresoras AirPrint, abra **Terminal** (en **/Aplicaciones/Utilidades**).
2. En Terminal, escriba `ippfind` y seleccione Entrar.

    Anote la información de la impresora. Por ejemplo, puede devolver algo parecido a `ipp://myprinter.local.:631/ipp/port1`. La primera parte es el nombre de la impresora. La última parte (`ipp/port1`) es la ruta de acceso del recurso.

3. En Terminal, escriba `ping myprinter.local` y seleccione Entrar.

   Anote la dirección IP. Por ejemplo, puede devolver algo parecido a `PING myprinter.local (10.50.25.21)`.

4. Use los valores de dirección IP y de ruta de acceso del recurso. En este ejemplo, la dirección IP es `10.50.25.21` y la ruta de acceso del recurso es `/ipp/port1`.

## <a name="home-screen-layout-settings"></a>Configuración de diseño de pantalla principal

Estas configuraciones definen el diseño de aplicaciones y carpetas en la base y las pantallas principales de los dispositivos iOS. Para usar esta característica, los dispositivos iOS deben estar en modo supervisado y ejecutar iOS 9.3 o versiones posteriores.

### <a name="dock"></a>Acoplar

Use la configuración **Acoplar**, para agregar hasta seis elementos o carpetas a la base de la pantalla de iOS. Muchos dispositivos admiten menos elementos. Por ejemplo, los dispositivos iPhone admiten hasta cuatro elementos. En este caso, en el dispositivo solo se muestran los primeros cuatro elementos que agrega.

1. En **Configuración**, seleccione **Diseño de pantalla principal (solo supervisado)** > **Acoplar** > **Agregar**. Puede agregar hasta **seis** elementos (aplicaciones y carpetas combinadas) para la base del dispositivo.
2. En **Tipo**, elija una de estas dos opciones para agregar: **Aplicación** o **Carpeta**.

    - **Agregar una aplicación**: elija esta opción para agregar aplicaciones a la base en la pantalla. Introduzca:

      - **Nombre de la aplicación**: escriba un nombre para la aplicación. Este nombre se usa como referencia en Azure Portal. *No* se muestra en el dispositivo iOS.
      - **Identificador del paquete de aplicaciones**: escriba el identificador del paquete de la aplicación. Consulte [Identificadores de lote para aplicaciones iOS integradas](#bundle-ids-for-built-in-ios-apps) (en este artículo) para ver algunos ejemplos.

      Haga clic en **Aceptar** para guardar los cambios.

    - **Agregar una carpeta**: elija esta opción para agregar una carpeta a la base en la pantalla. 

      Las aplicaciones que agrega a una página en una carpeta se organizan de izquierda a derecha y en el mismo orden que en la lista. Si agrega más aplicaciones de las que pueden caber en una página, se mueven a otra página.

      1. Escriba un nombre en **Nombre de carpeta**. Este nombre se muestra en los dispositivos de los usuarios.
      2. Vaya a **Agregar** y escriba las siguientes propiedades:

          - **Nombre de la página**: escriba un nombre para la página. Este nombre se usa como referencia en Azure Portal. *No* se muestra en el dispositivo iOS.
          - **Nombre de la aplicación**: escriba un nombre para la aplicación. Este nombre se usa como referencia en Azure Portal. *No* se muestra en el dispositivo iOS.
          - **Identificador del paquete de aplicaciones**: escriba el identificador del paquete de la aplicación. Consulte [Identificadores de lote para aplicaciones iOS integradas](#bundle-ids-for-built-in-ios-apps) (en este artículo) para ver algunos ejemplos.

      3. Seleccione **Agregar**. Puede agregar hasta **20** páginas para base del dispositivo.
      4. Haga clic en **Aceptar** para guardar los cambios.

#### <a name="example"></a>Ejemplo

En el ejemplo siguiente, la pantalla de la base muestra solo las aplicaciones Safari, Correo y Bolsa. Se ha seleccionado la aplicación Correo para mostrar sus propiedades:

![Configuración de base de iOS de ejemplo](./media/FfFiUcP.png)

Cuando asigna la directiva a un iPhone, la base tiene un aspecto similar al de la siguiente imagen:

![Diseño de base de iOS de ejemplo en iPhone](./media/bAgCe8F.png)

### <a name="pages"></a>Páginas

Agregue las páginas que quiere que aparezcan en la pantalla principal y las aplicaciones que desea que se muestren en cada página. Las aplicaciones que agrega a una página se organizan de izquierda a derecha, en el mismo orden que en la lista. Si agrega más aplicaciones de las que pueden caber en una página, se mueven a otra página.

> [!TIP]
> Para reordenar elementos en cualquier pantalla principal y listas de páginas, puede arrastrarlos y soltarlos.

1. En **Configuración**, seleccione **Diseño de pantalla principal (solo supervisado)** > **Páginas** > **Agregar**. Puede agregar hasta **40** páginas en un dispositivo.
2. Escriba un nombre en **Nombre de la página**. Este nombre se usa como referencia en Azure Portal y *no* se muestra en el dispositivo iOS. 

    Seleccione **Agregar**. Puede agregar hasta **60** elementos (aplicaciones y carpetas combinadas) en un dispositivo.

3. En **Tipo**, elija una de estas dos opciones para agregar: **Aplicación** o **Carpeta**.

    - **Agregar una aplicación**: elija esta opción para agregar aplicaciones a una página en la pantalla. Introduzca:

      - **Nombre de la aplicación**: escriba un nombre para la aplicación. Este nombre se usa como referencia en Azure Portal. *No* se muestra en el dispositivo iOS.
      - **Identificador del paquete de aplicaciones**: escriba el identificador del paquete de la aplicación. Consulte [Identificadores de lote para aplicaciones iOS integradas](#bundle-ids-for-built-in-ios-apps) (en este artículo) para ver algunos ejemplos.

      Haga clic en **Aceptar** para guardar los cambios.

    - **Agregar una carpeta**: elija esta opción para agregar una carpeta a la base en la pantalla. 

      Las aplicaciones que agrega a una página en una carpeta se organizan de izquierda a derecha y en el mismo orden que en la lista. Si agrega más aplicaciones de las que pueden caber en una página, se mueven a otra página.

      1. Escriba un nombre en **Nombre de carpeta**. Este nombre se muestra en los dispositivos de los usuarios.
      2. Vaya a **Agregar** y escriba las siguientes propiedades:

          - **Nombre de la página**: escriba un nombre para la página. Este nombre se usa como referencia en Azure Portal. *No* se muestra en el dispositivo iOS.
          - **Nombre de la aplicación**: escriba un nombre para la aplicación. Este nombre se usa como referencia en Azure Portal. *No* se muestra en el dispositivo iOS.
          - **Identificador del paquete de aplicaciones**: escriba el identificador del paquete de la aplicación. Consulte [Identificadores de lote para aplicaciones iOS integradas](#bundle-ids-for-built-in-ios-apps) (en este artículo) para ver algunos ejemplos.

      3. Seleccione **Agregar**.
      4. Haga clic en **Aceptar** para guardar los cambios.

#### <a name="example"></a>Ejemplo

En el ejemplo siguiente, se agrega una nueva página denominada **Contoso**. La página muestra las aplicaciones Buscar a mis amigos y Ajustes. Se ha seleccionado la aplicación Ajustes para mostrar sus propiedades:

![Ejemplo de configuración de pantalla principal de iOS](./media/Jc2OxyX.png)

Cuando asigna la directiva a un iPhone, la página tiene un aspecto similar al de la siguiente imagen:

![Dispositivo iOS con la pantalla principal modificada](./media/Bd37PHa.png)

## <a name="app-notifications-settings"></a>Configuración de notificaciones de aplicación

Elija cómo las aplicaciones instaladas en dispositivos iOS envían notificaciones. Esta configuración admite dispositivos supervisados que ejecuten iOS 9.3 y versiones posteriores.

1. En **Configuración**, seleccione **Notificaciones de la aplicación (solo supervisado)** > **Agregar**:

    ![Agregar una notificación de aplicación en el perfil de iOS en Intune](./media/ios-macos-app-notifications.png)

2. Escriba las propiedades siguientes:

    - **Identificador de lote de aplicaciones**: escriba el **identificador de lote de aplicaciones** de la aplicación que quiere agregar. Consulte [Identificadores de lote para aplicaciones iOS integradas](#bundle-ids-for-built-in-ios-apps) (en este artículo) para ver algunos ejemplos.
    - **Nombre de la aplicación**: escriba el nombre de la aplicación que quiera agregar. Este nombre se usa como referencia en Azure Portal. *No* se muestra en el dispositivo.
    - **Publicador**: escriba el publicador de la aplicación que se va a agregar. Este nombre se usa como referencia en Azure Portal. *No* se muestra en el dispositivo.
    - **Notificaciones**: **habilite** o **deshabilite** el envío de notificaciones de la aplicación al dispositivo.
       - **Mostrar en Centro de notificaciones**: **Habilitar** permite que la aplicación muestre notificaciones en el Centro de notificaciones del dispositivo. **Deshabilitar** impide a la aplicación mostrar notificaciones en el centro de notificaciones.
       - **Mostrar en pantalla de bloqueo**: seleccione **Habilitar** para ver las notificaciones de la aplicación en la pantalla de bloqueo del dispositivo. **Deshabilitar** impide a la aplicación mostrar notificaciones en la pantalla de bloqueo.
       - **Tipo de alerta**: cuando el dispositivo está desbloqueado, elija cómo se muestra la notificación. Las opciones son:
         - **Ninguna**: no se muestra ninguna notificación.
         - **Banner**: se muestra brevemente un banner con la notificación.
         - **Modal**: se muestra la notificación y el usuario debe descartarla manualmente antes de continuar usando el dispositivo.
       - **Distintivo en el icono de la aplicación**: seleccione **habilitar** para agregar un distintivo en el icono de la aplicación. El distintivo significa que la aplicación envió una notificación.
       - **Sonidos**: seleccione **Habilitar** para reproducir un sonido cuando se entrega una notificación.

3. Haga clic en **Aceptar** para guardar los cambios. Continúe agregando las aplicaciones que quiera. Cuando termine, seleccione **Aceptar**.

## <a name="lock-screen-message-settings"></a>Configuración del mensaje de la pantalla de bloqueo

Use esta configuración para mostrar un mensaje o un texto personalizado en la ventana de inicio de sesión y la pantalla de bloqueo. Por ejemplo, puede escribir el mensaje "En caso de pérdida, devolver a..." y agregar información sobre la etiqueta de activo. 

Esta característica es compatible con dispositivos que ejecutan:

- iOS 9.3 y versiones posteriores

1. En **Configuración**, seleccione **Mensaje de pantalla de bloqueo (solo supervisado)**.
2. Escriba los valores siguientes:

    - **Información de etiqueta de activo**: escriba información sobre la etiqueta de activo del dispositivo. Por ejemplo, escriba `Owned by Contoso Corp` o `Serial Number: {{serialnumber}}`. 

      El texto que escriba se mostrará en la ventana de inicio de sesión y en la pantalla de bloqueo del dispositivo.

    - **Nota al pie de pantalla de bloqueo**: si el dispositivo se pierde o se lo roban, escriba una nota que pueda ayudar a que se lo devuelvan. Puede escribir el texto que quiera. Por ejemplo, escriba algo parecido a `If found, call Contoso at ...`.

    Los tokens de dispositivo también se pueden usar para agregar información específica sobre el dispositivo a estos campos. Por ejemplo, para que se muestre el número de serie, escriba `Serial Number: {{serialnumber}}`. En la pantalla de bloqueo, el texto tendrá un aspecto similar a este: `Serial Number 123456789ABC`. Al especificar variables, no olvide usar llaves: `{{ }}`. En los [tokens de configuración de aplicación](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) podrá ver una lista de las variables que puede usar. También puede usar `deviceName` o cualquier otro valor específico del dispositivo.

    > [!NOTE]
    > Las variables no se validan en la interfaz de usuario. Como resultado, es posible que vea perfiles guardados con entradas incorrectas. Por ejemplo, si escribe `{{Devicename}}` en lugar de `{{devicename}}`, se muestra la cadena literal en lugar del nombre único del dispositivo.

3. Cuando termine, seleccione **Aceptar** para guardar los cambios.

## <a name="single-sign-on-settings"></a>Configuración de inicio de sesión único

La mayoría de las aplicaciones de línea de negocio (LOB) necesita cierto nivel de autenticación de usuario para ofrecer seguridad. En muchos casos, esta autenticación exige que el usuario escriba las mismas credenciales repetidamente, lo que es frustrante para los usuarios. Para mejorar la experiencia del usuario, los desarrolladores pueden crear aplicaciones que usen el inicio de sesión único (SSO). El uso del inicio de sesión único reduce el número de veces que un usuario debe escribir las credenciales.

Para usar el inicio de sesión único, asegúrese de que tiene:

- Una aplicación programada para buscar el almacén de credenciales del usuario en el inicio de sesión único en el dispositivo.
- Intune configurado para el inicio de sesión único para dispositivos iOS.

1. En **Configuración**, seleccione **Inicio de sesión único**:

   ![Panel Inicio de sesión único](./media/sso-blade.png)

2. Escriba los valores siguientes:

    - **Username attribute from AAD** (Atributo de nombre de usuario de AAD): Intune busca este atributo para cada usuario de Azure AD. Después, Intune rellena el campo correspondiente (como UPN) antes de generar el código XML que se instala en el dispositivo. Las opciones son:

      - **Nombre principal de usuario**: se analiza el UPN de la manera siguiente:

        ![Atributo de nombre de usuario](media/User-name-attribute.png)

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

3. Cuando termine, seleccione **Aceptar** para guardar los cambios.

## <a name="web-content-filter-settings"></a>Configuración del filtro de contenido web

Esta configuración controla el acceso de dirección URL del explorador en dispositivos iOS.

1. En **Configuración**, seleccione **Filtro de contenido web (solo supervisados)**.
2. Elija un tipo en **Tipo de filtro**. Las opciones son:

    - **Configurar direcciones URL**: use el filtro web integrado de Apple que busca términos para adultos, incluido lenguaje obsceno y sexualmente explícito. Esta característica evalúa cada página web cuando se carga e identifica y bloquea contenido inadecuado. También puede agregar direcciones URL que no desea que el filtro compruebe. O bien, puede bloquear direcciones URL específicas, independientemente de la configuración del filtro de Apple.

      - **URL permitidas**: **agregar** las direcciones URL que desea permitir. Estas direcciones URL no son capturadas por el filtro web de Apple.

        > [!NOTE]
        > Las direcciones URL que especifique son las direcciones URL que no desea que el filtro web de Apple evalúe. Estas direcciones URL no son una lista de sitios web permitidos. Para crear una lista de sitios web permitidos, establezca **Tipo de filtro** en **Solo sitios web específicos**.

        Haga clic en **Aceptar** para guardar los cambios.

      - **URL bloqueadas**: **agregue** las direcciones URL que quiera impedir que se abran, independientemente de la configuración del filtro web de Apple.

        Haga clic en **Aceptar** para guardar los cambios.

    - **Solo sitios web específicos** (solo para el explorador web Safari): estas direcciones URL se agregan a los marcadores del explorador Safari. El usuario **solo** tiene permiso para visitar estos sitios; no pueden abrir otros sitios. Use esta opción solo si conoce la lista exacta de direcciones URL a las que pueden acceder los usuarios.

      - **URL**: escriba la dirección URL del sitio web que quiere permitir. Por ejemplo, escriba `https://www.contoso.com`.
      - **Ruta de acceso de marcador**: escriba la ruta de acceso para almacenar el marcador. Por ejemplo, escriba `/Contoso/Business Apps`. Si no agrega una ruta de acceso, el marcador se agregará a la carpeta predeterminada de marcadores del dispositivo.
      - **Título**: escriba un título descriptivo para el marcador.

      Si no especifica ninguna dirección URL, los usuarios finales no pueden acceder a ningún sitio web, excepto `microsoft.com`, `microsoft.net` y `apple.com`. Intune permite automáticamente estas direcciones URL.

      Haga clic en **Aceptar** para guardar los cambios.

## <a name="wallpaper-settings"></a>Configuración del fondo de pantalla

Agregue una imagen .png, .jpg o .jpeg personalizada a los dispositivos iOS supervisados. Por ejemplo, use un logotipo de empresa en la pantalla de bloqueo.

Puede experimentar un comportamiento inesperado cuando un perfil sin imagen se asigna a dispositivos con una imagen existente. Por ejemplo, crea un perfil sin una imagen. Este perfil se asigna a dispositivos que ya tienen una imagen. En este escenario, la imagen puede cambiar a la predeterminada del dispositivo, o bien la imagen original puede permanecer en el dispositivo. Este comportamiento se controla y limita por medio de la plataforma MDM de Apple.

- **Ubicación para mostrar del papel tapiz**: elija una ubicación en el dispositivo para mostrar la imagen. Las opciones son:
  - **No configurado**: no se agrega una imagen personalizada en el dispositivo. El dispositivo usa la configuración predeterminada del sistema operativo.
  - **Pantalla de bloqueo**: agrega la imagen en la pantalla de bloqueo.
  - **Pantalla principal**: agrega la imagen en la pantalla principal.
  - **Pantalla de bloqueo y la pantalla principal**: utiliza la misma imagen en la pantalla de bloqueo y la pantalla principal.
- **Imagen de fondo de pantalla**: cargue una imagen .png, .jpg o .jpeg existente que quiera usar. Asegúrese de que el tamaño del archivo es inferior a 750 KB. También puede **quitar** una imagen que ha agregado.

> [!TIP]
> Para mostrar diferentes imágenes en la pantalla de bloqueo y en la pantalla de inicio, cree un perfil con la imagen de la pantalla de bloqueo. Cree otro perfil con la imagen de la pantalla de inicio. Asigne ambos perfiles a los grupos de usuarios o dispositivos de iOS.

## <a name="bundle-ids-for-built-in-ios-apps"></a>Identificadores de lote para aplicaciones iOS integradas

En la lista siguiente se muestra el identificador de lote de algunas aplicaciones iOS integradas comunes. Póngase en contacto con el proveedor de software para encontrar el identificador de lote de otras aplicaciones.

| Identificador de lote                   | Nombre de la aplicación     | Publicador |
|-----------------------------|--------------|-----------|
| com.apple.AppStore          | Tienda de aplicaciones    | Apple     |
| com.apple.calculator        | Calculadora   | Apple     |
| com.apple.mobilecal         | Calendario     | Apple     |
| com.apple.camera            | Cámara       | Apple     |
| com.apple.mobiletimer       | Reloj        | Apple     |
| com.apple.compass           | Compass      | Apple     |
| com.apple.MobileAddressBook | Contactos     | Apple     |
| com.apple.facetime          | FaceTime     | Apple     |
| com.apple.DocumentsApp      | Archivos        | Apple     |
| com.apple.mobileme.fmf1     | Buscar amigos | Apple     |
| com.apple.mobileme.fmip1    | Buscar mi iPhone  | Apple     |
| com.apple.gamecenter        | Centro de juegos  | Apple     |
| com.apple.mobilegarageband  | GarageBand   | Apple     |
| com.apple.Health            | Mantenimiento       | Apple     |
| com.apple.Home              | Inicio         | Apple     |
| com.apple.iBooks            | iBooks       | Apple     |
| com.apple.iMovie            | iMovie       | Apple     |
| com.apple.itunesconnect.mobile | iTunes Connect | Apple |
| com.apple.MobileStore       | iTunes Store | Apple     |
| com.apple.itunesu           | iTunes U     | Apple     |
| com.apple.Keynote           | Keynote      | Apple     |
| com.apple.mobilemail        | Mail         | Apple     |
| com.apple.Maps              | Asignaciones         | Apple     |
| com.apple.MobileSMS         | Mensajes     | Apple     |
| com.apple.Music             | Música        | Apple     |
| com.apple.news              | Noticias         | Apple     |
| com.apple.mobilenotes       | Notas        | Apple     |
| com.apple.Numbers           | Números      | Apple     |
| com.apple.Pages             | Páginas        | Apple     |
| com.apple.Photo-Booth       | Photo Booth  | Apple     |
| com.apple.mobileslideshow   | Fotos       | Apple     |
| com.apple.podcasts          | Podcasts     | Apple     |
| com.apple.reminders         | Recordatorios    | Apple     |
| com.apple.mobilesafari      | Safari       | Apple     |
| com.apple.Preferences       | Configuración     | Apple     |
| com.apple.SiriViewService   | Siri         | Apple     |
| com.apple.stocks            | Acciones       | Apple     |
| com.apple.tips              | Sugerencias         | Apple     |
| com.apple.TV                | TV           | Apple     |
| com.apple.videos            | Vídeos       | Apple     |
| com.apple.VoiceMemos        | VoiceMemos   | Apple     |
| com.apple.Passbook          | Wallet       | Apple     |
| com.apple.Bridge            | Inspección        | Apple     |
| com.apple.weather           | Clima      | Apple     |

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

También puede crear perfiles de característica de dispositivo para dispositivos [macOS](macos-device-features-settings.md).
