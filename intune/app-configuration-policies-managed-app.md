---
title: "Agregar directivas de configuración para aplicaciones administradas sin inscripción de dispositivos | Microsoft Docs"
titlesuffix: Azure portal
description: "Obtenga información sobre cómo usar directivas de configuración para aplicaciones administradas sin inscripción de dispositivos."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: E61C1618-79D0-41A1-B61F-4123FB6672FC
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 750ce7dbb0dccf08757e076826e2d3650b6e6ab5
ms.sourcegitcommit: 67c037af31c1f167ec9b4f4baa754631c817e7d1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2017
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>Agregar directivas de configuración para aplicaciones administradas sin inscripción de dispositivos

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Puede usar directivas de configuración de aplicaciones con aplicaciones administradas que admiten Intune App SDK incluso en los dispositivos que no están inscritos. 

1. Inicie sesión en Azure Portal.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** + **Intune**.
3. Elija la carga de trabajo **Aplicaciones móviles**.
4. En el grupo **Administrar**, haga clic en **Directivas de configuración de aplicaciones** y en **Agregar**.
5. Especifique los siguientes detalles:
    - **Nombre**  
      Nombre del perfil que aparecerá en Azure Portal.
    - **Descripción**  
      Descripción del perfil que aparecerá en Azure Portal.
    - **Tipo de inscripción del dispositivo**  
      Elija **Administrar aplicaciones**.
6. Seleccione **Aplicación asociada** para elegir la aplicación que se va a configurar. Seleccione la aplicación en la lista de aplicaciones que ha aprobado y sincronizado con Intune.
7. Para cada opción de configuración compatible con la aplicación, escriba el **Nombre** y **Valor**, y haga clic en los puntos suspensivos (**...**).  
    Para eliminar una configuración, haga clic en los puntos suspensivos (**...**) y seleccione **Eliminar**.  
    Las aplicaciones habilitadas para Intune App SDK admiten configuraciones en pares de clave y valor. Consulte la documentación de cada aplicación obtener más información sobre qué configuraciones de clave y valor se admiten.  
    Además, puede usar tokens que se rellenarán de forma dinámica con datos generados por la aplicación.

## <a name="configuration-values-using-tokens"></a>Valores de configuración con tokens

Ciertos tokens se pueden generar y enviar a la aplicación administrada por Intune. Por ejemplo, si la configuración de la aplicación incluye una opción de correo electrónico, puede usar un token para agregar un correo electrónico dinámico. Escriba el nombre esperado por la aplicación en el campo **Nombre** y luego escriba `\{\{mail\}\}` en el campo **Valor**.

Intune admite los siguientes tipos de token en las opciones de configuración:

- \{\{userprincipalname\}\} - (Ejemplo: **John@contoso.com**)
- \{\{mail\}\} - (Ejemplo: **John@contoso.com**)
- \{\{partialupn\}\} - (Ejemplo: **Alberto**)
- \{\{accountid\}\} - (Ejemplo: **fc0dc142-71d8-4b12-bbea-bae2a8514c81**)
- \{\{deviceid\}\} - (Ejemplo: **b9841cd9-9843-405f-be28-b2265c59ef97**)
- \{\{userid\}\} - (Ejemplo: **3ec2c00f-b125-4519-acf0-302ac3761822**)
- \{\{username\}\} - (Ejemplo: **Alberto Tercedor**)
- \{\{PrimarySMTPAddress\}\} - (Ejemplo: testuser@ad.domain.com) 


> [!Note]  
> Los caracteres \{\{ y \}\} solo se usan para los tipos de token y no deben usarse para otros fines.

## <a name="next-steps"></a>Pasos siguientes

Siga [asignando](apps-deploy.md) y [supervisando](apps-monitor.md) la aplicación como de costumbre.