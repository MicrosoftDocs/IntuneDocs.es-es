---
title: Ajuste de aplicaciones Android con la herramienta de ajuste de aplicaciones | Microsoft Intune
description: "Utilice la información de este tema para obtener información sobre cómo ajustar las aplicaciones Android sin modificar el código de la propia aplicación. Prepare las aplicaciones de modo que pueda aplicar las directivas de administración de aplicaciones móviles."
keywords: 
author: karthikaraman
manager: arob98
ms.date: 07/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: matgates
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2038ed6219a94dc4285891d71ce00fd51310f3e3
ms.openlocfilehash: 15d0877f799c89e2a8af65c416c0e914f898641f


---

# Preparar aplicaciones Android para la administración de aplicaciones móviles con la Herramienta de ajuste de aplicaciones de Intune
Use la **Herramienta de ajuste de aplicaciones de Microsoft Intune para Android** para modificar el comportamiento de las aplicaciones Android internas para poder configurar características de la aplicación sin modificar el código de la propia aplicación.

La herramienta es una aplicación de línea de comandos de Windows que se ejecuta en PowerShell y crea un "contenedor" alrededor de la aplicación. Una vez que se procesa la aplicación, puede cambiar su funcionalidad con [directivas de administración de aplicaciones móviles](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) que configure.

