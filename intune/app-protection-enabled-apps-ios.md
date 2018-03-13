---
title: "Aplicaciones iOS con directivas de protección de aplicaciones"
titlesuffix: Microsoft Intune
description: "Obtenga información sobre las aplicaciones para iOS con políticas de protección."
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 586d9440-3813-4dec-b865-8bd319befde0
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 13833d41603e24e4471f0bb5fdda40d000f29a34
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2018
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>Qué esperar cuando la aplicación iOS se administra con directivas de protección de aplicaciones

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Obtenga información sobre la experiencia del usuario para las aplicaciones de iOS con directivas de protección de aplicaciones. Las directivas de protección de aplicaciones solo se aplican cuando se usan aplicaciones en el ámbito profesional. Por ejemplo, al acceder a una aplicación con una cuenta profesional o a archivos almacenados en la ubicación de OneDrive de su empresa.
##  <a name="accessing-apps"></a>Acceso a aplicaciones

Si el dispositivo **no está inscrito en Intune**, al usuario se le pedirá que reinicie la aplicación cuando la use por primera vez.  Se requiere un reinicio para poder aplicar directivas de protección de aplicaciones a la aplicación. En la captura de pantalla siguiente se puede ver esto con la aplicación Skype:


![captura de pantalla del dispositivo iOS con la solicitud de PIN](./media/ios-pin-prompt.png)

En cambio, en los dispositivos que **están inscritos para la administración en Intune**, el usuario verá un mensaje que indica que la aplicación ahora está administrada:

![captura de pantalla del dispositivo iOS con el mensaje de administración por parte de la empresa con la solicitud de PIN](./media/ios-managed-devices-pin-prompt.png)

##  <a name="using-apps-with-multi-identity-support"></a>Uso de aplicaciones con compatibilidad con varias identidades

Las directivas de protección de aplicaciones solo se aplicarán cuando un usuario intente acceder a datos relacionados con la empresa.  Si el usuario accede a la aplicación para su uso personal, puede que observe distintos comportamientos. 

Para las aplicaciones que admiten varias identidades, Intune solo aplica las directivas de protección de aplicaciones si un usuario accede a datos relacionados con la empresa.  Por ejemplo, puede que un usuario reciba una solicitud de PIN.  En la **aplicación Outlook**, se genera una solicitud cuando un usuario inicia la aplicación. En la **aplicación OneDrive**, se genera una solicitud cuando un usuario escribe su cuenta profesional.  En Microsoft **Word**, **PowerPoint** y **Excel**, se genera una solicitud cuando un usuario accede a documentos de la empresa en OneDrive.
##  <a name="managing-user-accounts-on-the-device"></a>Administración de cuentas de usuario en el dispositivo

En Intune solo se pueden implementar directivas de protección de aplicaciones en una única cuenta de usuario por dispositivo.

* Dependiendo de la aplicación que use, el segundo usuario puede o no estar bloqueado en el dispositivo. Sin embargo, en todos los casos, la directiva solo se aplica al primer usuario que obtenga las directivas de protección de aplicaciones.
  * **Microsoft Word**, **Excel** y **PowerPoint** no bloquearán el acceso a cuentas de usuario adicionales. No obstante, las directivas de protección de aplicaciones no se aplicarán a la cuenta de usuario.

  * En **aplicaciones de OneDrive y Outlook**, solo se puede usar una cuenta profesional.  La adición de varias cuentas profesionales está bloqueada en estas aplicaciones.  Sin embargo, puede quitar a un usuario de un dispositivo y agregar otro usuario a este.

* Un dispositivo puede tener varias cuentas de usuario existentes antes de implementar las directivas de protección de aplicaciones. En este caso, las directivas de protección de aplicaciones de Intune administrarán la primera cuenta en la que se hayan aplicado las directivas de protección de aplicaciones.


Lea el siguiente escenario de ejemplo para obtener información sobre cómo Intune gestiona varias cuentas de usuario.

El usuario A trabaja para dos empresas: la **empresa X** y la **empresa Y**. El usuario A tiene una cuenta profesional para cada empresa y en ambas se usa Intune para implementar directivas de protección de aplicaciones. La **Compañía X** implementa directivas de protección de aplicaciones **antes que** la **Compañía Y**. La cuenta asociada a la **empresa X** obtendrá la directiva de protección de aplicaciones, pero la cuenta asociada a la empresa Y no lo hará. Si quiere que la cuenta de usuario de la empresa Y se administre mediante las directivas de protección de aplicaciones, deberá quitar la cuenta de usuario de la empresa X.
### <a name="adding-a-second-account"></a>Agregar una segunda cuenta

Si usa un dispositivo iOS, puede que aparezca un mensaje de bloqueo si intenta agregar una segunda cuenta profesional en el mismo dispositivo.  Se mostrarán las cuentas y podrá elegir la que quiere quitar.

![Captura de pantalla del cuadro de diálogo con el mensaje de bloqueo y las opciones Sí y No](./media/ios-switch-user.PNG)

## <a name="next-steps"></a>Pasos siguientes
[What to expect when your Android app is managed by app protection policies](app-protection-enabled-apps-android.md) (Qué esperar cuando la aplicación Android se administra con directivas de protección de aplicaciones)
### <a name="see-also"></a>Vea también
[Creación e implementación de directivas de protección de aplicaciones con Microsoft Intune](app-protection-policies.md)
