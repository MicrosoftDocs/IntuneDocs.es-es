---
title: Conexiones Wi-Fi
description: Use perfiles de Wi-Fi para que los usuarios se conecten a las redes Wi-Fi.
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 02/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0b1b86ed-2e80-474d-8437-17dd4bc07b55
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9b99762dfc8e527fc845755365a09fab8a0d3a0c
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="configure-devices-to-connect-to-your-corporate-wi-fi-networks"></a>Configurar dispositivos para que se conecten a las redes corporativas de Wi-Fi

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Use perfiles de Wi-Fi de Microsoft Intune para implementar la configuración de red inalámbrica en los usuarios y los dispositivos de la organización. Al implementar un perfil de Wi-Fi, los usuarios tendrán acceso a su red Wi-Fi corporativa sin tener que configurarla ellos mismos.

Por ejemplo, instala una nueva red Wi-Fi denominada **Contoso Wi-Fi** y quiere configurar todos los dispositivos iOS para que se conecten a esta red. Este es el proceso:

![Resumen del proceso del perfil de Wi-Fi](..\media\wi-fi-process-diagram.png)

1.   Cree un perfil de Wi-Fi que contenga la configuración necesaria para conectarse a la red inalámbrica **Contoso Wi-Fi**.

2.   Implemente el perfil en el grupo de usuarios con dispositivos iOS.

3.   Los usuarios encuentran la nueva red **Contoso Wi-Fi** en la lista de redes inalámbricas y pueden conectarse fácilmente a ella.


## <a name="create-a-wi-fi-profile"></a>Crear un perfil de Wi-Fi

Puede implementar perfiles de Wi-Fi en las siguientes plataformas:

-   Android 4.0 y versiones posteriores

-   Android for Work   

-   iOS 8.0 y versiones posteriores

-   Mac OS X 10.9 y versiones posteriores

En el caso de dispositivos que ejecutan sistemas operativos Windows 8.1 o Windows 10 para móvil o escritorio, puede importar un perfil de configuración de Wi-Fi que se haya exportado anteriormente a un archivo. Para más información, consulte [Exportar o importar un perfil de configuración de Wi-Fi para dispositivos Windows](#export-or-import-a-wi-fi-configuration-profile-for-windows-devices).

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), seleccione **Directiva** &gt; **Agregar directiva**.

2.  Seleccione uno de los siguientes tipos de directiva y elija **Crear directiva**:

    -   Perfil de Wi-Fi (Android 4 y versiones posteriores)

    -   Perfil de Wi-Fi (Android for Work)

    -   Perfil de Wi-Fi (iOS 8.0 y versiones posteriores)

    -   Perfil de Wi-Fi (Mac OS X 10.9 y versiones posteriores)


No hay ninguna configuración recomendada para este tipo de directiva. Debe crear una directiva personalizada.

3.  Proporcione un nombre y una descripción para el perfil.

4. Especifique los valores de **Conexiones de red**.
 - **SSID (identificador de red)**: seleccione esta opción si quiere que los usuarios vean el nombre de la red en lugar del SSID.
 - **Conectarse cuando la red no esté difundiendo su nombre (SSID)**: seleccione esta opción para permitir que los dispositivos se conecten a la red cuando no esté visible en la lista de redes (porque está oculta y no se difunde su nombre).

