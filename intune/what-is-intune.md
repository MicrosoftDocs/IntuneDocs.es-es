---
title: "Introducción a Intune en Azure Portal"
titlesuffix: Azure portal
description: "Conozca los conceptos básicos sobre Intune en Azure Portal y cómo puede ayudarle a administrar sus dispositivos\"."
keywords: 
author: arob98
ms.author: angrobe
nmanager: dougeby
ms.date: 02/14/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a085264-232a-4af0-97f1-747496c44517
ms.suite: ems
ms.custom: 
ms.openlocfilehash: 6e2528c243938e81a6f730a950ee3949ca44047c
ms.sourcegitcommit: cccbb6730a8c84dc3a62093b8910305081ac9d24
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2018
---
# <a name="introduction-to-microsoft-intune-in-the-azure-portal"></a>Introducción a Microsoft Intune en Azure Portal


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Al igual que otros servicios de Azure, Microsoft Intune está disponible en Azure Portal. Si selecciona **Intune** en Azure Portal, podrá administrar los dispositivos móviles, los equipos y las aplicaciones de la organización.

>[!NOTE] 
> Si ha usado una versión anterior de Microsoft Intune, puede que le resulte útil la siguiente información:
    * [¿Dónde está mi característica en Azure?](ui-changes.md) es una referencia para mostrar las UI y los flujos de trabajo específicos que cambiaron con la migración a Azure.
    * [Grupos de Intune clásicos en Azure Portal](groups-get-started.md) explica las implicaciones del cambio a los grupos de seguridad de Azure Active Directory para la administración de grupos.

Los aspectos destacados de la experiencia de Microsoft Intune en Azure Portal incluyen lo siguiente:

- Consola integrada para todos los componentes de Enterprise Mobility + Security (EMS)
- Consola basada en HTML basada en estándares web
- Soporte técnico de la API de Microsoft Graph para automatizar muchas acciones
- Grupos de Azure Active Directory (AD) para proporcionar compatibilidad entre todas las aplicaciones de Azure
- Compatibilidad con la mayoría de los exploradores web más modernos

## <a name="before-you-start"></a>Antes de empezar

Para usar Intune en el portal de Azure, debe tener una cuenta de administrador y de inquilino de Intune. [Regístrese para obtener una cuenta](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20) si todavía no tiene una.

## <a name="supported-web-browsers-for-the-azure-portal"></a>Exploradores web admitidos en el portal de Azure

El portal de Azure funciona en la mayoría de equipos PC, Mac y tabletas más modernos. No es compatible con teléfonos móviles.
Actualmente, se admiten los siguientes exploradores:

- Microsoft Edge (última versión)
- Microsoft Internet Explorer 11
- Safari (solo en Mac, última versión)
- Chrome (última versión)
- Firefox (última versión)

Para obtener la información más reciente sobre los exploradores admitidos, vea [Azure Portal](https://docs.microsoft.com/azure/azure-preview-portal-supported-browsers-devices).

## <a name="microsoft-intune-in-the-azure-portal"></a>Microsoft Intune en Azure Portal

[Azure Portal](https://portal.azure.com) es la ubicación en la que se encuentra el servicio Microsoft Intune. Azure cuenta con varios servicios, muchos de los cuales es posible que no use habitualmente. Para leer una guía rápida para la personalización de la experiencia del portal, vea [Introducción a Intune en Azure Portal](get-started-azure.md).

## <a name="the-microsoft-intune-documentation"></a>Documentación de Microsoft Intune

Este tema, así como todo el conjunto de documentación de Microsoft Intune, se actualiza continuamente. Si tiene sugerencias que le gustaría ver, deje sus comentarios en la sección de comentarios sobre el tema. Queremos saber su opinión.

La documentación refleja la distribución de Microsoft Intune en Azure Portal (se muestra a continuación), para que le resulte más fácil encontrar la información que necesita.

![Cargas de trabajo del portal de Azure](./media/azure-portal-workloads.png)

### <a name="documentation-guide"></a>Guía de documentación

Use la tabla siguiente para encontrar rápidamente y entender las principales áreas de Microsoft Intune.

| Sección                                                      | Descripción                                                                                                                                                                                                                                                                                      |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Introducción y primeros pasos](introduction-intune.md)       | Entienda los conceptos básicos de Intune, lo que incluye:<br /> - Soluciones comunes<br /> - Funcionamiento de Microsoft Intune<br /> - Administración de dispositivos en Intune<br /> - Administración de aplicaciones en Intune<br /> - Enterprise Mobility Management (EMM) con y sin inscripción de dispositivos                                                         |
| [Planear y diseñar](planning-guide.md)                         | Guía para ayudar a planear y diseñar correctamente el entorno de Microsoft Intune.                                                                                                                                                                                                             |
| [Inscripción de dispositivos](device-enrollment.md)                    | Entienda cómo Microsoft Intune ayuda a administrar los dispositivos de los recursos mediante su inscripción en el servicio Intune. Hay varios métodos para inscribir los dispositivos de los recursos.                                                                                                         |
| [Conformidad de dispositivos](device-compliance.md)                    | Las directivas de cumplimiento de dispositivos de Intune definen las reglas y configuraciones con las que debe ser conforme un dispositivo para que Microsoft Intune lo considere conforme. Por ejemplo, exigir una contraseña para el acceso de dispositivos, cifrar los dispositivos y exigir una versión mínima del sistema operativo son ejemplos de cumplimiento. |
| [Configuración de dispositivos](device-profiles.md)                   | Configure las opciones y características en todos los dispositivos que administre con Microsoft Intune mediante la creación de perfiles de dispositivo. Por ejemplo, puede configurar capacidades como las notificaciones, el uso compartido de datos, la compatibilidad con el correo electrónico, la conectividad Wi-Fi, los certificados y Endpoint Protection.              |
| [Dispositivos](device-management.md)                              | Asegúrese de que los dispositivos que administra proporcionen los recursos que los usuarios finales necesitan para realizar su trabajo a la vez que protegen los datos de la empresa frente a riesgos. Para administrar los dispositivos, revise el inventario de dispositivos de los recursos y realice acciones de dispositivo remoto.                                                      |
| [Aplicaciones móviles](app-management.md)                             | Entienda cómo agregar, implementar, supervisar, configurar y proteger las aplicaciones.                                                                                                                                                                                                                             |
| [Acceso condicional](conditional-access.md)                  | Defina condiciones basadas en aplicaciones y dispositivos que filtren el acceso a los datos corporativos.                                                                                                                                                                                                            |
| [Usuarios](users-add.md)                                        | Obtenga más información sobre cómo agregar usuarios de dispositivos y aplicaciones que administre.                                                                                                                                                                                                                                           |
| [Grupos](groups-get-started.md)                              | Obtenga más información sobre cómo crear y administrar grupos con Intune. Con los grupos puede asignar rápidamente directivas de protección y configuración de dispositivos y aplicaciones.                                                                                                                                             |
| [Roles de Intune](role-based-access-control.md)                 | Obtenga más información sobre cómo controlar quién puede realizar las distintas acciones de Intune y cómo se aplican esas acciones. Puede usar los roles integrados que abarcan algunos escenarios de Intune comunes, o crear los suyos propios.                                                                                 |
| [Actualizaciones de software](windows-update-for-business-configure.md) | Obtenga más información sobre cómo configurar las actualizaciones de software para dispositivos Windows 10.                                                                                                                                                                                                                                  |

## <a name="whats-new"></a>Novedades

Para obtener información sobre las características más recientes de Microsoft Intune, vea [Novedades](whats-new.md).
