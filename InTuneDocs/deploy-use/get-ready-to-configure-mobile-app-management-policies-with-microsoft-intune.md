---
title: Requisitos previos para directivas de MAM | Microsoft Intune
description: "En este tema se describen los requisitos previos de configuración de los usuarios antes de crear directivas de administración de aplicaciones móviles."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e6a85e7-e007-41b6-9034-64d77f547b87
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: ac820146d81fb121a60f7029f6a52a0056d6ab0a


---

# <a name="get-ready-to-configure-mobile-app-management-policies-on-the-azure-portal"></a>Preparación para configurar directivas de administración de aplicaciones móviles en Azure Portal
En este tema se describen los requisitos previos y los pasos que debe completar **antes** de que pueda crear directivas de administración de aplicaciones móviles (MAM) en Azure Portal.

Para comprender de qué modo las directivas de MAM de Intune pueden proteger los datos de su empresa, vea [Proteger aplicaciones y datos con Microsoft Intune](protect-apps-and-data-with-microsoft-intune.md).

## <a name="what-is-the-azure-portal"></a>¿Qué es Azure Portal?

El Portal de Azure es la nueva consola de administración para crear directivas de MAM. Admite los siguientes escenarios de MAM:
- Dispositivos móviles inscritos por Intune
- Dispositivos administrados por otra solución de Administración de dispositivos móviles (MDM)
- Dispositivos que no están administrados por ninguna solución de MDM (BYOD)

Actualmente, tanto la **consola de administrador de Intune** como **Azure Portal** le permiten configurar directivas de MAM.  Tenga en cuenta lo siguiente:

* Las directivas que crea en **Azure Portal** se admiten en **todos los escenarios de MAM** mencionados anteriormente. La **consola de administrador de Intune** solo admite la creación de directivas para **dispositivos que estén inscritos y administrados mediante Intune**.

* Podría no ver toda la configuración de directivas de MAM en la consola de administrador de Intune ya que la **nueva configuración** solo puede agregarse a **Azure Portal**.

* Si crea directivas de MAM **tanto** en la consola de administrador de Intune como en Azure Portal, la directiva de **Azure Portal se aplica a las aplicaciones y se implementa para los usuarios**.
    * Las directivas de MAM que se hayan creado en la consola de administración de Intune no pueden importarse en el Portal de Azure.  Las directivas de MAM deben volver a crearse en el Portal de Azure.


* Otras **características de administración de aplicaciones**, como las directivas de configuración e implementación de aplicaciones, solo están disponibles en estos momentos en la **consola de administrador de Intune**.


Si no está familiarizado con Azure Portal, lea el tema [Azure Portal para directivas de MAM de Microsoft Intune](azure-portal-for-microsoft-intune-mam-policies.md) para obtener los conceptos básicos sobre cómo usar Azure Portal.

Para obtener instrucciones sobre cómo crear una directiva de MAM mediante la consola de administrador de Intune, consulte [Configurar e implementar directivas de administración de aplicaciones móviles en la consola de Microsoft Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).


##  <a name="supported-platforms"></a>Plataformas compatibles
- iOS 8.1 o posterior
- Android 4 o posterior

>[!NOTE]
>Los dispositivos Windows no admiten estas directivas de administración de aplicaciones móviles. En cambio, cuando inscribe los dispositivos Windows 10 en Intune, puede usar Windows Information Protection, ya que ofrece una funcionalidad similar. Para obtener más información, vea [Protege los datos de su empresa con Windows Information Protection (WIP)](https://technet.microsoft.com/en-us/itpro/windows/keep-secure/protect-enterprise-data-using-wip).

##  <a name="supported-apps"></a>Aplicaciones compatibles
* **Aplicaciones de Microsoft:** estas aplicaciones tienen el SDK para aplicaciones de Intune integrado y no requieren ningún procesamiento adicional antes de aplicar las directivas de MAM.
Para ver la lista completa de las aplicaciones de Microsoft compatibles, vaya a [Microsoft Intune mobile application gallery (Galería de aplicaciones móviles de Microsoft Intune)](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps) en la página de partners de aplicaciones de Microsoft Intune. Haga clic en una aplicación para ver los escenarios y las plataformas admitidos y si la aplicación admite varias identidades.

* **Aplicaciones de línea de negocio de su organización:** debe preparar estas aplicaciones para incluir el SDK para aplicaciones de Intune y poder aplicar las directivas de MAM.

  * Para dispositivos administrados por Intune, vea [Decide how to prepare apps for MAM](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md) (Decidir cómo preparar las aplicaciones para MAM).

  * Para dispositivos no administrados (como dispositivos propiedad de los empleados) o para dispositivos administrados por otra solución de administración de dispositivos móviles, vea [Proteger aplicaciones y datos de línea de negocio en dispositivos no inscritos en Microsoft Intune](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md).

## <a name="prerequisites"></a>Requisitos previos

-   **Una suscripción a Microsoft Intune**. Los usuarios necesitan licencias de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] para obtener aplicaciones que tienen directivas de MAM.
Ya tiene una suscripción de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] si usa [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] actualmente para administrar los dispositivos. También tiene una suscripción de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] si ha adquirido una licencia de Enterprise Mobility Suite (EMS). Si está probando [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] para comprobar las funcionalidades de MAM, puede obtener una cuenta de prueba en la [página de Microsoft Intune](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/).

    Para comprobar si tiene una suscripción de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], en el portal de Office, vaya a la página de **facturación**.  Si tiene una suscripción, debe ver [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] como **Activo** en las suscripciones.

