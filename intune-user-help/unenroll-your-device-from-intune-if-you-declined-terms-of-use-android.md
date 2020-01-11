---
title: Quitar un dispositivo de la administración si ha rechazado los términos de uso | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 4278f000-0258-4de5-93a1-195b48e5061e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: f54f0d9453e93ad54a1d2a96ff25051f3d8bd3a1
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75857680"
---
# <a name="remove-your-device-from-management-if-you-declined-terms-of-use"></a>Quitar un dispositivo de la administración si ha rechazado los "términos de uso"

Si rechazó los términos de uso al intentar iniciar sesión en la aplicación Portal de empresa, se le impedirá iniciar sesión en dicha aplicación en futuros intentos, por lo que necesita seguir estas instrucciones alternativas para quitar el dispositivo de Intune.

Cuando se desinstala la aplicación Portal de empresa, también se quita el dispositivo de Intune. El dispositivo ya no puede acceder a los recursos de la empresa. Para obtener más información sobre lo que ocurre cuando se deja de administrar un dispositivo, vea [¿Qué ocurre cuando se anula la inscripción de un dispositivo de Intune?](what-happens-if-you-unenroll-your-device-from-intune-android.md)

Para poder desinstalar la aplicación Portal de empresa, debe ir a la opción **Administradores de dispositivos** y desactivar **Portal de empresa**. Los pasos pueden ser algo distintos, en función del dispositivo Android que tenga.

## <a name="removing-the-device-from-the-company-portal-app"></a>Quitar un dispositivo de la aplicación Portal de empresa

Para quitar un dispositivo de Intune y desinstalar la aplicación Portal de empresa:

1. Vaya a **configuración** &gt; **seguridad &amp; bloqueo de pantalla** &gt; **administradores de dispositivos**.

    Al completar este se anula la inscripción del dispositivo de forma inmediata.

2. Desactive el **Portal de empresa** o la casilla situada a su lado.

    Ahora puede desinstalar la aplicación Portal de empresa.

## <a name="removing-data-collected-by-the-company-portal-app"></a>Eliminación de datos recopilados por la aplicación Portal de empresa

Para quitar todos los datos que la aplicación Portal de empresa para Android almacena en el dispositivo:

- Para borrar los datos de la aplicación, vaya a Aplicaciones, haga clic en la aplicación y luego en el botón "Borrar datos".
- Elimine la carpeta "\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal".


¿Aún necesita ayuda? Póngase en contacto con el equipo de soporte técnico de su empresa (visite el [sitio web del Portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980) para obtener la información de contacto), o escriba al <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having unenrolling my Android device&body=Describe the issue you're experiencing here.">equipo de Microsoft Android</a>.
