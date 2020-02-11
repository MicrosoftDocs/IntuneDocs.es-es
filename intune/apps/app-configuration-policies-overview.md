---
title: Directivas de configuración de aplicaciones para Microsoft Intune
titleSuffix: ''
description: Obtenga información sobre cómo usar las directivas de configuración de aplicaciones en un dispositivo iOS o Android en Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8c9dc1d95806bcddf423bb4d92dbdf4961c15809
ms.sourcegitcommit: b0d683917af83170f85022b270270d8ced8e301c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76812477"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>Directivas de configuración de aplicaciones para Microsoft Intune

Las directivas de configuración de aplicaciones pueden ayudar a eliminar problemas de configuración de aplicaciones, ya que permiten asignar opciones de configuración a una directiva que se asigna a los usuarios finales antes de que ejecuten la aplicación. La configuración se proporciona de forma automática al configurar la aplicación en el dispositivo de los usuarios finales, que no tendrán que realizar ninguna acción. Los valores de configuración son únicos para cada aplicación. 

Puede crear y usar directivas de configuración de aplicaciones para proporcionar valores de configuración para aplicaciones iOS o Android. Estos valores de configuración permiten personalizar una aplicación mediante el uso de la configuración y administración de aplicaciones. Los valores de la directiva de configuración se usan cada vez que la aplicación los comprueba, que suele ser la primera vez que se ejecuta. 

Por ejemplo, para una aplicación podría ser necesario especificar uno de estos detalles:

- Un número de puerto personalizado
- Configuración de idioma
- Configuración de seguridad
- Configuración de marca, como un logotipo de empresa

Si en su lugar los usuarios finales tuvieran que escribir esta configuración, podrían hacerlo de forma incorrecta. Las directivas de configuración de aplicaciones pueden ayudar a proporcionar coherencia en una empresa y reducir las llamadas al departamento de soporte técnico de los usuarios finales que intentan configurar las opciones por sí solos. Mediante el uso de directivas de configuración de aplicaciones, la adopción de nuevas aplicaciones puede ser más fácil y rápida.

Los desarrolladores de la aplicación deciden en última instancia los parámetros de configuración disponibles. Se debe revisar la documentación del proveedor de la aplicación para ver si una aplicación admite la configuración y qué configuraciones están disponibles. En algunas aplicaciones, Intune rellenará las opciones de configuración disponibles. 

