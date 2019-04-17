---
title: Directivas de configuración para aplicaciones administradas sin inscripción de dispositivos
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo configurar directivas para aplicaciones administradas sin inscripción de dispositivos.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/15/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: E61C1618-79D0-41A1-B61F-4123FB6672FC
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 69340d8a5bee9dbeb74c0ed0792d53c770f3f3c3
ms.sourcegitcommit: 8c795b041cd39e3896595f64f53ace48be0ec84c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2019
ms.locfileid: "59587457"
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>Agregar directivas de configuración para aplicaciones administradas sin inscripción de dispositivos

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Puede usar directivas de configuración de aplicaciones con aplicaciones administradas que admiten Intune App SDK incluso en los dispositivos que no están inscritos. 

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. Elija la carga de trabajo **Aplicaciones cliente**.
4. En el grupo **Administrar**, elija **Directivas de configuración de aplicaciones** y **Agregar**.
5. Especifique los siguientes detalles:
    - **Nombre**  
      Nombre del perfil que aparecerá en Azure Portal.
    - **Descripción**  
      Descripción del perfil que aparecerá en Azure Portal.
    - **Tipo de inscripción del dispositivo**  
      Elija **Administrar aplicaciones**.
6. Seleccione **Aplicación asociada**  para elegir la aplicación que se va a configurar. Seleccione la aplicación en la lista de aplicaciones que ha aprobado y sincronizado con Intune.
7. En cada opción de configuración que la aplicación admita, escriba el **Nombre** y **Valor** y elija los puntos suspensivos (**...**).  
    Para eliminar una configuración, elija los puntos suspensivos (**...**) y seleccione **Eliminar**.  
    
Las aplicaciones habilitadas para Intune App SDK admiten configuraciones en pares de clave y valor. Para obtener más información sobre qué configuraciones de clave y valor se admiten, consulte la documentación de cada aplicación. Tenga en cuenta que puede usar tokens que se rellenarán de forma dinámica con datos generados por la aplicación. Para obtener información sobre los ajustes de directivas de Outlook para la configuración de aplicaciones iOS, vea [Manage Outlook for iOS app configuration with Microsoft Intune](https://technet.microsoft.com/library/mt813789(v=exchg.150).aspx) (Administración de Outlook para la configuración de aplicaciones iOS con Microsoft Intune).

## <a name="configuration-values-for-using-tokens"></a>Valores de configuración para usar tokens

Intune puede generar ciertos tokens y enviarlos a la aplicación administrada. Por ejemplo, si la configuración de la aplicación incluye una opción de correo electrónico, puede usar un token para agregar un correo electrónico dinámico. Escriba el nombre esperado por la aplicación en el campo **Nombre** y luego escriba `\{\{mail\}\}` en el campo **Valor**.

Intune admite los siguientes tipos de token en las opciones de configuración. No se admiten otros pares clave/valor personalizados.

- \{\{userprincipalname\}\}. Por ejemplo, John@contoso.com
- \{\{mail\}\}. Por ejemplo, John@contoso.com
- \{\{partialupn\}\}. Por ejemplo, John
- \{\{accountid\}\}. Por ejemplo, fc0dc142-71d8-4b12-bbea-bae2a8514c81
- \{\{userid\}\}. Por ejemplo, 3ec2c00f-b125-4519-acf0-302ac3761822
- \{\{username\}\}. Por ejemplo, John Doe
- \{\{PrimarySMTPAddress\}\}. Por ejemplo, testuser@ad.domain.com


> [!Note]  
> Los caracteres \{\{ y \}\} solo se usan para los tipos de token y no deben usarse para otros fines.

## <a name="next-steps"></a>Pasos siguientes

Siga [asignando](apps-deploy.md) y [supervisando](apps-monitor.md) la aplicación como de costumbre.
