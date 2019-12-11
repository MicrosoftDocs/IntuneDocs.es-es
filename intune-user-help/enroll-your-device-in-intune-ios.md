---
title: Configuración del acceso de dispositivos iOS a los recursos de la empresa | Microsoft Docs
description: Describe cómo hacer que Intune administre los dispositivos iOS
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/12/2019
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
ms.collection: M365-identity-device-management
ms.openlocfilehash: e468042ab81d563c9fa4b272661508a340d61aa9
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506236"
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

    ![Captura de pantalla de ejemplo del inicio de sesión de la aplicación Portal de empresa.](./media/ios-01-cp-enroll-1904.PNG)  

2. Cuando se le pregunte si quiere recibir notificaciones de Portal de empresa, pulse **Permitir**. Portal de empresa usa notificaciones para indicarle, por ejemplo, si se debe actualizar la configuración del dispositivo. 

    ![Captura de pantalla de ejemplo del aviso “Notificaciones” de la página principal de Portal de empresa.](./media/ios-02-cp-enroll-1904.PNG)  

3. En la pantalla **Configurar el acceso**, seleccione **Empezar**.  

     ![Captura de pantalla de ejemplo de la pantalla “Configurar el acceso” de Portal de empresa.](./media/ios-03-cp-enroll-1904.PNG)  

4. Lea la lista de información del dispositivo que puede y no puede ver su organización. Después, pulse **Continuar**.  

5. Lea las instrucciones que aparecen en la pantalla **¿Cuál es el siguiente paso?** Cuando tenga todo listo para descargar e instalar el perfil de administración, pulse **Continuar**.  

 > [!IMPORTANT]
> Los siguientes pasos y pantallas variarán según la versión de iOS que tenga. Siga los pasos de su versión de iOS. 

6. Safari abre el sitio web de Portal de empresa en el dispositivo. Cuando se le pida que descargue el perfil de configuración, pulse **Permitir**. Si está en un dispositivo que ejecuta:  
    * iOS 12.2 y versiones posteriores: cundo se complete la descarga, pulse **Listo**. Vaya al paso 7 de este artículo.
    * iOS 12.1 y versiones anteriores: se le redirigirá automáticamente a la aplicación Ajustes. Vaya al paso 8 de este artículo.  
 
    Si pulsa accidentalmente **Omitir**, actualice la página. Se le pedirá que abra la aplicación Portal de empresa. En la aplicación, puede pulsar **Volver a descargar**.

  > [!NOTE]
  > Debe instalar el perfil de administración tal y como se describe en los pasos siguientes en un plazo de 8 minutos tras descargarlo. Si no lo hace, se quitará el perfil y tendrá que reiniciar la inscripción.  

7. Solo iOS 12.2 y versiones posteriores: cuando se le pida que abra Portal de empresa, pulse **Abrir**. En la pantalla **Instalando el perfil de administración** aparecen los pasos para instalar el perfil.

    ![Captura de pantalla de ejemplo de la pantalla Instalando el perfil de administración de Portal de empresa.](./media/ios-07-cp-enroll-1904.PNG)  

8. Vaya a la aplicación Ajustes y pulse **Perfil descargado**.  

    Si no aparece **Perfil descargado** como opción, vaya a **General** > **Perfiles**. Si sigue sin ver el perfil, es posible que tenga que descargarlo de nuevo.  

    ![Captura de pantalla de ejemplo de la configuración Perfil descargado de la aplicación Ajustes.](./media/ios-1904-settings-badge.PNG)  

9. Pulse **Instalar**.  
    
10. Escriba la contraseña del dispositivo. Después pulse **Instalar**.    

    ![Captura de pantalla de ejemplo de la pantalla Instalando perfil de la aplicación Ajustes, con un cursor en el botón **Instalar**.](./media/ios-10-cp-enroll-1904.PNG)  


11. La pantalla siguiente es una advertencia estándar del sistema de administración de dispositivos. Para continuar con la instalación, pulse **Instalar**. Si se le pide que confíe en la administración remota, pulse **Confiar**.  

    ![Captura de pantalla de ejemplo de la pantalla de advertencia estándar del sistema de la administración de dispositivos móviles y certificados raíz de la aplicación Ajustes.](./media/ios-11-cp-enroll-1904.PNG)  

12. Cuando se haya completado la instalación, pulse **Listo**. Para comprobar que el perfil se ha instalado, vaya a la configuración **Profiles & Device Management** (Administración de perfiles y dispositivos). Debería ver el perfil en **Administración de dispositivos móviles**.   

    ![Captura de pantalla de la configuración Administración de perfiles y dispositivos de la aplicación Ajustes, que muestra el perfil de administración.](./media/ios-12-cp-enroll-1904.PNG)  

13. Vuelva a la aplicación Portal de empresa. Portal de empresa comenzará a sincronizar y configurar el dispositivo. Portal de empresa podría pedirle que actualice alguna configuración adicional del dispositivo. Si lo hace, pulse **Continuar**.  

    ![Captura de pantalla de ejemplo de la pantalla “Configurar el acceso” de Portal de empresa, con un triángulo amarillo junto al requisito de configuración.](./media/ios-13-cp-enroll-1904.PNG)  

14. Sabrá que la configuración se ha completado cuando todos los elementos de la lista muestren un círculo verde. Pulse **Listo**.   
    
    ![Captura de pantalla de ejemplo de la pantalla ¡Ya está todo listo! de la aplicación Portal de empresa, que muestra todos los círculos verdes.](./media/ios-14-cp-enroll-1904.PNG)  

> [!Note]
> Si su organización supervisa los límites de voz y datos, o le proporciona un dispositivo propiedad de la empresa, puede que tenga que completar algunos pasos más. Si se le pide que instale la aplicación **Datalert**, consulte [Inscripción del dispositivo en la administración de gastos de telecomunicaciones](enroll-your-device-with-telecom-expense-management-ios.md). Si su organización forma parte del Programa de inscripción de dispositivos de Apple, descubra [cómo inscribir su dispositivo de la empresa](enroll-your-device-dep-ios.md).  

## <a name="it-administrator-support"></a>Soporte técnico para administradores de TI  
Si es administrador de TI y detecta problemas al inscribir dispositivos, vea [Troubleshooting iOS device enrollment problems in Microsoft Intune](https://support.microsoft.com/en-us/help/4039809) (Solucionar problemas de inscripción de dispositivos iOS en Microsoft Intune). En este artículo se enumeran errores habituales, sus causas y los pasos para resolverlos.  

## <a name="next-steps"></a>Pasos siguientes  
Busque aplicaciones que le ayudarán en el trabajo o la escuela. Obtenga información sobre [cómo se ponen las aplicaciones a su disposición](use-managed-apps-on-your-device-ios.md) mediante el Portal de empresa.  

¿Sigue necesitando ayuda? Póngase en contacto con el equipo de soporte técnico de su empresa. Puede encontrar su información de contacto en el [sitio web del Portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  
