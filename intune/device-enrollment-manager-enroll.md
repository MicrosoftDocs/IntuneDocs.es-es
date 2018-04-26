---
title: Inscripción de dispositivos mediante una cuenta de administrador de inscripción de dispositivos
titlesuffix: Microsoft Intune
description: Use la cuenta del administrador de inscripciones de dispositivos para inscribir dispositivos en Intune. "
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 870d61cce47132b19b4c3d8b7357f84a21a443e4
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="enroll-devices-by-using-a-device-enrollment-manager-account"></a>Inscripción de dispositivos mediante una cuenta de administrador de inscripción de dispositivos

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Las organizaciones pueden usar Intune para administrar un gran número de dispositivos móviles con una sola cuenta de usuario. La cuenta del *administrador de inscripción de dispositivos (DEM)* es una cuenta de usuario especial de Intune con permisos para inscribir hasta 1000 dispositivos. Agregue usuarios existentes a la cuenta del DEM para proporcionarles capacidades de DEM especiales. Cada dispositivo inscrito usa una sola licencia. Recomendamos que utilice dispositivos inscritos mediante esta cuenta como dispositivos compartidos en lugar de dispositivos personales ("BYOD").  

Los usuarios deben existir en [Azure Portal](https://portal.azure.com) para poder agregarlos como administradores de inscripción de dispositivos. Para lograr una seguridad óptima, el usuario DEM no debería ser también un administrador de Intune.

>[!NOTE]
>No se puede usar el método de inscripción de DEM con estos otros métodos de inscripción: [Apple Configurator con el Asistente de instalación](apple-configurator-setup-assistant-enroll-ios.md), [Apple Configurator con inscripción directa](apple-configurator-direct-enroll-ios.md), [Apple School Manager (ASM)](apple-school-manager-set-up-ios.md) o el [Programa de inscripción de dispositivos (DEP)](device-enrollment-program-enroll-ios.md).

## <a name="example-of-a-device-enrollment-manager-scenario"></a>Ejemplo de escenario de administrador de inscripción de dispositivos

Un restaurante quiere proporcionar 50 tabletas de punto de venta para los camareros y monitores de pedidos para el personal de cocina. Los empleados nunca necesitan acceder a los datos de la empresa ni iniciar sesión como usuarios. El administrador de Intune crea una cuenta de administrador de inscripción de dispositivos y agrega un supervisor restaurante a la cuenta DEM. Ahora, el supervisor tiene capacidades DEM. El supervisor puede inscribir ahora los 50 dispositivos de tabletas mediante las credenciales DEM.

Solo los usuarios de [Azure Portal](https://portal.azure.com) pueden ser administradores de inscripción de dispositivos. El usuario administrador de inscripción de dispositivos no puede ser un administrador de Intune.

El usuario DEM puede:

-   Inscribir hasta 1000 dispositivos en Intune
-   Iniciar sesión en Portal de empresa para obtener aplicaciones de empresa
-   Configurar el acceso a los datos de la empresa implementando aplicaciones específicas del rol en las tabletas

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>Limitaciones de los dispositivos que están inscritos con una cuenta DEM

Los dispositivos inscritos con una cuenta de administrador de inscripción de dispositivos tienen las siguientes limitaciones:

  - Sin acceso por usuario. Dado que los dispositivos no tienen un usuario asignado, el dispositivo no puede acceder a los datos de la compañía ni al correo electrónico. A pesar de ello, se podrían usar, por ejemplo, configuraciones VPN para proporcionar a las aplicaciones de los dispositivos acceso a los datos.
  - El usuario DEM no puede anular la inscripción de dispositivos inscritos de DEM en el propio dispositivo mediante el Portal de empresa. El administrador de Intune puede anular la inscripción.
  - Solo el dispositivo local aparece en el sitio web o en la aplicación de Portal de empresa.
  - Los usuarios no pueden usar aplicaciones del Programa de Compras por Volumen de Apple (PCV) con las licencias de usuario debido a los requisitos de identificador de Apple por usuario para la administración de aplicaciones.
  - (Solo iOS) Si usa DEM para inscribir dispositivos iOS, no podrá usar Apple Configurator, el Programa de inscripción de dispositivos de Apple (DEP) o Apple School Manager (ASM) para inscribir dispositivos.
  - (Solo Android) Existe un límite en cuanto a número de dispositivos Android for Work que se pueden inscribir con una sola cuenta DEM. Se puede inscribir un máximo de 10 dispositivos Android for Work por cada cuenta DEM. Esta limitación no engloba los dispositivos Android heredados.
  - Los dispositivos pueden instalar aplicaciones de PCV si disponen de licencias de dispositivo.
  - Cada dispositivo requiere una licencia. Más información sobre [licencias de usuario y dispositivo](licenses-assign.md#how-user-and-device-licenses-affect-access-to-services).


> [!NOTE]
> Puede implementar aplicaciones de empresa en dispositivos administrados por el administrador de inscripción de dispositivos. Implemente la aplicación Portal de empresa como un **instalación requerida** a la cuenta de usuario del administrador de inscripción de dispositivos.
> Para mejorar el rendimiento, al ver la aplicación de portal de empresa en un dispositivo de DEM solo se muestra el dispositivo local. La administración remota de otros dispositivos de DEM solo puede realizarse desde la consola de administración de Intune.


## <a name="add-a-device-enrollment-manager"></a>Agregar un administrador de inscripción de dispositivos

1.  En Intune, en [Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Administradores de inscripción de dispositivos**.

2.  Seleccione **Agregar**.

3.  En la hoja **Agregar usuario**, escriba un nombre principal de usuario para el usuario de DEM y seleccione **Agregar**. El usuario DEM se agrega a la lista de usuarios DEM.

## <a name="permissions-for-dem"></a>Permisos para DEM

Para llevar a cabo tareas de inscripción de DEM, se requieren los roles de Azure AD Administrador global o Administrador de servicios de Intune. Estos roles también son necesarios para ver todos los usuarios de DEM, pese a los permisos de RBAC que se enumeran y están disponibles en el rol de usuario personalizado. Los usuarios que no tengan asignado un rol Administrador global o Administrador de servicios de Intune, pero que tengan permiso de lectura para el rol Administradores de inscripciones de dispositivos, solo pueden ver los usuarios de DEM que hayan creado. La compatibilidad del rol RBAC con estas características se anunciarán en el futuro.

Si un usuario no tiene asignado el rol Administrador global o Administrador de servicios de Intune, pero tiene habilitados permisos de lectura para el rol Administradores de inscripciones de dispositivos que tiene asignado, solo podrá ver los usuarios de DEM que haya creado.

## <a name="remove-a-device-enrollment-manager"></a>Eliminación de un administrador de inscripción de dispositivos

La eliminación de un administrador de inscripción de dispositivos no afecta a los dispositivos inscritos. Cuando se elimina un administrador de inscripción de dispositivos:

-   Los dispositivos inscritos no resultan afectados y seguirán estando totalmente administrados.
-   Las credenciales de la cuenta del administrador de inscripción de dispositivos eliminado siguen siendo válidas.
-   El administrador de inscripción de dispositivos eliminado aún no puede borrar ni retirar dispositivos.
-   El administrador de inscripciones de dispositivos eliminado solo puede inscribir un número de dispositivos hasta el límite por usuario configurada por el administrador de Intune.

**Eliminación de un administrador de inscripción de dispositivos**

1. En [Intune, en Azure Portal](https://aka.ms/intuneportal), seleccione **Inscripción de dispositivos** y, luego, **Administradores de inscripción de dispositivos**.
2. En la hoja **Administradores de inscripción de dispositivos**, seleccione el usuario DEM y **Eliminar**.

## <a name="view-the-properties-of-a-device-enrollment-manager"></a>Visualización de las propiedades de un administrador de inscripción de dispositivos

1. En [Azure Portal](https://portal.azure.com), seleccione **Inscripción de dispositivos** y, luego, **Administradores de inscripción de dispositivos**.
2. En la hoja **Administradores de inscripción de dispositivos**, haga clic con el botón derecho en el usuario DEM y seleccione **Propiedades**.
