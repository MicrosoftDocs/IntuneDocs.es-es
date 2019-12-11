---
title: Configuración de la integración de Sophos Mobile con Intune
titleSuffix: Intune on Azure
description: Procedimientos para configurar la solución Sophos Mobile con Microsoft Intune para controlar el acceso de los dispositivos móviles a los recursos corporativos.
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
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: aad6268606dfcf69c304bb5c5b270c8c4795e4b2
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72681284"
---
# <a name="integrate-sophos-mobile-with-intune"></a>Integración de Sophos Mobile con Intune  

Complete los pasos siguientes para integrar la solución Sophos Mobile Threat Defense con Intune.  

> [!NOTE]
> Este proveedor de Mobile Threat Defense no es compatible con dispositivos no inscritos.

## <a name="before-you-begin"></a>Antes de comenzar  

Antes de iniciar el proceso de integración de Sophos Mobile con Intune, asegúrese de disponer de lo siguiente:  
- Suscripción a Microsoft Intune  
- Credenciales de administrador de Azure Active Directory para conceder los permisos siguientes:  
  - Iniciar sesión y leer el perfil del usuario  
  - Obtener acceso al directorio con el usuario que tiene la sesión iniciada  
  - Leer datos de directorio  
  - Enviar información del dispositivo a Intune  
- Credenciales de administrador para acceder a la consola de administración de Sophos Mobile.  


### <a name="sophos-mobile-app-authorization"></a>Autorización de la aplicación Sophos Mobile  
  
El proceso de autorización de la aplicación Sophos Mobile es el siguiente:  
- Permita que el servicio Sophos Mobile comunique a Intune la información relacionada con el estado de mantenimiento del dispositivo.  
- Sophos Mobile se sincroniza con la pertenencia a grupos de inscripción de Azure AD para rellenar la base de datos de su dispositivo.  
- Permita que la consola de administración de Sophos Mobile use el inicio de sesión único (SSO) de Azure AD.  
- Permita que la aplicación Sophos Mobile inicie sesión con el SSO de Azure AD.  


## <a name="to-set-up-sophos-mobile-integration"></a>Para configurar la integración de Sophos Mobile  

1. Inicie sesión en [Azure Portal]( https://portal.azure.com/), vaya a **Intune** > **Conformidad de dispositivos** > **Mobile Threat Defense** > y seleccione **Agregar**.  
2. En la página **Agregar conector**, use la lista desplegable y seleccione **Sophos**. Después seleccione **Crear**.  
3. Seleccione el vínculo *Open the Sophos admin console* (Abrir la consola de administración de Sophos).  
4. Inicie sesión en la [consola de administración de Sophos](https://central.sophos.com/) con sus credenciales de Sophos.  
5. Vaya a **Mobile** > **Settings** > **Setup** > **Sophos setup** (Dispositivos móviles>Ajustes>Configuración>Configurar Sophos).  
6. En la página **Sophos setup** (Configurar Sophos), seleccione la pestaña **Intune MTD** (MTD de Intune).  
   ![Configuración de Sophos](./media/sophos-mtd-connector-integration/sophos-setup.png) 
 
7. Seleccione **Bind** (Enlazar) y después **Yes** (Sí). Sophos se conecta a Intune y requiere que inicie sesión en la suscripción de Intune. 
8. En la ventana de autenticación de Microsoft Intune, escriba las credenciales de Intune y **acepte** la solicitud de permisos para *Sophos Mobile Thread Defense*.  
   ![Autenticación de Intune](./media/sophos-mtd-connector-integration/intune-authentication.png)

9. En la página **Sophos setup**, seleccione **Save** (Guardar) para completar la configuración de Intune:  
   ![Guardado de la configuración de Sophos](./media/sophos-mtd-connector-integration/save-sophos-configuration.png)  

1. Cuando aparezca el mensaje **Successful Integration** (Integración correcta), se habrá completado la integración.  
1. En la consola de Intune, Sophos ya está disponible.  


## <a name="next-steps"></a>Pasos siguientes  
[Configuración de aplicaciones cliente de Sophos](mtd-apps-ios-app-configuration-policy-add-assign.md)
