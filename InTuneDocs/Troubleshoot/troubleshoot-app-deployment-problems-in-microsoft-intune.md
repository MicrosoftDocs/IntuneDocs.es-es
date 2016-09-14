---
title: "Solucionar problemas de implementación de aplicaciones | Microsoft Intune"
description: "Este tema le ayudará a solucionar problemas de implementación de aplicaciones con Microsoft Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 28ac298e-fb73-4c1c-b3fd-8336639e05e6
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: aa96cf3a1909e3ea2187a3beb0aede3228894504
ms.openlocfilehash: 9f4b91bd523c82665bcac54902b2e8cc9c72ef75


---

# Solucionar problemas de implementación de aplicaciones en Microsoft Intune
Si tiene problemas al implementar y administrar aplicaciones con Intune, empiece aquí. En este tema se incluyen algunos problemas comunes que pueden surgir y sus soluciones.

## Problemas habituales de implementación de aplicaciones

### Falta la información de contacto de TI en el Portal de empresa

1.  En la consola de administración de Intune, seleccione **Administración** &gt; **Portal de empresa**.

2.  Establezca los detalles de **TI de contacto** .

### Si no puede ver aplicaciones específicas en la lista

1.  Asegúrese de que esté consultando la lista de aplicaciones para un usuario o dispositivo en el que se implementó la aplicación.

2.  Asegúrese de que el dispositivo cumple los requisitos de la aplicación.

### Si obtiene un error al descargar una aplicación

1.  Asegúrese de que no haya más de una descarga simultánea por usuario. Cada usuario puede descargar una aplicación a la vez.

2.  Asegúrese de que no existen demasiadas descargas simultáneas por cuenta. Espere unos minutos y, a continuación, vuelva a intentarlo.

3.  Si recibe un mensaje nativo de iOS indicándole que no puede realizar la instalación, que la instalación se ha cancelado o que debe volver a intentarlo, puede deberse a una sobrecarga. Espere unos minutos y, a continuación, vuelva a intentarlo.

4.  Si la barra de progreso de descarga de la aplicación de iOS se completa, pero se produce un error al instalarla, es posible que haya algún problema en los archivos de la aplicación que proporcionó.


### Si la aplicación se queda bloqueada con el estado "en curso" durante la carga

1.  Al cargar una aplicación, primero se agregan los metadatos y, a continuación, el paquete de la aplicación. Después de cargar los metadatos, la aplicación aparece con el estado "en curso". Si observa que la aplicación se encuentra en el estado "en curso" durante un período de tiempo excesivo, elimine la aplicación y cárguela de nuevo.

2.  Asegúrese de no administrar la implementación de la aplicación mientras se encuentra en el estado "en curso".

### Si detecta un error durante la instalación de una aplicación de iOS

1.  Asegúrese de que el servidor de seguridad de la organización permite el acceso a los sitios web de certificación y aprovisionamiento de Apple.

2.  Para obtener más información, consulte la documentación para desarrolladores de Apple.

### Si las aplicaciones administradas no envían informes de estado de la instalación

El estado de la instalación no se recopilaba para las instalaciones de aplicaciones administradas antes de la actualización de servicio de Microsoft Intune en noviembre de 2014. Para los dispositivos en que se instalaron aplicaciones administradas antes de esta actualización de servicio, actualice cada implementación de aplicación asociada con la acción de implementación adecuada (por ejemplo, **Instalación disponible**). Cada dispositivo actualizará la aplicación durante la comprobación automática de aplicaciones disponibles. Para obtener más información, consulte [Update apps using Microsoft Intune (Actualizar aplicaciones con Microsoft Intune)](/intune/deploy-use/update-apps-using-microsoft-intune).

## <a name="BKMK_SoftDistErrorCodes"></a>Códigos de error de implementación de aplicaciones
En la tabla siguiente se indican los errores comunes que se pueden producir durante la implementación de aplicaciones de Intune, las causas más probables y las soluciones posibles.

|Código de error|Posible problema|Solución recomendada|
|--------------|--------------------|------------------------|
|0x80073CFF<br /><br />0x80CF201C (error de cliente)|Para instalar esta aplicación, debe tener un sistema habilitado para instalación de prueba.|Asegúrese de que el paquete de la aplicación tenga una firma de confianza y se haya instalado en un dispositivo unido al dominio que tenga habilitada la directiva AllowAllTrustedApps o en un dispositivo que tenga una licencia de instalación de prueba de Windows con la directiva AllowAllTrustedApps habilitada (que se aplica cuando se inscribe un dispositivo Windows RT).|
|0x80073CF0|No se pudo abrir el paquete.|Posibles causas:<br /><br />-   El paquete no está firmado.<br />-   El nombre del publicador no coincide con el sujeto que firma el certificado.<br /><br />Compruebe el registro de eventos AppxPackagingOM para obtener más información.|
|0x80073CF3|Error de actualización, dependencia o validación de conflicto en el paquete.|Posibles causas:<br /><br />-   El paquete entrante tiene conflicto con un paquete instalado.<br />-   No se encuentra una dependencia del paquete especificado.<br />-   El paquete no es compatible con la arquitectura correcta del procesador.<br /><br />Compruebe el registro de eventos AppXDeployment-Server para obtener más información.|
|0x80073CFB|El paquete suministrado ya está instalado y se ha bloqueado la reinstalación del paquete|Podría recibir este error si está instalando un paquete que no es idéntico al paquete que ya está instalado. Confirme que la firma digital también forma parte del paquete. Cuando un paquete se vuelve a generar o a firmar, dicho paquete ya no es idéntico bit a bit al paquete instalado previamente. Dos opciones para corregir este error son:<br /><br />-   Incrementar el número de versión de la aplicación y luego recompilar y volver a firmar el paquete.<br />-   Quitar el paquete antiguo para todos los usuarios del sistema antes de instalar el nuevo paquete.|
|0x87D1041C|La instalación de la aplicación se realizó correctamente, pero esta no se detecta.|-La aplicación se implementó correctamente mediante Intune y luego se desinstaló (posiblemente por parte del usuario final). Indique al usuario que vuelva a instalar la aplicación desde el portal de empresa. Las aplicaciones necesarias se volverán a instalar automáticamente cuando se vuelva a comprobar el dispositivo.|

### Pasos siguientes
Si esta información para solucionar problemas no le ha ayudado, póngase en contacto con el soporte técnico de Microsoft como se indica en [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico de Microsoft Intune).



<!--HONumber=Aug16_HO5-->


