---
title: "Establecer la entidad de administración de dispositivos móviles"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda a configurar la entidad de administración de dispositivos móviles en Intune. "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: c36ddef7e53d6f4f15c82c97dc6d18863e6859f1
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017

---

# <a name="set-the-mobile-device-management-authority"></a>Establecer la entidad de administración de dispositivos móviles

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

La configuración de la entidad de administración de dispositivos móviles (MDM) determina cómo se administran los dispositivos. Como administrador de TI, debe establecer una entidad de MDM antes de que los usuarios puedan inscribir dispositivos para la administración.

Las configuraciones posibles son:

- **Intune independiente**: administración solo en la nube, que se configura mediante el portal de Azure. Incluye el conjunto completo de funcionalidades que ofrece Intune. [Establecer la entidad de MDM en la consola de Intune](#mdm-authority-set-to-intune).

- **Intune híbrido**: integración de la solución de nube de Intune con System Center Configuration Manager. Intune se configura mediante la consola de Configuration Manager. [Establecer la entidad de MDM en Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription).

- **Administración de dispositivos móviles para Office 365**: integración de Office 365 con la solución de nube de Intune. Intune se configura desde el Centro de administración de Office 365. Incluye un subconjunto de las funcionalidades que están disponibles con la versión independiente de Intune. Establecer la entidad de MDM en el Centro de administración de Office 365.

>[!IMPORTANT]
>Una vez establecida la entidad de administración de dispositivos móviles, tendrá que ponerse en contacto con el [soporte técnico de Microsoft](https://docs.microsoft.com/intune-classic/troubleshoot/get-support) para cambiarla, así que tenga cuidado cuando haga su elección.

## <a name="set-mdm-authority-to-intune"></a>Establecimiento de la entidad de MDM en Intune

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.
  ![Captura de pantalla de la carga de trabajo de solución de problemas de Intune con el vínculo Seleccionar usuario](media/set-mdm-auth.png)
2. En la hoja de Intune, elija **Inscripción de dispositivos** y luego elija **Información general**.

3. En la hoja **Empezar a administrar dispositivos**, elija **Establecer Intune como entidad de MDM**. Un mensaje indica que ha configurado correctamente su entidad de MDM en Intune.

