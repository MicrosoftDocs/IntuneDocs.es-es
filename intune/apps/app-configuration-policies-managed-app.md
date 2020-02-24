---
title: Directivas de configuración para aplicaciones administradas sin inscripción de dispositivos
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo configurar directivas para aplicaciones administradas sin inscripción de dispositivos.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: E61C1618-79D0-41A1-B61F-4123FB6672FC
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4301afca471d0aa56fa1a0826ad7f88bcdf23de2
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414865"
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>Agregar directivas de configuración para aplicaciones administradas sin inscripción de dispositivos

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Puede usar directivas de configuración de aplicaciones con aplicaciones administradas que admiten Intune App SDK incluso en los dispositivos que no están inscritos. 

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Elija **Aplicaciones** > **Directivas de configuración de aplicaciones** > **Agregar** > **Aplicaciones administradas**.
3. En la página **Aspectos básicos**, establezca los detalles siguientes:
    - **Nombre**: Nombre del perfil que aparecerá en Azure Portal.
    - **Descripción**: Descripción del perfil que aparecerá en Azure Portal.
    - **Tipo de inscripción del dispositivo**: está seleccionada la opción Aplicaciones administradas.
4. Elija **Seleccionar aplicaciones públicas** o **Seleccionar aplicaciones personalizadas** para seleccionar la aplicación que va a capturar. Seleccione la aplicación en la lista de aplicaciones que ha aprobado y sincronizado con Intune.
5. Haga clic en **Siguiente** para abrir la página **Configuración**.
6. En cada opción de configuración que la aplicación admita, escriba el **Nombre** y **Valor**. 

   Las aplicaciones habilitadas para Intune App SDK admiten configuraciones en pares de clave y valor. Para obtener más información sobre qué configuraciones de clave y valor se admiten, consulte la documentación de cada aplicación. Tenga en cuenta que puede usar tokens que se rellenarán de forma dinámica con datos generados por la aplicación. Para más información, consulte [Valores de configuración para usar tokens](~/apps/app-configuration-policies-managed-app.md#configuration-values-for-using-tokens). Para obtener información sobre los ajustes de las directivas de Outlook para la configuración de aplicaciones iOS/iPadOS, vea [Administración de Outlook para la configuración de aplicaciones iOS/iPadOS con Microsoft Intune](https://technet.microsoft.com/library/mt813789(v=exchg.150).aspx).

    Para eliminar una configuración, elija los puntos suspensivos ( **...** ) y seleccione **Eliminar**.  

7. Haga clic en **Siguiente** para abrir la página **Asignaciones**.
8. Haga clic en **Seleccionar grupos para incluir**.
9. Seleccione un grupo en el panel **Seleccionar grupos para incluir** y haga clic en **Seleccionar**.
10. Haga clic en **Seleccionar grupos para excluir** para mostrar el panel relacionado.
11. Seleccione los grupos que quiera excluir y después haga clic en **Seleccionar**.

    >[!NOTE]
    >Al agregar un grupo, si ya se ha incluido otro a un tipo de asignación determinado, este se preselecciona y no se puede cambiar por otros tipos de asignación de inclusión. Por lo tanto, ese grupo que se ha usado no se puede usar como un grupo de exclusión.

12. Elija **Siguiente** para mostrar la página **Revisar y crear**.
13. Haga clic en **Crear** para agregar la Ddrectiva de configuración de aplicaciones a Intune.

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
