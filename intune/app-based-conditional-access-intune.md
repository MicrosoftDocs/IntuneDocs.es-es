---
title: "Acceso condicional basado en aplicación con Intune"
description: "Conozca los conceptos sobre el funcionamiento del acceso condicional basado en aplicación con Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b399fba0-5dd4-4777-bc9b-856af038ec41
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9899f08cac650b1fea05370eb52327bc3c204a48
ms.sourcegitcommit: 3bafbec5822bb5baa2d313f2bd19f35a67438beb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2017
---
# <a name="app-based-conditional-access-with-intune"></a>Acceso condicional basado en aplicación con Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Las [directivas de protección de aplicaciones de Intune](app-protection-policy.md) ayudan a proteger los datos de la empresa en dispositivos inscritos en Intune. También puede usar directivas de protección de aplicaciones en dispositivos que poseen los empleados que no están inscritos para administración en Intune. En este caso, aunque la empresa no administre el dispositivo, deberá asegurarse de que los datos y los recursos de la empresa están protegidos.

El acceso condicional basado en aplicación y la administración de aplicaciones móviles agregan una capa de seguridad al garantizar que solo las aplicaciones móviles que admiten las directivas de protección de aplicaciones de Intune pueden tener acceso a Exchange Online y a otros servicios de Office 365.

> [!NOTE]
> Una aplicación administrada es aquella que tiene las directivas de protección de aplicaciones aplicadas y puede administrarse mediante Intune.

Puede bloquear las aplicaciones de correo electrónico integradas en iOS y Android cuando solo se permite a la aplicación Microsoft Outlook tener acceso a Exchange Online. Además, puede bloquear las aplicaciones que no tienen directivas de protección de aplicaciones de Intune aplicadas para que no puedan acceder a SharePoint Online.

## <a name="prerequisites"></a>Requisitos previos
Antes de crear una directiva de acceso condicional basado en aplicación, debe tener:

- **Enterprise Mobility + Security (EMS)** o una **suscripción Premium de Azure Active Directory (AD)**
- Licencia para EMS o Azure AD por parte de los usuarios

Para obtener más información, vea los [precios de Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) o los [precios de Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

## <a name="supported-apps"></a>Aplicaciones compatibles

- **Exchange Online**:
    - Microsoft Outlook para Android y iOS.
<br></br>
- **SharePoint Online**
    - Microsoft Word para iOS y Android
    - Microsoft Excel para iOS y Android
    - Microsoft PowerPoint para iOS y Android
    - Microsoft OneDrive para la Empresa para iOS y Android
    - Microsoft OneNote para iOS
<br></br>
- **Microsoft Teams**

El acceso condicional basado en aplicación [también admite aplicaciones de línea de negocio (LOB)](https://docs.microsoft.com/intune-classic/deploy-use/block-apps-with-no-modern-authentication), pero dichas aplicaciones deben usar la [autenticación moderna de Office 365](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a).

## <a name="how-app-based-conditional-access-works"></a>Funcionamiento del acceso condicional basado en aplicación

En este ejemplo, el administrador ha aplicado directivas de protección de aplicaciones a la aplicación Outlook, seguidas de una regla de acceso condicional que agrega la aplicación Outlook a una lista de aplicaciones admitidas que pueden usarse al obtener acceso al correo electrónico corporativo.

> [!NOTE]
> La estructura de diagrama de flujo siguiente puede usarse para otras aplicaciones administradas.

![Diagrama de flujo del acceso condicional basado en aplicación con Intune](./media/ca-intune-common-ways-3.png)

1.  El usuario intenta autenticarse en Azure AD desde la aplicación Outlook.

2.  Al usuario se le redirige a la tienda de aplicaciones para instalar una aplicación de agente al intentar autenticarse por primera vez. La aplicación de agente puede ser Microsoft Authenticator para iOS o el Portal de empresa de Microsoft para dispositivos Android.

 Si los usuarios intentan usar una aplicación nativa de correo electrónico, se les redirige a la tienda de aplicaciones para instalar la aplicación Outlook.

3.  La aplicación de agente se instala en el dispositivo.

4.  La aplicación de agente inicia el proceso de registro de Azure AD que crea un registro de dispositivo en Azure AD. No se trata del mismo proceso que para la inscripción de administración de dispositivos móviles (MDM), pero este registro resulta necesario para que las directivas de acceso condicional se puedan aplicar en el dispositivo.

5.  La aplicación de agente verifica la identidad de la aplicación. Hay un nivel de seguridad para que la aplicación de agente pueda validar si la aplicación está autorizada para que el usuario la utilice.

6.  La aplicación de agente envía el identificador de cliente de la aplicación a Azure AD como parte del proceso de autenticación de usuario para comprobar si se encuentra en la lista aprobada de directivas.

7.  Azure AD permite al usuario autenticarse y usar la aplicación en función de la lista aprobada de directivas. Si la aplicación no se encuentra en la lista, Azure AD deniega el acceso a la aplicación.

8.  La aplicación Outlook se comunica con el servicio en la nube de Outlook para iniciar la comunicación con Exchange Online.

9.  El servicio en la nube de Outlook se comunica con Azure AD para recuperar el token de acceso al servicio Exchange Online para el usuario.

10.  La aplicación Outlook se comunica con Exchange Online para recuperar el correo electrónico corporativo del usuario.

11.  El correo electrónico corporativo se entrega en el buzón de correo del usuario.

## <a name="next-steps"></a>Pasos siguientes
[Crear una directiva de acceso condicional basado en aplicación](app-based-conditional-access-intune-create.md)

[Bloqueo de aplicaciones que no usan la autenticación moderna](app-modern-authentication-block.md)
