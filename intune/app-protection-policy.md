---
title: "¿Qué son las directivas de protección de aplicaciones?"
titleSuffix: Azure portal
description: "Use este tema para aprender a proteger los datos de empresa con directivas de protección de aplicaciones de Microsoft Intune."
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 01/19/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a6645261e2a90ea3890dc22b42fe65d6af4af6e5
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="what-are-app-protection-policies"></a>¿Qué son las directivas de protección de aplicaciones?


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Las directivas de protección de aplicaciones de Microsoft Intune ayudan a proteger los datos de empresa y evitan la pérdida de datos.

## <a name="how-you-can-protect-app-data"></a>Cómo puede proteger los datos de la aplicación
Los empleados usan dispositivos móviles para tareas personales y de trabajo.  Mientras se asegura de que los empleados pueden ser productivos, también puede evitar la pérdida de datos, ya sea intencional o involuntaria.  Además, quiere tener la capacidad de proteger los datos de la empresa a los que se accede mediante dispositivos (incluso aquellos datos que usted no administre).

Puede usar directivas de protección de aplicaciones de Intune para ayudar a proteger los datos de su empresa. Dado que las directivas de protección de aplicaciones se pueden usar **independientemente de cualquier solución de administración de dispositivos móviles (MDM)**, puede usarlas para proteger los datos de la empresa con o sin inscripción de los dispositivos en una solución de administración de dispositivos. Mediante la implementación de **directivas de nivel de aplicación**, puede restringir el acceso a los recursos de la empresa y mantener los datos dentro del ámbito del departamento de TI.

Se pueden configurar directivas de protección de aplicaciones para aplicaciones que se ejecutan en dispositivos que están:

- **Inscritos en Microsoft Intune:** los dispositivos de esta categoría son normalmente dispositivos corporativos.

-   **Inscritos en una solución de administración de dispositivos móviles (MDM) de otro fabricante:** los dispositivos de esta categoría son normalmente dispositivos corporativos.

  > [!NOTE]
  > Las directivas de administración de la aplicaciones móviles no deben usarse con soluciones de contenedor seguro ni de administración de aplicaciones móviles de terceros.

-   **No inscritos en ninguna solución de administración de dispositivos móviles:** los dispositivos de esta categoría normalmente son dispositivos de empleados no administrados ni inscritos en Intune ni en ninguna otra solución MDM.

> [!IMPORTANT]
> Puede crear directivas de administración de aplicaciones móviles para aplicaciones móviles de Office que se conectan a servicios de Office 365. Las directivas de protección de aplicaciones no son compatibles con las aplicaciones que se conectan a los servicios de Exchange o SharePoint locales.

**Las ventajas más importantes del uso de directivas de protección de aplicaciones son:**

-   Protección de datos de su compañía a nivel de aplicación.  Puesto que la administración de aplicaciones móviles no requiere la administración de dispositivos, puede proteger los datos de la empresa en dispositivos administrados y no administrados. La administración se centra en la identidad del usuario, lo que elimina la necesidad de administrar dispositivos.

-   La productividad del usuario final no se ve afectada y no se aplican las directivas cuando se usa la aplicación en un contexto personal.  Las directivas se aplican solo en un contexto de trabajo, lo cual le ofrece la capacidad de proteger los datos de la compañía sin tocar los datos personales.

Hay otras ventajas derivadas del uso de MDM con directivas de protección de aplicaciones, y las empresas pueden usar estas directivas con o sin MDM al mismo tiempo. Por ejemplo, un empleado puede usar un teléfono de la compañía, así como una tableta personal.  En este caso, el teléfono de la empresa está inscrito en MDM y está protegido por directivas de protección de aplicaciones, y el dispositivo personal está protegido únicamente por directivas de protección de aplicaciones.

- **MDM garantiza que el dispositivo esté protegido**.  Por ejemplo, puede solicitar un PIN para acceder al dispositivo o puede implementar aplicaciones administradas en el dispositivo. También puede implementar aplicaciones en dispositivos a través de la solución MDM para proporcionarle más control sobre la administración de aplicaciones.

- **Las directivas de protección de aplicaciones garantizan que las protecciones de la capa de aplicaciones estén establecidas**. Por ejemplo, puede solicitar un PIN para abrir una aplicación en un contexto de trabajo, o si se pueden compartidos datos entre aplicaciones, o evitar el almacenamiento de datos de aplicaciones de la compañía en una ubicación de almacenamiento personal.


### <a name="supported-platforms-for-app-protection-polices"></a>Plataformas admitidas para directivas de protección de aplicaciones
-   iOS 9 o posterior
-   Android 4.4 o posterior

