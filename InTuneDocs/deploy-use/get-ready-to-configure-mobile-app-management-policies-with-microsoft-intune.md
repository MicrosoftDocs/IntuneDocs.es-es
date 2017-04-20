---
title: Requisitos previos para directivas de MAM | Microsoft Docs
description: "En este tema se describen los requisitos previos de configuración de los usuarios antes de crear directivas de administración de aplicaciones móviles."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e6a85e7-e007-41b6-9034-64d77f547b87
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: a85b9f603e022b3296cb16754effd06087074a72
ms.openlocfilehash: 9759c1331a3fb5308e1dbc53564059618a8ef45c
ms.lasthandoff: 04/01/2017


---

# <a name="get-ready-to-configure-app-protection-policies-in-the-azure-portal"></a>Preparativos para la configuración de directivas de protección de aplicaciones en Azure Portal

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

En este tema se describen los requisitos previos y los pasos que debe completar **antes** de crear directivas de protección de aplicaciones en Azure Portal.

Para comprender de qué modo las directivas de protección de aplicaciones de Intune pueden proteger los datos de su empresa, consulte [Protección de aplicaciones y datos con directivas de protección de aplicaciones](protect-apps-and-data-with-microsoft-intune.md).

## <a name="what-is-the-azure-portal"></a>¿Qué es Azure Portal?

Azure Portal es la nueva consola de administración para crear directivas de protección de aplicaciones. Admite los siguientes escenarios de MAM:
- Dispositivos móviles inscritos por Intune
- Dispositivos administrados por otra solución de Administración de dispositivos móviles (MDM)
- Dispositivos que no están administrados por ninguna solución de MDM (BYOD)

Actualmente, tanto la **consola de administrador de Intune** como **Azure Portal** permiten configurar directivas de protección de aplicaciones.  Tenga en cuenta lo siguiente:

* Las directivas que crea en **Azure Portal** se admiten en **todos los escenarios de MAM** mencionados anteriormente. La **consola de administrador de Intune** solo admite la creación de directivas para **dispositivos que estén inscritos y administrados mediante Intune**.

* Es posible que no vea toda la configuración de directivas de protección de aplicaciones en la consola de administrador de Intune, ya que la **nueva configuración** solo puede agregarse a **Azure Portal**.

* Si crea directivas de protección de aplicaciones **tanto** en la consola de administrador de Intune como en Azure Portal, la directiva de **Azure Portal se aplica a las aplicaciones y se implementa para los usuarios**.
    * Las directivas de protección de aplicaciones que se hayan creado en la consola de administrador de Intune no pueden importarse en Azure Portal.  Las directivas de protección de aplicaciones deben volver a crearse en Azure Portal.


* Otras **características de administración de aplicaciones**, como las directivas de configuración e implementación de aplicaciones, solo están disponibles en estos momentos en la **consola de administrador de Intune**.


Si no está familiarizado con Azure Portal, lea el tema [Azure Portal para directivas de protección de aplicaciones de Microsoft Intune](azure-portal-for-microsoft-intune-mam-policies.md) para obtener los conceptos básicos sobre su uso.

Para obtener instrucciones sobre cómo crear una directiva de aplicaciones mediante la consola de administrador de Intune, consulte [Configurar e implementar directivas de protección de aplicaciones en la consola de Microsoft Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).


##  <a name="supported-platforms"></a>Plataformas compatibles
- iOS 8.1 o posterior
- Android 4 o posterior
- Windows 10

