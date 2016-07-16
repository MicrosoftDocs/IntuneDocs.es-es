---
title: Administrar alertas | Microsoft Intune
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 74dc4ce4-21da-4f40-a07f-3eea34561eee
ROBOTS: noindex,nofollow
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f33a86c51320c75ce74d20e0cac2b9581990ecec
ms.openlocfilehash: bfea7213f67b55807045bfd8b29fdb083b841a56


---

# Administrar alertas en Microsoft Intune
Utilice el área de trabajo **Alertas** en la consola de administración de Intune para evaluar el estado general de los dispositivos administrados de la organización y para identificar problemas.

#### Para ver las alertas activas

1.  En la consola de administración de Intune, realice una de las siguientes acciones:

    -   **Para mostrar información general sobre las alertas**, incluyendo las tres principales alertas y el número total de alertas activas, haga clic en **Información general del sistema**. Puede hacer clic en los vínculos de estas alertas para explorar en profundidad en busca de información más detallada.

    -   **Para mostrar datos de resumen de las alertas**, haga clic en **Alertas &gt; Información general**. En la página **Información general de alertas**, el área **Resumen de tipos de alerta** muestra un resumen de las alertas. Las alertas críticas aparecen en primer lugar. Puede hacer clic en los vínculos de estas alertas para explorar en profundidad en busca de información más detallada.

        > [!NOTE]
        > En algunos casos, es posible que un tipo de alerta aparezca más de una vez en la lista **Resumen de tipos de alerta**.
        > 
        > Por ejemplo, pueden aparecer en la lista las siguientes instancias del tipo de alerta Espacio libre en disco lógico:
        > 
        > -   3 Espacio libre en disco lógico
        > -   2 Espacio libre en disco lógico
        > 
        > Este comportamiento se produce cuando se genera el mismo tipo de alerta para dispositivos que ejecutan sistemas operativos distintos. En el ejemplo, la primera instancia del tipo de alerta Espacio libre en disco lógico, 3 Espacio libre en disco lógico, puede haber sido generada por equipos que ejecutan Windows® 7. La segunda instancia del tipo de alerta Espacio libre en disco lógico puede haber sido generada por equipos que ejecutan Windows Vista®.

    -   **Para mostrar todas las alertas activas**, haga clic en **Alertas &gt; Todas las alertas**. En la página **Alertas** se muestra una lista de todas las alertas activas con las columnas siguientes:

        1.  **Nombre** : el nombre del tipo de alerta que generó la alerta.

        2.  **Origen** : el vínculo al origen de la alerta. Si el umbral para mostrar del tipo de alerta se configura como **Mostrar todo**, este vínculo mostrará un único dispositivo. Si el umbral para mostrar del tipo de alerta se configura como un valor, este vínculo mostrará una lista de cada dispositivo afectado por esta alerta.

        3.  **Última actualización**: indica el momento de la última modificación de la alerta. Si una alerta está cerrada, se muestra el momento en el que se cerró.

        4.  **Gravedad**: indica la gravedad de la alerta.

## Visualización de las alertas del Tablón de anuncios
Las alertas del tablón de anuncios proporcionan importantes avisos de servicios, como una próxima actualización, mantenimiento o interrupción de un servicio. Utilice este procedimiento para ver y administrar alertas del tablón de anuncios.

#### Para ver y administrar las alertas del tablón de anuncios

1.  En la consola de administración de Intune, haga clic en **Información general del sistema**.

2.  Si hay anuncios de servicio importantes, se muestran en el área **Tablón de anuncios**.

3.  Si desea exportar una alerta del tablón de anuncios a un archivo de valores separados por comas (.csv) o HTML, en la consola de administración de Intune, haga clic en **Alertas &gt; Todas las alertas &gt; Notificaciones**. Seleccione una notificación, haga clic en el icono de exportación de la lista y, a continuación, siga las instrucciones.

## Revisión de los estados de Intune
En el área de trabajo **Información general del sistema**, vea los resúmenes de estado del sistema de Endpoint Protection, Actualizaciones, Estado del agente, Directiva y Software que le ayudan a identificar y priorizar los problemas que requieren atención inmediata. Cuando se interrumpe el sistema, en los mensajes de error también se proporciona un vínculo al resumen **Estado del servicio**. El resumen **Estado del servicio** muestra detalles acerca del problema en cada ubicación y siempre muestra la última actualización.

#### Para ver el estado de la suscripción

1.  En la consola de administración de Intune, haga clic en **Información general del sistema**.

2.  En el área **Estado del sistema**, puede examinar el estado de los diversos componentes de Microsoft Intune. Muchos de los elementos contienen vínculos que permiten examinar en profundidad para obtener más información. Por ejemplo, en **Endpoint Protection**, si selecciona el número de instancias aparecerá el área de trabajo **Endpoint Protection** con una lista del malware detectado. Si selecciona el número de dispositivos aparecerá el área de trabajo **Grupos** con una lista de los dispositivos en los que se ha detectado el malware.

## Cierre y reactivación de alertas
Las alertas de Intune permanecen activas hasta que se produce uno de los siguientes eventos:

-   Se resuelve el problema que provocó que se generara la alerta.

-   La alerta se cierra manualmente.

-   Pasan 5 días tras generarse la alerta. Después de 45 días, la alerta caduca y se cierra automáticamente.

Las alertas que se marcan como cerradas se eliminan permanentemente después de 90 días.

#### Para cerrar manualmente una alerta

1.  En la consola de administración de Intune, realice una de las siguientes acciones:

    1.  **Para cerrar una alerta de la lista de alertas**: haga clic en **Alertas &gt; Todas las alertas**. Seleccione una alerta y, después, haga clic en **Cerrar alerta**.

    2.  **Para cerrar una alerta para un dispositivo específico**: haga clic en **Grupos &gt; Todos los dispositivos**. Seleccione un dispositivo y haga clic en **Ver propiedades**. Después, en la pestaña **Alertas**, seleccione una alerta y haga clic en **Cerrar alerta**.

    3.  **Para cerrar una alerta del tablón de anuncios**: haga clic en **Información general del sistema**. Haga clic en la **X** de color gris junto a la alerta del tablón de anuncios.

#### Para ver y volver a activar alertas cerradas

1.  En la consola de administración de Intune, haga clic en **Alertas &gt; Todas las alertas**.

2.  En la lista **Filtros**, haga clic en **Cerrada**.

    Los nombres y la información adicional sobre las alertas aparecen en el panel de la lista de administración. Los detalles sobre la alerta seleccionada aparecen en el panel de vista previa.

3.  Para volver a activar la alerta seleccionada, haga clic en **Reactivar alerta**.

### Consulte también
[Recibir notificaciones mediante alertas de Microsoft Intune](get-notified-by-alerts.md)




<!--HONumber=Jun16_HO4-->


