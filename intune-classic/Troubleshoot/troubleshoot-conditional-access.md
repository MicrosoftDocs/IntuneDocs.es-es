---
title: Solucionar problemas de acceso condicional
description: Qué hacer cuando los usuarios no pueden obtener acceso a los recursos a través del acceso condicional de Intune.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 10/24/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 433fc32c-ca9c-4bad-9616-852c72faf996
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 67a2891e4c7a6adcd7bd132c5663c9a78426ea07
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="troubleshoot-conditional-access"></a>Solucionar problemas de acceso condicional

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Normalmente, cuando un usuario intenta acceder al correo o a SharePoint recibe una solicitud de inscripción. Esa solicitud llevará al usuario al portal de empresa.

En este tema se explica qué hacer cuando los usuarios no pueden obtener acceso a los recursos a través del acceso condicional de Intune.


## <a name="the-basics-for-success-in-conditional-access"></a>Aspectos básicos para el éxito del acceso condicional

Para que el acceso condicional funcione, necesita las siguientes condiciones:

-   Intune tiene que administrar el dispositivo
-   El dispositivo tiene que estar registrado con Azure Active Directory (AAD). En circunstancias normales, este registro se realiza automáticamente durante la inscripción de Intune
-   El dispositivo debe ser compatible con las directivas de cumplimiento de Intune, para el dispositivo y para el usuario del dispositivo.  Si no hay ninguna directiva de cumplimiento, la inscripción de Intune es suficiente.
-   Si el usuario recupera el correo a través del cliente de correo nativo del dispositivo en lugar de hacerlo a través de Outlook, Exchange ActiveSync debe estar activado en el dispositivo.     Esto ocurre automáticamente para dispositivos estándar iOS, Windows Phone y Android/KNOX.
-   Intune Exchange Connector debe estar configurado correctamente. Consulte [Solucionar problemas de Exchange Connector en Microsoft Intune](troubleshoot-exchange-connector.md) para obtener más información.

Es posible ver si estas condiciones se cumplen en un dispositivo en el Portal de administración de Azure y en el informe de inventario del dispositivo.

## <a name="enrollment-issues"></a>Problemas de inscripción

 -  El dispositivo no está inscrito, así que la inscripción solucionará el problema.
 -  El usuario inscribió el dispositivo, pero se produjo un error en la unión al área de trabajo. El usuario debe actualizar la inscripción desde el portal de empresa.

