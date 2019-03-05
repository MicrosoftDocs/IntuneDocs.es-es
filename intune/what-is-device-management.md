---
title: Administración de dispositivos en Microsoft 365
description: Microsoft 365 Enterprise incluye Microsoft Intune. Vea cómo Intune proporciona a su organización la administración de dispositivos móviles y la administración de aplicaciones móviles, incluidos escenarios comunes y usando Intune para implementar Microsoft 365 en el entorno.
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/21/2018
ms.topic: conceptual
audience: ITPro
ms.prod: microsoft-365-enterprise
ms.service: ''
ms.technology: ''
ms.custom: intune
ms.assetid: 0649d310-43a7-4b01-85d2-da255d03e1da
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 93e34c3de77dde59b87829617b8cbbd2614f7081
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2019
ms.locfileid: "57231254"
---
# <a name="what-is-device-management"></a>¿Qué es la administración de dispositivos? 

Una tarea esencial para cualquier administrador es la de proteger y asegurar los recursos y los datos de la organización. Esta tarea se conoce como administración de dispositivos. Los usuarios tienen muchos dispositivos con los que abren y comparten archivos personales, visitan sitios web e instalan aplicaciones y juegos. Estos usuarios también son empleados y estudiantes que quieren usar sus dispositivos para acceder a recursos educativos o profesionales, tener como el correo electrónico y OneNote. La *administración de dispositivos* permite a las organizaciones proteger y asegurar sus recursos y datos. 

La organización usa un proveedor de administración de dispositivos para tener la garantía de que solo acceden a la información de su propiedad aquellas personas y dispositivos que están autorizados. Del mismo modo, los usuarios de los dispositivos pueden acceder con tranquilidad a los datos de su trabajo desde la comodidad de su teléfono, porque saben que su dispositivo cumple los requisitos de seguridad de su organización. Las organizaciones se preguntarán: **¿qué debemos usar para proteger nuestros recursos?**

