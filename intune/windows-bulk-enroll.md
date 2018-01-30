---
title: "Inscripción masiva para Windows 10"
titlesuffix: Azure portal
description: "Creación de un paquete de inscripción masiva para Microsoft Intune"
keywords: 
author: Erikje
ms.author: erikje
manager: dougeby
ms.date: 10/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: damionw
ms.custom: intune-azure
ms.openlocfilehash: 8b4c9f5685c12bb6c15d15d85c73d573dfcd66e8
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="bulk-enrollment-for-windows-devices"></a>Inscripción masiva para dispositivos Windows

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Como administrador, puede unir una gran cantidad de dispositivos Windows nuevos a Azure Active Directory e Intune. Para inscribir de forma masiva dispositivos para el inquilino de Azure AD, debe crear un paquete de aprovisionamiento con la aplicación Windows Configuration Designer (WC). Aplicar el paquete de aprovisionamiento en dispositivos corporativos une estos dispositivos al inquilino de Azure AD y los inscribe para la administración de Intune. Una vez que se aplica el paquete, está listo para que los usuarios de Azure AD inicien sesión.

Los usuarios de Azure AD son usuarios estándar en estos dispositivos y reciben las aplicaciones requeridas y las directivas de Intune asignadas. En este momento, no se admiten los escenarios de autoservicio ni de portal de empresa.

## <a name="prerequisites-for-windows-devices-bulk-enrollment"></a>Requisitos previos para la inscripción masiva de dispositivos Windows

