---
title: Adición de directivas de configuración de aplicaciones para dispositivos Android Enterprise administrados
titleSuffix: Microsoft Intune
description: Use las directivas de configuración de aplicaciones de Microsoft Intune para proporcionar los valores de configuración cuando los usuarios ejecutan una aplicación de Google Play administrado.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9561c50e21a9667ccec3f9de3627e7a933cf0736
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72584994"
---
# <a name="add-app-configuration-policies-for-managed-android-enterprise-devices"></a>Adición de directivas de configuración de aplicaciones para dispositivos Android Enterprise administrados

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Las directivas de configuración de aplicaciones en Microsoft Intune proporcionan la configuración para las aplicaciones de Google Play administrado en dispositivos Android Enterprise administrados. El desarrollador de aplicaciones expone los valores de configuración de aplicaciones administradas por Android. Intune usa estos valores expuestos para permitir que el administrador configure las características de la aplicación. La directiva de configuración de aplicaciones se asigna a los grupos de usuarios. La configuración de directivas se usa cada vez que la aplicación la comprueba, que suele ser la primera vez que se ejecuta.

> [!NOTE]  
> No todas las aplicaciones admiten la configuración de aplicaciones. Póngase en contacto con el desarrollador de la aplicación para comprobar si la aplicación admite directivas de configuración de aplicaciones.

1. En [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), seleccione **Aplicaciones cliente** > **Directivas de configuración de aplicaciones** >  **Agregar**.
2. Escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre descriptivo para la directiva. Asígnele un nombre a las directivas para que pueda identificarlas de manera sencilla más adelante. Por ejemplo, un buen nombre de directiva es **Directiva de la aplicación Nine Work de Android Enterprise para toda la compañía**.
    - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
    - **Tipo de inscripción del dispositivo**: Seleccione **Dispositivos administrados**.
    - **Plataforma**: Seleccione **Android**.

