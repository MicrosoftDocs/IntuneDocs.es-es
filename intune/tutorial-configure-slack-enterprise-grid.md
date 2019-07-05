---
title: 'Tutorial: Configuración de Slack para usar Intune para EMM y la configuración de aplicaciones'
titleSuffix: Microsoft Intune
description: En este tutorial, configurará Slack para usar Intune para EMM y la configuración de aplicaciones.
keywords: ''
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 06/11/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 55db37c5-0da7-4d9c-8027-525afb1c6349
Customer intent: As an Intune admin, I want to learn how to configure Slack to use Intune for EMM and app configuration..
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: da6c9b544d86c9c4b09c061c0f1500ed8612a047
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2019
ms.locfileid: "67530709"
---
# <a name="tutorial-configure-slack-to-use-intune-for-emm-and-app-configuration"></a>Tutorial: Configuración de Slack para usar Intune para EMM y la configuración de aplicaciones

Slack es una aplicación de colaboración que puede usar con Microsoft Intune.   

En este tutorial, aprenderá a:
> [!div class="checklist"]
> - Establecer Intune como el proveedor de Enterprise Mobility Management (EMM) en Slack Enterprise Grid. Podrá limitar el acceso a las áreas de trabajo del plan de Grid a los dispositivos administrados de Intune.
> - Crear directivas de configuración de aplicaciones para administrar la aplicación Slack para EMM en iOS y la aplicación Slack para los dispositivos Android con perfiles de trabajo.
> - Crear directivas de cumplimiento de dispositivos de Intune para establecer las condiciones que deben cumplir los dispositivos Android e iOS para que se los considere compatibles.

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](free-trial-sign-up.md).

