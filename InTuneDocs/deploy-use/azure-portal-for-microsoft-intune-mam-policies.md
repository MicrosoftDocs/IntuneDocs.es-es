---
title: Azure Portal para directivas de MAM | Microsoft Docs
description: "Cree directivas de administración de aplicaciones móviles con Azure Portal. Las directivas que cree aquí se pueden aplicar a dispositivos con o sin inscripción en Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7d6dae94-a833-40b7-9016-14ea234bb33c
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: fe44466fbcef67d02b16d3d2d335f657251451d3
ms.openlocfilehash: fa8d839da1cf0b2d207edc0b28de8a714ba0df02


---

# <a name="azure-portal-for-microsoft-intune-mam-policies"></a>Portal de Azure para directivas de MAM de Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Azure Portal se usa para crear y administrar directivas de administración de aplicaciones móviles (MAM) para:

- Aplicaciones que se ejecutan en dispositivos **inscritos y administrados con Intune**.

- Aplicaciones que se ejecutan en dispositivos **no inscritos** en ninguna solución de MDM
- Aplicaciones que se ejecutan en dispositivos **inscritos en una solución de MDM de terceros**.

>[!IMPORTANT]
> Azure Portal es la nueva consola de administración para crear directivas MAM, pero también puede crear una directiva MAM que admita aplicaciones para dispositivos inscritos en Intune mediante el uso de la [consola de administración de Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) para escenarios MDM.

> Es posible que no vea todas las configuraciones de directivas de MAM disponibles en la consola de administración de Intune. Además, si crea directivas MAM en la consola de administración de Intune y en Azure Portal, las directivas creadas en Azure Portal invalidarán las creadas en la consola de administración de Intune. En este escenario, las directivas de MAM de Azure Portal se aplicarán a las aplicaciones y se implementarán en usuarios.


## <a name="sign-in-to-the-azure-portal-and-customize-your-start-page"></a>Iniciar sesión en Azure Portal y personalizar la página de inicio

1.  Vaya a [Azure Portal](https://portal.azure.com) e inicie sesión con sus credenciales de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

    ![Captura de pantalla de la página de inicio de sesión de Azure Portal](../media/AppManagement/AzurePortal_MAMSigninPage.png)

2.  Después de iniciar sesión correctamente, verá el **Panel**. La página **Panel** se puede personalizar.

    ![Captura de pantalla del panel del Portal de Azure](../media/AppManagement/AzurePortal_MAMStartboard_NoMAM.png)

3.  En el menú **Examinar**, busque **Intune**.

    ![Captura de pantalla del menú Examinar con Intune resaltado](../media/AppManagement/MAM-Azure-Portal-1.png)

4.  Elija **Intune** > **Administración de aplicaciones móviles de Intune** > **Configuración**.

    ![Captura de pantalla de la hoja Administración de aplicaciones móviles de Intune](../media/AppManagement/MAM-Azure-Portal-2.png)

5. (Opcional): Para anclar una hoja a la página **Inicio** , puede usar la opción **anclar** de la hoja. Haga clic en el icono de anclar de la **hoja de administración de aplicaciones móviles de Intune** para anclarla a la página **Inicio**.

    ![Captura de pantalla de la hoja Administración de aplicaciones móviles de Intune con el icono de anclaje resaltado](../media/AppManagement/AzurePortal_MAM_PinBladeAction.png)

    ![Captura de pantalla del panel con el icono de Intune anclado](../media/AppManagement/AzurePortal_MAM_Startboard_withMAM.png)

## <a name="next-steps"></a>Pasos siguientes
[Preparación para configurar directivas de administración de aplicaciones móviles](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Jan17_HO2-->


