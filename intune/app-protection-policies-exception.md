---
title: Excepciones de la directiva de transferencia de datos para aplicaciones
titleSuffix: Azure portal
description: "Cree excepciones a la directiva de transferencia de datos de la administración de aplicaciones móviles (MAM) de Intune."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/20/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f9015e3a-c22c-42eb-90e6-ba48dee3a41d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b24060d1b042322f1c7607aba7266421a0effc52
ms.sourcegitcommit: 80a2eefc1896a42cc2bc16be23093d1abf58b088
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/27/2018
---
# <a name="how-to-create-exceptions-to-the-intune-mobile-application-management-mam-data-transfer-policy"></a>Cómo crear excepciones a la directiva de transferencia de datos de la administración de aplicaciones móviles (MAM) de Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Como administrador, puede crear excepciones a la directiva de transferencia de datos de la administración de aplicaciones móviles (MAM) de Intune. Una excepción le permite elegir de manera específica qué aplicaciones no administradas pueden transferir datos hacia y desde aplicaciones administradas. Las aplicaciones no administradas que incluya en la lista de excepciones deben ser de confianza para el departamento de TI. 

>[!WARNING] 
> Usted es el responsable de realizar cambios en la directiva de excepciones de transferencia de datos. Las adiciones a esta directiva permiten que las aplicaciones no administradas (aplicaciones que no administra Intune) accedan a datos protegidos por las aplicaciones administradas. Este acceso a datos protegidos puede dar lugar a pérdidas de seguridad de datos. Agregue excepciones de transferencia de datos únicamente a las aplicaciones que su organización deba usar, pero que no admitan APP (directivas de protección de aplicaciones) de Intune. Además, agregue solo excepciones a las aplicaciones que no considere que sean riesgos de pérdida de datos.

Esta característica se aplica al crear una directiva de protección de aplicaciones de Intune con la transferencia de datos establecida en **Managed apps only** (Solo aplicaciones administradas). Aparte de las excepciones que cree, si la directiva de transferencia de datos se establece en **Managed apps only** (Solo aplicaciones administradas), la transferencia de datos seguirá estando limitada a las aplicaciones que se administran mediante Intune. Puede crear las restricciones mediante protocolos (iOS) o paquetes (Android).

Puede configurar esta característica para habilitar excepciones a la **restricción de transferencia de datos** de la directiva de protección de aplicaciones MAM de Intune. Esta directiva solo es necesaria si quiere permitir que los datos se transfieran a una aplicación que no admita las directivas de protección de aplicaciones de Intune. Esta directiva permite que las aplicaciones administradas por Intune, con la configuración de transferencia de datos establecida en **Managed apps only** (Solo aplicaciones administradas), invoquen aplicaciones no administradas en función del protocolo de URL (iOS) o el nombre de paquete (Android). Intune agrega aplicaciones nativas fundamentales a la lista predeterminada de excepciones. 

## <a name="ios-data-transfer-exceptions"></a>Excepciones de transferencia de datos de iOS
Para una directiva que tenga iOS como destino, puede configurar excepciones de transferencia de datos mediante el protocolo de URL. Para agregar una excepción, compruebe la documentación proporcionada por el desarrollador de la aplicación para buscar información sobre los protocolos de URL admitidos. Para obtener más información sobre las excepciones de transferencia de datos de iOS, consulte la sección [Exenciones de transferencia de datos del artículo Configuración de directivas de protección de aplicaciones de iOS](app-protection-policy-settings-ios.md#data-transfer-exemptions).

## <a name="android-data-transfer-exceptions"></a>Excepciones de transferencia de datos de Android
Para una directiva que tenga Android como destino, puede configurar excepciones de transferencia de datos mediante el nombre del paquete de aplicación. Puede comprobar la página de **Google Play Store** de la aplicación para la que quiera agregar una excepción a fin de encontrar el nombre del paquete de la aplicación. Para obtener más información sobre las excepciones de transferencia de datos de Android, consulte la sección [Exenciones de transferencia de datos del artículo Configuración de directivas de protección de aplicaciones de Android](app-protection-policy-settings-android.md#data-transfer-exemptions).

### <a name="example"></a>Ejemplo
Si agrega el paquete **Webex** como una excepción a la directiva de transferencia de datos de MAM, los vínculos de Webex de un mensaje de correo electrónico administrado de Outlook pueden abrirse directamente en la aplicación de Webex. Se sigue restringiendo la transferencia de datos en otras aplicaciones no administradas.

- Ejemplo de **Webex** de iOS: para excluir la aplicación **Webex** para que se pueda invocar mediante aplicaciones administradas de Intune, debe agregar una excepción de transferencia de datos para la siguiente cadena: <code>wbx</code>.

- Ejemplo de **Webex** de Android: para excluir la aplicación **Webex** para que se pueda invocar mediante aplicaciones administradas de Intune, debe agregar una excepción de transferencia de datos para la siguiente cadena: <code>com.cisco.webex.meetings</code>. 

## <a name="next-steps"></a>Pasos siguientes

- [Crear e implementar directivas de protección de aplicaciones](app-protection-policies.md)
- [Configuración de directivas de protección de aplicaciones de iOS: Exenciones de transferencia de datos](app-protection-policy-settings-ios.md#data-transfer-exemptions)
- [Configuración de directivas de protección de aplicaciones de Android: Exenciones de transferencia de datos](app-protection-policy-settings-android.md#data-transfer-exemptions)
