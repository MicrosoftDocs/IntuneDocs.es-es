---
title: Configurar perfiles de certificado | Microsoft Intune
description: Aprenda a crear un perfil de certificado de Intune.
keywords: 
author: nbigman
manager: angrobe
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 679a20a1-e66f-4b6b-bd8f-896daf1f8175
ms.reviewer: kmyrup
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 55d3bd060b5567e98ca9ee6f4c4a003ce40a0371
ms.openlocfilehash: 370a21f559fd1f86f60aeef5cbddea05d6fea682


---

# Configurar perfiles de certificado de Intune
Después de configurar la infraestructura y los certificados descritos en [Configurar la infraestructura de certificado para SCEP](configure-certificate-infrastructure-for-scep.md) o [Configurar la infraestructura de certificado de PFX](configure-certificate-infrastructure-for-pfx.md), puede crear perfiles de certificado. Este es el proceso:

- **Tarea 1**: Exportar el certificado de CA raíz de confianza
- **Tarea 2**: Crear perfiles de certificado de CA de confianza
- **Tarea 3**: Crear uno de los dos tipos de perfil de certificado:
  - Perfiles de certificados de SCEP
  - Perfiles de certificado .PFX

## **Tarea 1**: Exportar el certificado de CA raíz de confianza
Exporte el certificado de entidades de certificación raíz de confianza (CA) como archivo **.cer** desde la CA emisora o desde cualquier dispositivo que confíe en la CA emisora. No exporte la clave privada.

Importará este certificado al configurar un perfil de certificado de confianza.

## **Tarea 2**: Crear perfiles de certificado de CA de confianza
Debe crear un perfil de Certificado de CA de confianza para poder crear un perfil de certificado PKCS #12 (.PFX) o de Protocolo de inscripción de certificados simple. Necesita un perfil de certificado de confianza y un SCEP o perfil PFX para cada plataforma de dispositivo móvil.

### Para crear un perfil de certificado de confianza

