---
title: "Introducción a la administración de usuarios"
titlesuffix: Microsoft Intune
description: "Agregue un usuario a Intune y asígnele una licencia para que pueda acceder a recursos de la empresa en dispositivos móviles."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 22a232de-ab93-44ab-b0b5-d2b3ccb007fe
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4e06b335c03caee0bd997748f9c48ed78d7d379b
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2018
---
# <a name="get-started-managing-users"></a>Introducción a la administración de usuarios

Tenga en cuenta a todas las personas de su organización. Cada una de ellas que use los datos de la empresa necesitará disponer de un usuario para administrar el acceso a ellos en Intune.

## <a name="how-do-i-create-a-user"></a>¿Cómo se crea un usuario?

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Con **Buscar recursos**, busque **Intune**.
3. Después de abrir la hoja **Microsoft Intune**, seleccione **Usuarios**. En la página **Todos los usuarios**, seleccione **+ Usuario nuevo**.
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

## <a name="next-steps"></a>Pasos siguientes

[Introducción a los grupos](get-started-groups.md): organice a los usuarios en grupos para administrar las directivas y las aplicaciones a las que pueden acceder con más facilidad.
