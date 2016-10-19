---
title: Ajuste de aplicaciones Android con la herramienta de ajuste de aplicaciones | Microsoft Intune
description: "Utilice la información de este tema para obtener información sobre cómo ajustar las aplicaciones Android sin modificar el código de la propia aplicación. Prepare las aplicaciones de modo que pueda aplicar las directivas de administración de aplicaciones móviles."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: oldang
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 69d8ff8eecd238cfbbf0b01671b80e6ee77ae357
ms.openlocfilehash: c041fbbbec9e1812427d9810489d35480ae8c09b


---

# Preparar aplicaciones Android para la administración de aplicaciones móviles con la Herramienta de ajuste de aplicaciones de Intune
Use la **Herramienta de ajuste de aplicaciones de Microsoft Intune para Android** para modificar el comportamiento de las aplicaciones Android internas mediante la restricción de características de la aplicación sin modificar el código de la propia aplicación.

La herramienta es una aplicación de línea de comandos de Windows que se ejecuta en PowerShell y crea un "contenedor" alrededor de la aplicación Android. Una vez que se procesa la aplicación, puede cambiar su funcionalidad con [directivas de administración de aplicaciones móviles](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) que configure.


Antes de ejecutar la herramienta, lea [Security considerations for running the app wrapping tool](#security-considerations-for-running-the-app-wrapping-tool) (Consideraciones de seguridad para ejecutar la herramienta de ajuste de aplicaciones). Para descargar la herramienta, consulte [Microsoft Intune App Wrapping Tool for Android - Español](https://www.microsoft.com/download/details.aspx?id=47267).

>[!IMPORTANT]
>La versión de la herramienta de ajuste de aplicaciones para Android, que es compatible con dispositivos no inscritos en la administración de dispositivos móviles (MDM) de Intune, está disponible para vista previa pública. Si quiere participar en la vista previa pública, puede descargar la herramienta en [este almacén de Github](https://github.com/msintuneappsdk/intune-app-wrapper-android-preview).

>El escenario se describe en el tema [Proteger aplicaciones y datos de línea de negocio en dispositivos no inscritos en Intune](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md).


## Paso 1: cumplir los requisitos previos para usar la herramienta de ajuste de aplicaciones

-   Debe ejecutar la herramienta de ajuste de aplicaciones en un equipo de Windows con Windows 7 o posterior.

-   La aplicación de entrada debe ser un paquete de aplicación de Android válido con el archivo de extensión **.apk** y:

    -   No se puede cifrar

    -   No debe haberse ajustado aún con la herramienta de ajuste de aplicaciones de Intune
    -   Debe estar escrita para Android 4.0 o posterior

-   La aplicación debe haber sido desarrollada por o para su compañía. No se puede usar esta herramienta en aplicaciones descargadas de Google Play Store.

-   Para ejecutar la herramienta de ajuste de aplicaciones, debe instalar la versión más reciente de [Java Runtime Environment](http://java.com/download/) y, luego, asegurarse de que se ha establecido la variable de ruta de acceso de Java en **C:\ProgramData\Oracle\Java\javapath** en las variables de entorno de Windows. Para obtener más información, consulte la [documentación de Java](http://java.com/download/help/).

    > [!NOTE]
    > En algunos casos, la versión de 32 bits de Java puede producir problemas de memoria. En su lugar, se recomienda instalar la versión de 64 bits.

- Android requiere que estén firmados todos los paquetes de aplicaciones (.apks). Utilice la herramienta de claves de Java para generar las credenciales necesarias para firmar la aplicación de salida ajustada. Por ejemplo, el siguiente comando utiliza el ejecutable de Java **keytool.exe** para generar las claves que pueden utilizarse para iniciar sesión mediante la herramienta de ajuste de aplicaciones para firmar la aplicación de salida ajustada.

    ```
    keytool.exe -genkeypair -v -keystore mykeystorefile -alias mykeyalias -keyalg RSA -keysize 2048 -validity 50000
    ```
    En este ejemplo se genera un par de claves (una clave pública y una clave privada asociada de 2048 bits) mediante el algoritmo RSA y, después, se ajusta la clave pública en un certificado X.509 v3 firmado por sí mismo, que se almacena como una cadena de certificados de un solo elemento. Esta cadena de certificados y la clave privada se almacenan en una entrada nueva del almacén de claves denominada "mykeystorefile" e identificada mediante el alias "mykeyalias." La entrada del almacén de claves es válida durante 50 000 días.

    El comando le solicitará que proporcione las contraseñas para el almacén de claves y la clave. Use contraseñas seguras y difíciles de adivinar, pero recuérdelas porque las necesitará más adelante para ejecutar la herramienta de ajuste de aplicaciones.

    Para obtener documentación detallada, obtenga más información sobre la [herramienta de claves](http://docs.oracle.com/javase/6/docs/technotes/tools/windows/keytool.html) de Java y Java [KeyStore](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html) de Java en el sitio web de la documentación de Oracle.

## Paso 2: instalar la herramienta de ajuste de aplicaciones

1.  Desde el centro de descarga de Microsoft, descargue y abra el archivo de instalación de la herramienta de ajuste de aplicaciones en un equipo de Windows.

2.  Acepte el contrato de licencia y complete la instalación.

Tome nota de la carpeta donde instala la herramienta. La ubicación predeterminada es: **C:\Archivos de programa (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool**.

## Paso 3: ejecutar la herramienta de ajuste de aplicaciones

1.  En el equipo de Windows donde instaló la herramienta de ajuste de aplicaciones, abra una ventana de PowerShell en modo de administrador.

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
|**-OutputPath**&lt;String&gt;|Ruta de acceso a la aplicación de Android de "salida". Si se trata de la misma ruta de acceso al directorio que InputPath, se producirá un error en el empaquetado.| |
|**-KeyStorePath**&lt;String&gt;|Ruta de acceso al archivo de almacén de claves que contiene el par de claves pública y privada para firmar.|De forma predeterminada los archivos de almacén de claves se almacenan en "C:\Archivos de programa (x86)\Java\jreX.X.X_XX\bin." |
|**-KeyStorePassword**&lt;SecureString&gt;|Contraseña usada para descifrar el almacén de claves. Android requiere que todos los paquetes de la aplicación (.apk) estén firmados. Utilice la herramienta de claves de Java para generar el valor KeyStorePassword. Obtenga más información sobre Java [KeyStore](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html) aquí.| |
|**-KeyAlias**&lt;String&gt;|Nombre de la clave que se usará para firmar.| |
|**-KeyPassword**&lt;SecureString&gt;|Contraseña usada para descifrar la clave privada que se usará para firmar.| |
|**-SigAlg**&lt;SecureString&gt;| (Opcional) Nombre del algoritmo de firma que se usará para firmar. El algoritmo debe ser compatible con la clave privada.|Ejemplos: SHA256withRSA, SHA1withRSA, MD5withRSA|
| **&lt;CommonParameters&gt;** | (Opcional) El comando admite parámetros comunes de PowerShell como verbose, debug, etc. |


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
Ejecute la herramienta de ajuste de aplicaciones en la aplicación nativa **HelloWorld.apk**. 
```
invoke-AppWrappingTool -InputPath .\app\HelloWorld.apk -OutputPath .\app_wrapped\HelloWorld_wrapped.apk -KeyStorePath "C:\Program Files (x86)\Java\jre1.8.0_91\bin\mykeystorefile" -keyAlias mykeyalias -SigAlg SHA1withRSA -Verbose
```

A continuación, se le pedirá que especifique **KeyStorePassword** y **KeyPassword**. Escriba las credenciales que usó para crear el archivo de almacén de claves.

La aplicación ajustada se genera y guarda, junto con un archivo de registro en la ruta de acceso de salida especificada.

## Consideraciones de seguridad para ejecutar la aplicación en la herramienta de ajuste
Para evitar posibles suplantaciones de identidad, la divulgación de información y ataques de elevación de privilegios:

-   Asegúrese de que la aplicación de línea de negocio de entrada, la aplicación de salida y Java KeyStore estén en el mismo equipo de Windows donde se ejecuta la herramienta de ajuste de aplicaciones.

-   Importe la aplicación de salida a la consola de Intune en el mismo equipo donde se ejecuta la herramienta. Consulte [keytool](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html) para obtener más información acerca de keytool de Java.

-   Si la aplicación de salida y la herramienta se encuentran en una ruta de acceso de convención de nomenclatura universal (UNC), y no ejecuta la herramienta y los archivos de entrada en el mismo equipo, configure el entorno para que sea seguro mediante el [protocolo de seguridad de Internet  (IPsec)](http://en.wikipedia.org/wiki/IPsec) o [la firma del bloque de mensajes del servidor (SMB)](https://support.microsoft.com/en-us/kb/887429).

-   Asegúrese de que la aplicación procede de un origen de confianza.

-   Proteja el directorio de salida que contiene la aplicación ajustada. Considere el uso de un directorio de nivel de usuario para la salida.



### Consulte también
- [Decidir cómo preparar las aplicaciones para la administración de aplicaciones móviles mediante Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)

- [Use the SDK to enable apps for mobile application management (Usar el SDK para habilitar aplicaciones para la administración de aplicaciones móviles)](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Sep16_HO4-->


