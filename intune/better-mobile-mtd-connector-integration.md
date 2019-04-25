---
title: Configuración de la integración de Better Mobile con Intune
titleSuffix: Intune on Azure
description: Integración del conector de Better Mobile con Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/25/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 282fb642e147353f50e730884037815ef2dc16aa
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61508503"
---
# <a name="integrate-better-mobile-with-intune"></a>Integración de Better Mobile con Intune

Complete estos pasos para integrar la solución Better Mobile Threat Defense con Intune.

## <a name="before-you-begin"></a>Antes de comenzar

> [!NOTE]
> Los pasos siguientes debe completarlos en la [consola de administración de Better Mobile](https://aad.bmobi.net).

Antes de iniciar el proceso de integración de Better Mobile con Intune, asegúrese de disponer de lo siguiente:

-   Suscripción a Microsoft Intune

-   Credenciales de administrador de Azure Active Directory para conceder los permisos siguientes:

    -   Iniciar sesión y leer el perfil del usuario

    -   Obtener acceso al directorio con el usuario que tiene la sesión iniciada

    -   Leer datos de directorio

    -   Enviar información del dispositivo a Intune

-   Credenciales de administrador para tener acceso a la consola de administración de Better Mobile.

### <a name="better-mobile-app-authorization"></a>Autorización de aplicación de Better Mobile

El proceso de autorización de la aplicación Better Mobile es el siguiente:

-   Permita que el servicio de Better Mobile comunique a Intune la información relacionada con el estado de mantenimiento del dispositivo.

-   Better Mobile se sincroniza con la pertenencia a grupos de inscripción de Azure AD para rellenar la base de datos de su dispositivo.

-   Permita que la consola de administración de Better Mobile use el inicio de sesión único (SSO) de Azure AD.

-   Permita que la aplicación de Better Mobile inicie sesión con el SSO de Azure AD.

## <a name="to-set-up-better-mobile-integration"></a>Para configurar la integración de Better Mobile

1. Vaya a la [consola de administración de Better Mobile](https://aad.bmobi.net) e inicie sesión con sus credenciales.
2. Elija **Integration** (Integración) > **EMM/MDM** > **ADD ACCOUNT** (AGREGAR CUENTA).

     ![Imagen de la consola de administración de Better Mobile](media/better_mobile_console.png)
 
3. Elija **Intune**.
4. Junto a **ACCOUNT NAME** (NOMBRE DE CUENTA), escriba un descriptor. 
5. En la ventana de **inicio de sesión de Microsoft**, escriba sus credenciales de Intune.
6. En la ventana **Permissions requested** (Permisos solicitados), elija **Accept** (Aceptar).
7. Busque los grupos de seguridad de Azure AD desde los que desea que Better Mobile sincronice los dispositivos y selecciónelos en la lista. Luego, seleccione **Continue** (Continuar).
8. Seleccione **Listo**.
9. Volverá a aparecer la página **Add account** (Agregar cuenta). Cierre la página. 

## <a name="next-steps"></a>Pasos siguientes

-   [Configurar mejores aplicaciones cliente](mtd-apps-ios-app-configuration-policy-add-assign.md)
