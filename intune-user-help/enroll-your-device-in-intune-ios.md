---
title: Configuración del acceso de dispositivos iOS a los recursos de la empresa | Microsoft Docs
description: Describe cómo hacer que Intune administre los dispositivos iOS
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/18/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilv
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 92d1ca850d8bb542f0b7fe027ab7af8c12089ef8
ms.sourcegitcommit: 9ee2401a2f01373a962749b0728c22385dbcba6d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181762"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>Configuración del acceso de dispositivos iOS a los recursos de la empresa  

Inscriba el dispositivo iOS con la aplicación Portal de empresa de Intune para obtener acceso seguro a las aplicaciones, los archivos y el correo electrónico de la organización.

Después de haber inscrito el dispositivo, se convierte en *administrado*. La organización puede asignar directivas y aplicaciones al dispositivo mediante un proveedor de administración de dispositivos móviles (MDM), como Intune.  

> [!NOTE]
> No vendemos ningún dato recogido por nuestro servicio a terceros por ningún motivo.  

Para conservar el acceso a la información profesional o educativa desde el dispositivo, deberá configurarlo para que coincida con la configuración preferida de la organización. En este artículo se describe cómo usar Portal de empresa para inscribir el dispositivo y mantener los requisitos de configuración de su organización.  
</br>
> [!VIDEO https://www.youtube.com/embed/mJyv6YcHi7c?rel=0]

> [!NOTE]
> Este artículo le interesará si ha intentado acceder al correo electrónico de la empresa en la aplicación Correo y se le ha pedido que administrara su dispositivo. Siga estas instrucciones para acceder a su correo electrónico y a otros recursos de la empresa en su dispositivo iOS.  


## <a name="what-to-expect-from-the-company-portal-app"></a>Qué esperar de la aplicación Portal de empresa  

### <a name="security"></a>Seguridad  
Durante la instalación inicial, la aplicación requiere que se autentique con la organización. Después le informa de cualquier configuración del dispositivo que debe actualizar. Por ejemplo, las organizaciones suelen definir requisitos de caracteres mínimos o máximos para las contraseñas que tendrá que cumplir.

### <a name="protection"></a>Protección  
Una vez inscrito el dispositivo, la aplicación Portal de empresa continuará para asegurarse de que el dispositivo esté protegido. Por ejemplo, si instala una aplicación desde un origen que no sea de confianza, la aplicación le avisará y, en ocasiones, revocará el acceso a los datos de la empresa. Este tipo de directiva es común en las organizaciones y suele requerirle que desinstale la aplicación que no es de confianza para poder recuperar el acceso.  

### <a name="setting-notifications"></a>Configuración de notificaciones  
Si después de la inscripción, la organización exige un nuevo requisito de seguridad, como la autenticación multifactor, la aplicación Portal de empresa se lo notificará. Tendrá la oportunidad de ajustar la configuración para poder seguir trabajando desde su dispositivo.  

Para obtener más información sobre la inscripción, vea [¿Qué ocurre si instalo la aplicación de Portal de empresa e inscribo el dispositivo?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios).  

## <a name="enroll-your-ios-device"></a>Inscripción de dispositivos iOS  

Vaya al App Store para descargar e instalar la [aplicación Portal de empresa de Intune](install-and-sign-in-to-the-intune-company-portal-app-ios.md) en su dispositivo. También tendrá que mantener una conexión Wi-Fi y tener acceso a Safari durante la inscripción. 

Si hace una pausa de más de unos minutos durante la inscripción, puede provocar que la aplicación se cierre o que finalice la configuración. Si ocurre esto, abra la aplicación Portal de empresa y vuelva a intentarlo.  

1. Abra el Portal de empresa de Intune e inicie sesión con su cuenta profesional o educativa.  

2. Cuando se le pregunte si quiere recibir notificaciones de Portal de empresa, pulse **Permitir**. Portal de empresa usa notificaciones para indicarle, por ejemplo, si se debe actualizar la configuración del dispositivo.  

3. En la pantalla **Configurar el acceso**, seleccione **Empezar**.   

    ![Captura de pantalla de ejemplo de la pantalla “Configurar el acceso” de Portal de empresa.](./media/ios-enrollment-checklist-1909.PNG)  

4. Aparecerá la pantalla **Seleccionar dispositivo y tipo de inscripción**, en la que se le solicita el tipo de dispositivo.  
    * Pulse **(Organización) es el propietario de este dispositivo** si ha recibido el dispositivo de la organización. Después, vaya a [Protección de todo el dispositivo](#secure-entire-device) en este artículo para finalizar la instalación.  
    * Pulse **Soy el propietario de este dispositivo** si usa un dispositivo personal que ha traído de casa. Luego vaya al paso siguiente.  

    Si no ve esta pantalla, vaya a [Protección de todo el dispositivo](#secure-entire-device) para finalizar la instalación.  
    
    ![Captura de pantalla de ejemplo de Portal de empresa, la pantalla "Seleccionar dispositivo y tipo de inscripción" y las opciones de tipo de dispositivo.](./media/ios-device-type-1909.PNG)  


5. Elija cómo proteger los datos en el dispositivo una vez inscrito.  
    * Pulse **Proteger todo el dispositivo** para proteger todas las aplicaciones y los datos del dispositivo. Después, vaya a [Protección de todo el dispositivo](enroll-your-device-in-intune-ios.md#secure-entire-device) para finalizar la instalación.
    * Pulse **Proteger solo datos y aplicaciones relacionados con el trabajo** para proteger solo las aplicaciones y los datos a los que acceda con la cuenta profesional. Después, vaya a [Protección de datos y aplicaciones relacionados con el trabajo](enroll-your-device-in-intune-ios.md#secure-work-related-apps-and-data).  

    ![Captura de pantalla de ejemplo de Portal de empresa, la pantalla "Seleccionar dispositivo y tipo de inscripción" y las opciones de tipo de inscripción.](./media/ios-enrollment-type-1909.PNG)  


### <a name="secure-entire-device"></a>Protección de todo el dispositivo  

1. En la pantalla **Administración de dispositivos y privacidad**, lea la lista de información del dispositivo que puede y no puede ver su organización. Después, pulse **Continuar**.  


 > [!IMPORTANT]
> Los siguientes pasos y pantallas variarán según la versión de iOS que tenga. Siga los pasos de su versión de iOS. 

2. Safari abre el sitio web de Portal de empresa en el dispositivo. Cuando se le pida que descargue el perfil de configuración, pulse **Permitir**. Si está en un dispositivo que ejecuta:  
    * iOS 12.2 y versiones posteriores: cuando se complete la descarga, pulse en **Cerrar**. Luego vaya al paso 3.  
    * iOS 12.1 y versiones anteriores: Una vez completada la descarga, se le redirigirá automáticamente a la aplicación Configuración. Vaya al paso 4.  
 
    Si pulsa accidentalmente **Omitir**, actualice la página. Se le pedirá que abra la aplicación Portal de empresa. Una vez allí, pulse **Volver a descargar**.

  > [!NOTE]
  > Debe instalar el perfil de administración tal y como se describe en los pasos siguientes en un plazo de 8 minutos tras descargarlo. Si no lo hace, se quitará el perfil y tendrá que reiniciar la inscripción.  

3. Cuando se le pida que abra Portal de empresa, pulse **Abrir**. Lea la información de la pantalla **Cómo instalar el perfil de administración**.  

4. Vaya a la aplicación Configuración y pulse **Inscribir en < nombre de la organización >** o **Perfil descargado**.  

    ![Captura de pantalla de ejemplo de la aplicación Configuración, opción Inscribir en la organización.](./media/enroll-in-organization-ios-1909.PNG)  

   Si no aparecen las opciones, vaya a **General** > **Administración de perfiles y dispositivos**> **Perfil de administración**. Si sigue sin ver un perfil de administración, es posible que tenga que descargarlo de nuevo.  

5. Pulse **Instalar**.  
    
6. Escriba la contraseña del dispositivo. Después pulse **Instalar**.    

7. La pantalla siguiente es una advertencia estándar del sistema sobre la administración de dispositivos. Para continuar con la instalación, pulse **Instalar**. Si se le pide que confíe en la administración remota, pulse **Confiar**.  

8. Cuando se haya completado la instalación, pulse **Listo**. Para comprobar que el perfil se ha instalado, vaya a la configuración **Profiles & Device Management** (Administración de perfiles y dispositivos). Debería ver el perfil en **Administración de dispositivos móviles**.   

    ![Captura de pantalla de la configuración Administración de perfiles y dispositivos de la aplicación Ajustes, que muestra el perfil de administración.](./media/ios-12-cp-enroll-1904.PNG)  

9. Vuelva a la aplicación Portal de empresa. Portal de empresa comenzará a sincronizar y configurar el dispositivo. Portal de empresa podría pedirle que actualice alguna configuración adicional del dispositivo. Si lo hace, pulse **Continuar**.  

10. Se sabe que la configuración se ha completado cuando todos los elementos de la lista muestran una marca de verificación verde. Pulse **Listo**.   

> [!Note]
> Si su organización supervisa los límites de voz y datos, o le proporciona un dispositivo propiedad de la empresa, puede que tenga que completar algunos pasos más. Si se le pide que instale la aplicación **Datalert**, consulte [Inscripción del dispositivo en la administración de gastos de telecomunicaciones](enroll-your-device-with-telecom-expense-management-ios.md). Si su organización forma parte del Programa de inscripción de dispositivos de Apple, descubra [cómo inscribir su dispositivo de la empresa](enroll-your-device-dep-ios.md).  

### <a name="secure-work-related-apps-and-data"></a>Protección de datos y aplicaciones relacionados con el trabajo  
1. Aparece la pantalla **Descargar Microsoft Authenticator** (si ya tiene el autenticador, no verá esta pantalla, por lo que vaya al paso 2).  
    1. Pulse **Descargar de App Store**.
    2. Cuando se abra App Store, instale la aplicación. 
    3. Vuelva al Portal de empresa y pulse **Continuar**.    
    
   Después de instalar Microsoft Authenticator, no tendrá que hacer nada más con la aplicación. Solo tiene que estar presente en el dispositivo. 

   ![Captura de pantalla de ejemplo de Portal de empresa, pantalla "Descargar Microsoft Authenticator".](./media/download-ms-authenticator-1909.PNG)  

2. En la pantalla **Administración de dispositivos y privacidad**, lea la lista de información del dispositivo que puede y no puede ver su organización. Después, pulse **Continuar**.  


 > [!IMPORTANT]
> Los siguientes pasos y pantallas variarán según la versión de iOS que tenga. Siga los pasos de su versión de iOS. 

3. Safari abre el sitio web de Portal de empresa en el dispositivo. Cuando se le pida que descargue el perfil de configuración, pulse **Permitir**. Si está en un dispositivo que ejecuta:  
    * iOS 12.2 y versiones posteriores: cuando se complete la descarga, pulse en **Cerrar**. Luego vaya al paso 4.  
    * iOS 12.1 y versiones anteriores: Una vez completada la descarga, se le redirigirá automáticamente a la aplicación Configuración. Vaya al paso 5.  
 
    Si pulsa accidentalmente **Omitir**, actualice la página. Se le pedirá que abra la aplicación Portal de empresa. En la aplicación, puede pulsar **Volver a descargar**.

  > [!NOTE]
  > Debe instalar el perfil de administración tal y como se describe en los pasos siguientes en un plazo de 8 minutos tras descargarlo. Si no lo hace, se quitará el perfil y tendrá que reiniciar la inscripción.  

4. Cuando se le pida que abra Portal de empresa, pulse **Abrir**. Lea la información de la pantalla **Cómo instalar el perfil de administración**. 

5. Vaya a la aplicación Configuración y pulse **Inscribir en < nombre de la organización >** o **Perfil descargado**.  

    ![Captura de pantalla de ejemplo de la aplicación Configuración, opción Inscribir en la organización.](./media/enroll-in-organization-ios-1909.PNG)  

   Si no aparecen las opciones, vaya a **General** > **Administración de perfiles y dispositivos**> **Perfil de administración**. Si sigue sin ver un perfil de administración, es posible que tenga que descargarlo de nuevo.   


6. En la pantalla **Inscripción de usuario**, pulse **Inscribir mi iPhone**.  

    ![Captura de pantalla de ejemplo de la aplicación Configuración, pantalla Inscripción de usuario, con el botón Inscribir resaltado.](./media/user-enrollment-information-1909.PNG)  

7. Escriba la contraseña del dispositivo. Después pulse **Instalar**.  

8. En la pantalla **Iniciar sesión**, escriba la contraseña del identificador de Apple administrado. En la mayoría de los casos, estas credenciales serán las mismas que se usan para iniciar sesión en la cuenta profesional o educativa, a menos que la organización le haya proporcionado un conjunto de credenciales diferente. 
9. Pulse **Iniciar sesión**.  
10. Una vez que se haya instalado el perfil, aparecerá un mensaje de operación correcta en la pantalla. Para comprobar que el perfil se ha instalado, vaya a la configuración  **Administración de perfiles y dispositivos** . Debería ver el perfil en  **Administración de dispositivos móviles**.  

    ![Captura de pantalla de la configuración Administración de perfiles y dispositivos de la aplicación Ajustes, que muestra el perfil de administración.](./media/ios-12-cp-enroll-1904.PNG)  

11. Vuelva a la aplicación Portal de empresa. Portal de empresa comenzará a sincronizar y configurar el dispositivo. Portal de empresa podría pedirle que actualice alguna configuración adicional del dispositivo. Si lo hace, pulse **Continuar**.    

12. Se sabe que la configuración se ha completado cuando todos los elementos de la lista muestran una marca de verificación verde. Pulse  **Listo**.  

## <a name="it-administrator-support"></a>Soporte técnico para administradores de TI  
Si es administrador de TI y detecta problemas al inscribir dispositivos, vea [Troubleshooting iOS device enrollment problems in Microsoft Intune](https://support.microsoft.com/en-us/help/4039809) (Solucionar problemas de inscripción de dispositivos iOS en Microsoft Intune). En este artículo se enumeran errores habituales, sus causas y los pasos para resolverlos.  

## <a name="next-steps"></a>Pasos siguientes  
Busque aplicaciones que le ayudarán en el trabajo o la escuela. Obtenga información sobre [cómo se ponen las aplicaciones a su disposición](use-managed-apps-on-your-device-ios.md) mediante el Portal de empresa.  

¿Aún necesita ayuda? Póngase en contacto con el equipo de soporte técnico de su empresa. Puede encontrar su información de contacto en el [sitio web del Portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  
