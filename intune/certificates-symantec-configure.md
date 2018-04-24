---
title: Emisión de certificados PKCS de Symantec con Microsoft Intune
titlesuffix: ''
description: Instale y configure Intune Certificate Connector para emitir certificados PKCS desde el servicio web del administrador de PKI de Symantec a los dispositivos administrados por Intune.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ff642c7d8d836979fadebc799e2e7373cd299f4e
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="set-up-intune-certificate-connector-for-symantec-pki-manager-web-service"></a>Configuración de Intune Certificate Connector para el servicio web del administrador de PKI de Symantec

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En este artículo se muestra cómo instalar y configurar Intune Certificate Connector para emitir certificados PKCS desde un servicio web del administrador de PKI de Symantec a los dispositivos administrados por Intune.

En este artículo, el servicio web del administrador de PKI de Symantec será CA de Symantec. Si ya configuró Intune Certificate Connector para emitir certificados PKCS y certificados SCEP desde la entidad de certificación (CA) de Microsoft, también se puede usar Connector para configurar y emitir certificados PKCS desde una CA de Symantec. En este caso, Intune Certificate Connector puede emitir los certificados siguientes:

* Certificados PKCS desde una CA de Microsoft
* Certificados SCEP desde una CA de Microsoft
* Certificados PKCS desde una CA de Symantec

Si desea usar Intune Certificate Connector para una CA de Microsoft y una CA de Symantec, primero debe completar la configuración de Intune Certificate Connector para la CA de Microsoft y, luego, seguir estos pasos para configurarlo para la CA de Symantec.  Para obtener más información sobre cómo configurar Intune Certificate Connector para una entidad de certificación de Microsoft, vea [Configuración de certificados en Microsoft Intune](certificates-configure.md).

## <a name="prepare-to-install-intune-certificate-connector"></a>Preparación de la instalación de Intune Certificate Connector

Si ya usa Intune Certificate Connector para una CA de Microsoft existente y desea agregar compatibilidad con una CA de Symantec, omita este paso y siga los pasos restantes después de instalar la versión más reciente de Intune Certificate Connector del portal de administración de Intune. Este paso solo es necesario cuando desea usar Intune Certificate Connector para una CA de Symantec independiente.

1. Elija una de las versiones del sistema operativo Windows en la lista siguiente e instálela en un equipo:
   * Windows Server 2012 R2 Datacenter
   * Windows Server 2012 R2 Standard
   * Windows Server 2016 Datacenter
   * Windows Server 2016 Standard

2. Cree un usuario con privilegios administrativos y úselo para completar los pasos siguientes.

3. Revise las actualizaciones más recientes de Windows Update e instálelas si están disponibles.

   > [!IMPORTANT]
   > Después de instalarlas, reinicie el equipo.

4. Instale .NET Framework 3.5:

    a. Abra **Panel de control** > **Programas y características** > **Activar o desactivar las características de Windows**

    b. Seleccione **.NET Framework 3.5** e instálelo.

## <a name="install-the-symantec-registration-authorization-certificate"></a>Instalación del certificado de autorización de registro de Symantec

Use estos pasos para obtener el certificado de autorización de registro (RA) desde la CA de Symantec. Debe tener una suscripción activa a la CA de Symantec para obtener el certificado de RA.

1. Guarde el fragmento de código siguiente en un archivo denominado **certreq.ini** y actualícelo según corresponda (por ejemplo: *el nombre del firmante en formato CN*).

   ```
    [Version] 
    Signature="$Windows NT$" 

    [NewRequest] 
    ;Change to your,country code, company name and common name 
    Subject = "Subject Name in CN format"

    KeySpec = 1 
    KeyLength = 2048 
    Exportable = TRUE 
    MachineKeySet = TRUE 
    SMIME = False 
    PrivateKeyArchive = FALSE 
    UserProtected = FALSE 
    UseExistingKeySet = FALSE 
    ProviderName = "Microsoft RSA SChannel Cryptographic Provider" 
    ProviderType = 12 
    RequestType = PKCS10 
    KeyUsage = 0xa0 

    [EnhancedKeyUsageExtension] 
    OID=1.3.6.1.5.5.7.3.2 ; Client Authentication  // Uncomment if you need a mutual TLS authentication

    ;----------------------------------------------- 
   ```

