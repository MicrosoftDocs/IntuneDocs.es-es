---
title: Configuración del quiosco multimedia para Android en Microsoft Intune - Azure | Microsoft Docs
description: Configure dispositivos de quiosco multimedia en Android con una aplicación o con varias aplicaciones.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cef98527ee2c281547f8046f3c6f08275d8f0807
ms.sourcegitcommit: e814cfbbefe818be3254ef6f859a7bf5f5b99123
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2018
ms.locfileid: "43329390"
---
# <a name="kiosk-settings-for-android-devices-in-intune"></a>Configuración del quiosco multimedia para Android en Intune

Puede configurar un dispositivo de quiosco multimedia para una sola aplicación o para varias usando la configuración del dispositivo. Cuando un dispositivo está en modo de quiosco multimedia, el uso del dispositivo se limita a los vínculos web o las aplicaciones definidos por el perfil de restricción. 

## <a name="restrict-an-android-kiosk-device-to-a-single-app"></a>Restringir un dispositivo Android de quiosco multimedia para una sola aplicación

Si el perfil de restricción de un dispositivo de quiosco multimedia se establece en **Modo de quiosco multimedia** = **Quiosco multimedia con una sola aplicación**, los usuarios solo podrán acceder a una sola aplicación. Al iniciar un dispositivo configurado en este modo, se inicia la aplicación específica; los usuarios no pueden abrir nuevas aplicaciones ni modificar la aplicación en ejecución.

1. Asegúrese de que la aplicación que quiere usar en el dispositivo de quiosco multimedia se ha [implementado en el dispositivo](apps-deploy.md) y que ha asignado la aplicación al grupo de dispositivos que creó para los dispositivos de quiosco multimedia.
2. Vaya al [Portal de Intune](https://portal.azure.com) y elija **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. En la hoja **Crear perfil**, rellene los campos siguientes:
     - **Nombre**
     - **Plataforma**: Android Enterprise
     - **Tipo de perfil**: Solo el propietario del dispositivo > Restricciones del dispositivo
4. Elija **Configuración** > **Quiosco multimedia**.
5. En **Modo de quiosco multimedia**, elija **Quiosco multimedia con una sola aplicación**.
6. Elija **Seleccionar una aplicación administrada** y después seleccione en Google Play administrado la aplicación que quiera que sea la única disponible para los dispositivos que usen este perfil.
7. Elija **Aceptar** > **Aceptar** > **Aceptar** > **Crear**.
8. Elija el perfil que acaba de crear > **Asignaciones**.
9. En **Asignar a**, elija **Grupos seleccionados**.
10. Elija **Seleccionar los grupos para incluir** > elija el grupo de dispositivos que ha creado para los dispositivos de quiosco multimedia > **Seleccionar**.

## <a name="restrict-a-kiosk-device-to-a-set-of-apps-or-web-links"></a>Restringir un dispositivo de quiosco multimedia a un conjunto de aplicaciones o vínculos web

Si el perfil de restricción de un dispositivo de quiosco multimedia se establece en **Modo de quiosco multimedia** = **Quiosco multimedia con varias aplicaciones**, los usuarios solo pueden acceder al número limitado de aplicaciones que configure. También puede definir un conjunto de vínculos web que pueden visitar los usuarios. Al aplicar la directiva, los usuarios ven los iconos de las aplicaciones permitidas en la pantalla principal.

Para configurar un dispositivo Android como quiosco multimedia para varias aplicaciones, siga estos pasos principales:

1. [Importe e implemente la aplicación Managed Home Screen desde Google Play administrado](#import-and -deploy-the-managed-home-screen-app).
2. [Agregue y asigne aplicaciones que se puedan utilizar en el quiosco multimedia](#add-and-assign-apps-that-can-be-used-in-kiosk-mode).
3. (Opcional) [Agregue vínculos web que se puedan usar en el quiosco multimedia](#add-web-links-that-can-be-used-in-kiosk-mode).

### <a name="import-and-deply-the-managed-home-screen-app"></a>Importar e implementar la aplicación Managed Home Screen

1. Vaya a la [página Managed Home Screen desde Google Play](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise) e inicie sesión con la misma cuenta que usa para otras aplicaciones de Google Play administrado.
2. Elija **Aprobar**.
3. Vaya al [portal de Intune](https://portal.azure.com) y elija **Aplicaciones cliente** > **Google Play administrado** > **Sincronización**.
4. Elija **Aplicaciones** > **Managed Home Screen** > **Asignaciones** > **Agregar grupo**.
5. En **Tipo de asignación**, elija **Obligatoria**.
6. Elija **Grupos para incluir** > **Seleccionar grupos para incluir** > elija el grupo de dispositivos que ha creado para los dispositivos de quiosco multimedia > **seleccione** > **Aceptar** > **Aceptar** > **Guardar**.

### <a name="add-and-assign-apps-that-can-be-used-in-kiosk-mode"></a>Agregar y asignar aplicaciones que se puedan usar en el quiosco multimedia

Para cada aplicación que quiera que esté disponible en los dispositivos de quiosco multimedia, siga estos pasos:

1. [Agregue la aplicación a Intune](store-apps-android.md).
2. Elija **Aplicaciones cliente** > **Aplicaciones** > elija la aplicación > **Asignaciones** > **Agregar grupo**.
3. En **Tipo de asignación**, elija **Obligatoria**.
4. Elija **Grupos para incluir** > **Seleccionar grupos para incluir** > elija el grupo de dispositivos que ha creado para los dispositivos de quiosco multimedia > **seleccione** > **Aceptar** > **Aceptar** > **Guardar**.

### <a name="add-web-links-that-can-be-used-in-kiosk-mode"></a>Agregar vínculos web que se puedan usar en el quiosco multimedia

1. Vaya al [portal de Intune](https://portal.azure.com) y elija **Aplicaciones cliente** > **Aplicaciones** > **Agregar**.
2. En **Tipo de aplicación**, elija **Vínculo web**.
3. Elija **Configurar** y proporcione la información necesaria. No es necesario agregar una imagen de logotipo, puesto que se obtendrá automáticamente del favicon.ico del sitio web.
4. Seleccione **Aceptar** > **Agregar**.

Asegúrese de implementar una aplicación de explorador web en los dispositivos del quiosco mediante [Aplicaciones móviles](apps-add.md).

### <a name="create-a-multi-app-kiosk-profile"></a>Crear un perfil de quiosco multimedia con varias aplicaciones

1. Vaya al [Portal de Intune](https://portal.azure.com) y elija **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. En la hoja **Crear perfil**, rellene los campos siguientes:
     - **Nombre**: escriba un nombre intuitivo
     - **Plataforma**: Android Enterprise
     - **Tipo de perfil**: Solo el propietario del dispositivo > Restricciones del dispositivo
4. Elija **Configuración** > **Quiosco multimedia**.
5. En **Modo de quiosco multimedia**, elija **Quiosco multimedia con varias aplicaciones**.
6. Elija **Agregar** y después seleccione las aplicaciones o vínculos web que quiera que estén disponibles para dispositivos con este perfil.
7. Elija **Aceptar** > **Aceptar** > **Aceptar** > **Crear**.
8. Elija el perfil que acaba de crear > **Asignaciones**.
9. En **Asignar a**, elija **Grupos seleccionados**.
10. Elija **Seleccionar los grupos para incluir** > elija el grupo de dispositivos que ha creado para los dispositivos de quiosco multimedia > **Seleccionar** > **Guardar**.

## <a name="next-steps"></a>Pasos siguientes
[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).
