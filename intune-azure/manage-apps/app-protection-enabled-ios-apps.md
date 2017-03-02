---
title: "Aplicaciones iOS con directivas de protección de aplicaciones | Versión preliminar de Intune Azure"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: este tema describe qué esperar cuando la aplicación iOS está administrada por directivas de protección de aplicaciones."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 586d9440-3813-4dec-b865-8bd319befde0
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 5a4ce6d6248378ba48cddeaefb941c139dd990f6
ms.lasthandoff: 02/18/2017


---

# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>Qué esperar cuando la aplicación iOS se administra con directivas de protección de aplicaciones
[!INCLUDE[azure_preview](../includes/azure_preview.md)]En este tema se describe la experiencia del usuario en aplicaciones con directivas de protección de aplicaciones. Las directivas de protección de aplicaciones solo se aplican cuando se usan aplicaciones en el contexto profesional: por ejemplo, cuando se accede a aplicaciones con la cuenta profesional o cuando se accede a los archivos almacenados en la ubicación empresarial de OneDrive.
##  <a name="accessing-apps"></a>Acceso a aplicaciones

Si el dispositivo **no está inscrito en Intune**, al usuario final se le pedirá que reinicie la aplicación cuando la use por primera vez.  Se requiere un reinicio para poder aplicar directivas de protección de aplicaciones a la aplicación. En la captura de pantalla siguiente se puede ver esto con la aplicación Skype:


![captura de pantalla del dispositivo iOS con la solicitud de PIN](../media/ios-pin-prompt.png)

En los dispositivos que **están inscritos para la administración en Intune**, el usuario final verá un mensaje que indica que la aplicación ahora está administrada:

![captura de pantalla del dispositivo iOS con el mensaje de administración por parte de la empresa con la solicitud de PIN](../media/ios-managed-devices-pin-prompt.png)

##  <a name="using-apps-with-multi-identity-support"></a>Uso de aplicaciones con compatibilidad con varias identidades

Las directivas de protección de aplicaciones solo se aplican en el contexto profesional cuando se usa la aplicación, por lo que es posible que observe distintos comportamientos de las aplicaciones según el contexto: profesional o personal.  

En las aplicaciones que admiten varias identidades, Intune solo aplica las directivas de protección de aplicaciones cuando el usuario final está usando la aplicación en el contexto laboral.  Por ejemplo, el usuario final verá una solicitud de PIN al acceder a los datos de trabajo.  En la **aplicación Outlook**, al usuario final se le pide un PIN al iniciar la aplicación. En la **aplicación OneDrive**, esto ocurre cuando el usuario final escribe en la cuenta de trabajo.  En Microsoft **Word**, **PowerPoint* y **Excel**, esto ocurre cuando el usuario final accede a documentos almacenados en la ubicación de OneDrive para la empresa.
##  <a name="managing-user-accounts-on-the-device"></a>Administración de cuentas de usuario en el dispositivo

En Intune solo se pueden implementar directivas de protección de aplicaciones en una única cuenta de usuario por dispositivo.

* Dependiendo de la aplicación que use, el segundo usuario puede o no estar bloqueado en el dispositivo. Sin embargo, en todos los casos, solo el primer usuario que obtenga las directivas de protección de aplicaciones se verá afectado por la directiva.
  * **Microsoft Word**, **Excel** y **PowerPoint** no bloquean una segunda cuenta de usuario, pero esa segunda cuenta no se verá afectada por las directivas de protección de aplicaciones.  

  * En **aplicaciones de OneDrive y Outlook**, solo se puede usar una cuenta profesional.  La adición de varias cuentas profesionales está bloqueada en estas aplicaciones.  Sin embargo, puede quitar un usuario y agregar un usuario diferente en el dispositivo.

* Si un dispositivo tiene varias cuentas de usuario existentes antes de implementar las directivas de protección de aplicaciones, solo la cuenta en la que estas directivas se implementan primero se administra mediante directivas de protección de aplicaciones de Intune.


Consulte el siguiente escenario de ejemplo para ahondar aún más en cómo se tratan varias cuentas de usuario.

El usuario A trabaja para dos empresas: la **empresa X** y la **empresa Y**. El usuario A tiene una cuenta profesional para cada empresa y en ambas se usa Intune para implementar directivas de protección de aplicaciones. La **Compañía X** implementa directivas de protección de aplicaciones **antes que** la **Compañía Y**. La cuenta asociada a la **Compañía X** obtendrá la directiva de protección de aplicaciones, pero no la cuenta asociada a la Compañía Y. Si quiere que la cuenta de usuario asociada a la Compañía Y se administre por medio de directivas de protección de aplicaciones, deberá quitar la cuenta de usuario asociada a la Compañía X.
### <a name="adding-a-second-account"></a>Agregar una segunda cuenta

Si usa un dispositivo iOS, puede que aparezca un mensaje de bloqueo si intenta agregar una segunda cuenta profesional en el mismo dispositivo.  Se mostrarán las cuentas y podrá elegir la que quiere quitar.

![Captura de pantalla del cuadro de diálogo con el mensaje de bloqueo y las opciones Sí y No](../media/ios-switch-user.PNG)

## <a name="next-steps"></a>Pasos siguientes
[What to expect when your Android app is managed by app protection policies](app-protection-enabled-android-apps.md) (Qué esperar cuando la aplicación Android se administra con directivas de protección de aplicaciones)
### <a name="see-also"></a>Consulte también
[Creación e implementación de directivas de protección de aplicaciones con Microsoft Intune](app-protection-policies.md)

