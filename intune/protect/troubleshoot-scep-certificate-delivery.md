---
title: Solución de problemas de entrega de certificados a dispositivos cuando se usa SCEP con Microsoft Intune | Microsoft Docs
description: Solucione los problemas de entrega de un certificado a un dispositivo desde la entidad de certificación usando perfiles de certificado SCEP con Intune para implementar certificados.
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
ms.openlocfilehash: 77be59d126dc7e73bee468ca938938c6bb1b2e1a
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "76915881"
---
# <a name="troubleshoot-the-delivery-of-certificates-provisioned-by-scep-to-devices-in-microsoft-intune"></a>Solución de problemas con la entrega de certificados aprovisionados por SCEP a dispositivos en Microsoft Intune

Utilice la información de este artículo como ayuda para investigar la entrega de certificados a los dispositivos cuando se usa el protocolo de inscripción de certificados simple (SCEP) para aprovisionar certificados en Intune. Cuando el servidor del servicio de inscripción de dispositivos de red (NDES) recibe el certificado solicitado para un dispositivo de la entidad de certificación (CA), pasa ese certificado de nuevo al dispositivo.

Este artículo se aplica al paso 5 del [flujo de trabajo de comunicación de SCEP](troubleshoot-scep-certificate-profiles.md); entrega del certificado al dispositivo que envió la solicitud de certificado.

## <a name="review-the-certification-authority"></a>Revisión de la entidad de certificación

Cuando la entidad de certificación haya emitido el certificado, verá una entrada similar a la del ejemplo siguiente en la entidad de certificación:

![Ejemplo de certificados emitidos](../protect/media/troubleshoot-scep-certificate-delivery/certificate-authority.png)

## <a name="review-the-device"></a>Revisión del dispositivo

### <a name="android"></a>Android

En el caso de los dispositivos inscritos por el administrador de dispositivos, verá una notificación similar a la siguiente imagen, que le pide que instale el certificado:

![Notificación de Android](../protect/media/troubleshoot-scep-certificate-delivery/android-notification.png)

En el caso de Android Enterprise o Samsung Knox, la instalación del certificado es automática y silenciosa.

Para ver un certificado instalado en Android, use una aplicación de visualización de certificados de terceros.

También puede revisar el [registro OMADM de los dispositivos](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices). Busque entradas similares a las siguientes, que se registran cuando se instalan los certificados:

**Certificado raíz**:

```
2018-02-27T04:50:52.1890000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595        9    Root cert '17…' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALL_REQUESTED
2018-02-27T04:53:31.1300000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595        0    Root cert '17…' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALLING
2018-02-27T04:53:32.0390000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595       14    Root cert '17…' state changed from CERT_INSTALLING to CERT_INSTALL_SUCCESS
```

**Certificado aprovisionado a través de SCEP**

```
2018-02-27T05:16:08.2500000    VERB    Event     com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager    18327       10    There are 1 requests
2018-02-27T05:16:08.2500000    VERB    Event     com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager    18327       10    Trying to enroll certificate request: ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787
2018-02-27T05:16:20.6150000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Sending GetCACert(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=ca
2018-02-27T05:16:20.6530000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Received '200 OK' when sending GetCACert(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=ca
2018-02-27T05:16:21.7460000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Sending GetCACaps(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:21.7890000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Received '200 OK' when sending GetCACaps(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:28.0340000    VERB    Event     org.jscep.transaction.EnrollmentTransaction    18327       10    Response: org.jscep.message.CertRep@3150777b[failInfo=<null>,pkiStatus=SUCCESS,recipientNonce=Nonce [GUID],messageData=org.spongycastle.cms.CMSSignedData@27cc8998,messageType=CERT_REP,senderNonce=Nonce [GUID],transId=TRANSID]
2018-02-27T05:16:28.2440000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       10    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_ENROLLED to CERT_INSTALL_REQUESTED
2018-02-27T05:18:44.9820000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327        0    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALLING
2018-02-27T05:18:45.3460000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       14    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_INSTALLING to CERT_ACCESS_REQUESTED
2018-02-27T05:20:15.3520000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       21    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_ACCESS_REQUESTED to CERT_ACCESS_GRANTED
```

### <a name="ios-and-ipados"></a>iOS y iPadOS

