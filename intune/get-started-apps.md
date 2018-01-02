---
title: "Introducción a las aplicaciones"
titlesuffix: Azure portal
description: "Busque aplicaciones y agréguelas a dispositivos para que los empleados puedan trabajar."
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 12/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bb02c362f056c454f4d141ce7ae20b9c3ca8035d
ms.sourcegitcommit: a7c1e10e615e5c975bb5d52eca986c5cf5287687
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2017
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
4. Seleccione **Agregar**, luego **iOS** en **Aplicación de la tienda** como **Tipo de aplicación**.
5. Elija **Seleccionar aplicación** para mostrar la hoja **Buscar en App Store**.
6. En el cuadro de texto, busque una aplicación para asignarla al dispositivo. Elija la aplicación y después haga clic en **Seleccionar**.
7. En la hoja **Agregar aplicación**, seleccione **Información de la aplicación** y, después, asegúrese de que toda la información de la aplicación se ha rellenado. Puede agregar otros detalles opcionales para ayudarle a organizar esta aplicación, como **Propietario**, **Notas**, **Desarrollador** y una **Dirección URL de privacidad** para la directiva de privacidad de su empresa.
8. Asegúrese de que ha seleccionado **Sí** en **Mostrar como aplicación destacada en el Portal de empresa** y después seleccione **Aceptar**.
9. Seleccione **Agregar** en la hoja **Agregar aplicación** para agregar la aplicación. Esto le llevará a la **Información general** de la aplicación. Pulse **Asignaciones**, después haga clic en **Seleccionar grupos** para asignarla a su grupo de prueba. Haga que la aplicación esté **disponible** para su descarga. La aplicación debe aparecer entonces como una **Aplicación destacada** en su dispositivo de prueba.

## <a name="learn-more"></a>Obtener más información

* [¿Qué es la administración de aplicaciones mediante Intune?](app-management.md)
* [Información general sobre el ciclo de vida de la aplicación](app-lifecycle.md)
* [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md)
