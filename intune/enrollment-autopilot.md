---
title: Inscribir dispositivos mediante el programa Windows AutoPilot Deployment
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo inscribir dispositivos Windows 10 mediante el programa Windows AutoPilot Deployment.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.openlocfilehash: 934b80d1c174c25d37e30695f46afc88c8d8bfc3
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
---
# <a name="enroll-windows-devices-by-using-the-windows-autopilot-deployment-program"></a>Inscribir dispositivos Windows mediante el programa Windows AutoPilot Deployment
El programa Windows AutoPilot Deployment simplifica el aprovisionamiento de dispositivos. Crear y mantener imágenes personalizadas de sistemas operativos es un proceso que conlleva mucho tiempo. También se requiere tiempo para aplicar estas imágenes en dispositivos nuevos a la hora de prepararlos para que los puedan usar los usuarios finales. Con Microsoft Intune y AutoPilot, puede proporcionar nuevos dispositivos a los usuarios finales sin necesidad de crear, mantener y aplicar imágenes personalizadas del sistema operativo a los dispositivos. Al usar Intune para administrar dispositivos AutoPilot, puede administrar directivas, perfiles, aplicaciones, etc. en los dispositivos después de inscribirlos. Para obtener información general sobre las ventajas, los escenarios y los requisitos previos, consulte [Información general sobre Windows AutoPilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).

