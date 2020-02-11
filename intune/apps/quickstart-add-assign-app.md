---
title: 'Inicio rápido: Agregar y asignar una aplicación cliente'
titleSuffix: Microsoft Intune
description: En este tutorial de inicio rápido usará Microsoft Intune para agregar y asignar una aplicación cliente.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dab6f5c8-1ebb-42c4-a7a7-7af001f94e15
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40337b3c45885dacf486173814044a27b7f3f6cc
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755075"
---
# <a name="quickstart-add-and-assign-a-client-app"></a>Inicio rápido: Agregar y asignar una aplicación cliente

En este tutorial de inicio rápido va a usar Intune para agregar y asignar una aplicación cliente a los empleados de su empresa. Una de las prioridades de un administrador es garantizar que los usuarios finales tengan acceso a las aplicaciones que necesitan para hacer su trabajo. 

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Requisitos previos

- Para llevar a cabo este tutorial de inicio rápido, deberá [crear un usuario](../fundamentals/quickstart-create-user.md), [crear un grupo](../fundamentals/quickstart-create-group.md) e [inscribir un dispositivo](../quickstart-setup-auto-enrollment.md).

## <a name="sign-in-to-intune"></a>Iniciar sesión en Intune

Inicie sesión en [Intune](https://aka.ms/intuneportal) como [administrador global o administrador de servicios de Intune](../fundamentals/users-add.md#types-of-administrators). Si ha creado una suscripción de prueba de Intune, la cuenta con la que creó la suscripción es el administrador global.

## <a name="add-the-client-app-to-intune"></a>Agregar la aplicación cliente a Intune

Se puede incluir una aplicación para que Intune pueda administrar los distintos aspectos de la aplicación. 

Siga estos pasos para agregar una aplicación a Intune:
1. En [Intune](https://aka.ms/intuneportal), seleccione **Aplicaciones** > **Todas las aplicaciones** > **Agregar**. 
2. Seleccione **Windows 10** en la sección **Conjunto de aplicaciones Office 365** del panel **Seleccionar tipo de aplicación**.
3. Haga clic en **Seleccionar**. Se muestran los pasos para **Agregar aplicación**.
4. Confirme los detalles predeterminados en la página **Información del conjunto de aplicaciones**.
5. Haga clic en **Siguiente** para mostrar la página **Configurar conjunto de aplicaciones**.
6. Junto a **Canal de actualización**, seleccione **Mensual** desde el cuadro desplegable.
7. Confirme el resto de los detalles predeterminados en la página ***Configurar conjunto de aplicaciones**.
8. Haga clic en **Siguiente** para mostrar la página **Etiquetas de ámbito**.
9. Si quiere, haga clic en **Seleccionar etiquetas de ámbito** para agregar etiquetas de ámbito para la aplicación. Para más información, consulte [Usar control de acceso basado en rol (RBAC) y etiquetas de ámbito para TI distribuida](~/fundamentals/scope-tags.md).
10. Haga clic en **Siguiente** para abrir la página **Asignaciones**.
11. Seleccione las asignaciones de grupo para la aplicación. Para más información, consulte [Agregar grupos para organizar usuarios y dispositivos](~/fundamentals/groups-add.md). 
12. Elija **Siguiente** para mostrar la página **Revisar y crear**. Revise los valores y la configuración que especificó para la aplicación.
13. Cuando haya terminado, haga clic en **Crear** para agregar la aplicación a Intune.

## <a name="assign-the-app-to-a-group"></a>Asignar la aplicación a un grupo

Después de agregar una aplicación a Microsoft Intune, puede asignarla a los grupos de usuarios o dispositivos.

> [!NOTE]
> Este tutorial de inicio rápido se basa en los tutoriales de inicio rápido anteriores de esta serie. Consulte los [requisitos previos](quickstart-add-assign-app.md#prerequisites) de este tutorial de inicio rápido para obtener información detallada.

Siga estos pasos para asignar una aplicación a un grupo:
1. En [Intune](https://aka.ms/intuneportal), seleccione **Aplicaciones** > **Todas las aplicaciones**. 
2. Seleccione la aplicación que quiere asignar a un grupo.
3. Haga clic en **Asignaciones** > **Agregar grupo** y se mostrará el panel **Agregar grupo**.
4. Seleccione **Disponible para dispositivos inscritos** en el cuadro desplegable **Tipo de asignación**. 
5. Haga clic en **Grupos incluidos** > **Seleccionar grupos para incluir** > **Contoso Testers** (Evaluadores de Contoso).
6. Haga clic en **Seleccionar** > **Aceptar** > **Aceptar** > **Guardar** para asignar el grupo.

Ya ha asignado la aplicación al grupo **Contoso Testers** (Evaluadores de Contoso).

## <a name="install-the-app-on-the-enrolled-device"></a>Instalar la aplicación en el dispositivo inscrito

Debe instalar y usar la aplicación del Portal de empresa para instalar la aplicación **To-Do de Contoso** que facilita Intune. Siga estos pasos para comprobar que la aplicación está disponible para el usuario del dispositivo inscrito.

1. Inicie sesión en su dispositivo Windows 10 Escritorio inscrito.

    > [!IMPORTANT]
    > El dispositivo debe estar [inscrito en Intune](../quickstart-enroll-windows-device.md). Además, debe iniciar sesión en el dispositivo con una cuenta incluida en el grupo que ha asignado a la aplicación.

2. En el menú **Inicio**, abra **Microsoft Store**. Luego, busque la aplicación **Portal de empresa** e instálela.
3. Inicie la aplicación **Portal de empresa**.
4. Haga clic en la aplicación que ha agregado mediante Intune. En este tutorial de inicio rápido ha agregado la aplicación **Conjunto de aplicaciones de Microsoft Office 365**.

    > [!NOTE]
    > Si no ha logrado asignar ninguna aplicación al usuario de Intune, verá el siguiente mensaje: *El administrador de TI no puso a su disposición ninguna aplicación*.

5. Haga clic en **Instalar**.

Pero si las necesidades empresariales exigen que debe asignar la aplicación Portal de empresa a sus empleados, puede asignar manualmente dicha aplicación para Windows 10 directamente desde Intune. Para obtener más información, consulte [Adición manual de la aplicación Portal de empresa para Windows 10 con Microsoft Intune](../company-portal-app.md).

## <a name="next-steps"></a>Pasos siguientes

En este tutorial de inicio rápido ha agregado aplicaciones a Intune, las ha asignado a un grupo y las ha instalado en el dispositivo Windows 10 Escritorio inscrito. Para obtener más información sobre cómo administrar aplicaciones en Intune, consulte [¿Qué es la administración de aplicaciones de Microsoft Intune?](app-management.md)

Para seguir esta serie de tutoriales de inicio rápido de Intune, pase al siguiente tutorial de inicio rápido.

> [!div class="nextstepaction"]
> [Inicio rápido: Crear y asignar una directiva de protección de aplicaciones](quickstart-create-assign-app-policy.md)
