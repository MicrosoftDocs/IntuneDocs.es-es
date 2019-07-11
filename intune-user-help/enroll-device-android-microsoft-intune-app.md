---
title: Inscribir dispositivos corporativos con la aplicación Microsoft Intune | Microsoft Docs
description: Explica cómo inscribir un dispositivo corporativo Android en Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: b23323766e91e31c48aec6a51dfae971c3a333e8
ms.sourcegitcommit: 1dc9d4e1d906fab3fc46b291c67545cfa2231660
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735746"
---
# <a name="enroll-your-corporate-device-with-the-microsoft-intune-app"></a>Inscribir dispositivos corporativos con la aplicación Microsoft Intune

Inscriba el dispositivo corporativo Android para obtener acceso seguro al correo electrónico, las aplicaciones y otros datos corporativos que la organización ponga a su disposición. La aplicación Microsoft Intune es compatible con los dispositivos corporativos con Android 6.0 y posterior. Se instala automáticamente en dispositivos nuevos y restablecidos de fábrica durante la inscripción. 

Hay cuatro maneras de inscribir. La organización debe indicarle qué opción usar.
 
* Transmisión de datos en proximidad (NFC)  
* Token  
* Código QR   
* Google Zero Touch  

## <a name="enroll-device"></a>Inscribir un dispositivo 
Siga estos pasos para configurar e inscribir el dispositivo.  

> [!NOTE]
> El fabricante del dispositivo o la versión Android pueden requerir que realice otros pasos que no se tratan en este procedimiento. Los colores y el texto que ve en las capturas de pantalla también pueden ser distintos en el dispositivo.  

