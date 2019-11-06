---
title: Aplicaciones iOS con directivas de protección de aplicaciones
description: En este tema se describe qué esperar cuando la aplicación iOS está administrada por directivas de protección de aplicaciones.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: a1a3dcd7068a004f94b97b5ec6c43c609662a76d
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73414573"
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>Qué esperar cuando la aplicación iOS se administra con directivas de protección de aplicaciones

 En este tema se describe la experiencia del usuario cuando se usan aplicaciones con directivas de protección de aplicaciones aplicadas. Las directivas de protección de aplicaciones solo se aplican cuando se usan aplicaciones en el contexto laboral: por ejemplo, cuando el usuario obtiene acceso a las aplicaciones con la cuenta profesional o a archivos que están almacenados en la ubicación de OneDrive para la Empresa.

## <a name="access-apps"></a>Acceso a las aplicaciones

Si el dispositivo **no está inscrito en Intune**, al usuario final se le pide que reinicie la aplicación cuando la use por primera vez. Se requiere un reinicio para poder aplicar directivas de protección de aplicaciones a la aplicación.

<!--- The following screenshot from the Skype app illustrates this restart request: --->

<!---  ![Screenshot of the iOS device showing PIN prompt](./media/end-user-mam-apps-ios/iOS_AppPINPrompt.png) --->

En los dispositivos que **están inscritos para la administración en Intune**, el usuario ve un mensaje que indica que la aplicación ahora está administrada.

## <a name="use-apps-with-multi-identity-support"></a>Uso de aplicaciones con compatibilidad con varias identidades

Las aplicaciones que admiten varias identidades permiten usar diferentes cuentas (profesionales y personales) para obtener acceso a las mismas aplicaciones, aunque las directivas de protección de aplicaciones se aplican solo cuando las aplicaciones se usen en el contexto laboral.  

Por ejemplo, el usuario obtiene una solicitud de PIN al obtener acceso a los datos de trabajo. En la **aplicación Outlook**, al usuario se le pide un PIN al iniciar la aplicación. En la **aplicación OneDrive**, al usuario se le pide un PIN cuando escribe la cuenta profesional.  En Microsoft **Word**, **PowerPoint** y **Excel**, al usuario se le pide un PIN cuando obtiene acceso a documentos que se encuentran almacenados en la ubicación OneDrive para la Empresa.

- Obtenga más información sobre las aplicaciones que admiten [protección de aplicaciones y varias identidades](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) con Intune.

Las directivas de protección de aplicaciones solo se aplican en el contexto laboral. Por lo tanto, la aplicación podría comportarse de manera distinta si el contexto es laboral o personal.

## <a name="manage-user-accounts-on-the-device"></a>Administración de cuentas de usuario en el dispositivo

Las aplicaciones de varias identidades permiten a los usuarios agregar varias cuentas.  Intune App solo admite una cuenta administrada.  Intune App no limita el número de cuentas no administradas.

Cuando hay una cuenta administrada en una aplicación:

- Si un usuario intenta agregar una segunda cuenta administrada, se le pide que seleccione cuál quiere usar.  La otra cuenta se quita.
- Si el administrador de TI agrega una directiva a una segunda cuenta existente, se pide al usuario que seleccione qué cuenta administrada quiere usar.  La otra cuenta se quita.

Consulte el siguiente escenario de ejemplo para profundizar aún más en cómo se tratan varias cuentas de usuario.

El usuario A trabaja para dos empresas: la **empresa X** y la **empresa Y**. El usuario A tiene una cuenta profesional para cada empresa y en ambas se usa Intune para implementar directivas de protección de aplicaciones. La **Compañía X** implementa directivas de protección de aplicaciones **antes que** la **Compañía Y**. La cuenta que está asociada a la **empresa X** obtiene la directiva de protección de aplicaciones en primer lugar. Si quiere que la cuenta de usuario asociada a la empresa Y se administre mediante las directivas de protección de aplicaciones, deberá quitar la cuenta de usuario asociada a la empresa X y agregar la cuenta de usuario que esté asociada a la empresa Y.

### <a name="add-a-second-account"></a>Incorporación de una segunda cuenta

Si usa un dispositivo iOS, puede que aparezca un mensaje de bloqueo si intenta agregar una segunda cuenta profesional en ese dispositivo. Se muestran las cuentas y, luego, puede elegir la que quiera quitar.

## <a name="next-steps"></a>Pasos siguientes

[What to expect when your Android app is managed by app protection policies](end-user-mam-apps-android.md) (Qué esperar cuando la aplicación Android se administra con directivas de protección de aplicaciones)
