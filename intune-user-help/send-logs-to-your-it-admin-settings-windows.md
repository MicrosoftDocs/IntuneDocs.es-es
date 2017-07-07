---
title: "Envío de registros al administrador de TI para dispositivos Windows 10 | Microsoft Docs"
description: "Inscribir un dispositivo Windows 10 versión 1511 en Intune"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 05/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 038747fb-5b52-47c4-a2b6-f9218da4cfe1
searchScope: User help
ROBOTS: 
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: be9976f03bf749222ca372040d4d936e6a8fd26b
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="send-logs-to-your-it-admin-from-the-settings-app-for-windows-10"></a>Envío de registros al administrador de TI desde la aplicación de configuración para Windows 10

Si se produce un error mientras usa la el dispositivo Windows 10 administrado por su empresa, puede ayudar a su administrador de TI a solucionar el problema enviándole información por correo electrónico. Esta información se conserva en su dispositivo en un documento especial denominado "_registro de diagnóstico_".

1.  Abra la aplicación **Configuración** de Windows al ir al **menú Inicio** y seleccionar el botón **Configuración**. También puede buscar "configuración" en la barra de búsqueda.
2.  Vaya a **Cuentas** > **Obtener acceso a trabajo o escuela**.
3.  Seleccione "Exporta los archivos de registro de administración".

  ![La "pantalla de acceso a trabajo o escuela", que presenta la opción "Exportar" debajo del título "Configuración relacionada".](./media/w10-export-logs.png)

4. Los registros se guardarán en **C:\Users\Public\Public Documents\MDMDiagnostics**. Se crearán dos archivos: uno es el propio registro y el otro es un documento especial que permite al administrador revisar los registros en diferentes programas, como Microsoft Excel. Adjunte los dos archivos a un correo electrónico y envíelo al administrador. Si lo hace más de una vez, simplemente elija los archivos desde el día en que creó los registros. 

También debe enviar [registros desde la aplicación del Portal de empresa](send-logs-to-your-it-admin-cp-windows.md) para proporcionar a su administrador de TI más ayuda para intentar solucionar los problemas que puede encontrar. 

¿Sigue necesitando ayuda? Póngase en contacto con el administrador de TI. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](http://portal.manage.microsoft.com).
