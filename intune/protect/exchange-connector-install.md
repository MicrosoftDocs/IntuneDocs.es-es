---
title: Configuración de una instancia de Microsoft Intune Exchange Connector
titleSuffix: Microsoft Intune
description: Use la instancia de Intune Exchange Connector local para administrar el acceso del dispositivo a los buzones de Exchange en función de la inscripción de Intune y Exchange Active Sync (EAS).
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 30b5debc6e1ab113a08d8930f96f6cbc9bf12b48
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509521"
---
# <a name="set-up-the-on-premises-intune-exchange-connector"></a>Configuración de Intune Exchange Connector local
Para ayudar a proteger el acceso a Exchange, Intune se basa en un componente local conocido como Microsoft Intune Exchange Connector. Este conector también se conoce como *Exchange ActiveSync Connector local* en algunas ubicaciones de la consola de Intune. 

La información de este artículo puede ayudarle a instalar y supervisar Intune Exchange Connector. Puede usar el conector con las [directivas de acceso condicional](conditional-access-exchange-create.md) para permitir o bloquear el acceso a los buzones locales de Exchange. 

El conector se instala y se ejecuta en el hardware local. Detecta dispositivos que se conectan a Exchange y comunican información del dispositivo al servicio de Intune. El conector admite o bloquea dispositivos en función de si los dispositivos están inscritos y son compatibles. Estas comunicaciones usan el protocolo HTTPS.

Cuando un dispositivo intenta acceder al servidor de Exchange local, Exchange Connector asigna registros de Exchange Active Sync (EAS) en Exchange Server a los registros de Intune para asegurarse de que el dispositivo está inscrito en Intune y cumple las directivas del dispositivo. En función de las directivas de acceso condicional, el dispositivo puede admitirse o bloquearse. Consulte [¿Cuáles son las formas habituales de usar el acceso condicional con Intune?](conditional-access-intune-common-ways-use.md) para obtener más información.

Las operaciones de *detección* y *admisión y bloqueo* se realizan mediante los cmdlets de Exchange PowerShell estándar. Estas operaciones utilizan la cuenta de servicio que se proporciona cuando se instala inicialmente Exchange Connector. 

Intune admite la instalación de varias instancias de Intune Exchange Connector por suscripción. Si tiene más de una organización de Exchange local, puede configurar un conector independiente para cada una de ellas. Sin embargo, solo se puede instalar un conector para cada organización de Exchange.  

Para configurar una conexión que permita a Intune comunicarse con una instancia local de Exchange Server, siga estos pasos generales:

1. Descargue el conector local desde el portal de Intune.
2. Instale y configure Exchange Connector en un equipo de la organización de Exchange local.
3. Valide la conexión de Exchange.
4. Repita estos pasos para cada organización adicional de Exchange que quiera conectar a Intune.

## <a name="intune-exchange-connector-requirements"></a>Requisitos de Intune Exchange Connector

Para conectarse a Exchange, necesita una cuenta que tenga una licencia de Intune que el conector pueda usar. La cuenta se especifica al instalar el conector.  

En esta tabla se indican los requisitos del equipo en el que se instala Intune Exchange Connector.  

|  Requisito  |   Más información     |
|---------------|------------------------|
|  Sistemas operativos        | Intune admite Intune Exchange Connector en equipos con Windows Server 2008 SP2 de 64 bits, Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 o Windows Server 2016.<br /><br />El conector no es compatible con ninguna instalación de Server Core.  |
| Microsoft Exchange          | Para la instancia local de Exchange Connector se necesita Microsoft Exchange 2010 SP3 o una versión posterior o Exchange Online dedicado heredado. Para determinar si la configuración de su entorno Exchange Online dedicado es *nueva* o *heredada*, póngase en contacto con su administrador de cuentas. |
| Entidad de administración de dispositivos móviles           | [Establecer la entidad de administración de dispositivos móviles en Intune](../fundamentals/mdm-authority-set.md). |
| Hardware              | El equipo donde se instala el conector debe requiere una CPU de 1,6 GHz con 2 GB de RAM y 10 GB de espacio libre en disco. |
|  Sincronización de Active Directory             | Antes de usar el conector para conectar Intune a su servidor de Exchange, [configure la sincronización de Active Directory](../fundamentals/users-add.md). Los usuarios locales y los grupos de seguridad deben estar sincronizados con su instancia de Azure Active Directory. |
| Software adicional         | El equipo que hospede el conector debe tener una instalación completa de Microsoft .NET Framework 4.5 y Windows PowerShell 2.0. |
| Network (Red)               | El equipo en el que se instala el conector debe estar en un dominio que tenga una relación de confianza con el dominio que hospeda el servidor de Exchange.<br /><br />Configure el equipo para permitirle acceder al servicio de Intune a través de firewalls y servidores proxy mediante los puertos 80 y 443. Intune usa estos dominios: <br> - manage.microsoft.com <br> - \*manage.microsoft.com<br> - \*.manage.microsoft.com <br><br> Intune Exchange Connector se comunica con los siguientes servicios: <br> - Servicio Intune: puerto HTTPS 443 <br> - Servidor de acceso de cliente de Exchange (CAS): puerto del servicio WinRM 443<br> - Detección automática de Exchange 443<br> - Servicios web de Exchange (EWS) 443  |

