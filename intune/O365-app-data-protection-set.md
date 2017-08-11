---
title: "Establecimiento de la administración básica de datos en aplicaciones de Office 365 en Intune"
titleSuffix: Intune on Azure
description: "Documentación complementaria del asistente Administrar aplicaciones de Office 365."
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 852612ac-f146-4372-a900-3f6fdebd05ad
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ayesham
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d21b6a03cdc8094bc8da3cecd5331b3f11400302
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2017
---
# <a name="how-your-users-will-experience-basic-protection-on-managed-office-365-apps"></a>Cómo sus usuarios experimentarán la protección básica en las aplicaciones administradas de Office 365

El **asistente para administrar aplicaciones de Office 365** crea una directiva de protección de aplicaciones para cada plataforma de dispositivo.

El asistente activa las siguientes directivas:

**iOS**
* Cifrar datos de aplicación

**Android**
* Cifrar datos de aplicación
* Requerir PIN simple en acceso

Estas directivas garantizan que puede administrar las aplicaciones de Office 365, dándole la posibilidad de borrar datos de trabajo de las aplicaciones de Office cuando lo necesite. También garantizan la protección básica en caso de robo o pérdida de un dispositivo, al asegurar que los datos de trabajo están cifrados y que se debe escribir un PIN para ver los datos en las aplicaciones de Office 365.


Este artículo usa OneDrive para la Empresa como ejemplo para demostrar la experiencia del usuario en una aplicación administrada por Intune.


>[!NOTE]
>En un dispositivo personal, normalmente el usuario final descargaría la aplicación. Si el dispositivo se administra mediante una solución de administración de dispositivos móviles (MDM), puede implementar la aplicación en el dispositivo.

## <a name="user-experience-on-an-ios-device"></a>Experiencia del usuario en un dispositivo iOS

1. Inicie la aplicación OneDrive para la Empresa para abrir la página de inicio de sesión.  <br/> ![Imagen de la pantalla de inicio de sesión de OneDrive para iOS](./media/onedrive-ios-sign-in.png)
2. Escriba su nombre de usuario de la cuenta profesional. Se le redirigirá a la página de autenticación de Office 365 para que indique las credenciales de trabajo. <br/> ![Imagen de la página de inicio de sesión de Office 365](./media/o365-sign-in-ios.png)
3. Una vez que Azure Active Directory autentique correctamente sus credenciales, se aplican las directivas de protección de aplicaciones y se le pide que reinicie la aplicación OneDrive para la Empresa.  <br/>![Imagen del mensaje de reinicio para iOS](./media/ios-restart-prompt.png)    
  > [!NOTE]
  > El mensaje de reinicio requerido solo se muestra en dispositivos que no estén inscritos en Intune.


4. Vuelva a iniciar la aplicación OneDrive para la Empresa. La aplicación se inicia con las directivas de protección de aplicaciones activadas y se le pide que establezca un PIN para el dispositivo (si aún no tiene uno). <br/> ![Imagen del mensaje para crear un PIN](./media/pin-prompt-ios.png)    
  > [!NOTE]
  > La mayoría de los usuarios no verá este mensaje. Solo los usuarios que no hayan habilitado un PIN en su dispositivo iOS verán este mensaje.


5. Una vez que haya establecido el PIN y lo haya confirmado, vuelva a la aplicación OneDrive para la Empresa. Verá un único aviso de que su administrador de TI está ahora protegiendo los datos de trabajo en OneDrive. <br/> ![Imagen de único aviso de su administrador de TI](./media/one-time-notice.png)
6. Haga clic en este aviso para acceder a los archivos de OneDrive para la Empresa. <br/> ![Imagen de los archivos de OneDrive en el dispositivo iOS](./media/onedrive-files-ios.png) <br/>

>[!NOTE]
>Al cambiar una directiva implementada, los cambios se aplicarán la próxima vez que abra la aplicación.


## <a name="user-experience-on-an-android-device"></a>Experiencia del usuario en un dispositivo Android

1. Inicie la aplicación OneDrive para la Empresa para abrir la página de inicio de sesión.  <br/> ![Imagen de la pantalla de bienvenida de la aplicación OneDrive](./media/onedrive-android-welcome.png)
2. Escriba su nombre de usuario de la cuenta profesional. Se le redirigirá a la página de autenticación de Office 365 para que indique las credenciales de trabajo. <br/> ![Imagen de inicio de sesión de Office 365 en Android](./media/o365-sign-in-android.png)
3. Una vez que Azure Active Directory autentique correctamente sus credenciales, verá un mensaje que le indica que instale la aplicación Portal de empresa, si aún no está instalada en el dispositivo. Pulse en **Ir a la tienda** para continuar. <br/> ![Imagen del mensaje para obtener la aplicación Portal de empresa](./media/get-company-portal-android.png) <br/>Si ya tiene instalada la aplicación Portal de empresa en el teléfono, la aplicación OneDrive para la Empresa se iniciará automáticamente y podrá saltar a la nota final.    
  > [!IMPORTANT]
  > En Android, una vez que ha configurado aplicaciones de Office para que se administren mediante una directiva de protección de aplicaciones, el usuario del dispositivo **debe** instalar la aplicación de portal de empresa para acceder a los correos electrónicos y documentos de trabajo, aunque en realidad el usuario final no tenga necesidad de abrir la aplicación o iniciar sesión en ella para leer los correos electrónicos o los documentos.

