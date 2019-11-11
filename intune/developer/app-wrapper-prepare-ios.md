---
title: Ajuste de aplicaciones iOS con la herramienta de ajuste de aplicaciones de Intune
description: Obtenga información sobre cómo ajustar las aplicaciones iOS sin modificar el código de la propia aplicación. Prepare las aplicaciones de modo que pueda aplicar las directivas de administración de aplicaciones móviles.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/06/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 99ab0369-5115-4dc8-83ea-db7239b0de97
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: c0fac5e9d34890272253eaefd82ed13dc1014ba0
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "73713477"
---
# <a name="prepare-ios-apps-for-app-protection-policies-with-the-intune-app-wrapping-tool"></a>Preparar aplicaciones iOS para directivas de protección de aplicaciones con la herramienta de ajuste de aplicaciones de Intune

Use la herramienta de ajuste de aplicaciones de Microsoft Intune para iOS para habilitar las directivas de protección de aplicaciones de Intune para aplicaciones iOS internas sin cambiar el código de la propia aplicación.

La herramienta es una aplicación de línea de comandos de macOS que crea un contenedor alrededor de una aplicación. Una vez que se haya procesado la aplicación, puede cambiar su función implementando [directivas de protección de aplicaciones](../apps/app-protection-policies.md) en esta.

Para descargar la herramienta, consulte [Microsoft Intune App Wrapping Tool for iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) (Herramienta de ajuste de aplicaciones de Microsoft Intune para iOS) en GitHub.

## <a name="general-prerequisites-for-the-app-wrapping-tool"></a>Requisitos previos generales de la herramienta de ajuste de aplicaciones

Antes de ejecutar la herramienta de ajuste de aplicaciones, necesita cumplir algunos requisitos previos generales:

* Descargue la [Herramienta de ajuste de aplicaciones de Microsoft Intune para iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) de GitHub.

* Un equipo macOS que ejecute OS X 10.8.5 o posterior y que tenga instalada la versión 9 o posterior del conjunto de herramientas Xcode.

