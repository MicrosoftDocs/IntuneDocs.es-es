---
title: Solucionar problemas de acceso condicional
titleSuffix: Microsoft Intune
description: Qué hacer cuando los usuarios no pueden obtener acceso a los recursos a través del acceso condicional de Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/25/2018
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5fa59501-5f33-46b7-a5f5-75eeae9f1209
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9a5aeae0d4256232d01c7e6171b10159a130b513
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66044669"
---
# <a name="troubleshoot-conditional-access"></a>Solucionar problemas de acceso condicional

Puede proteger el acceso a servicios de Office 365 como Exchange Online, SharePoint Online, Skype Empresarial Online, Exchange local y otros servicios mediante el acceso condicional de Intune. Esta característica le permite asegurarse de que el acceso a los recursos de la empresa está restringido a los dispositivos que están inscritos en Intune y cumplen con las reglas de acceso condicional que estableció en la consola de administración de Intune o en Azure Active Directory. En este artículo se describe qué hacer cuando los usuarios no pueden obtener acceso a los recursos protegidos con el acceso condicional o cuando los usuarios pueden acceder a recursos protegidos, pero se debería bloquear el acceso.

## <a name="requirements-for-conditional-access"></a>Requisitos del acceso condicional

Para que funcione el acceso condicional, se deben cumplir los siguientes requisitos:

- El dispositivo debe estar inscrito en Intune, e Intune tiene que administrarlo.
- El usuario y el dispositivo deben cumplir las directivas de cumplimiento de Intune asignadas.
- De forma predeterminada, el usuario debe tener asignada una directiva de cumplimiento. Esto puede depender de cómo se configure la opción **Marcar los dispositivos sin directiva de cumplimiento asignada como** en **Cumplimiento del dispositivo** > **Configuración de directiva de cumplimiento** en el portal de administración de Intune.
-   Si el usuario usa el cliente de correo nativo del dispositivo en lugar de Outlook, Exchange ActiveSync debe estar activado en el dispositivo. Esto ocurre automáticamente para dispositivos iOS, Windows Phone y Android.
-   Intune Exchange Connector debe estar configurado correctamente. Consulte [Solucionar problemas de Exchange Connector en Microsoft Intune](troubleshoot-exchange-connector.md) para obtener más información.

Puede ver si estas condiciones se cumplen en los dispositivos en Azure Portal y en el informe de inventario del dispositivo.

## <a name="devices-appear-compliant-but-users-are-still-blocked"></a>Los dispositivos aparecen como compatibles pero los usuarios siguen bloqueados

- Los dispositivos Android que no sean Knox no tendrán acceso hasta que el usuario haga clic en el vínculo **Empezar ahora** del correo electrónico de cuarentena que reciben. Esto se aplica incluso si el usuario ya está inscrito en Intune. Si el usuario no recibe el correo electrónico con el vínculo en su teléfono, pueden usar un equipo para tener acceso a su correo electrónico y reenviarlo a una cuenta de correo electrónico en su dispositivo.
- El registro de la información de cumplimiento de un dispositivo puede llevar un tiempo cuando se inscribe por primera vez. Espere unos minutos y vuelva a intentarlo .
- Para dispositivos iOS, un perfil de correo electrónico existente podría bloquear la implementación de un perfil de correo electrónico creado por el administrador de Intune y asignado a ese usuario, haciendo que el dispositivo no sea compatible. En este escenario, la aplicación Portal de empresa notificará al usuario de que no es compatible por su perfil de correo electrónico configurado manualmente y le solicitará que quite ese perfil. Una vez que el usuario haya quitado el perfil de correo electrónico existente, el perfil de correo electrónico de Intune se implementará correctamente. Para evitar este problema, indique a los usuarios que deben quitar los perfiles de correo electrónico existentes en sus dispositivos antes de inscribirse.
- Un dispositivo puede quedarse atascado en un estado de comprobación de cumplimiento e impedir que el usuario inicie otra comprobación. Si tiene un dispositivo en este estado, intente lo siguiente:
  - Asegúrese de que el dispositivo está usando la versión más reciente de la aplicación de Portal de empresa.
  - Reinicie el dispositivo.
  - Compruebe si el problema persiste en diferentes redes (p. ej. red de telefonía móvil, Wi-Fi, etc.).

  Si el problema persiste, póngase en contacto con el Soporte técnico de Microsoft como se indica en [obtener asistencia para Microsoft Intune](get-support.md).
- Algunos dispositivos Android podrían parecer cifrados, pero la aplicación Portal de empresa reconoce estos dispositivos como no cifrados y los marca como no compatibles. En este caso, el usuario verá una notificación en la aplicación Portal de empresa que le pedirá que configure un código de acceso de inicio para el dispositivo. Después de pulsar en la notificación y confirmar el PIN o la contraseña existentes, seleccione la opción **Solicitar PIN para iniciar el dispositivo** en la pantalla **Inicio seguro**. Después, pulse en el botón **Comprobar cumplimiento** para el dispositivo en la aplicación Portal de empresa. El dispositivo debería detectarse ahora como cifrado. 
  > [!NOTE]
  > Algunos fabricantes de dispositivos cifran sus dispositivos con un PIN predeterminado, en vez de con un PIN establecido por el usuario. Intune considera que el cifrado mediante el PIN predeterminado es inseguro y marcará estos dispositivos como no compatibles hasta que el usuario cree un nuevo PIN no predeterminado.
