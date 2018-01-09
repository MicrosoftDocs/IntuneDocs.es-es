---
title: "Cómo agregar aplicaciones iOS de la tienda a Intune | Microsoft Docs"
titlesuffix: Azure portal
description: "Obtenga información sobre cómo agregar aplicaciones iOS de la tienda a Intune\"."
keywords: Intune
author: Erikre
ms.author: erikre
manager: angrobe
ms.date: 09/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7dcb857127b3c36d2b90208aac9b8ad901e31d89
ms.sourcegitcommit: 833b1921ced35be140f0107d0b4205ecacd2753b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2018
---
# <a name="how-to-add-ios-store-apps-to-microsoft-intune"></a>Adición de aplicaciones de la tienda iOS a Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Use la información de este tema para agregar a Intune aplicaciones de la tienda de iOS.

>[!NOTE]
>Si bien los usuarios de dispositivos iOS pueden quitar algunas de las aplicaciones iOS integradas, como Bolsa y Mapas, no pueden usar Intune para volver a implementar esas aplicaciones. Si los usuarios finales eliminan estas aplicaciones, deben ir a la tienda de aplicaciones y reinstalarlas manualmente.

## <a name="before-you-start"></a>Antes de empezar

Solo se pueden asignar aplicaciones mediante este método si son gratuitas en la tienda de aplicaciones. Si desea asignar aplicaciones de pago mediante Intune, considere usar el [programa de compra por volumen de iOS](vpp-apps-ios.md).


## <a name="step-1---search-for-the-app-in-the-store"></a>Paso 1: Búsqueda de la aplicación en la tienda

1. Inicie sesión en el portal de Azure.
2. Elija **Más servicios** > **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Administrar aplicaciones**.
4. En la carga de trabajo **Mobile Apps**, elija Administrar > **Aplicaciones**.
5. Encima de la lista de aplicaciones, elija **Agregar**.
6. En la hoja **Agregar aplicación**, elija **Buscar en App Store**.
7. En la hoja **App Store de Apple**, seleccione la configuración regional del país del App Store.
8. Escriba el nombre (o parte del nombre) en el cuadro de búsqueda. Intune busca en la tienda y devuelve una lista de resultados pertinentes.
9. En la lista, elija la aplicación que desee y haga clic en **Aceptar**.

## <a name="step-2---configure-app-information"></a>Paso 2: Configuración de la información de la aplicación

1. En la hoja **Agregar aplicación**, elija **Información de la aplicación**.
2. En la hoja **Editar aplicación**, configure la información de la aplicación. Cuando haya terminado, haga clic en **Aceptar**. Dependiendo de la aplicación que haya elegido, algunos de los valores de esta hoja pueden haber sido rellenados automáticamente:
- **Nombre**: escriba el nombre de la aplicación que se mostrará en el portal de empresa. Asegúrese de que todos los nombres de aplicación que usa son únicos. Si el mismo nombre de aplicación aparece dos veces, en el portal de empresa solo se muestra una de las aplicaciones a los usuarios.
- **Descripción**: escriba una descripción para la aplicación que se mostrará a los usuarios en el portal de empresa.
- **Editor:** escriba el nombre del editor de la aplicación.
- **Dirección URL de AppStore**: escriba la dirección URL de la tienda de aplicaciones de la aplicación que quiere crear.
- **País o región de la tienda**: seleccione la configuración regional del país de la tienda de aplicaciones.
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
3. Cuando haya terminado, en la hoja **Agregar aplicación**, elija **Aceptar**.

La aplicación que ha creado aparece en la lista de aplicaciones, donde puede asignarla a los grupos que elija. Para obtener ayuda, consulte [Asignación de aplicaciones a grupos](apps-deploy.md).
