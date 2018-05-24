---
title: Quitar el dispositivo Windows de Intune
description: Describe cómo quitar un dispositivo Windows de Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 018bda65-7238-41f5-b92a-e5f67b7fe085
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: a3cad6a73b3455790441c594933d599b2c6e89f9
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="remove-your-windows-device-from-intune-management"></a>Quitar el dispositivo Windows de la administración de Intune

Quite un dispositivo Windows registrado de Intune cuando ya no quiera ni necesite:  
* Usar el dispositivo para el trabajo o la escuela. 
* Acceder al correo, las aplicaciones u otros recursos profesionales o educativos.

Después de quitarlo, no podrá acceder a los recursos profesionales ni educativo desde el dispositivo. Entre los dispositivos de Windows que se pueden quitar de Intune se incluyen:  
* Dispositivos Windows 10 
* Equipos Windows 8.1
* Dispositivos móviles Windows 8.1
 
Para más información sobre lo que sucede cuando Intune deja de administrar el dispositivo, consulte [¿Qué ocurre si anula la inscripción del dispositivo Windows de Intune?](what-happens-if-you-unenroll-your-device-from-intune-windows.md)

## <a name="remove-your-windows-10-device"></a>Quitar un dispositivo con Windows 10
Complete estos pasos para quitar un dispositivo Windows 10 de Intune.

### <a name="via-the-company-portal-app"></a>A través de la aplicación Portal de empresa

1. Abra la aplicación del portal de empresa.
2. Inicie sesión con las credenciales de su trabajo o escuela.
3. En **Mis dispositivos**, seleccione el dispositivo que desea quitar.
4. En la esquina superior de la derecha de la aplicación, seleccione el icono **Más información**.
5. Seleccione **Quitar**. 
6. Para confirmar la eliminación del dispositivo, seleccione **Quitar dispositivo**.

### <a name="via-device-settings-app"></a>A través de la aplicación de configuración del dispositivo
1. Abra la aplicación de configuración. 
2. Vaya a **Cuentas** > **Obtener acceso a trabajo o escuela**.
3. Seleccione la cuenta conectada que desea quitar > **Desconectar**.
4. Para confirmar la eliminación del dispositivo, seleccione **Sí**.

## <a name="remove-your-windows-81-computer"></a>Quitar un equipo con Windows 8.1
Complete estos pasos para quitar un equipo Windows 8.1 de Intune.

1.  Vaya a **Configuración de PC** > **Red** > **Área de trabajo**.
2.  En **Workplace Join**, seleccione **Salir**.
3.  En **Activar la administración de dispositivos**, seleccione **Desactivar**.
4.  En la ventana emergente que se abre, seleccione **Desactivar**.

## <a name="remove-your-windows-81-mobile-device"></a>Quitar un dispositivo móvil Windows Phone 8.1
Complete estos pasos para quitar un dispositivo móvil Windows 8.1 de Intune.

1.  Vaya a **Configuración** > **Área de trabajo**.
2.  Pulse la cuenta de trabajo cuya inscripción quiere anular.
3.  Pulse en **Eliminar** en la parte inferior de la pantalla.
4.  En el cuadro de diálogo **Eliminar cuenta**, pulse en **Eliminar**.  
## <a name="removing-your-personal-information-after-removing-the-company-portal"></a>Eliminar la información personal después de quitar el Portal de empresa
Hay dos tipos de datos que el Portal de empresa almacena en el dispositivo Windows:

-   **Registros de diagnóstico**: datos de actividad de la aplicación estándar que recopila Microsoft. Se borran automáticamente cuando desinstala la aplicación Portal de empresa. Los datos de actividad de la aplicación son, por ejemplo, los que indican cuánto tiempo estuvo abierta la aplicación o si se bloqueó.
-   **Caché de la aplicación**: archivos auxiliares necesarios para el funcionamiento de la aplicación, como iconos y valores de configuración.

Para eliminar los registros almacenados y la memoria caché, siga uno de esos pasos:

* [Desinstale la aplicación Portal de empresa](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs) 

* Restablezca la aplicación Portal de empresa. Abra la aplicación **Configuración** y seleccione > **Aplicaciones** > **Portal de empresa** > **Opciones avanzadas** > **Restablecer**. 

¿Sigue necesitando ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://portal.manage.microsoft.com#HelpDeskDialog).
