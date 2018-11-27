---
title: Opciones de inscripción para dispositivos administrados por Microsoft Intune
titleSuffix: ''
description: Una lista de opciones de inscripción que los administradores pueden establecer para dispositivos administrados por Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: cf4ad6d4-423f-4826-ab8d-6eb7a7cfb559
search.appverid: MET150
ms.custom: get-started
ms.openlocfilehash: 99a880145fc51ce6eca39bd4470157c80fa097c2
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52182875"
---
# <a name="enrollment-options-for-devices-managed-by-intune"></a>Opciones de inscripción para dispositivos administrados por Intune

Como administrador de Intune, puede configurar la inscripción de dispositivos para ayudar a los usuarios y habilitar las capacidades de Intune.  Intune incluye las siguientes opciones de inscripción:

## <a name="terms-and-conditions"></a>términos y condiciones

Puede requerir que los usuarios acepten los términos y condiciones de la empresa antes de que puedan usar el Portal de empresa para inscribir sus dispositivos y obtener acceso a recursos como el correo electrónico y las aplicaciones de la empresa. La configuración de términos y condiciones es opcional. Obtenga más información sobre los [términos y condiciones](terms-and-conditions-create.md).

## <a name="enrollment-restrictions"></a>Restricciones de inscripción

Puede optar por restringir la inscripción de dispositivos por:
- Plataforma de dispositivo
- Número de dispositivos por usuario
- Bloquear dispositivos personales

Obtenga más información sobre las [restricciones de inscripción](enrollment-restrictions-set.md).

## <a name="enable-apple-device-enrollment"></a>Habilitar la inscripción de dispositivos de Apple

Se necesita un certificado push MDM para la inscripción de dispositivos iOS y macOS. Obtenga más información sobre los [certificados push MDM](apple-mdm-push-certificate-get.md).

## <a name="corporate-identifiers"></a>Identificadores corporativos

Puede mostrar los números de serie y los números de identidad internacional de equipo móvil (IMEI) para identificar los dispositivos corporativos. Obtenga más información sobre los [identificadores corporativos](corporate-identifiers-add.md).
## <a name="multi-factor-authentication"></a>Multi-factor Authentication

Puede requerir a los usuarios que usen un método de comprobación adicional, como un teléfono, un PIN o los datos biométricos, al inscribir un dispositivo. Obtenga más información sobre los [requisitos de la autenticación multifactor](multi-factor-authentication.md).

## <a name="device-enrollment-manager"></a>Administrador de inscripción de dispositivos
Puede hacer que los usuarios sean administradores de inscripción de dispositivos.  Los usuarios DEM pueden inscribir un gran número de dispositivos móviles con una sola cuenta de usuario. La cuenta del administrador de inscripción de dispositivos (DEM) puede inscribir hasta 1000 dispositivos. Obtenga más información sobre los [administradores de inscripción de dispositivos](device-enrollment-manager-enroll.md).

## <a name="device-categories"></a>Categorías de dispositivos

Puede usar las categorías de dispositivos para agregar automáticamente dispositivos a grupos en función de las categorías que defina. La organización de los dispositivos en grupos le facilita la tarea de administrar esos dispositivos. Obtenga más información sobre las [categorías de dispositivos](device-group-mapping.md).
