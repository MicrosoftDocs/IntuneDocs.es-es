---
title: 'Inicio rápido: Agregar y asignar una aplicación cliente'
titleSuffix: Microsoft Intune
description: En este tutorial de inicio rápido usará Microsoft Intune para agregar y asignar una aplicación cliente.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/25/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dab6f5c8-1ebb-42c4-a7a7-7af001f94e15
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1fa23deb26dbf54f8e3e98ec0b9604859a34a90d
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2019
ms.locfileid: "67528314"
---
# <a name="quickstart-add-and-assign-a-client-app"></a>Inicio rápido: Agregar y asignar una aplicación cliente

En este tutorial de inicio rápido va a usar Intune para agregar y asignar una aplicación cliente a los empleados de su empresa. Una de las prioridades de un administrador es garantizar que los usuarios finales tengan acceso a las aplicaciones que necesitan para hacer su trabajo. 

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](free-trial-sign-up.md).

## <a name="prerequisites"></a>Requisitos previos

- Para llevar a cabo este tutorial de inicio rápido, deberá [crear un usuario](quickstart-create-user.md), [crear un grupo](quickstart-create-group.md) e [inscribir un dispositivo](quickstart-setup-auto-enrollment.md).

## <a name="sign-in-to-intune"></a>Iniciar sesión en Intune

Inicie sesión en [Intune](https://aka.ms/intuneportal) como [administrador global o administrador de servicios de Intune](users-add.md#types-of-administrators). Si ha creado una suscripción de prueba de Intune, la cuenta con la que creó la suscripción es el administrador global.

## <a name="add-the-client-app-to-intune"></a>Agregar la aplicación cliente a Intune

Se puede incluir una aplicación para que Intune pueda administrar los distintos aspectos de la aplicación. 

Siga estos pasos para agregar una aplicación a Intune:

1. En [Intune](https://aka.ms/intuneportal), seleccione **Aplicaciones cliente** > **Aplicaciones** > **Agregar**. 
2. Seleccione **Windows 10** en la sección **Conjunto de aplicaciones Office 365** del cuadro desplegable **Tipo de aplicación**.
3. Seleccione **Configure conjunto de aplicaciones** para seleccionar las aplicaciones de Office que se van a asignar al usuario de Intune.
4. Haga clic en **Aceptar** para aceptar las aplicaciones seleccionadas de forma predeterminada.
5. Seleccione **Información del conjunto de aplicaciones**.
6. Escriba **Conjunto de aplicaciones de Microsoft Office 365** como **nombre del conjunto**.
7. Escriba **El conjunto de aplicaciones de Microsoft Office 365** como **Descripción del conjunto de aplicaciones**.
8. Haga clic en **Sí** junto a **Mostrar como aplicación destacada en el Portal de empresa**.
9. Haga clic en **Aceptar**.

    ![Captura de pantalla al agregar información de la aplicación](media/quickstart-add-assign-app/quickstart-add-assign-app-01.png)

8. Seleccione **Configuración del conjunto de aplicaciones**.
9. En el cuadro desplegable **Canal de actualización**, seleccione **Mensual**.
10. Haga clic en **Aceptar** > **Agregar**.

## <a name="assign-the-app-to-a-group"></a>Asignar la aplicación a un grupo

Después de agregar una aplicación a Microsoft Intune, puede asignarla a los grupos de usuarios o dispositivos.

> [!NOTE]
> Este tutorial de inicio rápido se basa en los tutoriales de inicio rápido anteriores de esta serie. Consulte los [requisitos previos](quickstart-add-assign-app.md#prerequisites) de este tutorial de inicio rápido para obtener información detallada.

Siga estos pasos para asignar una aplicación a un grupo:
1. En [Intune](https://aka.ms/intuneportal), seleccione **Aplicaciones cliente** > **Aplicaciones**. 
2. Seleccione la aplicación que quiere asignar a un grupo.
3. Haga clic en **Asignaciones** > **Agregar grupo** y se mostrará la hoja **Agregar grupo**.
4. Seleccione **Disponible para dispositivos inscritos** en el cuadro desplegable **Tipo de asignación**. 
5. Haga clic en **Grupos incluidos** > **Seleccionar grupos para incluir** > **Contoso Testers** (Evaluadores de Contoso).
6. Haga clic en **Seleccionar** > **Aceptar** > **Aceptar** > **Guardar** para asignar el grupo.

Ya ha asignado la aplicación al grupo **Contoso Testers** (Evaluadores de Contoso).

## <a name="install-the-app-on-the-enrolled-device"></a>Instalar la aplicación en el dispositivo inscrito

Debe instalar y usar la aplicación del Portal de empresa para instalar la aplicación **To-Do de Contoso** que facilita Intune. Siga estos pasos para comprobar que la aplicación está disponible para el usuario del dispositivo inscrito.

1. Inicie sesión en su dispositivo Windows 10 Escritorio inscrito.

    > [!IMPORTANT]
    > El dispositivo debe estar [inscrito en Intune](quickstart-enroll-windows-device.md). Además, debe iniciar sesión en el dispositivo con una cuenta incluida en el grupo que ha asignado a la aplicación.

2. En el menú **Inicio**, abra **Microsoft Store**. Luego, busque la aplicación **Portal de empresa** e instálela.
3. Inicie la aplicación **Portal de empresa**.
4. Haga clic en la aplicación que ha agregado mediante Intune. En este tutorial de inicio rápido ha agregado la aplicación **Conjunto de aplicaciones de Microsoft Office 365**.

    > [!NOTE]
    > Si no ha logrado asignar ninguna aplicación al usuario de Intune, verá el siguiente mensaje: *El administrador de TI no puso a su disposición ninguna aplicación*.

5. Haga clic en **Instalar**.

Pero si las necesidades empresariales exigen que debe asignar la aplicación Portal de empresa a sus empleados, puede asignar manualmente dicha aplicación para Windows 10 directamente desde Intune. Para obtener más información, consulte [Adición manual de la aplicación Portal de empresa para Windows 10 con Microsoft Intune](store-apps-company-portal-app.md).

## <a name="next-steps"></a>Pasos siguientes

En este tutorial de inicio rápido ha agregado aplicaciones a Intune, las ha asignado a un grupo y las ha instalado en el dispositivo Windows 10 Escritorio inscrito. Para obtener más información sobre cómo administrar aplicaciones en Intune, consulte [¿Qué es la administración de aplicaciones de Microsoft Intune?](app-management.md)

Para seguir esta serie de tutoriales de inicio rápido de Intune, pase al siguiente tutorial de inicio rápido.

> [!div class="nextstepaction"]
> [Inicio rápido: Crear y asignar una directiva de protección de aplicaciones](quickstart-create-assign-app-policy.md)
