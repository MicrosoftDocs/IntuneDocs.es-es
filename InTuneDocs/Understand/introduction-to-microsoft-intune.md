---
title: "¿Qué es Microsoft Intune? | Microsoft Docs"
description: "Obtenga información sobre cómo Intune es el componente de administración de dispositivos móviles de la solución Enterprise Mobility + Security y sobre cómo ayuda a proteger los datos de la empresa."
keywords: "¿Qué es Intune?"
author: Lindavr
ms.author: lindavr
manager: angrobe
ms.date: 11/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6932a0d81654edc4c2e3108ca11df892e9ec5bf4
ms.openlocfilehash: 50a9b89140a0fff9994b267f10fa7912af89f116


---

# <a name="what-is-intune"></a>¿Qué es Intune?
Intune es un servicio de administración de movilidad empresarial (EMM) basado en nube que ayuda a los empleados a ser productivos mientras mantiene protegidos los datos corporativos. Intune permite:
* Administrar los dispositivos móviles que los empleados usan para tener acceso a datos de la empresa.
* Administrar las aplicaciones móviles que usa la plantilla.
* Proteger la información de la empresa al ayudar a controlar la manera en que los empleados tienen acceso a ella y la comparten.
* Garantizar que los dispositivos y las aplicaciones sean compatibles con los requisitos de seguridad de la empresa.

Intune se integra perfectamente con Azure Active Directory (Azure AD) para la identidad y el control de acceso y con Azure Rights Management (Azure RMS) para la protección de datos. Es el *brazo administrativo* de Microsoft Enterprise Mobility + Security (EMS), mientras que Office 365 es el *brazo productivo* de la solución de movilidad de Microsoft.  

Juntos, Office 365 y EMS permiten que los empleados sean productivos en todos sus dispositivos sin poner en peligro la información de la organización. Office 365 con EMS es un conjunto integrado de aplicaciones diseñadas para favorecer la movilidad empresarial, así como la productividad, la identidad, el control de acceso, la administración y la protección de datos. Ofrece una manera eficaz de implementar y usar una solución de movilidad en su organización.

## <a name="how-does-intune-work"></a>¿Cómo funciona Intune?
Intune proporciona administración de dispositivos móviles (MDM) y administración de aplicaciones móviles (MAM). Las características MDM y MAM de Intune contribuyen a una serie de escenarios de cumplimiento y protección de datos de EMS.  