-   **Una suscripción de Office 365**, que se necesita para lo siguiente:

  - Para aplicar las directivas de MAM a las aplicaciones que admiten varias identidades.

  - Para crear cuentas profesionales de SharePoint Online y Exchange Online. Exchange local y SharePoint local no se admiten.

-   **Configuración de Skype Empresarial Online para la autenticación moderna**. Para más información, consulte [Habilitar la autenticación moderna](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).


- Azure Active Directory (Azure AD) para crear usuarios. Azure AD autentica a los usuarios cuando estos abre la aplicación y escriban sus credenciales de trabajo.

    > [!NOTE]
    > Los grupos de usuarios deben configurarse en Azure AD. Los grupos de usuarios de Intune no pueden usarse para implementar directivas de MAM en Azure Portal.

### <a name="create-users-and-assign-microsoft-intune-licenses"></a>Crear usuarios y asignar licencias de Microsoft Intune

1.  Inicie sesión en el [Portal de Office](http://portal.office.com) con sus credenciales de administrador.

2.  Agregue los usuarios como se describió en los **Pasos para completar una evaluación de 30 días de Intune** de la [guía de evaluación de Intune](https://docs.microsoft.com/en-us/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune) y, luego, asigne las licencias de Intune. Para conceder a un usuario la capacidad de acceder al portal de Office, al Portal de Azure AD y al Portal de Azure, asígnele el **rol de administrador global**.

5.  Las directivas MAM se implementan para grupos de usuarios de Azure Active Directory. Para crear grupos de usuarios para sus directivas de MAM, cree un grupo de usuarios como se describió en la sección **Crear un grupo de usuarios** de [Crear grupos para organizar los dispositivos y usuarios de la suscripción de evaluación](https://docs.microsoft.com/en-us/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune-step-3).

### <a name="assign-roles-to-non-global-admin-users"></a>Asignar roles a usuarios administradores no globales

Los administradores globales tienen acceso al [Portal de Azure](https://portal.azure.com).  Si quiere que los usuarios que no son administradores globales puedan configurar directivas y realizar otras tareas de administración de aplicaciones móviles, puede asignar el rol Colaborador a los usuarios. Para obtener instrucciones detalladas, vea [Uso de asignaciones de roles para administrar el acceso a los recursos de la suscripción de Azure](https://azure.microsoft.com/en-us/documentation/articles/role-based-access-control-configure/).



En la tabla siguiente se enumeran los roles y permisos que puede asignar a los usuarios de administración.



|||
|--|----|
|**Rol**|**Permisos**|
|Administrador global (portal de O365)|Acceso al portal de Office 365 y al portal de Azure AD.<br /><br />Acceso al Portal de Azure (se pueden realizar las tareas de administración de roles y de administración de aplicaciones móviles).|
|Propietario (Portal de Azure)|Acceso al Portal de Azure (se pueden realizar las tareas de administración de roles y de administración de aplicaciones móviles).|
|Colaborador (Portal de Azure)|Acceso al Portal de Azure (solo se pueden realizar las tareas de administración de aplicaciones móviles).|




## <a name="next-steps"></a>Pasos siguientes
[Crear e implementar directivas de administración de aplicaciones móviles con Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


