---
title: 'Uso de certificados PKCS con Microsoft Intune: Azure | Microsoft Docs'
description: Agregue o cree certificados de Public Key Cryptography Standards con Microsoft Intune, incluidos los pasos para exportar un certificado raíz, configurar la plantilla de certificado, descargar e instalar Microsoft Intune Certificate Connector, crear un perfil de configuración de dispositivo, crear un perfil de certificado PKCS en Azure y la entidad de certificación
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 61a190be2b4685030438988dab0d0134a8fa9f9b
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31836194"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Configuración y uso de certificados PKCS con Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Los certificados se usan para autenticar y proteger el acceso a los recursos corporativos, por ejemplo, una VPN o la red Wi-Fi. En este artículo, se muestra cómo exportar un certificado PKCS y, después, agregarlo a un perfil de Intune. 

## <a name="requirements"></a>Requisitos

Para usar los certificados PKCS con Intune, asegúrese de que tiene la infraestructura siguiente:

* Un dominio existente de Active Directory Domain Services (AD DS) configurado.
 
  Para obtener más información sobre cómo instalar y configurar AD DS, consulte [Planeación y diseño de AD DS](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

* Una entidad de certificación (CA) empresarial existente configurada.

  Para obtener más información sobre cómo instalar y configurar los Servicios de certificados de Active Directory (AD CS), consulte [Active Directory Certificate Services Step-by-Step Guide](https://technet.microsoft.com/library/cc772393) (Guía detallada de los Servicios de certificados de Active Directory).

  > [!WARNING]
  > Intune requiere ejecutar AD CS con una entidad de certificación (CA) empresarial, no una CA independiente.

* Un cliente que tenga conectividad a la CA empresarial.
* Una copia exportada del certificado raíz desde la CA empresarial.
* Microsoft Intune Certificate Connector (NDESConnectorSetup.exe) descargado del portal de Intune.
* Se trata de una instancia de Windows Server para hospedar Microsoft Intune Certificate Connector (NDESConnectorSetup.exe).

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Exportación del certificado raíz desde la CA empresarial

Para autenticarse con VPN, Wi-Fi y otros recursos, necesita un certificado de entidad de certificación raíz o intermedio en cada dispositivo. Los pasos siguientes explican cómo obtener el certificado requerido desde la CA empresarial.

1. Inicie sesión en la entidad de certificación empresarial con una cuenta que tenga privilegios de administración.
2. Abra un símbolo del sistema como administrador.
3. Exporte el certificado de la entidad de certificación raíz (.cer) en una ubicación a la que pueda acceder más adelante.

   Por ejemplo:

4. Cuando se complete el asistente, pero antes de cerrarlo, haga clic en **Iniciar la UI del conector de certificado**.

   `certutil -ca.cert certnew.cer`

   Para más información, consulte las [tareas CertUtil para administrar los certificados](https://technet.microsoft.com/library/cc772898.aspx#BKMK_ret_sign).

## <a name="configure-certificate-templates-on-the-certification-authority"></a>Configuración de plantillas de certificado en la entidad de certificación

1. Inicie sesión en la entidad de certificación empresarial con una cuenta que tenga privilegios de administración.
2. En la consola de la **entidad de certificación**, haga clic con el botón derecho en **Plantillas de certificado** y seleccione **Administrar**.
3. Busque la plantilla de certificado **Usuario**, haga clic con el botón derecho en ella y elija **Duplicar plantilla**. Se abre **Propiedades de plantilla nueva**.
4. En la pestaña **Compatibilidad**: 
   * Establezca **Entidad de certificación** en **Windows Server 2008 R2**
   * Establezca **Destinatario del certificado** en **Windows 7 / Server 2008 R2**
5. En la pestaña **General** :
   * Establezca el **nombre para mostrar de la plantilla** en un nombre significativo para usted.

   > [!WARNING]
   > El **nombre de la plantilla** predeterminado es el mismo que el **nombre para mostrar de la plantilla** *sin espacios*. Apunte el nombre de la plantilla, lo necesitará más adelante.

6. En **Tratamiento de la solicitud**, seleccione **Permitir que la clave privada se pueda exportar**.
7. En **Criptografía**, confirme que el **Tamaño mínimo de clave** esté establecido en 2048.
8. En **Nombre del firmante**, elija **Proporcionado por el solicitante**.
9. En **Extensiones**, confirme que ve Sistema de cifrado de archivos, Correo seguro y Autenticación de cliente en las **Directivas de aplicación**.
    
      > [!IMPORTANT]
      > En el caso de plantillas de certificado de iOS, vaya a la pestaña **Extensiones**, actualice **Uso de la clave** y confirme que no está seleccionada la opción **Firma como prueba de origen**.

10. En **Seguridad**, agregue la cuenta de equipo para el servidor donde instala Microsoft Intune Certificate Connector.
    * Permita que esta cuenta tenga los permisos **Lectura** e **Inscripción**.
11. Seleccione **Aplicar** y, luego, **Aceptar** para guardar la plantilla de certificado.
12. Cierre la **Consola de plantillas de certificado**.
13. En la consola de la **entidad de certificación**, haga clic con el botón secundario en **Plantillas de certificado**, **Nuevo**, **Plantilla de certificado que se va a emitir**.
    * Elija la plantilla que ha creado en los pasos anteriores y seleccione **Aceptar**.
14. Para que el servidor administre los certificados en nombre de los usuarios y dispositivos inscritos en Intune, siga estos pasos:

    a. Haga clic con el botón secundario en la entidad de certificación y elija **Propiedades**.

    b. En la pestaña Seguridad, agregue la cuenta de equipo del servidor donde ejecuta Microsoft Intune Certificate Connector.
      * Conceda los permisos **Emitir y administrar certificados** y **Solicitar certificados** a la cuenta de equipo.
15. Cierre la sesión de la entidad de certificación empresarial.

## <a name="download-install-and-configure-the-microsoft-intune-certificate-connector"></a>Descarga, instalación y configuración de Microsoft Intune Certificate Connector

![ConnectorDownload][ConnectorDownload]

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios** y filtre por **Intune**. Seleccione **Microsoft Intune** y, luego, **Configuración del dispositivo**. 
2. Seleccione **Entidad de certificación**, **Agregar** y, después, **Descargue el archivo del conector**. Guarde la descarga en una ubicación a la que pueda acceder desde el servidor donde se instalará. 
3. Inicie sesión en este servidor y ejecute el instalador: 

    1. Acepte la ubicación predeterminada. Se instala el conector en `\Program Files\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe`.
    2. En Opciones del instalador, seleccione **Distribución PFX** y **Siguiente**.
    3. Seleccione **Instalar** y espere a que se complete la instalación.
    4. Cuando se complete, marque **Iniciar el conector de Intune** y, después, seleccione **Finalizar**.

4. Se debería abrir la ventana Conector NDES en la pestaña **Inscripción**. Para habilitar la conexión con Intune, seleccione **Iniciar sesión** y escriba una cuenta con permisos administrativos globales.
5. En la pestaña **Avanzadas**, deje seleccionado **Usar la cuenta SYSTEM de este equipo (predeterminado)**.
6. Haga clic en **Aplicar** y después en **Cerrar**.
7. Vuelva a Azure Portal (**Intune** > **Configuración del dispositivo** > **Entidad de certificación**). Después de unos minutos, se muestra una marca de verificación verde y el **Estado de la conexión** es **Activo**. Ahora, el servidor del conector puede comunicarse con Intune.

## <a name="create-a-device-configuration-profile"></a>Creación de un perfil de configuración de dispositivo

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Vaya a **Intune**, **Configuración de dispositivos**, **Perfiles** y seleccione **Crear perfil**.

   ![NavigateIntune][NavigateIntune]

3. Introduzca las siguientes propiedades:
   * **Nombre** del perfil
   * Si lo desea, establezca una descripción
   * **Plataforma** en la cual implementar el perfil
   * Establezca el **tipo del perfil** en **Certificado de confianza**

4. Vaya a **Configuración** y escriba el certificado de entidad de certificación raíz del archivo .cer que ha exportado anteriormente.

   > [!NOTE]
   > En función de la plataforma que ha elegido en el **paso 3**, es posible que tenga o no la opción de seleccionar el **Almacén de destino** del certificado.

   ![ProfileSettings][ProfileSettings]

5. Seleccione **Aceptar** y, luego, **Crear** para guardar el perfil.
6. Para asignar el perfil nuevo a uno o varios dispositivos, consulte [Asignación de perfiles de dispositivo en Microsoft Intune](device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Creación de un perfil de certificado PKCS

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Vaya a **Intune**, **Configuración de dispositivos**, **Perfiles** y seleccione **Crear perfil**.
3. Introduzca las siguientes propiedades:
   * **Nombre** del perfil
   * Si lo desea, establezca una descripción
   * **Plataforma** en la cual implementar el perfil
   * Establezca el **tipo del perfil** en **Certificado PKCS**
4. Vaya a **Configuración** y escriba las siguientes propiedades:
   * **Umbral de renovación (%)**: el valor recomendado es 20 %.
   * **Período de validez del certificado**: si no ha cambiado la plantilla de certificado, esta opción debe estar establecida en un año.
   * **Entidad de certificación**: muestra el nombre de dominio completo (FQDN) interno de la entidad de certificación empresarial.
   * **Nombre de entidad de certificación**: muestra el nombre de la entidad de certificación empresarial y puede ser distinto del elemento anterior.
   * **Nombre de plantilla de certificado**: el nombre de la plantilla que ha creado anteriormente. Recuerde que el **nombre de la plantilla** predeterminado es el mismo que el **nombre para mostrar de la plantilla** *sin espacios*.
   * **Formato de nombre del firmante**: establezca esta opción en **Nombre común**, a menos que se requiera de otro modo.
   * **Nombre alternativo del firmante**: establezca esta opción en **Nombre principal de usuario (UPN)**, a menos que se requiera de otro modo.
   * **Uso mejorado de clave**: siempre que haya usado la configuración predeterminada en el paso 10, la sección [Configuración de plantillas de certificado en la entidad de certificación](#configure-certificate-templates-on-the-certification-authority) (en este artículo), agregue los **Valores predefinidos** siguientes de la selección:
      * **Cualquier propósito**
      * **Autenticación de cliente**
      * **Proteger correo electrónico**
   * **Certificado raíz**: (para perfiles Android) muestra el archivo .cer que se ha exportado en el paso 3 de la sección [Exportación del certificado raíz desde la CA empresarial](#export-the-root-certificate-from-the-enterprise-ca) (en este artículo).

5. Seleccione **Aceptar** y, luego, **Crear** para guardar el perfil.
6. Para asignar el perfil nuevo a uno o varios dispositivos, consulte el artículo [Asignación de perfiles de dispositivo de Microsoft Intune](device-profile-assign.md).


[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "Navegue a Intune en Azure Portal y cree un perfil nuevo de un certificado de confianza"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "Cree un perfil y cargue un certificado de confianza"
[ConnectorDownload]: ./media/certificates-download-connector.png "Descargue Certificate Connector desde Azure Portal"  
