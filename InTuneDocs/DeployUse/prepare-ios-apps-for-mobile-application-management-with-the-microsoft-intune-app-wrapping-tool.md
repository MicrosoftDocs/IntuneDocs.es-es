---
title: Ajuste de aplicaciones iOS con la herramienta de ajuste de aplicaciones | Microsoft Intune
description: "Utilice la información de este tema para obtener información sobre cómo ajustar las aplicaciones iOS sin modificar el código de la propia aplicación. Prepare las aplicaciones de modo que pueda aplicar las directivas de administración de aplicaciones móviles."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 99ab0369-5115-4dc8-83ea-db7239b0de97
ms.reviewer: matgates
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: bebf57269ae41f04a47240063cde4a4dd0bf334f
ms.openlocfilehash: 3d9def8f906746cf6e3d014d251b94406d839067


---

# Preparar aplicaciones iOS para la administración de aplicaciones móviles con la Herramienta de ajuste de aplicaciones de Intune
Use la **Herramienta de ajuste de aplicaciones de Microsoft Intune para iOS** para modificar el comportamiento de las aplicaciones iOS internas mediante la restricción de características de la aplicación sin modificar el código de la propia aplicación.

La herramienta es una aplicación de línea de comandos de Mac OS que crea un "contenedor" alrededor de una aplicación. Una vez que se procesa la aplicación, puede cambiar su funcionalidad con [directivas de administración de aplicaciones móviles](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) que configure.