>[!NOTE]
>A partir de la versión 1703, se pueden definir directivas de protección de aplicaciones para dispositivos Windows 10 en MAM sin escenario de inscripción. Para obtener más información, vea [Protege los datos de su empresa con Windows Information Protection (WIP)](https://technet.microsoft.com/en-us/itpro/windows/keep-secure/protect-enterprise-data-using-wip).

##  <a name="supported-apps"></a>Aplicaciones compatibles
* **Aplicaciones de Microsoft:** estas aplicaciones tienen el SDK para aplicaciones de Intune integrado y no requieren ningún procesamiento adicional antes de aplicar las directivas de protección de aplicaciones.
Para ver la lista completa de las aplicaciones de Microsoft compatibles, vaya a [Microsoft Intune mobile application gallery (Galería de aplicaciones móviles de Microsoft Intune)](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps) en la página de partners de aplicaciones de Microsoft Intune. Haga clic en una aplicación para ver los escenarios y las plataformas admitidos y si la aplicación admite varias identidades.

* **Aplicaciones de línea de negocio de su organización:** debe preparar estas aplicaciones para incluir el SDK para aplicaciones de Intune y poder aplicar las directivas de protección de aplicaciones.

  * Para dispositivos administrados por Intune, vea [Decide how to prepare apps for MAM](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md) (Decidir cómo preparar las aplicaciones para MAM).

  * Para dispositivos no administrados (como dispositivos propiedad de los empleados) o para dispositivos administrados por otra solución de administración de dispositivos móviles, vea [Proteger aplicaciones y datos de línea de negocio en dispositivos no inscritos en Microsoft Intune](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md).

## <a name="prerequisites"></a>Requisitos previos

-   **Una suscripción a Microsoft Intune**. Los usuarios necesitan licencias de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] para obtener aplicaciones que tienen directivas de protección de aplicaciones.
Ya tiene una suscripción de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] si usa [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] actualmente para administrar los dispositivos. También tiene una suscripción de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] si ha adquirido una licencia de Enterprise Mobility Suite (EMS). Si está probando [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] para comprobar las funcionalidades de MAM, puede obtener una cuenta de prueba en la [página de Microsoft Intune](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/).

    Para comprobar si tiene una suscripción de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], en el portal de Office, vaya a la página de **facturación**.  Si tiene una suscripción, debe ver [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] como **Activo** en las suscripciones.

-   **Una suscripción de Office 365**, que se necesita para lo siguiente:

  - Para aplicar las directivas de protección de aplicaciones a las aplicaciones que admiten varias identidades.

  - Para crear cuentas profesionales de SharePoint Online y Exchange Online. Exchange local y SharePoint local no se admiten.

-   **Configuración de Skype Empresarial Online para la autenticación moderna**. Para más información, consulte [Habilitar la autenticación moderna](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).


- Azure Active Directory (Azure AD) para crear usuarios. Azure AD autentica a los usuarios cuando estos abre la aplicación y escriban sus credenciales de trabajo.

    > [!NOTE]
    > Los grupos de usuarios deben configurarse en Azure AD. Los grupos de usuarios de Intune no pueden usarse para implementar directivas de protección de aplicaciones en Azure Portal.

### <a name="create-users-and-assign-microsoft-intune-licenses"></a>Crear usuarios y asignar licencias de Microsoft Intune

1.  Inicie sesión en el [Portal de Office](http://portal.office.com) con sus credenciales de administrador.

2.  Agregue los usuarios como se describió en los **Pasos para completar una evaluación de 30 días de Intune** de la [guía de evaluación de Intune](https://docs.microsoft.com/en-us/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune) y, luego, asigne las licencias de Intune. Para conceder a un usuario la capacidad de acceder al portal de Office, al Portal de Azure AD y al Portal de Azure, asígnele el **rol de administrador global**.

5.  Las directivas de protección de aplicaciones se implementan para grupos de usuarios de Azure Active Directory. Para crear grupos de usuarios para sus directivas de protección de aplicaciones, cree un grupo de usuarios como se describe en la sección **Creación de un grupo de usuarios** de [Crear grupos para organizar los dispositivos y usuarios de la suscripción de evaluación](https://docs.microsoft.com/en-us/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune-step-3).

### <a name="assign-roles-to-non-global-admin-users"></a>Asignar roles a usuarios administradores no globales

Los administradores globales tienen acceso al [Portal de Azure](https://portal.azure.com).  Si quiere que los usuarios que no sean administradores globales puedan configurar directivas y realizar otras tareas de administración de aplicaciones móviles, consulte el artículo [Uso de asignaciones de roles para administrar el acceso a los recursos de la suscripción de Azure](https://azure.microsoft.com/en-us/documentation/articles/role-based-access-control-configure/).

## <a name="next-steps"></a>Pasos siguientes
[Creación e implementación de directivas de protección de aplicaciones con Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)

