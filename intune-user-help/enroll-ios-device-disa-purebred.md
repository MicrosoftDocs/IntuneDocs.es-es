---
title: Inscripción de un dispositivo iOS o iPad con Portal de empresa de Intune y DISA purebred
description: Obtenga información sobre cómo inscribir un dispositivo iOS o iPad y configurar la autenticación de credenciales derivadas con DISA purebred.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilver
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 31858828cbbfaa1ca71d94f6e0f568c35bb490c1
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75856586"
---
# <a name="set-up-ios-or-ipados-device-with-company-portal-and-disa-purebred"></a>Configuración de dispositivos iOS o iPad con Portal de empresa y DISA purebred  

Inscriba el dispositivo con la aplicación Portal de empresa de Intune para obtener acceso seguro desde el móvil a las aplicaciones, los archivos y el correo electrónico de la organización. Después de haber inscrito el dispositivo, se convierte en *administrado*. La organización puede asignar directivas y aplicaciones al dispositivo mediante un proveedor de administración de dispositivos móviles (MDM), como Intune.  

Durante la inscripción, también instalará una credencial derivada en el dispositivo. Su organización puede requerir que use la credencial derivada como método de autenticación al obtener acceso a los recursos o para firmar y cifrar los mensajes de correo electrónico. 

Es probable que necesite configurar una credencial derivada si usa una tarjeta inteligente para:

* Iniciar sesión en las aplicaciones educativas o de trabajo, Wi-Fi y redes privadas virtuales (VPN)
* Firmar y cifrar correos electrónicos escolares o de trabajo mediante certificados S/MIME  

