---
title: "Configuración de directivas de configuración del Equipo de Windows"
description: "Use la **directiva general de configuración de Windows 10 Team** de Microsoft Intune para definir la configuración de los dispositivos Windows 10 Team inscritos, como Microsoft Surface Hub."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38194ef3-e26e-4682-958d-14b395fccba1
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d8d0ec02fccd7aff391d794f4db4c5c2db03c4dd
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/15/2017
---
# <a name="windows-team-configuration-policy-settings-in-microsoft-intune"></a>Configuración de directivas de configuración del Equipo de Windows en Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Use la **directiva general de configuración de Windows 10 Team** de Microsoft Intune para definir la configuración de los dispositivos con Windows 10 Team inscritos, como Microsoft Surface Hub.

|Nombre de la configuración|Detalles|
|----------------|-----------|
|**Permitir que la pantalla se active automáticamente cuando haya alguien en la sala**|Permite que el dispositivo se active automáticamente cuando su sensor detecta alguien en la sala.|
|**Requerir PIN para la proyección inalámbrica**|Especifica si debe escribir un PIN para poder usar las capacidades de proyección inalámbrica del dispositivo.|
|**Establecer una ventana de mantenimiento para actualizaciones del dispositivo**|Configura la ventana cuando las actualizaciones tienen lugar en el dispositivo. Puede configurar la hora de inicio de la ventana y la duración (de 1 a 5 horas).|
|**Habilitar Visión operativa de Azure**|Azure Operational Insights, parte del conjunto de aplicaciones Microsoft Operations Manager recopila, almacena y analiza los datos de archivos de registro de dispositivos con Windows 10 Team.<br /><br />Para conectarse a Visión operativa de Azure, se debe especificar un **Id. de área de trabajo** y una **Clave de área de trabajo**.|
|**Habilitar proyección inalámbrica de Miracast**|Habilite esta opción si quiere permitir que el dispositivo con Windows 10 Team use los dispositivos habilitados para Miracast para proyectar.<br /><br />Si habilita esta opción en **Seleccionar canal de Miracast**, seleccione el canal de Miracast que se usa para proyectar contenido.|
|**Seleccione la información sobre la reunión que se muestra en la pantalla de inicio de sesión**|Si habilita esta opción, puede elegir la información que se mostrará en el icono **Reuniones** de la **pantalla de inicio de sesión**. Puede:<br /><br />-   **Mostrar solo el organizador y la hora**<br />-   **Mostrar el organizador, la hora y el asunto (asunto oculto para reuniones privadas)**|
|**URL de imagen de fondo de pantalla de bloqueo**|Habilite esta opción para mostrar un fondo personalizado en la pantalla de **inicio de sesión** de los dispositivos Windows 10 Team desde la dirección URL que especifique.<br /><br />La imagen debe estar en formato PNG y la dirección URL debe comenzar con **https://**.|


### <a name="see-also"></a>Consulte también
[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

