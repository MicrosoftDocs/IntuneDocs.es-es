---
title: Administración de dispositivos en Microsoft 365
description: Microsoft 365 Enterprise incluye Microsoft Intune. Vea cómo Intune proporciona administración de dispositivos móviles y administración de aplicaciones móviles para su organización. Lea escenarios comunes y use Intune para implementar Microsoft 365 en su entorno.
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/13/2019
ms.topic: conceptual
audience: ITPro
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.technology: ''
ms.custom: intune
ms.assetid: 0649d310-43a7-4b01-85d2-da255d03e1da
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3a15bf0bd8ed0a46f330b159e45d0a5d5a4c7059
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77510391"
---
# <a name="device-management-overview"></a>Información general sobre la administración de dispositivos

Una tarea esencial para cualquier administrador es la de proteger y asegurar los recursos y los datos de la organización. Esta tarea se conoce como *administración de dispositivos*. Los usuarios tienen muchos dispositivos donde que abren y comparten archivos personales, visitan sitios web e instalan aplicaciones y juegos. Estos mismos usuarios también son empleados o alumnos que quieren usar sus dispositivos para acceder a recursos educativos o profesionales, como el correo electrónico y OneNote.

La administración de dispositivos permite a las organizaciones proteger y asegurar sus recursos y datos, y desde diferentes dispositivos.

Si la organización usa un proveedor de administración de dispositivos, tendrá la garantía de que solo acceden a la información de su propiedad aquellas personas y dispositivos que están autorizados. Del mismo modo, los usuarios de los dispositivos pueden acceder con tranquilidad a los datos de su trabajo desde la comodidad de su teléfono, porque saben que su dispositivo cumple los requisitos de seguridad de su organización. Las organizaciones se preguntarán: **¿qué debemos usar para proteger nuestros recursos?**

La respuesta es [Microsoft Intune](what-is-intune.md). Intune ofrece administración de dispositivos móviles (MDM) y administración de aplicaciones móviles (MAM). Estas son algunas tareas esenciales de cualquier solución de MDM o MAM:

- Admitir un entorno móvil variado y administrar dispositivos iOS/iPadOS, Android, Windows y macOS de forma segura.
- Garantizar que los dispositivos y las aplicaciones sean compatibles con los requisitos de seguridad de la organización.
- Crear directivas que ayuden a proteger los datos de la organización en dispositivos personales y corporativos.
- Usar una solución móvil única y unificada para aplicar estas directivas y ayudar a administrar dispositivos, aplicaciones, usuarios y grupos.
- Proteger la información de la empresa al ayudar a controlar la manera en que los empleados tienen acceso a sus datos y los comparten.

Intune se incluye con Microsoft Azure y Microsoft 365 y se integra con Azure Active Directory (Azure AD). Con Azure AD es más fácil controlar quién tiene acceso y a qué tiene acceso.

## <a name="microsoft-intune"></a>Microsoft Intune

Muchas organizaciones, como Microsoft, usan Intune para proteger datos de su propiedad a los que acceden los usuarios desde sus dispositivos móviles personales o de la empresa. Intune incluye directivas de configuración de dispositivos y aplicaciones, directivas de actualización de software y estados de instalación (gráficos, tablas e informes) con los que puede proteger y supervisar el acceso a los datos.

Es habitual que las personas tengan varios dispositivos que usan plataformas distintas. Por ejemplo, es posible que un empleado use Surface Pro para el trabajo y un dispositivo móvil Android a nivel personal. Y es habitual que una persona acceda a los recursos de la organización, como Microsoft Outlook y SharePoint, desde distintos dispositivos.

Con Intune, es posible administrar varios dispositivos por persona y las distintas plataformas que se ejecutan en cada uno, como iOS/iPadOS, macOS, Android y Windows. Intune separa las directivas y la configuración por plataforma de dispositivo, para que resulte fácil administrar y ver los dispositivos de una plataforma específica.

**[Usos habituales de Microsoft Intune](common-scenarios.md)** es un excelente recurso para ver cómo Intune responde ante preguntas comunes al trabajar con dispositivos móviles. Encontrará escenarios sobre:  

- Protección del correo electrónico con Exchange local
- Acceso a Office 365 de forma segura
- Uso de dispositivos personales para acceder a recursos de la organización

Para más información sobre Intune, consulte [¿Qué es Intune?](what-is-intune.md)

## <a name="integration-with-secure-and-protect-services"></a>Integración con servicios de protección

Una tarea esencial de cualquier solución de administración de dispositivos consiste en proporcionar seguridad y protección. Intune se integra a la perfección con otros servicios para realizar esta tarea. Por ejemplo:

- **Microsoft 365** es un componente clave para simplificar las tareas comunes de TI. En el centro de administración de Microsoft 365, se crean usuarios y se administran grupos. También se puede acceder a otros servicios, como Intune, Azure AD y mucho más.

  Por ejemplo, cree un grupo de dispositivos iOS/iPadOS en Microsoft 365. Después, use Intune para insertar directivas en el grupo de dispositivos iOS/iPadOS que se centra en características de iOS/iPadOS, como acceder a la tienda de aplicaciones, usar AirDrop, hacer copias de seguridad en iCloud, usar el filtro web de Apple y mucho más.

