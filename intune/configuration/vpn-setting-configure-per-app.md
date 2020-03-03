---
title: 'Configuración de VPN por aplicación para dispositivos iOS/iPadOS en Microsoft Intune: Azure | Microsoft Docs'
description: Vea los requisitos previos, cree un grupo para los usuarios de la red privada virtual (VPN), agregue un perfil de certificado SCEP, configure un perfil de VPN por aplicación y asigne algunas aplicaciones al perfil de VPN en Microsoft Intune en dispositivos iOS/iPadOS. También se indican los pasos necesarios para comprobar la conexión VPN en el dispositivo.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: D9958CBF-34BF-41C2-A86C-28F832F87C94
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fd53172a1086f48dc1646e1b8a63de8bec37b934
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512609"
---
# <a name="set-up-per-app-virtual-private-network-vpn-for-iosipados-devices-in-intune"></a>Configuración de la red privada virtual (VPN) por aplicación para dispositivos iOS/iPadOS en Intune

En Microsoft Intune, puede crear y usar redes privadas virtuales (VPN) asignadas a una aplicación. Esta característica se denomina "VPN por aplicación". Debe elegir las aplicaciones administradas que pueden usar su VPN en dispositivos administrados por Intune. Al usar una VPN por aplicación, los usuarios finales se conectan de forma automática a través de la VPN y obtienen acceso a recursos de la organización, como los documentos.

Esta característica se aplica a:

- iOS 9 y versiones más recientes
- IPadOS 13.0 y versiones más recientes

Compruebe la documentación de su proveedor de VPN para ver si su VPN admite la VPN por aplicación.

En este artículo se muestra cómo crear un perfil de VPN por aplicación y asignar este perfil a sus aplicaciones. Siga estos pasos para crear una experiencia de VPN por aplicación perfecta para los usuarios finales. En el caso de la mayoría de las VPN que admiten la VPN por aplicación, el usuario abre una aplicación y se conecta automáticamente a la VPN.

Algunas VPN permiten la autenticación de nombre de usuario y contraseña con la VPN por aplicación. Es decir, los usuarios tienen que escribir un nombre de usuario y una contraseña para conectarse a la VPN.

> [!IMPORTANT]
> La VPN por aplicación no es compatible con los perfiles de VPN de IKEv2 para iOS/iPadOS.

## <a name="per-app-vpn-with-zscaler"></a>VPN por aplicación con Zscaler

