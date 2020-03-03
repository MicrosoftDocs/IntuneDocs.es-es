---
title: Incorporación de aplicaciones de la tienda iOS a Microsoft Intune
titleSuffix: ''
description: Descubra cómo agregar aplicaciones de la tienda iOS a Microsoft Intune. Puede asignar aplicaciones mediante este método si son gratuitas en App Store.
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
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
ms.openlocfilehash: f2baf60fed2c6010e5ae0784cda166ac4fabfd57
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511742"
---
# <a name="add-ios-store-apps-to-microsoft-intune"></a>Incorporación de aplicaciones de la tienda iOS a Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Use la información de este artículo para agregar aplicaciones de la tienda iOS a Microsoft Intune. Las aplicaciones de la tienda iOS son aplicaciones que Intune instala en los dispositivos de los usuarios. Un usuario forma parte de los trabajadores de su empresa. Las aplicaciones de la tienda iOS se actualizan automáticamente.

>[!NOTE]
>Si bien los usuarios de dispositivos iOS/iPadOS pueden quitar algunas de las aplicaciones iOS/iPadOS integradas, como Bolsa y Mapas, no pueden usar Intune para volver a implementarlas. Si los usuarios eliminan estas aplicaciones, deben ir a la App Store y reinstalarlas manualmente.

## <a name="before-you-start"></a>Antes de empezar

Puede asignar aplicaciones mediante este método solo si son gratuitas en la App Store. Si quiere asignar aplicaciones de pago mediante Intune, considere la posibilidad de usar el [programa de compra por volumen de iOS/iPadOS](vpp-apps-ios.md).

>[!NOTE]
>Cuando trabaja con Microsoft Intune, se recomienda usar el explorador Microsoft Edge o Google Chrome.

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Aplicaciones** > **Todas las aplicaciones** > **Agregar**.
3. En el panel **Seleccionar tipo de aplicación**, en los tipos de **Aplicación de la Tienda** disponibles, seleccione la **Aplicación de la tienda iOS**.
4. Haga clic en **Seleccionar**.<br>
   Se muestran los pasos para **Agregar aplicación**.
5. Seleccione **Buscar en App Store**.
6. En el panel **Buscar en App Store**, seleccione la configuración regional del país de la App Store.
7. En el cuadro de **búsqueda**, escriba el nombre (o parte del nombre) de la aplicación.  
    Intune busca en la tienda y devuelve una lista de resultados pertinentes.
8. En la lista de resultados, seleccione la aplicación que desee y, luego, **Seleccionar**.<br>

   La página **Información de la aplicación** se mostrará en el panel **Agregar aplicación**. Cuando sea posible, se agregará información de la aplicación en función de la aplicación que haya seleccionado en la tienda.

9. En la página **Información de la aplicación**, agregue los detalles de la aplicación. Según la aplicación que haya elegido, algunos de los valores de este panel pueden haberse rellenado automáticamente:
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
10. Haga clic en **Siguiente** para mostrar la página **Etiquetas de ámbito**.
11. Si quiere, haga clic en **Seleccionar etiquetas de ámbito** para agregar etiquetas de ámbito para la aplicación. Para más información, consulte [Usar control de acceso basado en rol (RBAC) y etiquetas de ámbito para TI distribuida](~/fundamentals/scope-tags.md).
12. Haga clic en **Siguiente** para abrir la página **Asignaciones**.
13. Seleccione las asignaciones de grupo para la aplicación. Para más información, consulte [Agregar grupos para organizar usuarios y dispositivos](~/fundamentals/groups-add.md). 
14. Elija **Siguiente** para mostrar la página **Revisar y crear**. Revise los valores y la configuración que especificó para la aplicación.
15. Cuando haya terminado, haga clic en **Crear** para agregar la aplicación a Intune.

Se muestra la hoja **Información general** de la aplicación que creó.

## <a name="next-steps"></a>Pasos siguientes

- [Asignar aplicaciones a grupos](apps-deploy.md)
