---
title: Obtener una clave de recuperación para un dispositivo macOS desde el sitio web de Portal de empresa de Intune
description: Vea la clave de recuperación de un dispositivo macOS inscrito y administrado.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/04/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 1e7831712b4c07d015aa0f587ff6ba6183940897
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75855243"
---
# <a name="get-a-recovery-key-for-a-macos-device"></a>Obtención de una clave de recuperación para un dispositivo macOS

Use el sitio web de Portal de empresa para obtener una clave de recuperación para el dispositivo de macOS bloqueado. Si olvida la contraseña del dispositivo, puede iniciar sesión en el Portal de empresa desde otro dispositivo para recuperar la clave.  

## <a name="get-recovery-key-from-company-portal-website"></a>Obtención de la clave de recuperación desde Portal de empresa sitio web

Esta opción está disponible para los dispositivos cifrados por su organización mediante FileVault. No está disponible para los dispositivos que ha cifrado personalmente.

1. En cualquier dispositivo, inicie sesión en el [sitio web de portal de empresa](https://portal.manage.microsoft.com) y seleccione el botón de **menú** > **dispositivos**.  
2. Seleccione el dispositivo macOS cifrado.  
3. Seleccione **Obtener clave de recuperación**.  

    ![Captura de pantalla del sitio web de Portal de empresa, resaltando la sección obtener clave de recuperación.](./media/1907-recovery2-cpweb-intune.PNG)  

4. Aparecerá la clave de recuperación.

    ![Captura de pantalla del sitio web de Portal de empresa, que muestra la clave de recuperación.](./media/1907-recovery-cpweb-intune.PNG)  

    Por motivos de seguridad, la clave desaparecerá después de cinco minutos. Para volver a ver la clave, seleccione **obtener clave de recuperación**.

Si no se encuentra una clave pero el dispositivo está correctamente cifrado, póngase en contacto con el personal de soporte técnico de su organización. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  

## <a name="get-recovery-key-from-company-portal-app-for-ios"></a>Obtención de la clave de recuperación de Portal de empresa aplicación para iOS

Puede recuperar su clave de recuperación personal (clave FileVault) mediante la aplicación Portal de empresa para iOS. El dispositivo que tiene la clave de recuperación personal debe inscribirse en Intune y cifrarse con FileVault a través de Intune. Esta opción no está disponible para los dispositivos que ha cifrado personalmente. 

Con la aplicación Portal de empresa, puede abrir la vista Web de Safari y recuperar su clave de recuperación personal. 

1. Abra Portal de empresa.
2. Haga clic en **obtener clave de recuperación**.

    ![Captura de pantalla de Portal de empresa aplicación para iOS, que muestra la clave de recuperación](./media/get-recovery-key-cpweb-02.png)  

El sitio web de Portal de empresa se abre en la vista Web de Safari y muestra la clave. 

## <a name="it-pro-support"></a>Soporte para profesionales de TI

Si es una persona de soporte técnico de ti y desea configurar y administrar el cifrado de FileVault para dispositivos macOS, consulte [uso del cifrado de dispositivos con Intune](/intune/protect/encrypt-devices).

## <a name="next-steps"></a>Pasos siguientes

Averigüe qué más puede hacer en el sitio web de Portal de empresa. Consulte [uso del sitio web de portal de empresa de Intune](using-the-intune-company-portal-website.md) para ver la lista de acciones.  

¿Aún necesita ayuda? Póngase en contacto con el personal de soporte técnico de ti. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  
