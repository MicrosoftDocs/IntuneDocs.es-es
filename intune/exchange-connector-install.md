---
title: Configuración de Exchange Connector local de Microsoft Intune | Microsoft Intune
description: Use Exchange Connector local para administrar el acceso del dispositivo a los buzones de Exchange en función de la inscripción de Intune y Exchange Active Sync (EAS).
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 3e66dd3d77cc36a6d311afea82e0f2087b469495
ms.sourcegitcommit: 8c1590db761cc411369cae26677f909d3a8ca297
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/12/2019
ms.locfileid: "54239598"
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune-azure"></a>Configuración de Exchange Connector local de Intune en Microsoft Intune Azure

En un entorno de Exchange Server local, se puede usar el acceso condicional de Intune para permitir o bloquear el acceso a buzones locales de Exchange. Use los conectores locales de Exchange Active Sync para conectar Intune a las organizaciones de Exchange y configure el acceso condicional de Intune junto con las directivas de conformidad de dispositivos. Luego, cuando un dispositivo intenta conectarse a Exchange, Intune determina si el dispositivo está inscrito en Intune y es conforme. Para determinar qué dispositivos están inscritos en Intune, la instancia local de Exchange Connector asigna registros de Exchange Active Sync (EAS) en Exchange Server a los registros de Intune. Para saber más sobre cómo funciona, vea [¿Cuáles son las formas habituales de usar el acceso condicional con Intune?](conditional-access-intune-common-ways-use.md)

> [!IMPORTANT]
> Intune admite ahora varias instancias locales de Exchange Connector por suscripción. Si tiene más de una organización de Exchange local, puede configurar un conector independiente para cada organización de Exchange.

Para configurar una conexión que permita a Microsoft Intune comunicarse con una instancia local de Exchange Server, debe seguir estos pasos:

1.  Descargue la instancia local de Intune Exchange Connector desde Azure Portal.
2.  Instale y configure Exchange Connector en un equipo de la organización de Exchange local.
3.  Valide la conexión de Exchange.
4. Repita estos pasos para cada organización de Exchange que quiera conectar a Intune.

## <a name="intune-on-premises-exchange-connector-requirements"></a>Requisitos de la instancia local de Intune Exchange Connector
En esta tabla se indican los requisitos del equipo en el que se instala la instancia local de Exchange Connector.


|            Requisito             |                                                                                                                                                                                                        Más información                                                                                                                                                                                                        |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         Sistemas operativos          |                                                               Intune admite la instancia local de Exchange Connector en equipos con Windows Server 2008 SP2 de 64 bits, Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 o Windows Server 2016.<br /><br />El conector no es compatible con ninguna instalación de Server Core.                                                                |
|         Microsoft Exchange         |                                                                           Para la instancia local de Exchange Connector se necesita Microsoft Exchange 2010 SP3 o una versión posterior o Exchange Online dedicado heredado. Para determinar si la configuración de su entorno Exchange Online dedicado es <strong>nueva</strong> o <strong>heredada</strong>, póngase en contacto con su administrador de cuentas.                                                                           |
| Entidad de administración de dispositivos móviles |                                                                                                                              [Establecer la entidad de administración de dispositivos móviles en Intune](mdm-authority-set.md).                                                                                                                               |
|              Hardware              |                                                                                                                                                     El equipo donde se instala el conector debe requiere una CPU de 1,6 GHz con 2 GB de RAM y 10 GB de espacio libre en disco.                                                                                                                                                      |
|  Sincronización de Active Directory  |                                                                                      Para poder usar el conector para conectar Intune a su instancia de Exchange Server, debe [configurar la sincronización de Active Directory](users-add.md) de forma que los usuarios locales y los grupos de seguridad estén sincronizados con su instancia de Azure Active Directory.                                                                                      |
|        Software adicional         |                                                                                                                                           El equipo que hospede el conector debe tener una instalación completa de Microsoft .NET Framework 4.5 y Windows PowerShell 2.0.                                                                                                                                           |
|              Network (Red)               | El equipo en el que se instala el conector debe estar en un dominio que tenga una relación de confianza con el dominio que hospeda Exchange Server.<br /><br />El equipo requiere configuraciones que le permitan obtener acceso al servicio de Intune a través de firewalls y servidores proxy mediante los puertos 80 y 443. Entre los dominios usados por Intune están manage.microsoft.com, &#42;manage.microsoft.com y &#42;.manage.microsoft.com. |

### <a name="exchange-cmdlet-requirements"></a>Requisitos del cmdlet de Exchange

