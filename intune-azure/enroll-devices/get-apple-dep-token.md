---
title: "Obtención de un certificado de DEP de Apple para Intune"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: instrucciones para configurar y cargar un certificado push MDM, que es un requisito previo para administrar dispositivos de Apple en Intune. "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/03/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e5c79c5-2883-4841-9be6-74cba16ee447
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 8edc42bb86e3856ac6568cc3c1acc5d757978e79
ms.lasthandoff: 02/18/2017

---

# <a name="get-an-apple-dep-certificate"></a>Obtención de un certificado de DEP de Apple

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Antes de poder inscribir dispositivos iOS propiedad de la empresa con el programa de inscripción de dispositivos (DEP) de Apple, necesita un token de DEP de Apple. Este token permite a Intune sincronizar información sobre dispositivos corporativos que participan en DEP. También permite a Intune realizar cargas de perfiles de inscripción a Apple y asignar dispositivos a esos perfiles.

Para administrar dispositivos iOS corporativos con el DEP, la organización debe unirse a DEP de Apple y obtener los dispositivos a través de ese programa. Puede consultar los detalles de este proceso en: https://deploy.apple.com. Las ventajas del programa incluyen dispositivos configurados con manos libres sin necesidad de usar un cable USB para conectar cada dispositivo a un equipo.

> [!NOTE]
> Esta nota solo se aplica a los clientes de Intune que se han migrado desde la consola de administración de Intune a Azure Portal. Si eliminó un token de DEP de Apple de la consola de administración de Intune durante el período de migración, es posible que dicho token se haya restaurado en su cuenta de Intune. Si esto sucede, elimine el token de DEP del portal de Azure.

## <a name="steps-to-get-the-apple-dep-certificate"></a>Pasos para obtener el certificado de DEP de Apple
En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**. En la hoja de Intune, elija **Inscribir dispositivos** > **Token de DEP de Apple**, y luego siga los pasos numerados en el portal de Azure, que se indican a continuación.

**Paso 1. Descargue un certificado de clave pública de Intune necesario para crear un token de DEP de Apple.**<br>
Seleccione **Download your public key** (Descargar la clave pública) para descargar y guardar localmente el archivo de la clave de cifrado (.pem). El archivo .pem se usa para solicitar un certificado de relación de confianza en el portal del Programa de Inscripción de Dispositivos de Apple.

**Paso 2. Descargue un token de DEP de Apple desde el sitio web de Apple adecuado.**<br>
Seleccione [Crear token de DEP mediante los Programas de implementación de Apple](https://deploy.apple.com) (https://deploy.apple.com) e inicie sesión con su id. de Apple de empresa. Debe usar este id. de Apple para renovar el token de DEP.

   a.  En el [portal del Programa de inscripción de dispositivos](https://deploy.apple.com), vaya a **Programa de inscripción de dispositivos** &gt; **Administrar servidores** y, después, elija **Add MDM Server (Agregar servidor MDM)**.

   b.  Escriba el **nombre del servidor MDM** y, después, elija **Siguiente**. El nombre del servidor es su referencia para identificar el servidor de administración de dispositivos móviles (MDM). No es el nombre ni la dirección URL del servidor de Microsoft Intune.

   c.  Se abre el cuadro de diálogo **Agregar &lt;NombreDeServidor&gt;**. Elija **Elegir archivo...** para cargar el archivo .pem y, después, elija **Siguiente**.

   d.  El cuadro de diálogo **Agregar &lt;NombreDeServidor&gt;** muestra un vínculo **Your Server Token (Su token de servidor)**. Descargue el archivo de token de servidor (.p7m) en el equipo y, después, elija **Listo**.

    This certificate (.p7m) file is used to establish a trust relationship between Intune and Apple’s Device Enrollment Program servers.

**Paso 3. Escriba el id. de Apple usado para crear el token de DEP de Apple. Este id. se puede usar para renovar el token de DEP de Apple.**

**Paso 4. Vaya a su token de DEP de Apple para cargarlo. Intune se sincronizará automáticamente con su cuenta de DEP.**<br>
Vaya al archivo de certificado (.pem), elija **Abrir** y luego elija **Cargar**. Con el certificado push, Intune puede inscribir y administrar dispositivos iOS insertando la directiva en los dispositivos móviles inscritos.

