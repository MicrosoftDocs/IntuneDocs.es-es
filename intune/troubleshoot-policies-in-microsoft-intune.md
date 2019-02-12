---
title: 'Solución de problemas de directivas de Microsoft Intune: Azure | Microsoft Docs'
description: Vea cómo se usa la característica de solución de problemas integrada y obtenga información sobre problemas comunes y sus soluciones cuando se usan las directivas de cumplimiento y los perfiles de configuración en Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/29/2019
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
ms.collection: M365-identity-device-management
ms.openlocfilehash: 77e86912870b22168a7e2dd3e146b9410c482744
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55841086"
---
# <a name="troubleshoot-policies-and-profiles-and-in-intune"></a>Solución de problemas de directivas y perfiles en Intune

Microsoft Intune incluye algunas características integradas de solución de problemas. Use estas características para solucionar problemas de directivas de cumplimiento y perfiles de configuración en el entorno.

En este artículo se enumeran algunas técnicas de solución de problemas comunes y se describen algunos problemas que puede experimentar.

## <a name="use-built-in-troubleshooting"></a>Uso de la solución de problemas integrada

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** > seleccione **Intune**.
2. Haga clic en **Solucionar problemas**:

    ![En Intune, vaya a Ayuda y soporte técnico, y haga clic en Solucionar problemas](./media/help-and-support-troubleshoot.png)

3. Haga clic en **Seleccionar el usuario** > seleccione el usuario que tenga un problema > **Seleccionar**.
4. Confirme que se muestran marcas de verificación de color verde para **Licencia de Intune** y **Estado de la cuenta**:

    ![En Intune, haga clic en el usuario y confirme que se muestran marcas de verificación de color verde para el estado en Licencia de Intune y Estado de la cuenta](./media/account-status-intune-license-show-green.png)

    **Vínculos de ayuda**:

    - [Asignar licencias a los usuarios para que puedan inscribir dispositivos en Intune](licenses-assign.md)
    - [Agregar usuarios a Intune](users-add.md)

