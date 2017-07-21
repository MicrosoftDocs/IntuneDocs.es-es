---
title: Acceso condicional con Intune
titleSuffix: Intune on Azure
description: Formas habituales de usar el acceso condicional con Intune
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a0b8e55e-c3d8-4599-be25-dc10c1027b62
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0ba1f12d762a6288fc2e7a3bfdae637f8ae13a94
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="common-ways-to-use-conditional-access-with-intune"></a>Formas habituales de usar el acceso condicional con Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Para impulsar el cumplimiento del acceso condicional en su organización, es necesario configurar la directiva de cumplimiento de dispositivos móviles de Intune y las funcionalidades de administración de aplicaciones móviles (MAM) de Intune. Se hablará sobre las formas comunes de usar el acceso condicional con Intune.

## <a name="device-based-conditional-access"></a>Acceso condicional basado en dispositivos

Intune y Azure Active Directory trabajan juntos para asegurarse de que solo los dispositivos administrados y compatibles tengan permiso para acceder al correo electrónico, los servicios de Office 365, las aplicaciones de software como servicio (SaaS) y las [aplicaciones locales](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started). Adicionalmente, puede configurar una directiva en Azure Active Directory para permitir que solo los equipos unidos a un dominio o los dispositivos móviles inscritos en Intune tengan acceso a los servicios de Office 365.

Intune ofrece funcionalidades de directivas de cumplimiento de dispositivos que evalúan el estado de cumplimiento de los dispositivos. El estado de cumplimiento se notifica a Azure Active Directory, que usa esta información para exigir la directiva de acceso condicional creada en Azure Active Directory cuando el usuario intenta acceder a los recursos de la compañía.

A partir del [nuevo portal de Azure](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune), las directivas de acceso condicional basado en dispositivos para Exchange en línea y otros productos de Office 365 se configuran mediante el portal de Azure.

-   Más información sobre el [acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

-   Más información sobre [qué es el cumplimiento de dispositivos de Intune](device-compliance.md).

-   Más información sobre la [protección del correo electrónico, Office 365 y otros servicios mediante el acceso condicional con Intune](https://docs.microsoft.com/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune).

### <a name="conditional-access-for-exchange-on-premises"></a>Acceso condicional para Exchange local

El acceso condicional se puede usar para permitir o bloquear el acceso a **Exchange local** en función de las directivas de cumplimiento y el estado de inscripción de los dispositivos. Cuando el acceso condicional se usa en combinación con una directiva de cumplimiento de dispositivo, solo los dispositivos compatibles pueden acceder a Exchange local.

Puede realizar la configuración avanzada del acceso condicional para un control más específico, por ejemplo:

-   Permitir o bloquear determinadas plataformas.

-   Bloquear inmediatamente dispositivos que no estén administrados por Intune.

Todos los dispositivos usados para acceder a Exchange local son objeto de comprobación del cumplimiento cuando se aplican directivas de acceso condicional y cumplimiento de dispositivos.

Cuando los dispositivos no cumplen las condiciones establecidas, se guía al usuario final por el proceso de inscribir el dispositivo para corregir el problema que impide que el dispositivo sea compatible.

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

-   Más información sobre [Intune y Mobile Threat Defense](https://docs.microsoft.com/intune-classic/deploy-use/mobile-threat-defense).

### <a name="conditional-access-for-windows-pcs"></a>Acceso condicional para equipos Windows

El acceso condicional para equipos proporciona funcionalidades similares a las disponibles para dispositivos móviles. Vamos a hablar sobre las formas en que puede usar el acceso condicional al administrar equipos con Intune.

#### <a name="corporate-owned"></a>Propiedad corporativa

-   **Unidos a un dominio de AD local:** esta ha sido la opción de implementación más común de acceso condicional para las organizaciones, quienes están razonablemente cómodas con el hecho de que ya se están administrando sus equipos mediante directivas de grupo de AD o con System Center Configuration Manager.

-   **Unidos a un dominio de Azure AD y administración de Intune:** este escenario va encaminado principalmente a elegir su propio dispositivo (CYOD) y a situaciones de itinerancia de equipos portátiles en las que estos dispositivos raramente se conectan a la red corporativa. El dispositivo se une a Azure AD y se inscribe en Intune, lo que elimina las dependencias del entorno local de AD y de los controladores de dominio. Esta opción puede usarse como criterio de acceso condicional al acceder a los recursos corporativos.

-   **Unidos a un dominio de AD y System Center Configuration Manager:** a partir de la rama actual, System Center Configuration Manager proporciona funcionalidades de acceso condicional que pueden evaluar determinados criterios de cumplimiento, además de los de un equipo unido a un dominio:

    -   ¿Está cifrado el equipo?

    -   ¿Hay malware instalado? ¿Está actualizado?

    -   ¿Está el dispositivo liberado o modificado?

#### <a name="bring-your-own-device-byod"></a>Bring your own device (BYOD)

-   **Unidos al área de trabajo y administración de Intune:** aquí el usuario puede unir sus dispositivos personales para acceder a los servicios y recursos corporativos. Puede usar la unión al área de trabajo e inscribir dispositivos en Intune para recibir directivas de nivel de dispositivo, que es también otra opción para evaluar los criterios de acceso condicional.

## <a name="app-based-conditional-access"></a>Acceso condicional basado en la aplicación

Intune y Azure Active Directory funcionan conjuntamente para asegurarse de que solo las aplicaciones administradas puedan acceder al correo electrónico corporativo u otros servicios de Office 365.

-   Más información sobre el [acceso condicional basado en la aplicación con Intune](app-based-conditional-access-intune.md).

## <a name="next-steps"></a>Pasos siguientes

[Configuración del acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

[Instalación del conector de Exchange local con Intune](https://docs.microsoft.com/intune/exchange-connector-install).

[Creación de una directiva de acceso condicional para el entorno local de Exchange](conditional-access-exchange-create.md)