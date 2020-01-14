---
title: Aplicaciones iOS con directivas de protección de aplicaciones
description: En este tema se describe qué esperar cuando la aplicación iOS está administrada por directivas de protección de aplicaciones.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/18/2019
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
ms.openlocfilehash: 165ce160339647e396b9cfc3a8374f21c77665f8
ms.sourcegitcommit: f9dc50642efa8656054ef67f9335b9b46b655f93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2020
ms.locfileid: "75606628"
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>Qué esperar cuando la aplicación iOS se administra con directivas de protección de aplicaciones

Las directivas de protección de aplicaciones de Intune se aplican a las aplicaciones que se usan para el trabajo o la escuela. Esto significa que, cuando los empleados y los alumnos usan sus aplicaciones en un contexto personal, es posible que no noten ninguna diferencia en su experiencia. Sin embargo, en el contexto profesional o educativo, pueden recibir mensajes para tomar decisiones con respecto a la cuenta, actualizar su configuración o ponerse en contacto con usted para obtener ayuda. Use este artículo para obtener información sobre lo que experimentan los usuarios cuando intentan acceder a aplicaciones protegidas por Intune y usarlas.  

## <a name="access-apps"></a>Acceso a las aplicaciones

Si el dispositivo **no está inscrito en Intune**, al usuario final se le pide que reinicie la aplicación cuando la use por primera vez. Se requiere un reinicio para poder aplicar directivas de protección de aplicaciones a la aplicación.

<!--- The following screenshot from the Skype app illustrates this restart request: --->

<!---  ![Screenshot of the iOS device showing PIN prompt](./media/end-user-mam-apps-ios/iOS_AppPINPrompt.png) --->

En los dispositivos que **están inscritos para la administración en Intune**, el usuario ve un mensaje que indica que la aplicación ahora está administrada.

## <a name="use-apps-with-multi-identity-support"></a>Uso de aplicaciones con compatibilidad con varias identidades

Las aplicaciones que admiten varias identidades permiten usar diferentes cuentas de trabajo y personales para tener acceso a las mismas aplicaciones. Las directivas de protección de aplicaciones, como escribir un PIN de dispositivo, se activan cuando los usuarios acceden a estas aplicaciones en un contexto profesional o educativo.   

Los usuarios pueden experimentar la solicitud de PIN de manera diferente en todas sus aplicaciones, en función de cómo configure las directivas.  Por ejemplo, puede configurar las directivas para que:       
* Microsoft Outlook solicite al usuario un PIN cuando inicie la aplicación. 
* OneDrive solicite al usuario un PIN cuando inicie sesión en su cuenta profesional.  
* Microsoft Word, PowerPoint y Excel soliciten un PIN al usuario cuando acceda a documentos almacenados en la ubicación de OneDrive para la Empresa.  

- Obtenga más información sobre las aplicaciones que admiten [protección de aplicaciones y varias identidades](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) con Intune.  

## <a name="manage-user-accounts-on-the-device"></a>Administración de cuentas de usuario en el dispositivo  

Las directivas de protección de aplicaciones de Intune limitan a los usuarios a una cuenta profesional o educativa administrada por aplicación. Las directivas de protección de aplicaciones no limitan el número de cuentas no administradas que un usuario puede agregar.   

- Si un usuario intenta agregar una segunda cuenta administrada, se le pide que seleccione cuál quiere usar. Si el usuario agrega la segunda cuenta, se quita la primera.
- Si agrega directivas de protección a otra de las cuentas del usuario, se le pedirá al usuario que seleccione la cuenta administrada que se va a usar. La otra cuenta se quita. 

Algunos usuarios no tendrán la opción de cambiar o seleccionar entre cuentas administradas. La opción no está disponible en los dispositivos que:
* Administra Intune  
* Los administran soluciones de Enterprise Mobility Management y se configuran con el valor IntuneMAMUPN 

En el escenario de ejemplo siguiente se describe cómo se tratan varias cuentas de usuario:  

El usuario A trabaja para dos empresas: la **empresa X** y la **empresa Y**. El usuario A tiene una cuenta profesional para cada empresa y en ambas se usa Intune para implementar directivas de protección de aplicaciones. La **Empresa X** implementa directivas de protección de aplicaciones **antes que** la **Empresa Y**. La cuenta que está asociada a la **empresa X** obtiene la directiva de protección de aplicaciones en primer lugar. Si quiere que la cuenta de usuario asociada a la empresa Y se administre mediante las directivas de protección de aplicaciones, deberá quitar la cuenta de usuario asociada a la empresa X y agregar la cuenta de usuario que esté asociada a la empresa Y.  

## <a name="next-steps"></a>Pasos siguientes

[What to expect when your Android app is managed by app protection policies](end-user-mam-apps-android.md) (Qué esperar cuando la aplicación Android se administra con directivas de protección de aplicaciones)
