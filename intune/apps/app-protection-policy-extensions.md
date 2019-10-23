---
title: Directivas de protección de aplicaciones para las extensiones
titleSuffix: Microsoft Intune
description: En este tema se describe la directiva de protección de aplicaciones (APP) para las extensiones.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1a94f3d175fe5c036c5e90635a66467263b23122
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72499119"
---
# <a name="protecting-application-extensions"></a>Protección de las extensiones de aplicación

En este artículo se describen las directivas de protección de aplicaciones para las extensiones en Microsoft Intune.

## <a name="add-ins-for-outlook-app"></a>Complementos para la aplicación Outlook

Los complementos de Outlook permiten integrar aplicaciones populares con el cliente de correo electrónico. Los complementos para Outlook están disponibles en la Web, Windows, Mac y Outlook para Android e iOS. El SDK de APP para Intune y las directivas de protección de aplicaciones de Intune no incluyen compatibilidad con la administración de complementos de Outlook, pero existen otras maneras de limitar su uso. Dado que los complementos se administran mediante Microsoft Exchange, los usuarios podrán compartir datos y mensajes entre Outlook y aplicaciones de complementos sin administrar a no ser que en Exchange los complementos estén desactivado para el usuario.

Si quiere que los usuarios finales dejen de acceder a complementos de Outlook e instalarlos (esto afecta a todos los clientes de Outlook), asegúrese de que existen los siguientes cambios en los roles en el centro de administración de Exchange:

- Para evitar que los usuarios instalen complementos de la Tienda Office, quíteles el rol Mi Marketplace.
- Para evitar que los usuarios carguen complementos, quíteles el rol Mis aplicaciones personalizadas.
- Para evitar que los usuarios instalen todos los complementos, quíteles los roles Mis aplicaciones personalizadas y Mi Marketplace.

Estas instrucciones se aplican a Office 365, Exchange 2016, Exchange 2013 a través de Outlook en la Web, Windows, Mac y dispositivos móviles.

- Más información sobre [complementos para Outlook](https://technet.microsoft.com/library/jj943753(v=exchg.150).aspx).
- Aprenda [cómo especificar los administradores y los usuarios que pueden instalar y administrar complementos para la aplicación Outlook](https://technet.microsoft.com/library/jj943754(v=exchg.150).aspx).

## <a name="linkedin-account-connections-for-microsoft-apps"></a>Conexiones de cuenta de LinkedIn para las aplicaciones de Microsoft

Las conexiones de cuenta de LinkedIn permiten a los usuarios ver información pública de perfiles de LinkedIn dentro de determinadas aplicaciones de Microsoft. De forma predeterminada, los usuarios pueden conectarse a sus cuentas profesionales o educativas de LinkedIn y Microsoft para ver información adicional de perfiles de LinkedIn. 

> [!NOTE]
> La integración de LinkedIn no está disponible actualmente para clientes del gobierno de Estados Unidos y para las organizaciones con buzones de correo de Exchange Online hospedados en Alemania, Australia, Canadá, China, Corea del Sur, Francia, India, Japón, Reino Unido y Sudáfrica.

El SDK de Intune y las directivas de protección de aplicaciones de Intune no incluyen compatibilidad con la administración de conexiones de cuentas de LinkedIn, pero existen otras maneras de administrarlas. Puede deshabilitar las conexiones de cuenta de LinkedIn para toda la organización o habilitarlas para determinados grupos de usuarios de su organización. Esta configuración afecta a las conexiones de LinkedIn en las aplicaciones de Office 365 en todas las plataformas (web, móviles y escritorio). Puede:

- Habilitar o deshabilitar las conexiones de cuenta de LinkedIn para el inquilino en Azure Portal. 
- Habilitar o deshabilitar las conexiones de cuenta de LinkedIn para las aplicaciones de Office 2016 de su organización mediante la directiva de grupo.

Si la integración de LinkedIn está habilitada para el inquilino, cuando los usuarios de su organización conecten sus cuentas profesionales o educativas de LinkedIn y Microsoft, tendrán dos opciones: 

- Pueden dar permiso para compartir datos entre ambas cuentas. Esto significa que otorgan permiso para que sus cuentas de LinkedIn compartan datos con sus cuentas profesionales o educativas de Microsoft, así como para que estas últimas compartan datos con sus cuentas de LinkedIn. Los datos que se comparten con LinkedIn dejan los servicios en línea. 
- Pueden dar permiso para compartir datos solo de sus cuentas de LinkedIn a sus cuentas profesionales o educativas de Microsoft.

Si un usuario da su consentimiento para compartir datos entre las cuentas, como con complementos de Office, la integración de LinkedIn usa las API de Microsoft Graph existentes. La integración de LinkedIn usa únicamente un subconjunto de las API disponibles para los complementos de Office y admite diversas exclusiones.


|Permisos de Microsoft Graph  |Descripción  |
|---------|---------|
|Permisos de lectura para [Contactos](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#people-permissions)     |Permite que la aplicación lea una lista puntuada de personas relevantes para el usuario que inició sesión. La lista puede incluir contactos locales, contactos de redes sociales o el directorio de su organización, así como personas con las que se ha comunicado recientemente (por ejemplo, por correo electrónico y Skype).         |
|Permisos de lectura para [Calendarios](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#calendars-permissions)     |Permite que la aplicación lea eventos de los calendarios de los usuarios. Incluye las reuniones recogidas en los calendarios del usuario que ha iniciado sesión, las horas, las ubicaciones y los asistentes.         |
|Permisos de lectura para [Perfil de usuario](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#user-permissions)     |Permite que los usuarios inicien sesión en la aplicación y que la aplicación lea el perfil del usuario que ha iniciado sesión. También permite que la aplicación lea información básica de la empresa para los usuarios que han iniciado sesión.         |
|Subscriptions     |Este ámbito no está disponible y aún no está en uso. Incluye suscripciones proporcionadas por la organización del usuario a aplicaciones y servicios de Microsoft, como Office 365.         |
|Información detallada     |Este ámbito no está disponible y aún no está en uso. Incluye los intereses asociados a la cuenta del usuario que ha iniciado sesión en función de su uso de los servicios de Microsoft.         |

### <a name="learn-more"></a>Obtener más información

- Descubra [información y características de LinkedIn en las aplicaciones de Microsoft](https://go.microsoft.com/fwlink/?linkid=850740).
- Obtenga información sobre la publicación de las conexiones de cuenta de LinkedIn en la página [Plan de desarrollo de Office 365](https://products.office.com/en-US/business/office-365-roadmap?filters=%26freeformsearch=linkedin#abc). 
- Obtenga información sobre cómo [configurar conexiones de cuenta de LinkedIn](https://docs.microsoft.com/azure/active-directory/linkedin-integration).
- Para obtener más información sobre los datos que se comparten entre las cuentas de LinkedIn y las cuentas profesionales o educativas de Microsoft de los usuarios, consulte [LinkedIn in Microsoft applications at your work or school](https://www.linkedin.com/help/linkedin/answer/84077) (LinkedIn en aplicaciones de Microsoft en su trabajo o centro educativo).

