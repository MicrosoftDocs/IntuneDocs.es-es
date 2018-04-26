---
title: Establecer la entidad de administración de dispositivos móviles
titlesuffix: Microsoft Intune
description: Establezca la entidad de administración de dispositivos móviles en Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e15e1678fa93269eb650f8a5684091b430ebf1cd
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="set-the-mobile-device-management-authority"></a>Establecer la entidad de administración de dispositivos móviles

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

La configuración de la entidad de administración de dispositivos móviles (MDM) determina cómo se administran los dispositivos. Como administrador de TI, debe establecer una entidad de MDM antes de que los usuarios puedan inscribir dispositivos para la administración.

Las configuraciones posibles son:

- **Intune independiente**: administración solo en la nube, que se configura mediante el portal de Azure. Incluye el conjunto completo de funcionalidades que ofrece Intune. [Establecer la entidad de MDM en la consola de Intune](#set-mdm-authority-to-intune).

- **Intune híbrido**: integración de la solución de nube de Intune con System Center Configuration Manager. Intune se configura mediante la consola de Configuration Manager. [Establecer la entidad de MDM en Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription).

- **Administración de dispositivos móviles para Office 365**: integración de Office 365 con la solución de nube de Intune. Intune se configura desde el Centro de administración de Office 365. Incluye un subconjunto de las funcionalidades que están disponibles con la versión independiente de Intune. Establecer la entidad de MDM en el Centro de administración de Office 365.

> [!IMPORTANT]
> En la versión 1610 o posterior de Configuration Manager y en la versión 1705 de Microsoft Intune, puede cambiar la entidad de MDM sin tener que ponerse en contacto con el soporte técnico de Microsoft y sin necesidad de anular la inscripción de los dispositivos administrados existentes e inscribirlos de nuevo. Para más información, consulte [Qué hacer si se elige la configuración incorrecta de la entidad de MDM](/intune-classic/deploy-use/prerequisites-for-enrollment#what-to-do-if-you-choose-the-wrong-mdm-authority-setting).

## <a name="set-mdm-authority-to-intune"></a>Establecimiento de la entidad de MDM en Intune

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. Seleccione el banner de color naranja para abrir el ajuste **Entidad de administración de dispositivos móviles**.
4. En **Entidad de administración de dispositivos móviles**, elija la entidad de MDM entre las opciones siguientes:
   - **Entidad de MDM de Intune**
   - **Entidad de MDM Configuration Manager**
   - **Ninguno**

   ![Captura de pantalla de la sección para configurar Intune como la entidad de administración de dispositivos móviles](media/set-mdm-auth.png)

   Un mensaje indica que ha configurado correctamente su entidad de MDM en Intune.

## <a name="enable-device-enrollment"></a>Permitir la inscripción de dispositivos

Al establecer Intune como entidad de MDN, los usuarios pueden inscribir sus dispositivos personales y acceder a recursos como el correo siguiendo uno de estos métodos: instalando Portal de empresa (iOS, macOS y Android), agregando las credenciales profesionales (Windows) o bien accediendo al sitio web de Portal de empresa (iOS, Android y macOS).

Las plataformas presentan los requisitos siguientes para habilitar o simplificar la inscripción:
- **iOS** (obligatorio)[: obtener un certificado push de MDM de Apple](apple-mdm-push-certificate-get.md) y después [habilitar la inscripción para dispositivos iOS propiedad de la empresa](ios-enroll.md) (opcional).
- **Android** (opcional)[: habilitar perfiles profesionales de Android](android-enroll.md)
- **Windows** (opcional): habilitar la [inscripción automática](windows-enroll.md) o la [inscripción masiva](windows-bulk-enroll.md)
- **macOS** (obligatorio): [Obtener un certificado push MDM de Apple](apple-mdm-push-certificate-get.md).


## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Limpieza de dispositivos móviles tras la expiración del certificado MDM

El certificado MDM se renueva automáticamente cuando los dispositivos móviles se comunican con el servicio de Intune. Si se borran los dispositivos móviles o estos no pueden comunicarse con el servicio de Intune durante un tiempo, el certificado MDM no se renovará. El dispositivo se quita del portal de Azure 180 días después de que expire el certificado MDM.
