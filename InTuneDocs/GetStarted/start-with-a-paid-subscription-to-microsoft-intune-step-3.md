---
title: Sincronizar Active Directory y agregar usuarios a Intune | Microsoft Intune
description: "Se describe la sincronización de usuarios locales con Azure AD y la concesión de permisos de administrador para la suscripción de Intune."
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2a192c71b1b82f59b34ea614d09d895174f8112b
ms.openlocfilehash: 49eb9d1658df352c68677eaa3f29e1d57c43947e


---


# Sincronizar Active Directory y agregar usuarios a Intune
Puede configurar la sincronización de directorios para importar las cuentas de usuario desde su instancia local de Active Directory a Microsoft Azure Active Directory (Azure AD). Tener el servicio local de Active Directory conectado con todos los servicios basados en Azure Active Directory facilita la administración de identidades de usuario en gran medida. También puede configurar características de inicio de sesión único para que la experiencia de autenticación resulte fácil y familiar a los usuarios.

Para facilitar todavía más las cosas, al usar varios servicios con el mismo [inquilino de Azure AD](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant), las cuentas de usuario que se sincronizaron previamente están disponibles para todos los servicios basados en la nube que comparten la misma suscripción de inquilino de Azure AD.

## Sincronizar usuarios locales con Azure AD
La única herramienta que necesita para sincronizar las cuentas de usuario con Azure AD es el [Asistente de Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). El Asistente de Azure AD Connect proporciona una experiencia guiada y simplificada que conectará su infraestructura de identidad local con la nube.  Elija la topología según sus necesidades (directorio único o varios directorios, sincronización de contraseñas o federación) y el Asistente implementará y configurará todos los componentes necesarios para preparar la conexión y ejecutarla. Esto incluye los servicios de sincronización, los servicios de federación de Active Directory (AD FS) y el módulo de PowerShell de Azure AD.

> [!TIP]
> Azure AD Connect abarca funciones que se publicaron anteriormente, como la Sincronización de directorios y la Sincronización de Azure AD. Obtenga más información sobre la [integración de directorios](http://technet.microsoft.com/library/jj573653.aspx). Para más información sobre las ventajas de sincronizar cuentas de usuario del directorio local con Azure AD, consulte [Similitudes entre Active Directory y Azure AD](http://technet.microsoft.com/library/dn518177.aspx).

## Conceder permisos de administrador
Tras agregar usuarios adicionales a la suscripción de Intune, es recomendable conceder [credenciales administrativas](administrative-accounts-websites-perms.md) a algunas cuentas de usuario. La consola que debe usar para asignar credenciales administrativas depende del tipo de administrador que quiera asignar:

-   **Administrador de inquilinos**: para asignar este tipo de administrador y administrar la suscripción, incluida la facturación, el almacenamiento en la nube y los usuarios que pueden usar [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], emplee **[!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)]**.

-   **Administrador de servicios**: para asignar este tipo de administrador para las tareas habituales, como la administración de dispositivos móviles o equipos, la implementación de directivas o software y la ejecución de informes, use la **[!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]**.


### Pasos siguientes
Enhorabuena. Acaba de completar el paso 3 de la *Guía de inicio rápido de Intune*.

>[!div class="step-by-step"]

>[&larr; **Configuración del dominio**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md) [**Administrar licencias de Intune** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)  



<!--HONumber=Jul16_HO4-->


