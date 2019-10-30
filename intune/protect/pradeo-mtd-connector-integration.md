---
title: Configuración de la integración de Pradeo con Intune
titleSuffix: Intune on Azure
description: Integración del conector de Pradeo con Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 82872ba6-80f8-4cc9-adf4-0ccd8ff26dd2
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 32e67ac961f2831a881bc160e19cefdb75723ff0
ms.sourcegitcommit: 1a5b185acd27954b10b6d59409d82eb80fd71284
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72681249"
---
# <a name="integrate-pradeo-mobile-threat-defense-with-intune"></a>Integración de Mobile Threat Defense de Pradeo con Intune

Complete estos pasos para integrar la solución Mobile Threat Defense de Pradeo con Intune.

> [!NOTE]  
> Este proveedor de Mobile Threat Defense no es compatible con dispositivos no inscritos.

## <a name="before-you-begin"></a>Antes de comenzar

> [!NOTE]
> Los pasos siguientes debe completarlos en la [consola Pradeo Security](https://www.apps-security.com).

Antes de iniciar el proceso de integración de Pradeo con Intune, asegúrese de disponer de lo siguiente:

- Suscripción a Microsoft Intune

- Credenciales de administrador de Azure Active Directory para conceder los permisos siguientes:

  - Iniciar sesión y leer el perfil del usuario

  - Obtener acceso al directorio con el usuario que tiene la sesión iniciada

  - Leer datos de directorio

  - Enviar información del dispositivo a Intune

- Credenciales de administrador para obtener acceso a la consola Pradeo Security.

### <a name="pradeo-app-authorization"></a>Autorización de la aplicación Pradeo

El proceso de autorización de la aplicación Pradeo es el siguiente:

- Permita que el servicio de Pradeo comunique a Intune la información relacionada con el estado de mantenimiento del dispositivo.

- Pradeo se sincroniza con la pertenencia a grupos de inscripción de Azure AD para rellenar la base de datos de su dispositivo.

- Permita que la consola de administración de Pradeo use el inicio de sesión único (SSO) de Azure AD.

- Permita que la aplicación de Pradeo inicie sesión con el SSO de Azure AD.

## <a name="to-set-up-pradeo-integration"></a>Para configurar la integración de Pradeo

1. Vaya a la [consola Pradeo Security](https://www.apps-security.com) e inicie sesión con sus credenciales.

2. En el menú, elija **Administración - Enterprise Mobility Management**.

3. Elija el **logotipo de Intune**.

4. En la ventana **EMM (Enterprise Mobility Management) - Intune**, en el **paso 1**, elija el botón **Pradeo Connector** (Connector de Pradeo). 

    ![Captura de pantalla de la ventana Pradeo EMM Intune](./media/pradeo-mtd-connector-integration/pradeo_setup.png)

5. En la ventana de conexión de Microsoft Intune, escriba sus credenciales de Intune.

5. La página web de Pradeo se volverá a abrir. En el **paso 2**, elija el botón **Pradeo Device Health** (Estado del dispositivo de Pradeo).

7. En la ventana del conector de Pradeo-Intune, seleccione **Aceptar**. 

8. En la ventana del conector de la API del dispositivo de Pradeo, seleccione **Aceptar**.

9. La página web de Pradeo se volverá a abrir. En el **paso 3**, elija el botón **Connect to Microsoft** (Conectarse a Microsoft). 

10. En la ventana de autenticación de Microsoft Intune, escriba sus credenciales de Intune.

11. Cuando aparezca el mensaje **Successful Integration** (Integración correcta), se habrá completado la integración.

## <a name="next-steps"></a>Pasos siguientes

- [Configuración de aplicaciones Pradeo de dispositivos inscritos](mtd-apps-ios-app-configuration-policy-add-assign.md)
