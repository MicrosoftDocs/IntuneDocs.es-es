---
title: Directivas de configuración de aplicaciones para Microsoft Intune
titleSuffix: ''
description: Obtenga información sobre cómo usar las directivas de configuración de aplicaciones en un dispositivo iOS o Android en Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cda0453009855d96e7c13e170ba908479a0773ea
ms.sourcegitcommit: 513e805bbea8bf652c2901dfc5460e34946077df
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2019
ms.locfileid: "70160566"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>Directivas de configuración de aplicaciones para Microsoft Intune

Las directivas de configuración de aplicaciones pueden ayudar a eliminar problemas de configuración de aplicaciones, ya que permiten asignar opciones de configuración a una directiva que se asigna a los usuarios finales antes de que ejecuten la aplicación. La configuración se proporciona de forma automática al configurar la aplicación en el dispositivo de los usuarios finales, que no tendrán que realizar ninguna acción. Los valores de configuración son únicos para cada aplicación. 

Puede crear y usar directivas de configuración de aplicaciones para proporcionar valores de configuración para aplicaciones iOS o Android. Estos valores de configuración permiten personalizar una aplicación mediante el uso de un [enfoque estándar del sector](https://www.appconfig.org/) para la configuración y administración de aplicaciones. Los valores de la directiva de configuración se usan cada vez que la aplicación los comprueba, que suele ser la primera vez que se ejecuta. 

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
> ![Captura de pantalla de una aplicación configurada](./media/app-configuration-policy-overview/configured-app.png)
>
> Al usar Dispositivos administrados como Tipo de inscripción para dispositivos Android, solo verá las aplicaciones de [Google Play Store administrado](https://play.google.com/work), no de [Google Play Store](https://play.google.com/store/apps). Google Play Store administrado, que también se denomina Android for Work (AfW) y Android Enterprise, son las aplicaciones del perfil de trabajo que contienen las versiones de la aplicación que admiten la configuración de la aplicación.

Puede asignar una directiva de configuración de aplicaciones a un grupo de usuarios finales y dispositivos mediante una combinación de [asignaciones de inclusión y exclusión](apps-inc-exl-assignments.md). Tras agregar una directiva de configuración de aplicación, podrá establecer las asignaciones de la directiva de configuración de aplicación. Al establecer las asignaciones de la directiva, puede elegir si quiere incluir o excluir los [grupos](groups-add.md) de usuarios finales a los que se aplica la directiva. Si decide incluir uno o varios grupos, puede optar por seleccionar grupos específicos para incluir o seleccionar los grupos integrados. Los grupos integrados incluyen **Todos los usuarios**, **Todos los dispositivos** y **Todos los usuarios + todos los dispositivos**.

Tiene dos opciones para usar las directivas de configuración de aplicaciones con Intune:
- **Dispositivos administrados**: el dispositivo se administra mediante Intune como el proveedor de administración de dispositivos móviles (MDM). La aplicación debe estar diseñada para admitir la configuración de la aplicación.
- **Aplicaciones administradas**: una aplicación que se ha desarrollado para integrar Intune App SDK. Esto se conoce como Administración de aplicaciones móviles sin necesidad de inscripción ([MAM-WE](app-management.md#mobile-application-management-mam-basics)). También puede encapsular una aplicación para implementar y admitir Intune App SDK. Para más información sobre cómo encapsular una aplicación, vea [Preparación de aplicaciones de línea de negocio para las directivas de protección de aplicaciones](apps-prepare-mobile-application-management.md).

    > [!NOTE]
    > Las aplicaciones administradas de Intune se insertarán en el repositorio con un intervalo de 30 minutos para el estado de la Directiva de configuración de aplicaciones de Intune, cuando se implementen junto con una directiva de Intune App Protection. Si una directiva de Protección de aplicaciones de Intune no está asignada al usuario, el intervalo de inserción en el repositorio de la directiva de configuración de aplicaciones de Intune se establece en 720 minutos.

## <a name="apps-that-support-app-configuration"></a>Aplicaciones que admiten la configuración de aplicaciones

### <a name="managed-devices"></a>Dispositivos administrados
Puede usar las directivas de configuración de aplicaciones en las aplicaciones que las admitan. Para admitir la configuración de aplicaciones en Intune, las aplicaciones se deben escribir para este fin, como lo define la [AppConfig Community](https://www.appconfig.org/members). Consulte con el proveedor de su aplicación para obtener más información.

### <a name="managed-apps"></a>Aplicaciones administradas
Puede preparar las aplicaciones de línea de negocio si incorpora [Intune App SDK](app-sdk.md) en la aplicación, o bien si la encapsula después de que haberla desarrollado con la [Herramienta de ajuste de aplicaciones de Intune](apps-prepare-mobile-application-management.md). Intune App SDK intenta minimizar la cantidad de cambios de código que debe realizar el desarrollador de la aplicación. Para obtener más información, vea [Información general del SDK para aplicaciones de Intune](app-sdk.md). Para obtener una comparación entre Intune App SDK y la herramienta de ajuste de aplicaciones de Intune, vea [Preparación de aplicaciones de línea de negocio para las directivas de protección de aplicaciones](apps-prepare-mobile-application-management.md#feature-comparison).

La selección de **Aplicaciones administradas** como el **Tipo de inscripción de dispositivos** hace referencia específicamente a las aplicaciones configuradas mediante directivas de configuración de Intune en un dispositivo que no está inscrito en la administración de dispositivos, mientras que **Dispositivos administrados** se aplica a las aplicaciones implementadas a través del canal de MDM y que, por tanto, se administran mediante Intune. Seleccione la opción adecuada en función de estas descripciones. 

![Tipo de inscripción del dispositivo](./media/app-configuration-policy-overview/device-enrollment-type.png)

> [!NOTE]
> En el caso de las aplicaciones de varias identidades, como Microsoft Outlook, se pueden tener en cuenta las preferencias del usuario. La Bandeja de entrada Prioritarios, por ejemplo, respetará la configuración del usuario y no la cambiará. Otros parámetros permiten controlar si un usuario puede o no cambiar la configuración. Para más información, vea [Implementación de las opciones de configuración de la aplicación de Outlook para iOS y Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

## <a name="validate-the-applied-app-configuration-policy"></a>Validación de la directiva de configuración de aplicaciones aplicada

Puede validar la directiva de configuración de aplicaciones mediante los tres métodos siguientes:

   1. De forma visible en el dispositivo. ¿La aplicación de destino muestra el comportamiento aplicado en la Directiva de configuración de aplicaciones?
   2. A través de registros de diagnóstico (vea la sección Registros de diagnóstico a continuación).
   3. En el portal de Intune. La sección **Supervisión** de una directiva puede proporcionar el estado relevante:

      ![Primera captura de pantalla del estado de instalación del dispositivo](./media/app-configuration-policy-overview/device-install-status-1.png)

      ![Segunda captura de pantalla del estado de instalación del dispositivo](./media/app-configuration-policy-overview/device-install-status-2.png)

      Además, en **Intune** -> **Dispositivos** -> **Todos los dispositivos** en el lado izquierdo de la pantalla, la opción **Configuración de la aplicación** mostrará todas las directivas asignadas y su estado:

      ![Captura de pantalla de la configuración de la aplicación](./media/app-configuration-policy-overview/app-configuration.png)

## <a name="graph-api-support-for-app-configuration"></a>Compatibilidad de Graph API para la configuración de aplicaciones

Puede usar Graph API para realizar tareas de configuración de aplicaciones. Para obtener más información, consulte la [referencia sobre Graph API para la configuración de destino de MAM](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

## <a name="troubleshooting"></a>Solucionar problemas

### <a name="using-logs-to-show-a-configuration-parameter"></a>Uso de registros para mostrar un parámetro de configuración
Cuando los registros muestran un parámetro de configuración que se confirma que se está aplicando pero parece no funcionar, es posible que haya un problema con la implementación de la configuración por parte del desarrollador de la aplicación. Ponerse en contacto primero con el desarrollador de la aplicación, o bien comprobar su base de conocimiento, puede ahorrarle una llamada al servicio de soporte técnico de Microsoft. Si se trata de un problema con la forma de controlar la configuración en una aplicación, tendría que solucionarse en una futura versión actualizada de esa aplicación.

## <a name="next-steps"></a>Pasos siguientes

### <a name="managed-devices"></a>Dispositivos administrados

- Obtenga información sobre cómo usar la configuración de aplicaciones con los dispositivos iOS.  Consulte [Agregar directivas de configuración de aplicaciones para dispositivos iOS administrados](app-configuration-policies-use-ios.md).
- Obtenga información sobre cómo usar la configuración de aplicaciones con los dispositivos Android.  Vea [Agregar directivas de configuración de aplicaciones para dispositivos Android administrados](app-configuration-policies-use-android.md).

### <a name="managed-apps"></a>Aplicaciones administradas

- Obtenga información sobre cómo usar la configuración de aplicaciones con aplicaciones administradas. Consulte [Agregar directivas de configuración para aplicaciones administradas sin inscripción de dispositivos](app-configuration-policies-managed-app.md).
