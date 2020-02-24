---
title: Envío de notificaciones personalizadas a los usuarios con Microsoft Intune
titleSuffix: Microsoft Intune
description: Uso de Intune para crear y enviar notificaciones push personalizadas a los usuarios de dispositivos iOS/iPadOS y Android
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/15/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 412dc631f2092d1eb7d9a7332b903a4742472202
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/17/2020
ms.locfileid: "77413882"
---
# <a name="send-custom-notifications-in-intune"></a>Envío de notificaciones personalizadas en Intune  

Use Microsoft Intune para enviar notificaciones personalizadas a los usuarios de dispositivos iOS/iPadOS y Android administrados. Estos mensajes aparecen como notificaciones push estándar desde la aplicación Portal de empresa y la de Microsoft Intune en el dispositivo de un usuario, tal y como se muestran las notificaciones de otras aplicaciones del dispositivo. Los dispositivos Windows y macOS no admiten las notificaciones personalizadas de Intune.   

Los mensajes de notificación personalizados incluyen un título corto y un cuerpo de mensaje de 500 caracteres como máximo. Estos mensajes se pueden personalizar para cualquier propósito general de comunicación.

### <a name="what-the-notification-looks-like-on-an-iosipados-device"></a>Aspecto de la notificación en un dispositivo iOS/iPadOS

Si tiene la aplicación Portal de empresa abierta en un dispositivo iOS/iPadOS, la notificación es similar a la que se muestra en la captura de pantalla siguiente:

> [!div class="mx-imgBorder"]
> ![Notificación de prueba de Portal de empresa para iOS/iPadOS](./media/custom-notifications/105046-1.png)

Si el dispositivo está bloqueado, la notificación es similar a la captura de pantalla siguiente:

> [!div class="mx-imgBorder"]
> ![Notificación de prueba de Dispositivo bloqueado para iOS/iPadOS](./media/custom-notifications/105046-2.png)

### <a name="what-the-notification-looks-like-on-an-android-device"></a>Aspecto de la notificación en un dispositivo Android

Si tiene la aplicación Portal de empresa abierta en un dispositivo Android, la notificación es similar a la captura de pantalla siguiente:

> [!div class="mx-imgBorder"]
> ![Notificación de prueba para Android](./media/custom-notifications/105046-3.png)

## <a name="common-scenarios-for-sending-custom-notifications"></a>Escenarios habituales para el envío de notificaciones personalizadas  

- Notificar a los empleados un cambio en el horario, como el cierre de un edificio debido a inclemencias del tiempo.
- Enviar una notificación al usuario de un solo dispositivo para comunicar una solicitud urgente, como el reinicio del dispositivo para completar la instalación de una actualización. 

## <a name="considerations-for-using-custom-notifications"></a>Consideraciones sobre el uso de notificaciones personalizadas

**Configuración del dispositivo** 

- Los dispositivos deben tener la aplicación Portal de empresa o la de Microsoft Intune instalada para que los usuarios puedan recibir notificaciones personalizadas. También deben tener permisos configurados para permitir que la aplicación Portal de empresa o la de Microsoft Intune envíe notificaciones push. En caso necesario, la aplicación Portal de empresa y la de Microsoft Intune pueden pedir a los usuarios que permitan las notificaciones.  
- En Android, Google Play Services es una dependencia necesaria.  
- El dispositivo debe estar inscrito en MDM.

**Permisos**:
- Para enviar notificaciones a los grupos, su cuenta debe tener los siguientes permisos de RBAC en Intune: *Organization* > **Actualizar**.
- Para enviar notificaciones a un dispositivo, su cuenta debe tener los siguientes permisos de RBAC en Intune: *Tareas remotas* > **Envío de notificaciones personalizadas**.

