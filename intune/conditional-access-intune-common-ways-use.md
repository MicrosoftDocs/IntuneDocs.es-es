---
title: Escenarios de acceso condicional
titlesuffix: Microsoft Intune
description: Obtenga información sobre cómo se acostumbra a utilizar el acceso condicional de Intune para obtener acceso condicional basado en el dispositivo y en la aplicación.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/25/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a0b8e55e-c3d8-4599-be25-dc10c1027b62
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started; seodec18
ms.openlocfilehash: 7073c5c617806bcf35934aba73bf15a9a195a506
ms.sourcegitcommit: 5058dbfb0e224207dd4e7ca49712c6ad3434c83c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112483"
---
# <a name="what-are-common-ways-to-use-conditional-access-with-intune"></a>¿Cuáles son las formas habituales de usar el acceso condicional con Intune?

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Hay dos tipos de acceso condicional con Intune: acceso condicional basado en el dispositivo y acceso condicional basado en la aplicación. Debe configurar las directivas de cumplimiento relacionadas para aplicar el cumplimiento del acceso condicional en su organización. Normalmente, el acceso condicional se utiliza para, por ejemplo, permitir o bloquear el acceso a Exchange local, controlar el acceso a la red o integrarse con una solución de Mobile Threat Defense.

La siguiente información le ayudará a comprender cómo usar las capacidades de cumplimiento de *dispositivos* móviles de Intune y las capacidades de administración de *aplicaciones* móviles (MAM) de Intune. 

> [!NOTE]
> El acceso condicional es una función de Azure Active Directory que se incluye con una licencia Premium de Azure Active Directory. Intune mejora esta función al agregar el cumplimiento de dispositivos móviles y la administración de aplicaciones móviles a la solución.

## <a name="device-based-conditional-access"></a>Acceso condicional basado en dispositivos

Intune y Azure Active Directory trabajan juntos para asegurarse de que solo los dispositivos administrados y compatibles tengan permiso para acceder al correo electrónico, los servicios de Office 365, las aplicaciones de software como servicio (SaaS) y las [aplicaciones locales](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started). Adicionalmente, puede configurar una directiva en Azure Active Directory para permitir que solo los equipos unidos a un dominio o los dispositivos móviles inscritos en Intune tengan acceso a los servicios de Office 365.

Intune ofrece funcionalidades de directivas de cumplimiento de dispositivos que evalúan el estado de cumplimiento de los dispositivos. El estado de cumplimiento se notifica a Azure Active Directory, que usa esta información para exigir la directiva de acceso condicional creada en Azure Active Directory cuando el usuario intenta acceder a los recursos de la compañía.

Las directivas de acceso condicional basado en dispositivos para Exchange en línea y otros productos de Office 365 se configuran mediante [Azure Portal](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).

