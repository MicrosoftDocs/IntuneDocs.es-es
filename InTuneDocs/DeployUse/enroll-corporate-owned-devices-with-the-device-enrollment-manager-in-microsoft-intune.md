---
title: "Inscripción con el administrador de inscripción de dispositivos | Microsoft Intune"
description: "La cuenta de administrador de inscripción de dispositivos (DEM) puede administrar un gran número de dispositivos móviles corporativos y compartidos con una única cuenta de usuario."
keywords: 
author: NathBarn
manager: arob98
ms.date: 07/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a23abc61-69ed-44f1-9b71-b86aefc6ba03
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1f6f98d582ce9a686ca02682a9066d8b2162d6ab
ms.openlocfilehash: d126bbfc40cada71458b03c23e571490b4af4d44


---


# Inscribir dispositivos propiedad de la empresa con el Administrador de inscripción de dispositivos de Microsoft Intune
Las organizaciones pueden usar Intune para administrar un gran número de dispositivos móviles con una sola cuenta de usuario. El *administrador de inscripción de dispositivos* (DEM) es una cuenta especial de Intune con permisos para inscribir hasta 1000 dispositivos. Use dispositivos inscritos mediante la cuenta de administrador de inscripción de dispositivos como dispositivos compartidos en lugar de dispositivos personales ("BYOD"). Por ejemplo, los usuarios no podrán usar aplicaciones de correo electrónico "nativas". Puede asignar un administrador o supervisor de almacén, por ejemplo, una cuenta de usuario de administrador de inscripción de dispositivos que le permita hacer lo siguiente:

-   Inscribir dispositivos en Intune

-   Iniciar sesión en el portal de empresa para obtener aplicaciones de empresa

-   Instalar y desinstalar software

-   Configurar el acceso a los datos de la empresa


**Ejemplos de escenario de administrador de inscripción de dispositivos:** Un restaurante quiere tener tabletas de punto de venta para que las usen los camareros y monitores de pedidos para el personal de cocina. Los empleados no necesitan nunca acceder a los datos de la empresa ni iniciar sesión como usuario. El administrador de Intune crea una cuenta de administrador de inscripción de dispositivos e inscribe los dispositivos propiedad de la empresa usando esa cuenta. El administrador también podría dar las credenciales de inscripción de dispositivos a un responsable del restaurante, para que pueda inscribir y administrar los dispositivos.

El administrador puede implementar aplicaciones específicas de cada rol en los dispositivos del restaurante. Un administrador también puede seleccionar el dispositivo en la consola de Intune y retirarlo de la administración de dispositivos móviles con la consola de administración.

Los dispositivos inscritos con una cuenta de administrador de inscripción de dispositivos tienen las siguientes restricciones:
  - Ningún usuario específico por lo que todos los dispositivos son "user-less"; ningún correo electrónico o acceso a los datos de la empresa mediante una VPN, por ejemplo, todavía puede proporcionar aplicaciones de dispositivos con acceso a los datos
  - Ningún acceso condicional porque son escenarios por usuario
  - No se pueden restablecer los dispositivos del portal de empresa
  - Solo el dispositivo local aparece en el sitio web o en la aplicación de portal de empresa
  - Ninguna aplicación del Programa de Compras por Volumen de Apple debido a los requisitos de identificador de Apple por usuario para la administración de aplicaciones
  - Tampoco puede inscribirse con Apple Configurator o el programa de inscripción de dispositivos de Apple (dispositivos iOS)

> [!NOTE]
> Para implementar aplicaciones de empresa en dispositivos administrados con el administrador de inscripción de dispositivos, implemente la aplicación Portal de empresa como una **Instalación requerida** en la cuenta de usuario del administrador de inscripción de dispositivos.
> Para mejorar el rendimiento, al ver la aplicación de portal de empresa en un dispositivo de DEM solo se muestra el dispositivo local. La administración remota de otros dispositivos de DEM solo puede realizarse desde la consola de administración de Intune.

## Crear cuentas de administrador de inscripción de dispositivos
Las cuentas de administrador de inscripción de dispositivos son cuentas de usuario con permisos para inscribir un gran número de dispositivos propiedad de la empresa. Solo los usuarios de la consola Intune pueden ser administradores de inscripción de dispositivos.

#### Agregar un administrador de inscripción de dispositivos a Intune

1.  Vaya al [Portal de cuentas Microsoft Intune](http://go.microsoft.com/fwlink/?LinkId=698854) e inicie sesión con su cuenta de administrador.

2.  Elija **Agregar usuario**.

3.  Confirme que aparece la cuenta de usuario que será el administrador de inscripción de dispositivos. Si no es así, agregue el usuario al elegir **Nuevo** y complete el proceso para agregar un usuario. Se requiere una licencia de suscripción para cada usuario que acceda al servicio y el *administrador de inscripción de dispositivos* no puede ser un administrador de Intune. Determine si necesita agregar más licencias antes de usar esta característica.

4.  Inicie sesión en la [consola de administración de Microsoft Intune](http://manage.microsoft.com) con su inicio de sesión como administrador.

5.  En el panel de navegación, elija **Administración**, vaya a **Administración de administradores** y seleccione **Administrador de inscripción de dispositivos**. Se abre la página Administradores de inscripción de dispositivos.

6.  Elija **Agregar...**. Se abre el cuadro de diálogo **Agregar administrador de inscripción de dispositivos** .

7.  Escriba el **Id. de usuario** de la cuenta de Intune y, después, elija **Aceptar**. El usuario administrador de inscripción de dispositivos no puede ser un administrador de Intune.

8.  El administrador de inscripción de dispositivos ahora puede inscribir dispositivos móviles mediante el mismo procedimiento que un usuario final usa para un escenario de BYOD en el portal de empresa.

## Eliminar un administrador de inscripción de dispositivos de Intune

1.  Inicie sesión en el [portal de administración de Microsoft Intune](http://manage.microsoft.com) con su inicio de sesión como administrador.

2.  En el panel de navegación, haga clic en **Administración** y vaya a **Administración de administradores** y seleccione **Administrador de inscripción de dispositivos**. Se abre la página Administradores de inscripción de dispositivos.

3.  Seleccione el **Usuario** administrador de inscripción de dispositivos que quiere eliminar y elija **Eliminar**. Este usuario no se eliminará de Intune y los dispositivos que este usuario administra permanecerán inscritos en Intune. Eliminar un administrador de inscripción de dispositivos impide que el usuario inscriba más dispositivos en Intune.

4.  Elija **Sí** para confirmar que quiere eliminar el administrador de inscripción de dispositivos.

La eliminación de un administrador de inscripción de dispositivos no afecta a los dispositivos inscritos. Cuando se elimina un administrador de inscripción de dispositivos:

-   Ningún dispositivo inscrito se ve afectado

-   Los dispositivos inscritos se continuarán administrando de manera completa

-   Las credenciales de la cuenta del administrador de inscripción de dispositivos eliminado siguen siendo válidas para iniciar sesión en el portal de empresa para tener acceso a las aplicaciones

-   Las credenciales de la cuenta del administrador de inscripción de dispositivos eliminado todavía no pueden borrar ni retirar dispositivos

-   La relación de la cuenta del administrador de inscripción de dispositivos eliminado se mantiene pero no se pueden inscribir dispositivos adicionales



<!--HONumber=Jul16_HO4-->


