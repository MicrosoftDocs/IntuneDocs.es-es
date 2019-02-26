---
title: 'Usar certificados SCEP con Microsoft Intune: Azure | Microsoft Docs'
description: Para usar certificados SCEP en Microsoft Intune, configure el dominio de AD local, cree una entidad de certificación, configure el servidor NDES e instale Intune Certificate Connector. Luego cree un perfil de certificado SCEP y asígnelo a grupos. Vea también los distintos identificadores de evento y sus descripciones, así como los códigos de diagnóstico para el servicio de conector de Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cdc0f02aa09edd05314d0d4a6a2abacc98c94bf2
ms.sourcegitcommit: e5f501b396cb8743a8a9dea33381a16caadc51a9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2019
ms.locfileid: "56742744"
---
# <a name="configure-and-use-scep-certificates-with-intune"></a>Configurar y usar certificados SCEP con Intune

En este artículo se muestra cómo configurar la estructura y, luego, crear y asignar perfiles de certificados de Protocolo de inscripción de certificados simple (SCEP) con Intune.

## <a name="configure-on-premises-infrastructure"></a>Configuración de la infraestructura local

- **Dominio de Active Directory**: Todos los servidores enumerados en esta sección (excepto el servidor proxy de aplicación web) deben estar unidos al dominio de Active Directory.