Aquí es donde [Microsoft Intune](https://docs.microsoft.com/intune/introduction-intune) entra en juego. Intune ofrece administración de dispositivos móviles (MDM) y administración de aplicaciones móviles (MAM). Estas son algunas tareas esenciales de cualquier solución de MDM o MAM:

- Admitir un entorno móvil variado &mdash;administrar dispositivos iOS, Android, Windows y macOS de forma segura
- Garantizar que los dispositivos y las aplicaciones sean compatibles con los requisitos de seguridad de la organización
- Crear directivas que ayuden a proteger los datos de la organización en dispositivos personales y corporativos
- Usar una solución móvil única y unificada para aplicar estas directivas y ayudar a administrar dispositivos, aplicaciones, usuarios y grupos.

Intune se incluye con Microsoft 365 y se integra con Azure Active Directory (Azure AD). Con Azure AD es más fácil controlar quién tiene acceso y a qué tiene acceso.

## <a name="hello-intune"></a>Intune a fondo
Muchas organizaciones, como Microsoft, usan Intune para proteger datos de su propiedad a los que acceden los usuarios desde sus dispositivos móviles personales o de la empresa. Intune incluye características como directivas de configuración de dispositivos y aplicaciones, directivas de actualización de software y estados de instalación (así como gráficos, tablas e informes) con los que puede proteger y supervisar el acceso a los datos.

Es habitual que las personas tengan varios dispositivos que usan plataformas distintas. Por ejemplo, es posible que un empleado use Surface Pro para el trabajo y un dispositivo móvil Android a nivel personal. Y es habitual que una persona acceda a los recursos de la organización, como Microsoft Outlook y SharePoint, desde distintos dispositivos.

Con Intune es posible administrar varios dispositivos por persona y las distintas plataformas que se ejecutan en cada dispositivo, incluido iOS, macOS, Android y Windows. Intune separa las directivas y la configuración por plataforma de dispositivo, con lo que resulta fácil administrar y ver los dispositivos de una plataforma específica.

**[Usos habituales de Microsoft Intune](https://docs.microsoft.com/intune/common-scenarios)** es un excelente recurso para ver cómo Intune responde ante preguntas comunes al trabajar con dispositivos móviles. Encontrará escenarios sobre:  
- Protección del correo electrónico con Exchange local
- Acceso a Office 365 de forma segura
- Uso de dispositivos personales para acceder a recursos de la organización

## <a name="integration-with-secure-and-protect-services"></a>Integración con servicios de protección
Una tarea esencial de cualquier solución de administración de dispositivos consiste en proporcionar seguridad y protección. Intune se integra a la perfección con otros servicios para realizar esta tarea. Por ejemplo:

- **Microsoft 365** es un componente clave para simplificar las tareas comunes de TI. Con el centro de administración de Microsoft 365, puede crear usuarios, administrar grupos y acceder a otros servicios, como Intune, Azure Active Directory y mucho más. Por ejemplo, puede crear un grupo de dispositivos iOS en Microsoft 365. Después, use Intune para insertar directivas en el grupo de dispositivos iOS que se centra en características de iOS, como acceder a la tienda de aplicaciones, usar AirDrop, hacer copias de seguridad en iCloud, usar el filtro web de Apple y mucho más.

- **Windows Defender** incluye muchas características de seguridad con las que puede proteger dispositivos Windows 10. Por ejemplo, con Intune y Windows Defender juntos puede hacer esto: 

    - Habilitar [Windows Defender SmartScreen](https://docs.microsoft.com/intune/endpoint-protection-windows-10) para buscar actividades sospechosas en archivos y aplicaciones en dispositivos móviles. 
    - Usar [Protección contra amenazas avanzada de Windows Defender (ATP)](https://docs.microsoft.com/intune/advanced-threat-protection) para evitar que se cometan infracciones de seguridad en dispositivos móviles y limitar el impacto de una infracción de seguridad mediante el bloqueo de un usuario desde recursos corporativos.

- **Acceso condicional** es una característica de Azure Active Directory que se integra perfectamente con Intune. Al usar el [acceso condicional](https://docs.microsoft.com/intune/conditional-access), se asegura de que solo los dispositivos compatibles pueden acceder al correo electrónico, a SharePoint y a otras aplicaciones. 

## <a name="choose-the-device-management-solution-thats-right-for-you"></a>Elegir la solución de administración de dispositivos que más le conviene

Hay dos maneras de aproximarse a la administración de dispositivos. Primero, puede administrar todos los aspectos de los dispositivos usando todas las características integradas en Intune. Esto se denomina **Administración de dispositivos móviles (MDM)**. Al seguir este enfoque, los usuarios "inscriben" sus dispositivos y usan certificados para comunicarse con Intune. Como administrador de TI, puede insertar aplicaciones en dispositivos, restringir dispositivos a un sistema operativo específico, bloquear dispositivos personales y mucho más. Si alguna vez se pierde un dispositivo o lo roban, también puede quitar todos los datos del dispositivo. 

El otro enfoque consiste en administrar las aplicaciones en los dispositivos. Esto se denomina **Administración de aplicaciones móviles (MAM)**. En este enfoque, los usuarios pueden usar sus dispositivos personales para acceder a recursos de la organización. Al abrir una aplicación, como el correo electrónico o SharePoint, se pedirá a los usuarios una autenticación adicional. Si alguna vez se pierde un dispositivo o lo roban, puede quitar todos los datos de la organización del dispositivo. 

También puede usar una combinación de [MDM y MAM](https://docs.microsoft.com/intune/byod-technology-decisions) juntos.

Al configurar Intune, también elige si trabaja solo en el portal de Azure para administrar dispositivos o si usa Intune y Microsoft 365 juntos para administrar dispositivos. Vea cómo Microsoft IT eligió un enfoque de administración de dispositivos moderno y conozca las lecciones aprendidas en el caso práctico de Microsoft IT [Migrating mobile device management to Intune in the Azure portal](https://www.microsoft.com/itshowcase/Article/Content/1042/Migrating-mobile-device-management-to-Intune-in-the-Azure-portal) (Migración de administración de dispositivos móviles a Intune en Azure Portal). 

## <a name="simplify-it-tasks-using-the-device-management-dashboard"></a>Simplificar tareas de TI mediante el panel Administración de dispositivos

El panel [Administración de dispositivos](https://devicemanagement.portal.azure.com/) es un punto centralizado donde se pueden administrar y completar tareas para los dispositivos móviles. Este panel incluye los servicios usados para la administración de dispositivos, incluido Intune y Azure Active Directory, y también para administrar aplicaciones cliente. 

En el panel Administración de dispositivos, puede:

- [Inscripción de dispositivos](https://docs.microsoft.com/intune/device-enrollment)
- [Establecimiento del cumplimiento de los dispositivos](https://docs.microsoft.com/intune/device-compliance-get-started)
- [Administrar dispositivos](https://docs.microsoft.com/intune/device-management)
- [Administración de aplicaciones](https://docs.microsoft.com/intune/app-management)  
- [eBooks de iOS](https://docs.microsoft.com/intune/vpp-ebooks-ios)  
- [Instalar el conector local de Exchange](https://docs.microsoft.com/intune/exchange-connector-install)  
- [Administración de roles](https://docs.microsoft.com/intune/role-based-access-control)  
- Administrar actualizaciones de software
  - [Administrar actualizaciones de Windows 10](https://docs.microsoft.com/intune/windows-update-for-business-configure)  
  - [Administrar actualizaciones de iOS](https://docs.microsoft.com/intune/software-updates-ios)  
- [Azure Active Directory](https://docs.microsoft.com/azure/active-directory)  
- [Administración de usuarios](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory)
- [Administrar grupos y miembros](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-manage-groups)
- [Solución de problemas](https://docs.microsoft.com/intune/help-desk-operators)

## <a name="next-step"></a>Paso siguiente
Cuando esté listo para empezar a trabajar con una solución de MDM o MAM, seguir los distintos pasos para configurar Intune, inscribir dispositivos y empezar a crear directivas, lea [Mobile device management for Microsoft 365](https://docs.microsoft.com/microsoft-365/enterprise/mobility-infrastructure) (Administración de dispositivos móviles para Microsoft 365). 
