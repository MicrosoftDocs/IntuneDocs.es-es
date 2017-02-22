---
title: "Configuración de certificados con Intune | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: aprenda a usar Intune para crear y asignar certificados que ayuden a proteger conexiones Wi-Fi, VPN y otras."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3f05e0018fb202ab5774e935c3f59855e4aa2e75
ms.openlocfilehash: a0183f2a170ed458b19c7688b20ee5ba5c2c696e


---

# <a name="how-to-configure-certificates-with-intune-azure-preview"></a>Configuración de certificados con la versión preliminar de Intune Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Si proporciona a los usuarios acceso a los recursos corporativos a través de VPN, Wi-Fi o perfiles de correo electrónico, tiene la opción de protegerlo con un certificado instalado en el dispositivo de cada usuario. El flujo de trabajo de alto nivel es el siguiente:

1. Asegúrese de que disponga de la infraestructura de certificados adecuada. Puede usar [certificados SCEP](configure-certificate-infrastructure-for-scep.md) y [certificados PKCS](configure-certificate-infrastructure-for-pfx.md).
2. Instale un certificado raíz o certificado de entidad de certificación (CA) intermedia en cada dispositivo para que el dispositivo reconozca la legitimidad de la entidad de certificación. Para ello, cree y asigne un **perfil de certificado de confianza**. Al asignar este perfil, los dispositivos que se administren con Intune solicitarán y recibirán el certificado raíz. Debe crear un perfil independiente para cada plataforma. Existen perfiles de certificado de confianza para las siguientes plataformas:
    - iOS 8.0 y versiones posteriores
    - macOS 10.9 y versiones posteriores
    - Android 4.0 y versiones posteriores <!--Android for Work --->
    - Windows 8.1 y posterior
    - Windows Phone 8.1 y versiones posteriores
    - Windows 10 y versiones posteriores
3. Cree perfiles de certificados para que los dispositivos soliciten un certificado para la autenticación del acceso al correo electrónico y a las redes VPN y Wi-Fi. Puede crear e implementar un perfil de certificado **PKCS** o **SCEP** para dispositivos que ejecutan estas plataformas:
    - iOS 8.0 y versiones posteriores
    - Android 4.0 y versiones posteriores
    - Android for Work
    - Windows 10 para escritorios y Windows 10 Mobile y versiones posteriores

    Solo puede usar un perfil de certificado SCEP con estas plataformas:

-   macOS 10.9 y versiones posteriores
-   Windows Phone 8.1 y versiones posteriores

Debe crear un perfil independiente para cada plataforma de dispositivo. Cuando cree el perfil, asócielo con el perfil de certificado raíz de confianza que creó previamente.

### <a name="further-considerations"></a>Otras consideraciones

- Si no dispone de una entidad de certificación empresarial, debe crear una.
- Si decide, en función de sus plataformas de dispositivo, usar el Protocolo de inscripción de certificados simple (SCEP), también tendrá que configurar un servidor del Servicio de inscripción de dispositivos de red (NDES).
- Si planea usar perfiles SCEP o PFX, debe descargar y configurar Microsoft Intune Certificate Connector.

## <a name="before-you-start"></a>Antes de empezar


### <a name="if-you-want-to-use-scep-certificates"></a>Si quiere usar certificados SCEP

Complete los requisitos previos necesarios en [Infraestructura de certificado para SCEP](/intune-azure/configure-devices/configure-certificate-infrastructure-for-scep).

### <a name="if-you-want-to-use-pkcs-certificates"></a>Si quiere usar certificados PKCS

Complete los requisitos previos necesarios en [Infraestructura de certificado para PKCS](/intune-azure/configure-devices/configure-certificate-infrastructure-for-pfx).

## <a name="task-1-export-the-trusted-root-ca-certificate"></a>Tarea 1: Exportación del certificado de la entidad de certificación raíz de confianza
Exporte el certificado de entidades de certificación (CA) raíz de confianza como un archivo **.cer** desde la CA emisora o desde cualquier dispositivo que confíe en la CA emisora. No exporte la clave privada.

Volverá a importar este certificado cuando configure un perfil de certificado de confianza.

## <a name="task-2-create-trusted-certificate-profiles"></a>Tarea 2: Creación de perfiles de certificado de confianza
Debe crear un perfil de certificado de confianza para poder crear un perfil de certificado SCEP o PKCS. Necesitará un perfil de certificado de confianza y un perfil de SCEP o PKCS para cada plataforma de dispositivo.

