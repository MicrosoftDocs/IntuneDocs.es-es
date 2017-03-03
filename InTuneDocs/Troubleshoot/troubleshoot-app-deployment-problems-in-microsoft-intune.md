---
title: "Solucionar problemas de implementación de aplicaciones | Microsoft Docs"
description: "Este tema le ayudará a solucionar problemas de implementación de aplicaciones con Microsoft Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 09/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 28ac298e-fb73-4c1c-b3fd-8336639e05e6
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 239371198cbbc01b1345c72b3f887055acd44462


---

# <a name="troubleshoot-app-deployment-problems-in-microsoft-intune"></a>Solucionar problemas de implementación de aplicaciones en Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Si tiene problemas al implementar y administrar aplicaciones con Intune, empiece aquí. En este tema se incluyen algunos problemas comunes que pueden surgir y sus soluciones.

## <a name="common-app-deployment-error-codes"></a>Códigos de error comunes de implementación de aplicaciones

|Código de error|Posible problema|Solución recomendada|
|--------------|--------------------|------------------------|
|0x80073CFF<br /><br />0x80CF201C (error de cliente)|Para instalar esta aplicación, debe tener un sistema habilitado para instalación de prueba.|Asegúrese de que el paquete de la aplicación tenga una firma de confianza y se haya instalado en un dispositivo unido al dominio que tenga habilitada la directiva AllowAllTrustedApps o en un dispositivo que tenga una licencia de instalación de prueba de Windows con la directiva AllowAllTrustedApps habilitada.|
|0x80073CF0|No se pudo abrir el paquete.|Posibles causas:<br /><br />-   El paquete no está firmado.<br />-   El nombre del publicador no coincide con el sujeto que firma el certificado.<br /><br />Compruebe el registro de eventos AppxPackagingOM para obtener más información.|
|0x80073CF3|Error de actualización, dependencia o validación de conflicto en el paquete.|Posibles causas:<br /><br />-   El paquete entrante tiene conflicto con un paquete instalado.<br />-   No se encuentra una dependencia del paquete especificado.<br />-   El paquete no es compatible con la arquitectura correcta del procesador.<br /><br />Compruebe el registro de eventos AppXDeployment-Server para obtener más información.|
|0x80073CFB|El paquete suministrado ya está instalado y se ha bloqueado la reinstalación del paquete|Podría recibir este error si está instalando un paquete que no es idéntico al paquete que ya está instalado. Confirme que la firma digital también forma parte del paquete. Cuando un paquete se vuelve a generar o a firmar, dicho paquete ya no es idéntico bit a bit al paquete instalado previamente. Dos opciones para corregir este error son:<br /><br />-   Incrementar el número de versión de la aplicación y luego recompilar y volver a firmar el paquete.<br />-   Quitar el paquete antiguo para todos los usuarios del sistema antes de instalar el nuevo paquete.|
|0x87D1041C|La instalación de la aplicación se realizó correctamente, pero esta no se detecta.|-La aplicación se implementó correctamente mediante Intune y luego se desinstaló (posiblemente por parte del usuario final). Indique al usuario que vuelva a instalar la aplicación desde el portal de empresa. Las aplicaciones necesarias se volverán a instalar automáticamente cuando se vuelva a comprobar el dispositivo.|

## <a name="troubleshooting-apps-from-the-windows-store"></a>Solucionar problemas de aplicaciones de la Tienda Windows

La información contenida en el tema [Troubleshooting packaging, deployment, and query of Windows Store apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) (Solución de problemas de empaquetado, implementación y consulta de aplicaciones de la Tienda Windows) le ayuda a solucionar problemas comunes que pueden surgir al instalar aplicaciones desde la Tienda Windows, tanto si usa Intune como otros medios.

## <a name="troubleshooting-app-deployment-to-pcs-managed-by-the-intune-software-client"></a>Solucionar problemas de implementación de aplicaciones en equipos administrados por el cliente de software de Intune
Para solucionar problemas relacionados con la implementación de aplicaciones en equipos administrados por el cliente de software de Intune, puede consultar los dos archivos de registro siguientes:
- %Archivos de programa%\Microsoft\OnlineManagement\Logs folder
- %Archivos de programa%\Microsoft\OnlineManagement\Updates\ReportingEvents.log

Además, si necesita abrir un caso de soporte técnico para Intune, también le resultará útil enviar estos registros a Microsoft.


### <a name="next-steps"></a>Pasos siguientes
Si esta información para solucionar problemas no le ha ayudado, póngase en contacto con el soporte técnico de Microsoft como se indica en [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico de Microsoft Intune).



<!--HONumber=Dec16_HO2-->


