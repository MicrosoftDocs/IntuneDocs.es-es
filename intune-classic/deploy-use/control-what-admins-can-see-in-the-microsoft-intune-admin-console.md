---
title: Personalización de las vistas de consola para roles de administrador
description: Use este tema para ayudarle a filtrar la vista de la consola de administración de Intune para que los administradores solo puedan ver los elementos que necesiten de acuerdo con su rol.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e0783eaa-67dc-410e-9e80-4d3aa72f36d8
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9baa0325a90e152ffd6cf6a31cdd0a458588758a
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="customize-intune-console-views-according-to-admin-roles"></a>Personalizar vistas de consola de Intune según los roles de administración

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

La vista de la consola de administración de Microsoft Intune se puede filtrar de forma que los administradores solo puedan ver los elementos que necesiten de acuerdo con su rol. Así, por ejemplo, puede permitir que solo los operadores de la consola de administración actualicen definiciones de malware o restablezcan la contraseña en los dispositivos. Para ello, se usan **designaciones** preestablecidas que se asignan a usuarios específicos. Cuando estos usuarios obtienen acceso a la consola de administración, solo ven los elementos específicos de su designación.

## <a name="to-create-a-custom-view"></a>Para crear una vista personalizada

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Administración**&gt;**Administradores de servicios**.

2.  En la lista de administradores de servicios, seleccione el usuario cuya designación quiera cambiar y, después, seleccione **Administrar acceso**.

3.  En el cuadro de diálogo **Administrar acceso** , seleccione el nivel de acceso que desea asignar al usuario seleccionado. Puede elegir entre:

    -   **Acceso completo**
    -   **Acceso de solo lectura**
    -   **Departamento de soporte técnico: nodo Grupos**

    El acceso total y el acceso de solo lectura no necesitan explicación. <!--- **Helpdesk - Groups Node** allows users to choose from one of the following designations that provide custom levels of access to the Intune admin console:--->

    En cuanto a **Departamento de soporte técnico: nodo Grupos**, limita lo que el administrador puede ver y hacer a lo siguiente:

    -   Ver listas de usuarios y dispositivos. El administrador no puede usar filtros para modificar la vista. Pero se puede usar el filtrado de grupo para modificar lo que el administrador puede ver. Para obtener más información, vea [Usar grupos para administrar usuarios y dispositivos en Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).

    -   Imprimir la lista de usuarios y dispositivos

    -   Exporte la lista de usuarios y dispositivos.

    -   Ver las propiedades de un usuario o de un dispositivo

    -   Realice las siguientes tareas remotas:

        -   Ejecutar un examen completo de malware

        -   Ejecutar un examen rápido de malware

        -   Reiniciar un equipo

        -   Actualizar definiciones de malware

        -   Actualizar directivas

        -   Actualizar el inventario

        -   Bloquear un dispositivo de forma remota

        -   Restablecer un código de acceso

Cuando el administrador configurado abra la consola de administración de Intune, se le dará el nivel de acceso que se haya especificado.
