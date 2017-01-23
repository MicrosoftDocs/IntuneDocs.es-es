---
title: El dispositivo no tiene un certificado | Microsoft Docs
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: df973b18-9166-417d-8aa3-49edd2bda256
searchScope:
- Company Portal
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: arnab
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d6fcfac7c8bd469f5163ec9b4017ae8c3d486428
ms.openlocfilehash: e0aaa48e46e547d4853478fdbb80711700a9c22a

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

6. Vuelva a abrir la aplicación del portal de empresa. Ahora debería poder iniciar sesión en la aplicación Portal de empresa. Si todavía no puede usar la aplicación de portal de empresa, póngase en contacto con el administrador de TI con la información proporcionada en el [sitio web del portal de empresa](http://portal.manage.microsoft.com) para obtener más instrucciones.

>[!NOTE]
> Si instala este certificado, no se soluciona el problema, verá un mensaje distinto "Falta un certificado" y tendrá que realizar pasos adicionales para [instalar el certificado que falta](your-device-is-missing-an-IT-required-certificate-android.md).

¿Sigue necesitando ayuda? Póngase en contacto con el administrador de TI. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](http://portal.manage.microsoft.com).



<!--HONumber=Jan17_HO1-->


