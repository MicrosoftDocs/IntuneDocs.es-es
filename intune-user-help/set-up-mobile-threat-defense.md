---
title: Instalación de Mobile Threat Defense en su dispositivo móvil
description: Aprenda a instalar Mobile Threat Defense en su dispositivo móvil.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/25/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7f395a9cedc72a8184cfe3e29d6fcd3117a1473d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72980363"
---
# <a name="install-mobile-threat-defense"></a>Instalación de Mobile Threat Defense   

Como parte de los requisitos de seguridad de su organización, es posible que deba instalar una aplicación de proveedor de Mobile Threat Defense (MTD). Este tipo de aplicación detecta y alerta sobre amenazas en el dispositivo, como aplicaciones sospechosas, redes o vulnerabilidades del sistema operativo.  

Si no tiene la aplicación MTD requerida, no podrá iniciar sesión en las aplicaciones protegidas con su cuenta profesional o educativa. En este artículo, aprenderá [a instalar una aplicación MTD](set-up-mobile-threat-defense.md#install-app) para desbloquearla.  

Hay una gran variedad de aplicaciones de proveedor de MTD disponibles para instalar. su organización le informará de cuál debe usar. 


## <a name="information-your-organization-can-see"></a>Información que su organización puede ver   

Su organización no puede ver ningún dato, como textos, correos electrónicos e imágenes, en sus aplicaciones personales. La aplicación MTD informa de la información sobre las aplicaciones, como el nombre y la versión, a su organización. La información real que se notifique dependerá del proveedor de MTD que use su empresa. Es posible que su organización vea lo siguiente:   

* Nombre de la aplicación  
* Id. de aplicación: el nombre único que identifica la aplicación en Google Play.  
* Versión de la aplicación y número abreviado de la versión: los números de la versión específica de una aplicación.  
* Grupo de aplicaciones y tamaño dinámico: la cantidad de espacio que usa una aplicación en el dispositivo. 


## <a name="install-app"></a>Instalar aplicación    
Al iniciar sesión en una aplicación protegida, se le pedirá automáticamente que instale una aplicación MTD. Siga los pasos en pantalla para completar la instalación. Siga los pasos de esta sección para obtener ayuda adicional.  
 
También es posible que se le pida que registre el dispositivo. El registro es necesario para confirmar su identidad y conectar su cuenta profesional o educativa al dispositivo. Si no está registrado, se le guiará automáticamente a través de ese programa de instalación antes de instalar la aplicación MTD. Cuando llegue a la pantalla **obtener acceso** , puede iniciar los pasos de instalación.  

Para obtener más información sobre el registro de dispositivos, consulte [registrar el dispositivo personal en la red de su organización](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network).  

### <a name="ios-setup"></a>configuración de iOS  

1. En la pantalla **obtener acceso** , siga las instrucciones para instalar la aplicación MTD requerida por su organización.   
2. Vuelva a la pantalla **obtener acceso** y seleccione **abrir**.  
3. La aplicación MTD solicita permiso para abrir Microsoft Authenticator. Seleccione **Abrir**. 
4. Seleccione su cuenta profesional para iniciar sesión. 
5. Espere mientras la aplicación MTD examina el dispositivo en busca de amenazas de seguridad. 
6. Vuelva a la aplicación educativa o de trabajo a la que estaba intentando acceder originalmente. En este punto, su organización podría pedirle que configure otros requisitos de seguridad de la aplicación, como la creación de un PIN.   
7. Ahora debería tener acceso a la aplicación. Si todavía está bloqueado:  
    * En la pantalla **obtener acceso, seleccione volver a** **comprobar**.  
    * Vaya a la aplicación MTD y compruebe si hay amenazas existentes. Complete los pasos recomendados para resolver la amenaza y recuperar el acceso.    

### <a name="android-setup"></a>Configuración de Android 

1. En la pantalla **obtener acceso** , siga las instrucciones para instalar la aplicación MTD requerida por su organización.  
2. Vuelva a la pantalla **obtener acceso** y seleccione **abrir**.  
3. La aplicación MTD solicita permiso para tener acceso a determinadas áreas del dispositivo, en caso de que sea necesario. Para que esta aplicación funcione correctamente, debe **permitir** el acceso a los contactos. Los permisos solicitados variarán en los proveedores de MTD.  
4. Seleccione su cuenta profesional para iniciar sesión.  
5. Espere mientras la aplicación MTD examina el dispositivo en busca de amenazas de seguridad.  
6. Vuelva a la aplicación educativa o de trabajo a la que estaba intentando acceder originalmente. En este punto, su organización podría pedirle que configure otros requisitos de seguridad de la aplicación, como la creación de un PIN.  
7. Ahora debería tener acceso a la aplicación. Si todavía está bloqueado:  
    * En la pantalla **obtener acceso, seleccione volver a** **comprobar**.  
    * Vaya a la aplicación MTD y compruebe si hay amenazas existentes. Complete los pasos recomendados para resolver la amenaza y recuperar el acceso.  

### <a name="installation-failed"></a>Error de instalación  

Si se produce un error en la instalación, póngase en contacto con el personal de soporte de ti. Vaya al [sitio web Portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980) para buscar la información de contacto de su empresa.  

También puede enviar los registros de la aplicación al personal de soporte técnico de TI para proporcionarles más contexto sobre la instalación.  
* Usuarios de Android: [cargue y envíe por correo electrónico sus registros](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android) desde portal de empresa.   

* usuarios de dispositivos iOS: [recupere y envíe los registros](https://docs.microsoft.com/intune/apps/manage-microsoft-edge#use-microsoft-edge-on-ios-to-access-managed-app-logs) de Microsoft Edge para iOS.  

## <a name="resolve-a-threat"></a>Resolución de amenazas  
Si una amenaza supera el nivel de amenaza definido de la organización, la organización podrá:  
   
* Bloquear acceso: le impide usar las aplicaciones protegidas de su organización mientras inicia sesión en su cuenta profesional o educativa.  
* Borrar datos: elimina los datos profesionales o educativos de una o varias de las aplicaciones protegidas de su organización.  

Para resolver una amenaza y recuperar el acceso, abra la aplicación MTD en el dispositivo. Lea la información proporcionada para obtener información sobre cómo la amenaza podría afectar al dispositivo y cómo resolverlo. Después de seguir los pasos para resolver la amenaza, vuelva a la aplicación MTD e inicie un nuevo examen. Puede tardar unos minutos en recuperar el acceso a su organización.  

## <a name="next-steps"></a>Pasos siguientes  

¿Sigue necesitando ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).

