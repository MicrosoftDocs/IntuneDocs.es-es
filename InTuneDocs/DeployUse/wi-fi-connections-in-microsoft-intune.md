---
title: Conexiones Wi-Fi | Microsoft Intune
description: Use perfiles de Wi-Fi para que los usuarios se conecten a las redes Wi-Fi.
keywords: 
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.date: 10/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0b1b86ed-2e80-474d-8437-17dd4bc07b55
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 27ba29f57bba1f3807c4b593ecac8c0af0851962
ms.openlocfilehash: 7b49b7d9b6054f7d153359c1ee1b6cf5875fba32


---

# Configurar dispositivos para que se conecten a las redes corporativas de Wi-Fi

Use perfiles de Wi-Fi de Microsoft Intune para implementar la configuración de red inalámbrica en los usuarios y los dispositivos de la organización. Al implementar un perfil de Wi-Fi, los usuarios tendrán acceso a su red Wi-Fi corporativa sin tener que configurarla ellos mismos.

Por ejemplo, instala una nueva red Wi-Fi denominada **Contoso Wi-Fi** y quiere configurar todos los dispositivos iOS para que se conecten a esta red. Este es el proceso:

![Resumen del proceso del perfil de Wi-Fi](..\media\wi-fi-process-diagram.png) 

1.   Cree un perfil de Wi-Fi que contenga la configuración necesaria para conectarse a la red inalámbrica **Contoso Wi-Fi**.

2.   Implemente el perfil en el grupo de usuarios con dispositivos iOS.

3.   Los usuarios encuentran la nueva red **Contoso Wi-Fi** en la lista de redes inalámbricas y pueden conectarse fácilmente a ella.


## Cómo crear un perfil de Wi-Fi

Puede implementar perfiles de Wi-Fi en las siguientes plataformas:

-   Android 4.0 y versiones posteriores

-   Android for Work   

-   iOS 8.0 y versiones posteriores

-   Mac OS X 10.9 y versiones posteriores

En el caso de los dispositivos que ejecutan Windows 8.1 o Windows 10 para escritorio o móvil, puede importar un perfil de configuración de Wi-Fi que se haya exportado previamente a un archivo. Para obtener más información, consulte [Exportar o importar un perfil de configuración de Wi-Fi para dispositivos Windows](#export-or-import-a-wi-fi-configuration-profile-for-windows-devices).

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), haga clic en **Directiva** &gt; **Agregar directiva**.

2.  Seleccione uno de los siguientes tipos de directiva y haga clic en **Crear directiva**:

    -   Perfil de Wi-Fi (Android 4 y versiones posteriores)

    -   Perfil de Wi-Fi (Android for Work)

    -   Perfil de Wi-Fi (iOS 8.0 y versiones posteriores)

    -   Perfil de Wi-Fi (Mac OS X 10.9 y versiones posteriores)
    
    
    No hay ninguna configuración recomendada para este tipo de directiva. Debe crear una directiva personalizada.

3.  Proporcione un nombre y una descripción para el perfil.

4. Especifique los valores de **Conexiones de red**.
 - **SSID (identificador de conjunto de servicios)**: los usuarios verán el nombre de la red, no el SSID.
 - **Conectarse cuando la red no esté difundiendo su nombre (SSID)**: seleccione esta opción para permitir que los dispositivos se conecten a la red cuando no esté visible en la lista de redes (porque está oculta y no se difunde su nombre).
 
