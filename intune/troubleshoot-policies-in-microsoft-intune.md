---
title: 'Solución de problemas de directivas de Microsoft Intune: Azure | Microsoft Docs'
description: Problemas comunes o problemas y soluciones al usar directivas en Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: bb55ddc283ce4633b5057d5b96ae2ed6973dcf8a
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52181775"
---
# <a name="troubleshoot-policies-in-intune"></a>Solución de problemas de directivas en Intune

Si tiene problemas al implementar y administrar las directivas de Intune, empiece aquí. En este artículo se describen algunos problemas comunes que podría experimentar y posibles soluciones.

## <a name="general-issues"></a>Problemas generales

### <a name="was-a-deployed-policy-applied-to-the-device"></a>¿Se aplicó una directiva implementada en el dispositivo?
**Problema:** no está seguro de si una directiva se aplicó correctamente.

En Intune > **Dispositivos** > **Todos los dispositivos** > seleccione el dispositivo > **Configuración del dispositivo**, todos los dispositivos muestran sus directivas. Cada directiva tiene un **estado**. El estado se aplica cuando todas las directivas aplicables al dispositivo, así como las restricciones y los requisitos del hardware y el sistema operativo, se consideran conjuntamente. Los estados posibles son:

- **Cumple**: el dispositivo ha recibido la directiva e indica al servicio que se ajusta a la configuración.

- **No aplicable**: la configuración de directiva no es aplicable. Por ejemplo, la configuración de correo electrónico para dispositivos iOS no se aplicaría a un dispositivo Android.

- **Pendiente**: la directiva se ha enviado al dispositivo, pero no se ha informado de su estado al servicio. Por ejemplo, el cifrado en Android requiere que el usuario final lo habilite y, por tanto, la directiva podría mostrarse como pendiente.

> [!NOTE]
> Cuando dos directivas con distintos niveles de restricción se aplican al mismo dispositivo o usuario, la directiva más restrictiva es la que se aplica.

## <a name="issues-with-enrolled-devices"></a>Problemas con los dispositivos inscritos

### <a name="alert-saving-of-access-rules-to-exchange-has-failed"></a>Alerta: error al guardar las reglas de acceso en Exchange
**Problema**: recibe la alerta **Error al guardar las reglas de acceso en Exchange**  en la consola de administración.

Si creó directivas en el área de trabajo de la directiva local de Exchange en la consola de administración pero usa O365, Intune no aplica las opciones configuradas de la directiva. Tenga en cuenta el origen de la directiva de la alerta.  En el área de trabajo de la directiva local de Exchange, elimine las reglas heredadas. Las reglas heredadas son reglas de Exchange globales en Intune para Exchange local y no son pertinentes para Office 365. A continuación, cree una directiva nueva para Office 365.

### <a name="cannot-change-security-policy-for-various-enrolled-devices"></a>No se puede cambiar la directiva de seguridad en varios dispositivos inscritos
Una vez establecidas las directivas de seguridad mediante MSM o EAS, los dispositivos Windows Phone no permiten que se reduzca el nivel de seguridad de estas. Por ejemplo, si establece una **contraseña con un número mínimo de 8 caracteres** no podrá reducirla a 4. Esto es debido a que ya se ha aplicado la directiva más restrictiva en el dispositivo.

Dependiendo de la plataforma del dispositivo, si desea cambiar la directiva a un valor de menos seguro debe restablecer las directivas de seguridad.

Por ejemplo, en el escritorio de Windows, deslice el dedo desde la derecha para abrir la barra **Accesos**. Elija **Configuración** > **Panel de Control** y seleccione **Cuentas de usuario**. En el lado izquierdo, seleccione el vínculo **Restablecer directivas de seguridad** y elija **Restablecer directivas**.

En otros dispositivos MDM, como Android, Windows Phone 8.1 y versiones posteriores, e iOS, es posible que tenga que eliminar la inscripción en el servicio y volver a hacerla para poder aplicar una directiva menos restrictiva.

## <a name="issues-with-pcs-that-run-the-intune-software-client"></a>Problemas con equipos que ejecutan el cliente de software de Intune

Se aplica al portal clásico.

### <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>Errores relacionados con las directivas de Microsoft Intune en policyplatform.log
Para los equipos Windows con el cliente de software de Intune, los errores de directivas del archivo policyplatform.log pueden ser el resultado de opciones de configuración no predeterminadas en el Control de cuentas de usuario (UAC) de Windows en el dispositivo. Algunas opciones de configuración de UAC no predeterminadas pueden afectar a las instalaciones de cliente de Microsoft Intune y a la ejecución de directivas.

#### <a name="resolve-uac-issues"></a>Resolución de problemas de UAC

1. Retire el equipo. Consulte, [Retirada de dispositivos](devices-wipe.md).

2. Espere 20 minutos a que se quite el software de cliente.

    > [!NOTE]
    > No intente quitar el cliente desde Programas y características.

3. En el menú Inicio, escriba **UAC** para abrir Configuración del Control de cuentas de usuario.

4. Mueva el control deslizante de las notificaciones a la opción de configuración predeterminada.

### <a name="error-cannot-obtain-the-value-from-the-computer-0x80041013"></a>ERROR: No se puede obtener el valor del equipo, 0x80041013
Se produce si la hora del sistema local está desfasada cinco minutos o más. Si el tiempo en el equipo local no está sincronizado, no se podrán llevar a cabo transacciones seguras porque las marcas de tiempo no serán válidas.

Para resolver este problema, establezca la hora del sistema local de modo que sea lo más parecida posible a la hora de Internet o a la hora establecida en los controladores de dominio de la red.

### <a name="next-steps"></a>Pasos siguientes
Si esta información de solución de problemas no le ha ayudado, póngase en contacto con el soporte técnico de Microsoft como se indica en [Cómo obtener asistencia para Microsoft Intune](get-support.md).
