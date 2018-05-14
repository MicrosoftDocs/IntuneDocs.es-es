---
title: Configuración de la inscripción de dispositivos macOS
titlesuffix: Microsoft Intune
description: Descubra cómo configurar la inscripción de dispositivos macOS en Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4f8cddb69ac85e45acde8a846df3b5413c3b75bf
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
---
# <a name="set-up-enrollment-for-macos-devices-in-intune"></a>Configuración de la inscripción de dispositivos macOS en Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune le permite administrar dispositivos macOS. Para habilitar la administración de dispositivos, los usuarios deben inscribir sus dispositivos dirigiéndose al [sitio web del portal de empresa](http://portal.manage.microsoft.com) y seguir las indicaciones. Una vez que los dispositivos macOS estén bajo su administración, puede [crear una configuración personalizada para dispositivos macOS](custom-settings-macos.md). Próximamente habrá mas funciones.

## <a name="prerequisites"></a>Requisitos previos

Complete los siguientes requisitos previos antes de configurar la inscripción de dispositivos macOS:

- [Configurar dominios](custom-domain-name-configure.md)
- [Establecer la entidad de MDM](mdm-authority-set.md)
- [Crear grupos](https://docs.microsoft.com/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [Configurar el Portal de empresa](company-portal-app.md)
- Asignar licencias de usuario en el [Portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Obtener un certificado push MDM de Apple](apple-mdm-push-certificate-get.md)

## <a name="user-owned-ios-devices-byod"></a>Dispositivos iOS corporativos (BYOD)

Puede permitir que los usuarios inscriban sus dispositivos personales para la administración de Intune. Esto se conoce como "Bring Your Own Device" o BYOD. Tras completar los requisitos previos y asignar licencias a los usuarios, estos podrán descargar la aplicación Portal de empresa para macOS en la tienda de aplicaciones y seguir las instrucciones de inscripción.

## <a name="company-owned-ios-devices"></a>Dispositivos iOS propiedad de la empresa
Para las organizaciones que adquieran dispositivos para sus usuarios, Intune admite la inscripción de dispositivos macOS propiedad de la empresa con una cuenta de [administrador de inscripción de dispositivos](device-enrollment-manager-enroll.md).

## <a name="set-up-macos-enrollment"></a>Configuración de la inscripción de macOS

De manera predeterminada, Intune ya permite la inscripción de dispositivos macOS.

Para bloquear la inscripción de dispositivos macOS, vea [Set device type restrictions](enrollment-restrictions-set.md) (Establecer restricciones de tipos de dispositivo).

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Indique a los usuarios cómo inscribir sus dispositivos para acceder a recursos de la empresa.

Indique a sus usuarios finales que vayan al [sitio web del Portal de empresa](https://portal.manage.microsoft.com) y sigan las indicaciones para inscribir sus dispositivos. También puede enviarles un vínculo sobre los pasos de inscripción en línea: [Inscriba el dispositivo macOS en Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos).

Para más información acerca de otras tareas de usuario final, consulte estos artículos:

- [Recursos sobre la experiencia del usuario final con Microsoft Intune](end-user-educate.md)
- [Usar un dispositivo macOS con Intune](/intune-user-help/using-your-macos-device-with-intune)

## <a name="enroll-virtual-macos-machines-for-testing"></a>Inscribir máquinas virtuales macOS para realizar pruebas

> [!NOTE]
> Las máquinas virtuales macOS solo se pueden usar para efectuar pruebas. No las use como dispositivos de producción para los usuarios finales. 

Las máquinas virtuales macOS se pueden inscribir con Parallels Desktop o con VMware Fusion para realizar pruebas en ellas. 

Si se usa Parallels Desktop, hay que indicar el tipo de hardware y el número de serie de las máquinas virtuales para que Intune pueda reconocerlas. Siga las instrucciones de Parallels para [establecer el tipo de hardware](http://kb.parallels.com/123594) y el [número de serie](http://kb.parallels.com/123455) con objeto de configurar los valores necesarios para las pruebas. Es recomendable que el tipo de hardware del dispositivo donde se ejecutan las máquinas virtuales y el tipo de hardware de las máquinas virtuales que vaya a crear sea el mismo. El tipo de hardware se encuentra en **menú Apple** > **Acerca de este Mac** > **Información del Sistema** > **Identificador del modelo**. 

En el caso de VMware Fusion, hay que [editar el archivo .vmx](https://kb.vmware.com/s/article/1014782) para establecer el modelo de hardware y el número de serie de la máquina virtual. Es recomendable que el tipo de hardware del dispositivo donde se ejecutan las máquinas virtuales y el tipo de hardware de las máquinas virtuales que vaya a crear sea el mismo. El tipo de hardware se encuentra en **menú Apple** > **Acerca de este Mac** > **Información del Sistema** > **Identificador del modelo**. 

## <a name="user-approved-enrollment"></a>Inscripción aprobada por el usuario

La inscripción de MDM aprobada por el usuario es un tipo de inscripción de macOS que se puede usar para administrar cierta configuración relacionada con la seguridad. Para más información, consulte la [documentación de soporte técnico de Apple](https://support.apple.com/HT208019).

Para ser aprobado por el usuario, el usuario final debe, tras inscribirse con el Portal de empresa de macOS, proporcionar manualmente aprobación mediante Preferencias del sistema. En el Portal de empresa de macOS se explica cómo hacerlo para usuarios con macOS 10.13.2 y posterior.

Para averiguar si un dispositivo es aprobado por el usuario, vaya al portal de Intune y, a continuación, elija **Dispositivos** > **Todos los dispositivos**> elija el dispositivo > **Hardware**. Compruebe el campo **Aprobado por usuario**.