---
title: 'Restablecimiento de dispositivos Windows 10 con Microsoft Intune: Azure | Microsoft Docs'
description: Use Empezar de cero para quitar o desinstalar aplicaciones en equipos con Windows 10 con Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/09/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 294f06b078b06cfba9376ba6db0eb42cb884e141
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "73712323"
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Uso de Empezar de cero para restablecer dispositivos Windows 10 con Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

La acción de dispositivo **Comienzo de cero** quita las aplicaciones que están instaladas en un equipo que ejecuta Windows 10, versión 1703 o posterior. Comienzo de cero ayuda a eliminar las aplicaciones preinstaladas (OEM) que normalmente se instalan con un nuevo equipo. 

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) y seleccione **Dispositivos** > **Todos los dispositivos**.
2. En la lista de dispositivos que administra, elija un dispositivo de escritorio de Windows 10.
3. Haga clic en **Comienzo de cero**. 
4. Seleccione **Conservar los datos de usuario en este dispositivo** para:
   * Mantener el dispositivo unido a Azure AD
   * El dispositivo vuelve a estar inscrito en la administración de dispositivos móviles cuando un usuario habilitado de Azure Active Directory inicia sesión en el dispositivo.
   * Mantener el contenido de la carpeta Inicio del usuario del dispositivo y quitar las aplicaciones y la configuración

  > [!IMPORTANT]
 > Si no conserva los datos de usuario, el dispositivo se restaurará al estado completado de OOBE (configuración rápida) predeterminada que conserva la cuenta de administrador integrada.
 > Se quitará la inscripción de los dispositivos BYOD de Azure AD y la administración de dispositivos móviles.
 > Los dispositivos unidos a Azure AD volverán a estar inscritos en la administración de dispositivos móviles cuando un usuario habilitado de Azure Active Directory inicie sesión en el dispositivo.
 
5. Haga clic en **Aceptar**.   
6. Para ver el estado de esta acción, vuelva a **Dispositivos** y haga clic en **Acciones de dispositivo**.  
7. El dispositivo se restaurará en la pantalla de información de inicio de sesión inicial.
