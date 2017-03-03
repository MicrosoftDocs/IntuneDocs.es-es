---
title: Ajuste de aplicaciones Android con la herramienta de ajuste de aplicaciones | Microsoft Docs
description: "Utilice la información de este tema para aprender a ajustar las aplicaciones Android sin modificar el código de la propia aplicación. Prepare las aplicaciones de modo que pueda aplicar las directivas de administración de aplicaciones móviles."
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: oldang
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: f46f13e9dbf03fa2b3e2ec7339cad927ea0b38e0
ms.openlocfilehash: 9a9899e192db1488c9a2c0fd38ffed6cef625c34


---

# <a name="prepare-android-apps-for-mobile-application-management-with-the-intune-app-wrapping-tool"></a>Preparar aplicaciones Android para la administración de aplicaciones móviles con la Herramienta de ajuste de aplicaciones de Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Use la herramienta de ajuste de aplicaciones de Microsoft Intune para Android para modificar el comportamiento de las aplicaciones Android internas mediante la restricción de características de la aplicación sin modificar el código de la propia aplicación.

La herramienta es una aplicación de línea de comandos de Windows que se ejecuta en PowerShell y crea un "contenedor" alrededor de la aplicación Android. Una vez que se encapsula la aplicación, puede cambiar su funcionalidad configurando [directivas de administración de aplicaciones móviles](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) en Intune.


