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
ms.sourcegitcommit: 9eb7e79bee2bc36dffab97ffdb6f665218bc739e
ms.openlocfilehash: 0acef421f179ebf922ec8af71ba336e3e5f96bd2


---

# Portal de Azure para directivas de MAM de Microsoft Intune
## Usar Azure Portal
Azure Portal le permite crear y administrar directivas de administración de aplicaciones móviles (MAM).

En el Portal de Azure se pueden crear directivas de MAM aplicables a los siguientes elementos:
- Aplicaciones que se ejecutan en dispositivos **inscritos y administrados con Intune**.
- Aplicaciones que se ejecutan en dispositivos **no inscritos** en ninguna solución de MDM
- Aplicaciones que se ejecutan en dispositivos **inscritos en una solución de MDM de terceros**.

>[!IMPORTANT]

> Si usa la consola de administración de Intune para administrar los dispositivos, puede crear una directiva de MAM que admita aplicaciones para los dispositivos inscritos en Intune mediante la [consola de administración de Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).

> Es posible que no vea todas las configuraciones de directivas de MAM en la consola de administración de Intune. El Portal de Azure es la nueva consola de administración para crear directivas de MAM. Si crea directivas de MAM en la consola de administración de Intune y en Azure Portal, la directiva de Azure Portal se aplica a las aplicaciones y se implementa para los usuarios.

## Iniciar sesión en Azure Portal y personalizar la página de inicio

1.  Vaya a [Azure Portal](https://portal.azure.com) e inicie sesión con sus credenciales de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

    ![Captura de pantalla de la página de inicio de sesión de Azure Portal](../media/AppManagement/AzurePortal_MAMSigninPage.png)

2.  Después de iniciar sesión, verá la página **Panel**. La página **Panel** se puede personalizar.

    ![Captura de pantalla del panel del Portal de Azure](../media/AppManagement/AzurePortal_MAMStartboard_NoMAM.png)

3.  En el menú **Examinar**, busque **Intune**.![Captura de pantalla del menú Examinar con Intune resaltado](../media/AppManagement/AzurePortal_MAM_Browse_Intune.png)

4.  Elija **Intune** > **Administración de aplicaciones móviles de Intune** > **Configuración**.

    ![Captura de pantalla de la hoja Administración de aplicaciones móviles de Intune](../media/AppManagement/AzurePortal_MAM_Mainblade.png)

    > [!TIP]
    > Para anclar una hoja a la página **Inicio**, elija el icono de anclar en la hoja **Administración de aplicaciones móviles de Intune**.

    ![Captura de pantalla de la hoja Administración de aplicaciones móviles de Intune con el icono de anclaje resaltado](../media/AppManagement/AzurePortal_MAM_PinBladeAction.png)

    ![Captura de pantalla del panel con el icono de Intune anclado](../media/AppManagement/AzurePortal_MAM_Startboard_withMAM.png)
## Pasos siguientes
[Get ready to configure mobile app management policies (Preparación para configurar directivas de administración de aplicaciones móviles)](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Oct16_HO3-->


