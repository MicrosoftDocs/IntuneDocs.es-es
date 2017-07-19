---
title: "Introducción a los usuarios"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 22a232de-ab93-44ab-b0b5-d2b3ccb007fe
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fc1c4f6d18fd78f455be8e333bb765080184c908
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2017
---
# <a name="get-started-with-users"></a>Introducción a los usuarios

![Un usuario genérico en Azure](/intune/media/generic-intune-user.png)

Azure AD administra los grupos de objetos de la organización, como dispositivos y aplicaciones, y también grupos de usuarios. Puede agrupar usuarios o dispositivos conjuntamente en lugar de tener que administrar cada dispositivo de manera individual. Esto le permite asignar aplicaciones y opciones fácilmente a muchos usuarios y dispositivos.

## <a name="how-do-i-create-a-user"></a>¿Cómo se crea un usuario?

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Con **Buscar recursos**, busque **Usuarios y grupos**.
3. Una vez que haya abierto la hoja **Usuarios y grupos**, seleccione **Todos los usuarios**, después seleccione **+ Nuevo usuario**.
4. Escriba la información del usuario, como el **nombre** y el **nombre de usuario**. La parte del nombre de dominio del nombre de usuario debe ser el nombre de dominio predeterminado inicial "contoso.onmicrosoft.com" o un nombre de dominio no federado comprobado como "contoso.com".
5. En **Grupos**, elija el grupo de prueba al que agregar el usuario.
6. Guarde la contraseña de usuario que se ha generado automáticamente de manera que pueda usarla para iniciar sesión en un dispositivo de prueba. Debe proporcionar esta contraseña a los usuarios para que puedan cambiarla a una contraseña normal que puedan recordar.
7. En la hoja **Usuario**, seleccione **Crear**.

## <a name="assigning-licenses-to-users"></a>Asignar licencias a usuarios

Después de que haya creado un usuario, necesita usar el [Portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) para asignar una licencia de Intune a ese usuario. Sin asignarles una licencia, no pueden inscribir su dispositivo en la administración.

1. Inicie sesión en el [Portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) con las mismas credenciales que ha usado para iniciar sesión en Intune.
2. Seleccione **Usuarios** > **Usuarios activos**, después seleccione el usuario que ha creado anteriormente.
3. Puede que necesite esperar un momento a que se cargue toda la información del usuario. Una vez que se cargue, seleccione **Editar** para las **Licencias de productos** del usuario.
4. Asigne al usuario una **Ubicación** y, después, cambie Intune a **Activado**.

 > [!NOTE]
 > Esto usa una de las licencias de este usuario. Si está usando un entorno dinámico, puede desactivarlo usando esta licencia más tarde para volver a asignarla a un usuario real.

5. Seleccione **Guardar**.