En el dispositivo iOS o iPadOS, puede ver el certificado en el perfil de administración de dispositivos. Profundice para ver los detalles de los certificados instalados.

![Certificado de iOS](../protect/media/troubleshoot-scep-certificate-delivery/ios-certificate.png)

También puede buscar entradas similares a las siguientes en el [registro de depuración de iOS](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices):

```
Debug 18:30:53.691033 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=SCEP%20Authority\  
Debug 18:30:54.640644 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=SCEP%20Authority\ 
Debug 18:30:55.487908 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=PKIOperation&message=MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgMFADCABgkqhkiG9w0BBwGggCSABIIZfzCABgkqhkiG9w0BBwOggDCAAgEAMYIBgjCCAX4CAQAwZjBPMRUwEwYKCZImiZPyLGQBGRYFbG9jYWwxHDAaBgoJkiaJk/IsZAEZFgxmb3VydGhjb2ZmZWUxGDAWBgNVBAMTD0ZvdXJ0aENvZmZlZSBDQQITaAAAAAmaneVjEPlcTwAAAAAACTANBgkqhkiG9w0BAQEFAASCAQCqfsOYpuBToerQLkw/tl4tH9E+97TBTjGQN9NCjSgb78fF6edY0pNDU+PH4RB356wv3rfZi5IiNrVu5Od4k6uK4w0582ZM2n8NJFRY7KWSNHsmTIWlo/Vcr4laAtq5rw+CygaYcefptcaamkjdLj07e/Uk4KsetGo7ztPVjSEFwfRIfKv474dLDmPqp0ZwEWRQG 
Debug 18:30:57.285730 -0500 profiled Adding dependent Microsoft.Profiles.MDM to parent www.windowsintune.com.SCEP.ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295 in domain ManagedProfileToManagingProfile to system\ 
Default 18:30:57.320616 -0500 profiled Profile \'93www.windowsintune.com.SCEP.ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295\'94 installed.\ 
```

### <a name="windows"></a>Windows

En el dispositivo Windows, compruebe que el certificado se entregó:

- Ejecute **eventvwr.msc** para abrir el Visor de eventos. Vaya a **Registros de aplicaciones y servicios** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostic-Provider** > **Administración** y busque el **evento 39**. Este evento debe tener una descripción general de: **SCEP: certificado instalado correctamente.**

   ![Evento 39 en el registro de aplicaciones de Windows](../protect/media/troubleshoot-scep-certificate-delivery/device-app-log.png)

Para ver el certificado en el dispositivo, ejecute **certmgr.msc** para abrir el complemento MMC Certificados y comprobar que los certificados raíz y SCEP están instalados correctamente en el dispositivo del almacén personal:

   1. Vaya a **Certificados (equipo local)**  > **Entidades de certificación raíz de confianza** > **Certificados** y compruebe que el certificado raíz de la entidad de certificación está presente. Los valores de *Emitidos para* y *Emitido por* serán los mismos.
   2. En el complemento MMC Certificados, vaya a **Certificados – Usuario actual** > **Personal** > **Certificados** y compruebe que el certificado solicitado esté presente, con *Emitidos por* igual al nombre de la entidad de certificación.

## <a name="troubleshoot-failures"></a>Solución de errores

### <a name="android"></a>Android

Para solucionar este paso, revise los errores que se registran en el registro DM de OMA.

### <a name="ios-and-ipados"></a>iOS y iPadOS

Para solucionar este paso, revise los errores que se registran en el registro de depuración de dispositivos.

### <a name="windows"></a>Windows

Para solucionar problemas relacionados con la no instalación del certificado en el dispositivo, busque en el registro de eventos de Windows los errores que sugieren problemas:

- En el dispositivo, ejecute **eventvwr.msc** para abrir el **Visor de eventos** y luego vaya a  > Registros de aplicaciones y servicios**Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider** > **Administrador**.

Los errores de entrega e instalación del certificado en el dispositivo suelen estar relacionados con las operaciones de Windows y no con Intune.

## <a name="next-steps"></a>Pasos siguientes

Si el certificado se implementa correctamente en el dispositivo, pero Intune no informa del éxito, consulte [Información de NDES a Intune](troubleshoot-scep-certificate-reporting.md) para solucionar problemas de información.
