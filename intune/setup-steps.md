---
title: Configurar Microsoft Intune
description: Condiciones y requisitos previos para comenzar a usar su suscripción de Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/24/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d158503c-1276-422b-ab81-5f66c1cd7e7a
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.openlocfilehash: db499f2d55318919f420e03be0883ec70d949d20
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180382"
---
# <a name="set-up-intune"></a>Configurar Intune

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Estos pasos de configuración le ayudarán a habilitar la administración de dispositivos móviles (MDM) mediante Intune. Los dispositivos deben administrarse antes de conceder acceso a los recursos de la empresa a los usuarios o administrar su configuración.

Algunos pasos, como la configuración de una suscripción a Intune y de la entidad de MDM, son necesarios para la mayoría de los escenarios. Otros pasos, tales como configurar un dominio personalizado o agregar aplicaciones, son opcionales según cuáles sean las necesidades de su empresa.

Si actualmente usa Microsoft System Center Configuration Manager para administrar equipos y servidores, también puede [ampliar Configuration Manager para administrar dispositivos móviles](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management).

>[!TIP]
>Si adquiere un mínimo de 150 licencias de Intune en un plan válido, puede usar el *Beneficio del centro de FastTrack*. Con este servicio, los especialistas de Microsoft trabajan con usted para preparar su entorno para Intune. Consulte [Programa FastTrack para Enterprise Mobility Suite](https://docs.microsoft.com/enterprise-mobility-security/Solutions/enterprise-mobility-fasttrack-program).



| Pasos |                                                                                                                       Estado                                                                                                                       |
|-------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   1   |                                        [Configuraciones compatibles](supported-devices-browsers.md): información necesaria antes de empezar. Esto incluye las configuraciones admitidas y los requisitos de red.                                         |
|   2   |                                                                 [Iniciar sesión en Intune](account-sign-up.md): inicie sesión en la suscripción de prueba o cree una suscripción a Intune.                                                                  |
|   3   |                [Configurar el nombre de dominio](custom-domain-name-configure.md): establezca el registro DNS para conectar el nombre de dominio de la empresa con Intune. Esto proporciona a los usuarios un dominio conocido al conectarse a Intune y usar los recursos.                |
|   4   |                                   [Agregar usuarios](users-add.md): agregue usuarios manualmente o conecte Active Directory para sincronizar usuarios con Intune. Se requiere, a menos que los dispositivos sean de pantalla completa "sin usuarios".                                    |
|   5   |                                            [Asignar licencias](licenses-assign.md): conceda permiso a los usuarios para que usen Intune. Cada usuario o dispositivo sin usuarios necesita una licencia de Intune para poder acceder al servicio.                                             |
|   6   |                                               [Agregar grupos](groups-add.md): use grupos de usuarios y dispositivos para simplificar las tareas de administración. Los grupos se usan para asignar aplicaciones, configuraciones y otros recursos.                                                |
|   7   |                                                                        [Agregar aplicaciones](apps-add.md): las aplicaciones se pueden asignar a grupos e instalarse de forma automática u opcional.                                                                         |
|   8   | [Configurar dispositivos](device-profiles.md): configure los perfiles que administren la configuración de los dispositivos. Los perfiles de dispositivo pueden establecer con antelación la configuración del correo, la VPN, el Wi-Fi y las características del dispositivo. También pueden restringir dispositivos para ayudar a proteger tanto a los propios dispositivos como a los datos. |
|   9   |       [Personalizar el Portal de empresa](company-portal-app.md): personalice el Portal de empresa de Intune que los usuarios emplean para inscribir dispositivos e instalar aplicaciones. Estos valores se muestran tanto en la aplicación Portal de empresa como en el sitio web del Portal de empresa de Intune.       |
|  10   |                                [Habilitar la inscripción de dispositivos](mdm-authority-set.md): habilite la administración de Intune de dispositivos iOS, Windows, Android y Mac estableciendo la entidad MDM y activando plataformas específicas.                                 |
|  11   |                                                        [Configurar directivas de aplicaciones](app-protection-policy.md): proporcione valores concretos en función de las directivas de protección de aplicaciones en Microsoft Intune.                                                         |

