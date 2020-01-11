---
title: Activar Windows Defender | Microsoft Docs
description: Obtenga información sobre cómo activar Windows Defender para tener acceso a los recursos de la empresa.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/08/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: d16dd2de-3ed5-474f-a04b-36dcd350162c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: shburbid
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 63d5ebc00182c8edaea6956612ecd047a1778dec
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75859039"
---
# <a name="turn-on-windows-defender-to-access-company-resources"></a>Activar Windows Defender para tener acceso a los recursos de la empresa

Su empresa o centro educativo quiere asegurarse de que los dispositivos que tienen acceso a los recursos están protegidos. Hay varias maneras de que usen [Windows Defender](https://www.microsoft.com/safety/pc-security/windows-defender.aspx), que es la protección integrada de Windows que busca software malintencionado.

Existen algunas opciones de configuración que puede que tenga que cambiar en Windows Defender para solucionar problemas de acceso. Estos pasos pueden requerir que deba desplazarse a un par de ubicaciones en el equipo.

## <a name="turn-on-windows-defender"></a>Activar Windows Defender

1. En **Inicio**, abra el **Panel de Control**.
2. Abra **Herramientas administrativas** > **Editar directiva de grupo**. Se abrirá el **Editor de directivas de grupo local** en una ventana nueva.
3. Abra **Configuración del equipo** > **Plantillas administrativas** > **Componentes de Windows** > **Antivirus de Windows Defender**. La opción **Desactivar Antivirus de Windows Defender** está bajo las carpetas de otras opciones. 
4. Abra **Desactivar Antivirus de Windows Defender** y asegúrese de que está establecido en **Deshabilitado** o en **No configurado**.

## <a name="turn-on-real-time-protection"></a>Activar Protección en tiempo real

Asegúrese de que Protección en tiempo real está activada; para ello, vaya a **Inicio** y busque **Centro de seguridad de Windows Defender**. Seleccione **Configuración de antivirus y protección contra amenazas** y confirme que tanto **Protección en tiempo real** como **Protección que proporciona la nube** están en estado **Activado**. Si estas opciones no aparecen, haga lo siguiente para habilitarlas:

1. En **Inicio**, abra el **Panel de Control**.
2. Abra **Herramientas administrativas** > **Editar directiva de grupo**. Se abrirá el **Editor de directivas de grupo local** en una ventana nueva.
3. Abra **Configuración del equipo** > **Plantillas administrativas** > **Componentes de Windows** > **Centro de seguridad de Windows Defender** > **Protección antivirus y contra amenazas**.
4. Abra la opción **Protección antivirus y contra amenazas** y establézcala en **Deshabilitado**.

## <a name="update-your-antivirus-definitions"></a>Actualizar las definiciones de antivirus

Asegúrese de que las definiciones de antivirus están actualizadas; para ello, vaya a **Inicio** y busque **Centro de seguridad de Windows Defender**. Seleccione **Actualizaciones de protección** y **Buscar actualizaciones** para asegurarse de que la protección frente a virus del dispositivo está actualizada. Si esta opción no aparece, siga los pasos de [Activar Protección en tiempo real](turn-on-defender-windows.md#turn-on-real-time-protection).

¿Aún necesita ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para obtener información de contacto, consulte el [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
