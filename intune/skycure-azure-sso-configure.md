---
title: "Configuración de Skycure para usar el inicio de sesión único de Azure AD con Intune"
titleSuffix: Intune on Azure
description: "Configuración de Skycure para usar el inicio de sesión único de Azure AD con Intune"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e0466ac4-4942-4c4c-b8af-996b597c701d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b2d8a79baf65208e87dbe85d8cc934e167710144
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="configure-skycure-to-use-azure-active-directory-single-sign-on-sso"></a>Configuración de Skycure para utilizar el inicio de sesión único (SSO) de Azure Active Directory

El SSO de Azure AD se usa al integrar Intune con Skycure. Estas son las ventajas principales:

-   Los **administradores** pueden usar las mismas credenciales sin tener que ingresarlas cada vez que inicien y cierren sesión en los portales de Microsoft (Intune, Azure) y en la consola de administración de Skycure.

-   Los **usuarios finales** puede usar las mismas credenciales de Azure AD sin tener que ingresarlas cada vez que inicien y cierren sesión en las aplicaciones de Skycure.

A continuación, se indican los pasos para integrar Skycure con el inicio de sesión único (SSO) de Azure Active Directory.

## <a name="to-retrieve-the-azure-active-directory-tenant-id"></a>Para recuperar el identificador de inquilino de Azure Active Directory

Debe recuperar el identificador de inquilino de Azure AD.

1.  Vaya al [Portal de Azure](https://portal.azure.com/) e inicie sesión con sus credenciales.

2.  Verá el **Panel**. Elija **Azure Active Directory**.

    ![Panel de Azure AD](./media/skycure-sso-1.png)

3.  Se abrirá la hoja **Azure Active Directory**. Elija **Propiedades**.

    ![Hoja de propiedades de AD de Azure](./media/skycure-sso-2.png)

4.  Haga clic en el **icono de copia** en el **Identificador de inquilino del directorio** en la hoja **Propiedades de Azure Active Directory**.

5. Pegue el valor copiado del identificador del directorio en un archivo de texto para que pueda usarlo más adelante. El valor del identificador del directorio será necesario más adelante en el proceso de integración de Skycure e Intune.

    ![Panel de Azure AD](./media/skycure-sso-3.png)

## <a name="allow-skycure-to-communicate-with-azure-active-directory"></a>Concesión de permiso para que Skycure se comunique con Azure Active Directory

1.  Escriba la siguiente dirección URL en el explorador. En lugar de **DIRECTORY_ID**, escriba el Identificador del inquilino de Azure Active Directory copiado anteriormente en el archivo de texto.

        https://login.microsoftonline.com/<DIRECTORY_ID>/oauth2/authorize?client_id=28fd67fdb1794629a8b0dad420b697c7&prompt=admin_consent&redirect_uri=https%3A%2F%2Fmc.skycure.com%2Fapi%2Fexternal%2Fmdm%2Faad_app_consent%2Fmanagement_callback&response_type=code

2.  Debe iniciar sesión con sus credenciales de Azure Active Directory. Haga clic en **Siguiente** para continuar.

![Página de inicio de sesión de Azure AD](./media/skycure-sso-4.png)

## <a name="create-an-azure-ad-security-group-for-skycure-optional"></a>Crear un grupo de seguridad de Azure AD para Skycure (opcional)

Le recomendamos crear un grupo de usuarios exclusivo que incluya a los usuarios que ejecutan Skycure (por ejemplo, usuarios de Skycure). Esto puede resultar útil al analizar la actividad de Skycure a través de los informes.

-   Obtenga más información sobre [cómo crear un grupo y agregar miembros en Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal).

> [!NOTE] 
> También puede usar un grupo de seguridad de Azure AD existente.

## <a name="configure-the-azure-ad-account-to-integrate-intune-with-skycure"></a>Configure la cuenta de Azure AD para integrar Intune con Skycure

1.  Desde la [consola de administración de Skycure](https://aad.skycure.com/), escriba el identificador del inquilino de Azure Active Directory previamente guardado en el archivo de texto.

![Consola de administración de Skycure: Campo del identificador del inquilino de Azure AD](./media/skycure-sso-5.png)

> [!IMPORTANT] 
> Skycure valida si el identificador del inquilino de Azure AD existe al consultar a Azure AD. Una vez que Skycure lo encuentra, el administrador puede continuar con el paso siguiente, que es la configuración básica.

## <a name="next-steps"></a>Pasos siguientes

[Descarga de la directiva de configuración de la aplicación de iOS de Skycure](skycure-ios-app-configuration-policy-download.md)