### <a name="exchange-cmdlet-requirements"></a>Requisitos del cmdlet de Exchange

Cree una cuenta de usuario Active Directory para Intune Exchange Connector. La cuenta debe tener permiso para ejecutar los siguientes cmdlets de Windows PowerShell Exchange:  

- `Get-ActiveSyncOrganizationSettings`, `Set-ActiveSyncOrganizationSettings`
- `Get-CasMailbox`, `Set-CasMailbox`
- `Get-ActiveSyncMailboxPolicy`, `Set-ActiveSyncMailboxPolicy`, `New-ActiveSyncMailboxPolicy`, `Remove-ActiveSyncMailboxPolicy`
- `Get-ActiveSyncDeviceAccessRule`, `Set-ActiveSyncDeviceAccessRule`, `New-ActiveSyncDeviceAccessRule`, `Remove-ActiveSyncDeviceAccessRule`
- `Get-ActiveSyncDeviceStatistics`
- `Get-ActiveSyncDevice`
- `Get-ExchangeServer`
- `Get-ActiveSyncDeviceClass`
- `Get-Recipient`
- `Clear-ActiveSyncDevice`, `Remove-ActiveSyncDevice`
- `Set-ADServerSettings`
- `Get-Command`

## <a name="download-the-installation-package"></a>Descarga del paquete de instalación

1. En un servidor de Windows compatible con Intune Exchange Connector, inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973). Use una cuenta que sea administrador en el servidor local de Exchange y que tenga una licencia para usar Exchange Server.

2. Vaya a **Intune** > **Acceso de Exchange**.  

3. En **Configuración**, elija **Exchange ActiveSync Connector local** y, luego, seleccione **Agregar**.

4. En la página **Agregar conector**, seleccione **Descargar el conector local**. La instancia de Intune Exchange Connector se encuentra en una carpeta comprimida (.zip) que se puede abrir o guardar. En el cuadro de diálogo **Descarga de archivos**, haga clic en **Guardar** para almacenar la carpeta comprimida en una ubicación segura.


## <a name="install-and-configure-the-intune-exchange-connector"></a>Instalación y configuración de Intune Exchange Connector

Siga estos pasos para instalar Intune Exchange Connector. Si tiene varias organizaciones de Exchange, repita estos pasos para cada conector de Exchange que quiera instalar.

1. En un sistema operativo compatible con Intune Exchange Connector, extraiga los archivos de **Exchange_Connector_Setup.zip** en una ubicación segura.
   > [!IMPORTANT]
   > No cambie el nombre de los archivos que se encuentran en la carpeta *Exchange_Connector_Setup* ni los mueva. Estos cambios harían que se produjera un error en la instalación del conector.

2. Una vez extraídos los archivos, abra la carpeta extraída y haga doble clic en **Exchange_Connector_Setup.exe** para instalar el conector.

   > [!IMPORTANT]
   > Si la carpeta de destino no es una ubicación segura, elimine el archivo de certificado *MicrosoftIntune.accountcert* cuando termine de instalar los conectores locales.

3. En el cuadro de diálogo de **Microsoft Intune Exchange Connector**, seleccione **Microsoft Exchange Server local** o **Microsoft Exchange Server hospedado**.

   ![Imagen que muestra dónde debe elegir el tipo de Exchange Server](./media/exchange-connector-install/intune-sa-exchange-connector-config.png)

   Para un servidor Exchange local, proporcione el nombre del servidor o el nombre de dominio completo del servidor Exchange que hospeda el rol de **servidor de acceso de cliente**.

   Para un servidor de Exchange hospedado, proporcione la dirección del servidor Exchange. Para buscar la dirección URL del servidor Exchange hospedado:

   1. Abra Outlook para Office 365.

   2. Elija el icono **?** en la esquina superior izquierda y, a continuación, seleccione **Acerca de**.

   3. Busque el valor **Servidor externo POP** .

   4. Elija **Servidor proxy** para especificar la configuración del servidor proxy para el servidor Exchange hospedado.

       1. Seleccione **Usar un servidor proxy al sincronizar información de dispositivos móviles**.

       1. Escriba el **nombre del servidor proxy** y el **número de puerto** que se utilizará para tener acceso al servidor.

       1. Si se necesitan las credenciales de usuario para acceder al servidor proxy, seleccione **Usar credenciales para conectarse al servidor proxy**. A continuación, escriba el **dominio\usuario** y la **contraseña**.

       1. Elija **Aceptar**.

