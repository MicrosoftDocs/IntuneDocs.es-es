---
title: Configuración del acceso de dispositivos iOS a los recursos de la empresa | Microsoft Docs
description: Describe cómo hacer que Intune administre los dispositivos iOS
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/26/2019
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
ms.openlocfilehash: ee0f438d929abd6b5b90acbaeeddc41e3ce11f98
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490649"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>Configuración del acceso de dispositivos iOS a los recursos de la empresa  

Inscriba el dispositivo iOS con la aplicación Portal de empresa de Intune para obtener acceso seguro a las aplicaciones, los archivos y el correo electrónico de la organización.

Antes de que pueda acceder a datos de propiedad desde un dispositivo corporativo o personal, es necesario tener el dispositivo administrado. Una vez que el dispositivo esté administrado, la organización asignará directivas y aplicaciones al dispositivo a través de un proveedor de administración de dispositivos móviles (MDM), como Intune. 

Para conservar el acceso a la información profesional o educativa desde el dispositivo, debe configurarlo para que coincida con la configuración preferida de la organización. En este artículo se describe cómo usar el Portal de empresa, inscribir dispositivos y mantener los requisitos de configuración de su organización. 

> [!NOTE]
> Este artículo le interesará si ha intentado acceder al correo electrónico de la empresa en la aplicación Correo y se le ha pedido que administrara su dispositivo. Siga estas instrucciones para acceder a su correo electrónico y a otros recursos de la empresa en su dispositivo iOS.  

## <a name="what-to-expect-from-the-company-portal-app"></a>Qué esperar de la aplicación Portal de empresa  

### <a name="security"></a>Seguridad  
Durante la instalación inicial, la aplicación requiere que se autentique con la organización. Después le informa de cualquier configuración del dispositivo que debe actualizar. Por ejemplo, las organizaciones suelen definir requisitos de caracteres mínimos o máximos para las contraseñas que tendrá que cumplir.     

### <a name="protection"></a>Protección  
Una vez inscrito el dispositivo, la aplicación Portal de empresa continuará para asegurarse de que el dispositivo esté protegido. Por ejemplo, si instala una aplicación desde un origen que no sea de confianza, la aplicación le avisará y, en ocasiones, revocará el acceso a los datos de la empresa. Una directiva similar al siguiente es común en las organizaciones y, a menudo, deberá desinstalar la aplicación de confianza para recuperar el acceso.  

### <a name="setting-notifications"></a>Configuración de notificaciones  
Si después de la inscripción, la organización exige un nuevo requisito de seguridad, como la autenticación multifactor, la aplicación Portal de empresa se lo notificará. Tendrá la oportunidad de ajustar la configuración para poder seguir trabajando desde su dispositivo.  

Para obtener más información sobre la inscripción, vea [¿Qué ocurre si instalo la aplicación de Portal de empresa e inscribo el dispositivo?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios).  

## <a name="enroll-your-ios-device"></a>Inscripción de dispositivos iOS   

> [!IMPORTANT]
> Las capturas de pantalla en esta sección muestran la experiencia para dispositivos que ejecutan iOS versión 12.1 y versiones anteriores. En su caso, hemos incluido instrucciones específicas de iOS versión 12.2 y versiones posteriores. Si observa que su experiencia es diferente de las capturas de pantalla que se muestra, consulte las 12,2 instrucciones.      

Vaya a la tienda de aplicaciones para descargar e instalar el [aplicación Portal de empresa de Intune](install-and-sign-in-to-the-intune-company-portal-app-ios.md) al dispositivo. Durante la inscripción, también necesitará una conexión Wi-Fi y el acceso a Safari. 

Si se pausa durante más de unos minutos durante la inscripción, la aplicación podría cerrar o finalizar el programa de instalación. Si esto ocurre, abra la aplicación de Portal de empresa e inténtelo de nuevo.  

1. Abra el Portal de empresa de Intune e inicie sesión con su cuenta profesional o educativa. 

    ![Captura de pantalla de ejemplo de aplicación de Portal de empresa de inicio de sesión.](./media/ios-01-cp-enroll-1903.PNG)  

2. Cuando se le solicite para recibir notificaciones de Portal de empresa, pulse **permitir.** Portal de empresa utiliza notificaciones para alertar si, por ejemplo, la configuración del dispositivo debe actualizarse. 

    ![Captura de pantalla de ejemplo de página principal de Portal de empresa, símbolo del sistema de "Notificaciones".](./media/ios-04-cp-enroll-1903.PNG)  

3. En el **configurar el acceso** pantalla, seleccione **comenzar.**  

     ![Captura de pantalla de ejemplo de Portal de empresa, la pantalla "Configuración del acceso de".](./media/ios-05-cp-enroll-1903.PNG)  

4. Lea la lista de su organización puede y no puede ver información del dispositivo. [Detalles adicionales sobre este tema](what-info-can-your-company-see-when-you-enroll-your-device-in-Intune.md) puede encontrarse a través de la **más** vínculo. Cuando haya terminado, pulse **continuar**.  

    ![Captura de pantalla de ejemplo de aplicación de Portal de empresa, "¿qué puede ver de mi organización", con el botón Continuar.](./media/ios-06-cp-enroll-1903.PNG)  
 
