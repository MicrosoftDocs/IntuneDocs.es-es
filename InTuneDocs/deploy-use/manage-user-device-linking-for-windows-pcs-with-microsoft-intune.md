---
title: "Administrar la vinculación de dispositivos de usuario en PC de Windows | Microsoft Intune"
description: "Cómo vincular un usuario a un PC de Windows administrado por Intune."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 53c99d63-c312-442a-8a71-de1b10fcd39b
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 39fec6a2ea8d8c0f4b6ea1460c76a8a6c652d614


---

# <a name="manage-user-device-linking-for-windows-pcs"></a>Administrar la vinculación de dispositivos de usuario en PC de Windows
Antes de implementar software en un usuario, debe vincular el usuario a un equipo. Puede vincular un usuario a varios equipos, pero cada equipo puede vincularse sólo a un usuario. Los usuarios se vinculan automáticamente a los equipos que tengan inscritos en Intune a través del portal de la empresa.

Para vincular un usuario a un equipo:

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Grupos** &gt; **Todos los dispositivos** (u otro grupo que contenga el equipo que quiera vincular a un usuario).

2.  Seleccione el equipo que quiera vincular a un usuario y, después, elija **Vincular usuario**.

    El cuadro de diálogo **Vincular usuario** muestra una lista de usuarios disponibles con su nombre para mostrar, Id. de usuario, y el número de equipos a los que cada usuario que está vinculado. Si un usuario ya está vinculado al equipo seleccionado, el nombre del usuario y su Id. se muestran en **Usuario actual**. Si el equipo no está vinculado a ningún usuario, aparece **Ningún usuario** bajo el **Usuario actual**.

3.  Realice una de las siguientes acciones:

    -   Para dejar el equipo vinculado a su usuario actual (si lo hay), seleccione **Cancelar**.

    -   Para quitar el vínculo al usuario actual (si lo hay), seleccione **Quitar vínculo** &gt; **Aceptar**.

    -   Para vincular el equipo a un usuario nuevo, en la lista **Todos los usuarios** , seleccione un usuario. Confirme que los datos de usuario son correctos y, luego, seleccione **Aceptar**.

> [!TIP]
> Si desea restringir la capacidad de los usuarios finales para vincularse a equipos, habilite la opción **Restringir la capacidad de los usuarios de vincularse a equipos** en la directiva de **Configuración de agente de Microsoft Intune**.

### <a name="see-also"></a>Consulte también

[Tareas comunes de administración de equipos Windows con el cliente de software de Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)


<!--HONumber=Nov16_HO4-->


