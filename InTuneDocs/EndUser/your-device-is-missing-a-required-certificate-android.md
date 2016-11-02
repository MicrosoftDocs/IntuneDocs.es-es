---
title: El dispositivo no tiene un certificado necesario | Microsoft Intune
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: arnab
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 016449720f6e77b8862fcaa232d252eefa8b20b3
ms.openlocfilehash: 27b3e3d4aefade368d900df95454c3d02e37bed4


---


# <a name="your-device-is-missing-a-required-certificate"></a>El dispositivo no tiene un certificado necesario


## <a name="your-device-is-missing-a-certificate-that-usually-comes-installed-on-your-phone"></a>El dispositivo no tiene un certificado que normalmente viene instalado en el teléfono
Si el dispositivo Android no está inscrito en Intune y no tiene un certificado que normalmente viene instalado en el teléfono, no podrá iniciar sesión en la aplicación Portal de empresa de Android. Cuando intente iniciar sesión, verá el siguiente mensaje:

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

Para resolver este problema y obtener el certificado necesario:

1.  En un explorador, vaya a esta [página de certificado Digicert](https://www.digicert.com/digicert-root-certificates.htm).

2.  Busque y descargue el certificado Baltimore CyberTrust Root (https://www.digicert.com/CACerts/BaltimoreCyberTrustRoot.crt).

3.  Deslice el dedo desde la parte superior de la pantalla hacia abajo para abrir sus notificaciones y pulse en **BaltimoreCyberTrustRoot.crt** en la lista de notificaciones.

4.  En el cuadro de diálogo **Nombre del certificado**, acepte el nombre de certificado predeterminado.

5. Asegúrese de que **Uso de credencial** está configurado como **Usada para VPN y aplicaciones** y pulse en **Aceptar**.

    ![screenshot-certificate-name-dialog-showing-baltimore-certificate-name](./media/andr-cert_install-2-add_cert_name.png)

6. Cierre el explorador web y la aplicación Portal de empresa.

7. Vuelva a abrir la aplicación del portal de empresa. Ahora debería poder iniciar sesión en la aplicación Portal de empresa. Si necesita ayuda, póngase en contacto con el administrador de TI.

## <a name="your-device-is-missing-a-certificate-required-by-your-it-admin"></a>El dispositivo no tiene un certificado que necesita el administrador de TI
Si el dispositivo Android no está inscrito en Intune y no tiene un certificado determinado que necesita el administrador de TI, no podrá iniciar sesión en la aplicación de portal de empresa de Android. Cuando intente iniciar sesión, verá el siguiente mensaje:

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

>[!NOTE]
> Si ya ha visto un mensaje en el que se indica que "falta un certificado" y ha seguido los pasos de [El dispositivo no tiene un certificado que normalmente viene instalado en el teléfono](#your-device-is-missing-a-certificate-that-usually-comes-installed-on-your-phone), ha hecho lo correcto. Es un certificado y mensaje diferente de este, así que continúe y siga los pasos de esta sección para obtener el certificado que falta.

Para resolver este problema y obtener el certificado necesario, hay dos pasos principales que necesitará realizar:

- Identificar el certificado que falta mirando en el equipo de una empresa o escuela.
- Usar el dispositivo para descargar el certificado que falta desde Internet.

### <a name="identify-the-missing-certificate-by-looking-on-a-company-or-school-pc"></a>Identificar el certificado que falta mirando en el equipo de una empresa o escuela

1. Abra un equipo y, luego, Internet Explorer. Si no tiene un equipo para esto, póngase en contacto con el administrador de TI. Para encontrar la información de contacto del administrador de TI, vaya al [sitio web del portal de empresa](http://portal.manage.microsoft.com).

2. Vaya al [sitio web del portal de empresa](http://portal.manage.microsoft.com) e inicie sesión con sus credenciales profesionales o educativas.

3. A la derecha de la barra de direcciones del explorador, elija el símbolo que parece un candado como se muestra en la siguiente captura de pantalla.

    ![screenshot-internet-explorer-address-bar-padlock-symbol](./media/andr-missing-cert-ie-padlock-symbol.png)

    Si no ve el símbolo del candado, deténgase y póngase en contacto con el administrador de TI. El candado significa que la sesión iniciada es segura, por lo que no debe continuar a menos que vea dicho símbolo.

4. Elija **Ver certificados**.

    ![screenshot-internet-explorer-view-certificases-button-on-website-identification-dialog](./media/andr-missg-cert-ie-view-cert-button.png)

5. En el cuadro de diálogo **Certificado**, elija la pestaña **Ruta de certificación** y, luego, identifique el certificado que tiene que obtener desde Internet. El nombre del certificado que necesita estará en la misma posición que el que está resaltado en la captura de pantalla del ejemplo anterior.

### <a name="download-and-install-the-missing-certificate-on-your-android-mobile-device"></a>Descargar e instalar el certificado que falta en el dispositivo móvil Android

1. Con un motor de búsqueda como Bing o Google, busque el nombre del certificado que falta que identificó en la sección anterior. El certificado puede terminar con diferentes "extensiones", como ".crt", ".pem", etc.

2. Descargue el certificado raíz desde el sitio web.

3. Una vez que descargue el certificado, arrastre hacia abajo desde la parte superior del dispositivo para abrir las notificaciones y luego pulse el nombre del certificado en la lista de notificaciones.

4. En el cuadro de diálogo **Nombre del certificado** que se muestra en la siguiente captura de pantalla, acepte el nombre de certificado predeterminado.

5. Asegúrese de que **Uso de credencial** está configurado como **Usada para VPN y aplicaciones** y pulse en **Aceptar**.

    ![screenshot-certificate-name-dialog-showing-certificate-name](./media/andr-missing-cert-cert-name.png)

6. Cierre la aplicación del portal de empresa.

7. Vuelva a abrir la aplicación del portal de empresa. Ahora debería poder iniciar sesión en la aplicación Portal de empresa. Si necesita ayuda, póngase en contacto con el administrador de TI.

Si aparece el mismo mensaje que indica que "falta un certificado" como el que se ha mostrado anteriormente, y ya ha seguido el procedimiento, probablemente todavía haya otro certificado que el administrador de TI necesitará ayudarle a instalar. Póngase en contacto con su administrador de TI y proporcione a esa persona este vínculo a [Problemas de certificado de Android](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues), donde se incluyen los pasos para solucionar el problema.



<!--HONumber=Oct16_HO2-->