5. Establezca la **Configuración de seguridad** para la plataforma seleccionada. Las opciones disponibles dependen de los tipos de seguridad que seleccione. Puede encontrar su descripción en [Configuración de seguridad](#security-settings).

6. Configure **el proxy** (solo iOS y MAC OS X).

    |Nombre de la configuración|Más información|Cuándo se debe utilizar|
    |----------------|-------------------|-------------|
    |**Configuración del proxy para esta conexión Wi-Fi**|Elija el tipo de configuración de proxy:<br /><br />-   **Ninguna**: (valor predeterminado)<br />-   **Manual**: especifique manualmente la dirección URL y el número de puerto del servidor proxy.<br />-   **Automática**: use un archivo de configuración para configurar el servidor proxy.|Siempre|
    |**Dirección del servidor proxy** y **Número de puerto**|Especifique la dirección URL y el número de puerto del servidor proxy.|Si la opción **Configuración de proxy para esta conexión Wi-Fi** está establecido en **Manual**.|
    |**Dirección URL del servidor proxy**|Especifique la dirección URL del archivo que contiene la configuración del servidor proxy.|Si la opción **Configuración de proxy para esta conexión Wi-Fi** está establecida en **Automática**.|

7.  Guardar el perfil de Wi-Fi

La nueva directiva se muestra en el nodo **Directivas de configuración** del área de trabajo **Directiva**. Para obtener información sobre cómo implementar el perfil, consulte los **pasos siguientes**.

## <a name="export-or-import-a-wi-fi-configuration-profile-for-windows-devices"></a>Exportar o importar un perfil de configuración de Wi-Fi para dispositivos Windows

En el caso de dispositivos que ejecutan sistemas operativos Windows 8.1 o Windows 10 para móvil o escritorio, puede importar un perfil de configuración de Wi-Fi que se haya exportado anteriormente a un archivo.

### <a name="export-a-wi-fi-profile"></a>Exportar un perfil de Wi-Fi
En Windows, puede usar la utilidad **netsh wlan** para exportar un perfil de Wi-Fi existente a un archivo XML que Intune pueda leer. En un equipo Windows que ya tenga instalado el perfil de Wi-Fi necesario, estos son los pasos que debe seguir:

1.  Cree una carpeta local para los perfiles de Wi-Fi exportados. Por ejemplo, cree una carpeta denominada **c:\WiFi.**

2.  Abra un símbolo del sistema como administrador.

3.  Ejecute el comando `netsh wlan show profiles` y anote el nombre del perfil que quiere exportar.  En este ejemplo, el nombre de perfil es **WiFiName**.

4.  Ejecute este comando: `netsh wlan export profile name="ProfileName" folder=c:\Wifi`. Se creará un archivo de perfil de Wi-Fi denominado **Wi-Fi-WiFiName.xml** en la carpeta de destino.

### <a name="import-a-wi-fi-profile"></a>Importar un perfil de Wi-Fi
Use la **Directiva de importación de Wi-Fi de Windows** para importar un conjunto de opciones de Wi-Fi que luego puede implementar en los grupos de usuarios o de dispositivos necesarios.


1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), haga clic en **Directiva** &gt; **Agregar directiva**.

2.  Configure una directiva del tipo **Windows** &gt; **Importación de Wi-Fi (Windows 8.1 y posterior)**.

    Esta directiva puede aplicarse a dispositivos que ejecuten los sistemas operativos Windows 8.1 y Windows 10 para móvil y escritorio.

    Solo puede crear e implementar una directiva *personalizada* de importación de Wi-Fi de Windows. La configuración recomendada no está disponible.

3.  Especifique los siguientes valores generales para la Directiva de importación de Wi-Fi de Windows:

    |Nombre de la configuración|Más información|
    |----------------|--------------------|
    |**Nombre**|Escriba un nombre único para el perfil de Wi-Fi que permita identificarlo en la consola de Intune.|
    |**Descripción**|Proporcione una descripción del perfil de Wi-Fi y cualquier otra información pertinente que ayude a encontrarlo.|

4.  Especifique los valores siguientes en el encabezado **Perfil de Wi-Fi personalizado**:

    |Nombre de la configuración|Más información|
    |----------------|--------------------|
    |**Archivo del perfil de configuración**|Elija **Importar** para seleccionar el archivo XML que contiene la configuración del perfil Wi-Fi que quiere importar en Intune.|
    |**Nombre del perfil de configuración personalizada (que se muestra a los usuarios)**|Elija cómo se mostrará el nombre del perfil de configuración de Wi-Fi a los usuarios en su dispositivo.|
    |**Detalles del perfil de configuración**|Elija cómo se mostrará el código XML del perfil de configuración que ha seleccionado.|

