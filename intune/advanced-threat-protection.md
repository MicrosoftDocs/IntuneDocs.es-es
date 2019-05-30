---
title: Uso de ATP de Windows Defender en Microsoft Intune - Azure | Microsoft Docs
description: Consulte cómo habilitar la Protección contra amenazas avanzada (ATP) de Windows Defender en un escenario de un extremo a otro, incluida la activación de ATP en Intune y el Centro de seguridad de Windows Defender (portal de ATP), incorporar dispositivos con un perfil de configuración de protección ATP, crear una directiva de configuración de cumplimiento de dispositivo de Intune, crear una directiva de acceso condicional de Azure AD y supervisar el cumplimiento de dispositivo.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a53ae7f43f135f7316b665672dc410812ef14d08
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66050129"
---
# <a name="enforce-compliance-for-windows-defender-atp-with-conditional-access-in-intune"></a>Aplicación del cumplimiento de ATP de Windows Defender con acceso condicional en Intune

La Protección contra amenazas avanzada (ATP) de Windows Defender y Microsoft Intune funcionan conjuntamente para ayudar a evitar infracciones de seguridad y limitar el impacto de dichas infracciones dentro de una organización.

Esta característica se aplica a: Dispositivos Windows 10

Por ejemplo, alguien envía datos adjuntos de Word con código malintencionado insertado a un usuario dentro de su organización. El usuario abre los datos adjuntos y habilita el contenido. Se inicia un ataque con privilegios elevados y un atacante desde una máquina remota tiene derechos de administrador al dispositivo de la víctima. Después, el atacante, accede remotamente a otros dispositivos del usuario.

Esta infracción de seguridad puede afectar a toda la organización.

ATP de Windows Defender puede resolver eventos de seguridad como el de este escenario. El Centro de seguridad de Windows Defender (consola ATP) informa que los dispositivos son de “alto riesgo” e incluye un informe detallado de una actividad sospechosa. En nuestro ejemplo, ATP de Windows Defender detecta que el dispositivo ejecutó código anómalo, experimentó un aumento de privilegios de proceso, inyectó código malintencionado y emitió un shell remoto sospechoso. Después, ATP de Windows Defender le ofrece opciones para mitigar la amenaza.

Mediante Intune, puede crear una directiva de cumplimiento que determine un nivel de riesgo aceptable. Si un dispositivo supera este riesgo, el dispositivo pasa a ser no compatible. Cuando se combina con el Acceso condicional de Azure Active Directory (AD), el usuario tiene el acceso bloqueado desde los recursos corporativos.

En este artículo se muestra cómo:

- Habilitar Intune en ATP y viceversa. Estas tareas crean una conexión de servicio a servicio entre Intune y ATP de Windows Defender. Esta conexión permite que ATP de Windows Defender escriba el riesgo de máquina para los dispositivos de Intune.
- Crear la directiva de cumplimiento en Intune.
- Habilitar el acceso condicional en Azure Active Directory (AD) en los dispositivos según su nivel de amenaza.

## <a name="prerequisites"></a>Requisitos previos

Para usar ATP con Intune, asegúrese de que tiene lo siguientes configurado y listo para usar:

- Inquilino con licencia para Enterprise Mobility + Security E3 y Windows E5 (o Microsoft 365 Enterprise E5)
- Entorno de Microsoft Intune, con dispositivos Windows 10 [administrados por Intune](windows-enroll.md) que también están unidos a Azure AD
- [ATP de Windows Defender](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) y acceso al Centro de seguridad de Windows Defender (portal de ATP)

## <a name="enable-windows-defender-atp-in-intune"></a>Habilitación de ATP de Windows Defender en Intune

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Cumplimiento del dispositivo** > **ATP de Windows Defender** > **Abrir el Centro de seguridad de Windows Defender**.

    ![Seleccionar para abrir el Centro de seguridad de Windows Defender](./media/atp-device-compliance-open-windows-defender.png)

4. En el **Centro de seguridad de Windows Defender**:
    1. Seleccione **Configuración** > **Características avanzadas**.
    2. Para **Microsoft Intune connection** (Conexión con Intune), elija **Activado**:

        ![Habilitar la conexión a Intune](./media/atp-security-center-intune-toggle.png)

    3. Seleccione **Guardar preferencias**.

