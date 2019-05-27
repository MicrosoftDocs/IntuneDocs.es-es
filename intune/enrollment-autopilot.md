---
title: Inscribir dispositivos con Windows Autopilot
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo inscribir dispositivos Windows 10 con Windows Autopilot.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/5/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2615c058c5de04842e8d607b717a290663b1a9b1
ms.sourcegitcommit: bc5e4dff18f5f9b79077a888f8a58dcc490708c0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/21/2019
ms.locfileid: "65983270"
---
# <a name="enroll-windows-devices-in-intune-by-using-the-windows-autopilot"></a>Inscripción de dispositivos Windows en Intune con Windows Autopilot  
Windows Autopilot simplifica el proceso de inscripción de dispositivos en Intune. Crear y mantener imágenes personalizadas de sistemas operativos es un proceso que conlleva mucho tiempo. También se requiere tiempo para aplicar estas imágenes en dispositivos nuevos a la hora de prepararlos para que los puedan usar los usuarios finales. Con Microsoft Intune y Autopilot, puede proporcionar nuevos dispositivos a los usuarios finales sin necesidad de crear, mantener y aplicar imágenes personalizadas del sistema operativo a los dispositivos. Al usar Intune para administrar dispositivos Autopilot, puede administrar directivas, perfiles y aplicaciones (entre otros) después de inscribirlos. Para obtener información general sobre las ventajas, los escenarios y los requisitos previos, vea [Overview of Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot) (Introducción a Windows Autopilot).