4. Ahora se encuentra en Google Play Store, donde puede descargar e instalar la aplicación Portal de empresa. La aplicación ayuda a mantener los datos seguros y protegidos. <br/> ![Imagen de la aplicación en Google Play Store](./media/google-play-get-app-android.png)
5. Cuando haya completado la instalación de la aplicación, elija **Aceptar** para aceptar los términos. La aplicación OneDrive para la Empresa se iniciará automáticamente.


>[!NOTE]
>La próxima vez que abra OneDrive para la Empresa, es posible que se le pida que establezca un PIN si así lo exige su responsable de TI. Después de configurar y confirmar el PIN, puede continuar con OneDrive para la Empresa.

![Imagen del mensaje del PIN](./media/pin-prompt-android.png)


<!--- Original steps: 6. The next time you open OneDrive for Business, you may be asked to set a PIN, if your IT requires one to use the OneDrive for Business app. ART 7. After you set and confirm the PIN, you can continue on to OneDrive for Business. -->

## <a name="what-policies-does-this-wizard-set"></a>¿Qué directivas establece este asistente?
|     |       | |
|----|--------|-|
|**Nombre**|Administración de aplicaciones de Office 365| |
| **Descripción**|Creado por el asistente para administrar aplicaciones de Office 365| |
| |  | |
| **Nombre de la configuración** |**Valor de la directiva de iOS** | **Valor de la directiva de Android** |
|Impedir copias de seguridad de iTunes e iCloud| No | No aplicable |
|Impedir copias de seguridad de Android |No aplicable | No|
|Permitir que la aplicación transfiera datos a otras aplicaciones | Todas las aplicaciones | Todas las aplicaciones|
|Permitir que la aplicación reciba datos de otras aplicaciones| Todas las aplicaciones | Todas las aplicaciones|
|Impedir "Guardar como" | No | No|
|Restringir cortar, copiar y pegar con otras aplicaciones | Cualquier aplicación | Cualquier aplicación |
|Restringir contenido web para mostrar en un explorador administrado corporativo | No| No|
|Cifrar datos de aplicación | Cuando el dispositivo está bloqueado | Sí|
|Deshabilitar la sincronización de contactos | No| No|
|Deshabilitar la impresión | No | No|
|Requerir PIN para acceder | No | Sí|
|Número de intentos antes de restablecimiento del PIN | No aplicable |5|
|Permitir PIN sencillo | No aplicable |Sí|
|Longitud del PIN | No aplicable | 4|
|Permitir desbloqueo mediante huellas digitales en lugar de mediante PIN | No aplicable | Sí |
|Requerir credenciales corporativas en acceso | No | No|
|Bloquear la ejecución de aplicaciones administradas en dispositivos liberados o modificados | No | No|
|Volver a comprobar los requisitos de acceso después de (minutos): tiempo de espera | 30 | 30|
|Volver a comprobar los requisitos de acceso después de (minutos): período de gracia sin conexión | 720 |720|
|Intervalo sin conexión (días) antes de que se borren los datos de la aplicación | 90 | 90|
|Bloquear captura de pantalla (solo en dispositivos Android) | No aplicable | No |

### <a name="why-is-an-app-pin-policy-only-configured-for-android-devices"></a>¿Por qué sólo se configura una directiva de PIN de aplicación para dispositivos Android?
El cifrado funciona de forma diferente en iOS y Android.

En iOS, para las aplicaciones que están asociadas con una directiva de protección de aplicaciones de Intune, los datos se cifran en reposo mediante el cifrado de nivel de dispositivo proporcionado por el sistema operativo. Por lo tanto, al activar la directiva de cifrado de la aplicación, está también exigiendo automáticamente que el usuario tenga un PIN y lo escriba para acceder a los datos de trabajo. A los usuarios que no tengan ya un PIN de dispositivo configurado en el dispositivo se les pedirá que creen uno.

En Android, para las aplicaciones que están asociadas con una directiva de protección de aplicaciones de Intune, los datos se cifran de forma sincrónica durante las tareas de E/S de archivos. El contenido del almacenamiento del dispositivo estará siempre cifrado. En dispositivos que no están administrados por MDM, la directiva de protección de aplicaciones no puede forzar el requisito de un PIN de dispositivo. Para asegurarse de que se pida a los usuarios que usen un PIN para acceder a los datos de trabajo, el asistente habilita la directiva de PIN de la aplicación.

Siempre puede modificar estas opciones de directiva para satisfacer los requisitos de su organización.

### <a name="how-can-i-view-and-edit-the-policies-created-by-the-wizard"></a>¿Cómo puedo ver y editar las directivas creadas por el asistente?
Para ver o actualizar estas directivas, o las directivas que se crean en el portal de Azure de Intune, en el panel, elija **Administrar aplicaciones** > **Directivas de protección de aplicaciones**. Se abrirá la lista de directivas a la derecha. Seleccione la directiva que desea ver para editar la configuración. <br/>
![Imagen de la ruta de la interfaz de usuario para ver las directivas](./media/image-for-faq.png)

## <a name="next-steps"></a>Pasos siguientes
Más información sobre [las directivas de protección de aplicaciones](https://docs.microsoft.comapp-protection-policy.md).
