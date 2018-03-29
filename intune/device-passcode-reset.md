---
title: 'Restablecimiento de códigos de acceso de dispositivos con Microsoft Intune: Azure | Microsoft Docs'
description: Quite o restablezca el código de acceso con la acción Quitar código de acceso en dispositivos que administre o supervise con Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4cca5922f036711093469e71489e267af53f05a9
ms.sourcegitcommit: e6319ff186d969da34bd19c9730ba003d6cce353
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2018
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Restablecimiento o eliminación del código de acceso de un dispositivo en Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Para crear un código de acceso para un dispositivo, use la acción **Quitar código de acceso**.

## <a name="supported-platforms"></a>Plataformas compatibles

- Windows Phone 8.1 (no combinado con Azure Active Directory), incluidas las versiones hasta Windows 10 Creators Update
- Windows 10 Creators Update y versiones posteriores
- iOS
- Versiones de Android anteriores a Android 7

Esta característica no se admite en los siguientes sistemas:

- Windows
- macOS
- Android for Work

## <a name="reset-a-passcode"></a>Restablecer un código de acceso

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Dispositivos** y, después, **Todos los dispositivos**.
4. En la lista de dispositivos que administra, seleccione un dispositivo y seleccione **...Más**. Luego, elija la acción remota de dispositivo **Quitar código de acceso**.

## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de la acción que acaba de realizar, en **Dispositivos**, elija **Acciones de dispositivo**.
