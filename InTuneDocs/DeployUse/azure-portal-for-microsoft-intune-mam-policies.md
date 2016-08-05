---
title: Portal de Azure para directivas de MAM | Microsoft Intune
description: "Cree directivas de administración de aplicaciones móviles con el Portal de Azure. Las directivas que cree aquí se pueden aplicar a dispositivos con o sin inscripción en Intune."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7d6dae94-a833-40b7-9016-14ea234bb33c
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: be1ebcdf2514e45d383dd49890e0e21acf6ede44
ms.openlocfilehash: 1ddb7a30a6f23a3f3d754bd18975c50f32662578


---

# Portal de Azure para directivas de MAM de Microsoft Intune
## Acceso al Portal de Azure
En el **Portal de Azure** se pueden crear y administrar directivas de administración de aplicaciones móviles.

En el Portal de Azure se pueden crear directivas de MAM aplicables a los siguientes elementos:
- Aplicaciones que se ejecutan en dispositivos **inscritos y administrados con Intune**.
- Aplicaciones que se ejecutan en dispositivos **no inscritos** en ninguna solución de MDM
- Aplicaciones que se ejecutan en dispositivos **inscritos en una solución de MDM de terceros**.

>[!IMPORTANT]

> Si actualmente usa la consola de administración de Intune para administrar sus dispositivos, puede crear una directiva de MAM que admita aplicaciones para los dispositivos inscritos en Intune mediante la [consola de administración de Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).

> Es posible que no vea todas las configuraciones de directivas de MAM en la consola de administración de Intune. El Portal de Azure es la nueva consola de administración para crear directivas de MAM. Si crea directivas de MAM en la consola de administración de Intune y en el portal de Azure, la directiva del portal de Azure se aplica a las aplicaciones y se implementa para los usuarios.

## Iniciar sesión en el Portal de Azure y personalizar la página de inicio

1.  Vaya al [Portal de Azure](https://portal.azure.com) e inicie sesión con sus credenciales de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

    ![Captura de pantalla de la página de inicio de sesión del Portal de Azure](../media/AppManagement/AzurePortal_MAMSigninPage.png)

2.  Tras iniciar sesión correctamente, aparecerá el **Panel**. La página **Panel** se puede personalizar.

    ![Captura de pantalla del panel del Portal de Azure](../media/AppManagement/AzurePortal_MAMStartboard_NoMAM.png)

3.  En el menú **Examinar**, busque **Intune**.![Captura de pantalla del menú Examinar con Intune resaltado](../media/AppManagement/AzurePortal_MAM_Browse_Intune.png)

4.  Elija **Intune > Administración de aplicaciones móviles de Intune > Configuración**.

    ![Captura de pantalla de la hoja Administración de aplicaciones móviles de Intune](../media/AppManagement/AzurePortal_MAM_Mainblade.png)

    > [!TIP]
    > Para anclar una hoja a la página **Inicio** , puede usar la opción **anclar** de la hoja.  Haga clic en el icono del ancla de la **Hoja de administración de aplicaciones móviles de Intune**para anclarlo a la página **Inicio** .

    ![Captura de pantalla de la hoja Administración de aplicaciones móviles de Intune con el icono de anclaje resaltado](../media/AppManagement/AzurePortal_MAM_PinBladeAction.png)

    ![Captura de pantalla del panel con el icono de Intune anclado](../media/AppManagement/AzurePortal_MAM_Startboard_withMAM.png)
## Pasos siguientes
[Get ready to configure mobile app management policies (Preparación para configurar directivas de administración de aplicaciones móviles)](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Jul16_HO5-->


