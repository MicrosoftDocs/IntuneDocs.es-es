---
title: Solución de problemas del módulo de directiva Microsoft Intune Certificate Connector | Microsoft Docs
description: Solucione problemas en el funcionamiento del módulo de directivas de NDES cuando el módulo procesa una solicitud de certificado al utilizar los perfiles de certificado SCEP para implementar certificados con Intune.
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
ms.openlocfilehash: be53f6102226b004cab2bd953357e8c360a00f67
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "76915842"
---
# <a name="troubleshoot-the-ndes-policy-module-in-microsoft-intune"></a>Solución de problemas del módulo de directivas de NDES en Microsoft Intune

La información de este artículo puede ayudarle a validar el funcionamiento del módulo de directivas del servicio de inscripción de dispositivos de red (NDES) que se instala con Microsoft Intune Certificate Connector. Cuando NDES recibe una solicitud de certificado, reenvía la solicitud al módulo de directivas, que valida la solicitud para el dispositivo. Después de la validación, NDES se pone en contacto con la entidad de certificación (CA) para solicitar el certificado en nombre del dispositivo.

Este artículo se aplica a los pasos 3 y 4 del [flujo de trabajo de comunicación de SCEP](troubleshoot-scep-certificate-profiles.md).

## <a name="ndes-communication-to-the-policy-module"></a>Comunicación de NDES con el módulo de directivas

Después de recibir la solicitud de certificado de un dispositivo, NDES valida esa solicitud con Intune a través del módulo de directivas que se instala con Microsoft Intune Certificate Connector. Estas entradas hacen referencia al *punto de registro de certificados*.

**Entradas del registro que indican que la operación se completó correctamente**:

Para confirmar que la solicitud de validación se envía al módulo, busque una entrada similar a los siguientes ejemplos en los registros del servidor NDES:

- **Registros IIS**:

  ```
  fe80::f53d:89b8:c3e8:5fec%13 POST /CertificateRegistrationSvc/Certificate/VerifyRequest - 443 - 
  fe80::f53d:89b8:c3e8:5fec%13 NDES_Plugin - 201 0 0 341 875
  ```

- **NDESPlugin log**:

  ```
  Calling VerifyRequest ...  
  Sending request to certificate registration point.
  ```

  En el ejemplo siguiente se indica una validación correcta de la solicitud de desafío de los dispositivos y que NDES ahora puede ponerse en contacto con la entidad de certificación:

  ```
  Verify challenge returns true
  Exiting VerifyRequest with 0x0
  ```

- **CertificateRegistrationPoint.svclog**:

  `Validation Phase 1 finished with status True.`  
  `Validation Phase 3 finished with status True.`  
  `VerifyRequest Finished with status True`


**Cuando no hay indicadores que señalen que la operación se ha completado correctamente**:

Si no encuentra estas entradas, empiece por revisar la guía de solución de problemas de [comunicación del dispositivo al servidor NDES](troubleshoot-scep-certificate-device-to-ndes.md#troubleshoot-common-errors).

Si la información de ese artículo no le ayuda a resolver el problema, las siguientes son entradas adicionales que pueden indicar problemas.

### <a name="ndespluginlog-contains-an-error-12175"></a>NDESPlugin.log contiene un error 12175

Cuando el registro contiene un error 12175 similar al siguiente, puede haber un problema con el certificado SSL:

```
WINHTTP_CALLBACK_STATUS_FLAG_CERT_CN_INVALID
Failed to send http request /CertificateRegistrationSvc/Certificate/VerifyRequest. Error 12175
```

Los exploradores modernos y los exploradores de dispositivos móviles omiten el *nombre común* en un certificado SSL si hay *nombres alternativos del firmante* presentes.

**Solución**:  Emita el certificado SSL del servidor web con los siguientes atributos para las opciones de *nombre común* y *nombre alternativo del firmante* y, a continuación, enlácelo al puerto 443 en IIS:

  - **Nombre del firmante**  
    CN = nombre del servidor externo
  - **Nombre alternativo del firmante**  
     Nombre = nombre del servidor externo  
     Nombre de DNS = nombre del servidor interno

### <a name="ndespluginlog-contains-an-error-403--forbidden-access-is-denied"></a>NDESPlugin.log contiene un error "403 – Forbidden: Access is denied"

Cuando los registros siguientes contienen un error 403 similar al siguiente, es posible que el certificado de cliente no sea de confianza o no sea válido:

**NDESPlugin.log**:

```
Sending request to certificate registration point.
Verify challenge returns <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"> <html xmlns="http://www.w3.org/1999/xhtml"> <head><meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1"/>
<title>403 - Forbidden: Access is denied.</title>
```

**Registro IIS**:

```
POST /CertificateRegistrationSvc/Certificate/VerifyRequest - 443 -<IP_address>
NDES_Plugin - 403 16 2148204809 453  
```

Este problema ocurre si hay certificados de entidades de certificación intermedios en el almacén de certificados de entidades de certificación raíz de confianza del servidor NDES.

Un certificado que tiene los mismos valores *Emitido para* y *Emitido por* es un certificado raíz. De lo contrario, es un certificado intermedio.

**Solución**: Para solucionar el problema, identifique y quite los certificados de la entidad de certificación intermedios del almacén de certificados de entidades de certificación raíz de confianza.

### <a name="ndespluginlog-indicates-the-challenge-returns-false"></a>NDESPlugin.log indica que el desafío devuelve false

Cuando el resultado del desafío devuelva **false**, compruebe si hay errores en *CertificateRegistrationPoint.svclog*. Por ejemplo, podría ver un error ""Signing certificate could not be retrieved" que se parece a la entrada siguiente:

```
Signing certificate could not be retrieved. System.Security.Cryptography.CryptographicException: m_safeCertContext is an invalid handle. at System.Security.Cryptography.X509Certificates.X509Certificate.ThrowIfContextInvalid() at System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString() at Microsoft.ConfigurationManager.CertRegPoint.CRPCertificate.RetrieveSigningCert(String certThumbprint
```

**Solución**: En el servidor en el que está instalado el conector, abra el Editor del Registro, busque la clave del Registro `HKLM\SOFTWARE\Microsoft\MicrosoftIntune\NDESConnector` y, a continuación, compruebe si existe el valor SigningCertificate.

Si este valor no existe, reinicie el servicio del conector de Intune en services.msc y, a continuación, compruebe si el valor aparece en el Registro. Si todavía falta el valor, suele deberse a problemas de conectividad de red entre el servidor NDES y el servicio de Intune.

## <a name="ndes-passes-the-request-to-issue-the-certificate"></a>NDES pasa la solicitud para emitir el certificado

Después de que el punto de registro de certificados (el módulo de directivas) realice una validación correcta, NDES pasa la solicitud de certificado a la entidad de certificación en nombre del dispositivo.

**Entradas del registro que indican que la operación se completó correctamente**:

- **Registro NDESPlugin**:

  ```
  Verify challenge returns true
  Exiting VerifyRequest with 0x0
  ```

- **Registros IIS**:

  ```
  fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe ... 80 - 
  fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 2713 1296
  ```

- **CertificateRegistrationPoint.svclog**:

  `Validation Phase 1 finished with status True.`  
  `Validation Phase 3 finished with status True.`  
  `VerifyRequest Finished with status True`

**Cuando no hay indicadores que señalen que la operación se ha completado correctamente**:

Si no ve las entradas que indican que la operación se ha realizado correctamente, siga estos pasos:

1. Busque los problemas que se registran en *CertificateRegistrationPoint.svclog* cuando el punto de registro de certificados verifica el desafío. Busque las entradas entre las líneas siguientes:

   - VerifyRequest Started.
   - VerifyRequest Finished con estado False

2. Abra el complemento MMC de la entidad de certificación en la entidad de certificación y seleccione **Solicitudes con error** para buscar errores que ayuden a identificar un problema. La imagen siguiente es un ejemplo:

   ![Ejemplo de una solicitud con error](../protect/media/troubleshoot-scep-certificate-ndes-policy-module/failed-requests.png)

3. Revise el registro de eventos de la aplicación en la entidad de certificación en busca de errores. Normalmente, puede ver errores que coinciden con lo que ve en **Solicitudes con error** en el paso anterior. La imagen siguiente es un ejemplo:

   ![Revisión del registro de aplicaciones](../protect/media/troubleshoot-scep-certificate-ndes-policy-module/application-log-errors.png)

## <a name="next-steps"></a>Pasos siguientes

Si el módulo de directivas de NDES valida la solicitud y la solicitud se reenvía a la entidad de certificación, el siguiente paso es revisar la [entrega de certificados al dispositivo](troubleshoot-scep-certificate-delivery.md).
