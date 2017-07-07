---
title: "Configuración de la integración de Skycure con Intune"
description: "Configure la integración de Skycure con Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 93722f66-7641-4a3f-b1fb-3a0a58a36675
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1d5a59f34a5dacdc2e1a0d5c6601b4ede1a908e4
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="set-up-the-skycure-integration-with-intune"></a>Configuración de la integración de Skycure con Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Debe agregar las aplicaciones de Skycure en Azure AD para tener capacidades de inicio de sesión único.

## <a name="before-you-begin"></a>Antes de comenzar

### <a name="azure-ad-account-used-to-integrate-intune-and-skycure"></a>Cuenta de Azure AD utilizada para integrar Intune y Skycure

-   Asegúrese de que la cuenta de Azure AD esté configurada correctamente en la [consola de administración de Skycure](https://aad.skycure.com) antes de iniciar el proceso de configuración de Skycure Basic.

### <a name="full-integration-vs-read-only"></a>Integración completa en comparación con Solo lectura

Skycure admite dos modos de integración con Intune:

-   **Integración de solo lectura (configuración básica):** solo crea un inventario de dispositivos de Azure Active Directory y los rellena en la consola de Skycure.
<br>
    -   Si las casillas **Report the health and risk of devices to Intune** (Notificar el estado y riesgo de los dispositivos a Itune) y **Also report security incidents to Intune** (También informar incidentes de seguridad a Intune) no están seleccionadas en la consola de administración de Skycure, la integración es de solo lectura y, por tanto, nunca cambiará el estado de un dispositivo (compatible o no compatible) en Intune.
<br></br>
-   **Integración completa:** le permite a Skycure informar a los dispositivos sobre riesgos y detalles de seguridad del incidente a Intune, lo que crea una comunicación bidireccional entre ambos servicios en la nube.

### <a name="how-the-skycure-apps-are-used-with-azure-ad-and-intune"></a>¿Cómo se usan las aplicaciones de Skycure con Azure AD y Intune?

-   **Aplicación de iOS:** permite a los usuarios finales iniciar sesión en Azure AD mediante una aplicación de iOS.

-   **Aplicación de Android:** permite a los usuarios finales iniciar sesión en Azure AD mediante una aplicación de Android.

-   **Aplicación de administración:** se trata de la aplicación de varios inquilinos de Skycure Azure AD que permite la comunicación de servicio a servicio con Intune.

## <a name="to-set-up-the-read-only-integration-between-intune-and-skycure"></a>Para configurar la integración de solo lectura entre Intune y Skycure

> [!IMPORTANT]
> Las credenciales de administrador de Skycure son un correo electrónico que debe pertenecer a un usuario válido en Azure Active Directory, de lo contrario, el inicio de sesión no se realizará. Skycure usa Azure Active Directory para autenticar que el administrador use el inicio de sesión único (SSO).

1.  Vaya a la [consola de administración de Skycure](https://aad.skycure.com).

2.  Escriba las **credenciales de administrador de Skycure** y, a continuación, haga clic en **Continuar**.

3.  Vaya a **Configuración**, elija **Configuración básica** en **Integración con Intune**.

4.  En la etiqueta **Aplicación de iOS**, haga clic en **Agregar a Active Directory**.

    ![Aplicación de iOS en la consola de administración de Skycure](../media/mtp/skycure-setup-1.png)

5.  Se abre la página de inicio de sesión, escriba sus credenciales de Intune y, luego, haga clic en **Aceptar**.

    ![Solicitud de inicio de sesión en Intune de aplicación de iOS](../media/mtp/skycure-setup-2.png)

6.  Una vez agregada la aplicación en Azure AD, puede ver una indicación de que la aplicación se agregó correctamente a Azure AD en la consola de administración de Skycure.

    ![Pantalla de completado de la aplicación de iOS](../media/mtp/skycure-setup-3.png)

> [!NOTE]
> Repita el mismo proceso para las aplicaciones de **Skycure Android** y de **Administración**.

### <a name="add-an-azure-ad-security-group-into-skycure"></a>Adición de un grupo de seguridad de Azure AD a Skycure

Debe agregar un grupo de seguridad de Azure AD que contenga todos los dispositivos que ejecutan Skycure.

1.  Escriba y seleccione todos los grupos de seguridad de los dispositivos que ejecutan Skycure y, a continuación, haga clic en **Aplicar cambios**.

    ![Configuración de la consola de administración de Skycure del grupo de seguridad](../media/mtp/skycure-setup-4.png)

Skycure sincroniza los dispositivos que ejecutan el servicio Mobile Threat Defense con los grupos de seguridad de Azure AD.

![Configuración del grupo de seguridad completada en la consola de administración de Skycure](../media/mtp/skycure-setup-5.png)

## <a name="set-up-the-full-integration-between-intune-and-skycure"></a>Configuración de la integración completa entre Intune y Skycure

1.  Vaya a la [consola de administración de Skycure](https://aad.skycure.com).

2.  Escriba las **credenciales de administrador de Skycure** y, a continuación, haga clic en **Continuar**.

3.  Vaya a **Configuración**, elija **Configuración completa** en **Integración con Intune**.

4.  Utilice la siguiente configuración:

    a.  Informar del estado y el riesgo del dispositivo a Intune

    b.  También informar de los incidentes de seguridad a Intune

5.  Haga clic en **Aplicar cambios**.

    ![Integración completa de Skycure completada](../media/mtp/skycure-setup-6.png)

## <a name="next-steps"></a>Pasos siguientes

[Habilitación de Mobile Threat Defense de Skycure en Intune](/intune-classic/deploy-use/enable-skycure-mobile-threat-defense-in-intune)
