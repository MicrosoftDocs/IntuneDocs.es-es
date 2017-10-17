---
title: "Configurar la administración de Android"
description: "Habilite la administración de dispositivos móviles (MDM) para dispositivos Android y KNOX Standard con Microsoft Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dbe5cad1-3e0d-41a9-966b-738156089700
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: lacranda
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5826cd29bf07a3f1cf9b91ec75f0e0bb46050d60
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2017
---
# <a name="set-up-android-device-management"></a>Configurar la administración de dispositivos Android

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Como administrador de Intune, puede habilitar la administración de dispositivos Android, incluidos dispositivos Samsung Knox Standard, desde el Portal de empresa. Luego los usuarios pueden inscribir sus dispositivos mediante la aplicación del Portal de empresa, disponible en Google Play.

De manera predeterminada, los dispositivos Android pueden inscribirse en Intune. Para bloquear la inscripción de dispositivos Android, inicie sesión en el [portal de administración de Microsoft Intune](https://manage.microsoft.com) con sus credenciales de administrador. Elija **Administrador** > **Administración de dispositivos móviles** > **Reglas de inscripción** y después desactive la casilla **Permitir dispositivos Android**.

1.  **Configurar Intune**<br>
    Si aún no lo ha hecho, prepárese para la administración de dispositivos móviles. Para ello, [defina la entidad de administración de dispositivos móviles](prerequisites-for-enrollment.md#step-2-set-mdm-authority) como **Microsoft Intune** y configure MDM.

2.  **Inscripción de Android habilitada**<br>
    No se requieren configuraciones adicionales en la consola de Intune para habilitar la inscripción de dispositivos móviles de Android.

3.  **Indique a los usuarios cómo inscribir sus dispositivos para acceder a recursos de la empresa.**

    Para obtener instrucciones de inscripción del usuario final, consulte [Inscribir el dispositivo Android en Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android). El proceso de inscripción indica a los usuarios lo que pueden esperar y qué pueden o no ver los administradores de TI en sus dispositivos.

    Para más información acerca de otras tareas de usuario final, consulte estos artículos:
  - [Recursos sobre la experiencia del usuario final con Microsoft Intune](/intune/end-user-educate)
  - [Guía de usuario final para dispositivos Android](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

Debido a la ausencia de Google Play Store en China, los dispositivos Android deben obtener el Portal de empresa en los mercados de aplicaciones chinos. La aplicación Portal de empresa para Android estará disponible para su descarga en las siguientes tiendas:
* [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
* [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
* [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
* [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)
* [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)

La aplicación del Portal de empresa para Android usa Google Play Services para comunicarse con el servicio de Microsoft Intune. Como Google Play Services no está todavía disponible en China, la realización de cualquiera de las siguientes tareas puede tardar hasta 8 horas en completarse. 

|Consola de administración de Intune| Aplicación del Portal de empresa de Intune para Android |Sitio web del Portal de empresa de Intune|   
|---|---|---|
|Borrar todos los datos| Quitar un dispositivo remoto| Quitar dispositivo (local y remoto)|
|La eliminación de datos selectiva| Restablecer dispositivo| Restablecer dispositivo|
|Implementaciones de aplicaciones nuevas o actualizadas| Instalar aplicaciones de línea de negocio disponibles| Restablecimiento de la contraseña del dispositivo|
|Bloqueo remoto|||
|Restablecimiento de la contraseña|||

### <a name="see-also"></a>Consulte también
[Requisitos previos para la inscripción de dispositivos en Microsoft Intune](prerequisites-for-enrollment.md)
