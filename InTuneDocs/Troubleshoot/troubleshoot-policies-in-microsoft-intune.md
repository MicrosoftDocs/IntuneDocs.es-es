---
title: "Directivas de solución de problemas | Microsoft Intune"
description: "Solucionar problemas de configuración de directivas."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ms.reviewer: tscott
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a5256d4decfcd14de2d50a32a0906b6894639010
ms.openlocfilehash: 8b2f725dd71a9d5da5387c543261df8607be6d6f


---

# Directivas de solución de problemas en Microsoft Intune

Si tiene problemas de implementación y administración de directivas con Intune, empiece aquí. Este tema contiene algunos problemas comunes que puede encontrar, junto con sus soluciones.

## Problemas generales

### ¿Se aplicó una directiva implementada en el dispositivo?
**Problema:** no está seguro de si una directiva se aplicó correctamente.

En la consola de administración de Intune, cada dispositivo tiene una pestaña de directivas en **Propiedades del dispositivo**. Cada directiva tiene un **Valor previsto** y un **Estado**. El valor previsto es lo que tenía pensado lograr al asignar la directiva. El estado es lo que se aplica realmente cuando todas las directivas aplicables al dispositivo, así como las restricciones y los requisitos del hardware y el sistema operativo, se tienen en cuenta conjuntamente. Los estados posibles son:

-   **Cumple**: el dispositivo recibió la directiva e indica al servicio que se ajusta a la configuración.

-   **No aplicable**: la configuración de la directiva no es aplicable. Por ejemplo, la configuración de correo electrónico para dispositivos iOS no se aplicaría a un dispositivo Android.

-   **Pendiente**: la directiva se ha enviado al dispositivo, pero no se ha informado de su estado al servicio. Por ejemplo, el cifrado en Android requiere que el usuario lo habilite y, por tanto, la directiva podría estar pendiente.

En la captura de pantalla que tiene a continuación se pueden ver dos ejemplos claros:

-   **Permitir contraseñas sencillas** está configurado como **Sí**, como se muestra en la columna **Valor previsto**, pero su **Estado** es **No aplicable**. Esto es porque no se admiten contraseñas sencillas para dispositivos Android.

-   De forma similar, el elemento de directiva expandido **Configuración de correo electrónico para dispositivos iOS** no se aplica a este dispositivo, ya que es un dispositivo Android.

![Directiva de dispositivos de Intune](../media/Intune-Device-Policy-v.2.jpg)

> [!NOTE]
> Recuerde que cuando dos directivas con distintos niveles de restricción se aplican al mismo dispositivo o usuario, la directiva más restrictiva se aplica en la práctica.


## Problemas con los dispositivos inscritos

### Alerta: error al guardar las reglas de acceso en Exchange
**Problema**: recibe la alerta **Error al guardar las reglas de acceso en Exchange** en la consola de administración.

Si creó directivas en el área de trabajo de la directiva local de Exchange en la consola de administración, pero usa Office 365, Intune no aplica las opciones configuradas de la directiva. Tenga en cuenta el origen de la directiva de la alerta.  En el área de trabajo de la directiva local de Exchange, elimine las reglas heredadas ya que son reglas de Exchange globales que se encuentran en el servicio Intune dedicado a Exchange local y no son relevantes para Office 365. A continuación, cree una directiva nueva para Office 365.

### No se puede cambiar la directiva de seguridad de varios dispositivos inscritos
Una vez establecidas las directivas de seguridad a través de MSM o EAS, los dispositivos Windows Phone y Windows RT no permiten que se reduzca el nivel de seguridad de las mismas. Por ejemplo, si establece una **contraseña con un número mínimo** de 8 caracteres, no podrá reducirla a 4. Esto es debido a que ya se ha aplicado la directiva más restrictiva en el dispositivo.

Dependiendo de la plataforma del dispositivo, si desea cambiar la directiva a un valor de menos seguro debe restablecer las directivas de seguridad.
Por ejemplo, en el escritorio de Windows RT, deslice el dedo desde la derecha para abrir la barra de **Botones de acceso** y elija **Configuración** &gt; **Panel de control**.  Seleccione el applet **Cuentas de usuario**.
En el menú de navegación izquierdo, hay un vínculo denominado **Restablecer directivas de seguridad** en la parte inferior. Elíjalo y, después, elija el botón **Restablecer directivas**.
En otros dispositivos MDM como Android, Windows Phone 8.1 y posteriores e iOS, es posible que tenga que eliminar la inscripción y volver a hacerla para que pueda aplicar una directiva menos restrictiva.

## Problemas con equipos que ejecutan el cliente de software de Intune

### Errores relacionados con la directiva de Microsoft Intune en policyplatform.log
En los equipos con Windows administrados con el cliente de software de Intune, pueden producirse errores de directiva en el archivo policyplatform.log debido a que haya opciones de configuración no predeterminadas en el Control de cuentas de usuario (UAC) de Windows en el dispositivo. Algunas opciones de configuración no predeterminadas de UAC pueden afectar a las instalaciones de cliente de Microsoft Intune y a la ejecución de directivas.

#### Para resolver los problemas de UAC

1.  Retire el equipo como se describe en [Retirar dispositivos de la administración de Microsoft Intune](/intune/deploy-use/retire-devices-from-microsoft-intune-management).

2.  Espere 20 minutos para que se quite el software de cliente.

    > [!NOTE]
    > No intente quitar el cliente desde Programas y características.

3.  En el menú Inicio, escriba **UAC** para abrir las opciones de Control de cuentas de usuario.

4.  Mueva el control deslizante de las notificaciones a la opción de configuración predeterminada.

### ERROR: No se puede obtener el valor del equipo, 0x80041013
Esto puede ocurrir si la hora del sistema local no está sincronizada por cinco minutos o más. Si la hora del equipo local no está sincronizada, se producirá un error en las transacciones seguras porque las marcas de tiempo no serán válidas.

Para resolver este problema, establezca la hora del sistema local de modo que sea lo más parecida posible a la hora de Internet o a la hora establecida en los controladores de dominio de la red.








### Pasos siguientes
Si esta información de solución de problemas no le ha ayudado, póngase en contacto con el soporte técnico de Microsoft como se describe en [Cómo obtener asistencia para Microsoft Intune](how-to-get-support-for-microsoft-intune.md).



<!--HONumber=Sep16_HO1-->