La manera en que use las características MDM y MAM de Intune y la protección de datos de EMS dependerá del [problema empresarial que intente resolver](#common-business-problems-that-intune-helps-solve). Por ejemplo:
* Si está creando un conjunto de dispositivos de uso único que compartirán los trabajadores por turnos de un comercio, hará un uso intensivo de MDM.
* Si permite que los empleados usen sus dispositivos personales para tener acceso a los datos corporativos (BYOD), usará MAM y la protección de datos.  
* Si distribuye teléfonos corporativos entre los trabajadores de la información, dependerá en gran medida de todas estas tecnologías.

## <a name="intune-mobile-device-management-mdm-explained"></a>Descripción de la administración de dispositivos móviles (MDM) de Intune
MDM funciona mediante los protocolos o las API que están disponibles en los sistemas operativos móviles. Incluye tareas como las siguientes:
* Inscribir dispositivos en la administración para que el departamento que TI tenga un inventario de los dispositivos con acceso a los servicios corporativos.
* Configurar dispositivos para asegurarse de que cumplen los estándares de mantenimiento y seguridad de la empresa.
* Proporcionar certificados y perfiles de Wi-Fi o VPN para tener acceso a los servicios corporativos.
* Medir el cumplimiento de los estándares corporativos por parte del dispositivo y crear informes al respecto.
* Quitar datos corporativos de los dispositivos administrados.  

En ocasiones, se cree que el **control de acceso a datos corporativos** es una característica de MDM. En nuestra opinión no lo es, ya que no lo proporciona el sistema operativo móvil, sino el proveedor de identidades. En nuestro caso, el proveedor de identidades es Azure Active Directory (Azure AD), el sistema de administración de identidad y acceso de Microsoft.  

Intune se integra con Azure AD para permitir una amplia gama de escenarios de control de acceso. Por ejemplo, puede requerir que un dispositivo móvil sea compatible con los estándares corporativos definidos en Intune para que pueda tener acceso a un servicio corporativo como Exchange. También puede bloquear el servicio corporativo para que no tenga acceso a un conjunto específico de aplicaciones móviles. Por ejemplo, puede bloquear Exchange Online de modo que solo Outlook o Outlook Mobile tengan acceso a él.

## <a name="intune-mobile-app-management-mam-explained"></a>Descripción de la administración de aplicaciones móviles (MAM) de Intune
Cuando hablamos de MAM, nos referimos a todo lo que nuestras soluciones permiten hacer a los profesionales de TI con aplicaciones móviles, por ejemplo:
* Publicar aplicaciones móviles para empleados
* Configurar aplicaciones
* Controlar la manera en que se usan y se comparten los datos corporativos en las aplicaciones móviles
* Quitar datos corporativos de las aplicaciones móviles   
* Actualizar aplicaciones móviles
* Crear informes sobre el inventario de aplicaciones móviles
* Realizar un seguimiento del uso de las aplicaciones móviles

Hemos visto que el término MAM se usa para indicar una de estas tareas individualmente o la combinación de algunas de ellas. En concreto, es común que se combine el concepto de configurar aplicaciones (es decir, usar tecnologías como la [configuración de aplicaciones administradas en iOS](https://developer.apple.com/library/content/samplecode/sc2279/Introduction/Intro.html)) con el concepto de proteger los datos corporativos en aplicaciones móviles. Esto se debe a que algunas aplicaciones móviles contienen opciones que permiten configurar sus características de seguridad de datos.

Esto, unido a las características del sistema operativo para la protección de datos (por ejemplo, características de MDM como Windows Information Protection en Windows 10), ofrece una elevada protección de los datos en dispositivos móviles.

Al usar Intune con los demás servicios de EMS, puede proporcionar a la organización una seguridad adicional para las aplicaciones móviles, que se añade a la que proporcionan el sistema operativo móvil y las propias aplicaciones móviles mediante la configuración de la aplicación. Una aplicación administrada con EMS tiene acceso a un conjunto más amplio de características de protección de datos y aplicaciones móviles que incluye lo siguiente:

* [Inicio de sesión único](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-appssoaccess-whatis)  
*   [Autenticación multifactor](https://docs.microsoft.com/en-us/multi-factor-authentication/multi-factor-authentication)
* [Acceso condicional a aplicaciones (permitir el acceso si la aplicación móvil contiene datos corporativos)](https://docs.microsoft.com/en-us/intune/deploy-use/allow-policy-managed-apps-access-to-o365)
* [Aislamiento de los datos corporativos y los datos personales dentro de la misma aplicación](https://docs.microsoft.com/en-us/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)
* [Directiva de protección de aplicaciones (PIN, cifrado, guardar como, Portapapeles, etc.)](https://docs.microsoft.com/en-us/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)
* [Borrado de los datos corporativos de una aplicación móvil](https://docs.microsoft.com/en-us/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)
* [Compatibilidad con Rights Management](https://docs.microsoft.com/en-us/information-protection/understand-explore/what-is-azure-rms)

![Imagen en la que se muestran los niveles de seguridad de datos de la administración de aplicaciones](./media/managing-mobile-apps.png)

### <a name="intune-mobile-app-security"></a>Seguridad de aplicaciones móviles de Intune
Una parte de MAM consiste en proporcionar seguridad de aplicaciones. En Intune, cuando hablamos sobre seguridad de aplicaciones móviles, nos referimos a lo siguiente:
* Mantener la información personal aislada del reconocimiento por parte del departamento de TI de la empresa
* Restringir las acciones que pueden realizar los usuarios con la información corporativa, como copiar, cortar, pegar, guardar y ver
* Quitar los datos corporativos de aplicaciones móviles, lo que también se conoce como borrado selectivo o corporativo

Una de las maneras en que Intune proporciona seguridad de aplicaciones móviles es a través de su característica de **directiva de protección de aplicaciones**. La directiva de protección de aplicaciones usa la identidad de Azure AD para aislar los datos corporativos de los datos personales. Los datos a los que se obtiene acceso mediante una credencial corporativa recibirán protecciones corporativas adicionales.

Cuando un usuario inicia sesión en su dispositivo con sus credenciales corporativas, su identidad corporativa le permite tener acceso a datos a los que no tiene acceso con su identidad personal. Cuando usa los datos corporativos, Intune y otras tecnologías de EMS controlan cómo los guarda y los comparte. Estas mismas protecciones no se aplican a los datos a los que el usuario tiene acceso cuando inicia sesión en su dispositivo con su identidad personal. De esta manera, el departamento de TI controla los datos corporativos, mientras que el usuario final mantiene el control y la privacidad de sus datos personales.

## <a name="emm-with-and-without-device-enrollment"></a>EMM con y sin inscripción de dispositivos
La mayoría de las soluciones de administración de movilidad empresarial admiten tecnologías básicas de dispositivos y aplicaciones móviles. Normalmente, están vinculadas al dispositivo que se inscribe en la solución MDM de la organización. Intune es compatible con estos escenarios y, además, admite numerosos escenarios "sin inscripción".  

Las organizaciones diferirán en la medida en que adopten escenarios "sin inscripción". Para algunas organizaciones son estándar, otras los permiten en dispositivos complementarios, como una tableta personal, y otras no los admiten en absoluto. Incluso en este último caso, en el que se requiere que todos los dispositivos de los empleados se inscriban en MDM, las organizaciones suelen admitir escenarios "sin inscripción" para contratistas, proveedores y otros dispositivos con exenciones específicas.

También se puede usar tecnología de "sin inscripción" de Intune en los dispositivos inscritos. Por ejemplo, un dispositivo inscrito en MDM puede tener protecciones "Open-in" proporcionadas por el sistema operativo móvil. Además, el departamento de TI puede aplicar la directiva de protección de aplicaciones a las aplicaciones móviles administradas por EMS para controlar la opción de guardar como o proporcionar autenticación multifactor.

Sea cual sea la postura de su organización con respecto a los dispositivos y aplicaciones móviles inscritos y no inscritos, Intune, como parte de EMS, dispone de herramientas que le ayudarán a aumentar la productividad de sus empleados mientras protege los datos de la empresa.

## <a name="common-business-problems-that-intune-helps-solve"></a>Problemas empresariales comunes que Intune ayuda a resolver
La siguiente lista de problemas empresariales contiene vínculos a información más detallada sobre las soluciones que podemos proporcionar. Solo el último elemento requiere la inscripción de MDM como parte de la solución:

* [Proteger el correo electrónico y los datos locales para tener acceso a ellos desde un dispositivo móvil](common-ways-to-use-intune.md#Protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Proteger el correo electrónico y los datos de Office 365 para tener acceso a ellos sin riesgos desde un dispositivo móvil](common-ways-to-use-intune.md#Protecting-your-Office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Distribuir teléfonos de propiedad corporativa entre los trabajadores](common-ways-to-use-intune.md#Issue-corporate-owned-phones-to-your-information-workers)
* [Ofrecer un programa "Bring Your Own Device" (BYOD) o de dispositivo personal a todos los empleados](common-ways-to-use-intune.md#Offer-a-bring-your-own-device-program-to-all-employees)
* [Permitir que los empleados tengan un acceso seguro a Office 365 desde un quiosco público no administrado](common-ways-to-use-intune.md#Enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
* [Distribuir tabletas compartidas de uso limitado entre los trabajadores de tareas](common-ways-to-use-intune.md#Issue-limited-use-shared-tablets-to-your-task-workers)

### <a name="next-steps"></a>Pasos siguientes
* Lea sobre algunas [formas comunes de usar Intune](common-ways-to-use-intune.md).
* Familiarícese con el producto [con una evaluación de prueba de 30 días de Intune](get-started-with-a-30-day-trial-of-microsoft-intune.md).
* Sumérjase en los [requisitos técnicos y las funciones](/intune/get-started/what-to-know-before-you-start-microsoft-intune) de Intune.



<!--HONumber=Nov16_HO3-->


