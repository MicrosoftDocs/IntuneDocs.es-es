---
title: Obtener un certificado push MDM de Apple para Intune
titleSuffix: ''
description: Obtenga un certificado push MDM de Apple para administrar dispositivos iOS con Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 805c3da286acddcda16d845182ba192124f88d21
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723494"
---
# <a name="get-an-apple-mdm-push-certificate"></a>Obtener un certificado push MDM de Apple

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Se requiere un certificado push MDM de Apple para que Intune pueda administrar dispositivos iOS y macOS. Después de agregar el certificado a Intune, los usuarios pueden inscribir sus dispositivos usando:

- la aplicación Portal de empresa;

- métodos de inscripción masiva de Apple, como el Programa de inscripción de dispositivos, Apple School Manager o Apple Configurator.

Para obtener más información sobre las opciones de inscripción, consulte [Elegir cómo inscribir los dispositivos iOS](ios-enroll.md).

Cuando un certificado de inserción expira, se debe renovar. En el momento de renovarlo, asegúrese de usar el mismo ID de Apple que utilizó la primera vez que creó el certificado de inserción.


## <a name="steps-to-get-your-certificate"></a>Pasos para obtener el certificado
Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), elija **Inscripción de dispositivos** > **Inscripción de Apple** > **Certificado push MDM de Apple** y luego siga estos pasos en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

### <a name="step-1-grant-microsoft-permission-to-send-user-and-device-information-to-apple"></a>Paso 1. Conceder a Microsoft permiso para enviar información de usuarios y dispositivos a Apple
Seleccione **Acepto** para conceder permiso a Microsoft para el envío de datos a Apple.

![Pantalla Configurar certificado push MDM con la inserción de MDM sin configurar.](./media/apple-mdm-push-certificate-get/create-mdm-push-certificate.png)

### <a name="step-2-download-the-intune-certificate-signing-request-required-to-create-an-apple-mdm-push-certificate"></a>Paso 2. Descargar la solicitud de firma de certificado de Intune necesaria para crear un certificado push MDM de Apple
Seleccione **Descargue su CSR** para descargar y guardar localmente el archivo de solicitud. El archivo se usa para solicitar un certificado de relación de confianza desde el portal de certificados push de Apple.

### <a name="step-3-create-an-apple-mdm-push-certificate"></a>Paso 3: Crear un certificado push MDM de Apple
Seleccione **Crear el certificado push MDM** para ir al Portal de certificados push de Apple. Inicie sesión con el id. de Apple de su empresa y, después, haga clic en **Crear certificado**. Seleccione **Elegir archivo** y busque el archivo de solicitud de firma de certificado y, luego, elija **Cargar**. En la página de confirmación, elija **Descargar** para descargar el archivo de certificado (.pem) y guárdelo localmente.

> [!NOTE]
> El certificado está asociado con el id. de Apple que se usó para crearlo. Como procedimiento recomendado, use un Id. de Apple de empresa para las tareas de administración y asegúrese de que el buzón de correo está supervisado por más de una persona como en una lista de distribución. No use nunca un id. de Apple personal.

### <a name="step-4-enter-the-apple-id-used-to-create-your-apple-mdm-push-certificate"></a>Paso 4. Escribir el ID de Apple usado para crear el certificado push MDM de Apple
Registre este identificador como un recordatorio para renovar el certificado.

### <a name="step-5-browse-to-your-apple-mdm-push-certificate-to-upload"></a>Paso 5. Buscar el certificado push MDM de Apple que quiere cargar
Vaya al archivo de certificado (.pem), elija **Abrir** y luego elija **Cargar**. Con el certificado de inserción, Intune puede inscribir y administrar dispositivos de Apple.

## <a name="renew-apple-mdm-push-certificate"></a>Renovar un certificado push MDM de Apple
El certificado push MDM de Apple es válido durante un año y debe renovarse anualmente para mantener la administración de dispositivos iOS y macOS. Si el certificado expira, no se podrá establecer una conexión con los dispositivos Apple inscritos.

El certificado está asociado con el id. de Apple que se usó para crearlo. Renueve el certificado push MDM con el mismo id. de Apple que se usó para crearlo.

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), elija **Inscripción de dispositivos** > **Inscripción de Apple** y luego, en el área de detalles, seleccione el icono **Certificado push MDM de Apple**.
2. Seleccione **Descargue su CSR** para descargar y guardar localmente el archivo .csr. El archivo se usa para solicitar un certificado de relación de confianza desde el portal de certificados push de Apple.
3. Seleccione **Crear el certificado push MDM** para ir al Portal de certificados push de Apple. Busque el certificado que quiera renovar y seleccione **Renovar**.
4. En la pantalla **Renew Push Certificate** (Renovar certificado push), indique notas que le ayuden a identificar el certificado más adelante, seleccione **Elegir archivo** para buscar el nuevo archivo de solicitud descargado y, después, elija **Cargar**.
   > [!TIP]
   > Se puede identificar un certificado por su UID. Examine el **Id. de asunto** en los detalles del certificado para encontrar la parte de GUID del UID. O bien, en un dispositivo iOS inscrito, vaya a **Configuración** > **General** > **Dispositivo** **Administración** > **Perfil de administración** > **Más detalles** > **Perfil de administración**. El segundo elemento de línea, **Tema**, contiene el GUID único que puede hacer que coincida con el certificado en el portal de certificados Push de Apple.
 
6. En la pantalla **Confirmación**, seleccione **Descargar** y guarde el archivo .pem localmente.
7. En [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), seleccione el icono para examinar **Certificado push MDM de Apple**, seleccione el archivo .pem descargado de Apple y elija **Cargar**.

El certificado push MDM de Apple aparece como **Activo** y expira al cabo de 365 días.
