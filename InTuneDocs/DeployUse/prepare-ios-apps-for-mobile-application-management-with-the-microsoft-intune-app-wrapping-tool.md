---
title: Ajuste de aplicaciones iOS con la herramienta de ajuste de aplicaciones | Microsoft Intune
description: "Utilice la información de este tema para obtener información sobre cómo ajustar las aplicaciones iOS sin modificar el código de la propia aplicación. Prepare las aplicaciones de modo que pueda aplicar las directivas de administración de aplicaciones móviles."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 99ab0369-5115-4dc8-83ea-db7239b0de97
ms.reviewer: oldang
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c67a5042fd177a4c5bd897092e84281db0977f5e
ms.openlocfilehash: 2c187b61b8fe25b2870d0cbc62f8352494583fc2


---

# Preparar aplicaciones iOS para la administración de aplicaciones móviles con la Herramienta de ajuste de aplicaciones de Intune
Use la **Herramienta de ajuste de aplicaciones de Microsoft Intune para iOS** para modificar el comportamiento de las aplicaciones iOS internas mediante la restricción de características de la aplicación sin modificar el código de la propia aplicación.

La herramienta es una aplicación de línea de comandos de Mac OS que crea un "contenedor" alrededor de una aplicación. Una vez que se procesa la aplicación, puede cambiar su funcionalidad con las [directivas de administración de aplicaciones móviles](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) de Intune que configure.

Para descargar la herramienta, consulte [Microsoft Intune App Wrapping Tool for iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) (Herramienta de ajuste de aplicaciones de Microsoft Intune para iOS).



## Paso 1. Cumplir los requisitos previos para el uso de la herramienta de ajuste de aplicaciones
Lea [esta entrada de blog](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) para obtener más información sobre los requisitos previos y cómo establecerlos.

