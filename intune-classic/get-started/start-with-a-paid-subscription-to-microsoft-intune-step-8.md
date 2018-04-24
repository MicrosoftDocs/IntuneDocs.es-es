---
title: Permitir la inscripción de dispositivos
description: Establezca la entidad de MDM y habilite la inscripción para dispositivos iOS, Windows, Android y Mac.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 02/14/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5d3215e7-0a5c-44bd-afb0-aeafce98c43f
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1b09545e99f18815e690ad224e11e772e8911c8a
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="enable-enrollment-for-mobile-devices"></a>Habilitar la inscripción de dispositivos móviles

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

En este tema se describe el procedimiento que deben seguir los administradores de Intune para habilitar la inscripción de dispositivos móviles. Para obtener ayuda sobre el uso de Intune en el teléfono, consulte el [uso de dispositivos administrados para realizar el trabajo](https://docs.microsoft.com/intune-user-help/company-portal-frequently-asked-questions).

Para configurar la administración de dispositivos móviles con Intune, primero debe establecer la *autoridad de administración de dispositivos móviles*, que identifica el servicio que puede administrar los dispositivos asociados a su cuenta. En esta guía se asume que usará el servicio de Intune en lugar de System Center Configuration Manager. Una vez establecida la entidad de MDM, puede habilitar la administración para plataformas de dispositivos e inscribir sus dispositivos con la aplicación del Portal de empresa.

## <a name="enable-device-enrollment"></a>Permitir la inscripción de dispositivos

1. **Convertir Intune en la entidad de administración de dispositivos móviles** En la [consola de administración de Intune](https://manage.microsoft.com/), pulse **Administración** > **Administración de dispositivos móviles** y, después, **Establecer entidad de MDM** en **Tareas**.  

2. Elija **Sí** en el cuadro de diálogo Entidad de MDM.

    ![Consola de administración. Establecer MDM en Intune](../media/intune-mdm-authority.png)

## <a name="choose-how-to-enroll-devices"></a>Elegir cómo inscribir los dispositivos

Intune puede administrar dispositivos de diferentes maneras, dependiendo de los requisitos de su empresa. "Traiga su propio dispositivo" (BYOD), dispositivos corporativos, "elija su propio dispositivo" (CYOD) y los dispositivos de pantalla completa son unos pocos escenarios de inscripción disponibles.

Siga estos pasos para [elegir cómo inscribir dispositivos](choose-how-to-enroll-devices1.md).

## <a name="enable-mdm-for-your-device-platform"></a>Habilitación de MDM para su plataforma de dispositivo
La inscripción debe estar habilitada para dispositivos iOS, Mac y Android for Work que establecen una relación entre el proveedor de la plataforma y el inquilino de Intune. Los dispositivos Windows y Android no necesitan pasos adicionales, pero puede simplificar la inscripción de dispositivos Windows para sus usuarios mediante la creación de una entrada especial de DNS en el Registro.

Habilite la inscripción de dispositivos para la plataforma de dispositivos que desee administrar. Los requisitos necesarios varían según la plataforma:

- [iOS y macOS](/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)
- [Windows 10 y Windows Phone](/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune)
- [PC Windows](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune) (cliente de software de Intune)
- [Android for Work](/intune-classic/deploy-use/set-up-android-for-work)

Después de habilitar la inscripción, los usuarios pueden descargar la aplicación del Portal de empresa en sus dispositivos y completar el proceso de inscripción de dispositivos.

### <a name="enable-company-owned-device-enrollment"></a>Habilitar la inscripción de dispositivos corporativos
También puede habilitar diversos escenarios de [inscripción de dispositivos corporativos](/intune-classic/deploy-use/manage-corporate-owned-devices), como por ejemplo:
- [Programa de inscripción de dispositivos de Apple](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune)
- [Inscripción de Apple Configurator mediante el Asistente de configuración](/intune-classic/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune)
- [Inscripción directa de Apple Configurator](/intune-classic/deploy-use/ios-direct-enrollment-in-microsoft-intune)
- [Administrador de inscripción de dispositivos](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

### <a name="next-steps"></a>Pasos siguientes
Enhorabuena. Acaba de completar el último paso de la *Guía de inicio rápido de Intune*. Ahora que ha finalizado la configuración inicial, puede habilitar funciones de MDM adicionales.

>[!div class="step-by-step"]
>[&larr;**Inscribir dispositivos**](./start-with-a-paid-subscription-to-microsoft-intune-step-8.md)      [**Tareas posteriores a la configuración** &rarr;](./post-configuration-tasks.md)  
