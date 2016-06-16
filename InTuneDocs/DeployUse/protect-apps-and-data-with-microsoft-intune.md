---
# required metadata

title: Proteger aplicaciones y datos | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 5c46e188-87eb-4ce2-b184-24809e8bf783

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: chrisgre
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Proteger aplicaciones y datos con Microsoft Intune


Intune protege los datos empresariales mediante varias capas de tecnología.  En la capa de identidad, el acceso condicional protege el acceso a los servicios, puesto que solo permite el acceso desde dispositivos administrados que cumplan los requisitos.  En la capa de aplicaciones cliente, la administración de aplicaciones móviles (MAM) protege frente a la pérdida de datos; para ello, evita que estos se muevan a aplicaciones no protegidas o a ubicaciones de almacenamiento y los borra cuando se pierde o se roba un dispositivo.  Estas dos capas de protección deben usarse conjuntamente con el fin de proteger los datos y mantener la productividad de los recursos móviles.

Un primer paso importante para proteger los datos empresariales es implementar el acceso condicional asegurándose de que los dispositivos usados para acceder a los datos emplean protecciones de seguridad (como contraseña segura y cifrado) y de que no están liberados mediante jailbreak. Microsoft Intune ofrece la posibilidad de establecer las condiciones que los dispositivos deben cumplir para poder acceder al correo electrónico y los datos empresariales.

El [acceso condicional](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) viene determinado por dos tipos de directivas que se pueden definir en Intune:
- Las [directivas de cumplimiento](introduction-to-device-compliance-policies-in-microsoft-intune.md) determinan el cumplimiento de un dispositivo. Evalúan la configuración y las condiciones, como:
  - PIN y contraseñas: puede crear reglas para solicitar contraseñas antes de desbloquear un dispositivo, para establecer los requisitos de complejidad de la contraseña y otras opciones de contraseña.
  - Cifrado: puede restringir el acceso a los dispositivos cifrados.
  - El dispositivo no está liberado o modificado: Intune puede detectar si un dispositivo inscrito ha sido liberado mediante jailbreak y se puede establecer la directiva para bloquear el acceso a estos dispositivos.
- Las [directivas de acceso condicional](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) se configuran para un servicio determinado, como Exchange Online o SharePoint Online. Para cada servicio, puede definir a qué grupos de usuarios se deben aplicar estas directivas. Por ejemplo, puede asegurarse de que todas las personas del departamento de finanzas solo puedan acceder al correo electrónico de la empresa desde dispositivos inscritos y de conformidad.

La protección del acceso a los recursos de la empresa es solo el primer paso para proteger los datos empresariales. Todavía necesita proteger los datos una vez que se ha accedido a ellos en el dispositivo. Los datos ahora se pueden copiar, mover, guardar en otra ubicación o compartir. Para resolver este problema, Intune ofrece la posibilidad de restringir el movimiento de datos mediante la creación de un conjunto de reglas, como:
- Bloquear las acciones de copiar y pegar o evitar la transferencia de datos fuera del contexto laboral.
- Evitar la copia de seguridad en el almacenamiento personal en la nube, impedir "Guardar como".
- Proteger el acceso a la aplicación mediante PIN, código de acceso o credenciales corporativas.
- Hacer que todos los vínculos web se abran en Intune Managed Browser.

Estos conjuntos de reglas se conocen como [directivas de administración de aplicaciones móviles (MAM)](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).  Las directivas de MAM se pueden aplicar a aplicaciones que se ejecutan en dispositivos que pueden estar administrados o no por el usuario.  Puede proteger los datos empresariales mediante directivas de MAM en los dispositivos inscritos en Intune, en los dispositivos inscritos y administrados en una solución MDM de terceros o en otros dispositivos que pueden estar administrados o no por el usuario, como los dispositivos personales de los empleados.

Para asociar una aplicación a una directiva de MAM, la aplicación debe incorporar el Kit de desarrollo de software (SDK) de aplicaciones de Microsoft Intune o usar la herramienta de ajuste de aplicaciones.

Algunas aplicaciones, como las de Microsoft Office, tienen integrado el SDK de aplicaciones. Puede encontrar la lista completa de las aplicaciones compatibles en la [Galería de aplicaciones móviles de Microsoft Intune](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) de la página de socios de aplicaciones de Microsoft Intune. Seleccione la aplicación para ver los escenarios y las plataformas admitidos y si la aplicación admite o no varias identidades.

También puede [habilitar sus aplicaciones personalizadas de línea de negocio](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md) para usarlas con directivas de MAM.

Además de restringir el movimiento de datos, si un dispositivo se pierde o es robado, o bien si el usuario ya no trabaja con la empresa, puede [borrar de forma selectiva datos empresariales](wipe-managed-company-app-data-with-microsoft-intune.md) y dejar solo los datos personales.


<!--HONumber=Jun16_HO2-->


