---
title: Ajuste de aplicaciones Android con la herramienta de ajuste de aplicaciones de Intune
description: Descubra cómo ajustar las aplicaciones Android sin modificar el código de la propia aplicación. Prepare las aplicaciones de modo que pueda aplicar las directivas de administración de aplicaciones móviles.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/11/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 64de72822ad8d2f8d9893e3428208ff1363d33e2
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566053"
---
# <a name="prepare-android-apps-for-app-protection-policies-with-the-intune-app-wrapping-tool"></a>Preparar aplicaciones Android para directivas de protección de aplicaciones con la herramienta de ajuste de aplicaciones de Intune

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Use la herramienta de ajuste de aplicaciones de Microsoft Intune para Android para modificar el comportamiento de las aplicaciones Android internas mediante la restricción de características de la aplicación sin modificar el código de la propia aplicación.

La herramienta es una aplicación de línea de comandos de Windows que se ejecuta en PowerShell y crea un "contenedor" alrededor de la aplicación Android. Una vez que se encapsula la aplicación, puede cambiar su funcionalidad configurando [directivas de administración de aplicaciones móviles](app-protection-policies.md) en Intune.

Antes de ejecutar la herramienta, lea [Consideraciones de seguridad para ejecutar la herramienta de ajuste de aplicaciones](#security-considerations-for-running-the-app-wrapping-tool). Para descargar la herramienta, vaya a [Microsoft Intune App Wrapping Tool for Android](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android) en GitHub.

## <a name="fulfill-the-prerequisites-for-using-the-app-wrapping-tool"></a>Cumplimiento de los requisitos previos para usar la herramienta de ajuste de aplicaciones

-   Debe ejecutar la herramienta de ajuste de aplicaciones en un equipo Windows con Windows 7 o posterior.

-   La aplicación de entrada debe ser un paquete de aplicaciones de Android válido con el archivo de extensión .apk y:

    -   No puede estar cifrado.
    -   No debe haberse ajustado aún con la herramienta de ajuste de aplicaciones de Intune.
    -   Debe estar escrito para Android 4.0 o posterior.

-   La aplicación debe haber sido desarrollada por o para su empresa. No se puede usar esta herramienta en aplicaciones descargadas de Google Play Store.

-   Para ejecutar la herramienta de ajuste de aplicaciones, debe instalar la versión más reciente de [Java Runtime Environment](https://java.com/download/) y, luego, asegurarse de que se ha establecido la variable de ruta de acceso de Java en C:\ProgramData\Oracle\Java\javapath en las variables de entorno de Windows. Para obtener más información, consulte la [documentación de Java](https://java.com/download/help/).

    > [!NOTE]
    > En algunos casos, la versión de 32 bits de Java puede producir problemas de memoria. Es muy conveniente instalar la versión de 64 bits.

- Android requiere que todos los paquetes de aplicaciones estén firmados (.apks). Para **volver a usar** certificados existentes e instrucciones generales de certificado de firma, vea [Reutilización de certificados de firma y aplicaciones de encapsulado](https://docs.microsoft.com/intune/app-wrapper-prepare-android#reusing-signing-certificates-and-wrapping-apps). El archivo ejecutable de Java keytool.exe se usa para generar **nuevas** credenciales necesarias para firmar la aplicación de salida ajustada. Cualquier contraseña que se establezca debe ser segura, pero anótelas ya que las necesitará para ejecutar la herramienta de ajuste de aplicaciones.

    > [!NOTE]
    > La Herramienta de ajuste de aplicaciones de Intune no admite los esquemas de firma de la versión 2 ni la próxima versión 3 para la firma de aplicaciones. Una vez se ha ajustado el archivo .apk con la Herramienta de ajuste de aplicaciones de Intune, se recomienda utilizar [la herramienta Apksigner que proporciona Google]( https://developer.android.com/studio/command-line/apksigner). Así se asegurará de que una vez que la aplicación llegue a los dispositivos del usuario final, se podrá iniciar correctamente por los estándares de Android. 

- (Opcional) A veces, una aplicación puede alcanzar el límite de tamaño de archivo ejecutable Dalvik (DEX) debido a las clases del SDK de MAM de Intune que se agregan durante el ajuste. Los archivos DEX forman parte de la compilación de una aplicación Android. Intune App Wrapping Tool controla automáticamente el desbordamiento del archivo DEX durante el ajuste de aplicaciones con un mínimo de API de nivel de 21 o superior (como de [v. 1.0.2501.1](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android/releases)). Para las aplicaciones con un mínimo nivel de API de < 21, lo más recomendable sería aumentar el número mínimo de nivel de API mediante el contenedor `-UseMinAPILevelForNativeMultiDex` marca. Para los clientes que no se puede aumentar el nivel de API mínimo de la aplicación, están disponibles las siguientes soluciones alternativas de desbordamiento DEX. En algunas organizaciones, esto podría requerir trabajar con la persona que compile la aplicación (es decir, el equipo de compilación de aplicaciones):
* Usar ProGuard para eliminar las referencias de clase sin usar del archivo DEX principal de la aplicación.
* Para los clientes que usan v3.1.0 o posterior del complemento de Gradle Android, deshabilite la [dexer D8](https://android-developers.googleblog.com/2018/04/android-studio-switching-to-d8-dexer.html).  

## <a name="install-the-app-wrapping-tool"></a>Instalar la herramienta de ajuste de aplicaciones

1.  En el [repositorio de GitHub](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android), descargue el archivo de instalación InstallAWT.exe de Intune App Wrapping Tool for Android en un equipo Windows. Abra el archivo de instalación.

2.  Acepte el contrato de licencia y finalice la instalación.

Tome nota de la carpeta donde instala la herramienta. La ubicación predeterminada es C:\Archivos de programa (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool.

## <a name="run-the-app-wrapping-tool"></a>Ejecutar la herramienta de ajuste de aplicaciones

1. En el equipo de Windows donde instaló la herramienta de ajuste de aplicaciones, abra una ventana de PowerShell.

2. Desde la carpeta donde instaló la herramienta, importe el módulo de PowerShell de la aplicación de ajuste de aplicaciones:

   ```PowerShell
   Import-Module .\IntuneAppWrappingTool.psm1
   ```

3. Ejecute la herramienta mediante el comando **invoke-AppWrappingTool**, que tiene la sintaxis siguiente:
   ```PowerShell
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
|**-SigAlg**&lt;SecureString&gt;| (Opcional) Nombre del algoritmo de firma que se usará para firmar. El algoritmo debe ser compatible con la clave privada.|Ejemplos: SHA256withRSA, SHA1withRSA|
|**-UseMinAPILevelForNativeMultiDex**| (Opcional) Use esta marca para aumentar el nivel de API mínimo de la aplicación Android de origen en 21. Este indicador solicitará confirmación limitará quién puede instalar esta aplicación. Los usuarios pueden omitir el cuadro de diálogo de confirmación anexando el parámetro "-confirmar: $false" a su comando de PowerShell. La marca solo debe usarse por los clientes en las aplicaciones con 21 < min API que no se pueden ajustar correctamente debido a errores de desbordamiento DEX. | |
| **&lt;CommonParameters&gt;** | (Opcional) El comando admite parámetros comunes de PowerShell como verbose y debug. |


- Para obtener una lista de los parámetros comunes, consulte el [Centro de scripts de Microsoft](https://technet.microsoft.com/library/hh847884.aspx).

- Para ver información detallada del uso de la herramienta, introduzca el comando:

    ```PowerShell
    Help Invoke-AppWrappingTool
    ```

**Ejemplo:**

Importe el módulo de PowerShell.
```PowerShell
Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1"
```
Ejecute la herramienta de ajuste de aplicaciones en la aplicación nativa HelloWorld.apk.
```PowerShell
invoke-AppWrappingTool -InputPath .\app\HelloWorld.apk -OutputPath .\app_wrapped\HelloWorld_wrapped.apk -KeyStorePath "C:\Program Files (x86)\Java\jre1.8.0_91\bin\mykeystorefile" -keyAlias mykeyalias -SigAlg SHA1withRSA -Verbose
```

A continuación, se le pedirá que especifique **KeyStorePassword** y **KeyPassword**. Escriba las credenciales que usó para crear el archivo de almacén de claves.

La aplicación ajustada se genera y guarda, junto con un archivo de registro en la ruta de acceso de salida especificada.

## <a name="how-often-should-i-rewrap-my-android-application-with-the-intune-app-wrapping-tool"></a>¿Con qué frecuencia conviene reajustar mi aplicación de Android con la herramienta de ajuste de aplicaciones de Intune?
Los casos principales en los que resulta necesario reajustar las aplicaciones son los siguientes:
* La aplicación tiene una nueva versión. La versión anterior de la aplicación se ha ajustado y cargado en la consola de Intune.
* La herramienta de ajuste de aplicaciones de Intune para Android tiene una nueva versión que permite corregir errores importantes o bien presenta características nuevas y específicas relativas a la directiva de protección de la aplicación de Intune. Esto suele darse cada seis u ocho semanas a través del repositorio de GitHub para la [herramienta de ajuste de aplicaciones de Microsoft Intune para Android](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android).

Entre los procedimientos recomendados para el reajuste destacan los siguientes: 
* Mantenimiento de los certificados de firma utilizados durante el proceso de compilación ([Reutilización de certificados de firma y aplicaciones de encapsulado](https://docs.microsoft.com/intune/app-wrapper-prepare-android#reusing-signing-certificates-and-wrapping-apps))

## <a name="reusing-signing-certificates-and-wrapping-apps"></a>Reutilización de certificados de firma y aplicaciones de encapsulado
Android requiere que todas las aplicaciones estén firmadas mediante un certificado válido para instalarlo en dispositivos Android.

Las aplicaciones encapsuladas se pueden firmar ya sea como parte del proceso de encapsulado o *después* del encapsulado con las herramientas de firma existentes (se descarta cualquier información de firma en la aplicación antes del encapsulado). Si es posible, ya información de firma que ya se usó durante el proceso de compilación se debe usar durante el encapsulado. En ciertas organizaciones, esto podría requerir trabajar con la persona propietaria de la información del almacén de claves (es decir, el equipo de compilación de aplicaciones). 

Si no se puede usar el certificado de firma anterior o si la aplicación no se implementó antes, puede crear un certificado de firma nuevo con las instrucciones que aparecen en la [Guía para desarrolladores de Android](https://developer.android.com/studio/publish/app-signing.html#signing-manually).

Si la aplicación se implementó anteriormente con otro certificado de firma, la aplicación no se puede cargar en Intune después de la actualización. Los escenarios de actualización de la aplicación se interrumpirá si la aplicación se firma con un certificado distinto del certificado con que se compila la aplicación. Por tanto, se deben conservar todos los certificados de firma nuevos para las actualizaciones de la aplicación. 

## <a name="security-considerations-for-running-the-app-wrapping-tool"></a>Consideraciones de seguridad para ejecutar la herramienta de ajuste de aplicaciones
Para evitar posibles suplantaciones de identidad, la divulgación de información y ataques de elevación de privilegios:

-   Asegúrese de que la aplicación de línea de negocio de entrada, la aplicación de salida y Java KeyStore estén en el mismo equipo de Windows donde se ejecuta la herramienta de ajuste de aplicaciones.

-   Importe la aplicación de salida a Intune en el mismo equipo donde se ejecuta la herramienta. Vea [KeyTool](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html) para más información sobre Java KeyTool.

-   Si la aplicación de salida y la herramienta se encuentran en una ruta de acceso de convención de nomenclatura universal (UNC), y no ejecuta la herramienta y los archivos de entrada en el mismo equipo, configure el entorno para que sea seguro mediante el [protocolo de seguridad de Internet (IPsec)](https://wikipedia.org/wiki/IPsec) o [la firma del bloque de mensajes del servidor (SMB)](https://support.microsoft.com/kb/887429).

-   Asegúrese de que la aplicación procede de un origen de confianza.

-   Proteja el directorio de salida que contiene la aplicación ajustada. Considere el uso de un directorio de nivel de usuario para la salida.

### <a name="see-also"></a>Consulte también
- [Decidir cómo preparar las aplicaciones para la administración de aplicaciones móviles mediante Microsoft Intune](apps-prepare-mobile-application-management.md)

- [Guía para desarrolladores sobre el SDK de aplicaciones de Microsoft Intune para Android](app-sdk-android.md)