- Dispositivos que ejecuten Windows 10 Creator Update o posterior
- [Inscripción automática de Windows](windows-enroll.md#enable-windows-10-automatic-enrollment)

## <a name="create-a-provisioning-package"></a>Creación de un paquete de aprovisionamiento

1. Descargue el [Diseñador de configuración de Windows (WCD)](https://www.microsoft.com/store/apps/9nblggh4tx22) de la Microsoft Store.
![Captura de pantalla de la descripción y capturas de pantalla de la aplicación Windows Configuration Designer](media/bulk-enroll-store.png)

2. Abra la aplicación **Windows Configuration Designer** y seleccione **Provision desktop devices** (Aprovisionar dispositivos de escritorio).
![Captura de pantalla con la opción Provision desktop devices seleccionada en la aplicación Windows Configuration Designer](media/bulk-enroll-select.png)

3. Se abre una ventana de **nuevo proyecto** cuando especifica la siguiente información:
  - **Name**: nombre para el proyecto
  - **Carpeta de proyecto**: guarde la ubicación para el proyecto
  - **Description**: descripción opcional del proyecto ![Captura de pantalla de la especificación de nombre, carpeta de proyecto y descripción en la aplicación Windows Configuration Designer](media/bulk-enroll-name.png)

4.  Escriba un nombre único para los dispositivos. Los nombres pueden incluir un número de serie (%%SERIAL%%) o un conjunto aleatorio de caracteres. De manera opcional, también puede escribir una clave de producto si actualiza la edición de Windows, configura el dispositivo para su uso compartido y quita software instalado previamente.
![Captura de pantalla de la especificación de nombre, carpeta de proyecto y descripción en la aplicación Windows Configuration Designer](media/bulk-enroll-device.png)

5.  De manera opcional, puede configurar la red Wi-Fi a la que se conectan los dispositivos cuando se inician por primera vez.  Si no están configurados los dispositivos de red, se requiere una conexión de red con cable cuando se inicia por primera vez el dispositivo.
![Captura de pantalla de la habilitación de la red Wi-Fi, incluidas opciones de tipo de red y SSID de red en la aplicación Windows Configuration Designer](media/bulk-enroll-network.png)

6.  Seleccione **Enroll in Azure AD** (Inscribirse en Azure AD), escriba una fecha de expiración en **Bulk Token Expiry** (Expiración de token de operación masiva) y, luego, seleccione **Get Bulk Token** (Obtener token de operación masiva).
![Captura de pantalla de la especificación de nombre, carpeta de proyecto y descripción en la aplicación Windows Configuration Designer](media/bulk-enroll-account.png)

7. Proporcione sus credenciales de Azure AD para obtener un token de operación masiva.
![Captura de pantalla de la especificación de nombre, carpeta de proyecto y descripción en la aplicación Windows Configuration Designer](media/bulk-enroll-cred.png)

8.  Haga clic en **Siguiente** cuando el **Bulk Token** (Token de operación masiva) se recupere correctamente.

9. De manera opcional, puede **agregar aplicaciones** y **agregar certificados**. Estas aplicaciones y certificados se aprovisionan en el dispositivo.

10. De manera opcional, puede proteger el paquete de aprovisionamiento con contraseña.  Haga clic en **Crear**.
![Captura de pantalla de la especificación de nombre, carpeta de proyecto y descripción en la aplicación Windows Configuration Designer](media/bulk-enroll-create.png)

## <a name="provision-devices"></a>Aprovisionamiento de dispositivos

1. Obtenga acceso al paquete de aprovisionamiento en la ubicación especificada en la **carpeta de proyecto** que se especificó en la aplicación.

2. Elija cómo se aplicará el paquete de aprovisionamiento en el dispositivo.  Un paquete de aprovisionamiento se puede aplicar en un dispositivo de una de las siguientes maneras:
 - Coloque el paquete de aprovisionamiento en una unidad USB, inserte esta unidad en el dispositivo que desea inscribir de forma masiva y aplíquelo durante la configuración inicial
 - Coloque el paquete de aprovisionamiento en una carpeta de red y aplíquelo en el dispositivo que desee inscribir de forma masiva después de la configuración inicial

 Si desea obtener instrucciones paso a paso sobre cómo aplicar un paquete de aprovisionamiento, consulte [Apply a provisioning package](https://technet.microsoft.com/itpro/windows/configure/provisioning-apply-package) (Aplicación de un paquete de aprovisionamiento).

3. Una vez que aplique el paquete, el dispositivo se reiniciará automáticamente en 1 minuto.
 ![Captura de pantalla de la especificación de nombre, carpeta de proyecto y descripción en la aplicación Windows Configuration Designer](media/bulk-enroll-add.png)

4. Cuando el dispositivo se reinicia, se conecta a Azure Active Directory y se inscribe en Microsoft Intune.

## <a name="troubleshooting-windows-bulk-enrollment"></a>Solución de problemas con la inscripción masiva de Windows

### <a name="provisioning-issues"></a>Problemas de aprovisionamiento
El aprovisionamiento está diseñado para usarlo en dispositivos Windows nuevos. Los errores de aprovisionamiento pueden requerir un restablecimiento de fábrica del dispositivo o recuperar el dispositivo a partir de una imagen de arranque. En estos ejemplos se describen algunas de las razones para los errores de aprovisionamiento:

- Un paquete de aprovisionamiento que intenta unirse a un dominio de Active Directory o a un inquilino de Azure Active Directory que no crea una cuenta local podría generar que el dispositivo no sea accesible si el proceso de unión al dominio presenta un error debido a la falta de conectividad de red.
- Los scripts ejecutados por el paquete de aprovisionamiento se ejecutan en el contexto del sistema. Los scripts pueden realizar cambios arbitrarios en el sistema de archivos del dispositivo y las configuraciones. Un script incorrecto o malintencionado podría poner el dispositivo en un estado que solo se podría recuperar si se restablece la imagen inicial o se realiza un restablecimiento de fábrica del dispositivo.

### <a name="problems-with-bulk-enrollment-and-company-portal"></a>Problemas con la inscripción masiva y el portal de empresa
Si un usuario intenta inscribir un dispositivo inscrito de manera masiva anteriormente con el portal de empresa, recibirá una advertencia de que su dispositivo necesita más acciones, de configuración o de inscripción. El dispositivo está inscrito, pero el sitio web o la aplicación del portal de empresa no reconocen la inscripción.

### <a name="bulk-enrollment-with-wi-fi"></a>Inscripción masiva mediante Wi-Fi 

Los certificados de usuarios específicos y la implementación Wi-Fi no se pueden usar con los dispositivos inscritos de forma masiva. Para administrar estas conexiones, es necesario usar [certificados de nivel de dispositivo](certificates-configure.md). 

### <a name="conditional-access"></a>Acceso condicional
El acceso condicional no está disponible para los dispositivos Windows inscritos mediante la inscripción masiva.
