---
title: Inscripción de un dispositivo iOS o iPad con Portal de empresa de Intune y Entrust Datacard
description: Inscriba un dispositivo iOS o iPad y configure la autenticación de credenciales derivadas con Entrust Datacard.
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
ms.openlocfilehash: b976e9a47a56c7af1e754f5b5b0162410e278025
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75856399"
---
# <a name="set-up-ios-or-ipados-device-with-company-portal-and-entrust-datacard"></a>Configuración de dispositivos iOS o iPad con Portal de empresa y Entrust Datacard

Inscriba el dispositivo con la aplicación Portal de empresa de Intune para obtener acceso seguro desde el móvil a las aplicaciones, los archivos y el correo electrónico de la organización. Después de haber inscrito el dispositivo, se convierte en *administrado*. La organización puede asignar directivas y aplicaciones al dispositivo mediante un proveedor de administración de dispositivos móviles (MDM), como Intune.  

Durante la inscripción, también instalará una credencial derivada en el dispositivo. Su organización puede requerir que use la credencial derivada como método de autenticación al obtener acceso a los recursos o para firmar y cifrar los mensajes de correo electrónico. 

Es probable que necesite configurar una credencial derivada si usa una tarjeta inteligente para:  

* Iniciar sesión en las aplicaciones educativas o de trabajo, Wi-Fi y redes privadas virtuales (VPN)
* Firmar y cifrar correos electrónicos escolares o de trabajo mediante certificados S/MIME  

En este artículo, aprenderá lo siguiente:  

   * Inscriba un dispositivo móvil iOS o iPados con Portal de empresa de Intune.  
   * Obtener una credencial derivada del proveedor de credenciales derivadas de la organización, [Entrust Datacard](https://www.entrustdatacard.com/).  

### <a name="what-are-derived-credentials"></a>¿Cuáles son las credenciales derivadas?  
Una credencial derivada es un certificado que se deriva de las credenciales de la tarjeta inteligente y que se instala en el dispositivo. Le concede acceso remoto a los recursos de trabajo, a la vez que evita que usuarios no autorizados tengan acceso a información confidencial.  

Las credenciales derivadas se utilizan para: 
* Autentique a los estudiantes y empleados que inicien sesión en las aplicaciones escolares o de trabajo, Wi-Fi y VPN
* Firmar y cifrar correos electrónicos escolares o de trabajo con certificados S/MIME

Las credenciales derivadas son una implementación de las directrices del National Institute of Standards and Technology (NIST) para las credenciales derivadas de verificación de identidad personal (PIV) como parte de la publicación especial (SP) 800-157.  

## <a name="prerequisites"></a>Requisitos previos

 Para completar la inscripción, debe tener:

* Su tarjeta inteligente académica o proporcionada por el trabajo
* Acceso a un equipo o quiosco donde puede iniciar sesión con su tarjeta inteligente
* El dispositivo móvil
* La aplicación Portal de empresa de Intune para iOS y iPados instalados en el dispositivo  


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
    b. Puntee en **comenzar**.  

    ![Captura de pantalla de ejemplo de la pantalla Portal de empresa configurar el acceso a tarjetas inteligentes móviles.](./media/smart-card-info-intercede.png)

9. Cambie al dispositivo habilitado para tarjetas inteligentes y abra IdentityGuard. 
10. Busque el área de inicio de sesión de credenciales inteligentes y seleccione el botón de inicio de sesión.  
11. Cuando se le pida que seleccione un certificado, elija sus credenciales de tarjeta inteligente. Después, seleccione **Aceptar**. 
12. Escriba el PIN de la tarjeta inteligente.  
13. Se le pedirá que elija entre una lista de acciones. Seleccione la que le permita inscribirse para una credencial inteligente móvil derivada. El vínculo o el botón podría indicar que **me gustaría inscribirse en una credencial de tarjeta inteligente móvil derivada.**  
14. Seleccione que ha descargado e instalado correctamente la aplicación Smart Credential habilitada. A continuación, vaya a la pantalla siguiente.   
15. Escriba información acerca de las credenciales de tarjeta inteligente derivadas.  
    a. Como nombre de identidad, escriba cualquier nombre, como *Entrust derived CRED*.  
    b. En el menú desplegable, seleccione **Entrust IdentityGudard Mobile Smart Credential**.  
    c. Continúe en la pantalla siguiente. Verá un código QR con una contraseña numérica en él.  

16. Vuelva a su dispositivo móvil. En la Portal de empresa > pantalla **obtener código QR** , puntee en **continuar**. 

    ![Captura de pantalla de ejemplo de la pantalla Portal de empresa obtener código QR.](./media/get-qr-code-intercede.png)  
17. Pulse **usar cámara** > **Aceptar**.  

    ![Captura de pantalla de ejemplo de un mensaje de Portal de empresa, pidiéndole permiso para permitir el acceso a la cámara.](./media/allow-cp-camera-access-intercede.png)  
18. Digitalice la imagen del código QR que se encuentra en el dispositivo habilitado para tarjetas inteligentes.  
19. Escriba la contraseña numérica que aparece bajo el código QR.  

    ![Captura de pantalla de ejemplo de la pantalla Portal de empresa contraseña requerida, escriba el campo contraseña.](./media/enter-password-derived-credentials.png)   

20. Espere a que Portal de empresa termine de configurar el dispositivo.  


## <a name="next-steps"></a>Pasos siguientes  
Una vez completada la inscripción, tendrá acceso a los recursos de trabajo, como correo electrónico, Wi-Fi y cualquier aplicación que su organización esté disponible. Para obtener más información acerca de cómo obtener, buscar, instalar y desinstalar aplicaciones en el Portal de empresa consulte:

* [Administrar aplicaciones desde el sitio web del Portal de empresa](manage-apps-cpweb.md)  
* [Usar aplicaciones administradas en el dispositivo](use-managed-apps-on-your-device-ios.md)  

¿Aún necesita ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  
