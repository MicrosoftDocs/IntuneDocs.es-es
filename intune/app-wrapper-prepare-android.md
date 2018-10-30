---
title: Ajuste de aplicaciones Android con la herramienta de ajuste de aplicaciones de Intune
description: Descubra cómo ajustar las aplicaciones Android sin modificar el código de la propia aplicación. Prepare las aplicaciones de modo que pueda aplicar las directivas de administración de aplicaciones móviles.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b4b10d3dfa83e3fcfda6ba34bebc1257b19d83ac
ms.sourcegitcommit: 24d9ae0396ca410f72cc061a3c4c402835ef32a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2018
ms.locfileid: "49643001"
---
# <a name="prepare-android-apps-for-app-protection-policies-with-the-intune-app-wrapping-tool"></a>Preparar aplicaciones Android para directivas de protección de aplicaciones con la herramienta de ajuste de aplicaciones de Intune

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Use la herramienta de ajuste de aplicaciones de Microsoft Intune para Android para modificar el comportamiento de las aplicaciones Android internas mediante la restricción de características de la aplicación sin modificar el código de la propia aplicación.

La herramienta es una aplicación de línea de comandos de Windows que se ejecuta en PowerShell y crea un "contenedor" alrededor de la aplicación Android. Una vez que se encapsula la aplicación, puede cambiar su funcionalidad configurando [directivas de administración de aplicaciones móviles](/intune-classic/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console) en Intune.


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

