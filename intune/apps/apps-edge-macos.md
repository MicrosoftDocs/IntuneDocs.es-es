---
title: Adición de Microsoft Edge a dispositivos macOS con Microsoft Intune
titleSuffix: ''
description: Aprenda a agregar Microsoft Edge a dispositivos macOS con Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: kellieei
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6ebcb81cd0f186a3fd23e0701d12ea871eab129a
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912580"
---
# <a name="add-microsoft-edge-to-macos-devices-using-microsoft-intune"></a>Adición de Microsoft Edge a dispositivos macOS con Microsoft Intune

Para poder implementar, configurar, supervisar o proteger aplicaciones, antes debe agregarlas a Intune. Uno de los [tipos de aplicaciones](~/apps/apps-add.md#app-types-in-microsoft-intune) disponibles es Microsoft Edge *versión 77 y posteriores*. Al seleccionar este tipo de aplicación en Intune, puede asignar e instalar Microsoft Edge *versión 77 y posteriores* en los dispositivos que administra y que ejecutan macOS. Este tipo de aplicación facilita la asignación de Microsoft Edge a dispositivos macOS sin necesidad de usar la herramienta de ajuste de aplicaciones de macOS. Para ayudar a mantener las aplicaciones más seguras y actualizadas, la aplicación incluye Microsoft AutoUpdate (MAU).

> [!IMPORTANT]
> Este tipo de aplicación está en **versión preliminar pública** y ofrece canales de desarrollador y beta para macOS. La implementación solo está en inglés (EN), pero los usuarios finales pueden cambiar el idioma para mostrar en el explorador, en **Configuración** > **Idiomas**. 

> [!NOTE]
> Microsoft Edge *versión 77 y posteriores* también está disponible para Windows 10.

## <a name="prerequisites"></a>Requisitos previos
- El dispositivo macOS debe ejecutar macOS 10.12 o una versión posterior para poder instalar Microsoft Edge.

## <a name="add-microsoft-edge-to-intune"></a>Adición de Microsoft Edge a Intune
Puede agregar a Intune una instancia de Microsoft Edge versión 77 y posteriores haciendo lo siguiente:

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Aplicaciones** > **Todas las aplicaciones** > **Agregar**.
3. En la lista **Tipo de aplicación** en **Microsoft Edge, versión 77 y posteriores**, seleccione **macOS**.

## <a name="configure-app-information"></a>Configuración de información de la aplicación
En este paso, proporcionará información sobre la implementación de esta aplicación. Esta información ayuda a identificar la aplicación en Intune y sirve para que los usuarios la encuentren en el Portal de empresa.

1. Haga clic en **Información de la aplicación** para mostrar el panel **Información de la aplicación**.
2. En el panel **Información de la aplicación**, proporcione información sobre la implementación de esta aplicación. Esta información ayuda a identificar la aplicación en Intune y sirve para que los usuarios la encuentren en el Portal de empresa.
    - **Nombre**: Escriba el nombre de la aplicación tal como se mostrará en el portal de empresa. Asegúrese de que todos los nombres son únicos. Si el mismo nombre de aplicación existe dos veces, solo se muestra a los usuarios una de las aplicaciones en el portal de empresa.
    - **Descripción**: Escriba una descripción de la aplicación. Por ejemplo, podría enumerar los usuarios de destino en la descripción.
    - **Publicador**: Microsoft aparece como publicador.
    - **Categoría**: de manera opcional, seleccione una o varias de las categorías de aplicaciones integradas o una categoría que haya creado. Este valor facilita que los usuarios encuentren la aplicación cuando exploren el Portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: seleccione esta opción para mostrar la aplicación de forma destacada en la página principal del Portal de empresa cuando los usuarios busquen aplicaciones.
    - **Dirección URL de información**: Opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Dirección URL de privacidad**: Opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Desarrollador**: Microsoft aparece como desarrollador.
    - **Propietario**: Microsoft aparece como propietario.
    - **Notas**: opcionalmente, escriba las notas que desea asociar a esta aplicación.
3. Seleccione **Aceptar**.

## <a name="configure-microsoft-edge-settings"></a>Configuración de las opciones de Microsoft Edge
En este paso, configure las opciones de instalación de la aplicación.

1. En el panel **Agregar aplicación**, seleccione **Configuración de la aplicación**.
2. En el panel **Configuración de la aplicación**, seleccione **Estable**, **Beta** o **Desarrollo** en la lista **Canal** para determinar desde qué canal de Edge se implementará la aplicación.

    - El canal **estable** es el canal recomendado para la implementación en general en entornos empresariales. Se actualiza cada seis semanas y cada versión incorpora mejoras del canal beta.
    - El canal **beta** es la experiencia de versión preliminar de Microsoft Edge más estable y la mejor opción para tener una prueba piloto completa dentro de la organización. Con actualizaciones principales cada seis semanas, cada versión incorpora los aprendizajes y las mejoras del canal de desarrollo.
    - El canal de **desarrollo** está listo para los comentarios empresariales en Windows, Windows Server y macOS. Se actualiza cada semana y contiene las mejoras y correcciones más recientes.

    > [!NOTE]
    > El logotipo del explorador Microsoft Edge se muestra con la aplicación cuando los usuarios examinan el Portal de empresa.

3.  Seleccione **Aceptar**.

## <a name="select-scope-tags-optional"></a>Selección de Etiquetas de ámbito (opcional)
Puede usar las etiquetas de ámbito para determinar quién puede ver información de la aplicación cliente en Intune. Para más información sobre las etiquetas de ámbito, vea Uso del control de acceso basado en rol y de las etiquetas de ámbito para la TI distribuida.
1.  Seleccione **Ámbito (Etiquetas)**  > **Agregar**.
2.  Use el cuadro **Seleccionar** para buscar las etiquetas de ámbito.
3.  Seleccione la casilla de verificación situada junto a las etiquetas de ámbito que desea asignar a esta aplicación.
4.  Haga clic en **Seleccionar** > **Aceptar**.

## <a name="add-the-app"></a>Agregar la aplicación
Cuando acabe de configurar, seleccione **Agregar** en el panel **Agregar aplicación**. 

La aplicación que ha creado aparece en la lista de aplicaciones, donde puede asignarla a los grupos que seleccione. 

> [!NOTE]
> Actualmente, Apple no proporciona ningún método para que Intune desinstale Microsoft Edge en dispositivos macOS.

## <a name="next-steps"></a>Pasos siguientes
- Para más información sobre cómo configurar Microsoft Edge en dispositivos macOS, vea [Configuración de Microsoft Edge en dispositivos macOS](https://docs.microsoft.com/deployedge/configure-microsoft-edge-on-mac).
- Para información sobre cómo incluir y excluir las asignaciones de aplicaciones para grupos de usuarios, consulte [Inclusión y exclusión de asignaciones de aplicaciones](~/apps/apps-inc-exl-assignments.md).
- [Asignar aplicaciones a grupos](~/apps/apps-deploy.md)

