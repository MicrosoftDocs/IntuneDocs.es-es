---
title: Configuración de un nombre de dominio personalizado
titleSuffix: Microsoft Intune
description: Adición de un nombre de dominio personalizado de su suscripción de Microsoft Intune
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 06/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 33d5c994e4a51542c39c61a1f2311fda5a0a7caf
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/20/2019
ms.locfileid: "71239504"
---
# <a name="configure-a-custom-domain-name"></a>Configuración de un nombre de dominio personalizado

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

En este tema se indica a los administradores cómo se puede crear un CNAME de DNS para simplificar y personalizar la experiencia de inicio de sesión con Microsoft Intune.

Cuando su organización se registra en un servicio en la nube de Microsoft como es Intune, se le asigna un nombre de dominio inicial hospedado en Azure Active Directory (AD) similar a **su-dominio.onmicrosoft.com**. En este ejemplo, **su-dominio** es el nombre del dominio que eligió al suscribirse. **onmicrosoft.com** es el sufijo asignado a las cuentas que agregue a su suscripción. Puede configurar el dominio personalizado de su organización para obtener acceso a Intune en lugar del nombre de dominio proporcionado con la suscripción.

Le recomendamos encarecidamente que, antes de crear nuevas cuentas de usuario o de sincronizar su instancia de Active Directory local, decida si va a usar únicamente el dominio .onmicrosoft.com o si va a agregar uno o más nombres de dominio personalizados. Configure un dominio personalizado antes de agregar usuarios para simplificar la administración de usuarios. La configuración de un dominio de cliente permite a los usuarios iniciar sesión con las credenciales que usan para obtener acceso a otros recursos del dominio.

Al suscribirse a un servicio basado en la nube de Microsoft, la instancia de ese servicio se convierte en un [inquilino de Microsoft Azure AD](https://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant), que proporciona servicios de identidad y directorio al servicio basado en la nube. Además, como las tareas de configuración de Intune para que use el nombre de dominio personalizado de las organizaciones son las mismas que para otros inquilinos de Azure AD, puede usar la información y los procedimientos que se describen en [Agregar el dominio](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

> [!TIP]
> Para obtener más información sobre los dominios personalizados, consulte [Información general conceptual de nombres de dominio personalizado en Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/).

No puede cambiar el nombre del dominio inicial onmicrosoft.com ni quitarlo. Puede agregar, comprobar o quitar los nombres de dominio personalizado usados en Intune para identificar claramente su negocio.

## <a name="to-add-and-verify-your-custom-domain"></a>Para agregar y comprobar el dominio personalizado

1. Vaya al [Centro de administración de Microsoft 365](https://admin.microsoft.com/) e inicie sesión con su cuenta de administrador.

2. En el panel de navegación, elija **Configuración** &gt; **Dominios**.

3. Elija **Agregar dominio** y escriba el nombre de su dominio personalizado. Seleccione **Siguiente**.
   ![Captura de pantalla del Centro de administración de Microsoft 365 con la opción Configuración > Dominios seleccionada y un nombre de dominio nuevo agregado](./media/domain-custom-add.png)
4. El cuadro de diálogo **Comprobar dominio** se abre proporcionándole los valores para crear el registro TXT en su proveedor de host DNS.
    - **Usuarios de GoDaddy**: el Centro de administración de Microsoft 365 lo lleva a la página de inicio de sesión de GoDaddy. El registro TXT se crea automáticamente después de escribir sus credenciales y de aceptar el acuerdo del permiso de cambio de dominio. También puede [crear el registro TXT](https://support.office.com/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a).
    - **Usuarios de Register.com**: siga las [instrucciones paso a paso](https://support.office.com/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e#BKMK_verify) para crear el registro TXT.
5. [Es posible que necesite crear registros DNS adicionales para las inscripciones de Intune](windows-enroll.md#simplify-windows-enrollment-without-azure-ad-premium).

Los pasos para agregar y comprobar un dominio personalizado también se pueden [realizar en Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

Puede obtener más información [sobre su dominio inicial onmicrosoft.com en Office 365](https://support.office.com/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A)

Puede obtener más información sobre cómo [simplificar la inscripción de Windows sin Azure AD Premium](windows-enroll.md#simplify-windows-enrollment-without-azure-ad-premium) mediante la creación de un CNAME de DNS que redirija la inscripción a los servidores de Intune.
