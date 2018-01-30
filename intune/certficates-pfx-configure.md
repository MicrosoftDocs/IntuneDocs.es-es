---
title: "Configuración y administración de certificados PKCS con Intune"
titleSuffix: Intune on Azure
description: Cree y asigne certificados PKCS con Intune."
keywords: 
author: MicrosoftGuyJFlo
ms.author: joflore
manager: dougeby
ms.date: 12/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d877a1de8e66372d36641dd863a517fecf176d69
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="configure-and-manage-pkcs-certificates-with-intune"></a>Configuración y administración de certificados PKCS con Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="requirements"></a>Requisitos

Para usar los certificados PKCS con Intune, debe tener la infraestructura siguiente:

* Un dominio existente de Active Directory Domain Services (AD DS) configurado.
 
  Si necesita más información sobre cómo instalar y configurar AD DS, consulte el artículo [Planeación y diseño de AD DS](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

* Una entidad de certificación (CA) empresarial existente configurada.

  Si necesita más información sobre cómo instalar y configurar los Servicios de certificados de Active Directory (AD CS), consulte el artículo con la [guía paso a paso de Servicios de certificados de Active Directory](https://technet.microsoft.com/library/cc772393).

  > [!WARNING]
  > Intune requiere ejecutar AD CS con una entidad de certificación (CA) empresarial, no una CA independiente.

* Un cliente que tenga conectividad a la CA empresarial.
* Una copia exportada del certificado raíz desde la CA empresarial.
* Microsoft Intune Certificate Connector (NDESConnectorSetup.exe) descargado del portal de Intune.
* Una instancia de Windows Server disponible para hospedar Microsoft Intune Certificate Connector (NDESConnectorSetup.exe).

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Exportación del certificado raíz desde la CA empresarial

Necesita un certificado de entidad de certificación raíz o intermedio en cada dispositivo para autenticación con VPN, WiFi y otros recursos. Los pasos siguientes explican cómo obtener el certificado requerido desde la CA empresarial.

1. Inicie sesión en la CA empresarial con una cuenta que tenga privilegios administrativos.
2. Abra un símbolo del sistema como administrador.
3. Exporte el certificado de CA raíz en una ubicación a la que pueda acceder más adelante.

   Por ejemplo:

4.  Cuando se complete el asistente, pero antes de cerrarlo, haga clic en **Iniciar la UI del conector de certificado**.

   `certutil -ca.cert certnew.cer`

   Para más información, consulte las [tareas CertUtil para administrar los certificados](https://technet.microsoft.com/library/cc772898.aspx#BKMK_ret_sign).

## <a name="configure-certificate-templates-on-the-certification-authority"></a>Configuración de plantillas de certificado en la entidad de certificación

1. Inicie sesión en la CA empresarial con una cuenta que tenga privilegios administrativos.
2. Abra la consola de **entidad de certificación**.
3. Haga clic con el botón secundario en **Plantillas de certificado** y elija **Administrar**.
4. Ubique la plantilla de certificado **Usuario**, haga doble clic en ella y elija **Duplicar plantilla**. Se abre la ventana **Propiedades de la plantilla nueva**.
5. En la pestaña **Compatibilidad**
   * Establezca **Entidad de certificación** en **Windows Server 2008 R2**
   * Establezca **Destinatario del certificado** en **Windows 7 / Server 2008 R2**
6. En la pestaña **General** :
   * Establezca el **nombre para mostrar de la plantilla** en un nombre significativo para usted.

   > [!WARNING]
   > El **nombre de la plantilla** predeterminado es el mismo que el **nombre para mostrar de la plantilla** *sin espacios*. Anote el nombre de la plantilla para usarlo más adelante.

7. En la pestaña **Administración de solicitudes**, active la casilla **Permitir que la clave privada se pueda exportar**.
8. En la pestaña **Criptografía**, confirme que el **tamaño mínimo de la clave** esté establecido en 2048.
9. En la pestaña **Nombre del firmante**, elija el botón de radio **Proporcionar en la solicitud**.
10. En la pestaña **Extensiones**, confirme que ve Sistema de cifrado de archivos, Proteger correo electrónico y Autenticación de cliente en las **Directivas de aplicación**.
    
      > [!IMPORTANT]
      > En el caso de plantillas de certificado de iOS y macOS, en la pestaña **Extensiones**, edite **Uso de claves** y asegúrese de que la opción **Firma como prueba de origen** no esté seleccionada.

11. En la pestaña **Seguridad**, agregue la cuenta de equipo para el servidor donde instala Microsoft Intune Certificate Connector.
    * Permita que esta cuenta tenga los permisos **Lectura** e **Inscripción**.
12. Haga clic en **Aplicar** y, luego, haga clic en **Aceptar** para guardar la plantilla de certificado.
13. Cierre la **Consola de plantillas de certificado**.
14. En la consola de la **entidad de certificación**, haga clic con el botón secundario en **Plantillas de certificado**, **Nuevo**, **Plantilla de certificado que se va a emitir**.
    * Elija la plantilla que creó en los pasos anteriores y haga clic en **Aceptar**.
15. Para que el servidor administre los certificados en nombre de los usuarios y dispositivos inscritos en Intune, siga estos pasos:

    a. Haga clic con el botón secundario en la entidad de certificación y elija **Propiedades**.

    b. En la pestaña Seguridad, agregue la cuenta de equipo del servidor donde ejecuta Microsoft Intune Certificate Connector.
      * Conceda los permisos **Emitir y administrar certificados** y **Solicitar certificados** a la cuenta de equipo.
16. Cierre sesión en la CA empresarial.

## <a name="download-install-and-configure-the-microsoft-intune-certificate-connector"></a>Descarga, instalación y configuración de Microsoft Intune Certificate Connector

![ConnectorDownload][ConnectorDownload]

1. En Azure Portal, seleccione **Más servicios** > **Supervisión y administración** > **Intune**.
2. En la hoja **Intune**, seleccione **Configuración del dispositivo**. 
3. En la hoja **Configuración del dispositivo**, seleccione **Entidad de certificación**. 
4. Haga clic en **Agregar** y seleccione **Descargue el archivo del conector**. Guarde la descarga en una ubicación a la que pueda acceder desde el servidor donde vaya a realizar la instalación. 
5.  Inicie sesión en el servidor donde instalará Microsoft Intune Certificate Connector.
6.  Ejecute el instalador y acepte la ubicación predeterminada. Instala el conector en C:\Archivos de programa\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe.
    1. En la página Opciones del instalador, elija **Distribución .PFX** y haga clic en **Siguiente**.
    2. Haga clic en **Instalar** y espere que se complete la instalación.
    3. En la página Finalización, active la casilla denominada **Iniciar el conector de Intune** y haga clic en **Finalizar**.
7.  La ventana del conector NDES ahora debería abrirse en la pestaña **Inscripción**. Para habilitar la conexión con Intune, haga clic en **Iniciar sesión** y proporcione una cuenta con permisos administrativos.
8.  En la pestaña **Avanzadas**, puede dejar seleccionado el botón de radio **Usar la cuenta SYSTEM de este equipo (predeterminado)**.
9.  Haga clic en **Aplicar** y, luego, en **Cerrar**.
10. Ahora vuelva a Azure Portal. Pasados unos minutos, debería ver una marca de verificación verde y la palabra **Activo** en **Estado de la conexión**, en **Intune** > **Configuración del dispositivo** > **Entidad de certificación**. Esta confirmación permite saber que el servidor del conector se puede comunicar con Intune.


## <a name="create-a-device-configuration-profile"></a>Creación de un perfil de configuración de dispositivo

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Navegue a **Intune**, **Configuración de dispositivos**, **Perfiles** y haga clic en **Crear perfil**.

   ![NavigateIntune][NavigateIntune]

3. Rellene la información siguiente:
   * **Nombre** del perfil
   * Si lo desea, establezca una descripción
   * **Plataforma** en la cual implementar el perfil
   * Establezca el **tipo del perfil** en **Certificado de confianza**
4. Navegue a **Configuración** y proporcione el certificado de entidad de certificación raíz del archivo .cer que exportó anteriormente.

   > [!NOTE]
   > En función de la plataforma que eligió en el **paso 3**, es posible que tenga o no la opción de elegir el **almacén de destino** del certificado.

   ![ProfileSettings][ProfileSettings]

5. Haga clic en **Aceptar** y, luego, en **Crear** para guardar el perfil.
6. Para asignar el perfil nuevo a uno o varios dispositivos, consulte [Asignación de perfiles de dispositivo de Microsoft Intune](device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Creación de un perfil de certificado PKCS

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Navegue a **Intune**, **Configuración de dispositivos**, **Perfiles** y haga clic en **Crear perfil**.
3. Rellene la información siguiente:
   * **Nombre** del perfil
   * Si lo desea, establezca una descripción
   * **Plataforma** en la cual implementar el perfil
   * Establezca el **tipo del perfil** en **Certificado PKCS**
4. Navegue a **Configuración** y proporcione la información siguiente:
   * **Umbral de renovación (%)**: el valor recomendado es 20 %.
   * **Período de validez del certificado**: si no cambió la plantilla de certificado, esta opción debe estar establecida en un año.
   * **Entidad de certificación**: este opción es el nombre de dominio completo (FQDN) interno de la CA empresarial.
   * **Nombre de la entidad de certificación**: esta opción es el nombre de la CA empresarial y puede ser distinto del elemento anterior.
   * **Nombre de plantilla de certificado**: esta opción es el nombre de la plantilla se creó anteriormente. Recuerde que el **nombre de la plantilla** predeterminado es el mismo que el **nombre para mostrar de la plantilla** *sin espacios*.
   * **Formato de nombre del firmante**: establezca esta opción en **Nombre común**, a menos que se requiera de otro modo.
   * **Nombre alternativo del firmante**: establezca esta opción en **Nombre principal de usuario (UPN)**, a menos que se requiera de otro modo.
   * **Uso mejorado de clave**: siempre que haya usado la configuración predeterminada en el paso 10 de la sección anterior, **Configuración de plantillas de certificado en la entidad de certificación**, agregue los **valores predefinidos** siguientes del cuadro de selección:
      * **Cualquier propósito**
      * **Autenticación de cliente**
      * **Proteger correo electrónico**
   * **Certificado raíz**: (para perfiles Android) esta opción es el archivo .cer que se exportó en el paso 3 de la sección anterior [Exportación del certificado raíz desde la CA empresarial](#export-the-root-certificate-from-the-enterprise-ca).

5. Haga clic en **Aceptar** y, luego, en **Crear** para guardar el perfil.
6. Para asignar el perfil nuevo a uno o varios dispositivos, consulte el artículo [Asignación de perfiles de dispositivo de Microsoft Intune](device-profile-assign.md).


[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "Navegue a Intune en Azure Portal y cree un perfil nuevo de un certificado de confianza"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "Cree un perfil y cargue un certificado de confianza"
[ConnectorDownload]: ./media/certificates-download-connector.png "Descargue Certificate Connector desde Azure Portal"  
