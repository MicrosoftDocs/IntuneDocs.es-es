---
title: Conexiones VPN | Microsoft Intune
description: "Use los perfiles de VPN para implementar la configuración de VPN en los usuarios y los dispositivos de la organización."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 09/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: abc57093-7351-408f-9f41-a30877f96f73
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 957edcf6910dd15f15ab5020773233c6a6ba0ea7
ms.openlocfilehash: fb5fbbe50295d3fc26f3cd4def4f40898bb6ffd2


---

# Conexiones VPN en Microsoft Intune
 Puede usar redes privadas virtuales (VPN) para ofrecer a los usuarios un acceso remoto seguro a la red de la empresa. Los usuarios remotos pueden trabajar como si su dispositivo estuviera conectado físicamente a la red. Los dispositivos utilizan un perfil de conexión VPN para iniciar una conexión con el servidor VPN. Use los *perfiles de VPN* en Microsoft Intune para implementar la configuración de VPN en los usuarios y los dispositivos de la organización. Mediante la implementación de esta configuración, se minimiza la intervención del usuario final necesaria para conectarse a los recursos de la red de la empresa.

Por ejemplo, supongamos que quiere aprovisionar todos los dispositivos iOS con la configuración necesaria para conectarse a un recurso compartido de archivos de la red corporativa. Debe crear un perfil de VPN que contenga la configuración necesaria para conectarse a la red corporativa y, después, debe implementar este perfil en todos los usuarios que tengan dispositivos iOS. Los usuarios ven la conexión VPN en la lista de redes disponibles y pueden conectarse con un esfuerzo mínimo.

Puede configurar los siguientes tipos de dispositivo mediante perfiles de VPN:

* Dispositivos que ejecutan Android 4 y versiones posteriores
* Dispositivos que ejecutan iOS 8.0 y versiones posteriores
* Dispositivos que ejecutan Mac OS X 10.9 y versiones posteriores
* Dispositivos inscritos que ejecutan Windows 8.1 y versiones posteriores
* Dispositivos que ejecutan Windows Phone 8,1 y versiones posteriores
* Dispositivos que ejecutan Windows 10 Escritorio y Mobile

Las opciones de configuración del perfil de VPN varían según el tipo de dispositivo que seleccione.

## Tipos de conexión VPN

Intune permite crear perfiles de VPN que usan los siguientes tipos de conexión:




Tipo de conexión |iOS y Mac OS X  |Android|Windows 8.1|Windows RT|Windows RT 8.1|Windows Phone 8.1|Windows 10 Escritorio y Mobile |
----------------|------------------|-------|-----------|----------|--------------|-----------------|----------------------|
Cisco AnyConnect|Sí |Sí   |No    |     No    |No  |No    | Sí (OMA-URI, solo Mobile)|     
Cisco (IPsec)|Sí |No   |No  |  No|No  |No | No|
Citrix|Sí |No   |No  |  No|No  |No | No|
Pulse Secure|Sí  |Sí |Sí   |No  |Sí  |Sí| Sí|        
F5 Edge Client|Sí |Sí |Sí |No  |Sí  |   Sí |  Sí|   
Dell SonicWALL Mobile Connect|Sí |Sí |Sí |No  |Sí |Sí |Sí|         
CheckPoint Mobile VPN|Sí |Sí |Sí |Sí |Sí|Sí|Sí|
Microsoft SSL (SSTP)|No |No |No |No |No|No|VPNv1 OMA-URI*|
Microsoft Automatic|No |No |No |No |No|Sí (OMA-URI)|Sí|
IKEv2|Perfil personalizado de iOS|No |No |No |No|Sí (OMA-URI)|Sí|
PPTP|Perfil personalizado de iOS|No |No |No |No|No|Sí|
L2TP|Perfil personalizado de iOS|No |No |No |No|Sí (OMA-URI)|Sí|

\* Sin las opciones de configuración adicionales que están disponibles para Windows 10 en los demás casos.

> [!IMPORTANT]
> Para poder usar perfiles de VPN que se implementen en un dispositivo, debe instalar la aplicación VPN aplicable para el perfil. Puede usar la información del tema [Implementar aplicaciones en Microsoft Intune](deploy-apps-in-microsoft-intune.md) para que le sea más fácil implementar la aplicación correspondiente con Intune.  

 Obtenga información sobre cómo crear perfiles de VPN personalizados mediante la configuración de URI indicada en [Configuraciones personalizadas para perfiles de VPN](custom-configurations-for-vpn-profiles.md).     

