---
title: Adición de Microsoft Edge para Windows 10 a Microsoft Intune
titleSuffix: ''
description: Obtenga información sobre cómo agregar Microsoft Edge para Windows a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
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
ms.openlocfilehash: b4839340ba1f3bad6f28a1120d882d0f600b1d44
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563576"
---
# <a name="add-microsoft-edge-for-windows-10-to-microsoft-intune"></a>Adición de Microsoft Edge para Windows 10 a Microsoft Intune

Antes de poder implementar, configurar, supervisar, o proteger las aplicaciones, debe agregarlas a Intune. Uno de los [tipos de aplicaciones](~/apps/apps-add.md#app-types-in-microsoft-intune) disponibles es Microsoft Edge *versión 77 y posteriores*. Al seleccionar este tipo de aplicación en Intune, puede asignar e instalar Microsoft Edge *versión 77 y posteriores* en los dispositivos que administra y que ejecutan Windows 10.

> [!IMPORTANT]
> Este tipo de aplicación está en **versión preliminar pública** y ofrece canales de desarrollador y beta para Windows 10. La implementación solo está en inglés (EN), pero los usuarios finales pueden cambiar el idioma para mostrar en el explorador desde **Configuración** > **Idiomas**. Microsoft Edge es una aplicación Win32 que se instala en el contexto del sistema y en arquitecturas similares (aplicación x86 en sistemas operativos x86 y aplicación x64 en sistemas operativos x64). Intune detectará todas las instalaciones existentes de Microsoft Edge. Si está instalado en el contexto del usuario, una instalación del sistema lo sobrescribirá. Si está instalado en el contexto del sistema, se notifica que la instalación se ha realizado correctamente. Además, las actualizaciones automáticas de Microsoft Edge están **activadas** de forma predeterminada, y Microsoft Edge no se puede desinstalar.

> [!NOTE]
> Microsoft Edge *versión 77 y posteriores* también está disponible para macOS.
> 
> No se puede usar la implementación de aplicaciones integrada de Microsoft Edge para equipos de unión al área de trabajo. La implementación de aplicaciones integradas requiere la extensión de administración de Intune, que solo existe para dispositivos unidos a AAD. Todavía puede implementar Microsoft Edge *versión 77 y posteriores* con un archivo *.msi* cargado en **Aplicaciones**; vea [Incorporación de una aplicación de línea de negocio de Windows a Microsoft Intune](~/apps/lob-apps-windows.md).

## <a name="prerequisites"></a>Requisitos previos
- Se requiere Windows 10 RS2 y versiones posteriores.
- Cualquier versión preinstalada de Microsoft Edge *versión 77 y posteriores* para los canales de **desarrollador** y **beta** en el contexto del usuario se sobrescribirá con la instalación de Edge en el contexto del sistema.

## <a name="configure-the-app-in-intune"></a>Configuración de la aplicación en Intune
Puede agregar una instancia de Microsoft Edge versión 77 y posteriores a Intune mediante los pasos siguientes:

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Aplicaciones** > **Todas las aplicaciones** > **Agregar**.
3. En la lista **Tipo de aplicación** en **Microsoft Edge, versión 77 y posteriores**, seleccione **Windows 10**.

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

## <a name="configure-app-settings"></a>Configuración de aplicaciones
En este paso, configure las opciones de instalación de la aplicación.

1. En el panel **Agregar aplicación**, seleccione **Configuración de la aplicación**.
2. En el panel **Configuración de la aplicación**, seleccione **Beta** o **Dev** en la lista **Canal** para determinar desde qué canal de Edge se implementará la aplicación.
    - El canal **Beta** es la experiencia de versión preliminar de Microsoft Edge más estable y la mejor opción para una prueba piloto completa dentro de la organización. Con actualizaciones principales cada seis semanas, cada versión incorpora los aprendizajes y las mejoras del canal de desarrollo.
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
Cuando haya terminado de configurar la aplicación, seleccione **Agregar** en el panel **Agregar aplicación**. 

La aplicación que ha creado aparece en la lista de aplicaciones, donde puede asignarla a los grupos que seleccione. 

> [!NOTE]
> Actualmente, si anula la asignación de la implementación de Microsoft Edge, permanecerá en el dispositivo.

## <a name="troubleshooting"></a>Solucionar problemas
**Microsoft Edge versión 77 y posteriores para Windows 10:**<br>
Intune usa la extensión de administración de Intune para descargar e implementar el instalador de Microsoft Edge en los dispositivos Windows 10 asignados y, después, comunica la configuración de implementación al instalador de Microsoft Edge, que descarga e instala el explorador Microsoft Edge directamente desde la red CDN. Consulte los [requisitos previos de la extensión de administración de Intune](~/apps/intune-management-extension.md#prerequisites) y los procedimientos recomendados que se describen en el acceso al servicio de actualización de Azure y la red CDN para asegurarse de que la configuración de red permite que los dispositivos Windows 10 accedan a estas ubicaciones. Además, para permitir el acceso a los archivos de instalación desde una red CDN para instalar el explorador, debe permitir el acceso a los puntos de conexión de Windows Update. Para más información, consulte [Administrar los puntos de conexión para Windows 10, versión 1809: Windows Update](https://docs.microsoft.com/windows/privacy/manage-windows-1809-endpoints#windows-update) y [Puntos de conexión de red para Microsoft Intune](~/fundamentals/intune-endpoints.md).

## <a name="next-steps"></a>Pasos siguientes
- [Asignar aplicaciones a grupos](~/apps/apps-deploy.md)