Si la aplicación usa la Biblioteca de autenticación de Azure Active Directory (ADAL), debe completar los pasos de [Cómo ajustar aplicaciones que usan la Biblioteca de Azure Active Directory](#how-to-wrap-apps-that-use-the-azure-active-directory-library) antes de ajustar la aplicación. Si no está seguro de si su aplicación usa esta biblioteca, póngase en contacto con el desarrollador de la aplicación.

Antes de ejecutar la herramienta, lea [Security considerations for running the app wrapping tool](#security-considerations-for-running-the-app-wrapping-tool) (Consideraciones de seguridad para ejecutar la herramienta de ajuste de aplicaciones). Para descargar la herramienta, consulte [Microsoft Intune App Wrapping Tool for Android - Español](https://www.microsoft.com/download/details.aspx?id=47267).

## Paso 1: cumplir los requisitos previos para usar la herramienta de ajuste de aplicaciones

-   Debe ejecutar la herramienta de ajuste de aplicaciones en un equipo de Windows con Windows 7 o posterior.

-   La aplicación de entrada debe ser un paquete de aplicación de Android válido con la extensión **.apk** y:

    -   No se puede cifrar

    -   No debe haberse ajustado aún con la herramienta de ajuste de aplicaciones

    -   Debe estar escrita para Android 4.0 o posterior

-   La aplicación debe haber sido desarrollada por o para su compañía. No se puede usar esta herramienta para procesar aplicaciones descargadas de Google Play Store.

-   Para ejecutar la herramienta de ajuste de aplicaciones, debe instalar la versión más reciente de [Java Runtime Environment](http://java.com/download/) y, luego, asegurarse de que se ha establecido la variable de ruta de acceso de Java en **C:\ProgramData\Oracle\Java\javapath** en las variables de entorno de Windows. Para obtener más información, consulte la [documentación de Java](http://java.com/download/help/).

    > [!NOTE]
    > En algunos casos, la versión de 32 bits de Java puede producir problemas de memoria. En su lugar, se recomienda instalar la versión de 64 bits.

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

3.  Ejecute la herramienta mediante el comando **invoke-AppWrappingTool** con los siguientes parámetros. Los parámetros que están marcados como "opcionales" son para las aplicaciones que usan la Biblioteca de Azure Active Directory (ADAL). Para obtener más información, consulte [Cómo ajustar aplicaciones que usan la Biblioteca de Azure Active Directory](#how-to-wrap-apps-that-use-the-azure-active-directory-library).

|Parámetro|Más información|Ejemplos|
|-------------|--------------------|---------|
|**-InputPath**&lt;String&gt;|Ruta de acceso de la aplicación de Android (.apk) de origen.| |
|**-OutputPath**&lt;String&gt;|Ruta de acceso a la aplicación de Android de "salida". Si se trata de la misma ruta de acceso al directorio que InputPath, se producirá un error en el empaquetado.| |
|**-KeyStorePath**&lt;String&gt;|Ruta de acceso al archivo de almacén de claves que contiene el par de claves pública y privada para firmar.| |
|**-KeyStorePassword**&lt;SecureString&gt;|Contraseña usada para descifrar el almacén de claves. Android requiere que todos los paquetes de la aplicación (.apk) estén firmados. Utilice la herramienta de claves de Java para generar el valor KeyStorePassword tal como se muestra en el ejemplo. Obtenga más información sobre [keystore](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html).|keytool.exe -genkey -v -keystore keystorefile -alias ks -keyalg RSA -keysize 2048 -validity 50000 |
|**-KeyAlias**&lt;String&gt;|Nombre de la clave que se usará para firmar.| |
|**-KeyPassword**&lt;SecureString&gt;|Contraseña usada para descifrar la clave privada que se usará para firmar.| |
|**-SigAlg**&lt;SecureString&gt;|Nombre del algoritmo de firma que se usará para firmar. El algoritmo debe ser compatible con la clave privada.|Ejemplos: SHA256withRSA, SHA1withRSA, MD5withRSA|
|**-ClientID**&lt;GUID&gt;|Identificador de cliente de Azure Active Directory de la aplicación de entrada (opcional).| |
|**-AuthorityURI**&lt;Uri&gt;|URI de autoridad de Azure Active Directory de la aplicación de entrada (opcional).| |
|**-SkipBroker**&lt;Boolean&gt;|Indica si la aplicación de entrada admite el inicio de sesión único asíncrono en todo el dispositivo (opcional). |**True**: la aplicación de entrada no admite el inicio de sesión único asíncrono en todo el dispositivo. Use el parámetro NonBrokerRedirectURI. **False**: la aplicación de entrada admite el inicio de sesión único asíncrono en todo el dispositivo.|
|**-NonBrokerRedirectURI**&lt;URI&gt;|URI de redireccionamiento de Azure Active Directory que se debe usar si SkipBroker es true (opcional).|  |


**&lt;CommonParameters&gt;**
: (opcional, admite parámetros comunes de PowerShell como verbose, debug, etc.)

- Para obtener una lista de los parámetros comunes, consulte el [Centro de scripts de Microsoft](https://technet.microsoft.com/library/hh847884.aspx).

- Para ver la ayuda de la herramienta, escriba el comando:

    ```
    Help Invoke-AppWrappingTool
    ```
- Para obtener más información sobre la integración de Azure Active Directory (AAD), consulte [Cómo ajustar aplicaciones que usan la Biblioteca de Azure Active Directory](#how-to-wrap-apps-that-use-the-azure-active-directory-library).

**Ejemplo:**


    Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1"
    invoke-AppWrappingTool -InputPath .\app\HelloWorld.apk -OutputPath .\app.wrapped\HelloWorld_wrapped2.apk -KeyStorePath "C:\Program Files (x86)\Java\jre1.8.0_91\bin\keystorefile" -keyAlias ks -SigAlg SHA1withRSA -Verbose

A continuación, se le pedirá que especifique **KeyStorePassword** y **KeyPassword**.

La aplicación ajustada se genera y guarda, junto con un archivo de registro en la ruta de acceso de salida especificada.

## Consideraciones de seguridad para ejecutar la aplicación en la herramienta de ajuste
Para evitar posibles suplantaciones de identidad, la divulgación de información y ataques de elevación de privilegios:

-   Asegúrese de que la aplicación de línea de negocio de entrada, la aplicación de salida y Java KeyStore estén en el mismo equipo donde se ejecuta la herramienta de ajuste de aplicaciones.

-   Importe la aplicación de salida a la consola de Intune en el mismo equipo donde se ejecuta la herramienta. Consulte [keytool](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html) para obtener más información acerca de keytool de Java.

-   Si la aplicación de salida y la herramienta se encuentran en una ruta de acceso de convención de nomenclatura universal (UNC), y no ejecuta la herramienta y los archivos de entrada en el mismo equipo, configure el entorno para que sea seguro mediante el [protocolo de seguridad de Internet  (IPsec)](http://en.wikipedia.org/wiki/IPsec) o [la firma del bloque de mensajes del servidor (SMB)](https://support.microsoft.com/en-us/kb/887429).

-   Asegúrese de que la aplicación procede de un origen de confianza, especialmente si utiliza Azure Active Directory (AAD), que podría permitir a la aplicación acceder al token de AAD durante el tiempo de ejecución.

-   Proteja el directorio de salida que contiene la aplicación ajustada. Considere el uso de un directorio de nivel de usuario para la salida.

## Cómo ajustar aplicaciones que usan la Biblioteca de Azure Active Directory
Si la aplicación usa la Biblioteca de autenticación de Azure Active Directory (ADAL), debe completar estos pasos antes de ajustar la aplicación.

### Paso 1: asegúrese de cumplir los requisitos de ADAL
Para las aplicaciones que usen ADAL, deben cumplirse las siguientes condiciones:

-   La aplicación debe incorporar una versión de ADAL igual o posterior a la versión 1.0.2.

-   Los desarrolladores deben conceder acceso a su aplicación al recurso Administración de aplicaciones móviles de Intune, como se describe en [Paso 3: configure el acceso a la administración de aplicaciones móviles en AAD](#step-3-configure-access-to-mobile-app-management-in-aad).

### Paso 2: revise los identificadores que necesita obtener al registrar la aplicación
En el paso siguiente, va a usar el Portal de administración de Azure para registrar las aplicaciones (que usan ADAL con Azure Active Directory (AAD)) para obtener los identificadores únicos que se muestran en la siguiente tabla. A continuación, entregue los identificadores al desarrollador cuando vaya a integrar ADAL con la aplicación.

|Identificador|Más información|Valor predeterminado|
|--------------|--------------------|-----------------|
|**Identificador de cliente**|Identificador GUID único que se genera para la aplicación después de registrarla con AAD.<br /><br />Si conoce el identificador de cliente de la aplicación, especifique ese valor. De lo contrario, use el valor predeterminado.|6c7e8096-f593-4d72-807f-a5f86dcc9c77|
|**URI de autoridad**|El valor del identificador uniforme de recursos (URI) de autoridad para los objetos de AAD (por ejemplo, los usuarios y grupos).<br /><br />El parámetro AuthorityURI es opcional para la herramienta de ajuste de aplicaciones. Si no usa el parámetro, se usa el URI predeterminado.||
|**SkipBroker**|Valor que indica si el portal de empresa se usará como agente.<br /><br />**True**: el portal de empresa no se usará para la autenticación de ADAL.<br /><br />**False**: el portal de empresa se usará para la autenticación de ADAL. El portal de empresa usa el usuario inscrito para fines de inicio de sesión único.||
|**URI de redireccionamiento que no es del agente**|URI de inicio de sesión que se usará cuando ADAL no use la aplicación del agente (portal de empresa de Intune)|urn:ietf:wg:oauth:2.0:oob|
|**Identificador de recurso**|Puntero a los recursos de AAD de la aplicación.||

### Paso 3: configure el acceso a la administración de aplicaciones móviles en AAD
Para poder usar los valores de registro de AAD de una aplicación en la herramienta de ajuste de aplicaciones, el desarrollador de aplicaciones debe conceder acceso a esa aplicación al recurso Administración de aplicaciones móviles de Intune mediante estos pasos:

1.  Inicie sesión en una cuenta de AAD existente en el Portal de administración de Azure.

2.  Seleccione un **registro existente de la aplicación LOB**.

3.  En la sección **Configurar** , elija **Configurar acceso a API web en otras aplicaciones**.

4.  En la primera lista desplegable de la sección **Permission to other applications** (Permiso en otras aplicaciones), seleccione **Administración de aplicaciones móviles de Intune**.

Ahora puede usar el identificador de cliente de la aplicación en la herramienta de ajuste de aplicaciones. Puede encontrar el identificador de cliente en el Portal de administración de Azure Active Directory, como se describe en la tabla de [Paso 2: revise los identificadores que necesita obtener al registrar la aplicación](#step-2-review-the-identifiers-you-need-to-get-when-you-register-the-app).

### Paso 4: use los valores del identificador de AAD en la herramienta de ajuste de aplicaciones
A partir de los valores del identificador que obtuvo en el proceso de registro, escriba los valores como propiedades de línea de comandos en la herramienta de ajuste de aplicaciones. Debe especificar todos los valores de la tabla en orden para que los usuarios finales puedan autenticar correctamente la aplicación. Si no especifica algún valor, se usarán los predeterminados.

|Identificador|Parámetro|
|--------------|-------------|
|Identificador de cliente|ClientID|
|URI de autoridad|Authority-URI|
|SkipBroker|SkipBroker|
|URI de redireccionamiento que no es del agente|NonBrokerRedirectURI|
|Identificador de recurso|ResourceID|
Tenga presentes los siguientes puntos al ajustar la aplicación:

-   Para comprobar que la autenticación se realizó correctamente, [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] captura el token de AAD que está asociado con el identificador de recurso MAM. Sin embargo, el token no se usa en ninguna llamada que a su vez pueda comprobar la validez del token. [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] solo lee el nombre principal de usuario (UPN) del usuario con sesión iniciada para determinar el acceso a la aplicación. El token de AAD no se usa para las demás llamadas de servicio.

-   Las peticiones de inicio de sesión dobles pueden evitarse si proporciona el identificador de cliente y el URI de entidad de la aplicación cliente. Deberá registrar el identificador de cliente para habilitar su acceso al identificador del recurso MAM de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] publicado en panel de AAD. Si no registra el identificador de cliente, los usuarios obtendrán un error de inicio de sesión cuando se ejecute la aplicación.


### Consulte también
- [Decidir cómo preparar las aplicaciones para la administración de aplicaciones móviles mediante Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)

- [Use the SDK to enable apps for mobile application management (Usar el SDK para habilitar aplicaciones para la administración de aplicaciones móviles)](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Jul16_HO4-->


