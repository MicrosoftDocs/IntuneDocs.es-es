---
title: El dispositivo no tiene un certificado necesario | Microsoft Docs
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/11/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213
searchScope:
- User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: 207297601634f390051a6345b96bf09e1d031747
ms.openlocfilehash: 6b37cede797f965b82c067b274517277d8597939
ms.lasthandoff: 01/12/2017

---


# <a name="your-device-is-missing-a-required-certificate"></a>El dispositivo no tiene un certificado necesario

## <a name="whats-a-certificate"></a>¿Qué es un certificado?

La [criptografía](https://technet.microsoft.com/en-us/library/cc962030.aspx) es la ciencia mediante la que se proporciona seguridad de información. Tradicionalmente, la criptografía se ha utilizado para aprobar los mensajes codificados y [garantizar la privacidad de la comunicación](https://technet.microsoft.com/en-us/library/cc962019.aspx). En su forma más simple, la criptografía sustituye o transpone letras para crear un mensaje codificado en un mensaje ilegible, codificado u oculto. Solo alguien con una clave de descodificación o _certificado_ puede revertir el mensaje codificado a su forma original y legible. El dispositivo Android utiliza certificados con Intune para asegurarse de que las comunicaciones entre el dispositivo y los recursos organizativos, como el correo electrónico y los documentos, se mantienen seguros desde un extremo, a través del aire, al otro.

## <a name="fixing-certificate-issues"></a>Corrección de errores de certificado

Si el dispositivo Android no está inscrito en Intune y no tiene un certificado determinado que necesita el administrador de TI, no podrá iniciar sesión en la aplicación de portal de empresa. Cuando intente iniciar sesión, verá el siguiente mensaje:

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

El primer paso que debe intentar es ver si en el dispositivo [falta un certificado que normalmente viene preinstalado en él](your-device-is-missing-a-preinstalled-certificate-android.md).

Si esto no funciona, el administrador de TI podría [requerir que instale un segundo certificado para obtener una mayor seguridad](your-device-is-missing-an-IT-required-certificate-android.md).

¿Sigue necesitando ayuda? Póngase en contacto con el administrador de TI. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](http://portal.manage.microsoft.com).

