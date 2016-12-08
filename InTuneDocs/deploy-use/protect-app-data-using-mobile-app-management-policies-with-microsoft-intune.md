---
title: "Protección de los datos de la aplicación mediante directivas MAM | Microsoft Intune"
description: "En este tema se explica cómo pueden ayudar las directivas de administración de aplicaciones móviles a proteger los datos de su empresa, evitar la pérdida de datos y separar la información personal y profesional."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab6cd622-b738-4a63-9c91-56044aaafa6d
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 87c1f90f41ec72ff74c23bfa270efade31890fc0


---

# <a name="protect-app-data-using-mobile-application-management-policies-with-microsoft-intune"></a>Proteger datos mediante las directivas de administración de aplicaciones móviles con Microsoft Intune

## <a name="how-you-can-protect-app-data"></a>Cómo puede proteger los datos de la aplicación
Los empleados usan dispositivos móviles para tareas personales y de trabajo. Mientras se asegura de que los empleados pueden ser productivos, también puede evitar la pérdida de datos, ya sea intencional o involuntaria.  Además, desea tener la capacidad de proteger datos de la compañía a los que los empleados obtienen acceso mediante el uso de dispositivos que no administra.

Puede usar directivas de administración de aplicaciones móviles (MAM) de Intune para ayudar a proteger los datos de la empresa. Dado que las directivas de MAM de Intune se pueden usar **independientemente de cualquier solución de administración de dispositivos móviles (MDM)**, puede usar MAM para proteger los datos de la empresa con o sin inscripción de los dispositivos en una solución de administración de dispositivos. Mediante la implementación de **directivas de nivel de aplicación**, puede restringir el acceso a los recursos de la empresa y mantener los datos dentro del ámbito del departamento de TI.

Se pueden configurar directivas MAM para aplicaciones que se ejecutan en dispositivos que están:

-   **Inscritos en Microsoft Intune:** los dispositivos de esta categoría son normalmente dispositivos corporativos.

-   **Inscritos en una solución MDM de terceros:** los dispositivos de esta categoría son normalmente dispositivos corporativos.

  > [!NOTE]
  > No se recomienda utilizar directivas MAM con soluciones de contenedor seguras o administración de aplicaciones móviles de terceros.

-   **No inscritos en ninguna solución MDM:** los dispositivos de esta categoría normalmente son dispositivos de empleados no administrados ni inscritos en Intune ni en ninguna otra solución MDM.

> [!IMPORTANT]
> Puede crear directivas de administración de aplicaciones móviles para aplicaciones móviles de Office que se conectan a servicios de Office 365. Las directivas de MAM no son compatibles con las aplicaciones que se conectan a los servicios locales de Exchange, SharePoint o Skype Empresarial.

## <a name="benefits-of-using-mam-policies"></a>Ventajas del uso de directivas MAM

-   **Ayudan a proteger los datos de su compañía a nivel de aplicación.** Puesto que la administración de aplicaciones móviles no requiere la administración de dispositivos, puede proteger los datos de la empresa en dispositivos administrados y no administrados. La administración se centra en la identidad del usuario, lo que elimina la necesidad de administrar dispositivos.

-   **La productividad del usuario no se ve afectada y no se aplican las directivas cuando se usa la aplicación en un contexto personal.** Las directivas se aplican solo en un contexto de trabajo, lo que le ofrece la capacidad de proteger los datos de la compañía sin tocar los datos personales.

Hay otras ventajas derivadas del uso de MDM con directivas de MAM, y las empresas pueden usar MAM con y sin MDM al mismo tiempo. Por ejemplo, un empleado puede usar un teléfono de la compañía, así como una tableta personal. En este caso, el teléfono de la compañía está inscrito en MDM y protegido por las directivas de MAM y el dispositivo personal está protegido únicamente por las directivas de MAM.

- **MDM garantiza que el dispositivo esté protegido** Por ejemplo, puede solicitar un PIN para acceder al dispositivo o puede implementar aplicaciones administradas en el dispositivo. También puede implementar aplicaciones en dispositivos a través de la solución MDM para proporcionarle más control sobre la administración de aplicaciones.

- **Las directivas MAM garantizan que las protecciones de la capa de aplicaciones estén establecidas** Por ejemplo, puede tener una directiva que requiera un PIN para abrir una aplicación en un contexto de trabajo, evitar que los datos se compartan entre aplicaciones o evitar que los datos de la aplicación de la compañía se guarden en una ubicación de almacenamiento personal.

## <a name="devices-that-support-mam"></a>Dispositivos que admiten MAM
Actualmente las directivas de MAM se admiten en:
-   iOS 8.1 o posterior
-   Android 4 o posterior

