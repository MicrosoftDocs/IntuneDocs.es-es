---
title: Configurar VPN por aplicación para dispositivos iOS en Microsoft Intune - Azure | Microsoft Docs
description: Vea los requisitos previos, cree un grupo para los usuarios de la red privada virtual (VPN), agregue un perfil de certificado SCEP, configure un perfil de VPN por aplicación y asigne algunas aplicaciones al perfil de VPN en Microsoft Intune en dispositivos iOS. También se indican los pasos necesarios para comprobar la conexión VPN en el dispositivo.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: D9958CBF-34BF-41C2-A86C-28F832F87C94
ms.reviewer: karanda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 12131fe0b78814850cfadee15533620dd5813f6c
ms.sourcegitcommit: e9ba1280b95565a5c5674b825881655d0303e688
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2019
ms.locfileid: "54297407"
---
# <a name="set-up-per-app-virtual-private-network-vpn-in-intune-for-ios-devices"></a>Configuración de la red privada virtual (VPN) por aplicación en Intune para dispositivos iOS

Puede especificar las aplicaciones administradas que pueden usar su red privada virtual (VPN) en dispositivos iOS administrados por Intune. Al crear una VPN por aplicación en Intune, los usuarios finales podrán conectarse automáticamente mediante la VPN para acceder a documentos corporativos.

VPN por aplicación está actualmente disponible para los siguientes proveedores:

 - Checkpoint Remote Access VPN
 - Cisco AnyConnect
 - Citrix
 - F5
 - Pulse Connect Secure
 - Palo Alto Networks
 - SonicWall
 - Zscaler Private Access

## <a name="prerequisites-for-per-app-vpn"></a>Requisitos previos de VPN por aplicación

> [!IMPORTANT]
> Su proveedor de VPN puede tener otros requisitos específicos para la VPN por aplicación, como hardware o licencias específicos. Asegúrese de comprobar su documentación y cumplir los requisitos previos antes de configurar la VPN por aplicación en Intune.

Con el objetivo de demostrar su identidad, el servidor VPN presenta el certificado pertinente, el cual debe aceptarse sin ningún aviso del dispositivo. Para garantizar la aprobación automática del certificado, cree un perfil de certificado de confianza que contenga el certificado raíz del servidor VPN emitido por la entidad de certificación (CA). 

Exporte el certificado y agregue la entidad de certificación.

1. Abra la consola de administración en el servidor VPN.
2. Compruebe que el servidor VPN use una autenticación basada en certificado. 
3. Exporte el archivo del certificado raíz de confianza. Este presenta la extensión .cer, y puede agregarlo a la hora de crear un perfil de certificado de confianza.
4. Agregue el nombre de la entidad de certificación que ha emitido el certificado para la autenticación en el servidor VPN.
    Si la entidad de certificación que ha presentado el dispositivo coincide con alguna de las que figuran en la lista de entidades de certificación de confianza del servidor VPN, dicho servidor VPN autenticará el dispositivo correctamente.

## <a name="create-a-group-for-your-vpn-users"></a>Creación de un grupo para los usuarios de la VPN

Cree o elija un grupo existente en Azure Active Directory (Azure AD) para incluir los miembros que tengan acceso a la VPN por aplicación.

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Elija **Grupos** y haga clic en **Nuevo grupo**.
3. Seleccione un **Tipo de grupo** para el grupo. 
3. Escriba el **Nombre de grupo** del grupo. 
4. Escriba la **Descripción de grupo** del grupo. 
5. Para la opción **Tipo de pertenencia**, seleccione **Asignada**.
7. En el panel **Miembros** puede buscar los usuarios de la VPN por nombre o correo electrónico.
8. Seleccione cada usuario y haga clic en **Seleccionar**.
9. Haga clic en **Crear**.

## <a name="create-a-trusted-certificate-profile"></a>Creación de un perfil de certificado de confianza

Importe el certificado raíz del servidor VPN emitido por la entidad de certificación en un perfil creado en Intune. El perfil de certificado de confianza indicará al dispositivo iOS que puede confiar automáticamente en la entidad de certificación del servidor VPN.

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Elija **Configuración del dispositivo** y haga clic en **Perfiles**.
3. Haga clic en **Crear perfil**. En **Crear perfil**:
    1. Escriba el **nombre**.
    2. Escriba la **descripción**.
    3. Para la opción **Plataforma**, seleccione **iOS**.
    4. Para la opción **Tipo de perfil**, seleccione **Certificado de confianza**.
