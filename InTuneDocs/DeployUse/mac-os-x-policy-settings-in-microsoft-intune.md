---
# required metadata

title: Configuración de directivas de Mac OS X | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 98b2f19b-bee8-42d7-a215-a716d56a25a3

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configuración de directivas de configuración de Mac OS X en Microsoft Intune

## Configuración general de directivas

Use la **directiva de configuración general de Mac OS X** de Microsoft Intune para configurar las siguientes opciones:

-   **Configuración de seguridad de los dispositivos**: elija entre las opciones de una lista de configuraciones predefinidas que permiten controlar diversas características y funcionalidades en el dispositivo.

-   **Aplicaciones compatibles y no compatibles**: especifique una lista de las aplicaciones compatibles y no compatibles de su empresa. El informe de aplicaciones no compatibles puede usarse para comparar la compatibilidad de las aplicaciones especificadas en la lista frente a las aplicaciones que los usuarios han instalado (pero en realidad no pueden bloquear la instalación de la aplicación).

Si el valor que busca no aparece en esta lista, puede crearlo mediante una directiva personalizada de Mac OS X que le permita importar la configuración que ha creado con la herramienta Apple Configurator. Para obtener más información, consulte **Configuración de directivas personalizadas**.

### Configuración de contraseña

|Nombre de la configuración|Detalles|
|----------------|---------------|
|**Requerir contraseña para desbloquear dispositivos**|Especifica si el usuario debe utilizar una contraseña para acceder a su equipo Mac. **Importante:** A diferencia de los dispositivos iOS, en los dispositivos Mac OS X no se envía una notificación al usuario inmediatamente para que actualice su contraseña para cumplir con esta configuración.|
|**Tipo de contraseña obligatoria**|Especifica si la contraseña usada solo puede ser numérica o si debe ser **alfanumérica** (contener letras y números). **Importante:** Esta configuración solo es compatible con Mac OS X versión 10.10.3 y posteriores.|
|**Número de caracteres complejos requeridos en la contraseña**|Especifica el número de caracteres complejos que requiere la contraseña (**0** - **4**).<br /><br />Un carácter complejo es un símbolo, como “**?**”.|
|**Longitud mínima de contraseña**|Especifica la longitud mínima de la contraseña (entre **4** y **14** caracteres).|
|**Permitir contraseñas sencillas**|Permite el uso de contraseñas sencillas, como "**0000**" o "**1234**".|
|**Minutos de inactividad antes de que se pida la contraseña**|Especifica el tiempo que el equipo debe estar inactivo antes de que se solicite una contraseña para desbloquearlo.|
|**Caducidad de contraseña (días)**|Especifica cuántos días deben transcurrir para que el usuario deba cambiar la contraseña (de **1** a **255** días).|
|**Recordar el historial de contraseñas**|Esta configuración se utiliza para evitar que el usuario emplee una contraseña usada previamente. Al establecerla, también puede indicar la opción **Impedir la reutilización de contraseñas anteriores** para especificar el número de contraseñas usadas previamente que no se pueden volver a usar (**1** - **24**).|
|**Minutos de inactividad antes de que se active el protector de pantalla**|Especifica el tiempo durante el que el equipo debe estar inactivo antes de que se active el protector de pantalla.|

### Configuración de aplicaciones conformes y no conformes
En la **Lista de aplicaciones compatibles y no compatibles para Mac OS X**, habilite **Configuración administrada para dispositivos** y especifique una lista de las aplicaciones compatibles y no compatibles con la siguiente información:

> [!NOTE]
> Una única directiva solo puede contener una lista de aplicaciones conformes o una lista de aplicaciones no conformes. No se pueden especificar ambas en la misma directiva.
> 
> Intune permite informar sobre dispositivos con aplicaciones no compatibles. No bloquea la instalación ni quita las aplicaciones no compatibles.

|Nombre de la configuración|Detalles|
|----------------|---------------|
|**Notificar la no compatibilidad cuando los usuarios instalan las aplicaciones de la lista**|Enumera las aplicaciones Mac OS X que los usuarios no pueden instalar. Si los usuarios instalan cualquiera de estas aplicaciones, se notificará en **Informes de aplicaciones no compatibles**.|
|**Informar sobre la incompatibilidad cuando los usuarios instalen aplicaciones no enumeradas**|Enumera las aplicaciones Mac OS X que los usuarios pueden instalar. Si los usuarios instalan otras aplicaciones, se notificará en **Informes de aplicaciones no compatibles**.|
|**Agregar**|Agrega una aplicación a la lista seleccionada. Especifique un nombre de su elección (opcionalmente, el editor de la aplicación) y el identificador de paquete de la aplicación. **Sugerencia:** Para buscar el identificador de paquete de una aplicación, siga los pasos que se indican a continuación en un equipo Mac que tenga la aplicación instalada.<ol><li>Abra la carpeta en la que está instalada la aplicación (por ejemplo, **/Applications**).</li><li>Seleccione el paquete *&lt;nombre de la aplicación&gt;***.app** y seleccione **Mostrar contenido del paquete**.</li><li>Abra el archivo **Info.plist** </li><li>Compruebe el valor asociado a la clave **CFBundleIdentifier**</li></ol>El formato del identificador de paquete es **com.contoso.appname**|
|**Importar aplicaciones**|Importa la lista de las aplicaciones que ha especificado en un archivo de valores separados por comas. Use el formato, el nombre de la aplicación, el editor y el identificador de paquete de la aplicación en el archivo.|
|**Editar**|Permite editar el nombre, el editor y el identificador de paquete de la aplicación seleccionada.|
|**Eliminar**|Elimina la aplicación seleccionada de la lista.|
> [!TIP] Para obtener más información sobre los informes de Intune, consulte [Comprender las operaciones de Microsoft Intune mediante informes](understand-microsoft-intune-operations-by-using-reports.md).

