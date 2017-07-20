---
title: "Configuración de Exchange Connector para EAS local con Intune"
titleSuffix: Intune Azure
description: "Intune Azure: MDM de Exchange ActiveSync – Uso de la herramienta Connector para permitir la comunicación entre Intune y Exchange Server local"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1dd5143ce6c604f416af1c6b6b1df684346e2f6d
ms.sourcegitcommit: be12974a7eaa4ce9cffe45aabe456c858d582e20
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2017
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune-azure"></a>Configuración de Exchange Connector local de Intune en Microsoft Intune Azure

Los entornos de Exchange Server local pueden usar Exchange Connector local de Intune para administrar el acceso de dispositivos a buzones de correo de Exchange locales, en función de si los dispositivos están inscritos o no en Intune y si se atienen a las directivas de cumplimiento de dispositivos de Intune. Exchange Connector local también es responsable de detectar los dispositivos móviles que se conectan a servidores locales de Exchange mediante la sincronización del registro existente de Exchange Active Sync (EAS) con Intune.

> [!IMPORTANT]
> Intune solo admite una conexión de Exchange Connector local de cualquier tipo por suscripción.

Para configurar una conexión que permite a Microsoft Intune comunicarse con Exchange Server local, debe seguir estos pasos:

1.  Descargue Exchange Connector local de Intune del portal de Intune.
2.  Instale y configure Exchange Connector local de Intune.
3.  Valide la conexión de Exchange.

## <a name="on-premises-exchange-connector-requirements"></a>Requisitos de On-Premises Exchange Connector
En la siguiente tabla se indican los requisitos del equipo en el que se instala On-Premises Exchange Connector.

