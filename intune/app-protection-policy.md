---
title: ¿Qué son las directivas de protección de aplicaciones?
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo las directivas de protección de aplicaciones de Microsoft Intune ayudan a proteger los datos de su empresa y evitan la pérdida de datos.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, get-started, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 45e9f50881ff7da0554a4731712441b5fedb01d8
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "59569420"
---
# <a name="what-are-app-protection-policies"></a>¿Qué son las directivas de protección de aplicaciones?


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Las directivas de protección de aplicaciones de Microsoft Intune ayudan a proteger los datos de empresa y evitan la pérdida de datos.

## <a name="how-you-can-protect-app-data"></a>Cómo puede proteger los datos de la aplicación
Los empleados usan dispositivos móviles para tareas personales y de trabajo. Mientras se asegura de que los empleados pueden ser productivos, puede evitar la pérdida de datos, ya sea intencional o involuntaria. También conviene proteger los datos de empresa que son accesibles desde dispositivos que no están administrados por usted.

Puede usar directivas de protección de aplicaciones de Intune **independientemente de cualquier otra solución de administración de dispositivos móviles (MDM)**. Esta independencia le ayuda a proteger los datos de su empresa con o sin inscripción de dispositivos en una solución de administración de dispositivos. Mediante la implementación de **directivas de nivel de aplicación**, puede restringir el acceso a los recursos de la empresa y mantener los datos dentro del ámbito del departamento de TI.

Se pueden configurar directivas de protección de aplicaciones para aplicaciones que se ejecutan en dispositivos:

- **Inscritos en Microsoft Intune:** estos dispositivos suelen ser propiedad de la empresa.

- **Inscritos en una solución de administración de dispositivos móviles (MDM) de terceros:** estos dispositivos suelen ser propiedad de la empresa.

  > [!NOTE]
  > Las directivas de administración de la aplicaciones móviles no deben usarse con soluciones de contenedor seguro ni de administración de aplicaciones móviles de terceros.

- **No inscritos en ninguna solución de administración de dispositivos móviles:** los dispositivos normalmente son dispositivos de empleados que no están administrados ni inscritos en Intune ni en ninguna otra solución MDM.

> [!IMPORTANT]
> Puede crear directivas de administración de aplicaciones móviles para aplicaciones móviles de Office que se conectan a servicios de Office 365. También puede proteger el acceso a los buzones locales de Exchange mediante la creación de directivas de protección de aplicaciones de Intune para Outlook para iOS y Android habilitadas con autenticación moderna híbrida. Antes de usar esta característica, asegúrese de cumplir los [requisitos de Outlook para iOS y Android](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx). Las directivas de protección de aplicaciones no son compatibles con otras aplicaciones que se conectan a los servicios de Exchange o SharePoint locales.

**Las ventajas más importantes del uso de directivas de protección de aplicaciones son**:

-   Protección de datos de su compañía a nivel de aplicación. Puesto que la administración de aplicaciones móviles no requiere la administración de dispositivos, puede proteger los datos de la empresa en dispositivos administrados y no administrados. La administración se centra en la identidad del usuario, lo que elimina la necesidad de administrar dispositivos.

-   La productividad del usuario final no se ve afectada y no se aplican las directivas cuando se usa la aplicación en un contexto personal. Las directivas se aplican solo en un contexto de trabajo, lo que le ofrece la capacidad de proteger los datos de la compañía sin tocar los datos personales.

Hay otras ventajas derivadas del uso de MDM con directivas de protección de aplicaciones, y las empresas pueden usar estas directivas con o sin MDM al mismo tiempo. Por ejemplo, piense el caso de un empleado que utiliza tanto un teléfono proporcionado por la empresa como su propia tableta personal. El teléfono de la empresa está inscrito en MDM y está protegido por directivas de protección de aplicaciones, mientras que el dispositivo personal está protegido únicamente por directivas de protección de aplicaciones.

