---
title: Roles de Intune (RBAC) para Microsoft Intune
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda cómo RBAC le permite controlar quién puede realizar acciones y efectuar cambios."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: deea78dcea9ade031441bf12b388a862235a8e9c
ms.openlocfilehash: e60edd86289e0fca2aa03660d8ce782e373c0236
ms.lasthandoff: 03/15/2017


---

# <a name="intune-roles-rbac-for-microsoft-intune"></a>Roles de Intune (RBAC) para Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

En términos sencillo, los **roles** (o RBAC) de Intune le ayudan a controlar quién puede realizar varias acciones de Intune y a quién se aplican esas acciones. Puede usar los roles integrados que abarcan algunos escenarios de Intune comunes, o crear los suyos propios.

Un rol se define mediante:

- **Definición**: el nombre de un rol y los permisos que configura.
- **Miembros**: el usuario o el grupo de usuarios a los que se concederán esos permisos.
- **Ámbito**: los usuarios o dispositivos que puede administrar una persona determinada (el miembro).
- **Asignación**: una vez configurados la definición, los miembros y el ámbito, se asigna el rol.

## <a name="built-in-roles"></a>Roles integrados

Los siguientes roles están integrados en Intune y puede personalizarlos o asignarlos a grupos sin necesidad de ninguna otra configuración.

- **Administrador de Intune**: tiene permisos totales para todas las operaciones de Intune.
- **Administrador de aplicaciones**: administrar e implementa aplicaciones y perfiles.
- **Administrador de directivas de configuración**: administrar e implementa perfiles y opciones de configuración.
- **Departamento de soporte técnico**: realiza tareas remotas y ve información de usuarios y dispositivos.
- **Operador de solo lectura**: ve información en el portal de Intune sin posibilidad de realizar cambios.


## <a name="custom-roles"></a>Roles personalizados

Si ninguno de los roles integrados se adapta a sus necesidades, puede crear uno propio. Para ello, elija valores de configuración que abarquen muchas de las funcionalidades de Intune. Puede ver una lista de los valores de configuración disponibles más adelante en este tema.

### <a name="example"></a>Ejemplo

Contrata a un nuevo administrador de TI que se encargará de implementar y administrar aplicaciones para los usuarios de la oficina de Londres. Los usuarios están en un grupo de Azure AD denominado **Londres**. Quiere asegurarse de que el administrador de TI no pueda implementar aplicaciones para los usuarios de ninguna otra oficina. Realiza las siguientes acciones:

- Asigna el rol integrado **Administrador de aplicaciones** con las siguientes propiedades:
    - **Miembros**: seleccione un grupo que contenga el administrador de TI que implementará las aplicaciones.
    - **Ámbito**: seleccione el grupo de Azure AD **Londres**.

    >[!IMPORTANT]
    >Para crear, editar o asignar roles, la cuenta debe tener uno de los siguientes permisos en Azure AD:
    >- **Administrador de AAD global**
    >- **Administrador del servicio Intune**

### <a name="how-to-create-a-custom-role"></a>Creación de un rol personalizado

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Intune roles** (Roles de Intune).
![Carga de trabajo de control de acceso](./media/axxess-control.png)
1. En la hoja **Roles** de la carga de trabajo **Control de acceso**, elija **Agregar personalizado**.
2. En la hoja **Agregar rol personalizado**, escriba un nombre y una descripción para el nuevo rol y luego haga clic en **Permisos**.
3. En la hoja **Permisos**, elija los permisos que quiere usar con este rol. Puede usar como ayuda la lista de referencia de configuración de roles que aparece más adelante en este tema.
4. Cuando haya terminado, haga clic en **Aceptar**.
5. En la hoja **Agregar rol de personalizado**, haga clic en **Crear**.

El nuevo rol se muestra en la lista de la hoja **Roles**.

## <a name="how-to-assign-a-role"></a>Asignación de un rol

1. En la hoja **Roles** de la carga de trabajo **Control de acceso**, elija el rol personalizado integrado que quiere asignar.
2. En la hoja <*nombre del rol*> - **Propiedades**, elija **Administrar** > **Asignaciones**.
    >[!TIP]
    >En esta hoja, también puede editar o eliminar roles existentes.
3. En la siguiente hoja, elija **Asignar**.
4. En la hoja **Asignaciones de roles**, escriba un **nombre** y una **descripción** opcional para la asignación y luego elija lo siguiente:
    - **Miembros**: seleccione un grupo que contenga el usuario al que quiere conceder los permisos.
    - **Ámbito** seleccione un grupo que contenga los usuarios que tendrá permiso para administrar el miembro anterior.