5. Vuelva a Intune, **Cumplimiento del dispositivo** > **ATP de Windows Defender**. Establezca **Conectar dispositivos Windows de la versión 10.0.15063 y posteriores a ATP de Windows Defender** en **Activado**.
6. Seleccione **Guardar**.

Por lo general, esta tarea se realiza una vez. Por tanto, si ATP ya se ha habilitado en el recurso de Intune, no necesita hacerlo de nuevo.

## <a name="onboard-devices-using-a-configuration-profile"></a>Incorporación de dispositivos mediante un perfil de configuración

Cuando un usuario se inscribe en Intune, se pueden insertar varios valores al dispositivo mediante un perfil de configuración. Esto también se aplica a ATP de Windows Defender.

Windows Defender incluye un paquete de configuración de carga que se comunica con los [servicios de ATP de Windows Defender](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) para examinar los archivos, detectar las amenazas e informar del riesgo a ATP de Windows Defender.

Cuando lo cargue, Intune obtendrá un paquete de configuración generado automáticamente de ATP de Windows Defender. Cuando el perfil se inserte o se implemente en el dispositivo, este paquete de configuración también se insertará en el dispositivo. Ello permite que ATP de Windows Defender supervise el dispositivo para ver si hay amenazas.

Una vez incorporado un dispositivo mediante el paquete de configuración, no es necesario que vuelva a hacerlo. También puede incorporar dispositivos mediante una [directiva de grupo o System Center Configuration Manager (SCCM)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-windows-defender-advanced-threat-protection).

### <a name="create-the-configuration-profile"></a>Creación de un perfil de configuración

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba la información que desee en **Nombre** y **Descripción**.
4. En **Plataforma**, seleccione **Windows 10 y versiones posteriores**.
5. En **Tipo de perfil**, seleccione **ATP de Windows Defender (Windows 10 Desktop)**.
6. Defina la configuración:

  - **Tipo de paquete de configuración del cliente ATP de Windows Defender**: seleccione **Incorporar** para agregar el paquete de configuración al perfil. Seleccione **Cesar** para quitar el paquete de configuración del perfil.
  
    > [!NOTE] 
    > Si ha establecido correctamente una conexión con ATP de Windows Defender, Intune **incorporará** automáticamente el perfil de configuración, mientras que la configuración **Tipo de paquete de configuración del cliente ATP de Windows Defender** no estará disponible.
  
  - **Uso compartido de muestras para todos los archivos**: la opción **Habilitar** permite recopilar muestras y compartirlas con ATP de Windows Defender. Por ejemplo, si ve un archivo sospechoso, puede enviarlo a ATP de Windows Defender para un análisis profundo. **No configurado**: no se comparte ninguna muestra con ATP de Windows Defender.
  - **Frecuencia de informes de telemetría urgentes**: para los dispositivos que presentan un riesgo alto, **habilite** esta opción para informar de la telemetría al servicio de ATP de Windows Defender con más frecuencia.

    [Incorporar máquinas Windows 10 con System Center Configuration Manager](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-sccm-windows-defender-advanced-threat-protection) tiene más detalles sobre estas configuraciones de ATP de Windows Defender.

7. Seleccione **Aceptar** y **Crear** para guardar los cambios, lo que crea el perfil.

