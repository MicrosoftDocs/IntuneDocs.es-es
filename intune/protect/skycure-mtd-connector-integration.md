---
title: Configuración de la integración de Symantec con Microsoft Intune
titleSuffix: Microsoft Intune
description: Configuración de la solución Symantec Endpoint Protection Mobile con Microsoft Intune para controlar el acceso de los dispositivos móviles a los recursos corporativos.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/21/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 359448d9-2384-42ac-a21c-a25148c20a7b
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a7271937c7675e82d2d3b3f32074ec07431536a2
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726705"
---
# <a name="set-up-symantec-endpoint-protection-mobile-integration-with-intune"></a>Configuración de la integración de Symantec Endpoint Protection Mobile con Intune

Realice los pasos siguientes para integrar la solución Symantec Endpoint Protection Mobile (SEP Mobile) con Intune. Debe agregar las aplicaciones de SEP Mobile a Azure AD para tener funcionalidades de inicio de sesión único.

## <a name="before-you-begin"></a>Antes de comenzar

### <a name="azure-ad-account-used-to-integrate-intune-and-sep-mobile"></a>Cuenta de Azure AD usada para integrar Intune y SEP Mobile

- Asegúrese de que la cuenta de Azure AD está correctamente configurada en la [consola de administración de Symantec Endpoint Protection Mobile](https://aad.skycure.com) antes de iniciar el proceso de configuración básica de SEP Mobile.
- Para realizar la integración, la cuenta de Azure AD debe ser una cuenta de administrador global.
### <a name="network-setup"></a>Configuración de red

Para asegurarse de que la red está configurada correctamente para la integración con el programa de instalación de SEP Mobile, consulte el artículo de Symantec [Setting up your network configuration](https://portal.skycure.com/articles/Documentation/Setting-up-your-network-configuration-26-8-2016) (Configuración de red).

### <a name="full-integration-vs-read-only"></a>Integración completa en comparación con Solo lectura

SEP Mobile admite dos modos de integración con Intune:

- **Integración de solo lectura (configuración básica):** solo se crea un inventario de dispositivos de Azure Active Directory y se rellenan en la consola de administración de Symantec Endpoint Protection Mobile.
<br>
  - Si las casillas **Report the health and risk of devices to Intune** (Notificar el estado y el riesgo de los dispositivos a Intune) y **Also report security incidents to Intune** (Notificar también los incidentes de seguridad a Intune) no están seleccionadas en la consola de administración de Symantec Endpoint Protection Mobile, la integración es de solo lectura y, por tanto, el estado de un dispositivo (conforme o no conforme) nunca cambia en Intune.
<br></br>
- **Integración completa:** permite que SEP Mobile notifique la información de riesgo e incidentes de seguridad de los dispositivos a Intune, lo que crea una comunicación bidireccional entre ambos servicios en la nube.

### <a name="how-are-the-sep-mobile-apps-used-with-azure-ad-and-intune"></a>¿Cómo se usan las aplicaciones de SEP Mobile con Azure AD e Intune?

- **Aplicación de iOS:** permite a los usuarios finales iniciar sesión en Azure AD mediante una aplicación de iOS.

- **Aplicación de Android:** permite a los usuarios finales iniciar sesión en Azure AD mediante una aplicación de Android.

- **Aplicación de administración:** es la aplicación multiinquilino de Azure AD para SEP Mobile que permite la comunicación de servicio a servicio con Intune.

## <a name="to-set-up-the-read-only-integration-between-intune-and-sep-mobile"></a>Para configurar la integración de solo lectura entre Intune y SEP Mobile, siga estos pasos:

> [!IMPORTANT]
> Las credenciales de administración de SEP Mobile deben estar formadas por una cuenta de correo electrónico que pertenezca a un usuario válido en Azure Active Directory, de lo contrario, el inicio de sesión dará error. SEP Mobile usa Azure Active Directory para autenticar a su administrador mediante el inicio de sesión único (SSO).

1. Vaya a la [consola de administración de Symantec Endpoint Protection Mobile](https://aad.skycure.com).

2. Escriba sus **credenciales de administrador de SEP Mobile** y luego elija **Continue** (Continuar).

3. Vaya a **Settings** (Configuración) y, en, **Intune Integration** (Integración de Intune), elija **Basic Setup** (Configuración básica).

4. Junto a **iOS App** (Aplicación iOS), elija **Add to Active Directory** (Agregar a Active Directory).

    ![Imagen de la consola de administración de Symantec Endpoint Protection Mobile](./media/skycure-mtd-connector-integration/symantec-portal-basic-add.png)

5. Cuando se abra la página de inicio de sesión, escriba sus credenciales de Intune y, a continuación, elija **Accept** (Aceptar).

    ![Imagen de la solicitud de inicio de sesión en Intune de aplicación de iOS](./media/skycure-mtd-connector-integration/symantec-portal-basic-accept.png)

6. Después de agrega la aplicación a Azure AD, verá una indicación de que la aplicación se ha agregado correctamente.

    ![Imagen de la pantalla de finalización de la aplicación iOS](./media/skycure-mtd-connector-integration/symantec-portal-basic-added.png)

7. Repita estos pasos con las aplicaciones **SEP Mobile Android** y **Administración**.

### <a name="add-an-azure-ad-security-group-into-sep-mobile"></a>Adición de un grupo de seguridad de Azure AD a SEP Mobile

Debe agregar un grupo de seguridad de Azure AD que contenga todos los dispositivos que ejecutan SEP Mobile.

- Escriba y seleccione todos los grupos de seguridad de los dispositivos que ejecutan SEP Mobile y, luego, guarde los cambios.

    ![Imagen que muestra los grupos de usuarios de aplicaciones de SEP Mobile](./media/skycure-mtd-connector-integration/symantec-portal-basic-groups.png)

SEP Mobile sincroniza los dispositivos que ejecutan su servicio Mobile Threat Defense con los grupos de seguridad de Azure AD.

![Imagen de la configuración del grupo de seguridad en la consola de administración de SEP Mobile](./media/skycure-mtd-connector-integration/symantec-portal-basic-status.png)

## <a name="to-set-up-the-full-integration-between-intune-and-sep-mobile"></a>Configuración de la integración completa entre Intune y SEP Mobile

### <a name="retrieve-the-directory-id-in-azure-ad"></a>Recuperar el identificador de directorio de Azure AD

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).

2. Escriba "Active Directory" en el cuadro de búsqueda y, a continuación, seleccione **Azure Active Directory**.

3. Seleccione **Propiedades**.

4. Junto a **Id. de directorio**, elija el icono de copia y, a continuación, péguelo en una ubicación segura. Necesitará este identificador en un paso posterior.

    ![Imagen que muestra el identificador de directorio en Azure Portal](./media/skycure-mtd-connector-integration/symantec-azure-portal-directory-ID.png)

### <a name="optional-create-a-dedicated-security-group-for-devices-that-need-to-run-the-sep-mobile-apps"></a>(Opcional) Crear un grupo de seguridad dedicado para dispositivos que deban ejecutar aplicaciones de SEP Mobile
1. En [Azure Portal](https://portal.azure.com), en **Administrar**, elija **Usuarios y grupos** y, a continuación, **Todos los grupos**.

2. Elija el botón **Agregar**. En **Nombre**, escriba el nombre del grupo. En **Tipo de pertenencia**, elija **Asignado**.

3. En la hoja **Miembros**, seleccione los miembros del grupo y, a continuación, elija el botón **Seleccionar**.

4. En la hoja **Grupo**, elija **Crear**.

### <a name="set-up-the-integration-between-symantec-endpoint-protection-mobile-and-intune"></a>Configurar la integración entre Intune y Symantec Endpoint Protection Mobile

1. Vaya a la [consola de administración de Symantec Endpoint Protection Mobile](https://aad.skycure.com).

2. Escriba sus **credenciales de administrador de SEP Mobile** y, luego, elija **Continue** (Continuar).

3. Vaya a la sección **Settings** >  (Configuración) **Integrations** >  (Integraciones) **Intune** > **EMM Integration Selection** (Selección de la integración de EMM).

4. En el cuadro **Directory ID** (Id. de directorio), pegue el identificador de directorio que copió de Azure Active Directory en la sección anterior y guarde la configuración.

    ![Imagen que muestra el identificador de directorio en el portal de SEP Mobile](./media/skycure-mtd-connector-integration/symantec-portal-directory-ID.png)

5. Vaya a la sección **Settings** >  (Configuración) **Integrations** >  (Integraciones) **Intune** > **Basic Setup** (Configuración básica).

6. Junto a **iOS App** (Aplicación iOS), elija el botón **Add to Active Directory** (Agregar a Active Directory).

    ![Imagen que muestra cómo agregar la aplicación de iOS a Active Directory](./media/skycure-mtd-connector-integration/symantec-portal-basic-add.png)

7. Inicie sesión con las credenciales de Azure Active Directory en la cuenta de Office 365 que administra el directorio.

8. Elija el botón **Aceptar** para agregar la aplicación iOS para SEP Mobile a Azure Active Directory.

    ![Imagen que muestra el botón Aceptar](./media/skycure-mtd-connector-integration/symantec-portal-basic-accept.png)

9. Repita el mismo proceso con la **aplicación de Android** y la **aplicación de administración**.

10. Seleccione todos los grupos de usuarios que deben ejecutar las aplicaciones de SEP Mobile; por ejemplo, el grupo de seguridad que creó anteriormente.

    ![Imagen que muestra los grupos de usuarios de aplicaciones de SEP Mobile](./media/skycure-mtd-connector-integration/symantec-portal-basic-groups.png)

11. SEP Mobile sincroniza los dispositivos de los grupos seleccionados y comienza a enviar información a Intune. Puede ver estos datos en la sección de integración completa. Vaya a la sección **Settings** >  (Configuración) **Integrations** >  (Integración) **Intune** > **Full Integration** (Integración completa).

     ![Imagen que muestra la integración completa finalizada de SEP Mobile](./media/skycure-mtd-connector-integration/symantec-portal-basic-status.PNG)
## <a name="next-steps"></a>Pasos siguientes

[Configuración de aplicaciones de SEP Mobile](mtd-apps-ios-app-configuration-policy-add-assign.md)