5. Establezca la **Configuración de seguridad** para la plataforma seleccionada. Las opciones disponibles dependen de los tipos de seguridad que seleccione, que se describen en [Configuración de seguridad](#security-settings).

6. (Solo iOS y MAC OS X) **Configuración de proxy**

    |Nombre de la configuración|Más información|Se debe usar cuando:|
    |----------------|-------------------|-------------|
    |**Configuración del proxy para esta conexión Wi-Fi**|Elija el tipo de configuración de proxy:<br /><br />-   **Ninguna**: (valor predeterminado)<br />-   **Manual**: especifique manualmente la dirección URL y el número de puerto del servidor proxy.<br />-   **Automática**: use un archivo de configuración para configurar el servidor proxy.|Siempre|
    |**Dirección del servidor proxy** y **Número de puerto**|Especifique la dirección URL y el número de puerto del servidor proxy.|La opción **Configuración del proxy para esta conexión Wi-Fi** está establecida en **Manual**.|
    |**Dirección URL del servidor proxy**|Especifique la dirección URL del archivo que contiene la configuración del servidor proxy.|La opción **Configuración del proxy para esta conexión Wi-Fi** está establecida en **Automática**.|

7.  Guardar el perfil de Wi-Fi

La nueva directiva se muestra en el nodo **Directivas de configuración** del área de trabajo **Directiva**. Para obtener información sobre cómo implementar el perfil, consulte los **pasos siguientes**.

## Exportar o importar un perfil de configuración de Wi-Fi para dispositivos Windows
 
En el caso de los dispositivos que ejecutan Windows 8.1 o Windows 10 para escritorio o móvil, puede importar un perfil de configuración de Wi-Fi que se haya exportado previamente a un archivo. 

### Exportar un perfil de Wi-Fi
En Windows, puede usar la utilidad **netsh wlan** para exportar un perfil de Wi-Fi existente a un archivo XML que Intune pueda leer. En un equipo de Windows que ya tenga instalado el perfil de Wi-Fi necesario, siga el procedimiento siguiente.

1.  Cree una carpeta local para los perfiles de Wi-Fi exportados, como c:\Wi-Fi

2.  Abra un símbolo del sistema como administrador.

3.  Ejecute el comando `netsh wlan show profiles` y anote el nombre del perfil que quiere exportar.  En este ejemplo, el nombre de perfil es *WiFiName*.

4.  Ejecute este comando: `netsh wlan export profile name="ProfileName" folder=c:\Wifi`. Esto creará un archivo de perfil de Wi-Fi denominado "Wi-Fi-WiFiName.xml en la carpeta de destino".

### Importar un perfil de Wi-Fi
Use la **Directiva de importación de Wi-Fi de Windows** para importar un conjunto de opciones de Wi-Fi que luego puede implementar en los grupos de usuarios o de dispositivos necesarios.


1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), haga clic en **Directiva** &gt; **Agregar directiva**.

2.  Configure una directiva del tipo **Windows** &gt; **Importación de Wi-Fi (Windows 8.1 y posterior)**.

    Esta directiva puede aplicarse a dispositivos de escritorio y móviles con Windows 8.1 y Windows 10.

    Solo puede crear e implementar una directiva *personalizada* de importación de Wi-Fi de Windows. La configuración recomendada no está disponible.

3.  Especifique los siguientes valores generales para la Directiva de importación de Wi-Fi de Windows:

    |Nombre de la configuración|Más información|
    |----------------|--------------------|
    |**Nombre**|Escriba un nombre único para el perfil de Wi-Fi que permita identificarlo en la consola de Intune.|
    |**Descripción**|Proporcione una descripción del perfil de Wi-Fi y cualquier otra información relevante para que sea más fácil encontrarlo.|

4.  Especifique los valores siguientes en el encabezado **Perfil de Wi-Fi personalizado**:

    |Nombre de la configuración|Más información|
    |----------------|--------------------|
    |**Archivo del perfil de configuración**|Haga clic en **Importar** para seleccionar el archivo XML que contiene la configuración del perfil de Wi-Fi que quiere importar a Intune.|
    |**Nombre del perfil de configuración personalizada (que se muestra a los usuarios)**|Muestra el nombre del perfil de configuración de Wi-Fi tal y como se mostrará a los usuarios en su dispositivo.|
    |**Detalles del perfil de configuración**|Muestra el código XML para el perfil de configuración seleccionado.|

5.  Cuando haya terminado haga clic en **Guardar directiva**.

6.  La nueva directiva se muestra en el nodo **Directivas de configuración** del área de trabajo **Directiva** .

