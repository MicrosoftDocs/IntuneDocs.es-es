---
# required metadata

title: Inscribir dispositivos de propiedad corporativa con el administrador de inscripción de dispositivos de Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: a23abc61-69ed-44f1-9b71-b86aefc6ba03

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Inscribir dispositivos propiedad de la empresa con el Administrador de inscripción de dispositivos de Microsoft Intune
Las organizaciones pueden usar Intune para administrar un gran número de dispositivos móviles con una sola cuenta de usuario. El *administrador de inscripción de dispositivos* es una cuenta especial de Intune con permisos para inscribir más de cinco dispositivos. Puede asignar un administrador o supervisor de almacén, por ejemplo, una cuenta de usuario de administrador de inscripción de dispositivos que le permita hacer lo siguiente:

-   Inscribir dispositivos en Intune

-   Iniciar sesión en el portal de empresa para obtener aplicaciones de empresa

-   Instalar y desinstalar software

-   Configurar el acceso a los datos de la empresa

Use la cuenta de administrador de dispositivos únicamente para los dispositivos que no vayan a recibir correo electrónico o inicios de sesión como un usuario específico. Los dispositivos administrados con una cuenta de administrador de dispositivos no se pueden configurar con acceso condicional, dado que también son escenarios por usuario. El administrador del almacén no puede restablecer el dispositivo desde el portal de empresa.

**Ejemplos de escenario de administrador de inscripción de dispositivos:**
Un restaurante quiere tabletas de punto de venta para los camareros y monitores de pedidos para el personal de cocina. Los empleados no necesitan nunca acceder a los datos de la empresa ni iniciar sesión como usuario. El administrador de Intune crea una cuenta de administrador de inscripción de dispositivos e inscribe los dispositivos propiedad de la empresa usando esa cuenta. El administrador también podría dar las credenciales de inscripción de dispositivos a un responsable del restaurante, para que pueda inscribir y administrar los dispositivos.

El administrador puede implementar aplicaciones específicas de cada rol en los dispositivos del restaurante. Un administrador también puede seleccionar el dispositivo en la consola de Intune y retirarlo de la administración de dispositivos móviles con la consola de administración.

> [!NOTE]
> Las cuentas de usuario del administrador de inscripción de dispositivos con más de 20 dispositivos inscritos podrían tener problemas al usar la aplicación Portal de empresa. Para implementar aplicaciones de empresa en dispositivos administrados con el administrador de inscripción de dispositivos, implemente la aplicación Portal de empresa como una **Instalación requerida** en la cuenta de usuario del administrador de inscripción de dispositivos.

## Crear cuentas de administrador de inscripción de dispositivos
Las cuentas de administrador de inscripción de dispositivos son cuentas de usuario con permisos para inscribir un gran número de dispositivos propiedad de la empresa. Solo los usuarios de la consola Intune pueden ser administradores de inscripción de dispositivos.

#### Agregar un administrador de inscripción de dispositivos a Intune

1.  Vaya al [Portal de cuentas Microsoft Intune](http://go.microsoft.com/fwlink/?LinkId=698854) e inicie sesión con su cuenta de administrador.

2.  Haga clic en **Agregar usuario**..

3.  Confirme que aparece la cuenta de usuario que será el administrador de inscripción de dispositivos. Si no es así, agregue el usuario haciendo clic en **Nuevo** y complete el proceso para agregar un usuario. Se requiere una licencia de suscripción para cada usuario que acceda al servicio y el *administrador de inscripción de dispositivos* no puede ser un administrador de Intune. Determine si necesita agregar más licencias antes de usar esta característica.

4.  Inicie sesión en la [consola de administración de Microsoft Intune](http://manage.microsoft.com) con su inicio de sesión como administrador.

5.  En el panel de navegación, haga clic en **Administración**, vaya a **Administración de administradores** y seleccione **Administrador de inscripción de dispositivos**. Se abre la página Administradores de inscripción de dispositivos.

6.  Haga clic en **Agregar...**. Se abre el cuadro de diálogo **Agregar administrador de inscripción de dispositivos** .

7.  Escriba el **Id. de usuario** de la cuenta de Intune y, después, haga clic en **Aceptar**. El usuario administrador de inscripción de dispositivos no puede ser un administrador de Intune.

8.  El administrador de inscripción de dispositivos ahora puede inscribir dispositivos móviles mediante el mismo procedimiento que un usuario final usa para un escenario de BYOD en el portal de empresa.

## Eliminar un administrador de inscripción de dispositivos de Intune

1.  Inicie sesión en el [portal de administración de Microsoft Intune](http://manage.microsoft.com) con su inicio de sesión como administrador.

2.  En el panel de navegación, haga clic en **Administración** y vaya a **Administración de administradores** y seleccione **Administrador de inscripción de dispositivos**. Se abre la página Administradores de inscripción de dispositivos.

3.  Seleccione el **Usuario** administrador de inscripción de dispositivos que quiere eliminar y haga clic en **Eliminar**. Este usuario no se eliminará de Intune y los dispositivos que este usuario administra permanecerán inscritos en Intune. Eliminar un administrador de inscripción de dispositivos impide que el usuario inscriba más dispositivos en Intune.

4.  Haga clic en **Sí** para confirmar que quiere eliminar el administrador de inscripción de dispositivos.

La eliminación de un administrador de inscripción de dispositivos no afecta a los dispositivos inscritos. Cuando se elimina un administrador de inscripción de dispositivos:

-   Ningún dispositivo inscrito se ve afectado

-   Los dispositivos inscritos se continuarán administrando de manera completa

-   Las credenciales de la cuenta del administrador de inscripción de dispositivos eliminado siguen siendo válidas para iniciar sesión en el portal de empresa para tener acceso a las aplicaciones

-   Las credenciales de la cuenta del administrador de inscripción de dispositivos eliminado todavía no pueden borrar ni retirar dispositivos

-   La relación de la cuenta del administrador de inscripción de dispositivos eliminado se mantiene pero no se pueden inscribir dispositivos adicionales


<!--HONumber=May16_HO1-->


