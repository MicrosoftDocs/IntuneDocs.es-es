---
title: "Guía para desarrolladores acerca del SDK de aplicaciones de Microsoft Intune para iOS | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b7f62c5ee18d8f69fa174f09a1c46b6925c7517c
ms.openlocfilehash: 820ec2da0554f0af383895482241be7d1c0cf305


---

# Guía para desarrolladores acerca del SDK de aplicaciones de Microsoft Intune para iOS

> [!NOTE]
> Puede que quiera leer la [Guía de introducción al SDK de la aplicación Intune](intune-app-sdk-get-started.md), en la que se explica cómo preparar la integración en cada plataforma compatible.* 

El SDK de la aplicación Microsoft Intune para iOS permite incorporar la administración de aplicaciones móviles (MAM) de Intune en su aplicación iOS. Una aplicación habilitada para MAM está integrada con el SDK para aplicaciones de Intune y permite a los administradores de TI implementar directivas en su aplicación móvil cuando la aplicación se administra de manera activa.

# Qué hay en el SDK

El SDK de la aplicación Intune para iOS incluye una biblioteca estática, archivos de recursos, encabezados de API, un plist de configuración de depuración y una herramienta de configuración. Las aplicaciones móviles pueden incluir simplemente los archivos de recursos y vincularse estáticamente para la mayor parte de la aplicación de las directivas. Las características avanzadas de MAM de Intune se aplican a través de las API.
En esta guía se tratará el uso de lo siguiente al integrar el SDK para aplicaciones de Intune para iOS:

* **`libIntuneMAM.a`**: biblioteca del SDK para aplicaciones de Intune. Vincule esta biblioteca a su proyecto para que su aplicación móvil esté habilitada para MAM. Encontrará instrucciones en la sección "Creación de la aplicación con el SDK para aplicaciones de Intune".

* **`IntuneMAMResources.Bundle`**: lote de recursos que contiene los recursos en los que se basa el SDK. 

* **Encabezados**: expone las API del SDK para aplicaciones de Intune. Si usa una API, deberá incluir el archivo de encabezado que contiene la API. 

# Cómo funciona el SDK para aplicaciones de Intune

El objetivo del SDK para aplicaciones de Intune para iOS es agregar capacidades de administración a las aplicaciones de iOS con mínimos cambios en el código. La reducción de la cantidad de los cambios del código disminuye el tiempo de comercialización, a la vez que aumenta la coherencia y la estabilidad de la aplicación móvil. 

La aplicación debe vincularse a la biblioteca estática e incluir el lote de recursos. El archivo MAMDebugSettings.plist es opcional y puede incluirse en el paquete para simular las directivas MAM que se aplican a la aplicación sin necesidad de implementar la aplicación mediante Microsoft Intune. Además, en las compilaciones de depuración, se pueden aplicar las directivas del archivo MAMDebugSettings.plist transfiriendo el archivo MAMDebugSettings.plist al directorio de documentos de la aplicación mediante el uso compartido de archivos de iTunes.

# Creación de una aplicación con el SDK para aplicaciones de Intune 

Complete los pasos siguientes para habilitar el SDK para aplicaciones de Intune:

1. Vincule a la biblioteca `libIntuneMAM.a` mediante el siguiente procedimiento:

    Arrastre y coloque la biblioteca libIntuneMAM.a a la lista de "Marcos y bibliotecas vinculados" del destino del proyecto.  

    ![SDK de la aplicación Intune para iOS: marcos y bibliotecas vinculados](../media/intune-app-sdk-ios-linked-frameworks-and-libraries.png)
 
    **Nota**: al publicar en la tienda de aplicaciones, use la versión de libIntuneMAM.a que se compila para publicación, y no la versión de depuración. La versión de lanzamiento estará en la carpeta "release". La versión de depuración tiene un resultado detallado que es adecuado para problemas de depuración con el SDK para aplicaciones de Intune.