## Implementar el perfil

Un perfil es un tipo de directiva, por lo que debe usar el área de trabajo Directiva para implementarlo.

1.  En el área de trabajo **Directiva** , seleccione la directiva que quiera implementar y, a continuación, haga clic en **Administrar implementación**.

2.  En el cuadro de diálogo **Administrar la implementación** :

    -   **Para implementar la directiva**: seleccione uno o más grupos en los que quiera implementar la directiva y haga clic en **Agregar** &gt; **Aceptar**.

    -   **Para cerrar el cuadro de diálogo sin implementarla**: haga clic en **Cancelar**.


En el área de trabajo **Directiva** de la página **General** , un resumen de estado y las alertas identifican los problemas de la directiva que requieren su atención. Además, aparece un resumen de estado en el área de trabajo Panel.

## Configuración de seguridad
Estas tablas contienen la información de la configuración de seguridad disponible para los perfiles de Wi-Fi de Android, iOS y Mac OS X. 

### Configuración de seguridad para dispositivos Android

  |Nombre de la configuración|Más información|Se debe usar cuando:|
|----------------|--------------------|-------------|
|**Tipo de seguridad**|Seleccione el protocolo de seguridad de la red inalámbrica:<br /><br />-   **WPA-Enterprise/WPA2-Enterprise**<br />-   **Sin autenticación (abierto)** si la red no es segura.|Siempre|
|**Tipo de EAP**|Elija el tipo Protocolo de autenticación extensible (EAP) que se usa para autenticar conexiones inalámbricas seguras:<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   **EAP-TTLS**|Seleccionó el tipo de seguridad **WPA-Enterprise/WPA2-Enterprise**.|
|**Seleccionar certificados raíz para la validación del servidor**|Haga clic en **Seleccionar**y elija el perfil de certificado raíz de confianza que se usa para autenticar la conexión. **Importante:** Para crear el perfil de certificado raíz de confianza, consulte [Secure resource access with certificate profiles (Proteger el acceso a recursos con perfiles de certificado en Microsoft Intune)](secure-resource-access-with-certificate-profiles.md).|Se seleccionó cualquier **Tipo de EAP** .|
|**Método de autenticación**|Seleccione el método de autenticación para la conexión:<br /><br />-   **Certificados** para especificar el certificado de cliente<br />-   **Nombre de usuario y contraseña** para especificar otro método de autenticación|El **Tipo de EAP** es **PEAP** o **EAP-TTLS**.|
|**Seleccionar un método no EAP para la autenticación (identidad interna)**|Seleccione cómo se autenticará la conexión:<br /><br />-   **Ninguno**<br />-   **Contraseña no cifrada (PAP)**<br />-   **Protocolo de autenticación de desafío mutuo (CHAP)**<br />-   **Microsoft CHAP (MS-CHAP)**<br />-   **Microsoft CHAP versión 2 (MS-CHAP v2)**<br /><br />Las opciones disponibles dependen del tipo de EAP seleccionado.|El **Método de autenticación** es **Nombre de usuario y contraseña**.|
|**Habilitar privacidad de identidad (identidad externa)**|Especifique el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor. Durante la autenticación, esta identidad anónima se envía inicialmente, seguida de la identificación real enviada en un túnel seguro.|El **Tipo de EAP** es **PEAP** o **EAP-TTLS**.|
|**Seleccionar un certificado de cliente para la autenticación de cliente (certificado de identidad)**|Haga clic en **Seleccionar**y elija el perfil de certificado SCEP que se usa para autenticar la conexión. **Importante:** Para crear un perfil de certificado SCEP, consulte [Secure resource access with certificate profiles (Proteger el acceso a recursos con perfiles de certificado en Microsoft Intune)](secure-resource-access-with-certificate-profiles.md).|El tipo de seguridad es **WPA-Enterprise/WPA2-Enterprise** y se selecciona cualquier **tipo de EAP**.|

