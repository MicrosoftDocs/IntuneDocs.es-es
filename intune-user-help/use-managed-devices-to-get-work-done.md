---
title: Usar dispositivos administrados para realizar el trabajo | Microsoft Docs
description: Entienda lo que conlleva inscribir el dispositivo en la administración con Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 523caa6b-d792-4bb6-bddb-24b2479932d8
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2f698f03ed3c7523ef1d768d2a1361d6d1a55008
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67883865"
---
# <a name="enroll-device-for-access-to-work-or-school-resources"></a>Inscripción del dispositivo para el acceso a recursos profesionales o educativos
Para inscribir el dispositivo y obtener acceso al correo electrónico y a las aplicaciones, debe instalar la aplicación Portal de empresa de Intune o Microsoft Intune aplicación. Al inscribirse, se aplican a su dispositivo las directivas de administración básicas que su organización ha configurado, como contraseña, PIN y cifrado. Una vez que la configuración del dispositivo cumple todos los requisitos de su organización, puede acceder de forma segura a la información del trabajo desde prácticamente cualquier lugar.  

Las aplicaciones Portal de empresa y Microsoft Intune mantienen la seguridad del dispositivo inscrito asegurándose de que la configuración del dispositivo coincide con las directivas de su organización. 

La aplicación Portal de empresa también puede hacer lo siguiente:  
* Mantiene la información personal y de trabajo independiente.  
* Facilita la búsqueda e instalación de aplicaciones profesionales y educativas relevantes.   

## <a name="get-the-apps"></a>Obtención de las aplicaciones
Para obtener el Portal de empresa, siga estos pasos:

- Instale la aplicación Portal de empresa desde la tienda de aplicaciones específica de la plataforma. En algunos casos, la organización instalará la aplicación Portal de empresa automáticamente.  
- Vaya al [sitio web de portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980) para acceder a la aplicación desde un explorador.  

Si se le pide que use la aplicación Microsoft Intune, su organización la instalará automáticamente.  


## <a name="what-information-can-my-company-see-when-i-enroll"></a>¿Qué información puede ver mi empresa cuando me inscribo?
Una vez inscrito el dispositivo, los usuarios de soporte técnico de su organización solo podrán ver la información pertinente para el trabajo. Es decir, no podrá ver su información personal. Si va a inscribir un dispositivo personal para usarlo en el trabajo, [Aprenda exactamente lo que puede y no se puede ver](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).  


## <a name="whats-the-difference-between-the-apps-and-the-website"></a>¿Cuál es la diferencia entre las aplicaciones y el sitio web?
La aplicación Portal de empresa está disponible para dispositivos Windows 10, iOS, macOS y Android. Se integra perfectamente con la plataforma respectiva del dispositivo. Se puede acceder a la versión del sitio web desde cualquier dispositivo y este le ofrece la misma experiencia universal sin importar el dispositivo que use. 

La aplicación Microsoft Intune es para dispositivos Android propiedad de la empresa.  

## <a name="what-kind-of-devices-can-you-enroll-with-company-portal"></a>¿Qué tipo de dispositivos puede inscribir con Portal de empresa?
- Dispositivos de Apple con iOS (como iPhone y iPad) y macOS (como MacBook y iMac)
- Dispositivos Android
- Dispositivos Windows
  - Windows 10 Mobile
  - Windows 10 Escritorio
  - Windows Phone 8,1
  - Windows 8.1

## <a name="what-kind-of-devices-can-you-enroll-with-the-microsoft-intune-app"></a>¿Qué tipo de dispositivos puede inscribir con la aplicación Microsoft Intune?  
Puede inscribir dispositivos Android propiedad de la empresa que la organización ha configurado para usar con la aplicación. La aplicación es compatible con Android 6,0 y versiones posteriores. 

