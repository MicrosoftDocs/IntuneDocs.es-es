---
title: Configuración de directivas de configuración del Equipo de Windows
description: Use la **directiva general de configuración de Windows 10 Team** de Microsoft Intune para definir la configuración de los dispositivos con Windows 10 Team inscritos, como Microsoft Surface Hub.
keywords: ''
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 38194ef3-e26e-4682-958d-14b395fccba1
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 70b1091cd58439b7d42eab1a612b0b63ca39103d
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="windows-team-configuration-policy-settings-in-microsoft-intune"></a>Configuración de directivas de configuración del Equipo de Windows en Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Use la **directiva general de configuración de Windows 10 Team** de Microsoft Intune para definir la configuración de los dispositivos con Windows 10 Team inscritos, como Microsoft Surface Hub.


|                                  Nombre de la configuración                                   |                                                                                                                                                                Detalles                                                                                                                                                                |
|---------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <strong>Permitir que la pantalla se active automáticamente cuando haya alguien en la sala</strong>   |                                                                                                                         Permite que el dispositivo se active automáticamente cuando su sensor detecta alguien en la sala.                                                                                                                          |
|              <strong>Requerir PIN para la proyección inalámbrica</strong>               |                                                                                                             Especifica si debe escribir un PIN para poder usar las capacidades de proyección inalámbrica del dispositivo.                                                                                                             |
|          <strong>Establecer una ventana de mantenimiento para actualizaciones del dispositivo</strong>           |                                                                                          Configura la ventana cuando las actualizaciones tienen lugar en el dispositivo. Puede configurar la hora de inicio de la ventana y la duración (de 1 a 5 horas).                                                                                           |
|               <strong>Habilitar Visión operativa de Azure</strong>                |                  Azure Operational Insights, parte del conjunto de aplicaciones Microsoft Operations Manager recopila, almacena y analiza los datos de archivos de registro de dispositivos con Windows 10 Team.<br /><br />Para conectarse a Visión operativa de Azure, se debe especificar un <strong>Id. de área de trabajo</strong> y una <strong>Clave de área de trabajo</strong>.                   |
|              <strong>Habilitar proyección inalámbrica de Miracast</strong>               |                                          Habilite esta opción si quiere permitir que el dispositivo con Windows 10 Team use los dispositivos habilitados para Miracast para proyectar.<br /><br />Si habilita esta opción en <strong>Seleccionar canal de Miracast</strong>, seleccione el canal de Miracast que se usa para proyectar contenido.                                           |
| <strong>Seleccione la información sobre la reunión que se muestra en la pantalla de inicio de sesión</strong> | Si habilita esta opción, puede elegir la información que se mostrará en el icono <strong>Reuniones</strong> de la <strong>pantalla de inicio de sesión</strong>. Puede:<br /><br />-   <strong>Mostrar solo el organizador y la hora</strong><br />-   <strong>Mostrar el organizador, la hora y el asunto (asunto oculto para reuniones privadas)</strong> |
|                <strong>URL de imagen de fondo de pantalla de bloqueo</strong>                 |                                           Habilite esta opción para mostrar un fondo personalizado en la pantalla de <strong>inicio de sesión</strong> de los dispositivos Windows 10 Team desde la dirección URL que especifique.<br /><br />La imagen debe estar en formato PNG y la dirección URL debe comenzar con <strong>https://</strong>.                                            |

### <a name="see-also"></a>Vea también
[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