En este artículo, aprenderá lo siguiente:  

   * Inscriba un dispositivo móvil iOS o iPados con Portal de empresa de Intune.  
   * Obtenga una credencial derivada del proveedor de credenciales derivadas de su organización, [DISA purebred](https://cyber.mil/pki-pke/purebred/).  

## <a name="what-are-derived-credentials"></a>¿Cuáles son las credenciales derivadas?  
Una credencial derivada es un certificado que se deriva de las credenciales de la tarjeta inteligente y que se instala en el dispositivo. Le concede acceso remoto a los recursos de trabajo, a la vez que evita que usuarios no autorizados tengan acceso a información confidencial.  

Las credenciales derivadas se utilizan para: 
* Autentique a los estudiantes y empleados que inicien sesión en las aplicaciones escolares o de trabajo, Wi-Fi y VPN
* Firmar y cifrar correos electrónicos escolares o de trabajo con certificados S/MIME

Las credenciales derivadas son una implementación de las directrices del National Institute of Standards and Technology (NIST) para las credenciales derivadas de verificación de identidad personal (PIV) como parte de la publicación especial (SP) 800-157.  

## <a name="prerequisites"></a>Requisitos previos

 Para completar la inscripción, debe tener:

* Su tarjeta inteligente académica o proporcionada por el trabajo
* Acceso a un equipo o quiosco donde puede iniciar sesión con su tarjeta inteligente
* Dispositivo móvil
* La aplicación Portal de empresa de Intune para iOS y iPados instalados en el dispositivo   

También necesitará ponerse en contacto con un agente o representante de purebred durante la instalación.      

## <a name="enroll-device"></a>Inscribir un dispositivo  
1. Abra la aplicación Portal de empresa para iOS/iPados en el dispositivo móvil e inicie sesión con su cuenta profesional.  

2. Anote el código en pantalla.  

    ![Imagen de ejemplo de Portal de empresa aplicación con el código y el mensaje en pantalla.](./media/copy-code-intercede.png)  
3. Cambie al dispositivo habilitado para tarjetas inteligentes y vaya a https://microsoft.com/devicelogin. 
4. Escriba el código que anotó anteriormente.  

    ![Captura de pantalla de ejemplo del sitio web de Portal de empresa "escribir código".](./media/enter-code-intercede.png)   

5. Inserte la tarjeta inteligente para iniciar sesión.  
6. Vuelva a la aplicación Portal de empresa en el dispositivo móvil y siga las instrucciones en pantalla para inscribir el dispositivo.  
7. Una vez completada la inscripción, Portal de empresa le notificará para que configure la tarjeta inteligente. Pulse en la notificación. Si no recibe una notificación, consulte el correo electrónico.   

    ![Captura de pantalla de ejemplo de la Portal de empresa notificación de extracción en la pantalla principal del dispositivo.](./media/action-required-in-app-intercede.png)  
8. En la pantalla **configuración de acceso a tarjetas inteligentes móviles** :  
    a. Puntee en el vínculo a las instrucciones de configuración de su organización. Si su organización no proporciona instrucciones adicionales, se le enviará a este artículo.  
    b. Haga clic en **abrir** para abrir la aplicación purebred.  

    ![Captura de pantalla de ejemplo de la pantalla Portal de empresa configurar el acceso a tarjetas inteligentes móviles.](./media/smart-card-open-disa-purebred.png)  
9. Cuando se le pida que permita Portal de empresa para abrir la aplicación de registro purebred, seleccione **abrir**.   

    ![Captura de pantalla de ejemplo de la solicitud de Portal de empresa para abrir la aplicación purebred de DISA.](./media/open-app-prompt-disa-purbred.png)  
10. Cuando la aplicación funcione, trabaje con el agente de purebred de su organización para configurar y descargar el perfil de configuración de inscripción previa de purebred.   
11. Vaya a la aplicación Configuración > **General** > **perfiles & administración de dispositivos** > **Perfil de instalación** y pulse **instalar**.  
12. Escriba el código de acceso del dispositivo.  
13. Instale el perfil. Es posible que tenga que pulsar **instalar** más de una vez para iniciar la instalación. 
14. Vuelva a la aplicación de registro purebred. Siga las instrucciones del agente de purebred para continuar.  
 
15. Después de descargar el perfil de configuración, vaya a la aplicación Configuración > **General** > **perfiles & administración de dispositivos** > Perfil de **instalación** y pulse **instalar**.   
16.  Escriba el código de acceso del dispositivo.
17. Instale el perfil. Es posible que tenga que pulsar **instalar** más de una vez para iniciar la instalación. 
18. Una vez finalizada la instalación, vuelva a la aplicación Portal de empresa.  
19.  En la pantalla **configuración de acceso a tarjetas inteligentes móviles** , puntee en **continuar**.  

20. En la pantalla **importar certificados** , recuperará e importará las credenciales derivadas que recibió de DISA purebred.  

    a. Pulse **Continuar**.   

    ![captura de pantalla de ejemplo de la pantalla Portal de empresa establecer certificados de importación.](./media/import-certificate-disa-purebred.png)  
    b. Vaya a la unidad de iCloud **examinar** > **ubicaciones** y puntee en **más ubicaciones**.  

    ![captura de pantalla de ejemplo de la unidad iCloud, en el menú examinar se resalta la opción más ubicaciones.](./media/icloud-drive-more-locations.png)  
    c. Pulse el conmutador para habilitar la **cadena de claves de purebred**.  

    ![Captura de pantalla de ejemplo de la unidad iCloud, examinar vista, resaltando que el modificador de la cadena de claves purebred está habilitado.](./media/icloud-drive-enable-purebred-keychain.png)   

    d. Puntee en **paquete de credenciales de purebred**.  

    ![captura de pantalla de ejemplo de una pantalla de iOS con una opción de paquete de credenciales purebred seleccionable.](./media/purebred-credential-package.png)  
    f. Aparece una lista de certificados. Seleccione uno y, a continuación, puntee en **Importar clave**.  

    ![Captura de pantalla de ejemplo de una lista de certificados seleccionables, con uno ya seleccionado.](./media/import-purebred-keychain.png) 
21. Vuelva a la aplicación Portal de empresa y espere a que Portal de empresa termine de configurar el dispositivo.   

## <a name="next-steps"></a>Pasos siguientes  
Una vez completada la inscripción, tendrá acceso a los recursos de trabajo, como correo electrónico, Wi-Fi y cualquier aplicación que su organización esté disponible. Para obtener más información acerca de cómo obtener, buscar, instalar y desinstalar aplicaciones en el Portal de empresa consulte:

* [Administrar aplicaciones desde el sitio web del Portal de empresa](manage-apps-cpweb.md)  
* [Usar aplicaciones administradas en el dispositivo](use-managed-apps-on-your-device-ios.md)  

¿Aún necesita ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
