---
title: "Configurar la suscripción con Lookout | Microsoft Intune"
description: "En este tema se proporciona información sobre cómo configurar la protección contra amenazas de dispositivo de Lookout."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 8477a2f1-2e1d-4d42-8bcb-e1181cc900bb
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: de65f43ac83b25fa2dd1dacd2a7807668c2b6e9a
ms.openlocfilehash: fa3230e1faf24bdbbd7e84a211ca95c1fd0fadfd


---

# Configurar la suscripción para la protección contra amenazas de dispositivo de Lookout
Para preparar la suscripción para el servicio de protección contra amenazas de dispositivo de Lookout, el soporte técnico de Lookout (enterprisesupport@lookout.com) necesita la siguiente información sobre su suscripción de Azure Active Directory (Azure AD). 

* **El identificador del inquilino de Azure AD**
* El **identificador del objeto de grupo de Azure AD** para el acceso **completo** a la consola de Lookout
* El **identificador del objeto de grupo de Azure AD** para el acceso **restringido** a la consola de Lookout (opcional)

Use la sección siguiente para recopilar la información que debe proporcionar al equipo de soporte técnico de Lookout.  

## Obtener la información de Azure AD
### El identificador del inquilino de Azure AD
Inicie sesión en el [Portal de administración de Azure AD](https://manage.windowsazure.com) y seleccione su suscripción. 

![captura de pantalla de la página de Azure AD que muestra el nombre del inquilino](../media/mtp/aad_tenant_name.png) Cuando elija el nombre de la suscripción, la dirección URL resultante incluirá el identificador de la suscripción.  Si tiene problemas para encontrar el identificador de la suscripción, consulte en este [artículo de soporte técnico de Microsoft](https://support.office.com/en-us/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b?ui=en-US&rs=en-US&ad=US) sugerencias para encontrarlo.   
### Identificador de grupo de Azure AD
La consola de Lookout admite dos niveles de acceso:  
* **Acceso completo:** el administrador de Azure AD puede crear un grupo para los usuarios que tendrán acceso total y, opcionalmente, crear un grupo para los usuarios que tendrán acceso restringido.  Solo los usuarios de estos grupos podrán iniciar sesión en la **consola de Lookout**.
* **Acceso restringido:** los usuarios de este grupo no tienen acceso a varios módulos relacionados con la configuración y la inscripción de la consola de Lookout. Únicamente tienen acceso de solo lectura al módulo **Directiva de seguridad** de la consola de Lookout.  

Para obtener más información sobre los permisos, lea [este artículo](https://personal.support.lookout.com/hc/en-us/articles/114094105653) en el sitio web de Lookout.

El **identificador del objeto de grupo** se encuentra en la página **Propiedades** del grupo en la **consola de administración de Azure AD**.

![captura de pantalla de la página de propiedades con el campo GroupID resaltado](../media/mtp/aad_group_object_id.png)

Una vez que haya recopilado esta información, póngase en contacto con el soporte técnico de Lookout (correo electrónico: enterprisesupport@lookout.com).

El soporte técnico de Lookout colaborará con su contacto principal para incorporar su suscripción y crear su cuenta de empresa de Lookout con la información recopilada.


## Configurar la suscripción con protección contra amenazas de dispositivo de Lookout
### Paso 1: configurar la protección contra amenazas de dispositivo
Cuando el soporte técnico de Lookout haya creado su cuenta de empresa de Lookout, podrá iniciar sesión en la consola de Lookout.   Lookout envía un correo electrónico al contacto principal de su empresa con un vínculo a la dirección URL de inicio de sesión https://aad.lookout.com/les?action=consent.

Debe usar una cuenta de usuario con el rol de Azure AD de administrador global cuando inicie sesión por primera vez en la consola de Lookout, ya que Lookout necesita esta información para registrar el inquilino de Azure AD.   En los inicios de sesión posteriores no será necesario que el usuario tenga este nivel de privilegios de Azure AD.  En este primer inicio de sesión, se muestra una página de consentimiento. Elija **Aceptar** para completar el registro.

![captura de pantalla de la página del primer inicio de sesión de la consola de Lookout](../media/mtp/lookout_mtp_initial_login.png) Una vez que haya aceptado y haya dado su consentimiento, se le redirigirá a la consola de Lookout. Los inicios de sesión posteriores al registro inicial se pueden hacer a través de la dirección URL https://aad.lookout.com.

Consulte el [artículo de solución de problemas](https://docs.microsoft.com/en-us/intune/troubleshoot/troubleshooting-lookout-integration) si tiene problemas de inicio de sesión.

En los pasos siguientes se describen las tareas que se deben realizar para completar la configuración de Lookout en la [consola de Lookout](https://aad.lookout.com).

### Paso 2: configurar el conector de Intune

1.  En la consola de Lookout, en el módulo **Sistema**, elija la pestaña **Conectores** y seleccione **Intune**.

  ![captura de pantalla de la consola de Lookout con la pestaña Conectores abierta y la opción Intune resaltada](../media/mtp/lookout_mtp_setup-intune-connector.png)

2.  En la opción de configuración de la conexión, configure la frecuencia de latido en minutos.  El conector de Intune ya está listo.  

  ![captura de pantalla de la pestaña de configuración de la conexión en la que se muestra la frecuencia de latido configurada](../media/mtp/lookout-mtp-connection-settings.png)

### Paso 3: configurar los grupos de inscripción
En la opción **Enrollment Management** (Administración de inscripciones), defina un conjunto de usuarios cuyos dispositivos deban inscribirse con Lookout. Se recomienda empezar con un pequeño grupo de usuarios para probar y familiarizarse con el funcionamiento de la integración.  Una vez que esté satisfecho con los resultados de la prueba, puede ampliar la inscripción a más grupos de usuarios.

Para empezar a trabajar con grupos de inscripciones, defina primero un grupo de seguridad de Azure AD que considere un buen conjunto inicial de usuarios para inscribirlos en la protección contra amenazas de dispositivo de Lookout. Una vez que el grupo esté creado en Azure AD, en la consola de Lookout, vaya a la opción **Enrollment Management** (Administración de inscripciones) y agregue el grupo de seguridad de Azure AD **Display Name(s)** (Nombres para mostrar) para la inscripción.

Cuando un usuario se encuentra en un grupo de inscripción, todos sus dispositivos que se identifican y se admiten en Azure AD se inscriben y son aptos para la activación en la protección contra amenazas de dispositivo de Lookout.  La primera vez que abre la aplicación Lookout for Work en un dispositivo compatible, el dispositivo se activa en Lookout.

![captura de pantalla de la página de inscripción del conector de Intune](../media/mtp/lookout-mtp-enrollment.png)

Se recomienda usar el valor predeterminado (5 minutos) como incremento para buscar nuevos dispositivos.

>[!IMPORTANT]
> El nombre para mostrar distingue mayúsculas de minúsculas.  Use el **Nombre para mostrar** tal como se muestra en la página **Propiedades** del grupo de seguridad en Azure Portal. Observe en la imagen siguiente de la página **Propiedades** del grupo de seguridad que el nombre para mostrar aparece en mayúsculas y minúsculas.  En cambio, el título se muestra todo en minúsculas y no se debe usar para escribirlo en la consola de Lookout.
>![captura de pantalla de Azure Portal, página de propiedades del servicio de Azure Active Directory](../media/mtp/aad-group-display-name.png)

La versión actual tiene las limitaciones siguientes:  
* No se realiza ninguna validación de los nombres para mostrar del grupo.  Asegúrese de usar el valor del campo **NOMBRE PARA MOSTRAR** que aparece en Azure Portal para el grupo de seguridad de Azure AD.
* Actualmente no se admite la creación de grupos dentro de grupos.  Los grupos de seguridad de Azure AD especificados solo pueden contener usuarios y no grupos anidados.


### Paso 4: configurar la sincronización del estado
En la opción **State Sync** (Sincronización del estado), especifique el tipo de datos que se enviarán a Intune.  Actualmente, debe habilitar el estado del dispositivo y el estado de amenaza para que la integración de Lookout e Intune funcione correctamente.  Están habilitados de forma predeterminada.
### Paso 5: configurar la información del destinatario de correo electrónico de los informes de error
En la opción **Error Management** (Administración de errores), escriba la dirección de correo electrónico que debe recibir los informes de error.

![captura de pantalla de la página de administración de errores del conector de Intune](../media/mtp/lookout-mtp-connector-error-notifications.png)

### Paso 6. Configurar las opciones de inscripción
En el módulo **Sistema**, en la página **Conectores**, especifique el número de días antes de que un dispositivo se considere como desconectado.  Los dispositivos desconectados se consideran como no conforme y se les bloqueará el acceso a las aplicaciones de empresa basadas en las directivas de acceso condicional de Intune. Puede especificar valores entre 1 y 90 días.

![](../media/mtp/lookout-console-enrollment-settings.png)

### Paso 7: Configurar notificaciones de correo electrónico
Si quiere recibir alertas de correo electrónico sobre las amenazas, inicie sesión en la [consola de Lookout](https://aad.lookout.com) con la cuenta de usuario que debe recibir las notificaciones. En la pestaña **Preferencias** del módulo **Sistema**, elija las notificaciones deseadas y configúrelas como **ACTIVADO**. Guarde los cambios.

![captura de pantalla de la página de preferencias en la que se muestra la cuenta de usuario](../media/mtp/lookout-mtp-email-notifications.png) Si ya no quiere recibir notificaciones por correo electrónico, configure las notificaciones como **DESACTIVADO** y guarde los cambios.
### Paso 8: Configurar la clasificación de amenazas
La protección contra amenazas de dispositivo de Lookout clasifica amenazas móviles de diversos tipos. Las [clasificaciones de amenazas de Lookout](http://personal.support.lookout.com/hc/en-us/articles/114094130693) tienen asociados niveles de riesgo predeterminados. Estos pueden cambiarse en cualquier momento de acuerdo con los requisitos de la empresa.

![captura de pantalla de la página de directivas en la que se muestran amenazas y clasificaciones](../media/mtp/lookout-mtp-threat-classification.png)

>[!IMPORTANT]
> Los niveles de riesgo especificados aquí son un aspecto importante de la protección contra amenazas de dispositivo, ya que la integración de Intune calcula el cumplimiento del dispositivo según estos niveles de riesgo en tiempo de ejecución. Dicho de otro modo, el administrador de Intune establece una regla en la directiva para identificar un dispositivo como no conforme si dicho dispositivo tiene una amenaza activa con un nivel mínimo alto, medio o bajo. La directiva de clasificación de amenazas de la protección contra amenazas de dispositivo de Lookout determina directamente el cálculo del cumplimiento del dispositivo en Intune.

## Inspección de la inscripción
Una vez completada la configuración, la protección contra amenazas de dispositivo de Lookout empieza a sondear Azure AD en busca de dispositivos que se correspondan con los grupos de inscripción especificados.  Encontrará información sobre los dispositivos inscritos en el módulo Dispositivos.  El estado inicial de los dispositivos se muestra como pendiente.  El estado del dispositivo cambia después de que la aplicación Lookout for Work se haya instalado, abierto y activado en el dispositivo.  Para obtener más información sobre cómo insertar la aplicación Lookout for Work en el dispositivo, consulte el tema [Configurar e implementar aplicaciones Lookout for Work](configure-and-deploy-lookout-for-work-apps.md).
## Pasos siguientes
[Habilitar la conexión de Lookout MTP en Intune](enable-lookout-mtp-connection-in-intune.md)



<!--HONumber=Oct16_HO2-->


