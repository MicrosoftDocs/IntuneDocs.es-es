---
title: Inscribir dispositivos con Windows AutoPilot
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo inscribir dispositivos Windows 10 con Windows AutoPilot.
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
ms.openlocfilehash: a640e6d914da6fead7a64d5235c1cdeac164ac9e
ms.sourcegitcommit: 7c70c3e0fcae7c4fa8c9e108aafb1cebb366332d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44096544"
---
# <a name="enroll-windows-devices-by-using-the-windows-autopilot"></a>Inscribir dispositivos Windows con Windows AutoPilot
Windows AutoPilot simplifica el aprovisionamiento de dispositivos. Crear y mantener imágenes personalizadas de sistemas operativos es un proceso que conlleva mucho tiempo. También se requiere tiempo para aplicar estas imágenes en dispositivos nuevos a la hora de prepararlos para que los puedan usar los usuarios finales. Con Microsoft Intune y AutoPilot, puede proporcionar nuevos dispositivos a los usuarios finales sin necesidad de crear, mantener y aplicar imágenes personalizadas del sistema operativo a los dispositivos. Al usar Intune para administrar dispositivos AutoPilot, puede administrar directivas, perfiles y aplicaciones (entre otros) después de inscribirlos. Para obtener información general sobre las ventajas, los escenarios y los requisitos previos, consulte [Información general sobre Windows AutoPilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).

