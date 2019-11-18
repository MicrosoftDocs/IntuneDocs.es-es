---
title: Emisión de certificados PKCS de DigiCert con Microsoft Intune
titleSuffix: Microsoft Intune
description: Instale y configure Intune Certificate Connector para emitir certificados PKCS desde la plataforma de PKI de DigiCert a los dispositivos administrados por Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ca76ffe0c8fa42f1c2cf24fcdefd287140231220
ms.sourcegitcommit: b5e719fb507b1bc4774674e76c856c435e69f68c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/08/2019
ms.locfileid: "73801646"
---
# <a name="set-up-intune-certificate-connector-for-digicert-pki-platform"></a>Configuración de Intune Certificate Connector para la plataforma de PKI de DigiCert

Use Intune Certificate Connector para emitir certificados PKCS desde la plataforma de PKI de DigiCert a los dispositivos administrados por Intune. Puede usar el conector solo con una entidad de certificación (CA) de DigiCert o con una CA de DigiCert y otra de Microsoft.

> [!TIP]
> DigiCert adquirió Website Security de Symantec y la empresa PKI Solutions relacionada. Para obtener más información sobre este cambio, consulte el [artículo de soporte técnico de Symantec](https://support.symantec.com/en_US/article.INFO4722.html).

Si ya usa Intune Certificate Connector para emitir certificados desde una CA de Microsoft mediante PKCS o System Center Endpoint Protection, puede utilizar ese mismo conector para configurar y emitir certificados PKCS desde una CA de DigiCert. Una vez que complete la configuración para admitir la CA de DigiCert, Intune Certificate Connector puede emitir los siguientes certificados:

* Certificados PKCS desde una CA de Microsoft
* Certificados PKCS desde una CA de DigiCert
* Certificados Endpoint Protection desde una CA de Microsoft

Si no tiene el conector instalado, pero tiene previsto usarlo tanto para una CA de Microsoft como para una CA de DigiCert, complete la configuración del conector para la CA de Microsoft en primer lugar. A continuación, vuelva a este artículo para configurarlo de modo que también admita DigiCert. Para obtener más información sobre los perfiles de certificado y el conector, consulte [Configuración de un perfil de certificado para sus dispositivos en Microsoft Intune](certificates-configure.md).  

Si va a usar el conector solo con la CA de DigiCert, puede utilizar las instrucciones de este artículo para instalar y, a continuación, configurar el conector.

## <a name="prerequisites"></a>Requisitos previos

- **Una suscripción activa en la CA de DigiCert**: la suscripción es necesaria para obtener un certificado de entidad de registro (RA) desde el CA de DigiCert.

## <a name="install-the-digicert-ra-certificate"></a>Instalación del certificado de RA de DigiCert

1. Guarde el fragmento de código siguiente en un archivo denominado **certreq.ini** y actualícelo según corresponda (por ejemplo: *el nombre del firmante en formato CN*).

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

2. Abra un símbolo del sistema con privilegios elevados y genere una solicitud de firma de certificado (CSR) con el comando siguiente:

   `Certreq.exe -new certreq.ini request.csr`

3. Abra el archivo request.csr en el Bloc de notas y copie el contenido CSR con el formato siguiente:

        -----BEGIN NEW CERTIFICATE REQUEST-----
        MIID8TCCAtkCAQAwbTEMMAoGA1UEBhMDVVNBMQswCQYDVQQIDAJXQTEQMA4GA1UE
        …
        …
        fzpeAWo=
        -----END NEW CERTIFICATE REQUEST-----


4. Inicie sesión en la CA de DigiCert y vaya a **Obtener certificado RA** en las tareas.

   a. En el cuadro de texto, proporcione el contenido CSR del paso 3.

   b. Proporcione un nombre descriptivo del certificado.

   c. Seleccione **Continuar**.

   d. Use el vínculo proporcionado para descargar el certificado de RA en el equipo local.

5. Importe el certificado de RA en el almacén de certificados de Windows:

   a. Abra una consola de MMC.

   b. Seleccione **Archivo** > **Agregar o quitar complementos** > **Certificado** > **Agregar**.

   c. Seleccione **Cuenta de equipo** > **Siguiente**.

   d. Seleccione **Equipo local** > **Finalizar**.

   e. Seleccione **Aceptar** en la ventana **Agregar o quitar complementos**. Expanda **Certificados (equipo local)**  > **Personal** > **Certificados**.

   f. Haga clic con el botón derecho en el nodo **Certificados** y seleccione **Todas las tareas** > **Importar**.

   g. Seleccione la ubicación del certificado de RA que descargó de la CA de DigiCert y, a continuación, seleccione **Siguiente**.

   h. Seleccione **Almacén de certificados personal** > **Siguiente**.

   i. Seleccione **Finalizar** para importar el certificado de RA y su clave privada en el almacén **personal de la máquina local**.

6. Exporte e importe el certificado de clave privada:

   a. Expanda **Certificados (máquina local)**  > **Personal** > **Certificados**.

   b. Seleccione el certificado que se importó en el paso anterior.

   c. Haga clic con el botón derecho en el certificado y seleccione **Todas las tareas** > **Exportar**.

   d. Seleccione **Siguiente** y, a continuación, escriba la contraseña.

   e. Seleccione la ubicación de la exportación y, a continuación, seleccione **Finalizar**.

   f. Use el procedimiento del paso 5 para importar el certificado de clave privada en el almacén **personal del equipo local**.

   g. Registre una copia de la huella digital del certificado de RA sin ningún espacio. Observe la huella digital de ejemplo:

        RA Cert Thumbprint: “EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5”

    > [!NOTE]
    > Para recibir ayuda a la hora de obtener el certificado de RA de la CA de DigiCert, póngase en contacto con la [asistencia al cliente de DigiCert](mailto:enterprise-pkisupport@digicert.com).

## <a name="prepare-to-install-intune-certificate-connector"></a>Preparación de la instalación de Intune Certificate Connector

> [!TIP]
> Esta sección se aplica si va a usar Intune Certificate Connector solo con una CA de DigiCert. Si usa Intune Certificate Connector con una CA de Microsoft y desea agregar compatibilidad con la CA de DigiCert, vaya directamente a la sección sobre cómo [configurar el conector para admitir DigiCert](#configure-the-connector-to-support-digicert).

1. Elija una de las versiones del sistema operativo Windows en la lista siguiente e instálela en un equipo:
   * Windows Server 2012 R2 Datacenter
   * Windows Server 2012 R2 Standard
   * Windows Server 2016 Datacenter
   * Windows Server 2016 Standard

2. Cree un usuario con privilegios administrativos y úselo para completar los pasos siguientes.

3. Compruebe las actualizaciones más recientes de Windows Update e instálelas si están disponibles. Después de instalarlas, reinicie el equipo.

4. Instale .NET Framework 3.5:

   a. Abra **Panel de control** > **Programas y características** > **Activar o desactivar las características de Windows**.

   b. Seleccione **.NET Framework 3.5** e instálelo.

## <a name="install-intune-certificate-connector-for-use-with-digicert"></a>Instalación de Intune Certificate Connector para su uso con DigiCert

> [!TIP]
> Si usa Intune Certificate Connector con una CA de Microsoft y desea agregar compatibilidad con la CA de DigiCert, vaya directamente a la sección sobre cómo [configurar el conector para admitir DigiCert](#configure-the-connector-to-support-digicert).

Descargue la versión más reciente de Intune Certificate Connector del portal de administración de Intune y siga estas instrucciones.

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Seleccione **Administración de inquilinos** > **Conectores y tokens** > **Conectores de certificados** >  **+ Agregar**.

3. Haga clic en *Descargar el software de Certificate Connector* para el conector de PKCS #12 y guarde el archivo en una ubicación a la que pueda acceder desde el servidor en el que va a instalar el conector.

   ![Descarga del software del conector](./media/certificates-digicert-configure/connector-download.png)

4. En el servidor donde desee instalar el conector, ejecute **NDESConnectorSetup.exe** con privilegios elevados.

5. En la página **Opciones de instalación**, seleccione **Distribución PFX**.

   ![Selección de Distribución PFX](./media/certificates-digicert-configure/digicert-ca-connector-install.png)

   > [!IMPORTANT]
   > Si va a usar Intune Certificate Connector para emitir certificados desde una CA de Microsoft y una CA de DigiCert, seleccione **Distribución de perfiles de SCEP y PFX**.

6. Use las selecciones predeterminadas para terminar de configurar el conector.

## <a name="configure-the-connector-to-support-digicert"></a>Configuración del conector para admitir DigiCert

De forma predeterminada, Intune Certificate Connector está instalado en **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc**.

1. En la carpeta **NDESConnectorSvc**, abra el archivo **NDESConnector.exe.config** en el Bloc de notas.

   a. Actualice el valor de clave `RACertThumbprint` con el valor de huella digital de certificado que copió en la sección anterior. Por ejemplo:

        <add key="RACertThumbprint"
        value="EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5"/>

   b. Guarde y cierre el archivo.

2. Abra **services.msc**:

   a. Seleccione **Intune Connector Service**.

   b. Detenga el servicio y, luego, inícielo.

   c. Cierre la ventana del servicio.

## <a name="set-up-the-intune-administrator-account"></a>Configuración de la cuenta de administrador de Intune  

> [!TIP]
> Si usa Intune Certificate Connector con una CA de Microsoft y desea agregar compatibilidad con la CA de DigiCert, vaya directamente a la sección sobre cómo [crear un perfil de certificado de confianza](#create-a-trusted-certificate-profile).
 
1. Abra la interfaz de usuario del conector NDES en **%ProgramFiles%\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe**.

2. En la pestaña **Inscripción**, seleccione **Iniciar sesión**.

3. Proporcione las credenciales de administrador del inquilino de Intune.

4. Seleccione **Iniciar sesión** y, a continuación, seleccione **Aceptar** para confirmar una inscripción realizada correctamente. A continuación, puede cerrar la interfaz de usuario del conector NDES.

   ![Interfaz del conector NDES con el mensaje "Correctamente inscrito"](./media/certificates-digicert-configure/certificates-digicert-configure-connector-configure.png)

## <a name="create-a-trusted-certificate-profile"></a>Creación de un perfil de certificado de confianza

Los certificados PKCS que implementará para los dispositivos administrados por Intune deben estar encadenados con un certificado raíz de confianza. Para establecer esta cadena, cree un perfil de certificado de confianza de Intune con el certificado raíz de la CA de DigiCert.

1. Obtenga un certificado raíz de confianza de la CA de DigiCert:

   a. Inicie sesión en el portal de administración de la CA de DigiCert.

   b. Seleccione **Administrar CA** desde las **tareas**.

   c. Seleccione la CA adecuada en la lista.

   d. Seleccione **Descargar el certificado raíz** para descargar el certificado raíz de confianza.

2. Cree un perfil de certificado de confianza en el portal de Intune:

   a. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

   b. Seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.

   c. Escriba las propiedades siguientes:

      - **Nombre** del perfil
      - Si lo desea, puede rellenar el campo **Descripción**.
      - **Plataforma** en la cual implementar el perfil
      - Establezca el **tipo del perfil** en **Certificado de confianza**

   d. Seleccione **Configuración** y busque el archivo .cer del certificado de entidad de certificación raíz de confianza que ha exportado para usar con este perfil de certificado y, después, seleccione **Aceptar**.

   e. Solo para dispositivos Windows 8.1 y Windows 10, seleccione el **almacén de destino** del certificado de confianza. Las opciones son:
      - **Almacén de certificados de equipo - Raíz**
      - **Almacén de certificados de equipo - Intermedio**
      - **Almacén de certificados de usuario - Intermedio**

   f. Cuando haya terminado, seleccione **Aceptar**, vuelva al panel **Crear perfil** y seleccione **Crear**.  

  El perfil aparece en la lista de perfiles del panel de vista **Configuración del dispositivo - Perfiles**, con un tipo de perfil de **Certificado de confianza**.  Asegúrese de asignar este perfil a los dispositivos que vayan a recibir certificados. Para asignar el perfil a grupos, consulte [Asignación de perfiles de dispositivo](../configuration/device-profile-assign.md).


## <a name="get-the-certificate-profile-oid"></a>Obtención del OID del perfil de certificado  

El OID del perfil de certificado está asociado con una plantilla de perfil de certificado en la CA de DigiCert. Para crear un perfil de certificado PKCS en Intune, el nombre de la plantilla de certificado debe tener el formato de un OID de perfil de certificado que está asociado con una plantilla de certificado en la CA de DigiCert.

1. Inicie sesión en el portal de administración de la CA de DigiCert.
2. Seleccione **Administrar perfiles de certificado**.
3. Seleccione el perfil de certificado que desea usar.
4. Copie el OID del perfil de certificado. Es similar al ejemplo siguiente:

       Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109 

> [!NOTE]
> Si necesita ayuda para obtener el OID del perfil de certificado, póngase en contacto con la [asistencia al cliente de DigiCert](mailto:enterprise-pkisupport@digicert.com).

## <a name="create-a-pkcs-certificate-profile"></a>Creación de un perfil de certificado PKCS

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.

3. Escriba las propiedades siguientes:

   - **Nombre** del perfil
   - Si lo desea, puede rellenar el campo **Descripción**.
   - **Plataforma** en la cual implementar el perfil
   - Establezca **Tipo del perfil** en **Certificado PKCS**

4. En el panel **Certificado PKCS**, configure los parámetros con los valores de la siguiente tabla. Estos valores son necesarios para emitir certificados PKCS desde una CA de DigiCert, a través de Intune Certificate Connector.

   |Parámetro de certificado PKCS | Valor | Descripción |
   | --- | --- | --- |
   | Entidad de certificación | pki-ws.symauth.com | Este valor debe ser el FQDN del servicio de base de la CA de DigiCert sin las barras diagonales finales. Si no está seguro de si se trata del FQDN del servicio de base correcto de la suscripción de la CA de DigiCert, póngase en contacto con la asistencia al cliente de DigiCert. <br><br>*Con el cambio de Symantec a DigiCert, esta dirección URL permanece sin cambios*. <br><br> Si este FQDN no es correcto, Intune Certificate Connector no emitirá los certificados PKCS desde la CA de DigiCert.| 
   | Nombre de la entidad de certificación | Symantec | Este valor debe ser la cadena **Symantec**. <br><br> Si hay algún cambio en este valor, Intune Certificate Connector no emitirá los certificados PKCS desde la CA de DigiCert.|
   | Nombre de plantilla de certificado | OID del perfil de certificado de la CA de DigiCert. Por ejemplo: **2.16.840.1.113733.1.16.1.2.3.1.1.61904612**| Este valor debe ser un OID del perfil de certificado [que se obtuvo en la sección anterior](#get-the-certificate-profile-oid) desde la plantilla del perfil de certificado de la CA de DigiCert. <br><br> Si Intune Certificate Connector no puede encontrar una plantilla de certificado asociada a este OID del perfil de certificado en la CA de DigiCert, no emitirá los certificados PKCS desde la CA de DigiCert.|

   ![Selecciones correspondientes a la plantilla de certificado y la CA](./media/certificates-digicert-configure/certificates-digicert-pkcs-example.png)

   > [!NOTE]
   > No es necesario que el perfil de certificado PKCS para las plataformas Windows esté asociado a un perfil de certificado de confianza. Sin embargo, sí es necesario para los perfiles de plataformas distintas de Windows, como Android.

5. Complete la configuración del perfil para satisfacer sus necesidades empresariales y, luego, seleccione **Crear** para guardar el perfil.

6. En la página *Información general* del nuevo perfil, seleccione **Asignaciones** y configure un grupo adecuado que recibirá este perfil. Al menos un usuario o dispositivo debe ser parte del grupo asignado.
 
Después de completar los pasos anteriores, Intune Certificate Connector emitirá certificados PKCS desde la CA de DigiCert a los dispositivos administrados por Intune en el grupo asignado. Estos certificados estarán disponibles en el almacén **personal** del almacén de certificados del **usuario actual** en el dispositivo administrado por Intune.

### <a name="supported-attributes-for-the-pkcs-certificate-profile"></a>Atributos compatibles con el perfil de certificado PKCS

|Atributo | Formatos compatibles con Intune | Formatos compatibles con la CA en la nube de DigiCert | result |
| --- | --- | --- | --- |
| Nombre de sujeto |Intune admite el nombre del firmante solo en los tres formatos siguientes: <br><br> 1. Nombre común <br> 2. Nombre común que incluye el correo electrónico <br> 3. Nombre común como correo electrónico <br><br> Por ejemplo: <br><br> `CN = IWUser0 <br><br> E = IWUser0@samplendes.onmicrosoft.com` | La CA de DigiCert admite más atributos.  Si desea seleccionar más atributos, se deben definir con valores fijos en la plantilla de perfil de certificado de DigiCert.| Usamos el nombre común o el correo electrónico de la solicitud de certificado PKCS. <br><br> Cualquier error de coincidencia en la selección de los atributos entre el perfil de certificado de Intune y la plantilla de perfil de certificado de DigiCert generará que no se emita ningún certificado desde la CA de DigiCert.|
| SAN | Intune solo admite los valores de campo de SAN siguientes: <br><br> **AltNameTypeEmail** <br> **AltNameTypeUpn** <br> **AltNameTypeOtherName** (valor codificado) | La CA en la nube de DigiCert también admite estos parámetros. Si desea seleccionar más atributos, se deben definir con valores fijos en la plantilla de perfil de certificado de DigiCert. <br><br> **AltNameTypeEmail**: si este tipo no se encuentra en SAN, Intune Certificate Connector usará el valor de **AltNameTypeUpn**.  Si tampoco se encuentra **AltNameTypeUpn** en SAN, usa el valor del nombre del firmante si tiene el formato de correo electrónico.  Si todavía no se encuentra el tipo, Intune Certificate Connector no puede emitir los certificados. <br><br> Ejemplo: `RFC822 Name=IWUser0@ndesvenkatb.onmicrosoft.com`  <br><br> **AltNameTypeUpn**: si este tipo no se encuentra en SAN, Intune Certificate Connector usará el valor de **AltNameTypeEmail**. Si tampoco se encuentra **AltNameTypeEmail** en SAN, usa el valor del nombre del firmante si tiene el formato de correo electrónico. Si todavía no se encuentra el tipo, Intune Certificate Connector no puede emitir los certificados.  <br><br> Ejemplo: `Other Name: Principal Name=IWUser0@ndesvenkatb.onmicrosoft.com` <br><br> **AltNameTypeOtherName**: si este tipo no se encuentra en SAN, Intune Certificate Connector no puede emitir los certificados. <br><br> Ejemplo: `Other Name: DS Object Guid=04 12 b8 ba 65 41 f2 d4 07 41 a9 f7 47 08 f3 e4 28 5c ef 2c` <br><br>  La entidad de certificación DigiCert solo admite el valor de este campo en formato codificado (valor hexadecimal). Para cualquier valor de este campo, Intune Certificate Connector lo codifica en Base 64 antes de enviar la solicitud de certificado. *Intune Certificate Connector no valida si este valor ya está codificado o no.* | Ninguno |

## <a name="troubleshooting"></a>Solucionar problemas

Los registros del servicio Intune Certificate Connector están disponibles en **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\Logs\Logs** en la máquina del conector NDES. Abra los registros en [SvcTraceViewer](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) y busque mensajes de excepción o de error.

| Mensaje de emisión o error | Pasos de resolución |
| --- | --- |
| No se puede iniciar sesión con la cuenta de administración del inquilino de Intune en la interfaz de usuario del conector NDES. | Esto puede ocurrir cuando el conector de certificado local no está habilitado en el Centro de administración del Administrador de puntos de conexión de Microsoft. Para resolver este problema: <br><br> 1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431). <br> 2. Seleccione **Administración de inquilinos** > **Conectores y tokens** > **Conectores de certificados**. <br> 3. Busque el conector de certificado y asegúrese de que está habilitado. <br><br> Después de completar los pasos anteriores, intente iniciar sesión con la misma cuenta de administrador de inquilinos de Intune en la interfaz de usuario del conector de NDES. |
| No se encontró el certificado del conector NDES. <br><br> System.ArgumentNullException: El valor no puede ser NULL. | Intune Certificate Connector muestra este error si la cuenta de administrador del inquilino de Intune nunca inició sesión en la interfaz de usuario del conector NDES. <br><br> Si este error persiste, reinicie Intune Service Connector. <br><br> 1. Abra **services.msc**. <br> 2. Seleccione **Intune Connector Service**. <br> 3. Haga clic con el botón derecho y seleccione **Reiniciar**.|
| Conector NDES: IssuePfx - Excepción genérica: <br> System.NullReferenceException: Referencia de objeto no establecida en una instancia de un objeto. | Este error es transitorio. Reinicie Intune Service Connector. <br><br> 1. Abra **services.msc**. <br> 2. Seleccione **Intune Connector Service**. <br> 3. Haga clic con el botón derecho y seleccione **Reiniciar**. |
| Proveedor de DigiCert: No se pudo obtener la directiva de DigiCert. <br><br>"La operación ha agotado el tiempo de espera". | Intune Certificate Connector recibió un error de tiempo de espera agotado de la operación al comunicarse con la CA de DigiCert. Si este error persiste, aumente el valor de tiempo de espera de la conexión y vuelva a intentarlo. <br><br> Para aumentar el tiempo de espera de la conexión: <br> 1. Vaya al equipo del conector NDES. <br>2. Abra el archivo **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config** en el Bloc de notas. <br> 3. Aumente el valor de tiempo de espera para el parámetro siguiente: <br><br> `CloudCAConnTimeoutInMilliseconds` <br><br> 4. Reinicie el servicio Intune Certificate Connector. <br><br> Si el problema persiste, póngase en contacto con la asistencia al cliente de DigiCert. |
| Proveedor de DigiCert: No se pudo obtener el certificado de cliente. | Intune Certificate Connector no pudo recuperar el certificado de autorización de recursos desde el almacén de certificados personales de la máquina local. Para resolver este problema, instale el certificado de autorización de recursos en el almacén de certificados personales de la máquina local junto con su clave privada. <br><br> El certificado de autorización de recursos se debe obtener desde la CA de DigiCert. Para más detalles, póngase en contacto con la asistencia al cliente de DigiCert. | 
| Proveedor de DigiCert: No se pudo obtener la directiva de DigiCert. <br><br>"Se anuló la solicitud: no se pudo crear el canal seguro SSL/TLS". | Este error se produce en los siguientes escenarios: <br><br> 1. El servicio Intune Certificate Connector no tiene permisos para leer el certificado de autorización de recursos junto con su clave privada desde el almacén de certificados personales de la máquina local. Para resolver este problema, revise la cuenta de contexto en ejecución del servicio Connector en services.msc. El servicio Connector debe ejecutarse en el contexto de NT AUTHORITY\SYSTEM. <br><br> 2. El perfil de certificado PKCS en el portal de administración de Intune puede estar configurado con un nombre de dominio completo del servicio de base de la CA de DigiCert no válido. El nombre de dominio completo es similar a **pki-ws.symauth.com**. Para resolver este problema, consulte con la atención al cliente de DigiCert si la dirección URL es correcta para la suscripción. <br><br> 3. Intune Certificate Connector no puede realizar la autenticación con la CA de DigiCert mediante el certificado de autorización de recursos porque no puede recuperar la clave privada. Para resolver este problema, instale el certificado de autorización de recursos junto con su clave privada en el almacén de certificados personales de la máquina local. <br><br> Si el problema persiste, póngase en contacto con la asistencia al cliente de DigiCert. |
| Proveedor de DigiCert: No se pudo obtener la directiva de DigiCert. <br><br>"No se comprende un elemento de la solicitud". | Intune Certificate Connector no pudo obtener la plantilla de perfil del certificado de DigiCert, porque el OID del perfil de cliente no coincide con el perfil del certificado de Intune. En otro caso, Intune Certificate Connector no puede encontrar la plantilla de perfil del certificado que está asociada con el OID del perfil de cliente en la CA de DigiCert. <br><br> Para resolver este problema, obtenga el OID de perfil de cliente correcto de la plantilla de certificado de DigiCert en la CA de DigiCert. Después, actualice el perfil de certificado PKCS en el portal de administración de Intune. <br><br> Obtenga el OID del perfil de cliente de la CA de DigiCert: <br> 1. Inicie sesión en el portal de administración de la CA de DigiCert. <br> 2. Seleccione **Administrar perfiles de certificado**. <br> 3. Seleccione el perfil de certificado que desea usar. <br> 4. Obtenga el OID del perfil de certificado. Es similar al ejemplo siguiente: <br> `Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109` <br><br> Actualice el perfil del certificado PKCS con el OID del perfil de certificado correcto: <br>1. Inicie sesión en el portal de administración de Intune. <br> 2. Vaya al perfil de certificado PKCS y seleccione **Editar**. <br> 3. Actualice el OID del perfil de certificado en el campo de nombre de la plantilla de certificado. <br> 4. Guarde el perfil de certificado PKCS. |
| Proveedor de DigiCert: Error de comprobación de directiva. <br><br> El atributo no pertenece a la lista de atributos de plantilla de certificados compatibles con DigiCert. | La CA de DigiCert muestra este mensaje cuando hay una discrepancia entre la plantilla del perfil de certificado de DigiCert y el perfil de certificado de Intune. Es probable que este problema se deba a un error de coincidencia de atributos en **SubjectName** o en **SubjectAltName**. <br><br> Para resolver este problema, seleccione los atributos compatibles con Intune para **SubjectName** y **SubjectAltName** en la plantilla del perfil de certificado de DigiCert. Para más información, consulte los atributos compatibles con Intune en la sección **Parámetros de certificado**. |
| Algunos dispositivos de usuario no reciben los certificados PKCS desde la CA de DigiCert. | Este problema se produce cuando el UPN de usuario contiene caracteres especiales como guion bajo (ejemplo: `global_admin@intune.onmicrosoft.com`). <br><br> La CA de DigiCert no admite caracteres especiales en **mail_firstname** y **mail_lastname**. <br><br> Los pasos siguientes ayudan a resolver este problema: <br><br> 1. Inicie sesión en el portal de administración de la CA de DigiCert. <br> 2. Vaya a **Administrar perfiles de certificado**. <br> 3. Seleccione el perfil de certificado que se usa para Intune. <br> 4. Seleccione el vínculo para **personalizar opciones**. <br> 5. Seleccione el botón de las **opciones avanzadas**. <br> 6. En los **campos del certificado – Subject DN**, agregue un campo **Nombre común (CN)** y elimine el campo **Nombre común (CN)** existente. Las operaciones para agregar y eliminar se deben realizar en conjunto. <br> 7. Seleccione **Guardar**. <br><br> Con el campo anterior, el perfil de certificado de DigiCert solicita **“CN=<upn>”** en lugar de **mail_firstname** y **mail_lastname**. |
| El usuario eliminó manualmente un certificado ya implementado desde el dispositivo. | Intune vuelve a implementar el mismo certificado durante la siguiente comprobación o aplicación de la directiva. En este caso, el conector NDES no recibe una solicitud de certificado PKCS. |

## <a name="next-steps"></a>Pasos siguientes

Use la información de este artículo junto con la información que aparece en [¿Qué son los perfiles de dispositivo de Microsoft Intune?](../configuration/device-profiles.md) para administrar los dispositivos de la organización y los certificados que incluyen.