5. El **qué será lo próximo?** pantalla resume los pasos restantes. Estos pasos podrían ser diferentes en función de la versión de iOS. 
    * **iOS 12,2 y versiones posteriores**: su experiencia en su lugar puede requerir que:  

        a. **Permitir la descarga del perfil de administración de**: el explorador abrirá el sitio Web de Portal de empresa y le pedirá que permita la descarga. La descarga se guardará en la aplicación configuración.  

        b. **Abra la aplicación de configuración e instalar el perfil**: deberá ir a la aplicación de configuración e instalar el perfil de administración.  

        c. **Vuelva a la aplicación de Portal de empresa**:, deberá volver a la aplicación de Portal de empresa para completar la instalación.  

    Cuando esté listo para descargar el perfil de administración, pulse **continuar**.  

6. Safari abrirá el sitio Web de Portal de empresa. Cuando se le pida que descargue el perfil de configuración, puntee en **permitir**.  
    * **iOS 12,2 y versiones posteriores**: espere a que el perfil de terminar de descargar en Safari y luego pulse **realiza**. Luego, abra la aplicación de **configuración** del dispositivo.  

    > [!IMPORTANT]
    > Debe ir a la **configuración** aplicación e instalar este perfil en 8 minutos de descargarlo. Si no lo hace, se quitará el perfil y tendrá que reiniciar la inscripción. 

7. En el **configuración** aplicación, puntee en **instalar el perfil descargado** > **instalar**. Si **instalar el perfil descargado** no aparece como opción, vaya a **General** > **perfiles**. Si aún no ve el perfil, deberá descargarlo de nuevo.  

    ![Captura de pantalla de ejemplo de la aplicación de configuración de la opción de instalar el perfil descargado, con una notificación de rojo que indica un perfil recientemente descargado.](./media/ios-10-cp-enroll-1903.PNG)  
    
8. Si se le solicite, escriba la contraseña del dispositivo. A continuación, puntee en **instalar**.      

9. La pantalla siguiente es una advertencia estándar del sistema de administración de dispositivos. Para obtener más información sobre lo que su organización puede y no se puede ver en el dispositivo, consulte la correspondiente [artículo de docs Intune](what-info-can-your-company-see-when-you-enroll-your-device-in-Intune.md). Para continuar con la instalación, pulse **instalar**. Si se le pedirá que la administración remota de confianza, pulse **confianza**.  

    ![Captura de pantalla de ejemplo de aplicación de configuración, la pantalla de advertencia estándar del sistema para el certificado raíz y administración de dispositivos móviles.](./media/ios-15-cp-enroll-1903.PNG)  

10. Una vez completada la instalación, pulse **realiza**. Para comprobar que el perfil se ha instalado, vaya a la **Profiles & Device Management** configuración. Debería ver el perfil que se anuncie **administración de dispositivos móviles**.   

    ![Captura de pantalla de ejemplo de aplicación de configuración, administración de dispositivo y perfiles de configuración, que muestra el perfil de administración.](./media/ios-00-cp-enroll-1903.PNG)  


11. Vuelva a la aplicación **Portal de empresa de Intune**. Portal de empresa comenzará a sincronizar y configurar el dispositivo. Portal de empresa podría solicitarle que actualizar la configuración de dispositivo adicionales. Si lo hace, pulse **continuar**.

    ![Captura de pantalla de ejemplo de Portal de empresa, la pantalla "Configuración del acceso de", con un triángulo amarillo junto al requisito de configuración.](./media/ios-12-cp-enroll-1903.PNG)  

12. Sabrá que la instalación está completa cuando todos los elementos de la lista muestran un círculo verde. Pulse **Listo**.  
    
    ![Captura de pantalla de ejemplo de Portal de empresa, "todo listo!" pantalla, que muestra todos los círculos verdes.](./media/ios-13-cp-enroll-1903.PNG)  

> [!Note]
> Si la organización supervisa los límites de voz y datos, o le proporcionará un dispositivo propiedad de la empresa, puede que tenga unos pocos pasos más en completarse. Si se le pedirá que instale el **Datalert** aplicación, consulte [inscribir el dispositivo en la administración de gastos de telecomunicaciones](enroll-your-device-with-telecom-expense-management-ios.md). Si su organización es parte del programa de inscripción de dispositivos de Apple, puede averiguar [cómo inscribir el dispositivo de la empresa](enroll-your-device-dep-ios.md).  

## <a name="next-steps"></a>Pasos siguientes  
Buscar aplicaciones que le ayudará en el trabajo o escuela. Obtenga información sobre [cómo las aplicaciones se ponen a disposición](use-managed-apps-on-your-device-ios.md) a través del Portal de empresa.  

¿Sigue necesitando ayuda? Póngase en contacto con el equipo de soporte técnico de su empresa. Puede encontrar su información de contacto en el [sitio web del Portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  
