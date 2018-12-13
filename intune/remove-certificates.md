---
title: 'Eliminación de certificados SCEP o PKCS en Microsoft Intune: Azure | Microsoft Docs'
titleSuffix: ''
description: Los administradores pueden usar la acción de borrar o retirar para quitar certificados de Microsoft Intune. En algunos casos los certificados se eliminan automáticamente, como al anular la inscripción de un dispositivo o quitar una directiva de cumplimiento. En otros, permanecen automáticamente en el dispositivo, como cuando se pierde o se quita la licencia de Intune. Vea lo que sucede con los dispositivos Android, Android Enterprise, iOS, macOS y Windows.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 06b568ee7cc2dc55a8d44cf04b96078b47d8c4b3
ms.sourcegitcommit: 77a1047f5d93c1924e5c9ea243454532881be031
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/28/2018
ms.locfileid: "52579173"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>Eliminación de certificados SCEP y PKCS en Microsoft Intune

En Microsoft Intune, puede agregar certificados SCEP y PKCS a los dispositivos. Estos certificados también se pueden quitar cuando al [borrar](devices-wipe.md#wipe) o [retirar](devices-wipe.md#retire) el dispositivo. En algunos casos los certificados se quitan automáticamente, mientras que en otros permanecen en el dispositivo.

En este artículo se muestran algunos casos comunes y el impacto en los certificados PKCS y SCEP.

> [!NOTE]
> A fin de quitar y revocar certificados para un usuario que se está eliminando de Active Directory (AD) o Azure AD, asegúrese de seguir estos pasos en orden:
>
>    1. Borrar o retirar el dispositivo del usuario
>    2. Eliminar el usuario de AD o Azure AD

## <a name="windows-devices"></a>Dispositivos Windows

#### <a name="scep-certificates"></a>Certificados SCEP

- Un certificado SCEP se revoca *y* se elimina cuando:

  - Un usuario final anula su inscripción
  - Un administrador ejecuta la acción de [borrar](devices-wipe.md#wipe)
  - Un administrador ejecuta la acción de [retirar](devices-wipe.md#retire)
  - El dispositivo se quita del grupo de Azure Active Directory (AD)
  - El perfil de certificación se quita de la asignación de grupo

- Un certificado SCEP se revoca cuando:
  - El administrador cambia o actualiza el perfil SCEP

- Un certificado raíz se elimina cuando:
  - Un usuario final anula su inscripción
  - Un administrador ejecuta la acción de [borrar](devices-wipe.md#wipe)
  - Un administrador ejecuta la acción de [retirar](devices-wipe.md#retire)

- Los certificados SCEP **permanecen** en el dispositivo (es decir, no se revocan ni se quitan) cuando:
  - Un usuario final pierde la licencia de Intune
  - El administrador retira la licencia de Intune
  - El administrador elimina el usuario o el grupo de Azure AD

#### <a name="pkcs-certificates"></a>Certificados PKCS

- Un certificado PKCS se revoca *y* se elimina cuando:

  - Un usuario final anula su inscripción
  - Un administrador ejecuta la acción de [borrar](devices-wipe.md#wipe)
  - Un administrador ejecuta la acción de [retirar](devices-wipe.md#retire)

- Un certificado raíz se elimina cuando:
  - Un usuario final anula su inscripción
  - Un administrador ejecuta la acción de [borrar](devices-wipe.md#wipe)
  - Un administrador ejecuta la acción de [retirar](devices-wipe.md#retire)

- Los certificados PKCS **permanecen** en el dispositivo (es decir, no se revocan ni se quitan) cuando:
  - Un usuario final pierde la licencia de Intune
  - El administrador retira la licencia de Intune
  - El administrador elimina el usuario o el grupo de Azure AD
  - El administrador cambia o actualiza el perfil PKCS
  - El perfil de certificación se quita de la asignación de grupo


## <a name="ios-devices"></a>Dispositivos iOS

#### <a name="scep-certificates"></a>Certificados SCEP

- Un certificado SCEP se revoca *y* se elimina cuando:

  - Un usuario final anula su inscripción
  - Un administrador ejecuta la acción de [borrar](devices-wipe.md#wipe)
  - Un administrador ejecuta la acción de [retirar](devices-wipe.md#retire)
  - El dispositivo se quita del grupo de Azure Active Directory (AD)
  - El perfil de certificación se quita de la asignación de grupo

- Un certificado SCEP se revoca cuando:
  - El administrador cambia o actualiza el perfil SCEP

- Un certificado raíz se elimina cuando:
  - Un usuario final anula su inscripción
  - Un administrador ejecuta la acción de [borrar](devices-wipe.md#wipe)
  - Un administrador ejecuta la acción de [retirar](devices-wipe.md#retire)

- Los certificados SCEP **permanecen** en el dispositivo (es decir, no se revocan ni se quitan) cuando:
  - Un usuario final pierde la licencia de Intune
  - El administrador retira la licencia de Intune
  - El administrador elimina el usuario o el grupo de Azure AD

#### <a name="pkcs-certificates"></a>Certificados PKCS

- Un certificado PKCS se revoca *y* se elimina cuando:

  - Un usuario final anula su inscripción
  - Un administrador ejecuta la acción de [borrar](devices-wipe.md#wipe)
  - Un administrador ejecuta la acción de [retirar](devices-wipe.md#retire)

- Un certificado PKCS se elimina cuando:
  - El perfil de certificación se quita de la asignación de grupo
  
- Un certificado raíz se elimina cuando:
  - Un usuario final anula su inscripción
  - Un administrador ejecuta la acción de [borrar](devices-wipe.md#wipe)
  - Un administrador ejecuta la acción de [retirar](devices-wipe.md#retire)

- Los certificados PKCS **permanecen** en el dispositivo (es decir, no se revocan ni se quitan) cuando:
  - Un usuario final pierde la licencia de Intune
  - El administrador retira la licencia de Intune
  - El administrador elimina el usuario o el grupo de Azure AD
  - El administrador cambia o actualiza el perfil PKCS

## <a name="android-knox-devices"></a>Dispositivos Android KNOX

#### <a name="scep-certificates"></a>Certificados SCEP

- Un certificado SCEP se revoca *y* se elimina cuando:
  - Un usuario final anula su inscripción
  - Un administrador ejecuta la acción de [borrar](devices-wipe.md#wipe)

- Un certificado SCEP se revoca cuando:
  - Un administrador ejecuta la acción de [retirar](devices-wipe.md#retire)
  - El dispositivo se quita del grupo de Azure Active Directory (AD)
  - El perfil de certificación se quita de la asignación de grupo
  - El administrador elimina el usuario o el grupo de Azure Active Directory (AD)
  - El administrador cambia o actualiza el perfil SCEP

- Un certificado raíz se elimina cuando:
  - Un usuario final anula su inscripción
  - Un administrador ejecuta la acción de [borrar](devices-wipe.md#wipe)
  - Un administrador ejecuta la acción de [retirar](devices-wipe.md#retire)

- Los certificados SCEP **permanecen** en el dispositivo (es decir, no se revocan ni se quitan) cuando:
  - Un usuario final pierde la licencia de Intune
  - El administrador retira la licencia de Intune
  - El administrador elimina el usuario o el grupo de Azure AD

#### <a name="pkcs-certificates"></a>Certificados PKCS

- Un certificado PKCS se revoca *y* se elimina cuando:

  - Un usuario final anula su inscripción
  - Un administrador ejecuta la acción de [borrar](devices-wipe.md#wipe)
  - Un administrador ejecuta la acción de [retirar](devices-wipe.md#retire)

- Un certificado raíz se elimina cuando:
  - Un usuario final anula su inscripción
  - Un administrador ejecuta la acción de [borrar](devices-wipe.md#wipe)
  - Un administrador ejecuta la acción de [retirar](devices-wipe.md#retire)

- Los certificados PKCS **permanecen** en el dispositivo (es decir, no se revocan ni se quitan) cuando:
  - Un usuario final pierde la licencia de Intune
  - El administrador retira la licencia de Intune
  - El administrador elimina el usuario o el grupo de Azure AD
  - El administrador cambia o actualiza el perfil PKCS
  - El perfil de certificación se quita de la asignación de grupo
  
  
> [!NOTE]
> Los dispositivos Android for Work no están validados para los escenarios anteriores. Los dispositivos heredados de Android (todos los dispositivos de perfiles que no sean de trabajo ni de Samsung) no están habilitados para la eliminación de certificados. 

## <a name="macos-certificates"></a>Certificados macOS

#### <a name="scep-certificates"></a>Certificados SCEP

- Un certificado SCEP se revoca *y* se elimina cuando:
  - Un usuario final anula su inscripción
  - Un administrador ejecuta la acción de [retirar](devices-wipe.md#retire)
  - El dispositivo se quita del grupo de Azure Active Directory (AD)
  - El perfil de certificación se quita de la asignación de grupo

- Un certificado SCEP se revoca cuando:
  - El administrador cambia o actualiza el perfil SCEP

- Los certificados SCEP **permanecen** en el dispositivo (es decir, no se revocan ni se quitan) cuando:
  - Un usuario final pierde la licencia de Intune
  - El administrador retira la licencia de Intune
  - El administrador elimina el usuario o el grupo de Azure AD

> [!NOTE]
> No se admite el uso de la acción de [borrar](devices-wipe.md#wipe) para el restablecimiento de fábrica de dispositivos macOS.

#### <a name="pkcs-certificates"></a>Certificados PKCS

No se admiten certificados PKCS en macOS.