5.  Cuando termine, elija **Guardar directiva**.

6.  La nueva directiva se muestra en el nodo **Directivas de configuración** del área de trabajo **Directiva** .

## <a name="deploy-the-profile"></a>Implementar el perfil

Como un perfil es un tipo de directiva, usará el área de trabajo **Directiva** para implementarlo.

1.  En el área de trabajo **Directiva**, seleccione la directiva que quiera implementar y, después, haga clic en **Administrar la implementación**.

2.  En el cuadro de diálogo **Administrar la implementación** :

    -   **Para implementar la directiva**: seleccione uno o más grupos en los que desee implementar la directiva. A continuación, elija  **Agregar** &gt; **Aceptar**.

    -   **Para cerrar el cuadro de diálogo sin implementarla**: haga clic en **Cancelar**.


En la página **Información general** del área de trabajo **Directiva**, se muestran los problemas con la directiva que necesitan su atención. Además, aparece un resumen de estado en el área de trabajo Panel.

## <a name="security-settings"></a>Configuración de seguridad
Estas tablas contienen la información de la configuración de seguridad disponible para los perfiles de Wi-Fi de Android, iOS y Mac OS X.

### <a name="security-settings-for-android-devices"></a>Configuración de seguridad para dispositivos Android

  |Nombre de la configuración|Más información|Cuándo se debe utilizar|
|----------------|--------------------|-------------|
|**Tipo de seguridad**|Seleccione el protocolo de seguridad de la red inalámbrica:<br /><br />-   **WPA-Enterprise/WPA2-Enterprise**<br />-   **Sin autenticación (abierto)** si la red no es segura.|Siempre|
|**Tipo de EAP**|Elija el tipo Protocolo de autenticación extensible (EAP) que se usa para autenticar conexiones inalámbricas seguras:<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   **EAP-TTLS**|Si ha seleccionado el tipo de seguridad **WPA-Enterprise/WPA2-Enterprise**.|
|**Seleccionar certificados raíz para la validación del servidor**|Elija **Seleccionar** y luego el perfil de certificado raíz de confianza que se usa para autenticar la conexión. Para más información sobre cómo crear el perfil de certificado raíz de confianza, consulte [Proteger el acceso a recursos con perfiles de certificado](secure-resource-access-with-certificate-profiles.md).|Si ha seleccionado cualquier **tipo de EAP**.|
|**Método de autenticación**|Seleccione el método de autenticación que se usa para la conexión:<br /><br />-   **Certificados** para especificar el certificado de cliente<br />-   **Nombre de usuario y contraseña** para especificar otro método de autenticación|El **Tipo de EAP** es **PEAP** o **EAP-TTLS**.|
|**Seleccionar un método no EAP para la autenticación (identidad interna)**|Seleccione cómo se autenticará la conexión:<br /><br />-   **Ninguno**<br />-   **Contraseña no cifrada (PAP)**<br />-   **Protocolo de autenticación por desafío mutuo (CHAP)**<br />-   **Microsoft CHAP (MS-CHAP)**<br />-   **Microsoft CHAP versión 2 (MS-CHAP v2)**<br /><br />Las opciones disponibles dependen del tipo de EAP seleccionado.|El **Método de autenticación** es **Nombre de usuario y contraseña**.|
|**Habilitar privacidad de identidad (identidad externa)**|Especifique el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor. Durante la autenticación, se envía inicialmente esta identidad. Luego se envía la identificación real en un túnel seguro.|Si el **tipo de EAP** es **PEAP** o **EAP-TTLS**.|
|**Seleccionar un certificado de cliente para la autenticación de cliente (certificado de identidad)**|Elija **Seleccionar** y luego el perfil de certificado SCEP que se usa para autenticar la conexión. Para más información sobre cómo crear un perfil de certificado SCEP, consulte [Proteger el acceso a recursos con perfiles de certificado](secure-resource-access-with-certificate-profiles.md).|Si el tipo de seguridad es **WPA-Enterprise/WPA2-Enterprise** y se selecciona cualquier **tipo de EAP**.|

