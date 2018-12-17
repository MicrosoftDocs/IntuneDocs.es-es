---
title: Actualizar a Windows Holographic for Business
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo actualizar dispositivos que ejecuten Windows Holographic a Windows Holographic for Business
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 4839206db5e34a039c9e99dd74f5ab1bad328418
ms.sourcegitcommit: 5058dbfb0e224207dd4e7ca49712c6ad3434c83c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112347"
---
# <a name="upgrade-devices-running-windows-holographic-to-windows-holographic-for-business"></a>Actualización de dispositivos que ejecutan Windows Holographic a Windows Holographic for Business


Para administrar los dispositivos que ejecutan Windows Holographic con Microsoft Intune, debe actualizar los dispositivos de Windows Holographic a Windows Holographic for Business. Puede crear un perfil Actualización de edición para realizar la actualización. Para Microsoft HoloLens, puede adquirir Commercial Suite para obtener la licencia necesaria para la actualización. Para obtener más información, consulte [Desbloquear las funcionalidades de Windows Holographic for Business](https://docs.microsoft.com/hololens/hololens-upgrade-enterprise).

## <a name="to-set-up-an-edition-upgrade-device-configuration-profile"></a>Configuración de un perfil de configuración de dispositivos de actualización de edición

1. Inicie sesión en [Azure Portal](https://portal.azure.com) con su cuenta de administrador.


2.  Haga clic en **configuración del dispositivo**, **Perfiles**y después haga clic en **+ Crear perfil**.

    ![Crear perfil](media/Holographic-create-profile.png)

3.  En la página **Crear perfil**, escriba un nombre para el perfil, seleccione **Windows 10 y versiones posteriores** como plataforma y **Actualización de edición** como tipo de perfil. Haga clic en **Configuración**.

5. En la página **Actualización de edición**, en **Edición a la que actualizar**, seleccione **Windows 10 Holographic for Business**. En **Archivo de licencia**, busque y seleccione el archivo de licencia XML que se le proporcionó.

    ![Escriba el nombre de archivo XML](media/Holographic-edition-upgrade.png)
 
5.  Haga clic en **Aceptar** y después en **Crear** para crear el perfil.


## <a name="deploy-the-edition-upgrade-policy"></a>Implementación de la directiva de actualización de edición

A continuación, asigne el perfil de actualización de edición a dispositivos o grupos seleccionados.

1. En el perfil que creó en los pasos anteriores, haga clic en **Asignaciones**.

2. En la página **Asignaciones**, seleccione los grupos de usuarios y dispositivos que quiera incluir y excluir de la directiva.

![Incluir y excluir grupos](media/Holographic-groups.PNG)

Cuando estos usuarios o dispositivos se inscriben en Intune, se aplica el perfil de actualización de edición. 

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre los grupos, consulte [Introducción a los grupos](get-started-groups.md).


