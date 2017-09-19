---
title: "Configuración de directiva de Mac OS X"
description: "Intune proporciona diversas configuraciones generales integradas que puede configurar en dispositivos Mac OS X. Además, puede usar la herramienta Apple Configurator para crear una configuración personalizada que no esté disponible en Intune."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 98b2f19b-bee8-42d7-a215-a716d56a25a3
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d4e7fd2aa4d6e20397533f678bd10b25b604181a
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/15/2017
---
# <a name="mac-os-x-configuration-policy-settings-in-microsoft-intune"></a>Configuración de directivas de configuración de Mac OS X en Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune proporciona diversas configuraciones generales integradas que puede configurar en dispositivos Mac OS X. Además, puede usar la herramienta Apple Configurator para crear una configuración personalizada que no esté disponible en Intune.

## <a name="general-configuration-policy-settings"></a>Configuración general de directivas

Use la **directiva de configuración general de Mac OS X** de Microsoft Intune para configurar las siguientes opciones:

-   **Configuración de seguridad de dispositivos**. Elija entre las opciones de una lista de configuraciones predefinidas que permiten controlar diversas características y funcionalidades en el dispositivo.

-   **Aplicaciones conformes y no conformes**. Especifique una lista de las aplicaciones conformes y no conformes en su empresa. El informe de aplicaciones no conformes puede usarse para comparar la conformidad de las aplicaciones especificadas en la lista con las aplicaciones que los usuarios han instalado (pero en realidad no pueden bloquear la instalación de la aplicación).

Si el valor que busca no aparece en esta lista, puede crearlo mediante una directiva personalizada de Mac OS X que permita importar la configuración que ha creado con la herramienta Apple Configurator. Para obtener más información, consulte "Configuración de directivas personalizadas" más adelante en este tema.

### <a name="password-settings"></a>Configuración de contraseña

|Nombre de la configuración|Detalles|
|----------------|---------------|
|**Requerir contraseña para desbloquear dispositivos**|Especificar si el usuario debe usar una contraseña para acceder a su equipo Mac. **Importante:** A diferencia de los dispositivos iOS, en los dispositivos Mac OS X no se envía una notificación al usuario inmediatamente para que actualice su contraseña para cumplir con esta configuración.|
|**Tipo de contraseña obligatoria**|Especificar si la contraseña solo puede ser **numérica** o si debe ser **alfanumérica** (contener letras y números). **Importante:** Esta configuración solo es compatible con Mac OS X versión 10.10.3 y posteriores.|
|**Número de caracteres complejos necesarios en la contraseña**|Especificar el número de caracteres complejos que requiere la contraseña (entre **0** y **4**).<br /><br />Un carácter complejo es un símbolo, como **?**.|
|**Longitud mínima de contraseña**|Especificar la longitud mínima de la contraseña (entre **4** y **14** caracteres).|
|**Permitir contraseñas sencillas**|Permitir el uso de contraseñas sencillas, como **0000** o **1234**.|
|**Minutos de inactividad antes de que se pida la contraseña**|Especificar el tiempo que el equipo debe estar inactivo antes de que se solicite una contraseña para desbloquearlo.|
|**Expiración de contraseña (días)**|Especificar cuántos días deben transcurrir para que el usuario deba cambiar la contraseña (entre **1** y **255** días).|
|**Recordar el historial de contraseñas**|Evitar que el usuario use una contraseña usada previamente. Al establecer esta configuración, también puede indicar la opción **Impedir la reutilización de contraseñas anteriores** para especificar el número de contraseñas usadas previamente que no se pueden volver a usar (entre **1** y **24**).|
|**Minutos de inactividad antes de que se active el protector de pantalla**|Especificar el período de tiempo que el equipo debe estar inactivo antes de que el protector de pantalla se active.|

### <a name="settings-for-compliant-and-noncompliant-apps"></a>Configuración de aplicaciones conformes y no conformes
En la **Lista de aplicaciones conformes y no conformes para Mac OS X**, habilite **Configuración administrada para dispositivos** y, después, especifique una lista de aplicaciones conformes y no conformes con la siguiente información.

> [!NOTE]
> Una única directiva solo puede contener una lista de aplicaciones conformes o una lista de aplicaciones no conformes. No se pueden especificar ambas en la misma directiva.
>
> Intune permite informar sobre dispositivos con aplicaciones no compatibles. No bloquea la instalación ni quita las aplicaciones no conformes.

