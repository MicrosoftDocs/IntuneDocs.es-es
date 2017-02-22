---
title: "Establecimiento de la entidad de administración de dispositivos móviles | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: aprenda a configurar la entidad de administración de dispositivos móviles en Intune. "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: 3c0de501c172484f036aa2d812f0c40fcfa1d93f

---

# <a name="set-the-mobile-device-management-authority"></a>Establecer la entidad de administración de dispositivos móviles 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

La configuración de la entidad de administración de dispositivos móviles determina cómo se administran los dispositivos. Las configuraciones posibles son:

- **Intune independiente**: administración solo en la nube, que se configura mediante el portal de Azure. Incluye el conjunto completo de funcionalidades que ofrece Intune.

- **Intune híbrido**: integración de la solución de nube de Intune con System Center Configuration Manager. Intune se configura mediante la consola de Configuration Manager.

- **Administración de dispositivos móviles para Office 365**: integración de Office 365 con la solución de nube de Intune. Intune se configura desde el Centro de administración de Office 365. Incluye un subconjunto de las funcionalidades que están disponibles con la versión independiente de Intune.

>[!IMPORTANT]
>Una vez establecida la entidad de administración de dispositivos móviles, tendrá que ponerse en contacto con el [soporte técnico de Microsoft](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune) para cambiarla, así que tenga cuidado cuando haga su elección.

**Para establecer la entidad de administración de dispositivos móviles**

1. En el portal de Azure, elija **More Services** (Más servicios), escriba **Intune** en el cuadro de texto y luego seleccione **Other** (Otros)  > **Intune**.

2. En la hoja de Intune, elija **Inscribir dispositivos** y luego elija **Overview** (Información general).

3. En la hoja **Empezar a administrar dispositivos**, elija **Establecer Intune como entidad de MDM**. Un mensaje indica que ha configurado correctamente su entidad de MDM en Intune.



<!--HONumber=Feb17_HO1-->


