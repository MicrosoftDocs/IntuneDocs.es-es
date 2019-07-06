---
title: El dispositivo no tiene un certificado | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/04/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: df973b18-9166-417d-8aa3-49edd2bda256
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 119e3399067297764abb8a14d2f5861cba33e408
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2019
ms.locfileid: "67529299"
---
# <a name="your-android-device-is-missing-a-certificate-that-usually-comes-installed-on-your-phone"></a>El dispositivo Android no tiene un certificado que normalmente viene instalado en el teléfono

Si el dispositivo no está inscrito en Intune y no tiene un certificado que normalmente viene instalado en el teléfono, no podrá iniciar sesión en la aplicación de portal de empresa. Cuando intente iniciar sesión, verá el siguiente mensaje:

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

Puede solucionar este problema al obtener el certificado necesario de la [página del certificado de Digicert](https://www.digicert.com/digicert-root-certificates.htm).

1. Busque y descargue el certificado __Baltimore CyberTrust Root__. También puede descargarlo directamente desde [aquí](https://www.digicert.com/CACerts/BaltimoreCyberTrustRoot.crt).

2. Deslice el dedo desde la parte superior de la pantalla para mostrar la lista de sus notificaciones recientes y pulse en **BaltimoreCyberTrustRoot.crt**.

3. El dispositivo le pedirá que **proporcione un nombre al certificado**. No cambie el nombre del certificado predeterminado que aparece.

4. Asegúrese de que **Uso de credencial** está configurado como **Usada para VPN y aplicaciones** y pulse en **Aceptar**.

    ![screenshot-certificate-name-dialog-showing-baltimore-certificate-name](./media/andr-cert_install-2-add_cert_name.png)

5. Cierre el explorador y la aplicación de portal de empresa.

6. Vuelva a abrir la aplicación del portal de empresa. Ahora debería poder iniciar sesión en la aplicación Portal de empresa. Si todavía no puede usar la aplicación de Portal de empresa, póngase en contacto con el equipo de soporte técnico de su empresa con la información proporcionada en el [sitio web del Portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980) para obtener más instrucciones.

>[!NOTE]
> Si instala este certificado, no se soluciona el problema, verá un mensaje distinto "Falta un certificado" y tendrá que realizar pasos adicionales para [instalar el certificado que falta](your-device-is-missing-an-IT-required-certificate-android.md).

¿Sigue necesitando ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
