---
title: Solucionar problemas de directivas
description: "Solucionar problemas de configuración de directivas."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 00f3487ed7f9fe920d89f449703723bfe80eb109
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="troubleshoot-policies-in-microsoft-intune"></a>Directivas de solución de problemas en Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Si tiene problemas al implementar y administrar las directivas de Intune, empiece aquí. En este tema se incluyen algunos problemas comunes que pueden surgir y sus soluciones.

## <a name="general-issues"></a>Problemas generales

### <a name="was-a-deployed-policy-applied-to-the-device"></a>¿Se aplicó una directiva implementada en el dispositivo?
**Problema:** no está seguro de si una directiva se aplicó correctamente.

En la consola de administración de Intune, cada dispositivo tiene una pestaña de directivas en **Propiedades del dispositivo**. Cada directiva tiene un **Valor previsto** y un **Estado**. El valor previsto es lo que tenía pensado lograr al asignar la directiva. El estado es lo que se aplica realmente cuando todas las directivas aplicables al dispositivo, así como las restricciones y los requisitos del hardware y el sistema operativo, se consideran conjuntamente. Los estados posibles son:

-   **Cumple**: el dispositivo ha recibido la directiva e indica al servicio que se ajusta a la configuración.

-   **No es aplicable**: la configuración de directiva no es aplicable. Por ejemplo, la configuración de correo electrónico para dispositivos iOS no se aplicaría a un dispositivo Android.

-   **Pendiente**: la directiva se ha enviado al dispositivo, pero no se ha informado de su estado al servicio. Por ejemplo, el cifrado en Android requiere que el usuario final lo habilite y, por tanto, la directiva puede estar pendiente.

En la captura de pantalla que tiene a continuación se pueden ver dos ejemplos claros:

-   **Permitir contraseñas sencillas** está establecido en **Sí**, como se muestra en la columna **Valor previsto** , pero su **Estado** es **No aplicable**. Esto es porque no se admiten contraseñas sencillas para dispositivos Android.

-   De forma similar, el elemento de directiva expandido**Configuración de correo electrónico para dispositivos iOS** no se aplica a este dispositivo, ya que es un dispositivo Android.

![Directiva de dispositivos de Intune](../media/Intune-Device-Policy-v.2.jpg)

> [!NOTE]
> Recuerde que cuando dos directivas con distintos niveles de restricción se aplican al mismo dispositivo o usuario, la directiva más restrictiva se aplica en la práctica.


## <a name="issues-with-enrolled-devices"></a>Problemas con los dispositivos inscritos

### <a name="alert-saving-of-access-rules-to-exchange-has-failed"></a>Alerta: error al guardar las reglas de acceso en Exchange
**Problema**: recibe la alerta **Error al guardar las reglas de acceso en Exchange**  en la consola de administración.

Si creó directivas en el área de trabajo de la directiva local de Exchange en la consola de administración pero usa O365, Intune no aplica las opciones configuradas de la directiva. Tenga en cuenta el origen de la directiva de la alerta.  En el área de trabajo de la directiva local de Exchange, elimine las reglas heredadas ya que son reglas de Exchange globales que se encuentran en el servicio Intune dedicado a Exchange local y no son relevantes para Office 365. A continuación, cree una directiva nueva para Office 365.

### <a name="cannot-change-security-policy-for-various-enrolled-devices"></a>No se puede cambiar la directiva de seguridad en varios dispositivos inscritos
Una vez establecidas las directivas de seguridad a través de MSM o EAS, los dispositivos Windows Phone no permiten que se reduzca el nivel de seguridad de las mismas. Por ejemplo, si establece una **contraseña con un número mínimo de 8 caracteres** no podrá reducirla a 4. Esto es debido a que ya se ha aplicado la directiva más restrictiva en el dispositivo.

Dependiendo de la plataforma del dispositivo, si desea cambiar la directiva a un valor de menos seguro debe restablecer las directivas de seguridad.
Por ejemplo, en el escritorio de Windows, deslice el dedo desde la derecha para abrir la barra de **Botones de acceso** y seleccione **Configuración** &gt; **Panel de Control**.  Seleccione el applet **Cuentas de usuario** .
En el menú de navegación izquierdo, hay un vínculo denominado **Restablecer las directivas de seguridad** en la parte inferior. Selecciónelo y luego elija el botón **Restablecer directivas**.
En otros dispositivos MDM como Android, Windows Phone 8.1 y posteriores e iOS, es posible que tenga que eliminar la inscripción y volver a hacerla para que pueda aplicar una directiva menos restrictiva.

## <a name="issues-with-pcs-that-run-the-intune-software-client"></a>Problemas con equipos que ejecutan el cliente de software de Intune

### <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>Errores relacionados con las directivas de Microsoft Intune en policyplatform.log
Para los equipos Windows con el cliente de software de Intune, los errores de directivas del archivo policyplatform.log pueden ser el resultado de opciones de configuración no predeterminadas en el Control de cuentas de usuario (UAC) de Windows en el dispositivo. Algunas opciones de configuración de UAC no predeterminadas pueden afectar a las instalaciones de cliente de Microsoft Intune y a la ejecución de directivas.

#### <a name="to-resolve-uac-issues"></a>Para resolver problemas de UAC

1.  Retire el equipo, como se describe en [Retire devices from Microsoft Intune management (Retirar dispositivos de la administración de Microsoft Intune)](/intune-classic/deploy-use/retire-devices-from-microsoft-intune-management).

2.  Espere 20 minutos a que se quite el software de cliente.

    > [!NOTE]
    > No intente quitar el cliente desde Programas y características.

3.  En el menú Inicio, escriba **UAC** para abrir Configuración del Control de cuentas de usuario.

4.  Mueva el control deslizante de la notificación a la opción de configuración predeterminada.

### <a name="error-cannot-obtain-the-value-from-the-computer-0x80041013"></a>ERROR: No se puede obtener el valor del equipo, 0x80041013
Esto puede ocurrir si la hora del sistema local está desfasada cinco minutos o más. Si el tiempo en el equipo local no está sincronizado, no se podrán llevar a cabo transacciones seguras porque las marcas de tiempo no serán válidas.

Para resolver este problema, establezca la hora del sistema local lo más cercana posible a la hora de Internet o la hora establecida en los controladores de dominio en la red.








### <a name="next-steps"></a>Pasos siguientes
Si esta información para solucionar problemas no le ha ayudado, póngase en contacto con el servicio de soporte técnico de Microsoft como se indica en [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico de Microsoft Intune).