## <a name="prerequisites"></a>Requisitos previos
- [La inscripción automática de Windows 10 debe estar habilitada](https://docs.microsoft.com/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune#enable-windows-10-automatic-enrollment)
- [Se requiere una suscripción a Azure Active Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="add-devices"></a>Agregar dispositivos

Para agregar dispositivos de Windows AutoPilot, puede importar un archivo CSV con su información.

1. En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Dispositivos** > **Importar**.

    ![Captura de pantalla de dispositivos de Windows AutoPilot](media/enrollment-autopilot/autopilot-import-device.png)

2. En **Agregar dispositivos Windows AutoPilot**, vaya a un archivo CSV que contiene los números de serie, los identificadores de producto de Windows y los hash de hardware de los dispositivos que quiere agregar.

    ![Captura de pantalla de Agregar dispositivos Windows AutoPilot](media/enrollment-autopilot/autopilot-import-device2.png)

3. Elija **Importar** para comenzar a importar la información del dispositivo. Esta operación puede tardar varios minutos.

## <a name="synchronize-devices"></a>Sincronizar dispositivos
Sincronice los dispositivos registrados en Intune para poderlos configurar.

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En **Intune**, seleccione **Inscripción de dispositivos**.
4. Elija **Inscripción de Windows** y en la sección **Programa de Windows AutoPilot Deployment** , elija **Dispositivos**.
5. Haga clic en **Sincronizar** para importar los dispositivos registrados. Aparecerá un mensaje en el que se indica que la sincronización está en curso.
6. Actualice la vista para ver los nuevos dispositivos. El proceso puede tardar unos minutos en completarse, en función de cuántos dispositivos se estén sincronizando.  

## <a name="create-an-autopilot-deployment-profile"></a>Crear un perfil de AutoPilot Deployment
Los perfiles de AutoPilot Deployment sirven para configurar los dispositivos AutoPilot.
1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En **Intune**, seleccione **Inscripción de dispositivos**.
4. Elija **Inscripción de Windows** y en la sección **Programa de Windows AutoPilot Deployment** , elija **Perfiles de dispositivo**.
5. Seleccione **Crear perfil**, elija un nombre y, si lo desea, una descripción.
6. Para **Unirse a Azure AD como**, seleccione **Unidos a Azure AD**.
7. En **Configuración rápida**, configure las siguientes opciones y haga clic en **Guardar**:

   - **Contrato de licencia para el usuario final (CLUF)**: elija si quiere mostrar los términos de licencia a los usuarios.
   - **Configuración de privacidad**: elija si quiere mostrar la configuración de privacidad a los usuarios.
   - **Tipo de cuenta de usuario**: elija si el tipo de cuenta de usuario es de **Administrador** o de usuario **Estándar**.

     > [!Note]    
     > Esta configuración no se aplica a las cuentas de administrador global ni de administrador de la compañía. Estas cuentas no pueden ser usuarios estándar porque tienen acceso a todas las características de administración en Azure AD.


6. Haga clic en **Crear** para crear el perfil. Ahora el perfil de implementación AutoPilot se puede asignar a los dispositivos.

> [!Note]    
> Las siguientes opciones se configuran con todos los perfiles de AutoPilot Deployment:
> - Omitir las páginas de configuración de registro de Cortana, OneDrive y OEM
> - Configurar automáticamente cuentas para el trabajo o la escuela
> - Iniciar sesión con la marca de empresa o centro educativo    

## <a name="assign-an-autopilot-deployment-profile"></a>Asignar un perfil de AutoPilot Deployment
Después de crear los perfiles de AutoPilot Deployment, puede asignarlos a los dispositivos seleccionados.

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En **Intune**, seleccione **Inscripción de dispositivos**.
4. Elija **Inscripción de Windows** y en la sección **Programa de Windows AutoPilot Deployment** , elija **Dispositivos**.
5. Seleccione los dispositivos a los que quiera asignar el perfil de implementación. También puede filtrar la columna **Estado del perfil** para encontrar fácilmente los dispositivos que no tengan ningún perfil asignado.
6. Haga clic en **Asignar perfil**, seleccione el perfil de AutoPilot Deployment y después haga clic en **Asignar**. Aparecerá un mensaje en el que se indica que la asignación está en curso.
7. Actualice la vista para ver que el perfil se ha asignado a los dispositivos. El proceso puede tardar unos minutos en completarse, en función de cuántos dispositivos haya seleccionado.

> [!Note]
> El nuevo perfil se ha asignado al dispositivo. En el caso de los dispositivos que ya se han inscrito en Intune, el perfil se aplicará después de que el dispositivo se haya restablecido y se haya vuelto a inscribir.

### <a name="assign-a-different-autopilot-deployment-profile"></a>Asignar un perfil distinto de AutoPilot Deployment
Si después de asignar un perfil de AutoPilot Deployment a un dispositivo, decide asignar otro perfil, asigne el nuevo perfil al dispositivo.  

## <a name="edit-an-autopilot-deployment-profile"></a>Editar un perfil de AutoPilot Deployment
Cuando haya creado un perfil de AutoPilot Deployment, puede editar ciertas partes del perfil de implementación.   

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En **Intune**, seleccione **Inscripción de dispositivos**.
4. En **Inscripción de Windows**, en la sección **Programa de Windows AutoPilot Deployment** , elija **Dispositivos**.
5. Seleccione el perfil que quiera editar.
6. Haga clic en **Propiedades**, a la izquierda, para cambiar el nombre o la descripción del perfil de implementación. Después de realizar cambios, haga clic en **Guardar**.
7. Para realizar cambios en la configuración rápida, haga clic en **Configuración**. Después de realizar cambios, haga clic en **Guardar**.

> [!NOTE]
> El perfil actualizado se asigna a los dispositivos. En cambio, el perfil actualizado no se aplicará a dispositivos que ya se hayan inscrito en Intune hasta que el dispositivo se restablezca y se vuelva a inscribir.

## <a name="using-autopilot-in-other-portals"></a>Usar AutoPilot en otros portales
Si no está interesado en la administración de dispositivos móviles, puede usar AutoPilot en Tienda Microsoft para Empresas, por ejemplo. Aunque tiene la opción de usar otros portales, le recomendamos que use solo Intune para administrar las implementaciones de AutoPilot. Si usa Intune y otro portal, Intune no podrá:
- Mostrar los cambios realizados en perfiles creados en Intune, pero editados en otro portal.
- Sincronizar los perfiles creados en otro portal.
- Mostrar los cambios efectuados en las asignaciones de perfil realizadas en otro portal.
- Sincronizar los cambios efectuados en las asignaciones de perfil realizadas en otro portal.
- Mostrar los cambios en la lista de dispositivos que se realizaron en otro portal

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Alertas de dispositivos sin asignar de Windows AutoPilot <!-- 163236 -->
Puede ver una alerta de dispositivos sin asignar de Windows AutoPilot para saber cuántos dispositivos del programa AutoPilot no tienen asignados perfiles de implementación de AutoPilot. Use la información provista en la alerta para crear perfiles y asignarlos a los dispositivos sin asignar. Al hacer clic en la alerta, verá una lista completa de dispositivos de Windows AutoPilot e información detallada sobre ellos.

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En **Intune**, seleccione **Inscripción de dispositivos**.
4. Para ver la alerta, seleccione **Información general**. Haga clic en la alerta para ver una lista de dispositivos de AutoPilot.  

## <a name="delete-autopilot-devices"></a>Eliminación de dispositivos AutoPilot

Puede eliminar los dispositivos Windows AutoPilot que no estén inscritos. Puede anular la suscripción de los dispositivos y luego eliminarlos.

1. En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Dispositivos**.

2. En **Dispositivos Windows AutoPilot**, elija los dispositivos que quiere eliminar y, luego, elija **Eliminar**.

3. Para confirmar la eliminación, elija **Sí**. Esta operación puede tardar unos minutos.


## <a name="next-steps"></a>Pasos siguientes
Después de configurar Windows AutoPilot en dispositivos Windows 10 registrados, infórmese sobre cómo administrar los dispositivos. Para obtener más información, consulte [¿Qué es la administración de dispositivos de Microsoft Intune?](https://docs.microsoft.com/intune/device-management)
