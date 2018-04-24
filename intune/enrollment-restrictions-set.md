---
title: Establecer restricciones de inscripción en Microsoft Intune
titlesuffix: ''
description: Restrinja las inscripciones por plataforma y establezca un límite de inscripciones de dispositivos en Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9b17cb50ead094962196bb030c3a18e4119c6904
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="set-enrollment-restrictions"></a>Establecer restricciones de inscripción

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Como administrador de Intune, puede crear y administrar las restricciones de inscripción que definen el número y los tipos de dispositivos que se pueden inscribir en la administración con Intune. Puede crear varias restricciones y aplicarlas a diferentes grupos de usuarios. Puede establecer el [orden de prioridad](#change-enrollment-restriction-priority) para las distintas restricciones.

>[!NOTE]
>Las restricciones de inscripción no son características de seguridad. Los dispositivos en peligro pueden falsificar su carácter. Estas restricciones son un obstáculo al mejor esfuerzo para los usuarios no malintencionados.

>[!NOTE]
>La funcionalidad de prioridad y la restricción de inscripción asignada a grupos que se mencionan en este artículo se están implementando en la base de clientes de Intune. Es posible que no tenga acceso a dichas características hasta que la implementación se haya completado.

Las restricciones de inscripción específicas que se pueden crear son:

- Número máximo de dispositivos inscritos.
- Plataformas de dispositivo que se pueden inscribir:
  - Android.
  - Android for Work.
  - iOS.
  - macOS.
  - Windows.
- Versión del sistema operativo de la plataforma para iOS, Android, Android for Work y Windows (solo se pueden usar las versiones de Windows 10; déjelo en blanco si se admite Windows 8.1).
  - Versión mínima.
  - Versión máxima.
- Restricción de los dispositivos de propiedad personal (solo iOS, Android, Android for Work y macOS).

## <a name="default-restrictions"></a>Restricciones predeterminadas

Las restricciones predeterminadas se proporcionan automáticamente para las restricciones de inscripción de tipo de dispositivo y límite de dispositivo. Puede cambiar las opciones para los valores predeterminados. Las restricciones predeterminadas se aplican a todos los usuarios e inscripciones sin usuario. Puede invalidar estos valores predeterminados mediante la creación de nuevas restricciones con prioridades más altas.

## <a name="create-a-restriction"></a>Crear una restricción

1. Inicie sesión en Azure Portal.
2. Seleccione **Más servicios**, busque **Intune** y, después, seleccione **Intune**.
3. Seleccione **Inscripción de dispositivos** > **Restricciones de inscripción**.
4. Seleccione **Crear restricción**.
5. Asigne un nombre y una descripción a la restricción.
6. Elija un **tipo de restricción** y, después, seleccione **Crear**.
7. Para las restricciones de límite de dispositivo, seleccione **Límite de dispositivos** para establecer el número máximo de dispositivos que puede inscribir un usuario.
8. Para las restricciones de tipo de dispositivo, seleccione **Plataformas** y **Configuraciones de plataforma** para permitir o bloquear varias versiones y plataformas.
9. Seleccione **Asignaciones** > **+ Seleccionar grupos**.
10. En **Seleccionar grupos**, seleccione uno o más grupos y, después, elija **Seleccionar**. La restricción se aplica únicamente a los grupos a los que está asignada. Si no asigna una restricción al menos a un grupo, no tendrá ningún efecto.
11. Seleccione **Guardar**.
12. La nueva restricción se crea con una prioridad justo por encima del valor predeterminado. También puede [cambiar la prioridad](#change-enrollment-restriction-priority).

## <a name="set-device-type-restrictions"></a>Establecer restricciones de tipo de dispositivo

Puede cambiar la configuración de una restricción de tipo de dispositivo mediante estos pasos:

1. Inicie sesión en Azure Portal.
2. Seleccione **Más servicios**, busque **Intune** y, después, seleccione **Intune**.
3. Seleccione **Inscripción de dispositivos** > **Restricciones de inscripción**.
4. En **Restricciones de tipo de dispositivo**, elija la restricción que quiera establecer.
5. Bajo el nombre de la restricción (**Todos los usuarios** para la restricción predeterminada), seleccione **Plataformas**. Pulse **Permitir** o **Bloquear** para cada plataforma de la lista.
6. Seleccione **Guardar**.
7. Bajo el nombre de la restricción (**Todos los usuarios** para la restricción predeterminada), seleccione **Configuraciones de plataforma**. Después, seleccione las **versiones** mínima y máxima de las plataformas especificadas. Entre las versiones admitidas se incluyen:
    - Android y Android for Work admiten major.minor.rev.build.
    - iOS admite major.minor.rev.
    - Windows admite major.minor.rev.build únicamente para Windows 10.
  Las versiones de sistema operativo no son relevantes en dispositivos Apple que se inscriban en el Programa de inscripción de dispositivos, Apple School Manager ni la aplicación Apple Configurator.
8. Especifique si quiere **Permitir** o **Bloquear** dispositivos de **propiedad personal** para las plataformas de la lista.
    ![Área de trabajo de restricciones de dispositivos con las configuraciones de plataforma de dispositivos predeterminadas en la que se muestran las opciones de propiedad personal configuradas](media/device-restrictions-platform-configurations.png)
9. Seleccione **Guardar**.


>[!NOTE]
>- Si bloquea los dispositivos Android de propiedad personal de la inscripción, los dispositivos Android for Work de propiedad personal todavía pueden inscribirse.
>- De forma predeterminada, la configuración de los dispositivos Android for Work es igual que la configuración de los dispositivos Android. Dejará de ser así después de modificar la configuración de Android for Work.
>- Si bloquea la inscripción de Android for Work personal, tan solo los dispositivos Android corporativos podrán inscribirse como Android for Work.

## <a name="set-device-limit-restrictions"></a>Establecer restricciones de límite de dispositivos

Para cambiar la configuración de una restricción de límite de dispositivos, siga estos pasos:

1. Inicie sesión en Azure Portal.
2. Seleccione **Más servicios**, busque **Intune** y, después, seleccione **Intune**.
3. Seleccione **Inscripción de dispositivos** > **Restricciones de inscripción**.
4. En **Restricciones de límite de dispositivo**, elija la restricción que quiera establecer.
5. Seleccione **Límite de dispositivos** y, después, en la lista desplegable, seleccione el número máximo de dispositivos que puede inscribir un usuario.
    ![Hoja de restricciones de límite de dispositivos con las restricciones de límite de dispositivos](./media/device-restrictions-limit.png)
6. Seleccione **Guardar**.


Cuando el usuario alcance el límite de dispositivos inscritos, recibirá una notificación en la que se le informará de ello. Por ejemplo, en iOS, tiene un aspecto similar al siguiente:

![Notificación del límite en un dispositivo iOS](./media/enrollment-restrictions-ios-set-limit-notification.png)

## <a name="change-enrollment-restriction-priority"></a>Cambiar la prioridad de las restricciones de inscripción

La prioridad se usa cuando un usuario existe en varios grupos a los que se asignan restricciones. Los usuarios solo están sujetos a la restricción de prioridad más alta asignada a un grupo al que pertenecen. Por ejemplo, Juan está en el grupo A asignado a restricciones de prioridad 5, así como en el grupo B asignado a restricciones de prioridad 2. Juan solo está sujeto a las restricciones de prioridad 2.

Cuando se crea una restricción, se agrega a la lista justo encima de la predeterminada.

La inscripción de dispositivos incluye restricciones predeterminadas para el tipo y límite de dispositivo. Estas dos restricciones se aplican a todos los usuarios a menos que se reemplacen por restricciones de prioridad más alta.

Puede cambiar la prioridad de cualquier restricción que no sea la predeterminada.

1. Inicie sesión en Azure Portal.
2. Seleccione **Más servicios**, busque **Intune** y, después, seleccione **Intune**.
3. Seleccione **Inscripción de dispositivos** > **Restricciones de inscripción**.
4. Mantenga el puntero sobre la restricción en la lista de prioridades.
5. Con los tres puntos verticales, arrastre la prioridad a la posición deseada en la lista.
