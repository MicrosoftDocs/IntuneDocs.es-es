---
# required metadata

title: Clasificar dispositivos con la asignación de grupos de dispositivos en Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8b8c06a3-6b6c-4cf1-8646-b24fa9b1a39e

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Clasificar los dispositivos con la asignación de grupos de dispositivos en Microsoft Intune
Use la **asignación de grupos de dispositivos** de Microsoft Intune para agrupar dispositivos en las categorías que haya definido y que, de este modo, sea más fácil administrarlos. 

En la asignación de grupos de dispositivos se produce el siguiente flujo de trabajo:
1. Se crean grupos de dispositivos de Intune para cada categoría que quiera usar.
2. Se configuran reglas de asignación de grupos de dispositivos con las que se asigna la categoría que elija al grupo de dispositivos creado.
3. Cuando los usuarios finales inscriben sus dispositivos, deben elegir una categoría de entre las categorías configuradas. Tras elegirlas, sus dispositivos se agregarán automáticamente al grupo de dispositivos correspondientes.
4. A partir de aquí, esos grupos de dispositivos se pueden usar cuando se implementen directivas y aplicaciones.

Estos son algunos ejemplos de categorías:
* Personal
* Dispositivo de punto de venta
* Dispositivo de demostración
* Ventas
* Cuentas
* Manager

Pero puede configurar las categorías que quiera.

## Cómo configurar una asignación de grupos de dispositivos
1. Cree un grupo de dispositivos de Intune para cada categoría que quiera usar. Para obtener más información sobre cómo crear grupos, vea [Usar grupos para administrar usuarios y dispositivos en Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)..
2. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), haga clic en **Administración**..
3. En el área de trabajo **Administración**, expanda **Administración de dispositivos móviles**y haga clic en **Asignación de grupos de dispositivos**..
4. En la página **Asignación de grupos de dispositivos**, habilite la asignación de grupos de dispositivos.
5. Haga clic en **Agregar** para crear una regla de asignación.
6. En el cuadro de diálogo **Agregar regla de asignación de grupos de dispositivos**, escriba el nombre de la categoría que quiere crear y, luego, en la lista desplegable, elija la colección de dispositivos que quiera asignar a esta categoría. Haga clic en **Agregar** cuando haya acabado.
7. Cuando termine de agregar categorías y grupos, haga clic en **Guardar**..

Ahora, cuando los usuarios inscriban sus dispositivos, verán una lista de las categorías configuradas. Tras elegir una categoría y finalizar la inscripción, sus dispositivos se agregarán al grupo de dispositivos correspondiente a la categoría que eligieron.

### Consulte también
[Utilizar grupos para administrar usuarios y dispositivos en Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)

<!--HONumber=May16_HO1-->


