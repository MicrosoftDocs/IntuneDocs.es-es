---
title: "Solucionar problemas de perfiles de correo electrónico | Microsoft Intune"
description: "Perfiles de correo electrónico y cómo se pueden solucionar."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 05/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9915b275101e287498217c4f35e1c0e56d2425c2
ms.openlocfilehash: 9b699229489be2f09ea4c7a80e1e80f6ec7b106e


---

# Solucionar problemas de perfiles de correo electrónico en Microsoft Intune
Aquí se indican algunos problemas relacionados con los perfiles de correo electrónico y cómo se pueden solucionar.

Si esta información no soluciona el problema, vea [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico para Microsoft Intune) para conocer otras formas de obtener ayuda.


## No se pueden enviar imágenes desde la cuenta de correo electrónico
Los usuarios que tienen cuentas de correo electrónico configuradas automáticamente no pueden enviar imágenes ni fotos desde sus dispositivos.
Esto ocurre cuando no está habilitada la opción **Allow e-mail to be sent from third-party applications** (Permitir que se envíe correo electrónico desde aplicaciones de terceros).

### Solución de Intune

1.  Abra la consola de administración de Microsoft Intune, seleccione la carga de trabajo **Directiva** &gt; **Directiva de configuración**.

2.  Seleccione el perfil de correo electrónico y luego **Editar**.

3.  Seleccione **Permitir que se envíe correo electrónico desde aplicaciones de terceros.**

### Configuration Manager integrado con la solución de Intune

1.  Abra la consola de Configuration Manager &gt; **Activos y compatibilidad**.

2.  Expanda **Introducción** -&gt; **Configuración de cumplimiento** -&gt; **Acceso a los recursos de la compañía** y seleccione **Perfiles de correo electrónico**.

3.  Haga clic con el botón derecho en el perfil de correo electrónico y abra **Propiedades**.

4.  En la pestaña **Configuración de sincronización**, seleccione **Permitir el envío de correo electrónico desde aplicaciones de terceros**.

## Pasos siguientes
Si esta información para solucionar problemas no le ha ayudado, póngase en contacto con el servicio de soporte técnico de Microsoft como se indica en [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico de Microsoft Intune).



<!--HONumber=Jul16_HO4-->


