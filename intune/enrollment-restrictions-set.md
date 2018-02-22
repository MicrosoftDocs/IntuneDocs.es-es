---
title: "Establecer restricciones de inscripción en Intune"
titlesuffix: Azure portal
description: "Restrinja las inscripciones por plataforma y establezca un límite de inscripciones de dispositivos en Intune. \""
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/30/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fab385762efa3ab095553fe21fb045f4f11ff197
ms.sourcegitcommit: 93622d740cbd12043eedc25a9699cc4256e23e7e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2018
---
# <a name="set-enrollment-restrictions"></a>Establecer restricciones de inscripción

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Como administrador de Intune, puede crear y administrar las restricciones de inscripción que definen el número y los tipos de dispositivos que se pueden inscribir en la administración con Intune. Puede crear varias restricciones y aplicarlas a diferentes grupos de usuarios. Puede establecer el [orden de prioridad](#change-enrollment-restriction-priority) para las distintas restricciones.

>[!NOTE]
>Las restricciones de inscripción no son características de seguridad. Los dispositivos en peligro pueden falsificar su carácter. Estas restricciones son un obstáculo al mejor esfuerzo para los usuarios no malintencionados.

>[!NOTE]
>La funcionalidad de prioridad y la restricción de inscripción asignada a grupos que se mencionan a continuación se están implementando en la base de clientes de Intune. Es posible que no tenga acceso a dichas características hasta que la implementación se haya completado.

Las restricciones de inscripción específicas que se pueden crear son:

- Número máximo de dispositivos inscritos
- Plataformas de dispositivo que se pueden inscribir:
  - Android
  - Android for Work
  - iOS
  - macOS
  - Windows
- Versión del sistema operativo de plataforma para iOS, Android, Android for Work y Windows (solo se pueden usar versiones de Windows 10, dejar en blanco si se permite Windows 8.1)
  - Versión mínima
  - Versión máxima
- Restricción de los dispositivos de propiedad personal (solo iOS, Android, Android for Work y macOS)

## <a name="default-restrictions"></a>Restricciones predeterminadas

Las restricciones predeterminadas se proporcionan automáticamente para las restricciones de inscripción de tipo de dispositivo y límite de dispositivo. Puede cambiar las opciones para los valores predeterminados. Las restricciones predeterminadas se aplican a todos los usuarios e inscripciones sin usuario. Puede invalidar estos valores predeterminados mediante la creación de nuevas restricciones con prioridades más altas.

## <a name="create-a-restriction"></a>Crear una restricción

1. Inicie sesión en el portal de Azure.
2. Elija **Más servicios**, busque **Intune** y, después, seleccione **Intune**.
3. Seleccione **Inscripción de dispositivos** > **Restricciones de inscripción**.
4. Haga clic en **Crear restricción**.
5. Asigne un nombre y una descripción a la restricción.
6. Elija un **Tipo de restricción** y, después, haga clic en **Crear**.
7. Para las restricciones de límite de dispositivo, haga clic en **Límite de dispositivos** para establecer el número máximo de dispositivos que un usuario puede inscribir.
8. Para las restricciones de tipo de dispositivo, haga clic en **Plataformas** y **Configuraciones de plataforma** para permitir o bloquear varias versiones y plataformas.
9. Haga clic en **Asignaciones** > **+ Seleccionar grupos**.
10. En **Seleccionar grupos**, seleccione uno o más grupos y, después, haga clic en **Seleccionar**. La restricción se aplica únicamente a los grupos a los que está asignada. Si no asigna una restricción al menos a un grupo, no tendrá ningún efecto.
11. Haga clic en **Guardar**.
12. La nueva restricción se crea con una prioridad justo por encima del valor predeterminado. También puede [cambiar la prioridad](#change-enrollment-restriction-priority).

## <a name="set-device-type-restrictions"></a>Establecer restricciones de tipo de dispositivo

Puede cambiar la configuración de una restricción de tipo de dispositivo mediante estos pasos:

1. Inicie sesión en el portal de Azure.
2. Elija **Más servicios**, busque **Intune** y, después, seleccione **Intune**.
3. Seleccione **Inscripción de dispositivos** > **Restricciones de inscripción**.
4. En **Restricciones de tipo de dispositivo**, elija la restricción que quiera establecer.
5. Bajo el nombre de la restricción (**Todos los usuarios** para la restricción predeterminada), seleccione **Plataformas**. Pulse **Permitir** o **Bloquear** para cada plataforma de la lista.
6. Haga clic en **Guardar**.
7. Bajo el nombre de la restricción (**Todos los usuarios** para la restricción predeterminada), haga clic en **Configuraciones de plataforma** y seleccione las **Versiones** mínima y máxima para las plataformas de la lista. Entre las versiones admitidas se incluyen:
  - Android y Android for Work admiten major.minor.rev.build.
  - iOS admite major.minor.rev.
  - Windows admite major.minor.rev.build únicamente para Windows 10.
  Las versiones de sistema operativo no son relevantes en dispositivos Apple que se hayan inscrito con el Programa de inscripción de dispositivos, Apple School Manager o la aplicación Apple Configurator.
8. Especifique si quiere **Permitir** o **Bloquear** dispositivos de **propiedad personal** para las plataformas de la lista.

    ![Captura de pantalla del área de trabajo de restricciones de dispositivos con las configuraciones de plataforma de dispositivos predeterminadas en la que se muestran las opciones de propiedad personal configuradas.](media/device-restrictions-platform-configurations.png)
9. Haga clic en **Guardar**.

>[!NOTE]
>- Si bloquea los dispositivos Android de propiedad personal de la inscripción, los dispositivos Android for Work de propiedad personal todavía pueden inscribirse.
>- De forma predeterminada, la configuración de los dispositivos Android for Work será igual que la configuración de los dispositivos Android. Sin embargo, dejará de ser así tras modificar la configuración de Android for Work.
>- Si bloquea la inscripción de Android for Work personal, tan solo los dispositivos Android corporativos podrán inscribirse como Android for Work.

## <a name="set-device-limit-restrictions"></a>Establecer restricciones de límite de dispositivos

Para cambiar la configuración de una restricción de límite de dispositivos, siga estos pasos:

1. Inicie sesión en el portal de Azure.
2. Elija **Más servicios**, busque **Intune** y, después, seleccione **Intune**.
3. Seleccione **Inscripción de dispositivos** > **Restricciones de inscripción**.
4. En **Restricciones de límite de dispositivo**, elija la restricción que quiera establecer.
5. Haga clic en **Límite de dispositivos** y después, en la lista desplegable, seleccione el número máximo de dispositivos que puede inscribir un usuario.
    ![Captura de pantalla de la hoja de restricciones de límite de dispositivos con las restricciones de límite de dispositivos.](./media/device-restrictions-limit.png)
6. Haga clic en **Guardar**.

Cuando el usuario final alcance el límite de dispositivos inscritos, recibirá una notificación en que se le informará de ello. Por ejemplo, en iOS, tendría una aspecto similar al siguiente:

![Captura de pantalla de la notificación de límite en un dispositivo iOS](./media/enrollment-restrictions-ios-set-limit-notification.png)

## <a name="change-enrollment-restriction-priority"></a>Cambiar la prioridad de las restricciones de inscripción

La prioridad se usa cuando un usuario existe en varios grupos a los que se asignan restricciones. Los usuarios solo están sujetos a la restricción de prioridad más alta asignada a un grupo al que pertenecen. Por ejemplo, Juan está en el grupo A asignado a restricciones de prioridad 5 y en el grupo B asignado a restricciones de prioridad 2. Juan solo está sujeto a las restricciones de prioridad 2.

Cuando se crea una restricción, se agrega a la lista justo encima de la predeterminada.

La inscripción de dispositivos incluye restricciones predeterminadas para el tipo y límite de dispositivo. Estas dos restricciones se aplican a todos los usuarios a menos que se reemplacen por restricciones de prioridad más alta.

Puede cambiar la prioridad de cualquier restricción que no sea la predeterminada.

**Para cambiar la prioridad de las restricciones**

1. Inicie sesión en el portal de Azure.
2. Elija **Más servicios**, busque **Intune** y, después, seleccione **Intune**.
3. Seleccione **Inscripción de dispositivos** > **Restricciones de inscripción**.
4. Mantenga el puntero sobre la restricción en la lista de prioridades.
5. Con los tres puntos verticales, arrastre la prioridad a la posición deseada en la lista.