5. En **Dispositivos**, busque el dispositivo que tenga un problema. Revise las diferentes columnas:

    - **Administrado**: Para que un dispositivo reciba las directivas de configuración o cumplimiento, esta propiedad debe mostrar **MDM** o **EAS/MDM**.

      - Si **Administrado** no está establecido en **MDM** o **EAS/MDM**, el dispositivo no está inscrito. No recibirá las directivas de configuración o cumplimiento hasta que se inscriba.

      - Las directivas de protección de aplicaciones (administración de aplicaciones móviles) no requieren que los dispositivos se inscriban. Para más información, vea [Creación y asignación de directivas de protección de aplicaciones](app-protection-policies.md).

    - **Tipo de combinación de Azure AD**: se debe establecer en **Área de trabajo** o **AzureAD**.
 
      - Si el valor de esta columna es **No registrado**, es posible que haya un problema con la inscripción. Normalmente, anular la inscripción y volver a inscribir el dispositivo resuelve este estado.

    - **Conforme con Intune**: el valor debe ser **Sí**. Si se muestra **No**, es posible que haya un problema con las directivas de cumplimiento, o bien que el dispositivo no se conecte al servicio de Intune. Por ejemplo, es posible que el dispositivo esté apagado o que no tenga una conexión de red. Finalmente, el dispositivo pasa a ser no compatible, posiblemente después de 30 días.

      Para más información, vea [Introducción a las directivas de cumplimiento de dispositivos](device-compliance-get-started.md).

    - **Conforme con Azure AD**: el valor debe ser **Sí**. Si se muestra **No**, es posible que haya un problema con las directivas de cumplimiento, o bien que el dispositivo no se conecte al servicio de Intune. Por ejemplo, es posible que el dispositivo esté apagado o que no tenga una conexión de red. Finalmente, el dispositivo pasa a ser no compatible, posiblemente después de 30 días.

      Para más información, vea [Introducción a las directivas de cumplimiento de dispositivos](device-compliance-get-started.md).

    - **Última conexión**: debe ser una fecha y hora recientes. De forma predeterminada, los servicios de Intune se conectan cada 8 horas.

      - Si el valor de **Última conexión** es superior a 24 horas, es posible que haya un problema con el dispositivo. Un dispositivo que no se puede conectar no puede recibir las directivas de Intune.

      - Para forzar la conexión:
        - En el dispositivo Android, abra la aplicación de Portal de empresa > **Dispositivos** > elija el dispositivo en la lista > **Comprobar configuración del dispositivo**.
        - En el dispositivo iOS, abra la aplicación de Portal de empresa > **Dispositivos** > elija el dispositivo en la lista > **Comprobar configuración**. 
        - En un dispositivo Windows, abra **Configuración** > **Cuentas** > **Acceso profesional o educativo** > seleccione la cuenta o inscripción MDM >  **Información** > **Sincronización**.

    - Seleccione el dispositivo para ver información específica de la directiva.

      En **Conformidad de dispositivos** se muestran los estados de las directivas de cumplimiento asignadas al dispositivo.

      En **Configuración del dispositivo** se muestran los estados de las directivas de configuración asignadas al dispositivo.

      Si no se muestran las directivas esperadas en **Conformidad de dispositivos** o **Configuración del dispositivo**, las directivas no están destinadas correctamente. Abra la directiva y asígnela a este usuario o dispositivo.

      **Estados de directiva**:

      - **No aplicable**: esta directiva no se admite en esta plataforma. Por ejemplo, las directivas de iOS no funcionan en Android. Las directivas de Samsung KNOX no funcionan en dispositivos Windows.
      - **Conflicto**: hay una configuración existente en el dispositivo que Intune no puede invalidar. O bien, ha implementado dos directivas con la misma configuración mediante valores diferentes.
      - **Pendiente**: el dispositivo no se ha conectado a Intune para obtener la directiva. O bien, el dispositivo ha recibido la directiva, pero no ha informado del estado a Intune.
      - **Errores**: busque los errores y las posibles resoluciones en [Solucionar problemas de acceso a los recursos de la empresa](troubleshoot-company-resource-access-problems.md).

      **Vínculos de ayuda**: 

      - [Formas de implementar las directivas de cumplimiento de dispositivos](device-compliance-get-started.md#ways-to-deploy-device-compliance-policies)
      - [Supervisión de las directivas de cumplimiento de dispositivos de Intune](compliance-policy-monitor.md)

## <a name="youre-unsure-if-a-profile-is-correctly-applied"></a>No está seguro de si se ha aplicado correctamente un perfil

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** > seleccione **Intune**.
2. Seleccione **Dispositivos** > **Todos los dispositivos** > seleccione el dispositivo > **Configuración del dispositivo**. 

    Todos los dispositivos enumeran sus perfiles. Cada perfil tiene un **estado**. El estado se aplica cuando todos los perfiles asignados, incluidos los requisitos y las restricciones de hardware y del sistema operativo, se consideran de forma conjunta. Entre los estados posibles se incluyen los siguientes:

    - **Cumple**: el dispositivo ha recibido el perfil y notifica a Intune que cumple la configuración.

    - **No aplicable**: la configuración de perfil no es aplicable. Por ejemplo, la configuración de correo electrónico para dispositivos iOS no se aplica a un dispositivo Android.

    - **Pendiente**: el perfil ha enviado al dispositivo, pero no ha informado del estado a Intune. Por ejemplo, el cifrado en Android requiere que el usuario final lo habilite y, por tanto, la directiva podría mostrarse como pendiente.

**Vínculo de ayuda**: [Supervisar perfiles de dispositivo](device-profile-monitor.md)

> [!NOTE]
> Cuando dos directivas con distintos niveles de restricción se aplican al mismo dispositivo o usuario, la directiva más restrictiva es la que se aplica.

## <a name="alert-saving-of-access-rules-to-exchange-has-failed"></a>Alerta: Error al guardar las reglas de acceso en Exchange

**Problema**: recibe la alerta **Error al guardar las reglas de acceso en Exchange** en la consola de administración.

Si crea directivas en el área de trabajo Directiva de Exchange local (consola de administración) pero usa Office 365, Intune no aplica las opciones configuradas de la directiva. En la alerta, tenga en cuenta el origen de la directiva. En el área de trabajo Directiva de Exchange local, elimine las reglas heredadas. Las reglas heredadas son reglas de Exchange globales en Intune para Exchange local y no son pertinentes para Office 365. Después, cree una directiva para Office 365.

[Solucionar problemas de Intune On-Premises Exchange Connector](troubleshoot-exchange-connector.md) puede ser un buen recurso.

## <a name="cant-change-security-policies-for-enrolled-devices"></a>No se pueden cambiar las directivas de seguridad para los dispositivos inscritos

Una vez establecidas las directivas de seguridad a través de MDM o EAS, los dispositivos Windows Phone no permiten que se reduzca su nivel de seguridad. Por ejemplo, establece una **contraseña con un número mínimo de caracteres** en 8 y después intenta reducirla a 4. Se aplica la directiva más restrictiva al dispositivo.

En función de la plataforma del dispositivo, si quiere cambiar la directiva a un valor menos seguro, es posible que tenga que restablecer las directivas de seguridad.

Por ejemplo, en el escritorio de Windows, deslice el dedo desde la derecha para abrir la barra **Accesos**. Seleccione **Configuración** > **Panel de control** > **Cuentas de usuario**. En el lado izquierdo, seleccione el vínculo **Restablecer directivas de seguridad** y elija **Restablecer directivas**.

En otros dispositivos MDM, como Android, iOS y Windows Phone 8.1, es posible que tenga que retirarlos y volver a inscribirlos para aplicar una directiva menos restrictiva.

[Solución de problemas con la inscripción de dispositivos en Intune](troubleshoot-device-enrollment-in-intune.md) puede ser un buen recurso.

## <a name="pcs-using-the-intune-software-client---classic-portal"></a>Equipos en los que se usa el cliente de software de Intune: portal clásico

> [!NOTE]
> Esta sección se aplica al portal clásico. 

### <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>Errores relacionados con las directivas de Microsoft Intune en policyplatform.log

Para los equipos Windows con el cliente de software de Intune, los errores de directivas del archivo `policyplatform.log` se pueden deber a opciones de configuración no predeterminadas en el Control de cuentas de usuario (UAC) de Windows en el dispositivo. Algunas opciones de configuración de UAC no predeterminadas pueden afectar a las instalaciones de cliente de Microsoft Intune y a la ejecución de directivas.

#### <a name="resolve-uac-issues"></a>Resolución de problemas de UAC

1. Retire el equipo. Consulte, [Retirada de dispositivos](devices-wipe.md).

2. Espere 20 minutos a que se quite el software de cliente.

    > [!NOTE]
    > No intente quitar el cliente desde Programas y características.

3. En el menú Inicio, escriba **UAC** para abrir la configuración de Control de cuentas de usuario.

4. Mueva el control deslizante de la notificación a la configuración predeterminada.

### <a name="error-cannot-obtain-the-value-from-the-computer-0x80041013"></a>ERROR: No se puede obtener el valor del equipo, 0x80041013

Se produce si la hora del sistema local está desfasada cinco minutos o más. Si la hora en el equipo local no está sincronizada, se produce un error en las transacciones seguras porque las marcas de tiempo no son válidas.

Para resolver este problema, establezca la hora del sistema local lo más cerca posible a la hora de Internet. O bien, establezca a la hora en los controladores de dominio en la red.

## <a name="next-steps"></a>Pasos siguientes

Si sigue necesitando ayuda, puede [obtener soporte técnico de Microsoft Intune](get-support.md).