## <a name="can-you-remove-a-computer-or-device-from-the-company-portal"></a>¿Se puede eliminar un equipo o dispositivo del Portal de empresa?
Sí, puede quitar o restablecer un equipo o un dispositivo del Portal de empresa. Hay una diferencia entre **quitar** y **restablecer**.

Al quitar un equipo o dispositivo del Portal de empresa, está anulando la inscripción de este en Intune. Tras anular una inscripción, dejará de tener acceso al Portal de empresa y es posible que se quiten del dispositivo algunos datos de la empresa. Para obtener información sobre cómo quitar el dispositivo del Portal de empresa, consulte los vínculos siguientes:  

- [Anular la inscripción del dispositivo Android](unenroll-your-device-from-intune-android.md)
- [Anular la inscripción del dispositivo iOS](unenroll-your-device-from-intune-ios.md)
- [Anular la inscripción del dispositivo macOS](unenroll-your-device-from-intune-macos.md)
- [Anular la inscripción del dispositivo Windows](unenroll-your-device-from-intune-windows.md)

Al restablecer un equipo o dispositivo, Portal de empresa intenta restablecer la configuración predeterminada de fábrica del equipo o dispositivo. Si restablece el dispositivo, se quitarán todos los datos personales y de empresa del dispositivo. Si ha perdido el dispositivo, lo puede restablecer también de forma remota desde el sitio web de Portal de empresa.  

Para obtener información sobre cómo restablecer el dispositivo, consulte [restablecer el dispositivo desde el sitio web de portal de empresa](reset-erase-your-device-cpwebsite.md).  

## <a name="can-you-remove-a-computer-or-device-from-the-microsoft-intune-app"></a>¿Se puede quitar un equipo o dispositivo de la aplicación Microsoft Intune?
No, no hay ninguna manera de quitar un dispositivo propiedad de la empresa de la aplicación Microsoft Intune.  

## <a name="what-if-i-cant-see-my-device-in-the-company-portal-or-microsoft-intune-app"></a>¿Qué ocurre si no puedo ver el dispositivo en la aplicación Portal de empresa o Microsoft Intune?
Para ver un dispositivo, primero debe agregarlo al Portal de empresa. Vaya a lo que le haya recomendado su administrador en el Portal de empresa y siga los pasos correspondientes a su dispositivo. Además, no podrá ver los dispositivos que posee y administra su empresa.

Si usa la aplicación Microsoft Intune, solo verá el dispositivo que está usando actualmente. Los demás dispositivos inscritos no serán visibles en la aplicación.  

## <a name="where-else-can-i-go-for-help"></a>¿Dónde más se puede obtener ayuda?  
Para solucionar problemas comunes y preguntas, consulte estos documentos específicos de la plataforma:  

- [Solucionar problemas habituales en el dispositivo Android](check-compliance-on-your-device-android.md)  
- [Solucionar problemas habituales en el dispositivo iOS](troubleshoot-your-device-ios.md)
- [Solucionar problemas habituales en el dispositivo macOS](troubleshoot-your-device-macos.md)
- [Solucionar problemas habituales en el dispositivo Windows](troubleshoot-your-device-windows.md)

También puede ponerse en contacto con el personal de soporte técnico. La aplicación Portal de empresa y Microsoft Intune ofrece páginas de ayuda y soporte técnico que muestran información de contacto y formas de notificar un problema. La información de contacto también está disponible en el [sitio web de portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980)de su organización.  

## <a name="next-steps"></a>Pasos siguientes  

Obtenga la ayuda a partir de la inscripción, que es específica de la plataforma del dispositivo:  

- [Uso del dispositivo Android](using-your-android-device-with-intune.md)
- [Uso de dispositivos iOS](using-your-ios-device-with-intune.md)
- [Uso de dispositivos macOS](using-your-macos-device-with-intune.md)
- [Uso del dispositivo Windows](using-your-windows-device-with-intune.md)
- [Uso del sitio web del portal de empresa](using-the-intune-company-portal-website.md)