2. Agregue los siguientes marcos de iOS al proyecto (si faltan).
    * `MessageUI.framework`
    * `Security.framework`
    * `MobileCoreServices.framework`
    * `SystemConfiguration.framework`
    * `libsqlite3.dylib`
    * `libc++.dylib`
    * `ImageIO.framework`
    * `LocalAuthentication.Framework`
    * `AudioToolbox.framework`<br>

    **Nota**: si la aplicación está destinada a iOS7, establezca el atributo "Estado" de `LocalAuthentication.Framework` en "Opcional". 

    Si no se establece el "Estado" , se producirá un error al iniciarse la aplicación en iOS7.

    **Nota**: Xcode 7 ha cambiado las extensiones `.dylib` a `.tbd`.

3. Agregue el lote de recursos `IntuneMAMResources.bundle` al proyecto arrastrando el lote de recursos en "Copiar recursos del lote" en "Fases de compilación". 

    ![Entune App SDK iOS - copy bundle resources](../media/intune-app-sdk-ios-copy-bundle-resources.png)

4. Agregue `-force_load {PATH_TO_LIB}/libIntuneMAM.a` a cualquiera de lo siguiente, reemplazando `{PATH_TO_LIB}` por la ubicación del SDK para aplicaciones de Intune:
    * ajuste de la configuración de compilación OTHER_LDFLAGS del proyecto 
    * "Otras marcas del enlazador" de la interfaz de usuario<br>

    **Nota**: para encontrar `PATH_TO_LIB`, seleccione el archivo `libIntuneMAM.a` y elija "Obtener información" en el menú "Archivo". Copie y pegue la información "Dónde" (la ruta de acceso) de la sección "General" de la ventana "Información".

5. Si la aplicación móvil define un guión gráfico o Nib principal en su `info.plist`, quite los campos del archivo Nib principal o del guión gráfico principal. Agregue los valores de guión gráfico o Nib que quitó anteriormente en un diccionario nuevo llamado `IntuneMAMSettings` con los siguientes nombres de clave, según corresponda:
    * `MainStoryboardFile`
    * `MainStoryboardFile~ipad`
    * `MainNibFile`
    * `MainNibFile~ipad `
    
    Si la aplicación móvil no define un Nib principal o el guión gráfico en su `info.plist`, estos valores **no son necesarios**. 

    **Nota**: para ver `info.plist` en formato sin procesar (para ver los nombres de claves), haga clic en cualquier lugar del cuerpo del documento y cambie el tipo de vista a "Mostrar claves/valores sin procesar".

6. Para habilitar el uso compartido de la cadena de claves (si aún no está habilitado), haga clic en "Capacidades" en cada destino del proyecto y habilite el modificador del uso compartido de cadena de claves. El uso compartido de cadena de claves es necesario para continuar con el siguiente paso.

    **Nota**: el perfil de aprovisionamiento debe admitir nuevos valores de uso compartido de cadena de claves. Los grupos de acceso a cadena de claves deben admitir un carácter comodín. Para comprobarlo, abra el archivo `.mobileprovision` en un editor de texto, busque "keychain-access-groups" y asegúrese de que tiene un carácter comodín, por ejemplo: 

       <key>keychain-access-groups</key>
       <array>
       <string>YOURBUNDLESEEDID.*</string>
       </array>

7. Después de habilitar el uso compartido de cadena de claves, siga estos pasos para crear un grupo de acceso independiente en el que se almacenarán los datos del SDK para aplicaciones de Intune. Puede crear un grupo de acceso a cadena de claves mediante la interfaz de usuario o mediante el archivo de derechos:

    Mediante la interfaz de usuario para crear un grupo de acceso a cadena de claves: 
    
    * Si la aplicación móvil no tiene ningún grupo de acceso a cadena de claves definido, agregue el id. del lote de la aplicación como el primer grupo.
    * Agregue el grupo de cadenas de claves compartidas com.microsoft.intune.mam. El SDK para aplicaciones de Intune usa este grupo de acceso para almacenar datos.  
    * Agregue el lote de recursos `com.microsoft.adalcache` a los grupos de acceso existentes. 
 
    ![SDK para aplicaciones de Intune de IOS: uso compartido de cadena de claves](../media/intune-app-sdk-ios-keychain-sharing.png)

    Si usa el archivo de derechos para crear el grupo de acceso a la cadena de claves, en lugar de la interfaz de usuario normal, deberá anteponer `$(AppIdentifierPrefix)` al grupo de accesos de cadena de claves en el archivo de derechos. Por ejemplo: `$(AppIdentifierPrefix)com.microsoft.intune.mam` y `$(AppIdentifierPrefix)com.microsoft.adalcache`.

    **Nota**: un archivo de derechos es un archivo XML único para su aplicación móvil que se usa para especificar permisos especiales y capacidades dentro de su aplicación iOS.

