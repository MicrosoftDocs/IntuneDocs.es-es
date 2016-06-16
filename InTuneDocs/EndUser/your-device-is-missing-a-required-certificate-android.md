---
# required metadata

title: El dispositivo no tiene un certificado necesario | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 05/05/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: arnab
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# El dispositivo no tiene un certificado necesario
Si el dispositivo Android no está inscrito en Intune y no tiene un certificado que normalmente viene instalado en el teléfono, no podrá iniciar sesión en la aplicación Portal de empresa de Android. Cuando intente iniciar sesión, verá el siguiente mensaje:

![andr-cert-install-cert-missing](./media/andr-cert_install-1-cert_missing.png)

Para resolver este problema y obtener el certificado necesario:

1.  En un explorador, vaya a esta [página de certificado Digicert](https://www.digicert.com/digicert-root-certificates.htm).

2.  Busque y descargue el certificado Baltimore CyberTrust Root (https://www.digicert.com/CACerts/BaltimoreCyberTrustRoot.crt).

3.  Deslice el dedo desde la parte superior de la pantalla hacia abajo para abrir sus notificaciones y pulse en **BaltimoreCyberTrustRoot.crt** en la lista de notificaciones.

4.  En el cuadro de diálogo **Nombre del certificado**, acepte el nombre de certificado predeterminado.

5. Asegúrese de que **Uso de credencial** está configurado como **Usada para VPN y aplicaciones** y pulse en **Aceptar**.

    ![andr-cert-install-add-cert-name](./media/andr-cert_install-2-add_cert_name.png)

6. Cierre el explorador web y la aplicación Portal de empresa.

7. Vuelva a abrir la aplicación del portal de empresa. Ahora debería poder iniciar sesión en la aplicación Portal de empresa. Si necesita ayuda, póngase en contacto con el Administrador de TI.

Si necesita ayuda y no encuentra la información de contacto del administrador de TI, vea si aparece en el [sitio web del portal de empresa](http://portal.manage.microsoft.com).

<!--HONumber=Jun16_HO1-->


