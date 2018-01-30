---
title: Inscribir dispositivos mediante el programa Windows AutoPilot Deployment
description: "Obtenga información sobre cómo inscribir nuevos dispositivos Windows 10 mediante el programa Windows AutoPilot Deployment."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.openlocfilehash: 1e6052c914406c9cd2fe9dc72597ee4dbe5b8902
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="enroll-windows-devices-using-windows-autopilot-deployment-program"></a>Inscribir dispositivos mediante el programa Windows AutoPilot Deployment
El programa Windows AutoPilot Deployment simplifica el aprovisionamiento de dispositivos. Crear y mantener imágenes personalizadas de sistemas operativos es un proceso que conlleva mucho tiempo. También se requiere tiempo para aplicar estas imágenes en dispositivos nuevos a la hora de prepararlos para que los puedan usar los usuarios finales. Con Microsoft Intune y AutoPilot, puede proporcionar nuevos dispositivos a los usuarios finales sin necesidad de crear, mantener y aplicar imágenes personalizadas del sistema operativo a los dispositivos. Al usar Intune para administrar dispositivos AutoPilot, puede administrar directivas, perfiles, aplicaciones, etc. en los dispositivos después de inscribirlos. Para obtener información general sobre las ventajas, los escenarios y los requisitos previos, consulte [Información general sobre Windows AutoPilot](https://docs.microsoft.com/windows/deployment/windows-10-auto-pilot).

## <a name="prerequisites"></a>Requisitos previos
- [Los dispositivos deben estar registrados en su organización](https://docs.microsoft.com/en-us/windows/deployment/windows-autopilot/windows-10-autopilot#device-registration-and-oobe-customization)
- [La inscripción automática de Windows 10 debe estar habilitada](https://docs.microsoft.com/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune#enable-windows-10-automatic-enrollment)
- [Se requiere una suscripción a Azure Active Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="synchronize-devices"></a>Sincronizar dispositivos
Sincronice los dispositivos registrados en Intune para poderlos configurar.

1. Inicie sesión en [Azure](https://portal.azure.com/).
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En **Intune**, seleccione **Inscripción de dispositivos**.
4. En **Inscripción de Windows**, en la sección **Programa de Windows AutoPilot Deployment** , elija **Dispositivos**.
5. Haga clic en **Sincronizar** para importar los dispositivos registrados. Aparecerá un mensaje en el que se indica que la sincronización está en curso.
6. Actualice la vista para ver los nuevos dispositivos. El proceso puede tardar unos minutos en completarse, en función de cuántos dispositivos se estén sincronizando.  

## <a name="create-an-autopilot-deployment-profile"></a>Crear un perfil de AutoPilot Deployment
Los perfiles de AutoPilot Deployment sirven para configurar los dispositivos AutoPilot.
1. Inicie sesión en [Azure](https://portal.azure.com/). 
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En **Intune**, seleccione **Inscripción de dispositivos**.
4. En **Inscripción de Windows**, en la sección **Programa de Windows AutoPilot Deployment** , elija **Dispositivos**.
5. Haga clic en **Crear perfil** y elija un nombre y, opcionalmente, una descripción. 
6. En **Tipo de combinación**, seleccione **Unidos a Azure AD**.
7. En **Configuración rápida**, configure las siguientes opciones y haga clic en **Aceptar**: 
   - **Configuración de privacidad**: elija si quiere mostrar la configuración de privacidad a los usuarios. 
   - **Contrato de licencia para el usuario final (CLUF)**: elija si quiere mostrar los términos de licencia a los usuarios.
   - **Tipo de cuenta de usuario**: elija si el tipo de cuenta de usuario es de **Administrador** o de usuario **Estándar**.

     > [!Note]    
     > Esta configuración no se aplica a las cuentas de administrador global ni de administrador de la compañía. Estas cuentas no pueden ser usuarios estándar porque tienen acceso a todas las características de administración en Azure AD.
8. Haga clic en **Crear** para crear el perfil. Ahora el perfil de implementación AutoPilot se puede asignar a los dispositivos.
     
> [!Note]    
> Las siguientes opciones se configuran con todos los perfiles de AutoPilot Deployment:
> - Omitir las páginas de configuración de registro de Cortana, OneDrive y OEM
> - Configurar automáticamente cuentas para el trabajo o la escuela
> - Iniciar sesión con la marca de empresa o centro educativo    

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Alertas de dispositivos sin asignar de Windows AutoPilot <!-- 163236 -->
Puede ver una alerta de dispositivos sin asignar de Windows AutoPilot para saber cuántos dispositivos del programa AutoPilot no tienen asignados perfiles de implementación de AutoPilot. Use la información provista en la alerta para crear perfiles y asignarlos a los dispositivos sin asignar. Al hacer clic en la alerta, verá una lista completa de dispositivos de Windows AutoPilot e información detallada sobre ellos. 
1. Inicie sesión en [Azure](https://portal.azure.com/). 
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En **Intune**, seleccione **Inscripción de dispositivos**.
4. Para ver la alerta, seleccione **Información general**. Haga clic en la alerta para ver una lista de dispositivos de AutoPilot.  

## <a name="assign-an-autopilot-deployment-profile"></a>Asignar un perfil de AutoPilot Deployment
Después de crear los perfiles de AutoPilot Deployment, puede asignarlos a los dispositivos seleccionados.

1. Inicie sesión en [Azure](https://portal.azure.com/). 
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En **Intune**, seleccione **Inscripción de dispositivos**.
4. En la hoja **Inscripción de Windows**, en la sección **Programa de Windows AutoPilot Deployment** , elija **Dispositivos**.
5. Seleccione los dispositivos a los que quiera asignar el perfil de implementación. También puede filtrar la columna **Estado** para encontrar fácilmente los dispositivos que no tengan ningún perfil asignado. 
6. Haga clic en **Asignar perfil**, seleccione el perfil de AutoPilot Deployment y después haga clic en **Asignar**. Aparecerá un mensaje en el que se indica que la asignación está en curso.
7. Actualice la vista para ver que el perfil se ha asignado a los dispositivos. El proceso puede tardar unos minutos en completarse, en función de cuántos dispositivos haya seleccionado. 

> [!Note]
> El nuevo perfil se ha asignado al dispositivo. En el caso de los dispositivos que ya se han inscrito en Intune, el perfil se aplicará después de que el dispositivo se haya restablecido y se haya vuelto a inscribir.

### <a name="assign-a-different-autopilot-deployment-profile"></a>Asignar un perfil distinto de AutoPilot Deployment
Si después de asignar un perfil de AutoPilot Deployment a un dispositivo, decide asignar otro perfil, asigne el nuevo perfil al dispositivo.  

## <a name="edit-an-autopilot-deployment-profile"></a>Editar un perfil de AutoPilot Deployment 
Cuando haya creado un perfil de AutoPilot Deployment, puede editar ciertas partes del perfil de implementación.   
1. Inicie sesión en [Azure](https://portal.azure.com/). 
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
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

## <a name="next-steps"></a>Pasos siguientes
Después de configurar Windows AutoPilot en dispositivos Windows 10 registrados, infórmese sobre cómo administrar los dispositivos. Para obtener más información, consulte [¿Qué es la administración de dispositivos de Microsoft Intune?](https://docs.microsoft.com/intune/device-management)