Los dispositivos Windows no son compatibles actualmente. En cambio, cuando inscribe los dispositivos Windows 10 en Intune, puede usar Windows Information Protection, ya que ofrece una funcionalidad similar. Para obtener más información, vea [Protege los datos de su empresa con Windows Information Protection (WIP)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).
##  <a name="how-app-protection-policies-protect-app-data"></a>Protección de datos de una aplicación con directivas de protección de aplicaciones

####  <a name="apps-without-app-protection-policies"></a>Aplicaciones sin directivas de protección de aplicaciones

![Imagen que muestra que los datos se pueden mover libremente entre aplicaciones cuando no hay ninguna directiva de protección de aplicaciones establecida.](./media/apps-without-protection-policies.png)

Cuando se usan aplicaciones sin restricciones, se pueden entremezclar los datos empresariales y personales.  Los datos de la compañía podrían acabar en ubicaciones como el almacenamiento personal o transferidas a aplicaciones fuera de su ámbito, lo cual provocaría una pérdida de datos. Las flechas del diagrama muestran el movimiento sin restricciones de los datos entre aplicaciones (personales y corporativas) y hacia ubicaciones de almacenamiento.

### <a name="data-protection-with-app-protection-policies"></a>Protección de datos con directivas de protección de aplicaciones

![Imagen que muestra cómo se protegen los datos de la empresa cuando se aplican directivas de protección de aplicaciones. ](./media/apps-with-protection-policies.png)


Puede usar directivas de protección de aplicaciones para evitar que los datos de la empresa se guarden en el almacenamiento local del dispositivo y para restringir el movimiento de datos a otras aplicaciones que no estén protegidas por estas directivas. La configuración de directivas de protección de aplicaciones incluyen:
- Directivas de reubicación de datos como **Impedir "Guardar como"**, **Restringir cortar, copiar y pegar**.
- Opciones de directivas de acceso como **Requerir PIN sencillo para el acceso**, **Bloquear las aplicaciones administradas para que no se ejecuten en dispositivos con jailbreak o rooting**.

### <a name="data-protection-with-app-protection-policies-on-devices-managed-by-a-mdm-solution"></a>Protección de datos con directivas de protección de aplicaciones en dispositivos administrados por una solución MDM:

![Imagen que muestra cómo funcionan las directivas de protección de aplicaciones en dispositivos BYOD.](./media/app-protection-policies-with-mdm.png)

**En dispositivos inscritos en una solución MDM**-

En la ilustración anterior se muestran las capas de protección que ofrecen juntas las directivas MDM y las directivas de protección de aplicaciones.

La solución MDM:

-   Inscribe el dispositivo.

-   Implementa las aplicaciones en el dispositivo

-   Proporciona administración y conformidad continua de los dispositivos

**Las directivas de protección de aplicaciones agregan valor:**

-   Ayudando a evitar la fuga de datos de la compañía a aplicaciones y servicios de consumidor

-   Aplicando restricciones (Guardar como, Portapapeles, PIN, etc.) a las aplicaciones móviles

-   Borrar datos de compañía de las aplicaciones sin borrar esas aplicaciones del dispositivo


### <a name="data-protection-with-app-protection-policies-for-devices-without-enrollment"></a>Protección de datos con directivas de protección de aplicaciones para dispositivos sin inscripción

![Imagen que muestra cómo funcionan las directivas de protección de aplicaciones en dispositivos administrados.](./media/app-protection-policies-without-mdm.png)

En el diagrama anterior se muestra cómo funcionan las directivas de protección de datos en el nivel de aplicación sin MDM.

En dispositivos BYOD no inscritos en ninguna solución MDM, las directivas de protección de aplicaciones pueden ayudar a proteger los datos de la compañía a nivel de aplicación.
Sin embargo, existen algunas limitaciones que se deben tener en cuenta, como:

-   No se puede implementar aplicaciones en el dispositivo.  El usuario final debe obtener las aplicaciones del almacén.

-   No se puede proporcionar perfiles de certificados en estos dispositivos.

-   No se puede proporcionar configuraciones de Wi-Fi y VPN de compañía en estos dispositivos.


## <a name="multi-identity"></a>Varias identidades

Las aplicaciones que admiten varias identidades permiten usar diferentes cuentas (profesionales y personales) para obtener acceso a las mismas aplicaciones, aunque las directivas de protección de aplicaciones se aplican solo cuando las aplicaciones se usen en el contexto laboral.

Por ejemplo, cuando el usuario inicia la aplicación OneDrive con su cuenta profesional, no puede mover los archivos a una ubicación de almacenamiento personal. Sin embargo, cuando usa OneDrive con su cuenta personal, puede copiar y mover los datos de su OneDrive personal sin restricciones.

- Obtenga más información sobre las aplicaciones que admiten [MAM y varias identidades](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) con Intune.

##  <a name="next-steps"></a>Pasos siguientes

[Creación e implementación de directivas de protección de aplicaciones con Microsoft Intune](app-protection-policies.md)
