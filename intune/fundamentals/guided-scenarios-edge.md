---
title: 'Escenario guiado: Implementación de Microsoft Edge para dispositivos móviles'
titleSuffix: Microsoft Intune
description: Obtenga información sobre el escenario guiado para implementar Microsoft Edge para dispositivos móviles desde el portal de administración de dispositivos de Microsoft 365.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e86f3a469169e7a805cb3f56e570ba4d3a90e925
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72585701"
---
# <a name="guided-scenario---deploy-microsoft-edge-for-mobile"></a>Escenario guiado: Implementación de Microsoft Edge para dispositivos móviles 

Al seguir este [escenario guiado](~/fundamentals/guided-scenarios-overview.md), puede asignar la aplicación Microsoft Edge a sus usuarios en dispositivos iOS o Android de su organización. La asignación de esta aplicación permitirá a los usuarios examinar contenido sin problemas con sus dispositivos corporativos. 

Microsoft Edge permite a los usuarios abrirse camino a través del desorden de la web con características integradas que les ayudarán a consolidar, organizar y administrar el contenido de trabajo. Los usuarios de dispositivos iOS y Android que inician sesión con sus cuentas corporativas de Azure AD en la aplicación Microsoft Edge encontrarán el explorador precargado con los **favoritos** del lugar de trabajo y los filtros de sitios web que defina.

> [!NOTE]
> Si ha bloqueado a usuarios para que no inscriban dispositivos iOS o Android, en este escenario no se habilitará la inscripción y los usuarios deberán instalar Edge por su propia cuenta.
Están disponibles las características empresariales de Microsoft Edge siguientes habilitadas por directivas de Intune: 

- **Identidad dual**: los usuarios pueden agregar una cuenta profesional, al igual que una cuenta personal, para realizar la exploración. Hay una separación total entre ambas identidades, que es similar a la arquitectura y experiencia existente en Office 365 y Outlook. Los administradores de Intune podrán establecer las directivas deseadas para lograr una experiencia de exploración protegida dentro de la cuenta profesional. 
- **Integración de directivas de protección de la aplicación Intune**: los administradores ahora pueden dirigir las directivas de protección de aplicación a Microsoft Edge, incluido el control de las acciones de cortar, copiar y pegar, lo que impide las capturas de pantalla y garantiza que los vínculos seleccionados por el usuario solo se abran en otras aplicaciones administradas.
- **Integración de proxy de la aplicación de Azure**: los administradores pueden controlar el acceso a las aplicaciones web y a las aplicaciones SaaS, lo que permite garantizar que las aplicaciones basadas en explorador solo se ejecuten en el explorador seguro de Microsoft Edge, ya sea que los usuarios finales se conecten desde la red corporativa o desde Internet. 
- **Favoritos administrados y accesos directos a la página principal**: para facilitar el acceso, los administradores pueden establecer direcciones URL para que aparezcan en los favoritos cuando los usuarios finales estén en su contexto corporativo. Los administradores pueden establecer un acceso directo a la página principal, que se mostrará como el acceso directo principal cuando el usuario corporativo abra una página o una pestaña nueva en Microsoft Edge.

## <a name="prerequisites"></a>Requisitos previos