### <a name="to-create-a-trusted-certificate-profile"></a>Para crear un perfil de certificado de confianza

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
3. En la hoja **Intune**, elija **Configurar dispositivos**.
2. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
3. En la hoja de perfiles, elija **Create Profile** (Crear perfil).
4. En la hoja **Create Profile** (Crear perfil), escriba un **nombre** y una **descripción** para el perfil de certificado de confianza.
5. En la lista desplegable **Plataforma**, seleccione la plataforma de dispositivo para este certificado de confianza. Actualmente, puede elegir una de las siguientes plataformas para la configuración de restricciones de dispositivos:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 y versiones posteriores**
    - **Windows 10 y versiones posteriores**
6. En la lista desplegable de **tipos de perfil**, elija **Certificado de confianza**.
7. Busque el certificado que guardó en la tarea 1 y haga clic en **Aceptar**.
8. Solo para dispositivos Windows 8.1 y Windows 10, seleccione el **almacén de destino** del certificado de confianza. Las opciones son:
    - **Almacén de certificados de equipo - Raíz**
    - **Almacén de certificados de equipo - Intermedio**
    - **Almacén de certificados de usuario - Intermedio**
8. Cuando haya terminado, elija **Aceptar**, vuelva a la hoja **Create Profile** (Crear perfil) y seleccione **Crear**.

El perfil se crea y aparece en la hoja de la lista de perfiles.
Si desea continuar y asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](how-to-assign-device-profiles.md).


> [!Note]
> Los dispositivos Android mostrarán un aviso diciendo que un tercero ha instalado un certificado de confianza.

## <a name="task-3-create-scep-or-pkcs-certificate-profiles"></a>Tarea 3: Creación de perfiles de certificado SCEP o PKCS
Después de haber creado un perfil de certificado de confianza, cree perfiles de certificado SCEP o PKCS para cada plataforma que quiera usar. Al crear un perfil de certificado SCEP, debe especificar un perfil de certificado de confianza para esa misma plataforma. Esto vincula los dos perfiles de certificado, aunque todavía debe asignar cada perfil por separado.

### <a name="to-create-an-scep-certificate-profile"></a>Para crear un perfil de certificado SCEP

1. En Azure Portal, seleccione la carga de trabajo **Configurar dispositivos**.
2. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
3. En la hoja de perfiles, elija **Create Profile** (Crear perfil).
4. En la hoja **Create Profile** (Crear perfil), escriba un **nombre** y una **descripción** para el perfil de certificado SCEP.
5. En la lista desplegable **Plataforma**, seleccione la plataforma de dispositivo para este certificado SCEP. Actualmente, puede elegir una de las siguientes plataformas para la configuración de restricciones de dispositivos:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 y versiones posteriores**
    - **Windows 10 y versiones posteriores**
