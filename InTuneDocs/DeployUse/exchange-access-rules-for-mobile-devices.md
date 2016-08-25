---
title: "Reglas de acceso a Exchange para dispositivos móviles | Microsoft Intune"
description: Reglas de acceso de Exchange ActiveSync para permitir o bloquear las conexiones con dispositivos con EAS
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 208b9f45-02d9-413a-b86a-8bad9b5008fa
ms.reviewer: muhosabe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c49e19e8c478af252d7b59c380d5500a57b71db5
ms.openlocfilehash: 7714a338d02afedde2ac090964e4d18d4410a80e


---

# Reglas de acceso a Exchange para dispositivos móviles
Las reglas de acceso a Exchange para dispositivos móviles determinan el nivel de acceso a Exchange ActiveSync que tienen esos dispositivos. Esta configuración afecta a todos los dispositivos móviles, incluidos los que no están inscritos en Microsoft Intune. Puede empezar por definir una **Regla predeterminada** que se aplicará a cualquier dispositivo móvil al que no se le aplique una regla personalizada. La tabla siguiente contiene los niveles de acceso administrados por Exchange ActiveSync:

|Nivel de acceso|Descripción|
|----------------|---------------|
|**Permitir a los dispositivos el acceso a Exchange**|En el estado de *permitir acceso*, los dispositivos móviles pueden sincronizarse a través de Exchange ActiveSync y conectarse con el servidor Exchange para recuperar el correo electrónico y administrar el Calendario, los Contactos, las Tareas y las Notas. Esto es así siempre que el dispositivo cumpla las directivas de buzón de Exchange ActiveSync que haya configurado en Exchange, a menos que el administrador de Exchange haya bloqueado el usuario o el dispositivo móvil específico.|
|**Bloquear a los dispositivos el acceso a Exchange**|En el estado *bloquear el acceso*, los dispositivos móviles se bloquean y no podrán conectarse al servidor Exchange. Los dispositivos recibirán un error HTTP 403 Forbidden (Prohibido). El usuario recibirá un mensaje de correo electrónico desde el servidor Exchange indicando que se bloqueó el acceso al buzón desde el dispositivo móvil. Este mensaje no puede estar en el dispositivo móvil bloqueado. Puede agregar texto personalizado a este mensaje con instrucciones para los usuarios cuyos dispositivos estén bloqueados mediante la tarea **Establecer notificación de usuario**.|
|**Poner en cuarentena los dispositivos para permitirlos o bloquearlos más tarde**|Cuando se pone en cuarentena un dispositivo móvil, este puede conectarse al servidor Exchange. Sin embargo, se le concede únicamente acceso limitado a los datos. El usuario puede agregar contenido a sus propias carpetas de calendario, contactos, tareas y notas, pero el servidor no permitirá al dispositivo que recupere contenido del buzón del usuario. El usuario recibirá un solo mensaje de correo que indica que el dispositivo móvil se pone en cuarentena. Este mensaje se recibe en el dispositivo y en el buzón del usuario. Puede agregar texto personalizado a este mensaje con instrucciones para los usuarios cuyos dispositivos estén en cuarentena a través de la tarea **Establecer notificación de usuario** .|

Una estrategia de acceso es una combinación de una **Regla predeterminada** y de **Excepciones de plataforma** que se aplican a todos los dispositivos móviles conectados a Exchange. La tabla siguiente contiene algunos ejemplos de estrategias de acceso.

|Estrategia de acceso|Descripción|
|-------------------|---------------|
|Lista de admisión|Puede usar una *lista de admisión* para conceder acceso a una lista de dispositivos conocidos y restringir el acceso al resto. Para ello, debe crear reglas personalizadas para las plataformas de dispositivo que tengan acceso a los buzones de los usuarios. Tan pronto como cree dicha regla, debe establecer la regla de acceso predeterminada para bloquear o poner en cuarentena el resto de dispositivos. Para agregar un nuevo dispositivo a la lista de admisión, cree una nueva regla personalizada|
|Lista de bloqueo|Puede usar una *lista de bloqueo* para conceder acceso de forma predeterminada a todos los dispositivos y bloquear un conjunto de dispositivos que no quiere que accedan a su organización. Cree una lista de bloqueo mediante reglas personalizadas para bloquear las plataformas de dispositivo que no quiere sincronizar con los buzones de la organización. La regla predeterminada debe establecerse para permitir el acceso a todos los dispositivos que no estén explícitamente bloqueados por las reglas existentes. Para agregar un nuevo dispositivo o un conjunto de dispositivos a la lista de bloqueo, cree una nueva regla personalizada.|
|Admisión y bloqueo mixto|Además de crear listas de admisión y bloqueo, puede poner en cuarentena nuevos dispositivos móviles a medida que se introducen en la organización en el momento de la evaluación. Por ejemplo, si tiene una lista de bloqueo de dispositivos móviles no permitidos en su organización y una lista de admisión de dispositivos móviles permitidos en su organización, puede establecer la regla predeterminada en cuarentena. El resto de dispositivos se pondrá en cuarentena automáticamente. Esto le permitirá examinar los nuevos dispositivos a medida que se introducen en la organización y decidir si los agrega a la lista de admisión o a la lista de bloqueo.|
El siguiente procedimiento describe cómo crear una regla personalizada.

## Crear una regla de acceso predeterminada

1.  En [Consola de administración de Microsoft Intune](http://manage.microsoft.com)&gt;**Directiva**&gt;**Exchange ActiveSync**.

2.  En la lista **Regla predeterminada** , seleccione la regla de acceso que desea aplicar a todos los dispositivos móviles no cubiertos por una regla o exención personal. Elija **Guardar**.

El siguiente procedimiento describe cómo crear una regla personalizada.

## Crear una regla de acceso personalizada

1. En [Consola de administración de Microsoft Intune](http://manage.microsoft.com)&gt;**Directiva**&gt;**Exchange ActiveSync**.

2.  En la lista **Excepciones de plataforma**, elija **Agregar regla** y cree una regla personalizada. Elija **Guardar**.



<!--HONumber=Aug16_HO1-->


