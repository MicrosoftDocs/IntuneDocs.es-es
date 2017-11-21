---
title: "Inscribir dispositivos: Administrador de inscripción de dispositivos"
titlesuffix: Azure portal
description: Use la cuenta del administrador de inscripciones de dispositivos para inscribir dispositivos en Intune. "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0faca372a8bc9a632cf99133b9843b4b219f285c
ms.sourcegitcommit: e692be57ec7044dfc224b70941affbfd7efba421
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/08/2017
---
# <a name="enroll-devices-using-device-enrollment-manager"></a>Inscripción de dispositivos mediante el administrador de inscripción de dispositivos

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Las organizaciones pueden usar Intune para administrar un gran número de dispositivos móviles con una sola cuenta de usuario. La cuenta del *administrador de inscripción de dispositivos (DEM)* es una cuenta de usuario especial de Intune con permisos para inscribir hasta 1000 dispositivos. Agregue usuarios existentes a la cuenta del DEM para proporcionarles capacidades de DEM especiales. Cada dispositivo inscrito usa una sola licencia. Recomendamos que utilice dispositivos inscritos mediante esta cuenta como dispositivos compartidos en lugar de dispositivos personales ("BYOD").  

Los usuarios deben existir en Azure Portal para agregarlos como administradores de inscripción de dispositivos. Para lograr una seguridad óptima, el usuario DEM no debería ser también un administrador de Intune.

>[!NOTE]
>No se puede usar el método de inscripción de DEM con estos otros métodos de inscripción: [Apple Configurator con el Asistente de instalación](apple-configurator-setup-assistant-enroll-ios.md), [Apple Configurator con inscripción directa](apple-configurator-direct-enroll-ios.md), [Apple School Manager (ASM)](apple-school-manager-set-up-ios.md) o el [Programa de inscripción de dispositivos (DEP)](device-enrollment-program-enroll-ios.md).

## <a name="example-of-a-device-enrollment-manager-scenario"></a>Ejemplo de escenario de administrador de inscripción de dispositivos

Un restaurante quiere proporcionar 50 tabletas de punto de venta para los camareros y monitores de pedidos para el personal de cocina. Los empleados nunca necesitan acceder a los datos de la empresa ni iniciar sesión como usuarios. El administrador de Intune crea una cuenta de administrador de inscripción de dispositivos y agrega un supervisor de restaurante a la cuenta DEM y le proporciona capacidades DEM. El supervisor puede inscribir ahora los 50 dispositivos de tabletas mediante las credenciales DEM.

Solo los usuarios de Azure Portal pueden ser administradores de inscripción de dispositivos. El usuario administrador de inscripción de dispositivos no puede ser un administrador de Intune.

El usuario DEM puede:

-   Inscribir hasta 1000 dispositivos en Intune
-   Iniciar sesión en Portal de empresa para obtener aplicaciones de empresa
-   Configurar el acceso a los datos de la empresa implementando aplicaciones específicas del rol en las tabletas

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>Limitaciones de los dispositivos que están inscritos con una cuenta DEM