6. En la lista desplegable de **tipos de perfil**, elija **Certificado SCEP**.
7. En la hoja **Certificado SCEP**, configure los siguientes valores:
    - **Período de validez del certificado**: si ha ejecutado el comando **certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE** en la entidad de certificación emisora, que permite un período de validez personalizado, puede especificar la cantidad de tiempo restante antes de que expire el certificado.<br>Puede especificar un valor inferior al período de validez de la plantilla de certificado especificada, pero no superior. Por ejemplo, si el período de validez del certificado en la plantilla de certificado es de dos años, puede especificar un valor de un año, pero no un valor de cinco años. El valor también debe ser menor que el período de validez restante del certificado de la CA emisora. 
    - **Proveedor de almacenamiento de claves (KSP)** (Windows Phone 8.1, Windows 8.1, Windows 10): especifique dónde se almacenará la clave del certificado. Elija uno de los siguientes valores:
        - **Inscribirse en KSP Módulo de plataforma segura (TPM) si está presente, si no en KSP Software**
        - **Inscribirse en KSP del Módulo de plataforma segura (TPM) o se producirá un error**
        - **Inscribirse en Passport o se producirá un error (Windows 10 y versiones posteriores)**
        - **Inscribirse en el KSP Software**
    - **Formato de nombre del sujeto**: en la lista, seleccione cómo Intune crea automáticamente el nombre del sujeto en la solicitud de certificado. Si el certificado es para un usuario, también puede incluir la dirección de correo electrónico del usuario en el nombre del sujeto. Elija de entre las siguientes opciones:
        - **No configurado**.
        - **Nombre común**
        - **Nombre común, incluyendo la dirección de correo electrónico**
        - **Nombre común como correo electrónico**
    - **Subject alternative name** (Nombre alternativo del sujeto): especifique cómo Intune creará automáticamente los valores del nombre alternativo del sujeto (SAN) en la solicitud de certificado. Por ejemplo, si seleccionó un tipo de certificado de usuario, puede incluir el nombre principal de usuario (UPN) en el nombre alternativo del sujeto. Si el certificado de cliente se utilizará para autenticar un servidor de directivas de redes, debe establecer el nombre alternativo del sujeto en el UPN. 
    - **Uso de la clave**: especifique las opciones de uso de claves para el certificado. Puede elegir entre las siguientes opciones: 
        - **Cifrado de clave**: permite el intercambio de claves solo si la clave está cifrada. 
        - **Firma digital**: permite el intercambio de claves solo cuando una firma digital ayuda a proteger la clave. 
    - **Tamaño de la clave (bits)**: seleccione el número de bits que contendrá la clave. 
    - **Algoritmo hash** (Android, Windows Phone 8.1, Windows 8.1, Windows 10): seleccione uno de los tipos de algoritmos hash disponibles para usar con este certificado. Seleccione el nivel máximo de seguridad que admiten los dispositivos de conexión. 
    - **Certificado raíz**: elija un perfil de certificado de CA raíz que previamente haya configurado y asignado al usuario o dispositivo. Este certificado de CA debe ser el certificado raíz para la entidad de certificación que emitirá el certificado que va a configurar en este perfil de certificado. 
    - **Uso mejorado de clave**: elija **Agregar** para agregar valores para la finalidad prevista del certificado. En la mayoría de los casos, el certificado requerirá **Autenticación de cliente** para que el usuario o dispositivo pueda autenticarse en un servidor. Sin embargo, puede agregar otros usos de clave según sea necesario. 
    - **Configuración de la inscripción**
        - **Umbral de renovación (%)**: especifique qué porcentaje de la duración del certificado tiene que quedar para que el dispositivo solicite la renovación del certificado.
        - **Direcciones URL del servidor SCEP**: especifique una o varias direcciones URL para los servidores NDES que emitirán certificados mediante SCEP. 
8. Cuando haya terminado, vuelva a la hoja **Create Profile** (Crear perfil) y presione **Crear**.

El perfil se crea y aparece en la hoja de la lista de perfiles.

Siga las instrucciones de la página de configuración de perfil para configurar las opciones de perfil de certificado SCEP.
>[!Note]
> Solo para dispositivos iOS: en Formato de nombre del firmante, seleccione Personalizado para especificar un formato de nombre de firmante personalizado.
> Las dos variables que se admiten actualmente para el formato personalizado son **nombre común (CN)** y **correo electrónico (E)**. Mediante una combinación de estas cadenas estáticas y variables, puede crear un formato de nombre de firmante personalizado, como este: **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US** En este ejemplo, ha creado un formato de nombre del firmante que, además de las variables CN y E, usa cadenas para los valores Unidad organizativa, Organización, Ubicación, Estado y País. [En este tema](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) se muestra la función **CertStrToName** y sus cadenas admitidas.


### <a name="to-create-a-pkcs-certificate-profile"></a>Creación de un perfil de certificado PKCS

En Azure Portal, seleccione la carga de trabajo **Configurar dispositivos**.
2. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
3. En la hoja de perfiles, haga clic en **Create Profile** (Crear perfil).
4. En la hoja **Create Profile** (Crear perfil), escriba un **nombre** y una **descripción** para el perfil de certificado PKCS.
5. En la lista desplegable **Plataforma**, seleccione la plataforma de dispositivo para este certificado PKCS:
    - **Android**
    - **iOS**
    - **Windows 10 y versiones posteriores**
