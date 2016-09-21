---
title: "Solucionar problemas de implementación de aplicaciones | Microsoft Intune"
description: "Este tema le ayuda a resolver los problemas de implementación de aplicaciones con Windows Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 28ac298e-fb73-4c1c-b3fd-8336639e05e6
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a5256d4decfcd14de2d50a32a0906b6894639010
ms.openlocfilehash: 552514971a64b16f88a7d83a0f7d66a0c00b61b0


---

# Solucionar problemas de implementación de aplicaciones en Microsoft Intune
Si tiene problemas de implementación y administración de aplicaciones con Intune, empiece aquí. Este tema contiene algunos problemas comunes que puede encontrar junto con las soluciones.

## Códigos de error comunes de implementación de aplicaciones

|Código de error|Posible problema|Solución recomendada|
|--------------|--------------------|------------------------|
|0x80073CFF<br /><br />0x80CF201C (error de cliente)|Para instalar esta aplicación, debe tener un sistema habilitado para instalación de prueba.|Asegúrese de que el paquete de la aplicación tenga una firma de confianza y se haya instalado en un dispositivo unido al dominio que tenga habilitada la directiva AllowAllTrustedApps o en un dispositivo que tenga una licencia de instalación de prueba de Windows con la directiva AllowAllTrustedApps habilitada (que se aplica cuando se inscribe un dispositivo Windows RT).|
|0x80073CF0|No se pudo abrir el paquete.|Posibles causas:<br /><br />-   El paquete no está firmado.<br />-   El nombre del publicador no coincide con el sujeto que firma el certificado.<br /><br />Compruebe el registro de eventos AppxPackagingOM para obtener más información.|
|0x80073CF3|Error de actualización, dependencia o validación de conflicto en el paquete.|Posibles causas:<br /><br />-   El paquete entrante entra en conflicto con un paquete instalado.<br />-   No se encuentra una dependencia del paquete especificado.<br />-   El paquete no es compatible con la arquitectura correcta del procesador.<br /><br />Compruebe el registro de eventos AppXDeployment-Server para obtener más información.|
|0x80073CFB|El paquete suministrado ya está instalado y se ha bloqueado la reinstalación del paquete|Podría recibir este error si está instalando un paquete que no es idéntico al paquete que ya está instalado. Confirme que la firma digital también forma parte del paquete. Cuando un paquete se vuelve a generar o a firmar, dicho paquete ya no es idéntico bit a bit al paquete instalado previamente. Dos opciones para corregir este error son:<br /><br />-   Incrementar el número de versión de la aplicación y, a continuación, volver a generar y a firmar el paquete.<br />-   Quitar el paquete antiguo para todos los usuarios del sistema antes de instalar el nuevo paquete.|
|0x87D1041C|Instalación de la aplicación correcta, pero no se ha detectado la aplicación.|- Intune implementó la aplicación correctamente y, a continuación, la desinstaló (posiblemente el usuario final). Indique al usuario que vuelva a instalar la aplicación desde el portal de empresa. Las aplicaciones necesarias se reinstalarán automáticamente cuando vuelva a registrar el dispositivo.|

### Pasos siguientes
Si esta información de solución de problemas no le ha ayudado, póngase en contacto con el soporte técnico de Microsoft como se describe en [Cómo obtener soporte técnico de Microsoft Intune](how-to-get-support-for-microsoft-intune.md).



<!--HONumber=Sep16_HO1-->


