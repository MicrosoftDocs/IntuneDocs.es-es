---
title: "Obtención de un certificado de DEP de Apple para Intune | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: instrucciones para configurar y cargar un certificado push MDM, que es un requisito previo para administrar dispositivos de Apple en Intune. "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/03/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e5c79c5-2883-4841-9be6-74cba16ee447
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08dad848a48adad7d9c6f0b5b3286f6550a266bd
ms.openlocfilehash: b2c79e92f6378825bdaac03d2d9be699bdaca95b
ms.lasthandoff: 02/15/2017

---

# <a name="get-an-apple-dep-certificate"></a>Obtención de un certificado de DEP de Apple 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Antes de poder inscribir dispositivos iOS corporativos con DEP, necesita un token de DEP de Apple. Este token permite a Intune sincronizar información sobre dispositivos corporativos que participan en DEP. También permite a Intune realizar cargas de perfiles de inscripción a Apple y asignar dispositivos a esos perfiles.

Para administrar dispositivos iOS corporativos con el Programa de inscripción de dispositivos (DEP) de Apple, la organización debe unirse a DEP de Apple y obtener dispositivos a través de ese programa. Puede consultar los detalles de este proceso en: https://deploy.apple.com. Las ventajas del programa incluyen dispositivos configurados con manos libres sin necesidad de usar un cable USB para conectar cada dispositivo a un equipo.

> [!NOTE]
> Lea esta nota solo si es un cliente que se ha migrado desde la consola de administración de Intune al portal de Azure. Si eliminó un token de DEP de Apple de la consola de administración de Intune durante el período de migración, es posible que dicho token se haya restaurado en su cuenta de Intune. Si esto sucede, elimine el token de DEP del portal de Azure. 

**Obtención del certificado de DEP de Apple**</br>
En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**. En la hoja de Intune, elija **Inscribir dispositivos** > **Token de DEP de Apple**, y luego siga los pasos numerados en el portal de Azure, que se indican a continuación.

**Paso 1. Descargue un certificado de clave pública de Intune necesario para crear un token de DEP de Apple.**<br>
Seleccione **Download your public key** (Descargar la clave pública) para descargar y guardar localmente el archivo de la clave de cifrado (.pem). El archivo .pem se usa para solicitar un certificado de relación de confianza en el portal del Programa de Inscripción de Dispositivos de Apple.

**Paso 2. Descargue un token de DEP de Apple desde el sitio web de Apple adecuado.**<br>
Seleccione [Crear token de DEP mediante los Programas de implementación de Apple](https://deploy.apple.com) (https://deploy.apple.com) e inicie sesión con su id. de Apple de empresa. Debe usar este id. de Apple para renovar el token de DEP.

   1.  En el [portal del Programa de inscripción de dispositivos](https://deploy.apple.com), vaya a **Programa de inscripción de dispositivos** &gt; **Administrar servidores** y, después, elija **Add MDM Server (Agregar servidor MDM)**.

   2.  Escriba el **nombre del servidor MDM** y, después, elija **Siguiente**. El nombre del servidor es su referencia para identificar el servidor de administración de dispositivos móviles (MDM). No es el nombre ni la dirección URL del servidor de Microsoft Intune.

   3.  Se abre el cuadro de diálogo **Agregar &lt;NombreDeServidor&gt;**. Elija **Elegir archivo...** para cargar el archivo .pem y, después, elija **Siguiente**.

   4.  El cuadro de diálogo **Agregar &lt;NombreDeServidor&gt;** muestra un vínculo **Your Server Token (Su token de servidor)**. Descargue el archivo de token de servidor (.p7m) en el equipo y, después, elija **Listo**.

    Este archivo de certificado (.p7m) se usa para establecer una relación de confianza entre los servidores de Intune y los del Programa de Inscripción de Dispositivos de Apple.

**Paso 3. Escriba el id. de Apple usado para crear el token de DEP de Apple. Este id. se puede usar para renovar el token de DEP de Apple.**

**Paso 4. Vaya a su token de DEP de Apple para cargarlo. Intune se sincronizará automáticamente con su cuenta de DEP.**<br>
Vaya al archivo de certificado (.pem), elija **Abrir** y luego elija **Cargar**. Con el certificado push, Intune puede inscribir y administrar dispositivos iOS insertando la directiva en los dispositivos móviles inscritos.