-   Más información sobre el [acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

-   Más información sobre las [directivas de cumplimiento de dispositivos de Intune](device-compliance.md).

-   Más información sobre la [protección del correo electrónico, Office 365 y otros servicios mediante el acceso condicional con Intune](app-based-conditional-access-intune.md).

> [!NOTE]
> En los dispositivos Android, cuando habilita el acceso basado en dispositivos para SharePoint Online, los usuarios deben activar la opción **Habilitar acceso al explorador** en el dispositivo inscrito como se indica aquí:
> 1. Inicie la **aplicación de portal de empresa**.
> 2. Vaya a la página **Configuración** desde los tres puntos (...) o el botón de menú de hardware.
> 3. Presione el botón **Habilitar acceso al explorador** . 
> 4. En el explorador Chrome, cierre la sesión de Office 365 y reinicie Chrome.

### <a name="conditional-access-for-exchange-on-premises"></a>Acceso condicional para Exchange local

El acceso condicional se puede usar para permitir o bloquear el acceso a **Exchange local** en función de las directivas de cumplimiento y el estado de inscripción de los dispositivos. Cuando el acceso condicional se usa en combinación con una directiva de cumplimiento de dispositivo, solo los dispositivos compatibles pueden acceder a Exchange local.

Puede realizar la configuración avanzada del acceso condicional para un control más específico, por ejemplo:

-   Permitir o bloquear determinadas plataformas.

-   Bloquear inmediatamente dispositivos que no estén administrados por Intune.

Todos los dispositivos usados para acceder a Exchange local son objeto de comprobación del cumplimiento cuando se aplican directivas de acceso condicional y cumplimiento de dispositivos.

Cuando los dispositivos no cumplen las condiciones establecidas, se guía al usuario final por el proceso de inscripción del dispositivo para corregir el problema que impide que el dispositivo sea conforme.

#### <a name="how-conditional-access-for-exchange-on-premises-works"></a>Funcionamiento del acceso condicional en Exchange local

Intune Exchange Connector extrae todos los registros de Exchange Active Sync (EAS) que existen en el servidor de Exchange de forma que Intune pueda tomar estos registros y asignarlos a registros de dispositivos de Intune. Estos registros son de dispositivos inscritos y reconocidos por Intune. El proceso permite o bloquea el acceso al correo electrónico.

Si el registro de EAS es completamente nuevo e Intune no lo sabe, emite un cmdlet que bloquea el acceso al correo electrónico. A continuación encontrará más detalles sobre cómo funciona este proceso:

![Exchange local con diagrama de flujo de la entidad de certificación](./media/ca-intune-common-ways-1.png)

1.  El usuario intenta acceder al correo electrónico corporativo, que está hospedado en Exchange local 2010 SP1 o posterior.

2.  Si el dispositivo no se administra mediante Intune, tendrá bloqueado el acceso al correo electrónico. Intune envía notificaciones de bloqueo al cliente de EAS.

3.  EAS recibe la notificación de bloqueo, mueve el dispositivo a cuarentena y envía el correo electrónico de cuarentena con pasos de corrección que contienen vínculos para que los usuarios puedan inscribir sus dispositivos.

4.  Tiene lugar el proceso de unirse al área de trabajo, que es el primer paso para que el dispositivo se administre mediante Intune.

5.  El dispositivo se inscribe en Intune.

6.  Intune asigna el registro de EAS a un registro del dispositivo y guarda el estado de cumplimiento del dispositivo.

7.  El id. de cliente de EAS se registra mediante el proceso de Registro de dispositivos de Azure AD, que crea una relación entre el registro del dispositivo de Intune y el id. de cliente de EAS.

8.  El Registro de dispositivos de Azure AD guarda la información de estado del dispositivo.

9.  Si el usuario satisface las directivas de acceso condicional, Intune emite un cmdlet mediante Intune Exchange Connector que permite sincronizar el buzón de correo.

10. El servidor de Exchange envía la notificación al cliente de EAS para que el usuario pueda acceder al correo electrónico.

#### <a name="whats-the-intune-role"></a>¿Cuál es la función de Intune?

Intune evalúa y administra el estado del dispositivo.

#### <a name="whats-the-exchange-server-role"></a>¿Cuál es la función del servidor de Exchange?

El servidor de Exchange proporciona la API y la infraestructura para mover los dispositivos a su cuarentena.

> [!IMPORTANT]
> Tenga en cuenta que el usuario que usa el dispositivo debe tener asignado un perfil de cumplimiento para que se pueda evaluar el cumplimiento del dispositivo. Si no se implementa ninguna directiva de cumplimiento en el usuario, el dispositivo se considera conforme y no se aplicarán restricciones de acceso.

### <a name="conditional-access-based-on-network-access-control"></a>Acceso condicional basado en el control de acceso a redes

Intune se integra con partners como Cisco ISE, Aruba Clear Pass y Citrix NetScaler para proporcionar controles de acceso en función de la inscripción en Intune y el estado de cumplimiento del dispositivo.

Cuando los usuarios intentan acceder a los recursos corporativos mediante Wi-Fi o VPN, se les puede permitir o denegar el acceso. Todo depende de si el dispositivo se administra mediante Intune y guarda conformidad con las directivas de cumplimiento de dispositivos de Intune.

-   Obtenga más información sobre la [integración NAC con Intune](network-access-control-integrate.md).

### <a name="conditional-access-based-on-device-risk"></a>Acceso condicional basado en el riesgo del dispositivo

Intune se ha asociado con proveedores de Mobile Threat Defense para proporcionar una solución de seguridad para la detección de malware, troyanos y otras amenazas en los dispositivos móviles.

#### <a name="how-the-intune-and-mobile-threat-defense-integration-works"></a>Funcionamiento de la integración de Intune y Mobile Threat Defense

Cuando los dispositivos móviles tienen instalado el agente de Mobile Threat Defense, este puede devolver mensajes de estado de cumplimiento a Intune para notificar si se ha encontrado una amenaza en el dispositivo móvil propiamente dicho.

La integración de Intune y Mobile Threat Defense juega un papel en las decisiones de acceso condicional basado en el riesgo del dispositivo.

-   Más información sobre [Intune y Mobile Threat Defense](mobile-threat-defense.md).

### <a name="conditional-access-for-windows-pcs"></a>Acceso condicional para equipos Windows

El acceso condicional para equipos proporciona funcionalidades similares a las disponibles para dispositivos móviles. Vamos a hablar sobre las formas en que puede usar el acceso condicional al administrar equipos con Intune.

#### <a name="corporate-owned"></a>Propiedad corporativa

-   **Unidos a un dominio de AD local:** esta opción se usa habitualmente por las organizaciones que están razonablemente cómodas con la manera en que ya se están administrando sus equipos mediante directivas de grupo de AD o con System Center Configuration Manager.

-   **Unidos a un dominio de Azure AD y administración de Intune:** este escenario va encaminado principalmente a elegir su propio dispositivo (CYOD) y a situaciones de itinerancia de equipos portátiles en las que estos dispositivos raramente se conectan a la red corporativa. El dispositivo se une a Azure AD y se inscribe en Intune, lo que elimina las dependencias del entorno local de AD y de los controladores de dominio. Esta opción puede usarse como criterio de acceso condicional al acceder a los recursos corporativos.

-   **Unidos a un dominio de AD y System Center Configuration Manager:** a partir de la rama actual, System Center Configuration Manager proporciona funcionalidades de acceso condicional que pueden evaluar determinados criterios de cumplimiento, además de los de un equipo unido a un dominio:

    -   ¿Está cifrado el equipo?

    -   ¿Hay malware instalado? ¿Está actualizado?

    -   ¿Está el dispositivo liberado o modificado?

#### <a name="bring-your-own-device-byod"></a>Bring your own device (BYOD)

-   **Unidos al área de trabajo y administración de Intune:** aquí el usuario puede unir sus dispositivos personales para obtener acceso a los servicios y recursos corporativos. Puede usar la unión al área de trabajo e inscribir dispositivos en Intune para recibir directivas de nivel de dispositivo, que es también otra opción para evaluar los criterios de acceso condicional.

## <a name="app-based-conditional-access"></a>Acceso condicional basado en la aplicación

Intune y Azure Active Directory funcionan conjuntamente para asegurarse de que solo las aplicaciones administradas puedan acceder al correo electrónico corporativo u otros servicios de Office 365.

-   Más información sobre el [acceso condicional basado en la aplicación con Intune](app-based-conditional-access-intune.md).

## <a name="next-steps"></a>Pasos siguientes

[Configuración del acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

[Instalación del conector de Exchange local con Intune](https://docs.microsoft.com/intune/exchange-connector-install).

[Creación de una directiva de acceso condicional para el entorno local de Exchange](conditional-access-exchange-create.md)
