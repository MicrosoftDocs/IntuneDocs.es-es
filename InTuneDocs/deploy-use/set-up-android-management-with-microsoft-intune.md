---
title: "Configurar la administración de Android | Microsoft Docs"
description: "Habilite la administración de dispositivos móviles (MDM) para dispositivos Android y KNOX Standard con Microsoft Intune."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dbe5cad1-3e0d-41a9-966b-738156089700
ms.reviewer: lacranda
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 6b99854e17e00a0dd0f91fa82fd1b79d1dfe5663
ms.openlocfilehash: 8e2588e2bb0537877f0164bc996fa973f25ea4dd


---

# <a name="set-up-android-device-management"></a>Configurar la administración de dispositivos Android

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Como administrador de Intune, puede habilitar la administración de dispositivos Android, incluidos dispositivos Samsung Knox Standard, desde el Portal de empresa. Luego los usuarios pueden inscribir sus dispositivos mediante la aplicación del Portal de empresa, disponible en Google Play.

De manera predeterminada, los dispositivos Android pueden inscribirse en Intune. Para bloquear la inscripción de dispositivos Android, inicie sesión en el [portal de administración de Microsoft Intune](http://manage.microsoft.com) con sus credenciales de administrador. Elija **Administrador** > **Administración de dispositivos móviles** > **Reglas de inscripción** y después desactive la casilla **Permitir dispositivos Android**.

1.  **Configurar Intune**<br>
    Si aún no lo ha hecho, prepárese para la administración de dispositivos móviles. Para ello, [defina la entidad de administración de dispositivos móviles](prerequisites-for-enrollment.md#step-2-set-mdm-authority) como **Microsoft Intune** y configure MDM.

2.  **Inscripción de Android habilitada**<br>
    No se requieren configuraciones adicionales en la consola de Intune para habilitar la inscripción de dispositivos móviles de Android.

3.  **Indique a los usuarios cómo inscribir sus dispositivos para acceder a recursos de la empresa.**

    Para obtener instrucciones de inscripción del usuario final, consulte [Inscribir el dispositivo Android en Intune](../enduser/enroll-your-device-in-intune-android.md). El proceso de inscripción indica a los usuarios lo que pueden esperar y qué pueden o no ver los administradores de TI en sus dispositivos.

    Para más información acerca de otras tareas de usuario final, consulte estos artículos:
  - [Recursos sobre la experiencia del usuario final con Microsoft Intune](how-to-educate-your-end-users-about-microsoft-intune.md)
  - [Guía de usuario final para dispositivos Android](../enduser/using-your-android-device-with-intune.md)

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



<!--HONumber=Feb17_HO3-->