|Requisito|Más información|
|---------------|--------------------------------|
|Sistema operativo y conjunto de herramientas admitidos|Debe ejecutar la herramienta de ajuste de aplicaciones en un equipo Mac OS que ejecute OS X 10.8.5 o posterior que tenga instalada la versión 5 o posterior del conjunto de herramientas XCode.|
|Certificado de firma y perfil de aprovisionamiento|Debe poseer un perfil de aprovisionamiento y un certificado de firma de Apple. Consulte la [documentación para desarrolladores de Apple](https://developer.apple.com/).|
|Procesamiento de una aplicación con la herramienta de ajuste de aplicaciones|Las aplicaciones deben estar desarrolladas y firmadas por la compañía o por un fabricante de software independientes (ISV). No se puede usar esta herramienta para procesar aplicaciones de la tienda de Apple. Las aplicaciones deben estar escritas para iOS 8.0 o posterior. Las aplicaciones, además, deben estar en formato ejecutable independiente de la posición (PIE). Para obtener más información acerca del formato PIE, consulte la documentación para desarrolladores de Apple. Por último, la aplicación debe tener el formato de extensión **.app** o **.ipa**.|
|Aplicaciones que la herramienta de ajuste no puede procesar|Aplicaciones cifradas, aplicaciones sin firmar y aplicaciones con atributos de archivo extendidos.|
|Derechos de configuración de la aplicación|Debe establecer los derechos antes de ajustar la aplicación. Estos derechos conceden permisos de aplicación adicionales y capacidades que van más allá de aquellas que se conceden en general. Consulte [Configurar los derechos de la aplicación](#setting-app-entitlements) para obtener instrucciones.|

## Paso 2. Instalar la herramienta de ajuste de aplicaciones

1.  Desde el [repositorio hospedado en GitHub](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) denominado **Microsoft Intune App Wrapping Tool for iOS** (Herramienta de ajuste de aplicaciones de Microsoft Intune para iOS), descargue los archivos de la herramienta de ajuste de aplicaciones localmente en un equipo Mac OS.

2.  Haga doble clic en el archivo de instalación **Microsoft Intune App Wrapping Tool for iOS.dmg**. Aparecerá una ventana con los términos de licencia. Lea detenidamente el documento.

3. Elija **Acepto** para aceptar los términos de licencia, con lo que se monta el paquete en el equipo.

4.  Abra el paquete **IntuneMAMPackager** y guarde los archivos en una carpeta local en el equipo Mac OS. Ahora está preparado para ejecutar la herramienta de ajuste de aplicaciones.

## Paso 3: Ejecutar la herramienta de ajuste de aplicaciones
* En el equipo Mac OS, abra una ventana de Terminal y navegue hasta la carpeta donde guardó los archivos de la herramienta de ajuste de aplicaciones. La herramienta ejecutable se denomina **IntuneMAMPackager** y se encuentra en **IntuneMAMPackager/Contents/MacOS**. Debe ejecutar el comando de la manera siguiente:

    ```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> -p /<path to provisioning profile> -c <SHA1 hash of the certificate> [-b [<output app build string>]] [-v] [-e] [-x /<array of extension provisioning profile paths>]

    ```

    > [!NOTE]
    > Algunos parámetros son opcionales, tal como se muestra en la tabla siguiente.

    **Ejemplo:** el comando del ejemplo siguiente ejecuta la herramienta de ajuste de aplicaciones en una aplicación denominada **MyApp.ipa**. Se especifican un perfil de aprovisionamiento y el hash SHA-1. Se crea la aplicación procesada, denominada **MyApp_Wrapped.ipa**, y se almacena en la carpeta Escritorio del usuario.

    ```
    ./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i ~/Desktop/MyApp.ipa -o ~/Desktop/MyApp_Wrapped.ipa -p ~/Desktop/My_Provisioning_Profile_.mobileprovision -c 12A3BC45D67EF8901A2B3CDEF4ABC5D6E7890FAB  -v true
    ```
    Puede usar las siguientes propiedades de línea de comandos con la herramienta de ajuste de aplicaciones:

    |Propiedad|Cómo usarla|
  |------------|--------------------|
  |**-i**|`<Path of the input native iOS application file>`. El archivo debe acabar en .app o .ipa. |
  |**-o**|`<Path of the wrapped output application>` |
  |**-p**|`<Path of your provisioning profile for iOS apps>`|
  |**-c**|`<SHA1 hash of the signing certificate>`|
    |-h|Muestra información de uso detallada sobre las propiedades de línea de comandos disponibles para la herramienta de ajuste de aplicaciones.|
  |-v|(Opcional pero útil) Muestra mensajes detallados en la consola.|
  |-e | (Opcional) Use esta marca para que la herramienta de ajuste de aplicaciones quite los derechos que faltan mientras procesa la aplicación. Consulte la sección "Configurar los derechos de la aplicación" para obtener más detalles.|
  |-xe| (Opcional) Imprime información sobre las extensiones de iOS de la aplicación y sobre los derechos necesarios para usarlas. Consulte la sección "Configurar los derechos de la aplicación" para obtener más detalles. |
  |-x| (Opcional) `<An array of paths to extension provisioning profiles>`. Úsela si la aplicación necesita perfiles de aprovisionamiento de extensión.|
  |-f |(Opcional) `<Path to a plist file specifying arguments.>` Use esta marca delante del archivo [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html) si decide usar la plantilla plist para especificar el resto de las propiedades IntuneMAMPackager: -i, -o, -p, etc. Consulte la sección "Usar un archivo plist para la entrada de argumentos" para obtener más información. |
  |-b|(Opcional) Use -b sin un argumento si quiere que la aplicación de salida ajustada tenga la misma versión de paquete que la aplicación de entrada (no recomendado). <br/><br/> Use `-b <custom bundle version>` si quiere que la aplicación ajustada tenga un valor CFBundleVersion personalizado. Si decide especificar un valor CFBundleVersion personalizado, se recomienda que incremente el valor de CFBundleVersion de la aplicación nativa por el componente menos significativo, por ejemplo, 1.0.0 -> 1.0.1. |


###Usar un archivo plist para la entrada de argumentos
Una manera fácil de ejecutar la herramienta de ajuste de aplicaciones consiste en colocar todos los argumentos de comando en un archivo [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html). El formato de archivo plist es similar a XML. Se puede usar para la entrada de argumentos de línea de comandos mediante una interfaz de formulario.

En la carpeta **IntuneMAMPackager/Contents/MacOS**, abra `Parameters.plist`, que es una plantilla plist en blanco, con un editor de texto o Xcode. Escriba los argumentos para las claves siguientes:

| Clave de plist |  Valor predeterminado| Notas |
|------------------|--------------|-----|
| Ruta de acceso del paquete de aplicación de entrada  |vacío| Igual que -i. |
| Ruta de acceso del paquete de aplicación de salida |vacío| Igual que -o.|
| Ruta de acceso del perfil de aprovisionamiento |vacío| Igual que -p. |
| Hash del certificado SHA-1 |vacío| Igual que -c. |
| Modo detallado habilitado |false| Igual que -v. |
| Quitar los derechos que faltan | false| Igual que -c.|
| Impedir la compilación predeterminada |false | Equivale a usar -b sin argumentos. |
|Invalidación de la cadena de compilación | vacío| Valor de CFBundleVersion personalizado de la aplicación de salida ajustada. |
|Rutas de acceso del perfil de aprovisionamiento de extensión | vacío| Matriz de perfiles de aprovisionamiento de extensión para la aplicación.
  

Por último, ejecute IntuneMAMPackager con plist como único argumento:

```
./IntuneMAMPackager –f Parameters.plist
```

* Una vez que se complete el proceso, se mostrará el mensaje "**The application was successfully wrapped**" (La aplicación se ajustó correctamente).

    Si se produce un error, consulte [Mensajes de error](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md#error-messages) para obtener ayuda.

*   La aplicación ajustada se guarda en la carpeta de salida que especificó anteriormente. Ahora puede cargar la aplicación en [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] y asociarla a una directiva de administración de aplicaciones móviles.

    > [!IMPORTANT]
    > Al cargar una aplicación ajustada, puede intentar actualizar una versión anterior de la aplicación si ya se ha implementado en Intune una versión anterior (ajustada o nativa). Si experimenta un error, cargue la aplicación como una aplicación nueva y elimine la versión anterior.

    A continuación, podrá implementar la aplicación en sus grupos de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] y esta se ejecutará en el dispositivo con las restricciones de aplicación especificadas.

## Archivos de registro y mensajes de error
Use la siguiente información para solucionar los problemas que tenga con la herramienta de ajuste de aplicaciones.

### Mensajes de error
Si la herramienta de ajuste de aplicaciones no se completa correctamente, se mostrará uno de los siguientes mensajes de error en la consola:

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
|Se especificó un certificado de firma no válido. Especifique un certificado de firma de Apple válido.|Asegúrese de haber descargado el certificado de firma correcto desde el portal para desarrolladores de Apple. El certificado podría haber expirado o puede que falte una clave pública o privada. Si el perfil de aprovisionamiento y el certificado de Apple se pueden usar para firmar correctamente una aplicación en Xcode, son válidos para la herramienta de ajuste de aplicaciones.|
|La aplicación de entrada especificada no es válida. Especifique una aplicación válida.|Asegúrese de que tenga una aplicación iOS válida que se haya compilado como archivo .app o .ipa.|
|La aplicación de entrada especificada está cifrada. Especifique una aplicación sin cifrar válida.|La herramienta de ajuste de aplicaciones no es compatible con aplicaciones cifradas. Proporcione una aplicación sin cifrar.|
|La aplicación de entrada especificada no está en un formato ejecutable independiente de la posición (PIE). Especifique una aplicación válida en formato PIE.|Las aplicaciones de archivo ejecutable independiente de la posición (PIE) se pueden cargar en una dirección de memoria aleatoria al ejecutarse, lo que puede tener ventajas de seguridad. Para obtener más información, consulte la documentación para desarrolladores de Apple.|
|La aplicación de entrada especificada ya se ajustó. Especifique una aplicación sin ajustar válida.|No puede procesar una aplicación que la herramienta ya procesó. Si desea volver a procesar una aplicación, ejecute la herramienta con la versión original de la aplicación.|
|La aplicación de entrada especificada no está firmada. Especifique una aplicación firmada válida.|La herramienta de ajuste de aplicaciones requiere que las aplicaciones estén firmadas. Consulte la documentación para desarrolladores para aprender a firmar una aplicación ajustada.|
|La aplicación de entrada especificada debe tener formato .ipa o .app.|La herramienta de ajuste de aplicaciones solo acepta aplicaciones con las extensiones .app e .ipa. Asegúrese de que el archivo de entrada tenga una extensión válida y se haya compilado como archivo .app o .ipa.|
|La aplicación de entrada especificada ya se ajustó y se encuentra en la última versión de la plantilla de directiva.|La herramienta de ajuste de aplicaciones no ajustará una aplicación ajustada existente con la última versión de la plantilla de directiva.|
|ADVERTENCIA: no ha especificado un hash de certificado SHA1. Asegúrese de que la aplicación ajustada se firme antes de implementarla.|Asegúrese de especificar un valor de hash SHA1 válido después de la marca de línea de comandos **–c**. |

### Archivos de registro de la herramienta de ajuste de aplicaciones
Las aplicaciones que se ajustaron mediante la herramienta de ajuste de aplicaciones generan los registros que se escriben en la consola del dispositivo cliente de iOS. Esta información resulta útil cuando se tienen problemas con la aplicación y se necesita diagnosticar si el problema está relacionado con la herramienta de ajuste de aplicaciones. Para resolver este problema, use los siguientes pasos:

1.  Reproduzca el problema ejecutando la aplicación.

2.  Recopile la salida de consola siguiendo las instrucciones de [Depuración de aplicaciones iOS implementadas](https://developer.apple.com/library/ios/qa/qa1747/_index.html)de Apple.

3.  Filtre los registros guardados para la salida de restricciones de la aplicación especificando el siguiente script en la consola:

    ```
    grep “IntuneAppRestrictions” <text file containing console output> > <required filtered log file name>
    ```
    Puede enviar los registros filtrados a Microsoft.

    > [!NOTE]
    > En el archivo de registro, el elemento "versión" representa la versión de compilación de Xcode.

    Las aplicaciones ajustadas también ofrecen a los usuarios la opción de enviar registros directamente desde el dispositivo a través de correo electrónico después de que la aplicación se bloquea. Los usuarios pueden enviarle los registros para que los examine y los reenvíe a Microsoft si es necesario.


### Requisitos de autenticación, perfil de aprovisionamiento y certificados

La herramienta de ajuste de aplicaciones tiene algunos requisitos que se deben cumplir para garantizar una funcionalidad completa.

|Requisito|Detalles|
|---------------|-----------|
|Perfil de aprovisionamiento|**Asegúrese de que el perfil de aprovisionamiento sea válido antes de incluirlo**. La herramienta de ajuste de aplicaciones no comprueba si el perfil de aprovisionamiento ha expirado al procesar una aplicación iOS. Si se especifica un perfil de aprovisionamiento expirado, la herramienta de ajuste de aplicaciones incluirá el perfil de aprovisionamiento caducado y no sabrá que hay un problema hasta que la aplicación no se pueda instalar en un dispositivo iOS.|
|Certificado|**Asegúrese de que el certificado sea válido antes de especificarlo**. La herramienta no comprueba si un certificado ha expirado al procesar aplicaciones iOS. Si se proporciona el valor hash de un certificado expirado, la herramienta procesará y firmará la aplicación, pero no se podrá instalar en dispositivos.<br /><br />**Asegúrese de que el certificado proporcionado para firmar la aplicación empaquetada tenga una coincidencia en el perfil de aprovisionamiento**. La herramienta no valida si el perfil de aprovisionamiento tiene una coincidencia con el certificado proporcionado para firmar la aplicación ajustada.|
|Autenticación|Un dispositivo debe tener un PIN para que el cifrado funcione. En dispositivos en los que haya implementado una aplicación ajustada, si se toca la barra de estado en el dispositivo será necesario que el usuario vuelva a autenticarse con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. La directiva predeterminada de una aplicación ajustada es *autenticación al volver a iniciar*. Para controlar las notificaciones externas (por ejemplo, una llamada telefónica), iOS sale de la aplicación y, después, vuelve a iniciarla.


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

-   El certificado de firma, el perfil de aprovisionamiento y la aplicación de línea de negocio que especifique deben estar en el mismo equipo Mac OS que use para ejecutar la herramienta de ajuste de aplicaciones. Si los archivos están en una ruta de acceso UNC, asegúrese de que se pueda acceder a ellos desde el equipo Mac OS. La ruta de acceso debe estar protegida mediante la firma SMB o IPsec.

    La aplicación ajustada que se importa a la consola de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] debe estar en el mismo equipo en el que se ejecuta la herramienta. Si el archivo está en una ruta de acceso UNC, asegúrese de que se pueda acceder a ella desde el equipo en el que se ejecuta la consola de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. La ruta de acceso debe estar protegida mediante la firma SMB o IPsec.

-   El entorno en donde se descarga la herramienta de ajuste de aplicaciones desde el repositorio de GitHub debe protegerse mediante la firma SMB o IPsec.

-   La aplicación que procese debe proceder de un origen de confianza para garantizar la protección frente a ataques.

-   Asegúrese de que la carpeta de salida especificada en la herramienta de ajuste de aplicaciones esté protegida, especialmente si se trata de una carpeta remota.

-   Las aplicaciones iOS que incluyen un cuadro de diálogo de carga de archivos pueden permitir a los usuarios evitar las restricciones al cortar, copiar y pegar aplicadas a la aplicación. Por ejemplo, un usuario podría usar el cuadro de diálogo de carga de archivos para cargar una captura de pantalla de los datos de aplicación.

-   Cuando los usuarios supervisan la carpeta de documentos en su dispositivo desde dentro de una aplicación ajustada, puede que vean una carpeta de nombre **.msftintuneapplauncher**. Si esta carpeta se cambia o elimina, esto podría afectar al funcionamiento correcto de las aplicaciones restringidas.

### Consulte también
- [Decidir cómo preparar las aplicaciones para la administración de aplicaciones móviles mediante Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)</br>
- [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)</br>
- [Use the SDK to enable apps for mobile application management (Usar el SDK para habilitar aplicaciones para la administración de aplicaciones móviles)](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Oct16_HO2-->


