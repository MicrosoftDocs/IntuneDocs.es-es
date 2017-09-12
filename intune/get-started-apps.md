---
title: "Introducción a las aplicaciones"
titlesuffix: Azure portal
description: "Busque aplicaciones y agréguelas a dispositivos para que los empleados puedan trabajar."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 28bc8547d56073a2175ca57e03dbd9b94fc03ba9
ms.sourcegitcommit: fa6aaf12611c3e03e38e467806fc30b1d0255e88
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2017
---
# <a name="get-started-with-adding-apps"></a>Introducción a la adición de aplicaciones

Intune admite diferentes maneras de implementar aplicaciones en sus dispositivos corporativos:

* **Instaladores de software**: donde carga un archivo que se descarga en los dispositivos de los usuarios
* __Vínculos externos__: cuando tiene una aplicación en una tienda de aplicaciones pública o en una aplicación web
* **Aplicaciones administradas**: para los dispositivos iOS donde necesita una administración de aplicaciones móviles adicional aplicada a las aplicaciones disponibles en el App Store

Va a recorrer uno de los métodos de implementación de aplicaciones más rápido mediante la asignación de una aplicación de tienda pública.

## <a name="how-do-i-assign-a-public-store-app"></a>¿Cómo asigno una aplicación de almacén público?

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Con **Buscar recursos**, busque **Intune**.
3. Seleccione **Mobile Apps**, después seleccione **Aplicaciones**.
4. Seleccione **Agregar**, después **Aplicación de la tienda iOS** como el **Tipo de aplicación**.
5. En el cuadro de texto, busque una aplicación para asignarla al dispositivo. Seleccione la aplicación y, después, seleccione **Aceptar**.
6. En la hoja **Agregar aplicación**, seleccione **Información de la aplicación** y, después, asegúrese de que toda la información de la aplicación se ha rellenado. Puede agregar otros detalles opcionales para ayudarle a organizar esta aplicación, como **Propietario**, **Notas**, **Desarrollador** y una **Dirección URL de privacidad** para la directiva de privacidad de su empresa.
7. Asegúrese de que ha seleccionado Sí para Mostrar como aplicación destacada en el portal de empresa y, después, seleccione Aceptar.
8. Seleccione **Agregar** para agregar la aplicación. Esto le llevará a la **Información general** de la aplicación. Pulse **Asignaciones**, después haga clic en **Seleccionar grupos** para asignarla a su grupo de prueba. Haga que la aplicación esté **disponible** para su descarga. La aplicación debe aparecer entonces como una **Aplicación destacada** en su dispositivo de prueba.

## <a name="learn-more"></a>Obtener más información

* [¿Qué es la administración de aplicaciones mediante Intune?](app-management.md)
* [Información general sobre el ciclo de vida de la aplicación](app-lifecycle.md)
* [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md)
