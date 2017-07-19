---
title: "Establecer restricciones de inscripción en Intune"
titleSuffix: Intune on Azure
description: "Restrinja las inscripciones por plataforma y establezca un límite de inscripciones de dispositivos en Intune. \""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2dfcba8c788f262ce816dcd23dc2921fd57f331b
ms.sourcegitcommit: d1ad84edf4f03cb4c11fe55131556b43fc3a4500
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2017
---
# <a name="set-enrollment-restrictions"></a>Establecer restricciones de inscripción

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Como administrador de Intune, puede determinar qué dispositivos pueden inscribirse en la administración con Intune. Use el portal de Intune para establecer las siguientes restricciones para la inscripción de dispositivos:

- Número máximo de dispositivos inscritos
- Plataformas de dispositivo que se pueden inscribir:
  - Android
  - iOS
  - macOS
  - Windows
- Restringir los dispositivos de propiedad personal (solo iOS y Android)

>[!NOTE]
>Las restricciones de inscripción no son una característica de seguridad. Los dispositivos en peligro pueden falsificar su carácter. Estas restricciones son un obstáculo al mejor esfuerzo para los usuarios no malintencionados.

## <a name="set-device-type-restrictions"></a>Establecer restricciones de tipo de dispositivo
Las restricciones de inscripción predeterminadas se aplican a todos los usuarios a los que no se les han asignado restricciones de inscripción de mayor prioridad.  
1. En el portal de Intune, pulse **Inscripción de dispositivos** y **Restricciones de inscripción**.
![Captura de pantalla del área de trabajo de restricciones de dispositivos con las restricciones de tipo de dispositivo predeterminadas y las restricciones de límite de dispositivos.](media/device-restrictions-set-default.png)
2. En **Restricciones de inscripción** > **Restricciones de tipo de dispositivo**, seleccione **Predeterminado**.
3. En **Todos los usuarios**, seleccione **Plataformas**. Pulse **Permitir** o **Bloquear** para cada plataforma:
  - **Android**
  - **iOS**
  - **macOS**
  - **Windows**

  Haga clic en **Guardar**.
4. En **Todos los usuarios**, seleccione **Configuraciones de plataforma** y seleccione las configuraciones siguientes:
  - **Propiedad personal**: especifica si **Permitir** o **Bloquear** dispositivos Android e iOS.
  ![Captura de pantalla del área de trabajo de restricciones de dispositivos con las configuraciones de plataforma de dispositivos predeterminadas que muestran las opciones de propiedad personal configuradas.](media/device-restrictions-platform-configurations.png)
  Haga clic en **Guardar**.

>[!NOTE]
>Si bloquea los dispositivos Android de propiedad personal de la inscripción, los dispositivos Android for Work todavía pueden inscribirse.

## <a name="set-device-limit-restrictions"></a>Establecer restricciones de límite de dispositivos
Las restricciones de inscripción predeterminadas se aplican a todos los usuarios a los que no se les han asignado restricciones de inscripción de mayor prioridad.  
1. En el portal de Intune, pulse **Inscripción de dispositivos** y **Restricciones de inscripción**.
2. Pulse **Restricciones de inscripción** > **Restricciones de límite de dispositivos**.
3. En **Todos los usuarios**, seleccione **Límite de dispositivos**. Especifique el número máximo de dispositivos inscritos por usuario.  
![Captura de pantalla de la hoja de restricciones de límite de dispositivos con las restricciones de límite de dispositivos.](./media/device-restrictions-limit.png)

  Haga clic en **Guardar**.