- **Windows Defender** incluye muchas características de seguridad con las que puede proteger dispositivos Windows 10. Por ejemplo, con Intune y Windows Defender juntos puede hacer esto:

  - Habilitar [Windows Defender SmartScreen](../protect/endpoint-protection-windows-10.md) para buscar actividades sospechosas en archivos y aplicaciones en dispositivos móviles.
  - Usar [Protección contra amenazas avanzada de Microsoft Defender (ATP)](../protect/advanced-threat-protection.md) para evitar infracciones de seguridad en dispositivos móviles, y limitar el impacto de una infracción de seguridad mediante el bloqueo de un usuario desde los recursos corporativos.

- **Acceso condicional** es una característica de Azure Active Directory que se integra perfectamente con Intune. Al usar el [acceso condicional](../protect/conditional-access.md), asegúrese de que solo los dispositivos compatibles pueden acceder al correo electrónico, SharePoint y otras aplicaciones.

## <a name="choose-the-device-management-solution-thats-right-for-you"></a>Elegir la solución de administración de dispositivos que más le conviene

Hay dos maneras de aproximarse a la administración de dispositivos. Primero, puede administrar diferentes aspectos de los dispositivos usando las características integradas en Intune. Este método se denomina **Administración de dispositivos móviles (MDM)** . Consiste en que los usuarios "inscriben" sus dispositivos y usan certificados para comunicarse con Intune. Como administrador de TI, puede insertar aplicaciones en dispositivos, restringir dispositivos a un sistema operativo específico, bloquear dispositivos personales y mucho más. Si alguna vez se pierde un dispositivo o lo roban, también puede quitar todos los datos del dispositivo.

El otro enfoque consiste en administrar las aplicaciones en los dispositivos. Este método se denomina **Administración de aplicaciones móviles (MAM)** . Con este método, los usuarios pueden usar sus dispositivos personales para acceder a recursos de la organización. Al abrir una aplicación, como el correo electrónico o SharePoint, se pedirá a los usuarios una autenticación adicional. Si alguna vez se pierde un dispositivo o lo roban, puede quitar todos los datos de la organización del dispositivo.

También puede usar una combinación de [MDM y MAM](byod-technology-decisions.md) juntos.

Al configurar Intune, también elige si trabaja solo en el portal de Azure para administrar dispositivos o si usa Intune y Microsoft 365 juntos para administrar dispositivos. [Migración de administración de dispositivos móviles a Intune en Azure Portal](https://www.microsoft.com/itshowcase/Article/Content/1042/Migrating-mobile-device-management-to-Intune-in-the-Azure-portal) es un caso práctico de Microsoft IT. En este caso práctico, se explica cómo Microsoft IT ha elegido un enfoque moderno de administración de dispositivos y las lecciones aprendidas.

## <a name="simplify-it-tasks-using-the-device-management-admin-center"></a>Simplificación de las tareas de TI mediante el centro de administración de Administración de dispositivos

El [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) es un punto centralizado donde se pueden administrar y completar tareas para los dispositivos móviles. Esta área de trabajo incluye los servicios usados para la administración de dispositivos, incluido Intune y Azure Active Directory, y también para administrar aplicaciones cliente.

En el centro de administración de dispositivos, puede:

- [Inscripción de dispositivos](../enrollment/device-enrollment.md)
- [Establecimiento del cumplimiento de los dispositivos](../protect/device-compliance-get-started.md)
- [Administrar dispositivos](../remote-actions/device-management.md)
- [Administración de aplicaciones](../apps/app-management.md)  
- [eBooks de iOS](../apps/vpp-ebooks-ios.md)  
- [Instalar el conector local de Exchange](../protect/exchange-connector-install.md)  
- [Administración de roles](role-based-access-control.md)  
- Administrar actualizaciones de software
  - [Administrar actualizaciones de Windows 10](../protect/windows-update-for-business-configure.md)  
  - [Administración de actualizaciones de iOS/iPadOS](../protect/software-updates-ios.md)  
- [Azure Active Directory](https://docs.microsoft.com/azure/active-directory)  
- [Administración de usuarios](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory)
- [Administrar grupos y miembros](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-manage-groups)
- [Solución de problemas](help-desk-operators.md)

## <a name="next-steps"></a>Pasos siguientes

Cuando esté listo para empezar a trabajar con una solución de MDM o MAM, siga los distintos pasos para configurar Intune, inscribir dispositivos y empezar a crear directivas. [Mobile device management for Microsoft 365](https://docs.microsoft.com/microsoft-365/enterprise/mobility-infrastructure) (Administración de dispositivos móviles para Microsoft 365) también es un excelente recurso.
