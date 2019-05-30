---
title: Configuración de la integración de Lookout con Microsoft Intune
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo integrar Intune con Lookout Mobile Threat Defense para controlar el acceso de los dispositivos móviles a los recursos corporativos.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5b0d7644-3183-45ba-a165-0d82d70cb71e
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ffdfd203b2b67a25d5826798d89ae548e33d7756
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66047140"
---
# <a name="set-up-your-lookout-mobile-threat-defense-integration-with-intune"></a>Configurar la integración de Mobile Threat Defense de Lookout con Intune

Los pasos siguientes son necesarios para configurar la suscripción de Mobile Threat Defense de Lookout:

| #        |Paso  |
| ------------- |:-------------|
| 1 | [Recopilar información de Azure AD](#collect-azure-ad-information) |
| 2 | [Configurar la suscripción](#configure-your-subscription) |
| 3 | [Configurar los grupos de inscripción](#configure-enrollment-groups) |
| 4 | [Configurar la sincronización del estado](#configure-state-sync) |
| 5 | [Configurar la información del destinatario de correo electrónico de los informes de error](#configure-error-report-email-recipient-information) |
| 6 | [Configurar las opciones de inscripción](#configure-enrollment-settings) |
| 7 | [Configurar las notificaciones de correo electrónico](#configure-email-notifications) |
| 8 | [Configurar la clasificación de amenazas](#configure-threat-classification) |
| 9 | [Inspección de la inscripción](#watching-enrollment) |

> [!IMPORTANT]
> No se puede usar un inquilino de Lookout Mobile Endpoint Security existente que no esté asociado ya a su inquilino de Azure AD para la integración con Azure AD e Intune. Póngase en contacto con el servicio de soporte técnico de Lookout para obtener un nuevo inquilino de Lookout Mobile Endpoint Security. Use el nuevo inquilino para incorporar sus nuevos usuarios de Azure AD.

## <a name="collect-azure-ad-information"></a>Recopilar información de Azure AD
El inquilino de Lookout Mobility Endpoint Security se asociará a la suscripción a Azure AD para integrar Lookout con Intune. Para habilitar la suscripción al servicio Mobile Threat Defense de Lookout, el soporte técnico de Lookout (enterprisesupport@lookout.com) necesita la siguiente información:

* **Identificador del inquilino de Azure AD**
* **Id. del objeto de grupo de Azure AD** para el acceso **completo** a la consola de Lookout
* El **identificador del objeto de grupo de Azure AD** para el acceso **restringido** a la consola de Lookout (opcional)

Use los pasos siguientes para recopilar la información que debe proporcionar al equipo de soporte técnico de Lookout.

1. Inicie sesión en [Azure Portal](https://portal.azure.com) y seleccione su suscripción. 

2. Cuando elige el nombre de la suscripción, la dirección URL resultante incluye el id. de suscripción.  Si tiene problemas para encontrar el identificador de la suscripción, consulte en este [artículo de soporte técnico de Microsoft](https://support.office.com/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b) sugerencias para encontrarlo.

3. Busque el identificador de grupo de Azure AD. La consola de Lookout admite dos niveles de acceso:  
   * **Acceso completo:** el administrador de Azure AD puede crear un grupo para los usuarios que tengan acceso total y, opcionalmente, crear un grupo para los usuarios que tengan acceso restringido.  Solo los usuarios de estos grupos podrán iniciar sesión en la **consola de Lookout**.
   * **Acceso restringido:** los usuarios de este grupo no tienen acceso a varios módulos relacionados con la configuración y la inscripción de la consola de Lookout. Únicamente tienen acceso de solo lectura al módulo **Directiva de seguridad** de la consola de Lookout.  

     > [!TIP] 
     > Para obtener más información sobre los permisos, lea [este artículo](https://personal.support.lookout.com/hc/articles/114094105653) en el sitio web de Lookout.

     > [!NOTE] 
     > El **identificador del objeto de grupo** se encuentra en la página **Propiedades** del grupo en el **portal de administración de Azure AD**.

4. Una vez que haya recopilado esta información, póngase en contacto con el soporte técnico de Lookout (correo electrónico: enterprisesupport@lookout.com). El soporte técnico de Lookout colaborará con su contacto principal para incorporar su suscripción y crear su cuenta de empresa de Lookout con la información recopilada.

## <a name="configure-your-subscription"></a>Configurar la suscripción

1. Después de que el soporte técnico de Lookout cree su cuenta de empresa de Lookout, Lookout envía un correo electrónico al contacto principal de su empresa con un vínculo a la dirección URL de inicio de sesión:<https://aad.lookout.com/les?action=consent>.

2. El primer inicio de sesión en la consola de Lookout debe realizarse con una cuenta de usuario con el rol de Azure AD de administrador global para registrar el inquilino de Azure AD. Después, el inicio de sesión no necesita este nivel de privilegio de Azure AD. Se muestra una página de consentimiento. Elija **Aceptar** para completar el registro. Una vez que haya aceptado y dado su consentimiento, se le redirige a la consola de Lookout.

   ![captura de pantalla de la página del primer inicio de sesión en la consola de Lookout](./media/lookout_mtp_initial_login.png)

3. En la [consola de Lookout](https://aad.lookout.com), en el módulo **Sistema**, elija la pestaña **Conectores** y seleccione **Intune**.

   ![Imagen de la consola de Lookout con la pestaña Conectores abierta y la opción Intune](./media/lookout_mtp_setup-intune-connector.png)

4. Vaya a **Conectores** > **Configuración de conexión** y especifique la **Frecuencia de latido** en minutos.

   ![Imagen de la pestaña Configuración de la conexión con la frecuencia de latido configurada](./media/lookout-mtp-connection-settings.png)

## <a name="configure-enrollment-groups"></a>Configurar los grupos de inscripción
1. Como procedimiento recomendado, cree un grupo de seguridad de Azure AD en el [Portal de administración de Azure AD](https://manage.windowsazure.com) que contenga un número pequeño de usuarios para probar la integración de Lookout.

    > [!NOTE] 
    > Todos los dispositivos inscritos en Intune y admitidos en Lookout de usuarios de un grupo de inscripción en Azure AD que se identifican y se admiten, se inscriben y son aptos para la activación en la consola de MTD de Lookout.

2. En la [consola de Lookout](https://aad.lookout.com), en el módulo **System** (System), elija la pestaña **Connectors** (Conectores) y seleccione **Enrollment Management** (Administración de inscripciones) para definir un conjunto de usuarios cuyos dispositivos se deban inscribir en Lookout. Agregue el **Nombre para mostrar** del grupo de seguridad de Azure AD para la inscripción.

    ![captura de pantalla de la página de inscripción del conector de Intune](./media/lookout-mtp-enrollment.png)

    >[!IMPORTANT]
    > El **Nombre para mostrar** distingue mayúsculas de minúsculas, tal como se muestra en la página **Propiedades** del grupo de seguridad en Azure Portal. Como se muestra en la imagen siguiente, el **Nombre para mostrar** del grupo de seguridad utiliza mayúsculas y minúsculas, mientras que el título está todo en minúsculas. En la consola de Lookout deben coincidir las mayúsculas y minúsculas del **Nombre para mostrar** con el grupo de seguridad.
    >![Imagen de Azure Portal, página de propiedades del servicio de Azure Active Directory](./media/aad-group-display-name.png)

    >[!NOTE] 
    >Se recomienda usar el valor predeterminado (5 minutos) como incremento para buscar nuevos dispositivos. Limitaciones actuales, **Lookout no puede validar los nombres para mostrar de grupos:** Asegúrese de que el campo **NOMBRE PARA MOSTRAR** de Azure Portal coincide exactamente con el grupo de seguridad de Azure AD. **No se admite la creación de grupos anidados:**  Los grupos de seguridad de Azure AD que se usan en Lookout solo deben contener usuarios. No pueden contener otros grupos.

3.  Una vez que se agrega un grupo, la próxima vez que un usuario abre la aplicación Lookout for Work en un dispositivo compatible, el dispositivo se activa en Lookout.

4.  Cuando esté satisfecho con los resultados, amplíe la inscripción a grupos de usuarios adicionales.

## <a name="configure-state-sync"></a>Configurar la sincronización del estado
En la opción **State Sync** (Sincronización del estado), especifique el tipo de datos que se enviarán a Intune.  El estado del dispositivo y el estado de amenaza son necesarios para que la integración de Lookout de Intune funcione correctamente. Estas opciones están habilitadas de manera predeterminada.

## <a name="configure-error-report-email-recipient-information"></a>Configurar la información del destinatario de correo electrónico de los informes de error
En la opción **Error Management** (Administración de errores), escriba la dirección de correo electrónico que debe recibir los informes de error.

![captura de pantalla de la página de administración de errores del conector de Intune](./media/lookout-mtp-connector-error-notifications.png)

## <a name="configure-enrollment-settings"></a>Configurar las opciones de inscripción
En el módulo **Sistema**, en la página **Conectores**, especifique el número de días antes de que un dispositivo se considere como desconectado.  Los dispositivos desconectados se consideran no conformes y se les bloqueará el acceso a las aplicaciones de la empresa de acuerdo con las directivas de acceso condicional de Intune. Puede especificar valores entre 1 y 90 días.

![Configuración de inscripción de Lookout en el módulo del sistema](./media/lookout-console-enrollment-settings.png)

## <a name="configure-email-notifications"></a>Configurar las notificaciones de correo electrónico
Si quiere recibir alertas de correo electrónico sobre las amenazas, inicie sesión en la [consola de Lookout](https://aad.lookout.com) con la cuenta de usuario que debe recibir notificaciones. En la pestaña **Preferencias** del módulo **Sistema**, elija los niveles de amenaza de las notificaciones y configúrelos como **ACTIVADO**. Guarde los cambios.

![captura de pantalla de la página de preferencias en la que se muestra la cuenta de usuario](./media/lookout-mtp-email-notifications.png) Si ya no quiere recibir notificaciones por correo electrónico, configure las notificaciones como **DESACTIVADO** y guarde los cambios.

### <a name="configure-threat-classification"></a>Configurar la clasificación de amenazas
Mobile Threat Defense de Lookout clasifica amenazas móviles de diversos tipos. Las [clasificaciones de amenazas de Lookout](https://personal.support.lookout.com/hc/articles/114094130693) tienen asociados niveles de riesgo predeterminados. Estos pueden cambiarse en cualquier momento para cumplir los requisitos de la empresa.

![captura de pantalla de la página de directivas en la que se muestran amenazas y clasificaciones](./media/lookout-mtp-threat-classification.png)

>[!IMPORTANT]
> Los niveles de riesgo son un aspecto importante de Mobile Threat Defense, ya que la integración de Intune calcula el cumplimiento del dispositivo según estos niveles de riesgo en tiempo de ejecución. El administrador de Intune establece una regla en la directiva para identificar un dispositivo como no conforme si dicho dispositivo presenta una amenaza activa con un nivel mínimo de **Alto**, **Medio** o **Bajo**. La directiva de clasificación de amenazas de Mobile Threat Defense de Lookout determina directamente el cálculo del cumplimiento del dispositivo en Intune.

## <a name="watching-enrollment"></a>Inspección de la inscripción
Una vez completada la configuración, Mobile Threat Defense de Lookout empieza a sondear Azure AD en busca de dispositivos que se correspondan con los grupos de inscripción especificados.  Encontrará información sobre los dispositivos inscritos en el módulo Dispositivos.  El estado inicial de los dispositivos se muestra como pendiente.  El estado del dispositivo cambia después de que la aplicación Lookout for Work se haya instalado, abierto y activado en el dispositivo.  Para obtener más información sobre cómo insertar la aplicación Lookout for Work en el dispositivo, vea [Agregar aplicaciones Lookout for Work con Intune](mtd-apps-ios-app-configuration-policy-add-assign.md).

## <a name="next-steps"></a>Pasos siguientes

[Configurar aplicaciones Lookout](mtd-apps-ios-app-configuration-policy-add-assign.md)
