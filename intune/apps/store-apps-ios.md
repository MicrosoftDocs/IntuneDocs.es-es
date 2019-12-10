---
title: Incorporación de aplicaciones de la tienda iOS a Microsoft Intune
titleSuffix: ''
description: Descubra cómo agregar aplicaciones de la tienda iOS a Microsoft Intune. Puede asignar aplicaciones mediante este método si son gratuitas en App Store.
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c5616b27b97d5623958ec872390e2a6de79db3c5
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563447"
---
# <a name="add-ios-store-apps-to-microsoft-intune"></a>Incorporación de aplicaciones de la tienda iOS a Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Use la información de este artículo para agregar aplicaciones de la tienda iOS a Microsoft Intune. Las aplicaciones de la tienda iOS son aplicaciones que Intune instala en los dispositivos de los usuarios. Un usuario forma parte de los trabajadores de su empresa. Las aplicaciones de la tienda iOS se actualizan automáticamente.

>[!NOTE]
>Si bien los usuarios de dispositivos iOS pueden quitar algunas de las aplicaciones iOS integradas, como Bolsa y Mapas, no pueden usar Intune para volver a implementar esas aplicaciones. Si los usuarios eliminan estas aplicaciones, deben ir a la App Store y reinstalarlas manualmente.

## <a name="before-you-start"></a>Antes de empezar

Puede asignar aplicaciones mediante este método solo si son gratuitas en la App Store. Si desea asignar aplicaciones de pago mediante Intune, considere usar el [programa de compra por volumen de iOS](vpp-apps-ios.md).

>[!NOTE]
>Cuando trabaja con Microsoft Intune, se recomienda usar el explorador Microsoft Edge o Google Chrome.

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Aplicaciones** > **Todas las aplicaciones** > **Agregar**.
3. En la lista **Tipo de aplicación**, en los tipos de **Aplicación de la Tienda**, seleccione **iOS**.
4. Seleccione **Buscar en App Store**.
5. En el panel **Buscar en App Store**, seleccione la configuración regional del país de la App Store.
6. En el cuadro de **búsqueda**, escriba el nombre (o parte del nombre) de la aplicación.  
    Intune busca en la tienda y devuelve una lista de resultados pertinentes.
7. En la lista de resultados, seleccione la aplicación que desee y, luego, **Seleccionar**.
8. En el panel **Agregar aplicación**, seleccione **Información de la aplicación** para configurar la aplicación.
9. En el panel **Información de la aplicación**, agregue la información de la aplicación. Según la aplicación que haya elegido, algunos de los valores de este panel pueden haberse rellenado automáticamente:
    - **Nombre**: escriba el nombre de la aplicación como se va a mostrar en el Portal de empresa. Asegúrese de que cualquier nombre de aplicación que use sea exclusivo. Si hay un nombre de aplicación duplicado, solo se muestra uno a los usuarios del Portal de empresa.
    - **Descripción**: Escriba una descripción de la aplicación. Esta descripción se muestra a los usuarios del Portal de empresa.
    - **Publicador**: Escriba el nombre del publicador de la aplicación.
    - **Dirección URL de Appstore**: escriba la dirección URL de App Store de la aplicación que quiere crear.
    - **Versión mínima del sistema operativo**: en la lista, seleccione la versión mínima del sistema operativo en la que se puede instalar la aplicación. Si la aplicación se asigna a un dispositivo con un sistema operativo anterior, no se instalará.
    - **Tipo de dispositivo aplicable**: en la lista, seleccione los dispositivos que usa la aplicación.
    - **Categoría**: de manera opcional, seleccione una o varias de las categorías de aplicaciones integradas o una categoría que haya creado. Esto facilita que los usuarios puedan encontrar la aplicación cuando exploran el Portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: seleccione esta opción para mostrar el conjunto de aplicaciones de forma destacada en la página principal del Portal de empresa cuando los usuarios busquen aplicaciones.
    - **Dirección URL de información**: Opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Dirección URL de privacidad**: Opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Desarrollador**: opcionalmente, escriba el nombre del desarrollador de la aplicación. Este campo solo es visible para los administradores y no para los usuarios.
    - **Propietario**: opcionalmente, escriba un nombre para el propietario de esta aplicación, por ejemplo, *Departamento de Recursos Humanos*. Este campo solo es visible para los administradores y no para los usuarios.
    - **Notas**: opcionalmente, escriba las notas que desea asociar a esta aplicación. Este campo solo lo podrán ver los administradores, pero no los usuarios finales.
    - **Logotipo**: opcionalmente, cargue un icono que se asociará con la aplicación. Este icono se muestra con la aplicación cuando los usuarios examinan el portal de empresa.
10. Seleccione **Aceptar**.
11. Seleccione **Agregar**.

La aplicación que ha creado aparece en la lista de aplicaciones, donde puede asignarla a los grupos que seleccione.

## <a name="next-steps"></a>Pasos siguientes

- [Asignar aplicaciones a grupos](apps-deploy.md)