**Creación de notificaciones**:  
- Para crear un mensaje, use una cuenta que tenga asignado un rol de Intune que incluya el permiso **Actualizar** para la **Organización**. Para asignar permisos a un usuario, consulte [Asignaciones de rol](../fundamentals/role-based-access-control.md#role-assignments).  
- Las notificaciones personalizadas se limitan a títulos de 50 caracteres y mensajes de 500.  
- Intune no guarda los mensajes enviados. Para enviar de nuevo un mensaje, debe volver a crearlo.  
- Solo puede enviar hasta 25 mensajes a grupos por hora. Esta restricción está en el nivel de inquilino. Esta limitación no se aplica cuando se envían notificaciones a individuos.
- Al enviar mensajes a dispositivos individuales, solo puede enviar hasta 10 mensajes por hora al mismo dispositivo. 
- Puede enviar notificaciones a varios usuarios o dispositivos asignando la notificación a los grupos. Al usar grupos, cada notificación puede destinarse directamente a 25 grupos como máximo. Los grupos anidados no cuentan para este total.  

  Los grupos pueden incluir usuarios o dispositivos, pero los mensajes solo se envían a los usuarios y a los dispositivos iOS/iPadOS o Android que el usuario haya registrado.  
- Puede enviar notificaciones a un solo dispositivo. En lugar de usar grupos, seleccione un dispositivo y, a continuación, use una [acción de dispositivo](device-management.md#available-device-actions) remota para enviar la notificación personalizada.  

**Entrega**:  
- Intune envía mensajes a la aplicación Portal de empresa o la de Microsoft Intune de los usuarios, que después crea la notificación push. No es necesario que los usuarios inicien sesión en la aplicación para que la notificación se inserte en el dispositivo.  
- Intune, al igual que la aplicación Portal de empresa y la de Microsoft Intune, no puede garantizar la entrega de una notificación personalizada. Las notificaciones personalizadas pueden aparecer después de varias horas de retraso, si acaso, por lo que no deben usarse para mensajes urgentes.  
- Los mensajes de notificación personalizados de Intune aparecen en los dispositivos como notificaciones push. Si la aplicación Portal de empresa está abierta en un dispositivo iOS/iPadOS cuando recibe la notificación, esta se muestra en la aplicación en lugar de ser una notificación push.  
- Las notificaciones personalizadas pueden verse en pantallas de bloqueo en dispositivos iOS/iPadOS y Android, en función de la configuración del dispositivo.  
- En los dispositivos Android, es posible que otras aplicaciones tengan acceso a los datos de las notificaciones personalizadas. No las use para las comunicaciones confidenciales.  
- Los usuarios de un dispositivo que ha anulado la inscripción recientemente o los que se han quitado de un grupo pueden seguir recibiendo una notificación personalizada, que posteriormente se envía a ese grupo.  Del mismo modo, si agrega un usuario a un grupo después de enviar una notificación personalizada al grupo, es posible que el usuario recién agregado reciba ese mensaje de notificación enviado anteriormente.  

## <a name="send-a-custom-notification-to-groups"></a>Envío de una notificación personalizada a grupos  

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) con una cuenta que tenga permisos para crear y enviar notificaciones, y vaya a **Administración de inquilinos** > **Notificaciones personalizadas**.  

2. En la pestaña Datos básicos, especifique lo siguiente y, después, seleccione **Siguiente** para continuar.  
   - **Título**: especifique un título para esta notificación. Los títulos están limitados a 50 caracteres.  
   - **Cuerpo**: especifique el mensaje. Los mensajes están limitados a 500 caracteres.

   ![Creación de una notificación personalizada](./media/custom-notifications/custom-notifications.png)  

3. En la pestaña **Asignaciones**, seleccione los grupos a los que le gustaría enviar esta notificación personalizada y, luego, seleccione Siguiente para continuar.  

4. En la pestaña **Revisar y crear**, revise la información y, cuando esté listo para enviar la notificación seleccione **Crear**.  

Intune procesa los mensajes que crea de forma inmediata. La única confirmación de que se ha enviado el mensaje es la notificación de Intune que confirma que se ha enviado la notificación personalizada.  

![Confirmación de una notificación enviada](./media/custom-notifications/notification-sent.png)  

Intune no realiza un seguimiento de las notificaciones personalizadas que envía y los dispositivos no registran la recepción fuera del centro de notificaciones del dispositivo.  

## <a name="send-a-custom-notification-to-a-single-device"></a>Envío de una notificación personalizada a un solo dispositivo  

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) con una cuenta que tenga permisos para crear y enviar notificaciones y vaya a **Dispositivos** > **Todos los dispositivos**.

2. Haga doble clic en el nombre del dispositivo administrado al que quiere enviar una notificación para abrir la página *Información general* de esos dispositivos.

3. En la página **Información general** de los dispositivos, seleccione la acción de dispositivo **Enviar notificación personalizada** para abrir el panel *Enviar notificación personalizada*. Si esta opción no está disponible, seleccione los puntos suspensivos ( **...** ) en la parte superior derecha de la página y, luego, seleccione **Enviar notificación personalizada**.

4. En el panel **Enviar notificación personalizada**, especifique los siguientes detalles del mensaje:  

   - **Título**: especifique un título para esta notificación. Los títulos están limitados a 50 caracteres.  
   - **Cuerpo**: especifique el mensaje. Los mensajes están limitados a 500 caracteres.  

5. Seleccione **Enviar** para enviar la notificación personalizada al dispositivo. A diferencia de las notificaciones que envía a los grupos, no configura una asignación ni revisa el mensaje antes de enviarlo.  

Intune procesa el mensaje inmediatamente. La única confirmación de que se ha enviado el mensaje es la notificación de Intune que recibirá en la consola, que muestra el texto del mensaje que ha enviado.  

## <a name="receive-a-custom-notification"></a>Recepción de una notificación personalizada  

En un dispositivo, los usuarios ven mensajes de notificación personalizados que envía Intune como una notificación push estándar desde la aplicación Portal de empresa o la de Microsoft Intune. Estas notificaciones son parecidas a las notificaciones push que reciben los usuarios de otras aplicaciones del dispositivo.  

En dispositivos iOS/iPadOS, si la aplicación Portal de empresa está abierta cuando se recibe la notificación, esta se muestra en la aplicación en lugar de ser una notificación push.  

La notificación permanece hasta que el usuario la descarta.  

## <a name="next-steps"></a>Pasos siguientes  

[Administrar dispositivos](device-management.md)