- Android requiere que todos los paquetes de aplicaciones estén firmados (.apks). Para **volver a usar** certificados existentes e instrucciones generales de certificado de firma, vea [Reutilización de certificados de firma y aplicaciones de encapsulado](https://docs.microsoft.com/intune/app-wrapper-prepare-android#reusing-signing-certificates-and-wrapping-apps). El archivo ejecutable de Java keytool.exe se usa para generar **nuevas** credenciales necesarias para firmar la aplicación de salida ajustada. Cualquier contraseña que se establezca debe ser segura, pero anótelas ya que las necesitará para ejecutar la herramienta de ajuste de aplicaciones.

> [!NOTE]
> La Herramienta de ajuste de aplicaciones de Intune no admite los esquemas de firma de la versión 2 ni la próxima versión 3 para la firma de aplicaciones. Una vez se ha ajustado el archivo .apk con la Herramienta de ajuste de aplicaciones de Intune, se recomienda utilizar [la herramienta Apksigner que proporciona Google]( https://developer.android.com/studio/command-line/apksigner). Así se asegurará de que una vez que la aplicación llegue a los dispositivos del usuario final, se podrá iniciar correctamente por los estándares de Android. 

- (Opcional) Habilitar Multidex en la aplicación de entrada. A veces, una aplicación puede alcanzar el límite de tamaño de archivo ejecutable Dalvik (DEX) debido a las clases del SDK de MAM de Intune que se agregan durante el ajuste. Los archivos DEX forman parte de la compilación de una aplicación Android. En este escenario, lo más recomendable sería habilitar Multidex dentro de la propia aplicación. En algunas organizaciones, esto podría requerir trabajar con la persona que compile la aplicación (es decir, el equipo de compilación de aplicaciones). 

## <a name="install-the-app-wrapping-tool"></a>Instalar la herramienta de ajuste de aplicaciones

1.  En el [repositorio de GitHub](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android), descargue el archivo de instalación InstallAWT.exe de Intune App Wrapping Tool for Android en un equipo Windows. Abra el archivo de instalación.

2.  Acepte el contrato de licencia y finalice la instalación.

Tome nota de la carpeta donde instala la herramienta. La ubicación predeterminada es C:\Archivos de programa (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool.

## <a name="run-the-app-wrapping-tool"></a>Ejecutar la herramienta de ajuste de aplicaciones

1. En el equipo de Windows donde instaló la herramienta de ajuste de aplicaciones, abra una ventana de PowerShell.

2. Desde la carpeta donde instaló la herramienta, importe el módulo de PowerShell de la aplicación de ajuste de aplicaciones:

   ```
   Import-Module .\IntuneAppWrappingTool.psm1
   ```

3. Ejecute la herramienta mediante el comando **invoke-AppWrappingTool**, que tiene la sintaxis siguiente:
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
|**-SigAlg**&lt;SecureString&gt;| (Opcional) Nombre del algoritmo de firma que se usará para firmar. El algoritmo debe ser compatible con la clave privada.|Ejemplos: SHA256withRSA, SHA1withRSA|
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

-   Si la aplicación de salida y la herramienta se encuentran en una ruta de acceso de convención de nomenclatura universal (UNC), y no ejecuta la herramienta y los archivos de entrada en el mismo equipo, configure el entorno para que sea seguro mediante el [protocolo de seguridad de Internet (IPsec)](http://wikipedia.org/wiki/IPsec) o [la firma del bloque de mensajes del servidor (SMB)](https://support.microsoft.com/kb/887429).

-   Asegúrese de que la aplicación procede de un origen de confianza.

-   Proteja el directorio de salida que contiene la aplicación ajustada. Considere el uso de un directorio de nivel de usuario para la salida.

## <a name="requiring-user-login-prompt-for-an-automatic-app-we-service-enrollment-requiring-intune-app-protection-policies-in-order-to-use-your-wrapped-android-lob-app-and-enabling-adal-sso-optional"></a>Mensaje de Requerir inicio de sesión de usuario para la inscripción automática del servicio APP-WE, que requiere directivas de protección de aplicaciones de Intune para poder usar la aplicación ajustada de LOB de Android, así como para habilitar el SSO de ADAL (opcional)

La siguiente es una guía para el mensaje de Requerir usuario al iniciar la aplicación para una inscripción automática del servicio APP-WE (denominada**inscripción predeterminada** en esta sección), que requiere directivas de protección de aplicaciones de Intune para permitir que solo los usuarios protegidos de Intune usen la aplicación ajustada de LOB de Android. También se describe cómo habilitar el SSO para la aplicación ajustada de LOB de Android. 

> [!NOTE] 
> Las ventajas de la **inscripción predeterminada** incluyen un método simplificado de obtención de la directiva del servicio APP-WE para una aplicación en el dispositivo.

### <a name="general-requirements"></a>Requisitos generales
* El equipo del SDK de Intune solicitará el identificador de aplicación de su aplicación. Puede encontrar este dato mediante [Azure Portal](https://portal.azure.com/), en **Todas las aplicaciones**, en la columna de **Id. de aplicación**. Una buena manera de ponerse en contacto con el equipo de SDK de Intune es enviando un correo electrónico a msintuneappsdk@microsoft.com.
     
### <a name="working-with-the-intune-sdk"></a>Trabajar con el SDK de Intune
Estas instrucciones son específicas para todas las aplicaciones de Android y Xamarin que quieren solicitar directivas de protección de aplicaciones de Intune para su uso en un dispositivo de usuario final.

1. Configure ADAL siguiendo los pasos definidos en la [Guía para desarrolladores de Android acerca del SDK para aplicaciones de Microsoft Intune](https://docs.microsoft.com/intune/app-sdk-android#configure-azure-active-directory-authentication-library-adal).

> [!NOTE]
> El término "Id. de cliente" vinculado a la aplicación es el mismo que el término "Id. de aplicación" de Azure Portal vinculado a la aplicación. 
> * Para habilitar el SSO, necesita el punto n.º 2 de la "Configuración de ADAL común".

2. Habilite la inscripción predeterminada indicando el siguiente valor en el manifiesto:```xml <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />```
   > [!NOTE] 
   > Esta debe ser la única integración de MAM-WE en la aplicación. Podrían surgir conflictos si hay cualquier otro intento de llamada a las API de MAMEnrollmentManager.

3. Habilite la directiva de MAM necesaria indicando el siguiente valor en el manifiesto:```xml <meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />```
   > [!NOTE] 
   > Esto obliga al usuario a descargar el Portal de empresa en el dispositivo y completar el flujo de inscripción predeterminada antes de usarlo.

### <a name="see-also"></a>Vea también
- [Decidir cómo preparar las aplicaciones para la administración de aplicaciones móviles mediante Microsoft Intune](apps-prepare-mobile-application-management.md)

- [Guía para desarrolladores sobre el SDK de aplicaciones de Microsoft Intune para Android](app-sdk-android.md)
