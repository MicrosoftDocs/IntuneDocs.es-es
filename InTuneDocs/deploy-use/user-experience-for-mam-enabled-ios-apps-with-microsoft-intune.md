---
title: Aplicaciones iOS con directivas MAM | Microsoft Intune
description: "En este tema se describe qué esperar cuando la aplicación iOS está administrada por directivas de administración de aplicaciones móviles."
keywords: 
author: NathBarn
ms.author: nathbarn
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
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: 3aa6728036ff66ea489176063af2d136bef4c7cc


---

# <a name="what-to-expect-when-your-ios-app-is-managed-by-mam-policies"></a>What to expect when your iOS app is managed by MAM policies (Qué esperar cuando la aplicación iOS está administrada por directivas de MAM)
 En este tema se describe la experiencia del usuario en aplicaciones con directivas de administración de acceso a aplicaciones móviles (MAM). Las directivas de MAM solo se aplican cuando se usan aplicaciones en el contexto laboral: por ejemplo, cuando el usuario obtiene acceso a las aplicaciones con la cuenta profesional o a archivos que están almacenados en la ubicación empresarial de OneDrive.

##  <a name="access-apps"></a>Acceso a las aplicaciones

Si el dispositivo **no está inscrito en Intune**, al usuario final se le pide que reinicie la aplicación cuando la use por primera vez.  Se exige un reinicio para poder aplicar las directivas MAM a la aplicación. En la captura de pantalla siguiente de la aplicación de Skype se muestra esta solicitud de reinicio:


![Captura de pantalla del dispositivo iOS con la solicitud de PIN](../media/appmanagement/iOS_AppPINPrompt.png)

En los dispositivos que **están inscritos para la administración en Intune**, el usuario ve un mensaje que indica que la aplicación ahora está administrada:

![Captura de pantalla del dispositivo iOS con el mensaje que indica que la aplicación ahora la administra la empresa, con la solicitud de PIN](../media/appmanagement/ios-managed-devices-pin-prompt.png)

##  <a name="use-apps-with-multi-identity-support"></a>Uso de aplicaciones con compatibilidad con varias identidades

Las directivas de MAM solo se aplican en el contexto laboral. Por lo tanto, la aplicación podría comportarse de manera distinta si el contexto es laboral o personal.

 Por ejemplo, el usuario obtiene una solicitud de PIN al obtener acceso a los datos de trabajo. En la **aplicación Outlook**, al usuario se le pide un PIN al iniciar la aplicación. En la **aplicación OneDrive**, al usuario se le pide un PIN cuando escribe la cuenta profesional.  En Microsoft **Word**, **PowerPoint** y **Excel**, al usuario se le pide un PIN cuando obtiene acceso a documentos que se encuentran almacenados en la ubicación OneDrive para la Empresa.

##  <a name="manage-user-accounts-on-the-device"></a>Administración de cuentas de usuario en el dispositivo

Intune solo admite la implementación de directivas de MAM en una cuenta de usuario por dispositivo.

* Dependiendo de la aplicación que use, el segundo usuario puede estar bloqueado en el dispositivo. Pero, en todos los casos, solo el primer usuario que obtiene las directivas de MAM se verá afectado por la directiva.
  * **Microsoft Word**, **Excel** y **PowerPoint** no bloquean una segunda cuenta de usuario, pero esa segunda cuenta no se verá afectada por las directivas de MAM.  

  * En **aplicaciones de Outlook** y **OneDrive**, solo se puede usar una cuenta profesional. No puede agregar varias cuentas profesionales para estas aplicaciones. Sin embargo, puede quitar un usuario y agregar un usuario diferente en el dispositivo.

* Si un dispositivo tiene varias cuentas de usuario existentes antes de implementar las directivas de MAM, estas directivas de MAM de Intune solo administrarán la primera cuenta en las que se implementen.


Consulte el siguiente escenario de ejemplo para profundizar aún más en cómo se tratan varias cuentas de usuario.

El usuario A trabaja para dos empresas: la **empresa X** y la **empresa Y**. El usuario A tiene una cuenta profesional en cada empresa y en ambas se usa Intune para implementar directivas de MAM. La **empresa X** implementa directivas de MAM **antes** que la **empresa Y**. La cuenta que está asociada a la **empresa X** obtiene la directiva de MAM, pero no la cuenta asociada a la empresa Y. Si quiere que la cuenta de usuario asociada a la empresa Y se administre por medio de las directivas de MAM, deberá quitar la cuenta de usuario asociada a la empresa X.

### <a name="add-a-second-account"></a>Incorporación de una segunda cuenta

Si usa un dispositivo iOS, puede que aparezca un mensaje de bloqueo si intenta agregar una segunda cuenta profesional en ese dispositivo. Se mostrarán las cuentas y, luego, podrá elegir la que desea quitar.

![Captura de pantalla del cuadro de diálogo con el mensaje de bloqueo y las opciones Sí y No](../media/AppManagement/iOS_SwitchUser.PNG)
## <a name="next-steps"></a>Pasos siguientes
[Qué esperar cuando la aplicación Android está administrada por directivas MAM](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
### <a name="see-also"></a>Consulte también
[Crear e implementar directivas de administración de aplicaciones móviles con Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