3. Seleccione **Aplicación asociada**. Elija la aplicación para la que quiere definir una directiva de configuración de aplicaciones. Selecciónela en la lista de aplicaciones de Google Play administrado que ha aprobado y sincronizado con Intune.
4. Seleccione **Permisos**. Las configuraciones se pueden establecer con lo siguiente:

    - [Diseñador de configuraciones](#use-the-configuration-designer)
    - [Editor JSON](#enter-the-json-editor)

5. Seleccione **Aceptar** > **Agregar**.

## <a name="use-the-configuration-designer"></a>Uso del diseñador de configuración

Puede usar el Diseñador de configuración para las aplicaciones de Google Play administrado si la aplicación está diseñada para admitir las opciones de configuración. La configuración se aplica a los dispositivos inscritos en Intune. El diseñador le permite configurar opciones específicas de la configuración que expone una aplicación.

1. Seleccione **Agregar**. Seleccione la lista de valores de configuración que quiere especificar para la aplicación.

    Si usa GMail o Nine Work para su aplicación de correo electrónico, consulte [Configuración del dispositivo Android Enterprise para definir el correo electrónico](../email-settings-android-enterprise.md) para obtener más información sobre estos ajustes.

2. Para cada clave y valor de la configuración, establezca lo siguiente:

    - **Tipo de valor**: Tipo de datos del valor de configuración. Para los tipos de valor de cadena, si quiere puede elegir un perfil de certificado o una variable como tipo de valor.
    - **Valor de configuración:** Se trata del valor de la configuración. Si selecciona una variable o un certificado como **tipo de valor**, puede elegir una opción de una lista de variables o de perfiles de certificado. Si elige un certificado, el alias del certificado implementado en el dispositivo se rellenará en tiempo de ejecución.

### <a name="supported-variables-for-configuration-values"></a>Variables admitidas para los valores de configuración

Puede elegir las opciones siguientes si elige una variable como tipo de valor:

| Opción | Ejemplo |
|----|----|
| Id. del dispositivo AAD | dc0dc142-11d8-4b12-bfea-cae2a8514c82 |
| Id. de cuenta | fc0dc142-71d8-4b12-bbea-bae2a8514c81 |
| Identificador de dispositivo de Intune | b9841cd9-9843-405f-be28-b2265c59ef97 |
| Dominio | contoso.com |
| Mail | john@contoso.com |
| UPN parcial | Juan |
| Identificador de usuario | 3ec2c00f-b125-4519-acf0-302ac3761822 |
| Nombre de usuario | John Doe |
| Nombre principal de usuario | john@contoso.com |


### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>Permitir solo cuentas de organización configuradas en aplicaciones de varias identidades 

Para dispositivos Android, use los siguientes pares de clave/valor:

| **Clave** | com.microsoft.intune.mam.AllowedAccountUPNs |
|---|---|
| **Valores** | <ul><li>Uno o varios UPN delimitados por <code>;</code>.</li><li>Las cuentas permitidas son las únicas cuentas de usuario administradas que define esta clave.</li><li> Para los dispositivos inscritos en Intune, el token <code>{{userprincipalname}}</code> se puede usar para representar la cuenta de usuario inscrito.</li></ul> |

   > [!NOTE]
   > Debe usar Outlook para Android 2.2.222 y versiones posteriores, Word, Excel, PowerPoint para Android 16.0.9327.1000 y versiones posteriores o OneDrive para Android 5.28 y versiones posteriores al permitir solo cuentas de organización configuradas con varias identidades.<p></p>
   > Como administrador de Microsoft Intune, puede controlar qué cuentas de usuario se agregan a las aplicaciones de Microsoft Office en dispositivos administrados. Puede limitar el acceso solo a las cuentas de usuario de la organización permitidas y bloquear las cuentas personales en los dispositivos inscritos. Las aplicaciones auxiliares procesan la configuración de la aplicación y quitan y bloquean las cuentas no aprobadas.<p></p>

## <a name="enter-the-json-editor"></a>Editor de JSON

Algunos valores de configuración de las aplicaciones (como las que tienen tipos de agrupaciones) no se pueden configurar con el Diseñador de configuración. Para esos valores, se deberá usar el editor JSON. La configuración se proporciona a las aplicaciones de forma automática cuando se instalan.

1. En **Formato de opciones de configuración**, seleccione **Enter JSON editor** (Especificar editor JSON).
2. En el editor puede definir los valores JSON para las opciones de configuración. Puede elegir **Download JSON template** (Descargar plantilla JSON) para descargar un archivo de ejemplo que después puede configurar.
3. Elija **Aceptar** y, luego, **Agregar**.

La directiva se crea y se muestra en la lista.

Cuando se ejecuta la aplicación asignada en un dispositivo, lo hará con las opciones configuradas en la directiva de configuración de aplicaciones.

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>Preconfiguración del estado de concesión de permisos para las aplicaciones

También puede preconfigurar permisos para que las aplicaciones accedan a las características de dispositivos Android. Las aplicaciones de Android que requieren permisos de dispositivo (como el acceso a la ubicación o la cámara del dispositivo) solicitan a los usuarios de forma predeterminada que acepten o denieguen permisos.

Por ejemplo, una aplicación usa el micrófono del dispositivo. Se solicita al usuario que conceda el permiso de aplicación para usar el micrófono.

1. En [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), seleccione **Aplicaciones cliente** > **Directivas de configuración de aplicaciones** >  **Agregar**.
2. Escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre descriptivo para la directiva. Asígnele un nombre a las directivas para que pueda identificarlas de manera sencilla más adelante. Por ejemplo, un buen nombre de directiva es **Directiva de la aplicación sobre solicitud de permisos de Android Enterprise para toda la compañía**.
    - **Descripción**. escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
    - **Tipo de inscripción del dispositivo**: Seleccione **Dispositivos administrados**.
    - **Plataforma**: Seleccione **Android**.

3. Seleccione **Aplicación asociada**. Elija la aplicación para la que quiere definir una directiva de configuración. Seleccione una de la lista de aplicaciones de perfil de trabajo Android que ha aprobado y sincronizado con Intune.
4. Seleccione **Permisos** > **Agregar**. En la lista, seleccione los permisos de aplicación disponibles > **Aceptar**.
5. Seleccione una opción para cada permiso que se concede con esta directiva:
    - **Pedir confirmación**. Pedir al usuario que acepte o deniegue
    - **Concesión automática**. Aprobar automáticamente sin notificar al usuario.
    - **Denegación automática**. Denegar automáticamente sin notificar al usuario.
6. Para asignar la directiva de configuración de aplicaciones, seleccione la directiva de configuración de aplicaciones > **Asignación** > **Seleccionar grupos**. Elija los grupos de usuarios que se van a asignar > **Seleccionar**.
7. Elija **Guardar** para asignar la directiva.

## <a name="additional-information"></a>Información adicional

- [Asignación de una aplicación de Google Play administrado para dispositivos de Android Enterprise](apps-add-android-for-work.md#assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices)
- [Implementación de las opciones de configuración de la aplicación de Outlook para iOS y Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)

## <a name="next-steps"></a>Pasos siguientes

Siga [asignando](apps-deploy.md) y [supervisando](apps-monitor.md) la aplicación.