2. Abra un símbolo del sistema con privilegios elevados y genere contenido CSR con el comando siguiente:

   `Certreq.exe -new certreq.ini request.csr`

3. Abra el archivo request.csr en el Bloc de notas y copie el contenido CSR con el formato siguiente:

    ```
    -----BEGIN NEW CERTIFICATE REQUEST-----
    MIID8TCCAtkCAQAwbTEMMAoGA1UEBhMDVVNBMQswCQYDVQQIDAJXQTEQMA4GA1UE
    …
    …
    fzpeAWo=
    -----END NEW CERTIFICATE REQUEST-----
    ```

4. Inicie sesión en la CA de Symantec y navegue a **Get an RA Cert** (Obtener un certificado de RA) desde las tareas.

   a. Proporcione el contenido CSR del paso 3 en el cuadro de texto designado.

   b. Proporcione el nombre descriptivo del certificado en el cuadro de texto designado.

   c. Haga clic en **Continue**.

      Se muestra un vínculo descargable para el certificado de RA.

   d. Descargue el certificado de RA en el equipo local.

5. Importe el certificado de RA en el almacén de certificados de Windows:

    a. Abra una consola de MMC.

    b. Haga clic en **Archivo** > **Agregar o quitar complementos** > **Certificado** > y haga clic en **Agregar**.

    c. Seleccione **Cuenta de equipo** > y haga clic en **Siguiente**.

    d. Seleccione **Equipo local** > y haga clic en **Finalizar**.

    e. Haga clic en **Aceptar** en la ventana **Agregar o quitar complementos**. Expanda **Certificados (equipo local)** > **Personal** > **Certificados**.

    f. Haga clic con el botón derecho en el nodo **Certificados** y seleccione **Todas las tareas** > **Importar**.

    g. Seleccione la ubicación del certificado de RA que descargó de la CA de Symantec y haga clic en **Siguiente**.

    h. Seleccione **Almacén de certificados personales** y haga clic en **Siguiente**.

    i. Haga clic en **Finalizar**. Con esto se importa el certificado de RA en el almacén personal de la máquina local junto con su clave privada.  

6. Exporte e importe el certificado de clave privada:

    a. Expanda **Certificados (máquina local)** > **Personal** > **Certificados**.

    b. Seleccione el certificado que se importó en el paso anterior.

    c. Haga clic con el botón derecho en el certificado y elija **Todas las tareas** > **Exportar**.

    d. Haga clic en **Siguiente** y escriba la contraseña.

    e. Seleccione la ubicación de la exportación y haga clic en **Finalizar**.

    f. Siga el mismo procedimiento del paso 5 para importar el certificado de clave privada en el almacén personal del equipo local.

7. Copie la huella digital del certificado de RA sin ningún espacio.  Observe la huella digital de ejemplo:

   ```
   RA Cert Thumbprint: “EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5”
   ```


   > [!NOTE]
   > Si existe algún problema para obtener el certificado de RA desde la CA de Symantec, póngase en contacto con la asistencia al cliente de Symantec.

## <a name="install-intune-certificate-connector"></a>Instalación de Intune Certificate Connector

Si ya usa la versión más reciente de Intune Certificate Connector para una CA de Microsoft existente y desea agregar la compatibilidad de la CA de Symantec, omita este paso. En caso contrario, descargue la versión más recientes de Intune Certificate Connector del portal de administración de Intune y siga estas instrucciones.

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, seleccione **Configuración del dispositivo**.
4. En el panel **Configuración del dispositivo**, seleccione **Entidad de certificación**.
5. Haga clic en **Agregar** y seleccione **Descargue el archivo del conector**. Guarde la descarga en una ubicación a la que pueda acceder desde el servidor donde vaya a realizar la instalación. 
3. Ejecute NDESConnectorSetup.exe con privilegios elevados.

    a. En la pantalla **Opciones de instalación**, seleccione **Distribución .PFX** como se muestra en la captura de pantalla siguiente.  Complete el resto de la configuración con las selecciones predeterminadas.

   > [!IMPORTANT]
   > Si desea configurar Intune Certificate Connector para emitir certificados desde una CA de Microsoft y una CA de Symantec, seleccione **Distribución de perfiles de SCEP y PFX**. Complete el resto de la configuración con las selecciones predeterminadas.

   ![InstallConnector][InstallConnector]
 
