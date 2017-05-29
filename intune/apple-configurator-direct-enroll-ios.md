---
title: "Inscripción de dispositivos iOS con Apple Configurator e inscripción directa"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda a usar Apple Configurator para inscribir dispositivos iOS corporativos con inscripción directa."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6c0a430-1851-4108-812a-87e0fc2623b5
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 5347e2023a9ce19f8e8ab960e2eebf8107530220
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="enroll-ios-devices-with-apple-configurator-and-direct-enrollment"></a>Inscripción de dispositivos iOS con Apple Configurator e inscripción directa 

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Intune permite la inscripción de dispositivos iOS corporativos con la herramienta [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) desde un equipo Mac. Este proceso no restablece los valores de fábrica del dispositivo e inscribe el dispositivo con una directiva predefinida. Este método está destinado a dispositivos **sin afinidad de usuario** y requiere una conexión USB entre el dispositivo iOS y un equipo Mac para configurar la inscripción corporativa.

>[!NOTE]
>Este método de inscripción no se puede usar con el método del [administrador de inscripción de dispositivos](device-enrollment-manager-enroll.md).

Cuando inscribe dispositivos iOS directamente, puede inscribir un dispositivo sin adquirir su número de serie. También puede nombrar el dispositivo con fines de identificación antes de que Intune capture el nombre del dispositivo durante la inscripción. No se admite la aplicación de portal de empresa para dispositivos inscritos directamente. Esta guía supone que se usa Apple Configurator 2.0 en un equipo Mac.

En [Choose how to enroll iOS devices in Intune](enrollment-method-choose-ios.md) (Selección del método para inscribir dispositivos iOS en Intune), se describen otros métodos de inscripción de dispositivos iOS).


## <a name="prerequisites"></a>Requisitos previos

Complete los siguientes requisitos previos antes de configurar la inscripción de dispositivos iOS:

- [Configurar dominios](https://docs.microsoft.com/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [Establecer la entidad de MDM](mdm-authority-set.md)
- [Crear grupos](https://docs.microsoft.com/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [Configurar el Portal de empresa](company-portal-app.md)
- Asignar licencias de usuario en el [Portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Obtener un certificado push MDM de Apple](apple-mdm-push-certificate-get.md)
- Asegurarse de tener acceso físico a dispositivos iOS
- Tener los números de serie de los dispositivos (consulte [Encontrar el número de serie de un producto Apple](https://support.apple.com//HT204308))
- Tener a mano cables de conexión USB
- Asegurarse de tener un equipo Mac que tenga instalado [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)

## <a name="create-an-apple-configurator-profile-for-devices"></a>Creación de un perfil de Apple Configurator para los dispositivos

Un perfil de inscripción de dispositivo define la configuración que se aplica a un grupo de dispositivos. Los siguientes pasos muestran cómo crear un perfil de inscripción de dispositivos para dispositivos iOS inscritos mediante Apple Configurator.

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

2. En la hoja de Intune, elija **Inscribir dispositivos** y luego elija **Inscripción de Apple**.

3. En **Administrar la configuración de inscripción de Apple Configurator**, seleccione **Perfiles AC**.

4. En la hoja **Perfiles de inscripción de Apple Configurator**, seleccione **Crear**.

5. En la hoja **Crear perfil de inscripción**, escriba un nombre y una descripción para el perfil.

6. Para **Afinidad de usuario**, elija **Inscribir sin afinidad de usuario** para garantizar que el dispositivo no está asociado a un usuario. Utilice esta afiliación para dispositivos que realizan tareas sin tener acceso a datos de usuario local. Las aplicaciones que requieren la afiliación de un usuario no funcionarán, incluida la aplicación Portal de empresa cuando se usa para instalar aplicaciones de línea de negocio.

7. Seleccione **Crear** para guardar el perfil.

## <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>Exportación del perfil como .mobileconfig a dispositivos iOS

1. En la hoja **Exportar perfil**, descargue el perfil de inscripción en [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) para insertarlo directamente como un perfil de administración en un dispositivo iOS conectado. Este método no realiza un restablecimiento de fábrica del dispositivo.

2. Prepare el dispositivo con Apple Configurator mediante los pasos siguientes.

   a. En un equipo Mac, abra Apple Configurator 2.0.

   b. Conecte el dispositivo iOS al equipo Mac con un cable USB. Cierre Fotos, iTunes y otras aplicaciones que se abren en el dispositivo cuando se detecta el dispositivo.

   c. En Apple Configurator, elija el dispositivo iOS conectado y, después, elija el botón **Agregar**. Las opciones que se pueden agregar al dispositivo aparecen en la lista desplegable. Elija **Perfiles**.

   d. Use el selector de archivos para seleccionar el archivo .mobileconfig que ha exportado desde Intune y, después, elija **Agregar**. El perfil se agrega al dispositivo. Si el dispositivo es No supervisado, la instalación requerirá la aceptación en el dispositivo.

3. Use los pasos siguientes para instalar el perfil en el dispositivo iOS. El dispositivo debe haber completado el Asistente de configuración y estar listo para usarse. Si la inscripción implica implementaciones de aplicaciones, el dispositivo debe tener un identificador de Apple configurado, porque las implementaciones de aplicaciones requerirán que disponga de un identificador de Apple con la sesión iniciada en App Store.

   a. Desbloquee el dispositivo iOS.

   b. En el cuadro de diálogo **Instalar el perfil** de **Perfil de administración**, elija **Instalar**.

   c. Proporcione la contraseña de dispositivo o el id. de Apple, si es necesario.

   d. Acepte la **advertencia** y elija **Instalar**.

   e. Acepte la **advertencia remota** y elija **Confiar**.

   f. Cuando el cuadro **Perfil instalado** confirme el perfil como Instalado, elija **Listo**.

4. En el dispositivo iOS, abra **Configuración** y vaya a **General**  > **Administración de dispositivos** > **Perfil de administración**. Confirme que aparece la instalación del perfil y compruebe las restricciones de directivas de iOS y las aplicaciones instaladas. Las aplicaciones y las restricciones de directivas pueden tardar hasta 10 minutos en aparecer en el dispositivo.

5. Distribuya los dispositivos. Ahora el dispositivo iOS está inscrito con Intune y administrado.