Los dispositivos Windows no son compatibles actualmente.
##  <a name="how-mam-policies-protect-app-data"></a>Cómo protegen las directivas de MAM los datos de las aplicaciones

###  <a name="apps-without-mam-policies"></a>Aplicaciones sin directivas de MAM

![Imagen que muestra que los datos se pueden mover libremente entre aplicaciones cuando no hay ninguna directiva de MAM aplicada](../media/Apps_without_MAM_policies.png)

Cuando use aplicaciones sin restricciones, se pueden entremezclar los datos empresariales y personales. Los datos de la compañía podrían acabar en ubicaciones como el almacenamiento personal o transferidas a aplicaciones fuera de su ámbito, lo cual provocaría una pérdida de datos. Las flechas del diagrama muestran el movimiento sin restricciones de los datos entre aplicaciones (personales y corporativas) y hacia ubicaciones de almacenamiento.

### <a name="data-protection-with-mam-policies"></a>Protección de datos con directivas de MAM

![Imagen que muestra cómo se protegen los datos de la empresa cuando se aplican directivas de MAM](../media/Apps_with_mobile_app_policies.png)

Puede usar directivas de MAM para evitar que los datos de la empresa se guarden en el almacenamiento local del dispositivo y para restringir el movimiento de datos a otras aplicaciones que no estén protegidas por directivas de MAM. La configuración de las directivas de MAM incluye:
- Directivas de reubicación de datos como **Impedir "Guardar como"**, **Restringir cortar, copiar y pegar**.
- Opciones de directivas de acceso como **Requerir PIN sencillo para el acceso**, **Bloquear las aplicaciones administradas para que no se ejecuten en dispositivos con jailbreak o rooting**.

### <a name="data-protection-with-mam-policies-on-devices-that-are-managed-by-a-mdm-solution"></a>Protección de datos con directivas de MAM en dispositivos administrados por una solución MDM

![Imagen que muestra cómo funcionan las directivas de MAM en los dispositivos Bring Your Own Devices (BYOD)](../media/MAM_BYOD_November.png)

**Para los dispositivos inscritos en una solución MDM**: el diagrama anterior muestra las capas de protección que las directivas MDM y MAM ofrecen juntas.

La solución MDM:

-   Inscribe el dispositivo.

-   Implementa las aplicaciones en el dispositivo.

-   Proporciona administración y conformidad continua de los dispositivos.

**Las directivas MAM agregan valor porque:**

-   Ayudan a evitar la fuga de datos de la compañía a aplicaciones y servicios de consumidor.

-   Aplican restricciones (Guardar como, Portapapeles, PIN, etc.) a las aplicaciones móviles.

-   Borran datos de compañía de las aplicaciones sin borrar esas aplicaciones del dispositivo.


### <a name="data-protection-with-mam-policies-for-devices-without-enrollment"></a>Protección de datos con directivas de MAM para dispositivos sin inscripción

![Imagen que muestra cómo funcionan las directivas de MAM en los dispositivos administrados](../media/MAM_ManagedDevices_November.png)

En el diagrama anterior se muestra cómo funcionan las directivas de protección de datos en el nivel de aplicación sin MDM.

En los dispositivos BYOD no inscritos en ninguna solución MDM, las directivas de MAM pueden ayudar a proteger los datos de la compañía a nivel de aplicación.

Sin embargo, existen algunas limitaciones que se deben tener en cuenta:

-   No se puede implementar aplicaciones en el dispositivo. El usuario debe obtener las aplicaciones del almacén.

-   No se puede proporcionar perfiles de certificados en estos dispositivos.

-   No se puede establecer configuraciones de Wi-Fi y VPN de compañía en estos dispositivos.


## <a name="multi-identity"></a>Varias identidades

Las aplicaciones que admiten varias identidades les permiten usar diferentes cuentas (profesional y personal) para obtener acceso a las mismas aplicaciones mientras se apliquen directivas MAM solo cuando las aplicaciones se usen en el contexto laboral.  

Por ejemplo, cuando el usuario inicia la aplicación OneDrive con su cuenta profesional, no puede mover los archivos a una ubicación de almacenamiento personal. Sin embargo, cuando usa OneDrive con su cuenta personal, puede copiar y mover los datos de su OneDrive personal sin restricciones.  

Todas las aplicaciones móviles de Office admiten el acceso de varias identidades.

##  <a name="next-steps"></a>Pasos siguientes
- [Prepárese para configurar directivas de administración de aplicaciones móviles](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)

- [Crear e implementar directivas de administración de aplicaciones móviles con Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Nov16_HO5-->