- **Entidad de certificación** (CA): debe ser una entidad de certificación (CA) empresarial de Microsoft que se ejecute en una edición Enterprise de Windows Server 2008 R2 o posterior. No se admiten CA independientes. Para detalles, consulte [Instalación de la entidad de certificación](http://technet.microsoft.com/library/jj125375.aspx).
    Si la CA ejecuta Windows Server 2008 R2, se debe [instalar la revisión de KB2483564](http://support.microsoft.com/kb/2483564/).

- **Servidor SCEP**: en Windows Server 2012 R2 o posterior, configure el rol de servidor Servicio de inscripción de dispositivos de red (SCEP). En Intune no se puede usar el Servicio de inscripción de dispositivos de red en un servidor que también ejecuta la entidad de certificación empresarial. Consulte [Orientación para el Servicio de inscripción de dispositivos de red](http://technet.microsoft.com/library/hh831498.aspx) para obtener instrucciones sobre cómo configurar Windows Server 2012 R2 para hospedar NDES.
El servidor NDES debe estar unido a un dominio dentro del mismo bosque que la CA de empresa. Puede encontrar más información sobre cómo implementar el servidor NDES en un bosque independiente, una red aislada o un dominio interno en [Uso de un módulo de directivas con el servicio de inscripción de dispositivos de red](https://technet.microsoft.com/library/dn473016.aspx).

- **Microsoft Intune Certificate Connector**: descargue el instalador de **Certificate Connector** (**NDESConnectorSetup.exe**) en el portal de administración de Intune. Deberá ejecutar este instalador en el servidor con el rol NDES.  

  - El conector de certificado de NDES también admite el modo Estándar federal de procesamiento de información (FIPS). FIPS no es necesario, pero puede emitir y revocar certificados cuando está habilitado.

- **Servidor proxy de aplicación web** (opcional): use un servidor con Windows Server 2012 R2 o posterior como servidor proxy de aplicación web (WAP). Esta configuración:
  - Permite a los dispositivos recibir certificados mediante una conexión a Internet.
  - Es una recomendación de seguridad cuando los dispositivos se conectan a través de Internet para recibir y renovar certificados.
  
- **Azure AD Application Proxy** (opcional): Azure AD Application Proxy se puede usar en lugar de un servidor proxy de aplicación web (WAP) dedicado para publicar el servidor SCEP en Internet. Para más información, consulte [Provisión de acceso remoto seguro a aplicaciones locales](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).

#### <a name="additional"></a>Adicional

- El servidor que hospeda WAP [debe instalar una actualización](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) que habilite la compatibilidad con las direcciones URL largas que usa el Servicio de inscripción de dispositivos de red. Esta actualización está incluida en el [paquete acumulativo de actualizaciones de diciembre de 2014](http://support.microsoft.com/kb/3013769)o está disponible por separado, en [KB3011135](http://support.microsoft.com/kb/3011135).
- El servidor WAP debe tener un certificado SSL que coincida con el nombre que se publica para los clientes externos, así como confiar en el certificado SSL que se usa en el servidor NDES. Estos certificados habilitan al servidor WAP para terminar la conexión SSL entre clientes y crear una nueva conexión SSL hacia el servidor NDES.

Para más información, consulte [Planeamiento de certificados para WAP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates) e [Información general sobre los servidores WAP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11)).

### <a name="network-requirements"></a>Requisitos de red

Si no usa ningún proxy inverso (por ejemplo, WAP o el proxy de aplicación de Azure AD), deberá permitir el tráfico TCP en el puerto 443 desde todos los hosts o direcciones IP de Internet al servidor NDES.

Permita todos los puertos y protocolos necesarios entre el servidor NDES y cualquier infraestructura de soporte. Por ejemplo, el servidor NDES necesita comunicarse con la entidad de certificación, los servidores DNS, los servidores de Configuration Manager, los controladores de dominio y posiblemente con otros servicios de su entorno.

Se recomienda encarecidamente publicar el servidor NDES a través de un proxy inverso, como el [proxy de aplicación de Azure AD](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/), [el proxy de acceso web](https://technet.microsoft.com/library/dn584107.aspx) o un proxy de terceros.

### <a name="certificates-and-templates"></a>Certificados y plantillas  

|Objeto|Detalles|
|----------|-----------|
|**Plantilla de certificado**|Configure esta plantilla en la CA emisora.|
|**Certificado de autenticación del cliente**|Solicitado desde la CA emisora o la CA pública; instale este certificado en el servidor NDES.|
|**Certificado de autenticación de servidor**|Solicitado desde la CA emisora o la CA pública, este certificado SSL se instala y se enlaza en IIS, en el servidor NDES. Si el certificado tiene el conjunto de usos de claves de autenticación de cliente y servidor (**Usos mejorados de clave**), puede usar el mismo certificado.|
|**Certificado de CA raíz de confianza**|Exportará este certificado como un archivo **.cer** desde la entidad de certificación raíz o cualquier dispositivo que confíe en ella. Luego, asígnelo a los usuarios o dispositivos que usan el perfil de certificado de CA de confianza, o bien a ambos.<br /><b>NOTA:<b /> al asignar un perfil de certificado SCEP, asegúrese de asignar el perfil de certificado raíz de confianza al que se hace referencia en el perfil de su certificado SCEP al mismo grupo de usuarios o dispositivos.<br /><br />Use un único certificado de CA raíz de confianza por cada plataforma de sistema operativo y asócielo a cada perfil de certificado raíz de confianza que cree.<br /><br />Puede usar certificados de CA raíz de confianza adicionales cuando sea necesario. Por ejemplo, podría hacerlo para proporcionar una relación de confianza con una CA que firme los certificados de autenticación de servidor para los puntos de acceso Wi-Fi.|

### <a name="accounts"></a>Cuentas

|Nombre|Detalles|
|--------|-----------|
|**Cuenta de servicio NDES**|Especifique una cuenta de usuario de dominio que vaya a usar como cuenta de servicio NDES. |

## <a name="configure-your-infrastructure"></a>Configurar la infraestructura
Para poder configurar perfiles de certificado, lleve a cabo los siguientes pasos. Estos pasos requieren conocimientos de Windows Server 2012 R2 o versiones posteriores y de Servicios de certificados de Active Directory (ADCS):

#### <a name="step-1---create-an-ndes-service-account"></a>Paso 1: crear una cuenta de servicio NDES

Cree una cuenta de usuario de dominio que vaya a usar como cuenta de servicio NDES. Esta cuenta se especifica al configurar las plantillas en la CA emisora antes de instalar y configurar NDES. Asegúrese de que el usuario tenga los derechos predeterminados, los derechos **Iniciar sesión localmente**, **Iniciar sesión como un servicio** e **Iniciar sesión como trabajo por lotes**. Algunas organizaciones tienen directivas de protección que deshabilitan estos derechos.

#### <a name="step-2---configure-certificate-templates-on-the-certification-authority"></a>Paso 2: configurar plantillas de certificado en la entidad de certificación
En este paso, hará lo siguiente:

- Configurar una plantilla de certificado para NDES
- Publicar la plantilla de certificado para NDES

##### <a name="configure-the-certification-authority"></a>Configurar la entidad de certificación

1. Inicie sesión como administrador de organización.

2. En la CA emisora, use el complemento Plantillas de certificado para crear una nueva plantilla personalizada. O bien, copie una plantilla existente y luego actualícela (por ejemplo, la plantilla Usuario) para usarla con NDES.

   >[!NOTE]
   > La plantilla de certificado NDES debe basarse en una plantilla de certificado v2 (con compatibilidad con Windows 2003).

   La plantilla debe tener las siguientes configuraciones:

   - En **General**:
   
       - Confirme que la propiedad **Publicar certificado en Active Directory** **no** está activada.
       - Especifique un **Nombre para mostrar de plantilla** descriptivo para la plantilla.

   - En **Nombre del firmante**, seleccione **Proporcionado por el solicitante**. (La seguridad la aplica el módulo de directivas de Intune para NDES).

   - En **Extensiones**, confirme que **Descripción de las directivas de aplicación** incluya **Autenticación del cliente**.

     > [!IMPORTANT]
     > En el caso de plantillas de certificado de iOS y macOS, en la pestaña **Extensiones**, edite **Uso de claves** y confirme que **Firma como prueba de origen** no esté seleccionado.

   - En **Seguridad**, agregue la cuenta de servicio NDES y otórguele permisos de **inscripción**en la plantilla. Los administradores de Intune que crean perfiles SCEP necesitan derechos de **lectura** para poder ir a la plantilla al crear los perfiles SCEP.

     > [!NOTE]
     > Para revocar certificados, la cuenta de servicio NDES necesita derechos para *emitir y administrar certificados* referentes a cada plantilla de certificado que use un perfil de certificado.

3. Revise la configuración de **Período de validez** en la pestaña **General** de la plantilla. Intune usa de forma predeterminada el valor configurado en la plantilla. No obstante, puede configurar la entidad de certificación para permitir que el solicitante especifique otro valor, lo que se puede establecer desde la consola de administrador de Intune. Si quiere usar siempre el valor de la plantilla, omita el resto de este paso.

   > [!IMPORTANT]
   > iOS y macOS siempre usa el valor establecido en la plantilla con independencia de otras configuraciones que realice.

Configuración de plantilla de ejemplo:

![Plantilla, pestaña Administración de solicitudes](./media/scep_ndes_request_handling.png)

![Plantilla, pestaña Nombre del sujeto](./media/scep_ndes_subject_name.jpg)

![Plantilla, pestaña Seguridad](./media/scep_ndes_security.jpg)

![Plantilla, pestaña Extensiones](./media/scep_ndes_extensions.jpg)

![Plantilla, pestaña Requisitos de emisión](./media/scep_ndes_issuance_reqs.jpg)

> [!IMPORTANT]
> En el caso de directivas de aplicación, agregue únicamente las directivas de aplicación necesarias. Confirme las elecciones con los administradores de seguridad.

Configure la CA para permitir que el solicitante especifique el período de validez:

1. En la entidad de certificación, ejecute los comandos siguientes:
   - **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**
   - **net stop certsvc**
   - **net start certsvc**

2. En la CA emisora, use el complemento Entidad de certificación para publicar la plantilla de certificado.
   Seleccione el nodo **Plantillas de certificado**, haga clic en **Acción** > **Nueva** > **Plantilla de certificado que se va a emitir** y seleccione la plantilla que creó en el paso 2.

3. Valide que la plantilla se publicó visualizándola en la carpeta **Plantillas de certificado** .

#### <a name="step-3---configure-prerequisites-on-the-ndes-server"></a>Paso 3: configurar los requisitos previos en el servidor NDES
En este paso, hará lo siguiente:

- Agregar NDES a un servidor con Windows Server y configurar IIS para que admita NDES
- Agregar la cuenta de servicio NDES al grupo IIS_IUSRS
- Establecer el nombre de entidad de seguridad de servicio (SPN) para la cuenta de servicio de NDES

1. En el servidor en el que se hospeda NDES, inicie sesión como **Administrador de organización** y, luego, use el [Asistente para agregar roles y características](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11)) para instalar NDES:

   1. En el asistente, seleccione **Servicios de certificados de Active Directory** para obtener acceso a los servicios de rol de AD CS. Seleccione el **Servicio de inscripción de dispositivos de red**, desactive **Entidad de certificación**y complete el asistente.

      > [!TIP]
      > En **Progreso de la instalación**, no marque **Cerrar**. En su lugar, seleccione el vínculo **Configurar Servicios de certificados de Active Directory en el servidor de destino**. Se abre el asistente para **Configuración de AD CS**, que se usa en el siguiente paso. Una vez abierta la configuración de AD CS, puede cerrar al Asistente para agregar roles y características.

   2. Cuando NDES se agrega al servidor, el asistente instala también IIS. Confirme que IIS tenga la siguiente configuración:

       - **Servidor web** > **Seguridad** > **Filtrado de solicitudes**

       - **Servidor web** > **Desarrollo de aplicaciones** > **ASP.NET 3.5** 

            Al instalar ASP.NET 3.5 se instala .NET Framework 3.5. Al instalar .NET Framework 3.5, se instala tanto la característica básica **.NET Framework 3.5** como la característica **Activación HTTP**.

       - **Servidor web** > **Desarrollo de aplicaciones** > **ASP.NET 4.5** 

            Al instalar ASP.NET 4.5 se instala .NET Framework 4.5. Al instalar .NET Framework 4.5, se instalan la característica básica **.NET Framework 4.5**, la característica **ASP.NET 4.5** y la característica **Servicios WCF** > **Activación HTTP**.

       - **Herramientas de administración** > **Compatibilidad con la administración de IIS 6** > **Compatibilidad con la metabase de IIS 6**

       - **Herramientas de administración** > **Compatibilidad con la administración de IIS 6** > **Compatibilidad con WMI de IIS 6**

       - En el servidor, agregue la cuenta de servicio NDES como miembro del grupo local **IIS_IUSR**.

2. En un símbolo del sistema con privilegios elevados, ejecute el siguiente comando para establecer el SPN de la cuenta de servicio SCEP:

    `setspn -s http/<DNS name of NDES Server> <Domain name>\<NDES Service account name>`

    Por ejemplo, si el servidor NDES se denomina **Server01**, su dominio es **Contoso.com**y la cuenta de servicio es **NDESService**, use:

    `setspn –s http/Server01.contoso.com contoso\NDESService`

#### <a name="step-4---configure-ndes-for-use-with-intune"></a>Paso 4: configurar NDES para su uso con Intune
En este paso, hará lo siguiente:

- Configurar NDES para su uso con la CA emisora
- Enlazar el certificado de autenticación (SSL) de servidor en IIS
- Configurar el filtrado de solicitudes en IIS

1. En el servidor NDES, abra el asistente para Configuración de AD CS y realice las actualizaciones siguientes:

    > [!TIP]
    > Si hizo clic en el vínculo del paso anterior, este asistente ya está abierto. De lo contrario, abra el Administrador del servidor para obtener acceso a la configuración posterior a la implementación de Servicios de certificados de Active Directory.

   - En **Servicios de rol**, seleccione el **Servicio de inscripción de dispositivos de red**.
   - En **Cuenta de servicio para NDES**, especifique la cuenta de servicio NDES.
   - En **CA para NDES**, haga clic en **Seleccionar** y seleccione la CA emisora en donde ha configurado la plantilla de certificado.
   - En **Criptografía para NDES**, establezca la longitud de clave que satisfaga los requisitos de la empresa.
   - En **Confirmación**, seleccione **Configurar** para completar el asistente.

2. Una vez finalizado el asistente, actualice la siguiente clave del Registro en el servidor NDES:

    `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`

    Para actualizar esta clave, identifique el **Propósito** de la plantilla de certificado (se encuentra en la pestaña **Administración de solicitudes**). Luego actualice la entrada correspondiente del Registro mediante la sustitución de los datos existentes por el nombre de la plantilla de certificado (no el nombre para mostrar de la plantilla) que ha especificado en el paso 2. La tabla siguiente asigna el propósito de la plantilla de certificado a los valores del registro:

    |Plantilla de certificado Propósito (en la pestaña Tratamiento de la solicitud)|Valor del registro que se va a editar|Valor que se ve en la consola de administración de Intune para el perfil de SCEP|
    |---|---|---|
    |Firma|SignatureTemplate|Firma digital|
    |Cifrado|EncryptionTemplate|Cifrado de clave|
    |Firma y cifrado|GeneralPurposeTemplate|Cifrado de clave<br/>Firma digital|

    Por ejemplo, si el propósito de la plantilla de certificado es **Cifrado**, edite el valor **EncryptionTemplate** para que sea el nombre de la plantilla de certificado.

3. El servidor NDES recibe direcciones URL (consultas) largas que requieren que se agreguen dos entradas del Registro:


   |                        Ubicación                        |      Valor      | Tipo  |      Datos       |
   |--------------------------------------------------------|-----------------|-------|-----------------|
   | HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters | MaxFieldLength  | DWORD | 65534 (decimal) |
   | HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters | MaxRequestBytes | DWORD | 65534 (decimal) |

4. En el Administrador de IIS, seleccione **Sitio web predeterminado** > **Filtrado de solicitudes** > **Modificar configuración de característica**. Cambie **Longitud máxima de dirección URL** y **Cadena de consulta máxima** a *65534*, como se muestra:

    ![Longitud de dirección URL y de consulta máximas de IIS](./media/SCEP_IIS_max_URL.png)

5. Reinicie el servidor. No use **iisreset**; no finaliza estos cambios.
6. Vaya a `http://*FQDN*/certsrv/mscep/mscep.dll`. Debe ver una página NDES similar a esta:

    ![Probar SCEP](./media/SCEP_NDES_URL.png)

    Si aparece **503 Servicio no disponible**, compruebe el Visor de eventos. Es probable que el grupo de aplicaciones se haya detenido debido a la falta de un derecho para el usuario SCEP. Esos derechos se describen en el paso 1.

##### <a name="install-and-bind-certificates-on-the-ndes-server"></a>Instalar y enlazar certificados en el servidor NDES

1. En el servidor NDES, solicite e instale un certificado de **autenticación de servidor** de la CA interna o de una CA pública. Después, este certificado SSL se enlaza en IIS.

    > [!TIP]
    > Después de enlazar el certificado SSL en IIS, instale un certificado de autenticación del cliente. Este certificado puede estar emitido por una CA de confianza para el servidor NDES. Se puede usar el mismo certificado si este tiene el conjunto de usos de claves de autenticación de cliente y servidor (**Usos mejorados de clave**). Revise los siguientes pasos para obtener información sobre estos certificados de autenticación.

   1. Después de obtener el certificado de autenticación de servidor, abra el **Administrador de IIS** y seleccione el **Sitio web predeterminado**. En el panel **Acciones**, seleccione **Enlaces**.

   2. Seleccione **Agregar**, configure **Tipo** como **https** y confirme que el puerto es **443**. Solo se admite el puerto 443 para Intune independiente.

   3. En **Certificado SSL**, especifique el certificado de autenticación de servidor.

      > [!NOTE]
      > Si el servidor NDES usa un nombre externo e interno para una única dirección de red, el certificado de autenticación de servidor debe tener:
      > - Un **nombre del firmante** con un nombre de servidor público externo
      > - Un **Nombre alternativo del firmante** que incluya el nombre del servidor interno

2. En el servidor NDES, solicite e instale un certificado de **autenticación del cliente** de la CA interna o de una entidad de certificación pública. Este certificado puede ser el mismo que el certificado de autenticación del servidor si dicho certificado tiene ambas funcionalidades.

    El certificado de autenticación del cliente debe tener las siguientes propiedades:

    - **Uso mejorado de clave**: este valor debe incluir **Autenticación del cliente**

    - **Nombre del firmante**: este valor debe ser igual al nombre DNS del servidor donde se instala el certificado (el servidor SCEP)

##### <a name="configure-iis-request-filtering"></a>Configurar el filtrado de solicitudes de IIS

1. En el servidor NDES, abra el **Administrador de IIS**, seleccione el **Sitio web predeterminado** en el panel **Conexiones** y abra **Filtrado de solicitudes**.

2. Seleccione **Modificar configuración de característica** y después configure los valores:

    - **Cadena de consulta (bytes)** = **65534**
    - **Longitud máxima de dirección URL (bytes)** = **65534**

3. Revise la siguiente clave del registro:

    `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`

    Confirme que los siguientes valores se establezcan como entradas DWORD:

    - Nombre: **MaxFieldLength**, con un valor decimal de **65534**
    - Nombre: **MaxRequestBytes**, con un valor decimal de **65534**

4. Reinicie el servidor de NDES. El servidor está ya preparado para admitir el conector certificado.

#### <a name="step-5---enable-install-and-configure-the-intune-certificate-connector"></a>Paso 5: habilitar, instalar y configurar Intune Certificate Connector
En este paso, hará lo siguiente:

- Habilitar la compatibilidad con SCEP en Intune.
- Descargue, instale y configure Certificate Connector en el servidor que hospede el rol Servicio de inscripción de dispositivos de red (NDES) de su entorno. Para aumentar la escala de la implementación de NDES en la organización, puede instalar varios servidores NDES con Microsoft Intune Certificate Connector en cada uno de ellos.

##### <a name="download-install-and-configure-the-certificate-connector"></a>Descargar, instalar y configurar Certificate Connector

> [!IMPORTANT] 
> Microsoft Intune Certificate Connector **debe** instalarse en un servidor Windows independiente. No se puede instalar en la entidad de certificación (CA) emisora. También se **debe** instalar en el mismo servidor que el rol de Servicio de inscripción de dispositivos de red (NDES).

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Configuración de dispositivos** > **Entidad de certificación** > **Agregar**.
3. Descargue y guarde el archivo del conector. Guárdelo en una ubicación accesible desde el servidor donde va a instalar el conector.

    ![ConnectorDownload](./media/certificates-download-connector.png)

4. Una vez finalizada la descarga, vaya al servidor que hospeda el rol Servicio de inscripción de dispositivos de red (NDES). Después:

    1. Asegúrese de que .NET Framework 4.5 esté instalado, tal como requiere el conector de certificado NDES. .NET framework 4.5 se incluye automáticamente con Windows Server 2012 R2 y las versiones más recientes.
    2. Ejecute el instalador (**NDESConnectorSetup.exe**). El instalador también instala el módulo de directivas para SCEP y el servicio web de CRP. El servicio web de CRP, CertificateRegistrationSvc, se ejecuta como una aplicación en IIS.

    > [!NOTE]
    > Cuando instala NDES para Intune independiente, el servicio de CRP se instala automáticamente con Certificate Connector. Al usar Intune con Configuration Manager, instale el punto de registro de certificados como un rol de sistema de sitio independiente.

5. Cuando se le solicite el certificado de cliente para el conector de certificado, haga clic en **Seleccionar** y seleccione el certificado de **autenticación del cliente** instalado en el servidor NDES en el paso 4.

    Después de seleccionar el certificado de autenticación del cliente, volverá a la superficie del **Certificado de cliente para el conector de certificado para Microsoft Intune** . Aunque no se muestra el certificado seleccionado, seleccione **Siguiente** para ver las propiedades de dicho certificado. Seleccione **Siguiente** y luego **Instalar**.

    > [!IMPORTANT]
    > La configuración de seguridad mejorada de Internet Explorer [debe estar deshabilitada en el servidor NDES](https://technet.microsoft.com/library/cc775800(v=WS.10).aspx) que hospeda Intune Certificate Connector.

6. Cuando se complete el asistente, pero antes de cerrarlo, haga clic en **Iniciar la UI del conector de certificado**.

    > [!TIP]
    > Si cierra al asistente antes de iniciar la IU del conector de certificado, puede volver a abrirlo ejecutando el comando siguiente:
    >
    > <install_Path>\NDESConnectorUI\NDESConnectorUI.exe

7. En la IU **Conector de certificado** :

    Seleccione **Iniciar sesión** y escriba sus credenciales de administrador de servicio de Intune o las credenciales de un administrador de inquilinos con permiso de administración global. Después de iniciar sesión, Intune Certificate Connector descargará un certificado de Intune. Este certificado sirve para la autenticación entre el conector e Intune.

    > [!IMPORTANT]
    > La cuenta de usuario debe tener una licencia válida de Intune asignada. Si la cuenta de usuario no tiene una licencia válida de Intune, NDESConnectorUI.exe produce un error.

    Si su organización usa un servidor proxy y el proxy es necesario para que el servidor NDES acceda a Internet, seleccione **Usar servidor proxy**. A continuación, escriba el nombre del servidor proxy, el puerto y las credenciales de cuenta para conectarse.

    Seleccione la pestaña **Avanzadas** y especifique las credenciales de una cuenta que tenga el permiso **Emitir y administrar certificados** en la entidad de certificación emisora. **Aplique** los cambios.

    Ahora puede cerrar la IU del conector de certificado.

8. Abra un símbolo del sistema, escriba **services.msc** y presione **Entrar**. Haga clic con el botón derecho en **Servicio del conector de Intune** >  y en **Reiniciar**.

Para validar que el servicio se ejecuta, abra un explorador y escriba la siguiente dirección URL. Debe devolver un error **403**:

`http://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`

> [!NOTE]
> Con el conector de certificado NDES se incluye la compatibilidad con TLS 1.2. Por tanto, si el servidor con el conector de certificado NDES instalado es compatible con TLS 1.2, entonces se usará TLS 1.2. Si el servidor no admite TLS 1.2, entonces se usará TLS 1.1. Actualmente, se usa TLS 1.1 para la autenticación entre los dispositivos y el servidor.

## <a name="create-a-scep-certificate-profile"></a>Creación de un perfil de certificado SCEP

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba un **Nombre** y una **Descripción** para el perfil de certificado SCEP.
4. En la lista desplegable **Plataforma**, seleccione la plataforma de dispositivo para este certificado SCEP. Actualmente puede seleccionar una de las siguientes plataformas para la configuración de restricciones de dispositivos:
   - **Android**
   - **Android Enterprise**
   - **iOS**
   - **macOS**
   - **Windows Phone 8.1**
   - **Windows 8.1 y versiones posteriores**
   - **Windows 10 y versiones posteriores**
5. En la lista desplegable de los **tipos de perfil**, seleccione **Certificado SCEP**.
6. Escriba los valores siguientes:

   - **Tipo de certificado**: elija **Usuario** para certificados de usuario. Elija **Dispositivo** para dispositivos sin usuario, como quioscos multimedia. Los certificados de **Dispositivo** están disponibles para estas plataformas:  
     - Android Enterprise
     - iOS
     - macOS
     - Windows 8.1 y posterior
     - Windows 10 y versiones posteriores


   - **Formato de nombre del sujeto**: seleccione cómo Intune crea automáticamente el nombre del sujeto en la solicitud de certificado. Las opciones cambian en función de si elige un tipo de certificado **Usuario** o un tipo de certificado **Dispositivo**. 

        **Tipo de certificado de usuario**  

        Puede incluir la dirección de correo electrónico del usuario en el nombre del firmante. Elija de entre las siguientes opciones:

        - **No configurado**.
        - **Nombre común**
        - **Nombre común, incluyendo la dirección de correo electrónico**
        - **Nombre común como correo electrónico**
        - **IMEI (Identidad de equipo móvil internacional)**
        - **Número de serie**
        - **Personalizado**: cuando se selecciona esta opción, se muestra también un cuadro de texto **Personalizado**. Use este campo para escribir un formato de nombre del firmante personalizado, incluidas las variables. El formato personalizado admite dos variables: **Nombre común (CN)** y **dirección de correo electrónico (E)**. **Nombre común (CN)** se puede establecer en cualquiera de las siguientes variables:

            - **CN={{UserName}}**: nombre principal de usuario, como janedoe@contoso.com
            - **CN={{AAD_Device_ID}}**: identificador asignado al registrar un dispositivo en Azure Active Directory (AD). Este identificador normalmente se usa para autenticarse en Azure AD.
            - **CN={{SERIALNUMBER}}**: número de serie (SN) único que normalmente usa el fabricante para identificar un dispositivo
            - **CN={{IMEINumber}}**: número exclusivo de identidad de equipo móvil internacional (IMEI) usado para identificar un teléfono móvil
            - **CN={{OnPrem_Distinguished_Name}}**: secuencia de nombres distintivos relativos separados por comas, como `CN=Jane Doe,OU=UserAccounts,DC=corp,DC=contoso,DC=com`

                Para usar la variable `{{OnPrem_Distinguished_Name}}`, asegúrese de sincronizar el atributo de usuario `onpremisesdistingishedname` mediante [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) con su instancia de Azure AD.

            - **CN={{onPremisesSamAccountName}}**: los administradores pueden sincronizar el atributo samAccountName de Active Directory con Azure AD mediante Azure AD Connect en un atributo llamado `onPremisesSamAccountName`. Intune puede sustituir esa variable como parte de una solicitud de emisión de certificado en el asunto de un certificado SCEP.  El atributo samAccountName es el nombre de inicio de sesión del usuario usado para admitir clientes y servidores de una versión anterior de Windows (anterior a Windows 2000). El formato del nombre de inicio de sesión del usuario es: `DomainName\testUser`, o solo `testUser`.

                Para usar la variable `{{onPremisesSamAccountName}}`, asegúrese de sincronizar el atributo de usuario `onPremisesSamAccountName` mediante [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) con su instancia de Azure AD.

            Mediante una combinación de una o muchas de estas variables y cadenas estáticas, puede crear un formato de nombre de firmante personalizado como este:  

            **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**

            En este ejemplo, se ha creado un formato de nombre de firmante que, además de las variables CN y E, usa cadenas para los valores Unidad organizativa, Organización, Ubicación, Estado y País. [CertStrToName](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) describe esta función y sus cadenas admitidas.

        **Tipo de certificado de dispositivo**  

        Cuando se usa el tipo de certificado **Dispositivo**, también puede usar estas variables de certificado de dispositivo para el valor:  

        ```
        "{{AAD_Device_ID}}",
        "{{Device_Serial}}",
        "{{Device_IMEI}}",
        "{{SerialNumber}}",
        "{{IMEINumber}}",
        "{{AzureADDeviceId}}",
        "{{WiFiMacAddress}}",
        "{{IMEI}}",
        "{{DeviceName}}",
        "{{FullyQualifiedDomainName}}",
        "{{MEID}}",
        ```

        Estas variables se pueden agregar con texto estático en un cuadro de texto de valor personalizado. Por ejemplo, se puede agregar el nombre común como `CN = {{DeviceName}}text`.

        > [!IMPORTANT]
        >  - En el texto estático del asunto, las llaves **{}** que no encierran una variable se resolverán en un error. 
        >  - Cuando use una variable de certificado de dispositivo, incluya la variable entre llaves **{ }**.
        >  - `{{FullyQualifiedDomainName}}` solo funciona para Windows y dispositivos unidos a dominios. 
        >  -  Al usar las propiedades del dispositivo como el IMEI, el número de serie y el nombre de dominio completo en el asunto o SAN para un certificado de dispositivo, tenga en cuenta que una persona con acceso al dispositivo podría suplantar estas propiedades.
        >  - El perfil no se instalará en el dispositivo si no se admiten las variables de dispositivo especificadas. Por ejemplo, si {{IMEI}} se usa en el nombre del sujeto del perfil SCEP asignado a un dispositivo que no tiene un número IMEI, la instalación del perfil no se completará con éxito. 


   - **Nombre alternativo del firmante**: especifique cómo Intune crea automáticamente los valores del nombre alternativo del sujeto (SAN) en la solicitud de certificado. Las opciones cambian en función de si elige un tipo de certificado **Usuario** o un tipo de certificado **Dispositivo**. 

        **Tipo de certificado de usuario**  

        Los siguientes atributos están disponibles:

        - Dirección de correo electrónico
        - Nombre principal de usuario (UPN)

            Por ejemplo, si selecciona un tipo de certificado de usuario, puede incluir el nombre principal de usuario (UPN) en el nombre alternativo del firmante. Si un certificado de cliente se usa para autenticar un servidor de directivas de redes, establezca el nombre alternativo del firmante en el UPN. 

        **Tipo de certificado de dispositivo**  

        Un cuadro de texto de formato de tabla que se puede personalizar. Los siguientes atributos están disponibles:

        - DNS

        Con el tipo de certificado **Dispositivo**, puede usar estas variables de certificado de dispositivo para el valor:  

        ```
        "{{AAD_Device_ID}}",
        "{{Device_Serial}}",
        "{{Device_IMEI}}",
        "{{SerialNumber}}",
        "{{IMEINumber}}",
        "{{AzureADDeviceId}}",
        "{{WiFiMacAddress}}",
        "{{IMEI}}",
        "{{DeviceName}}",
        "{{FullyQualifiedDomainName}}",
        "{{MEID}}",
        ```

        Estas variables se pueden agregar con texto estático en el cuadro de texto de valor personalizado. Por ejemplo, el atributo DNS puede agregarse como `DNS name = {{AzureADDeviceId}}.domain.com`.

        > [!IMPORTANT]
        >  - En el texto estático de SAN, no sirven las llaves **{ }**, los símbolos de barra vertical **|** y los signos de punto y coma **;**. 
        >  - Cuando use una variable de certificado de dispositivo, incluya la variable entre llaves **{ }**.
        >  - `{{FullyQualifiedDomainName}}` solo funciona para Windows y dispositivos unidos a dominios. 
        >  -  Al usar las propiedades del dispositivo como el IMEI, el número de serie y el nombre de dominio completo en el asunto o SAN para un certificado de dispositivo, tenga en cuenta que una persona con acceso al dispositivo podría suplantar estas propiedades.
        >  - El perfil no se instalará en el dispositivo si no se admiten las variables de dispositivo especificadas. Por ejemplo, si se usa {{IMEI}} en el nombre alternativo del firmante del perfil SCEP asignado a un dispositivo que no tiene un número IMEI, la instalación del perfil no se completará con éxito.  

   - **Período de validez del certificado**: si ejecutó el comando `certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE`, que permite un período de validez personalizado, en la CA emisora, puede especificar el tiempo restante hasta la expiración del certificado.<br>Puede especificar un valor inferior al período de validez de la plantilla de certificado, pero no uno superior. Por ejemplo, si el período de validez del certificado en la plantilla de certificado es de dos años, puede especificar un valor de un año, pero no un valor de cinco años. El valor también debe ser menor que el período de validez restante del certificado de la CA emisora. 
   - **Proveedor de almacenamiento de claves (KSP)** (Windows Phone 8.1, Windows 8.1, Windows 10): especifique dónde se almacena la clave del certificado. Elija uno de los siguientes valores:
     - **Inscribirse en KSP Módulo de plataforma segura (TPM) si está presente, si no en KSP Software**
     - **Inscribirse en KSP del Módulo de plataforma segura (TPM) o se producirá un error**
     - **Inscribirse en Passport o se producirá un error (Windows 10 y versiones posteriores)**
     - **Inscribirse en el KSP Software**

   - **Uso de la clave**: especifique las opciones de uso de claves del certificado. Las opciones son:
     - **Cifrado de clave**: permite el intercambio de claves solo si la clave está cifrada
     - **Firma digital**: permite el intercambio de claves solo si una firma digital protege la clave
   - **Tamaño de la clave (bits)**: seleccione el número de bits que contiene la clave
   - **Algoritmo hash** (Android, Windows Phone 8.1, Windows 8.1, Windows 10): Seleccione uno de los tipos de algoritmos hash disponibles para usar con este certificado. Seleccione el nivel máximo de seguridad que admiten los dispositivos de conexión.
   - **Certificado raíz**: elija un perfil de certificado de CA raíz que previamente haya configurado y asignado al usuario o dispositivo. Este certificado de CA debe ser el certificado raíz para la entidad de certificación que emite el certificado que va a configurar en este perfil de certificado. Asegúrese de asignar este perfil de certificado raíz de confianza al mismo grupo asignado en el perfil de certificado SCEP.
   - **Uso mejorado de clave**: elija **Agregar** para agregar valores para la finalidad prevista del certificado. En la mayoría de los casos, el certificado requiere **Autenticación de cliente** para que el usuario o dispositivo pueda autenticarse en un servidor. Sin embargo, puede agregar otros usos de clave según sea necesario.
   - **Configuración de la inscripción**
     - **Umbral de renovación (%)**: especifique qué porcentaje de la duración del certificado tiene que quedar para que el dispositivo solicite la renovación del certificado.
     - **Direcciones URL de servidor SCEP**: especifique una o varias direcciones URL para los servidores SCEP que emiten certificados mediante SCEP. Por ejemplo, escriba algo parecido a `https://ndes.contoso.com/certsrv/mscep/mscep.dll`.
     - Seleccione **Aceptar** y **Crear** el perfil.

Se creará el perfil y aparecerá en el panel con la lista de perfiles.

## <a name="assign-the-certificate-profile"></a>Asignar el perfil de certificado

Considere los siguiente aspectos antes de asignar perfiles de certificado a grupos:

- Cuando asigna perfiles de certificado a grupos, el archivo de certificado del perfil de certificado de CA de confianza se instala en el dispositivo. El dispositivo usa el perfil de certificado SCEP para crear una solicitud de certificado.
- Los perfiles de certificado solo se instalan en dispositivos que ejecutan la plataforma usada al crear el perfil.
- Puede asignar perfiles de certificado en recopilaciones de usuarios o en recopilaciones de dispositivos.
- Para publicar rápidamente un certificado en un dispositivo una vez inscrito el dispositivo, asigne el perfil de certificado en un grupo de usuarios (no en un grupo de dispositivos). Si lo asigna en un grupo de dispositivos, deberá efectuar un registro completo del dispositivo para que el dispositivo reciba directivas.
- Aunque asigne cada perfil por separado, también deberá asignar la CA raíz de confianza y el perfil SCEP o PKCS. De lo contrario, se produce un error en la directiva del certificado SCEP o PKCS.

    > [!NOTE]
    > En iOS, si implementa varios perfiles de recursos que usen el mismo perfil de certificado, es posible que vea varias copias del certificado en el perfil de administración.

Para obtener más información sobre cómo asignar perfiles, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).

## <a name="intune-connector-setup-verification-and-troubleshooting"></a>Comprobación del programa de instalación del conector de Intune y solución de problemas

Para solucionar problemas y comprobar la instalación del conector de Intune, vea [Certificate Authority script samples](https://aka.ms/intuneconnectorverificationscript) (Ejemplos de scripts de la entidad de certificación)

## <a name="intune-connector-events-and-diagnostic-codes"></a>Eventos de conector de Intune y códigos de diagnóstico

A partir de la versión 6.1806.x.x, el servicio de conector de Intune registra los eventos en el **Visor de eventos** (**Registros de aplicaciones y servicios** > **Conector de Microsoft Intune**). Con estos eventos podrá resolver posibles problemas en la configuración del conector de Intune. Estos eventos registran las operaciones que se realizan con éxito y con error, y también contienen códigos de diagnóstico con mensajes para ayudar a los administradores de TI a solucionar problemas.

### <a name="event-ids-and-descriptions"></a>Identificadores de evento y descripciones

> [!NOTE]
> Para más información sobre los códigos de diagnóstico relacionados para cada evento, use la tabla **Códigos de diagnóstico** (en este artículo).

| Id. de evento      | Nombre del evento    | Descripción del evento | Códigos de diagnóstico relacionados |
| ------------- | ------------- | -------------     | -------------            |
| 10010 | StartedConnectorService  | Se inició el servicio de conector | 0x00000000, 0x0FFFFFFF |
| 10020 | StoppedConnectorService  | Se detuvo el servicio de conector | 0x00000000, 0x0FFFFFFF |
| 10100 | CertificateRenewal_Success  | Se renovó correctamente el certificado de inscripción del conector | 0x00000000, 0x0FFFFFFF |
| 10102 | CertificateRenewal_Failure  | No se pudo renovar el certificado de inscripción del conector. Reinstale el conector. | 0x00000000, 0x00000405, 0x0FFFFFFF |
| 10302 | RetrieveCertificate_Error  | No se pudo recuperar el certificado de inscripción del conector del Registro. Revise los detalles del evento para la huella digital del certificado relacionado con este evento. | 0x00000000, 0x00000404, 0x0FFFFFFF |
| 10301 | RetrieveCertificate_Warning  | Compruebe la información de diagnóstico en los detalles del evento. | 0x00000000, 0x00000403, 0x0FFFFFFF |
| 20100 | PkcsCertIssue_Success  | Se emitió correctamente un certificado PKCS. Revise los detalles del evento relacionados con el identificador de dispositivo, el identificador de usuario, el nombre de entidad de certificación, el nombre de plantilla de certificado y la huella digital del certificado. | 0x00000000, 0x0FFFFFFF |
| 20102 | PkcsCertIssue_Failure  | No se pudo emitir un certificado PKCS. Revise los detalles del evento relacionados con el identificador de dispositivo, el identificador de usuario, el nombre de entidad de certificación, el nombre de plantilla de certificado y la huella digital del certificado. | 0x00000000, 0x00000400, 0x00000401, 0x0FFFFFFF |
| 20200 | RevokeCert_Success  | El certificado se revocó correctamente. Revise los detalles del evento relacionados con el identificador de dispositivo, el identificador de usuario, el nombre de entidad de certificación y el número de serie del certificado. | 0x00000000, 0x0FFFFFFF |
| 20202 | RevokeCert_Failure | No se pudo revocar el certificado. Revise los detalles del evento relacionados con el identificador de dispositivo, el identificador de usuario, el nombre de entidad de certificación y el número de serie del certificado. Para más información, vea los registros de SVC del Servicio de inscripción de dispositivos de red.   | 0x00000000, 0x00000402, 0x0FFFFFFF |
| 20300 | Upload_Success | Se cargaron correctamente los datos de revocación o de solicitud del certificado. Revise los detalles del evento para obtener los detalles de carga. | 0x00000000, 0x0FFFFFFF |
| 20302 | Upload_Failure | No se pudieron cargar los datos de revocación o de solicitud del certificado. Revise los detalles del evento y el estado de carga para determinar el momento del error.| 0x00000000, 0x0FFFFFFF |
| 20400 | Download_Success | Se descargó correctamente la solicitud para firmar un certificado, descargar un certificado de cliente o revocar un certificado. Revise los detalles del evento para obtener los detalles de descarga.  | 0x00000000, 0x0FFFFFFF |
| 20402 | Download_Failure | No se pudo descargar la solicitud para firmar un certificado, descargar un certificado de cliente o revocar un certificado. Revise los detalles del evento para obtener los detalles de descarga. | 0x00000000, 0x0FFFFFFF |
| 20500 | CRPVerifyMetric_Success  | El punto de registro de certificados comprobó correctamente un desafío de cliente | 0x00000000, 0x0FFFFFFF |
| 20501 | CRPVerifyMetric_Warning  | El punto de registro de certificados se completó pero se rechazó la solicitud. Vea el código de diagnóstico y el mensaje para más detalles. | 0x00000000, 0x00000411, 0x0FFFFFFF |
| 20502 | CRPVerifyMetric_Failure  | El punto de registro de certificados no pudo comprobar un desafío de cliente. Vea el código de diagnóstico y el mensaje para más detalles. Vea los detalles del mensaje del evento para el identificador de dispositivo correspondiente al desafío. | 0x00000000, 0x00000408, 0x00000409, 0x00000410, 0x0FFFFFFF |
| 20600 | CRPNotifyMetric_Success  | El punto de registro de certificados terminó correctamente el proceso de notificación y ha enviado el certificado al dispositivo cliente. | 0x00000000, 0x0FFFFFFF |
| 20602 | CRPNotifyMetric_Failure  | El punto de registro de certificados no pudo finalizar el proceso de notificación. Vea los detalles del mensaje del evento para más información sobre la solicitud. Compruebe la conexión entre el servidor del Servicio de inscripción de dispositivos de red y la entidad de certificación. | 0x00000000, 0x0FFFFFFF |

### <a name="diagnostic-codes"></a>Códigos de diagnóstico

| Código de diagnóstico | Nombre de diagnóstico | Mensaje de diagnóstico |
| -------------   | -------------   | -------------      |
| 0x00000000 | Correcto  | Correcto |
| 0x00000400 | PKCS_Issue_CA_Unavailable  | La entidad de certificación no es válida o no está disponible. Compruebe que la entidad de certificación está disponible y que el servidor puede comunicarse con él. |
| 0x00000401 | Symantec_ClientAuthCertNotFound  | No se encontró el certificado de autenticación de cliente de Symantec en el almacén de certificados local. Vea el artículo [Instalación del certificado de autorización de registro de Symantec](https://docs.microsoft.com/intune/certificates-symantec-configure#install-the-symantec-registration-authorization-certificate) para más información.  |
| 0x00000402 | RevokeCert_AccessDenied  | La cuenta especificada no tiene permisos para revocar un certificado de una entidad de certificación. Vea el campo Nombre de CA en los detalles del mensaje del evento para determinar la entidad de certificación emisora.  |
| 0x00000403 | CertThumbprint_NotFound  | No se pudo encontrar un certificado que coincida con los datos especificados. Inscriba el conector de certificado e inténtelo de nuevo. |
| 0x00000404 | Certificate_NotFound  | No se pudo encontrar un certificado que coincida con la entrada proporcionada. Vuelva a inscribir el conector de certificado e inténtelo de nuevo. |
| 0x00000405 | Certificate_Expired  | Certificado expirado. Vuelva a inscribir el conector de certificado para renovar el certificado e inténtelo de nuevo. |
| 0x00000408 | CRPSCEPCert_NotFound  | No se encontró el certificado de cifrado de CRP. Compruebe que el Servicio de inscripción de dispositivos de red y el conector de Intune están configurados correctamente. |
| 0x00000409 | CRPSCEPSigningCert_NotFound  | No se pudo recuperar el certificado de firma. Compruebe que el servicio de conector de Intune está configurado correctamente y que se está ejecutando. Compruebe también que los eventos de descarga del certificado se realizaron correctamente. |
| 0x00000410 | CRPSCEPDeserialize_Failed  | No se pudo deserializar la solicitud para el desafío de SCEP. Compruebe que el Servicio de inscripción de dispositivos de red y el conector de Intune están configurados correctamente. |
| 0x00000411 | CRPSCEPChallenge_Expired  | Solicitud denegada debido a que expiró el desafío de certificado. El dispositivo cliente puede reintentar obtener un nuevo desafío desde el servidor de administración. |
| 0x0FFFFFFFF | Unknown_Error  | No se puede completar la solicitud porque se produjo un error del lado servidor. Inténtelo de nuevo. |

## <a name="next-steps"></a>Pasos siguientes

- [Uso de certificados PKCS](certficates-pfx-configure.md) o [Emitir certificados PKCS desde un servicio web de administración de PKI de Symantec](certificates-symantec-configure.md).
- [Adición de entidades de certificación de terceros en Intune mediante SCEP](certificate-authority-add-scep-overview.md).
- Para obtener más ayuda, use la guía [Solucionar problemas de implementación de perfil de certificado SCEP en Microsoft Intune](https://support.microsoft.com/help/4457481/troubleshooting-scep-certificate-profile-deployment-in-intune).
