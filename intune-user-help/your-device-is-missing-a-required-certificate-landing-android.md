---
title: El dispositivo no tiene un certificado necesario | Microsoft Docs
titlesuffix: Microsoft Intune
description: El dispositivo no tiene un certificado que necesita el equipo de soporte técnico de su empresa.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: cc86a53dd790059297430fd6b08f1a699aafbc84
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "55850665"
---
# <a name="your-device-is-missing-a-required-certificate"></a>El dispositivo no tiene un certificado necesario

## <a name="whats-a-certificate"></a>¿Qué es un certificado?

La [criptografía](https://technet.microsoft.com/library/cc962030.aspx) es la ciencia mediante la que se proporciona seguridad de información. Tradicionalmente, la criptografía se ha utilizado para aprobar los mensajes codificados y [garantizar la privacidad de la comunicación](https://technet.microsoft.com/library/cc962019.aspx). En su forma más simple, la criptografía sustituye o transpone letras para crear un mensaje codificado en un mensaje ilegible, codificado u oculto. Solo alguien con una clave de descodificación o _certificado_ puede revertir el mensaje codificado a su forma original y legible. El dispositivo Android utiliza certificados con Intune para asegurarse de que las comunicaciones entre el dispositivo y los recursos organizativos, como el correo electrónico y los documentos, se mantienen seguros desde un extremo, a través del aire, al otro.

## <a name="fixing-certificate-issues"></a>Corrección de errores de certificado

Si el dispositivo Android no está inscrito en Intune y no tiene un certificado determinado que necesita el equipo de soporte técnico de su empresa, no podrá iniciar sesión en la aplicación de Portal de empresa. Cuando intente iniciar sesión, verá el siguiente mensaje:

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

El primer paso que debe intentar es ver si en el dispositivo [falta un certificado que normalmente viene preinstalado en él](your-device-is-missing-a-preinstalled-certificate-android.md).

Si la resolución de problemas de certificados no funciona, el equipo de soporte técnico de su empresa podría [requerir que instale un segundo certificado para obtener una mayor seguridad](your-device-is-missing-an-IT-required-certificate-android.md).

¿Sigue necesitando ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
