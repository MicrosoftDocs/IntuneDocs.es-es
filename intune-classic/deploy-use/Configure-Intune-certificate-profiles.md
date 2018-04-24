---
title: Configurar perfiles de certificado
description: Aprenda a crear un perfil de certificado de Intune.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 10/25/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 679a20a1-e66f-4b6b-bd8f-896daf1f8175
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: kmyrup
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 51da197b9b805fbac22b6a46453617b7703a37e8
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="configure-intune-certificate-profiles"></a>Configurar perfiles de certificado de Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Después de configurar la infraestructura y los certificados tal como se describe en [Configurar la infraestructura de certificados para SCEP](configure-certificate-infrastructure-for-scep.md) o [Configurar la infraestructura de certificados para PFX](configure-certificate-infrastructure-for-pfx.md), puede pasar a crear los perfiles de certificado. Este es el proceso:

- **Tarea 1**: exportar el certificado de CA raíz de confianza
- **Tarea 2**: crear perfiles de certificado de confianza
- **Tarea 3**: crear uno de los dos tipos de perfil de certificado:
  - Perfiles de certificados de SCEP
  - Perfiles de certificados .PFX

## <a name="task-1-export-the-trusted-root-ca-certificate"></a>**Tarea 1**: Exportar el certificado de CA raíz de confianza
Exporte el certificado de entidades de certificación raíz de confianza (CA) como archivo **.cer** desde la CA emisora o desde cualquier dispositivo que confíe en la CA emisora. No exporte la clave privada.

Volverá a importar este certificado cuando configure un perfil de certificado de confianza.

## <a name="task-2-create-trusted-certificate-profiles"></a>**Tarea 2**: Crear perfiles de certificado de CA de confianza
Debe crear un perfil de certificado de confianza para poder crear un perfil de certificado de Protocolo de inscripción de certificados simple (SCEP) o PKCS #12 (.PFX). Necesita un perfil de certificado de confianza y un perfil SCEP o .PFX para cada plataforma de dispositivo móvil.

### <a name="to-create-a-trusted-certificate-profile"></a>Para crear un perfil de certificado de confianza

