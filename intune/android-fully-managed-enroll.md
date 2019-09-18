---
title: Configuración de la inscripción en Intune de dispositivos Android Enterprise totalmente administrados
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo inscribir dispositivos Android Enterprise totalmente administrados en Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7dff37794d6c58094749821748dcc96a4f36e28a
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2019
ms.locfileid: "71071621"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-fully-managed-devices-preview"></a>Configuración de la inscripción en Intune de dispositivos Android Enterprise totalmente administrados (versión preliminar)

Los dispositivos Android Enterprise totalmente administrados son dispositivos de propiedad corporativa que están asociados a un solo usuario y se usan exclusivamente para el trabajo y no para uso personal. Los administradores pueden administrar todo el dispositivo y aplicar controles de directiva que no están disponibles para perfiles de trabajo, como:
- Permitir la instalación de aplicaciones solo desde Google Play administrado
- Bloquear la desinstalación de aplicaciones administradas
- Impedir que los usuarios restablezcan los dispositivos a los valores de fábrica, etc.

Con Intune es más fácil instalar aplicaciones y aplicar una configuración a los dispositivos Android de la empresa, incluidos los dispositivos Android Enterprise totalmente administrados. Para más detalles sobre Android Enterprise, vea [Requisitos para usar dispositivos Android en una empresa](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

## <a name="technical-requirements"></a>Requisitos técnicos

Debe tener un inquilino independiente de Intune para administrar dispositivos Android Enterprise totalmente administrados. La administración de dispositivos totalmente administrados no está disponible en modo híbrido (conectado a Configuration Manager) ni en la consola de administración heredada de Silverlight.

Los dispositivos deben cumplir estos requisitos para administrarse como dispositivo Android Enterprise totalmente administrados:

- Android OS versión 5.1 y versiones posteriores.
- Los dispositivos deben ejecutar una versión de Android que tenga conectividad con Servicios de Google para móviles (GMS). Los dispositivos deben tener GMS disponible y deben ser capaces de conectarse a GMS.

No hay ninguna restricción en cuanto al fabricante u OEM del dispositivo si se cumplen los requisitos anteriores.

## <a name="set-up-android-enterprise-fully-managed-device-management"></a>Configurar la inscripción de dispositivos Android Enterprise totalmente administrados

Para configurar la administración de dispositivos Android Enterprise totalmente administrados, siga estos pasos:

1. Para prepararse para administrar dispositivos móviles, debe [establecer la entidad de administración de dispositivos móviles (MDM) en **Microsoft Intune**](mdm-authority-set.md). Este elemento solo se establece una vez, la primera vez que configura Intune para la administración de dispositivos móviles.
2. [Conecte su cuenta de inquilino de Intune a su cuenta de Android Enterprise](connect-intune-android-enterprise.md).
3. [Permitir dispositivos de usuario de propiedad corporativa](#enable-corporate-owned-user-devices)
4. [Inscribir dispositivos totalmente administrados](#enroll-the-fully-managed-devices).

### <a name="enable-corporate-owned-user-devices"></a>Permitir dispositivos de usuario de propiedad corporativa

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) y elija **Inscripción de dispositivos** > **Inscripción de Android** > **Corporate-owned, fully managed user devices (Preview)** (Dispositivos de usuario totalmente administrados de propiedad corporativa [vista previa]).
2. En **Allow users to enroll corporate-owned user devices** (Permitir a los usuarios inscribir dispositivos de usuario de propiedad corporativa), elija **Sí**.

> [!NOTE]
> Si tiene definida una directiva de acceso condicional de Azure AD que use el control de *requerir que un dispositivo se marque como compatible* y se aplique a **Todas las aplicaciones en la nube**, **Android** y **Exploradores**, debe excluir la aplicación en la nube **Microsoft Intune** de esta directiva. Esto es así porque los procesos de instalación de Android usan una pestaña de Chrome para autenticar a los usuarios durante la inscripción. Para más información, vea [Documentación sobre el acceso condicional de Azure AD](https://docs.microsoft.com/azure/active-directory/conditional-access/).

Cuando esta opción se establece en **Sí**, proporciona un token de inscripción (una cadena aleatoria) y un código QR para el inquilino de Intune. Este token de inscripción único es válido para todos los usuarios y no expira. Según el sistema operativo Android y la versión del dispositivo, puede usar el token o un código QR para inscribir el dispositivo de quiosco multimedia.

## <a name="enroll-the-fully-managed-devices"></a>Inscribir dispositivos totalmente administrados
Ya puede [inscribir sus dispositivos totalmente administrados](android-dedicated-devices-fully-managed-enroll.md).

## <a name="considerations-for-this-preview-feature"></a>Consideraciones para esta característica en vista previa
Esta versión preliminar pública incluye un conjunto básico de características para el conjunto de dispositivos Android Enterprise totalmente administrados. Queremos conocer su experiencia con las características en vista previa mediante cualquiera de los canales de comunicación actuales con el equipo (como [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas?category_id=210853)).

Esta versión preliminar admite las siguientes características para dispositivos Android Enterprise totalmente administrados:
- Inscripción de dispositivos mediante NFC, entrada de token, código QR y Zero Touch
- Configuración de dispositivos para grupos de usuarios
- Configuración y distribución de aplicaciones para grupos de usuarios


Al usar estas características en vista previa, tenga en cuenta lo siguiente:
- No se recomienda usar características en vista previa para implementaciones críticas o de producción. 
- Las características en vista previa se implementan según los estándares de producción de Microsoft Intune. Pero no todas las características de Intune están disponibles para usarlas con dispositivos Android Enterprise totalmente administrados de los usuarios. Las características en vista previa están claramente etiquetadas con "(versión preliminar)" en la consola de Intune. 
- Las características en vista previa disponen de soporte a través de los canales habituales de soporte técnico de Intune.
- En la versión preliminar no se admite la inscripción de dispositivos Android Enterprise totalmente administrados a través de Samsung Knox Mobile Enrollment. 
- No es posible usar la aplicación Portal de empresa de Intune en dispositivos Android Enterprise totalmente administrados. 
- En la versión preliminar no se admiten algunas características de Intune, como el acceso condicional, las directivas de protección y la implementación de certificados. 
- En la versión preliminar no se admite la segmentación por grupos de dispositivos de cualquier perfil o aplicación. Solo se admite la segmentación de grupos de usuarios. 
- No hay ninguna interfaz de usuario de primera clase para configurar el correo electrónico, la Wi-Fi o la VPN. Se usan directivas de configuración de aplicaciones para configurar las opciones de configuración de aplicaciones compatibles.

## <a name="next-steps"></a>Pasos siguientes
- [Agregar directivas de configuración de dispositivos Android Enterprise totalmente administrados](device-restrictions-android-for-work.md#device-owner-only)
- [Configurar directivas de configuración de aplicaciones para dispositivos Android Enterprise totalmente administrados](app-configuration-policies-use-android.md)

