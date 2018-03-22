---
title: Introducción a las aplicaciones en Microsoft Intune
titlesuffix: ''
description: Busque aplicaciones y agréguelas a dispositivos para que sus recursos puedan trabajar.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 3/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3198a62e437e5ccaa3cfc71d1f643f073d41ed05
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="get-started-with-adding-apps-in-microsoft-intune"></a>Introducción a la adición de aplicaciones en Microsoft Intune

Para poder asignar, supervisar, configurar o proteger las aplicaciones, debe agregarlas a Intune. Intune admite varios tipos diferentes de aplicaciones. Además, las opciones disponibles varían en función del tipo de aplicación.

Intune le permite agregar y asignar estos tipos de aplicación a los dispositivos corporativos:
- **Aplicaciones de la tienda**: para dispositivos en que necesita una administración de aplicaciones móviles adicional aplicada a las aplicaciones disponibles en el App Store.
- **Aplicaciones escritas internamente (línea de negocio)**: donde carga un archivo que se descarga en los dispositivos de los usuarios.
- **Aplicaciones integradas**: donde asigna aplicaciones administradas y seleccionadas, como aplicaciones de Office 365, a dispositivos iOS y Android.
- **Aplicaciones en la web**: donde Intune crea un acceso directo a la aplicación web en la pantalla principal del dispositivo.

## <a name="how-do-i-assign-a-public-store-app"></a>¿Cómo asigno una aplicación de almacén público?

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. Seleccione **Mobile Apps**, después seleccione **Aplicaciones**.
4. Seleccione **Agregar** y después seleccione **iOS** como **Tipo de aplicación**.
5. Elija **Seleccionar aplicación** para mostrar el panel **Buscar en App Store**.
6. En el cuadro de texto, busque una aplicación para asignarla al dispositivo. Elija la aplicación y después haga clic en **Seleccionar**.
7. En el panel **Agregar aplicación**, seleccione **Información de la aplicación** y, después, asegúrese de que toda la información de la aplicación se ha rellenado. Puede agregar otros detalles opcionales para ayudarle a organizar esta aplicación, como **Propietario**, **Notas**, **Desarrollador** y una **Dirección URL de privacidad** para la directiva de privacidad de su empresa.
8. Asegúrese de que ha seleccionado **Sí** en **Mostrar como aplicación destacada en el Portal de empresa** y después seleccione **Aceptar**.
9. Seleccione **Agregar** en el panel **Agregar aplicación** para agregar la aplicación. Esta acción le dirigirá a la **Información general** de la aplicación. Seleccione **Asignaciones** y después haga clic en **Agregar grupos** para asignarla a su grupo de prueba. Haga que la aplicación esté **disponible** para su descarga. La aplicación debe aparecer entonces como una **Aplicación destacada** en su dispositivo de prueba.


- [Asignación de aplicaciones a grupos](apps-deploy.md)

## <a name="learn-more"></a>Obtener más información

* [¿Qué es la administración de aplicaciones mediante Intune?](app-management.md)
* [Información general sobre el ciclo de vida de la aplicación](app-lifecycle.md)
* [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md)