## <a name="configure-intune-certificate-connector"></a>Configuración de Intune Certificate Connector

De manera predeterminada, Intune Certificate Connector está instalado en `%ProgramFiles%\Microsoft Intune`.

1. Abra el archivo %ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config en el Bloc de notas.

    a. Actualice el valor de clave RACertThumbprint con el valor de huella digital de certificado que copió en la sección anterior.  Observe el siguiente ejemplo:

   ```
   <add key="RACertThumbprint"
   value="EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5"/>
   ```

    b. Guarde y cierre el archivo.

2. Abra services.msc.

    a. Seleccione **Intune Connector Service**.

    b. Detenga el servicio y, luego, inícielo.

    c. Cierre la ventana Servicios.

## <a name="setup-the-intune-administrator-account"></a>Configuración de la cuenta de administrador de Intune

Si ya usa Intune Certificate Connector para una CA de Microsoft existente y desea agregar la compatibilidad de la CA de Symantec, omita este paso y siga con el resto. 

1. Inicie la interfaz de usuario del conector NDES de ` %ProgramFiles%\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe `

    a. Haga clic en la pestaña **Inscripción** y haga clic en **Iniciar sesión**.

    b. Proporcione las credenciales de administrador del inquilino de Intune en los cuadros de texto designados.

    c. Haga clic en **Iniciar sesión**.  Aparecerá un cuadro de diálogo de confirmación con un mensaje de **inscripción correcta** como se muestra en la captura de pantalla siguiente.
2. Cierre la interfaz de usuario del conector NDES.

![ConfigureConnector][ConfigureConnector]
 
## <a name="create-a-trusted-certificate-profile"></a>Creación de un perfil de certificado de confianza

Los certificados PKCS implementados para los dispositivos administrados por Intune deben estar encadenados con un certificado raíz de confianza. Para esto, debe crear un perfil de certificado de confianza de Intune con el certificado raíz obtenido de la CA de Symantec.

1. Obtenga un certificado raíz de confianza de la CA de Symantec:

    a. Inicie sesión en el portal de administración de la CA de Symantec.

    b. Haga clic en Manage CAs (Administrar CA) desde las tareas:

    c. Seleccione la CA adecuada en la lista de CA.

    d. Haga clic en Download root certificate (Descargar el certificado raíz) para descargar el certificado raíz de confianza.

