---
title: Inscribir su Mac con Portal de empresa de Intune | Microsoft Docs
description: Obtenga información sobre cómo inscribir su Mac en Intune con la aplicación Portal de empresa.
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: kakyker
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: e04950a67938d883b0762c03efa371fcb74d0731
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75855483"
---
# <a name="enroll-your-macos-device-using-the-company-portal-app"></a>Inscripción del dispositivo macOS mediante la aplicación Portal de empresa  

Inscriba un dispositivo macOS con la aplicación Portal de empresa de Intune para obtener acceso seguro a las aplicaciones, los archivos y la dirección de correo electrónico profesional o educativa de su organización.

Normalmente, las organizaciones requieren la inscripción de su dispositivo antes de poder acceder a los datos de su propiedad. Después de haber inscrito el dispositivo, se convierte en *administrado*. La organización puede asignar directivas y aplicaciones al dispositivo mediante un proveedor de administración de dispositivos móviles (MDM), como Intune. Para obtener acceso continuo a la información profesional o educativa del dispositivo, debe configurarlo para que coincida con la configuración de directiva de su organización.  

En este artículo se describe cómo usar la aplicación Portal de empresa para que macOS inscriba, configure y mantenga su dispositivo para que cumpla los requisitos de su organización.  


## <a name="what-to-expect-from-the-company-portal-app"></a>Qué esperar de la aplicación Portal de empresa

Durante la instalación inicial, la aplicación Portal de empresa requiere que inicie sesión y se autentique con su organización. Portal de empresa le informa de cualquier configuración de dispositivo que necesite configurar para satisfacer los requisitos de su organización. Por ejemplo, las organizaciones suelen definir requisitos de caracteres mínimos o máximos para las contraseñas que tendrá que cumplir.    

Después de inscribir el dispositivo, Portal de empresa siempre se asegurará de que el dispositivo esté protegido según los requisitos de su organización. Por ejemplo, si instala una aplicación desde un origen que no es de confianza, Portal de empresa le avisará y podría restringir el acceso a los recursos de su organización. Las directivas de protección de aplicaciones como esta son comunes. Para recuperar el acceso, es probable que necesite desinstalar la aplicación que no es de confianza. 

Si después de la inscripción, la organización exige un nuevo requisito de seguridad, como la autenticación multifactor, Portal de empresa se lo notificará. Tendrá la oportunidad de ajustar la configuración para poder seguir trabajando desde su dispositivo.  

Para obtener más información sobre la inscripción, vea [¿Qué ocurre si instalo la aplicación de Portal de empresa e inscribo el dispositivo?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md).  

## <a name="get-your-macos-device-managed"></a>Cómo administrar el dispositivo macOS  
Siga estos pasos para inscribir su dispositivo macOS con su organización. El dispositivo debe ejecutar macOS 10,12 o posterior.   

> [!NOTE]
> A lo largo de este proceso, es posible que se le pida que permita a Portal de empresa usar información confidencial almacenada en la cadena de claves. Estos mensajes forman parte de la seguridad de Apple. Cuando reciba el mensaje, escriba la contraseña de la cadena de inicio de sesión y seleccione **permitir siempre**. Si presiona **entrar** o **retorno** en el teclado, el símbolo del sistema seleccionará **permitir**, lo que puede dar lugar a mensajes adicionales.  

