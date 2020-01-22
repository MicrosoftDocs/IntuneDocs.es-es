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
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up Windows Autopilot so that users can enroll in Intune.
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9b0bb0bd1f0df3aeb4185542d424bd3ffffe42cd
ms.sourcegitcommit: 52475fcd8d05d2f6b858d780ebb3d88eaadb0849
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2020
ms.locfileid: "76036541"
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

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](../fundamentals/free-trial-sign-up.md).

Para obtener información general sobre las ventajas, los escenarios y los requisitos previos de Autopilot, vea [Introducción a Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).


## <a name="prerequisites"></a>Requisitos previos
- [Configurar la inscripción automática para Windows](../quickstart-setup-auto-enrollment.md)
- [Suscripción a las ediciones Azure Active Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](https://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->


## <a name="add-devices"></a>Agregar dispositivos

El primer paso para configurar Windows Autopilot es agregar los dispositivos Windows a Intune. Lo único que debe hacer es crear un archivo CSV e importarlo en Intune.

1. En cualquier editor de texto, cree una lista de valores separados por comas (CSV) que identifican los dispositivos Windows. Use el formato siguiente:
    
    *número-de-serie*, *id.-de-producto-de-windows*, *hash-del-hardware*, *etiqueta-de-grupo-opcional*
    
    Los tres primeros elementos son necesarios, pero la etiqueta de grupo (anteriormente conocido como "id. de pedido") es opcional.

2. Guarde el archivo CSV.

3. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Dispositivos** > **Windows** > **Dispositivos** (en **Windows Autopilot Deployment Program** > **Importar**.

    ![Captura de pantalla de dispositivos de Windows Autopilot](./media/enrollment-autopilot/autopilot-import-device.png)

4. En **Agregar dispositivos Windows Autopilot**, examine el archivo CSV que guardó.

    ![Captura de pantalla de Agregar dispositivos Windows Autopilot](./media/tutorial-use-autopilot-enroll-devices/autopilot-import-device2.png)

5. Elija **Importar** para comenzar a importar la información del dispositivo. La importación puede tardar varios minutos.

4. Una vez finalizada la importación, elija **Dispositivos** > **Windows** > **Inscripción de Windows** > **Dispositivos** (en **Windows Autopilot Deployment Program** > **Sincronizar**. Aparecerá un mensaje en el que se indica que la sincronización está en curso. El proceso puede tardar unos minutos en completarse, en función de cuántos dispositivos vaya a sincronizar.

5. Actualice la vista para ver los nuevos dispositivos.

## <a name="create-an-autopilot-device-group"></a>Crear un grupo de dispositivos Autopilot

Después, se creará un grupo de dispositivos e incluirá en él los dispositivos Autopilot que acaba de cargar.

1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), seleccione **Grupos** > **Nuevo grupo**.
2. En la hoja **Grupo**:
    1. En **Tipo de grupo**, elija **Seguridad**.
    2. En **Nombre de grupo**, escriba *Grupo de Autopilot*. En **Descripción del grupo**, escriba *Probar grupo para dispositivos Autopilot*.
    3. En **Tipo de pertenencia**, elija **Asignado**.
3. En la hoja **Grupo**, elija **Miembros** y agregue los dispositivos Autopilot al grupo. Los dispositivos Autopilot que aún no estén inscritos son aquellos en los que el nombre de dispositivo y el número de serie son el mismo.
4. Elija **Crear**.  

## <a name="create-an-autopilot-deployment-profile"></a>Crear un perfil de implementación de Autopilot

Después de crear un grupo de dispositivos, debe crear un perfil de implementación para que pueda configurar los dispositivos Autopilot.

1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Dispositivos** > **Windows** > **Inscripción de Windows** > **Perfiles de implementación** > **Crear perfil**.
2. En la página **Aspectos básicos**, en **Nombre**, escriba *Perfil de Autopilot*. En **Descripción**, escriba *Probar perfil para dispositivos Autopilot*.
3. Establezca **Convertir todos los dispositivos de destino a Autopilot** en **Sí**. Esta configuración garantiza que todos los dispositivos de la lista se registren en el servicio de implementación de Autopilot. Permita un plazo de 48 horas para que se procese el registro.
4. Seleccione **Siguiente**.
5. En la página **Configuración rápida (OOBE)** , para **Modo de implementación**, elija **Controlado por el usuario**. Los dispositivos con este perfil están asociados al usuario que inscribe el dispositivo. Se necesitan credenciales de usuario para inscribir el dispositivo.
6. En el cuadro **Unirse a Azure AD como**, elija **Unidos a Azure AD**.
7. Configure las opciones siguientes y deje el valor predeterminado en las demás:
    - **Contrato de licencia para el usuario final (CLUF)** : **Ocultar**
    - **Configuración de privacidad**: **Mostrar**
    - **Tipo de cuenta de usuario**: **Estándar**
8. Seleccione **Siguiente**.
9. En la página **Asignaciones**, elija **Grupos seleccionados** para **Asignar a**.
10. Elija **Seleccionar grupos para incluir** y elija **Grupo de Autopilot**.
11. Seleccione **Siguiente**.
12. En la página **Revisión y creación**, elija **Crear** para crear un perfil.

## <a name="distribute-devices-to-users"></a>Distribuir los dispositivos a los usuarios

Ahora puede distribuir los dispositivos Windows a los usuarios. Cuando inician sesión por primera vez, el sistema Autopilot inscribirá y configurará automáticamente los dispositivos. 

## <a name="clean-up-resources"></a>Limpieza de recursos

Si ya no quiere usar más los dispositivos Autopilot, puede eliminarlos.

1. Si los dispositivos están inscritos en Intune, antes hay que [eliminarlos del portal de Azure Active Directory](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Dispositivos** > **Windows** > **Inscripción de Windows** > **Dispositivos** (en **Windows Autopilot Deployment Program**).

3. Elija los dispositivos que quiera eliminar y, después, seleccione **Eliminar**.

4. Para confirmar la eliminación, elija **Sí**. Esta operación puede tardar unos minutos.

## <a name="next-steps"></a>Pasos siguientes

Puede encontrar más información sobre otras opciones disponibles para Windows Autopilot.

> [!div class="nextstepaction"]
> [Artículo exhaustivo sobre la inscripción de Autopilot](enrollment-autopilot.md)