5. Cuando haya terminado, haga clic en **Aceptar**.

La nueva asignación se muestra en la lista de asignaciones.

## <a name="custom-role-settings-reference"></a>Referencia de la configuración de roles personalizados

Al crear un rol personalizado, puede configurar uno o varios de los siguientes valores:

### <a name="device-configurations"></a>Configuraciones de dispositivo

|||
|-|-|
|**Asignar**|Asignar perfiles de dispositivo a grupos.|
|**Crear**|Crear perfiles de dispositivo.|
|**Eliminar**|Eliminar perfiles de dispositivo.|
|**Lectura**|Leer perfiles de dispositivo y sus propiedades.|
|**Actualizar**|Actualizar los perfiles de dispositivo existentes.|

### <a name="managed-apps"></a>Aplicaciones administradas

|||
|-|-|
|**Asignar**|Asignar aplicaciones administradas a grupos.|
|**Crear**|Agregar nuevas aplicaciones administradas a Intune.|
|**Eliminar**|Eliminar aplicaciones administradas.|
|**Lectura**|Leer aplicaciones administradas y sus propiedades.|
|**Actualizar**|Actualizar aplicaciones administradas existentes.|
|**Eliminación de datos**|Borrar aplicaciones administradas de dispositivos.|

### <a name="managed-devices"></a>Dispositivos administrados

|||
|-|-|
|**Eliminar**|Eliminar dispositivos administrados de Intune.|
|**Lectura**|Ver información sobre los dispositivos administrados en el portal de Intune.|
|**Actualizar**|Actualizar información sobre dispositivos administrados.|

### <a name="mobile-apps"></a>Aplicaciones móviles

|||
|-|-|
|**Asignar**|Asignar aplicaciones móviles a grupos.|
|**Crear**|Agregar nuevas aplicaciones móviles a Intune.|
|**Eliminar**|Eliminar aplicaciones móviles.|
|**Lectura**|Leer aplicaciones móviles y sus propiedades.|
|**Actualizar**|Actualizar aplicaciones móviles existentes.|

### <a name="organization"></a>Organización

|||
|-|-|
|**Lectura**|Leer configuración de inquilino.|
|**Actualizar**|Actualizar configuración de inquilino.|

### <a name="remote-tasks"></a>Tareas remotas

|||
|-|-|
|**Omitir bloqueo de activación**|Quitar el bloqueo de activación de un dispositivo iOS sin el id. de Apple y la contraseña del usuario. |
|**Deshabilitar modo de pérdida**|Deshabilitar el modo de pérdida. El modo de pérdida le permite especificar un mensaje y un número de teléfono que se mostrarán en la pantalla de bloqueo del dispositivo.|
|**Habilitar modo de pérdida**|Habilitar el modo de pérdida. El modo de pérdida le permite especificar un mensaje y un número de teléfono que se mostrarán en la pantalla de bloqueo del dispositivo.|
|**Buscar dispositivo**|-|
|**Reiniciar ahora**|Hace que el dispositivo se reinicie.|
|**Bloqueo remoto**|Bloquea un dispositivo. El propietario del dispositivo debe usar su contraseña para desbloquearlo.|
|**Restablecer código acceso**|Genera una nueva contraseña para el dispositivo que se mostrará en la <device name> hoja de información general.|
|**Retirar**|Quita solo los datos de empresa administrados por Intune. No se quitan datos personales del dispositivo.|
|**Eliminación de datos**|Devuelve el dispositivo a su configuración predeterminada.|



### <a name="telecom-expenses"></a>Gastos de telecomunicaciones

|||
|-|-|
|**Lectura**|Leer la configuración de administración de gastos de telecomunicaciones (TEM).|
|**Actualizar**|Actualizar la configuración de administración de gastos de telecomunicaciones (TEM).|

### <a name="terms-and-conditions"></a>términos y condiciones

|||
|-|-|
|**Asignar**|Asignar términos y condiciones a grupos.|
|**Crear**|Crear configuración de términos y condiciones.|
|**Eliminar**|Eliminar la configuración de términos y condiciones.|
|**Lectura**|Leer la configuración de términos y condiciones en el portal de Intune.|
|**Actualizar**|Actualizar la configuración de términos y condiciones existente.|
