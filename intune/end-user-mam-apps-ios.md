---
title: "Aplicaciones iOS con directivas de protección de aplicaciones"
description: "En este tema se describe qué esperar cuando la aplicación iOS está administrada por directivas de protección de aplicaciones."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 05/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e66042e5198b76ec484fe0218127acb653394cce
ms.sourcegitcommit: f100c943a635f5a08254ba7cf30f1aaebb7e810e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2017
---
# Qué esperar cuando la aplicación iOS se administra con directivas de protección de aplicaciones
<a id="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies" class="xliff"></a>

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

 En este tema se describe la experiencia del usuario cuando se usan aplicaciones con directivas de protección de aplicaciones aplicadas. Las directivas de protección de aplicaciones solo se aplican cuando se usan aplicaciones en el contexto laboral: por ejemplo, cuando el usuario obtiene acceso a las aplicaciones con la cuenta profesional o a archivos que están almacenados en la ubicación de OneDrive para la Empresa.

##  Acceso a las aplicaciones
<a id="access-apps" class="xliff"></a>

Si el dispositivo **no está inscrito en Intune**, al usuario final se le pide que reinicie la aplicación cuando la use por primera vez. Se requiere un reinicio para poder aplicar directivas de protección de aplicaciones a la aplicación.

<!--- The following screenshot from the Skype app illustrates this restart request: --->


<!---  ![Screenshot of the iOS device showing PIN prompt](../media/appmanagement/iOS_AppPINPrompt.png) --->

En los dispositivos que **están inscritos para la administración en Intune**, el usuario ve un mensaje que indica que la aplicación ahora está administrada.

##  Uso de aplicaciones con compatibilidad con varias identidades
<a id="use-apps-with-multi-identity-support" class="xliff"></a>

Las aplicaciones que admiten varias identidades permiten usar diferentes cuentas (profesionales y personales) para obtener acceso a las mismas aplicaciones, aunque las directivas de protección de aplicaciones se aplican solo cuando las aplicaciones se usen en el contexto laboral.  

Por ejemplo, el usuario obtiene una solicitud de PIN al obtener acceso a los datos de trabajo. En la **aplicación Outlook**, al usuario se le pide un PIN al iniciar la aplicación. En la **aplicación OneDrive**, al usuario se le pide un PIN cuando escribe la cuenta profesional.  En Microsoft **Word**, **PowerPoint** y **Excel**, al usuario se le pide un PIN cuando obtiene acceso a documentos que se encuentran almacenados en la ubicación OneDrive para la Empresa.

- Obtenga más información sobre las aplicaciones que admiten [MAM y varias identidades](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) con Intune.

Las directivas de protección de aplicaciones solo se aplican en el contexto laboral. Por lo tanto, la aplicación podría comportarse de manera distinta si el contexto es laboral o personal.

##  Administración de cuentas de usuario en el dispositivo
<a id="manage-user-accounts-on-the-device" class="xliff"></a>

Intune solo admite la implementación de directivas de protección de aplicaciones en una cuenta de usuario por dispositivo.

* Dependiendo de la aplicación que use, el segundo usuario puede estar bloqueado en el dispositivo. Sin embargo, en todos los casos, solo el primer usuario que obtenga las directivas de protección de aplicaciones se verá afectado por la directiva.
  * **Microsoft Word**, **Excel** y **PowerPoint** no bloquean una segunda cuenta de usuario, pero esa segunda cuenta no se verá afectada por las directivas de protección de aplicaciones.  

  * En **aplicaciones de Outlook** y **OneDrive**, solo se puede usar una cuenta profesional. No puede agregar varias cuentas profesionales para estas aplicaciones. Sin embargo, puede quitar un usuario y agregar un usuario diferente en el dispositivo.

* Si un dispositivo tiene varias cuentas de usuario existentes antes de implementar las directivas de protección de aplicaciones, solo la cuenta en la que estas directivas se implementan primero se administra mediante directivas de protección de aplicaciones de Intune.


Consulte el siguiente escenario de ejemplo para profundizar aún más en cómo se tratan varias cuentas de usuario.

El usuario A trabaja para dos empresas: la **empresa X** y la **empresa Y**. El usuario A tiene una cuenta profesional para cada empresa y en ambas se usa Intune para implementar directivas de protección de aplicaciones. La **Compañía X** implementa directivas de protección de aplicaciones **antes que** la **Compañía Y**. La cuenta que está asociada a la **empresa X** obtiene la directiva de protección de aplicaciones, pero no la cuenta asociada a la empresa Y. Si quiere que la cuenta de usuario asociada a la empresa Y se administre por medio de las directivas de protección de aplicaciones, deberá quitar la cuenta de usuario asociada a la empresa X.

### Incorporación de una segunda cuenta
<a id="add-a-second-account" class="xliff"></a>

Si usa un dispositivo iOS, puede que aparezca un mensaje de bloqueo si intenta agregar una segunda cuenta profesional en ese dispositivo. Se mostrarán las cuentas y, luego, podrá elegir la que desea quitar.

## Pasos siguientes
<a id="next-steps" class="xliff"></a>
[What to expect when your Android app is managed by app protection policies](end-user-mam-apps-android.md) (Qué esperar cuando la aplicación Android se administra con directivas de protección de aplicaciones)
