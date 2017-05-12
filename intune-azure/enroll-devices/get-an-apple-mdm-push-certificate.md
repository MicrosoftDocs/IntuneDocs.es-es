---
title: "Obtención de un certificado push MDM de Apple"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: conozca los pasos para obtener un certificado push MDM de Apple para administrar dispositivos iOS con Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: 91c6b063fbc17cf92aab50c4911e4bb33b76deb9
ms.contentlocale: es-es
ms.lasthandoff: 05/10/2017


---

# <a name="get-an-apple-mdm-push-certificate"></a>Obtener un certificado push MDM de Apple

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune permite la administración de dispositivos móviles (MDM) de dispositivos iPad, iPhone y macOS, y concede acceso a los usuarios al correo electrónico y las aplicaciones de la empresa. Se requiere un certificado push MDM para que Intune pueda administrar dispositivos iOS y Mac. Después de agregar el certificado a Intune, los usuarios pueden instalar la aplicación Portal de empresa para inscribir sus dispositivos. También pueden configurar la administración de dispositivos iOS corporativos con el programa de inscripción de dispositivos de Apple, o bien inscribirlos con Apple Configurator, por ejemplo. Para obtener más información sobre las opciones de inscripción, consulte [Elegir cómo inscribir los dispositivos iOS](choose-ios-enrollment-method.md).

## <a name="steps-to-get-your-certificate"></a>Pasos para obtener el certificado
En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**. En la hoja Intune, elija **Inscribir dispositivos** > **Inscripción de Apple** **Certificado push MDM de Apple** y, luego, siga los pasos numerados en Azure Portal, que se indican a continuación.

**Paso 1. Descargue la solicitud de firma de certificado de Intune necesaria para crear un certificado push MDM de Apple.**<br>
Seleccione **Descargue su CSR** para descargar y guardar localmente el archivo .csr. Se utiliza el archivo .csr para solicitar un certificado de relación de confianza desde el portal de certificados push de Apple.

**Paso 2. Cree un certificado push MDM de Apple.**<br>
Seleccione **Crear el certificado push MDM** para ir al Portal de certificados push de Apple. Inicie sesión con el Id. de Apple de la empresa para crear el certificado push mediante el archivo .csr. Después de elegir **Cargar** en el Portal de certificados push de Apple, recibirá un archivo .json. Use este archivo para el certificado push. Complete la descarga, vuelva al portal de certificados push de Apple para Certificados para servidores de terceros y elija **Descargar**. Descargue el certificado push (archivo .pem) y guarde el archivo localmente.
Nota

**Paso 3. Escriba el id. de Apple usado para crear el certificado push MDM de Apple.**

**Paso 4. Busque el certificado push MDM de Apple que quiere cargar.**<br>
Vaya al archivo de certificado (.pem), elija **Abrir** y luego elija **Cargar**. Con el certificado push, Intune puede inscribir y administrar dispositivos iOS insertando la directiva en los dispositivos móviles inscritos.