4. Haga clic en el icono de carpeta y localice el certificado VPN (archivo .cer) que ha exportado de la consola de administración de la VPN. Haga clic en **Aceptar**.
5. Haga clic en **Crear**.

    ![Creación de un perfil de certificado de confianza](./media/vpn-per-app-create-trusted-cert.png)

## <a name="create-a-scep-certificate-profile"></a>Creación de un perfil de certificado SCEP

El perfil de certificado raíz de confianza permite al dispositivo iOS confiar de forma automática en el servidor VPN. El certificado SCEP proporciona las credenciales del cliente VPN de iOS para el servidor VPN. El certificado permite al dispositivo realizar la autenticación de forma silenciosa, sin solicitar al usuario del dispositivo iOS un nombre de usuario ni la contraseña. 

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Elija **Configuración del dispositivo** y haga clic en **Perfiles**.
3. Haga clic en **Crear perfil**. En **Crear perfil**:
    1. Escriba el **nombre**.
    2. Escriba la **descripción**.
    3. Para la opción **Plataforma**, seleccione **iOS**.
    4. Para la opción **Tipo de perfil**, seleccione **Certificado SCEP**.
4. En **Período de validez del certificado**, seleccione **Años** y escriba `2`.
5. Para la opción **Formato de nombre del sujeto**, seleccione **Nombre común**.
6. Para **Nombre alternativo del sujeto**, seleccione **Nombre principal del usuario (UPN)**.
7. Para la opción **Uso de la clave**, seleccione **Firma digital** y **Cifrado de clave**.
8. Para **Tamaño de la clave (bits)**, seleccione **2048**.
9. Haga clic en Certificado raíz y seleccione un certificado SCEP. Haga clic en **Aceptar**.
10. Para **Uso mejorado de clave**, escriba `Client Authentication` en **Nombre**.
11. En **Identificador de objeto**, escriba `1.3.6.1.5.5.7.3.2`.
12. Haga clic en **Agregar**.
13. Escriba la ***URL del servidor*** y haga clic en **Agregar**.
14. Haga clic en **Aceptar**.
15. Haga clic en **Crear**.

    ![Creación de un perfil de certificado SCEP](./media/vpn-per-app-create-scep-cert.png)

## <a name="create-a-per-app-vpn-profile"></a>Creación de un perfil de VPN por aplicación

El perfil de VPN contiene el certificado SCEP con las credenciales del cliente, la información de la conexión a la VPN y la marca de VPN por aplicación para habilitar dicha característica y que la aplicación iOS la pueda usar.

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Elija **Configuración del dispositivo** y haga clic en **Perfiles**.
3. Haga clic en **Crear perfil**. En **Crear perfil**:
    1. Escriba el **nombre**.
    2. Escriba la **descripción**.
    3. Para la opción **Plataforma**, seleccione **iOS**.
    4. Para **Tipo de perfil**, seleccione **VPN**.
4. Seleccione **VPN base**. En **VPN base**:
    1. Escriba el **nombre de la conexión**.
    2. Escriba la **dirección IP o el FQDN**.
    3. Para la opción **Método de autenticación**, seleccione **Certificados**.
    4. Seleccione el certificado SCEP en **Certificado de autenticación** y haga clic en **Aceptar**.
    5. Para **Tipo de conexión**, seleccione su VPN.
    6. Si es necesario, configure los atributos correspondientes a su VPN.
    7. Seleccione **Deshabilitar tunelización dividida**.
5. Haga clic en **VPN automática**. En **VPN automática**:
    1. Para **Tipo de VPN automática**, seleccione **VPN por aplicación**.
    2. Escriba la dirección URL de la VPN y haga clic en **Agregar**.
    3. Haga clic en **Aceptar**.
6. Haga clic en **Aceptar**.
7. Haga clic en **Crear**.

    ![Creación de un perfil de VPN por aplicación](./media/vpn-per-app-create-vpn-profile.png)


## <a name="associate-an-app-with-the-vpn-profile"></a>Asociación de una aplicación al perfil de VPN

Tras agregar el perfil de VPN, asocie la aplicación y el grupo de Azure AD al perfil.

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Elija **Aplicaciones cliente**.
4. Haga clic en **Aplicaciones**.
5. Seleccione la aplicación de la lista.
6. Haga clic en **Asignaciones**.
7. Haga clic en **Agregar grupo**.
8. Seleccione **Obligatorio** para el **Tipo de asignación** en el panel **Agregar grupo**.
9. Seleccione el grupo definido anteriormente y seleccione la opción **Hacer que esta aplicación sea obligatoria**.
10. Para **VPN**, seleccione la definición de su VPN.
 
    > [!NOTE]  
    > A veces, la definición de la VPN puede tardar hasta un minuto en recuperar el valor. Espere entre tres y cinco minutos antes de hacer clic en **Guardar**.

