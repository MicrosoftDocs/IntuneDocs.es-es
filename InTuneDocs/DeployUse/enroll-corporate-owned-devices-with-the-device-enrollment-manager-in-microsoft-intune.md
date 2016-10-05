---
title: "Inscribirse con el administrador de inscripción de dispositivos | Microsoft Intune"
description: "La cuenta del administrador de inscripción de dispositivos (DEM) puede administrar un gran número de dispositivos móviles compartidos propiedad de la empresa con una sola cuenta de usuario."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a23abc61-69ed-44f1-9b71-b86aefc6ba03
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e332bbf9aa8f6543950eba7e1fd734b3fb4b1edb
ms.openlocfilehash: ca81a72fe98d454591765296445215a2b574243b


---


# Inscribir dispositivos propiedad de la empresa con el administrador de inscripción de dispositivos de Microsoft Intune
Las organizaciones pueden usar Intune para administrar un gran número de dispositivos móviles con una sola cuenta de usuario. La cuenta del *administrador de inscripción de dispositivos* (DEM) es una cuenta especial de Intune que puede inscribir hasta 1.000 dispositivos. Se recomienda que use dispositivos inscritos a través de esta cuenta como dispositivos compartidos en lugar de dispositivos personales ("BYOD"). Los usuarios no podrán usar aplicaciones de correo electrónico "nativo", por ejemplo.

A modo de ejemplo, puede asignar una cuenta de usuario de administrador de inscripción de dispositivos a un administrador o supervisor de almacén que permita hacer lo siguiente:

-   Inscribir dispositivos en Intune.

-   Iniciar sesión en el portal de empresa para obtener aplicaciones de empresa.

-   Instalar y desinstalar software.

-   Configurar el acceso a los datos de la empresa.


**Escenario de administrador de inscripción de dispositivos:** un restaurante quiere tener tabletas de punto de venta para que las usen los camareros y monitores de pedidos para el personal de cocina. Los empleados no necesitan en ningún momento tener acceso a los datos de la empresa o iniciar sesión como usuarios. El administrador de Intune crea una cuenta de administrador de inscripción de dispositivos e inscribe los dispositivos propiedad de la empresa usando esa cuenta. El administrador también podría dar las credenciales de administrador de inscripción de dispositivos a un responsable del restaurante, para que pueda inscribir y administrar los dispositivos.

El administrador puede implementar aplicaciones específicas de cada rol en los dispositivos del restaurante. Un administrador también puede seleccionar el dispositivo en la consola de Intune y retirarlo de la administración de dispositivos móviles con la consola de administración.

Los dispositivos que se inscriben con una cuenta de administrador de inscripción de dispositivos tienen las limitaciones siguientes:
  - No hay ningún "usuario" de dispositivo específico, por lo que no hay correo electrónico ni acceso a datos de la empresa. Pero VPN, por ejemplo, podría seguir proporcionando a las aplicaciones de dispositivos acceso a los datos.
  - No hay acceso condicional porque estos escenarios dependen de cada usuario.
  - No es posible restablecer estos dispositivos desde el portal de empresa.
  - Solo aparece el dispositivo local en el sitio web o la aplicación del portal de empresa.
  - No pueden usar aplicaciones del Programa de Compras por Volumen (PCV) de Apple debido a los requisitos de los identificadores de Apple por usuario para la administración de aplicaciones.
  - Tampoco se pueden inscribir con Apple Configurator o con el Programa de inscripción de dispositivos de Apple (dispositivos iOS).

> [!NOTE]
> Para implementar aplicaciones de empresa en dispositivos administrados por el administrador de inscripción de dispositivos, implemente la aplicación del portal de empresa como una **instalación requerida** en la cuenta de usuario del administrador de inscripción de dispositivos.
> Para mejorar el rendimiento, cuando se ve la aplicación del portal de empresa en un dispositivo DEM solo se muestra el dispositivo local. La administración remota de otros dispositivos DEM solo se puede realizar desde la consola de administración de Intune.

## Crear cuentas de administrador de inscripción de dispositivos
Las cuentas de administrador de inscripción de dispositivos son cuentas de usuario con permisos para inscribir un gran número de dispositivos propiedad de la empresa. Solo los usuarios de la consola Intune pueden ser administradores de inscripción de dispositivos.

#### Agregar un administrador de inscripción de dispositivos a Intune

1.  Vaya al [portal de cuentas de Microsoft Intune](http://go.microsoft.com/fwlink/?LinkId=698854) e inicie sesión en su cuenta de administrador.

2.  Elija **Agregar usuario**.

3.  Confirme que aparece la cuenta de usuario que será el administrador de inscripción de dispositivos. Si no es así, agregue el usuario eligiendo **Nuevo** y complete el proceso para **agregar usuario**. Es necesaria una licencia de suscripción para cada usuario que acceda al servicio. El administrador de inscripción de dispositivos no puede ser un administrador de Intune. Compruebe si necesita agregar más licencias antes de usar esta característica.

4.  Inicie sesión en la [consola de administración de Microsoft Intune](http://manage.microsoft.com) con sus credenciales de administrador.

5.  En el panel de navegación, elija **Administración**, vaya a **Administración de administradores** y seleccione **Administrador de inscripción de dispositivos**. Se abre la página **Administradores de inscripción de dispositivos**.

6.  Elija **Agregar…**. Se abre el cuadro de diálogo **Agregar administrador de inscripción de dispositivos**.

7.  Escriba el **Id. de usuario** de la cuenta de Intune y, después, elija **Aceptar**. El usuario administrador de inscripción de dispositivos no puede ser un administrador de Intune.

8.  El administrador de inscripción de dispositivos ahora puede inscribir dispositivos móviles mediante el mismo procedimiento que emplea un usuario final para un escenario de BYOD en el portal de empresa.

## Eliminar un administrador de inscripción de dispositivos de Intune

1.  Inicie sesión en el [portal de administración de Microsoft Intune](http://manage.microsoft.com) con sus credenciales de administrador.

2.  En el panel de navegación, elija **Administración**, vaya a **Administración de administradores** y seleccione **Administrador de inscripción de dispositivos**. Se abre la página **Administradores de inscripción de dispositivos**.

3.  Seleccione el **Usuario** administrador de inscripción de dispositivos que quiere eliminar y elija **Eliminar**. Este usuario no se eliminará de Intune y los dispositivos que este usuario administra permanecerán inscritos en Intune. Eliminar un administrador de inscripción de dispositivos impide que el usuario inscriba más dispositivos en Intune.

4.  Elija **Sí** para confirmar que quiere eliminar el administrador de inscripción de dispositivos.

La eliminación de un administrador de inscripción de dispositivos no afecta a los dispositivos inscritos. Cuando se elimina un administrador de inscripción de dispositivos:

-   Esto no afecta a ningún dispositivo inscrito.

-   Los dispositivos inscritos se continuarán administrando de manera completa.

-   Las credenciales de la cuenta del administrador de inscripción de dispositivos eliminado siguen siendo válidas para iniciar sesión en el portal de empresa y acceder a las aplicaciones.

-   Las credenciales de la cuenta del administrador de inscripción de dispositivos eliminado todavía no pueden borrar ni retirar dispositivos.

-   La relación de la cuenta del administrador de inscripción de dispositivos eliminado con los dispositivos inscritos se mantiene, pero no se pueden inscribir dispositivos adicionales.



<!--HONumber=Sep16_HO1-->


