---
title: "Adición de aplicaciones de la tienda iOS a Microsoft Intune"
titlesuffix: 
description: "Descubra cómo agregar aplicaciones de la tienda iOS a Microsoft Intune."
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/21/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b5315d683abfc38a7f42d2f322cc77c625270e3c
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2018
---
# <a name="how-to-add-ios-store-apps-to-microsoft-intune"></a>Adición de aplicaciones de la tienda iOS a Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Use la información de este artículo para agregar aplicaciones de la tienda iOS a Microsoft Intune. Las aplicaciones de la tienda iOS son aplicaciones que Intune instala en el dispositivo de un usuario. El usuario forma parte de los trabajadores de su empresa. Las aplicaciones de la tienda iOS se actualizan automáticamente. 

>[!NOTE]
>Si bien los usuarios de dispositivos iOS pueden quitar algunas de las aplicaciones iOS integradas, como Bolsa y Mapas, no pueden usar Intune para volver a implementar esas aplicaciones. Si los usuarios finales eliminan estas aplicaciones, deben ir a la tienda de aplicaciones y reinstalarlas manualmente.

## <a name="before-you-start"></a>Antes de empezar

Solo se pueden asignar aplicaciones mediante este método si son gratuitas en la tienda de aplicaciones. Si desea asignar aplicaciones de pago mediante Intune, considere usar el [programa de compra por volumen de iOS](vpp-apps-ios.md).

>[!NOTE]
>Chrome y Microsoft Edge son los exploradores recomendados cuando se trabaja con Microsoft Intune.

## <a name="step-1---search-for-the-app-in-the-store"></a>Paso 1: Búsqueda de la aplicación en la tienda

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services (Todos los servicios)** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En la hoja **Intune**, elija **Aplicaciones móviles**.
4. En la carga de trabajo **Aplicaciones móviles**, elija **Aplicaciones** en la sección **Administrar**.
5. Elija **Agregar** en el lado derecho del panel **Aplicaciones**.
6. En la lista **Tipo de aplicación**, seleccione **iOS** en los tipos de **Aplicación de la Tienda** disponibles.
6. Elija **Buscar en App Store**.
7. En la hoja **Buscar en App Store**, seleccione la configuración regional del país de la tienda de aplicaciones.
8. Escriba el nombre (o parte del nombre) en el cuadro de búsqueda. Intune busca en la tienda y devuelve una lista de resultados pertinentes.
9. En la lista, elija la aplicación que quiera y haga clic en **Seleccionar**.

## <a name="step-2---configure-app-information"></a>Paso 2: Configuración de la información de la aplicación

1. En la hoja **Agregar aplicación**, elija **Información de la aplicación** para configurar la aplicación.
2. En la hoja **Información de la aplicación**, agregue la información de la aplicación. Dependiendo de la aplicación que haya elegido, algunos de los valores de esta hoja pueden haber sido rellenados automáticamente:
- **Nombre**: escriba el nombre de la aplicación que se mostrará en el portal de empresa. Asegúrese de que todos los nombres de aplicación que usa son únicos. Si el mismo nombre de aplicación aparece dos veces, en el portal de empresa solo se muestra una de las aplicaciones a los usuarios.
- **Descripción**: escriba una descripción para la aplicación que se mostrará a los usuarios en el portal de empresa.
- **Editor:** escriba el nombre del editor de la aplicación.
- **Dirección URL de AppStore**: escriba la dirección URL de la tienda de aplicaciones de la aplicación que quiere crear.
- **Sistema operativo mínimo**: en la lista, elija la versión mínima del sistema operativo en la que se puede instalar la aplicación. La aplicación no se instalará en un dispositivo con un sistema operativo anterior.
- **Tipo de dispositivo aplicable**: en la lista, seleccione los dispositivos que usa la aplicación.
- **Categoría** (opcional). Seleccione una o más de las categorías de aplicaciones integradas, o una categoría que haya creado. Las categorías facilitan a los usuarios encontrar la aplicación cuando exploran el portal de empresa.
- **Mostrar como aplicación destacada en el Portal de empresa**: la aplicación se muestra de forma destacada en la página principal del portal de empresa cuando los usuarios buscan aplicaciones.
- **Dirección URL de información**: si quiere, puede escribir la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
- **Dirección URL de privacidad**: si quiere, puede escribir la dirección URL de un sitio web que contenga información de privacidad sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
- **Desarrollador**: si quiere, puede escribir el nombre del desarrollador de la aplicación. Este campo solo lo podrán ver los administradores, pero no los usuarios finales.
- **Propietario**: si quiere, puede escribir un nombre para el propietario de esta aplicación, por ejemplo, **departamento de Recursos Humanos**.  Este campo solo lo podrán ver los administradores, pero no los usuarios finales.
- **Notas**: escriba notas que le gustaría asociar a esta aplicación. Este campo solo lo podrán ver los administradores, pero no los usuarios finales.
- **Logotipo**: cargue un icono que esté asociado a la aplicación. El icono se muestra con la aplicación cuando los usuarios examinan el portal de empresa.
3. Cuando haya terminado, haga clic en **Aceptar** en la hoja **Agregar información**.
4. Haga clic en **Agregar** en la hoja **Agregar aplicación**. 

La aplicación que ha creado aparece en la lista de aplicaciones, donde puede asignarla a los grupos que elija. 

## <a name="next-steps"></a>Pasos siguientes

- [Asignación de aplicaciones a grupos](apps-deploy.md)
