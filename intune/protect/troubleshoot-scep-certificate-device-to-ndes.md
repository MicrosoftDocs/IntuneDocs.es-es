---
title: Solución de problemas de comunicación entre un dispositivo administrado y NDES en Microsoft Intune | Microsoft Docs
description: Solucione los problemas de comunicación entre un dispositivo administrado y un servidor NDES al usar perfiles de certificado SCEP para implementar certificados con Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/30/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7945f1df3ddf1a6ff2c42a537e1071d1b5acff24
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514275"
---
# <a name="troubleshoot-device-to-ndes-server-communication-for-scep-certificate-profiles-in-microsoft-intune"></a>Solución de problemas de comunicación entre un dispositivo y el servidor NDES para perfiles de certificado SCEP en Microsoft Intune

Use la siguiente información para determinar si un dispositivo que ha recibido y procesado un perfil de certificado del protocolo de inscripción de certificados simple (SCEP) de Intune puede ponerse en contacto correctamente con el servicio de inscripción de dispositivos de red (NDES) para presentar un desafío. En el dispositivo, se genera una clave privada y la solicitud de firma de certificado (CSR) y el desafío se pasan desde el dispositivo al servidor NDES. Para ponerse en contacto con el servidor NDES, el dispositivo usa el URI del perfil de certificado SCEP.

En este artículo se hace referencia al paso 2 de la [información general del flujo de comunicación de SCEP](troubleshoot-scep-certificate-profiles.md).

## <a name="review-iis-logs-for-a-connection-from-the-device"></a>Revisión de los registros de IIS para obtener una conexión desde el dispositivo

Los registros de IIS incluyen el mismo tipo de entradas para todas las plataformas.


1. En el servidor NDES, abra el archivo de registro de IIS más reciente que se encuentra en la siguiente carpeta: *%SystemDrive%\inetpub\logs\logfiles\w3svc1*

2. Busque en el registro entradas similares a las de los ejemplos siguientes. Ambos ejemplos contienen un estado **200**, que aparece cerca del final:

   `fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe operation=GetCACaps&message=default 80 - fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 186 0.`

   And

   `fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe operation=GetCACert&message=default 80 - fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 3567 0`