4. En los campos **Usuario (Dominio\usuario)** y **Contraseña**, escriba las credenciales para conectarse a su servidor de Exchange. La cuenta que se especifique debe tener una licencia para usar Intune. 

5. Proporcione las credenciales para enviar notificaciones al buzón de Exchange Server de un usuario. Este usuario se puede destinar solo a las notificaciones. El usuario de notificaciones necesita un buzón de Exchange para enviar notificaciones por correo electrónico. Puede configurar estas notificaciones con directivas de acceso condicional en Intune.  

   Asegúrese de que el servicio de detección automática y los servicios Web Exchange están configurados en el servidor de acceso de cliente de Exchange. Para obtener más información, consulte [Client Access server](https://technet.microsoft.com/library/dd298114.aspx) (Servidor de acceso de cliente).

6. En el campo **Contraseña**, indique la contraseña de la cuenta para permitir que Intune obtenga acceso al servidor de Exchange.

   > [!NOTE]
   > La cuenta que use para iniciar sesión en el inquilino debe ser al menos de administrador del servicio de Intune. Sin esta cuenta de administrador, la conexión no se completará y recibirá el error "El servidor remoto ha devuelto un error: (400) Solicitud incorrecta".

7. Elija **Conectar**.

   > [!NOTE]
   > La configuración de la conexión puede tardar unos minutos.

Durante la configuración, Exchange Connector guarda la configuración de proxy para permitir el acceso a Internet. Si cambia la configuración de proxy, vuelva a configurar Exchange Connector para aplicarle la configuración de proxy actualizada.

Después de que Exchange Connector configure la conexión, los dispositivos móviles asociados a los usuarios administrados en Exchange se sincronizan automáticamente y se agregan a Exchange Connector. Esta sincronización puede tardar algún tiempo en completarse.

> [!NOTE]
> Si instala Intune Exchange Connector y después necesita eliminar la conexión de Exchange, debe desinstalar el conector del equipo en el que se instaló.



## <a name="install-connectors-for-multiple-exchange-organizations"></a>Instalar conectores para varias organizaciones de Exchange

Intune admite varias instancias de Intune Exchange Connector por suscripción. Para un inquilino con varias organizaciones de Exchange, solo puede configurar un conector para cada organización de Exchange. 

Para instalar conectores que se conecten a varias organizaciones de Exchange, descargue la carpeta. zip una vez. Vuelva a usar la misma descarga para cada conector que instale. Para cada conector adicional, siga los pasos descritos en la sección anterior para extraer y ejecutar el programa de instalación en un servidor en la organización de Exchange.

Cada organización de Exchange que se conecta a Intune admite alta disponibilidad, supervisión y sincronización manual. Estas características se describen en las siguientes secciones.

## <a name="on-premises-intune-exchange-connector-high-availability-support"></a>Compatibilidad de alta disponibilidad de Intune Exchange Connector local  

Para el conector local, "alta disponibilidad "significa que si el servidor de acceso de cliente (CAS) de Exchange que usa el conector deja de estar disponible, el conector puede cambiar a otro CAS para esa organización de Exchange. El propio Exchange Connector no es compatible con la alta disponibilidad. Si se produce un error en el conector, no hay conmutación automática por error. Debe [instalar un conector nuevo](#reinstall-the-intune-exchange-connector) para reemplazar el conector con error. 

Para conmutar por error, el conector usa el CAS especificado para crear una conexión correcta a Exchange. A continuación, detecta CAS adicionales para esa organización de Exchange. Esta detección permite al conector conmutar por error en otro CAS (si hay alguno disponible) hasta que el CAS principal esté disponible. 

De forma predeterminada, está habilitada la detección de CAS adicionales. Si tiene que desactivar la conmutación por error:  
1. En el servidor en el que esté instalado Exchange Connector, vaya a **%*ProgramData*%\Microsoft\Windows Intune Exchange Connector**. 
2. Con un editor de texto, abra **OnPremisesExchangeConnectorServiceConfiguration.xml**.
3. Cambie **\<IsCasFailoverEnabled>*true*\</IsCasFailoverEnabled>** a **\<IsCasFailoverEnabled>*false*\</IsCasFailoverEnabled>** .  
 
## <a name="performance-tune-the-exchange-connector-optional"></a>Ajuste del rendimiento de Exchange Connector (opcional)

Cuando se admiten 5000 o más dispositivos con Exchange ActiveSync, puede configurar un valor opcional para mejorar el rendimiento del conector. Se logra un mayor rendimiento al permitir que Exchange use varias instancias de un espacio de ejecución de comandos de PowerShell. 

Antes de realizar este cambio, asegúrese de que la cuenta que usa para ejecutar Exchange Connector no se utiliza para otras finalidades de administración de Exchange. Una cuenta de Exchange tiene un número limitado de espacios de ejecución, y el conector utilizará la mayoría de ellos. 

Este ajuste en el rendimiento no es adecuado para los conectores que se ejecuten en hardware antiguo o lento.  

Para mejorar el rendimiento de Exchange Connector: 

1. En el servidor en el que está instalado el conector, abra el directorio de instalación del conector.  La ubicación predeterminada es *C:\ProgramData\Microsoft\Windows Intune Exchange Connector*. 
2. Edite el archivo *OnPremisesExchangeConnectorServiceConfiguration.xml*.
3. Localice **EnableParallelCommandSupport** y establezca el valor en **true**:  
     
   \<EnableParallelCommandSupport>true\</EnableParallelCommandSupport>
4. Guarde el archivo y, después, reinicie el servicio Microsoft Intune Exchange Connector.

## <a name="reinstall-the-intune-exchange-connector"></a>Reinstalación de Intune Exchange Connector

Es posible que deba reinstalar una instancia de Intune Exchange Connector. Dado que solo se puede conectar un conector a cada organización de Exchange, si se instala un segundo conector para una organización, el nuevo que se instale reemplazará el original.

1. Para instalar el nuevo conector, siga los pasos descritos en la sección [Instalación y configuración de Intune Exchange Connector](#install-and-configure-the-intune-exchange-connector). 
2. Cuando se le solicite, seleccione **Reemplazar** para instalar el nuevo conector.  
   ![Advertencia de configuración para reemplazar un conector](./media/exchange-connector-install/prompt-to-replace.png)

3. Continúe con los pasos de la sección [Instalación y configuración de Intune Exchange Connector](#install-and-configure-the-intune-exchange-connector) e inicie sesión en Intune de nuevo.
4. En la ventana final, seleccione **Cerrar** para finalizar la instalación.  
   ![Finalizar la instalación](./media/exchange-connector-install/successful-reinstall.png)
 

## <a name="monitor-an-exchange-connector"></a>Supervisión de un conector Exchange Connector

Después de haber configurado correctamente la instancia de Exchange Connector, puede ver el estado de las conexiones y la última sincronización correcta. 

Para validar la conexión del conector de Exchange:

1. En el panel de Intune, elija **Acceso de Exchange**.
2. Seleccione **Acceso local a Exchange** para verificar el estado de la conexión para cada conector de Exchange.

También puede comprobar la fecha y la hora del último intento de sincronización correcto.

A partir de la versión 1710 de Intune, puede usar el [módulo de administración de System Center Operations Manager para Exchange Connector e Intune](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True). El módulo de administración proporciona distintas maneras de supervisar Exchange Connector cuando haya que resolver problemas.

## <a name="manually-force-a-quick-sync-or-full-sync"></a>Forzar manualmente una sincronización rápida o una sincronización completa

Una instancia de Intune Exchange Connector sincroniza automáticamente registros de dispositivos de EAS e Intune regularmente. Si cambia el estado de cumplimiento de un dispositivo, el proceso de sincronización automática actualiza regularmente los registros para que el acceso a los dispositivos pueda bloquearse o permitirse.

- La **sincronización rápida** se produce con regularidad, varias veces al día. Una sincronización rápida recupera información del dispositivo para usuarios de Exchange local con licencia de Intune destinados al acceso condicional y que hayan cambiado desde la última sincronización.

- La **sincronización completa** se realiza una vez al día de manera predeterminada. Una sincronización completa recupera información del dispositivo para todos los usuarios de Exchange local con licencia de Intune destinados al acceso condicional. Una sincronización completa también recupera información de Exchange Server y se asegura de que la configuración especificada por Intune en Azure Portal se actualiza en Exchange Server. 


Puede forzar que un conector ejecute una sincronización mediante las opciones **Sincronización rápida** o **Sincronización completa** en el panel de Intune:

   1. En el panel de Intune, elija **Acceso de Exchange**.
   2. Seleccione **Acceso local a Exchange**.
   3. Seleccione el conector que quiere sincronizar y elija **Sincronización rápida** o **Sincronización completa**.

## <a name="next-steps"></a>Pasos siguientes

Cree una [directiva de acceso condicional para servidores de Exchange locales](conditional-access-exchange-create.md).