### <a name="security-settings-for-ios-and-mac-os-x-devices"></a>Configuración de seguridad para dispositivos iOS y Mac OS X

  |Nombre de la configuración|Más información|Cuándo se debe utilizar|
|----------------|--------------------|-------------|
|**Tipo de seguridad**|Seleccione el protocolo de seguridad de red inalámbrica:<br /><br />-   **WPA-Personal/WPA2-Personal**<br />-   **WPA-Enterprise/WPA2-Enterprise**<br />-   **WEP**<br />-   **Sin autenticación (abierto)** si la red no es segura.|Siempre|
|**Tipo de EAP**|Elija el tipo Protocolo de autenticación extensible (EAP) que se usa para autenticar conexiones inalámbricas seguras:<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   **EAP-TLS**<br />-   **EAP-AST**<br />-   **LEAP**<br />-   **EAP-SIM**|Si seleccionó un tipo de seguridad de **WPA-Enterprise/WPA2-Enterprise**.|
|**Nombres de certificado de servidor de confianza**|Seleccione el perfil de certificado raíz de confianza que se usa para autenticar la conexión. Para más información sobre cómo crear el perfil de certificado raíz de confianza, consulte [Proteger el acceso a recursos con perfiles de certificado](secure-resource-access-with-certificate-profiles.md).|Si seleccionó un tipo de EAP de **EAP-TLS**, **PEAP**, **EAP-TTLS** o **EAP-FAST**.|
|**Usar credenciales de acceso protegido (PAC)**|Seleccione esta opción para usar credenciales de acceso protegido para establecer un túnel autenticado entre el cliente y el servidor de autenticación. Si está presente, se utiliza un archivo PAC existente.|Si el **tipo de EAP** es **EAP-FAST**.|
|**Aprovisionar PAC**|Configura el archivo PAC en sus dispositivos.<br /><br />Cuando se usa, también puede seleccionar **Aprovisionar PAC de forma anónima** para asegurarse de que el archivo PAC se configure sin autenticar el servidor.|Se seleccionó **Utilizar credencial de acceso protegido (PAC)**.|
|**Método de autenticación**|Seleccione el método de autenticación que se usa para la conexión:<br /><br /><ul><li>**Certificados** para especificar el certificado de cliente</li><li>**Nombre de usuario y contraseña** para especificar uno de los siguientes métodos de autenticación que no son EAP (también conocidos como identidad interna):<br /><br /><ul><li>**Ninguno**</li><li>**Contraseña no cifrada (PAP)**</li><li>**Protocolo de autenticación de desafío mutuo (CHAP)**</li><li>**Microsoft CHAP (MS-CHAP)**</li><li>**Microsoft CHAP versión 2 (MS-CHAP v2)**</li><li>**EAP-TLS**</li></ul></li></ul>|Si el **tipo de EAP** es **PEAP** o **EAP-TTLS**.|
|**Seleccionar un certificado de cliente para la autenticación de cliente (certificado de identidad)**|Seleccione el perfil de certificado SCEP que se usa para autenticar la conexión. Para más información sobre cómo crear un perfil de certificado SCEP, consulte [Proteger el acceso a recursos con perfiles de certificado](secure-resource-access-with-certificate-profiles.md).|Si el tipo de seguridad es **WPA-Enterprise/WPA2-Enterprise** y el **tipo de EAP** es **EAP-TLS**, **PEAP** o **EAP-TTLS**.|
|**Habilitar privacidad de identidad (identidad externa)**|Especifique el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor.<br /><br />Durante la autenticación, se envía inicialmente esta identidad. Luego se envía la identificación real en un túnel seguro.|Si el **tipo de EAP** está establecido en **PEAP**, **EAP-TTLS** o **EAP-FAST**.|


### <a name="see-also"></a>Consulte también
Aprenda a crear un perfil de Wi-Fi con una clave precompartida en [Crear un perfil de Wi-Fi con una clave precompartida](pre-shared-key-wi-fi-profile.md).