1. Encienda el dispositivo nuevo o restablecido de fábrica.  
2. En la pantalla **Bienvenida**, seleccione su idioma.   Si se le ha indicado que se inscriba con un código QR o NFC, siga el paso siguiente que coincida con el método.  
     * NFC: coloque el dispositivo compatible con NFC contra un dispositivo de programador para conectarse a la red de la organización. Siga los mensajes en pantalla. Cuando llegue a la pantalla de los términos del servicio de Chrome, vaya al paso 5.  

     * Código QR: siga los pasos de [Inscripción de código QR](#qr-code-enrollment).  

     Si se le ha indicado que use otro método, vaya al paso 3.    

1. Conéctese a Wi-Fi y pulse **SIGUIENTE**. Siga el paso que coincide con el método de inscripción. 

    * Token: cuando llegue a la pantalla de inicio de sesión de Google, siga los pasos de [Inscripción de token](#token-enrollment).    
    * Google Zero Touch: después de conectarse a Wi-Fi, la organización reconoce el dispositivo. Vaya al paso 4 y siga los mensajes en pantalla hasta que finalice la instalación.    
 
       ![Imagen de ejemplo de la pantalla de términos de Google que se ve si se usa Google Zero Touch con el botón Aceptar y continuar resaltado.](./media/google-zero-touch-intune-app-01.png)   
   
4. Revise los términos de Google. Luego pulse **ACEPTAR Y CONTINUAR**.  

      ![Imagen de ejemplo de la pantalla de términos de Google con el botón Aceptar y continuar resaltado.](./media/fully-managed-intune-app-04.png)   

6. Revise los términos del servicio de Chrome. Luego pulse **ACEPTAR Y CONTINUAR**.  

   ![Imagen de ejemplo de la pantalla de términos del servicio de Chrome con el botón Aceptar y continuar resaltado.](./media/fully-managed-intune-app-06.png)   

7. En las pantallas de inicio de sesión, inicie sesión con la cuenta profesional o educativa.   

    a. Escriba el correo electrónico y pulse **Siguiente**.      
    b. Escriba la contraseña y pulse **Iniciar sesión**.  

8. Según los requisitos de la organización, es posible que se le pida que actualice la configuración, por ejemplo, el bloqueo de pantalla o el cifrado. Si ve estos mensajes, pulse **ESTABLECER** y siga las instrucciones en pantalla.  

   ![Imagen de ejemplo de configuración de la pantalla del teléfono profesional con el botón Establecer resaltado.](./media/fully-managed-intune-app-10.png)   

9. Para instalar aplicaciones profesionales en el dispositivo, pulse **INSTALAR**. Cuando termine la instalación, pulse **SIGUIENTE**.  

   ![Imagen de ejemplo de configuración de la pantalla del teléfono profesional con el botón Instalar resaltado.](./media/fully-managed-intune-app-11.png)   

10. Cuando reciba el mensaje de que el dispositivo está listo, pulse **LISTO**. 

11. Vaya a las aplicaciones y abra la aplicación Microsoft Intune. Seleccione **INICIAR SESIÓN**. 

12. En la pantalla **Setup access** (Acceso a configuración), se ve una lista de tareas pendientes. Pulse **CONTINUAR**.  

       ![Imagen de ejemplo de la aplicación Microsoft Intune y la pantalla de acceso a configuración con las tareas pendientes.](./media/fully-managed-intune-app-14.png)   

13. Una vez terminado el registro del dispositivo, pulse **CONTINUAR**. Microsoft Intune puede pedirle que actualice otras configuraciones del dispositivo.   

       ![Imagen de ejemplo de la aplicación Microsoft Intune y la pantalla de configuración del dispositivo Actualizar.](./media/fully-managed-intune-app-15-2.png)   

14. La configuración ha terminado cuando todos los elementos de la lista muestran un círculo verde. Ya se puede acceder a los recursos de la empresa.  

       ![Imagen de ejemplo de la aplicación Microsoft Intune y la pantalla de acceso de configuración con las tareas terminadas.](./media/fully-managed-intune-app-16.png)   


## <a name="qr-code-enrollment"></a>Inscripción de código QR  
En esta sección se digitaliza el código QR proporcionado por la empresa.  Cuando termina, se le vuelve a redirigir a los pasos de inscripción del dispositivo.     
  
1. En la pantalla de **bienvenida**, pulse cinco veces para iniciar la configuración del código QR.  

   ![Imagen de ejemplo de la pantalla de bienvenida de instalación del dispositivo con las instrucciones de pulsar la pantalla resaltadas.](./media/qr-code-intune-app-01.png)  

2. Siga las instrucciones en pantalla para conectarse a Wi-Fi.  
3. Si el dispositivo no tiene un escáner de código QR, las pantallas de instalación muestran el progreso como un escáner en proceso de instalación. Espere a que la instalación se complete.  
4. Cuando se le pida, digitalice el código QR del perfil de inscripción que le ha proporcionado la organización.  
5. Vuelva al paso 4 de [Inscribir un dispositivo](#enroll-device) para continuar con la instalación.  

## <a name="token-enrollment"></a>Inscripción de token  
En esta sección se especifica el token proporcionado por la empresa. Cuando termina, se le vuelve a redirigir a los pasos de inscripción del dispositivo.  

1. En la pantalla de inicio de sesión de Google, en el cuadro **Correo electrónico o teléfono**, escriba **afw#setup**. Pulse **Siguiente**. 

   ![Imagen de ejemplo de la pantalla de inicio de sesión de Google con "afw#setup" escrito en el campo.](./media/token-intune-app-01.png)   

2. Seleccione **Instalar** para la aplicación **Android Device Policy** (Directiva de dispositivo Android). Continúe con la instalación. Según el dispositivo, es posible que deba revisar y aceptar más términos.    

3. En la pantalla **Inscribir este dispositivo**, seleccione **Siguiente**.  

   ![Imagen de ejemplo de la pantalla Inscribir este dispositivo. Muestra la ilustración de un código QR con el botón Siguiente resaltado.](./media/token-intune-app-02.png)  

4. Seleccione **Escribir código**.

   ![Captura de pantalla de ejemplo de un escáner de código QR activo. El botón Escribir código está resaltado.](./media/token-intune-app-03.png)  

5. En la pantalla **Scan or enter code** (Digitalizar o escribir código), escriba el código que le ha proporcionado la organización.  A continuación, haga clic en **Siguiente**.  

   ![Imagen de ejemplo de la pantalla Scan or enter code (Digitalizar o escribir código) con el botón Siguiente resaltado.](./media/token-intune-app-04.png)  

6. Vuelva al paso 4 de [Inscribir un dispositivo](#enroll-device) para continuar con la instalación.  



## <a name="next-steps"></a>Pasos siguientes   
¿Sigue necesitando ayuda? Póngase en contacto con el equipo de soporte técnico de su empresa (visite el [sitio web del Portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980) para obtener la información de contacto), o escriba al <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">equipo de Microsoft Android</a>.  
