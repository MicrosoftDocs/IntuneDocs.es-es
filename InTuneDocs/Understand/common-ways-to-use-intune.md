---
title: Usos habituales de Intune | Microsoft Intune
description: "Muestra seis de las tareas más comunes en las que Intune presta ayuda"
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f37d4ff-b5a7-4a89-8884-a6184908b09c
ms.reviewer: robstackmsft
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 76d0d9c620000864a4a554600985ba351c18d359
ms.openlocfilehash: e9315040972df39c543a1e99d197a64cf280b7ff


---

# Usos habituales de Intune

Antes de sumergirse en las tareas de implementación, es importante poner de acuerdo a las partes interesadas de Enterprise Mobility en torno a los objetivos empresariales.  Esto es fundamental cuando se es totalmente profano en Enterprise Mobility o al migrar desde otro producto.  Las necesidades de Enterprise Mobility están en constante evolución y, en este sentido, los distintos métodos de Microsoft para abordar estas necesidades pueden ser a veces diferentes de los de otras soluciones del mercado.  La mejor manera de ponerse de acuerdo en torno a los objetivos empresariales es expresar lo que se pretende lograr en lo relativo a los escenarios que se quieren habilitar para los empleados, asociados y TI.  Aquí se presentan brevemente los seis escenarios más comunes que se basan en Intune, así como vínculos para obtener más información sobre cómo planear e implementar cada uno de ellos.

