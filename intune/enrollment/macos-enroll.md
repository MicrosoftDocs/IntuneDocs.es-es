---
title: Configuración de la inscripción de dispositivos macOS
titleSuffix: Microsoft Intune
description: Descubra cómo configurar la inscripción de dispositivos macOS en Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/13/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ec0e22c55e337d6ffe9b617c3858982859995b77
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722441"
---
# <a name="set-up-enrollment-for-macos-devices-in-intune"></a>Configuración de la inscripción de dispositivos macOS en Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune le permite administrar dispositivos macOS para proporcionar a los usuarios acceso a las aplicaciones y el correo electrónico de empresa.

Como administrador de Intune, puede configurar la inscripción para dispositivos macOS propiedad de la empresa y dispositivos macOS de propiedad personal ("Bring Your Own Device" o BYOD). 

## <a name="prerequisites"></a>Requisitos previos

Complete los siguientes requisitos previos antes de configurar la inscripción de dispositivos macOS:

- [Asegúrese de que el dispositivo es apto para la inscripción de dispositivos de Apple](https://support.apple.com/en-us/HT204142#eligibility).
- [Configurar dominios](../fundamentals/custom-domain-name-configure.md)
- [Establecer la entidad de MDM](../fundamentals/mdm-authority-set.md)
- [Crear grupos](../fundamentals/groups-add.md)
- [Configurar el Portal de empresa](../apps/company-portal-app.md)
- Asignación de licencias de usuario en el [Centro de administración de Microsoft 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Obtener un certificado push MDM de Apple](../enrollment/apple-mdm-push-certificate-get.md)

## <a name="user-owned-macos-devices-byod"></a>Dispositivos macOS propiedad del usuario (BYOD)

Puede permitir que los usuarios inscriban sus dispositivos personales para la administración de Intune. Esto se conoce como "Bring Your Own Device" o BYOD. Una vez completados los requisitos previos y asignadas las licencias a los usuarios, estos pueden inscribir sus dispositivos de estas maneras:
- visitando el [sitio web Portal de empresa](https://portal.manage.microsoft.com) o
- descargando la aplicación de Portal de empresa.
También puede enviarles un vínculo sobre los pasos de inscripción en línea: [Inscriba el dispositivo macOS en Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos).

Para más información acerca de otras tareas de usuario final, consulte estos artículos:

- [Recursos sobre la experiencia del usuario final con Microsoft Intune](../fundamentals/end-user-educate.md)
- [Usar un dispositivo macOS con Intune](/intune-user-help/using-your-macos-device-with-intune)

## <a name="company-owned-macos-devices"></a>Dispositivos macOS propiedad de la empresa
Para las organizaciones que adquieran dispositivos para sus usuarios, Intune admite los métodos de inscripción de dispositivos macOS propiedad de la empresa siguientes:
- [Programa de inscripción de dispositivos (DEP) de Apple](device-enrollment-program-enroll-macos.md): Las organizaciones pueden adquirir dispositivos macOS a través del Programa de inscripción de dispositivos (DEP) de Apple. DEP permite implementar un perfil de inscripción "de forma inalámbrica" que traiga los dispositivos a la administración.
- [Administrador de inscripción de dispositivos (DEM)](device-enrollment-manager-enroll.md): puede usar una cuenta de DEM para inscribir hasta 1000 dispositivos.

## <a name="block-macos-enrollment"></a>Bloqueo de la inscripción de macOS
De forma predeterminada, Intune permite la inscripción de dispositivos macOS. Para bloquear la inscripción de dispositivos macOS, vea [Set device type restrictions](enrollment-restrictions-set.md) (Establecer restricciones de tipos de dispositivo).

## <a name="enroll-virtual-macos-machines-for-testing"></a>Inscribir máquinas virtuales macOS para realizar pruebas

> [!NOTE]
> Las máquinas virtuales macOS solo se pueden usar para efectuar pruebas. No las use como dispositivos de producción para los usuarios finales. 

Las máquinas virtuales macOS se pueden inscribir con Parallels Desktop o con VMware Fusion para realizar pruebas en ellas. 

Si se usa Parallels Desktop, hay que indicar el tipo de hardware y el número de serie de las máquinas virtuales para que Intune pueda reconocerlas. Siga las instrucciones de Parallels para establecer el tipo de hardware y el [número de serie](http://kb.parallels.com/123455) con objeto de configurar los valores necesarios para las pruebas. Es recomendable que el tipo de hardware del dispositivo donde se ejecutan las máquinas virtuales y el tipo de hardware de las máquinas virtuales que vaya a crear sea el mismo. El tipo de hardware se encuentra en **menú Apple** > **Acerca de este Mac** > **Información del Sistema** > **Identificador del modelo**. 

En el caso de VMware Fusion, hay que [editar el archivo .vmx](https://kb.vmware.com/s/article/1014782) para establecer el modelo de hardware y el número de serie de la máquina virtual. Es recomendable que el tipo de hardware del dispositivo donde se ejecutan las máquinas virtuales y el tipo de hardware de las máquinas virtuales que vaya a crear sea el mismo. El tipo de hardware se encuentra en **menú Apple** > **Acerca de este Mac** > **Información del Sistema** > **Identificador del modelo**. 

## <a name="user-approved-enrollment"></a>Inscripción aprobada por el usuario

La inscripción de MDM aprobada por el usuario es un tipo de inscripción de macOS que se puede usar para administrar cierta configuración relacionada con la seguridad. Para más información, consulte la [documentación de soporte técnico de Apple](https://support.apple.com/HT208019).

Para ser aprobado por el usuario, el usuario final debe, tras inscribirse con el Portal de empresa de macOS, proporcionar manualmente aprobación mediante Preferencias del sistema. En el Portal de empresa de macOS se explica cómo hacerlo para usuarios con macOS 10.13.2 y posterior.

Para averiguar si un dispositivo es aprobado por el usuario, vaya al portal de Intune y, a continuación, elija **Dispositivos** > **Todos los dispositivos**> elija el dispositivo > **Hardware**. Compruebe el campo **Aprobado por usuario**.

## <a name="next-steps"></a>Pasos siguientes

Una vez que los dispositivos macOS se hayan inscrito, puede [crear una configuración personalizada para dispositivos macOS](../configuration/custom-settings-macos.md).
