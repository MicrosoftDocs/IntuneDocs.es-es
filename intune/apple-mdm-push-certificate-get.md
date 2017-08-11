---
title: "Obtención de un certificado push MDM de Apple"
titleSuffix: Intune on Azure
description: Conozca los pasos para obtener un certificado push MDM de Apple para administrar dispositivos iOS con Intune.
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 915b432ed32565e820e16a65932fcdeac00d9bc3
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2017
---
# <a name="get-an-apple-mdm-push-certificate"></a>Obtener un certificado push MDM de Apple

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune permite la administración de dispositivos móviles (MDM) de dispositivos iPad, iPhone y macOS, y concede acceso a los usuarios al correo electrónico y las aplicaciones de la empresa. Se requiere un certificado push MDM para que Intune pueda administrar dispositivos iOS y Mac. Después de agregar el certificado a Intune, los usuarios pueden instalar la aplicación Portal de empresa para inscribir sus dispositivos. También pueden configurar la administración de dispositivos iOS corporativos con el programa de inscripción de dispositivos de Apple, o bien inscribirlos con Apple Configurator, por ejemplo. Para obtener más información sobre las opciones de inscripción, consulte [Elegir cómo inscribir los dispositivos iOS](enrollment-method-choose-ios.md).

## <a name="steps-to-get-your-certificate"></a>Pasos para obtener el certificado
En el portal de Intune, pulse **Inscripción de dispositivos** > **Inscripción de Apple** **Certificado push MDM de Apple** y, después, siga los pasos siguientes en Azure Portal.

**Paso 1. Descargue la solicitud de firma de certificado de Intune necesaria para crear un certificado push MDM de Apple.**<br>
Seleccione **Descargue su CSR** para descargar y guardar localmente el archivo de solicitud. El archivo se usa para solicitar un certificado de relación de confianza desde el portal de certificados push de Apple.

  ![Captura de pantalla que muestra la pantalla Configurar certificado push MDM con Inserción de MDM sin configurar.](./media/create-mdm-push-certificate.png)

**Paso 2. Cree un certificado push MDM de Apple.**<br>
Seleccione **Crear el certificado push MDM** para ir al Portal de certificados push de Apple. Inicie sesión con el id. de Apple de la empresa para crear el certificado push mediante el archivo de solicitud. Después de elegir **Cargar** en el Portal de certificados push de Apple, recibirá un archivo .json. Use este archivo para el certificado push. Complete la descarga, vuelva al portal de certificados push de Apple para Certificados para servidores de terceros y elija **Descargar**. Descargue el certificado push (archivo .pem) y guarde el archivo localmente.

> [!NOTE]
> El certificado está asociado con el id. de Apple que se usó para crearlo. Como práctica recomendada, use un id. de Apple de la empresa para tareas de administración. No use nunca un id. de Apple personal.

**Paso 3. Escriba el id. de Apple usado para crear el certificado push MDM de Apple.**

**Paso 4. Busque el certificado push MDM de Apple que quiere cargar.**<br>
Vaya al archivo de certificado (.pem), elija **Abrir** y luego elija **Cargar**. Con el certificado push, Intune puede inscribir y administrar dispositivos iOS insertando la directiva en los dispositivos móviles inscritos.

## <a name="renew-apple-mdm-push-certificate"></a>Renovar un certificado push MDM de Apple
El certificado push MDM de Apple es válido durante un año y debe renovarse anualmente para mantener la administración de dispositivos iOS y macOS. Si el certificado expira, no se podrá establecer una conexión con los dispositivos Apple inscritos.

El certificado está asociado con el id. de Apple que se usó para crearlo. Renueve el certificado push MDM con el mismo id. de Apple que se usó para crearlo.

> [!NOTE]
> El certificado está asociado con el id. de Apple que se usó para crearlo. Como práctica recomendada, use un id. de Apple de la empresa para tareas de administración. No use nunca un id. de Apple personal.

1. En el portal de Intune, pulse **Inscripción de dispositivos** > **Inscripción de Apple** y, después, seleccione **Certificado push MDM de Apple**.
2. Seleccione **Descargue su CSR** para descargar y guardar localmente el archivo .csr. El archivo se usa para solicitar un certificado de relación de confianza desde el portal de certificados push de Apple.
3. Busque el certificado que quiera renovar y seleccione **Renovar**.
4. En la pantalla **Renovar certificado push**, indique notas para identificar el certificado más adelante, seleccione **Elegir archivo** para buscar el nuevo archivo de solicitud descargado y, después, pulse **Cargar**.
5. En la pantalla **Confirmación**, seleccione **Descargar** y guarde el archivo .pem localmente.
6. En el portal de Azure Intune, seleccione el icono para examinar **Certificado push MDM de Apple**, seleccione el archivo .pem descargado de Apple y elija **Cargar**.

El certificado push MDM de Apple aparece como **Activo** y expira al cabo de 365 días.