* La aplicación iOS de entrada debe estar desarrollada y firmada por la empresa o por un proveedor de software independiente (ISV).

  * El archivo de aplicación de entrada debe tener la extensión **.ipa** o **.app**.

  * La aplicación de entrada debe compilarse para iOS 11 o posterior.

  * La aplicación de entrada no puede cifrarse.

  * La aplicación de entrada no puede tener atributos de archivo extendidos.

  * La aplicación de entrada debe tener derechos establecidos antes de que la herramienta de ajuste de aplicaciones de Intune los procese. Los [derechos](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/EntitlementKeyReference/Chapters/AboutEntitlements.html) conceden permisos y características adicionales a la aplicación que van más allá de aquellas que se conceden en general. Consulte [Configurar los derechos de la aplicación](#setting-app-entitlements) para obtener instrucciones.

## <a name="apple-developer-prerequisites-for-the-app-wrapping-tool"></a>Requisitos previos de Apple Developer para la herramienta de ajuste de aplicaciones

Para distribuir las aplicaciones ajustadas exclusivamente para los usuarios de la organización, necesita una cuenta con el [Programa Enterprise de Apple Developer](https://developer.apple.com/programs/enterprise/) y varias entidades para la firma de la aplicación que estén vinculadas a su cuenta de Apple Developer.

Para más información sobre la distribución de aplicaciones iOS de manera interna para los usuarios de su organización, lea la guía oficial para [Distributing Apple Developer Enterprise Program Apps (Distribuir aplicaciones del programa Enterprise de Apple Developer)](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/DistributingEnterpriseProgramApps/DistributingEnterpriseProgramApps.html#//apple_ref/doc/uid/TP40012582-CH33-SW1).

Necesitará lo siguiente para distribuir aplicaciones ajustadas con Intune:

* Una cuenta de desarrollador con el programa Enterprise de Apple Developer.

* Un certificado de firma de distribución ad hoc e interno con un identificador de equipo válido.

  * Necesitará el hash SHA1 del certificado de firma como un parámetro para la herramienta de ajuste de aplicaciones de Intune.


* Un perfil de aprovisionamiento de distribución interno.

### <a name="steps-to-create-an-apple-developer-enterprise-account"></a>Pasos para crear una cuenta Enterprise de Apple Developer

1. Vaya al [sitio del programa Enterprise de Apple Developer](https://developer.apple.com/programs/enterprise/).

2. En la parte superior derecha de la página, haga clic en **Inscribir**.

3. Lea la lista de comprobación de lo que necesita inscribir. Haga clic en **Start Your Enrollment (Iniciar la inscripción)** en la parte inferior de la página.

4. **Inicie sesión** con el id. de Apple de la organización. Si no tiene uno, haga clic en **Create Apple ID (Crear id. de Apple)** .

5. Seleccione su **Tipo de entidad** y haga clic en **Continuar**.

6. Rellene el formulario con la información de su organización. Haga clic en **Continue**. En este punto, Apple se pondrá en contacto con usted para comprobar que está autorizado para inscribir su organización.

7. Después de la comprobación, haga clic en **Agree to License (Acepto la licencia)** .

8. Después de aceptar la licencia, termine **comprando y activando el programa**.

9. Si es el agente de equipo (la persona que se une al programa Enterprise de Apple Developer en nombre de su organización), cree su equipo primero invitando a los miembros del equipo y asignando roles. Para obtener información sobre cómo administrar su equipo, lea la documentación de Apple en [Managing Your Developer Account Team (Administrar el equipo de cuentas de desarrollador)](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingYourTeam/ManagingYourTeam.html#//apple_ref/doc/uid/TP40012582-CH16-SW1).

### <a name="steps-to-create-an-apple-signing-certificate"></a>Pasos para crear un certificado de firma de Apple

1. Vaya al [Portal de Apple Developer](https://developer.apple.com/).

2. En la parte superior derecha de la página, haga clic en **Cuenta**.

3. **Inicie sesión** con su id. de Apple de la organización.

4. Haga clic en **Certificates, IDs & Profiles (Certificados, identificadores y perfiles)** .

   ![Portal para desarrolladores de Apple: certificados, identificadores y perfiles](./media/app-wrapper-prepare-ios/iOS-signing-cert-1.png)

5. Haga clic en la pestaña ![Signo más del Portal de Apple Developer](./media/app-wrapper-prepare-ios/iOS-signing-cert-2.png) en la esquina superior derecha para agregar un certificado iOS.

6. Pulse para crear un certificado **interno y ad hoc** en **Producción**.

   ![Seleccionar certificado interno y ad hoc](./media/app-wrapper-prepare-ios/iOS-signing-cert-3.png)

   >[!NOTE]
   >Si no planea distribuir la aplicación y solo quiere probarla internamente, puede usar un certificado de desarrollo de aplicaciones de iOS en lugar de un certificado para producción. Si usa un certificado de desarrollo, asegúrese de que el perfil móvil de aprovisionamiento haga referencia a los dispositivos en los que se instalará la aplicación.

7. Haga clic en **Siguiente** en la parte inferior de la página.

8. Lea las instrucciones sobre la creación de una **solicitud de firma de certificado (CSR)** con la aplicación Acceso a llaves en su equipo macOS.

   ![Leer instrucciones para crear una CSR](./media/app-wrapper-prepare-ios/iOS-signing-cert-4.png)

9. Siga las instrucciones anteriores para crear una solicitud de firma de certificado. En su equipo macOS, inicie la aplicación **Acceso a llaves**.

10. En el menú de macOS en la parte superior de la pantalla, vaya a **Acceso a llaves > Asistente de certificado > Request a Certificate From a Certificate Authority (Solicitar un certificado de una entidad de certificación)** .  

    ![Solicitar un certificado de una entidad de certificación en Acceso a llaves](./media/app-wrapper-prepare-ios/iOS-signing-cert-5.png)

11. Siga las instrucciones del sitio de Apple Developer anterior sobre cómo crear un archivo CSR. Guarde el archivo CSR en su equipo macOS.

    ![Escritura de la información para el certificado que se solicita](./media/app-wrapper-prepare-ios/iOS-signing-cert-6.png)

12. Vuelva al sitio de Apple Developer. Haga clic en **Continue**. Después, cargue el archivo CSR.

13. Apple genera su certificado de firma. Descargue y guárdelo en una ubicación fácil de recordar en su equipo macOS.

    ![Descargar su certificado de firma](./media/app-wrapper-prepare-ios/iOS-signing-cert-7.png)

14. Haga doble clic en el archivo de certificado que acaba de descargar para agregar el certificado a una cadena de claves.

15. Abra **Acceso a llaves** de nuevo. Busque su certificado al escribir su nombre en la barra de búsqueda de la parte superior derecha. Haga doble clic en el elemento para que aparezca el menú y haga clic en **Obtener información**. En las pantallas de ejemplo se está usando un certificado de desarrollo en lugar de un certificado de producción.

    ![Agregar su certificado a una cadena de claves](./media/app-wrapper-prepare-ios/iOS-signing-cert-8.png)

16. Aparece una ventana informativa. Desplácese a la parte inferior y busque en la etiqueta **Huellas digitales**. Copie la cadena **SHA1** (borrosa) para usarla como argumento para "-c" para la herramienta de ajuste de aplicaciones.

    ![Información de iPhone: cadena SHA1 de huellas digitales](./media/app-wrapper-prepare-ios/iOS-signing-cert-9.png)

### <a name="steps-to-create-an-in-house-distribution-provisioning-profile"></a>Pasos para crear un perfil de aprovisionamiento de distribución interno

1. Vuelva al [Portal de la cuenta de Apple Developer](https://developer.apple.com/account/) e **inicie sesión** con su id. de Apple de la organización.

2. Haga clic en **Certificates, IDs & Profiles (Certificados, identificadores y perfiles)** .

3. Haga clic en la pestaña ![Signo más del Portal de Apple Developer](./media/app-wrapper-prepare-ios/iOS-signing-cert-2.png) en la esquina superior derecha para agregar un perfil de aprovisionamiento de iOS.

4. Pulse para crear un perfil de aprovisionamiento **interno** en **Distribución**.

   ![Seleccionar el perfil de aprovisionamiento interno](./media/app-wrapper-prepare-ios/iOS-provisioning-profile-1.png)

5. Haga clic en **Continue**. Asegúrese de vincular el certificado de firma que se generó anteriormente al perfil de aprovisionamiento.

6. Siga los pasos para descargar el perfil (con la extensión .mobileprovision) en su equipo macOS.

7. Guarde el archivo en una ubicación fácil de recordar. Este archivo se usará para el parámetro -p al usar la herramienta de ajuste de aplicaciones.

## <a name="download-the-app-wrapping-tool"></a>Descargar la herramienta de ajuste de aplicaciones

1. Descargue los archivos de la herramienta de ajuste de aplicaciones de [GitHub](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) en un equipo macOS.

2. Haga doble clic en **Microsoft Intune App Wrapping Tool for iOS.dmg**. Aparecerá una ventana con los términos de licencia. Lea detenidamente el documento.

3. Elija **Acepto** para aceptar los términos de licencia, con lo que se monta el paquete en el equipo.

## <a name="run-the-app-wrapping-tool"></a>Ejecutar la herramienta de ajuste de aplicaciones

### <a name="use-terminal"></a>Usar Terminal

Abra el Terminal de macOS y ejecute el siguiente comando:

```bash
/Volumes/IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> -p /<path to provisioning profile> -c <SHA1 hash of the certificate> [-b [<output app build string>]] [-v] [-e] [-x /<array of extension provisioning profile paths>]
```

> [!NOTE]
> Algunos parámetros son opcionales, tal como se muestra en la siguiente tabla.

**Ejemplo:** el comando del ejemplo siguiente ejecuta la herramienta de ajuste de aplicaciones en una aplicación denominada MyApp.ipa. Para firmar la aplicación ajustada se usa un perfil de aprovisionamiento y un hash SHA-1 del certificado de firma. La aplicación de salida (MyApp_Wrapped.ipa) se crea y se almacena en la carpeta Escritorio.

```bash
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i ~/Desktop/MyApp.ipa -o ~/Desktop/MyApp_Wrapped.ipa -p ~/Desktop/My_Provisioning_Profile_.mobileprovision -c "12 A3 BC 45 D6 7E F8 90 1A 2B 3C DE F4 AB C5 D6 E7 89 0F AB"  -v true
```

### <a name="command-line-parameters"></a>Parámetros de línea de comandos

Puede usar los siguientes parámetros de línea de comandos con la herramienta de ajuste de aplicaciones:

|Propiedad|Cómo usarla|
|---------------|--------------------------------|
|**-i**|`<Path of the input native iOS application file>`. El nombre de archivo debe terminar en .app o .ipa. |
|**-o**|`<Path of the wrapped output application>` |
|**-p**|`<Path of your provisioning profile for iOS apps>`|
|**-c**|`<SHA1 hash of the signing certificate>`|
|**-h**| Muestra información de uso detallada sobre las propiedades de línea de comandos disponibles para la herramienta de ajuste de aplicaciones. |
|**-aa**|(Opcional) `<Authority URI of the input app if the app uses the Azure Active Directory Authentication Library>` es decir `login.windows.net/common` |
|**-ac**|(Opcional) `<Client ID of the input app if the app uses the Azure Active Directory Authentication Library>` es el GUID del campo ID. de cliente procede de la lista de la aplicación en la hoja registro de aplicaciones. |
|**-ar**|(Opcional) `<Redirect/Reply URI of the input app if the app uses the Azure Active Directory Authentication Library>` este es el URI de redireccionamiento configurado en el registro de la aplicación. Normalmente sería el protocolo de dirección URL de la aplicación a la que se devolvería la aplicación Microsoft Authenticator después de la autenticación negociada. |
|**-v**| (Opcional) Genera mensajes detallados para la consola. Se recomienda usar esta marca para depurar cualquier error. |
|**-e**| (Opcional) Use esta marca para que la herramienta de ajuste de aplicaciones quite los derechos que faltan mientras procesa la aplicación. Consulte [Configurar los derechos de la aplicación](#setting-app-entitlements) para más información.|
|**-xe**| (Opcional) Imprime información sobre las extensiones de iOS de la aplicación y sobre los derechos necesarios para usarlas. Consulte [Configurar los derechos de la aplicación](#setting-app-entitlements) para más información. |
|**-x**| (Opcional) `<An array of paths to extension provisioning profiles>`. Úsela si la aplicación necesita perfiles de aprovisionamiento de extensión.|
|**-b**|(Opcional) Use -b sin un argumento si quiere que la aplicación de salida ajustada tenga la misma versión de paquete que la aplicación de entrada (no recomendado). <br/><br/> Use `-b <custom bundle version>` si quiere que la aplicación ajustada tenga un valor CFBundleVersion personalizado. Si decide especificar un valor CFBundleVersion personalizado, se recomienda que incremente el valor de CFBundleVersion de la aplicación nativa según el componente menos significativo, por ejemplo, 1.0.0 -> 1.0.1. |
|**-citrix**|Opta Incluya el SDK para aplicaciones de Citrix XenMobile (variante solo de red). Para usar esta opción, debe tener el [Kit de herramientas de Citrix MDX](https://docs.citrix.com/en-us/mdx-toolkit/about-mdx-toolkit.html) instalado. |
|**-f**|(Opcional) `<Path to a plist file specifying arguments.>` Use esta marca delante del archivo [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html) si decide usar la plantilla plist para especificar el resto de las propiedades de IntuneMAMPackager, como -i, -o y -p. Consulte Usar un archivo plist para la entrada de argumentos. |

### <a name="use-a-plist-to-input-arguments"></a>Usar un archivo plist para la entrada de argumentos

Una manera fácil de ejecutar la herramienta de ajuste de aplicaciones consiste en colocar todos los argumentos de comando en un archivo [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html). El formato de archivo plist es similar a XML. Se puede usar para la entrada de argumentos de línea de comandos mediante una interfaz de formulario.

En la carpeta IntuneMAMPackager/Contents/MacOS, abra `Parameters.plist`, que es una plantilla plist en blanco, con un editor de texto o Xcode. Escriba los argumentos para las claves siguientes:

| Clave de plist | Tipo |  Valor predeterminado | Notas |
|------------------|-----|--------------|-----|
| Ruta de acceso del paquete de aplicación de entrada |String|vacío| Igual que -i|
| Ruta de acceso del paquete de aplicación de salida |String|vacío| Igual que -o|
| Ruta de acceso del perfil de aprovisionamiento |String|vacío| Igual que -p|
| Hash del certificado SHA-1 |String|vacío| Igual que -c|
| Autoridad de ADAL |String|vacío| Igual que -aa|
| IDENTIFICADOR de cliente de ADAL |String|vacío| Igual que -ac|
| URI de respuesta de ADAL |String|vacío| Igual que -ar|
| Modo detallado habilitado |Boolean|false| Igual que -v|
| Quitar los derechos que faltan |Boolean|false| Igual que -c|
| Impedir la actualización de la compilación predeterminada |Boolen|false| Equivale a usar -b sin argumentos|
| Invalidación de la cadena de compilación |String|vacío| Valor de CFBundleVersion personalizado de la aplicación de salida ajustada.|
| Incluir el SDK de aplicación de Citrix XenMobile (variante solo de red)|Boolean|false| Igual que-Citrix|
| Rutas de acceso del perfil de aprovisionamiento de extensión |Matriz de cadenas|vacío| Matriz de perfiles de aprovisionamiento de extensión para la aplicación.

Ejecute IntuneMAMPackager con plist como único argumento:

```bash
./IntuneMAMPackager –f Parameters.plist
```

### <a name="post-wrapping"></a>Después del ajuste

Después de que finaliza el proceso de ajuste, se muestra el mensaje "The application was successfully wrapped" (La aplicación se ajustó correctamente). Si se produce un error, consulte [Mensajes de error](#error-messages-and-log-files) para obtener ayuda.

La aplicación ajustada se guarda en la carpeta de salida que especificó anteriormente. Puede cargar la aplicación en la consola de administración de Intune y asociarla con una directiva de administración de aplicaciones móviles.

> [!IMPORTANT]
> Al cargar una aplicación ajustada, puede intentar actualizar una versión anterior de la aplicación si ya se ha implementado en Intune una versión anterior (ajustada o nativa). Si experimenta un error, cargue la aplicación como una aplicación nueva y elimine la versión anterior.

Ahora puede implementar la aplicación en los grupos de usuarios y definir directivas de protección de aplicaciones para la aplicación. La aplicación se ejecuta en el dispositivo con las directivas de protección de aplicaciones especificadas.

## <a name="how-often-should-i-rewrap-my-ios-application-with-the-intune-app-wrapping-tool"></a>¿Con qué frecuencia conviene reajustar mi aplicación de iOS con la herramienta de ajuste de aplicaciones de Intune?

Los casos principales en los que resulta necesario reajustar las aplicaciones son los siguientes:

* La aplicación tiene una nueva versión. La versión anterior de la aplicación se ha ajustado y cargado en la consola de Intune.
* La herramienta de ajuste de aplicaciones de Intune para iOS tiene una nueva versión que permite corregir errores importantes o bien presenta características nuevas y específicas relativas a la directiva de protección de la aplicación de Intune. Esto suele darse tras seis u ocho semanas a través del repositorio de GitHub para la [herramienta de ajuste de aplicaciones de Microsoft Intune para iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios).

Para iOS, aunque es posible ajustar con un perfil de certificados y aprovisionamiento diferente al original utilizado para firmar la aplicación, si los derechos especificados en la aplicación no se incluyen en el nuevo perfil de aprovisionamiento, se producirá un error en el ajuste. Al usar la opción de línea de comandos "-e", que quita los derechos que faltan de la aplicación, para forzar que el ajuste no produzca un error en este escenario, puede provocar interrupciones de la funcionalidad en la aplicación.

Entre los procedimientos recomendados para el reajuste destacan los siguientes:

* Asegurarse de que otro perfil de aprovisionamiento tenga todos los derechos necesarios como cualquier perfil de aprovisionamiento anterior. 

## <a name="error-messages-and-log-files"></a>Archivos de registro y mensajes de error

Use la siguiente información para solucionar los problemas que tenga con la herramienta de ajuste de aplicaciones.

### <a name="error-messages"></a>Mensajes de error

Si la herramienta de ajuste de aplicaciones no se completa correctamente, se mostrará uno de los siguientes mensajes de error en la consola:

|Mensaje de error|Más información|
|-----------------|--------------------|
|Debe especificar un perfil de aprovisionamiento de iOS válido.|Su perfil de aprovisionamiento podría no ser válido. Asegúrese de tener los permisos correctos para dispositivos y que su perfil se destine correctamente a desarrollo o a distribución. El perfil de aprovisionamiento también podría haber expirado.|
|Especifique un nombre de aplicación de entrada válido.|Asegúrese de que el nombre de la aplicación de entrada especificado sea correcto.|
|Especifique una ruta válida a la aplicación de salida.|Asegúrese de que la ruta de acceso a la aplicación de salida especificada exista y sea correcta.|
|Especifique un perfil de aprovisionamiento de entrada válido.|Asegúrese de que proporcionó un nombre y una extensión de perfil de aprovisionamiento válidos. Puede que el perfil de aprovisionamiento no disponga de derechos o que no se haya incluido la opción de línea de comandos –p.|
|No se encontró la aplicación de entrada especificada. Especifique un nombre de aplicación de entrada y una ruta de acceso válidos.|Asegúrese de que la ruta de acceso de la aplicación de entrada sea válida y exista. Asegúrese de que la aplicación de entrada exista en esa ubicación.|
|No se encontró el archivo de perfil de aprovisionamiento entrada especificado. Especifique un archivo de perfil de aprovisionamiento de entrada válido.|Asegúrese de que la ruta de acceso al archivo de aprovisionamiento de entrada sea válida y de que el archivo especificado exista.|
|No se encontró la carpeta de aplicación de salida especificada. Especifique una ruta válida a la aplicación de salida.|Asegúrese de que la ruta de acceso de salida especificada sea válida y exista.|
|La aplicación de salida no tiene extensión **.ipa**.|La herramienta de ajuste de aplicaciones solo acepta aplicaciones con las extensiones **.app** e **.ipa**. Asegúrese de que el archivo de salida tenga una extensión válida.|
|Se especificó un certificado de firma no válido. Especifique un certificado de firma de Apple válido.|Asegúrese de haber descargado el certificado de firma correcto desde el portal para desarrolladores de Apple. El certificado podría haber expirado o puede que falte una clave pública o privada. Si el perfil de aprovisionamiento y el certificado de Apple se pueden usar para firmar correctamente una aplicación en Xcode, son válidos para la herramienta de ajuste de aplicaciones.|
|La aplicación de entrada especificada no es válida. Especifique una aplicación válida.|Asegúrese de que tenga una aplicación iOS válida que se haya compilado como archivo .app o .ipa.|
|La aplicación de entrada especificada está cifrada. Especifique una aplicación sin cifrar válida.|La herramienta de ajuste de aplicaciones no es compatible con aplicaciones cifradas. Proporcione una aplicación sin cifrar.|
|La aplicación de entrada especificada no está en un formato ejecutable independiente de la posición (PIE). Especifique una aplicación válida en formato PIE.|Las aplicaciones de archivo ejecutable independiente de la posición (PIE) se pueden cargar en una dirección de memoria aleatoria al ejecutarse. Esto puede tener ventajas para la seguridad. Para más información sobre las ventajas para la seguridad, consulte la documentación para desarrolladores de Apple.|
|La aplicación de entrada especificada ya se ajustó. Especifique una aplicación sin ajustar válida.|No puede procesar una aplicación que la herramienta ya procesó. Si desea volver a procesar una aplicación, ejecute la herramienta con la versión original de la aplicación.|
|La aplicación de entrada especificada no está firmada. Especifique una aplicación firmada válida.|La herramienta de ajuste de aplicaciones requiere que las aplicaciones estén firmadas. Consulte la documentación para desarrolladores para aprender a firmar una aplicación ajustada.|
|La aplicación de entrada especificada debe tener formato .ipa o .app.|La herramienta de ajuste de aplicaciones solo acepta aplicaciones con las extensiones .app e .ipa. Asegúrese de que el archivo de entrada tenga una extensión válida y se haya compilado como archivo .app o .ipa.|
|La aplicación de entrada especificada ya se ajustó y se encuentra en la última versión de la plantilla de directiva.|La herramienta de ajuste de aplicaciones no ajustará una aplicación ajustada existente con la última versión de la plantilla de directiva.|
|ADVERTENCIA: no ha especificado un hash de certificado SHA1. Asegúrese de que la aplicación ajustada se firme antes de implementarla.|Asegúrese de especificar un valor de hash SHA1 válido después de la marca de línea de comandos –c. |

### <a name="collecting-logs-for-your-wrapped-applications-from-the-device"></a>Recopilación de registros para las aplicaciones ajustadas desde el dispositivo
Siga estos pasos para obtener registros para las aplicaciones ajustadas durante la solución de problemas.

1. Vaya a la aplicación de configuración de iOS en el dispositivo y seleccione la aplicación LOB.
2. Cambie la **Consola de diagnóstico** a **Activado**.
3. Inicie la aplicación de LOB.
4. Haga clic en el vínculo "Comenzar".
5. Ahora puede copiar los registros a través del correo electrónico o copiarlos en una ubicación de OneDrive.

> [!NOTE]
> La funcionalidad de registro está habilitada para las aplicaciones ajustadas con la versión de Intune App Wrapping Tool 7.1.13 o una posterior.

### <a name="collecting-crash-logs-from-the-system"></a>Recopilación de registros de bloqueo del sistema

Es posible que la aplicación registre información útil en la consola del dispositivo cliente de iOS. Esta información resulta útil cuando se tienen problemas con la aplicación y es necesario determinar si el problema está relacionado con la herramienta de ajuste de aplicaciones. Para resolver este problema, use los siguientes pasos:

1. Reproduzca el problema ejecutando la aplicación.

2. Recopile la salida de consola siguiendo las instrucciones de [Depuración de aplicaciones iOS implementadas](https://developer.apple.com/library/ios/qa/qa1747/_index.html)de Apple.

Las aplicaciones ajustadas también ofrecen a los usuarios la opción de enviar registros directamente desde el dispositivo a través de correo electrónico después de que la aplicación se bloquea. Los usuarios pueden enviarle los registros para que los examine y los reenvíe a Microsoft si es necesario.

### <a name="certificate-provisioning-profile-and-authentication-requirements"></a>Requisitos de autenticación, perfil de aprovisionamiento y certificados

La herramienta de ajuste de aplicaciones para iOS tiene algunos requisitos que se deben cumplir para garantizar una funcionalidad completa.

|Requisito|Detalles|
|---------------|-----------|
|Perfil de aprovisionamiento de iOS|Asegúrese de que el perfil de aprovisionamiento sea válido antes de incluirlo. La herramienta de ajuste de aplicaciones no comprueba si el perfil de aprovisionamiento ha expirado al procesar una aplicación iOS. Si se especifica un perfil de aprovisionamiento expirado, la herramienta de ajuste de aplicaciones incluirá el perfil de aprovisionamiento caducado y no sabrá que hay un problema hasta que la aplicación no se pueda instalar en un dispositivo iOS.|
|Certificado de firma de iOS|Asegúrese de que el certificado de firma sea válido antes de especificarlo. La herramienta no comprueba si un certificado ha expirado al procesar aplicaciones iOS. Si se proporciona el valor hash de un certificado expirado, la herramienta procesará y firmará la aplicación, pero no se podrá instalar en dispositivos.<br /><br />Asegúrese de que el certificado proporcionado para firmar la aplicación ajustada tenga una coincidencia en el perfil de aprovisionamiento. La herramienta no valida si el perfil de aprovisionamiento tiene una coincidencia con el certificado proporcionado para firmar la aplicación ajustada.|
|Autenticación|Un dispositivo debe tener un PIN para que el cifrado funcione. En dispositivos en los que haya implementado una aplicación ajustada, al tocar la barra de estado del dispositivo será necesario que el usuario inicie la sesión de nuevo con una cuenta profesional o educativa. La directiva predeterminada de una aplicación ajustada es *autenticación al volver a iniciar*. iOS controla cualquier notificación externa (por ejemplo, una llamada telefónica) saliendo de la aplicación e iniciándola de nuevo.

## <a name="setting-app-entitlements"></a>Configurar los derechos de la aplicación

Antes de ajustar la aplicación, puede concederle *derechos* para que tenga permisos y funcionalidades adicionales que normalmente no podría usar. Un *archivo de derechos* se usa durante la firma de código para especificar permisos especiales dentro de la aplicación (por ejemplo, acceso a una cadena de claves compartida). Los servicios de aplicaciones específicos, denominados *funcionalidades*, se habilitan en Xcode durante el desarrollo de las aplicaciones. Una vez habilitadas, las capacidades se reflejan en el archivo de derechos. Para obtener más información sobre los derechos y las funcionalidades, consulte [Adding Capabilities](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) (Agregar funcionalidades) en la biblioteca para desarrolladores de iOS. Para obtener una lista completa de las capacidades admitidas, consulte [Capacidades admitidas](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SupportedCapabilities/SupportedCapabilities.html).

### <a name="supported-capabilities-for-the-app-wrapping-tool-for-ios"></a>Capacidades admitidas por la herramienta de ajuste de aplicaciones para iOS

|Capacidad|Descripción|Uso recomendado|
|--------------|---------------|------------------------|
|Grupos de aplicaciones|Use los grupos de aplicaciones para permitir que varias aplicaciones tengan acceso a contenedores compartidos y que la comunicación entre procesos adicionales entre las aplicaciones sea posible.<br /><br />Para habilitar grupos de aplicaciones, abra el panel **Funcionalidades** y haga clic en **ACTIVAR** en **Grupos de aplicaciones**. Puede agregar grupos de aplicaciones o seleccionar los ya existentes.|Al usar grupos de aplicaciones, use la notación DNS inversa:<br /><br />*group.com.companyName.AppGroup*|
|Modos en segundo plano|Si habilita los modos en segundo plano, la aplicación de iOS podrá seguir ejecutándose en segundo plano.||
|Protección de datos|La opción Protección de datos agrega un nivel de seguridad a los archivos almacenados en el disco mediante la aplicación de iOS. Asimismo, la protección de datos usa el hardware de cifrado integrado en ciertos dispositivos para almacenar archivos en el disco con un formato cifrado. Debe aprovisionar la aplicación para usar la protección de datos.||
|Compras desde la aplicación|La opción de Compras desde la aplicación inserta una opción para acceder a la tienda directamente desde su aplicación, lo que le permitirá conectarse a la misma y procesar los pagos del usuario de forma segura. Puede usar la opción Compras desde la aplicación para pagar por funcionalidad mejorada o para conseguir contenidos adicionales que pueda usar la aplicación.||
|Uso compartido de cadenas de claves|Si habilita el uso compartido de las cadenas de claves, la aplicación podrá compartir contraseñas en la cadena de claves con otras aplicaciones desarrolladas por el equipo.|Cuando use de forma compartida las cadenas de claves, use la notación DNS inversa:<br /><br />*com.companyName.KeychainGroup*|
|VPN personal|Habilite la VPN personal para permitir a su aplicación crear y controlar un sistema personalizado de la configuración de VPN mediante el marco de la extensión de la red.||
|Notificaciones de inserción|El servicio de notificaciones push de Apple (APN) permite que una aplicación que no se está ejecutando en primer plano notifique al usuario que tiene información para él.|Para que funcionen las notificaciones push, debe usar un perfil de aprovisionamiento específico de la aplicación.<br /><br />Siga los pasos de la [documentación para desarrolladores de Apple](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html).|
|Configuración de accesorios inalámbricos|Al habilitar la configuración de accesorios inalámbricos, se agrega al proyecto el marco de accesorios externos y permite a la aplicación configurar accesorios MFi Wi-Fi.||

### <a name="steps-to-enable-entitlements"></a>Pasos para habilitar derechos

1. Habilite las capacidades de la aplicación:

    a.  En Xcode, vaya al destino de la aplicación y haga clic en **Capabilities** (Funcionalidades).

    b.  Active las capacidades adecuadas. Para obtener información detallada sobre cada funcionalidad y sobre cómo determinar los valores correctos, consulte [Adding Capabilities](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) (Agregar funcionalidades) en la biblioteca para desarrolladores de iOS.

    c.  Tenga en cuenta los identificadores que haya creado durante el proceso. Es posible que también se haga referencia a ellos como los valores `AppIdentifierPrefix`.

    d.  Compile y firme la aplicación para que se realicen los ajustes oportunos.

2. Habilite los derechos en el perfil de aprovisionamiento:

    a.  Inicie sesión en el Centro de usuarios registrados de Apple Developer.

    b.  Cree un perfil de aprovisionamiento para la aplicación. Para obtener instrucciones, consulte [How to Obtain the Prerequisites for the Intune App Wrapping Tool for iOS](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/) (Cómo obtener los requisitos previos para la Herramienta de ajuste de aplicaciones de Intune para iOS).

    c.  En el perfil de aprovisionamiento, habilite los mismos derechos que tiene en su aplicación. Debe proporcionar los mismos identificadores (los valores `AppIdentifierPrefix`) que especificó durante el desarrollo de la aplicación. 

    d.  Finalice el Asistente para perfiles de aprovisionamiento y descargue el archivo.

3. Asegúrese de que se hayan cumplido todos los requisitos previos y, a continuación, ajuste la aplicación.

### <a name="troubleshoot-common-errors-with-entitlements"></a>Solucionar errores comunes con derechos

Si la herramienta de ajuste de aplicaciones para iOS muestra un error de derecho, intente los siguientes pasos de solución de problemas.

|Problema|Causa|Solución|
|---------|---------|--------------|
|Error al analizar los derechos creados a partir de la aplicación de entrada.|La herramienta de ajuste de aplicaciones no puede leer el archivo de derechos que se ha extraído de la aplicación. Es posible que el archivo de derechos sea incorrecto.|Compruebe el archivo de derechos de la aplicación. Las instrucciones siguientes explican cómo hacerlo. Al inspeccionar el archivo de derechos, busque cualquier sintaxis incorrecta. Recuerde que el archivo debe estar en formato XML.|
|Faltan los derechos en el perfil de aprovisionamiento (se enumeran los derechos que faltan). Vuelva a empaquetar la aplicación con un perfil de aprovisionamiento que tenga estos derechos.|Existe una incoherencia entre los derechos habilitados en el perfil de aprovisionamiento y las capacidades habilitadas en la aplicación. Esta disparidad también se aplica a los identificadores asociados con funcionalidades concretas (por ejemplo, grupos de aplicaciones, acceso a cadenas de claves, etc.).|Por lo general, puede crear un nuevo perfil de aprovisionamiento que tenga las mismas capacidades que la aplicación. Cuando no coinciden los identificadores entre el perfil y la aplicación, la herramienta de ajuste de aplicaciones reemplazará los identificadores si le es posible. Si sigue apareciendo este error después de crear un nuevo perfil de aprovisionamiento, puede intentar quitar los derechos de la aplicación mediante el parámetro – e (consulte la sección "Uso del parámetro – e para quitar derechos de una aplicación" a continuación).|

### <a name="find-the-existing-entitlements-of-a-signed-app"></a>Buscar los derechos existentes de una aplicación firmada

Para revisar los derechos existentes de una aplicación firmada y de un perfil de aprovisionamiento:

1. Busque el archivo .ipa y cambie la extensión a .zip.

2. Expanda el archivo .zip. Esto creará una carpeta de carga que contiene el lote .app.

3. Use la herramienta de firma de código para comprobar los derechos en el paquete de aplicaciones, donde `YourApp.app` es el nombre real del paquete de aplicaciones:

    ```bash
    codesign -d --entitlements :- "Payload/YourApp.app"
    ```

4. Use la herramienta de seguridad para comprobar los derechos del perfil de aprovisionamiento de la aplicación incrustada, donde `YourApp.app` es el nombre real del grupo de aplicaciones.

    ```bash
    security cms -D -i "Payload/YourApp.app/embedded.mobileprovision"
    ```

### <a name="remove-entitlements-from-an-app-by-using-the-e-parameter"></a>Eliminación de derecho de una aplicación mediante el parámetro – e

Este comando quita cualquier funcionalidad habilitada en la aplicación que no esté en el archivo de derechos. Si quita funcionalidades que la aplicación esté usando, puede interrumpirla. Un ejemplo en el que podría quitar las funcionalidades que faltan es una aplicación producida por el proveedor que tenga todas las funcionalidades de forma predeterminada.

```bash
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -e
```

## <a name="security-and-privacy-for-the-app-wrapping-tool"></a>Seguridad y privacidad de la herramienta de ajuste de aplicaciones

Use los procedimientos recomendados de seguridad y privacidad siguientes al usar la herramienta de ajuste de aplicaciones.

- El certificado de firma, el perfil de aprovisionamiento y la aplicación de línea de negocio que especifique deben estar en el mismo equipo macOS que use para ejecutar la herramienta de ajuste de aplicaciones. Si los archivos están en una ruta de acceso UNC, asegúrese de que se pueda acceder a ellos desde la máquina macOS. La ruta de acceso debe estar protegida mediante la firma SMB o IPsec.

    La aplicación ajustada que se importa a la consola de administración debe estar en el mismo equipo en el que se ejecuta la herramienta. Si el archivo está en una ruta de acceso UNC, asegúrese de que sea accesible desde el equipo en el que se ejecuta la consola de administración. La ruta de acceso debe estar protegida mediante la firma SMB o IPsec.

- El entorno donde se descarga la herramienta de ajuste de aplicaciones desde el repositorio de GitHub debe protegerse mediante la firma SMB o IPsec.

- La aplicación que procese debe proceder de un origen de confianza para garantizar la protección frente a ataques.

- Asegúrese de que la carpeta de salida especificada en la herramienta de ajuste de aplicaciones esté protegida, especialmente si se trata de una carpeta remota.

- Las aplicaciones iOS que incluyen un cuadro de diálogo de carga de archivos pueden permitir a los usuarios evitar las restricciones al cortar, copiar y pegar aplicadas a la aplicación. Por ejemplo, un usuario podría usar el cuadro de diálogo de carga de archivos para cargar una captura de pantalla de los datos de aplicación.

- Cuando supervisa la carpeta de documentos en su dispositivo desde dentro de una aplicación ajustada, puede que vea una carpeta llamada .msftintuneapplauncher. Si cambia o elimina este archivo, podría afectar al funcionamiento correcto de las aplicaciones restringidas.

## <a name="intune-app-wrapping-tool-for-ios-with-citrix-mdx-mvpn"></a>Herramienta de ajuste de aplicaciones de Intune para iOS con mVPN de Citrix MDX

Esta característica es una integración con el contenedor de aplicaciones de Citrix MDX para iOS. La integración es simplemente una marca adicional y opcional de línea de comandos, `-citrix` para la Herramienta de ajuste de aplicaciones de Intune general.

### <a name="requirements"></a>Requisitos

Para usar la marca `-citrix`, también deberá instalar el [contenedor de aplicaciones de Citrix MDX para iOS](https://docs.citrix.com/en-us/mdx-toolkit/10/xmob-mdx-kit-app-wrap-ios.html) en el mismo equipo macOS. Las descargas se encuentran en [descargas de Citrix XenMobile](https://www.citrix.com/downloads/xenmobile/) y solo pueden acceder a ellas los clientes de Citrix una vez que inician sesión. Asegúrese de que se instala en la ubicación predeterminada: `/Applications/Citrix/MDXToolkit`. 

> [!NOTE] 
> La integración de Intune y Citrix solo es compatible en dispositivos iOS 10 o superiores.

### <a name="use-the--citrix-flag"></a>Uso de la marca `-citrix`

Simplemente ejecute el comando de ajuste de aplicaciones general con la marca `-citrix` adjunta. La marca `-citrix` actualmente no toma ningún argumento.

**Formato de uso**:

```bash
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> -p /<path to provisioning profile> -c <SHA1 hash of the certificate> [-b [<output app build string>]] [-v] [-e] [-x /<array of extension provisioing profile paths>] [-citrix]
```

**Comando de ejemplo**:

```bash
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i ~/Desktop/MyApp.ipa -o ~/Desktop/MyApp_Wrapped.ipa -p ~/Desktop/My_Provisioning_Profile_.mobileprovision -c 12A3BC45D67EF8901A2B3CDEF4ABC5D6E7890FAB  -v true -citrix
```

## <a name="see-also"></a>Consulte también

- [Decidir cómo preparar las aplicaciones para la administración de aplicaciones móviles mediante Microsoft Intune](apps-prepare-mobile-application-management.md)
- [Preguntas comunes, problemas y su solución con perfiles y directivas de dispositivos](../configuration/device-profile-troubleshoot.md)
- [Usar el SDK para habilitar aplicaciones para la administración de aplicaciones móviles)](app-sdk.md)