## <a name="create-the-compliance-policy"></a>Creación de la directiva de cumplimiento
La directiva de cumplimiento determina un nivel de riesgo aceptable en un dispositivo.

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Cumplimiento del dispositivo** > **Directivas** > **Crear directiva**.
3. Escriba la información que desee en **Nombre** y **Descripción**.
4. En **Plataforma**, seleccione **Windows 10 y versiones posteriores**.
5. En la configuración de **ATP de Windows Defender**, establezca **Solicitar que el dispositivo tenga o esté por debajo de la puntuación de riesgo de la máquina** en el nivel que prefiera. Las clasificaciones de nivel de amenaza vienen [determinadas por ATP de Windows Defender](https://review.docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/alerts-queue-windows-defender-advanced-threat-protection?branch=atp-server2008#sort-filter-and-group-the-alerts-queue).

   - **Borrar**: este nivel es el más seguro. El dispositivo no puede tener ninguna amenaza existente y aún puede acceder a los recursos de la empresa. Si se encuentra alguna amenaza, el dispositivo se clasificará como no conforme. (ATP de Windows Defender usa el valor *Seguro*).
   - **Baja**: el dispositivo se evalúa como compatible si solo hay amenazas de nivel bajo. Los dispositivos con niveles de amenaza medio o alto no son compatibles.
   - **Medio**: el dispositivo se evalúa como compatible si las amenazas que se encuentran en él son de nivel bajo o medio. Si se detectan amenazas de nivel alto, se determinará que el dispositivo no es compatible.
   - **Alto**: este nivel es el menos seguro, ya que permite todos los niveles de amenaza. Por tanto, los dispositivos con niveles de amenaza alto, medio o bajo se consideran compatibles.

6. Seleccione **Aceptar** y **Crear** para guardar los cambios (y crear la directiva).

## <a name="assign-the-policy"></a>Asignación de la directiva

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Cumplimiento del dispositivo** > **Directivas**> Seleccione la directiva de cumplimiento de ATP de Windows Defender.
3. Seleccione **Asignaciones**.
4. Incluya o excluya los grupos de Azure AD para asignarlos a la directiva.
5. Para implementar la directiva a los grupos, seleccione **Guardar**. Se evalúa el cumplimiento por parte de los dispositivos de usuario a los que se aplique la directiva.

## <a name="create-a-conditional-access-policy"></a>Creación de una directiva de acceso condicional
La directiva de acceso condicional bloquea el acceso a los recursos *s i* el dispositivo no es compatible. Por tanto, si un dispositivo supera el nivel de amenaza, puede bloquear el acceso a recursos corporativos, como SharePoint o Exchange Online.  

> [!TIP]  
> Acceso condicional es una tecnología de Azure Active Directory (Azure AD). El nodo de acceso condicional al que se accede desde *Intune* es el mismo nodo al que se accede desde *Azure AD*.  

1. En [Azure Portal](https://portal.azure.com), elija **Intune** > **Acceso condicional** > **Nueva directiva**.
2. En **Nombre**, escriba un nombre de directiva y seleccione **Usuarios y grupos**. Utilice las opciones Incluir o Excluir para agregar los grupos para la directiva y seleccione **Listo**.
3. Seleccione **Aplicaciones en la nube** y elija las aplicaciones que desea proteger. Por ejemplo, elija **Seleccionar aplicaciones** y seleccione **Office 365 SharePoint Online** y **Office 365 Exchange Online**.

    Haga clic en **Listo** para guardar los cambios.

4. Seleccione **Condiciones** > **Aplicaciones cliente** para aplicar la directiva a las aplicaciones y los exploradores. Por ejemplo, seleccione **Sí** y habilite **Explorador** y **Aplicaciones móviles y aplicaciones de escritorio**.

    Haga clic en **Listo** para guardar los cambios.

5. Seleccione **Conceder** para aplicar el acceso condicional basado en el cumplimiento del dispositivo. Por ejemplo, seleccione **Conceder acceso** > **requieren que el dispositivo se marquen como compatibles**.

    Elija **Seleccionar** para guardar los cambios.

6. Seleccione **Habilitar directiva** y luego **crear** para guardar los cambios.

[¿Qué es el acceso condicional?](conditional-access.md) es un buen recurso.

## <a name="monitor-device-compliance"></a>Supervisión del cumplimiento del dispositivo
A continuación, supervise el estado de los dispositivos que tienen la directiva de cumplimiento de ATP de Windows Defender.

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Cumplimiento del dispositivo** > **Directiva y cumplimiento**.
3. Busque la directiva de ATP de Windows Defender en la lista y vea qué dispositivos son compatibles o no compatibles.

## <a name="more-good-stuff"></a>Más cosas interesantes
[Acceso condicional de ATP de Windows Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/conditional-access-windows-defender-advanced-threat-protection)  
[Panel de riesgo de ATP de Windows Defender](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection)  
[Introducción a las directivas de cumplimiento de dispositivos de Intune](device-compliance-get-started.md)  
[Acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
