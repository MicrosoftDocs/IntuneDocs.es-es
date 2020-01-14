---
title: Configuración de Google Chrome para dispositivos Android con Intune
titleSuffix: Microsoft Intune
description: Use las directivas de configuración de Intune con Google Chrome para dispositivos Android.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: c02ea34417073091e2f2841b363edfb9966ce558
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2019
ms.locfileid: "75205911"
---
# <a name="configure-google-chrome-for-android-devices-using-intune"></a>Configuración de Google Chrome para dispositivos Android con Intune 

Puede usar una directiva de configuración de aplicaciones de Intune para configurar Google Chrome para dispositivos Android. La configuración de la aplicación se puede aplicar automáticamente. Por ejemplo, puede establecer de forma específica los marcadores y las direcciones URL que desea bloquear o permitir.

## <a name="prerequisites"></a>Requisitos previos

- El dispositivo Android Enterprise del usuario debe inscribirse en Intune. Para más información, vea [Configure la inscripción de dispositivos de perfil de trabajo Android](~/enrollment/android-work-profile-enroll.md).
- Google Chrome se agrega como una aplicación de Google Play administrado. Para más información acerca de Google Play administrado, consulte [Conexión de una cuenta de Intune a una cuenta de Google Play administrado](~/enrollment/connect-intune-android-enterprise.md).

## <a name="add-the-google-chrome-app-to-intune"></a>Adición de la aplicación Google Chrome a Intune

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Aplicaciones** > **Todas las aplicaciones** > **Agregar** y después agregue la aplicación **Google Play administrado**.
3. Vaya a Google Play administrado, busque con **Google Chrome** y apruebe.

    ![Búsqueda y aprobación de Google Chrome](~/apps/media/apps-configure-chrome-android/search.png)

4. Asigne Google Chrome a un grupo de usuarios como un tipo de aplicación requerido. Google Chrome se implementará automáticamente cuando el dispositivo esté inscrito en Intune.

Para obtener más información sobre cómo agregar una aplicación de Google Play administrado a Intune, consulte [Aplicaciones de la tienda de Google Play administrado](~/apps/apps-add-android-for-work.md#managed-google-play-store-apps).

## <a name="add-app-configuration-for-managed-ae-devices"></a>Adición de la configuración de aplicaciones para dispositivos AE administrados

1. En el [Centro de administración de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), seleccione **Aplicaciones** > **Directivas de configuración de aplicaciones** > **Agregar** > **Dispositivos administrados**.
2. Especifique los siguientes detalles:
    - **Nombre**: nombre del perfil que aparece en Azure Portal.
    - **Descripción**: descripción del perfil que aparece en Azure Portal.
    - **Tipo de inscripción del dispositivo**: esta configuración está establecida en **Dispositivos administrados**.
    - **Plataforma**: seleccione **Android**.

    ![Adición de la directiva de configuración de Google Chrome](~/apps/media/apps-configure-chrome-android/add-policy.png)

3. Haga clic en **Aplicación asociada** para mostrar el panel **Aplicación asociada**. Busque y seleccione **Google Chrome**. Esta lista contiene las [aplicaciones de Google Play administrado que ha aprobado y sincronizado con Intune](~/apps/apps-add-android-for-work.md).

    ![Selección de Google Chrome en aplicación asociada](~/apps/media/apps-configure-chrome-android/associated-app.png)

4. Haga clic en **Opciones de configuración**, seleccione **Usar diseñador de configuraciones** y haga clic en **Agregar** para seleccionar las claves de configuración.

    ![Adición de uso del diseñador de configuraciones](~/apps/media/apps-configure-chrome-android/configuration.png)

    A continuación se muestra un ejemplo con las opciones de configuración habituales:
    - **Bloquear el acceso a una lista de direcciones URL** : `["*"]`
    - **Permitir el acceso a una lista de direcciones URL** : `["baidu.com", "youtube.com", "chromium.org", "chrome://*"]`
    - **Marcadores administrados**: `[{"toplevel_name": "My managed bookmarks folder"  },  {"url": "baidu.com",   "name": "Baidu"},  {"url": "youtube.com", "name": "Youtube"},  {"name": "Chrome links",  "children": [{"url": "chromium.org", "name": "Chromium"},    {"url": "dev.chromium.org", "name": "Chromium Developers"}]}]`
    - **Disponibilidad del modo incógnito**: `Incognito mode disabled`

    Una vez que se agregan los valores de configuración mediante el diseñador de configuraciones, estos se presentarán en una tabla. 

    ![Configuración común](~/apps/media/apps-configure-chrome-android/common-settings.png)

    La configuración anterior crea marcadores y bloquea el acceso a todas las direcciones URL, excepto `baidu.com`, `yahoo.com`, `chromium.org` y `chrome://`.

5. Haga clic en **Aceptar** y **Agregar** para agregar la directiva de configuración a Intune.
6. Asigne esta directiva de configuración a un grupo de usuarios. Para más información, consulte [Asignación de aplicaciones a grupos con Microsoft Intune](~/apps/apps-deploy.md). 

## <a name="verify-the-device-settings"></a>Comprobación de la configuración del dispositivo

Una vez que el dispositivo Android esté inscrito en Android Enterprise, la aplicación de Google Chrome administrado con el icono de cartera se implementará automáticamente.
 
   <img alt="Managed Google Chrome with the portfolio icon" src="~/apps/media/apps-configure-chrome-android/chrome-icon.png" width="350">

Inicie Google Chrome y verá la configuración aplicada.

   Marcadores:<br>
   <img alt="Bookmarks" src="~/apps/media/apps-configure-chrome-android/bookmarks.png" width="350">

   Dirección URL bloqueada:<br>
   <img alt="Blocked URL" src="~/apps/media/apps-configure-chrome-android/blocked-url.png" width="350">

   Permitir dirección URL:<br>
   <img alt="Allow URL" src="~/apps/media/apps-configure-chrome-android/allowed-url.png" width="350">

   Pestaña de incógnito:<br>
   <img alt="Incognito tab" src="~/apps/media/apps-configure-chrome-android/incognito-tab.png" width="350">

## <a name="troubleshooting"></a>Solución de problemas

1. Consulte el portal de Intune para supervisar el estado de implementación de la directiva.

    ![Supervisión del estado de implementación de la directiva](~/apps/media/apps-configure-chrome-android/monitor-status.png)

2. Inicie Google Chrome y visite **chrome://policy**. Podemos confirmar si la configuración se aplica correctamente.

    ![Confirmación de la aplicación correcta de la configuración](~/apps/media/apps-configure-chrome-android/confirm.png)

## <a name="additional-information"></a>Información adicional

- [Adición de directivas de configuración de aplicaciones para dispositivos Android Enterprise administrados](~/app-configuration-policies-use-android.md)
- [Lista de directivas de Chrome Enterprise](https://cloud.google.com/docs/chrome-enterprise/policies/)

## <a name="next-steps"></a>Pasos siguientes

- Para más información sobre los dispositivos totalmente administrados de Android Enterprise, vea [Configuración de la inscripción en Intune de dispositivos Android Enterprise totalmente administrados](~/enrollment/android-fully-managed-enroll.md).
