---
title: 'Eliminación de certificados SCEP o PKCS en Microsoft Intune: Azure | Microsoft Docs'
titleSuffix: ''
description: Los administradores pueden usar la acción de borrar o retirar para quitar certificados de Microsoft Intune. En algunos casos los certificados se eliminan automáticamente, como al anular la inscripción de un dispositivo o quitar una directiva de cumplimiento. En otros, permanecen automáticamente en el dispositivo, como cuando se pierde o se quita la licencia de Intune. Vea lo que sucede con los dispositivos Android, Android Enterprise, iOS, macOS y Windows.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: lacranda
ms.openlocfilehash: e00600abb8327623eff4efe8509670779710ab7d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509036"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>Eliminación de certificados SCEP y PKCS en Microsoft Intune

En Microsoft Intune, puede usar perfiles de certificados de Protocolo de inscripción de certificados simple (SCEP) y Public Key Cryptography Standards (PKCS) para agregar certificados a los dispositivos.

Estos certificados se pueden quitar al [borrar](../remote-actions/devices-wipe.md#wipe) o [retirar](../remote-actions/devices-wipe.md#retire) el dispositivo. También hay casos en los que los certificados se quitan automáticamente y otros en los que permanecen en el dispositivo. En este artículo se muestran algunos casos comunes y el impacto en los certificados PKCS y SCEP.

> [!NOTE]
> A fin de quitar y revocar los certificados de un usuario en una instancia local de Active Directory o de Azure Active Directory (Azure AD), siga estos pasos en orden:
>
> 1. Borre o retire el dispositivo del usuario.
> 2. Quite al usuario de la instancia local de Active Directory o de Azure AD.

## <a name="manually-deleted-certificates"></a>Certificados eliminados manualmente

La eliminación manual de un certificado es un escenario que se aplica a las plataformas y los certificados aprovisionados por SCEP o los perfiles de certificado PKCS. Por ejemplo, un usuario podría eliminar un certificado de un dispositivo si a dicho dispositivo se le sigue aplicando una directiva de certificados.

En este caso, una vez eliminado el certificado, la próxima vez que el dispositivo se registra con Intune se detecta que este no es compatible, ya que carece del certificado esperado. A continuación, Intune emite un nuevo certificado para restaurar el cumplimiento del dispositivo. No es necesaria ninguna acción adicional para restaurar el certificado.

## <a name="windows-devices"></a>Dispositivos Windows

### <a name="scep-certificates"></a>Certificados SCEP

Un certificado SCEP se revoca *y* se elimina cuando:

- Un usuario anula su inscripción.
- Un administrador ejecuta la acción de [borrar](../remote-actions/devices-wipe.md#wipe).
- Un administrador ejecuta la acción de [retirar](../remote-actions/devices-wipe.md#retire).
- El dispositivo se quita de un grupo de Azure AD.
- Un perfil de certificado se quita de la asignación de grupo.

Un certificado SCEP se revoca cuando:
- Un administrador cambia o actualiza el perfil SCEP.

Un certificado raíz se elimina cuando:
- Un usuario anula su inscripción.
- Un administrador ejecuta la acción de [borrar](../remote-actions/devices-wipe.md#wipe).
- Un administrador ejecuta la acción de [retirar](../remote-actions/devices-wipe.md#retire).

Los certificados SCEP *permanecen* en el dispositivo (es decir, no se revocan ni se quitan) cuando:
- Un usuario pierde la licencia de Intune.
- Un administrador retira la licencia de Intune.
- Un administrador elimina el usuario o el grupo de Azure AD.

### <a name="pkcs-certificates"></a>Certificados PKCS

Un certificado PKCS se revoca *y* se elimina cuando:

- Un usuario anula su inscripción.
- Un administrador ejecuta la acción de [borrar](../remote-actions/devices-wipe.md#wipe).
- Un administrador ejecuta la acción de [retirar](../remote-actions/devices-wipe.md#retire).

Un certificado raíz se elimina cuando:
- Un usuario anula su inscripción.
- Un administrador ejecuta la acción de [borrar](../remote-actions/devices-wipe.md#wipe).
- Un administrador ejecuta la acción de [retirar](../remote-actions/devices-wipe.md#retire).

Los certificados PKCS *permanecen* en el dispositivo (es decir, no se revocan ni se quitan) cuando:
- Un usuario pierde la licencia de Intune.
- Un administrador retira la licencia de Intune.
- Un administrador elimina el usuario o el grupo de Azure AD.
- Un administrador cambia o actualiza el perfil PKCS.
- Un perfil de certificado se quita de la asignación de grupo.


## <a name="ios-devices"></a>Dispositivos iOS

### <a name="scep-certificates"></a>Certificados SCEP

Un certificado SCEP se revoca *y* se elimina cuando:

- Un usuario anula su inscripción.
- Un administrador ejecuta la acción de [borrar](../remote-actions/devices-wipe.md#wipe).
- Un administrador ejecuta la acción de [retirar](../remote-actions/devices-wipe.md#retire).
- El dispositivo se quita del grupo de Azure AD.
- Un perfil de certificado se quita de la asignación de grupo.

Un certificado SCEP se revoca cuando:
- Un administrador cambia o actualiza el perfil SCEP.

Un certificado raíz se elimina cuando:
- Un usuario anula su inscripción.
- Un administrador ejecuta la acción de [borrar](../remote-actions/devices-wipe.md#wipe).
- Un administrador ejecuta la acción de [retirar](../remote-actions/devices-wipe.md#retire).

Los certificados SCEP *permanecen* en el dispositivo (es decir, no se revocan ni se quitan) cuando:
- Un usuario pierde la licencia de Intune.
- Un administrador retira la licencia de Intune.
- Un administrador elimina el usuario o el grupo de Azure AD.

### <a name="pkcs-certificates"></a>Certificados PKCS

Un certificado PKCS se revoca *y* se elimina cuando:

- Un usuario anula su inscripción.
- Un administrador ejecuta la acción de [borrar](../remote-actions/devices-wipe.md#wipe).
- Un administrador ejecuta la acción de [retirar](../remote-actions/devices-wipe.md#retire).

Un certificado PKCS se elimina cuando:
- Un perfil de certificado se quita de la asignación de grupo.

Un certificado raíz se elimina cuando:
- Un usuario anula su inscripción.
- Un administrador ejecuta la acción de [borrar](../remote-actions/devices-wipe.md#wipe).
- Un administrador ejecuta la acción de [retirar](../remote-actions/devices-wipe.md#retire).

Los certificados PKCS *permanecen* en el dispositivo (es decir, no se revocan ni se quitan) cuando:
- Un usuario pierde la licencia de Intune.
- Un administrador retira la licencia de Intune.
- Un administrador elimina el usuario o el grupo de Azure AD.
- Un administrador cambia o actualiza el perfil PKCS.

## <a name="android-knox-devices"></a>Dispositivos Android KNOX

### <a name="scep-certificates"></a>Certificados SCEP

Un certificado SCEP se revoca *y* se elimina cuando:
- Un usuario anula su inscripción.
- Un administrador ejecuta la acción de [borrar](../remote-actions/devices-wipe.md#wipe).

Un certificado SCEP se revoca cuando:
- Un administrador ejecuta la acción de [retirar](../remote-actions/devices-wipe.md#retire).
- El dispositivo se quita de un grupo de Azure AD.
- Un perfil de certificado se quita de la asignación de grupo.
- Un administrador elimina el usuario o el grupo de Azure AD.
- Un administrador cambia o actualiza el perfil SCEP.

Un certificado raíz se elimina cuando:
- Un usuario anula su inscripción.
- Un administrador ejecuta la acción de [borrar](../remote-actions/devices-wipe.md#wipe).
- Un administrador ejecuta la acción de [retirar](../remote-actions/devices-wipe.md#retire).

Los certificados SCEP *permanecen* en el dispositivo (es decir, no se revocan ni se quitan) cuando:
- Un usuario pierde la licencia de Intune.
- Un administrador retira la licencia de Intune.
- Un administrador elimina el usuario o el grupo de Azure AD.

### <a name="pkcs-certificates"></a>Certificados PKCS

Un certificado PKCS se revoca *y* se elimina cuando:

- Un usuario anula su inscripción.
- Un administrador ejecuta la acción de [borrar](../remote-actions/devices-wipe.md#wipe).
- Un administrador ejecuta la acción de [retirar](../remote-actions/devices-wipe.md#retire).

Un certificado raíz se elimina cuando:
- Un usuario anula su inscripción.
- Un administrador ejecuta la acción de [borrar](../remote-actions/devices-wipe.md#wipe).
- Un administrador ejecuta la acción de [retirar](../remote-actions/devices-wipe.md#retire).

Los certificados PKCS *permanecen* en el dispositivo (es decir, no se revocan ni se quitan) cuando:
- Un usuario pierde la licencia de Intune.
- Un administrador retira la licencia de Intune.
- Un administrador elimina el usuario o el grupo de Azure AD.
- Un administrador cambia o actualiza el perfil PKCS.
- Un perfil de certificado se quita de la asignación de grupo.


> [!NOTE]
> Los dispositivos Android for Work no están validados para los escenarios anteriores.
> Los dispositivos antiguos de Android (todos los dispositivos de perfiles que no sean de trabajo ni de Samsung) no están habilitados para la eliminación de certificados.

## <a name="macos-certificates"></a>Certificados macOS

### <a name="scep-certificates"></a>Certificados SCEP

Un certificado SCEP se revoca *y* se elimina cuando:
- Un usuario anula su inscripción.
- Un administrador ejecuta una acción de [retirar](../remote-actions/devices-wipe.md#retire).
- El dispositivo se quita de un grupo de Azure AD.
- Un perfil de certificado se quita de la asignación de grupo.

Un certificado SCEP se revoca cuando:
- Un administrador cambia o actualiza el perfil SCEP.

Los certificados SCEP *permanecen* en el dispositivo (es decir, no se revocan ni se quitan) cuando:
- Un usuario pierde la licencia de Intune.
- Un administrador retira la licencia de Intune.
- Un administrador elimina el usuario o el grupo de Azure AD.

> [!NOTE]
> No se admite el uso de la acción de [borrar](../remote-actions/devices-wipe.md#wipe) para el restablecimiento de fábrica de dispositivos macOS.

### <a name="pkcs-certificates"></a>Certificados PKCS

No se admiten certificados PKCS en macOS.

