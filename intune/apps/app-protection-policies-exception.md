---
title: Excepciones de la directiva de transferencia de datos para aplicaciones
titleSuffix: Microsoft Intune
description: Cree excepciones a la directiva de transferencia de datos de la administración de aplicaciones móviles (MAM) de Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f9015e3a-c22c-42eb-90e6-ba48dee3a41d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 01c3bfe853d87f42a6171999f6b358fb73844fb1
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72499483"
---
# <a name="how-to-create-exceptions-to-the-intune-mobile-application-management-mam-data-transfer-policy"></a>Cómo crear excepciones a la directiva de transferencia de datos de la administración de aplicaciones móviles (MAM) de Intune

Como administrador, puede crear excepciones a la directiva de transferencia de datos de la administración de aplicaciones móviles (MAM) de Intune. Una excepción le permite elegir de manera específica qué aplicaciones no administradas pueden transferir datos hacia y desde aplicaciones administradas. El departamento de TI debe confiar en las aplicaciones no administradas que incluya en la lista de excepciones. 

>[!WARNING] 
> Usted es el responsable de realizar cambios en la directiva de excepciones de transferencia de datos. Las adiciones a esta directiva permiten que las aplicaciones no administradas (aplicaciones que no administra Intune) accedan a datos protegidos por las aplicaciones administradas. Este acceso a datos protegidos puede dar lugar a pérdidas de seguridad de datos. Agregue excepciones de transferencia de datos únicamente a las aplicaciones que su organización deba usar, pero que no admitan APP (directivas de protección de aplicaciones) de Intune. Además, agregue solo excepciones a las aplicaciones que no considere que sean riesgos de pérdida de datos.

Dentro de una directiva de protección de aplicaciones de Intune, el establecimiento de **Permitir que la aplicación transfiera datos a otras aplicaciones** en **Aplicaciones administradas por directivas** significa que la aplicación solo puede transferir datos a las aplicaciones administradas por Intune. Si necesita permitir la transferencia de datos a aplicaciones concretas que no son compatibles con la directiva de Intune App Protection, puede crear excepciones a esta directiva mediante el uso de **Select apps to exempt** (Seleccionar aplicaciones exentas). Las exenciones permiten que las aplicaciones administradas por Intune invoquen aplicaciones no administradas basadas en el protocolo de dirección URL (iOS) o el nombre del paquete (Android). De manera predeterminada, Intune agrega aplicaciones nativas fundamentales a esta lista de excepciones. 

> [!NOTE]
> Las modificaciones o adiciones a las excepciones de la directiva de transferencia de datos no afectan a otras directivas de protección de datos, como las restricciones para cortar, copiar y pegar. 

## <a name="ios-data-transfer-exceptions"></a>Excepciones de transferencia de datos de iOS
Para una directiva que tenga iOS como destino, puede configurar excepciones de transferencia de datos mediante el protocolo de URL. Para agregar una excepción, compruebe la documentación proporcionada por el desarrollador de la aplicación para buscar información sobre los protocolos de URL admitidos. Para obtener más información sobre las excepciones de transferencia de datos de iOS, vea [Configuración de directivas de protección de aplicaciones de iOS: Exenciones de transferencia de datos](app-protection-policy-settings-ios.md#data-transfer-exemptions).

> [!NOTE]
> Microsoft no tiene un método para buscar manualmente el protocolo URL para crear excepciones de aplicación para aplicaciones de terceros. 

## <a name="android-data-transfer-exceptions"></a>Excepciones de transferencia de datos de Android
Para una directiva que tenga Android como destino, puede configurar excepciones de transferencia de datos mediante el nombre del paquete de aplicación. Puede comprobar la página de **Google Play Store** de la aplicación para la que quiera agregar una excepción a fin de encontrar el nombre del paquete de la aplicación. Para obtener más información sobre las excepciones de transferencia de datos de Android, vea [Configuración de directivas de protección de aplicaciones de Android: Exenciones de transferencia de datos](app-protection-policy-settings-android.md#data-transfer-exemptions).


>[!TIP]
> Puede encontrar el identificador del paquete de una aplicación dirigiéndose a la aplicación en Google Play Store. El identificador del paquete se incluye en la dirección URL de la página de la aplicación. Por ejemplo, el identificador del paquete de la aplicación Microsoft Word es **com.microsoft.office.word**.

### <a name="example"></a>Ejemplo
Si agrega el paquete **Webex** como una excepción a la directiva de transferencia de datos de MAM, los vínculos de Webex de un mensaje de correo electrónico administrado de Outlook pueden abrirse directamente en la aplicación de Webex. Se sigue restringiendo la transferencia de datos en otras aplicaciones no administradas.

- Ejemplo de **Webex** de iOS:   Para excluir la aplicación **Webex** para que se pueda invocar mediante aplicaciones administradas de Intune, debe agregar una excepción de transferencia de datos para la siguiente cadena: <code>wbx</code>
    
- Ejemplo de **Maps** de iOS:   Para excluir la aplicación nativa **Maps** para que se pueda invocar mediante aplicaciones administradas de Intune, debe agregar una excepción de transferencia de datos para la siguiente cadena: <code>maps</code>

- Ejemplo de **Webex** de Android:   Para excluir la aplicación **Webex** para que se pueda invocar mediante aplicaciones administradas de Intune, debe agregar una excepción de transferencia de datos para la siguiente cadena: <code>com.cisco.webex.meetings</code>
    
- Ejemplo de **SMS** de Android:   Para excluir la aplicación **SMS** nativa para que la puedan invocar aplicaciones administradas de Intune en diferentes aplicaciones de mensajería y dispositivos Android, debe agregar excepciones de transferencia de datos para las siguientes cadenas: 
    <code>com.google.android.apps.messaging</code>
    
    <code>com.android.mms</code>
    
    <code>com.samsung.android.messaging</code>

## <a name="next-steps"></a>Pasos siguientes

- [Crear e implementar directivas de protección de aplicaciones](app-protection-policies.md)
- [Configuración de directivas de protección de aplicaciones de iOS: Exenciones de transferencia de datos](app-protection-policy-settings-ios.md#data-transfer-exemptions)
- [Configuración de directivas de protección de aplicaciones de Android: Exenciones de transferencia de datos](app-protection-policy-settings-android.md#data-transfer-exemptions)
