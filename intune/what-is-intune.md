---
title: ¿Qué es Microsoft Intune?
description: Obtenga información sobre cómo Intune es el componente de administración de dispositivos móviles (MDM) y de administración de aplicaciones móviles (MAM) de la solución Enterprise Mobility + Security y sobre cómo ayuda a proteger los datos de la empresa.
keywords: ¿Qué es Intune?
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 12/03/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
search.appverid: MET150
ms.custom: get-started
ms.openlocfilehash: ed87f9d2554972a0affd9c93eca1804c460e6144
ms.sourcegitcommit: d3b1e3fffd3e0229292768c7ef634be71e4736ae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2018
ms.locfileid: "52860986"
---
# <a name="what-is-microsoft-intune"></a>¿Qué es Microsoft Intune?

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Intune es un servicio de administración de movilidad empresarial (EMM) basado en nube que ayuda a los empleados a ser productivos mientras mantiene protegidos los datos corporativos. Al igual que otros servicios de Azure, Microsoft Intune está disponible en Azure Portal. Intune permite:
* Administrar los dispositivos móviles y los equipos que los empleados usan para tener acceso a datos de la empresa.
* Administrar las aplicaciones móviles que usa la plantilla.
* Proteger la información de la empresa al ayudar a controlar la manera en que los empleados tienen acceso a ella y la comparten.
* Garantizar que los dispositivos y las aplicaciones sean compatibles con los requisitos de seguridad de la empresa.

## <a name="common-business-problems-that-intune-helps-solve"></a>Problemas empresariales comunes que Intune ayuda a resolver

