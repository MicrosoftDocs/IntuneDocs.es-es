---
title: Página Estado del inquilino de Microsoft Intune
titleSuffix: Microsoft Intune
description: Use la página Estado del inquilino de Intune para ver detalles importantes del inquilino sin salir del portal de Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/09/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8bdb74c19e6b996bafc9284bfedaf0608fdf8fb
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55834626"
---
# <a name="intune-tenant-status-page"></a>Página Estado del inquilino de Intune
Use la página Estado del inquilino como centro para mantenerse al día sobre detalles importantes del inquilino, la disponibilidad de la licencia y el uso, el estado del conector y sobre comunicaciones importantes del servicio Intune.  

Para ver el panel, en Azure Portal, vaya a **Intune > Estado del inquilino**.  Estado del inquilino aparece en el grupo **Ayuda y soporte técnico**.  

La página se divide en cuatro áreas:

## <a name="tenant-details"></a>Detalles del inquilino
Detalles del inquilino proporciona información de un vistazo sobre el inquilino. Vea detalles como el nombre y la ubicación del inquilino, la entidad de MDM y el número de versión del servicio de inquilinos. El número de versión del servicio es un vínculo que abre el artículo *Novedades de Intune* en Microsoft Docs, donde puede leer sobre las últimas características y actualizaciones para el servicio Intune.  

En esta sección también se proporciona información básica sobre las licencias disponibles y cuántas se han asignado a los usuarios. No se muestran las licencias de los dispositivos.

## <a name="connector-status"></a>Estado del conector
Estado del conector es una ubicación única para revisar el estado de todos los conectores disponibles para Intune.  

Los conectores son:
- **Conexiones que se configuran a servicios externos**. Por ejemplo, el servicio *Programa de Compras por Volumen de Apple* o el servicio *Windows Autopilot*.  El estado de este tipo de conector se basa en la hora de la última sincronización correcta.
- **Certificados o credenciales necesarios para conectarse a un servicio externo no administrado**, como certificados de *Apple Push Notification Services* (APN). El estado de este tipo de conector se basa en la marca de tiempo de expiración del certificado o la credencial.  

De forma predeterminada, solo se muestran cinco conectores. Puede seleccionar **Ver todos los conectores** para ampliar esta lista a fin de ver todos los conectores disponibles, incluidos aquellos que no se han configurado para usarse.  

Si hay más de un conector de cualquier tipo, el estado es un resumen de todos esos conectores. El estado mínimo de cualquier conector se usa como estado del grupo.  

Los conectores con un estado incorrecto siempre se muestran en la parte superior de la lista. Luego aparecen los conectores con advertencias y, después, la lista de conectores correctos. Los conectores que todavía no se han configurado aparecen al final.

**Estado del conector**:
- **Incorrecto**:
    - El certificado o la credencial ha expirado
    - La última sincronización fue hace tres o más días
- **Advertencia**:
    - El certificado o la credencial expira en siete días
    - La última sincronización fue hace más de un día
- **Correcto**:
    - El certificado o la credencial no expira en los próximos siete días
    - La última sincronización fue hace menos de un día  

Cuando se selecciona un conector de la lista, el portal presenta la página del portal que es relevante para crear o configurar ese conector.  Por ejemplo, si selecciona el conector **Fecha de caducidad de VPP**, se abre la página **Tokens del programa de compras por volumen de iOS**, donde puede ver más detalles sobre ese conector. Luego puede crear una nueva configuración o editar y solucionar problemas con una ya existente.  

## <a name="intune-service-health"></a>Estado del servicio Intune  
Puede ver detalles de incidentes activos y avisos sin tener que ir al panel de estado del servicio Microsoft 365 ni el centro de mensajes, que se encuentran en el centro de administración de Microsoft 365 en https://portal.office.com. Solo se muestran los incidentes cuyo impacto influye en el inquilino.  

Al seleccionar un incidente, los detalles de este se presentan directamente en la página Estado del inquilino. Para ver avisos e incidentes pasados, seleccione **See past Incidents/Advisories** (Ver incidentes y avisos pasados). Se abre el centro de administración de Microsoft 365, donde puede ver los avisos e incidentes del inquilino de los últimos 30 días.  

Para ver información de *Estado del servicio Intune*, la cuenta debe tener el rol **Administrador global** o **Administrador de servicios** en Azure Active Directory o el portal de administración de Office. Para asignar estos permisos, inicie sesión en el [centro de administración de Microsoft 365](https://portal.officeppe.com/AdminPortal/Home#/homepage) con permisos de Administrador global. Seleccione **Usuarios > Usuarios activos** y luego seleccione la cuenta que requiere acceso. Seleccione **Editar** en los roles, seleccione *Administrador de servicios* o *Administrador global* y luego seleccione **Guardar** para asignar los permisos.  

Las preferencias de comunicación de Estado del servicio Intune solo se pueden establecer a través del centro de administración de Microsoft 365.

## <a name="intune-news"></a>Noticias de Intune  
Vea comunicaciones informativas del equipo del servicio Intune sin tener que ir al centro de mensajes de Office. Las comunicaciones incluyen mensajes sobre los cambios que se han producido recientemente en el servicio Intune o que están en camino para el inquilino.  

De forma predeterminada, se muestran los últimos diez mensajes activos. Para ver mensajes más antiguos, seleccione **See past Messages** (Ver mensajes pasados) para abrir el *centro de mensajes* en el portal del centro de administración de Microsoft 365.  

Para ver información de Noticias de Intune, la cuenta debe tener el rol **Administrador global** o **Administrador de servicios** en Azure Active Directory o el rol **Lector del Centro de mensajes**  en el portal de administración de Office.  Para asignar este permiso, inicie sesión en el [centro de administración de Microsoft 365](https://portal.officeppe.com/AdminPortal/Home#/homepage) con permisos de administrador. Seleccione **Usuarios > Usuarios activos** y luego seleccione la cuenta que requiere acceso. Seleccione **Editar** en *Roles*, seleccione *Administrador de comunicaciones de Teams*  y luego seleccione **Guardar** para asignar los permisos.  

Las preferencias de comunicación de Noticias de Intune solo se pueden establecer a través del centro de administración de Microsoft 365.
