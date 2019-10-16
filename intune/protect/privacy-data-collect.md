---
title: Recopilación de datos en Intune
titleSuffix: Microsoft Intune
description: Obtenga más información sobre cómo se recopilan los datos personales en Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1171740-936d-46a5-af37-f418bd6fa63e
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cd1d0de4b1ae930ebeff07539f9cfa8848f0b7ce
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306901"
---
# <a name="data-collection-in-intune"></a>Recopilación de datos en Intune

Cuando los usuarios inscriben sus dispositivos corporativos o personales con Intune, Intune recopila y comparte algunos datos personales. Intune recopila datos personales de los siguientes orígenes:

- Uso del administrador de Intune en Azure Portal.
- Dispositivos de usuario final (cuando se inscriben para la administración de Intune y durante el uso).
- Cuentas de clientes en servicios de terceros (por las instrucciones del administrador).
- Información de diagnóstico, rendimiento y uso.

Desde estos orígenes, Intune recopila información que se divide en las siguientes tres categorías: [identificados](#identified-data), [formato anónimo](#pseudonymized-data) y [agregados](#aggregated-data).

> [!NOTE]
> No vendemos ningún dato recogido por nuestro servicio a terceros por ningún motivo.

## <a name="identified-data"></a>Datos identificados

La mayoría de los datos personales recopilados por Intune son datos identificados. Estos datos están asociados a un usuario, dispositivo o aplicación, y son esenciales para la naturaleza de la administración. Los datos identificados se usan para administrar las aplicaciones y el dispositivo de un usuario, y para aprovisionar el servicio de Intune.

Los datos identificados recopilados por Intune pueden incluir lo siguiente, aunque no se trata de una lista exhaustiva: 

- Información de usuario
  - Nombre del propietario o usuario para mostrar (el nombre registrado en Azure del usuario identificado por theAzureUserID)
  - Nombre principal de usuario o dirección de correo electrónico
  - Identificador de usuario de terceros (como AppleID)
- Información de inventario de hardware
  - Nombre del dispositivo
  - Fabricante
  - Sistema operativo
  - Número de serie
  - Número IMEI.
  - Dirección IP
  - MacAddress Wi-Fi
  - ICCID
  - Número de teléfono
- Información de registro de auditoría, incluidos los datos sobre las siguientes actividades
  - Administrar
  - Crear
  - Actualización (edición)
  - Eliminar
  - Asignar
  - Tareas remotas
- Información de soporte técnico
  - Información de contacto (nombre, número de teléfono, dirección de correo electrónico)
  - Conversaciones de correo electrónico miembros del equipo de experiencia del usuario, de producto o de soporte técnico de Microsoft
- Información de control de acceso (Intune usa estos datos para administrar el acceso a las funciones y roles administrativos a través de características como [Control de acceso basado en roles](../fundamentals/role-based-access-control.md)).
  - Autenticadores estáticos (contraseña del cliente)
  - Claves de privacidad para los certificados 
- Información de cuenta y de administrador
  - Nombre y apellidos del usuario administrador
  - Nombre de usuario del administrador
  - UPN (correo electrónico)
  - Número de teléfono
  - Dirección de correo electrónico del propietario de la cuenta
  - Identificador de Active Directory de cada administrador de TI del cliente
  - Datos de facturación de los clientes de pago
  - Clave de suscripción
- Inventario de aplicaciones, como
  - nombre de la aplicación
  - Versión
  - identificador de la aplicación
  - tamaño
  - ubicación de instalación
  - Los datos de inventario de aplicaciones solo se recopilan cuando están marcados por el administrador como un dispositivo corporativo o si la característica de aplicación compatible está activada.  
- Identificadores de inquilino de terceros del cliente, como el identificador de Apple. 

## <a name="pseudonymized-data"></a>Datos de formato anónimo

Los datos de formato anónimo están asociados a un identificador único, con frecuencia un número generado por el sistema que por sí mismo no permite identificar a una persona, pero que se usa para proporcionar los servicios de empresa a los usuarios. 

Los datos de formato anónimo recopilados por Intune pueden incluir lo siguiente, aunque no se trata de una lista exhaustiva: 

- Datos de uso, rendimiento y diagnóstico ligados a un usuario o dispositivo
  - Número de veces que se usa una característica
  - Comandos proporcionados a la característica
  - Tiempo de respuesta de un servicio
  - Tasas de éxito de instalaciones y otros procesos
  - Errores de aplicación del portal de empresa de Intune
  - Identificadores de usuarios y dispositivos
  - Identificadores con fines de referencia, correlación o administración 
- Datos del dispositivo no asociados a un dispositivo o usuario (si estos datos están ligados a un dispositivo o usuario, Intune los trata como datos identificados)
  - Identificador de dispositivo de Intune.
  - Id. de dispositivo de Azure Active Directory
  - Id. de administración de dispositivos de Intune
  - Identificador de inquilino
  - Id. de cuenta
  - Id. del dispositivo EAS
  - Identificadores específicos de la plataforma
  - AppleID para dispositivos iOS
  - Dirección MAC para dispositivos Mac
  - Id. de Windows para dispositivos Windows
- Información de la aplicación administrada
  - Id. de la aplicación administrada
  - Etiqueta de dispositivo de la aplicación administrada
  - Id. de administración de dispositivos de Intune
  - Id. de dispositivo de Azure Active Directory
  - Claves de cifrado

## <a name="aggregated-data"></a>Datos agregados

Los datos agregados se usan para aprovisionar y mejorar el servicio de Intune. 

Los datos agregados recopilados por Intune pueden incluir lo siguiente, aunque no se trata de una lista exhaustiva: 

- Datos de uso del administrador de todos los inquilinos de Intune (por ejemplo, los controles de administración seleccionados al interactuar con la consola de administración)
- Información de la cuenta de inquilino (estos datos están disponibles en la hoja de Intune)
  - Número de dispositivos o usuario inscritos
  - Número de plataformas de dispositivo identificadas  
  - Número de dispositivos instalados
  - installedDeviceCount: Número de dispositivos en los que está instalada la aplicación.
  - notApplicableDeviceCount: Número de dispositivos para los que la aplicación no está disponible.
  - notInstalledDeviceCount: Número de dispositivos para los que la aplicación está disponible, pero no está instalada.
  - pendingInstallDeviceCount: Número de dispositivos para los que la aplicación está disponible y la instalación está pendiente.

## <a name="next-steps"></a>Pasos siguientes

Obtenga más información sobre cómo Intune [almacena y procesa](privacy-data-store-process.md), y [comparte](privacy-data-secure-share.md) los datos personales. 
