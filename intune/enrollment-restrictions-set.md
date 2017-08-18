---
title: "Establecer restricciones de inscripción en Intune"
titleSuffix: Intune on Azure
description: "Restrinja las inscripciones por plataforma y establezca un límite de inscripciones de dispositivos en Intune. \""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 47dc35e5b50670027a85f395f674345b934d377b
ms.sourcegitcommit: 7674efb7de5ad54390801165364f5d9c58ccaf84
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2017
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
- Versión de sistema operativo de la plataforma (solo iOS y Android)
  - Versión mínima
  - Versión máxima
- Restricción de los dispositivos de propiedad personal (solo iOS, Android y macOS)

>[!NOTE]
>Las restricciones de inscripción no son características de seguridad. Los dispositivos en peligro pueden falsificar su carácter. Estas restricciones son un obstáculo al mejor esfuerzo para los usuarios no malintencionados.

## <a name="set-device-type-restrictions"></a>Establecer restricciones de tipo de dispositivo
Las restricciones de inscripción predeterminadas se aplican a todos los usuarios y a las inscripciones sin usuario.
1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. Seleccione **Inscripción de dispositivos** > **Restricciones de inscripción**.
4. En **Restricciones de inscripción** > **Restricciones de tipo de dispositivo**, seleccione **Predeterminado**.
5. En **Todos los usuarios**, seleccione **Plataformas**. Pulse **Permitir** o **Bloquear** para cada plataforma:
  - **Android**
  - **iOS**
  - **macOS**
  - **Windows**

  Haga clic en **Guardar**.
6. En **Todos los usuarios**, seleccione **Configuraciones de plataforma** y elija las configuraciones siguientes. Para cada plataforma permitida, puede configurar las opciones siguientes:
  - **Versiones**: especifique las versiones **Mín.** y **Máx.** del sistema operativo de la plataforma para dispositivos iOS y Android. Las versiones de sistema operativo no son aplicables a los dispositivos que se inscriben con el Programa de inscripción de dispositivos, Apple School Manager o la aplicación Apple Configurator.
  - **Propiedad personal**: especifica si **Permitir** o **Bloquear** dispositivos Android, iOS y macOS.
  ![Captura de pantalla del área de trabajo de restricciones de dispositivos con las configuraciones de plataforma de dispositivos predeterminadas que muestran las opciones de propiedad personal configuradas.](media/device-restrictions-platform-configurations.png)
  Haga clic en **Guardar**.

>[!NOTE]
>Si bloquea los dispositivos Android de propiedad personal de la inscripción, los dispositivos Android for Work de propiedad personal todavía pueden inscribirse.

## <a name="set-device-limit-restrictions"></a>Establecer restricciones de límite de dispositivos
Las restricciones de inscripción predeterminadas se aplican a todos los usuarios.
1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. Seleccione **Inscripción de dispositivos** > **Restricciones de inscripción**.
4. En el portal de Intune, pulse **Inscripción de dispositivos** y **Restricciones de inscripción**.
5. Pulse **Restricciones de inscripción** > **Restricciones de límite de dispositivos**.
6. En **Todos los usuarios**, seleccione **Límite de dispositivos**. Especifique el número máximo de dispositivos inscritos por usuario.  
![Captura de pantalla de la hoja de restricciones de límite de dispositivos con las restricciones de límite de dispositivos.](./media/device-restrictions-limit.png)

  Haga clic en **Guardar**.