## <a name="prerequisites"></a>Requisitos previos
Necesitará a un inquilino de prueba con las siguientes suscripciones para este tutorial:
- Azure Active Directory Premium ([evaluación gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
- Suscripción a Intune ([evaluación gratuita](free-trial-sign-up.md))

También necesitará un plan de [Slack Enterprise Grid](https://get.slack.help/hc/articles/360004150931-What-is-Slack-Enterprise-Grid-).

## <a name="configure-your-slack-enterprise-grid-plan"></a>Configuración de un plan de Slack Enterprise Grid
Para activar EMM para el plan de Slack Enterprise Grid, siga las [instrucciones de Slack](https://get.slack.help/hc/articles/115002579426-Enable-Enterprise-Mobility-Management-for-your-org#step-2:-turn-on-emm) y [conecte Azure Active Directory](https://docs.microsoft.com/azure/active-directory/saas-apps/slack-tutorial) como el proveedor de identidades (IDP) del plan de Grid.

## <a name="sign-in-to-intune"></a>Iniciar sesión en Intune
Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) como administrador global o administrador de servicios de Intune. Si ha creado una suscripción de prueba de Intune, la cuenta con la que creó la suscripción es el administrador global.

## <a name="set-up-slack-for-emm-on-ios-devices"></a>Configuración de Slack para EMM en dispositivos iOS
Agregue la aplicación Slack para EMM de iOS al inquilino de Intune y cree una directiva de configuración de aplicaciones para permitir que los usuarios de iOS de las organizaciones tengan acceso a Slack con Intune como proveedor de EMM.

### <a name="add-slack-for-emm-to-intune"></a>Incorporación de Slack para EMM a Intune
Agregue Slack para EMM como una aplicación iOS administrada en Intune y asigne sus usuarios de Slack. Las aplicaciones son específicas para una plataforma, por lo que deberá agregar una aplicación de Intune distinta para los usuarios de Slack en dispositivos Android.
1. En Intune, seleccione **Aplicaciones cliente** > **Aplicaciones** > **Agregar**.
2. En Tipo de aplicación, seleccione **Store app - iOS** (Aplicación de la tienda: iOS).
3. Seleccione **Buscar en App Store**. Escriba el término de búsqueda "Slack para EMM" y seleccione la aplicación.
4. Seleccione **App information** (Información de la aplicación) y configure los cambios que considere necesarios.
5. Seleccione **Agregar**.
6. En la barra de búsqueda, escriba "Slack para EMM" y seleccione la aplicación que acaba de agregar.
7. En Administrar, seleccione **Asignaciones**.
8. Seleccione **Agregar grupo**. En función de quién haya elegido que se vea afectado al activar EMM para Slack, en **Tipo de asignación**, es posible que quiera seleccionar:
    -  **Disponible para dispositivos inscritos** si eligió "All members (including guests)"(Todos los miembros [incluidos los invitados]) O BIEN,
    -  **Disponible con o sin inscripción** si eligió "All members (excluding guests)" (Todos los miembros [excepto los invitados]) u "Optional" (Opcional).
9. Seleccione **Grupos incluidos** y seleccione **Sí** en Make this app available to all users (Hacer que esta aplicación esté disponible para todos los usuarios).
10. Haga clic en **Aceptar** y, luego, vuelva a hacer clic en **Aceptar**.
11. Haga clic en **Guardar**.

### <a name="add-an-app-configuration-policy-for-slack-for-emm"></a>Incorporación de una directiva de configuración de aplicaciones de Slack para EMM
Agregue una directiva de configuración de aplicaciones de Slack para EMM de iOS. Las directivas de configuración de aplicaciones para los dispositivos administrados son específicas para una plataforma, por lo que deberá agregar una directiva distinta para los usuarios de Slack en dispositivos Android.
1. En Intune, seleccione **Aplicaciones cliente** > **Directivas de configuración de aplicaciones** > **Agregar**.
2. En Nombre, escriba Prueba de la directiva de configuración de aplicaciones de Slack.
3. En Tipo de inscripción del dispositivo, seleccione **Dispositivos administrados**.
4. En Plataforma, seleccione **iOS**.
5. Seleccione **Aplicación asociada**.
6. En la barra de búsqueda, escriba "Slack para EMM" y seleccione la aplicación.
7. Haga clic en **Aceptar** y, luego, seleccione **Configuration settings** (Opciones de configuración). 
    -   Para información sobre las claves de configuración y sus valores, consulte la documentación que aparece en la pestaña "Technical" (Aspectos técnicos) de la [página web AppConfig de Slack](https://www.appconfig.org/company/slack/).
8. Seleccione **Aceptar** y, luego, seleccione **Agregar**.
9. En la barra de búsqueda, escriba "Prueba de la directiva de configuración de aplicaciones de Slack" y seleccione la directiva que acaba de agregar.
10. En Administrar, seleccione **Asignaciones**.
11. En Asignar a, seleccione **Todos los usuarios + todos los dispositivos**.
12. Haga clic en **Guardar**.

### <a name="optional-create-an-ios-device-compliance-policy"></a>(Opcional) Creación de una directiva de cumplimiento de dispositivos iOS
Configure una directiva de cumplimiento para dispositivos Intune para establecer las condiciones que debe cumplir un dispositivo para que se considere compatible. Para este tutorial, se creará una directiva de cumplimiento para dispositivos iOS. Las directivas de cumplimiento son específicas para una plataforma, por lo que deberá crear una directiva distinta para los usuarios de Slack en dispositivos Android.
1. En Intune, seleccione **Cumplimiento del dispositivo** > **Directivas** > **Crear directiva**.
2. En Nombre, escriba "Prueba de directiva de cumplimiento de iOS".
3. En Descripción, escriba "Prueba de directiva de cumplimiento de iOS".
4. En Plataforma, seleccione **iOS**.
5. Seleccione **Estado del dispositivo**. Junto a Dispositivos con Jailbreak, seleccione **Bloquear** y, luego, **Aceptar**.
6. Seleccione **Seguridad del sistema** y escriba el valor de la Contraseña. Para este tutorial, seleccione la siguiente configuración recomendada:
    -   En Requerir una contraseña para desbloquear dispositivos móviles, seleccione **Requerir**.
    -   En Contraseñas sencillas, seleccione **Bloquear**.
    -   En Longitud mínima de contraseña, escriba 4.
    -   Para Tipo de contraseña requerida, elija **Alfanumérica**.
    -   En Máximo de minutos tras bloqueo de pantalla antes de solicitar la contraseña, elija **Inmediatamente**.
    -   En Expiración de contraseña (días), escriba 41.
    -   En Número de contraseñas anteriores para impedir su reutilización, escriba 5.
7. Haga clic en **Aceptar** y, luego, en **Aceptar** nuevamente.
8. Haga clic en **Crear**.

## <a name="set-up-slack-on-android-work-profile-devices"></a>Configuración de Slack en dispositivos del perfil de trabajo de Android
Agregue la aplicación administrada de Google Play Slack al inquilino de Intune y cree una directiva de configuración de aplicaciones para permitir que los usuarios de Android de las organizaciones tengan acceso a Slack con Intune como proveedor de EMM.

### <a name="add-slack-to-intune"></a>Incorporación de Slack a Intune
Agregue Slack como aplicación administrada de Google Play en Intune y asigne sus usuarios de Slack. Las aplicaciones son específicas para una plataforma, por lo que deberá agregar una aplicación de Intune distinta para los usuarios de Slack en dispositivos iOS.
1. En Intune, seleccione **Aplicaciones cliente** > **Aplicaciones** > **Agregar**.
2. En Tipo de aplicación, seleccione **Store app – Managed Google Play** (Aplicación de la tienda: administrada de Google Play).
3. Seleccione **Managed Google Play - Approve** (Administrada de Google Play: aprobar). Escriba el término de búsqueda "Slack para EMM" y seleccione la aplicación.
4. Seleccione **Aprobar**.
5. En la barra de búsqueda, escriba "Slack" y seleccione la aplicación que acaba de agregar.
6. En Administrar, seleccione **Asignaciones**.
7. Seleccione **Agregar grupo**. En función de quién haya elegido que se vea afectado al activar EMM para Slack, en **Tipo de asignación**, es posible que quiera seleccionar:
    -   **Disponible para dispositivos inscritos** si eligió "All members (including guests)"(Todos los miembros [incluidos los invitados]) O BIEN,
    -   **Disponible con o sin inscripción** si eligió "All members (excluding guests)" (Todos los miembros [excepto los invitados]) u "Optional" (Opcional).
8. Seleccione Grupos incluidos y seleccione **Sí** en Make this app available to all users (Hacer que esta aplicación esté disponible para todos los usuarios).
9. Haga clic en **Aceptar** y, luego, vuelva a hacer clic en **Aceptar**.
10. Haga clic en **Guardar**.

### <a name="add-an-app-configuration-policy-for-slack"></a>Incorporación de una directiva de configuración de aplicaciones de Slack
Agregue una directiva de configuración de aplicaciones de Slack. Las directivas de configuración de aplicaciones para los dispositivos administrados son específicas para una plataforma, por lo que deberá agregar una directiva distinta para los usuarios de Slack en dispositivos iOS.
1. En Intune, seleccione **Aplicaciones cliente** > **Directivas de configuración de aplicaciones** > **Agregar**.
2. En Nombre, escriba Prueba de la directiva de configuración de aplicaciones de Slack.
3. En Tipo de inscripción del dispositivo, seleccione **Dispositivos administrados**.
4. En Plataforma, seleccione **Android**.
5. Seleccione **Aplicación asociada**.
6. En la barra de búsqueda, escriba "Slack" y seleccione la aplicación.
7. Seleccione **Aceptar** y, luego, seleccione **Configuration settings** (Opciones de configuración).
    -   Para información sobre las claves de configuración y sus valores, consulte la documentación que aparece en la pestaña "Technical" (Aspectos técnicos) de la [página web AppConfig de Slack](https://www.appconfig.org/company/slack/).
8. Haga clic en **Aceptar** y, luego, seleccione **Agregar**.
9. En la barra de búsqueda, escriba "Prueba de la directiva de configuración de aplicaciones de Slack" y seleccione la directiva que acaba de agregar.
10. En Administrar, seleccione **Asignaciones**.
11. En Asignar a, seleccione **Todos los usuarios + todos los dispositivos**.
12. Haga clic en **Guardar**.

### <a name="optional-create-an-android-device-compliance-policy"></a>(Opcional) Creación de una directiva de cumplimiento de dispositivos Android
Configure una directiva de cumplimiento para dispositivos Intune para establecer las condiciones que debe cumplir un dispositivo para que se considere compatible. Para este tutorial, se creará una directiva de cumplimiento para dispositivos Android. Las directivas de cumplimiento son específicas para una plataforma, por lo que deberá crear una directiva distinta para los usuarios de Slack en dispositivos iOS.
1. En Intune, seleccione **Cumplimiento del dispositivo** > **Directivas** > **Crear directiva**.
2. En Nombre, escriba "Prueba de directiva de cumplimiento de Android".
3. En Descripción, escriba "Prueba de directiva de cumplimiento de Android".
4. En Plataforma, seleccione **Android Enterprise**.
5. En Tipo de perfil, seleccione **Perfil de trabajo**.
6. Seleccione **Estado del dispositivo**. Junto a Dispositivos liberados, seleccione **Bloquear** y luego **Aceptar**.
7. Seleccione **Seguridad del sistema** y escriba la **configuración de la Contraseña**. Para este tutorial, seleccione la siguiente configuración recomendada:
    -   En Requerir una contraseña para desbloquear dispositivos móviles, seleccione **Requerir**.
    -   En Tipo de contraseña requerida, seleccione **Al menos alfanumérica**.
    -   En Longitud mínima de contraseña, escriba 4.
    -   En Máximo de minutos tras bloqueo de pantalla antes de solicitar la contraseña, elija **15 minutos**.
    -   En Expiración de contraseña (días), escriba 41.
    -   En Número de contraseñas anteriores para impedir su reutilización, escriba 5.
8. Haga clic en **Aceptar** y, luego, vuelva a hacer clic en **Aceptar**.
9. Haga clic en **Crear**.

## <a name="launch-slack"></a>Inicio de Slack

Con las directivas que acaba de crear, todo dispositivo iOS o Android con perfil de trabajo que intente iniciar sesión en una de las áreas de trabajo deberá estar inscrito en Intune. Para probar este escenario, intente iniciar Slack para EMM en un dispositivo iOS inscrito en Intune o iniciar Slack en un dispositivo Android con perfil de trabajo inscrito en Intune. 

## <a name="next-steps"></a>Pasos siguientes

En este tutorial:
- Estableció Intune como el proveedor de Enterprise Mobility Management (EMM) en Slack Enterprise Grid. 
- Creó directivas de configuración de aplicaciones para administrar la aplicación Slack para EMM en iOS y la aplicación Slack para los dispositivos Android con perfiles de trabajo.
- Creó directivas de cumplimiento de dispositivos de Intune para establecer las condiciones que deben cumplir los dispositivos Android e iOS para que se los considere compatibles.

Para más información sobre las directivas de configuración de aplicaciones, consulte las [directivas de configuración de aplicaciones para Microosft Intune](app-configuration-policies-overview.md). Para más información sobre las directivas de cumplimiento de los dispositivos, consulte [Establecimiento de reglas en los dispositivos para permitir el acceso a recursos de su organización con Intune](device-compliance-get-started.md).