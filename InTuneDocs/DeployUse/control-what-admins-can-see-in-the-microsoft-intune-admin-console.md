---
title: "Personalizar vistas de consola para roles de administración | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e0783eaa-67dc-410e-9e80-4d3aa72f36d8
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: 52a77e50b3dde24ba270766d4472bdd6176cc415


---

# Personalizar vistas de consola de Intune según los roles de administración
La vista de la consola de administración de Microsoft Intune se puede filtrar de forma que los administradores solo puedan ver los elementos que necesiten de acuerdo con su rol. Así, por ejemplo, puede permitir que solo los operadores de la consola de administración actualicen definiciones de malware o restablezcan la contraseña en los dispositivos. Para ello, se usan **designaciones** preestablecidas que se asignan a usuarios específicos. Cuando estos usuarios acceden a la consola de administración, solo ven los elementos específicos de su designación.

## Cómo crear una vista personalizada

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Administración**&gt;**Administradores de servicios**.

2.  En la lista de administradores de servicios, seleccione el usuario cuya designación quiera cambiar y, después, seleccione **Administrar acceso**.

3.  En el cuadro de diálogo **Administrar acceso** , seleccione el nivel de acceso que desea asignar al usuario seleccionado. Puede elegir entre:

    -   **Acceso completo**
    -   **Acceso solo de lectura**
    -   **Departamento de soporte técnico: nodo Grupos**

    El acceso total y el acceso de solo lectura no necesitan explicación. <!--- **Helpdesk - Groups Node** allows users to choose from one of the following designations that provide custom levels of access to the [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] admin console:--->

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

        -   Bloquear de forma remota un dispositivo

        -   Restablecimiento de la contraseña

Cuando el administrador configurado abra la consola de administración de Intune, se le dará el nivel de acceso que se haya especificado.



<!--HONumber=Jun16_HO4-->