Antes de ejecutar la herramienta, lea [Consideraciones de seguridad para ejecutar la herramienta de ajuste de aplicaciones](#security-considerations-for-running-the-app-wrapping-tool). Para descargar la herramienta, vaya a [Microsoft Intune App Wrapping Tool for Android](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android) en GitHub.



## <a name="fulfill-the-prerequisites-for-using-the-app-wrapping-tool"></a>Cumplimiento de los requisitos previos para usar la herramienta de ajuste de aplicaciones

-   Debe ejecutar la herramienta de ajuste de aplicaciones en un equipo Windows con Windows 7 o posterior.

-   La aplicación de entrada debe ser un paquete de aplicaciones de Android válido con el archivo de extensión .apk y:

    -   No puede estar cifrado.
    -   No debe haberse ajustado aún con la herramienta de ajuste de aplicaciones de Intune.
    -   Debe estar escrito para Android 4.0 o posterior.

-   La aplicación debe haber sido desarrollada por o para su empresa. No se puede usar esta herramienta en aplicaciones descargadas de Google Play Store.

-   Para ejecutar la herramienta de ajuste de aplicaciones, debe instalar la versión más reciente de [Java Runtime Environment](http://java.com/download/) y, luego, asegurarse de que se ha establecido la variable de ruta de acceso de Java en C:\ProgramData\Oracle\Java\javapath en las variables de entorno de Windows. Para obtener más información, consulte la [documentación de Java](http://java.com/download/help/).

    > [!NOTE]
    > En algunos casos, la versión de 32 bits de Java puede producir problemas de memoria. Es muy conveniente instalar la versión de 64 bits.

- Android requiere que todos los paquetes de aplicaciones estén firmados (.apks). Utilice la herramienta de claves de Java para generar las credenciales necesarias para firmar la aplicación de salida ajustada. Por ejemplo, el siguiente comando utiliza el ejecutable keytool.exe de Java para generar las claves que pueden usarse para iniciar sesión en la aplicación de salida ajustada con la herramienta de ajuste de aplicaciones.

    ```
    keytool.exe -genkeypair -v -keystore mykeystorefile -alias mykeyalias -keyalg RSA -keysize 2048 -validity 50000
    ```
    En este ejemplo se genera un par de claves (una clave pública y una clave privada asociada de 2048 bits) mediante el algoritmo RSA. Luego se encapsula la clave pública en un certificado X.509 v3 autofirmado, que se almacena como una cadena de certificados de un único elemento. Esta cadena de certificados y la clave privada se almacenan en una entrada nueva del almacén de claves denominada "mykeystorefile" e identificada mediante el alias "mykeyalias." La entrada del almacén de claves es válida durante 50 000 días.

    El comando le solicitará que proporcione las contraseñas para el almacén de claves y la clave. Utilice contraseñas seguras, pero anótelas ya que las necesitará para ejecutar la herramienta de ajuste de aplicaciones.

    Para obtener documentación detallada, obtenga más información sobre la [herramienta de claves](http://docs.oracle.com/javase/6/docs/technotes/tools/windows/keytool.html) de Java y Java [KeyStore](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html) de Java en el sitio web de la documentación de Oracle.

## <a name="install-the-app-wrapping-tool"></a>Instalar la herramienta de ajuste de aplicaciones

1.  En el [repositorio de GitHub](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android), descargue el archivo de instalación InstallAWT.exe de Intune App Wrapping Tool for Android en un equipo Windows. Abra el archivo de instalación.

2.  Acepte el contrato de licencia y finalice la instalación.

Tome nota de la carpeta donde instala la herramienta. La ubicación predeterminada es C:\Archivos de programa (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool.

## <a name="run-the-app-wrapping-tool"></a>Ejecutar la herramienta de ajuste de aplicaciones

1.  En el equipo Windows donde instaló la herramienta de ajuste de aplicaciones, abra una ventana de PowerShell en modo de administrador.

2.  Desde la carpeta donde instaló la herramienta, importe el módulo de PowerShell de la aplicación de ajuste de aplicaciones:

    ```
    Import-Module .\IntuneAppWrappingTool.psm1
    ```

3.  Ejecute la herramienta mediante el comando **invoke-AppWrappingTool**, que tiene la sintaxis siguiente:
    ```
    Invoke-AppWrappingTool [-InputPath] <String> [-OutputPath] <String> -KeyStorePath <String> -KeyStorePassword <SecureString>
    -KeyAlias <String> -KeyPassword <SecureString> [-SigAlg <String>] [<CommonParameters>]
    ```

 En la siguiente tabla se detallan las propiedades del comando **invoke-AppWrappingTool**:

|Propiedad|Información de|Ejemplo|
|-------------|--------------------|---------|
|**-InputPath**&lt;String&gt;|Ruta de acceso de la aplicación de Android (.apk) de origen.| |
|**-OutputPath**&lt;String&gt;|Ruta de acceso a la aplicación de Android de salida. Si se trata de la misma ruta de acceso al directorio que InputPath, se producirá un error en el empaquetado.| |
|**-KeyStorePath**&lt;String&gt;|Ruta de acceso al archivo de almacén de claves que contiene el par de claves pública y privada para firmar.|De forma predeterminada los archivos de almacén de claves se guardan en "C:\Archivos de programa (x86)\Java\jreX.X.X_XX\bin". |
|**-KeyStorePassword**&lt;SecureString&gt;|Contraseña usada para descifrar el almacén de claves. Android requiere que todos los paquetes de aplicaciones (.apk) estén firmados. Utilice la herramienta de claves de Java para generar el valor KeyStorePassword. Más información sobre Java [Keystore](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html) aquí.| |
|**-KeyAlias**&lt;String&gt;|Nombre de la clave que se usará para firmar.| |
|**-KeyPassword**&lt;SecureString&gt;|Contraseña usada para descifrar la clave privada que se usará para firmar.| |
|**-SigAlg**&lt;SecureString&gt;| (Opcional) Nombre del algoritmo de firma que se usará para firmar. El algoritmo debe ser compatible con la clave privada.|Ejemplos: SHA256withRSA, SHA1withRSA, MD5withRSA|
| **&lt;CommonParameters&gt;** | (Opcional) El comando admite parámetros comunes de PowerShell como verbose y debug. |


- Para obtener una lista de los parámetros comunes, consulte el [Centro de scripts de Microsoft](https://technet.microsoft.com/library/hh847884.aspx).

- Para ver información detallada del uso de la herramienta, introduzca el comando:

    ```
    Help Invoke-AppWrappingTool
    ```

**Ejemplo:**

Importe el módulo de PowerShell.
```
Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1"
```
Ejecute la herramienta de ajuste de aplicaciones en la aplicación nativa HelloWorld.apk.
```
invoke-AppWrappingTool -InputPath .\app\HelloWorld.apk -OutputPath .\app_wrapped\HelloWorld_wrapped.apk -KeyStorePath "C:\Program Files (x86)\Java\jre1.8.0_91\bin\mykeystorefile" -keyAlias mykeyalias -SigAlg SHA1withRSA -Verbose
```

A continuación, se le pedirá que especifique **KeyStorePassword** y **KeyPassword**. Escriba las credenciales que usó para crear el archivo de almacén de claves.

La aplicación ajustada se genera y guarda, junto con un archivo de registro en la ruta de acceso de salida especificada.

## <a name="security-considerations-for-running-the-app-wrapping-tool"></a>Consideraciones de seguridad para ejecutar la herramienta de ajuste de aplicaciones
Para evitar posibles suplantaciones de identidad, la divulgación de información y ataques de elevación de privilegios:

-   Asegúrese de que la aplicación de línea de negocio de entrada, la aplicación de salida y Java KeyStore estén en el mismo equipo de Windows donde se ejecuta la herramienta de ajuste de aplicaciones.

-   Importe la aplicación de salida a la consola de Intune en el mismo equipo donde se ejecuta la herramienta. Consulte [keytool](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html) para más información sobre Java KeyTool.

-   Si la aplicación de salida y la herramienta se encuentran en una ruta de acceso de convención de nomenclatura universal (UNC), y no ejecuta la herramienta y los archivos de entrada en el mismo equipo, configure el entorno para que sea seguro mediante el [protocolo de seguridad de Internet (IPsec)](http://en.wikipedia.org/wiki/IPsec) o [la firma del bloque de mensajes del servidor (SMB)](https://support.microsoft.com/en-us/kb/887429).

-   Asegúrese de que la aplicación procede de un origen de confianza.

-   Proteja el directorio de salida que contiene la aplicación ajustada. Considere el uso de un directorio de nivel de usuario para la salida.

### <a name="see-also"></a>Consulte también
- [Decidir cómo preparar las aplicaciones para la administración de aplicaciones móviles mediante Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)

- [Usar el SDK para habilitar aplicaciones para la administración de aplicaciones móviles)](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Dec16_HO3-->