3. Cuando el dispositivo se pone en contacto con IIS, se registra una solicitud HTTP GET para mscep.dll.

   Revise el código de estado cerca del final de esta solicitud:
   - **Código de estado de 200**: Este estado indica que la conexión con el servidor NDES se ha realizado correctamente.
   - **Código de estado de 500**: Es posible que el grupo de IIS_IURS carezca de los permisos correctos. Vea [Código de estado 500](#status-code-500), más adelante en este artículo.
   - Si el código de estado no es 200 o 500:

     - Consulte [Prueba de la dirección URL del servidor de SCEP](#test-the-scep-server-url) más adelante en este artículo para ayudar a validar la configuración.

     - Consulte [El código de estado HTTP en IIS 7 y versiones posteriores](https://support.microsoft.com/help/943891) para obtener información acerca de los códigos de error menos comunes.

   Si la solicitud de conexión no se registra en ningún caso, es posible que el contacto del dispositivo esté bloqueado en la red entre el dispositivo y el servidor NDES.

## <a name="review-device-logs-for-connections-to-ndes"></a>Revisión de los registros de dispositivos para las conexiones a NDES

### <a name="android-devices"></a>Dispositivos Android

Revise el [registro OMADM de los dispositivos](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices). Busque entradas similares a las siguientes, que se registran cuando el dispositivo se conecta a NDES:

```
2018-02-27T05:16:08.2500000  VERB  Event  com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager  18327    10  There are 1 requests
2018-02-27T05:16:08.2500000  VERB  Event  com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager  18327    10  Trying to enroll certificate request: ModelName=AC_51bad41f-3854-4eb5-a2f2-0f7a94034ee8%2FLogicalName_39907e78_e61b_4730_b9fa_d44a53e4111c;Hash=1677525787
2018-02-27T05:16:09.5530000  VERB  Event  org.jscep.transport.UrlConnectionGetTransport  18327    10  Sending GetCACaps(ca) to https://<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:14.6440000  VERB  Event  org.jscep.transport.UrlConnectionGetTransport  18327    10  Received '200 OK' when sending GetCACaps(ca) to https://<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:21.8220000  VERB  Event  org.jscep.message.PkiMessageEncoder  18327     10 Encoding message: org.jscep.message.PkcsReq@2b06f45f[messageData=org.<server>.pkcs.PKCS10CertificationRequest@699b3cd,messageType=PKCS_REQ,senderNonce=Nonce [D447AE9955E624A56A09D64E2B3AE76E],transId=251E592A777C82996C7CF96F3AAADCF996FC31FF]
2018-02-27T05:16:21.8790000  VERB  Event  org.jscep.message.PkiMessageEncoder  18327     10  Signing pkiMessage using key belonging to [dn=CN=<uesrname>; serial=1]
2018-02-27T05:16:21.9580000  VERB  Event  org.jscep.transaction.EnrollmentTransaction  18327     10  Sending org.<server>.cms.CMSSignedData@ad57775
```

Las entradas clave incluyen las siguientes cadenas de texto de ejemplo:

- Hay 1 solicitud
- Se recibió "200 OK" al enviar GetCACaps(ca) a https://\<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
- Firma de pkiMessage usando la clave que pertenece a [dn=CN=\<username>; serial=1]


IIS registra también la conexión en la carpeta %SystemDrive%\inetpub\logs\LogFiles\W3SVC1\ del servidor NDES. Este es un ejemplo:

```
fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll operation=GetCACert&message=ca 443 - 
fe80::f53d:89b8:c3e8:5fec%13 Dalvik/2.1.0+(Linux;+U;+Android+5.0;+P01M+Build/LRX21V) - 200 0 0 3909 0
fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll operation=GetCACaps&message=ca 443 - 
fe80::f53d:89b8:c3e8:5fec%13 Dalvik/2.1.0+(Linux;+U;+Android+5.0;+P01M+Build/LRX21V) - 200 0 0 421 
```

### <a name="iosipados-devices"></a>Dispositivos iOS/iPadOS

Revise el [registro de depuración de los dispositivos](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices). Busque entradas similares a las siguientes, que se registran cuando el dispositivo se conecta a NDES:

```
debug    18:30:53.691033 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=SCEP%20Authority\ 
debug    18:30:54.640644 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=SCEP%20Authority\ 
default    18:30:55.483977 -0500    profiled    Attempting to retrieve issued certificate...\ 
debug    18:30:55.487798 -0500    profiled    Sending CSR via GET.\  
debug    18:30:55.487908 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=PKIOperation&message=MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgMFADCABgkqhkiG9w0BBwGggCSABIIZfzCABgkqhkiG9w0BBwOggDCAAgEAMYIBgjCCAX4CAQAwZjBPMRUwEwYKCZImiZPyLGQBGRYFbG9jYWwxHDAaBgoJkiaJk/IsZAEZFgxmb3VydGhjb2ZmZWUxGDAWBgNVBAMTD0ZvdXJ0aENvZmZlZSBDQQITaAAAAAmaneVjEPlcTwAAAAAACTANBgkqhkiG9w0BAQEFAASCAQCqfsOYpuBToerQLkw/tl4tH9E+97TBTjGQN9NCjSgb78fF6edY0pNDU+PH4RB356wv3rfZi5IiNrVu5Od4k6uK4w0582ZM2n8NJFRY7KWSNHsmTIWlo/Vcr4laAtq5rw+CygaYcefptcaamkjdLj07e/Uk4KsetGo7ztPVjSEFwfRIfKv474dLDmPqp0ZwEWRQGZwmPoqFMbX3g85CJT8khPaqFW05yGDTPSX9YpuEE0Bmtht9EwOpOZe6O7sd77IhfFZVmHmwy5mIYN7K6mpx/4Cb5zcNmY3wmTBlKEkDQpZDRf5PpVQ3bmQ3we9XxeK1S4UsAXHVdYGD+bg/bCafMIAGCSqGSIb3DQEHATAUBggqhkiG9w0DBwQI5D5J2lwZS5OggASCF6jSG9iZA/EJ93fEvZYLV0v7GVo3JAsR11O7DlmkIqvkAg5iC6DQvXO1j88T/MS3wV+rqUbEhktr8Xyf4sAAPI4M6HMfVENCJTStJw1PzaGwUJHEasq39793nw4k268UV5XHXvzZoF3Os2OxUHSfHECOj
```

Las entradas clave incluyen las siguientes cadenas de texto de ejemplo:

- operation=GetCACert
- Intentando recuperar el certificado emitido
- Envío de CSR mediante GET
- operation=PKIOperation

### <a name="windows-devices"></a>Dispositivos Windows

En un dispositivo Windows que está realizando una conexión a NDES, puede ver el Visor de eventos de Windows de los dispositivos y buscar indicaciones de una conexión correcta. Las conexiones se registran como un identificador de evento **36** en el registro *DeviceManagement-Enterprise-Diagnostics-Provide* > **Administración** de los dispositivos.

Para abrir el registro:

1. En el dispositivo, ejecute **eventvwr.msc** para abrir el Visor de eventos de Windows

2. Expanda **Registros de aplicaciones y servicios** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostic-Provider** > **Administración**.

3. Busque el evento **36**, que es similar al ejemplo siguiente, con la línea de clave de **SCEP: La solicitud de certificado se generó correctamente**:

   ```
   Event ID:      36
   Task Category: None
   Level:         Information
   Keywords:
   User:          <UserSid>
   Computer:      <Computer Name>
   Description:
   SCEP: Certificate request generated successfully. Enhanced Key Usage: (1.3.6.1.5.5.7.3.2), NDES URL: (https://<server>/certsrv/mscep/mscep.dll/pkiclient.exe), Container Name: (), KSP Setting: (0x2), Store Location: (0x1).
   ```

## <a name="troubleshoot-common-errors"></a>Solución de problemas de errores comunes

Las secciones siguientes pueden ayudar con problemas comunes de conexión de todas las plataformas de dispositivos a NDES.

### <a name="status-code-500"></a>Código de estado 500

Las conexiones que se parecen al ejemplo siguiente, con un código de estado 500, indican que el derecho de usuario *Suplantar a un cliente después de la autenticación* no está asignado al grupo IIS_IURS en el servidor NDES. El valor de estado de **500** aparece al final:

```
2017-08-08 20:22:16 IP_address GET /certsrv/mscep/mscep.dll operation=GetCACert&message=SCEP%20Authority 443 - 10.5.14.22 profiled/1.0+CFNetwork/811.5.4+Darwin/16.6.0 - 500 0 1346 31
```

**Para solucionar este problema**:

1. En el servidor NDES, ejecute **secpol.msc** para abrir la directiva de seguridad local.

2. Expanda **Directivas locales** y, a continuación, haga clic en **Asignación de derechos de usuario**.

3. Haga doble clic en **Suplantar un cliente después de la autenticación** en el panel derecho.

4. Haga clic en **Agregar usuario o grupo...** , escriba **IIS_IURS** en el cuadro **Escribir los nombres de objeto para seleccionar** y, a continuación, haga clic en **Aceptar**.

5. Haga clic en **Aceptar**.

6. Reinicie el equipo y, a continuación, vuelva a intentar la conexión desde el dispositivo.

### <a name="test-the-scep-server-url"></a>Prueba de la dirección URL del servidor de SCEP

Use los pasos siguientes para probar la dirección URL que se especifica en el perfil de certificado SCEP.

1. En Intune, edite el perfil de certificado SCEP y copie la dirección URL del servidor. La dirección URL debe ser similar a *https://contoso.com/certsrv/mscep/msecp.dll* .

2. Abra un explorador web y, a continuación, vaya a la dirección URL del servidor SCEP. El resultado debe ser: **HTTP Error 403.0 – Forbidden**. Este resultado indica que la dirección URL funciona correctamente.

   Si no recibe ese error, seleccione el vínculo que se parece al error que aparece para ver la guía específica del problema:
   - [Recibo un mensaje general del servicio de inscripción de dispositivos de red](#general-ndes-message)
   - [Recibo el error "HTTP 503. The service is unavailable"](#http-error-503)
   - [Recibo el error "GatewayTimeout"](#gatewaytimeout)
   - [Recibo "HTTP 414 Request-URI Too Long"](#http-414-request-uri-too-long)
   - [Recibo "This page can't be displayed"](#this-page-cant-be-displayed)
   - [Recibo "500 - Internal server error"](#internal-server-error)

#### <a name="general-ndes-message"></a>Mensaje de NDES general

Al ir a la dirección URL del servidor SCEP, recibe el siguiente mensaje del servicio de inscripción de dispositivos de red:

![Dirección URL del servidor de SCEP](../protect/media/troubleshoot-scep-certificate-device-to-ndes/ndes-server-url-message.png)

- **Causa**: Este problema suele deberse a la instalación del conector de Microsoft Intune.

  Mscep.dll es una extensión ISAPI que intercepta la solicitud entrante y muestra el error HTTP 403 si se ha instalado correctamente.
  
  **Solución**: Examine el archivo *SetupMsi.log* para determinar si el conector de Microsoft Intune se ha instalado correctamente. En el ejemplo siguiente, *Installation completed successfully* e *Installation success or error status: 0* indican una instalación correcta:

  ```
  MSI (c) (28:54) [16:13:11:905]: Product: Microsoft Intune Connector -- Installation completed successfully.
  MSI (c) (28:54) [16:13:11:999]: Windows Installer installed the product. Product Name: Microsoft Intune Connector. Product Version: 6.1711.4.0. Product Language: 1033. Manufacturer: Microsoft Corporation. Installation success or error status: 0.
  ```

  Si se produce un error en la instalación, quite el conector de Microsoft Intune y, a continuación, vuelva a instalarlo.

#### <a name="http-error-503"></a>HTTP Error 503

Cuando vaya a la dirección URL del servidor SCEP, recibirá el siguiente error:

![HTTP Error 503. The service is unavailable](../protect/media/troubleshoot-scep-certificate-device-to-ndes/service-unavailable.png)

Este problema suele deberse a que no se ha iniciado el grupo de aplicaciones **SCEP** en IIS. En el servidor NDES, abra **Administrador de IIS** y vaya a **Grupos de aplicaciones**. Busque el grupo de aplicaciones de **SCEP** y confirme que se ha iniciado.

Si el grupo de aplicaciones de SCEP no se ha iniciado, compruebe el registro de eventos de la aplicación en el servidor:

1. En el dispositivo, ejecute **eventvwr.msc** para abrir el **Visor de eventos** y vaya a **Registros de Windows** > **Aplicación**.

2. Busque un evento similar al ejemplo siguiente, que significa que el grupo de aplicaciones se bloquea cuando se recibe una solicitud:

   ```
   Log Name:      Application
   Source:        Application Error
   Event ID:      1000
   Task Category: Application Crashing Events
   Level:         Error
   Keywords:      Classic
   Description: Faulting application name: w3wp.exe, version: 8.5.9600.16384, time stamp: 0x5215df96
   Faulting module name: ntdll.dll, version: 6.3.9600.18821, time stamp: 0x59ba86db
   Exception code: 0xc0000005
   ```

**Causas comunes de un bloqueo del grupo de aplicaciones**:

- **Causa 1**: Hay certificados de entidades de certificación intermedios (no autofirmados) en el almacén de certificados de entidades de certificación raíz de confianza del servidor NDES.

  **Solución**: Quite los certificados intermedios del almacén de certificados de entidades de certificación raíz de confianza y, a continuación, reinicie el servidor NDES.
  
  Para identificar todos los certificados intermedios del almacén de certificados de entidades de certificación raíz de confianza, ejecute el siguiente cmdlet de PowerShell: `Get-Childitem -Path cert:\LocalMachine\root -Recurse | Where-Object {$_.Issuer -ne $_.Subject}`

  Un certificado que tiene los mismos valores **Emitido para** y **Emitido por** es un certificado raíz. De lo contrario, es un certificado intermedio.

  Después de quitar los certificados y reiniciar el servidor, vuelva a ejecutar el cmdlet de PowerShell para confirmar que no hay certificados intermedios. Si hay alguno, compruebe si un directiva de grupo inserta los certificados intermedios en el servidor NDES. En ese caso, excluya el servidor NDES de la directiva de grupo y vuelva a quitar los certificados intermedios.

- **Causa 2**: Las direcciones URL de la lista de revocación de certificados (CRL) están bloqueadas o no son accesibles para los certificados que usa Intune Certificate Connector.

  **Solución**: Habilite el registro adicional para recopilar más información:
  1. Abra el Visor de eventos, haga clic en **Ver** y asegúrese de que esté activada la opción **Mostrar registros analíticos y de depuración**.
  2. Vaya a **Registros de aplicaciones y servicios** > **Microsoft** > **Windows** > **CAPI2** > **Operativo**, haga clic con el botón secundario en **Operativo** y, a continuación, haga clic en **Habilitar registro**.
  3. Una vez habilitado el registro de CAPI2, reproduzca el problema y examine el registro de eventos para solucionar el problema.

- **Causa 3**: El permiso IIS en **CertificateRegistrationSvc** tiene habilitada la **Autenticación de Windows**.

  **Solución**: Habilite la **Autenticación anónima**, deshabilite la **Autenticación de Windows** y, a continuación, reinicie el servidor NDES.

  ![Permisos de IIS](../protect/media/troubleshoot-scep-certificate-device-to-ndes/iis-permissions.png)

#### <a name="gatewaytimeout"></a>GatewayTimeout

Cuando vaya a la dirección URL del servidor SCEP, recibirá el siguiente error:

![Gatewaytimeout error](../protect/media/troubleshoot-scep-certificate-device-to-ndes/gateway-timeout.png)

- **Causa**: No se ha iniciado el servicio del **conector del proxy de aplicación de Microsoft AAD**.

  **Solución**:  Ejecute **services.msc** y, a continuación, asegúrese de que se está ejecutando el servicio del **conector del proxy de aplicación de AAD de Microsoft** y **Tipo de inicio** está establecido en **Automático**.

#### <a name="http-414-request-uri-too-long"></a>HTTP 414 Request-URI Too Long

Cuando vaya a la dirección URL del servidor SCEP, recibirá el siguiente error: `HTTP 414 Request-URI Too Long`

- **Causa**: El filtrado de solicitudes de IIS no está configurado para admitir las direcciones URL largas (consultas) que recibe el servicio NDES. Esta compatibilidad se configura al [configurar el servicio NDES](certificates-scep-configure.md#configure-the-ndes-service) para su uso con la infraestructura de SCEP.

- **Solución**: Configure la compatibilidad con direcciones URL largas.

  1. En el servidor NDES, abra el administrador de IIS, seleccione **Sitio web predeterminado** > **Filtrado de solicitudes** > **Modificar configuración de característica** para abrir la página **Modificar configuración del filtrado de solicitudes**.

  2. Configure las siguientes opciones:
     - **Longitud máxima de dirección URL (bytes)** = 65534
     - **Cadena de consulta máxima (bytes)** = 65534

  3. Seleccione **Aceptar** para guardar esta configuración y cerrar el administrador de IIS.

  4. Para validar esta configuración, busque la siguiente clave del Registro para confirmar que tiene los valores indicados:

     HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters

     Los valores siguientes se establecen como entradas DWORD:
     - Nombre: **MaxFieldLength**, con un valor decimal de **65534**
     - Nombre: **MaxRequestBytes**, con un valor decimal de **65534**

  5. Reinicie el servidor de NDES.

#### <a name="this-page-cant-be-displayed"></a>This page can't be displayed

Tiene configurado Azure AD Application Proxy. Cuando vaya a la dirección URL del servidor SCEP, recibirá el siguiente error:

`This page can't be displayed`

- **Causa**: Este problema se produce cuando la dirección URL externa de SCEP es incorrecta en la configuración de Application Proxy. Un ejemplo de esta dirección URL es https://contoso.com/certsrv/mscep/mscep.dll.

  **Solución**: Use el dominio predeterminado de *yourtenant.msappproxy.net* para la dirección URL externa de SCEP en la configuración de Application Proxy.

#### <a name="internal-server-error"></a>500 - Internal server error

Cuando vaya a la dirección URL del servidor SCEP, recibirá el siguiente error:

![500 - Internal server error](../protect/media/troubleshoot-scep-certificate-device-to-ndes/500-internal-server-error.png)

- **Causa 1**: La cuenta de servicio NDES está bloqueada o su contraseña ha expirado.

  **Solución**: Desbloquee la cuenta o restablezca la contraseña.

- **Causa 2**: Los certificados MSCEP-RA han expirado.

  **Solución**: Si los certificados MSCEP-RA han expirado, vuelva a instalar el rol NDES o solicite un nuevo certificado Cifrado CEP e Intercambiar agente de inscripción (solicitud sin conexión).

  Para solicitar nuevos certificados, siga estos pasos:

  1. En la entidad de certificación o la entidad de certificación emisora, abra el complemento MMC de plantillas de certificado. Asegúrese de que el usuario que ha iniciado sesión y el servidor NDES tienen permisos de **lectura** e **inscripción** en las plantillas de certificado Cifrado CEP e Intercambiar agente de inscripción (solicitud sin conexión).

  2. Compruebe los certificados caducados en el servidor NDES y copie la información del **Firmante** del certificado.

  3. Abra el complemento MMC Certificados para la **cuenta de equipo**.

  4. Expanda **Personal**, haga clic con el botón derecho en **Certificados** y, a continuación, seleccione **Todas las tareas** > **Solicitar un nuevo certificado**.

  5. En la página para **solicitar certificado**, haga clic en **Cifrado CEP** y luego haga clic en **Se necesita más información para inscribir este certificado. Haga clic aquí para configurar los valores**.

     ![Selección del cifrado CEP](../protect/media/troubleshoot-scep-certificate-device-to-ndes/select-scep-encryption.png)

  6. En **Propiedades del certificado**, haga clic en la pestaña **Firmante**, rellene el **Nombre del firmante** con la información recopilada durante el paso 2, haga clic en **Agregar** y, a continuación, haga clic en **Aceptar**.

  7. Complete la inscripción de certificados.

  8. Abra el complemento MMC Certificados para **Mi cuenta de equipo**.

     La inscripción para el certificado Intercambiar agente de inscripción (solicitud sin conexión) debe realizarse en el contexto del usuario porque el **Tipo de firmante** de esta plantilla de certificado está establecido en **Usuario**.

  9. Expanda **Personal**, haga clic con el botón derecho en **Certificados** y, a continuación, seleccione **Todas las tareas** > **Solicitar un nuevo certificado**.

  10. En la página para **solicitar certificado**, haga clic en **Intercambiar agente de inscripción (solicitud sin conexión)** y luego haga clic en **Se necesita más información para inscribir este certificado. Haga clic aquí para configurar los valores**.

      ![Selección de Intercambiar agente de inscripción](../protect/media/troubleshoot-scep-certificate-device-to-ndes/select-exchange-enrollment-agent.png)

  11. En **Propiedades del certificado**, haga clic en la pestaña **Firmante**, rellene el **Nombre del firmante** con la información recopilada durante el paso 2 y haga clic en **Agregar**.

      ![Propiedades de certificado](../protect/media/troubleshoot-scep-certificate-device-to-ndes/certificate-properties.png)

      Seleccione la pestaña **Clave privada**, seleccione  **Hacer exportable la clave privada** y, a continuación, haga clic en **Aceptar**.

      ![Clave privada](../protect/media/troubleshoot-scep-certificate-device-to-ndes/private-key.png)

  12. Complete la inscripción de certificados.

  13. Exporte el certificado Intercambiar agente de inscripción (solicitud sin conexión) del almacén de certificados del usuario actual. En el Asistente para exportación de certificados, haga clic en **Exportar la clave privada**.

  14. Importe en certificado en el almacén de certificados del equipo local.

  15. En el complemento MMC Certificados, realice la acción siguiente para cada uno de los nuevos certificados:

      Haga clic con el botón secundario en el certificado, haga clic en **Todas las tareas** > **Administrar claves privadas** y agregue el permiso **Leer** a la cuenta de servicio NDES.

  16. Ejecute el comando **iisreset** para reiniciar IIS.

## <a name="next-steps"></a>Pasos siguientes

Si el dispositivo llega correctamente al servidor NDES para presentar la solicitud de certificado, el siguiente paso es revisar el [módulo de directivas de Intune Certificate Connectors](troubleshoot-scep-certificate-ndes-policy-module.md).