## <a name="prerequisites"></a>Requisitos previos
- [Suscripción a Intune](licenses.md)
- [La inscripción automática de Windows 10 debe estar habilitada](windows-enroll.md#enable-windows-10-automatic-enrollment)
- [Suscripción a las ediciones Azure Active Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="how-to-get-the-csv-for-import-in-intune"></a>Obtención del archivo CSV para importarlo en Intune

Vea el cmdlet de Powershell para más información sobre cómo usarlo.

- [Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo/1.3/Content/Get-WindowsAutoPilotInfo.ps1)

## <a name="add-devices"></a>Agregar dispositivos

Para agregar dispositivos de Windows Autopilot, puede importar un archivo CSV con su información.

1. En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Dispositivos** > **Importar**.

    ![Captura de pantalla de dispositivos de Windows Autopilot](media/enrollment-autopilot/autopilot-import-device.png)

2. En **Agregar dispositivos Windows Autopilot**, vaya a un archivo CSV en el que se enumeren los dispositivos que quiera agregar. El archivo debe enumerar los números de serie, los identificadores de producto de Windows, los hashes de hardware y las etiquetas de grupo de los dispositivos.

    ![Captura de pantalla de Agregar dispositivos Windows Autopilot](media/enrollment-autopilot/autopilot-import-device2.png)

3. Elija **Importar** para comenzar a importar la información del dispositivo. La importación puede tardar varios minutos.

4. Una vez completada la importación, elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Windows Autopilot** > **Dispositivos** > **Sincronización**. Aparecerá un mensaje en el que se indica que la sincronización está en curso. El proceso puede tardar unos minutos en completarse, en función de cuántos dispositivos se estén sincronizando.

5. Actualice la vista para ver los nuevos dispositivos.

## <a name="create-an-autopilot-device-group"></a>Crear un grupo de dispositivos Autopilot

1. En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Grupos** > **Nuevo grupo**.
2. En la hoja **Grupo**:
    1. En **Tipo de grupo**, elija **Seguridad**.
    2. Escriba un **Nombre de grupo** y una **Descripción del grupo**.
    3. En **Tipo de pertenencia**, elija **Asignado** o **Dispositivo dinámico**.
3. Si ha elegido **Asignado** en **Tipo de pertenencia** en el paso anterior, elija **Miembros** en la hoja **Grupo** y agregue dispositivos Autopilot al grupo.
    Los dispositivos Autopilot que aún no estén inscritos son aquellos en los que el nombre de dispositivo y el número de serie son el mismo.
4. Si ha elegido **Dispositivos dinámicos** en **Tipo de pertenencia** anteriormente, elija **Miembros del dispositivo dinámico** en la hoja **Grupo** y escriba cualquiera de los siguientes códigos en el cuadro **Regla avanzada**.
    - Si quiere crear un grupo que incluya todos los dispositivos Autopilot, escriba `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`.
    - El campo de etiqueta de grupo de Intune se asigna al atributo OrderID en los dispositivos de Azure AD. Si quiere crear un grupo que incluya todos los dispositivos Autopilot con una etiqueta de grupo específica (OrderID), escriba `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881") `.
    - Si quiere crear un grupo que incluya todos los dispositivos Autopilot con un identificador de pedido de compra específico, escriba `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    Después de agregar el código de **Regla avanzada**, elija **Guardar**.
5. Elija **Crear**.  

## <a name="create-an-autopilot-deployment-profile"></a>Crear un perfil de implementación de Autopilot
Los perfiles de implementación de Autopilot sirven para configurar los dispositivos Autopilot.
1. En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Perfiles de implementación** > **Crear perfil**.
2. En la página de los **datos básicos**, escriba un **nombre** y, opcionalmente, una **descripción**.

    ![Captura de pantalla de la página de los datos básicos](media/enrollment-autopilot/create-profile-basics.png)

3. Si quiere que todos los dispositivos en los grupos asignados se conviertan automáticamente en Autopilot, establezca **Convertir todos los dispositivos de destino a Autopilot** en **Sí**. Todos los dispositivos que no sean Autopilot en grupos asignados se registrarán con el servicio de implementación de Autopilot. Permita un plazo de 48 horas para que se procese el registro. Cuando se anule la inscripción del dispositivo y este se restablezca, Autopilot lo inscribirá. Una vez registrado un dispositivo de este modo, si deshabilita esta opción o quitar la asignación de perfil, el dispositivo no se quitará desde el servicio de implementación de Autopilot, sino que deberá [quitar el dispositivo directamente](enrollment-autopilot.md#delete-autopilot-devices).
4. Seleccione **Siguiente**.
5. En la página **Configuración rápida (OOBE)**, para **Modo de implementación**, elija una de las siguientes dos opciones:
    - **Controlado por el usuario**: Los dispositivos con este perfil están asociados al usuario que inscribe el dispositivo. Se necesitan credenciales de usuario para inscribir el dispositivo.
    - **Implementación automática (versión preliminar)**: (Windows 10 Insider Preview, compilación 1809 o posteriores) los dispositivos con este perfil no están asociados al usuario que inscribe el dispositivo. No se necesitan credenciales de usuario para inscribir el dispositivo.

    ![Captura de pantalla de la página OOBE](media/enrollment-autopilot/create-profile-outofbox.png)

6. En el cuadro **Unirse a Azure AD como**, elija **Unidos a Azure AD**.
7. Configure las siguientes opciones:
    - **Contrato de licencia para el usuario final (CLUF)**: (Windows 10, versión 1709 o versiones posterior) elija si quiere mostrar el CLUF a los usuarios.
    - **Configuración de privacidad**: elija si quiere mostrar la configuración de privacidad a los usuarios.
    - **Ocultar opciones para cambiar la cuenta (se necesita Windows 10, versión 1809 o posteriores)**: elija **Ocultar** para impedir que se muestren opciones para cambiar la cuenta en las páginas de error de inicio de sesión y dominio de empresa. Esta opción requiere la [configuración de la personalización de marca de la empresa en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding).
    - **Tipo de cuenta de usuario**: elija el tipo de cuenta de usuario (**Administrador** o **Estándar**).
    - **Permitir OOBE de White Glove**: elija **Sí** para admitir White Glove.
    - **Aplicar plantilla de nombre de dispositivo**: elija **Sí** para crear una plantilla que se usará al asignar nombres a dispositivos durante la inscripción. Los nombres deben tener 15 caracteres o menos y pueden contener letras, números y guiones. Los nombres no pueden estar formados solo por números. Use la [macro %SERIAL%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) para agregar el número de serie de hardware específico. O use la [macro %RAND:x%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) para agregar una cadena de números aleatoria, donde x equivale al número de dígitos para agregar. 
    - **Idioma (región)**\*: elija el idioma que se usará en el dispositivo. Esta opción solo está disponible si ha elegido **Implementación automática** como **Modo de implementación**.
    - **Configurar el teclado automáticamente**\*: si se selecciona un valor de **Idioma (región)**, elija **Sí** para omitir la página de selección de teclado. Esta opción solo está disponible si ha elegido **Implementación automática** como **Modo de implementación**.
8. Seleccione **Siguiente**.
9. En la página **Etiquetas de ámbito**, opcionalmente, agregue las etiquetas de ámbito que quiera aplicar a este perfil. Para obtener más información sobre las etiquetas de ámbito, consulte [Use role-based access control and scope tags for distributed IT](scope-tags.md) (Uso del control de acceso basado en roles y de las etiquetas de ámbito para la TI distribuida).
10. Seleccione **Siguiente**.
11. En la página **Asignaciones**, elija **Grupos seleccionados** para **Asignar a**.

    ![Captura de pantalla de la página Asignaciones](media/enrollment-autopilot/create-profile-assignments.png)

12. Elija **Seleccionar grupos para incluir** y determine los grupos que quiera incluir en este perfil.
13. Para excluir algún grupo, elija **Seleccionar grupos para excluir** y determine los grupos que quiera excluir.
14. Seleccione **Siguiente**.
15. En la página **Revisión y creación**, elija **Crear** para crear un perfil.

    ![Captura de pantalla de la página Revisión](media/enrollment-autopilot/create-profile-review.png)

> [!NOTE]
> Intune buscará de forma periódica nuevos dispositivos en los grupos asignados y, después, iniciará el proceso de asignación de perfiles a esos dispositivos. Este proceso puede tardar varios minutos en completarse. Antes de implementar un dispositivo, asegúrese de haber completado este proceso.  Puede comprobarlo en **Inscripción de dispositivos** > **Inscripción de Windows ** > **Dispositivos**, donde verá el cambio de estado de perfil de "Sin asignar" a "Asignando" y, finalmente, a "Asignado".

## <a name="edit-an-autopilot-deployment-profile"></a>Editar un perfil de implementación de Autopilot
Cuando haya creado un perfil de implementación de Autopilot, puede editar ciertas partes del perfil de implementación.   

1. En [Intune en el portal de Azure](https://aka.ms/intuneportal), seleccione **Inscripción de dispositivos**.
2. En la sección **Windows Autopilot** de **Inscripción de Windows**, elija **Perfiles de implementación**.
3. Seleccione el perfil que quiera editar.
4. Haga clic en **Propiedades**, a la izquierda, para cambiar el nombre o la descripción del perfil de implementación. Después de realizar cambios, haga clic en **Guardar**.
5. Para realizar cambios en la configuración rápida, haga clic en **Configuración**. Después de realizar cambios, haga clic en **Guardar**.

> [!NOTE]
> Los cambios realizados en el perfil se aplican a los dispositivos asignados a ese perfil. En cambio, el perfil actualizado no se aplicará a dispositivos que ya se hayan inscrito en Intune hasta que el dispositivo se restablezca y se vuelva a inscribir.

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Alertas de dispositivos sin asignar de Windows Autopilot  <!-- 163236 -->  

Las alertas mostrarán cuántos dispositivos del programa Autopilot no tienen perfiles de implementación de Autopilot. Use la información provista en la alerta para crear perfiles y asignarlos a los dispositivos sin asignar. Al hacer clic en la alerta, verá una lista completa de dispositivos de Windows Autopilot e información detallada sobre ellos.


Para ver alertas sobre los dispositivos sin asignar, en [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Información general** > **Dispositivos sin asignar**.  


## <a name="assign-a-user-to-a-specific-autopilot-device"></a>Asignación de un usuario a un dispositivo Autopilot específico

Puede asignar un usuario a un dispositivo Autopilot específico. Esta asignación rellena previamente la página de inicio de sesión de [marca de la empresa](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding) con un usuario de Azure Active Directory durante la configuración de Windows. También permite establecer un nombre personalizado para el saludo. Esta operación no rellena previamente ni modifica el inicio de sesión de Windows. Solo los usuarios con licencia de Intune pueden asignarse de esta manera.

Requisitos previos: Necesita configurar el Portal de empresa de Azure Active Directory y usar Windows 10, versión 1809 o posteriores.

1. En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Dispositivos** > elija el dispositivo > **Asignar usuario**.

    ![Captura de pantalla de la asignación del usuario](media/enrollment-autopilot/assign-user.png)

2. Elija un usuario de Azure con licencia para usar Intune y elija **Seleccionar**.

    ![Captura de pantalla de la selección del usuario](media/enrollment-autopilot/select-user.png)

3. En el cuadro **Nombre descriptivo**, escriba uno o acepte el predeterminado. Esta cadena es el nombre descriptivo que se mostrará cuando el usuario inicie sesión durante la configuración de Windows.

    ![Captura de pantalla del nombre descriptivo](media/enrollment-autopilot/friendly-name.png)

4. Elija **Aceptar**.


## <a name="delete-autopilot-devices"></a>Eliminación de dispositivos Autopilot

Los dispositivos Windows Autopilot que no estén inscritos en Intune se pueden eliminar:

- Elimine los dispositivos Windows Autopilot en **Inscripción de dispositivos** > **Inscripción de Windows** > **Dispositivos**. Elija los dispositivos que quiera eliminar y, después, seleccione **Eliminar**. La eliminación de dispositivos Windows Autopilot puede tardar unos minutos en completarse.

Para eliminar completamente un dispositivo del inquilino, tendrá que eliminar el dispositivo de Intune, el dispositivo de Azure Active Directory y los registros de los dispositivos Windows Autopilot. Todo esto se puede hacer desde Intune:

1. Si los dispositivos están inscritos en Intune, primero tendrá que [eliminarlos desde la hoja Todos los dispositivos de Intune](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. Elimine los dispositivos de Azure Active Directory en **Dispositivos** > **Dispositivos de Azure AD**.

3. Elimine los dispositivos Windows Autopilot en **Inscripción de dispositivos** > **Inscripción de Windows** > **Dispositivos**. Elija los dispositivos que quiera eliminar y, después, seleccione **Eliminar**. La eliminación de dispositivos Windows Autopilot puede tardar unos minutos en completarse.

## <a name="using-autopilot-in-other-portals"></a>Usar Autopilot en otros portales
Si no está interesado en la administración de dispositivos móviles, puede usar Autopilot en otros portales. Aunque tiene la opción de usar otros portales, le recomendamos que use solo Intune para administrar las implementaciones de Autopilot. Cuando use Intune y otro portal, Intune no podrá:  

- Mostrar los cambios realizados en perfiles creados en Intune, pero editados en otro portal.
- Sincronizar los perfiles creados en otro portal.
- Mostrar los cambios efectuados en las asignaciones de perfil realizadas en otro portal.
- Sincronizar los cambios efectuados en las asignaciones de perfil realizadas en otro portal.
- Mostrar los cambios en la lista de dispositivos que se realizaron en otro portal

## <a name="windows-autopilot-for-existing-devices"></a>Windows Autopilot para dispositivos existentes

Puede agrupar dispositivos Windows mediante un identificador de correlación cuando se inscriban mediante [Autopilot para dispositivos existentes](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) a través de Configuration Manager. El identificador de correlación es un parámetro del archivo de configuración de AutoPilot. El [atributo enrollmentProfileName de dispositivo de Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) se establece de forma automática para que sea igual a "OfflineAutopilotprofile-\<identificador de correlación\>". Esto permite crear grupos dinámicos de Azure AD arbitrarios en función del identificador de correlación mediante el atributo enrollmentprofileName.

>[!WARNING] 
> Dado que el identificador de correlación no aparece previamente en Intune, es posible que el dispositivo notifique cualquier identificador de correlación que quiera. Si el usuario crea un identificador de correlación que coincide con un nombre de perfil de Autopilot o DEP de Apple, el dispositivo se agregará a cualquier grupo de dispositivos dinámico de Azure AD que se base en el atributo enrollmentProfileName. Para evitar este conflicto:
> - Cree siempre las reglas de los grupos dinámicos de forma que coincidan con *todo* el valor de enrollmentProfileName.
> - Nunca empiece el nombre de los perfiles de Autopilot o DEP de Apple con "OfflineAutopilotprofile-".

## <a name="next-steps"></a>Pasos siguientes
Después de configurar Windows Autopilot en dispositivos Windows 10 registrados, infórmese sobre cómo administrar esos dispositivos. Para obtener más información, consulte [¿Qué es la administración de dispositivos de Microsoft Intune?](https://docs.microsoft.com/intune/device-management)