* [Proteger el correo electrónico y los datos locales para tener acceso a ellos desde un dispositivo móvil](common-scenarios.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Proteger el correo electrónico y los datos de Office 365 para tener acceso a ellos sin riesgos desde un dispositivo móvil](common-scenarios.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Distribuir teléfonos de propiedad corporativa entre los trabajadores](common-scenarios.md#issue-corporate-owned-phones-to-your-employees)
* [Ofrecer un programa "Bring Your Own Device" (BYOD) o de dispositivo personal a todos los empleados](common-scenarios.md#offer-a-bring-your-own-device-program-to-all-employees)
* [Permitir que los empleados tengan un acceso seguro a Office 365 desde un quiosco público no administrado](common-scenarios.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
* [Distribuir tabletas compartidas de uso limitado entre los trabajadores de tareas](common-scenarios.md#issue-limited-use-shared-tablets-to-your-employees)


## <a name="how-does-intune-work"></a>¿Cómo funciona Intune?
Intune es el componente de Enterprise Mobility + Security (EMS) que administra aplicaciones y dispositivos móviles. Intune se integra perfectamente con otros componentes de EMS, como Azure Active Directory (Azure AD) para la identidad y el control de acceso y Azure Information Protection para la protección de datos. Al usarlo junto a Office 365, permite que los empleados sean productivos en todos sus dispositivos sin poner en peligro la información de la organización.

![Imagen de una arquitectura de Intune](./media/intunearch_sm.png)

Vea una [versión ampliada](./media/intunearchitecture.svg) del diagrama de arquitectura de Intune.

La manera en que use las características de administración de dispositivos y aplicaciones de Intune y la protección de datos de EMS dependerá del [problema empresarial que intente resolver](#common-business-problems-that-intune-helps-solve). Por ejemplo:
* Si está creando un grupo de dispositivos de uso único que compartirán los trabajadores por turnos de un comercio, hará un uso intensivo de la administración de dispositivos.
* Si permite que los empleados usen sus dispositivos personales para tener acceso a los datos corporativos (BYOD), usará la administración de aplicaciones y la protección de datos.  
* Si distribuye teléfonos corporativos entre los trabajadores de la información, dependerá de todas estas tecnologías.

## <a name="intune-device-management-explained"></a>Funcionamiento de la administración de dispositivos en Intune
La administración de dispositivos de Intune funciona mediante los protocolos o las API que están disponibles en los sistemas operativos móviles. Incluye tareas como las siguientes:
* Inscribir dispositivos en la administración para que el departamento de TI tenga un inventario de los dispositivos con acceso a los servicios corporativos
* Configurar dispositivos para asegurarse de que cumplen los estándares de mantenimiento y seguridad de la empresa.
* Proporcionar certificados y perfiles de Wi-Fi o VPN para tener acceso a los servicios corporativos.
* Medir el cumplimiento de los estándares corporativos por parte del dispositivo y crear informes al respecto.
* Quitar datos corporativos de los dispositivos administrados.  

En ocasiones, se cree que el **control de acceso a datos corporativos** es una característica de administración de dispositivos. En nuestra opinión no lo es, ya que no lo proporciona el sistema operativo móvil, sino el proveedor de identidades. En nuestro caso, el proveedor de identidades es Azure Active Directory (Azure AD), el sistema de administración de identidad y acceso de Microsoft.  

Intune se integra con Azure AD para permitir una amplia gama de escenarios de control de acceso. Por ejemplo, puede requerir que un dispositivo móvil sea compatible con los estándares corporativos que define en Intune para que pueda acceder a un servicio corporativo como Exchange. También puede bloquear el servicio corporativo para que no tenga acceso a un conjunto específico de aplicaciones móviles. Por ejemplo, puede bloquear Exchange Online de modo que solo Outlook o Outlook Mobile tengan acceso a él.

## <a name="intune-app-management-explained"></a>Funcionamiento de la administración de aplicaciones en Intune
Cuando hablamos sobre la administración de aplicaciones, nos referimos a lo siguiente:
* Asignar aplicaciones móviles a empleados
* Configurar aplicaciones mediante una configuración estándar que se usa al ejecutar la aplicación
* Controlar la manera en que se usan y se comparten los datos corporativos en las aplicaciones móviles
* Quitar datos corporativos de las aplicaciones móviles   
* Actualizar aplicaciones
* Crear informes sobre el inventario de aplicaciones móviles
* Realizar un seguimiento del uso de las aplicaciones móviles

Hemos visto que el término "administración de aplicaciones móviles" (MAM) se usa para indicar una de estas tareas individualmente o la combinación de algunas de ellas. En concreto, es común que se combine el concepto de configurar aplicaciones con el de proteger los datos corporativos en aplicaciones móviles. Esto se debe a que algunas aplicaciones móviles contienen opciones que permiten configurar sus características de seguridad de datos.

Cuando hablamos sobre la configuración de la aplicación de Intune, nos referimos específicamente a tecnologías como la [configuración de la aplicación administrada en iOS](https://developer.apple.com/library/content/samplecode/sc2279/Introduction/Intro.html).

Al usar Intune con los demás servicios de EMS, puede proporcionar a la organización una seguridad adicional para las aplicaciones móviles, que se añade a la que proporcionan el sistema operativo móvil y las propias aplicaciones móviles mediante la configuración de la aplicación. Una aplicación administrada con EMS tiene acceso a un conjunto más amplio de características de protección de datos y aplicaciones móviles que incluye lo siguiente:

* [Inicio de sesión único](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)  
*   [Autenticación multifactor](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication)
* [Acceso condicional a aplicaciones: permitir el acceso si la aplicación móvil contiene datos corporativos](app-based-conditional-access-intune.md)
* [Aislamiento de los datos corporativos y los datos personales dentro de la misma aplicación](app-protection-policy.md)
* [Directiva de protección de aplicaciones (PIN, cifrado, guardar como, Portapapeles, etc.)](app-protection-policies.md)
* [Borrado de los datos corporativos de una aplicación móvil](apps-selective-wipe.md)
* [Compatibilidad con Rights Management](https://docs.microsoft.com/information-protection/understand-explore/what-is-azure-rms)

![Imagen en la que se muestran los niveles de seguridad de datos de la administración de aplicaciones](./media/managing-mobile-apps.png)

### <a name="intune-app-security"></a>Seguridad de la aplicación de Intune
Una parte de la administración de aplicaciones consiste en proporcionar seguridad de aplicaciones. En Intune, cuando hablamos sobre seguridad de aplicaciones móviles, nos referimos a lo siguiente:
* Mantener la información personal aislada del reconocimiento por parte del departamento de TI de la empresa
* Restringir las acciones que pueden realizar los usuarios con la información corporativa, como copiar, cortar, pegar, guardar y ver
* Quitar los datos corporativos de aplicaciones móviles, lo que también se conoce como borrado selectivo o corporativo

Una de las maneras en que Intune proporciona seguridad de aplicaciones móviles es a través de su característica de **directiva de protección de aplicaciones**. La directiva de protección de aplicaciones usa la identidad de Azure AD para aislar los datos corporativos de los datos personales. Los datos a los que se obtiene acceso mediante una credencial corporativa recibirán protecciones corporativas adicionales.

Por ejemplo, cuando un usuario inicia sesión en su dispositivo con sus credenciales corporativas, su identidad corporativa le permite acceder a datos a los que no tiene acceso con su identidad personal. Dado que se usan datos corporativos, las directivas de protección de aplicaciones controlan cómo se guardan y se comparten. Estas mismas protecciones no se aplican a los datos a los que el usuario tiene acceso cuando inicia sesión en su dispositivo con su identidad personal. De esta manera, el departamento de TI controla los datos corporativos, mientras que el usuario final mantiene el control y la privacidad de sus datos personales.

## <a name="emm-with-and-without-device-enrollment"></a>EMM con y sin inscripción de dispositivos
La mayoría de las soluciones de administración de movilidad empresarial admiten tecnologías básicas de dispositivos y aplicaciones móviles. Normalmente, están vinculadas al dispositivo que se inscribe en la solución de administración de dispositivos móviles (MDM) de la organización. Intune es compatible con estos escenarios y, además, admite numerosos escenarios "sin inscripción".  

Las organizaciones diferirán en la medida en que adopten escenarios "sin inscripción". Para algunas organizaciones son estándar, otras los permiten en dispositivos complementarios, como una tableta personal, y otras no los admiten en absoluto. Incluso en este último caso, en el que se requiere que todos los dispositivos de los empleados se inscriban en MDM, suelen admitir escenarios "sin inscripción" para contratistas, proveedores y otros dispositivos con exenciones específicas.

También se puede usar tecnología de "sin inscripción" de Intune en los dispositivos inscritos. Por ejemplo, un dispositivo inscrito en MDM puede tener protecciones de apertura proporcionadas por el sistema operativo móvil. La protección de apertura es una función de iOS que impide que se abra un documento desde una aplicación, como Outlook, en otra aplicación, como Word, a menos que el proveedor de MDM administre ambas aplicaciones. Además, el departamento de TI puede aplicar la directiva de protección de aplicaciones a las aplicaciones móviles administradas por EMS para controlar la opción de guardar como o proporcionar autenticación multifactor.

Sea cual sea la postura de su organización con respecto a los dispositivos y aplicaciones móviles inscritos y no inscritos, Intune, como parte de EMS, dispone de herramientas que le ayudarán a aumentar la productividad de sus empleados mientras protege los datos de la empresa.

## <a name="microsoft-intune-in-the-azure-portal"></a>Microsoft Intune en Azure Portal

[Azure Portal](https://portal.azure.com) es la ubicación en la que se encuentra el servicio Microsoft Intune.

Los aspectos destacados de la experiencia de Microsoft Intune en Azure Portal incluyen lo siguiente:

- Consola integrada para todos los componentes de Enterprise Mobility + Security (EMS)
- Consola basada en HTML basada en estándares web
- Soporte técnico de la API de Microsoft Graph para automatizar muchas acciones
- Grupos de Azure Active Directory (AD) para proporcionar compatibilidad entre todas las aplicaciones de Azure
- Compatibilidad con la mayoría de los exploradores web más modernos

Para leer una guía rápida para la personalización de la experiencia del portal, vea [Introducción a Intune en Azure Portal](get-started-azure.md).

> [!NOTE]
> Si ha usado una versión anterior de Microsoft Intune, puede que le resulte útil la siguiente información:
> * [¿Dónde está mi característica en Azure?](ui-changes.md) es una referencia para mostrar las UI y los flujos de trabajo específicos que cambiaron con la migración a Azure.
> * [Grupos de Intune clásicos en Azure Portal](groups-get-started.md) explica las implicaciones del cambio a los grupos de seguridad de Azure Active Directory para la administración de grupos.

### <a name="before-you-start"></a>Antes de empezar

Para usar Intune en el portal de Azure, debe tener una cuenta de administrador y de inquilino de Intune. [Regístrese para obtener una cuenta](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20) si todavía no tiene una.

### <a name="supported-web-browsers-for-the-azure-portal"></a>Exploradores web admitidos en el portal de Azure

El portal de Azure funciona en la mayoría de equipos PC, Mac y tabletas más modernos. No es compatible con teléfonos móviles.
Actualmente, se admiten los siguientes exploradores:

- Microsoft Edge (última versión)
- Microsoft Internet Explorer 11
- Safari (solo en Mac, última versión)
- Chrome (última versión)
- Firefox (última versión)

Para obtener la información más reciente sobre los exploradores admitidos, vea [Azure Portal](https://docs.microsoft.com/azure/azure-preview-portal-supported-browsers-devices).

## <a name="next-steps"></a>Pasos siguientes
* Lea sobre algunas [formas comunes de usar Intune](common-scenarios.md).
* Familiarícese con el producto [con una evaluación de prueba de 30 días de Intune](free-trial-sign-up.md).
* Sumérjase en los [requisitos técnicos y las funciones](supported-devices-browsers.md) de Intune.
