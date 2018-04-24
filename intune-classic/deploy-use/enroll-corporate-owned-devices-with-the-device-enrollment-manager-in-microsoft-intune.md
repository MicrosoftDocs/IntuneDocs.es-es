---
title: Inscripción con el administrador de inscripción de dispositivos
description: La cuenta de administrador de inscripción de dispositivos (DEM) puede administrar un gran número de dispositivos móviles corporativos y compartidos con una única cuenta de usuario.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 01/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a23abc61-69ed-44f1-9b71-b86aefc6ba03
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4973e896109589a91891545bbf6db6ca6df45aad
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune"></a>Inscripción de dispositivos propiedad de la empresa con el Administrador de inscripción de dispositivos de Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Las organizaciones pueden usar Intune para administrar un gran número de dispositivos móviles con una sola cuenta de usuario. La cuenta del *administrador de inscripción de dispositivos (DEM)* es una cuenta de usuario especial de Intune con permisos para inscribir hasta 1000 dispositivos. Agregue usuarios existentes a la cuenta del DEM para proporcionarles capacidades de DEM especiales. Cada dispositivo inscrito usa una sola licencia. Recomendamos que use dispositivos inscritos mediante esta cuenta como dispositivos compartidos (es decir, sin afinidad de usuario) en lugar de dispositivos personales (“BYOD”).  

Los usuarios deben existir en Azure Portal para agregarlos como administradores de inscripción de dispositivos. Para lograr una seguridad óptima, el usuario DEM no debería ser también un administrador de Intune.

>[!NOTE]
>No se puede usar el método de inscripción de DEM con el [Asistente de configuración de Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md) o la [inscripción directa](ios-direct-enrollment-in-microsoft-intune.md), la inscripción macOS ni el [método de inscripción de DEP](ios-device-enrollment-program-in-microsoft-intune.md).

## <a name="example-of-a-device-enrollment-manager-scenario"></a>Ejemplo de escenario de administrador de inscripción de dispositivos

Un restaurante quiere proporcionar 50 tabletas de punto de venta para los camareros y monitores de pedidos para el personal de cocina. Los empleados nunca necesitan acceder a los datos de la empresa ni iniciar sesión como usuarios. El administrador de Intune crea una cuenta de administrador de inscripción de dispositivos y agrega un supervisor de restaurante a la cuenta DEM y le proporciona capacidades DEM. El supervisor puede inscribir ahora los 50 dispositivos de tabletas mediante las credenciales DEM.

Solo los usuarios de la consola Intune pueden ser administradores de inscripción de dispositivos. El usuario administrador de inscripción de dispositivos no puede ser un administrador de Intune.

El usuario DEM puede:

-   Inscribir hasta 1000 dispositivos en Intune
-   Usar la aplicación Portal de empresa para obtener aplicaciones de empresa
-   Configurar el acceso a los datos de la empresa implementando aplicaciones específicas del rol en las tabletas

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>Limitaciones de los dispositivos que están inscritos con una cuenta DEM

Los dispositivos inscritos con una cuenta de administrador de inscripción de dispositivos tienen las siguientes limitaciones:

  - No existe un "usuario" del dispositivo específico. Por lo tanto, no hay acceso de datos de la empresa o de correo electrónico. Sin embargo la VPN, por ejemplo, se podría seguir usando para proporcionar aplicaciones para dispositivos con acceso a datos.

  - No hay acceso condicional porque se trata de escenarios por usuario.

  - El usuario DEM no puede anular la inscripción de dispositivos inscritos de DEM en el propio dispositivo mediante el Portal de empresa. El administrador de Intune tiene esta capacidad, pero el usuario DEM no.

  - Solo el dispositivo local aparece en el sitio web o en la aplicación de Portal de empresa.

  - Los usuarios no pueden usar aplicaciones del Programa de Compras por Volumen de Apple (PCV) debido a los requisitos de identificador de Apple por usuario para la administración de aplicaciones.

  - (solo iOS) Si utiliza DEM para inscribir dispositivos iOS, no puede utilizar Apple Configurator o el Programa de Compras por Volumen de Apple (PCV) para inscribir dispositivos.