2. Cree un perfil de certificado de confianza en el portal de administración de Intune:

    a. Inicie sesión en [Azure Portal](https://portal.azure.com) con las credenciales de administrador del inquilino de Intune y busque los recursos de Intune.

    b. Cree un perfil de certificado de confianza en **Microsoft Intune** > **Configuración de dispositivos** > **Perfiles** > **Crear perfil**.

    c. Proporcione la información necesaria en los campos **Nombre** y **Descripción** y, luego, seleccione la plataforma de destino. 

    d. Seleccione el perfil de certificado de confianza en la lista desplegable de tipos de perfil.

    e. Cargue el certificado raíz de confianza que obtuvo de la CA de Symantec en el paso anterior.

    f. Complete el resto de los pasos de la creación de perfiles. 

    g. Haga clic en **Asignaciones** y seleccione el grupo correspondiente.  Al menos un usuario o dispositivo debe ser parte del grupo asignado.

## <a name="get-the-certificate-profile-oid"></a>Obtención del OID del perfil de certificado

El OID del perfil de certificado está asociado con una plantilla de perfil de certificado en la CA de Symantec.  Para crear un perfil de certificado PKCS en el portal de administración de Intune, el nombre de la plantilla de certificado se debe proporcionar en forma de un OID de perfil de certificado que está asociado con una plantilla de certificado en la CA de Symantec.

1. Inicie sesión en el portal de administración de la CA de Symantec.
2. Haga clic en Manage Certificate Profiles (Administrar perfiles de certificado).
3. Seleccione el perfil de certificado que desea usar.
4. Copie el OID del perfil de certificado. Es similar al ejemplo siguiente:

   ```
   Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109 
   ```

   > [!NOTE]
   > Si existe algún problema para obtener el OID del perfil de certificado, póngase en contacto con la asistencia al cliente de Symantec.

## <a name="create-a-pkcs-certificate-profile"></a>Creación de un perfil de certificado PKCS

1. Inicie sesión en [Azure Portal](https://portal.azure.com) con las credenciales de administrador del inquilino de Intune y busque los recursos de Intune.
2. Cree un perfil de certificado PKCS en **Microsoft Intune** > **Configuración de dispositivos > Perfiles** > **Crear perfil**.

    a. Proporcione la información necesaria en los campos **Nombre** y **Descripción** y, luego, seleccione la plataforma de destino.

    b. Seleccione el **perfil de certificado PKCS** en la lista desplegable de **tipos de perfil**.  

    c. Complete el resto de los pasos para crear el perfil.

   ![ConfigureProfile][ConfigureProfile]

   > [!IMPORTANT]
   > Los parámetros siguientes del perfil de certificado PKCS se deben configurar con los valores especificados en la siguiente tabla, tal como se muestra en la captura de pantalla para emitir los certificados PKCS mediante Intune Certificate Connector desde la CA de Symantec. 

    |Parámetro de certificado PKCS | Valor | Descripción |
    | --- | --- | --- |
    | Entidad de certificación | pki-ws.symauth.com | Este valor debe ser el FQDN del servicio de base de la CA de Symantec sin las barras diagonales finales.  Si no está seguro de si se trata del FQDN del servicio de base correcto de la suscripción de la CA de Symantec, póngase en contacto con la asistencia al cliente de Symantec. <br><br> Si este FQDN no es correcto, Intune Certificate Connector no emitirá los certificados PKCS desde la CA de Symantec.| 
    | Nombre de la entidad de certificación | Symantec | Este valor debe ser la cadena **Symantec**. <br><br> Si hay algún cambio en este valor, Intune Certificate Connector no emitirá los certificados PKCS desde la CA de Symantec.|
    | Nombre de plantilla de certificado | OID del perfil de certificado de la CA de Symantec. <br><br> Ejemplo: `2.16.840.1.113733.1.16.1.2.3.1.1.61904612`| Este valor debe ser un OID del perfil de certificado que se obtuvo en la sección anterior desde la plantilla del perfil de certificado de la CA de Symantec. <br><br> Si Intune Certificate Connector no puede encontrar una plantilla de certificado asociada con este OID del perfil de certificado en la CA de Symantec, no emitirá los certificados PKCS desde la CA de Symantec.|

   > [!NOTE]
   > No es necesario que los perfiles de certificado PKCS para las plataformas Windows estén asociados con un perfil de certificado de confianza. Sin embargo, sí es necesario para los perfiles de plataformas distintas de Windows, como Android.

3. Haga clic en **Asignaciones** y seleccione el grupo correspondiente.  Al menos un usuario o dispositivo debe ser parte del grupo asignado.
 
Después de completar los pasos anteriores, Intune Certificate Connector emitirá los certificados PKCS desde la CA de Symantec a los dispositivos administrados de Intune en el grupo asignado. Estos certificados estarán disponibles en el almacén personal del almacén de certificados del usuario actual en el dispositivo administrado de Intune.

### <a name="pkcs-certificate-profile-supported-attributes"></a>Atributos compatibles con el perfil de certificado PKCS

|Atributo | Formatos compatibles con Intune | Formatos compatibles con la CA en la nube de Symantec | Result |
| --- | --- | --- | --- |
| Nombre del firmante |Intune admite el nombre del firmante solo en los tres formatos siguientes: <br><br> 1. Nombre común <br> 2. Nombre común, incluido correo electrónico <br> 3. Nombre común como correo electrónico <br><br> Observe el siguiente ejemplo: <br><br> `CN = IWUser0 <br><br> E = IWUser0@samplendes.onmicrosoft.com` | La CA de Symantec admite atributos adicionales.  Si desea seleccionar atributos adicionales, se deben definir con valores fijos en la plantilla de perfil de certificado de Symantec.| Usamos el nombre común o el correo electrónico de la solicitud de certificado PKCS. <br><br> Cualquier error de coincidencia en la selección de los atributos entre el perfil de certificado de Intune y la plantilla de perfil de certificado de Symantec generará que no se emita ningún certificado desde la CA de Symantec.|
| SAN | Intune solo admite los valores de campo de SAN siguientes: <br><br> AltNameTypeEmail <br><br> AltNameTypeUpn <br><br> AltNameTypeOtherName (valor codificado) | La CA en la nube de Symantec también admite estos parámetros. Si desea seleccionar atributos adicionales, se deben definir con valores fijos en la plantilla de perfil de certificado de Symantec. <br><br> AltNameTypeEmail: si este tipo no se encuentra en SAN, usa el valor de AltNameTypeUpn.  Si tampoco se encuentra AltNameTypeUpn en SAN, usa el valor del nombre del firmante si tiene el formato de correo electrónico.  Si todavía no se encuentra, Intune Certificate Connector no puede emitir los certificados. <br><br> Ejemplo: `RFC822 Name=IWUser0@ndesvenkatb.onmicrosoft.com`  <br><br> AltNameTypeUpn: si este tipo no se encuentra en SAN, usa el valor de AltNameTypeEmail. Si tampoco se encuentra AltNameTypeEmail en SAN, usa el valor del nombre del firmante si tiene el formato de correo electrónico.  Si todavía no se encuentra, Intune Certificate Connector no puede emitir los certificados.  <br><br> Ejemplo: `Other Name: Principal Name=IWUser0@ndesvenkatb.onmicrosoft.com` <br><br> AltNameTypeOtherName: si este tipo no se encuentra en SAN, Intune Certificate Connector no puede emitir los certificados. <br><br> Ejemplo: `Other Name: DS Object Guid=04 12 b8 ba 65 41 f2 d4 07 41 a9 f7 47 08 f3 e4 28 5c ef 2c` <br><br>  **Nota importante:** La CA de Symantec solo admite el valor de este campo en formato codificado (valor hexadecimal). Por lo tanto, para cualquier valor de este campo, Intune Certificate Connector lo codifica en Base 64 antes de enviar la solicitud de certificado. **Intune Certificate Connector no valida si este valor ya está codificado o no.** | Ninguno |

## <a name="troubleshooting"></a>Solucionar problemas

Los registros de servicio de Intune Certificate Connector están disponibles en `%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\Logs\Logs` en la máquina del conector NDES. Abra los registros en [SvcTraceViewer](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) y busque mensajes de excepción o de error.

| Mensaje de emisión o error | Pasos de resolución |
| --- | --- |
| No se puede iniciar sesión con la cuenta de administración del inquilino de Intune en la interfaz de usuario del conector NDES | Esto puede ocurrir cuando la instancia de Certificate Connector local no está habilitada en el portal de administración de Intune. Para resolver este problema, use los siguientes pasos: <br><br> Desde la interfaz de usuario de Silverlight: <br> 1. Inicie sesión en el [portal de administración de Intune](https://admin.manage.microsoft.com) <br> 2. Haga clic en ADMIN <br> 3. Seleccione Administración de dispositivos móviles > Certificate Connector <br> 4. Haga clic en **Configurar Certificate Connector local** <br> 5. Active la casilla **Habilitar Certificate Connector** <br> 6. Haga clic en **Aceptar**. <br><br>O bien, <br><br> Desde la interfaz de usuario de Azure Portal: <br> 1. Inicie sesión en [Azure Portal](https://portal.azure.com) <br> 2. Vaya a Microsoft Intune <br> 3. Seleccione **Configuración de dispositivos** > **Entidad de certificación** <br> 4. Haga clic en **Habilitar**. <br><br> Después de completar los pasos anteriores desde la interfaz de usuario de Silverlight o en Azure Portal, intente iniciar sesión con la misma cuenta de administrador del inquilino de Intune en la interfaz de usuario del conector NDES. |
| No se encontró el certificado del conector NDES. <br><br> System.ArgumentNullException: el valor no puede ser nulo. | Intune Certificate Connector muestra este error si la cuenta de administrador del inquilino de Intune nunca inició sesión en la interfaz de usuario del conector NDES. <br><br> Si este error persiste, reinicie Intune Service Connector. <br><br> 1. Abra services.msc <br> 2. Seleccione **Intune Connector Service**. <br> 3. Haga clic con el botón derecho y seleccione **Reiniciar**.|
| Conector NDES: IssuePfx - Excepción genérica: <br> System.NullReferenceException: referencia de objeto no definida a una instancia de un objeto. | Este error es transitorio. Reinicie Intune Service Connector. <br><br> 1. Abra services.msc <br> 2. Seleccione **Intune Connector Service** <br> 3. Haga clic con el botón derecho y seleccione **Reiniciar**. |
| Proveedor de Symantec: No se pudo obtener la directiva de Symantec "Se agotó el tiempo de espera de la operación" | Intune Certificate Connector recibió un error de tiempo de espera agotado de la operación al comunicarse con la CA de Symantec. Si este error persiste, aumente el valor de tiempo de espera de la conexión y vuelva a intentarlo. <br><br> Para aumentar el tiempo de espera de la conexión: <br> 1. Vaya al equipo del conector NDES. <br>2. Abra el archivo `%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config` en el Bloc de notas. <br> 3. Aumente el valor de tiempo de espera para el parámetro siguiente: <br><br> `CloudCAConnTimeoutInMilliseconds` <br><br> 4. Reinicie Intune Connector Service. <br><br> Si el problema persiste, póngase en contacto con la asistencia al cliente de Symantec. |
| Proveedor de Symantec: No se pudo obtener el certificado de cliente | Intune Certificate Connector no pudo recuperar el certificado de autorización de recursos desde el almacén de certificados personales de la máquina local. Para resolver este problema, asegúrese de instalar el certificado de autorización de recursos en el almacén de certificados personales de la máquina local junto con su clave privada. <br><br> **Nota:** El certificado de autorización de recursos se debe obtener desde la CA de Symantec. Para más detalles, póngase en contacto con la asistencia al cliente de Symantec. | 
| Proveedor de Symantec: No se pudo obtener la directiva de Symantec "La solicitud se anuló: no se pudo crear el canal seguro SSL/TLS". | Este error se produce en los siguientes escenarios: <br><br> 1. El servicio de Intune Certificate Connector no tiene los permisos suficientes para leer el certificado de autorización de recursos junto con su clave privada desde el almacén de certificados personales de la máquina local. Para resolver este problema, revise el servicio Connector que ejecuta la cuenta de contexto en services.msc. El servicio Connector debe ejecutarse en el contexto de NT AUTHORITY\SYSTEM. <br><br> 2. El perfil de certificado PKCS en el portal de administración de Intune puede estar configurado con un nombre de dominio completo del servicio de base de la CA de Symantec no válido. El nombre de dominio completo es similar a `pki-ws.symauth.com`. Para resolver este problema, consulte con la atención al cliente de Symantec si la dirección URL es correcta para la suscripción. <br><br> 3. Intune Certificate Connector no puede realizar la autenticación con la CA de Symantec mediante el certificado de autorización de recursos porque no puede recuperar su clave privada. Para resolver este problema, asegúrese de instalar el certificado de autorización de recursos junto con su clave privada en el almacén de certificados personales de la máquina local. <br><br> Si el problema persiste, póngase en contacto con la asistencia al cliente de Symantec. |
| Proveedor de Symantec: No se pudo obtener la directiva de Symantec "No se entiende un elemento de solicitud". | Intune Certificate Connector no pudo obtener la plantilla de perfil del certificado de Symantec, porque el OID del perfil de cliente no coincide con el perfil del certificado de Intune. En otro caso, Intune Certificate Connector no puede encontrar la plantilla de perfil del certificado que está asociada con el OID del perfil de cliente determinado en la CA de Symantec. <br><br> Para resolver este problema, asegúrese de obtener el OID de perfil de cliente correcto de la plantilla de certificado de Symantec en la entidad de certificación de Symantec. Después, actualice el perfil de certificado PKCS en el portal de administración de Intune. <br><br> Obtenga el OID del perfil de cliente desde la CA de Symantec: <br> 1. Inicie sesión en el portal de administración de la CA de Symantec. <br> 2. Haga clic en Manage Certificate Profiles (Administrar perfiles de certificado). <br> 3. Seleccione el perfil de certificado que intenta usar. <br> 4. Obtenga el OID del perfil de certificado. Es similar al ejemplo siguiente: <br> `Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109` <br><br> Actualice el perfil del certificado PKCS con el OID del perfil de certificado correcto: <br>1. Inicie sesión en el portal de administración de Intune <br> 2. Vaya al perfil de certificado PKCS y haga clic en **Editar**. <br> 3. Actualice el OID del perfil de certificado en el campo de nombre de la plantilla de certificado. <br> 4. Guarde el perfil de certificado PKCS. |
| Proveedor de Symanted: Error de comprobación de directiva. <br><br> El atributo no pertenece a la lista de atributos de plantilla de certificados compatibles con Symantec | La CA de Symantec muestra este mensaje cuando hay una discrepancia entre la plantilla del perfil de certificado de Symantec y el perfil de certificado de Intune. Es probable que este problema se deba a un error de coincidencia de atributos en SubjectName o en SubjectAltName. <br><br> Para resolver este problema, asegúrese de seleccionar los atributos compatibles con Intune para SubjectName y SubjectAltName en la plantilla del perfil de certificado de Symantec. Para más información, consulte los atributos compatibles con Intune en la sección Parámetros de certificado. |
| Algunos dispositivos de usuario no reciben los certificados PKCS desde la CA de Symantec. | Este problema se produce cuando el UPN de usuario contiene caracteres especiales como guion bajo (ejemplo: `global_admin@intune.onmicrosoft.com`). <br><br> La CA de Symantec no admite caracteres especiales en mail_firstname y mail_lastname. <br><br> Los pasos siguientes ayudan a resolver este problema: <br><br> 1.   Inicie sesión en el portal de administración de la CA de Symantec. <br> 2. Vaya a Manage Certificate Profiles (Administrar perfiles de certificado). <br> 3.   Haga clic en el perfil de certificado que se usa para Intune. <br> 4.  Haga clic en el vínculo para personalizar opciones. <br> 5.   Haga clic en el botón de las opciones avanzadas. <br> 6.  En los campos del certificado – Subject DN, agregue el campo Nombre común (CN) y elimine el campo Nombre común (CN) existente. Las operaciones para agregar y eliminar se deben realizar en conjunto. <br> 7.    Haga clic en Guardar. <br><br> Con el campo anterior, el perfil de certificado de Symantec solicita "CN=<upn>" en lugar de mail_firstname y mail_lastname. |
| El usuario eliminó manualmente un certificado ya implementado desde el dispositivo. | Intune vuelve a implementar el mismo certificado durante la siguiente comprobación o aplicación de la directiva. En este caso, el conector NDES no recibe una solicitud de certificado PKCS. |

## <a name="next-steps"></a>Pasos siguientes

- Use la información de este artículo junto con la información que aparece en [¿Qué son los perfiles de dispositivo de Microsoft Intune?](device-profiles.md) para administrar los dispositivos de la organización y los certificados que incluyen.

[InstallConnector]:  ./media/certificates-symantec-connector-install.png "Instalación de Intune Certificate Connector y selección de la distribución .PFX"
[ConfigureConnector]: ./media/certificates-symantec-configure-connector-configure.png "Configuración de Intune Certificate Connector"
[ConfigureProfile]: ./media/certificates-symantec-pkcs-example.png "Creación del perfil de certificado PKCS en Azure Portal"
