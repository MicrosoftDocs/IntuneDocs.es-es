---
title: Descripción de los plazos de entrega de las directivas de protección de aplicaciones
titleSuffix: Microsoft Intune
description: Conozca los diferentes plazos de implementación de las directivas de protección de aplicaciones para comprender cuándo deben mostrarse los cambios en los dispositivos de usuarios finales.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ec111319-7e02-434f-946b-88647726bf1a
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: d26721ff27f380917fec7f4d23c0c5524737a4a3
ms.sourcegitcommit: fab685b22a010fe231b27a0c5eda34a6f22f4c8d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2020
ms.locfileid: "78216166"
---
# <a name="understand-app-protection-policy-delivery-timing"></a>Descripción de los plazos de entrega de las directivas de protección de aplicaciones

Conozca los diferentes plazos de implementación de las directivas de protección de aplicaciones para comprender cuándo deben mostrarse los cambios en los dispositivos de usuarios finales.

## <a name="delivery-timing-summary"></a>Resumen de plazos de entrega

La entrega de directivas de protección de aplicaciones depende del estado de la licencia y el registro del servicio de Intune para los usuarios.  

|    Estado de usuario    |    Comportamiento de protección de aplicaciones     |    Intervalo de reintento (véase nota)    |    ¿Por qué ocurre?    |
|-----------------------------------------------------|-------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
|    Inquilino no incorporado    |    Espere al próximo intervalo de reintento.  La protección de aplicaciones no está activa para el usuario.    |    24 horas    |    Se produce cuando no se ha configurado el inquilino de Intune.    |
|    Usuario sin licencia     |    Espere al próximo intervalo de reintento.  La protección de aplicaciones no está activa para el usuario.     |    12 horas. En dispositivos Android, para este intervalo se necesita la versión 5.6.0 o posterior del SDK de la directiva de protección de aplicaciones (APP) de Intune. Si no, para los dispositivos Android el intervalo es de 24 horas.   |    Se produce cuando el usuario no tiene licencia para Intune.    |
|    Usuario sin directivas de protección asignadas    |    Espere al próximo intervalo de reintento.  La protección de aplicaciones no está activa para el usuario.    |    12 horas        |    Se produce cuando no se ha asignado una configuración de directivas de protección de aplicaciones (APP) al usuario.    |
|    Directivas de protección de aplicaciones asignadas por el usuario, pero la aplicación no está definida en las directivas de protección de aplicaciones   |    Espere al próximo intervalo de reintento.  La protección de aplicaciones no está activa para el usuario.    |    12 horas        |    Se produce cuando no se ha agregado la aplicación a Protección de aplicaciones.    |
|    Usuario registrado correctamente para MAM de Intune    |    Se aplica la protección de aplicaciones según la configuración de la directiva.    Se realizan actualizaciones según el intervalo de reintento    |    Se define el servicio de Intune según la carga de usuarios.    Normalmente 30 minutos.     |    Se produce cuando el usuario se ha registrado correctamente con el servicio de Intune para la configuración de MAM.    |

> [!NOTE]
> Es posible que los intervalos de reintento necesiten que se produzca un uso activo de la aplicación, lo que significa que la aplicación se inicia y está en uso.  Si el intervalo de reintento es de 24 horas y el usuario espera 48 horas para iniciar la aplicación, el cliente de protección de aplicación volverá a intentarlo en 48 horas.

## <a name="handling-network-connectivity-issues"></a>Solucionar problemas de conectividad de la red

Cuando se produce un error en el registro del usuario debido a problemas de conectividad de la red, se usa un intervalo de reintento acelerado.  El cliente de protección de aplicación volverá a intentarlo a intervalos cada vez más largos hasta llegar al intervalo de 60 minutos o hasta que se realice una conexión correcta.  Después, el cliente seguirá intentándolo a intervalos de 60 minutos hasta que se realice una conexión correcta. Luego, el cliente volverá al intervalo de reintento estándar según el estado de usuario.

## <a name="next-steps"></a>Pasos siguientes

[Asignar licencias a los usuarios para que puedan inscribir dispositivos en Intune](../fundamentals/licenses-assign.md)

