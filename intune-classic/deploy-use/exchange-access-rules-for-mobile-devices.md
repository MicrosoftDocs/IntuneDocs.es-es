---
title: Reglas de acceso a Exchange para dispositivos móviles
description: Reglas de acceso de Exchange ActiveSync para permitir o bloquear las conexiones con dispositivos con EAS
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 07/19/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 208b9f45-02d9-413a-b86a-8bad9b5008fa
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9c3da7d517bd26bf694ea7bfa658ec1a4688d8f8
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="exchange-access-rules-for-mobile-devices"></a>Reglas de acceso a Exchange para dispositivos móviles

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Las reglas de acceso a Exchange para dispositivos móviles determinan el nivel de acceso que dichos dispositivos tienen a Exchange ActiveSync. Esta configuración afecta a todos los dispositivos móviles, incluidos los que no están inscritos en Microsoft Intune. Puede empezar por definir una **Regla predeterminada** que se aplique a cualquier dispositivo móvil al que no se le aplique una regla personalizada.

La tabla siguiente contiene los niveles de acceso administrados por Exchange ActiveSync:

|Nivel de acceso|Descripción|
|----------------|---------------|
|**Permitir a los dispositivos el acceso a Exchange**|En el estado *Permitir acceso*, los dispositivos móviles pueden sincronizarse a través de Exchange ActiveSync y conectarse con el servidor Exchange para recuperar el correo electrónico y administrar el calendario, los contactos, las tareas y las notas. Esto es así siempre que el dispositivo cumpla las directivas de buzón de Exchange ActiveSync que haya configurado en Exchange, a menos que el administrador de Exchange haya bloqueado el usuario o el dispositivo móvil específico.|
|**Bloquear a los dispositivos el acceso a Exchange**|En el estado *Bloquear acceso*, los dispositivos móviles están bloqueados y no se pueden conectar al servidor Exchange. Los dispositivos reciben un error de tipo HTTP 403 (prohibido). El usuario recibe un mensaje de correo electrónico desde el servidor Exchange indicando que se bloqueó el acceso al buzón desde el dispositivo móvil. Este mensaje no se puede mostrar en el dispositivo móvil bloqueado. Mediante la tarea **Establecer notificación de usuario**, puede agregar texto personalizado a este mensaje con instrucciones para los usuarios cuyos dispositivos estén bloqueados. |
|**Poner en cuarentena los dispositivos para permitirlos o bloquearlos más tarde**|Cuando se pone en cuarentena un dispositivo móvil, este puede conectarse al servidor Exchange. Sin embargo, se le concede únicamente acceso limitado a los datos. El usuario puede agregar contenido a sus propias carpetas de calendario, contactos, tareas y notas, pero el servidor no permite al dispositivo que recupere contenido del buzón del usuario. El usuario recibe un solo mensaje de correo electrónico donde se le notifica que el dispositivo móvil se pone en cuarentena. Este mensaje se envía al dispositivo y al buzón de correo del usuario. Mediante la tarea **Establecer notificación de usuario**, puede agregar texto personalizado a este mensaje con instrucciones para los usuarios cuyos dispositivos estén en cuarentena.|

Una estrategia de acceso es una combinación de una **Regla predeterminada** y de **Excepciones de plataforma** que se aplican a todos los dispositivos móviles conectados a Exchange. En la tabla siguiente se enumeran algunas estrategias de acceso de ejemplo.

|Estrategia de acceso|Descripción|
|-------------------|---------------|
|Lista de admisión|Puede usar una *lista de permitidos* para conceder acceso a una lista de dispositivos conocidos y restringir el acceso a los demás dispositivos. Para ello, debe crear reglas personalizadas para las plataformas de dispositivos que pueden tener acceso al buzón de correo de un usuario. Tan pronto como cree dicha regla, debe establecer la regla de acceso predeterminada para bloquear o poner en cuarentena el resto de dispositivos. Para agregar un dispositivo nuevo a la lista de permitidos, cree una regla personalizada.|
|Lista de bloqueo|Puede usar una *lista de bloqueados* para conceder acceso de forma predeterminada a todos los dispositivos y bloquear un conjunto de dispositivos que no quiere que accedan a su organización. Para crear una lista de bloqueados, debe crear reglas personalizadas para bloquear las plataformas de dispositivos que no quiere sincronizar con los buzones de la organización. Se recomienda que establezca la regla predeterminada de forma que permita el acceso a todos los dispositivos que no estén explícitamente bloqueados por las reglas existentes. Para agregar un nuevo dispositivo o un conjunto de dispositivos a la lista de bloqueo, cree una nueva regla personalizada.|
|Admisión y bloqueo mixto|Además de crear listas de admisión y bloqueo, puede poner en cuarentena nuevos dispositivos móviles a medida que se introducen en la organización en el momento de la evaluación. Por ejemplo, si tiene una lista de bloqueo de dispositivos móviles no permitidos en su organización y una lista de admisión de dispositivos móviles permitidos en su organización, puede establecer la regla predeterminada en cuarentena. El resto de los dispositivos se pone en cuarentena automáticamente, lo que le permitirá detectar los dispositivos nuevos a medida que se introducen en la organización y decidir si los agrega a la lista de permitidos o de bloqueados.|
El siguiente procedimiento describe cómo crear una regla personalizada.

## <a name="create-a-default-access-rule"></a>Crear una regla de acceso predeterminada

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Directiva** &gt; **Exchange ActiveSync**.

2.  En la lista **Regla predeterminada**, seleccione la regla de acceso que quiere aplicar a todos los dispositivos móviles que no están cubiertos por una regla o exención personal. Elija **Guardar**.

En el procedimiento siguiente se describe cómo crear una regla personalizada:

## <a name="create-a-custom-access-rule"></a>Crear una regla de acceso personalizada

1. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Directiva** &gt; **Exchange ActiveSync**.

2.  En la lista **Excepciones de plataforma**, elija **Agregar regla** y, después, cree una regla personalizada. Elija **Guardar**.
