---
title: Inscripción de dispositivos iOS o iPad con Portal de empresa de Intune y intervenir
description: Obtenga información sobre cómo inscribir un dispositivo iOS o iPad y configurar la autenticación de credenciales derivadas con intervenir.
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
ms.openlocfilehash: 2a2c3264b2894ad81a64e7aaa7d3697f069dbfbb
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75856294"
---
# <a name="set-up-ios-or-ipados-device-with-company-portal-and-intercede"></a>Configuración de dispositivos iOS o iPad con Portal de empresa y intervenir

Inscriba el dispositivo con la aplicación Portal de empresa de Intune para obtener acceso seguro desde el móvil a las aplicaciones, los archivos y el correo electrónico de la organización.  Después de haber inscrito el dispositivo, se convierte en *administrado*. La organización puede asignar directivas y aplicaciones al dispositivo mediante un proveedor de administración de dispositivos móviles (MDM), como Intune.  

Durante la inscripción, también instalará una credencial derivada en el dispositivo. Su organización puede requerir que use la credencial derivada como método de autenticación al obtener acceso a los recursos o para firmar y cifrar los mensajes de correo electrónico. 

Es probable que necesite configurar una credencial derivada si usa una tarjeta inteligente para:

* Iniciar sesión en las aplicaciones educativas o de trabajo, Wi-Fi y redes privadas virtuales (VPN)
* Firmar y cifrar correos electrónicos escolares o de trabajo mediante certificados S/MIME  

En este artículo, aprenderá lo siguiente:  

* Inscriba un dispositivo móvil iOS o iPados con Portal de empresa de Intune.  
* Obtenga una credencial derivada del proveedor de credenciales derivadas de su organización, [intervenir](https://www.intercede.com/).   


## <a name="what-are-derived-credentials"></a>¿Cuáles son las credenciales derivadas?  
Una credencial derivada es un certificado que se deriva de las credenciales de la tarjeta inteligente y que se instala en el dispositivo. Le concede acceso remoto a los recursos de trabajo, a la vez que evita que usuarios no autorizados tengan acceso a información confidencial.  

Las credenciales derivadas se utilizan para: 
* Autentique a los estudiantes y empleados que inicien sesión en las aplicaciones escolares o de trabajo, Wi-Fi y VPN
* Firmar y cifrar correos electrónicos escolares o de trabajo con certificados S/MIME  

Las credenciales derivadas son una implementación de las directrices del National Institute of Standards and Technology (NIST) para las credenciales derivadas de verificación de identidad personal (PIV) como parte de la publicación especial (SP) 800-157.  

## <a name="prerequisites"></a>Requisitos previos

 Para completar la inscripción, debe tener:

* Su tarjeta inteligente académica o proporcionada por el trabajo
* Acceso a un equipo o quiosco de autoservicio donde puede iniciar sesión con su tarjeta inteligente
* Dispositivo móvil
* La aplicación Portal de empresa de Intune para iOS y iPados instalados en el dispositivo


## <a name="enroll-device"></a>Inscribir un dispositivo  
1. Abra la aplicación Portal de empresa para iOS/iPados en el dispositivo móvil e inicie sesión con su cuenta profesional.  
2. Anote el código que aparece en la pantalla.  

    ![Imagen de ejemplo de Portal de empresa aplicación con el código y el mensaje en pantalla.](./media/copy-code-intercede.png)  
1. Cambie al dispositivo habilitado para tarjetas inteligentes y vaya a https://microsoft.com/devicelogin. 

1. Escriba el código que anotó anteriormente.
 
2. Inserte la tarjeta inteligente para iniciar sesión.   

3. Vuelva a la aplicación Portal de empresa en el dispositivo móvil y siga las instrucciones en pantalla para inscribir el dispositivo.  
4. Una vez completada la inscripción, Portal de empresa le notificará para que configure la tarjeta inteligente. Pulse en la notificación. Si no recibe una notificación, consulte el correo electrónico.   

    ![Captura de pantalla de ejemplo de la Portal de empresa notificación de extracción en la pantalla principal del dispositivo.](./media/action-required-in-app-intercede.png)  

5. En la pantalla **configuración de acceso a tarjetas inteligentes móviles** :  
    a. Puntee en el vínculo a las instrucciones de configuración de su organización. Si su organización no proporciona instrucciones adicionales, se le enviará a este artículo.  
    b. Puntee en **comenzar**.  

    ![Captura de pantalla de ejemplo de la pantalla Portal de empresa configurar el acceso a tarjetas inteligentes móviles.](./media/smart-card-info-intercede.png)  

6. Cambie al dispositivo habilitado para tarjeta inteligente o al quiosco de autoservicio y abra la aplicación MyID. Inicie sesión con sus credenciales de trabajo.  
7. Seleccione la opción para solicitar su identificador. 
8. Cuando se le pregunte qué perfil desea usar, seleccione la opción para activar con una credencial móvil. Aparece un código QR.  
9. Vuelva a su dispositivo móvil. En la Portal de empresa > pantalla **obtener código QR** , puntee en **continuar**.  

    ![Captura de pantalla de ejemplo de la pantalla Portal de empresa obtener código QR.](./media/get-qr-code-intercede.png) 
 
10. Pulse **usar cámara** > **Aceptar**.  

    ![Captura de pantalla de ejemplo de un mensaje de Portal de empresa, pidiéndole permiso para permitir el acceso a la cámara.](./media/allow-cp-camera-access-intercede.png)  

11. Digitalice la imagen del código QR que se encuentra en el dispositivo habilitado para tarjetas inteligentes. 
12. Espere a que Portal de empresa termine de configurar el dispositivo.  

## <a name="next-steps"></a>Pasos siguientes  
Una vez completada la inscripción, tendrá acceso a los recursos de trabajo, como correo electrónico, Wi-Fi y cualquier aplicación que su organización esté disponible. Para obtener más información acerca de cómo obtener, buscar, instalar y desinstalar aplicaciones en el Portal de empresa consulte:

* [Administrar aplicaciones desde el sitio web del Portal de empresa](manage-apps-cpweb.md)  
* [Usar aplicaciones administradas en el dispositivo](use-managed-apps-on-your-device-ios.md)  

¿Aún necesita ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