|Nombre de la configuración|Detalles|
|----------------|---------------|
|**Notificar la no compatibilidad cuando los usuarios instalan las aplicaciones de la lista**|Muestra las aplicaciones Mac OS X que los usuarios no pueden instalar. Si los usuarios instalan cualquiera de estas aplicaciones, se notificará en **Informes de aplicaciones no conformes**.|
|**Informar sobre la incompatibilidad cuando los usuarios instalen aplicaciones no enumeradas**|Muestra las aplicaciones Mac OS X que los usuarios pueden instalar. Si los usuarios instalan otras aplicaciones, se notificará en **Informes de aplicaciones no conformes**.|
|**Agregar**|Agregar una aplicación a la lista seleccionada. Especifique un nombre de su elección, opcionalmente, el editor de la aplicación, y el identificador de paquete de la aplicación. **Sugerencia:** Para buscar el identificador de paquete de una aplicación, siga los pasos que se indican a continuación en un equipo Mac que tenga la aplicación instalada.<ol><li>Abra la carpeta en la que está instalada la aplicación (por ejemplo, **/Applications**).</li><li>Seleccione el paquete *&lt;Nombre de la aplicación&gt;***.app** y elija **Mostrar contenido del paquete**.</li><li>Abra el archivo **Info.plist**.</li><li>Compruebe el valor asociado a la clave **CFBundleIdentifier**.</li></ol>El formato del identificador de paquete es **com.contoso.appname**.|
|**Importar aplicaciones**|Importe la lista de las aplicaciones que ha especificado en un archivo de valores separados por comas. En el archivo, use este formato: nombre de la aplicación, editor, identificador de paquete de la aplicación.|
|**Editarar**|Edite el nombre, el editor y el identificador de paquete de la aplicación seleccionada.|
|**Eliminar**|Eliminar la aplicación seleccionada de la lista.|
> [!TIP]
> Para obtener más información sobre los informes de Intune, vea [Comprender las operaciones de Microsoft Intune mediante informes](understand-microsoft-intune-operations-by-using-reports.md).

> [!IMPORTANT]
> Cuando un dispositivo Mac OS X está en modo de suspensión, no es posible entregar ni inventariar las directivas ni los perfiles. Como resultado, en la consola de Intune se podría mostrar temporalmente el estado **Configuraciones de directivas con errores** hasta la próxima ocasión en que el dispositivo salga del modo de suspensión.

### <a name="monitor-compliant-and-noncompliant-apps"></a>Supervisar las aplicaciones conformes y no conformes
Use los **Informes de aplicaciones no conformes** para ver la conformidad de las aplicaciones que ha especificado.

#### <a name="to-run-a-report"></a>Para ejecutar un informe

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Informes** &gt; **Informe de aplicaciones no conformes**.

2.  Seleccione los grupos de dispositivos que quiere comprobar, si quiere comprobar las aplicaciones conformes, las aplicaciones no conformes o ambas y, después, elija **Ver informe**.

## <a name="mac-os-x-custom-policy-settings-in-microsoft-intune"></a>Configuración de directivas personalizadas de Mac OS X en Microsoft Intune
Use la **directiva de configuración personalizada de Mac OS X** de Microsoft Intune para implementar la configuración que ha creado mediante la [herramienta Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) en dispositivos Mac OS X. Esta herramienta permite crear muchas configuraciones para controlar el funcionamiento de estos dispositivos y exportarlas a un perfil de configuración. A continuación, puede importar este perfil de configuración en una directiva personalizada de Mac OS X de Intune e implementar la configuración en los usuarios y dispositivos de su organización.

Esta funcionalidad permite implementar la configuración de Mac OS X que no se puede configurar con la directiva de configuración general de Mac OS X de Intune.

### <a name="prerequisites"></a>Requisitos previos
Antes de empezar, debe tener instalado Apple Configurator y haber creado un archivo de configuración que contenga la configuración que quiere implementar en usuarios o dispositivos. Puede descargar Apple Configurator y obtener información sobre esta aplicación en [Mac App Store](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12).

> [!NOTE]
> Intune no notifica el cumplimiento de opciones de configuración individuales de una directiva personalizada de Mac OS X. Sin embargo, se notifica el cumplimiento general de la directiva.

### <a name="general-settings"></a>Configuración general

|Nombre de la configuración|Detalles|
    |----------------|--------------------|
    |**Nombre**|Escriba un nombre único para la directiva personalizada de Mac OS X que le ayude a identificarla en la consola de Intune.|
    |**Descripción**|Proporcione una descripción que ofrezca una visión general de la directiva personalizada de Mac OS X y otra información relevante que le ayude a encontrarla.|


### <a name="custom-settings"></a>Configuración personalizada

|Nombre de la configuración|Detalles|
    |----------------|--------------------|
    |**Nombre del perfil de configuración personalizada (que se muestra a los usuarios)**|Proporcione el nombre de la directiva que se mostrará en el dispositivo y en los informes de directivas de Intune.|
    |**Archivo del perfil de configuración**|Elija **Importar** y, luego, examine el perfil de configuración que ha creado con Apple Configurator. **Sugerencia:** Vea "Cómo crear un archivo de perfil de configuración" en este tema de ayuda para crear el perfil de configuración.|
    |**Detalles del perfil de configuración**|Mostrar el código XML del perfil de configuración que ha importado.|



### <a name="how-to-create-a-configuration-profile-file"></a>Cómo crear un archivo de perfil de configuración
Puede crear el archivo de perfil de configuración usado por la directiva personalizada de dos maneras:

-   Exportar el archivo (con la extensión **.mobileconfig**) desde la herramienta Apple Configurator.

-   Crear el archivo mediante el esquema apropiado de la [Referencia principal de los perfiles de configuración de Apple](https://developer.apple.com/library/ios/featuredarticles/iPhoneConfigurationProfileRef/Introduction/Introduction.html).


### <a name="see-also"></a>Consulte también
[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
