---
title: 'Configuración de características de dispositivos macOS en Microsoft Intune: Azure | Microsoft Docs'
description: Consulte las opciones para configurar dispositivos macOS para AirPrint y personalizar la ventana de inicio de sesión para mostrar u ocultar los botones de encendido en Microsoft Intune. Consulte los pasos para obtener la dirección IP, la ruta de acceso y la configuración de puertos de un servidor de AirPrint en la red. Use esta configuración en un perfil de configuración de dispositivo para configurar dispositivos macOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5519bdc405e725556db18d36fa98289c4edb5090
ms.sourcegitcommit: df8e2c052fafb2d5d4e9b4fcd831ae0ecf7f8d16
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74992902"
---
# <a name="macos-device-feature-settings-in-intune"></a>Configuración de características de dispositivos macOS en Intune

Intune incluye algunas opciones integradas para personalizar las características de los dispositivos macOS. Por ejemplo, los administradores pueden agregar impresoras de desimpresión, elegir cómo los usuarios inician sesión, configurar los controles de energía, usar la autenticación de inicio de sesión único, etc.

Use estas características para controlar los dispositivos macOS como parte de la solución de administración de dispositivos móviles (MDM).

En este artículo se enumeran estas opciones de configuración y se describe lo que hace cada una de ellas. También muestra los pasos para obtener la dirección IP, la ruta de acceso y el puerto de las impresoras AirPrint mediante la aplicación Terminal (emulador). Para obtener más información sobre las características del dispositivo, vaya a [Agregar configuración de características de dispositivos iOS o MacOS](device-features-configure.md).

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración de dispositivo macOS](device-features-configure.md).

> [!NOTE]
> Esta configuración se aplica a diferentes tipos de inscripción, con algunas opciones de configuración aplicables a todas las opciones de inscripción. Para obtener más información sobre los diferentes tipos de inscripción, consulte [inscripción de MacOS](../enrollment/macos-enroll.md).

## <a name="airprint"></a>AirPrint

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>La configuración se aplica a: inscripción de dispositivos y inscripción de dispositivo automatizada 