## <a name="compliance-issues"></a>Problemas de cumplimiento

 -  El dispositivo no cumple la directiva de Intune. Algunos problemas comunes son los requisitos de cifrado y contraseña. Se redirigirá al usuario al portal de empresa, donde podrá configurar el dispositivo para que sea compatible.
 -  El registro de la información de cumplimiento de un dispositivo puede llevar un tiempo. Espere unos minutos y vuelva a intentarlo .
 -  Para dispositivos iOS:
     -   Un perfil de correo electrónico existente creado por el usuario bloqueará la implementación de un perfil de Intune creado por el administrador. Este es un problema común, ya que los usuarios de iOS suelen crear un perfil de correo y luego inscribirse. El portal de empresa informará al usuario de que no son compatibles debido a su perfil de correo configurado manualmente y le pedirá que quite ese perfil. El usuario debe quitar su perfil de correo para que se pueda implementar el perfil de Intune. Para evitar el problema, indique a los usuarios que se inscriban sin instalar un perfil de correo y que permitan que Intune implemente el perfil.
     -   Un dispositivo iOS puede quedarse atascado en un estado de comprobación de cumplimiento e impedir que el usuario inicie otra comprobación. Esto puede solucionarse reiniciando el portal de empresa y el estado de cumplimiento reflejará el estado del dispositivo en Intune. Después de que se recopilen todos los datos desde una sincronización de dispositivos, la comprobación del cumplimiento es rápida, menos de medio segundo de media.

        Normalmente, los dispositivos de motivo permanecen en este estado porque están teniendo problemas al conectarse con el servicio o la sincronización tarda mucho tiempo.  Si el problema persiste en diferentes configuraciones de red (red de telefonía móvil, Wi-Fi y VPN), a través de reinicios del dispositivo y después de comprobar que el SSP está actualizado en el dispositivo, póngase en contacto con el soporte técnico de Microsoft, tal y como se describe en [Cómo obtener soporte técnico de Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

 - Para dispositivos Android:
    - Algunos dispositivos Android podrían parecer cifrados, pero la aplicación de portal de empresa reconoce estos dispositivos como no cifrados. 
    
        -   Los dispositivos que se encuentran en este estado requieren que el usuario establezca un código de acceso de inicio seguro. El usuario verá una notificación de dispositivo de la aplicación de portal de empresa que le pedirá que establezca un código de acceso de inicio para el dispositivo. Después de pulsar la notificación de dispositivo y confirmar el PIN o el código de acceso existente, seleccione la opción **Require PIN to start device** (Solicitar PIN para iniciar el dispositivo) en la pantalla **Secure start-up** (Inicio seguro). Después, pulse el botón **Comprobar cumplimiento** para el dispositivo en la aplicación de portal de empresa. El dispositivo debería detectarse ahora como cifrado.
    
        -   Algunos fabricantes de dispositivos cifran sus dispositivos con un PIN predeterminado, en vez de con el PIN secreto establecido por el usuario. Intune reconoce el cifrado con el PIN predeterminado como no seguro, ya que este método de cifrado puede poner en peligro los datos del dispositivo si un usuario malintencionado tiene acceso físico al dispositivo. Si este es el caso, considere la posibilidad de usar [directivas de protección de aplicaciones](/intune-classic/deploy-use/azure-portal-for-microsoft-intune-mam-policies).

## <a name="policy-issues"></a>Problemas de directivas

Al crear una directiva de cumplimiento y vincularla a una directiva de correo, las dos directivas deben implementarse en el mismo usuario, así que tenga cuidado al planear qué directivas se implementan en qué grupos. Los usuarios que tienen una sola directiva aplicada probablemente descubran que sus dispositivos no son compatibles.


## <a name="exchange-activesync-issues"></a>Problemas de Exchange ActiveSync

### <a name="compliant-android-device-gets-quarantine-notice"></a>El dispositivo Android compatible obtiene un aviso de cuarentena
- Un dispositivo Android inscrito y compatible puede recibir un aviso de cuarentena al intentar acceder a recursos corporativos. Antes de seleccionar el vínculo **Comenzar**, el usuario debe asegurarse de que el portal de empresa no estaba abierto cuando intentó acceder a los recursos. Los usuarios deben cerrar el portal de empresa, intentar acceder de nuevo a los recursos y luego seleccionar el vínculo **Comenzar**.

### <a name="retired-device-continues-to-have-access"></a>El dispositivo retirado sigue teniendo acceso.
- Cuando se usa Exchange Online, un dispositivo retirado puede seguir teniendo acceso durante varias horas después de la retirada. Esto es se debe a que Exchange almacena en caché los derechos de acceso durante 6 horas. Considere otras formas de proteger los datos en dispositivos retirados en este escenario.

### <a name="device-is-compliant-and-registered-with-aad-but-still-blocked"></a>El dispositivo es compatible y se registra en AAD, pero sigue bloqueado
- A veces, se retrasa el aprovisionamiento del identificador de Exchange ActiveSync (EASID) a AAD. Una causa común de este problema es la limitación de peticiones, así que espere unos minutos e inténtelo de nuevo.

### <a name="device-blocked"></a>Dispositivo bloqueado

Se puede bloquear un dispositivo desde el acceso condicional sin recibir un correo electrónico de activación.

- ¿Hay una regla de Exchange predeterminada que ponga en cuarentena o bloquee los dispositivos? Si una regla predeterminada bloquea o pone en cuarentena los dispositivos, los dispositivos no podrán recibir el correo electrónico de activación desde Exchange Connector. Esto es así por diseño.
- ¿La cuenta de notificación está configurada correctamente como se describe en la configuración básica?
- ¿Está el dispositivo presente en la consola de administración de Intune como un dispositivo Exchange ActiveSync? Si no es así, es probable que la detección de dispositivos tenga errores, probablemente debido a un problema de sincronización de Exchange Connector. Consulte Dispositivo Exchange ActiveSync no detectado desde Exchange.
- Compruebe los registros de Exchange Connector para la actividad de sendemail y compruebe si hay errores. Un ejemplo del comando para buscar es SendEmail desde la cuenta de notificación a useremail.
- Antes de que Exchange Connector bloquee el dispositivo, envía el correo electrónico de activación. Si el dispositivo está desconectado, no puede recibir el correo electrónico de activación. Compruebe si el cliente de correo electrónico del dispositivo tiene la recuperación de correo electrónico mediante la inserción en lugar de sondeo, ya que esto podría causar también que el usuario pierda el correo electrónico. Cambie a encuesta y compruebe si el dispositivo recibe el correo electrónico.

## <a name="noncompliant-device-not-blocked"></a>Dispositivo no conforme no bloqueado

Si encuentra un dispositivo que no es compatible, pero sigue teniendo acceso, realice los pasos siguientes.

- Revise los grupos de destino y exclusión. Si un usuario no está en el grupo de destino correcto o está en el grupo de exclusión, no se bloqueará. Solo se comprueba el cumplimiento de los dispositivos de los usuarios de un grupo de destino.
- Asegúrese de que se detecte el dispositivo. ¿El conector de Exchange apunta a un CAS de Exchange 2010 mientras el usuario está en un servidor de Exchange 2013? En este caso, si la regla de Exchange predeterminada es Permitir, incluso si el usuario está en el grupo de destino, Intune no puede ser consciente de la conexión del dispositivo a Exchange.
- Comprobar estado de la existencia y acceso del dispositivo en Exchange:
    - Use este cmdlet de PowerShell para obtener una lista de todos los dispositivos móviles para un buzón de correo: "Get-ActiveSyncDeviceStatistics -mailbox mbx'. Si el dispositivo no aparece, no dispone de acceso a Exchange.
    - Si aparece el dispositivo, use el cmdlet Get-CASmailbox-identidad: 'upn' | fl para obtener información detallada sobre su estado de acceso y proporcione esta información al soporte técnico de Microsoft.

## <a name="before-you-open-a-support-ticket"></a>Para abrir una incidencia de soporte técnico
Si estos procedimientos de solución de problemas no resuelven el problema, hay información que se le pedirá que proporcione al soporte técnico de Microsoft, como los registros de buzón OWA o los registros de Exchange Connector.

### <a name="collecting-owa-mailbox-logs"></a>Recopilar registros de buzón OWA

1. Inicie sesión a través de OWA y seleccione el símbolo de configuración (engranaje) situado junto a su nombre en la esquina superior derecha.
2. Seleccione **Opciones**.
3. Seleccione **Teléfono** (podría ser **Dispositivos móviles**) en la columna del lado izquierdo.
4. En el menú superior, seleccione **Dispositivos móviles**.
5. Seleccione el dispositivo en la lista y luego **Iniciar registro**.
6. Cuando se le pida, seleccione **Sí** en el cuadro de diálogo emergente.
7. Realice la acción que causó el problema, para poder reproducirlo.
8. Espere entre 1 y 2 minutos y, a continuación, vuelva a la lista de teléfonos en OWA. Asegúrese de que el teléfono esté seleccionado en la lista y, a continuación, en el menú superior, elija **Recuperar registro**.
9. Ahora debería recibir un correo electrónico propio con datos adjuntos. Cuando abra una incidencia de soporte técnico, proporcione el contenido del correo al servicio de soporte técnico de Microsoft.

### <a name="exchange-connector-logs"></a>Registros de Exchange Connector

#### <a name="general-log-information"></a>Información del registro general
Para ver registros de Exchange Connector, use la [herramienta del visor de seguimiento del servidor] (herramienta del visor de seguimiento del servidor) (https://msdn.microsoft.com/library/ms732023(v=vs.110).aspx'). Esta herramienta requiere que descargue el SDK de Windows Server.

>[!NOTE]
>Los registros se encuentran en C:\ProgramData\Microsoft\Windows Intune Exchange Connector\Logs. Los registros se encuentran en una serie de 30 archivos de registro a partir de *Connector0.log* y que acaba en *Connector29.log*. Registra la sustitución de uno a otro después de 10 MB de datos acumulados en un registro. Una vez que los registros lleguen a Connector29, volverán a comenzar en Connector0 de nuevo y sobrescribirán los archivos de registro anteriores.

#### <a name="locating-sync-logs"></a>Localizar registros de sincronización

-    Localice una sincronización completa en los registros buscando **full sync**. Este texto marcará el principio de una sincronización completa:

    'Comando de control: obtener la lista de dispositivos móviles sin un filtro de tiempo (sincronización completa) para los usuarios de <number>'

    El final del registro de una sincronización completa tiene este aspecto:

    La obtención de la lista de dispositivos móviles sin un filtro de tiempo (sincronización completa) para 4 usuarios se completó correctamente. Detalles: resultado del comando de inventario - Dispositivos sincronizados 0 Identificador de comando: commandIDGUID' Estado de Exchange: 'Server health 'Nombre: 'PowerShellExchangeServer: <Name=mymailservername>' Estado: Conectado','

-   Localice una sincronización rápida (diferencial) en los registros buscando **quick sync**.

##### <a name="exceptions-in-get-next-command"></a>Excepciones en el siguiente comando de Get
Compruebe los registros de Exchange Connector para ver las excepciones en **Obtener el siguiente comando**, y proporciónelos al soporte técnico de Microsoft.

#### <a name="verbose-logging"></a>Registro detallado

Para habilitar el registro detallado:

1.  Abra el archivo de configuración de seguimiento de Exchange Connector. El archivo se encuentra en: %ProgramData%\Microsoft\Windows Intune Exchange Connector\TracingConfiguration.xml.
2.  Busque TraceSourceLine con la clave siguiente: OnPremisesExchangeConnectorService
3.  Cambie el valor del nodo **SourceLevel** de **Seguimiento de actividad de advertencia** (valor predeterminado) a **Seguimiento de actividad detallado**, tal como se muestra a continuación.

    <TraceSourceLine> <Key xsi:type="xsd:string">OnPremisesExchangeConnectorService</Key> <Value xsi:type="TraceSource"> <SourceLevel>All</SourceLevel> <Listeners> <Listener> <ListenerType>CircularTraceListener</ListenerType> <SourceLevel>Verbose ActivityTracing</SourceLevel> <FileSizeQuotaInBytes>10000000</FileSizeQuotaInBytes> <FileName>Microsoft\Windows Intune Exchange Connector\Logs\Connector.svclog</FileName> <FileQuota>30</FileQuota> </Listener> </Listeners> </Value>
    </TraceSourceLine>



### <a name="next-steps"></a>Pasos siguientes
Si esta información para solucionar problemas no le ha ayudado, póngase en contacto con el servicio de soporte técnico de Microsoft como se indica en [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico de Microsoft Intune).
