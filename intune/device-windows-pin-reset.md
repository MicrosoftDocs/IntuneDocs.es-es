---
title: "Restablecer código de acceso en dispositivos Windows con Intune"
titleSuffix: Intune on Azure
description: "Aprenda a usar Intune para restablecer el código de acceso en dispositivos Windows integrados con el \"Servicio de restablecimiento del PIN de Microsoft\"."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/05/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5027d012-d6c2-4971-a9ac-217f91d67d87
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3688eef68fc9dcfced976db02c8d50126fa30da8
ms.sourcegitcommit: fd5b7aa26446d2fa92c21638cb29371e43fe169f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2017
---
# <a name="reset-the-passcode-on-windows-devices-integrated-with-the-microsoft-pin-reset-service-using-intune"></a>Restablecer el código de acceso en dispositivos Windows integrados con el Servicio de restablecimiento del PIN de Microsoft mediante Intune

La capacidad de restablecimiento del código de acceso para dispositivos Windows se integra con el Servicio de restablecimiento del PIN de Microsoft para permitir la generación de un nuevo código de acceso para dispositivos con Windows 10 Mobile. Los dispositivos deben tener Windows 10 Creators Update o versiones posteriores.


## <a name="before-you-start"></a>Antes de empezar

Para restablecer de forma remota el código de acceso en los dispositivos Windows que administre, debe incorporar el Servicio de restablecimiento del PIN al inquilino de Intune y configurar los dispositivos que administra. Siga estas instrucciones para lograr esa configuración:

### <a name="connect-intune-with-the-pin-reset-service"></a>Conectar Intune al Servicio de restablecimiento del PIN

1. Visite el [sitio web de integración del Servicio de restablecimiento del PIN de Microsoft](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=b8456c59-1230-44c7-a4a2-99b085333e84&resource=https%3A%2F%2Fgraph.windows.net&redirect_uri=https%3A%2F%2Fcred.microsoft.com&state=e9191523-6c2f-4f1d-a4f9-c36f26f89df0&prompt=admin_consent) e inicie sesión con la cuenta de administrador de inquilino que usa para administrar el inquilino de Intune.
2. Después de iniciar sesión, haga clic en **Acepto** para dar su consentimiento a que el Servicio del restablecimiento del PIN acceda a la cuenta.<br>
![Página de permisos del Servicio de restablecimiento del PIN](./media/pin-reset-service-application.png)
3. En el portal de Azure, puede comprobar que Intune y el Servicio de restablecimiento del PIN se han integrado en la hoja Aplicaciones empresariales - Todas las aplicaciones, como se muestra en la captura de pantalla siguiente:<br>
![Aplicación del Servicio de restablecimiento del PIN en Azure](./media/pin-reset-service-home-screen.png)
4. Inicie sesión en [este sitio web](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=9115dd05-fad5-4f9c-acc7-305d08b1b04e&resource=https%3A%2F%2Fcred.microsoft.com%2F&redirect_uri=ms-appx-web%3A%2F%2FMicrosoft.AAD.BrokerPlugin%2F9115dd05-fad5-4f9c-acc7-305d08b1b04e&state=6765f8c5-f4a7-4029-b667-46a6776ad611&prompt=admin_consent) con las credenciales de administrador de inquilino de Intune y luego vuelva a elegir **Acepto** para dar su consentimiento a que el servicio acceda a la cuenta.

### <a name="configure-windows-devices-to-use-pin-reset"></a>Configurar dispositivos Windows para que usen el restablecimiento del PIN

Para configurar el restablecimiento del PIN en los dispositivos Windows que administra, use una [directiva de dispositivo personalizada de Windows 10 de Intune](custom-settings-windows-10.md) para habilitar la característica. Configure la directiva mediante los siguientes proveedores de servicios de configuración de directivas de Windows (CSP):


- **Para usuarios**: **./User/Vendor/MSFT/PassportForWork/<tenant ID>/Policies/EnablePinRecovery**
- **Para dispositivos**: **./Device/Vendor/MSFT/PassportForWork/<tenant ID>/Policies/EnablePinRecovery**

Los valores de estos CSP deben establecerse en ambos casos en **True**.

## <a name="steps-to-reset-the-passcode"></a>Pasos para restablecer el código de acceso

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Dispositivos**.
4. En la hoja **Dispositivos**, elija **Administrar** > **Todos los dispositivos**.
5. Seleccione el dispositivo cuyo código de acceso quiere restablecer y, luego, en la hoja de propiedades del dispositivo, elija **Nuevo código de acceso**.
6. En la confirmación que aparece, elija **Sí**. El código de acceso se genera y se muestra en el portal durante los próximos siete días.

## <a name="next-steps"></a>Pasos siguientes

Si se produce un error al restablecer el código de acceso, se proporciona un vínculo en el portal para obtener más información.

