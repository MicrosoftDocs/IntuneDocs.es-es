---
title: Conexiones VPN | Microsoft Docs
description: "Use los perfiles de VPN para implementar la configuración de VPN para los usuarios y dispositivos de su organización."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: abc57093-7351-408f-9f41-a30877f96f73
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: a9748a0ad6b9bbe10e36ba133ba74edb6aa6e09a
ms.openlocfilehash: 2801d6a3cc672fbf91f89d2586c36b6bd3f18490
ms.contentlocale: es-es
ms.lasthandoff: 05/05/2017


---

# <a name="vpn-connections-in-microsoft-intune"></a>VPN connections in Microsoft Intune (Conexiones VPN en Microsoft Intune)

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Las redes privadas virtuales (VPN) ofrecen a los usuarios un acceso remoto seguro a la red de la empresa. Los dispositivos utilizan un *perfil de conexión VPN* para iniciar una conexión con el servidor VPN. Use los *Perfiles de VPN* en Microsoft Intune para implementar la configuración de VPN para los usuarios y dispositivos de su organización, para que puedan conectarse de forma fácil y segura a la red.

Por ejemplo, suponga que quiere aprovisionar todos los dispositivos iOS con la configuración necesaria para conectarse a un recurso compartido de archivos de la red corporativa. Debe crear un perfil de VPN con la configuración necesaria para conectarse a la red corporativa y, a continuación, debe implementar este perfil en todos los usuarios con dispositivos iOS. Los usuarios ven la conexión VPN en la lista de redes disponibles y pueden conectarse realizando un mínimo esfuerzo.

Puede configurar los siguientes tipos de dispositivo con perfiles de VPN:

* Dispositivos que ejecutan Android 4 y versiones posteriores
* Dispositivos Android for Work
* Dispositivos que ejecutan iOS 8.0 y versiones posteriores
* Dispositivos que ejecutan Mac OS X 10.9 y versiones posteriores
* Dispositivos inscritos que ejecutan Windows 8.1 y versiones posteriores
* Dispositivos que ejecutan Windows Phone 8,1 y versiones posteriores
* Dispositivos que ejecutan Windows 10 para escritorios y Windows 10 Mobile

Las opciones de configuración del perfil de VPN varían según el tipo de dispositivo que seleccione.

## <a name="vpn-connection-types"></a>Tipos de conexión VPN

Intune permite crear perfiles de VPN que usan los siguientes tipos de conexión:


Tipo de conexión |iOS y Mac OS X  |Android y Android for Work|Windows 8.1|Windows RT 8.1|Windows Phone 8.1|Windows 10 para escritorios y Windows 10 Mobile |
----------------|------------------|-------|-----------|----------|--------------|-----------------|----------------------|
Cisco AnyConnect|Sí |Sí   |No    |No  |No    | Sí, (OMA-URI, solo móvil)|     
Cisco (IPsec)|Sí |Sí   |No  |No  |No | No|
Citrix|Sí |Sí (solo Android)   |No  |No  |No | No|
Pulse Secure|Sí  |Sí |Sí   |Sí  |Sí| Sí|        
F5 Edge Client|Sí |Sí |Sí |Sí  |   Sí |  Sí|   
Dell SonicWALL Mobile Connect|Sí |Sí |Sí |Sí |Sí |Sí|         
CheckPoint Mobile VPN|Sí |Sí |Sí |Sí|Sí|Sí|
Microsoft SSL (SSTP)|No |No |No |No|No|VPNv1 OMA-URI*|
Microsoft Automatic|No |No |No |No|Sí (OMA-URI)|Sí|
IKEv2|Perfil personalizado de iOS|No |No |No|Sí (OMA-URI)|Sí|
PPTP|Perfil personalizado de iOS|No |No |No|No|Sí|
L2TP|Perfil personalizado de iOS|No |No |No|Sí (OMA-URI)|Sí|

\*Sin configuración adicional que, de otro modo, está disponible en Windows 10.

> [!IMPORTANT]
> Para poder usar perfiles de VPN que se implementen en un dispositivo, debe instalar la aplicación VPN aplicable para el perfil. Puede usar la información del tema [Implementar aplicaciones en Microsoft Intune](deploy-apps-in-microsoft-intune.md) para ayudarle a implementar la aplicación correspondiente con Intune.  

 Obtenga información sobre cómo crear perfiles de VPN personalizados con la configuración de URI en [Personalizar configuraciones para perfiles de VPN](create-custom-vpn-profiles.md).     

## <a name="methods-of-securing-vpn-profiles"></a>Métodos para proteger los perfiles de VPN