|Requisito|Más información|
|---------------|--------------------|
|Sistemas operativos|Intune admite On-Premises Exchange Connector en equipos que ejecuten las ediciones Windows Server 2008 SP2 de 64 bits, Windows Server 2008 R2, Windows Server 2012 o Windows Server 2012 R2.<br /><br />El conector no es compatible con instalaciones de Server Core.|
|Microsoft Exchange|On-Premises Connector requiere Microsoft Exchange 2010 SP1 o una versión posterior o Exchange Online dedicado heredado. Para determinar si la configuración de su entorno Exchange Online dedicado es **nueva** o **heredada**, póngase en contacto con su administrador de cuentas.|
|Entidad de administración de dispositivos móviles| [Establecer la entidad de administración de dispositivos móviles en Intune](https://docs.microsoft.com/intune-classic/deploy-use/prerequisites-for-enrollment#step-2-mdm-authority-set).|
|Hardware|El equipo donde se instala el conector debe requiere una CPU de 1,6 GHz con 2 GB de RAM y 10 GB de espacio libre en disco.|users-add.md
|Sincronización de Active Directory|Para poder usar cualquiera el conector para conectar Intune a su instancia de Exchange Server, debe [configurar la sincronización de Active Directory](users-add.md) de forma que los usuarios locales y los grupos de seguridad estén sincronizados con su instancia de Azure Active Directory.|
|Software adicional|El equipo que hospede el conector debe tener una instalación completa de Microsoft .NET Framework 4.5 y Windows PowerShell 2.0.|
|Red|El equipo en el que se instala el conector debe estar en un dominio que tenga una relación de confianza con el dominio que hospeda Exchange Server.<br /><br />El equipo requiere configuraciones que le permitan obtener acceso al servicio de Intune a través de firewalls y servidores proxy mediante los puertos 80 y 443. Entre los dominios usados por Intune están manage.microsoft.com, &#42;manage.microsoft.com y &#42;.manage.microsoft.com.|


### <a name="exchange-cmdlet-requirements"></a>Requisitos del cmdlet de Exchange

Debe crear una cuenta de usuario de Active Directory que sea utilizada por Intune Exchange Connector. La cuenta debe tener permiso para ejecutar los siguientes cmdlets de Windows PowerShell Exchange necesarios:


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

## <a name="download-the-on-premises-exchange-connector-software-installation-package"></a>Descarga del paquete de instalación de software de On-Premises Exchange Connector

1. En un sistema operativo Windows Server compatible con Exchange Connector local, abra [Azure Portal](http://portal.azure.com) e inicie sesión con una cuenta de usuario que sea administrador del servidor local Exchange y que disponga de una licencia para usar Exchange Server.

2. Elija **Más servicios** en el menú izquierdo y, luego, escriba **Intune** en el filtro del cuadro de texto.

3. Elija **Intune** y, cuando se abra el panel de Intune, seleccione **Acceso local**.

4. En la hoja **Acceso local - Conector de Exchange ActiveSync**, en la sección **Instalación**, seleccione **Descargar el conector local**.

5.  On-Premises Exchange Connector se encuentra en una carpeta comprimida (.zip) que se puede abrir o guardar. En el cuadro de diálogo **Descarga de archivos**, haga clic en **Guardar** para almacenar la carpeta comprimida en una ubicación segura.

    > [!IMPORTANT]
    > No cambie el nombre ni mueva los archivos de la carpeta On-Premises Exchange Connector. Si lo hace, se producirá un error en la instalación de Exchange Connector.

## <a name="install-and-configure-the-intune-on-premises-exchange-connector"></a>Instalación y configuración de Intune On-Premises Exchange Connector
Siga estos pasos para instalar Intune On-Premises Exchange Connector. On-Premises Exchange Connector solo puede instalarse una vez y en un solo equipo por cada suscripción de Intune. Si intenta configurar otra instancia de On-Premises Exchange Connector, se reemplazará la conexión original por la nueva.

1.  En un sistema operativo compatible con On-Premises Connector, extraiga los archivos de **Exchange_Connector_Setup.zip** en una ubicación segura.

2.  Una vez extraídos los archivos, abra la carpeta extraída y haga doble clic en **Exchange_Connector_Setup.exe** para instalar On-Premises Exchange Connector.

    > [!IMPORTANT]
    > Si la carpeta de destino no es una ubicación segura, debe eliminar el archivo de certificado **WindowsIntune.accountcert** después de instalar On-Premises Connector.

3.  En el cuadro de diálogo de **Microsoft Intune Exchange Connector**, seleccione **Microsoft Exchange Server local** o **Microsoft Exchange Server hospedado**.

  ![Elegir el tipo de Exchange Server](./media/intune-sa-exchange-connector-config.png)

  Para un servidor Exchange local, proporcione el nombre del servidor o el nombre de dominio completo del servidor Exchange que hospeda el rol de **servidor de acceso de cliente**.

  Para un servidor de Exchange hospedado, proporcione la dirección del servidor Exchange. Para buscar la dirección URL del servidor Exchange hospedado:

    1. Abra Outlook Web App para Office 365.

    2. Elija el icono **?** de la esquina superior izquierda y luego seleccione **Acerca de**.

    3. Busque el valor **Servidor externo POP** .

    4. Elija **Servidor proxy** para especificar la configuración del servidor proxy para el servidor Exchange hospedado.
        1. Seleccione **Usar un servidor proxy al sincronizar información de dispositivos móviles**.

        2. Escriba el **nombre del servidor proxy** y el **número de puerto** que se utilizará para tener acceso al servidor.

        3. Si es necesario proporcionar credenciales de usuario para acceder al servidor proxy, seleccione **Usar credenciales para conectarse al servidor proxy**. A continuación, escriba el **dominio\usuario** y la **contraseña**.

        4. Elija **Aceptar**.

    5. En los campos **Usuario (Dominio\usuario)** y **Contraseña**, escriba las credenciales que son necesarias para conectarse a su servidor de Exchange.

    6.  Proporcione las credenciales administrativas necesarias para enviar notificaciones al buzón de Exchange Server de un usuario. Puede configurar estas notificaciones con directivas de acceso condicional en Intune.

        Asegúrese de que el servicio de detección automática y servicios Web Exchange están configurados en el servidor de acceso de cliente de Exchange. Para obtener más información, consulte [Client Access server](https://technet.microsoft.com/library/dd298114.aspx) (Servidor de acceso de cliente).

    7.  En el campo **Contraseña**, indique la contraseña de la cuenta para permitir que Intune obtenga acceso al servidor Exchange.

    8. Elija **Conectar**.

    > [!NOTE]
    > La conexión puede tardar unos minutos en configurarse.

Durante la configuración, Exchange Connector guarda la configuración de proxy para permitir el acceso a Internet. Si cambia la configuración de proxy, tendrá que volver a configurar Exchange Connector para aplicarle la configuración de proxy actualizada.

Después de que Exchange Connector configure la conexión, los dispositivos móviles asociados a los usuarios administrados en Exchange Connector se sincronizan automáticamente y se agregan a la Exchange Connector. Esta sincronización puede tardar algún tiempo en completarse.

> [!NOTE]
> Si ha instalado On-Premises Exchange Connector y en algún punto elimina la conexión de Exchange, deberá desinstalar On-Premises Exchange Connector del equipo en el que se instaló.

## <a name="validate-the-exchange-connection"></a>Validación de la conexión de Exchange

Después de haber configurado correctamente Exchange Connector, puede ver el estado de la conexión y la última sincronización correcta. Para validar la conexión de Exchange Connector:

- En el panel de Intune, elija **Acceso local**. En **Administrar**, seleccione **Acceso local a Exchange** para verificar el estado de la conexión.

También puede comprobar la fecha y la hora del último intento de sincronización correcto.

## <a name="next-steps"></a>Pasos siguientes
[Creación de una directiva de acceso condicional para el entorno local de Exchange](conditional-access-exchange-create.md)
