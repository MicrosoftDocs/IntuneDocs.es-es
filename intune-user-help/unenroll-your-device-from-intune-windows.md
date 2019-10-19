---
title: Quitar el dispositivo Windows de la administración de Intune
description: Describe cómo quitar un dispositivo Windows de la administración de Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 018bda65-7238-41f5-b92a-e5f67b7fe085
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: e64911ea9b1b1d3c619a82eac9dc78e4e78a53e9
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508131"
---
# <a name="remove-your-windows-device-from-management"></a>Quitar el dispositivo Windows de la administración

Quite un dispositivo Windows registrado de la administración cuando ya no quiera o no necesite:  
* Usar el dispositivo para el trabajo o la escuela. 
* Acceder al correo, las aplicaciones u otros recursos profesionales o educativos.

Después de cancelar la suscripción del dispositivo, perderá el acceso con este dispositivo a los recursos del trabajo o la escuela. Puede quitar los siguientes dispositivos Windows de administración.  
* Dispositivos Windows 10 
* Equipos Windows 8.1
* Teléfonos Windows 8.1
 
Para más información sobre lo que sucede cuando deja de administrar el dispositivo, vea [¿Qué ocurre si anula la inscripción del dispositivo Windows de Intune?](what-happens-if-you-unenroll-your-device-from-intune-windows.md)  

## <a name="remove-your-windows-10-device"></a>Quitar un dispositivo con Windows 10
Siga estos pasos para quitar un dispositivo Windows 10 de la administración.

### <a name="remove-in-company-portal-app-home-page"></a>Quitar desde la página **principal** de la aplicación Portal de empresa  

1. Abra la aplicación del portal de empresa.
2. En la **página principal**, vaya a la sección **Mis dispositivos**.
3. Seleccione el dispositivo que quiere quitar.
3. En la esquina superior de la derecha de la aplicación, seleccione el icono **Más información**.
4. Seleccione **Quitar**. 
5. Para confirmar la eliminación del dispositivo, seleccione **Quitar**.  

### <a name="remove-in-company-portal-app-device-context-menu"></a>Quitar desde el menú contextual del dispositivo de la aplicación Portal de empresa  

1. Abra la aplicación Portal de empresa y vaya a **Mis dispositivos**.

    ![Captura de pantalla de ejemplo de la página principal de la aplicación Portal de empresa para Windows, donde se resalta la sección Mis dispositivos.](./media/1809_CheckAccess_Context_Select_Device.png)

2. Haga clic con el botón derecho en un dispositivo o manténgalo pulsado para abrir el [menú contextual](https://docs.microsoft.com//windows/uwp/design/controls-and-patterns/menus).  

3. Seleccione **Quitar**.  

    ![Captura de pantalla de ejemplo de la página principal de la aplicación Portal de empresa para Windows. El menú contextual del dispositivo está visible en la sección **Mis dispositivos** de la página y muestra las acciones "Cambiar nombre", "Quitar" y "Comprobar acceso".](./media/1809_DeviceContextMenu_Windows_CP.png)  

5. En la confirmación, haga clic en **Más información** para leer cómo podría cambiar el acceso a los recursos del trabajo y la escuela. Para confirmar la eliminación del dispositivo, seleccione **Quitar**.   

     ![Captura de pantalla de ejemplo de la página principal de la aplicación Portal de empresa para Windows. El campo Cambiar nombre aparece sobre el dispositivo. Allí, el usuario puede escribir un nombre nuevo y hacer clic en Cambiar nombre o Cancelar.](./media/1808_RemoveDevice_Popup.png)  


### <a name="remove-in-device-settings-app"></a>Quitar a través de la aplicación de configuración del dispositivo
1. Abra la aplicación de configuración. 
2. Vaya a **Cuentas** > **Obtener acceso a trabajo o escuela**.
3. Seleccione la cuenta conectada que desea quitar > **Desconectar**.
4. Para confirmar la eliminación del dispositivo, seleccione **Sí**.

## <a name="remove-your-windows-81-computer"></a>Quitar un equipo con Windows 8.1
Complete estos pasos para quitar un equipo Windows 8.1 de Intune.

1. Vaya a **Configuración de PC** > **Red** > **Área de trabajo**.
2. En **Workplace Join**, seleccione **Salir**.
3. En **Activar la administración de dispositivos**, seleccione **Desactivar**.
4. En la ventana emergente que se abre, seleccione **Desactivar**.

## <a name="remove-your-windows-81-phone"></a>Quitar un teléfono con Windows 8.1
Siga estos pasos para quitar un teléfono con Windows 8.1 de Intune.

1. Vaya a **Configuración** > **Área de trabajo**.
2. Pulse la cuenta de trabajo cuya inscripción quiere anular.
3. Pulse en **Eliminar** en la parte inferior de la pantalla.
4. En el cuadro de diálogo **Eliminar cuenta**, pulse en **Eliminar**.  
## <a name="removing-your-personal-information-after-removing-the-company-portal"></a>Eliminar la información personal después de quitar el Portal de empresa  

Hay dos tipos de datos que el Portal de empresa almacena en el dispositivo Windows:

- **Registros de diagnóstico**: datos de actividad de la aplicación estándar que recopila Microsoft. Se borran automáticamente cuando desinstala la aplicación Portal de empresa. Los datos de actividad de la aplicación son, por ejemplo, los que indican cuánto tiempo estuvo abierta la aplicación o si se bloqueó.
- **Caché de la aplicación**: archivos auxiliares necesarios para el funcionamiento de la aplicación, como iconos y valores de configuración.

Para eliminar los registros almacenados y la memoria caché, siga uno de esos pasos:

* [Desinstale la aplicación Portal de empresa](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs) 

* Restablezca la aplicación Portal de empresa. Abra la aplicación **Configuración** y seleccione > **Aplicaciones** > **Portal de empresa** > **Opciones avanzadas** > **Restablecer**. 

¿Sigue necesitando ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
