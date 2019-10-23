---
title: Solución de problemas de Microsoft Intune Certificate Connector y los Id. de evento | Microsoft Docs
titleSuffix: Microsoft Intune
description: Solucione problemas de Microsoft Intune Certificate Connector mediante la revisión de los identificadores y las descripciones de eventos, y revise los códigos de diagnóstico del servicio de conector de Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/01/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2d9556cc0357e76ee617ac0770a3efc2e3a1957f
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508871"
---
# <a name="intune-certificate-connector-events-and-diagnostic-codes"></a>Eventos y códigos de diagnóstico de Intune Certificate Connector

A partir de la versión 6.1806.x.x, el servicio de conector de Intune registra los eventos en el **Visor de eventos** (**Registros de aplicaciones y servicios** > **Conector de Microsoft Intune**). Con estos eventos podrá resolver posibles problemas en la configuración del conector de Intune. Estos eventos registran las operaciones que se realizan con éxito y con error, y también contienen códigos de diagnóstico con mensajes para ayudar a los administradores de TI a solucionar problemas.

> [!TIP]  
> Para solucionar problemas y comprobar la instalación del conector de Intune, vea [Ejemplos de scripts de la entidad de certificación](https://aka.ms/intuneconnectorverificationscript).

## <a name="event-ids-and-descriptions"></a>Identificadores de evento y descripciones

| Id. de evento      | Nombre del evento    | Descripción del evento | Códigos de diagnóstico relacionados |
| ------------- | ------------- | -------------     | -------------            |
| 10010 | StartedConnectorService  | Se inició el servicio de conector | 0x00000000, 0x0FFFFFFF |
| 10020 | StoppedConnectorService  | Se detuvo el servicio de conector | 0x00000000, 0x0FFFFFFF |
| 10100 | CertificateRenewal_Success  | Se renovó correctamente el certificado de inscripción del conector | 0x00000000, 0x0FFFFFFF |
| 10102 | CertificateRenewal_Failure  | No se pudo renovar el certificado de inscripción del conector. Reinstale el conector. | 0x00000000, 0x00000405, 0x0FFFFFFF |
| 10302 | RetrieveCertificate_Error  | No se pudo recuperar el certificado de inscripción del conector del Registro. Revise los detalles del evento para la huella digital del certificado relacionado con este evento. | 0x00000000, 0x00000404, 0x0FFFFFFF |
| 10301 | RetrieveCertificate_Warning  | Compruebe la información de diagnóstico en los detalles del evento. | 0x00000000, 0x00000403, 0x0FFFFFFF |
| 20100 | PkcsCertIssue_Success  | Se emitió correctamente un certificado PKCS. Revise los detalles del evento relacionados con el identificador de dispositivo, el identificador de usuario, el nombre de entidad de certificación, el nombre de plantilla de certificado y la huella digital del certificado. | 0x00000000, 0x0FFFFFFF |
| 20102 | PkcsCertIssue_Failure  | No se pudo emitir un certificado PKCS. Revise los detalles del evento relacionados con el identificador de dispositivo, el identificador de usuario, el nombre de entidad de certificación, el nombre de plantilla de certificado y la huella digital del certificado. | 0x00000000, 0x00000400, 0x00000401, 0x0FFFFFFF |
| 20200 | RevokeCert_Success  | El certificado se revocó correctamente. Revise los detalles del evento relacionados con el identificador de dispositivo, el identificador de usuario, el nombre de entidad de certificación y el número de serie del certificado. | 0x00000000, 0x0FFFFFFF |
| 20202 | RevokeCert_Failure | No se pudo revocar el certificado. Revise los detalles del evento relacionados con el identificador de dispositivo, el identificador de usuario, el nombre de entidad de certificación y el número de serie del certificado. Para más información, vea los registros de SVC del Servicio de inscripción de dispositivos de red.   | 0x00000000, 0x00000402, 0x0FFFFFFF |
| 20300 | Upload_Success | Se cargaron correctamente los datos de revocación o de solicitud del certificado. Revise los detalles del evento para obtener los detalles de carga. | 0x00000000, 0x0FFFFFFF |
| 20302 | Upload_Failure | No se pudieron cargar los datos de revocación o de solicitud del certificado. Revise los detalles del evento y el estado de carga para determinar el momento del error.| 0x00000000, 0x0FFFFFFF |
| 20400 | Download_Success | Se descargó correctamente la solicitud para firmar un certificado, descargar un certificado de cliente o revocar un certificado. Revise los detalles del evento para obtener los detalles de descarga.  | 0x00000000, 0x0FFFFFFF |
| 20402 | Download_Failure | No se pudo descargar la solicitud para firmar un certificado, descargar un certificado de cliente o revocar un certificado. Revise los detalles del evento para obtener los detalles de descarga. | 0x00000000, 0x0FFFFFFF |
| 20500 | CRPVerifyMetric_Success  | El punto de registro de certificados comprobó correctamente un desafío de cliente | 0x00000000, 0x0FFFFFFF |
| 20501 | CRPVerifyMetric_Warning  | El punto de registro de certificados se completó pero se rechazó la solicitud. Vea el código de diagnóstico y el mensaje para más detalles. | 0x00000000, 0x00000411, 0x0FFFFFFF |
| 20502 | CRPVerifyMetric_Failure  | El punto de registro de certificados no pudo comprobar un desafío de cliente. Vea el código de diagnóstico y el mensaje para más detalles. Vea los detalles del mensaje del evento para el identificador de dispositivo correspondiente al desafío. | 0x00000000, 0x00000408, 0x00000409, 0x00000410, 0x0FFFFFFF |
| 20600 | CRPNotifyMetric_Success  | El punto de registro de certificados terminó correctamente el proceso de notificación y ha enviado el certificado al dispositivo cliente. | 0x00000000, 0x0FFFFFFF |
| 20602 | CRPNotifyMetric_Failure  | El punto de registro de certificados no pudo finalizar el proceso de notificación. Vea los detalles del mensaje del evento para más información sobre la solicitud. Compruebe la conexión entre el servidor del Servicio de inscripción de dispositivos de red y la entidad de certificación. | 0x00000000, 0x0FFFFFFF |

## <a name="diagnostic-codes"></a>Códigos de diagnóstico

| Código de diagnóstico | Nombre de diagnóstico | Mensaje de diagnóstico |
| -------------   | -------------   | -------------      |
| 0x00000000 | Correcto  | Correcto |
| 0x00000400 | PKCS_Issue_CA_Unavailable  | La entidad de certificación no es válida o no está disponible. Compruebe que la entidad de certificación está disponible y que el servidor puede comunicarse con él. |
| 0x00000401 | Symantec_ClientAuthCertNotFound  | No se encontró el certificado de autenticación de cliente de Symantec en el almacén de certificados local. Vea el artículo [Instalación del certificado de autorización de registro de Symantec](certificates-digicert-configure.md#install-the-digicert-ra-certificate) para más información.  |
| 0x00000402 | RevokeCert_AccessDenied  | La cuenta especificada no tiene permisos para revocar un certificado de una entidad de certificación. Vea el campo Nombre de CA en los detalles del mensaje del evento para determinar la entidad de certificación emisora.  |
| 0x00000403 | CertThumbprint_NotFound  | No se pudo encontrar un certificado que coincida con los datos especificados. Inscriba el conector de certificado e inténtelo de nuevo. |
| 0x00000404 | Certificate_NotFound  | No se pudo encontrar un certificado que coincida con la entrada proporcionada. Vuelva a inscribir el conector de certificado e inténtelo de nuevo. |
| 0x00000405 | Certificate_Expired  | Certificado expirado. Vuelva a inscribir el conector de certificado para renovar el certificado e inténtelo de nuevo. |
| 0x00000408 | CRPSCEPCert_NotFound  | No se encontró el certificado de cifrado de CRP. Compruebe que el Servicio de inscripción de dispositivos de red y el conector de Intune están configurados correctamente. |
| 0x00000409 | CRPSCEPSigningCert_NotFound  | No se pudo recuperar el certificado de firma. Compruebe que el servicio de conector de Intune está configurado correctamente y que se está ejecutando. Compruebe también que los eventos de descarga del certificado se realizaron correctamente. |
| 0x00000410 | CRPSCEPDeserialize_Failed  | No se pudo deserializar la solicitud para el desafío de SCEP. Compruebe que el Servicio de inscripción de dispositivos de red y el conector de Intune están configurados correctamente. |
| 0x00000411 | CRPSCEPChallenge_Expired  | Solicitud denegada debido a que expiró el desafío de certificado. El dispositivo cliente puede reintentar obtener un nuevo desafío desde el servidor de administración. |
| 0x0FFFFFFFF | Unknown_Error  | No se puede completar la solicitud porque se produjo un error del lado servidor. Inténtelo de nuevo. |


## <a name="next-steps"></a>Pasos siguientes
Para obtener más ayuda, use la guía [Solucionar problemas de implementación de perfil de certificado SCEP en Microsoft Intune](https://support.microsoft.com/help/4457481/troubleshooting-scep-certificate-profile-deployment-in-intune).
