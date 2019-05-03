---
title: Configuración del acceso de dispositivos iOS a los recursos de la empresa | Microsoft Docs
description: Describe cómo hacer que Intune administre los dispositivos iOS
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/05/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilv
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: d0c7ac239a67a51ba7165771206883f3c46f5f55
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "59292431"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>Configuración del acceso de dispositivos iOS a los recursos de la empresa  

Inscriba el dispositivo iOS con la aplicación Portal de empresa de Intune para obtener acceso seguro a las aplicaciones, los archivos y el correo electrónico de la organización.

Después de que el dispositivo esté inscrito, se convierte en *administrada*. Su organización puede asignar directivas y aplicaciones en el dispositivo a través de un proveedor de administración (MDM) de dispositivos móviles, como Intune.  

Para conservar el acceso a la información profesional o educativa desde el dispositivo, debe configurarlo para que coincida con la configuración preferida de la organización. En este artículo se describe cómo usar el Portal de empresa, inscribir dispositivos y mantener los requisitos de configuración de su organización. 

> [!NOTE]
> Este artículo le interesará si ha intentado acceder al correo electrónico de la empresa en la aplicación Correo y se le ha pedido que administrara su dispositivo. Siga estas instrucciones para acceder a su correo electrónico y a otros recursos de la empresa en su dispositivo iOS.  

## <a name="what-to-expect-from-the-company-portal-app"></a>Qué esperar de la aplicación Portal de empresa  

### <a name="security"></a>Seguridad  
Durante la instalación inicial, la aplicación requiere que se autentique con la organización. Después le informa de cualquier configuración del dispositivo que debe actualizar. Por ejemplo, las organizaciones suelen definir requisitos de caracteres mínimos o máximos para las contraseñas que tendrá que cumplir.     

### <a name="protection"></a>Protección  
Una vez inscrito el dispositivo, la aplicación Portal de empresa continuará para asegurarse de que el dispositivo esté protegido. Por ejemplo, si instala una aplicación desde un origen que no sea de confianza, la aplicación le avisará y, en ocasiones, revocará el acceso a los datos de la empresa. Este tipo de directiva es común en las organizaciones y, a menudo, deberá desinstalar la aplicación de confianza para recuperar el acceso.  

### <a name="setting-notifications"></a>Configuración de notificaciones  
Si después de la inscripción, la organización exige un nuevo requisito de seguridad, como la autenticación multifactor, la aplicación Portal de empresa se lo notificará. Tendrá la oportunidad de ajustar la configuración para poder seguir trabajando desde su dispositivo.  

Para obtener más información sobre la inscripción, vea [¿Qué ocurre si instalo la aplicación de Portal de empresa e inscribo el dispositivo?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios).  

## <a name="enroll-your-ios-device"></a>Inscripción de dispositivos iOS  

Vaya a la tienda de aplicaciones para descargar e instalar el [aplicación Portal de empresa de Intune](install-and-sign-in-to-the-intune-company-portal-app-ios.md) en el dispositivo. También tendrá que mantener una conexión Wi-Fi y tener acceso a Safari durante la inscripción. 

Hacer una pausa durante más de unos minutos durante la inscripción puede provocar que la aplicación cerrar o finalizar el programa de instalación. Si esto ocurre, abra la aplicación de Portal de empresa e inténtelo de nuevo.  

1. Abra el Portal de empresa de Intune e inicie sesión con su cuenta profesional o educativa. 

    ![Captura de pantalla de ejemplo de aplicación de Portal de empresa de inicio de sesión.](./media/ios-01-cp-enroll-1903.PNG)  

2. Cuando se le solicite para recibir notificaciones de Portal de empresa, pulse **permitir.** Portal de empresa utiliza notificaciones para alertar si, por ejemplo, la configuración del dispositivo debe actualizarse. 

    ![Captura de pantalla de ejemplo de página principal de Portal de empresa, símbolo del sistema de "Notificaciones".](./media/ios-04-cp-enroll-1903.PNG)  

3. En el **configurar el acceso** pantalla, seleccione **comenzar.**  

     ![Captura de pantalla de ejemplo de Portal de empresa, la pantalla "Configuración del acceso de".](./media/ios-05-cp-enroll-1903.PNG)  

4. Lea la lista de su organización puede y no puede ver información del dispositivo. A continuación, puntee en **continuar**.  

5. Lea las instrucciones que aparecen en la **qué será lo próximo?** pantalla. Cuando esté listo para descargar e instalar el perfil de administración, pulse **continuar**.  

 > [!IMPORTANT]
> Estos pasos y pantallas siguiente variarán según la versión de iOS. Siga los pasos para la versión de iOS. 