### <a name="install-company-portal-app"></a>Instalar la aplicación Portal de empresa  
1. Vaya a [inscribir mi Mac](https://go.microsoft.com/fwlink/?linkid=853070).  
2. Se descargará el archivo Portal de empresa Installer. pkg. Abra el instalador y continúe con los pasos. 
3. Acepte el contrato de licencia de software. 
4. Escriba la contraseña del dispositivo o la huella digital registrada para instalar el software.  
5. Abra Portal de empresa. 

> [!IMPORTANT]
> Microsoft AutoUpdate puede abrirse para actualizar el software de Microsoft. Una vez instaladas todas las actualizaciones, abra la aplicación Portal de empresa. Para obtener la mejor experiencia de instalación, instale las versiones más recientes de Microsoft AutoUpdate y Portal de empresa.  


### <a name="enroll-your-mac"></a>Inscribir su Mac  


1. Inicie sesión en el Portal de empresa con su cuenta profesional o educativa.  
2. Cuando se abra la aplicación, seleccione **comenzar**.  
3. Revise lo que su organización puede y no puede ver en el dispositivo inscrito. Luego, seleccione **Continue** (Continuar).
4.  Si se le solicita, escriba la contraseña del dispositivo en la pantalla **instalar el perfil de administración** .

    ![Captura de pantalla de ejemplo de Portal de empresa, instalar la pantalla de Perfil de administración, resaltando la solicitud de contraseña.](./media/install-management-profile-macos-1912.PNG)   
5. En la pantalla **confirmar la administración de dispositivos** , seleccione **abrir preferencias del sistema**.  

    ![Captura de pantalla de ejemplo de la pantalla confirmar la administración de dispositivos, resaltando el botón "abrir preferencias del sistema".](./media/confirm-device-management-macos-1912.PNG)  
6. Se abrirán las preferencias del sistema del dispositivo. Seleccione **Perfil de administración** en la lista perfiles de dispositivo y, a continuación, seleccione **aprobar** > **aprobar**.  
    ![captura de pantalla de ejemplo de preferencias del sistema, pantalla de Perfil de administración, resaltando el botón "aprobar".](./media/management-profile-approve-macos-1912.PNG)   
1. Vuelva a Portal de empresa y seleccione **continuar**.    
2. Su organización podría requerir que actualice la configuración del dispositivo. Cuando haya terminado de actualizar la configuración, seleccione **Comprobar configuración**.  

    ![Captura de pantalla de ejemplo de Portal de empresa, actualizar la pantalla de configuración del dispositivo, resaltando el botón "Comprobar configuración".](./media/update-settings-mac-1911.PNG)  
9. Una vez finalizada la instalación, seleccione **listo**.  


 ## <a name="troubleshooting-and-feedback"></a>Solución de problemas y comentarios   

Si surgen problemas durante la inscripción, vaya a **ayuda** > **Enviar informe de diagnóstico** para informar del problema a los desarrolladores de aplicaciones de Microsoft. Esta información se usa para ayudar a mejorar la aplicación. También usarán esta información para ayudar a resolver el problema si el personal de soporte técnico de ti llega a ellos para obtener ayuda.  

Después de notificar el problema a Microsoft, puede enviar los detalles de su experiencia al personal de soporte técnico de ti. Seleccione los **detalles del correo electrónico**. Escriba lo que experimentó en el cuerpo del mensaje de correo electrónico. Para encontrar la dirección de correo electrónico del personal de soporte técnico, vaya a la Portal de empresa aplicación > **contacto**. O bien compruebe el [sitio web Portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  
 

Además, el equipo de Portal de empresa de Microsoft Intune le encantaría oír sus comentarios. Vaya a **ayuda** > **Enviar comentarios** para compartir sus ideas e ideas.  

## <a name="unverified-profiles"></a>Perfiles sin comprobar  
Cuando se consultan los perfiles de administración de dispositivos móviles (MDM) instalados en **Preferencias del sistema** > **Perfiles**, algunos perfiles podrían mostrar un estado Sin comprobar. Mientras el perfil de administración muestre un estado Comprobado, no tiene por qué preocuparse.  

El perfil de administración es lo que define la conexión del canal de MDM. Mientras se compruebe el perfil de administración, cualquier otro perfil entregado a la máquina a través de ese canal, hereda las características de seguridad del perfil de administración.  

## <a name="updating-the-company-portal-app"></a>Actualización de la aplicación del Portal de empresa

La actualización de la aplicación del Portal de empresa se realiza del mismo modo que la de cualquier otra aplicación de Office, a través de Microsoft AutoUpdate para macOS. Obtenga más información sobre cómo [actualizar aplicaciones de Microsoft para macOS](https://support.office.com/article/Check-for-Office-for-Mac-updates-automatically-bfd1e497-c24d-4754-92ab-910a4074d7c1).  

## <a name="next-steps"></a>Pasos siguientes  
¿Aún necesita ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  


