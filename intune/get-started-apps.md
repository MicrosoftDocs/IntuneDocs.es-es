---
title: "Introducción a las aplicaciones en Microsoft Intune"
titlesuffix: 
description: "Busque aplicaciones y agréguelas a dispositivos para que sus recursos puedan trabajar."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 3/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0185eebbe436da73e1920d7cd834f0897a143894
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2018
---
# <a name="get-started-with-adding-apps-in-microsoft-intune"></a>Introducción a la adición de aplicaciones en Microsoft Intune

Para poder asignar, supervisar, configurar o proteger las aplicaciones, debe agregarlas a Intune. Intune admite varios tipos diferentes de aplicaciones. Además, las opciones disponibles varían en función del tipo de aplicación.

Intune le permite agregar y asignar estos tipos de aplicación a los dispositivos corporativos:
- **Aplicaciones de la tienda**: para dispositivos en que necesita una administración de aplicaciones móviles adicional aplicada a las aplicaciones disponibles en el App Store.
- **Aplicaciones escritas internamente (línea de negocio)**: donde carga un archivo que se descarga en los dispositivos de los usuarios.
- **Aplicaciones integradas**: donde asigna aplicaciones administradas y seleccionadas, como aplicaciones de Office 365, a dispositivos iOS y Android. 
- **Aplicaciones en la web**: donde Intune crea un acceso directo a la aplicación web en la pantalla principal del dispositivo.

## <a name="how-do-i-assign-a-public-store-app"></a>¿Cómo asigno una aplicación de almacén público?

En el ejemplo siguiente, se indican los pasos para agregar una aplicación iOS en Microsoft Intune.

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En la hoja **Intune**, elija **Aplicaciones móviles**.
4. En la carga de trabajo **Aplicaciones móviles**, elija **Aplicaciones** en la sección **Administrar**.
5. Elija **Agregar** en el lado derecho del panel **Aplicaciones**.
6. En la lista **Tipo de aplicación**, seleccione **iOS** en los tipos de **Aplicación de la Tienda** disponibles.
6. Elija **Buscar en App Store**.
7. En la hoja **Buscar en App Store**, seleccione la configuración regional del país del App Store.
8. Escriba el nombre (o parte del nombre) en el cuadro de búsqueda. Intune busca en la tienda y devuelve una lista de resultados pertinentes.
9. En la lista, elija la aplicación que quiera y haga clic en **Seleccionar**.
10. Seleccione **Información de la aplicación** para configurar la información de la aplicación.
11. (Opcional) Agregue detalles para ayudarle a organizar esta aplicación, como **Propietario**, **Notas**, **Desarrollador** y una **Dirección URL de privacidad** (que vaya a la directiva de privacidad de su empresa).
12. Seleccione **Sí** en la opción **Mostrar como aplicación destacada en el Portal de empresa**. 
13. Haga clic en **Aceptar** después de agregar toda la información de la aplicación necesaria.
14. Haga clic en **Agregar** en la hoja **Agregar aplicación**. Esto le llevará a la **Introducción** de esa aplicación. 

## <a name="next-steps"></a>Pasos siguientes

Ahora que ha agregado una aplicación a Intune, puede asignar los grupos de empleados que podrán incluir la aplicación en su dispositivo.

- [Asignación de aplicaciones a grupos](apps-deploy.md)
- 
## <a name="learn-more"></a>Obtener más información

* [¿Qué es la administración de aplicaciones mediante Intune?](app-management.md)
* [Información general sobre el ciclo de vida de la aplicación](app-lifecycle.md)
* [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md)