## <a name="prerequisites"></a>Requisitos previos
- [La inscripción automática de Windows 10 debe estar habilitada](https://docs.microsoft.com/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune#enable-windows-10-automatic-enrollment)
- [Se requiere una suscripción a Azure Active Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="add-devices"></a>Agregar dispositivos

Para agregar dispositivos de Windows AutoPilot, puede importar un archivo CSV con su información.

1. En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Dispositivos** > **Importar**.

    ![Captura de pantalla de dispositivos de Windows AutoPilot](media/enrollment-autopilot/autopilot-import-device.png)

2. En **Agregar dispositivos Windows Autopilot**, vaya a un archivo CSV en el que se enumeren los dispositivos que quiera agregar. El archivo debe contener los números de serie, los identificadores de producto de Windows, los hashes de hardware y los identificadores de pedido opcionales de los dispositivos.

    ![Captura de pantalla de Agregar dispositivos Windows AutoPilot](media/enrollment-autopilot/autopilot-import-device2.png)

3. Elija **Importar** para comenzar a importar la información del dispositivo. La importación puede tardar varios minutos.

4. Una vez completada la importación, elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Windows AutoPilot** > **Dispositivos** > **Sincronización**. Aparecerá un mensaje en el que se indica que la sincronización está en curso. El proceso puede tardar unos minutos en completarse, en función de cuántos dispositivos se estén sincronizando.

5. Actualice la vista para ver los nuevos dispositivos.

## <a name="create-an-autopilot-device-group"></a>Crear un grupo de dispositivos 	de AutoPilot

1. En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Grupos**.
2. En la hoja **Grupo**:
    1. En **Tipo de grupo**, elija **Seguridad**.
    2. Escriba un **Nombre de grupo** y una **Descripción del grupo**.
    3. En **Tipo de pertenencia**, elija **Asignado** o **Dispositivo dinámico**.
3. Si ha elegido **Asignado** en **Tipo de pertenencia** en el paso anterior, elija **Miembros** en la hoja **Grupo** y agregue dispositivos AutoPilot al grupo.
    Los dispositivos AutoPilot que aún no estén inscritos son aquellos en los que el nombre de dispositivo y el número de serie son el mismo.
4. Si ha elegido **Dispositivos dinámicos** en **Tipo de pertenencia** anteriormente, elija **Miembros del dispositivo dinámico** en la hoja **Grupo** y escriba cualquiera de los siguientes códigos en el cuadro **Regla avanzada**.
    - Si quiere crear un grupo que incluya todos los dispositivos AutoPilot, escriba `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - Si quiere crear un grupo que incluya todos los dispositivos AutoPilot con un identificador de pedido específico, escriba `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881") `
    - Si quiere crear un grupo que incluya todos los dispositivos AutoPilot con un identificador de pedido de compra específico, escriba `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    Después de agregar el código de **Regla avanzada**, elija **Guardar**.
5. Elija **Crear**.



## <a name="create-an-autopilot-deployment-profile"></a>Crear un perfil de AutoPilot Deployment
Los perfiles de AutoPilot Deployment sirven para configurar los dispositivos AutoPilot.
1. En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Perfiles de implementación** > **Crear perfil**.
2. Escriba un **Nombre** y una **Descripción** opcional.
3. En **Modo de implementación**, elija una de estas dos opciones:
    - **Controlado por el usuario**: los dispositivos con este perfil están asociados al usuario que inscribe el dispositivo. Se necesitan credenciales de usuario para aprovisionar el dispositivo.
    - **Implementación automática (versión preliminar)**: (requiere la [compilación de Windows 10 Insider Preview](https://docs.microsoft.com/windows-insider/at-work-pro/) más reciente) los dispositivos con este perfil no están asociados al usuarios que inscribe el dispositivo. No se necesitan credenciales de usuario para aprovisionar el dispositivo.
4. En el cuadro **Unirse a Azure AD como**, elija **Unidos a Azure AD**.
5. Elija **Configuración rápida**, configure las siguientes opciones y elija **Guardar**:
    - **Idioma (región)***: elija el idioma que se usará en el dispositivo. Esta opción solo está disponible si ha elegido **Implementación automática** como **Modo de implementación**.
    - **Configurar el teclado automáticamente***: si se selecciona un **Idioma (región)**, elija **Sí** para omitir la página de selección de teclado. Esta opción solo está disponible si ha elegido **Implementación automática** como **Modo de implementación**.
    - **Contrato de licencia para el usuario final (CLUF)**: (Windows 10, versión 1709 o posterior) elija si quiere mostrar o no los términos de licencia a los usuarios.
    - **Configuración de privacidad**: elija si quiere mostrar o no la configuración de privacidad a los usuarios.
    - **Ocultar las opciones para cambiar la cuenta (solo Windows Insider)**: elija **Ocultar** para que no se muestren las opciones para cambiar la cuenta en las páginas de inicio de sesión de la empresa y de error del dominio. Esta opción requiere la [configuración de la personalización de marca de la empresa en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding).
    - **Tipo de cuenta de usuario**: elija si el tipo de cuenta de usuario es de **Administrador** o de usuario **Estándar**.
    - **Aplicar la plantilla del nombre de equipo (solo Windows Insider)**: elija **Sí** para crear una plantilla y utilizarla al asignar un nombre a un dispositivo durante el aprovisionamiento. Los nombres deben tener 15 caracteres o menos, y pueden contener letras, números y guiones. Los nombres no pueden estar formados solo por números. Use la [macro %SERIAL%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) para agregar el número de serie de hardware específico. También puede usar la [macro %RAND:x%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) para agregar una cadena de números aleatoria, donde X equivale al número de dígitos para agregar. 

6. Elija **Crear** para crear el perfil. Ahora el perfil de implementación AutoPilot se puede asignar a los dispositivos.

*Tanto **Idioma (región)** como **Configurar el teclado automáticamente** estarán disponibles únicamente si ha elegido **Implementación automática (versión preliminar)** como **Modo de implementación**  (requiere la compilación de [Windows 10 Insider Preview](https://docs.microsoft.com/windows-insider/at-work-pro/) más reciente).


## <a name="assign-an-autopilot-deployment-profile-to-a-device-group"></a>Asignar un perfil de implementación de AutoPilot a un grupo de dispositivos

1. En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Perfiles de implementación** y seleccione un perfil.
2. En la hoja del perfil en cuestión, elija **Asignaciones**. 
3. Elija **Seleccionar grupos** y, en la hoja **Seleccionar grupos**, seleccione los grupos de dispositivos a los que quiera asignar el perfil. Tras ello, elija **Seleccionar**.

## <a name="edit-an-autopilot-deployment-profile"></a>Editar un perfil de AutoPilot Deployment
Cuando haya creado un perfil de AutoPilot Deployment, puede editar ciertas partes del perfil de implementación.   

1. En [Intune en el portal de Azure](https://aka.ms/intuneportal), seleccione **Inscripción de dispositivos**.
2. En la sección **Windows AutoPilot** de **Inscripción de Windows**, elija **Perfiles de implementación**.
3. Seleccione el perfil que quiera editar.
4. Haga clic en **Propiedades**, a la izquierda, para cambiar el nombre o la descripción del perfil de implementación. Después de realizar cambios, haga clic en **Guardar**.
5. Para realizar cambios en la configuración rápida, haga clic en **Configuración**. Después de realizar cambios, haga clic en **Guardar**.

> [!NOTE]
> Los cambios realizados en el perfil se aplican a los dispositivos asignados a ese perfil. En cambio, el perfil actualizado no se aplicará a dispositivos que ya se hayan inscrito en Intune hasta que el dispositivo se restablezca y se vuelva a inscribir.

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Alertas de dispositivos sin asignar de Windows AutoPilot <!-- 163236 -->
Puede ver una alerta para saber cuántos dispositivos del programa AutoPilot no tienen asignados perfiles de implementación de AutoPilot. Use la información provista en la alerta para crear perfiles y asignarlos a los dispositivos sin asignar. Al hacer clic en la alerta, verá una lista completa de dispositivos de Windows AutoPilot e información detallada sobre ellos.

Para ver alertas sobre los dispositivos sin asignar, en [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Información general** > **Dispositivos sin asignar**.  


## <a name="assign-a-user-to-a-specific-autopilot-device"></a>Asignación de un usuario a un dispositivo Autopilot específico

Puede asignar un usuario a un dispositivo Autopilot específico. Esta asignación rellena previamente la página de inicio de sesión de [marca de la empresa](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding) con un usuario de Azure Active Directory durante la configuración de Windows. También permite establecer un nombre personalizado para el saludo. Esta operación no rellena previamente ni modifica el inicio de sesión de Windows. Solo los usuarios con licencia de Intune pueden asignarse de esta manera.

Requisitos previos: se ha configurado el Portal de empresa de Azure Active Directory y la [compilación de Windows 10 Insider Preview](https://docs.microsoft.com/windows-insider/at-work-pro/) más reciente.

1. En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Dispositivos** > elija el dispositivo > **Asignar usuario**.
    ![Captura de pantalla de la asignación del usuario](media/enrollment-autopilot/assign-user.png)
2. Elija un usuario de Azure con licencia para usar Intune y elija **Seleccionar**.
    ![Captura de pantalla de la selección del usuario](media/enrollment-autopilot/select-user.png)
3. En el cuadro **Nombre descriptivo**, escriba uno o acepte el predeterminado. Este es el nombre descriptivo que se mostrará cuando el usuario inicie sesión durante la configuración de Windows.
    ![Captura de pantalla del nombre descriptivo](media/enrollment-autopilot/friendly-name.png)
4. Elija **Aceptar**.


## <a name="delete-autopilot-devices"></a>Eliminación de dispositivos AutoPilot

Los dispositivos Windows AutoPilot que no estén inscritos se pueden eliminar.

1. Si los dispositivos están inscritos en Intune, antes hay que [eliminarlos del portal de Azure Active Directory](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Dispositivos**.

3. En **Dispositivos Windows AutoPilot**, elija los dispositivos que quiere eliminar y, luego, elija **Eliminar**.

4. Para confirmar la eliminación, elija **Sí**. Esta operación puede tardar unos minutos.

## <a name="using-autopilot-in-other-portals"></a>Usar AutoPilot en otros portales
Si no está interesado en la administración de dispositivos móviles, puede usar AutoPilot en Tienda Microsoft para Empresas, por ejemplo. Aunque tiene la opción de usar otros portales, le recomendamos que use solo Intune para administrar las implementaciones de AutoPilot. Si usa Intune y otro portal, Intune no podrá:
- Mostrar los cambios realizados en perfiles creados en Intune, pero editados en otro portal.
- Sincronizar los perfiles creados en otro portal.
- Mostrar los cambios efectuados en las asignaciones de perfil realizadas en otro portal.
- Sincronizar los cambios efectuados en las asignaciones de perfil realizadas en otro portal.
- Mostrar los cambios en la lista de dispositivos que se realizaron en otro portal

## <a name="next-steps"></a>Pasos siguientes
Después de configurar Windows AutoPilot en dispositivos Windows 10 registrados, infórmese sobre cómo administrar los dispositivos. Para obtener más información, consulte [¿Qué es la administración de dispositivos de Microsoft Intune?](https://docs.microsoft.com/intune/device-management)
