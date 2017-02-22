---
title: "Obtención de un certificado push MDM de Apple para Intune | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: conozca los pasos para obtener un certificado push MDM de Apple para administrar dispositivos iOS con Intune."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: c0884ded1c8c55bb1b7968e483864b42f5bd6bde


---

# <a name="get-an-apple-mdm-push-certificate"></a>Obtención de un certificado push MDM de Apple 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune permite la administración de dispositivos móviles (MDM) de iPad, iPhone y dispositivos Mac OS X y concede acceso a los usuarios al correo electrónico y las aplicaciones de la empresa. El certificado del Servicio de notificaciones push de Apple (APNs) es necesario para que Intune pueda administrar dispositivos iOS y Mac. Después de agregar el certificado a Intune, los usuarios pueden instalar la aplicación Portal de empresa para inscribir sus dispositivos, o bien se puede configurar la administración de dispositivos iOS corporativos.

**Para obtener el certificado push MDM:**<br>

En el portal de Azure, elija **More Services** (Más servicios), escriba **Intune** en el cuadro de texto y luego seleccione **Other** (Otros)  > **Intune**. En la hoja de Intune, elija **Inscribir dispositivos** > **Certificado push MDM de Apple**, y luego siga los pasos numerados en el portal de Azure, que se indican a continuación.

**Paso 1. Descargue la solicitud de firma de certificado de Intune necesaria para crear un certificado push MDM de Apple.**<br>
Seleccione **Descargue su CSR** para descargar y guardar localmente el archivo .csr. Se utiliza el archivo .csr para solicitar un certificado de relación de confianza desde el portal de certificados push de Apple.

**Paso 2. Cree un certificado push MDM de Apple.**<br>
Seleccione **Crear el certificado push MDM** para ir al Portal de certificados push de Apple. Inicie sesión con su id. de Apple de empresa para crear el certificado push mediante el archivo .csr. Después de elegir **Cargar** en el Portal de certificados push de Apple, recibirá un archivo .json. Use este archivo para el certificado push. Complete la descarga, vuelva al portal de certificados push de Apple para Certificados para servidores de terceros y elija **Descargar**. Descargue el certificado push (archivo .pem) y guarde el archivo localmente.
Nota

**Paso 3. Escriba el id. de Apple usado para crear el certificado push MDM de Apple.**

**Paso 4. Busque el certificado push MDM de Apple que quiere cargar.**<br>
Vaya al archivo de certificado (.pem), elija **Abrir** y luego elija **Cargar**. Con el certificado push, Intune puede inscribir y administrar dispositivos iOS insertando la directiva en los dispositivos móviles inscritos.



<!--HONumber=Feb17_HO1-->


