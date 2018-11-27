---
title: 'Tutorial: Uso de Autopilot para inscribir dispositivos en Intune'
titleSuffix: Microsoft Intune
description: En este tutorial, deberá configurar Windows Autopilot para inscribir dispositivos en Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/19/2018
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up Windows Autopilot so that users can enroll in Intune.
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.openlocfilehash: 087f890f84c9bc0ff0c46f129ef84b8a268c738e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187742"
---
# <a name="tutorial-use-autopilot-to-enroll-windows-devices-in-intune"></a>Tutorial: Uso de Autopilot para inscribir dispositivos Windows en Intune
Windows Autopilot simplifica el proceso de inscripción de dispositivos. Con Microsoft Intune y Autopilot, puede proporcionar nuevos dispositivos a los usuarios finales sin necesidad de crear, mantener y aplicar imágenes personalizadas del sistema operativo. 

En este tutorial, aprenderá a:
> [!div class="checklist"]
> * Agregar dispositivos a Intune
> * Crear un grupo de dispositivos Autopilot
> * Crear un perfil de implementación de Autopilot
> * Asignar el perfil de implementación de Autopilot al grupo de dispositivos
> * Distribuir los dispositivos Windows a los usuarios

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](free-trial-sign-up.md).

Para obtener información general sobre las ventajas, los escenarios y los requisitos previos de Autopilot, vea [Introducción a Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).


## <a name="prerequisites"></a>Requisitos previos
- [Configurar la inscripción automática para Windows](quickstart-setup-auto-enrollment.md)
- [Se requiere una suscripción a Azure Active Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->


## <a name="add-devices"></a>Agregar dispositivos

El primer paso para configurar Windows Autopilot es agregar los dispositivos Windows a Intune. Lo único que debe hacer es crear un archivo CSV e importarlo en Intune.

1. En cualquier editor de texto, cree una lista de valores separados por comas (CSV) que identifican los dispositivos Windows. Utilice el siguiente formato:
    
    *número-de-serie*, *Id.-de-producto-de-windows*, *hash-del-hardware*, *Id.-de-pedido-opcional*
    
    Los tres primeros elementos son necesarios, pero el identificador de pedido es opcional.

2. Guarde el archivo CSV.

3. En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Dispositivos** > **Importar**.

    ![Captura de pantalla de dispositivos de Windows Autopilot](media/enrollment-autopilot/autopilot-import-device.png)

4. En **Agregar dispositivos Windows Autopilot**, examine el archivo CSV que guardó.

    ![Captura de pantalla de Agregar dispositivos Windows Autopilot](media/enrollment-autopilot/autopilot-import-device2.png)

5. Elija **Importar** para comenzar a importar la información del dispositivo. La importación puede tardar varios minutos.

4. Una vez completada la importación, elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Windows Autopilot** > **Dispositivos** > **Sincronización**. Aparecerá un mensaje en el que se indica que la sincronización está en curso. El proceso puede tardar unos minutos en completarse, en función de cuántos dispositivos vaya a sincronizar.

5. Actualice la vista para ver los nuevos dispositivos.

## <a name="create-an-autopilot-device-group"></a>Crear un grupo de dispositivos Autopilot

Después, se creará un grupo de dispositivos e incluirá en él los dispositivos Autopilot que acaba de cargar.

1. En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Grupos** > **Nuevo grupo**.
2. En la hoja **Grupo**:
    1. En **Tipo de grupo**, elija **Seguridad**.
    2. En **Nombre de grupo**, escriba *Grupo de Autopilot*. En **Descripción del grupo**, escriba *Probar grupo para dispositivos Autopilot*.
    3. En **Tipo de pertenencia**, elija **Asignado**.
3. En la hoja **Grupo**, elija **Miembros** y agregue los dispositivos Autopilot al grupo. Los dispositivos Autopilot que aún no estén inscritos son aquellos en los que el nombre de dispositivo y el número de serie son el mismo.
4. Elija **Crear**.  

## <a name="create-an-autopilot-deployment-profile"></a>Crear un perfil de implementación de Autopilot

Después de crear un grupo de dispositivos, debe crear un perfil de implementación para que pueda configurar los dispositivos Autopilot.

1. En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Perfiles de implementación** > **Crear perfil**.
2. En **Nombre**, escriba *Perfil de Autopilot*. En **Descripción**, escriba *Probar perfil para dispositivos Autopilot*.
3. Establezca **Convertir todos los dispositivos de destino a Autopilot** en **Sí**. Esta configuración garantiza que todos los dispositivos de la lista se registren en el servicio de implementación de Autopilot. Permita un plazo de 48 horas para que se procese el registro.
4. En **Modo de implementación**, elija **Controlado por el usuario**. Los dispositivos con este perfil están asociados al usuario que inscribe el dispositivo. Se necesitan credenciales de usuario para inscribir el dispositivo.
5. En el cuadro **Unirse a Azure AD como**, elija **Unidos a Azure AD**.
6. Elija **Configuración rápida**, configure las siguientes opciones, deje el resto con los valores predeterminados y elija **Guardar**:
    - **Contrato de licencia para el usuario final (EULA)**: **Ocultar**
    - **Configuración de privacidad**: **Mostrar**
    - **Tipo de cuenta de usuario**: **Estándar**

6. Elija **Crear** para crear el perfil. Ahora el perfil de implementación Autopilot se puede asignar a los dispositivos.

## <a name="assign-an-autopilot-deployment-profile-to-a-device-group"></a>Asignar un perfil de implementación de Autopilot a un grupo de dispositivos

Una vez creado el perfil de implementación, deberá asignarlo al grupo de dispositivos.
1. En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Perfiles de implementación** y seleccione un perfil.
2. En la hoja del perfil en cuestión, elija **Asignaciones**. 
3. Elija **Seleccionar grupos**; después, en la hoja **Seleccionar grupos**, elija **Grupo de Autopilot** y después **Seleccionar**.

## <a name="distribute-devices-to-users"></a>Distribuir los dispositivos a los usuarios

Ahora puede distribuir los dispositivos Windows a los usuarios. Cuando inician sesión por primera vez, el sistema Autopilot inscribirá y configurará automáticamente los dispositivos. 

## <a name="clean-up-resources"></a>Limpieza de recursos

Si ya no quiere usar más los dispositivos Autopilot, puede eliminarlos.

1. Si los dispositivos están inscritos en Intune, antes hay que [eliminarlos del portal de Azure Active Directory](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Dispositivos**.

3. En **Dispositivos Windows AutoPilot**, elija los dispositivos que quiere eliminar y, luego, elija **Eliminar**.

4. Para confirmar la eliminación, elija **Sí**. Esta operación puede tardar unos minutos.

## <a name="next-steps"></a>Pasos siguientes

Puede encontrar más información sobre otras opciones disponibles para Windows Autopilot.

> [!div class="nextstepaction"]
> [Artículo exhaustivo sobre la inscripción de Autopilot](enrollment-autopilot.md)


