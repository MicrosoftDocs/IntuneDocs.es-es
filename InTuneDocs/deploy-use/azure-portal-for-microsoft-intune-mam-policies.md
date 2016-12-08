---
title: Portal de Azure para directivas de MAM | Microsoft Intune
description: "Cree directivas de administración de aplicaciones móviles con Azure Portal. Las directivas que cree aquí se pueden aplicar a dispositivos con o sin inscripción en Intune."
keywords: 
author: karthikaraman
ms.author: karaman
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
ms.sourcegitcommit: 03410d1e82cfeb8d354ee1d010ada07ca86191bc
ms.openlocfilehash: e9d917401a8927099bdf8558e9f7e7185351f709


---

# <a name="azure-portal-for-microsoft-intune-mam-policies"></a>Portal de Azure para directivas de MAM de Microsoft Intune

## <a name="use-the-azure-portal"></a>Usar Azure Portal
Azure Portal le permite crear y administrar directivas de administración de aplicaciones móviles (MAM).

En el Portal de Azure se pueden crear directivas de MAM aplicables a los siguientes elementos:
- Aplicaciones que se ejecutan en dispositivos **inscritos y administrados con Intune**.

- Aplicaciones que se ejecutan en dispositivos **no inscritos** en ninguna solución de MDM
- Aplicaciones que se ejecutan en dispositivos **inscritos en una solución de MDM de terceros**.

>[!IMPORTANT]


> Si usa la consola de administración de Intune para administrar los dispositivos, puede crear una directiva de MAM que admita aplicaciones para los dispositivos inscritos en Intune mediante la [consola de administración de Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).

> Es posible que no vea todas las configuraciones de directivas de MAM en la consola de administración de Intune. El Portal de Azure es la nueva consola de administración para crear directivas de MAM. Si crea directivas de MAM en la consola de administración de Intune y en Azure Portal, la directiva de Azure Portal se aplica a las aplicaciones y se implementa para los usuarios.


## <a name="sign-in-to-the-azure-portal-and-customize-your-start-page"></a>Iniciar sesión en Azure Portal y personalizar la página de inicio

1.  Vaya a [Azure Portal](https://portal.azure.com) e inicie sesión con sus credenciales de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

    ![Captura de pantalla de la página de inicio de sesión de Azure Portal](../media/AppManagement/AzurePortal_MAMSigninPage.png)

2.  Después de iniciar sesión correctamente, verá el **Panel**. La página **Panel** se puede personalizar.

    ![Captura de pantalla del panel del Portal de Azure](../media/AppManagement/AzurePortal_MAMStartboard_NoMAM.png)

3.  En el menú **Examinar**, busque **Intune**.![Captura de pantalla del menú Examinar con Intune resaltado](../media/AppManagement/AzurePortal_MAM_Browse_Intune.png)

4.  Elija **Intune** > **Administración de aplicaciones móviles de Intune** > **Configuración**.

    ![Captura de pantalla de la hoja Administración de aplicaciones móviles de Intune](../media/AppManagement/AzurePortal_MAM_Mainblade.png)

    > [!TIP]

    > Para anclar una hoja a la página **Inicio** , puede usar la opción **anclar** de la hoja. Haga clic en el icono de anclar de la **hoja de administración de aplicaciones móviles de Intune** para anclarla a la página **Inicio**.

    ![Captura de pantalla de la hoja Administración de aplicaciones móviles de Intune con el icono de anclaje resaltado](../media/AppManagement/AzurePortal_MAM_PinBladeAction.png)

    ![Captura de pantalla del panel con el icono de Intune anclado](../media/AppManagement/AzurePortal_MAM_Startboard_withMAM.png)
## <a name="next-steps"></a>Pasos siguientes
[Preparación para configurar directivas de administración de aplicaciones móviles](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Nov16_HO2-->