11. Haga clic en **Aceptar** y en **Guardar**.

    ![Asociación de una aplicación a la VPN](./media/vpn-per-app-app-to-vpn.png)

Una asociación entre una aplicación y un perfil se quitará durante la próxima comprobación de dispositivos cuando se den las condiciones siguientes:
- La aplicación se diseñó con la intención de instalación requerida.
- El perfil y la aplicación se destinan al mismo grupo.
- Quita la configuración de VPN por aplicación de la asignación de la aplicación.

Una asociación entre una aplicación y un perfil seguirá existiendo hasta que el usuario final solicite una reinstalación desde el portal de empresa cuando se den las condiciones siguientes:
- La aplicación se diseñó con la intención de instalación disponible.
- El perfil y la aplicación se destinan al mismo grupo.
- El usuario final solicitó la instalación de la aplicación desde el portal de empresa, lo que da como resultado que la aplicación y el perfil se instalen en el dispositivo.
- Quite o cambie la configuración de VPN por aplicación de la asignación de la aplicación.

## <a name="verify-the-connection-on-the-ios-device"></a>Comprobación de la conexión en el dispositivo iOS

Una vez que la VPN por aplicación esté configurada y asociada a su aplicación, compruebe que la conexión funcione desde un dispositivo.

### <a name="before-you-attempt-to-connect"></a>Antes de probar la conexión

 - Asegúrese de que se está ejecutando iOS 9 o una versión posterior.
 - Asegúrese de implementar *todas* las directivas mencionadas anteriormente en el mismo grupo de usuarios. Si no lo hace, la experiencia de la VPN por aplicación se verá interrumpida.  
 - Asegúrese de tener instalada la aplicación VPN de terceros compatible. Se admiten las siguientes aplicaciones VPN:
    - Check Point Capsule Connect
    - Cisco AnyConnect
    - Citrix VPN
    - SSO de Citrix
    - F5 Access
    - Palo Alto Networks GlobalProtect
    - Pulse Secure
    - SonicWall Mobile Connect
    - Zscaler

    > [!NOTE]
    > Si utiliza la aplicación Pulse Secure VPN, puede elegir la tunelización de la capa de aplicaciones o de la capa de paquetes. Establezca el valor **ProviderType** en **app-proxy** para la tunelización de la capa de aplicaciones o **packet-tunnel** para la tunelización de la capa de paquetes.

### <a name="connect-using-the-per-app-vpn"></a>Conexión mediante la VPN por aplicación

Conéctese sin seleccionar la VPN ni escribir las credenciales para comprobar la experiencia sin intervención por parte del usuario. Por "experiencia sin intervención por parte del usuario" se entiende lo siguiente:

 - El dispositivo no solicita que confíe en el servidor VPN. Es decir, no verá el cuadro de diálogo **Confianza dinámica**.
 - No es necesario escribir las credenciales.
 - La conexión con la VPN se establece tras tocar el botón de conexión.

Compruebe la conexión en un dispositivo iOS.

1. Toque la aplicación VPN.
2. Toque el **botón para conectarse**.  
La VPN se conecta correctamente sin mostrar ningún otro aviso.

<!-- ## Troubleshooting the per-app VPN

The user experiences the feature by silently connecting to the VPN. This experience, however, can provide little information for troubleshooting. You can review the event logs crated by the iOS device.

`Note -- use the Apple Configurator as the supported tool. Only runs on a mac.'

To review event logs:

1. Connect your iOS device to a PC
2. Open the **iPhone Configuration Utility** (IPCU). If you do not have a copy, you can install it from [CompatCenter](http://www.microsoft.com/en-us/windows/compatibility/CompatCenter/ProductDetailsViewer?Name=iPhone%20Configuration%20Utility&vendor=Apple&Locale=1033%2C2057%2C3081%2C4105%2C16393&ModelOrVersion=3&BreadCrumbPath=iphone%20configuration%20utility&LastSearchTerm=iphone%2Bconfiguration%2Butility&Type=Software&tempOsid=Windows%208.1)
3. Review the logs. -->

## <a name="next-steps"></a>Pasos siguientes

- Para revisar la configuración de iOS, consulte [Configuración de VPN para dispositivos iOS en Microsoft Intune](vpn-settings-ios.md).
-  Para obtener más información sobre la configuración de VPN y Intune, consulte [Configuración de VPN en Microsoft Intune](vpn-settings-configure.md).