Debe crear una cuenta de usuario de Active Directory para usarla en la instancia local de Exchange Connector. La cuenta debe tener permiso para ejecutar los siguientes cmdlets de Windows PowerShell Exchange necesarios:


 -   Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 -   Get-CasMailbox, Set-CasMailbox
 -   Get-ActiveSyncMailboxPolicy, Set-ActiveSyncMailboxPolicy, New-ActiveSyncMailboxPolicy, Remove-ActiveSyncMailboxPolicy
 -   Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 -   Get-ActiveSyncDeviceStatistics
 -   Get-ActiveSyncDevice
 -   Get-ExchangeServer
 -   Get-ActiveSyncDeviceClass
 -   Get-Recipient
 -   Clear-ActiveSyncDevice, Remove-ActiveSyncDevice
 -   Set-ADServerSettings
 -   Get-Command

## <a name="download-the-on-premises-exchange-connector-software-installation-package"></a>Descarga del paquete de instalación de software de la instancia local de Exchange Connector

1. En un sistema operativo Windows Server compatible con la instancia local de Exchange Connector, abra [Azure Portal](https://portal.azure.com) e inicie sesión con una cuenta de usuario que sea administrador de la instancia local de Exchange Server y que disponga de una licencia para usar Exchange Server.

2. Elija **Todos los servicios** en el menú de la izquierda y, luego, escriba **Intune** en el filtro del cuadro de texto.

3. Elija **Intune** y, cuando se abra el panel de Intune, seleccione **Acceso local**.

4. En **Configuración**, elija **Conector de Exchange ActiveSync** y luego **Descargar el conector local**.

5.  El conector local de Exchange se encuentra en una carpeta comprimida (.zip) que se puede abrir o guardar. En el cuadro de diálogo **Descarga de archivos**, haga clic en **Guardar** para almacenar la carpeta comprimida en una ubicación segura.

    > [!IMPORTANT]
    > No cambie el nombre ni mueva los archivos de la carpeta de la instancia local de Exchange Connector. Si lo hace, se producirá un error en la instalación de Exchange Connector.

## <a name="install-and-configure-the-intune-on-premises-exchange-connector"></a>Instalar y configurar Intune On-Premises Exchange Connector
Siga estos pasos para instalar Intune On-Premises Exchange Connector. Si tiene varias organizaciones de Exchange, repita estos pasos para cada conector de Exchange adicional que quiera instalar.

1. En un sistema operativo compatible con On-Premises Exchange Connector, extraiga los archivos de **Exchange_Connector_Setup.zip** en una ubicación segura.

2. Una vez extraídos los archivos, abra la carpeta extraída y haga doble clic en **Exchange_Connector_Setup.exe** para instalar On-Premises Exchange Connector.

   > [!IMPORTANT]
   > Si la carpeta de destino no es una ubicación segura, debe eliminar el archivo de certificado **MicrosoftIntune.accountcert** cuando termine de instalar On-Premises Exchange Connector.

3. En el cuadro de diálogo de **Microsoft Intune Exchange Connector**, seleccione **Microsoft Exchange Server local** o **Microsoft Exchange Server hospedado**.

   ![Imagen que muestra dónde debe elegir el tipo de Exchange Server](./media/intune-sa-exchange-connector-config.png)

   Para un servidor Exchange local, proporcione el nombre del servidor o el nombre de dominio completo del servidor Exchange que hospeda el rol de **servidor de acceso de cliente**.

   Para un servidor de Exchange hospedado, proporcione la dirección del servidor Exchange. Para buscar la dirección URL del servidor Exchange hospedado:

   1. Abra Outlook en la web para Office 365.

   2. Elija el icono **?** de la esquina superior izquierda y luego seleccione **Acerca de**.

   3. Busque el valor **Servidor externo POP** .

   4. Elija **Servidor proxy** para especificar la configuración del servidor proxy para el servidor Exchange hospedado.
       1. Seleccione **Usar un servidor proxy al sincronizar información de dispositivos móviles**.

       2. Escriba el **nombre del servidor proxy** y el **número de puerto** que se utilizará para tener acceso al servidor.

       3. Si es necesario proporcionar credenciales de usuario para acceder al servidor proxy, seleccione **Usar credenciales para conectarse al servidor proxy**. A continuación, escriba el **dominio\usuario** y la **contraseña**.

       4. Elija **Aceptar**.

4. En los campos **Usuario (Dominio\usuario)** y **Contraseña**, escriba las credenciales que son necesarias para conectarse a su servidor de Exchange.

5. Proporcione las credenciales necesarias para enviar notificaciones al buzón de Exchange Server de un usuario. Este usuario se puede destinar solo a las notificaciones. El usuario de notificaciones necesita un buzón de Exchange para poder enviar notificaciones por correo electrónico. Puede configurar estas notificaciones con directivas de acceso condicional en Intune.  

       Ensure that the Autodiscover service and Exchange Web Services are configured on the Exchange Client Access Server. For more information, see [Client Access server](https://technet.microsoft.com/library/dd298114.aspx).

6. En el campo **Contraseña**, indique la contraseña de la cuenta para permitir que Intune obtenga acceso al servidor Exchange.

7. Elija **Conectar**.

   > [!NOTE]
   > La conexión puede tardar unos minutos en configurarse.

Durante la configuración, Exchange Connector guarda la configuración de proxy para permitir el acceso a Internet. Si cambia la configuración de proxy, tiene que volver a configurar el conector de Exchange para aplicarle la configuración de proxy actualizada.

Después de que Exchange Connector configure la conexión, los dispositivos móviles asociados a los usuarios administrados en Exchange se sincronizan automáticamente y se agregan a Exchange Connector. Esta sincronización puede tardar algún tiempo en completarse.

> [!NOTE]
> Si ha instalado On-Premises Exchange Connector y en algún momento elimina la conexión de Exchange, deberá desinstalar On-Premises Exchange Connector del equipo en el que se instaló.

## <a name="install-connectors-for-multiple-exchange-organizations"></a>Instalar conectores para varias organizaciones de Exchange
Intune admite varias instancias de On-premises Exchange Connector por suscripción. Para un inquilino con varias organizaciones de Exchange, puede configurar un conector para cada organización de Exchange. Descargue la carpeta .zip una vez y, para cada organización de Exchange, siga los pasos descritos en la sección anterior para extraer y ejecutar el programa de instalación en un servidor de la organización.

Las características de alta disponibilidad, supervisión y sincronización manual que se describen en las secciones siguientes se admiten para cada organización de Exchange conectada a Intune.

## <a name="on-premises-exchange-connector-high-availability-support"></a>Compatibilidad de alta disponibilidad de On-premises Exchange Connector 
Una vez que el conector de Exchange crea una conexión a Exchange mediante la CAS especificada, puede detectar otras CAS. Si la CAS principal deja de estar disponible, el conector conmutará por error a otra CAS, si está disponible, hasta que la CAS principal esté disponible. Esta característica está activada de manera predeterminada. Puede desactivar esta característica mediante el procedimiento siguiente:
1. En el servidor en el que está instalado el conector de Exchange, vaya a %*ProgramData*%\Microsoft\Windows Intune Exchange Connector. 
2. Con un editor de texto, abra **OnPremisesExchangeConnectorServiceConfiguration.xml**.
3. Cambie &lt;IsCasFailoverEnabled&gt;**true**&lt;/IsCasFailoverEnabled&gt; a &lt;IsCasFailoverEnabled&gt;**false**&lt;/IsCasFailoverEnabled&gt; para deshabilitar la característica.    


## <a name="monitor-the-exchange-connector-activity"></a>Supervisión de la actividad de Exchange Connector

Después de haber configurado correctamente Exchange Connector, puede ver el estado de la conexión y la última sincronización correcta. Para validar las conexiones de Exchange Connector:

1. En el panel de Intune, elija **Acceso local**.
2. En **Configuración**, seleccione **Conectores de Exchange ActiveSync** para comprobar el estado de conexión para cada conector de Exchange.

También puede comprobar la fecha y la hora del último intento de sincronización correcto.

### <a name="system-center-operations-manager-management-pack"></a>Módulo de administración de System Center Operations Manager

A partir de la versión 1710 de Intune, puede usar el [módulo de administración de Operations Manager para el conector de Exchange e Intune](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True). Este módulo de administración proporciona distintas maneras de supervisar Exchange Connector cuando haya que resolver problemas.

## <a name="manually-force-a-quick-sync-or-full-sync"></a>Forzar manualmente una sincronización rápida o una sincronización completa
Un conector de Exchange local sincroniza automáticamente registros de dispositivos de EAS e Intune regularmente. Si cambia el estado de cumplimiento de un dispositivo, el proceso de sincronización automática actualiza regularmente los registros para que el acceso a los dispositivos pueda bloquearse o permitirse en consecuencia.

   - La **Sincronización rápida** se produce con regularidad, varias veces al día. Una sincronización rápida recupera información del dispositivo para usuarios con licencia de Intune y con destino de acceso condicional a On-premises Exchange que hayan cambiado desde la última sincronización.

   - La **Sincronización completa** se realiza una vez al día de manera predeterminada. Una sincronización completa recupera información del dispositivo para todos los usuarios con licencia de Intune y con destino de acceso condicional a On-premises Exchange. Una sincronización completa también recupera información de Exchange Server y se asegura de que la configuración especificada por Intune en Microsoft Azure Portal se actualiza en Exchange Server. 

Puede forzar que un conector ejecute una sincronización mediante las opciones **Sincronización rápida** o **Sincronización completa** en el panel de Intune con los pasos siguientes:

   1. En el panel de Intune, elija **Acceso local**.
   2. En **Configuración**, elija **Conectores de Exchange ActiveSync**.
   3. Seleccione el conector que quiere sincronizar y elija **Sincronización rápida** o **Sincronización completa**.

## <a name="next-steps"></a>Pasos siguientes
[Creación de una directiva de acceso condicional para el entorno local de Exchange](conditional-access-exchange-create.md)