Los dispositivos inscritos con una cuenta de administrador de inscripción de dispositivos tienen las siguientes limitaciones:

  - Sin acceso por usuario. Dado que los dispositivos no tienen un usuario asignado, el dispositivo no puede acceder a los datos de la compañía ni al correo electrónico. A pesar de ello, se podrían usar, por ejemplo, configuraciones VPN para proporcionar a las aplicaciones de los dispositivos acceso a los datos.
  - No hay acceso condicional porque estos escenarios son por usuario.
  - El usuario DEM no puede anular la inscripción de dispositivos inscritos de DEM en el propio dispositivo mediante el Portal de empresa. El administrador de Intune puede hacerlo, pero el usuario de DEM no.
  - Solo el dispositivo local aparece en el sitio web o en la aplicación de Portal de empresa.
  - Los usuarios no pueden usar aplicaciones del Programa de Compras por Volumen de Apple (PCV) debido a los requisitos de identificador de Apple por usuario para la administración de aplicaciones.
  - (Solo iOS) Si usa DEM para inscribir dispositivos iOS, no podrá usar Apple Configurator, el Programa de inscripción de dispositivos de Apple (DEP) o Apple School Manager (ASM) para inscribir dispositivos.
  - (Solo Android) Existe un límite en cuanto a la cantidad de dispositivos Android for Work que se pueden inscribir con una sola cuenta DEM. Se puede inscribir un máximo de diez dispositivos Android for Work por cada cuenta DEM. Esta limitación no engloba los dispositivos Android heredados.
  - Cada dispositivo requiere una licencia. Más información sobre [licencias de usuario y dispositivo](licenses-assign.md#how-user-and-device-licenses-affect-access-to-services).


> [!NOTE]
> Para implementar aplicaciones de empresa en dispositivos administrados por el administrador de inscripción de dispositivos, implemente la aplicación de Portal de empresa como una **Instalación requerida** en la cuenta de usuario del administrador de inscripción de dispositivos.
> Para mejorar el rendimiento, al ver la aplicación de portal de empresa en un dispositivo de DEM solo se muestra el dispositivo local. La administración remota de otros dispositivos de DEM solo puede realizarse desde la consola de administración de Intune.


## <a name="add-a-device-enrollment-manager"></a>Agregar un administrador de inscripción de dispositivos

1.  En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

2.  En la hoja de Intune, elija **Inscribir dispositivos** y luego elija **Administradores de inscripción de dispositivos**.

3.  Seleccione **Agregar**.

4.  En la hoja **Agregar usuario**, escriba un nombre principal de usuario para el usuario de DEM y seleccione **Agregar**. El usuario DEM se agrega a la lista de usuarios DEM.

## <a name="permissions-for-dem"></a>Permisos para DEM

Para llevar a cabo tareas de inscripción de DEM, se requieren los roles de Azure AD Administrador global o Administrador de servicios de Intune. Estos roles también son necesarios para ver todos los usuarios de DEM, pese a los permisos de RBAC que se enumeran y están disponibles en el rol de usuario personalizado. Los usuarios que no tengan asignado un rol Administrador global o Administrador de servicios de Intune, pero que tengan permiso de lectura para el rol Administradores de inscripciones de dispositivos, solo pueden ver los usuarios de DEM que hayan creado. La compatibilidad del rol RBAC con estas características se anunciarán en el futuro.

Si un usuario no tiene asignado el rol Administrador global o Administrador de servicios de Intune, pero tiene habilitados permisos de lectura para el rol Administradores de inscripciones de dispositivos que tienen asignado, solo podrán ver los usuarios de DEM que hayan creado.

## <a name="remove-a-device-enrollment-manager"></a>Eliminación de un administrador de inscripción de dispositivos

La eliminación de un administrador de inscripción de dispositivos no afecta a los dispositivos inscritos. Cuando se elimina un administrador de inscripción de dispositivos:

-   Los dispositivos inscritos no resultan afectados y seguirán estando totalmente administrados.
-   Las credenciales de la cuenta del administrador de inscripción de dispositivos eliminado siguen siendo válidas.
-   El administrador de inscripción de dispositivos eliminado aún no puede borrar ni retirar dispositivos.
-   El administrador de inscripciones de dispositivos eliminado solo puede inscribir un número de dispositivos hasta el límite por usuario configurada por el administrador de Intune.

**Eliminación de un administrador de inscripción de dispositivos**

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.
2. En la hoja de Intune, elija **Inscribir dispositivos** y luego elija **Administradores de inscripción de dispositivos**.
3. En la hoja **Administradores de inscripción de dispositivos**, haga clic con el botón derecho en el usuario DEM y seleccione **Quitar**.

## <a name="view-the-properties-of-a-device-enrollment-manager"></a>Visualización de las propiedades de un administrador de inscripción de dispositivos

1. En Azure Portal, elija **Inscripción de dispositivos** y luego elija **Administradores de inscripción de dispositivos**.
2. En la hoja **Administradores de inscripción de dispositivos**, haga clic con el botón derecho en el usuario DEM y seleccione **Propiedades**.