- Un dispositivo Android inscrito y compatible podría quedar bloqueado y recibir un aviso de cuarentena al intentar acceder a recursos corporativos por primera vez. Si esto ocurre, asegúrese de que la aplicación Portal de empresa no se está ejecutando, después haga clic en el vínculo **Empezar ahora** del correo electrónico de cuarentena para desencadenar la evaluación. Esto solo debería tener que hacerse cuando el acceso condicional se habilita por primera vez.

## <a name="devices-are-blocked-and-no-quarantine-email-is-received"></a>Los dispositivos están bloqueados y no se recibe ningún correo electrónico de cuarentena

- Compruebe que el dispositivo está presente en la consola de administración de Intune como un dispositivo Exchange ActiveSync. Si no es así, es probable que la detección de dispositivos tenga errores, probablemente debido a un problema de Exchange Connector. Vea [Solucionar problemas de Intune On-Premises Exchange Connector](troubleshoot-exchange-connector.md) para obtener más información.
- Antes de que Exchange Connector bloquee un dispositivo, envía un correo electrónico de activación (cuarentena). Si el dispositivo está desconectado, no puede recibir el correo electrónico de activación. 
- Compruebe si el cliente de correo electrónico en el dispositivo está configurado para recuperar el correo electrónico mediante **Inserción** en lugar de **Extracción**. Si es así, esto podría provocar que el usuario pierda el correo electrónico. Cambie a **Inserción** y compruebe si el dispositivo recibe el correo electrónico.

## <a name="devices-are-noncompliant-but-users-are-not-blocked"></a>Los dispositivos no son compatibles pero no se bloquean a los usuarios

- Para equipos Windows, el acceso condicional sólo bloquea la aplicación de correo electrónico nativa, Office 2013 con autenticación moderna u Office 2016. El bloqueo de las versiones anteriores de Outlook o todas las aplicaciones de correo electrónico en los equipos de Windows requiere configuraciones de Servicios de federación de Active Directory (AD FS) y registro de dispositivo de AAD tal como se indicó en [Procedimientos para configurar SharePoint Online y Exchange Online para el acceso condicional de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication). 
- Si el dispositivo se borra selectivamente o se retira de Intune, podría continuar teniendo acceso durante varias horas después de la retirada. Esto es se debe a que Exchange almacena en caché los derechos de acceso durante 6 horas. Considere otras formas de proteger los datos en dispositivos retirados en este escenario.
- Los dispositivos de Surface Hub admiten el acceso condicional, pero debe implementar la directiva de cumplimiento a grupos de dispositivos (no a grupos de usuarios) para la evaluación correcta.
- Compruebe las asignaciones de las directivas de cumplimiento y las directivas de acceso condicional. Si un usuario no está en el grupo al que se asignan las directivas, o está en un grupo que se está excluyendo, el usuario no se bloqueará. Solo se comprueba el cumplimiento de los dispositivos de los usuarios de un grupo asignado.

## <a name="noncompliant-device-is-not-blocked"></a>No se bloquea un dispositivo que no es compatible

Si encuentra un dispositivo que no es compatible, pero sigue teniendo acceso, realice los pasos siguientes.
- Revise los grupos de destino y exclusión. Si un usuario no está en el grupo de destino correcto o está en el grupo de exclusión, no se bloqueará. Solo se comprueba el cumplimiento de los dispositivos de los usuarios de un grupo de destino.
- Asegúrese de que se detecte el dispositivo. ¿El conector de Exchange apunta a un CAS de Exchange 2010 mientras el usuario está en un servidor de Exchange 2013? En este caso, si la regla de Exchange predeterminada es Permitir, incluso si el usuario está en el grupo de destino, Intune no puede ser consciente de la conexión del dispositivo a Exchange.
- Comprobar estado de la existencia y acceso del dispositivo en Exchange:
  - Use este cmdlet de PowerShell para obtener una lista de todos los dispositivos móviles para un buzón de correo: "Get-ActiveSyncDeviceStatistics -mailbox mbx'. Si el dispositivo no aparece en la lista, no dispone de acceso a Exchange.
  - Si aparece el dispositivo, use el cmdlet Get-CASmailbox-identidad: 'upn' | fl para obtener información detallada sobre su estado de acceso y proporcione esta información al soporte técnico de Microsoft.

## <a name="next-steps"></a>Pasos siguientes
Si esta información no le es de ayuda, también puede [obtener soporte técnico de Microsoft Intune](get-support.md).
