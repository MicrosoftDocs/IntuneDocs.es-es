---
title: "Aplicaciones iOS con directivas de protección de aplicaciones | Microsoft Docs"
description: "En este tema se describe qué esperar cuando la aplicación iOS está administrada por directivas de protección de aplicaciones."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 665d3347636d5ec0c698ffb93b768028c9d59ce3
ms.openlocfilehash: fba18027039a0e49c5301f9d1a16947e97408034
ms.lasthandoff: 03/07/2017


---

# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>Qué esperar cuando la aplicación iOS se administra con directivas de protección de aplicaciones

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

 En este tema se describe la experiencia del usuario en aplicaciones con directivas de protección de aplicaciones. Las directivas de protección de aplicaciones solo se aplican cuando se usan aplicaciones en el contexto laboral: por ejemplo, cuando el usuario obtiene acceso a las aplicaciones con la cuenta profesional o a archivos que están almacenados en la ubicación empresarial de OneDrive.

##  <a name="access-apps"></a>Acceso a las aplicaciones

Si el dispositivo **no está inscrito en Intune**, al usuario final se le pide que reinicie la aplicación cuando la use por primera vez.  Se requiere un reinicio para poder aplicar directivas de protección de aplicaciones a la aplicación. 

<!--- The following screenshot from the Skype app illustrates this restart request: --->


<!---  ![Screenshot of the iOS device showing PIN prompt](../media/appmanagement/iOS_AppPINPrompt.png) --->

En los dispositivos que **están inscritos para la administración en Intune**, el usuario ve un mensaje que indica que la aplicación ahora está administrada.

##  <a name="use-apps-with-multi-identity-support"></a>Uso de aplicaciones con compatibilidad con varias identidades

Las directivas de protección de aplicaciones solo se aplican en el contexto laboral. Por lo tanto, la aplicación podría comportarse de manera distinta si el contexto es laboral o personal.

 Por ejemplo, el usuario obtiene una solicitud de PIN al obtener acceso a los datos de trabajo. En la **aplicación Outlook**, al usuario se le pide un PIN al iniciar la aplicación. En la **aplicación OneDrive**, al usuario se le pide un PIN cuando escribe la cuenta profesional.  En Microsoft **Word**, **PowerPoint** y **Excel**, al usuario se le pide un PIN cuando obtiene acceso a documentos que se encuentran almacenados en la ubicación OneDrive para la Empresa.

##  <a name="manage-user-accounts-on-the-device"></a>Administración de cuentas de usuario en el dispositivo

Intune solo admite la implementación de directivas de protección de aplicaciones en una cuenta de usuario por dispositivo.

* Dependiendo de la aplicación que use, el segundo usuario puede estar bloqueado en el dispositivo. Sin embargo, en todos los casos, solo el primer usuario que obtenga las directivas de protección de aplicaciones se verá afectado por la directiva.
  * **Microsoft Word**, **Excel** y **PowerPoint** no bloquean una segunda cuenta de usuario, pero esa segunda cuenta no se verá afectada por las directivas de protección de aplicaciones.  

  * En **aplicaciones de Outlook** y **OneDrive**, solo se puede usar una cuenta profesional. No puede agregar varias cuentas profesionales para estas aplicaciones. Sin embargo, puede quitar un usuario y agregar un usuario diferente en el dispositivo.

* Si un dispositivo tiene varias cuentas de usuario existentes antes de implementar las directivas de protección de aplicaciones, solo la cuenta en la que estas directivas se implementan primero se administra mediante directivas de protección de aplicaciones de Intune.


Consulte el siguiente escenario de ejemplo para profundizar aún más en cómo se tratan varias cuentas de usuario.

El usuario A trabaja para dos empresas: la **empresa X** y la **empresa Y**. El usuario A tiene una cuenta profesional para cada empresa y en ambas se usa Intune para implementar directivas de protección de aplicaciones. La **Compañía X** implementa directivas de protección de aplicaciones **antes que** la **Compañía Y**. La cuenta que está asociada a la **empresa X** obtiene la directiva de protección de aplicaciones, pero no la cuenta asociada a la empresa Y. Si quiere que la cuenta de usuario asociada a la empresa Y se administre por medio de las directivas de protección de aplicaciones, deberá quitar la cuenta de usuario asociada a la empresa X.

### <a name="add-a-second-account"></a>Incorporación de una segunda cuenta

Si usa un dispositivo iOS, puede que aparezca un mensaje de bloqueo si intenta agregar una segunda cuenta profesional en ese dispositivo. Se mostrarán las cuentas y, luego, podrá elegir la que desea quitar.

## <a name="next-steps"></a>Pasos siguientes
[What to expect when your Android app is managed by app protection policies](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md) (Qué esperar cuando la aplicación Android se administra con directivas de protección de aplicaciones)
### <a name="see-also"></a>Consulte también
[Crear e implementar directivas de administración de aplicaciones móviles con Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)

