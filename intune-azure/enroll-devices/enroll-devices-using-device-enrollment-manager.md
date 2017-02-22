---
title: "Inscripción de dispositivos: administrador de inscripción de dispositivos | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Azure: use la cuenta del administrador de inscripción de dispositivos para inscribir dispositivos en Intune. "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 521a37044d6721fe905db7740329688ba2c24b35
ms.openlocfilehash: 1ab58388f3d126d5d831c65ad3342ec87fb77b91

---

# <a name="enroll-devices-using-device-enrollment-manager"></a>Inscripción de dispositivos mediante el administrador de inscripción de dispositivos

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Las organizaciones pueden usar Intune para administrar un gran número de dispositivos móviles con una sola cuenta de usuario. La cuenta del *administrador de inscripción de dispositivos (DEM)* es una cuenta de usuario especial de Intune con permisos para inscribir hasta 1000 dispositivos. Agregue usuarios existentes a la cuenta del DEM para proporcionarles capacidades de DEM especiales. Cada dispositivo inscrito usa una sola licencia. Recomendamos que utilice dispositivos inscritos mediante esta cuenta como dispositivos compartidos en lugar de dispositivos personales ("BYOD").  

Los usuarios deben existir en Azure Portal para agregarlos como administradores de inscripción de dispositivos. Para lograr una seguridad óptima, el usuario DEM no debería ser también un administrador de Intune.

>[!NOTE]
>No se puede usar el método de inscripción de DEM con estos otros métodos de inscripción: [Apple Configurator con el Asistente de instalación](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md), [Apple Configurator con inscripción directa](enroll-ios-devices-with-apple-configurator-and-direct-enrollment.md) o [programa de inscripción de dispositivos](enroll-ios-devices-using-device-enrollment-program.md). 

## <a name="example-of-a-device-enrollment-manager-scenario"></a>Ejemplo de escenario de administrador de inscripción de dispositivos

Un restaurante quiere proporcionar 50 tabletas de punto de venta para los camareros y monitores de pedidos para el personal de cocina. Los empleados nunca necesitan acceder a los datos de la empresa ni iniciar sesión como usuarios. El administrador de Intune crea una cuenta de administrador de inscripción de dispositivos y agrega un supervisor de restaurante a la cuenta DEM y le proporciona capacidades DEM. El supervisor puede inscribir ahora los 50 dispositivos de tabletas mediante las credenciales DEM.

Solo los usuarios de la consola Intune pueden ser administradores de inscripción de dispositivos. El usuario administrador de inscripción de dispositivos no puede ser un administrador de Intune.

El usuario DEM puede:

-   Inscribir hasta 1000 dispositivos en Intune.
-   Iniciar sesión en el portal de empresa para obtener aplicaciones de empresa.
-   Configure el acceso a datos de la empresa mediante la implementación de aplicaciones específicas del rol a las tabletas.

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

1.  En el portal de Azure, elija **More Services** (Más servicios), escriba **Intune** en el cuadro de texto y luego seleccione **Other** (Otros)  > **Intune**.

2.  En la hoja de Intune, elija **Inscribir dispositivos** y luego elija **Administradores de inscripción de dispositivos**.

3.  Seleccione **Agregar**.

4.  En la hoja **Agregar usuario**, escriba un nombre principal de usuario para el usuario de DEM y seleccione **Agregar**. El usuario DEM se agrega a la lista de usuarios DEM.

## <a name="remove-a-device-enrollment-manager"></a>Eliminación de un administrador de inscripción de dispositivos

La eliminación de un administrador de inscripción de dispositivos no afecta a los dispositivos inscritos. Cuando se elimina un administrador de inscripción de dispositivos:

-   Al quitar un usuario de la lista de usuarios DEM, los dispositivos inscritos no resultan afectados y siguen estando completamente administrados.

-   Las credenciales de la cuenta del administrador de inscripción de dispositivos eliminado siguen siendo válidas.

-   El administrador de inscripción de dispositivos eliminado aún no puede borrar ni retirar dispositivos.

-   El administrador de inscripción de dispositivos eliminado no puede inscribir dispositivos adicionales salvo que el administrador de Intune no haya alcanzado el límite configurado por dispositivo.

**Eliminación de un administrador de inscripción de dispositivos**

1. En la hoja de Intune, elija **Inscribir dispositivos** y luego elija **Administradores de inscripción de dispositivos**.

2. En la hoja **Administradores de inscripción de dispositivos**, haga clic con el botón derecho en el usuario DEM y seleccione **Quitar**.

## <a name="view-the-properties-of-a-device-enrollment-manager"></a>Visualización de las propiedades de un administrador de inscripción de dispositivos

1. En la hoja de Intune, elija **Inscribir dispositivos** y luego elija **Administradores de inscripción de dispositivos**.

2. En la hoja **Administradores de inscripción de dispositivos**, haga clic con el botón derecho en el usuario DEM y seleccione **Propiedades**.



<!--HONumber=Feb17_HO1-->