1.  En la [consola de administración de Intune](https://manage.microsoft.com), seleccione **Directiva** &gt; **Agregar directiva** y elija una plataforma de dispositivo. Puede crear un perfil de certificado de confianza para estos dispositivos:

-  Android 4 y versiones posteriores

-  Android for Work

-  iOS 7.1 y versiones posteriores

-  Mac OS X 10.9 y versiones posteriores

-  Windows 8.1 y posterior

-  Windows Phone 8.1 y versiones posteriores

2.  Agregue una directiva **Perfil de certificado de confianza**.

    Más información: [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Proporcione la información que se le pide para configurar las opciones del perfil de certificado de confianza para Android, iOS, Mac OS X, Windows 8.1 o Windows Phone 8.1.
4.  En la opción **Archivo de certificado**, importe el certificado de CA raíz de confianza (archivo .cer) que exportó desde la CA emisora. La configuración **Almacén de destino** se aplica solo a dispositivos con Windows 8.1 y versiones posteriores, y solo si el dispositivo tiene más de un almacén de certificados.

4.  Seleccione **Guardar directiva**.

La nueva directiva aparece en el área de trabajo **Directiva**. Ya puede implementarla.

> [!NOTE]
>
> Los dispositivos Android y Android for Work mostrarán un aviso notificándole que un tercero ha instalado un certificado de confianza.


## <a name="task-3-create-scep-or-pfx-certificate-profiles"></a>**Tarea 3**: crear perfiles de certificado SCEP o .PFX
Después de haber creado un perfil de certificado de CA de confianza, cree perfiles de certificado SCEP o .PFX para cada plataforma que quiera usar. Al crear un perfil de certificado SCEP, debe especificar un perfil de certificado de confianza para esa misma plataforma. Esto vincula los dos perfiles de certificado, aunque todavía debe implementar cada perfil por separado.

### <a name="to-create-an-scep-certificate-profile"></a>Para crear un perfil de certificado SCEP

1.  En la [consola de administración de Intune](https://manage.microsoft.com), seleccione **Directiva** &gt; **Agregar directiva** y elija una plataforma de dispositivo.  Puede crear un perfil de certificado SCEP para estos dispositivos:

-  Android 4 y versiones posteriores

-  Android for Work

-  iOS 7.1 y versiones posteriores

-  Mac OS X 10.9 y versiones posteriores

-  Windows 8.1 y posterior

-  Windows Phone 8.1 y versiones posteriores

2. Agregue una directiva **Perfil de certificado SCEP**.

   Más información: [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3. Siga las instrucciones en la página de configuración de perfil para configurar las opciones del perfil de certificado SCEP.
   > [!NOTE]
   > 
   > En **Formato de nombre de sujeto**, seleccione **Personalizado** para especificar un formato de nombre de sujeto personalizado (solo en perfiles iOS).
   > 
   > Las dos variables que se admiten actualmente para el formato personalizado son `Common Name (CN)` y `Email (E)`. Mediante una combinación de estas variables y cadenas estáticas, puede crear un formato de nombre de sujeto personalizado, como el siguiente:
   > 
   >     CN={{nombreDeUsuario}},E={{direcciónDeCorreoElectrónico}},OU=Móvil,O=Departamento financiero,L=Redmond,ST=Washington,C=US
   > 
   > En este ejemplo, el administrador crea un formato de nombre de sujeto que, además de las variables `CN` y `E`, usa cadenas para los valores Unidad organizativa, Organización, Ubicación, Estado y País. [La función CertStrToName](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) muestra las cadenas admitidas.

4. Seleccione **Guardar directiva**.

La nueva directiva aparece en el área de trabajo **Directiva**. Ya puede implementarla.

### <a name="to-create-a-pfx-certificate-profile"></a>Para crear un perfil de certificado .PFX

1. En la [consola de administración de Intune](https://manage.microsoft.com), seleccione **Directiva** &gt; **Agregar directiva** y elija una plataforma de dispositivo. Se permiten los certificados .PFX para:
   - Android 4 y versiones posteriores
   - Android for Work
   - Windows 10 y versiones posteriores
   - Windows Phone 10 y versiones posteriores
   - iOS 8.0 y versiones posteriores    


2. Agregue una directiva **Perfil de certificado .PFX**.
     Más información: [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).
3. Escriba la información solicitada en el formulario de directiva.
4. Elija **Guardar directiva**.

La nueva directiva aparece en el área de trabajo **Directiva**. Ya puede implementarla.

## <a name="deploy-certificate-profiles"></a>Implementar perfiles de certificado
Al implementar perfiles de certificado, el archivo de certificado del perfil de certificado de CA de confianza se instala en el dispositivo. El dispositivo usa el perfil de certificado SCEP o .PFX para crear una solicitud de certificado por el dispositivo.

Los perfiles de certificado solo se instalan en los dispositivos que ejecutan la plataforma usada al crear el perfil.

-   Puede implementar perfiles de certificado en recopilaciones de usuarios o en recopilaciones de dispositivos.

    > [!TIP]
    > Para publicar rápidamente un certificado en un dispositivo una vez inscrito el dispositivo, implemente el perfil de certificado en un grupo de usuarios (no en un grupo de dispositivos). Si se implementa en un grupo de dispositivos, debe realizarse un registro de todos los dispositivos antes de que el dispositivo reciba la directiva.

-   Aunque implemente cada perfil por separado, también deberá implementar la CA raíz de confianza y el perfil SCEP o .PFX. De lo contrario, se producirá un error en la directiva del certificado SCEP o .PFX.

Implemente los perfiles de certificado igual que cualquier otra directiva para Intune:

1.  En el área de trabajo **Directiva**, seleccione la directiva que quiera implementar y, después, elija **Administrar la implementación**.
2.  En el cuadro de diálogo **Administrar implementación**:
    -   **Para implementar la directiva**, seleccione uno o varios grupos en los que quiera implementar la directiva y elija **Agregar** &gt; **Aceptar**.
    -   **Para cerrar el cuadro de diálogo sin implementarla**, seleccione **Cancelar**.

Al seleccionar una directiva implementada, puede ver más información sobre la implementación en la parte inferior de la lista de directivas.

### <a name="next-steps"></a>Pasos siguientes

Aprenda a usar los certificados para proteger los perfiles de VPN, el Wi-Fi y el correo electrónico.

-  [Configurar el acceso al correo electrónico corporativo mediante perfiles de correo electrónico](configure-access-to-corporate-email-using-email-profiles-with-Microsoft-Intune.md)
-  [Wi-Fi connections in Microsoft Intune](wi-fi-connections-in-microsoft-intune.md) (Conexiones Wi-Fi en Microsoft Intune)
-  [Conexiones VPN en Microsoft Intune](vpn-connections-in-microsoft-intune.md)