- **Dirección IP**: escriba la dirección IPv4 o IPv6 de la impresora. Si usa nombres de host para identificar las impresoras, puede obtener la dirección IP haciendo ping a la impresora en la aplicación Terminal. En la sección [Obtención de la dirección IP y la ruta de acceso](#get-the-ip-address-and-path) (en este artículo) se proporcionan más detalles.
- **Ruta de acceso**: escriba la ruta de acceso de la impresora. La ruta de acceso suele ser `ipp/print` para las impresoras de la red. En la sección [Obtención de la dirección IP y la ruta de acceso](#get-the-ip-address-and-path) (en este artículo) se proporcionan más detalles.
- **Puerto** (iOS 11.0 y versiones posteriores) escriba el puerto de escucha del destino de AirPrint. Si se deja esta propiedad en blanco, AirPrint usa el puerto predeterminado.
- **TLS** (iOS 11.0 y versiones posteriores): elija **Habilitar** para proteger las conexiones AirPrint con Seguridad de la capa de transporte (TLS).

- **Agregue** el servidor de AirPrint. Puede agregar varios servidores AirPrint.

También puede **importar** un archivo separado por comas (.csv) que incluya una lista de impresoras AirPrint. Además, después de agregar impresoras AirPrint en Intune, puede **Exportar** esta lista.

### <a name="get-the-ip-address-and-path"></a>Obtención de la dirección IP y la ruta de acceso

Para agregar servidores AirPrinter, necesita la dirección IP de la impresora, la ruta de acceso de recursos y el puerto. Los pasos siguientes muestran cómo obtener esta información.

1. En un equipo Mac conectado a la misma red local (subred) que las impresoras AirPrint, abra **Terminal** (en **/Aplicaciones/Utilidades**).
2. En la aplicación Terminal, escriba `ippfind` y seleccione Entrar.

    Anote la información de la impresora. Por ejemplo, puede devolver algo parecido a `ipp://myprinter.local.:631/ipp/port1`. La primera parte es el nombre de la impresora. La última parte (`ipp/port1`) es la ruta de acceso del recurso.

3. En Terminal, escriba `ping myprinter.local` y seleccione Entrar.

   Anote la dirección IP. Por ejemplo, puede devolver algo parecido a `PING myprinter.local (10.50.25.21)`.

4. Use los valores de dirección IP y de ruta de acceso del recurso. En este ejemplo, la dirección IP es `10.50.25.21` y la ruta de acceso del recurso es `/ipp/port1`.

## <a name="login-items"></a>Elementos de inicio de sesión

### <a name="settings-apply-to-all-enrollment-types"></a>La configuración se aplica a: todos los tipos de inscripción

- **Archivos, carpetas y aplicaciones personalizadas**: **agregue** la ruta de acceso de un archivo, una carpeta, una aplicación personalizada o una aplicación del sistema que quiera abrir cuando un usuario inicie sesión en el dispositivo. Las aplicaciones del sistema o las aplicaciones compiladas o personalizadas para su organización suelen estar en la carpeta `Applications`, con una ruta de acceso similar a `/Applications/AppName.app`. 

  Puede agregar muchos archivos, carpetas y aplicaciones. Por ejemplo, escriba:  
  
  - `/Applications/Calculator.app`
  - `/Applications`
  - `/Applications/Microsoft Office/root/Office16/winword.exe`
  - `/Users/UserName/music/itunes.app`
  
  Al agregar una aplicación, una carpeta o un archivo, asegúrese de escribir la ruta de acceso correcta. No todos los elementos se encuentran en la carpeta `Applications`. Si un usuario mueve un elemento de una ubicación a otra, la ruta de acceso cambia. Este elemento que se ha despasado no se abrirá cuando el usuario inicie sesión.

## <a name="login-window"></a>Ventana de inicio de sesión

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>La configuración se aplica a: inscripción de dispositivos y inscripción de dispositivo automatizada

#### <a name="window-layout"></a>Diseño de ventana

- **Mostrar información adicional en la barra de menús**: cuando se selecciona el área de tiempo en la barra de menús, **Permitir** muestra el nombre de host y la versión de macOS. **No configurado** (valor predeterminado) no muestra esta información en la barra de menús.
- **Banner**: escriba un mensaje que se mostrará en la pantalla de inicio de sesión del dispositivo. Por ejemplo, escriba la información de su organización, un mensaje de bienvenida, información de objetos perdidos, etc.
- **Elegir formato de inicio de sesión**: elija cómo inician sesión en el dispositivo los usuarios. Las opciones son:
  - **Solicitar nombre de usuario y contraseña** (valor predeterminado): los usuarios deben escribir un nombre de usuario y una contraseña.
  - **Enumerar todos los usuarios, solicitar contraseña**: los usuarios deben seleccionar su nombre de usuario de una lista de usuarios y, después, escribir su contraseña. Configure también:

    - **Usuarios locales**: **Ocultar** no muestra las cuentas de usuarios locales en la lista de usuarios, que puede incluir las cuentas de administrador y estándar. Se muestran únicamente las cuentas de usuario de red y del sistema. **No configurado** (valor predeterminado) muestra las cuentas de usuarios locales en la lista de usuarios.
    - **Cuentas móviles**: **Ocultar** no muestra las cuentas móviles en la lista de usuarios. **No configurado** (valor predeterminado) muestra las cuentas móviles en la lista de usuarios. Algunas cuentas móviles pueden aparecer como usuarios de red.
    - **Usuarios de red**: seleccione **Mostrar** para enumerar los usuarios de red en la lista de usuarios. **No configurado** (valor predeterminado) no muestra las cuentas de usuarios de red en la lista de usuarios.
    - **Usuarios administradores**: **Ocultar** no muestra las cuentas de usuarios administradores en la lista de usuarios. **No configurado** (valor predeterminado) muestra las cuentas de usuarios administradores en la lista de usuarios.
    - **Otros usuarios**: seleccione **Mostrar** para enumerar los usuarios de **Otros...** en la lista de usuarios. **No configurado** (valor predeterminado) no muestra las cuentas de otros usuarios en la lista de usuarios.

#### <a name="login-screen-power-settings"></a>Configuración de energía de la pantalla de inicio de sesión

- **Botón Apagar**: **Ocultar** no muestra el botón de apagado en la pantalla de inicio de sesión. **No configurado** (valor predeterminado) muestra el botón de apagado.
- **Botón Reiniciar**: **Ocultar** no muestra el botón de reinicio en la pantalla de inicio de sesión. **No configurado** (valor predeterminado) muestra el botón de reinicio.
- **Botón de suspensión**: **Ocultar** no muestra el botón de suspensión en la pantalla de inicio de sesión. **No configurado** (valor predeterminado) muestra el botón de suspensión.

#### <a name="other"></a>Otros

- **Deshabilitar inicio de sesión del usuario desde la consola**: **Deshabilitar** oculta la línea de comandos de macOS usada para iniciar sesión. Para usuarios típicos, **deshabilite** esta configuración. **No configurado** (valor predeterminado) permite a los usuarios avanzados iniciar sesión con la línea de comandos de macOS. Para entrar en modo de consola, los usuarios escriben `>console` en el campo de nombre de usuario de campo y deben autenticarse en la ventana de la consola.

#### <a name="apple-menu"></a>Menú Apple

Después de que los usuarios inicien sesión en los dispositivos, la siguiente configuración afecta a lo que puede hacer.

- **Deshabilitar Apagar**: **Deshabilitar** impide que los usuarios seleccionen la opción **Apagado** después de que el usuario inicie sesión. **No configurado** (valor predeterminado) permite que los usuarios seleccionen el elemento de menú **Apagado** en el dispositivo.
- **Deshabilitar Reiniciar**: **Deshabilitar** impide que los usuarios seleccionen la opción **Reiniciar** después de que el usuario inicie sesión. **No configurado** (valor predeterminado) permite que los usuarios seleccionen el elemento de menú **Reiniciar** en el dispositivo.
- **Deshabilitar Desconectar**: **Deshabilitar** impide que los usuarios seleccionen la opción **Desconectar** después de que el usuario inicie sesión. **No configurado** (valor predeterminado) permite que los usuarios seleccionen el elemento de menú **Desconectar** en el dispositivo.
- **Deshabilitar Cerrar sesión** (macOS 10.13 y versiones posteriores): **Deshabilitar** impide que los usuarios seleccionen la opción **Cerrar sesión** después de que el usuario inicie sesión. **No configurado** (valor predeterminado) permite que los usuarios seleccionen el elemento de menú **Cerrar sesión** en el dispositivo.
- **Deshabilitar pantalla de bloqueo** (macOS 10.13 y versiones posteriores): **Deshabilitar** impide que los usuarios seleccionen la opción **Pantalla de bloqueo** después de que el usuario inicie sesión. **No configurado** (valor predeterminado) permite que los usuarios seleccionen el elemento de menú **Pantalla de bloqueo** en el dispositivo.

## <a name="single-sign-on-app-extension"></a>Extensión de aplicación de inicio de sesión único

Esta característica se aplica a:

- macOS 10.15 y versiones más recientes

### <a name="settings-apply-to-all-enrollment-types"></a>La configuración se aplica a: todos los tipos de inscripción 

- **Tipo de extensión de aplicación de SSO**: elija el tipo de extensión de aplicación SSO de credenciales. Las opciones son:

  - **No configurado**: no se usan las extensiones de aplicación. Para deshabilitar una extensión de aplicación, cambie el tipo de extensión de aplicación de SSO a **no configurado**.
  - **Redirigir**: Use una extensión de aplicación de redireccionamiento genérica y personalizable para realizar el inicio de sesión único con flujos de autenticación modernos. Asegúrese de que conoce la extensión y el identificador del equipo para la extensión de la aplicación de su organización.
  - **Credential**: Use una extensión de aplicación de credenciales genérica y personalizable para realizar el inicio de sesión único con flujos de autenticación de desafío y respuesta. Asegúrese de que conoce el identificador de la extensión y del equipo para la extensión de la aplicación SSO de su organización.  
  - **Kerberos**: Use la extensión integrada de Kerberos de Apple, que se incluye en macOS Catalina 10,15 y versiones más recientes. Esta opción es una versión específica de Kerberos de la extensión de la aplicación de **credenciales** .

  > [!TIP]
  > Con los tipos de **credenciales** y **redireccionamiento** , agregue sus propios valores de configuración para pasar a través de la extensión. Si usa la **credencial**, considere la posibilidad de usar las opciones de configuración integradas proporcionadas por Apple en el tipo de **Kerberos** .

- **Identificador de extensión** (redirección y credencial): escriba el identificador de paquete que identifica la extensión de la aplicación de SSO, como `com.apple.ssoexample`.
- **Identificador de equipo** (redirección y credencial): escriba el identificador de equipo de la extensión de la aplicación de SSO. Un identificador de equipo es una cadena alfanumérica de 10 caracteres (números y letras) que genera Apple, como `ABCDE12345`. 

  [Busque el identificador de su equipo](https://help.apple.com/developer-account/#/dev55c3c710c) (abre el sitio web de Apple) para obtener más información.

- **Dominio** Kerberos (credencial y Kerberos): escriba el nombre del dominio Kerberos de autenticación. El nombre de dominio Kerberos debe escribirse en mayúsculas, como `CONTOSO.COM`. Normalmente, el nombre de dominio Kerberos es el mismo que el nombre de dominio DNS, pero en mayúsculas.

- **Dominios** (credenciales y Kerberos): escriba los nombres de dominio o de host de los sitios que pueden autenticarse a través de SSO. Por ejemplo, si el sitio web es `mysite.contoso.com`, `mysite` es el nombre de host y `contoso.com` es el nombre de dominio. Cuando los usuarios se conectan a cualquiera de estos sitios, la extensión de la aplicación controla el desafío de autenticación. Esta autenticación permite a los usuarios usar el ID. de la persona, Touch ID o pincode/PASSCODE de Apple para iniciar sesión.

  - Todos los dominios de la extensión de aplicación de inicio de sesión único perfiles de Intune deben ser únicos. No se puede repetir un dominio en ningún perfil de extensión de aplicación de inicio de sesión, aunque se usen distintos tipos de extensiones de aplicación de SSO.
  - Estos dominios no distinguen mayúsculas de minúsculas.

- **Direcciones URL** (solo redireccionamiento): escriba los prefijos de dirección URL de los proveedores de identidades en cuyo nombre la extensión de aplicación de redireccionamiento realiza SSO. Cuando un usuario se redirige a estas direcciones URL, la extensión de la aplicación SSO intervendrá y solicitará SSO.

  - Todas las direcciones URL de los perfiles de extensión de aplicación de inicio de sesión único de Intune deben ser únicas. No se puede repetir un dominio en ningún perfil de extensión de aplicación de SSO, aunque se usen distintos tipos de extensiones de aplicación de SSO.
  - Las direcciones URL deben comenzar por http://o https://.

- **Configuración adicional** (redirección y credencial): escriba datos adicionales específicos de la extensión para pasarlos a la extensión de la aplicación de SSO:
  - **Clave**: escriba el nombre del elemento que desea agregar, como `user name`.
  - **Tipo**: escriba el tipo de datos. Las opciones son:

    - String
    - Booleano: en **valor de configuración**, escriba `True` o `False`.
    - Entero: en **valor de configuración**, escriba un número.
    
  - **Valor**: escriba los datos.
  
  - **Agregar**: Seleccione esta configuración para agregar las claves de configuración.

- **Uso de cadena de claves** (solo Kerberos): elija **bloquear** para impedir que se guarden y almacenen contraseñas en la cadena de claves. **No configurado** (valor predeterminado) permite guardar y almacenar contraseñas en la cadena de claves.  
- **Identificador de la esfera, Touch ID o PASSCODE** (solo Kerberos): **requerir** obliga a los usuarios a escribir su identificador de la esfera, Touch ID o el código de acceso de Apple para iniciar sesión en los dominios que ha agregado. **No configurado** (valor predeterminado) no requiere que los usuarios utilicen la biometría o el código de acceso para iniciar sesión.
- **Dominio Kerberos predeterminado** (solo Kerberos): elija **Habilitar** para establecer el valor de **dominio** Kerberos que especificó como dominio predeterminado. **No configurado** (valor predeterminado) no establece un dominio Kerberos predeterminado.

  > [!TIP]
  > - **Habilite** esta opción si va a configurar varias extensiones de aplicación SSO de Kerberos en su organización.
  > - **Habilite** esta opción si usa varios dominios. Establece el valor de **dominio Kerberos** que escribió como el dominio Kerberos predeterminado.
  > - Si solo tiene un dominio Kerberos, déjelo como **no configurado** (valor predeterminado).

- **Detección** automática (solo Kerberos): cuando se establece en **bloquear**, la extensión de Kerberos no usa automáticamente LDAP y DNS para determinar su Active Directory nombre de sitio. **No configurado** (valor predeterminado) permite que la extensión Busque automáticamente el nombre del sitio Active Directory.
- **Cambios de contraseña** (solo Kerberos): **bloqueo** impide que los usuarios cambien las contraseñas que usan para iniciar sesión en los dominios que ha escrito. **No configurado** (valor predeterminado) permite cambios de contraseña.  
- **Sincronización de contraseñas** (solo Kerberos): elija **Habilitar** para sincronizar las contraseñas locales de los usuarios con Azure ad. **No configurado** (valor predeterminado) deshabilita la sincronización de contraseñas para Azure ad. Use esta opción como alternativa o copia de seguridad en SSO. Esta configuración no funciona si los usuarios han iniciado sesión con una cuenta de Apple Mobile.
- **Windows Server Active Directory la complejidad de la contraseña** (solo Kerberos): elija **requerir** para forzar que las contraseñas de usuario cumplan los requisitos de complejidad de contraseñas de Active Directory. Para obtener más información, consulte [la contraseña debe cumplir los requisitos de complejidad](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/password-must-meet-complexity-requirements) . **No configurado** (valor predeterminado) no requiere que los usuarios cumplan los requisitos de contraseña de Active Directory.
- **Longitud mínima** de la contraseña (solo Kerberos): escriba el número mínimo de caracteres que pueden conllevar la contraseña de un usuario. **No configurado** (valor predeterminado) no aplica una longitud de contraseña mínima en los usuarios.
- **Límite de reutilización de contraseñas** (solo Kerberos): escriba el número de contraseñas nuevas, de 1-24, que deben usarse hasta que se pueda reutilizar una contraseña anterior en el dominio. **No configurado** (valor predeterminado) no impone un límite de reutilización de contraseñas.
- **Vigencia mínima** de la contraseña (solo Kerberos): especifique el número de días que se debe usar una contraseña en el dominio para que un usuario pueda cambiarla. **No configurado** (valor predeterminado) no aplica una antigüedad mínima para las contraseñas antes de que se puedan cambiar.
- **Notificación de expiración de contraseña** (solo Kerberos): escriba el número de días antes de que una contraseña expire para que los usuarios reciban una notificación de que la contraseña expirará. **No configurado** (valor predeterminado) utiliza `15` días.
- **Expiración de la contraseña** (solo Kerberos): escriba el número de días antes de que se deba cambiar la contraseña del dispositivo. **No configurado** (valor predeterminado) significa que las contraseñas de usuario nunca expiran.
- **URL de cambio de contraseña** (solo Kerberos): escriba la dirección URL que se inicia cuando el usuario inicia un cambio de contraseña de Kerberos.
- **Nombre principal** (solo Kerberos): escriba el nombre de usuario de la entidad de seguridad de Kerberos. No es necesario incluir el nombre de dominio Kerberos. Por ejemplo, en `user@contoso.com`, `user` es el nombre principal y `contoso.com` es el nombre de dominio Kerberos.

  > [!TIP]
  > - También puede usar variables en el nombre de la entidad de seguridad si escribe llaves `{{ }}`. Por ejemplo, para mostrar el nombre de usuario, escriba `Username: {{username}}`. 
  > - Sin embargo, tenga cuidado con la sustitución de variables porque las variables no se validan en la interfaz de usuario y distinguen mayúsculas de minúsculas. Asegúrese de escribir la información correcta.
  
- **Código de sitio de Active Directory** (solo Kerberos): escriba el nombre del sitio Active Directory que debe usar la extensión de Kerberos. Es posible que no necesite cambiar este valor, ya que la extensión de Kerberos puede encontrar automáticamente el código del sitio Active Directory.
- **Nombre de caché** (solo Kerberos): escriba el nombre de los servicios de seguridad genéricos (GSS) de la memoria caché de Kerberos. Lo más probable es que no tenga que establecer este valor.  
- **Mensaje de requisitos de contraseña** (solo Kerberos): escriba una versión de texto de los requisitos de contraseña de su organización que se muestra a los usuarios. El mensaje se muestra si no necesita los requisitos de complejidad de la contraseña de Active Directory o no escribe una longitud mínima de la contraseña.  
- **Identificadores de lote de aplicaciones** (solo Kerberos): **agregue** los identificadores de lote de aplicaciones que deben usar el inicio de sesión único en los dispositivos. A estas aplicaciones se les concede acceso al vale de concesión de vales de Kerberos, el vale de autenticación y autenticar a los usuarios en los servicios a los que están autorizados para obtener acceso.
- **Asignación de dominio Kerberos** (solo Kerberos): **agregue** los sufijos DNS de dominio que deben asignarse a su dominio Kerberos. Use esta opción cuando los nombres DNS de los hosts no coincidan con el nombre de dominio Kerberos. Lo más probable es que no tenga que crear esta asignación personalizada de dominio a dominio Kerberos.
- **Certificado PKINIT** (solo Kerberos): **Seleccione** el certificado de criptografía de clave pública para la autenticación inicial (PKINIT) que se puede usar para la autenticación Kerberos. Puede elegir entre los certificados [PKCS](../protect/certficates-pfx-configure.md) o [SCEP](../protect/certificates-scep-configure.md) que ha agregado en Intune. Para obtener más información sobre los certificados, consulte [usar certificados para la autenticación en Microsoft Intune](../protect/certificates-configure.md).

## <a name="associated-domains"></a>Dominios asociados

En Intune, puede:

- Agregue muchas asociaciones de aplicación a dominio.
- Asociar muchos dominios a la misma aplicación.

Esta característica se aplica a:

- macOS 10.15 y versiones más recientes

### <a name="settings-apply-to-all-enrollment-types"></a>La configuración se aplica a: todos los tipos de inscripción

- **Identificador**de la aplicación: escriba el identificador de la aplicación que se va a asociar a un sitio Web. El identificador de la aplicación incluye el identificador del equipo y un identificador de paquete: `TeamID.BundleID`.

  El identificador de equipo es una cadena alfanumérica de 10 caracteres (letras y números) que Apple genera para los desarrolladores de aplicaciones, como `ABCDE12345`. [Busque el identificador de equipo](https://help.apple.com/developer-account/#/dev55c3c710c) (abre el sitio web de Apple) más información.

  El identificador de paquete identifica de forma única la aplicación y, normalmente, tiene el formato de notación de nombre de dominio inversa. Por ejemplo, el identificador de paquete del buscador es `com.apple.finder`. Para buscar el identificador de paquete, use el AppleScript en terminal:

  `osascript -e 'id of app "ExampleApp"'`

- **Dominio**: escriba el dominio del sitio web que se va a asociar a una aplicación. El dominio incluye un tipo de servicio y un nombre de host completo, como `webcredentials:www.contoso.com`.

  Puede hacer coincidir todos los subdominios de un dominio asociado escribiendo `*.` (un carácter comodín de asterisco y un punto) antes del principio del dominio. El período es obligatorio. Los dominios exactos tienen una prioridad más alta que los dominios comodín. Por lo tanto, los patrones de los dominios primarios coinciden *si* no se encuentra ninguna coincidencia en el subdominio completo.

  El tipo de servicio puede ser:

  - **authsrv**: extensión de aplicación de inicio de sesión único
  - **applink**: vínculo universal
  - **webcredentials**: contraseña Autorrellenar

- **Agregar**: Seleccione esta propiedad para agregar sus aplicaciones y dominios asociados.

> [!TIP]
> Para solucionar problemas, en el dispositivo macOS, Abra **preferencias del sistema** > **perfiles**. Confirme que el perfil que ha creado está en la lista de perfiles de dispositivo. Si aparece, asegúrese de que la **configuración de dominios asociados** está en el perfil e incluye el ID. de aplicación y los dominios correctos.

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

También puede configurar las características del dispositivo en [iOS](ios-device-features-settings.md).
