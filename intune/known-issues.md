---
title: Problemas conocidos de Microsoft Intune - Azure | Microsoft Docs
description: Obtenga información sobre problemas conocidos de Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 04/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f49b5050f4ce182699f0955bed6224309a4d7c7c
ms.sourcegitcommit: c1631ad8feba6c6fd03698ab20836b2e5d8a78d2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/12/2018
ms.locfileid: "34073842"
---
# <a name="known-issues-in-microsoft-intune"></a>Problemas conocidos de Microsoft Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Consulte este artículo para obtener información sobre los problemas conocidos de Microsoft Intune.

Si quiere notificar un error que no aparece aquí, [abra una solicitud de soporte técnico](get-support.md).

Si quiere solicitar una nueva característica para Intune, considere la posibilidad de presentar un informe en el sitio [Uservoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console).

## <a name="migration"></a>Migración

### <a name="intune-legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>Las características del cliente de equipo heredado de Intune solo están disponibles en la consola de Silverlight

La capacidad para administrar Windows 10 en Intune en Azure Portal está disponible a través de la inscripción de MDM de Windows. Para más información, vea [Consola de Intune en Azure y cliente de equipo de Intune heredado](https://docs.microsoft.com/intune-classic/deploy-use/intune-on-azure).

### <a name="groups-created-by-intune-during-migration-might-affect-functionality-of-other-microsoft-products"></a>Los grupos creados por Intune durante la migración pueden afectar a la funcionalidad de otros productos de Microsoft

Al migrar de Intune a Azure Portal, es posible que vea un nuevo grupo denominado **All Users - b0b08746-4dbe-4a37-9adf-9e7652c0b421**. Este grupo contiene todos los usuarios de Azure Active Directory, no solo los usuarios con licencia de Intune. Este uso podría causar problemas con otros productos de Microsoft si espera que algunos usuarios nuevos o existentes no sean miembros de los grupos.

### <a name="status-blades-for-migrated-policies-do-not-work"></a>Las hojas de estado para directivas migradas no funcionan.

No se puede ver la información de estado de las directivas que se migraron del portal clásico de Azure a Azure Portal. En cambio, aún puede ver informes de estas directivas en el portal clásico. Para ver la información de estado de las directivas de configuración migradas, vuelva a crearlas en Azure Portal.

## <a name="apps"></a>Aplicaciones


### <a name="multiple-app-install-prompts-for-certain-vpp-apps"></a>Varios mensajes de instalación de aplicación para determinadas aplicaciones de VPP
Es posible que vea varios mensajes de instalación de aplicación para determinadas aplicaciones de VPP que ya están instaladas en dispositivos de usuario final. Este problema se produce si tiene la opción **Actualizaciones automáticas de la aplicación** establecida en **Activado** para el token de VPP que ha cargado en Intune Azure Portal.    

Para solucionar este problema, puede deshabilitar la opción **Actualizaciones automáticas de la aplicación** para el token de VPP. Para ello, en Azure Portal, abra Microsoft Intune. En Intune, seleccione **Aplicaciones móviles** > **Tokens de VPP de iOS**. Luego seleccione el token de VPP que ha implementado la aplicación afectada y seleccione **Editar** > **Actualizaciones automáticas de la aplicación** > **Desactivado** > **Guardar**. También puede detener la implementación de la aplicación afectada como aplicación de VPP, lo que detiene los mensajes.    

Se trata de un problema conocido de la versión actual. En una próxima corrección se resolverá este problema. Una vez implementada la corrección, los usuarios ya no verán varios mensajes de instalación de aplicación.

### <a name="ios-volume-purchased-apps-only-available-in-default-intune-tenant-language"></a>Las aplicaciones compradas por volumen de iOS solo están disponibles en el idioma predeterminado del inquilino de Intune
Las aplicaciones compradas por volumen de iOS se muestran y solo pueden asignarse para el mismo código de país que su cuenta de Intune. Intune solo sincroniza aplicaciones desde la misma configuración regional de iTunes que el código de país de la cuenta de inquilino de Intune. Por ejemplo, si compra una aplicación que solo está disponible en una tienda de los Estados Unidos, pero su cuenta de Intune es alemana, Intune no mostrará esa aplicación.

### <a name="multiple-copies-of-the-same-ios-volume-purchase-program-are-uploaded"></a>Se cargan varias copias del mismo programa de compra por volumen de iOS
No haga clic en el botón **Cargar** varias veces desde el mismo token de PCV. Esto provocará que se carguen tokens de PCV duplicados y que las aplicaciones se sincronicen varias veces para el mismo token de PCV.

### <a name="some-managed-browser-traffic-not-routed-through-azure-app-proxy----2463492---"></a>Parte del tráfico de Managed Browser no se enruta a través de Azure App Proxy <!-- 2463492 -->
Hay un problema conocido con la integración de Managed Browser y App Proxy en el que cierto tráfico terciario (como llamadas AJAX o JavaScript) no se enrutan a través de Azure App Proxy. Se trata de un problema conocido de la versión actual.  

<!-- ## Groups -->

## <a name="device-configuration"></a>Configuración de los dispositivos

### <a name="you-cannot-save-a-windows-information-protection-policy-for-some-devices"></a>No se puede guardar una directiva de Windows Information Protection para algunos dispositivos.

Para dispositivos no inscritos con Intune, solo se puede especificar un dominio principal en el campo **Identidad corporativa** de la configuración de una directiva de Windows Information Protection.
Si se agregan dominios adicionales (mediante **Configuración avanzada** > **Perímetro de red** > **Agregar un dominio protegido**), no se puede guardar la directiva. El mensaje de error que se ve cambiará pronto para ser más preciso.

### <a name="cisco-anyconnect-and-cisco-legacy-anyconnect-vpn-client-support---ios"></a>Compatibilidad de cliente con VPN de Cisco AnyConnect y Cisco Legacy AnyConnect - iOS

En dispositivos iOS, la integración del control de acceso a la red (NAC) no funciona con el nuevo cliente Cisco AnyConnect. Estamos trabajando con Cisco para proporcionar integración de NAC.

La [creación de perfiles de VPN en Intune](vpn-settings-ios.md) proporciona más detalles sobre los clientes Cisco AnyConnect y Cisco Legacy AnyConnect.

### <a name="using-the-numeric-password-type-with-macos-sierra-devices"></a>Uso del tipo de contraseña numérica con los dispositivos macOS Sierra

En la actualidad, si selecciona **Numérico** como **Tipo de contraseña requerida** en un perfil de restricciones de dispositivos para dispositivos macOS Sierra, se aplica como **Alfanumérico**. Si desea utilizar una contraseña numérica con estos dispositivos, no configure esta opción.
Este problema podría corregirse en una versión futura de macOS.

Para obtener más información sobre estas opciones, vea [Configuración de restricciones de dispositivos macOS en Microsoft Intune](device-restrictions-macos.md).

## <a name="compliance"></a>Cumplimiento

### <a name="compliance-policies-from-intune-do-not-show-up-in-new-console"></a>Las directivas de cumplimiento de Intune no aparecen en la nueva consola.

Las directivas de cumplimiento que se crearon en el portal clásico se migran, pero no se muestran en Azure Portal debido a los cambios de diseño en Azure Portal. Las directivas de cumplimiento creadas en el portal de Intune clásico siguen siendo aplicables, pero debe verlas y editarlas en el portal clásico.

Además, las nuevas directivas de cumplimiento creadas en Azure Portal no están visibles en el portal clásico.

Para obtener más información, consulte [¿Qué es el cumplimiento del dispositivo?](device-compliance.md)

<!-- ## Enrollment -->


## <a name="data-protection"></a>Protección de datos

### <a name="ios-app-protection-policies"></a>Directivas de protección de aplicaciones iOS

Puede definir las [directivas de protección de aplicaciones para iOS](app-protection-policy-settings-ios.md) que están disponibles para usuarios en dispositivos administrados a través de la administración de aplicaciones móviles (MAM) sin inscripción. Debido a un error temporal, solo puede definir estas directivas para las versiones de iOS con un solo punto decimal en lugar de varios puntos decimales. En lugar de establecer una versión mínima de iOS 10.3.1, la establece para iOS 10.3. Esto se resolverá en una actualización disponible próximamente del SDK de iOS.


## <a name="administration-and-accounts"></a>Administración y cuentas

Los administradores globales (también denominados administradores de inquilinos) pueden seguir realizando tareas de administración cotidianas sin una licencia independiente de Intune o Enterprise Mobility Suite (EMS). Sin embargo, para usar el servicio, por ejemplo para inscribir sus dispositivos, un dispositivo de la empresa o para usar el Portal de empresa de Intune, necesitan una licencia de Intune o EMS.

<!-- ## Additional items -->