8. Para las aplicaciones móviles que se desarrollan para iOS 9+, debe incluir cada protocolo que su aplicación móvil pasa a `UIApplication canOpenURL` en la matriz `LSApplicationQueriesSchemes` del archivo `info.plist` de la aplicación móvil. Además, para cada protocolo que se muestra, se tiene que agregar y anexar un nuevo protocolo con `-intunemam`. También debe incluir `http-intunemam`, `https-intunemam`y `ms-outlook-intunemam` en la matriz. 

9. Si la aplicación define los esquemas de direcciones URL en su `info.plist file`, agregue otro esquema, con un sufijo `-intunemam` para cada esquema de dirección URL.

10. Si la aplicación tiene grupos de aplicaciones definidos en sus derechos, agregue estos grupos al diccionario `IntuneMAMSettings` en la clave `AppGroupIdentitifiers` como una matriz de cadenas.

11. Vincula la aplicación móvil a la biblioteca ADAL. La biblioteca ADAL para Objective C está [disponible en Github](https://github.com/AzureAD/azure-activedirectory-library-for-objc).

    **Nota**: el SDK para aplicaciones de Intune se ha probado con el código de la bifurcación del agente de AAL desde el 19/6/2015. Asegúrese de que está vinculando con la versión más reciente o de trabajo de la biblioteca ADAL.

12. Incluya el lote de `ADALiOSBundle.bundle resource` en el proyecto arrastrando el lote de recursos en "Copiar recursos del lote" en "Fases de compilación".

13. Use la opción del enlazador `-force_load PATH_TO_ADAL_LIBRARY` al vincular a la biblioteca.

    Agregue `-force_load {PATH_TO_LIB}/libADALiOS.a` al ajuste de la configuración de compilación OTHER_LDFLAGS del proyecto u "Otras marcas del enlazador" en la interfaz de usuario. "PATH_TO_LIB" debe reemplazarse por la ubicación de archivos binarios de ADAL. 

Si su aplicación móvil usa ADAL para su propia autenticación, revise la sección "Establecimiento de la configuración de la biblioteca de autenticación de Azure Directory" que encontrará aquí.

## Telemetría 

El SDK para aplicaciones de Intune registra los datos de telemetría en eventos de uso de manera predeterminada que se envían a Microsoft Intune.

Los datos se registran en los siguientes eventos de uso: 

1. Inicio de la aplicación para ayudar a Microsoft Intune a obtener información acerca del uso de la aplicación habilitada para MAM por tipo de administración.

2. Llamada de la API de EnrollApplication para ayudar a Microsoft Intune a obtener información acerca de la tasa de éxito y otras métricas de rendimiento diversas de la llamada de enrollApplication desde el cliente.

**Nota**: si decide no enviar datos de telemetría del SDK para aplicaciones de Intune a Microsoft desde su aplicación móvil, **debe deshabilitar** la transmisión de telemetría del SDK para aplicaciones de Intune estableciendo la propiedad `MAMTelemetryDisabled` en "Sí" en `IntuneMAMSettings`.

## Configuración de la Biblioteca de autenticación de Azure Directory (ADAL) (opcional)

El SDK para aplicaciones de Intune usa ADAL para su escenario de inicio condicional y de autenticación. Normalmente, ADAL requiere que las aplicaciones se registren y que obtengan un id. único, conocido como `ClientID`, y otros identificadores, para garantizar la seguridad de los tokens concedidos a la aplicación. El SDK para aplicaciones de Intune usa valores de registro predeterminados al ponerse en contacto con Azure Active Directory.  Si la propia aplicación usa ADAL para su escenario de autenticación, la aplicación debe usar sus valores de registro existentes y reemplazar el valor predeterminado del SDK para aplicaciones de Intune para asegurarse de que a los usuarios finales no se les solicitará la autenticación dos veces (una por el SDK para aplicaciones de Intune y otra por la aplicación). 

Los siguientes pasos son necesarios si la propia aplicación usa ADAL para la autenticación. Si la aplicación móvil no se basa en ADAL, no será necesario realizar ninguna otra acción. 

1. En `Info.plist`del proyecto, en un diccionario `IntuneMAMSettings` con el nombre de clave `ADALClientId`, especifique el `ClientID` que se usará para llamadas de ADAL. 

2. En `Info.plist`del proyecto, en el diccionario `IntuneMAMSettings` con el nombre de clave `ADALRedirectUri`, especifique el URI de redirección que se usará para llamadas de ADAL. También debe especificar `ADALRedirectScheme` según el formato del URI de redirección de la aplicación.

## Compilación de sus extensiones (opcional) 

Al compilar extensiones, siga las mismas instrucciones para compilar su aplicación móvil, tal como se describe en la sección "Creación de una aplicación con el SDK para aplicaciones de Intune" que se encuentra aquí. Además, actualice el archivo info.plist de cada extensión para agregar una clave ContainingAppBundleId en el diccionario IntuneMAMSettings con el valor del id. del lote de la aplicación contenedora.

## Compilación de los marcos (opcional)

Con los últimos cambios al SDK para aplicaciones de Intune, no es necesario compilar su aplicación móvil con cualquier marca de enlazador específica si la aplicación móvil contiene marcos de aplicaciones incrustados. 

## Archivos de imagen al inicio (opcional)

Cuando una aplicación habilitada para MAM se administra activamente con Microsoft Intune, el SDK para aplicaciones de Intune mostrará una pantalla de inicio al iniciar la aplicación para indicar al usuario que la aplicación está administrada. Opcionalmente, puede agregar archivos de imagen para que aparezcan en la página de inicio "Administradas por su empresa". Use las siguientes indicaciones para las imágenes:

* Agregue los nombres de archivo en el diccionario `IntuneMAMSettings` del archivo info.plist de la aplicación con los nombres de clave `SplashIconFile` y `SplashIconFile~ipad`. 

* Tamaño de la imagen y requisitos:

    * 180 x 180 para iPhone 6s Plus e iPhone 6 Plus, 120 x 120 para otros modelos de iPhone y 152 x 152 para iPad. 
    
    * Quitar la extensión `.png` de los nombres de archivo 
    
    * Use la opción del enlazador `@2x` para las versiones de escala 2x y el sufijo `@3x` para las versiones de escala 3x de los archivos de imagen. Si las imágenes no tienen el tamaño correcto, se escalarán para ajustarse. Si no se especifican los valores de SplashIconFile, el SDK para aplicaciones de Intune selecciona uno de los iconos de la aplicación (60 x 60 para todos los iPhone, 76 x 76 para iPad).

**Nota**: esta pantalla se desencadena en el inicio, pero el usuario la puede descartar de manera permanente.

# Establecer la configuración del SDK para aplicaciones de Intune

El diccionario `IntuneMAMSettings` que se encuentra en el archivo `info.plist` de la aplicación se usa para configurar el SDK para aplicaciones de Intune. La siguiente es una lista de todas las configuraciones admitidas. 

Es posible que se hayan tratado algunos de estos valores en las secciones anteriores y que otros no se apliquen a todas las aplicaciones. 

Configuración  | Tipo  | Definición | ¿Necesario?
--|--|--|--
ADALClientId  | String  | Identificador de cliente de AAD de la aplicación. | Se requiere si la aplicación ha usado ADAL.
ADALRedirectUri  | String  | URI de redirección de AAD de la aplicación. | Se requiere si la aplicación ha usado ADAL. 
AppGroupIdentifier | Matriz de cadena  | Matriz de grupos de aplicación de la sección de grupos de com.apple.security.application-groups de derechos de la aplicación. | Se requiere si la aplicación usa grupos de aplicaciones.
ContainingAppBundleId  | String | Especifica el id. del lote de la aplicación contenedora de la extensión. | Se requiere para las extensiones de iOS.
MainNibFile<br>MainNibFile~ipad  | String  | Esta configuración debe contener el nombre de archivo nib principal de la aplicación.  | Obligatorio si la aplicación define MainNibFile en su info.plist.
MainStoryboardFile<br>MainStoryboardFile~ipad  | String  | Esta configuración debe contener el nombre de archivo del guión gráfico principal de la aplicación. | Se requiere si la aplicación define UIMainStoryboardFile en su info.plist
SplashIconFile <br>SplashIconFile~ipad  | String  | Especifica el archivo del icono de la pantalla de presentación de Intune. Vea la sección "Archivos de imagen al inicio" para obtener más detalles. | Opcional.
SplashDuration | Número | Cantidad mínima de tiempo en segundos en que se mostrará la pantalla de presentación de Intune al iniciar la aplicación. El valor predeterminado es 1,5. | Opcional.
ADALLogOverrideDisabled | Boolean  | Especifica si el SDK enrutará todos los registros de ADAL (incluidas las llamadas de ADAL desde la aplicación de haberlas) a su propio archivo de registro. El valor predeterminado es NO. Establezca en Sí si desea que la aplicación establezca su propia devolución de llamada de registros ADAL. | Opcional.

# Encabezados para el SDK para aplicaciones de Intune 

Los encabezados siguientes incluyen las llamadas a funciones API necesarias para habilitar la funcionalidad del SDK para aplicaciones de Intune. 

    IntuneMAMAsyncResult.h
    IntuneMAMDataProtectionInfo.h
    IntuneMAMDataProtectionManager.h
    IntuneMAMFileProtectionInfo.h
    IntuneMAMFileProtectionManager.h
    IntuneMAMPolicyDelegate.h
    IntuneMAMLogger.h

# Depuración del SDK para aplicaciones de Intune en Xcode

Antes de probar la aplicación habilitada para MAM con Microsoft Intune, puede usar `Settings.bundle` mientras se encuentre en Xcode. Esto le permitirá establecer directivas de prueba sin necesidad de una conexión a Intune. Para habilitarlo:

* Agregue un `Settings.bundle` con el botón secundario en la carpeta de nivel superior del proyecto. Seleccione "Agregar -> Nuevo archivo" en el menú. Seleccione la plantilla de "Lote de configuración" en "Recursos" para agregarla.

* Solo en las compilaciones de depuración, copie el archivo `MAMDebugSettings.plist` en `Settings.bundle`.

* En `Root.plist` (en Settings.bundle), agregue una preferencia del panel secundario "Tipo", "FileName" `MAMDebugSettings`.

* En "Configuración -> SuNombreDeAplicación", active o desactive "Habilitar directivas de prueba".

* Inicie la aplicación (ya sea dentro o fuera de Xcode). 

* En "Configuración -> SuNombreDeAplicación -> Habilitar directivas de prueba", active o desactive una directiva, por ejemplo, "PIN".

* Inicie la aplicación (ya sea dentro o fuera de Xcode). Compruebe que el PIN funciona según lo previsto.

> [!NOTE]
> Ahora puede usar "Configuración -> SuNombreDeAplicación -> Habilitar directivas de prueba" para habilitar y activar o desactivar la configuración.

# Prácticas recomendadas de iOS

A continuación, se explican algunas prácticas recomendadas al desarrollar para iOS:

El sistema de archivos iOS distingue mayúsculas de minúsculas. Asegúrese de que las mayúsculas o minúsculas son correctas para los nombres de archivo como `libIntuneMAM.a` y `IntuneMAMResources.bundle`.

Si Xcode tiene problemas para encontrar `libIntuneMAM.a`, puede corregir el problema agregando la ruta de acceso a esta biblioteca en las rutas de acceso de búsqueda del enlazador.




<!--HONumber=Jul16_HO3-->