Los perfiles de VPN pueden utilizar diferentes tipos de conexiones y protocolos de diferentes fabricantes. Estas conexiones normalmente se protegen con uno de dos métodos.

### <a name="certificates"></a>Certificados

Al crear el perfil de VPN, elija un perfil de certificado SCEP o .PFX que haya creado previamente en Intune. Esto se conoce como certificado de identidad y se utiliza para autenticar con un perfil de certificado de confianza (o un *certificado raíz*) que ha creado para establecer que el dispositivo del usuario tiene permiso para conectarse. El certificado de confianza se implementa en el equipo que autentica la conexión VPN, por lo general, el servidor de VPN.

Para más información sobre cómo crear y usar perfiles de certificado en Intune, vea [Secure resource access with certificate profiles](secure-resource-access-with-certificate-profiles.md) (Proteger el acceso a recursos con perfiles de certificado).

### <a name="user-name-and-password"></a>Nombre de usuario y contraseña

El usuario se autentica en el servidor de VPN proporcionando el nombre de usuario y contraseña.

## <a name="create-a-vpn-profile"></a>Crear un perfil de VPN

1. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), seleccione **Directiva** > **Agregar directiva**.
2. Seleccione una plantilla para la nueva directiva expandiendo el tipo de dispositivo correspondiente y, a continuación, elija el perfil de VPN para dicho dispositivo:
    * **Perfil de VPN (Android 4 y versiones posteriores)**
    * **Perfil de VPN (Android for Work)**
    * **Perfil de VPN (iOS 8.0 y versiones posteriores)**
    * **Perfil de VPN (Mac OS X 10.9 y versiones posteriores)**
    * **Perfil de VPN (Windows 8.1 y versiones posteriores)**
    * **Perfil de VPN (Windows Phone 8.1 y versiones posteriores)**
    * **Perfil de VPN (Windows 10 para escritorios y Windows 10 Mobile y versiones posteriores)**

 Solo puede crear e implementar una directiva de perfiles de VPN. La configuración recomendada no está disponible.

> [!Note]
> Un perfil VPN para dispositivos Android for Work permitirá una conexión VPN solo a las aplicaciones que están instaladas en el perfil de trabajo del dispositivo.
>
> Algunos tipos de conexión VPN admiten VPN por aplicación para dispositivos Android for Work y para habilitar VPN por aplicación en aplicaciones distribuidas a través de Intune.  

3. Utilice la tabla siguiente como ayuda para configurar las opciones del perfil de VPN:

