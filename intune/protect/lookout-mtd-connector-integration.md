---
title: Configuración de la integración de Lookout con Microsoft Intune
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo integrar Intune con Lookout Mobile Endpoint Security, como una solución de Mobile Threat Defense, para controlar el acceso de los dispositivos móviles a los recursos corporativos.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/11/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5b0d7644-3183-45ba-a165-0d82d70cb71e
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b61281b0e82bcb839efdc31726d398eea08c364f
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502190"
---
# <a name="set-up-lookout-mobile-endpoint-security-integration-with-intune"></a>Configuración de la integración de Lookout Mobile Endpoint Security con Intune
Con un entorno que cumple con los [requisitos previos](lookout-mobile-threat-defense-connector.md#prerequisites), es posible integrar Lookout Mobile Endpoint Security con Intune. La información de este artículo lo guiará en la configuración de la integración y de los ajustes importantes de Lookout para usarlo con Intune.  

> [!IMPORTANT]
> No se puede usar un inquilino de Lookout Mobile Endpoint Security existente que no esté asociado ya a su inquilino de Azure AD para la integración con Azure AD e Intune. Póngase en contacto con el servicio de soporte técnico de Lookout para obtener un nuevo inquilino de Lookout Mobile Endpoint Security. Use el nuevo inquilino para incorporar sus nuevos usuarios de Azure AD.

## <a name="collect-azure-ad-information"></a>Recopilar información de Azure AD  
Para integrar Lookout con Intune, asocie su inquilino de Lookout Mobility Endpoint Security con la suscripción de Azure Active Directory (AD).

Para habilitar la integración de la suscripción de Lookout Mobile Endpoint Security con Intune, debe proporcionar la información siguiente al soporte técnico de Lookout (enterprisesupport@lookout.com):  

- **Identificador del directorio del inquilino de Azure AD**  

- El **identificador del objeto del grupo de Azure AD** para el grupo con acceso **total** a la consola de Lookout Mobile Endpoint Security (MES).  
  Puede crear este grupo de usuarios en Azure AD para contener los usuarios con *acceso total* para iniciar sesión en la **consola de Lookout**. Para iniciar sesión en la consola de Lookout, los usuarios deben ser miembros de este grupo o del grupo opcional con *acceso restringido*. 

- El **identificador del objeto del grupo de Azure AD** para el grupo con acceso **restringido** a la consola de Lookout MES *(grupo opcional)* . 
  Puede crear este grupo de usuarios opcional en Azure AD para contener los usuarios que no deberían tener acceso a varios módulos de la consola de Lookout relacionados con la configuración y la inscripción. En su lugar, estos usuarios tienen acceso de solo lectura al módulo **Directiva de seguridad** de la consola de Lookout. Para iniciar sesión en la consola de Lookout, los usuarios deben ser miembros de este grupo opcional o del grupo obligatorio con *acceso total*.

 > [!TIP] 
 > Para obtener más información sobre los permisos, lea [este artículo](https://personal.support.lookout.com/hc/articles/114094105653) en el sitio web de Lookout.

### <a name="collect-information-from-azure-ad"></a>Recopilación de información desde Azure AD 

1. Inicie sesión en [Azure Portal](https://portal.azure.com) con una cuenta de administrador global.

2. Vaya a **Azure Active Directory** > **Propiedades** y busque el **identificador del directorio**. Use el botón *Copiar* para copiar el identificador del directorio y, luego, guárdelo en un archivo de texto.

   ![Propiedades de Azure AD](./media/lookout-mtd-connector-integration/azure-ad-properties.png)  

3. Luego, busque el identificador del grupo de Azure AD de las cuentas que usa para conceder acceso a la consola de Lookout a los usuarios de Azure AD. Un grupo es para el *acceso total* y el segundo grupo, para el *acceso restringido*, es opcional. Para obtener el *identificador del objeto*, en cada cuenta:  
   1. Vaya a **Azure Active Directory** > **Grupos** para abrir el panel *Grupos: todos los grupos*.  

   2. Seleccione el grupo que creó para el *acceso total* para abrir el panel de *Información general* correspondiente.  

   3. Use el botón *Copiar* para copiar el identificador del objeto y, luego, guárdelo en un archivo de texto.  

   4. Repita el proceso para el grupo con *acceso restringido* si usa dicho grupo.  

      ![Identificador del objeto del grupo de Azure AD](./media/lookout-mtd-connector-integration/azure-ad-group-id.png)  

   Una vez que recopile esta información, póngase en contacto con el soporte técnico de Lookout (correo electrónico: enterprisesupport@lookout.com). El soporte técnico de Lookout colaborará con su contacto principal para incorporar su suscripción y crear su cuenta de empresa de Lookout con la información proporcionada.  

## <a name="configure-your-lookout-subscription"></a>Configuración de la suscripción de Lookout  
Una vez que el soporte técnico de Lookout cree su cuenta de empresa de Lookout, el soporte técnico de Lookout enviará un correo electrónico al contacto principal de su empresa con un vínculo a la dirección URL de inicio de sesión: https://aad.lookout.com/les?action=consent. 

### <a name="initial-sign-in"></a>Inicio de sesión inicial  
Cuando se inicia sesión por primera vez en la consola de Lookout MES aparece una página de consentimiento (https://aad.lookout.com/les?action=consent). Un administrador global de Azure AD simplemente inicia la sesión y **acepta**. En los inicios de sesión subsiguientes no será necesario que el usuario tenga este nivel de privilegio de Azure AD. 

 Se muestra una página de consentimiento. Elija **Aceptar** para completar el registro. 
   ![captura de pantalla de la página del primer inicio de sesión en la consola de Lookout](./media/lookout-mtd-connector-integration/lookout_mtp_initial_login.png)

Cuando haya aceptado y dado su consentimiento, se le redirigirá a la consola de Lookout.

Una vez que se completen el inicio de sesión inicial y el consentimiento, a los usuarios que inician sesión desde https://aad.lookout.com se les redirige a la consola de MES. Si todavía no se da el consentimiento, todos los intentos de inicio de sesión generarán un error de inicio de sesión incorrecto.

### <a name="configure-the-intune-connector"></a>Configuración del conector de Intune  
En el procedimiento siguiente se da por supuesto que anteriormente se creó un grupo de usuarios en Azure AD para probar la implementación de Lookout. El procedimiento recomendado es comenzar con un grupo pequeño de usuarios para permitir que los administradores de Lookout y de Intune se familiaricen con las integraciones de los productos. Una vez familiarizados, se puede extender la inscripción a grupos adicionales de usuarios.

1. Inicie sesión en la [consola de Lookout MES](https://aad.lookout.com), vaya a **Sistema** > **Conectores** y, luego, seleccione **Agregar conector**.  Seleccione **Intune**.

   ![Imagen de la consola de Lookout con la pestaña Conectores abierta y la opción Intune](./media/lookout-mtd-connector-integration/lookout_mtp_setup-intune-connector.png)

2. En el panel de *Microsoft Intune*, seleccione **Connection Settings** (Configuración de la conexión) y especifique la **frecuencia de latido** en cuestión de minutos. 

   ![Imagen de la pestaña Configuración de la conexión con la frecuencia de latido configurada](./media/lookout-mtd-connector-integration/lookout-mtp-connection-settings.png)

3. Seleccione **Administración de inscripción** y en **Use the following Azure AD security groups to identify devices that should be enrolled in Lookout for Work** (Usar los grupos de seguridad de Azure AD siguientes para identificar los dispositivos que se deben inscribir en Lookout for Work), especifique el *nombre del grupo* de un grupo de Azure AD para usar con Lookout y, luego, seleccione **Guardar cambios**.

    ![captura de pantalla de la página de inscripción del conector de Intune](./media/lookout-mtd-connector-integration/lookout-mtp-enrollment.png)  

   **Acerca de los grupos que usa**:
   - Como procedimiento recomendado, empiece con un grupo de seguridad de Azure AD que contiene un pequeño número de usuarios para probar la integración de Lookout.
   - El **nombre del grupo** distingue mayúsculas de minúsculas, tal como se muestra en las **propiedades** del grupo de seguridad en Azure Portal.  
   - Los grupos que especifique para la **administración de la inscripción** definen el conjunto de usuarios cuyos dispositivos se inscribirán con Lookout. Cuando un usuario está en un grupo de inscripción, sus dispositivos en Azure AD se inscriben y son aptos para su activación en Lookout MES. La primera vez que un usuario abra la aplicación *Lookout for Work* en un dispositivo compatible, se le pedirá que la active.

4. Seleccione **State Sync** (Sincronización de estado) y asegúrese de que tanto el *estado del dispositivo* como el *estado de la amenaza* estén establecidos en **On** (Activado).  Ambos estados son necesarios para que la integración de Lookout e Intune funcione correctamente.  

5. Seleccione **Error Management** (Administración de errores), especifique la dirección de correo electrónico donde se deben recibir los informes de errores y, luego, seleccione **Guardar cambios**.
 
   ![captura de pantalla de la página de administración de errores del conector de Intune](./media/lookout-mtd-connector-integration/lookout-mtp-connector-error-notifications.png)

6. Seleccione **Crear conector** para completar la configuración del conector. Más adelante, cuando esté satisfecho con los resultados, puede ampliar la inscripción a grupos de usuarios adicionales.

## <a name="configure-intune-to-use-lookout-as-a-mobile-threat-defense-provider"></a>Configuración de Intune para usar Lookout como proveedor de Mobile Threat Defense
Después de configurar Lookout MES, debe configurar una conexión a Lookout en Intune.  

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

2. Vaya a **Cumplimiento de dispositivos** > **Mobile Threat Defense** y seleccione **Agregar**.

3. En el panel *Agregar conector*, use el menú desplegable y seleccione **Lookout for Work**.  

4. Seleccione **Crear**. Una vez que el conector establezca contacto con Lookout MES, la *configuración del conector* queda disponible.

5. Establezca **Enable App Sync for iOS Devices** (Habilitar la sincronización de aplicaciones de dispositivos iOS) en **On** (Activado). 

6. Seleccione **Guardar** para completar la configuración.  Intune y Lookout MES ahora están integrados y listos para usar.


## <a name="additional-settings-in-the-lookout-mes-console"></a>Opciones adicionales de la consola de Lookout MES
Las siguientes son opciones adicionales que se pueden configurar en la consola de Lookout MES.  

### <a name="configure-enrollment-settings"></a>Configuración de las opciones de inscripción
En la consola de Lookout MES, seleccione **Sistema** > **Manage Enrollment** (Administrar la inscripción)  > **Enrollment settings** (Configuración de la inscripción).  

- En **Disconnected Status** (Estado desconectado), especifique el número de días antes de que un dispositivo no conectado se marque como desconectado.  

  Los dispositivos desconectados se consideran no conformes y se les bloqueará el acceso a las aplicaciones de la empresa de acuerdo con las directivas de acceso condicional de Intune. Puede especificar valores entre 1 y 90 días.

  ![Configuración de inscripción de Lookout en el módulo del sistema](./media/lookout-mtd-connector-integration/lookout-console-enrollment-settings.png)

### <a name="configure-email-notifications"></a>Configuración de las notificaciones de correo electrónico
Para recibir corres electrónicos con alertas de amenazas, inicie sesión en la [consola de Lookout MES](https://aad.lookout.com) con la cuenta de usuario que debe recibir las notificaciones.  

- Vaya a **Preferencias** y establezca las notificaciones que quiere recibir en **ON** (Activado). Luego, **guarde** los cambios.  

- Si ya no quiere recibir notificaciones por correo electrónico, establezca las notificaciones en **OFF** (Desactivado) y guarde los cambios.

  ![captura de pantalla de la página de preferencias donde se muestra la cuenta de usuario](./media/lookout-mtd-connector-integration/lookout-mtp-email-notifications.png)



## <a name="configure-threat-classifications"></a>Configuración de las clasificaciones de amenazas  
Lookout Mobile Endpoint Security clasifica las amenazas móviles de diversos tipos. Las clasificaciones de amenazas de Lookout tienen asociados niveles de riesgo predeterminados. Los niveles de riesgo pueden cambiarse en cualquier momento para adaptarse a los requisitos de la empresa.

Para información sobre las clasificaciones de los niveles de amenaza y cómo administrar los niveles de riesgo asociados, consulte la [referencia de Lookout sobre las amenazas](https://enterprise.support.lookout.com/hc/articles/360011812974).

>[!IMPORTANT]
> Los niveles de riesgo son un aspecto importante de Mobile Endpoint Security, ya que la integración de Intune calcula el cumplimiento del dispositivo según estos niveles de riesgo en tiempo de ejecución.  
> 
> El administrador de Intune establece una regla en la directiva para identificar un dispositivo como no conforme si dicho dispositivo presenta una amenaza activa con un nivel mínimo de **Alto**, **Medio** o **Bajo**. La directiva de clasificación de amenazas de Lookout Mobile Endpoint Security determina directamente el cálculo del cumplimiento del dispositivo en Intune.  

## <a name="monitor-enrollment"></a>Supervisión de la inscripción
Una vez que se completa la configuración, Lookout Mobile Endpoint Security empieza a sondear Azure AD en busca de dispositivos que se correspondan con los grupos de inscripción especificados.  Para encontrar información sobre los dispositivos inscritos, puede ir a **Dispositivos** en la consola de Lookout MES.  
- El estado inicial de los dispositivos es *pendiente*.  
- El estado del dispositivo se actualiza una vez que la aplicación *Lookout for Work* se instala, abre y activa en el dispositivo.

Para detalles sobre cómo implementar la aplicación *Lookout for Work* en un dispositivo, consulte [Agregar aplicaciones Lookout for Work con Intune](mtd-apps-ios-app-configuration-policy-add-assign.md).

## <a name="next-steps"></a>Pasos siguientes

[Configurar aplicaciones Lookout](mtd-apps-ios-app-configuration-policy-add-assign.md)
