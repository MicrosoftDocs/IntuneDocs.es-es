---
title: Solución de problemas de notificación de una implementación correcta de certificados en dispositivos cuando se usa SCEP con Microsoft Intune | Microsoft Docs
description: Solucione los problemas de notificación de NDES y el conector a Intune en relación con una implementación correcta de los certificados aprovisionados con perfiles de certificado SCEP.
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
ms.openlocfilehash: 2ccc738626efc140efca46d1b997164ed36dd37f
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "76916024"
---
# <a name="troubleshoot-ndes-reporting-of-certificate-deployments-in-microsoft-intune"></a>Solución de problemas de notificación de NDES de implementaciones de certificado en Microsoft Intune

Use la siguiente información para confirmar que NDES y Microsoft Intune Certificate Connector notifican correctamente a Intune que el certificado se entregó a un dispositivo. La notificación a Intune es la última fase del uso de perfiles de certificado SCEP para aprovisionar dispositivos Windows con un certificado.

Este artículo se aplica al paso 6 del [flujo de trabajo de comunicación de SCEP](troubleshoot-scep-certificate-profiles.md).

## <a name="review-for-signs-of-successful-reporting"></a>Revisión de síntomas que indiquen una correcta notificación

Si la notificación se produjo correctamente, encontrará entradas similares a los siguientes ejemplos en el servidor NDES:

- **Registro IIS**:

  `fe80::f53d:89b8:c3e8:5fec%13 POST /CertificateRegistrationSvc/Certificate/Notify - 443 - fe80::f53d:89b8:c3e8:5fec%13 NDES_Plugin - 204 0 0 277 62`

- **NDESPlugin.log**:

  ```
  Calling Notifyrequest ...
  Sending request to certificate registration point.
  Exiting Notify with 0x0
  ```

- **CertificateRegistrationPoint.svclog**:

  ![Registro de Intune Certificate Connector](../protect/media/troubleshoot-scep-certificate-reporting/certificate-registration-point-log.png)

- **NDESConnector.svclog**:

  ![Registro de Intune Certificate Connector](../protect/media/troubleshoot-scep-certificate-reporting/ndesconnector-log.png)

- **CertificateRequestStatus**:

  Vaya a la carpeta *%ProgramFiles%\Microsoft Intune\CertificateRequestStatus*, donde verá carpetas con estado de **error**, **en procesamiento** y **correcto** que contienen los archivos de certificado con su correspondiente estado de solicitud.

  Si la solicitud de certificado se procesa correctamente, verá los nuevos archivos en la carpeta de estado **correcto**. Puede usar *Notepad.exe* para abrir los archivos y ver los datos cargados en el servicio Intune mediante Intune Certificate Connector. Los datos que se cargan incluyen detalles como **CertificateSerialNumber**, **UserID**, **DeviceID** y **Thumbprint**.

### <a name="troubleshoot-stuck-files"></a>Solución de problemas de archivos atascados

Si no ve que se cree ningún archivo nuevo en la carpeta de estado *correcto*, compruebe si hay archivos atascados en la carpeta con el estado *en procesamiento*.

Compruebe que Intune Connector Service se ha iniciado en el servidor NDES y que no hay ningún error en Ndesconnector.svclog.

## <a name="next-steps"></a>Pasos siguientes

[Cómo obtener soporte técnico para Microsoft Intune](../fundamentals/get-support.md)