- [Establecer la entidad de MDM en Intune](mdm-authority-set.md#set-mdm-authority-to-intune): la configuración de la entidad de administración de dispositivos móviles (MDM) determina cómo se administran los dispositivos. Como administrador de TI, debe establecer una entidad de MDM antes de que los usuarios puedan inscribir dispositivos para la administración.
- Permisos de administrador de Intune necesarios:
    - Permisos de lectura, creación, eliminación y asignación de aplicaciones administradas
    - Permisos de lectura, creación y asignación de aplicaciones móviles
    - Permisos de lectura, creación y asignación de conjuntos de directivas
    - Permiso de lectura y actualización de la organización

## <a name="step-1---introduction"></a>Paso 1: introducción

Al seguir el escenario guiado **Implementar Microsoft Edge para dispositivos móviles**, configurará una implementación básica de Microsoft Edge para un grupo seleccionado de usuarios de iOS y Android. Esta implementación implementará una **identidad dual** y **accesos directos a los favoritos administrados y a la página de inicio**. Además, Intune instalará de forma automática la aplicación Microsoft Edge en los dispositivos inscritos por los usuarios seleccionados. Esta instalación automática se efectuará en todos los tipos de inscripción controlados por el usuario, entre los que se incluyen: 
- Inscripción de iOS con la aplicación Portal de empresa 
- Inscripción de afinidad de usuario de iOS mediante Apple Business Manager 
- Inscripción de Android heredada con la aplicación Portal de empresa 

En este escenario guiado se habilitará automáticamente **MyApps** para que aparezcan en los favoritos de Microsoft Edge y se configurará el explorador con la misma personalización de marca que haya definido para la aplicación Portal de empresa de Intune. 

### <a name="what-you-will-need-to-continue"></a>Qué se necesita para continuar
Le pediremos los favoritos del lugar de trabajo que necesitan sus usuarios y los filtros que necesita para la exploración web. Asegúrese de llevar a cabo las siguientes tareas antes de continuar:

- Agregue usuarios a los grupos de Azure AD. Para obtener más información, vea [Creación de un grupo básico e incorporación de miembros con Azure Active Directory](https://go.microsoft.com/fwlink/?linkid=2102458).
- Inscriba dispositivos iOS o Android en Intune. Para obtener más información, vea [Inscripción de dispositivos](https://go.microsoft.com/fwlink/?linkid=2102547).
- Recopile una lista de favoritos del lugar de trabajo para agregarlos a Microsoft Edge.
- Recopile una lista de filtros de sitios web para aplicarlos en Microsoft Edge.

## <a name="step-2---basics"></a>Paso 2: aspectos básicos

En este paso debe especificar un nombre y una descripción de las nuevas directivas de Microsoft Edge. Se puede hacer referencia a estas directivas más adelante si necesita cambiar las asignaciones y configuraciones. El escenario guiado agregará y asignará la aplicación Microsoft Edge para dispositivos iOS y la aplicación Microsoft Edge para dispositivos Android. Además, en este paso se crearán directivas de configuración para estas aplicaciones.

## <a name="step-3---configuration"></a>Paso 3: configuración

En este paso, el escenario guiado configurará Microsoft Edge para mostrar las demás aplicaciones asignadas a los usuarios a través de Intune y compartir la misma personalización de marca que la aplicación Portal de empresa de Microsoft Intune. Puede seguir configurando Microsoft Edge con una **dirección URL de acceso directo a la página de inicio**, una lista de **marcadores administrados** y una lista de **direcciones URL bloqueadas**. La **dirección URL de acceso directo a la página de inicio** se mostrará a los usuarios como el primer icono situado debajo de la barra de búsqueda cuando abran una nueva pestaña en Microsoft Edge en su dispositivo. Los **marcadores administrados** son una lista de direcciones URL favoritas que los usuarios tendrán disponibles al usar Microsoft Edge en su contexto de trabajo. Las **direcciones URL bloqueadas** especifican los sitios bloqueados para los usuarios mientras están en su contexto de trabajo. Se permitirán los demás sitios. 

## <a name="step-4---assignments"></a>Paso 4: asignaciones

En este paso puede elegir los grupos de usuarios que desea incluir para que tengan configurado Microsoft Edge para dispositivos móviles para el trabajo. Microsoft Edge también se instalará en todos los dispositivos iOS y Android inscritos por estos usuarios.

## <a name="step-5---review--create"></a>Paso 5: revisión y creación

El último paso permite revisar un resumen de los valores que ha configurado. Una vez que haya revisado las opciones, haga clic en **Crear** para completar el escenario guiado. 

> [!NOTE]
> Edge puede tardar hasta 12 horas en recibir la configuración. Para obtener más información, vea [Directivas de configuración de aplicaciones para Microsoft Intune](~/apps/app-configuration-policies-overview.md).

> [!IMPORTANT]
> Cuando se haya completado el escenario guiado, se mostrará un resumen. Los recursos mencionados en este resumen se pueden modificar más adelante, pero la tabla en la que se muestran estos recursos no se guardará.

## <a name="next-steps"></a>Pasos siguientes

- Mejorar la seguridad del uso de Microsoft Edge mediante la configuración de la integración de directivas de protección de aplicaciones de Intune. Para obtener más información, vea [Directivas de protección de aplicaciones para Microsoft Edge](~/apps/manage-microsoft-edge.md#application-protection-policies-for-microsoft-edge).
- Si desea incluir sitios de intranet, explore la protección del acceso con la integración de proxy de la aplicación de Azure. Para obtener más información, vea [Configuración de los valores del proxy de aplicación para Microsoft Edge](~/apps/manage-microsoft-edge.md#configure-application-proxy-settings-for-microsoft-edge).

