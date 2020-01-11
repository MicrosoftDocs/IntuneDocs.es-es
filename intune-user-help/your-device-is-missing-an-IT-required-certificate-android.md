---
title: El dispositivo no tiene un certificado | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/29/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: f0ba4cbb-ef0a-4335-86bf-f1d006867fa2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 9ac79311881b2f245cbdedcb6c9ac9763ba7cbf3
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75857156"
---
# <a name="install-missing-certificate-required-by-your-organization"></a>Instalar el certificado que falta en la organización  

Si el dispositivo no está inscrito en Intune y no tiene un certificado necesario, no podrá iniciar sesión en la aplicación Portal de empresa. Cuando intente iniciar sesión, verá el siguiente mensaje:

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

Hay dos opciones para intentar descargar el certificado necesario y obtener el dispositivo inscrito. 

- Habilite el acceso del explorador en Portal de empresa aplicación.
- Identifique el certificado que falta en el equipo de una empresa o escuela. A continuación, busque en Internet para descargar el certificado que falta. 

Complete los pasos para habilitar el acceso al explorador en primer lugar. Después, si todavía no puede inscribir el dispositivo, siga los pasos para buscar el certificado en Internet. 

## <a name="enable-browser-access"></a>Habilitar el acceso al explorador
Siga estos pasos para habilitar el acceso del explorador. Después de habilitar el acceso, Portal de empresa instalará el certificado adecuado y continuará la inscripción.    

1. En la aplicación Portal de empresa, vaya a la esquina derecha y seleccione el menú.  
2. Seleccione **Configuración**.  
3. Junto a **Habilitar el acceso al explorador** , seleccione **Habilitar**.  
4. En la pantalla administrador de dispositivos, seleccione **Activar**. 

## <a name="identify-and-download-the-missing-certificate-through-web-search"></a>Identificar y descargar el certificado que falta a través de la búsqueda web
Siga estos pasos para identificar e instalar manualmente el certificado en el dispositivo.  

1. Abra un equipo y, luego, Internet Explorer. Si no tiene un equipo para esto, póngase en contacto con el equipo de soporte técnico de su empresa. Para encontrar la información de contacto del equipo de soporte técnico de su empresa, vaya al [sitio web del Portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).

2. Vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980) e inicie sesión con sus credenciales profesionales o educativas.

3. A la derecha de la barra de direcciones del explorador, elija el símbolo que parece un candado como se muestra en la siguiente captura de pantalla.

    ![screenshot-internet-explorer-address-bar-padlock-symbol](./media/andr-missing-cert-ie-padlock-symbol.png)

    Si no ve el símbolo del candado, deténgase y póngase en contacto con el equipo de soporte técnico de su empresa. El candado significa que la sesión iniciada es segura, por lo que no debe continuar a menos que vea dicho símbolo.

4. Elija **Ver certificados**.

    ![screenshot-internet-explorer-view-certificases-button-on-website-identification-dialog](./media/andr-missg-cert-ie-view-cert-button.png)

5. Elija la pestaña **Ruta de certificación** e identifique el certificado que tiene que obtener desde Internet. El nombre del certificado que necesita estará en la misma posición que el que está resaltado en la captura de pantalla del ejemplo anterior.

6. Con un motor de búsqueda como Bing o Google, busque el nombre del certificado que falta que identificó en la sección anterior. El certificado puede terminar con diferentes "extensiones", como ".crt", ".pem", etc.

7. Descargue el certificado raíz desde el sitio web.

8. Una vez que descargue el certificado, arrastre hacia abajo desde la parte superior del dispositivo para abrir las notificaciones y luego pulse el nombre del certificado en la lista de notificaciones.

4. En el cuadro de diálogo **Nombre del certificado** que se muestra en la siguiente captura de pantalla, acepte el nombre de certificado predeterminado.

5. Asegúrese de que **Uso de credencial** está configurado como **Usada para VPN y aplicaciones** y pulse en **Aceptar**.

    ![screenshot-certificate-name-dialog-showing-certificate-name](./media/andr-missing-cert-cert-name.png)

6. Cierre la aplicación del portal de empresa.

7. Vuelva a abrir la aplicación del portal de empresa. Ahora debería poder iniciar sesión en la aplicación Portal de empresa. Si necesita ayuda, póngase en contacto con el equipo de soporte técnico de su empresa.

Si aparece el mismo mensaje que indica que "falta un certificado" como el que se ha mostrado anteriormente, y ya ha seguido el procedimiento, probablemente todavía haya otro certificado que el equipo de soporte técnico de su empresa necesitará ayudarle a instalar. Póngase en contacto con el equipo de soporte técnico de su empresa para obtener ayuda con la información de contacto disponible en el [sitio web del Portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).

## <a name="next-steps"></a>Pasos siguientes  

¿Aún necesita ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  
