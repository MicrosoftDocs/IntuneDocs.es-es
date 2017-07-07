---
title: Portal de Azure para directivas de MAM
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
ms.custom: intune-classic
ms.openlocfilehash: 00328885d7fb5e75ffe894326591c0225f4b07ab
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="azure-portal-for-intune-app-protection-policies"></a>Azure Portal para directivas de protección de aplicaciones de Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Azure Portal se utiliza para crear y administrar directivas de protección de aplicaciones para:

- Aplicaciones que se ejecutan en dispositivos **inscritos y administrados con Intune**.

- Aplicaciones que se ejecutan en dispositivos **no inscritos** en ninguna solución de MDM
- Aplicaciones que se ejecutan en dispositivos **inscritos en una solución de MDM de terceros**.

>[!IMPORTANT]
> Azure Portal es la nueva consola de administración para crear directivas de protección de aplicaciones, pero también puede crear una directiva de protección de aplicaciones que admita aplicaciones para dispositivos inscritos en Intune mediante el uso de la [consola de administración de Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) para escenarios MDM.

> Es posible que no vea todas las opciones de configuración de las directivas de protección de aplicaciones disponibles en la consola de administración de Intune. Además, si crea directivas de protección de aplicaciones en la consola de administración de Intune y en Azure Portal, las directivas creadas en Azure Portal invalidarán aquellas creadas en la consola de administración de Intune. En este caso, las directivas de protección de aplicaciones de Azure Portal se aplicarán a las aplicaciones y se implementarán para los usuarios.


## <a name="sign-in-to-the-azure-portal-and-customize-your-start-page"></a>Iniciar sesión en Azure Portal y personalizar la página de inicio

1.  Vaya a [Azure Portal](https://portal.azure.com) e inicie sesión con sus credenciales de Intune.

    ![Captura de pantalla de la página de inicio de sesión de Azure Portal](../media/AppManagement/AzurePortal_MAMSigninPage.png)

2.  Después de iniciar sesión correctamente, verá el **Panel**. La página **Panel** se puede personalizar.

    ![Captura de pantalla del panel del Portal de Azure](../media/AppManagement/AzurePortal_MAMStartboard_NoMAM.png)

3.  Elija **Más servicios** en el menú izquierdo y, luego, escriba **Intune** en el filtro del cuadro de texto.

    ![Captura de pantalla del menú Examinar con Intune resaltado](../media/AppManagement/MAM-Azure-Portal-1.png)

4.  Elija **Protección de aplicaciones de Intune** > **Administración de aplicaciones móviles de Intune** > **Toda la configuración**.

    ![Captura de pantalla de la hoja Administración de aplicaciones móviles de Intune](../media/AppManagement/MAM-Azure-Portal-2.png)

5. (Opcional): Para anclar una hoja a la página **Inicio** , puede usar la opción **anclar** de la hoja. Haga clic en el icono de anclar de la **hoja de administración de aplicaciones móviles de Intune** para anclarla a la página **Inicio**.

    ![Captura de pantalla de la hoja Administración de aplicaciones móviles de Intune con el icono de anclaje resaltado](../media/AppManagement/AzurePortal_MAM_PinBladeAction.png)

    ![Captura de pantalla del panel con el icono de Intune anclado](../media/AppManagement/AzurePortal_MAM_Startboard_withMAM.png)

## <a name="next-steps"></a>Pasos siguientes
[Preparativos para la configuración de directivas de protección de aplicaciones](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)
