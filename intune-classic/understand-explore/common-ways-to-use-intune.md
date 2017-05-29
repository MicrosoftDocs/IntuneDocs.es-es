---
title: Usos habituales de Intune | Microsoft Docs
description: "Muestra seis de las tareas más comunes en las que Intune presta ayuda"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/16/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f37d4ff-b5a7-4a89-8884-a6184908b09c
ms.reviewer: robstackmsft
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 6a20136e078edd2b4b82cdd8abe9cfe4968ca703
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="common-ways-to-use-intune"></a>Usos habituales de Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Antes de sumergirse en las tareas de implementación, es importante poner de acuerdo a las partes interesadas de Enterprise Mobility en torno a los objetivos empresariales.  Esto es fundamental cuando se es totalmente profano en Enterprise Mobility o al migrar desde otro producto.  

Las necesidades de Enterprise Mobility están en constante evolución y, en este sentido, los distintos métodos de Microsoft para abordar estas necesidades son a veces diferentes de los de otras soluciones del mercado. La mejor manera de ponerse de acuerdo en torno a los objetivos empresariales es expresar lo que se pretende lograr en lo relativo a los escenarios que se quieren habilitar para los empleados, los asociados y el departamento de TI.  

A continuación se presentan brevemente los seis escenarios más comunes que se basan en Intune, así como vínculos para obtener más información sobre cómo planear e implementar cada uno de ellos.