1.  En la [consola de administración de Intune](https://manage.microsoft.com), elija **Directiva** &gt; **Agregar directiva**.
2.  Agregue uno de estos tipos de directivas:
    - **Android &gt; Perfil de certificado de confianza (Android 4 y versiones posteriores)**
    - **iOS &gt; Perfil de certificado de confianza (iOS 7.1 y versiones posteriores)**
    - **Perfil de certificado de confianza Mac OS X &gt; (Mac OS X 10.9 y versiones posteriores)**
    - **Perfil de certificado de confianza Windows &gt; (Windows 8.1 y versiones posteriores)**
    - **Perfil de certificado de confianza Windows &gt; (Windows Phone 8.1 y versiones posteriores)**

    Más información: [Administrar la configuración y las funciones de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Especifique la información solicitada para configurar las opciones del perfil de certificado de confianza para Android, iOS, Mac OS X, Windows 8.1 o Windows Phone 8.1. 
4.  En la configuración **Archivo de certificado**, importe el certificado de CA raíz de confianza (archivo .cer) que exportó del CA de emisión. La configuración **Almacén de destino** se aplica solo a dispositivos con Windows 8.1 y versiones posteriores, y solo si el dispositivo tiene más de un almacén de certificados.
    
4.  Elija **Guardar directiva**.

La nueva directiva se muestra en el área de trabajo **Directiva**. Ahora puede implementarla.

## **Tarea 3**: Crear perfiles de certificado .PFX o SCEP
Después de crear un perfil de certificado de CA de confianza, cree perfiles de certificado SCEP o .PFX para cada plataforma que desee usar. Al crear un perfil de certificado SCEP, debe especificarse un perfil de certificado de confianza para esa misma plataforma. Esto vincula los dos perfiles de certificado, aunque aún debe implementar cada perfil por separado.

### Para crear un perfil de certificado SCEP

1.  En la [consola de administración de Intune](https://manage.microsoft.com), elija **Directiva** &gt; **Agregar directiva**.
2.  Agregue uno de estos tipos de directivas:
    - **Android &gt; Perfil de certificado SCEP (Android 4 y versiones posteriores)**
    - **iOS &gt; Perfil de certificado SCEP (iOS 7.1 y versiones posteriores)**
    - **Mac OS X &gt; Perfil de certificado SCEP (Mac OS X 10.9 y versiones posteriores)**
    - **Windows &gt; Perfil de certificado SCEP (Windows 8.1 y versiones posteriores)**
    - **Windows &gt; Perfil de certificado SCEP (Windows Phone 8.1 y versiones posteriores)**

    Más información: [Administrar la configuración y las funciones de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Siga las instrucciones en la página de configuración de perfil para configurar las opciones del perfil de certificado SCEP.
    > [!NOTE]
    >
    > En **Formato de nombre de sujeto**, seleccione **Personalizado** para especificar un formato de nombre de sujeto personalizado (solo en perfiles iOS).
    >
    > Las dos variables que se admiten actualmente para el formato personalizado son `Common Name (CN)` y `Email (E)`. Mediante una combinación de estas variables y cadenas estáticas, puede crear un formato de nombre de sujeto personalizado, como esta:

    >     CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US

    > En este ejemplo, el administrador creó un formato de nombre de sujeto que, además de las variables `CN` y `E`, usa cadenas de valores de unidad organizativa, organización, ubicación, estado y país. La función [CertStrToName](https://msdn.microsoft.com/en-us/library/windows/desktop/aa377160.aspx) enumera las cadenas compatibles.

4.  Elija **Guardar directiva**.

La nueva directiva se muestra en el área de trabajo **Directiva**. Ahora puede implementarla.

### Para crear un perfil de certificado .PFX

1.  En la [consola de administración de Intune](https://manage.microsoft.com), elija **Directiva** &gt; **Agregar directiva**.
2.  Agregue uno de estos tipos de directivas:
  - **Android &gt; Perfil de certificado .PFX (Android 4 y versiones posteriores)**
  - **Windows &gt; Perfil de certificado PKCS #12 (.PFX) (Windows 10 y versiones posteriores)**
  - **Windows &gt; Perfil de certificado PKCS #12 (.PFX) (Windows Phone 10 y versiones posteriores)**
  - **iOS > Perfil de certificado PKCS #12 (.PFX) (iOS 7.1 y versiones posteriores)**    
    Más información: [Administrar la configuración y las funciones de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).
3.  Proporcione la información solicitada en el formulario de la directiva.
4.  Elija **Guardar directiva**.

La nueva directiva se muestra en el área de trabajo **Directiva**. Ahora puede implementarla.

## Implementar perfiles de certificado
Al implementar perfiles de certificado, el archivo de certificado del perfil de certificado de CA de confianza se instala en el dispositivo. El dispositivo usa el perfil de certificado SCEP o .PFX para crear una solicitud de certificado por el dispositivo.

Los perfiles de certificado solo se instalan en dispositivos que ejecutan la plataforma que usa cuando crea el perfil.

-   Puede implementar perfiles de certificado en recopilaciones de usuarios o en recopilaciones de dispositivos.

    > [!TIP]
    > Para publicar un certificado en un dispositivo rápidamente después de que se inscriba el dispositivo, implemente el perfil de certificado en un grupo de usuarios en lugar de en un grupo de dispositivos. Si se implementa en un grupo de dispositivos, debe realizarse un registro de todos los dispositivos antes de que el dispositivo reciba la directiva.

-   Aunque implemente cada perfil por separado, también debe implementar la CA raíz de confianza y el perfil SCEP o .PFX. De lo contrario, se producirá un error en la directiva de certificado SCEP o .PFX.

Implemente los perfiles de certificado de la misma forma que implementa otras directivas para Intune:

1.  En el área de trabajo **Directiva**, seleccione la directiva que quiera implementar y, a continuación, elija **Administrar implementación**.
2.  En el cuadro de diálogo **Administrar implementación**:
    -   **Para implementar la directiva**, seleccione uno o más grupos en los que desee implementar la directiva y elija **Agregar** &gt; **Aceptar**.
    -   **Para cerrar el cuadro de diálogo sin implementarla**, haga clic en **Cancelar**.

Cuando se selecciona una directiva implementada, puede ver más información acerca de la implementación en la parte inferior de la lista de directivas.

### Pasos siguientes

A continuación, aprenda a usar certificados para ayudar a proteger los perfiles de correo electrónico, Wi-Fi y VPN.

-  [Configurar el acceso al correo electrónico corporativo mediante perfiles de correo electrónico](configure-access-to-corporate-email-using-email-profiles-with-Microsoft-Intune.md)
-  [Conexiones Wi-Fi en Microsoft Intune](wi-fi-connections-in-microsoft-intune.md)
-  [Conexiones VPN en Microsoft Intune](vpn-connections-in-microsoft-intune.md)



<!--HONumber=Sep16_HO2-->


