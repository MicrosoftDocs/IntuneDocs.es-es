---
title: Formas habituales de usar Intune | Microsoft Intune
description: Enumera seis tareas habituales en las que ayuda Intune
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f37d4ff-b5a7-4a89-8884-a6184908b09c
ms.reviewer: robstackmsft
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a5256d4decfcd14de2d50a32a0906b6894639010
ms.openlocfilehash: 9cb6a1e28e36a972a14cb39c12c3a539f4425c71


---

# Formas habituales de usar Intune

Antes de profundizar en las tareas de implementación, es importante alinear a las partes interesadas en la movilidad empresarial de la empresa con respecto a los objetivos empresariales.  Esto es importante tanto si no está familiarizado con la movilidad empresarial como si está realizando la migración desde otro producto.  Las necesidades de movilidad empresarial están evolucionando dinámicamente y el enfoque de Microsoft para abordar estas necesidades puede diferir del de otras soluciones del mercado.  La mejor manera de alinearse con respecto a los objetivos empresariales consiste en expresar lo que quiere lograr en los escenarios que le interesa habilitar para sus empleados, socios y equipo de TI.  A continuación se muestra una breve introducción a los seis escenarios más habituales que dependen de Intune, junto con vínculos para obtener más información sobre cómo planear e implementar cada uno de ellos.