6. Safari abrirá el sitio Web de Portal de empresa en el dispositivo. Cuando se le pida que descargue el perfil de configuración, puntee en **permitir**. Si se encuentra en un dispositivo que ejecute:  
    * iOS 12,2 y versiones posteriores: una vez completada la descarga, pulse **hecho.** Vaya al paso 7 de este artículo.
    * 12.1 y versiones anteriores de iOS: se le redirigirá automáticamente a la aplicación configuración. Vaya al paso 8 de este artículo.  
 
    Si pulsa accidentalmente **omitir**, actualice la página. Se le pedirá que abra la aplicación de Portal de empresa. Desde la aplicación, puede pulsar **volver a descargar**.

  > [!NOTE]
  > Debe instalar el perfil de administración como se describe en los pasos siguientes en 8 minutos de descargarlo. Si no lo hace, se quitará el perfil y tendrá que reiniciar la inscripción.  

7. iOS 12,2 y versiones posteriores únicamente: cuando se le pedirá que abra el Portal de empresa, pulse **abrir**. El **instalar perfil de administración** pantalla enumera los pasos para instalar el perfil.

    ![Captura de pantalla de ejemplo de Portal de empresa, la pantalla Instalar perfil de administración.](./media/ios-1904-settings-icon.PNG)  

8. Vaya a la aplicación de configuración y pulse **perfil descargado**.  

    Si **perfil descargado** no aparece como opción, vaya a **General** > **perfiles**. Si aún no ve el perfil, deberá descargarlo de nuevo.  

    ![Captura de pantalla de ejemplo de la aplicación de configuración, el perfil descargado configuración.](./media/ios-1904-settings-badge.PNG)  

9. Pulse **Instalar**.  
    
10. Escriba la contraseña del dispositivo. A continuación, puntee en **instalar**.    

    ![Captura de pantalla de ejemplo de la aplicación de configuración, la pantalla Instalar perfil, con un cursor en la ** Install ** botón.](./media/ios-1904-password-install.PNG)  


11. La pantalla siguiente es una advertencia estándar del sistema de administración de dispositivos. Para continuar con la instalación, pulse **instalar**. Si se le solicite confiar en administración remota, pulse **confianza**.  

    ![Captura de pantalla de ejemplo de aplicación de configuración, la pantalla de advertencia estándar del sistema para el certificado raíz y administración de dispositivos móviles.](./media/ios-15-cp-enroll-1903.PNG)  

12. Una vez completada la instalación, pulse **realiza**. Para comprobar que el perfil se ha instalado, vaya a la **Profiles & Device Management** configuración. Debería ver el perfil que se anuncie **administración de dispositivos móviles**.   

    ![Captura de pantalla de ejemplo de aplicación de configuración, administración de dispositivo y perfiles de configuración, que muestra el perfil de administración.](./media/ios-00-cp-enroll-1903.PNG)  

13. Vuelva a la aplicación Portal de empresa de Intune. Portal de empresa comenzará a sincronizar y configurar el dispositivo. Portal de empresa podría solicitarle que actualizar la configuración de dispositivo adicionales. Si lo hace, pulse **continuar**.  

    ![Captura de pantalla de ejemplo de Portal de empresa, la pantalla "Configuración del acceso de", con un triángulo amarillo junto al requisito de configuración.](./media/ios-12-cp-enroll-1903.PNG)  

14. Sabrá que la instalación está completa cuando todos los elementos de la lista muestran un círculo verde. Pulse **Listo**.   
    
    ![Captura de pantalla de ejemplo de Portal de empresa, "todo listo!" pantalla, que muestra todos los círculos verdes.](./media/ios-13-cp-enroll-1903.PNG)  

> [!Note]
> Si la organización supervisa los límites de voz y datos, o le proporcionará un dispositivo propiedad de la empresa, puede que tenga unos pocos pasos más en completarse. Si se le pedirá que instale el **Datalert** aplicación, consulte [inscribir el dispositivo en la administración de gastos de telecomunicaciones](enroll-your-device-with-telecom-expense-management-ios.md). Si su organización es parte del programa de inscripción de dispositivos de Apple, puede averiguar [cómo inscribir el dispositivo de la empresa](enroll-your-device-dep-ios.md).  

## <a name="next-steps"></a>Pasos siguientes  
Buscar aplicaciones que le ayudará en el trabajo o escuela. Obtenga información sobre [cómo las aplicaciones se ponen a disposición](use-managed-apps-on-your-device-ios.md) a través del Portal de empresa.  

¿Sigue necesitando ayuda? Póngase en contacto con el equipo de soporte técnico de su empresa. Puede encontrar su información de contacto en el [sitio web del Portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  
