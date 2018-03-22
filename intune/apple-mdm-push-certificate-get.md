---
title: Obtención de un certificado push MDM de Apple
titlesuffix: Microsoft Intune
description: Conozca los pasos para obtener un certificado push MDM de Apple para administrar dispositivos iOS con Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 504f2431754aa88ddf79bef4a201cbf7aa032834
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2018
---
# <a name="get-an-apple-mdm-push-certificate"></a>Obtención de un certificado push MDM de Apple

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

 Intune permite la administración de dispositivos móviles (MDM) de dispositivos iPad, iPhone y macOS, y concede acceso a los usuarios al correo electrónico y las aplicaciones de la empresa. Se requiere un certificado push MDM para que Intune pueda administrar dispositivos iOS y Mac. Después de agregar el certificado a Intune, los usuarios pueden instalar la aplicación Portal de empresa para inscribir sus dispositivos. También pueden configurar la administración de dispositivos iOS corporativos con el programa de inscripción de dispositivos de Apple, o bien inscribirlos con Apple Configurator, por ejemplo. Para obtener más información sobre las opciones de inscripción, consulte [Elegir cómo inscribir los dispositivos iOS](enrollment-method-choose-ios.md).

## <a name="steps-to-get-your-certificate"></a>Pasos para obtener el certificado
En [Azure Portal](https://portal.azure.com), elija **Inscripción de dispositivos** > **Inscripción de Apple** > **Certificado push MDM de Apple** y, luego, siga estos pasos en [Azure Portal](https://portal.azure.com).

**Paso 1. Descargue la solicitud de firma de certificado de Intune necesaria para crear un certificado push MDM de Apple.**<br>
Seleccione **Descargue su CSR** para descargar y guardar localmente el archivo de solicitud. El archivo se usa para solicitar un certificado de relación de confianza desde el portal de certificados push de Apple.

  ![Pantalla Configurar certificado push MDM con la inserción de MDM sin configurar.](./media/create-mdm-push-certificate.png)

**Paso 2. Cree un certificado push MDM de Apple.**<br>
Seleccione **Crear el certificado push MDM** para ir al Portal de certificados push de Apple. Inicie sesión con el id. de Apple de su empresa y, después, haga clic en **Crear certificado**. Seleccione **Elegir archivo** y busque el archivo de solicitud de firma de certificado y, luego, elija **Cargar**. En la página de confirmación, elija **Descargar** para descargar el archivo de certificado (.pem) y guárdelo localmente.

> [!NOTE]
> El certificado está asociado con el id. de Apple que se usó para crearlo. Como procedimiento recomendado, use un Id. de Apple de empresa para las tareas de administración y asegúrese de que el buzón de correo está supervisado por más de una persona como en una lista de distribución. No use nunca un id. de Apple personal.

**Paso 3. Escriba el id. de Apple usado para crear el certificado push MDM de Apple.**<br>
Registre este identificador como un recordatorio para renovar el certificado.

**Paso 4. Busque el certificado push MDM de Apple que quiere cargar.**<br>
Vaya al archivo de certificado (.pem), elija **Abrir** y luego elija **Cargar**. Con el certificado de inserción, Intune puede inscribir y administrar dispositivos de Apple.

## <a name="renew-apple-mdm-push-certificate"></a>Renovar un certificado push MDM de Apple
El certificado push MDM de Apple es válido durante un año y debe renovarse anualmente para mantener la administración de dispositivos iOS y macOS. Si el certificado expira, no se podrá establecer una conexión con los dispositivos Apple inscritos.

El certificado está asociado con el id. de Apple que se usó para crearlo. Renueve el certificado push MDM con el mismo id. de Apple que se usó para crearlo.

1. En [Azure Portal](https://portal.azure.com), elija **Inscripción de dispositivos** > **Inscripción de Apple** y después elija **Certificado push MDM de Apple** en el área de detalles.
2. Seleccione **Descargue su CSR** para descargar y guardar localmente el archivo .csr. El archivo se usa para solicitar un certificado de relación de confianza desde el portal de certificados push de Apple.
3. Seleccione **Crear el certificado push MDM** para ir al Portal de certificados push de Apple. Busque el certificado que quiera renovar y seleccione **Renovar**.
4. En la pantalla **Renew Push Certificate** (Renovar certificado push), indique notas que le ayuden a identificar el certificado más adelante, seleccione **Elegir archivo** para buscar el nuevo archivo de solicitud descargado y, después, elija **Cargar**.
   > [!TIP]
   > Se puede identificar un certificado por su UID. Examine el **Id. de asunto** en los detalles del certificado para encontrar la parte de GUID del UID. O bien, en un dispositivo iOS inscrito, vaya a **Configuración** > **General** > **Dispositivo** **Administración** > **Perfil de administración** > **Más detalles** > **Perfil de administración**. El segundo elemento de línea, **Tema**, contiene el GUID único que puede hacer que coincida con el certificado en el portal de certificados Push de Apple.
 
6. En la pantalla **Confirmación**, seleccione **Descargar** y guarde el archivo .pem localmente.
7. En [Azure Portal](https://portal.azure.com), seleccione el icono para examinar **Certificado push MDM de Apple**, seleccione el archivo .pem descargado de Apple y elija **Cargar**.

El certificado push MDM de Apple aparece como **Activo** y expira al cabo de 365 días.
