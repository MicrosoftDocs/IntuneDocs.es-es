---
title: Adición de ATP de Microsoft Defender a dispositivos macOS con Microsoft Intune
titleSuffix: ''
description: Obtenga información sobre cómo agregar ATP de Microsoft Defender a dispositivos macOS con Microsoft Intune.
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
ms.openlocfilehash: 6ae6e8a621b10ec969fa3fcfb2dfeabb8d5a7bdd
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569565"
---
# <a name="add-microsoft-defender-atp-to-macos-devices-using-microsoft-intune"></a>Adición de ATP de Microsoft Defender a dispositivos macOS con Microsoft Intune

Para poder implementar, configurar, supervisar o proteger aplicaciones, antes debe agregarlas a Intune. Uno de los [tipos de aplicación](~/apps/apps-add.md#app-types-in-microsoft-intune) disponibles es Advanced Threat Protection (ATP) de Microsoft Defender. Al seleccionar este tipo de aplicación en Intune, puede asignar e instalar ATP de Microsoft Defender en los dispositivos que administra y que ejecutan macOS. Este tipo de aplicación facilita la asignación de ATP de Microsoft Defender a dispositivos macOS sin necesidad de usar la herramienta de ajuste de aplicaciones de macOS. Para ayudar a mantener las aplicaciones más seguras y actualizadas, la aplicación incluye Microsoft AutoUpdate (MAU).

## <a name="prerequisites"></a>Requisitos previos
- El dispositivo macOS debe ejecutar macOS 10.13 o posterior.
- El dispositivo macOS debe tener al menos 650 MB de espacio en disco.
- Implemente la extensión de kernel en Intune. Para más información, vea [Adición de extensiones de kernel de macOS en Intune](~/configuration/kernel-extensions-overview-macos.md).

> [!IMPORTANT]
> La extensión de kernel solo se puede aprobar automáticamente si está presente en el dispositivo antes de que se instale la aplicación de ATP de Microsoft Defender. En caso contrario, los usuarios verán el mensaje "La extensión del sistema está bloqueada" en los equipos Mac y tendrán que aprobar la extensión si van a **Preferencias de seguridad** o **Preferencias del sistema** > **Seguridad y privacidad** y, después, seleccionan **Permitir**. Para obtener más información, vea [Solución de problemas de la extensión de kernel en ATP de Microsoft Defender para Mac](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/mac-support-kext).

## <a name="add-microsoft-defender-atp-to-intune"></a>Adición de ATP de Microsoft Defender a Intune
Puede agregar ATP de Microsoft Defender a Intune si sigue estos pasos:

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Aplicaciones** > **Todas las aplicaciones** > **Agregar**.
3. En la lista **Tipo de aplicación** en **ATP de Microsoft Defender**, seleccione **macOS**.

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

## <a name="select-scope-tags-optional"></a>Selección de Etiquetas de ámbito (opcional)
Puede usar las etiquetas de ámbito para determinar quién puede ver información de la aplicación cliente en Intune. Para más información sobre las etiquetas de ámbito, vea Uso del control de acceso basado en rol y de las etiquetas de ámbito para la TI distribuida.
1.  Seleccione **Ámbito (Etiquetas)** > **Agregar**.
2.  Use el cuadro **Seleccionar** para buscar las etiquetas de ámbito.
3.  Seleccione la casilla de verificación situada junto a las etiquetas de ámbito que desea asignar a esta aplicación.
4.  Haga clic en **Seleccionar** > **Aceptar**.

## <a name="add-the-app"></a>Agregar la aplicación
Cuando acabe de configurar, seleccione **Agregar** en el panel **Agregar aplicación**. 

La aplicación que ha creado aparece en la lista de aplicaciones, donde puede asignarla a los grupos que seleccione. 

> [!NOTE]
> Actualmente, Apple no proporciona ningún método para que Intune desinstale ATP de Microsoft Defender en dispositivos macOS.

## <a name="next-steps"></a>Pasos siguientes
- Para más información sobre cómo configurar ATP de Microsoft Defender en dispositivos macOS, vea [Configuración de ATP de Microsoft Defender en dispositivos macOS](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/mac-preferences).
- Para información sobre cómo incluir y excluir las asignaciones de aplicaciones para grupos de usuarios, consulte [Inclusión y exclusión de asignaciones de aplicaciones](~/apps/apps-inc-exl-assignments.md).
- [Asignar aplicaciones a grupos](~/apps/apps-deploy.md)