>[!NOTE]
>¿Quiere saber cómo el equipo de TI de Microsoft usa Intune para permitir que los empleados de Microsoft tengan acceso a los recursos corporativos en sus dispositivos móviles y, al mismo tiempo, tener protegidos los datos corporativos? [Lea este caso práctico técnico](https://www.microsoft.com/itshowcase/Article/Content/588) para ver en detalle cómo el equipo de TI de Microsoft usa Intune y otros servicios para administrar identidades, dispositivos, aplicaciones y datos.  

## Proteger el correo electrónico y los datos locales para tener acceso a ellos sin riesgos desde un dispositivo móvil
La mayoría de las estrategias de Enterprise Mobility arranca con un plan que permite que los empleados tengan un acceso seguro al correo electrónico con dispositivos móviles desde Internet. Muchas organizaciones siguen teniendo datos y servidores de aplicaciones (como Microsoft Exchange) hospedados en su red corporativa. Intune y Enterprise Mobility Suite (EMS) proporcionan una [solución de acceso condicional](/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune) integrada de forma única para Exchange Server que garantiza que ninguna aplicación móvil pueda tener acceso al correo electrónico hasta que el dispositivo esté inscrito con Intune, todo ello sin necesidad de implementar otro equipo de puerta de enlace en el extremo de la red corporativa.

Aparte del correo electrónico, Intune permite el acceso a aplicaciones móviles que precisan de un acceso seguro a datos locales, como puede ser una línea de servidor de aplicaciones de negocio.  Esto se suele realizar mediante [certificados administrados por Intune](/en-us/intune/deploy-use/secure-resource-access-with-certificate-profiles) para el control de acceso, combinado con un proxy o una puerta de enlace de VPN estándar en el perímetro (como, por ejemplo, el proxy de aplicación de Microsoft Azure AD).  En estos casos, la única manera de tener acceso a los datos corporativos es inscribir el dispositivo en la administración.  Una vez inscrito, el sistema de administración procura que los dispositivos que tienen acceso a los datos corporativos cumplan con las directivas en vigor.  También se puede usar el [SDK de aplicaciones y la herramienta de ajuste de aplicaciones](/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune) de Intune para contener los datos a los que se ha tenido acceso dentro de aplicación de línea de negocio, de forma que no se puedan pasar a servicios o aplicaciones de consumidor.

<!-- Learn more about how to plan and deploy Intune to help secure on-premises email and data. -->

## Proteger el correo electrónico y los datos de Office 365 para tener acceso a ellos sin riesgos desde un dispositivo móvil
Proteger los datos corporativos en Office 365 (correo electrónico, documentos, mensajes instantáneos, contactos) no podría ser más fácil ni más fluido para los usuarios. Intune y Enterprise Mobility Suite proporcionan una solución de acceso condicional integrada de forma única que garantiza que ningún usuario, aplicación o dispositivo puede tener acceso a los datos de Office 365 a menos que reúna los requisitos de cumplimiento de la empresa (como pueda ser realizar una [autenticación multifactor](/intune/deploy-use/protect-windows-devices-with-multi-factor-authentication), inscribirse en Intune, usar una aplicación administrada, una versión de sistema operativo compatible, un PIN de dispositivo, un perfil de usuario bajo riesgo, etc.). La aplicaciones móviles de Office en sus respectivas tiendas de aplicaciones están preparadas para respetar las directivas de contención de datos que se configuran a través de Intune, lo que impide que los datos se compartan con aplicaciones (por ejemplo, la aplicación de correo electrónico nativa) ni con ubicaciones de almacenamiento (por ejemplo, Dropbox) que no estén administrados por TI.  Todas estas funciones están integradas en Office 365 y EMS.  No tendrá que implementar ninguna otra infraestructura para poder disfrutar de ellas.

Una práctica común de implementación de Office 365 es exigir que los dispositivos estén inscritos en la administración si se tienen que aprovisionar completamente con configuraciones de aplicaciones/certificados/Wi-Fi/VPN corporativos, que suele ser el caso de los dispositivos de propiedad corporativa.  Sin embargo, si solo es necesario tener acceso a los documentos y el correo electrónico corporativos (que suele ser el caso de los dispositivos de propiedad personal), se deberán usar las aplicaciones móviles de Office (regidas por [directivas de contención de datos](/intune/deploy-use/protect-apps-and-data-with-microsoft-intune)) y no será preciso inscribir el dispositivo.  En cualquier caso, los datos de Office 365 estarán protegidos con las directivas que se hayan definido.

<!-- Learn more about how to plan and deploy Intune to help secure Office 365 email and data. -->

## Ofrecer un programa "Bring Your Own Device" (BYOD) a todos los empleados
BYOD es cada vez más popular entre las organizaciones como forma de reducir los gastos de hardware o de aumentar las opciones de productividad móvil de los empleados. A día de hoy, casi todo el mundo tiene un teléfono personal, así que, ¿qué necesidad hay de darles otro? El desafío más importante ha sido siempre convencer a los empleados para que inscriban sus propios dispositivos personales en la administración, ya que temen que el departamento de TI pueda verlos y controlarlos.  

Cuando la inscripción de dispositivos no es una opción viable, Intune ofrece un método alternativo de BYOD con el que simplemente se [administran las aplicaciones que contengan datos corporativos](/intune/deploy-use/protect-apps-and-data-with-microsoft-intune).  Intune protege los datos corporativos incluso cuando la aplicación en cuestión tiene acceso a datos personales y a datos corporativos, como ocurre en las aplicaciones móviles de Office.  Como administrador, puede obligar a que los usuarios tengan acceso a Office 365 desde las aplicaciones móviles de Office, así como configurar las aplicaciones con directivas que mantengan los datos protegidos (cifrados, protegidos con PIN, etc.).  Estas directivas evitan la pérdida de datos en aplicaciones y ubicaciones de almacenamiento no administradas, tanto dentro como fuera de esas aplicaciones.  Así, por ejemplo, las directivas impiden que un usuario copie texto de un perfil de correo electrónico corporativo en un perfil de correo electrónico de consumidor, aun cuando ambos perfiles estén configurados en Outlook Mobile.  Se pueden implementar configuraciones similares relativas a otros servicios y aplicaciones que los usuarios de BYOD necesiten.

<!-- Learn more about how to plan and deploy Intune to support BYOD.-->

## Distribuir teléfonos de propiedad corporativa entre los trabajadores de la información
En la actualidad, la mayoría de los trabajadores de la información está en constante movimiento, de modo que la productividad de los dispositivos móviles es esencial para ser competitivos.  Los empleados necesitan un acceso sin trabas a todas las aplicaciones y datos corporativos, en todo momento y estén donde estén.  En este sentido, conviene garantizar que los datos corporativos estén protegidos y los costos administrativos son bajos.  

Intune ofrece [soluciones de aprovisionamiento masivo y administración](/intune/deploy-use/manage-corporate-owned-devices) que se integran con las plataformas de administración de dispositivos corporativos más importantes del mercado de hoy día, incluidos el Programa de inscripción de dispositivos de Apple y la plataforma de seguridad móvil Samsung KNOX.  La creación centralizada de configuraciones de dispositivos con Intune hace posible que el aprovisionamiento de dispositivos corporativos se automatice en un alto grado.  

Imagínese: entrega una caja de iPhone sin abrir a un empleado. El empleado lo enciende y se le guía por un proceso de configuración de marca corporativa en el que debe autenticarse. El iPhone se configura sin problemas con [directivas de seguridad](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) (cifrado de la unidad de disco duro, PIN de dispositivo, etc.), con perfiles de [correo electrónico/Wi-Fi/VPN/certificado](/intune/deploy-use/enable-access-to-company-resources-with-microsoft-intune) y con un conjunto básico de [aplicaciones](/intune/deploy-use/add-apps). Tras ello, el empleado inicia la aplicación Portal de empresa de Intune para tener acceso a una serie de aplicaciones corporativas opcionales disponibles.

<!-- Learn more about how to plan and deploy Intune to support corporate owned devices. -->

## Distribuir tabletas compartidas de uso limitado entre los trabajadores de tareas
Los trabajadores de tareas usan las tecnologías móviles cada vez más.  Por ejemplo, ahora las tabletas compartidas están al orden del día entre los empleados de los comercios al por menor.  Independientemente de si se usan para tramitar una venta o comprobar el inventario de forma inmediata, las tabletas ayudan a lograr una excelente interacción con los clientes.  En este caso, la simplicidad de la experiencia del usuario es fundamental.  Por este motivo, las tabletas se suelen entregar a los empleados en un modo de uso limitado, de forma que solo puedan interactuar con una única aplicación de línea de negocio.  Intune permite aprovisionar de forma masiva, proteger y administrar centralmente estas tabletas de [iOS](/intune/deploy-use/ios-policy-settings-in-microsoft-intune#general-configuration-policy-settings) y [Android](/intune/deploy-use/android-policy-settings-in-microsoft-intune#general-configuration-policy) compartidas que pueden configurarse para funcionar en ese modo de uso limitado.

<!-- Learn more about how to plan and deploy Intune to support shared tablets. -->

## Permitir que los empleados tengan un acceso seguro a Office 365 desde un quiosco público no administrado
A veces, los empleados necesitan usar dispositivos, aplicaciones o exploradores que no se pueden administrar, como los equipos públicos de ferias y hoteles. ¿Conviene dejar que los empleados tengan acceso al correo electrónico corporativo desde esos equipos? Con Intune y Enterprise Mobility Suite, <!--you have choices. The--> la respuesta puede ser simplemente “no” y [limitar el acceso al correo electrónico a los dispositivos administrados por la organización](/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune).  <!-- Alternatively, you can choose to allow limited access to these untrusted computers by requiring multi-factor authentication and only allowing browser access (Outlook Web Access) in a mode where files cannot be downloaded (e.g. email attachments).-->  De esta manera, los empleados con una autenticación sólida no correrán el riesgo de dejar accidentalmente datos corporativos en el equipo que no es de confianza.

<!-- Learn more about how to plan and deploy Intune to support kiosks. -->



<!--HONumber=Jul16_HO4-->


