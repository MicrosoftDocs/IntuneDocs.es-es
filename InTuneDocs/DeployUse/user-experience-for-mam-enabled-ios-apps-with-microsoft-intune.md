---
title: Aplicaciones iOS con directivas MAM | Microsoft Intune
description: "En este tema se describe qué esperar cuando la aplicación iOS está administrada por directivas de administración de aplicaciones móviles."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 10/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 389daf0ed39fa2cd4b2e5d6e52cbd6809a568c9e
ms.openlocfilehash: 3f9d9c7cafcdac0db21e5ba35f713fe630c65b99


---

# Qué esperar cuando la aplicación iOS está administrada por directivas MAM
 En este tema se describe la experiencia del usuario en aplicaciones con directivas MAM. Las directivas de administración de aplicaciones móviles (MAM) solo se aplican cuando se usan aplicaciones en el contexto laboral: por ejemplo, al acceder a aplicaciones con la cuenta profesional o a archivos almacenados en la ubicación empresarial de OneDrive.
##  Acceso a aplicaciones

Si el dispositivo **no está inscrito en Intune**, al usuario final se le pedirá que reinicie la aplicación cuando la use por primera vez.  Se exige un reinicio para poder aplicar las directivas MAM a la aplicación. En la captura de pantalla siguiente se puede ver esto con la aplicación Skype:


![captura de pantalla del dispositivo iOS con la solicitud de PIN](../media/appmanagement/iOS_AppPINPrompt.png)

En los dispositivos que **están inscritos para la administración en Intune**, el usuario final verá un mensaje que indica que la aplicación ahora está administrada:

![captura de pantalla del dispositivo iOS con el mensaje de administración por parte de la empresa con la solicitud de PIN](../media/appmanagement/ios-managed-devices-pin-prompt.png)

##  Uso de aplicaciones con compatibilidad con varias identidades

Las directivas MAM solo se aplican en el contexto laboral cuando se usa la aplicación, por lo que es posible que observe distintos comportamientos según el contexto: laboral o personal.  

En las aplicaciones que admiten varias identidades, Intune solo aplica las directivas MAM cuando el usuario final está usando la aplicación en el contexto laboral.  Por ejemplo, el usuario final verá una solicitud de PIN al acceder a los datos de trabajo.  En la **aplicación Outlook**, al usuario final se le pide un PIN al iniciar la aplicación. En la **aplicación OneDrive**, esto ocurre cuando el usuario final escribe en la cuenta de trabajo.  En Microsoft **Word**, **PowerPoint* y **Excel**, esto ocurre cuando el usuario final accede a documentos almacenados en la ubicación de OneDrive para la empresa.
##  Administración de cuentas de usuario en el dispositivo

En Intune solo se pueden implementar directivas de MAM en una única cuenta de usuario por dispositivo.

* Dependiendo de la aplicación que use, el segundo usuario puede o no estar bloqueado en el dispositivo. Pero, en todos los casos, solo el primer usuario que obtiene las directivas de MAM se verá afectado por la directiva.
  * **Microsoft Word**, **Excel** y **PowerPoint** no bloquean una segunda cuenta de usuario, pero esa segunda cuenta no se verá afectada por las directivas de MAM.  

  * En **aplicaciones de OneDrive y Outlook**, solo se puede usar una cuenta profesional.  La adición de varias cuentas profesionales está bloqueada en estas aplicaciones.  Sin embargo, puede quitar un usuario y agregar un usuario diferente en el dispositivo.

* Si un dispositivo tiene varias cuentas de usuario existentes antes de implementar las directivas de MAM, estas directivas de MAM de Intune solo administrarán la primera cuenta en las que se implementen.


Consulte el siguiente escenario de ejemplo para ahondar aún más en cómo se tratan varias cuentas de usuario.

El usuario A trabaja para dos empresas: la **empresa X** y la **empresa Y**. El usuario A tiene una cuenta profesional en cada empresa y en ambas se usa Intune para implementar directivas de MAM. La **empresa X** implementa directivas de MAM **antes** que la **empresa Y**. La cuenta asociada a la **empresa X** obtendrá la directiva de MAM, pero no la cuenta asociada a la empresa Y. Si quiere que la cuenta de usuario asociada a la empresa Y se administre por medio de las directivas de MAM, deberá quitar la cuenta de usuario asociada a la empresa X.
### Agregar una segunda cuenta

Si usa un dispositivo iOS, puede que aparezca un mensaje de bloqueo si intenta agregar una segunda cuenta profesional en el mismo dispositivo.  Se mostrarán las cuentas y podrá elegir la que quiere quitar.

![Captura de pantalla del cuadro de diálogo con el mensaje de bloqueo y las opciones Sí y No](../media/AppManagement/iOS_SwitchUser.PNG)
## Pasos siguientes
[Qué esperar cuando la aplicación Android está administrada por directivas MAM](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
### Consulte también
[Crear e implementar directivas de administración de aplicaciones móviles con Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Oct16_HO3-->


