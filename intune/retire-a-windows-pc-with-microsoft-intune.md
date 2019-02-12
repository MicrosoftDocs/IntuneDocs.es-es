---
title: Retirar un PC de Windows
titlesuffix: Microsoft Intune
description: Cómo retirar un PC de Windows administrado por Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5c916182-d99c-44c5-a779-3f596f261c40
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 24a3c53cb9aa26277ac7aef0ed643c9492e6e401
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55846526"
---
# <a name="retire-a-windows-pc"></a>Retirar un PC de Windows

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Use los siguientes pasos para retirar equipos de escritorio que está administrando como PC ejecutando el cliente de software de Intune en ellos. Cuando retira un PC, este se quita de la administración de Intune. No se puede borrar un PC desde Intune para establecerlo de nuevo en la configuración de fábrica original.

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Grupos** &gt; **Todos los dispositivos** (u otro grupo que contenga el PC que quiera retirar).

2.  Seleccione los dispositivos que quiera retirar y, después, elija **Retirar/Eliminar datos**.

Para volver a inscribir un PC en Intune, vuelva a instalar el cliente de software en el PC según lo que se indica en [Instalar el cliente de equipos Windows con Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Si un PC no se puede conectar a Intune, verá un mensaje en el área de trabajo **Panel**.

Cuando retira un PC:

-   Se quita del inventario y la administración de Intune, y la licencia asociada al PC queda disponible para poder volver a usarla. La opción de retirar o borrar quita el cliente de software de Intune, pero no elimina las aplicaciones o los datos del PC. Esta retirada no efectúa un borrado completo en el PC.

-   Su estado deja de aparecer en la consola de Intune.

-   Intune quita el cliente de software del PC. Si el PC no está conectado al servicio de Intune, el cliente de software se quitará la próxima vez que se conecte.

-   Microsoft Intune Endpoint Protection se quita del PC. Si el PC tiene instalada otra aplicación de puntos de conexión que está deshabilitada, esa aplicación se puede volver a habilitar después de quitar Microsoft Intune Endpoint Protection y, así, garantizar la protección del PC.

-   Se quitan las directivas del PC y se cambian los valores establecidos por la directiva.

-   El PC deja de recibir actualizaciones de software o de definiciones de malware procedentes del servicio de Intune.

-   Según como estén configurados, los PC que se retiraron pueden seguir recibiendo actualizaciones mediante Windows Server Update Services, Windows Update o Microsoft Update.

    > [!IMPORTANT]
    > Si el software cliente se instaló con un objeto de directiva de grupo (GPO), debe quitar dicho objeto para poder quitar el software cliente, a fin de evitar que el software se reinstale.

    Si el cliente de Endpoint Protection no se puede desinstalar, lea [Solucionar problemas de Endpoint Protection](/intune/troubleshoot-endpoint-protection-in-microsoft-intune) para obtener más ayuda.

### <a name="see-also"></a>Consulte también

[Tareas comunes de administración de equipos Windows con el cliente de software de Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