Zscaler Private Access (ZPA) se integra con Azure Active Directory (Azure AD) para la autenticación. Al usar ZPA, no necesita los perfiles de [certificado de confianza](#create-a-trusted-certificate-profile) ni de [certificado SCEP o PKCS](#create-a-scep-or-pkcs-certificate-profile) (que se describen en este artículo). Si tiene un perfil de VPN por aplicación configurado para Zscaler, al abrir una de las aplicaciones asociadas no se conecta automáticamente a ZPA. En su lugar, el usuario tiene que iniciar sesión primero en la aplicación de Zscaler. Después, el acceso remoto se limita a las aplicaciones asociadas.

## <a name="prerequisites-for-per-app-vpn"></a>Requisitos previos de VPN por aplicación

> [!IMPORTANT]
> Su proveedor de VPN puede tener otros requisitos para la VPN por aplicación, como hardware o licencias específicos. Asegúrese de comprobar su documentación y cumplir los requisitos previos antes de configurar la VPN por aplicación en Intune.

Con el objetivo de demostrar su identidad, el servidor VPN presenta el certificado pertinente, el cual debe aceptarse sin ningún aviso del dispositivo. Para confirmar la aprobación automática del certificado, cree un perfil de certificado de confianza que contenga el certificado raíz del servidor VPN emitido por la entidad de certificación (CA). 

### <a name="export-the-certificate-and-add-the-ca"></a>Exportar el certificado y agregar la entidad de certificación

1. En el servidor VPN, abra la consola de administración.
2. Confirme que el servidor VPN usa una autenticación basada en certificado. 
3. Exporte el archivo del certificado raíz de confianza. Este presenta la extensión .cer, y puede agregarlo a la hora de crear un perfil de certificado de confianza.
4. Agregue el nombre de la entidad de certificación que ha emitido el certificado para la autenticación en el servidor VPN.

    Si la entidad de certificación que ha presentado el dispositivo coincide con una de las que figuran en la lista de entidades de certificación de confianza del servidor VPN, dicho servidor VPN autenticará el dispositivo correctamente.

## <a name="create-a-group-for-your-vpn-users"></a>Creación de un grupo para los usuarios de la VPN

Cree o elija un grupo existente en Azure Active Directory (Azure AD) para los usuarios o dispositivos que usen la VPN por aplicación. Para crear un grupo, vea [Agregar grupos para organizar usuarios y dispositivos](../fundamentals/groups-add.md).

## <a name="create-a-trusted-certificate-profile"></a>Creación de un perfil de certificado de confianza

Importe el certificado raíz del servidor VPN emitido por la entidad de certificación en un perfil creado en Intune. El perfil de certificado de confianza indicará al dispositivo iOS/iPadOS que puede confiar automáticamente en la entidad de certificación del servidor VPN.

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.
3. Escriba las propiedades siguientes:
    - **Nombre**: escriba un nombre descriptivo para el nuevo perfil. Asígnele un nombre a los perfiles para que pueda identificarlos de manera sencilla más adelante. Por ejemplo, un buen nombre de perfil es **Perfil de VPN de certificado de confianza de iOS/iPadOS en toda la empresa**.
    - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
    - **Plataforma**: Seleccione **iOS/iPad**.
    - **Tipo de perfil**: seleccione **Certificado de confianza**.
4. Haga clic en el icono de carpeta y localice el certificado VPN (archivo .cer) que ha exportado de la consola de administración de la VPN. 
5. Haga clic en **Aceptar** > **Crear**.

    ![Creación de un perfil de certificado de confianza para dispositivos iOS/iPadOS en Microsoft Intune](./media/vpn-setting-configure-per-app/vpn-per-app-create-trusted-cert.png)

## <a name="create-a-scep-or-pkcs-certificate-profile"></a>Creación de un perfil de certificado SCEP o PKCS

El perfil de certificado raíz de confianza permite al dispositivo confiar de forma automática en el servidor VPN. El certificado SCEP o PKCS proporciona las credenciales del cliente VPN de iOS/iPadOS para el servidor VPN. El certificado permite al dispositivo realizar la autenticación de forma silenciosa, sin solicitar un nombre de usuario ni la contraseña. 

Para configurar y asignar el certificado de autenticación del cliente, consulte uno de los siguientes artículos:

- [Configuración de la infraestructura para admitir SCEP con Intune](../protect/certificates-scep-configure.md)
- [Configuración y administración de certificados PKCS con Intune](../protect/certficates-pfx-configure.md)

Asegúrese de configurar el certificado para la autenticación de cliente. Puede establecer esto directamente en los perfiles de certificado SCEP (lista **Uso mejorado de clave** > **Autenticación de cliente**). En el caso de PKCS, establezca la autenticación de cliente en la plantilla de certificado en la entidad de certificación (CA).

![Creación de un perfil de certificado SCEP en Microsoft Intune, incluidos el formato de nombre del firmante, el uso de claves, el uso mejorado de clave y mucho más](./media/vpn-setting-configure-per-app/vpn-per-app-create-scep-cert.png)

## <a name="create-a-per-app-vpn-profile"></a>Creación de un perfil de VPN por aplicación

El perfil de VPN contiene el certificado SCEP o PKCS con las credenciales del cliente, la información de la conexión a la VPN y la marca de VPN por aplicación para permitir que la aplicación iOS/iPadOS use esa característica.

1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.
2. Escriba las propiedades siguientes:
    - **Nombre**: escriba un nombre descriptivo para el perfil personalizado. Asígnele un nombre a los perfiles para que pueda identificarlos de manera sencilla más adelante. Por ejemplo, un buen nombre de perfil es **Perfil de VPN de iOS/iPadOS por aplicación en toda la empresa**.
    - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
    - **Plataforma**: Seleccione **iOS/iPad**.
    - **Tipo de perfil**: seleccione **VPN**.
3. En **Tipo de conexión**, seleccione la aplicación de cliente VPN.
4. Seleccione **VPN base**. En [Configuración de VPN de iOS/iPadOS](vpn-settings-ios.md) se enumeran y describen todas las opciones de configuración. Al usar la VPN por aplicación, asegúrese de establecer las siguientes propiedades como se muestra:

    - **Método de autenticación**: seleccione **Certificados**. 
    - **Certificado de autenticación**: seleccione un certificado SCEP o PKCS existente > **Aceptar**.
    - **Tunelización dividida**: seleccione **Deshabilitar** para forzar que todo el tráfico use el túnel VPN cuando la conexión VPN esté activa. 

      ![En un perfil de VPN por aplicación, especifique una conexión, la dirección IP o FQDN, el método de autenticación y la tunelización dividida en Microsoft Intune](./media/vpn-setting-configure-per-app/vpn-per-app-create-vpn-profile.png)

    Para obtener información sobre las demás opciones de configuración, vea [Configuración de VPN de iOS/iPadOS](vpn-settings-ios.md).

5. Seleccione **VPN automática** > **Tipo de VPN automática** > **VPN por aplicación**.

    ![En Intune, establezca VPN automática en VPN por aplicación en dispositivos iOS/iPadOS](./media/vpn-setting-configure-per-app/vpn-per-app-automatic.png)

6. Seleccione **Aceptar** > **Aceptar** > **Crear**.

## <a name="associate-an-app-with-the-vpn-profile"></a>Asociación de una aplicación al perfil de VPN

Tras agregar el perfil de VPN, asocie la aplicación y el grupo de Azure AD al perfil.

1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), seleccione **Aplicaciones** > **Todas las aplicaciones**.
2. Seleccione una aplicación de la lista > **Asignaciones** > **Agregar grupo**.
3. En **Tipo de asignación**, seleccione **Requerida** o **Disponible para dispositivos inscritos**.
4. Seleccione **Grupos incluidos** > **Seleccionar grupos para incluir** > Seleccione el grupo [que ha creado](#create-a-group-for-your-vpn-users) (en este artículo) > **Seleccionar**.
5. En **VPN**, seleccione el perfil de VPN por aplicación [que ha creado](#create-a-per-app-vpn-profile) (en este artículo).

    ![Asignación de una aplicación al perfil de VPN por aplicación en Microsoft Intune](./media/vpn-setting-configure-per-app/vpn-per-app-app-to-vpn.png)

6. Seleccione **Aceptar** > **Guardar**.

Una asociación entre una aplicación y un perfil se quita durante la próxima comprobación de dispositivos cuando se den todas estas condiciones:

- La aplicación se diseñó con la intención de instalación requerida.
- El perfil y la aplicación se destinan al mismo grupo.
- Quita la configuración de VPN por aplicación de la asignación de la aplicación.

Una asociación entre una aplicación y un perfil sigue existiendo hasta que el usuario solicite una reinstalación desde el Portal de empresa cuando se den todas estas condiciones:

- La aplicación se diseñó con la intención de instalación disponible.
- El perfil y la aplicación se destinan al mismo grupo.
- El usuario final ha solicitado la instalación de la aplicación desde el Portal de empresa, lo que da como resultado que la aplicación y el perfil se instalen en el dispositivo.
- Quite o cambie la configuración de VPN por aplicación de la asignación de la aplicación.

## <a name="verify-the-connection-on-the-iosipados-device"></a>Comprobación de la conexión en el dispositivo iOS/iPadOS

Una vez que la VPN por aplicación esté configurada y asociada a su aplicación, compruebe que la conexión funcione desde un dispositivo.

### <a name="before-you-attempt-to-connect"></a>Antes de probar la conexión

- Asegúrese de implementar todas las directivas mencionadas anteriormente en el mismo grupo. En caso contrario, la experiencia de VPN por aplicación no funcionará.
- Si usa la aplicación de VPN Pulse Secure o una aplicación de cliente VPN personalizada, puede elegir la tunelización de la capa de aplicaciones o de la capa de paquetes. Establezca el valor **ProviderType** en **app-proxy** para la tunelización de la capa de la aplicación o **packet-tunnel** para la tunelización de la capa de paquetes. Compruebe la documentación de su proveedor de VPN para asegurarse de que usa el valor correcto.

### <a name="connect-using-the-per-app-vpn"></a>Conexión mediante la VPN por aplicación

Conéctese sin seleccionar la VPN ni escribir las credenciales para comprobar la experiencia sin intervención por parte del usuario. Por "experiencia sin intervención por parte del usuario" se entiende lo siguiente:

- El dispositivo no solicita que confíe en el servidor VPN. Es decir, el usuario no ve el cuadro de diálogo de **Dynamic Trust** (Confianza dinámica).
- El usuario no tiene que escribir las credenciales.
- El dispositivo del usuario está conectado a la VPN cuando el usuario abre una de las aplicaciones asociadas.

## <a name="next-steps"></a>Pasos siguientes

- Para revisar la configuración de iOS/iPadOS, vea [Configuración de VPN para dispositivos iOS/iPadOS en Microsoft Intune](vpn-settings-ios.md).
- Para obtener más información sobre la configuración de VPN e Intune, consulte [Configuración de VPN en Microsoft Intune](vpn-settings-configure.md).
