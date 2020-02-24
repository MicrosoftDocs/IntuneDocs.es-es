---
title: 'Restablecimiento del código de acceso en dispositivos Windows con Microsoft Intune: Azure | Microsoft Docs'
description: Para restablecer el código de acceso en los dispositivos Windows, instale el Servicio de restablecimiento del PIN de Microsoft y el Cliente de restablecimiento del PIN de Microsoft, cree una directiva de dispositivo mediante el identificador de directorio de Azure Active Directory y, después, restablezca el código de acceso en Azure Portal con Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/07/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5027d012-d6c2-4971-a9ac-217f91d67d87
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c4b3313d5ec7fe81944431276a63bfafb7a1b3dc
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/17/2020
ms.locfileid: "77413626"
---
# <a name="reset-the-passcode-on-windows-devices-using-intune"></a>Restablecimiento del código de acceso en dispositivos Windows con Intune

Puede restablecer el código de acceso para los dispositivos Windows. La característica de restablecimiento del código de acceso usa el Servicio de restablecimiento del PIN de Microsoft para generar un código de acceso nuevo para los dispositivos que ejecutan Windows 10 Mobile. 

## <a name="supported-platforms"></a>Plataformas compatibles

- Windows 10 Mobile que ejecuta Creators Update y versiones posteriores (unido a Azure AD).

**No** se admiten las plataformas siguientes:
- Windows
- iOS
- macOS
- Android

## <a name="authorize-the-pin-reset-services"></a>Autorizar los servicios de restablecimiento del PIN

Para restablecer el código de acceso en los dispositivos Windows, incorpore el servicio de restablecimiento del PIN al inquilino de Intune.

1. Vaya a la [producción del Servicio de restablecimiento del PIN de Microsoft](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=b8456c59-1230-44c7-a4a2-99b085333e84&resource=https%3A%2F%2Fgraph.windows.net&redirect_uri=https%3A%2F%2Fcred.microsoft.com&state=e9191523-6c2f-4f1d-a4f9-c36f26f89df0&prompt=admin_consent) e inicie sesión con la cuenta de administrador de inquilinos.
2. **Acepte** el consentimiento para que el servicio de restablecimiento del PIN tenga acceso a la cuenta: ![Aceptar la solicitud de permisos para el Servicio de restablecimiento del PIN](./media/device-windows-pin-reset/pin-reset-service-home-screen.png)
3. Vaya a la [producción del cliente del restablecimiento del PIN de Microsoft](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=9115dd05-fad5-4f9c-acc7-305d08b1b04e&resource=https%3A%2F%2Fcred.microsoft.com%2F&redirect_uri=ms-appx-web%3A%2F%2FMicrosoft.AAD.BrokerPlugin%2F9115dd05-fad5-4f9c-acc7-305d08b1b04e&state=6765f8c5-f4a7-4029-b667-46a6776ad611&prompt=admin_consent) e inicie sesión con la cuenta de administrador de inquilinos. **Acepte** el consentimiento para que el cliente de restablecimiento del PIN tenga acceso a la cuenta.
4. En [Azure Portal](https://portal.azure.com), confirme que los servicios de restablecimiento del PIN aparecen en Aplicaciones empresariales (Todas las aplicaciones): ![Página de permisos del servicio de restablecimiento del PIN](./media/device-windows-pin-reset/pin-reset-service-application.png)

> [!NOTE]
> Después de aceptar las solicitudes de restablecimiento del PIN, es posible que obtenga un mensaje `Page not found`, o bien puede aparecer como si no ocurriera nada. Este comportamiento es normal. Asegúrese de confirmar que las dos aplicaciones de restablecimiento del PIN aparecen para el inquilino.

## <a name="configure-windows-devices-to-use-pin-reset"></a>Configurar dispositivos Windows para que usen el restablecimiento del PIN

Para configurar el restablecimiento del PIN en los dispositivos Windows que administra, use una [directiva de dispositivo personalizada de Windows 10 de Intune](../configuration/custom-settings-windows-10.md). Configure la directiva mediante el siguiente proveedor de servicios de configuración de directivas de Windows (CSP):

**Uso de la directiva de dispositivo** - `./Device/Vendor/MSFT/PassportForWork/*tenant ID*/Policies/EnablePinRecovery`

Reemplace *id. de inquilino* por el identificador de directorio de Azure AD, que aparece en las **Propiedades** de Azure Active Directory en [Azure Portal](https://portal.azure.com).

Establezca el valor de este CSP en **True**.

> [!TIP]
> Después de crear la directiva, se asigna (o implementa) a un grupo. La directiva se puede asignar a grupos de usuarios o grupos de dispositivos. Si se asigna a un grupo de usuarios, es posible que el grupo incluya usuarios que tienen otros dispositivos, como iOS/iPadOS. Técnicamente, la directiva no se aplica, pero estos dispositivos se siguen incluyendo en los detalles del estado.

## <a name="reset-the-passcode"></a>Restablecimiento del código de acceso

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431). 
2. Seleccione **Dispositivos** y, después, **Todos los dispositivos**.
3. Seleccione el dispositivo en el que quiere restablecer el código de acceso. En las propiedades del dispositivo, seleccione **Restablecer código de acceso**.
4. Seleccione **Sí** para confirmar. El código de acceso se genera y se muestra en el portal durante los próximos siete días.

## <a name="next-step"></a>Paso siguiente

Si se produce un error al restablecer el código de acceso, se proporciona un vínculo en el portal con más información.
