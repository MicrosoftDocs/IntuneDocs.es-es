---
title: Borrado solo de datos corporativos de aplicaciones
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo borrar selectivamente solo los datos corporativos de aplicaciones administradas de Intune con Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 42605e6e-5b84-44ff-b86e-346ea123b53e
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c0ca82b434b83937c7962b2676ce3c2a12c1424
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74564016"
---
# <a name="how-to-wipe-only-corporate-data-from-intune-managed-apps"></a>Borrado solo de datos corporativos de aplicaciones administradas por Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Cuando un dispositivo se pierde o lo roban, o cuando un empleado deja la empresa, le interesa asegurarse de que se eliminan del dispositivo los datos de la aplicación de empresa. Pero es posible que no quiera quitar del dispositivo los datos personales, sobre todo si se trata de un dispositivo propiedad de un empleado.

>[!NOTE]
> Actualmente, solo se admiten las plataformas iOS, Android y Windows 10 para borrar datos corporativos de aplicaciones administradas de Intune. Las aplicaciones administradas de Intune incluyen Intune APP SDK y tienen una cuenta de usuario con licencia para su organización. No es necesaria la implementación de directivas de protección de aplicaciones para habilitar el borrado selectivo de aplicaciones.

Para quitar de forma selectiva datos de la aplicación de empresa, siga los pasos de este tema para crear una solicitud de borrado. Una vez finalizada la solicitud, la próxima vez que la aplicación se ejecute en el dispositivo, los datos de la empresa se quitarán de la aplicación. Además de crear una solicitud de borrado, puede configurar un borrado selectivo de los datos de la organización como una nueva acción cuando no se cumplan las condiciones de Configuración de acceso de las Directivas de protección de aplicaciones (APP). Mediante esta característica, podrá proteger y eliminar automáticamente datos confidenciales de la organización en las aplicaciones, en función de criterios configurados previamente.

>[!IMPORTANT]
> Se quitan los contactos sincronizados directamente desde la aplicación en la libreta de direcciones nativa. No se pueden borrar los contactos sincronizados desde la libreta de direcciones nativa en otro origen externo. Actualmente, esto solo se aplica a la aplicación Microsoft Outlook.

## <a name="deployed-wip-policies-without-user-enrollment"></a>Directivas de WIP implementadas sin la inscripción del usuario
Las directivas de Windows Information Protection (WIP) se pueden implementar sin requerir que los usuarios de MDM inscriban sus dispositivos Windows 10. Esta configuración permite a las empresas proteger sus documentos corporativos en función de la configuración de WIP, mientras que permite a los usuarios mantener la administración de sus propios dispositivos Windows. Una vez que los documentos están protegidos con una directiva de WIP, un administrador de Intune puede borrar de forma selectiva los datos protegidos. Mediante la selección del usuario y dispositivo, y el envío de una solicitud de borrado, todos los datos protegidos mediante la directiva de WIP quedarán inservibles. En Intune en Azure Portal, seleccione **Aplicación cliente** > **Borrado selectivo de aplicaciones**. Para obtener más información, consulte [Creación e implementación de una directiva de protección de aplicaciones de Windows Information Protection (WIP) con Intune](windows-information-protection-policy-create.md).

## <a name="create-a-wipe-request"></a>Crear una solicitud de borrado

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Aplicaciones** > **Borrado selectivo de aplicaciones** > **Crear solicitud de borrado**.<br>
   Se muestra el panel **Crear solicitud de borrado**.
3. Haga clic en **Seleccionar usuario**, elija el usuario cuyos datos de aplicación quiere borrar y haga clic en **Seleccionar** en la parte inferior del panel **Seleccionar usuario**.

    ![Captura de pantalla del panel "Seleccionar usuario"](./media/apps-selective-wipe/apps-selective-wipe-01.png)

4. Haga clic en **Seleccione el dispositivo**, elija el dispositivo y haga clic en **Seleccionar** en la parte inferior del panel **Seleccionar dispositivo**.

    ![Captura de pantalla del panel "Crear solicitud de borrado" donde se selecciona el dispositivo](./media/apps-selective-wipe/apps-selective-wipe-02.png)

5. Haga clic en **Crear** para realizar una solicitud de borrado.

El servicio crea y realiza el seguimiento de una solicitud de borrado independiente para cada aplicación protegida en el dispositivo, y del usuario asociado a la solicitud de borrado.

   ![Captura de pantalla del panel "Aplicaciones cliente - Borrado selectivo de aplicaciones"](./media/apps-selective-wipe/apps-selective-wipe-03.png)

## <a name="monitor-your-wipe-requests"></a>Supervisar las solicitudes de borrado de datos

Puede tener un informe resumido que muestre el estado general de la solicitud de borrado y que incluya el número de solicitudes pendientes y errores. Para obtener más información, siga estos pasos:

1. En el panel **Aplicaciones** > **Borrado selectivo de aplicaciones**, puede ver la lista de solicitudes agrupadas por usuarios. Debido a que el sistema crea una solicitud de borrado para cada aplicación protegida que se ejecuta en el dispositivo, puede que vea varias solicitudes para un mismo usuario. Este estado indica si una solicitud de borrado está **pendiente**, ha provocado un **error** o si es **correcta**.

    ![Captura de pantalla del estado de la solicitud de borrado en el panel Borrado selectivo de aplicaciones](./media/apps-selective-wipe/wipe-request-status-1.png)

Además, podrá ver el nombre del dispositivo y su tipo, lo que puede resultar útil al leer los informes.

>[!IMPORTANT]
> El usuario debe abrir la aplicación de la que se vaya a realizar el borrado, que puede tardar hasta 30 minutos después de efectuar la solicitud.

## <a name="delete-a-wipe-request"></a>Eliminación de una solicitud de borrado

Los borrados con estado pendiente se muestran hasta que se eliminen manualmente. Para eliminar manualmente una solicitud de borrado:

1. En el panel **Aplicaciones cliente - Borrado selectivo de aplicaciones**.

2. En la lista, haga clic con el botón derecho en la solicitud de borrado que quiere eliminar y elija **Eliminar solicitud de borrado**.

    ![Captura de pantalla de la lista de solicitudes de borrado en el panel Borrado selectivo de aplicaciones](./media/apps-selective-wipe/delete-wipe-request.png)

3. Se le pedirá que confirme la eliminación. Elija **Sí** o **No** y luego haga clic en **Aceptar**.

## <a name="see-also"></a>Consulte también
[What's app protection policy](app-protection-policy.md) (¿Qué es la directiva de protección de aplicaciones?)

[¿Qué es la administración de aplicaciones?](app-management.md)