> [!NOTE]
> En Google Play Store administrado, las aplicaciones que admiten la configuración se marcarán como tales:
> 
> ![Captura de pantalla de una aplicación configurada](./media/app-configuration-policies-overview/configured-app.png)
>
> Al usar Dispositivos administrados como Tipo de inscripción para dispositivos Android, solo verá las aplicaciones de [Google Play Store administrado](https://play.google.com/work), no de [Google Play Store](https://play.google.com/store/apps). Google Play Store administrado, que también se denomina Android for Work (AfW) y Android Enterprise, son las aplicaciones del perfil de trabajo que contienen las versiones de la aplicación que admiten la configuración de la aplicación.

Puede asignar una directiva de configuración de aplicaciones a un grupo de usuarios finales y dispositivos mediante una combinación de [asignaciones de inclusión y exclusión](apps-inc-exl-assignments.md). Tras agregar una directiva de configuración de aplicación, podrá establecer las asignaciones de la directiva de configuración de aplicación. Al establecer las asignaciones de la directiva, puede elegir si quiere incluir o excluir los [grupos](../fundamentals/groups-add.md) de usuarios finales a los que se aplica la directiva. Si decide incluir uno o varios grupos, puede optar por seleccionar grupos específicos para incluir o seleccionar los grupos integrados. Los grupos integrados incluyen **Todos los usuarios**, **Todos los dispositivos** y **Todos los usuarios + todos los dispositivos**.

Tiene dos opciones para usar las directivas de configuración de aplicaciones con Intune:
- **Dispositivos administrados**: el dispositivo se administra mediante Intune como el proveedor de administración de dispositivos móviles (MDM). La aplicación debe estar diseñada para admitir la configuración de la aplicación.
- **Aplicaciones administradas**: una aplicación que se ha desarrollado para integrar Intune App SDK. Esto se conoce como Administración de aplicaciones móviles sin necesidad de inscripción ([MAM-WE](app-management.md#mobile-application-management-mam-basics)). También puede encapsular una aplicación para implementar y admitir Intune App SDK. Para más información sobre cómo encapsular una aplicación, vea [Preparación de aplicaciones de línea de negocio para las directivas de protección de aplicaciones](../developer/apps-prepare-mobile-application-management.md).

    > [!NOTE]
    > Las aplicaciones administradas de Intune se insertarán en el repositorio con un intervalo de 30 minutos para el estado de la Directiva de configuración de aplicaciones de Intune, cuando se implementen junto con una directiva de Intune App Protection. Si una directiva de Protección de aplicaciones de Intune no está asignada al usuario, el intervalo de inserción en el repositorio de la directiva de configuración de aplicaciones de Intune se establece en 720 minutos.

## <a name="apps-that-support-app-configuration"></a>Aplicaciones que admiten la configuración de aplicaciones

### <a name="managed-devices"></a>Dispositivos administrados
Puede usar las directivas de configuración de aplicaciones en las aplicaciones que las admitan. Para admitir la configuración de aplicaciones en Intune, las aplicaciones se deben escribir para este fin, como lo define el sistema operativo. Consulte al proveedor de la aplicación para obtener más información sobre las claves de configuración de la aplicación que admite.

### <a name="managed-apps"></a>Aplicaciones administradas
Puede preparar las aplicaciones de línea de negocio si incorpora [Intune App SDK](../developer/app-sdk.md) en la aplicación, o bien si la encapsula después de que haberla desarrollado con la [Herramienta de ajuste de aplicaciones de Intune](../developer/apps-prepare-mobile-application-management.md). Intune App SDK intenta minimizar la cantidad de cambios de código que debe realizar el desarrollador de la aplicación. Para obtener más información, vea [Información general del SDK para aplicaciones de Intune](../developer/app-sdk.md). Para obtener una comparación entre Intune App SDK y la herramienta de ajuste de aplicaciones de Intune, vea [Preparación de aplicaciones de línea de negocio para las directivas de protección de aplicaciones](../developer/apps-prepare-mobile-application-management.md#feature-comparison).

La selección de **Aplicaciones administradas** como el **Tipo de inscripción de dispositivos** hace referencia específicamente a las aplicaciones configuradas mediante directivas de configuración de Intune en un dispositivo que no está inscrito en la administración de dispositivos, mientras que **Dispositivos administrados** se aplica a las aplicaciones implementadas a través del canal de MDM y que, por tanto, se administran mediante Intune. Seleccione la opción adecuada en función de estas descripciones. 

![Tipo de inscripción del dispositivo](./media/app-configuration-policies-overview/device-enrollment-type.png)

> [!NOTE]
> En el caso de las aplicaciones de varias identidades, como Microsoft Outlook, se pueden tener en cuenta las preferencias del usuario. La Bandeja de entrada Prioritarios, por ejemplo, respetará la configuración del usuario y no la cambiará. Otros parámetros permiten controlar si un usuario puede o no cambiar la configuración. Para más información, vea [Implementación de las opciones de configuración de la aplicación de Outlook para iOS y Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

## <a name="validate-the-applied-app-configuration-policy"></a>Validación de la directiva de configuración de aplicaciones aplicada

Puede validar la directiva de configuración de aplicaciones mediante los tres métodos siguientes:

   1. De forma visible en el dispositivo. ¿La aplicación de destino muestra el comportamiento aplicado en la Directiva de configuración de aplicaciones?
   2. A través de registros de diagnóstico (vea la sección Registros de diagnóstico a continuación).
   3. En el portal de Intune. La sección **Supervisión** de una directiva puede proporcionar el estado relevante:

      ![Primera captura de pantalla del estado de instalación del dispositivo](./media/app-configuration-policies-overview/device-install-status-1.png)

      ![Segunda captura de pantalla del estado de instalación del dispositivo](./media/app-configuration-policies-overview/device-install-status-2.png)

      Además, en **Intune** -> **Dispositivos** -> **Todos los dispositivos** en el lado izquierdo de la pantalla, la opción **Configuración de la aplicación** mostrará todas las directivas asignadas y su estado:

      ![Captura de pantalla de la configuración de la aplicación](./media/app-configuration-policies-overview/app-configuration.png)

## <a name="diagnostic-logs"></a>Registros de diagnóstico

### <a name="ios-configuration-on-unmanaged-devices"></a>Configuración de iOS en dispositivos no administrados

Puede validar la configuración de iOS con el **registro de diagnóstico de Intune** en dispositivos no administrados para la configuración de aplicaciones administradas. Además de los pasos siguientes, puede acceder a los registros de aplicaciones administradas con Microsoft Edge. Para obtener más información, consulte [Uso de Microsoft Edge en iOS para acceder a los registros de aplicaciones administradas](~/apps/manage-microsoft-edge.md#use-microsoft-edge-on-ios-to-access-managed-app-logs).

1. Si aún no está instalado en el dispositivo, descargue e instale **Microsoft Edge** desde la App Store. Para obtener más información, consulte [Aplicaciones protegidas de Microsoft Intune](apps-supported-intune-apps.md).
2. Inicie **Microsoft Edge** y seleccione **about** > **intunehelp** en la barra de navegación.
3. Haga clic en **Introducción**.
4. Haga clic en **Compartir registros**.
5. Use la aplicación de correo que prefiera para enviarse el registro y verlo en su PC. 
6. Revise **IntuneMAMDiagnostics.txt** en el visor del archivo de texto.
7. Busque `ApplicationConfiguration`. Los resultados tendrán un aspecto similar al siguiente:

    ``` JSON
        {
            (
                {
                    Name = "com.microsoft.intune.mam.managedbrowser.BlockListURLs";
                    Value = "https://www.aol.com";
                },
                {
                    Name = "com.microsoft.intune.mam.managedbrowser.bookmarks";
                    Value = "Outlook Web|https://outlook.office.com||Bing|https://www.bing.com";
                }
            );
        },
        {
            ApplicationConfiguration =             
            (
                {
                Name = IntuneMAMUPN;
                Value = "CMARScrubbedM:13c45c42712a47a1739577e5c92b5bc86c3b44fd9a27aeec3f32857f69ddef79cbb988a92f8241af6df8b3ced7d5ce06e2d23c33639ddc2ca8ad8d9947385f8a";
                },
                {
                Name = "com.microsoft.outlook.Mail.NotificationsEnabled";
                Value = false;
                }
            );
        }
    ```

Los detalles de configuración de la aplicación deben coincidir con las directivas de configuración de la aplicación configuradas para el inquilino. 

![Configuración de la aplicación de destino](./media/app-configuration-policies-overview/targeted-app-configuration-3.png)

### <a name="ios-configuration-on-managed-devices"></a>Configuración de iOS en dispositivos administrados

Puede validar la configuración de iOS con el **registro de diagnóstico de Intune** en dispositivos administrados para la configuración de aplicaciones administradas.

1. Si aún no está instalado en el dispositivo, descargue e instale **Microsoft Edge** desde la App Store. Para obtener más información, consulte [Aplicaciones protegidas de Microsoft Intune](apps-supported-intune-apps.md).
2. Inicie **Microsoft Edge** y seleccione **about** > **intunehelp** en la barra de navegación.
3. Haga clic en **Introducción**.
4. Haga clic en **Compartir registros**.
5. Use la aplicación de correo que prefiera para enviarse el registro y verlo en su PC. 
6. Revise **IntuneMAMDiagnostics.txt** en el visor del archivo de texto.
7. Busque `AppConfig`. Los resultados deben coincidir con las directivas de configuración de la aplicación configuradas para el inquilino.

### <a name="android-configuration-on-managed-devices"></a>Configuración de Android en dispositivos administrados

Puede validar la configuración de iOS con el **registro de diagnóstico de Intune** en dispositivos administrados para la configuración de aplicaciones administradas.

Para recopilar registros de un dispositivo Android, usted o el usuario final deben descargar los registros del dispositivo a través de una conexión USB (o el equivalente al **Explorador de archivos** del dispositivo). Estos son los pasos:

1. Conecte el dispositivo Android al equipo con el cable USB.
2. En el equipo, busque un directorio que contenga el nombre del dispositivo. En ese directorio, busque `Android Device\Phone\Android\data\com.microsoft.windowsintune.companyportal`.
3. En la carpeta `com.microsoft.windowsintune.companyportal`, abra la carpeta de archivos y abra `OMADMLog_0`.
3. Busque `AppConfigHelper` para ubicar mensajes relacionados con la configuración de la aplicación. Los resultados tendrán un aspecto similar al siguiente bloque de datos:

    `2019-06-17T20:09:29.1970000       INFO   AppConfigHelper     10888  02256  Returning app config JSON [{"ApplicationConfiguration":[{"Name":"com.microsoft.intune.mam.managedbrowser.BlockListURLs","Value":"https:\/\/www.aol.com"},{"Name":"com.microsoft.intune.mam.managedbrowser.bookmarks","Value":"Outlook Web|https:\/\/outlook.office.com||Bing|https:\/\/www.bing.com"},{"Name":"com.microsoft.intune.mam.managedbrowser.homepage","Value":"https:\/\/www.arstechnica.com"}]},{"ApplicationConfiguration":[{"Name":"IntuneMAMUPN","Value":"AdeleV@M365x935807.OnMicrosoft.com"},{"Name":"com.microsoft.outlook.Mail.NotificationsEnabled","Value":"false"},{"Name":"com.microsoft.outlook.Mail.NotificationsEnabled.UserChangeAllowed","Value":"false"}]}] for user User-875363642`
    
## <a name="graph-api-support-for-app-configuration"></a>Compatibilidad de Graph API para la configuración de aplicaciones

Puede usar Graph API para realizar tareas de configuración de aplicaciones. Para obtener más información, consulte la [referencia sobre Graph API para la configuración de destino de MAM](https://docs.microsoft.com/graph/api/resources/intune-shared-targetedmanagedappconfiguration?view=graph-rest-beta). Para obtener más información sobre Intune y Graph, consulte [Trabajar con Intune en Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-beta).

## <a name="troubleshooting"></a>Solución de problemas

### <a name="using-logs-to-show-a-configuration-parameter"></a>Uso de registros para mostrar un parámetro de configuración
Cuando los registros muestran un parámetro de configuración que se confirma que se está aplicando pero parece no funcionar, es posible que haya un problema con la implementación de la configuración por parte del desarrollador de la aplicación. Ponerse en contacto primero con el desarrollador de la aplicación, o bien comprobar su base de conocimiento, puede ahorrarle una llamada al servicio de soporte técnico de Microsoft. Si se trata de un problema con la forma de controlar la configuración en una aplicación, tendría que solucionarse en una futura versión actualizada de esa aplicación.

## <a name="next-steps"></a>Pasos siguientes

### <a name="managed-devices"></a>Dispositivos administrados

- Obtenga información sobre cómo usar la configuración de aplicaciones con los dispositivos iOS.  Consulte [Agregar directivas de configuración de aplicaciones para dispositivos iOS administrados](app-configuration-policies-use-ios.md).
- Obtenga información sobre cómo usar la configuración de aplicaciones con los dispositivos Android.  Vea [Agregar directivas de configuración de aplicaciones para dispositivos Android administrados](app-configuration-policies-use-android.md).

### <a name="managed-apps"></a>Aplicaciones administradas

- Obtenga información sobre cómo usar la configuración de aplicaciones con aplicaciones administradas. Consulte [Agregar directivas de configuración para aplicaciones administradas sin inscripción de dispositivos](app-configuration-policies-managed-app.md).