>[!NOTE]
>¿Quiere saber cómo usa Intune el departamento de TI de Microsoft para permitir que los empleados de Microsoft accedan a los recursos corporativos en sus dispositivos móviles al tiempo que protegen los datos corporativos? [Lea este caso práctico técnico](https://www.microsoft.com/itshowcase/Article/Content/588) para ver en detalle cómo el departamento de TI de Microsoft usa Intune y otros servicios para administrar identidades, dispositivos, aplicaciones y datos.  

>[!IMPORTANT]
>Asegurarse de que los dispositivos móviles estén actualizados<br>
>A la luz de los ataques de malware "Trident" recientes en dispositivos iOS, hemos publicado una nueva entrada de blog sobre cómo [asegurarse de que los dispositivos móviles estén actualizados con Microsoft Intune](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/26/ensuring-mobile-devices-are-up-to-date-using-microsoft-intune/) para que conozca las distintas formas en las que Intune puede ayudar a proteger y mantener actualizados sus dispositivos.

## Proteger los datos y el correo electrónico locales para que los dispositivos móviles tengan un acceso seguro
La mayoría de las estrategias de movilidad empresarial empiezan con un plan para permitir el acceso seguro al correo electrónico para los empleados con dispositivos móviles a través de Internet. Muchas organizaciones todavía tienen datos y servidores de aplicaciones locales, como Microsoft Exchange, hospedados en la red corporativa. Intune y Microsoft Enterprise Mobility + Security (EMS) proporcionan una [solución de acceso condicional](/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune) integrada de forma única para Exchange Server que se asegura de que ninguna aplicación móvil pueda acceder al correo electrónico hasta que el dispositivo se inscriba con Intune, todo ello sin necesidad de implementar otra máquina de puerta de enlace en el extremo de la red corporativa.

Además del correo electrónico, Intune permite el acceso a las aplicaciones móviles que requieren un acceso seguro a los datos locales, como un servidor de aplicaciones de línea de negocio.  Esto se suele hacer mediante [certificados administrados por Intune](/intune/deploy-use/secure-resource-access-with-certificate-profiles) para el control de acceso combinados con un proxy o puerta de enlace VPN estándar en el perímetro, como el proxy de aplicación de Microsoft Azure AD.  En estos casos, la única manera de tener acceso a los datos corporativos es inscribir el dispositivo en la administración.  Una vez inscrito, el sistema de administración se asegura de que los dispositivos que accedan a los datos corporativos cumplan las directivas.  Además, [la herramienta de ajuste de aplicaciones y el SDK de aplicaciones](/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune) de Intune se pueden usar para ayudar a contener los datos de acceso dentro de la aplicación de línea de negocio, de modo que no transmita datos empresariales a aplicaciones o servicios de consumidor.

<!-- Learn more about how to plan and deploy Intune to help secure on-premises email and data. -->

## Proteger los datos y el correo electrónico de Office 365 para que los dispositivos móviles puedan acceder a ellos de forma segura
La protección de los datos empresariales de Office 365 (correo electrónico, documentos, mensajes instantáneos, contactos) no podría ser más sencilla o transparente para los usuarios. Intune y Microsoft Enterprise Mobility + Security proporcionan una solución de acceso condicional integrada de forma única que se asegura de que ningún usuario, aplicación o dispositivo pueda tener acceso a los datos de Office 365 a menos que cumpla los requisitos de cumplimiento de la empresa (es decir, realizar una [autenticación multifactor](/intune/deploy-use/protect-windows-devices-with-multi-factor-authentication), estar inscrito con Intune, usar la aplicación administrada, disponer de una versión compatible del sistema operativo, tener un PIN de dispositivo, contar con un perfil de riesgo de usuario bajo, etc.). Las aplicaciones móviles de Office en sus tiendas de aplicaciones correspondientes están preparadas para adaptarse a las directivas de contención de datos que se pueden configurar mediante Intune, lo que permite impedir que los datos se compartan con aplicaciones (por ejemplo, la aplicación de correo electrónico nativa) y ubicaciones de almacenamiento (por ejemplo, Dropbox) que no están administradas por el equipo de TI.  Todas estas funciones están integradas en Office 365 y EMS.  No es necesario implementar una infraestructura adicional para obtener estas ventajas.

Una práctica habitual de implementación de Office 365 consiste en requerir que los dispositivos se inscriban en la administración si necesitan aprovisionarse por completo con configuraciones corporativas de aplicaciones, certificados, Wi-Fi o VPN, como suele ocurrir con los dispositivos de empresa.  Pero si el usuario solo necesita tener acceso a documentos y el correo electrónico de empresa, como suele suceder con los dispositivos personales, el usuario debe usar las aplicaciones móviles de Office (a las que usted ha [aplicado directivas de contención de datos](/intune/deploy-use/protect-apps-and-data-with-microsoft-intune)) y omitir la inscripción del dispositivo.  En cualquier caso, los datos de Office 365 estarán protegidos por las directivas que haya definido usted.

<!-- Learn more about how to plan and deploy Intune to help secure Office 365 email and data. -->

## Ofrecer un programa "Bring Your Own Device" (BYOD) a todos los empleados
BYOD sigue creciendo en popularidad entre las organizaciones como manera de reducir los gastos en hardware o aumentar las opciones de productividad móvil para los empleados. Hoy en día, prácticamente todas las personas tienen un teléfono personal. ¿Por qué obligarles a cargar con otro? El principal desafío siempre ha sido convencer a los empleados de que inscriban sus dispositivos personales en la administración, ya que les inquieta lo que el departamento de TI pueda ver en su dispositivo y hacer con él.  

Cuando la inscripción de dispositivos no es una opción viable, Intune ofrece un método BYOD alternativo, que consiste simplemente en [administrar las aplicaciones que contienen datos corporativos](/intune/deploy-use/protect-apps-and-data-with-microsoft-intune).  Intune protege los datos corporativos, incluso si la aplicación en cuestión tiene acceso a datos personales y corporativos, como es el caso de las aplicaciones móviles de Office.  Como administrador, puede requerir que los usuarios accedan a Office 365 desde las aplicaciones móviles de Office y que configuren las aplicaciones con directivas de protección de datos (cifrado, protección con PIN, etc.).  Estas directivas impiden la pérdida de datos en aplicaciones no administradas y ubicaciones de almacenamiento, tanto dentro como fuera de estas aplicaciones.  Por ejemplo, las directivas impiden que un usuario copie texto de un perfil de correo electrónico corporativo a un perfil de correo electrónico de consumidor, incluso si ambos perfiles están configurados dentro de Outlook Mobile.  Se pueden implementar configuraciones similares para otros servicios y aplicaciones requeridos por usuarios BYOD.

<!-- Learn more about how to plan and deploy Intune to support BYOD.-->

## Emitir teléfonos de empresa para los trabajadores de información
Hoy en día, la mayoría de los trabajadores de información son móviles, por lo que la productividad con dispositivos móviles es fundamental para ser competitivos.  Estos empleados necesitan tener acceso sin problemas a todas las aplicaciones y los datos de la empresa, en cualquier momento y desde cualquier lugar.  Debe asegurarse de que los datos de la empresa estén seguros y los costos administrativos sean bajos.  

Intune ofrece [soluciones de administración y aprovisionamiento masivo](/intune/deploy-use/manage-corporate-owned-devices) que se integran con las plataformas de administración de dispositivos corporativos más importantes del mercado actual, incluyendo el Programa de inscripción de dispositivos de Apple y la plataforma de seguridad móvil Samsung KNOX.  La creación centralizada de configuraciones de dispositivos con Intune hace que el aprovisionamiento de dispositivos corporativos pueda automatizarse en gran medida.  

Imagínese que le entrega a un empleado un iPhone nuevo. El empleado lo enciende y sigue el procedimiento de configuración de la empresa, en el que debe autenticarse. El iPhone se configura sin problemas con [directivas de seguridad](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) (cifrado del disco duro, PIN de dispositivo, etc.), [perfiles de correo electrónico, Wi-Fi, VPN y certificados](/intune/deploy-use/enable-access-to-company-resources-with-microsoft-intune) y un conjunto básico de [aplicaciones](/intune/deploy-use/add-apps). Después, el empleado inicia la aplicación de portal de empresa de Intune para tener acceso a aplicaciones corporativas opcionales que están a su disposición.

<!-- Learn more about how to plan and deploy Intune to support corporate owned devices. -->

## Emitir tabletas compartidas de uso limitado para los trabajadores de tareas
Los trabajadores de tareas cada vez usan más las tecnologías móviles.  Por ejemplo, hoy en día, en muchos comercios los empleados usan tabletas compartidas.  Ya sea para procesar una venta o para consultar el inventario de forma inmediata, las tabletas permiten crear interacciones excelentes con el cliente.  En este caso es fundamental la simplicidad de la experiencia del usuario.  Por este motivo, las tabletas se suelen entregar a los empleados en un modo de uso limitado, de modo que solo puedan interactuar con una aplicación de línea de negocio.  Intune permite aprovisionar de forma masiva, proteger y administrar centralmente estas tabletas compartidas [iOS](/intune/deploy-use/ios-policy-settings-in-microsoft-intune#general-configuration-policy-settings) y [Android](/intune/deploy-use/android-policy-settings-in-microsoft-intune#general-configuration-policy), que se pueden configurar para que se ejecuten en el modo de uso limitado.

<!-- Learn more about how to plan and deploy Intune to support shared tablets. -->

## Permitir que los empleados tengan acceso seguro a Office 365 desde un quiosco multimedia público no administrado
A veces, los empleados necesitan usar dispositivos, aplicaciones o exploradores que no puede administrar, como equipos públicos en ferias comerciales y hoteles. ¿Debe permitir que los empleados tengan acceso al correo electrónico de empresa desde ellos? Con Intune y Microsoft Enterprise Mobility + Security, <!--you have choices. The--> puede decidir no hacerlo y [limitar el acceso al correo electrónico a los dispositivos administrados por la organización](/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune).  <!-- Alternatively, you can choose to allow limited access to these untrusted computers by requiring multi-factor authentication and only allowing browser access (Outlook Web Access) in a mode where files cannot be downloaded (e.g. email attachments).-->  De este modo, se asegurará de que un empleado con una autenticación sólida no deje accidentalmente datos corporativos en un equipo que no es de confianza.

<!-- Learn more about how to plan and deploy Intune to support kiosks. -->



<!--HONumber=Sep16_HO1-->