## Métodos para proteger perfiles de VPN

Los perfiles de VPN pueden utilizar diferentes tipos de conexiones y protocolos de diferentes fabricantes. Para proteger estas conexiones, se suele emplear uno de los dos métodos posibles.

### Certificados

Al crear el perfil de VPN, elija un perfil de certificado SCEP o PFX que haya creado previamente en Intune.

Se denomina «certificado de identidad». Se usa para autenticar con un perfil de certificado de confianza (o un certificado raíz) que haya creado para hacer que el dispositivo del usuario tenga permiso para conectarse. El certificado de confianza se implementa en el equipo que autentica la conexión VPN, por lo general, el servidor de VPN.

Para obtener más información sobre cómo crear y usar perfiles de certificado en Intune, consulte [Proteger el acceso a recursos con perfiles de certificado](secure-resource-access-with-certificate-profiles.md).

### Nombre de usuario y contraseña

El usuario se autentica en el servidor de VPN proporcionando un nombre de usuario y una contraseña.

## Crear un perfil de VPN

1. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Directiva** > **Agregar directiva**.
2. Seleccione una plantilla para la nueva directiva expandiendo el tipo de dispositivo correspondiente y, después, elija el perfil de VPN para dicho dispositivo:
    * **Perfil de VPN (Android 4 y versiones posteriores)**
    * **Perfil de VPN (iOS 8.0 y versiones posteriores)**
    * **Perfil de VPN (Mac OS X 10.9 y versiones posteriores)**
    * **Perfil de VPN (Windows 8.1 y versiones posteriores)**
    * **Perfil de VPN (Windows Phone 8.1 y versiones posteriores)**
    * **Perfil de VPN (Windows 10 para escritorios y Windows 10 Mobile y versiones posteriores)**

 Solo puede crear e implementar una directiva personalizada de perfiles de VPN. La configuración recomendada no está disponible.

3. Utilice la tabla siguiente como ayuda para configurar las opciones del perfil de VPN:

Nombre de la configuración  |Más información  
---------|---------
**Nombre**     |Escriba un nombre único para el perfil de VPN que le ayude a identificarlo en la consola de Intune.         
**Descripción**     |Proporcione una descripción general del perfil de VPN y otra información relevante que le ayude a encontrarlo.         
**Nombre de conexión VPN (se muestra a los usuarios)**     |Especifique un nombre para el perfil de VPN. Este es el nombre que los usuarios verán en la lista de conexiones VPN disponibles en sus dispositivos.         
**Tipo de conexión**     |  Seleccione uno de los siguientes tipos de conexión para usarlo en el perfil de VPN: **Cisco AnyConnect** (no disponible para Windows 8.1 o Windows Phone 8.1), **Pulse Secure**, **F5 Edge Client**, **Dell SonicWALL Mobile Connect** o **CheckPoint Mobile VPN**.
**Descripción del servidor VPN**     | Especifique una descripción para el servidor VPN al que se conectarán los dispositivos. Ejemplo: **servidor VPN de Contoso**. Cuando el tipo de conexión sea **F5 Edge Client**, use el campo **Lista de servidores** para especificar una lista de descripciones de servidor y direcciones IP.
**Dirección IP o FQDN del servidor**    |Proporcione la dirección IP o el nombre de dominio completo del servidor VPN al que se conectarán los dispositivos. Ejemplos: **192.168.1.1**, **vpn.contoso.com**.  Cuando el tipo de conexión sea **F5 Edge Client**, use el campo **Lista de servidores** para especificar una lista de descripciones de servidor y direcciones IP.         |         
**Lista de servidores**     |Elija **Agregar** para agregar un nuevo servidor VPN que se usará para la conexión VPN. También puede especificar qué servidor será el servidor predeterminado para la conexión. Esta opción solo se muestra cuando el tipo de conexión es **F5 Edge Client**.         
**Enviar todo el tráfico de red a través de la conexión VPN**     |Si selecciona esta opción, todo el tráfico de red se envía a través de la conexión VPN. Si no selecciona esta opción, el cliente negociará dinámicamente las rutas de túnel dividido al conectarse al servidor VPN de terceros. Solo las conexiones con la red de la empresa se envían a través de un túnel VPN. El túnel de VPN no se utiliza al conectarse a recursos de Internet.
**Método de autenticación**| Seleccione el método de autenticación que usa la conexión VPN: **Certificados** o **Nombre de usuario y contraseña**. (La opción **Nombre de usuario y contraseña** no está disponible cuando el tipo de conexión es Cisco AnyConnect). La opción **Método de autenticación** no está disponible para Windows 8.1.
**Recordar las credenciales de usuario en cada inicio de sesión**|Seleccione esta opción para asegurarse de que se recuerdan las credenciales de usuario para que el usuario no tenga que escribirlas cada vez que se establezca una conexión.
**Seleccionar un certificado de cliente para la autenticación de cliente (certificado de identidad)**|Seleccione el certificado SCEP de cliente que creó previamente y que se usará para autenticar la conexión VPN. Para obtener más información sobre cómo usar perfiles de certificado en Intune, consulte [Proteger el acceso a recursos con perfiles de certificado](secure-resource-access-with-certificate-profiles.md). Esta opción solo se muestra cuando el método de autenticación es **Certificados**.
**Rol**| Especifique el nombre del rol de usuario que tiene acceso a esta conexión. Un rol de usuario define la configuración personal y las opciones, y habilita o deshabilita ciertas características de acceso. Esta opción solo se muestra cuando el tipo de conexión es **Pulse Secure**.
**Dominio Kerberos**|Especifique el nombre de dominio de autenticación que quiere usar. Un dominio de autenticación es una agrupación de recursos de autenticación usada por el tipo de conexión Pulse Secure. Esta opción solo se muestra cuando el tipo de conexión es **Pulse Secure**.
**Dominio o grupo de inicio de sesión**|Especifique el nombre del grupo o dominio de inicio de sesión al que quiere conectarse. Esta opción solo se muestra cuando el tipo de conexión es **Dell SonicWALL Mobile Connect**.
**Huella digital**|Especifique una cadena (por ejemplo, "Código de huella digital de Contoso") que se usará para comprobar que se puede confiar en el servidor VPN. Se puede enviar al cliente una huella digital para que sepa que puede confiar en cualquier servidor que presente esa misma huella digital al conectarse. Si el dispositivo todavía no tiene la huella digital, pedirá al usuario que confíe en el servidor VPN al que se está conectando mientras muestra la huella digital. (El usuario comprueba la huella digital manualmente y elige **Confiar** para conectarse). Esta opción solo se muestra cuando el tipo de conexión es **CheckPoint Mobile VPN**.
**VPN por aplicación**|Seleccione esta opción si quiere asociar esta conexión VPN con una aplicación iOS o Mac OS X para que la conexión se abra cuando se ejecute la aplicación. Puede asociar el perfil de VPN con una aplicación al implementar el software. Para obtener más información, consulte [Implementar aplicaciones en Microsoft Intune ](deploy-apps-in-microsoft-intune.md).
**VPN a petición**|Puede establecer VPN a petición para dispositivos iOS 8.0 y versiones posteriores. Se proporcionan instrucciones de configuración en [VPN a petición para dispositivos iOS](#on-demand-vpn-for-ios-devices).
**Detectar automáticamente configuración de proxy** (solo iOS, Mac OS X, Windows 8.1 y Windows Phone 8.1)|Si el servidor VPN requiere un servidor proxy para la conexión, especifique si quiere que los dispositivos detecten automáticamente la configuración de la conexión. Para obtener más información, consulte la documentación de Windows Server.
**Usar script de configuración automática** (solo iOS, Mac OS X, Windows 8.1 y Windows Phone 8.1)|Si el servidor VPN requiere un servidor proxy para la conexión, especifique si quiere usar un script de configuración automática para definir la configuración y, después, especifique la dirección URL del archivo que contiene la configuración. Para obtener más información, consulte la documentación de Windows Server.
**Usar servidor proxy** (solo iOS, Mac OS X, Windows 8.1 y Windows Phone 8.1)|Si el servidor VPN requiere un servidor proxy para la conexión, seleccione esta opción y especifique el número de puerto y la dirección del servidor proxy. Para obtener más información, consulte la documentación de Windows Server.
**Omitir configuración proxy para direcciones locales** (solo iOS, Mac OS X, Windows 8.1 y Windows Phone 8.1)|Si el servidor VPN requiere un servidor proxy para la conexión, seleccione esta opción si no quiere utilizar el servidor proxy para las direcciones locales que especifique. Para obtener más información, consulte la documentación de Windows Server.
**XML personalizado** (Windows 8.1 y versiones posteriores, y Windows Phone 8.1 y versiones posteriores)|Especifique los comandos XML personalizados que configuran la conexión VPN. Ejemplo de **Pulse Secure**: &lt;pulse-schema&gt;&lt;isSingleSignOnCredential&gt;true&lt;/isSingleSignOnCredential&gt;&lt;/pulse-schema&gt;. Ejemplo de **CheckPoint Mobile VPN**: &lt;CheckPointVPN port="443" name="CheckPointSelfhost" sso="true"  debug="3" /&gt;. Ejemplo de **Dell SonicWALL Mobile Connect**: &lt;MobileConnect&gt;&lt;Compression&gt;false&lt;/Compression&gt;&lt;debugLogging&gt;True&lt;/debugLogging&gt;&lt;packetCapture&gt;False&lt;/packetCapture&gt;&lt;/MobileConnect&gt;. Ejemplo de **F5 Edge Client**: &lt;f5-vpn-conf&gt;&lt;single-sign-on-credential /&gt;&lt;/f5-vpn-conf&gt;. Consulte la documentación de VPN de cada fabricante para obtener más información sobre cómo escribir comandos XML personalizados.
**Lista de búsqueda de sufijos DNS** (solo Windows Phone 8.1)|Especifique un sufijo DNS en cada línea. Al conectarse a un sitio web mediante un nombre corto, se buscará cada sufijo DNS que especifique. Por ejemplo, especifique los sufijos DNS **domain1.contoso.com** y **domain2.contoso.com**, visite la dirección URL **http://mywebsite** y se buscarán las direcciones URL **http://mywebsite.domain1.contoso.com** y **http://mywebsite.domain2.contoso.com**.
**Omitir VPN cuando se está conectado a una red Wi-Fi de la empresa** (solo Windows Phone 8.1)|Seleccione esta opción para especificar que la conexión VPN no se usará cuando el dispositivo esté conectado a la red Wi-Fi de la empresa.
**Omitir VPN cuando se está conectado a una red Wi-Fi doméstica** (solo Windows Phone 8.1)|Seleccione esta opción para especificar que la conexión VPN no se usará cuando el dispositivo esté conectado a una red Wi-Fi doméstica.

Los siguientes valores adicionales están disponibles para dispositivos que ejecutan Windows 10 Escritorio y Mobile.

Nombre de la configuración  |Más información  
---------|---------
**Reglas de tráfico de red**|Seleccione qué protocolos, puertos locales y remotos e intervalos de direcciones se habilitarán para la conexión VPN. Si no se crea ninguna regla de tráfico de red, se habilitan todos los protocolos, puertos e intervalos de direcciones. Una vez creada una regla, la conexión VPN solo usará los protocolos, puertos e intervalos de direcciones que especifique en esa regla.
**Rutas**|Seleccione qué rutas usarán la conexión VPN.
**Servidores DNS**| Seleccione qué servidores DNS usará la conexión VPN una vez establecida.         
**Aplicaciones asociadas**|Proporcione una lista de las aplicaciones que usarán automáticamente la conexión VPN. El tipo de aplicación determinará el identificador de la aplicación. Para una aplicación universal, proporcione el nombre de familia de paquete. Para una aplicación de escritorio, proporcione la ruta del archivo de la aplicación.          


> [!IMPORTANT]
> Se recomienda que proteja todas las listas de aplicaciones que se compilan para su uso en la configuración de VPN por aplicación. Si un usuario no autorizado modifica la lista y usted la importa en la lista de aplicaciones de VPN por aplicación, podría autorizar el acceso a VPN a aplicaciones que no deberían tener acceso. Una forma de proteger las listas de aplicaciones consiste en usar una lista de control de acceso (ACL).

A continuación se incluye un ejemplo de cuándo se puede usar la configuración de los límites corporativos. Si quiere habilitar VPN solo para Escritorio remoto, cree una regla de tráfico de red que permita el tráfico para el protocolo 27 en el puerto externo 3996. Ningún otro tráfico usará la VPN.

Definir las rutas en los límites de la empresa es útil cuando el tipo de conexión VPN no permite definir cómo se controla el tráfico de túnel dividido. En ese caso, use **Rutas** para enumerar las rutas que usarán la conexión VPN.

Puede restringir el uso de VPN de dispositivos Windows 10 a aplicaciones específicas mediante la creación de una configuración personalizada de OMA-URI.

La nueva directiva aparece en el nodo **Directivas de configuración** del área de trabajo **Directiva**.

### VPN a petición para dispositivos iOS
Puede configurar VPN a petición para dispositivos iOS 8.0 y versiones posteriores.

> [!NOTE]
>  
> No puede usar VPN por aplicación y VPN a petición en la misma directiva.
 
1. En la página de configuración de directivas, busque **Reglas a petición para esta conexión VPN**. Las columnas tienen las etiquetas **Coincidencia** (la condición que comprueban las reglas) y **Acción** (la acción que desencadenará la directiva cuando se cumpla la condición). 
2. Elija **Agregar** para crear una regla. Hay dos tipos de coincidencias que puede configurar en la regla. Solo se puede configurar uno de estos tipos por regla.
  - **SSID**, que hacen referencia a redes inalámbricas. 
  - **Dominios de búsqueda DNS**, que son...  Puede usar nombres de dominio completo como *team. corp.contoso.com* o dominios como *contoso.com*, que equivale a usar * *.contoso.com*.
3. Opcional: proporcione un sondeo de cadena de dirección URL, que es una dirección URL que la regla usa como prueba. Si el dispositivo en el que está instalado este perfil tiene acceso a esta dirección URL sin redireccionamiento, se establecerá la VPN y el dispositivo se conectará a la dirección URL de destino. El usuario no verá el sitio de sondeo de cadena de dirección URL. Un ejemplo de un sondeo de cadena de dirección URL es la dirección de un servidor web de auditoría que comprueba el cumplimiento del dispositivo antes de conectarse a la VPN. Otra posibilidad es que la dirección URL pruebe la capacidad de la VPN para conectarse a un sitio antes de conectar el dispositivo a la dirección URL de destino a través de la VPN.
4. Elija una de las acciones siguientes:
  - **Conectar**
  - **Evaluar conexión**, que tiene tres opciones de configuración. a. **Acción del dominio**: elija **Conectarse si es necesario** o **No conectarse nunca**
    . b. **Lista de dominios separados por comas**: configure esta opción solo si elige la **Acción del dominio** **Conectarse si es necesario** 
    . c. **Sondeo de cadena de dirección URL requerida**: dirección URL HTTP o HTTPS (opción preferida), como *https://vpntestprobe.contoso.com*. La regla comprueba si hay respuesta de esta dirección. Si no la hay y la **Acción del dominio** es **Conectarse si es necesario**, se activará la VPN.
     > [!TIP]
     >
     >Por ejemplo, puede usar esta acción cuando algunos sitios de la red corporativa requieren una conexión de red corporativa directa o de VPN, pero otros no. Si incluye en la **Lista de dominios de búsqueda de DNS separados por comas** *corp.contoso.com*, puede elegir **Conectarse si es necesario** y, después, mostrar sitios específicos dentro de esa red que pueden requerir una VPN, como *sharepoint.corp.contoso.com*. Después, la regla comprobará si se puede obtener acceso a *vpntestprobe.contoso.com*. Si no se puede, se activará la VPN para el sitio de SharePoint.
  - **Omitir**: esto no produce ningún cambio en la conectividad de VPN. Si la VPN está conectada, déjela conectada. Si no está conectada, no la conecte. Por ejemplo, tiene una regla que se conecta a la VPN para todos los sitios web corporativos internos, pero quiere que uno de esos sitios internos solo sea accesible cuando el dispositivo esté realmente conectado a la red corporativa. En ese caso, puede crear una regla Omitir para ese sitio en concreto.
  - **Desconectar**: los dispositivos se desconectan de la VPN cuando se cumplen las condiciones. Por ejemplo, puede enumerar las redes inalámbricas corporativas en el campo **SSID** y crear una regla que desconecte los dispositivos de la VPN cuando se conecten a una de esas redes.

Las reglas específicas del dominio se evalúan antes que las reglas de todos los dominios. 


## Implementar la directiva

1.  En el área de trabajo **Directiva**, seleccione la directiva que quiera implementar y, después, elija **Administrar implementación**.

2.  En el cuadro de diálogo **Administrar implementación**:

    -   Para implementar la directiva, seleccione uno o más grupos en los que quiera implementar la directiva y elija **Agregar** &gt; **Aceptar**.

    -   Para cerrar el cuadro de diálogo sin implementarla, haga clic en **Cancelar**.


Tras una implementación correcta, los usuarios verán el nombre de la conexión VPN especificado en la lista de conexiones VPN en su dispositivo.

En la página **General** del área de trabajo **Directiva**, un resumen de estado y las alertas identifican los problemas de la directiva que requieren su atención. Además, aparece un resumen de estado en el área de trabajo Panel.

### Consulte también
[Configuraciones personalizadas para perfiles de VPN](Custom-configurations-for-VPN-profiles.md)

[VPN por aplicación para Pulse Secure en Android](per-app-vpn-for-android-pulse-secure.md)



<!--HONumber=Sep16_HO1-->