> [!NOTE]
> Para implementar aplicaciones de empresa en dispositivos administrados por el administrador de inscripción de dispositivos, implemente la aplicación de Portal de empresa como una **Instalación requerida** en la cuenta de usuario del administrador de inscripción de dispositivos.
> Para mejorar el rendimiento, al ver la aplicación de portal de empresa en un dispositivo de DEM solo se muestra el dispositivo local. La administración remota de otros dispositivos de DEM solo puede realizarse desde la consola de administración de Intune.


## <a name="add-a-device-enrollment-manager"></a>Agregar un administrador de inscripción de dispositivos

1. Asegúrese de que el usuario que desea agregar a la cuenta DEM ya existe. Si necesita agregar el usuario, inicie sesión en el [Portal de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=698854) y siga los pasos de [Agregar usuarios individualmente o en masa en el Portal de Office 365](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec).

2. Inicie sesión en la [consola de administración de Microsoft Intune](https://manage.microsoft.com) con sus credenciales de administrador.

3. En el panel de navegación, elija **Administración**, vaya a **Administración de administradores** y seleccione **Administrador de inscripción de dispositivos**. Se abre la página **Administradores de inscripción de dispositivos**.

4. Elija **Agregar...**. Se abre el cuadro de diálogo **Agregar administrador de inscripción de dispositivos** .

5. Escriba el **Id. de usuario** de la cuenta de Intune y, después, elija **Aceptar**.

   El usuario DEM puede ahora inscribir dispositivos móviles mediante el mismo procedimiento que un usuario final usa para un escenario de BYOD en el portal de empresa. El usuario final de administrador puede instalar la aplicación de Portal de empresa e inscribir el dispositivo utilizando sus credenciales DEM en hasta 1000 dispositivos. Para los pasos de inscripción del usuario final para cada plataforma, consulte:

   - [Inscribir el dispositivo iOS en Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)
   - [Inscribir el dispositivo macOS en Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos)
   - [Inscribir el dispositivo Android en Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)
   - [Inscribir el dispositivo Windows en Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows)

## <a name="delete-a-device-enrollment-manager-from-intune"></a>Eliminar un administrador de inscripción de dispositivos de Intune

1.  Inicie sesión en el [portal de administración de Microsoft Intune](https://manage.microsoft.com) con sus credenciales como administrador.

2.  En el panel de navegación, elija **Administración**, vaya a **Administración de administradores** y seleccione **Administrador de inscripción de dispositivos**. Se abre la página **Administradores de inscripción de dispositivos**.

3.  Seleccione el **Usuario** administrador de inscripción de dispositivos que quiere eliminar y elija **Eliminar**. Este usuario no se eliminará de Intune y los dispositivos que este usuario administra permanecerán inscritos en Intune. Eliminar un administrador de inscripción de dispositivos impide que el usuario inscriba más dispositivos en Intune.

4.  Elija **Sí** para confirmar que quiere eliminar el administrador de inscripción de dispositivos.

La eliminación de un administrador de inscripción de dispositivos no afecta a los dispositivos inscritos. Cuando se elimina un administrador de inscripción de dispositivos:

-   Ningún dispositivo inscrito se ve afectado.

-   Los dispositivos inscritos se continuarán administrando de manera completa.

-   Las credenciales de la cuenta del administrador de inscripción de dispositivos eliminado siguen siendo válidas para iniciar sesión en el portal de empresa para tener acceso a las aplicaciones.

-   Las credenciales de la cuenta del administrador de inscripción de dispositivos eliminado todavía no pueden borrar ni retirar dispositivos.

-   La relación de la cuenta del administrador de inscripción de dispositivos eliminado se mantiene pero no se pueden inscribir dispositivos adicionales.