>[!NOTE]
>¿Quiere saber cómo el equipo de TI de Microsoft usa Intune para permitir que Microsoft tenga acceso a los recursos corporativos en sus dispositivos móviles y, al mismo tiempo, tener protegidos los datos de la empresa? [Lea este caso práctico técnico](https://www.microsoft.com/itshowcase/Article/Content/588) para ver en detalle cómo el equipo de TI de Microsoft usa Intune y otros servicios para administrar identidades, dispositivos, aplicaciones y datos.  

>[!IMPORTANT]
>En vista de los recientes ataques del malware "Trident" en dispositivos iOS, queremos asegurarnos de que los dispositivos móviles estén actualizados. Por este motivo, hemos publicado una entrada de blog titulada [Ensuring mobile devices are up to date using Microsoft Intune](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/26/ensuring-mobile-devices-are-up-to-date-using-microsoft-intune/) (Cómo asegurarse de que los dispositivos móviles están actualizados con Microsoft Intune). Proporciona información sobre las distintas formas en las que Intune ayuda a mantener los dispositivos seguros y actualizados.

## <a name="protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices"></a>Proteger el correo electrónico y los datos locales para tener acceso a ellos sin riesgos desde un dispositivo móvil
La mayoría de las estrategias de Enterprise Mobility arranca con un plan que permite que los empleados tengan un acceso seguro al correo electrónico con dispositivos móviles conectados a Internet. Muchas organizaciones todavía tienen datos y servidores de aplicaciones locales, como Microsoft Exchange, que están hospedados en la red corporativa.

Intune y Microsoft Enterprise Mobility + Security para Exchange Server, que aseguran que ninguna aplicación móvil pueda acceder al correo electrónico hasta que el dispositivo esté inscrito en Intune. Puede hacer todo esto sin necesidad de implementar otra máquina de puerta de enlace en el extremo de la red corporativa.

Intune también permite el acceso a las aplicaciones móviles que requieren un acceso seguro a los datos locales, como servidores de aplicaciones de línea de negocio. Esto se suele realizar mediante [certificados administrados por Intune](/intune-classic/deploy-use/secure-resource-access-with-certificate-profiles) para el control de acceso, combinado con un proxy o una puerta de enlace de VPN estándar en el perímetro (como, por ejemplo, el Proxy de aplicación de Microsoft Azure Active Directory).  

En estos casos, la única manera de tener acceso a los datos corporativos es inscribir el dispositivo en la administración. Una vez que se han inscrito los dispositivos, el sistema de administración procura que los dispositivos cumplan con las directivas en vigor para que puedan tener acceso a los datos corporativos.  Además, el [SDK de aplicaciones y la herramienta de ajuste de aplicaciones](/intune-classic/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune) de Intune pueden contener los datos a los que se ha tenido acceso dentro de aplicación de línea de negocio, de forma que los datos corporativos no se puedan pasar a servicios o aplicaciones de consumidor.

<!-- Learn more about how to plan and deploy Intune to help secure on-premises email and data. -->


## <a name="protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices"></a>Proteger el correo electrónico y los datos de Office 365 para tener acceso a ellos sin riesgos desde un dispositivo móvil
La protección de los datos empresariales de Office 365 (correo electrónico, documentos, mensajes instantáneos, contactos) no podría ser más sencilla o transparente para los usuarios.

Intune y Microsoft Enterprise Mobility + Security proporcionan una solución de acceso condicional integrada de forma única que se asegura de que ningún usuario, aplicación o dispositivo pueda tener acceso a los datos de Office 365 a menos que cumpla los requisitos de cumplimiento de la empresa, esté inscrito con Intune, use la aplicación administrada, disponga de una versión compatible del sistema operativo, tenga un PIN de dispositivo, cuente con un perfil de riesgo de usuario bajo, etc.

Las aplicaciones móviles de Office que se encuentran en sus respectivas tiendas de aplicaciones están preparadas para adaptarse a las directivas de contención de datos que se pueden configurar mediante Intune. Esto permite evitar que los datos se compartan con aplicaciones (por ejemplo, aplicaciones de correo electrónico nativas) y con ubicaciones de almacenamiento (por ejemplo, Dropbox) que no administra el departamento de TI. Todas estas funciones están integradas en Office 365 y EMS. No tendrá que implementar ninguna otra infraestructura para poder disfrutar de ellas.

Una práctica común de implementación de Office 365 es exigir que los dispositivos estén inscritos en la administración si se tienen que configurar completamente con las opciones de configuración de aplicaciones, certificados, Wi-Fi o VPN corporativos, un escenario habitual para dispositivos de propiedad corporativa.  

En cambio, si solo es necesario acceder a los documentos y al correo electrónico de la empresa (que suele ser el caso de los dispositivos de propiedad personal), puede exigir al usuario que use las aplicaciones móviles de Office y no será preciso inscribir el dispositivo.  

En cualquier caso, los datos de Office 365 estarán protegidos con las directivas que se hayan definido.

<!-- Learn more about how to plan and deploy Intune to help secure Office 365 email and data. -->


## <a name="offer-a-bring-your-own-device-program-to-all-employees"></a>Ofrecer un programa "Bring Your Own Device" a todos los empleados
Bring Your Own Device (BYOD) es cada vez más popular en las organizaciones como forma de reducir los gastos de hardware o de aumentar las opciones de productividad móvil de los empleados. A día de hoy, casi todo el mundo tiene un teléfono personal, así que, ¿qué necesidad hay de darles otro? El desafío más importante ha sido siempre convencer a los empleados para que inscriban sus propios dispositivos personales en la administración, ya que temen que el departamento de TI pueda verlos y controlarlos.  

Cuando la inscripción de dispositivos no es una opción viable, Intune ofrece un método alternativo de BYOD con el que simplemente se [administran las aplicaciones que contengan datos corporativos](/intune-classic/deploy-use/protect-apps-and-data-with-microsoft-intune).  Intune protege los datos corporativos incluso cuando la aplicación en cuestión tiene acceso a datos personales y a datos corporativos, como ocurre en las aplicaciones móviles de Office.  

Como administrador, puede obligar a que los usuarios tengan acceso a Office 365 desde las aplicaciones móviles de Office, así como configurar las aplicaciones con directivas que mantengan los datos protegidos (por ejemplo, mediante el cifrado, la protección con PIN, etc.). Estas directivas evitan la pérdida de datos en aplicaciones y ubicaciones de almacenamiento no administradas, tanto dentro como fuera de esas aplicaciones. Por ejemplo, las directivas impiden que un usuario copie texto de un perfil de correo electrónico corporativo en un perfil de correo electrónico de consumidor, aun cuando ambos perfiles estén configurados en Outlook Mobile. Se pueden implementar configuraciones similares relativas a otros servicios y aplicaciones que los usuarios de BYOD necesiten.

<!-- Learn more about how to plan and deploy Intune to support BYOD.-->

## <a name="issue-corporate-owned-phones-to-your-employees"></a>Distribuir teléfonos de propiedad corporativa entre los empleados
En la actualidad, la mayoría de los empleados está en constante movimiento, de modo que la productividad de los dispositivos móviles es esencial para ser competitivos. Los empleados necesitan un acceso sin trabas a todas las aplicaciones y datos corporativos, en todo momento y estén donde estén. En este sentido, conviene garantizar que los datos corporativos estén protegidos y los costos administrativos sean bajos.  

Intune ofrece [soluciones de aprovisionamiento masivo y administración](/intune-classic/deploy-use/manage-corporate-owned-devices) que se integran con las plataformas de administración de dispositivos corporativos más importantes del mercado de hoy día, incluidos el Programa de inscripción de dispositivos de Apple y la plataforma de seguridad móvil Samsung KNOX. La creación centralizada de configuraciones de dispositivos con Intune hace posible que el aprovisionamiento de dispositivos corporativos se automatice en un alto grado.  

Imagínese: entrega una caja de iPhone sin abrir a un empleado. El empleado lo enciende y se le guía por un proceso de configuración de marca corporativa en el que debe autenticarse. El iPhone se configura a la perfección junto a las [directivas de seguridad](/intune-classic/deploy-use/add-apps).

Después, el empleado inicia la aplicación de portal de empresa de Intune para tener acceso a una serie de aplicaciones corporativas opcionales disponibles.

<!-- Learn more about how to plan and deploy Intune to support corporate owned devices. -->

## <a name="issue-limited-use-shared-tablets-to-your-employees"></a>Distribuir tabletas compartidas de uso limitado entre los empleados
Los empleados usan las tecnologías móviles con una frecuencia cada vez mayor. Por ejemplo, ahora las tabletas compartidas están a la orden del día entre los empleados de los comercios al por menor.  Independientemente de si se usan para tramitar una venta o comprobar el inventario de forma inmediata, las tabletas ayudan a lograr una excelente interacción con los clientes.

En este caso, la simplicidad de la experiencia del usuario es fundamental. Por este motivo, las tabletas se suelen entregar a los empleados en un modo de uso limitado, de forma que solo puedan interactuar con una única aplicación de línea de negocio. Intune permite aprovisionar de forma masiva, proteger y administrar desde un solo sitio estas tabletas [iOS](/intune-classic/deploy-use/android-policy-settings-in-microsoft-intune#general-configuration-policy) compartidas, que pueden configurarse para funcionar en ese modo de uso limitado.

<!-- Learn more about how to plan and deploy Intune to support shared tablets. -->

## <a name="enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk"></a>Permitir que los empleados tengan un acceso seguro a Office 365 desde un quiosco público no administrado
A veces, los empleados necesitan usar dispositivos, aplicaciones o exploradores que no se pueden administrar, como los equipos públicos de ferias y hoteles.

¿Debe permitir que los empleados tengan acceso al correo electrónico de empresa desde ellos? Con Intune y Microsoft Enterprise Mobility + Security, <!--you have choices. The--> puede decidir no hacerlo y [limitar el acceso al correo electrónico a los dispositivos administrados por la organización](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune).  <!-- Alternatively, you can choose to allow limited access to these untrusted computers by requiring multi-factor authentication and only allowing browser access (Outlook Web Access) in a mode where files cannot be downloaded (e.g. email attachments).--> De este modo, se asegura de que un empleado con una autenticación sólida no deje accidentalmente datos corporativos en un equipo que no es de confianza.

<!-- Learn more about how to plan and deploy Intune to support kiosks. -->