6. En la lista desplegable de **tipos de perfil**, elija **Certificado PKCS**.
7. En la hoja **Certificado PKCS**, configure los siguientes valores:
    - **Umbral de renovación (%)**: especifique qué porcentaje de la duración del certificado tiene que quedar para que el dispositivo solicite la renovación del certificado.
    - **Período de validez del certificado**: si ha ejecutado el comando **certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE** en la entidad de certificación emisora, que permite un período de validez personalizado, puede especificar la cantidad de tiempo restante antes de que expire el certificado.<br>Puede especificar un valor inferior al período de validez de la plantilla de certificado especificada, pero no superior. Por ejemplo, si el período de validez del certificado en la plantilla de certificado es de dos años, puede especificar un valor de un año, pero no un valor de cinco años. El valor también debe ser menor que el período de validez restante del certificado de la CA emisora.
    - **Proveedor de almacenamiento de claves (KSP)** (Windows 10)
    - **Entidad de certificación** -
    - **Nombre de la entidad de certificación** -
    - **Nombre de plantilla de certificado**: escriba el nombre de una plantilla de certificado cuya utilización está configurada en el Servicio de inscripción de dispositivos de red y que se haya agregado a una CA emisora.
    Asegúrese de que el nombre coincida exactamente con una de las plantillas de certificado que se muestran en el Registro del servidor que ejecuta el Servicio de inscripción de dispositivos de red. Asegúrese de que especifica el nombre de la plantilla de certificado y no el nombre para mostrar de la plantilla de certificado. 
    Para buscar los nombres de las plantillas de certificado, vaya a la siguiente clave: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP. Verá las plantillas de certificado como los valores de **EncryptionTemplate**, **GeneralPurposeTemplate**y **SignatureTemplate**. De forma predeterminada, el valor de las tres plantillas de certificado es IPSECIntermediateOffline, que se asigna al nombre de plantilla para mostrar **IPSEC (solicitud sin conexión)**. 
    - **Formato de nombre del sujeto**: en la lista, seleccione cómo Intune crea automáticamente el nombre del sujeto en la solicitud de certificado. Si el certificado es para un usuario, también puede incluir la dirección de correo electrónico del usuario en el nombre del sujeto. Elija de entre las siguientes opciones:
        - **No configurado**.
        - **Nombre común**
        - **Nombre común, incluyendo la dirección de correo electrónico**
        - **Nombre común como correo electrónico**
    - **Subject alternative name** (Nombre alternativo del sujeto): especifique cómo Intune creará automáticamente los valores del nombre alternativo del sujeto (SAN) en la solicitud de certificado. Por ejemplo, si seleccionó un tipo de certificado de usuario, puede incluir el nombre principal de usuario (UPN) en el nombre alternativo del sujeto. Si el certificado de cliente se utilizará para autenticar un servidor de directivas de redes, debe establecer el nombre alternativo del sujeto en el UPN.
    - **Uso mejorado de clave** (Android): elija **Agregar** para agregar valores para la finalidad prevista del certificado. En la mayoría de los casos, el certificado requerirá **Autenticación de cliente** para que el usuario o dispositivo pueda autenticarse en un servidor. Sin embargo, puede agregar otros usos de clave según sea necesario. 
    - **Certificado raíz** (Android): elija un perfil de certificado de CA raíz que previamente haya configurado y asignado al usuario o dispositivo. Este certificado de CA debe ser el certificado raíz para la entidad de certificación que emitirá el certificado que va a configurar en este perfil de certificado.
8. Cuando haya terminado, vuelva a la hoja **Create Profile** (Crear perfil) y presione **Crear**.

El perfil se crea y aparece en la hoja de la lista de perfiles.

## <a name="task-4-assign-certificate-profiles"></a>Tarea 4: Asignación de perfiles de certificado

Considere los siguiente aspectos antes de asignar perfiles de certificado a grupos:

- Cuando asigna perfiles de certificado a grupos, el archivo de certificado del perfil de certificado de CA de confianza se instala en el dispositivo. El dispositivo usa el perfil de certificado SCEP o PKCS para crear una solicitud de certificado.
- Los perfiles de certificado solo se instalan en dispositivos que ejecutan la plataforma usada al crear el perfil.
- Puede implementar perfiles de certificado en recopilaciones de usuarios o en recopilaciones de dispositivos.
- Para publicar rápidamente un certificado en un dispositivo una vez inscrito el dispositivo, implemente el perfil de certificado en un grupo de usuarios (no en un grupo de dispositivos). Si lo implementa en un grupo de dispositivos, deberá efectuar un registro completo del dispositivo para que el dispositivo reciba directivas.
- Aunque implemente cada perfil por separado, también deberá implementar la CA raíz de confianza y el perfil SCEP o PKCS. De lo contrario, se producirá un error en la directiva del certificado SCEP o PKCS.

## <a name="next-steps"></a>Pasos siguientes
Consulte [Asignación de perfiles de dispositivo](how-to-assign-device-profiles.md) para obtener información general sobre cómo asignar dispositivos.



<!--HONumber=Feb17_HO1-->