Nombre de la configuración  |Más información  
---------|---------
**Nombre**     |Escriba un nombre único para el perfil de VPN que le ayude a identificarlo en la consola de Intune.         
**Descripción**     |Proporcione una descripción general del perfil de VPN y otra información relevante que le ayude a encontrarlo.         
**Nombre de conexión VPN (se muestra a los usuarios)**     |Especifique un nombre para el perfil de VPN. Este es el nombre que los usuarios verán en la lista de conexiones VPN disponibles en sus dispositivos.         
**Tipo de conexión**     |  Seleccione uno de los siguientes tipos de conexión para usarlo en el perfil de VPN: **Cisco AnyConnect** (no disponible para Windows 8.1 ni Windows Phone 8.1), **Pulse Secure**, **Citrix**, **F5 Edge Client**, **Dell SonicWALL Mobile Connect** o **CheckPoint Mobile VPN**.
**Descripción del servidor VPN**     | Especifique una descripción para el servidor VPN al que se conectarán los dispositivos. **Ejemplo:** servidor VPN de Contoso. Cuando el tipo de conexión es **F5 Edge Client**, use el campo **Lista de servidores** para especificar una lista de descripciones de servidor y direcciones IP.
**Dirección IP o FQDN del servidor**    |Proporcione la dirección IP o el nombre de dominio completo del servidor VPN al que se conectarán los dispositivos. Ejemplos: **192.168.1.1**, **vpn.contoso.com**.  Cuando el tipo de conexión es **F5 Edge Client**, use el campo **Lista de servidores** para especificar una lista de descripciones de servidor y direcciones IP.         |         
**Lista de servidores**     |Seleccione **Agregar** para agregar un nuevo servidor VPN que se usará para la conexión VPN. También puede especificar qué servidor será el servidor predeterminado para la conexión. Esta opción solo se muestra cuando el tipo de conexión es **F5 Edge Client**.         
**Enviar todo el tráfico de red a través de la conexión VPN**     |Si selecciona esta opción, todo el tráfico de red se envía a través de la conexión VPN. Si no selecciona esta opción, el cliente negociará dinámicamente las rutas de túnel dividido al conectarse al servidor VPN de terceros. Solo las conexiones con la red de la empresa se envían a través de un túnel VPN. El túnel de VPN no se utiliza al conectarse a recursos de Internet.
**Método de autenticación**| Seleccione el método de autenticación que use la conexión VPN: **Certificados** o **Nombre de usuario y contraseña**. (**Nombre de usuario y contraseña** no está disponible cuando el tipo de conexión es Cisco AnyConnect). La opción **Método de autenticación** no está disponible para Windows 8.1.
**Recordar las credenciales de usuario en cada inicio de sesión**|Seleccione esta opción para asegurarse de que se recuerdan las credenciales de usuario para que el usuario no tenga que escribirlas cada vez que se establezca una conexión.
**Seleccionar un certificado de cliente para la autenticación de cliente (certificado de identidad)**|Seleccione el certificado SCEP de cliente que creó previamente y que se utilizará para autenticar la conexión VPN. Para obtener más información sobre cómo usar perfiles de certificado en Intune, consulte [Secure resource access with certificate profiles (Proteger el acceso a recursos con perfiles de certificado)](secure-resource-access-with-certificate-profiles.md). Esta opción solo se muestra cuando el método de autenticación es **Certificados**.
**Rol**| Especifique el nombre del rol de usuario que tiene acceso a esta conexión. Un rol de usuario define la configuración personal y las opciones, y habilita o deshabilita ciertas características de acceso. Esta opción solo se muestra cuando el tipo de conexión es **Pulse Secure** o **Citrix**.
**Dominio Kerberos**|Especifique el nombre de dominio de autenticación que quiere usar. Un dominio de autenticación es una agrupación de recursos de autenticación que usa el tipo de conexión Pulse Secure o Citrix. Esta opción solo se muestra cuando el tipo de conexión es **Pulse Secure** o **Citrix**.
**Dominio o grupo de inicio de sesión**|Especifique el nombre del grupo o dominio de inicio de sesión al que quiere conectarse. Esta opción solo se muestra cuando el tipo de conexión es **Dell SonicWALL Mobile Connect**.
**Huella digital**|Especifique una cadena (por ejemplo "Código de huella digital de Contoso") que se utilizará para comprobar que se puede confiar en el servidor VPN. Una huella digital se puede enviar al cliente para que sepa que puede confiar en cualquier servidor que presente esa misma huella digital al conectarse. Si el dispositivo ya no tiene la huella digital, pedirá al usuario que confíe en el servidor VPN al que se está conectando mientras muestra la huella digital. El usuario comprueba la huella digital manualmente y elige **confiar** para conectar. Esta opción solo se muestra cuando el tipo de conexión es **CheckPoint Mobile VPN**.
**Por cada aplicación VPN**|Seleccione esta opción si quiere asociar esta conexión VPN con una aplicación iOS de Mac OS X para que la conexión se abra cuando se ejecute la aplicación. Puede asociar el perfil de VPN con una aplicación al implementar el software. Para obtener más información, consulte [Deploy apps in Microsoft Intune](deploy-apps-in-microsoft-intune.md) (Implementar aplicaciones en Microsoft Intune).
**VPN a petición**|Puede establecer la VPN a petición para dispositivos iOS 8.0 y versiones posteriores. Se proporcionan instrucciones para la configuración en [VPN a petición para dispositivos iOS](#on-demand-vpn-for-ios-devices).
**Detectar automáticamente la configuración de proxy** (solo iOS, Mac OS X, Windows 8.1 y Windows Phone 8.1)|Si el servidor VPN requiere un servidor proxy para la conexión, especifique si quiere que los dispositivos detecten automáticamente la configuración de la conexión. Para más información, vea la documentación de Windows Server.
**Usar script de configuración automática** (solo iOS, Mac OS X, Windows 8.1 y Windows Phone 8.1)|Si el servidor VPN requiere un servidor proxy para la conexión, especifique si desea usar un script de configuración automática para definir la configuración y, después, especifique una dirección URL al archivo que contiene la configuración. Para más información, vea la documentación de Windows Server.
**Usar servidor proxy** (solo iOS, Mac OS X, Windows 8.1 y Windows Phone 8.1)|Si el servidor VPN requiere un servidor proxy para la conexión, seleccione esta opción y especifique el número de puerto y la dirección del servidor proxy. Para más información, vea la documentación de Windows Server.
**Omitir configuración proxy para direcciones locales** (solo iOS, Windows 8.1 y Windows Phone 8.1)|Si el servidor VPN requiere un servidor proxy para la conexión, seleccione esta opción si no quiere utilizar el servidor proxy para las direcciones locales que especifique. Para más información, vea la documentación de Windows Server.
**XML personalizado** (Windows 8.1 y versiones posteriores y Windows Phone 8.1 y versiones posteriores)|Especifique los comandos XML personalizados que configuran la conexión VPN. Ejemplo para **Pulse Secure**: &lt;pulse-schema&gt;&lt;isSingleSignOnCredential&gt;true&lt;/isSingleSignOnCredential&gt;&lt;/pulse-schema&gt;. Ejemplo para **CheckPoint Mobile VPN**: &lt;CheckPointVPN port="443" name="CheckPointSelfhost" sso="true"  debug="3" /&gt;. Ejemplo para **Dell SonicWALL Mobile Connect**: &lt;MobileConnect&gt;&lt;Compression&gt;false&lt;/Compression&gt;&lt;debugLogging&gt;True&lt;/debugLogging&gt;&lt;packetCapture&gt;False&lt;/packetCapture&gt;&lt;/MobileConnect&gt;. Ejemplo para **F5 Edge Client**: &lt;f5-vpn-conf&gt;&lt;single-sign-on-credential /&gt;&lt;/f5-vpn-conf&gt;. Consulte la documentación de VPN de cada fabricante para más información sobre cómo escribir comandos XML personalizados.
**Lista de búsqueda de sufijos DNS** (solo Windows Phone 8.1)|Especifique un sufijo DNS en cada línea. Al conectarse a un sitio web mediante un nombre corto, se buscará cada sufijo DNS que especifique. Por ejemplo, especifique los sufijos DNS **domain1.contoso.com** y **domain2.contoso.com**, visite la dirección URL **http://mywebsite**, y se buscarán las direcciones URL **http://mywebsite.domain1.contoso.com** y **http://mywebsite.domain2.contoso.com**.
**Omitir VPN cuando se está conectado a una red Wi-Fi de la empresa** (solo Windows Phone 8.1)|Seleccione esta opción para especificar que la conexión VPN no se utilizará cuando el dispositivo se conecte a la red Wi-Fi de la empresa.
**Omitir VPN cuando se está conectado a una red Wi-Fi doméstica** (solo Windows Phone 8.1)|Seleccione esta opción para especificar que la conexión VPN no se utilizará cuando el dispositivo se conecte a la red Wi-Fi doméstica.

Los siguientes valores de configuración adicionales están disponibles para los dispositivos con Windows 10 Mobile y de escritorio.

Nombre de la configuración  |Más información  
---------|---------
**Reglas de tráfico de red**|Seleccione qué protocolos, y qué puertos locales y remotos e intervalos de direcciones se habilitarán para la conexión VPN. Si no se crea ninguna regla de tráfico de red, se habilitan todos los protocolos, puertos e intervalos de direcciones. Una vez creada una regla, la conexión VPN solo usará los protocolos, puertos e intervalos de direcciones que especifique en esa regla.
**Rutas**|Seleccione las rutas que usará la conexión VPN.
**Servidores DNS**| Seleccione los servidores DNS que utilizará la conexión VPN una vez establecida la conexión.         
**Aplicaciones asociadas**|Proporcione una lista de las aplicaciones que usarán automáticamente la conexión VPN. El tipo de aplicación determinará el identificador de la aplicación. Para una aplicación universal, proporcione el nombre de familia de paquete. Para una aplicación de escritorio, proporcione la ruta de acceso al archivo de la aplicación.          


> [!IMPORTANT]
> Se recomienda proteger todas las listas de aplicaciones que se compilen para su uso en la configuración de VPN por aplicación. Si un usuario no autorizado modifica la lista y, luego, se importa a la lista de aplicaciones de VPN por aplicación, se estará corriendo el riesgo de autorizar el acceso a VPN a aplicaciones que no deberían tenerlo. Una forma de proteger las listas de aplicaciones consiste en usar una lista de control de acceso (ACL).

A continuación se incluye un ejemplo de cuándo se puede utilizar la configuración de límites de la compañía. Si desea habilitar VPN solo para Escritorio Remoto, cree una regla de tráfico de red que permita el tráfico para el protocolo 27 en el puerto externo 3996. Ningún otro tráfico usará la VPN.

Definir las rutas en los límites de la empresa es útil cuando el tipo de conexión VPN no permite definir cómo se controla el tráfico de túnel dividido. En ese caso, use **Rutas** para enumerar las rutas que usarán la conexión VPN.

Puede restringir el uso de la VPN para dispositivos Windows 10 a aplicaciones específicas mediante la creación de una configuración personalizada de OMA-URI.

La nueva directiva aparece en el nodo **Directivas de configuración** del área de trabajo **Directiva** .

### <a name="on-demand-vpn-for-ios-devices"></a>VPN a petición para dispositivos iOS
Puede configurar la VPN a petición para dispositivos iOS 8.0 y versiones posteriores.

> [!NOTE]
>  
> No puede usar la VPN por aplicación y la VPN a petición en la misma directiva.

1. En la página de configuración de directiva, busque **Reglas a petición para esta conexión VPN**. Las columnas se etiquetan como **Coincidencia**, la condición que comprueba las reglas y **Acción**, la acción que la directiva desencadenará cuando la condición coincida.
2. Elija **Agregar** para crear una regla. Hay dos tipos de coincidencias que se pueden configurar en la regla. Solo se puede configurar uno de estos tipos por regla.
  - **SSID**, que se hacen referencia a las redes inalámbricas.
  - **Dominios de búsqueda DNS**. Puede utilizar nombres de dominio completo, como *team.corp.contoso.com* o usar dominios como *contoso.com*, que es equivalente a usar * *.contoso.com*.
3. Opcional: proporcione un sondeo de cadena de dirección URL, que es una dirección URL que usa la regla de prueba. Si el dispositivo en el que está instalado este perfil puede acceder a esta dirección URL sin redirección, se establecerá la VPN y el dispositivo se conectará a la dirección URL de destino. El usuario no verá el sitio de sondeo de cadena de dirección URL. Un ejemplo de un sondeo de cadena de dirección URL es la dirección de un servidor web de auditoría que comprueba el cumplimiento del dispositivo antes de conectarse a la VPN. Otra posibilidad es que la dirección URL comprueba la capacidad de la VPN para conectarse a un sitio, antes de conectar el dispositivo a la dirección URL de destino a través de VPN.
4. Elija una de las acciones siguientes:
  - **Connect**
  - **Evaluar conexión**, que tiene tres configuraciones a. **Acción del dominio**: elija **Conectarse si es necesario** o **No conectarse nunca**
     b. **Lista de dominios separados por comas**: configure esta opción solo si elige una **acción del dominio** de **Conectarse si es necesario**
     c. **Sondeo de cadena de dirección URL requerida**: dirección URL HTTP o HTTPS (preferido), como *https://vpntestprobe.contoso.com*. La regla comprueba si hay una respuesta desde esta dirección. Si no la hay y la **acción del dominio** es **Conectarse si es necesario**, se activará la VPN.
      
     > [!TIP]
     >
     >Un ejemplo de cuándo se puede usar esta acción es cuando algunos sitios de la red corporativa requieren una conexión de red corporativa directa o de VPN, pero otros no. Si la lista de **Lista de dominios de búsqueda de DNS separados por comas** *corp.contoso.com*, puede elegir **Conectarse si es necesario** y luego mostrar sitios específicos dentro de esa red que pueden requerir la VPN, como *sharepoint.corp.contoso.com*. La regla, después, comprobará si se puede conectar con *vpntestprobe.contoso.com*. En caso contrario, se activará la VPN para el sitio de SharePoint.
  - **Omitir**: no se produce ningún cambio en la conectividad de VPN. Si está conectada la VPN, déjela conectada; si no lo está, no la conecte. Por ejemplo, puede tener una regla que se conecte a la VPN para todos los sitios web corporativos internos, pero quiere que uno de esos sitios internos solo sea accesible cuando el dispositivo está realmente conectado a la red corporativa. En ese caso, podría crear una regla de omisión para ese sitio.
  - **Desconectar**: desconecte dispositivos de la VPN cuando se cumplen las condiciones. Por ejemplo, podría enumerar las redes inalámbricas corporativas en el campo **SSID** y crear una regla que desconecte los dispositivos de la VPN cuando se conecten a una de esas redes.

Las reglas específicas de dominio se evalúan antes que las reglas de todos los dominios.


## <a name="deploy-the-policy"></a>Implementar la directiva

1.  En el área de trabajo **Directiva**, seleccione la directiva que quiera implementar y, después, haga clic en **Administrar implementación**.

2.  En el cuadro de diálogo **Administrar la implementación** :

    -   Para implementar la directiva, seleccione uno o más grupos en los que quiera implementarla y luego elija **Add** (Agregar) &gt; **OK** (Aceptar).

    -   Para cerrar el cuadro de diálogo sin implementarla, seleccione **Cancelar**.


Tras una implementación correcta, los usuarios verán el nombre de la conexión VPN especificado en la lista de conexiones VPN en sus dispositivos.

En el área de trabajo **Directiva** de la página **General** , un resumen de estado y las alertas identifican los problemas de la directiva que requieren su atención. Además, aparece un resumen de estado en el área de trabajo Panel.

