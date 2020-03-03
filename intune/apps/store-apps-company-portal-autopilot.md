---
title: Adición y asignación de la aplicación Portal de empresa de Windows 10 para dispositivos aprovisionados con Autopilot
titleSuffix: Microsoft Intune
description: Agregue y asigne la aplicación Portal de empresa de Windows 10 a Intune para dispositivos aprovisionados con Autopilot.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c13d8d774037f0d2db5832af7f39c864330fef30
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/25/2020
ms.locfileid: "77577290"
---
# <a name="add-and-assign-the-windows-10-company-portal-app-for-autopilot-provisioned-devices"></a>Adición y asignación de la aplicación Portal de empresa de Windows 10 para dispositivos aprovisionados con Autopilot

Para administrar dispositivos e instalar aplicaciones, los usuarios pueden usar la aplicación Portal de empresa. Puede asignar la aplicación Portal de empresa de Windows 10 directamente desde Intune. 

## <a name="prerequisites"></a>Requisitos previos

En el caso de los dispositivos Windows 10 aprovisionados con Autopilot, se recomienda asociar la cuenta de Microsoft Store para Empresas con Intune. Para obtener más información, vea [Administración de aplicaciones compradas por volumen en Microsoft Store para Empresas con Microsoft Intune](~/apps/windows-store-for-business.md).

Portal de empresa (sin conexión) se elige para instalarse mediante los pasos siguientes. La aplicación Portal de empresa se instalará en el contexto de dispositivo cuando se asigne al grupo de Autopilot y se instalará en el dispositivo antes de que el usuario inicie sesión. 

## <a name="configure-settings-to-show-offline-apps"></a>Configuración de las opciones para mostrar las aplicaciones sin conexión
1. Inicie sesión en [Microsoft Store para Empresas](https://www.microsoft.com/business-store) con la cuenta de administrador.
2. Haga clic en la pestaña **Administrar**, situada cerca de la parte superior de la ventana.
3. En el panel de la izquierda, seleccione **Configuración**.
4. En **Experiencia de compra**, establezca **Mostrar aplicaciones sin conexión** en **Activado**.  
    Se muestran las aplicaciones con licencia sin conexión.

## <a name="get-the-offline-company-portal-app"></a>Obtención de la aplicación Portal de empresa sin conexión
1. Busque y seleccione la aplicación **Portal de empresa**.
2. Establezca **Tipo de licencia** en **Sin conexión**.
3. Seleccione **Obtener la aplicación** para adquirir y agregar la aplicación Portal de empresa sin conexión al inventario.

## <a name="assign-the-company-portal-app"></a>Asignación de la aplicación Portal de empresa
1. Inicie sesión en el  [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431)  con la cuenta de administrador. 
2. Seleccione la pestaña  **Aplicaciones** en el panel de la derecha. 
3. En  **Por plataforma**, seleccione **Windows**. 
4. Seleccione  **Portal de empresa (sin conexión)**.   
5. Debe esperar a que se complete la programación de sincronización, o bien realizar una sincronización manual desde el Centro de administración del Administrador de puntos de conexión de Microsoft.
6. Asigne la aplicación Portal de empresa como una aplicación necesaria a los grupos de dispositivos Autopilot seleccionados.

## <a name="next-steps"></a>Pasos siguientes

- Para obtener más información sobre cómo asignar aplicaciones, vea [Asignación de aplicaciones a grupos](apps-deploy.md).