> [!IMPORTANT]
> Cuando un dispositivo Mac OS X está en modo de suspensión, no es posible entregar ni inventariar las directivas y los perfiles. Como resultado, la consola de Intune podría mostrar temporalmente el estado **Configuraciones de directivas con errores** hasta el momento en que el dispositivo salga del modo de suspensión.

### Supervisar las aplicaciones conformes y no conformes
Use los **Informes de aplicaciones no conformes** para ver la conformidad de las aplicaciones que especificó.

#### Para ejecutar el informe

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), haga clic en **Informes** &gt; **Informes de aplicaciones no compatibles**.

2.  Seleccione los grupos de dispositivos que quiere comprobar, si quiere comprobar las aplicaciones conformes, las aplicaciones no conformes o ambas y, a continuación, haga clic en **Ver informe**.

## Configuración de directivas personalizadas de Mac OS X en Microsoft Intune
Use la **directiva de configuración personalizada de Mac OS X** de Microsoft Intune para implementar la configuración que creó mediante la [herramienta Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) en dispositivos Mac OS X. Esta herramienta permite crear muchas configuraciones para controlar el funcionamiento de estos dispositivos y exportarlas a un perfil de configuración. A continuación, puede importar este perfil de configuración en una directiva personalizada de Mac OS X de Intune e implementar la configuración en los usuarios y dispositivos de su organización.

Esta capacidad está destinada a permitirle implementar la configuración de Mac OS X que no se puede configurar con una directiva de configuración general de Mac OS X de Intune.

### Requisitos previos
Antes de empezar, debe tener instalado Apple Configurator y haber creado un archivo de configuración que contenga la configuración que desea implementar en usuarios o dispositivos. Puede descargar Apple Configurator y obtener información sobre esta herramienta en el [Mac App Store](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12).

> [!NOTE]
> Intune no notifica el cumplimiento de opciones de configuración individuales de una directiva personalizada de Mac OS X. Sin embargo, se notifica el cumplimiento general de la directiva.

### Configuración general

|Nombre de la configuración|Detalles|
    |----------------|--------------------|
    |**Nombre**|Escriba un nombre único para la directiva personalizada de Mac OS X que le ayude a identificarla en la consola de Intune.|
    |**Descripción**|Proporcione una descripción que ofrezca una visión general de la directiva personalizada de Mac OS X y otra información relevante que le ayude a encontrarla.|


### Configuración personalizada

|Nombre de la configuración|Detalles|
    |----------------|--------------------|
    |**Nombre del perfil de configuración personalizada (que se muestra a los usuarios)**|Proporcione el nombre de la directiva que se mostrará en el dispositivo y en los informes de directivas de Intune.|
    |**Archivo del perfil de configuración**|Haga clic en **Importar**y luego examine el perfil de configuración que ha creado con Apple Configurator. **Sugerencia:** Consulte [Cómo crear un archivo de perfil de configuración](#BKMK_Prof) en este tema de ayuda para crear el perfil de configuración.|
    |**Detalles del perfil de configuración**|Muestra el código XML del perfil de configuración que ha importado.|



### Cómo crear un archivo de perfil de configuración
Puede crear el archivo de perfil de configuración usado por la directiva personalizada de dos maneras:

-   Exportar el archivo (con la extensión **.mobileconfig**) desde la herramienta Apple Configurator.

-   Crear el archivo mediante el esquema apropiado de la [referencia principal de los perfiles de configuración de Apple](https://developer.apple.com/library/ios/featuredarticles/iPhoneConfigurationProfileRef/Introduction/Introduction.html).


> [!IMPORTANT]
> Cuando un dispositivo Mac OS X está en modo de suspensión, no es posible entregar ni inventariar las directivas y los perfiles. Como resultado, la consola de Intune podría mostrar temporalmente el estado **Configuraciones de directivas con errores** hasta el momento en que el dispositivo salga del modo de suspensión.

### Consulte también
[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=May16_HO2-->


