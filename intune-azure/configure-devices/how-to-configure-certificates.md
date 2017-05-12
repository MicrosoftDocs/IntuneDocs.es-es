---
title: "Configuración de certificados con Intune | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda a usar Intune para crear y asignar certificados que ayuden a proteger conexiones Wi-Fi, VPN y otras."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: ecb6a806e7870fd2b1986c4247607c9374431151
ms.contentlocale: es-es
ms.lasthandoff: 05/10/2017


---

# <a name="how-to-configure-certificates-in-microsoft-intune"></a>Configuración de certificados en Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Si proporciona a los usuarios acceso a los recursos corporativos a través de VPN, Wi-Fi o perfiles de correo electrónico, puede autenticar estas conexiones mediante certificados. Los certificados eliminan la necesidad de escribir nombres de usuario y contraseñas para autenticar las conexiones.

Puede usar Intune para asignar estos certificados a los dispositivos que administra. Intune admite asignar y administrar estos tipos de certificado:

- Protocolo de inscripción de certificados simple (SCEP)
- PKCS#12 (o PFX)

Cada uno de los tipos de certificado tiene sus propios requisitos previos y requisitos de infraestructura.

## <a name="general-workflow"></a>Flujo de trabajo general

1. Asegúrese de que disponga de la infraestructura de certificados adecuada. Puede usar [certificados SCEP](configure-certificate-infrastructure-for-scep.md) y [certificados PKCS](configure-certificate-infrastructure-for-pfx.md).
2. Instale un certificado raíz o certificado de entidad de certificación (CA) intermedia en cada dispositivo para que el dispositivo reconozca la legitimidad de la entidad de certificación. Para ello, cree y asigne un **perfil de certificado de confianza**. Al asignar este perfil, los dispositivos que se administren con Intune solicitarán y recibirán el certificado raíz. Debe crear un perfil independiente para cada plataforma. Existen perfiles de certificado de confianza para las siguientes plataformas:
    - iOS 8.0 y versiones posteriores
    - macOS 10.9 y versiones posteriores
    - Android 4.0 y versiones posteriores
    - Android for Work
    - Windows 8.1 y posterior
    - Windows Phone 8.1 y versiones posteriores
    - Windows 10 y versiones posteriores
3. Cree perfiles de certificados para que los dispositivos soliciten un certificado para la autenticación del acceso al correo electrónico y a las redes VPN y Wi-Fi. Puede crear y asignar un perfil de certificado **PKCS** o **SCEP** para dispositivos que ejecutan estas plataformas:
    - iOS 8.0 y versiones posteriores
    - Android 4.0 y versiones posteriores
    - Android for Work
    - Windows 10 para escritorios y Windows 10 Mobile y versiones posteriores

    Solo puede usar un perfil de certificado SCEP con estas plataformas:

-     macOS 10.9 y versiones posteriores
-     Windows Phone 8.1 y versiones posteriores

Debe crear un perfil independiente para cada plataforma de dispositivo. Cuando cree el perfil, asócielo con el perfil de certificado raíz de confianza que creó previamente.

### <a name="further-considerations"></a>Otras consideraciones

- Si no dispone de una entidad de certificación empresarial, debe crear una.
- Si decide, en función de sus plataformas de dispositivo, usar el Protocolo de inscripción de certificados simple (SCEP), también tendrá que configurar un servidor del Servicio de inscripción de dispositivos de red (NDES).
- Si planea usar perfiles SCEP o PFX, debe descargar y configurar Microsoft Intune Certificate Connector.


## <a name="step-1--configure-your-certificate-infrastructure"></a>Paso 1: configurar la infraestructura de certificados

Consulte uno de los temas siguientes para configurar la infraestructura de cada tipo de perfil de certificado:

- [Configuración y administración de certificados SCEP con Intune](configure-certificate-infrastructure-for-scep.md)
- [Configuración y administración de certificados PKCS con Intune](configure-certificate-infrastructure-for-pfx.md)


## <a name="step-2---export-your-trusted-root-ca-certificate"></a>Paso 2: exportar el certificado de CA raíz de confianza

Exporte el certificado de entidades de certificación (CA) raíz de confianza como un archivo **.cer** desde la CA emisora o desde cualquier dispositivo que confíe en la CA emisora. No exporte la clave privada.

Volverá a importar este certificado cuando configure un perfil de certificado de confianza.

## <a name="step-3-create-trusted-certificate-profiles"></a>Paso 3: crear perfiles de certificado de confianza
Debe crear un perfil de certificado de confianza para poder crear un perfil de certificado SCEP o PKCS. Necesitará un perfil de certificado de confianza y un perfil de SCEP o PKCS para cada plataforma de dispositivo. El flujo de la creación de certificados de confianza es similar en cada plataforma de dispositivo.

### <a name="to-create-a-trusted-certificate-profile"></a>Para crear un perfil de certificado de confianza

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
3. En la hoja **Intune**, elija **Configuración del dispositivo**.
2. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
3. En la hoja de perfiles, elija **Create Profile** (Crear perfil).
4. En la hoja **Create Profile** (Crear perfil), escriba un **nombre** y una **descripción** para el perfil de certificado de confianza.
5. En la lista desplegable **Plataforma**, seleccione la plataforma de dispositivo para este certificado de confianza. Actualmente, puede elegir una de las siguientes plataformas para la configuración del certificado:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 y versiones posteriores**
    - **Windows 10 y versiones posteriores**
6. En la lista desplegable de **Tipos de perfil**, elija **Certificado de confianza**.
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

## <a name="step-4-create-scep-or-pkcs-certificate-profiles"></a>Paso 4: crear perfiles de certificado SCEP o PKCS

Consulte uno de los temas siguientes para configurar y asignar cada tipo de perfil de certificado:

- [Configuración y administración de certificados SCEP con Intune](configure-certificate-infrastructure-for-scep.md)
- [Configuración y administración de certificados PKCS con Intune](configure-certificate-infrastructure-for-pfx.md)

Después de haber creado un perfil de certificado de confianza, cree perfiles de certificado SCEP o PKCS para cada plataforma que quiera usar. Al crear un perfil de certificado SCEP, debe especificar un perfil de certificado de confianza para esa misma plataforma. Esto vincula los dos perfiles de certificado, aunque todavía debe asignar cada perfil por separado.


## <a name="next-steps"></a>Pasos siguientes
Consulte [Asignación de perfiles de dispositivo](how-to-assign-device-profiles.md) para obtener información general sobre cómo asignar dispositivos.

