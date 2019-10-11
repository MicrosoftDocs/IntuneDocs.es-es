---
title: Solución de errores comunes de Intune Exchange Connector
titleSuffix: Microsoft Intune
description: Solución de problemas y resolución de errores comunes en el Microsoft Intune Exchange Connector local
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa4dbfb7c13d767df41655b391767fc7aa13d914
ms.sourcegitcommit: f04e21ec459998922ba9c7091ab5f8efafd8a01c
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71817591"
---
# <a name="resolve-common-errors-for-the-intune-exchange-connector"></a>Solución de errores comunes de Intune Exchange Connector

Este artículo puede ayudar al administrador de Intune a resolver errores y mensajes específicos sobre el funcionamiento de Intune Exchange Connector.  

## <a name="configuration-failed-and-returned-error-code-0x0000001"></a>Error de configuración y se devolvió el código de error 0x0000001

**Problema**:  
Al intentar configurar el Microsoft Intune Exchange Connector, recibirá el mensaje de error siguiente:

```
   The Microsoft Intune Exchange Connector cannot connect to the Microsoft Exchange server.  
   The following Microsoft Exchange Server address could not be reached <Exchange server Name FQDN>  
   Verify that the FQDN of the exchange server address and credentials that you entered is correct and the server is running. The Microsoft Intune Exchange Connector does not support Exchange server arrays.  
   Error code: 0x0000001  
```

Este problema puede producirse si la configuración de proxy de Internet no está configurada correctamente.

**Solución**:  
Configure los parámetros de proxy:
1. Póngase en contacto con el administrador de la red local para asegurarse de que la configuración del proxy está configurada correctamente. 
2. Use el comando **netsh WinHTTP** para configurar el servidor proxy y agregar la lista de exclusión necesaria. Por ejemplo:  

   ```
   Netsh winhttp set proxy proxy-server="http=proxy.corp.domain.com" bypass-list"34*.*;134.132.*.*;10.*.*;localhost;*.corp.domain.com;*.staging.domain.com"
   ```

## <a name="configuration-failed-and-returned-error-code-0x000000b"></a>Error de configuración y se devolvió el código de error 0x000000b   

**Problema**:  
Al intentar configurar el Microsoft Intune Exchange Connector, recibirá el mensaje de error siguiente:  

```
   The Microsoft Intune Exchange Connector experienced an error:  
   CertEnroll::CX509PrivateKey::Create: The system cannot find the file specified. 0x80070002 (WIN32: 2  
   ERROR_FILE_NOT_FOUND  
   Error code: 0x000000b  
```
Este problema puede producirse si la cuenta que usó para iniciar sesión en Intune no es una cuenta de administrador global de Intune.

**Solución**:  
Inicie sesión en Intune con una cuenta de administrador global o agregue su cuenta al grupo de administradores global. Para obtener más información, vea [Control de administración basada en roles (RBAC) con Microsoft Intune](../fundamentals/role-based-access-control.md).

## <a name="configuration-failed-and-returned-error-code-0x0000006"></a>Error de configuración y se devolvió el código de error 0x0000006

**Problema**:  
Al intentar configurar el Microsoft Intune Exchange Connector, recibirá el mensaje de error siguiente:  

```  
   The Microsoft Intune Exchange Connector cannot connect to Microsoft Intune  
   Verify that you are connected to the Internet, check the Microsoft Intune Service Status, and try to connect again.  
   Error code: 0x00000006  
```  
Este error puede producirse si se usa un servidor proxy para conectarse a Internet y está bloqueando el tráfico al servicio de Intune. Para determinar si un proxy está en uso, vaya a **Panel de Control** > **Opciones de Internet**, seleccione la pestaña **conexión** y, a continuación, haga clic en configuración de **LAN**.

**Solución**:  

- **Opción 1** : quitar la configuración de proxy para permitir que el equipo se conecte a Internet sin pasar por el proxy.  

- **Opción 2** : configurar el servidor proxy para permitir la comunicación con el servicio de Intune, como se documenta en [requisitos de Intune Exchange Connector](exchange-connector-install.md#intune-exchange-connector-requirements).



## <a name="event-7000-or-7041-microsoft-intune-exchange-connector-service-wont-start"></a>Evento 7000 o 7041: no se inicia el servicio Microsoft Intune Exchange Connector

**Problema**:  
Un dispositivo iOS no se inscribe en Intune y genera uno de los siguientes mensajes de error:  

```  
   Log Name:      System
   Source:            Service Control Manager
   Date:               <time>
   Task Category: None
   Level:               Error
   Keywords:        Classic
   User:                N/A
   Computer:      <computer>
   Description:
   The Microsoft Intune Exchange Connector Service service failed to start because of the following error:  
   The service did not start because of a logon failure.
```  

```  
   Log Name:      System
   Source:            Service Control Manager
   Date:               <time>
   Event ID:          7041
   Task Category: None
   Level:               Error   
   Keywords:        Classic
   User:                N/A
   Computer:       <computer>
   Description:
   The WIEC service was unable to log on as .\WIEC_USER with the currently configured password because of the following error:
   Logon failure: the user has not been granted the requested logon type at this computer.
   Service: WIEC
   Domain and account: .\WIEC_USER
   This service account does not have the required user right "Log on as a service."  
```
Este problema puede producirse si la cuenta **WIEC_User** no tiene el derecho de usuario **iniciar sesión como servicio** en la directiva local.

**Solución**:  
En el equipo que ejecuta Intune Exchange Connector, asigne el derecho de usuario **iniciar sesión como servicio** a la cuenta de servicio **WIEC_User** . Si el equipo es un nodo de un clúster, asegúrese de asignar el derecho de usuario *iniciar sesión como servicio* a la cuenta de servicio de clúster en todos los nodos del clúster.  

Para asignar el derecho de usuario **iniciar sesión como servicio** a la cuenta de servicio **WIEC_User** en el equipo, siga estos pasos:

1. Inicie sesión en el equipo como administrador o como miembro del grupo administradores.
2. Ejecute **SECPOL. msc** para abrir la Directiva de seguridad local.
3. Vaya a **configuración de seguridad** > **Directivas locales**y seleccione **asignación de derechos de usuario**.
4. En el panel derecho, haga doble clic en **Iniciar sesión como servicio**.
5. Seleccione **Agregar usuario o grupo**, agregue **WIEC_USER** a la Directiva y, a continuación, seleccione **Aceptar** dos veces.

Si el derecho de usuario **iniciar sesión como servicio** se asignó a **WIEC_User** pero se quitó posteriormente, póngase en contacto con el administrador del dominio para determinar si un valor de directiva de grupo lo está sobrescribiendo.  

## <a name="next-steps"></a>Pasos siguientes  

El artículo siguiente puede ayudar a resolver errores específicos:
- [Resolver problemas comunes de Intune Exchange Connector](troubleshoot-exchange-connector-common-problems.md). git 

Busque ayuda de soporte técnico o de la comunidad de Intune.
- Vea [obtener soporte técnico](../fundamentals/get-support.md) para usar la consola de Intune para ayudar a solucionar el problema o para abrir un caso de soporte técnico con Microsoft. 
- Publique su problema en los [foros de Microsoft Intune](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod).  
