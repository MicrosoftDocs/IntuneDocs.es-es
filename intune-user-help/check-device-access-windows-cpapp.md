---
title: Comprobar el acceso al dispositivo | Microsoft Docs
description: Compruebe el acceso al dispositivo para averiguar si cumple los requisitos y puede acceder a recursos profesionales o educativos.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1b4c1575c72e0563c4c55e262756c9b4aa0eddde
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "55848209"
---
# <a name="check-access-from-company-portal-app-for-windows"></a>Comprobar el acceso desde la aplicación Portal de empresa para Windows

Compruebe que el dispositivo tenga acceso a recursos profesionales o educativos. 

Las organizaciones exigen que se cumplan ciertos requisitos, como el cifrado y los límites de contraseña, para garantizar que solo los dispositivos seguros y de confianza accedan a sus datos. Los dispositivos administrados deben cumplir y mantener estos requisitos para poder acceder a los recursos de la organización.

La acción **Comprobar el acceso** evalúa la configuración del dispositivo y su estado de acceso. En la página **Detalles del dispositivo** se enumeran los valores que debe ajustar para recuperar el acceso. 

Complete los pasos que se describen en este artículo para comprobar el acceso desde la aplicación Portal de empresa para Windows.  

## <a name="check-access-from-device-details-page"></a>Comprobar el acceso desde la página de detalles del dispositivo  
1. Abra la aplicación Portal de empresa para Windows y vaya a **Mis dispositivos**.  

    ![Captura de pantalla de ejemplo de la página principal de la aplicación Portal de empresa para Windows, donde se resalta la sección Mis dispositivos.](./media/1809_CheckAccess_Context_Select_Device.png)  
2. Seleccione un dispositivo.  
3. En la página **Detalles del dispositivo**, seleccione **Comprobar acceso**. La aplicación sincroniza el dispositivo con los requisitos actuales de la organización y comprueba que el dispositivo los cumpla. Esta comprobación puede tardar unos minutos.  

    ![Captura de pantalla de ejemplo de la aplicación Portal de empresa para Windows, página de detalles del dispositivo, donde se resalta el botón Comprobar acceso.](./media/1809_CheckAccess_Checking_Status.png) 

4. Busque la actualización de estado, que le indicará que el dispositivo **Puede acceder a los recursos de su organización** o **No puede acceder a los recursos de su organización**.  

   ![Captura de pantalla de ejemplo de la aplicación Portal de empresa para Windows, página de detalles del dispositivo, donde se resalta la sección Estado.](./media/1809_CheckAccess_Device_details_status1.png)  
   
5. Si el dispositivo no puede acceder a los recursos, vaya a la alerta situada en la parte superior de la página. Haga clic en **Más** para expandir los detalles. Haga clic en **Menos** para contraerlos.  

    ![Captura de pantalla de ejemplo de la aplicación Portal de empresa para Windows, página de detalles del dispositivo, donde se resalta la alerta de la parte superior de la página.](./media/1809_CheckAccess_Device_details_alert1.png)  

6. Cuando corresponda, en el mensaje se mostrarán más vínculos de ayuda y medidas de corrección. Seleccione una o varias de estas opciones para empezar a solucionar problemas de inmediato. Las acciones de resolución, sincronización y contacto que se describen a continuación solo son visibles al usar el Portal de empresa en el dispositivo afectado.  

     * **Cómo resolverlo** abre el artículo de ayuda correspondiente, si está disponible.  
     * **Resolver** le redirige a la configuración del dispositivo.  
     * **Sincronizar** evalúa el dispositivo para asegurarse de que cumple los requisitos de su organización.  
     * **Contacto de TI** le redirige a la información de contacto de su equipo de TI.   
 
6. Después de actualizar la configuración, haga clic en **Comprobar acceso** para confirmar el estado del dispositivo.  

    ![Captura de pantalla de ejemplo de la aplicación Portal de empresa para Windows, página de detalles del dispositivo, donde se resalta la sección Estado.](./media/1809_CheckAccess_Device_details_status1.png)  

## <a name="check-access-from-device-context-menu"></a>Comprobar el acceso desde el menú contextual del dispositivo  
1. Abra la aplicación Portal de empresa para Windows y vaya a **Mis dispositivos**.  

    ![Captura de pantalla de ejemplo de la página principal de la aplicación Portal de empresa para Windows, donde se resalta la sección Mis dispositivos.](./media/1809_CheckAccess_Context_Select_Device.png)  

2. Haga clic con el botón derecho en un dispositivo o manténgalo pulsado para abrir el [menú contextual](https://docs.microsoft.com//windows/uwp/design/controls-and-patterns/menus).  

    ![Captura de pantalla de ejemplo de la página principal de la aplicación Portal de empresa para Windows. El menú contextual del dispositivo está visible en la sección **Mis dispositivos** de la página y muestra las acciones "Cambiar nombre", "Quitar" y "Comprobar acceso".](./media/1809_DeviceContextMenu_Windows_CP.png)  
3. Seleccione **Comprobar acceso**. La aplicación sincroniza el dispositivo con los requisitos actuales de la organización y comprueba que el dispositivo los cumpla. Esta comprobación puede tardar unos minutos.  
 
4. Aparece un mensaje en el dispositivo para informarle de que el dispositivo **Puede acceder a recursos de la empresa** o **No puede acceder a recursos de la empresa**. 

    ![Captura de pantalla de ejemplo de la aplicación Portal de empresa para Windows, página de detalles del dispositivo, donde se resalta la sección Estado.](./media/1809_CheckAccess_Context_Menu_Alert2.png) 

5. Si el dispositivo no puede acceder a los recursos, seleccione el dispositivo.  
6. En la página **Detalles del dispositivo**, vaya a la alerta situada en la parte superior de la página. Haga clic en **Más** para expandir los detalles. Haga clic en **Menos** para contraerlos.  

    ![Captura de pantalla de ejemplo de la aplicación Portal de empresa para Windows, página de detalles del dispositivo, donde se resalta la alerta de la parte superior de la página.](./media/1809_CheckAccess_Device_details_alert1.png)  

6. Cuando corresponda, en el mensaje se mostrarán más vínculos de ayuda y medidas de corrección. Seleccione una o varias de estas opciones para empezar a solucionar problemas de inmediato. Las acciones de resolución, sincronización y contacto que se describen a continuación solo son visibles al usar el Portal de empresa en el dispositivo afectado.  

     * **Cómo resolverlo** abre el artículo de ayuda correspondiente, si está disponible.  
     * **Resolver** le redirige a la configuración del dispositivo.  
     * **Sincronizar** evalúa el dispositivo para asegurarse de que cumple los requisitos de su organización.  
     * **Contacto de TI** le redirige a la información de contacto de su equipo de TI.    

7. Después de actualizar la configuración, haga clic en **Comprobar acceso** en la parte inferior de la página.  

    ![Captura de pantalla de ejemplo de la aplicación Portal de empresa para Windows, página de detalles del dispositivo, donde se resalta la acción Comprobar acceso.](./media/1809_CheckAccess_Device_details_button.png) 


¿Necesita más ayuda? Para encontrar la información de contacto del equipo de soporte técnico de su empresa, vaya al [sitio web del Portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