### Configuración de seguridad para dispositivos iOS y Mac OS X

  |Nombre de la configuración|Más información|Se debe usar cuando:|
|----------------|--------------------|-------------|
|**Tipo de seguridad**|Seleccione el protocolo de seguridad de red inalámbrica:<br /><br />-   **WPA-Personal/WPA2-Personal**<br />-   **WPA-Enterprise/WPA2-Enterprise**<br />-   **WEP**<br />-   **Sin autenticación (abierto)** si la red no es segura.|Siempre|
|**Tipo de EAP**|Elija el tipo Protocolo de autenticación extensible (EAP) que se usa para autenticar conexiones inalámbricas seguras:<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   **EAP-TLS**<br />-   **EAP-AST**<br />-   **LEAP**<br />-   **EAP-SIM**|Seleccionó un tipo de seguridad de **WPA-Enterprise/WPA2-Enterprise**.|
|**Nombres de certificado de servidor de confianza**|Seleccione el perfil de certificado raíz de confianza que se usa para autenticar la conexión. **Importante:** Para crear el perfil de certificado raíz de confianza, consulte [Secure resource access with certificate profiles (Proteger el acceso a recursos con perfiles de certificado en Microsoft Intune)](secure-resource-access-with-certificate-profiles.md).|Seleccionó un tipo de EAP de **EAP-TLS**, **PEAP**, **EAP-TTLS** o **EAP-FAST**.|
|**Usar credenciales de acceso protegido (PAC)**|Seleccione esta opción para usar credenciales de acceso protegido para establecer un túnel autenticado entre el cliente y el servidor de autenticación. Si está presente, se utiliza un archivo PAC existente.|El **Tipo de EAP** es **EAP-FAST**.|
|**Aprovisionar PAC**|Aprovisiona el archivo PAC en los dispositivos.<br /><br />Cuando se usa, también puede seleccionar **Aprovisionar PAC de forma anónima** para asegurarse de que el archivo PAC se aprovisione sin autenticar el servidor.|Se seleccionó**Usar credenciales de acceso protegido (PAC)** .|
|**Método de autenticación**|Seleccione el método de autenticación que se usa para la conexión:<br /><br /><ul><li>**Certificados** para especificar el certificado de cliente</li><li>**Nombre de usuario y contraseña** para especificar uno de los siguientes métodos de autenticación que no son EAP (también conocidos como identidad interna):<br /><br /><ul><li>**Ninguno**</li><li>**Contraseña no cifrada (PAP)**</li><li>**Protocolo de autenticación de desafío mutuo (CHAP)**</li><li>**Microsoft CHAP (MS-CHAP)**</li><li>**Microsoft CHAP versión 2 (MS-CHAP v2)**</li><li>**EAP-TLS**</li></ul></li></ul>|El **Tipo de EAP** es **PEAP** o **EAP-TTLS**.|
|**Seleccionar un certificado de cliente para la autenticación de cliente (certificado de identidad)**|Seleccione el perfil de certificado SCEP que se usa para autenticar la conexión. **Importante:** Para crear un perfil de certificado SCEP, consulte [Secure resource access with certificate profiles (Proteger el acceso a recursos con perfiles de certificado en Microsoft Intune)](secure-resource-access-with-certificate-profiles.md).|El tipo de seguridad es **WPA-Enterprise/WPA2-Enterprise** y el **Tipo de EAP** es **EAP-TLS**, **PEAP** o **EAP-TTLS**.|
|**Habilitar privacidad de identidad (identidad externa)**|Especifique el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor.<br /><br />Durante la autenticación, esta identidad anónima se envía inicialmente, seguida de la identificación real enviada en un túnel seguro.|El **Tipo de EAP** está establecido en **PEAP**, **EAP-TTLS** o **EAP-FAST**.|


### Consulte también
Aprenda a crear un perfil de Wi-Fi con una clave precompartida en [Crear un perfil de Wi-Fi con una clave precompartida](pre-shared-key-wi-fi-profile.md)



<!--HONumber=Oct16_HO2-->