Para descargar la herramienta, consulte [Microsoft Intune App Wrapping Tool for iOS - Español](http://www.microsoft.com/en-us/download/details.aspx?id=45218).

## Paso 1: cumplir los requisitos previos para usar la herramienta de ajuste de aplicaciones
Lea [esta entrada de blog](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) para obtener más información sobre los requisitos previos y cómo establecerlos.

|Requisito|Más información|
|---------------|--------------------------------|
|Sistema operativo y conjunto de herramientas admitidos|Debe ejecutar la herramienta de ajuste de aplicaciones en un equipo Mac que ejecute OS X 10.8.5 o posterior que tenga instalada la versión 5 o posterior del conjunto de herramientas XCode.|
|Certificado de firma y perfil de aprovisionamiento|Debe poseer un perfil de aprovisionamiento y un certificado de firma de Apple. Consulte la [documentación para desarrolladores de Apple](https://developer.apple.com/).|
|Procesamiento de una aplicación con la herramienta de ajuste de aplicaciones|Las aplicaciones deben estar desarrolladas y firmadas por la compañía o por un fabricante de software independientes (ISV). No se puede usar esta herramienta para procesar aplicaciones de la tienda de Apple. Las aplicaciones deben estar escritas para iOS 7.1 o posterior. Las aplicaciones, además, deben estar en formato ejecutable independiente de la posición (PIE). Para obtener más información acerca del formato PIE, consulte la documentación para desarrolladores de Apple. Por último, la aplicación debe tener el formato de extensión **.app** o **.ipa**.|
|Aplicaciones que la herramienta de ajuste no puede procesar|Aplicaciones cifradas, aplicaciones sin firmar y aplicaciones con atributos de archivo extendidos.|
|Aplicaciones que usan la biblioteca de Azure Active Directory (ADAL)|Si la aplicación usa ADAL, debe incorporar una versión de la biblioteca que sea mayor o igual que la versión 1.0.2, y el desarrollador debe concederle acceso al recurso Administración de aplicaciones móviles de Intune.<br /><br />Consulte [Información para aplicaciones que usan la Biblioteca de Azure Active Directory](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md#information-for-apps-that-use-the-azure-active-directory-library) en este artículo para obtener detalles sobre cómo usar ADAL.|
|Derechos de configuración de la aplicación|Debe establecer los derechos antes de ajustar la aplicación. Estos derechos conceden permisos de aplicación adicionales y capacidades que van más allá de aquellas que se conceden en general. Consulte [Configurar los derechos de la aplicación](#setting-app-entitlements) para obtener instrucciones.|

## Paso 2: instalar la herramienta de ajuste de aplicaciones

1.  En la página **Microsoft Intune App Wrapping Tool for iOS** (Herramienta de ajuste de aplicaciones de Microsoft Intune para iOS) del [Centro de descarga de Microsoft](https://www.microsoft.com/download/details.aspx?id=45218), descargue el archivo de instalación de la herramienta de ajuste de aplicaciones en un equipo Mac.

2.  En el equipo Mac, haga doble clic en el archivo de instalación **Microsoft Intune App Wrapping Tool for iOS.dmg**.

3.  Seleccione **Acepto** para aceptar los términos de licencia (CLUF). El instalador se monta y se muestra en el equipo Mac.

4.  Abra el programa de instalación y copie los archivos que se muestran en una nueva carpeta en el equipo Mac. Una vez hecho esto, ya puede desconectar la unidad del instalador montada.

    Ahora está preparado para ejecutar la herramienta de ajuste de aplicaciones.

## Paso 3: ejecutar la herramienta de ajuste de aplicaciones

1.  En el equipo Mac, abra una ventana de Terminal y navegue hasta la carpeta donde guardó los archivos. Dado que el archivo ejecutable reside dentro del paquete, deberá ejecutar el comando siguiente:
```
    ./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -a <client ID of input app> -r <reply URI of input app> -v true
```
    > [!NOTE]
    > Some parameters are optional as shown in the table below.

    **Example:** The following example command runs the app wrapping tool on an app named **MyApp.ipa**. A provisioning profile and SHA-1 hash are specified. The processed app is created and stored in the **/users/myadmin/Documents** on the Mac computer.

    ```
    /users/myadmin/Downloads/IntuneMAMPackager.app/Contents/MacOS/IntuneMAMPackager -i /users/myadmin/Downloads/MyApp.ipa -o /users/myadmin/Documents/MyApp_Wrapped.ipa -p /users/myadmin/Downloads/My_Provisioning_Profile_.mobileprovision -c 12A3BC45D67EF8901A2B3CDEF4ABC5D6E7890FAB –a 20e1cd0d-268e-4308-9583-02ae97dd353e –r https://contoso/ -v true
    ```
    You can use the following command line properties with the app wrapping tool:

|Propiedad|Más información|
  |------------|--------------------|
  |**-h**|Muestra las propiedades de línea de comandos disponibles para la herramienta de ajuste de aplicaciones.|
  |**-i**|Especifica la ruta de acceso y el nombre de archivo de la aplicación de entrada.|
  |**-o**|Especifica la ruta de acceso en la que se va a guardar la aplicación procesada.|
  |**-p**|Especifica la ruta de acceso al perfil de aprovisionamiento para las aplicaciones iOS.|
  |**-c**|Especifica el hash SHA1 del certificado de firma.|
  |**-a**|Identificador de cliente de la aplicación de entrada (en formato GUID) si la aplicación usa bibliotecas de Azure Active Directory (opcional).|
  |**-r**|URI de redireccionamiento de la aplicación de entrada si la aplicación usa bibliotecas de Azure Active Directory (opcional).|
  |**-v**|Salida de mensajes detallados en la consola (opcional).|

2. Una vez que complete el proceso, se mostrará el mensaje **La aplicación se ajustó correctamente** .

    Si se produce un error, consulte [Mensajes de error](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md#error-messages) para obtener ayuda.

3.  La aplicación ajustada se guarda en la carpeta de salida que especificó anteriormente. Ahora puede cargar la aplicación en [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] y asociarla a una directiva de administración de aplicaciones móviles.

    > [!IMPORTANT]
    > Debe cargar la aplicación como una nueva aplicación. No se puede actualizar una versión anterior y sin ajustar de la aplicación.

    A continuación, podrá implementar la aplicación en sus grupos de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] y esta se ejecutará en el dispositivo con las restricciones de aplicación especificadas.

## Archivos de registro y mensajes de error
Use la siguiente información para solucionar los problemas que tenga con la herramienta de ajuste de aplicaciones.

### Mensajes de error
Si la herramienta de ajuste de aplicaciones no se completa correctamente, se mostrará uno de los siguientes mensajes de error:

|Mensaje de error|Más información|
|-----------------|--------------------|
|Debe especificar un perfil de aprovisionamiento de iOS válido.|Su perfil de aprovisionamiento podría no ser válido. Asegúrese de que tenga los permisos correctos para dispositivos y que su perfil se destine correctamente a desarrollo o a distribución. El perfil de aprovisionamiento también podría haber expirado.|
|Especifique un nombre de aplicación de entrada válido.|Asegúrese de que el nombre de la aplicación de entrada especificado sea correcto.|
|Especifique una ruta válida a la aplicación de salida.|Asegúrese de que la ruta de acceso a la aplicación de salida especificada exista y sea correcta.|
|Especifique un perfil de aprovisionamiento de entrada válido.|Asegúrese de que proporcionó un nombre y una extensión de perfil de aprovisionamiento válidos. Puede que el perfil de aprovisionamiento no disponga de derechos o que no se haya incluido la opción de línea de comandos **–p**.|
|No se encontró la aplicación de entrada especificada. Especifique un nombre de aplicación de entrada y una ruta de acceso válidos.|Asegúrese de que la ruta de acceso de la aplicación de entrada sea válida y exista. Asegúrese de que la aplicación de entrada exista en esa ubicación.|
|No se encontró el archivo de perfil de aprovisionamiento entrada especificado. Especifique un archivo de perfil de aprovisionamiento de entrada válido.|Asegúrese de que la ruta de acceso al archivo de aprovisionamiento de entrada sea válida y de que el archivo especificado exista.|
|No se encontró la carpeta de aplicación de salida especificada. Especifique una ruta válida a la aplicación de salida.|Asegúrese de que la ruta de acceso de salida especificada sea válida y exista.|
|La aplicación de salida no tiene extensión .ipa.|La herramienta de ajuste de aplicaciones solo acepta aplicaciones con las extensiones **.app** e **.ipa** . Asegúrese de que el archivo de salida tenga una extensión válida.|
|Se especificó un certificado de firma no válido. Especifique un certificado de firma de Apple válido.|Asegúrese de haber descargado el certificado de firma correcto desde el portal para desarrolladores de Apple. También es posible que el certificado haya expirado. Si el perfil de aprovisionamiento y el certificado de Apple se pueden usar para firmar correctamente una aplicación en Xcode, son válidos para la herramienta de ajuste de aplicaciones.|
|La aplicación de entrada especificada no es válida. Especifique una aplicación válida.|Asegúrese de que tenga una aplicación iOS válida que se haya compilado como archivo .app o .ipa.|
|La aplicación de entrada especificada está cifrada. Especifique una aplicación sin cifrar válida.|La herramienta de ajuste de aplicaciones no es compatible con aplicaciones cifradas. Especifique una aplicación sin cifrar.|
|La aplicación de entrada especificada no está en un formato ejecutable independiente de la posición (PIE). Especifique una aplicación válida en formato PIE.|Las aplicaciones de archivo ejecutable independiente de la posición (PIE) se pueden cargar en una dirección de memoria aleatoria al ejecutarse, lo que puede tener ventajas de seguridad. Para obtener más información, consulte la documentación para desarrolladores de Apple.|
|La aplicación de entrada especificada ya se ajustó. Especifique una aplicación sin ajustar válida.|No puede procesar una aplicación que la herramienta ya procesó. Si desea volver a procesar una aplicación, ejecute la herramienta con la versión original de la aplicación.|
|La aplicación de entrada especificada no está firmada. Especifique una aplicación firmada válida.|La herramienta de ajuste de aplicaciones requiere que las aplicaciones estén firmadas. Consulte la documentación para desarrolladores para aprender a firmar una aplicación ajustada.|
|La aplicación de entrada especificada debe tener formato .ipa o .app.|La herramienta de ajuste de aplicaciones solo acepta aplicaciones con las extensiones .app e .ipa. Asegúrese de que el archivo de entrada tenga una extensión válida y se haya compilado como archivo .app o .ipa.|
|La aplicación de entrada especificada ya se ajustó y se encuentra en la última versión de la plantilla de directiva.|La herramienta de ajuste de aplicaciones no ajustará una aplicación ajustada existente con la última versión de la plantilla de directiva.|
|El identificador de cliente de Azure Active Directory especificado no es un GUID con formato correcto. Especifique un identificador de cliente válido.|Cuando use el parámetro de identificador de cliente, asegúrese de que haya proporcionado un identificador de cliente válido en formato GUID.|
|El URI de respuesta de Azure Active Directory especificado no es un URI con formato correcto. Especifique un URI de respuesta válido.|Cuando use la propiedad de línea de comandos de URI de respuesta, asegúrese de que haya proporcionado un URI de respuesta válido.|
|ADVERTENCIA: no ha especificado un hash de certificado SHA1. Asegúrese de que la aplicación ajustada se firme antes de implementarla.|Asegúrese de especificar un valor de hash SHA válido (mediante la propiedad de línea de comandos **–c** ).|

### Archivos de registro de la herramienta de ajuste de aplicaciones
Las aplicaciones que se ajustaron mediante la herramienta de ajuste de aplicaciones generan los registros que se escriben en la consola del dispositivo cliente de iOS. Esta información resulta útil en situaciones en las que tiene problemas con la aplicación y necesita diagnosticar si el problema está relacionado con la herramienta de ajuste de aplicaciones. Para resolver este problema, use los siguientes pasos:

1.  Reproduzca el problema ejecutando la aplicación.

2.  Recopile la salida de consola siguiendo las instrucciones de [Depuración de aplicaciones iOS implementadas](https://developer.apple.com/library/ios/qa/qa1747/_index.html)de Apple.

3.  Filtre los registros guardados para la salida de restricciones de la aplicación especificando el siguiente script en la consola:

    ```
    grep “IntuneAppRestrictions” <text file containing console output> > <required filtered log file name>
    ```
    Puede enviar los registros filtrados a Microsoft.

    > [!NOTE]
    > En el archivo de registro, el elemento "versión" representa la versión de compilación de Xcode.

    Las aplicaciones ajustadas también ofrecen a los usuarios la opción de enviar registros directamente desde el dispositivo a través de correo electrónico después de que la aplicación se bloquea. Los usuarios pueden enviarle el registro para que lo examine y reenviarlo a Microsoft si es necesario.

## Información para aplicaciones que usan la Biblioteca de Azure Active Directory
La información de esta sección solo se aplica a aplicaciones que usan la biblioteca de Azure Active Directory (ADAL). Si no está seguro de si su aplicación usa esta biblioteca, póngase en contacto con el desarrollador de la aplicación.

La aplicación debe incorporar una versión de ADAL igual o posterior a la versión 1.0.2.

Para las aplicaciones que usen ADAL, deben cumplirse las siguientes condiciones:

-   La aplicación debe incorporar una versión de ADAL posterior o igual a la versión 1.0.2

-   Los desarrolladores deben conceder acceso a sus aplicaciones al recurso Administración de aplicaciones móviles de Intune, como se describe en [Pasos que debe seguir en cuanto a las aplicaciones que usan ADAL](#steps-to-follow-for-apps-that-use-adal).

### Información general acerca de los identificadores que debe obtener
Las aplicaciones que usen ADAL deben registrarse a través del portal de administración de Azure para obtener dos identificadores únicos para la aplicación:

|Identificador|Más información|Valor predeterminado|
|--------------|--------------------|-----------------|
|**Identificador de cliente**|Una vez que se registra con Azure Active Directory, se genera un identificador GUID único para cada aplicación.<br /><br />Si conoce el identificador de cliente específico de las aplicaciones, puede especificar este valor. De lo contrario, debe usarse el valor predeterminado.|6c7e8096-f593-4d72-807f-a5f86dcc9c77|
|**URI de redireccionamiento**|Valor de URI que los desarrolladores pueden proporcionar al registrar la aplicación con Azure Active Directory para asegurarse de que los tokens de autenticación se devuelvan específicamente a ese extremo.<br /><br />La especificación de un URI de redireccionamiento es un parámetro opcional para la herramienta de ajuste de aplicaciones. Si no se especifica, se usará un identificador URI predeterminado.|urn:ietf:wg:oauth:2.0:oob|


### Pasos que debe seguir en cuanto a las aplicaciones que usan ADAL

1.  Lea [Información general acerca de los identificadores que debe obtener](#overview-of-identifiers-you-need-to-get) para identificar los valores que debe obtener.

2.  Configure el acceso a la administración de aplicaciones móviles en Azure Active Directory mediante los siguientes pasos:

    1. Inicie sesión en una cuenta de Azure Active Directory existente en el portal de administración de Azure.

    2.  Haga clic en **registro existente de la aplicación LOB** en Azure Active Directory.

    3.  En la sección de configuración, elija **Configurar acceso a las API web en otras aplicaciones**.

    4.  En la sección **Permission to other applications** (Permiso en otras aplicaciones), en la primera lista desplegable, seleccione **Administración de aplicaciones móviles de Intune**.

        Ahora puede usar el identificador de cliente de la aplicación en la herramienta de ajuste de aplicaciones. Puede encontrar el identificador de cliente de la aplicación en el Portal de administración de Azure Active Directory, como se describe en la sección [Información general acerca de los identificadores que debe obtener](#overview-of-identifiers-you-need-to-get).

3.  Use los valores **Client-ID** (mediante la propiedad **–a**) y **Redirect-URI** como propiedades de línea de comandos en la herramienta de ajuste de aplicaciones. Si no tiene estos valores, se usarán los predeterminados. Recuerde que debe especificar ambos valores o el usuario final no podrá autenticar correctamente la aplicación procesada.

### Requisitos de autenticación, perfil de aprovisionamiento y certificados

|Requisito|Detalles|
|---------------|-----------|
|Perfil de aprovisionamiento|**Asegúrese de que el perfil de aprovisionamiento sea válido antes de incluirlo**: la herramienta de ajuste de aplicaciones no comprueba si el perfil de aprovisionamiento ha expirado al procesar una aplicación iOS. Si se especifica un perfil de aprovisionamiento expirado, la herramienta de ajuste de aplicaciones incluirá el perfil de aprovisionamiento caducado y no sabrá que hay un problema hasta que la aplicación no se pueda instalar en un dispositivo iOS.|
|Certificado|**Asegúrese de que el certificado sea válido antes de especificarlo**: la herramienta no comprueba si un certificado ha expirado al procesar aplicaciones iOS. Si se proporciona el valor hash de un certificado expirado, la herramienta procesará y firmará la aplicación, pero no se podrá instalar en dispositivos.<br /><br />**Asegúrese de que el certificado proporcionado para firmar la aplicación empaquetada tenga una coincidencia en el perfil de aprovisionamiento**: la herramienta no valida si el perfil de aprovisionamiento tiene una coincidencia con el certificado proporcionado para firmar la aplicación ajustada.|
|Autenticación|Un dispositivo debe tener establecido un PIN para que el cifrado funcione. En dispositivos en los que haya implementado una aplicación ajustada, si se toca la barra de estado en el dispositivo será necesario que el usuario vuelva a autenticarse con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. La directiva predeterminada de una aplicación ajustada es *autenticación al volver a iniciar*. iOS controla cualquier notificación externa (por ejemplo, una llamada telefónica) como salir de la aplicación y, a continuación, volver a iniciarla.<br /><br />En el caso de aplicaciones ajustadas, el primer usuario que inicia sesión en cualquier aplicación ajustada del mismo editor se almacena en la memoria caché. A partir de entonces, solo ese usuario puede tener acceso a la aplicación. Para restablecer el usuario, tiene que anularse la inscripción del dispositivo y volver a inscribirlo.|

### Notas técnicas sobre ADAL y solución de problemas

-   Si no se encuentra ningún recurso ADAL, la herramienta incluirá la biblioteca dinámica ADAL. La herramienta buscará la biblioteca ADAL de nombre **ADALiOS.bundle** en la carpeta raíz.

-   La herramienta no buscará archivos binarios ADAL (si existen) en la aplicación. Si la aplicación se vincula a una versión no actualizada, puede haber errores en tiempo de ejecución durante el inicio de sesión cuando se habilitan directivas de autenticación.

-   [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] obtiene el token de AAD del identificador de recurso MAM de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] para autenticación. Sin embargo, no se utiliza en cualquier llamada que, a su vez, compruebe la validez del token. [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] solo lee el UPN del usuario con sesión iniciada para determinar el acceso de la aplicación. El token de AAD no se usa para las demás llamadas de servicio.

-   Los tokens de autenticación se comparten entre las aplicaciones del mismo editor ya que se almacenan en las llaves compartidas. Si desea aislar una aplicación concreta, debe usar un certificado de firma y un perfil de aprovisionamiento distintos para esa aplicación.

-   Las peticiones de inicio de sesión dobles se impiden si proporciona el identificador de cliente y el URI de redireccionamiento de la aplicación cliente. Este identificador de cliente debe registrarse para obtener acceso al identificador del recurso de MAM de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] MAM en el panel de AAD. Si no lo hace, provocará un error de inicio de sesión cuando se ejecute la aplicación.

## Configurar los derechos de la aplicación
Antes de ajustar la aplicación, puede concederle **derechos** para que tenga permisos y funcionalidades adicionales que normalmente no podría usar.  Un **archivo de derechos** se usa durante la firma de código para especificar permisos especiales dentro de la aplicación (por ejemplo, acceso a una cadena de claves compartida). Los servicios de aplicaciones específicos, denominados **uncionalidades**, se habilitan en Xcode durante el desarrollo de las aplicaciones. Una vez habilitadas, las capacidades se reflejan en el archivo de derechos. Para obtener más información sobre los derechos y las funcionalidades, consulte [Adding Capabilities](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) (Agregar funcionalidades) en la biblioteca para desarrolladores de iOS. Para obtener una lista completa de las capacidades admitidas, consulte [Capacidades admitidas](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SupportedCapabilities/SupportedCapabilities.html).

### Capacidades admitidas por la herramienta de ajuste de aplicaciones para iOS

|Capacidad|Descripción|Uso recomendado|
|--------------|---------------|------------------------|
|Grupos de aplicaciones|Use los grupos de aplicaciones para permitir que varias aplicaciones tengan acceso a contenedores compartidos y que la comunicación entre procesos adicionales entre las aplicaciones sea posible.<br /><br />Para habilitar grupos de aplicaciones, abra el panel **Capacidades** y haga clic en el conmutador **ACTIVAR** de la sección **Grupos de aplicaciones**. Puede agregar grupos de aplicaciones o seleccionar los ya existentes.|Al usar grupos de aplicaciones, use la notación DNS inversa:<br /><br />*group.com.companyName.AppGroup*|
|Modos en segundo plano|Si habilita los modos en segundo plano, la aplicación de iOS podrá seguir ejecutándose en segundo plano.||
|Protección de datos|La opción Protección de datos agrega un nivel de seguridad a los archivos almacenados en el disco mediante la aplicación de iOS. Asimismo, la protección de datos usa el hardware de cifrado integrado en ciertos dispositivos para almacenar archivos en el disco con un formato cifrado. Debe aprovisionar la aplicación para usar la protección de datos.||
|Compras desde la aplicación|La opción de Compras desde la aplicación inserta una opción para acceder a la tienda directamente desde su aplicación, lo que le permitirá conectarse a la misma y procesar los pagos del usuario de forma segura. Puede usar la opción Compras desde la aplicación para pagar por mejorar las funcionalidades o para conseguir contenidos adicionales que pueda usar la aplicación.||
|Uso compartido de cadenas de claves|Si habilita el uso compartido de las cadenas de claves, la aplicación podrá compartir contraseñas en la cadena de claves con otras aplicaciones desarrolladas por el equipo.|Cuando use de forma compartida las cadenas de claves, use la notación DNS inversa:<br /><br />*com.companyName.KeychainGroup*|
|VPN personal|Habilite la VPN personal para permitir a su aplicación crear y controlar un sistema personalizado de la configuración de VPN mediante el marco de la extensión de la red.||
|Notificaciones de inserción|El servicio de notificaciones push de Apple (APN) permite que una aplicación que no se está ejecutando en primer plano notifique al usuario que tiene información para el mismo.|Para que funcionen las notificaciones push, debe usar un perfil de aprovisionamiento específico de la aplicación.<br /><br />Siga los pasos de la [documentación para desarrolladores de Apple](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html).|
|Configuración de accesorios inalámbricos|Si habilita la configuración de accesorios inalámbricos, se agrega al proyecto el marco de accesorios externos y permite a la aplicación configurar accesorios MFi Wi-Fi.||

### Pasos para habilitar derechos

1.  Habilite las capacidades de la aplicación:

    1.  En Xcode, vaya al destino de la aplicación y haga clic en el panel **Capacidades**.

    2.  Active las capacidades adecuadas. Para obtener información detallada sobre cada funcionalidad y sobre cómo determinar los valores correctos, consulte [Adding Capabilities](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) (Agregar funcionalidades) en la biblioteca para desarrolladores de iOS.

    3.  Tenga en cuenta los identificadores que haya creado durante el proceso.

    4.  Compile y firme la aplicación para que se realicen los ajustes oportunos.

2.  Habilite los derechos en el perfil de aprovisionamiento:

    1.  Inicie sesión en el Centro de usuarios registrados para desarrolladores de Apple.

    2.  Cree un perfil de aprovisionamiento para la aplicación. Para obtener instrucciones, consulte [How to Obtain the Prerequisites for the Intune App Wrapping Tool for iOS](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/) (Cómo obtener los requisitos previos para la Herramienta de ajuste de aplicaciones de Intune para iOS).

    3.  En el perfil de aprovisionamiento, habilite los mismos derechos que tiene en su aplicación. Debe proporcionar los mismos identificadores que especificó durante el desarrollo de la aplicación.

    4.  Complete el Asistente para perfiles de aprovisionamiento y descargue el archivo.

3.  Asegúrese de que se hayan cumplido todos los requisitos previos y, a continuación, ajuste la aplicación.

### Solucionar errores comunes con derechos
Si la herramienta de ajuste de aplicaciones para iOS muestra un error de derecho, intente los siguientes pasos de solución de problemas.

|Problema|Causa|Solución|
|---------|---------|--------------|
|Error al analizar los derechos creados a partir de la aplicación de entrada.|La herramienta de ajuste de aplicaciones no puede leer el archivo de derechos que se ha extraído de la aplicación. Es posible que el archivo de derechos sea incorrecto.|Compruebe el archivo de derechos de la aplicación. Para ello, siga las instrucciones que se detallan a continuación. Al inspeccionar el archivo de derechos, busque cualquier sintaxis incorrecta. Recuerde que el archivo debe estar en formato XML.|
|Faltan los derechos en el perfil de aprovisionamiento (se enumeran los derechos que faltan). Vuelva a empaquetar la aplicación con un perfil de aprovisionamiento que tenga estos derechos.|Existe una incoherencia entre los derechos habilitados en el perfil de aprovisionamiento y las capacidades habilitadas en la aplicación. Esta disparidad también se aplica a los identificadores de capacidades concretas (por ejemplo, grupos de aplicaciones, acceso a cadenas de claves, etc.).|Por lo general, puede crear un nuevo perfil de aprovisionamiento que tenga las mismas capacidades que la aplicación. Cuando no coinciden los identificadores entre el perfil y la aplicación, la herramienta de ajuste de aplicaciones reemplazará los identificadores si le es posible. Si sigue apareciendo este error después de crear un nuevo perfil de aprovisionamiento, puede intentar quitar los derechos de la aplicación mediante el parámetro **– e** (consulte la sección "Usar el parámetro – e para quitar derechos de una aplicación" a continuación).|

### Buscar los derechos existentes de una aplicación firmada
Para revisar los derechos existentes de una aplicación firmada y de un perfil de aprovisionamiento:

1.  Busque el archivo .ipa y cambie la extensión a .zip.

2.  Expanda el archivo .zip. Esto creará una carpeta de carga que contiene el lote .app.

3.  Use la herramienta codesign para comprobar los derechos del lote .app de la siguiente manera:

    ```
    $ codesign -d --entitlements :- "Payload/YourApp.app"
    ```
    donde `YourApp.app` es el nombre del lote .app.

4.  Use la herramienta de seguridad para comprobar los derechos del perfil de aprovisionamiento incrustado de la aplicación:

    ```
    $ security -D -i "Payload/YourApp.app/embedded.mobileprovision"
    ```
    donde `YourApp.app` es el nombre del lote .app.

### Usar el parámetro – e para quitar derechos de una aplicación
Este comando quita cualquier funcionalidad habilitada en la aplicación que no esté en el archivo de derechos. Si quita funcionalidades que la aplicación esté usando, puede interrumpirla. Un caso en el que podría quitar las funcionalidades que faltan es una aplicación producida por el proveedor que tenga todas las funcionalidades de forma predeterminada.

```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -e
```

## Seguridad y privacidad de la herramienta de ajuste de aplicaciones
Use los procedimientos recomendados de seguridad y privacidad siguientes al usar la herramienta de ajuste de aplicaciones.

-   El certificado de firma, el perfil de aprovisionamiento y la aplicación de línea de negocio que especifique deben estar en el mismo equipo Mac que use para ejecutar la herramienta de ajuste de aplicaciones. Si los archivos están en una ruta de acceso UNC, asegúrese de que se pueda acceder a ellos desde el equipo Mac. La ruta de acceso debe estar protegida mediante la firma SMB o IPsec.

    La aplicación ajustada que se importa a la consola de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] debe estar en el mismo equipo en el que se ejecuta la herramienta. Si el archivo está en una ruta de acceso UNC, asegúrese de que se pueda acceder a ella desde el equipo en el que se ejecuta la consola de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. La ruta de acceso debe estar protegida mediante la firma SMB o IPsec.

-   El entorno en donde se descarga la herramienta de ajuste de aplicaciones desde el sitio Centro de descarga de Microsoft debe protegerse mediante la firma SMB o IPsec.

-   La aplicación que procese debe proceder de un origen de confianza para garantizar la protección frente a ataques.

-   Asegúrese de que la carpeta de salida especificada en la herramienta de ajuste de aplicaciones esté protegida, especialmente si se trata de una carpeta remota.

-   Las aplicaciones iOS que incluyen un cuadro de diálogo de carga de archivos pueden permitir a los usuarios sortear, cortar, copiar y pegar restricciones aplicadas a la aplicación. Por ejemplo, un usuario podría usar el cuadro de diálogo de carga de archivos para cargar una captura de pantalla de los datos de aplicación.

-   Cuando los usuarios supervisan la carpeta de documentos en su dispositivo desde dentro de una aplicación ajustada, puede que vean una carpeta de nombre **.msftintuneapplauncher**. Si esta carpeta se cambia o elimina, esto podría afectar al funcionamiento correcto de las aplicaciones restringidas.

### Consulte también
- [Decidir cómo preparar las aplicaciones para la administración de aplicaciones móviles mediante Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)</br>
- [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)</br>
- [Use the SDK to enable apps for mobile application management (Usar el SDK para habilitar aplicaciones para la administración de aplicaciones móviles)](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Aug16_HO1-->


