---
title: Inscribir el dispositivo Windows 10 en el Portal de empresa de Intune | Microsoft Docs
description: Pasos para inscribir dispositivos Windows 10 en el Portal de empresa de Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/11/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 812e82df-76df-402b-bfe9-29302838f40e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4eb5dbb150559de7ad30a598fb78a4fa78033c42
ms.sourcegitcommit: fdc6261f4ed695986e06d18353c10660a4735362
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2019
ms.locfileid: "58069373"
---
# <a name="enroll-windows-10-devices-with-intune-company-portal"></a>Inscribir dispositivos Windows 10 con el Portal de empresa de Intune

Usar el Portal de empresa de Intune para inscribir su dispositivo Windows 10 bajo la administración de su organización. En este artículo se describe cómo inscribir dispositivos con Windows 10 versión 1607 y posteriores y Windows 10 versión 1511 y versiones anterior. Antes de comenzar, asegúrese de [comprobar la versión del dispositivo](windows-enrollment-company-portal.md#find-windows-10-version-number) por lo que puede seguir los pasos correctos.  

Windows 10 es compatible entre distintos tipos de dispositivo, incluidos el escritorio, teléfono y tableta. Los pasos de inscripción son los mismos en cualquier dispositivo que esté usando. Sin embargo, la pantalla puede ser un poco diferente de las imágenes mostradas en este artículo.  

> [!VIDEO https://channel9.msdn.com/Series/IntuneEnrollment/Windows-Enrollment/player]  

## <a name="enroll-windows-10-version-1607-and-later-device"></a>Inscripción de Windows 10 versión 1607 y dispositivos posteriores 
Estos pasos describen cómo inscribir un dispositivo que se ejecuta en Windows 10, versión 1607 y posteriores.  

1. Vaya a **Inicio**. Si se encuentra en un dispositivo Windows 10 Mobile, continúe con el **todas las aplicaciones** lista.

2. Abra la aplicación **Configuración**. Si la aplicación no está disponible en la lista de aplicaciones, vaya a la barra de búsqueda y escriba "configuración".

3. Seleccione **Cuentas** > **Obtener acceso a trabajo o escuela** > **Conectar**.  


    ![Seleccionar cuenta Obtener acceso a trabajo o escuela](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

4. Escriba la dirección de correo electrónico profesional o educativa y seleccione **Siguiente**.  


   ![Escriba su cuenta profesional o educativa](./media/w10-enroll-rs1-set-up-work-or-school-account.png)  

5. Inicie sesión en Intune con su cuenta profesional o educativa.  


    ![Agregar una cuenta profesional o educativa](./media/w10-enroll-rs1-enter-your-credentials.png)  

    Al final verá un mensaje en el que se indica que la empresa o escuela están registradas en el dispositivo.

6. Si su organización, deberá configurar un PIN para Windows Hello, se le pedirá que escriba un código de verificación. Escriba el código y continúe con los pasos que aparecen en pantalla para crear un PIN.  

7. En la pantalla **Todo listo** , seleccione **Listo**. El dispositivo ya está inscrito.  

8. Para comprobar la conexión, vuelva a **configuración** > **cuentas** > **acceso profesional o educativo**.  Ahora debería aparecer su cuenta.  


    ![Compruebe que la conexión se ha configurado correctamente](./media/w10-enroll-rs1-validate-successful-enrollment.png)  

¿Sigue sin poder acceder a su correo electrónico, archivos u otros datos profesionales o educativos? Obtenga información sobre cómo [solucionar problemas de la cuenta](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-access-work-or-school).  

## <a name="enroll-windows-10-version-1511-and-earlier-device"></a>Inscripción de Windows 10 versión 1511 y anterior dispositivo  
Estos pasos describen cómo inscribir un dispositivo que se ejecuta en Windows 10, versión 1511 y versiones anterior.  

1. Vaya a **Inicio**. Si se encuentra en un dispositivo Windows 10 Mobile, continúe con el **todas las aplicaciones** lista.

2. Abra la aplicación **Configuración**. Si la aplicación no está disponible en la lista de aplicaciones, vaya a la barra de búsqueda y escriba "configuración".

3. Seleccione **cuentas** > **su cuenta**.  


    ![Seleccionar la cuenta](./media/W10-enroll-2-accounts-your-account.png)  

5. Seleccione **Agregar una cuenta profesional o educativa**.  


    ![Seleccionar agregar una cuenta profesional o educativa](./media/w10-enroll-3-add-work-school-acct.png)  

6. Inicie sesión con las credenciales de su trabajo o escuela.  


    ![Iniciar sesión](./media/W10-enroll-4-sign-in.png)  

¿Sigue sin poder acceder a su correo electrónico, archivos u otros datos profesionales o educativos? Obtenga información sobre cómo [solucionar problemas de la cuenta](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-your-account).   

## <a name="next-steps"></a>Pasos siguientes  

Para obtener ayuda, póngase en contacto con soporte técnico de su empresa. Puede encontrar su organización información de TI en el [sitio Web del Portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980). Inicie sesión en el sitio con la cuenta profesional o educativa.  

 