- **MDM garantiza que el dispositivo esté protegido**. Por ejemplo, puede solicitar un PIN para acceder al dispositivo o puede implementar aplicaciones administradas en el dispositivo. También puede implementar aplicaciones en dispositivos a través de la solución MDM para proporcionarle más control sobre la administración de aplicaciones.

- **Las directivas de protección de aplicaciones garantizan que las protecciones de la capa de aplicaciones estén establecidas**. Por ejemplo, puede:
  - Solicitar un PIN para abrir una aplicación en un contexto de trabajo 
  - Controlar el uso compartido de datos entre aplicaciones 
  - Impedir el almacenamiento de datos de la aplicación de empresa en una ubicación de almacenamiento personal


### <a name="supported-platforms-for-app-protection-policies"></a>Plataformas admitidas para directivas de protección de aplicaciones
La compatibilidad de plataformas de directivas de aplicaciones de Intune está alineada con la compatibilidad de plataformas de aplicaciones móviles de Office para dispositivos Android e iOS. Para obtener más información, consulte la sección **Aplicaciones móviles** de [Requisitos del sistema de Office](https://products.office.com/office-system-requirements#coreui-contentrichblock-9r05pwg).

> [!IMPORTANT]
> Es necesario que el Portal de empresa de Intune se encuentre en el dispositivo para recibir las directivas de protección de aplicación en Android. Para más información, consulte los [requisitos de las aplicaciones de acceso al Portal de empresa de Intune](end-user-mam-apps-android.md#access-apps).

## <a name="how-app-protection-policies-protect-app-data"></a>Protección de datos de una aplicación con directivas de protección de aplicaciones

#### <a name="apps-without-app-protection-policies"></a>Aplicaciones sin directivas de protección de aplicaciones

![Imagen conceptual de movimiento de datos entre aplicaciones sin ninguna directiva en vigor](./media/apps-without-protection-policies.png)

Cuando se usan aplicaciones sin restricciones, se pueden entremezclar los datos empresariales y personales. Los datos de la compañía pueden acabar en ubicaciones como el almacenamiento personal o transferirse a aplicaciones fuera de su ámbito y provocar una pérdida de datos. Las flechas del diagrama anterior muestran el movimiento sin restricciones de los datos entre aplicaciones (personales y corporativas) y hacia ubicaciones de almacenamiento.


### <a name="data-protection-with-app-protection-policies"></a>Protección de datos con directivas de protección de aplicaciones

![Imagen conceptual que muestra la datos de la compañía protegidos por directivas](./media/apps-with-protection-policies.png)


Puede usar directivas de protección de aplicaciones para evitar que los datos de empresa se guarden en el almacenamiento local del dispositivo. También puede restringir el movimiento de datos a otras aplicaciones que no estén protegidas por directivas de protección. La configuración de directivas de protección de aplicaciones incluyen:
- Directivas de reubicación de datos como **Impedir "Guardar como"**, **Restringir cortar, copiar y pegar**.
- Opciones de directivas de acceso como **Requerir PIN sencillo para el acceso**, **Bloquear las aplicaciones administradas para que no se ejecuten en dispositivos con jailbreak o rooting**.

### <a name="data-protection-with-app-protection-policies-on-devices-managed-by-a-mobile-device-management-solution"></a>Protección de datos con directivas de protección de aplicaciones en dispositivos administrados por una solución de administración de dispositivos móviles

![Imagen que muestra cómo funcionan las directivas de protección de aplicaciones en dispositivos BYOD.](./media/app-protection-policies-with-mdm.png)

**En dispositivos inscritos en una solución MDM**-

En la ilustración anterior se muestran las capas de protección que ofrecen juntas las directivas MDM y las directivas de protección de aplicaciones.

La solución MDM:

-   Inscribe el dispositivo.

-   Implementa las aplicaciones en el dispositivo

-   Proporciona administración y conformidad continua de los dispositivos

**Las directivas de protección de aplicaciones agregan valor:**

-   Ayudando a evitar la fuga de datos de la compañía a aplicaciones y servicios de consumidor

-   Aplicando restricciones (*Guardar como*, *Portapapeles*, *PIN*, etc.) a las aplicaciones cliente

-   Borrar datos de compañía de las aplicaciones sin borrar esas aplicaciones del dispositivo


### <a name="data-protection-with-app-protection-policies-for-devices-without-enrollment"></a>Protección de datos con directivas de protección de aplicaciones para dispositivos sin inscripción

![Imagen que muestra cómo funcionan las directivas de protección de aplicaciones en dispositivos administrados.](./media/app-protection-policies-without-mdm.png)

En el diagrama anterior se muestra cómo funcionan las directivas de protección de datos en el nivel de aplicación sin MDM.

En dispositivos BYOD no inscritos en ninguna solución MDM, las directivas de protección de aplicaciones pueden ayudar a proteger los datos de la compañía a nivel de aplicación.
Sin embargo, existen algunas limitaciones que se deben tener en cuenta, como:

-   No se puede implementar aplicaciones en el dispositivo. El usuario final debe obtener las aplicaciones del almacén.

-   No se puede proporcionar perfiles de certificados en estos dispositivos.

-   No se puede proporcionar configuraciones de Wi-Fi y VPN de compañía en estos dispositivos.

## <a name="app-protection-global-policy"></a>Directiva global de protección de aplicaciones

Si un administrador de OneDrive navega a **admin.office.com** y selecciona el acceso **Dispositivo**, podrá establecer los controles **Administración de aplicaciones móviles** en las aplicaciones cliente de OneDrive y SharePoint. 

La configuración, disponible en la consola de administración de OneDrive, establece una directiva de protección de aplicaciones de Intune especial llamada **Global**. Esta directiva global se aplica a todos los usuarios de su inquilino y no tiene forma de controlar los destinos de la directiva. 

Una vez habilitada, las aplicaciones de OneDrive y SharePoint para iOS y Android están protegidas con la configuración seleccionada de forma predeterminada. Un profesional de TI puede editar esta directiva en la consola de Intune y agregar más aplicaciones de destino y modificar cualquier configuración de directiva. 

De forma predeterminada, solo puede haber una directiva **Global** por inquilino, aunque puede usar una [Graph API de Intune](intune-graph-apis.md) para crear otras directivas globales por inquilino, aunque no se recomienda, dado que puede ser complicado solucionar problemas en la implementación de esta directiva.

Si bien la directiva **Global** se aplica a todos los usuarios del inquilino, cualquier directiva estándar de protección de aplicaciones de Intune anulará esta configuración.


## <a name="multi-identity"></a>Varias identidades

Las aplicaciones que admiten varias identidades permiten usar diferentes cuentas (profesionales y personales) para obtener acceso a las mismas aplicaciones, aunque las directivas de protección de aplicaciones se aplican solo cuando las aplicaciones se usen en el contexto laboral.

Como ejemplo de contexto personal, piense en un usuario que empieza un documento nuevo en Word: esto se considera contexto personal por lo que no se aplican las directivas Intune App Protection. Una vez que el documento se guarda en la cuenta corporativa de OneDrive, se le considerará como contexto corporativo y se aplicarán las directivas Intune App Protection.

Como ejemplo de contexto de trabajo, piense en un usuario que inicia la aplicación OneDrive con su cuenta profesional. En el contexto de trabajo, no puede mover los archivos a una ubicación de almacenamiento personal. Más adelante, cuando usa OneDrive con su cuenta personal, puede copiar y mover los datos de su OneDrive personal sin restricciones.

- Obtenga más información sobre las aplicaciones que admiten [MAM y varias identidades](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) con Intune.

## <a name="next-steps"></a>Pasos siguientes

[Creación e implementación de directivas de protección de aplicaciones con Microsoft Intune](app-protection-policies.md)

## <a name="see-also"></a>Consulte también
Las aplicaciones de terceros, como la aplicación móvil de Salesforce, funcionan con Intune de formas específicas para proteger los datos corporativos. Para más información sobre cómo la aplicación de Salesforce funciona con Intune en particular (incluida la configuración de la aplicación de MDM), vea [Salesforce App and Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf) (Aplicación de Salesforce y Microsoft Intune).
