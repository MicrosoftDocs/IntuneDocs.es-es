---
title: Perfiles de aprovisionamiento de aplicaciones
description: "Intune proporciona las herramientas para implementar proactivamente una nueva directiva de perfil de aprovisionamiento a dispositivos que tengan aplicaciones cuya expiración esté próxima."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 86fbe736-7bdb-4f5e-ae21-13c91eb2462c
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6e975aa7ee22f826c7a0a60d637d651fd347bc54
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="use-ios-mobile-provisioning-profile-policies-to-prevent-your-apps-from-expiring"></a>Uso de directivas de perfil de aprovisionamiento móvil iOS para evitar que las aplicaciones expiren

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Las aplicaciones de línea de negocio de Apple iOS implementadas en iPhone y iPad se crean con un perfil de aprovisionamiento incluido y un código firmado con un certificado. Cuando la aplicación está en ejecución, iOS confirma la integridad de la aplicación de iOS y exige el cumplimiento de las directivas definidas por el perfil de aprovisionamiento. Se producen las validaciones siguientes:

- **Integridad del archivo de instalación:** iOS compara los detalles de las aplicaciones con la clave pública del certificado de firma de la empresa. Si difieren, puede que el contenido de la aplicación haya cambiado, y esta no se podrá ejecutar.
- **Aplicación de las funcionalidades:** iOS intenta aplicar las funcionalidades de la aplicación del perfil de aprovisionamiento empresarial (no los perfiles de aprovisionamiento para desarrolladores individuales) presentes en el archivo de instalación de la aplicación (.ipa).


El certificado de firma empresarial que se usa para firmar aplicaciones normalmente tiene una validez de tres años. Sin embargo, el perfil de aprovisionamiento expira después de un año. Mientras siga siendo válido el certificado, Intune proporciona las herramientas para implementar proactivamente una nueva directiva de perfil de aprovisionamiento a dispositivos que tengan aplicaciones cuya expiración esté próxima.
Cuando el certificado haya expirado, debe volver a firmar la aplicación con un certificado nuevo e insertar un nuevo perfil de aprovisionamiento con la clave del nuevo certificado.



## <a name="how-to-find-out-when-a-line-of-business-app-will-expire"></a>Cómo averiguar cuándo expirará una aplicación de línea de negocio

1. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), seleccione **Aplicaciones** > **Aplicaciones**.
2. En la lista de aplicaciones, compruebe la columna **Expiration date** (Fecha de expiración) para ver la fecha de expiración de la aplicación. También puede establecer la lista desplegable **Filters** (Filtros) en **Expired/about to expire** (Expirada/a punto de expirar) para ver solo las aplicaciones respecto a las cuales debe actuar.

## <a name="how-to-create-an-ios-mobile-provisioning-profile-policy"></a>Cómo crear una directiva de perfil de aprovisionamiento móvil de iOS


1. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), seleccione **Directiva** > **Overview (Información general)** > **Agregar directiva**.
2. En el cuadro de diálogo **Crear nueva directiva**, elija primero **iOS** > **Directiva de perfil de aprovisionamiento móvil** y, luego, **Crear directiva**.
3. En la página **General**, configure los siguientes valores:
    - **Nombre**: proporcione un nombre para esta directiva de perfil de aprovisionamiento móvil.
    - **Descripción**: opcionalmente, especifique una descripción de la directiva.
    - **Archivo de perfil de configuración:** haga clic en **Importar** y, luego, elija un archivo de perfil de configuración móvil de Apple (con la extensión **.mobileprovision**) que ha descargado del sitio web para desarrolladores de Apple.
4. Cuando termine, elija **Guardar directiva**.
5. A continuación, implemente la directiva en los dispositivos iOS necesarios. Para más información, vea [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).
