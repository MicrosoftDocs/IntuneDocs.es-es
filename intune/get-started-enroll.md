---
title: "Introducción a la inscripción de dispositivos"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b595848d-c451-43ab-812d-b22e0170fb7a
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 36e658cebdfd23547e3c376124289046f81acc1f
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2017
---
# <a name="getting-started-enrolling-devices"></a>Introducción a la inscripción de dispositivos

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

![Dispositivo iOS que muestra la aplicación de portal de empresa. Se muestra la primera pantalla que se ha presentado al usuario para el proceso de inscripción.](/intune-user-help/media/ios-enroll-1a-comp-access-setup.png)

Microsoft Intune permite capacitar a los empleados con dispositivos móviles manteniendo protegidos los datos corporativos. Como los usuarios finales interactuarán con Intune en sus dispositivos en lugar de en la consola de administración, asegúrese de que está familiarizado con la experiencia de inscripción. De esta manera, puede combinar directivas de cumplimiento bien diseñadas con su experiencia para mostrar empatía con sus usuarios. Esto es especialmente importante porque los usuarios conocerán exactamente qué información puede ver como administrador:

## <a name="what-it-cannot-see"></a>Lo que el personal de TI no puede ver
* Historial de llamadas y exploración web
* Ubicación
* Correo electrónico personal
* Mensajes de texto
* Contactos
* Contraseñas de las cuentas personales
* Eventos del calendario
* Imágenes, ni siquiera lo que hay en la aplicación de fotos ni en el álbum de cámara

## <a name="what-it-can-see"></a>Lo que el personal de TI puede ver
* Modelo
* Número de serie
* Versión del sistema operativo
* Nombres de aplicación
* Propietario
* Nombre del dispositivo
* Fabricante (en el caso de dispositivos no fabricados por Apple)
* Número telefónico (para dispositivos de trabajo, el número completo. Para dispositivos personales, solo los cuatro últimos dígitos).

## <a name="how-do-i-enroll-a-device"></a>¿Cómo puedo inscribir un dispositivo?

Inscribir un dispositivo es la primera experiencia que tendrán muchos usuarios finales al acceder a los recursos corporativos. [Comprender esa experiencia](end-user-educate.md) puede ayudar a convertir una experiencia potencialmente desagradable en una mejor.

1. Abra **App Store** y busque **Portal de empresa de Intune**.
2. Descargue la aplicación **Portal de empresa de Microsoft Intune**.
3. Abra la aplicación **Portal de empresa**, escriba la dirección de correo electrónico del usuario de prueba y la contraseña y, después, pulse **Iniciar sesión**.
4. Actualice la contraseña temporal por una nueva.
5. En la página **Configuración de acceso a la empresa**, pulse **Inscripción de dispositivos**.
6. En la página **¿Por qué inscribir el dispositivo?**, lea sobre lo que un usuario puede hacer cuando inscribe su dispositivo y, después, pulse **Continuar**.
7. Revise una lista de qué acceso obtiene un usuario cuando se inscribe y, después, pulse **Continuar**.
8. Revise lo que los administradores de TI pueden y no pueden ver en un dispositivo y, después, pulse **Continuar**.
9. En la página **¿Qué ocurre después?**, lea lo que ocurre durante la inscripción y, después, pulse **Inscribir**.
10. En la página **Instalar perfil**, pulse **Instalar** y, después, escriba el código de acceso si se ha solicitado.
11. Pulse **Instalar**.
12. Pulse **Instalar** de nuevo para indicar que ha leído la advertencia.
13. En el elemento emergente de **advertencia**, pulse **Confiar**.
14. Cuando la pantalla cambie para indicar que el perfil ha terminado de instalarse, pulse **Listo**.
15. Se muestra un mensaje "Inscribiendo el dispositivo" en la pantalla y, después, se muestra que el dispositivo se ha inscrito correctamente. Aparecerá un elemento emergente pidiéndole que abra la página en el portal de empresa. Pulse **Abrir**.
16. Vuelva a la pantalla **Configuración de acceso a la empresa**. Si no tiene ninguna directiva de prueba configurada, entonces el dispositivo debe aparecer como conforme. Si tiene alguna directiva de prueba, entonces al pulsar **Conformidad de dispositivos** se mostrará que hay cosas que necesitan realizarse para que el dispositivo sea seguro.
