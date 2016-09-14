---
title: Configurar perfiles de certificado | Microsoft Intune
description: Aprenda a crear un perfil de certificado de Intune.
keywords: 
author: nbigman
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 679a20a1-e66f-4b6b-bd8f-896daf1f8175
ms.reviewer: kmyrup
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8e3f7cac8eb3495aad3835ec4713d67a58383c66
ms.openlocfilehash: 8b08f8fde6136b8eca61f6ae7a8c21635f7d452e


---

# Configurar perfiles de certificado de Intune
Después de configurar la infraestructura y los certificados tal como se describe en [Configurar la infraestructura de certificados para SCEP](configure-certificate-infrastructure-for-scep.md) o [Configurar la infraestructura de certificados para PFX](configure-certificate-infrastructure-for-pfx.md), puede pasar a crear los perfiles de certificado. Este es el proceso:

- **Tarea 1**: exportar el certificado de CA raíz de confianza
- **Tarea 2**: crear perfiles de certificado de confianza
- **Tarea 3**: crear uno de los dos tipos de perfil de certificado:
  - Perfiles de certificados de SCEP
  - Perfiles de certificados .PFX

## **Tarea 1**: exportar el certificado de CA raíz de confianza
Exporte el certificado de entidades de certificación (CA) raíz de confianza como un archivo **.cer** desde la CA emisora o desde cualquier dispositivo que confíe en la CA emisora. No exporte la clave privada.

Volverá a importar este certificado cuando configure un perfil de certificado de confianza.

## **Tarea 2**: crear perfiles de certificado de confianza
Debe crear un perfil de certificado de confianza para poder crear un perfil de certificado de Protocolo de inscripción de certificados simple (SCEP) o PKCS #12 (.PFX). Necesita un perfil de certificado de confianza y un perfil SCEP o .PFX para cada plataforma de dispositivo móvil.

### Para crear un perfil de certificado de confianza

1.  En la [consola de administración de Intune](https://manage.microsoft.com), seleccione **Directiva** &gt; **Agregar directiva**.
2.  Agregue uno de estos tipos de directivas:
    - **Android &gt; Perfil de certificado de confianza (Android 4 y versiones posteriores)**
    - **iOS &gt; Perfil de certificado de confianza (iOS 7.1 y versiones posteriores)**
    - **Mac OS X &gt; Perfil de certificado de confianza (Mac OS X 10.9 y versiones posteriores)**
    - **Windows &gt; Perfil de certificado de confianza (Windows 8.1 y versiones posteriores)**
    - **Windows &gt; Perfil de certificado de confianza (Windows Phone 8.1 y versiones posteriores)**

    Más información: [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Proporcione la información que se le pide para configurar las opciones del perfil de certificado de confianza para Android, iOS, Mac OS X, Windows 8.1 o Windows Phone 8.1.

    - En la opción **Archivo de certificado**, importe el certificado de CA raíz de confianza (archivo .cer) que exportó desde la CA emisora. La opción **Almacén de destino** es válida únicamente para dispositivos que ejecutan Windows 8.1 y versiones posteriores y solo si el dispositivo tiene más de un almacén de certificados.
    -  En **Formato de nombre de sujeto**, seleccione **Personalizado** para especificar un formato de nombre de sujeto personalizado.  
        Las dos variables que se admiten actualmente para el formato personalizado son `Common Name (CN)` y `Email (E)`. Mediante una combinación de estas variables y cadenas estáticas, puede crear un formato de nombre de sujeto personalizado, como el siguiente:  

        `CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US`  

        En este ejemplo, el administrador crea un formato de nombre de sujeto que, además de las variables `CN` y `E`, usa cadenas para los valores Unidad organizativa, Organización, Ubicación, Estado y País. [La función CertStrToName](https://msdn.microsoft.com/en-us/library/windows/desktop/aa377160.aspx) muestra las cadenas admitidas.  
4.  Seleccione **Guardar directiva**.

La nueva directiva aparece en el área de trabajo **Directiva**. Ya puede implementarla.

## **Tarea 3**: crear perfiles de certificado SCEP o .PFX
Después de haber creado un perfil de certificado de CA de confianza, cree perfiles de certificado SCEP o .PFX para cada plataforma que quiera usar. Al crear un perfil de certificado SCEP, debe especificar un perfil de certificado de confianza para esa misma plataforma. Esto vincula los dos perfiles de certificado, aunque todavía debe implementar cada perfil por separado.

### Para crear un perfil de certificado SCEP

1.  En la [consola de administración de Intune](https://manage.microsoft.com), seleccione **Directiva** &gt; **Agregar directiva**.
2.  Agregue uno de estos tipos de directivas:
    - **Android &gt; Perfil de certificado SCEP (Android 4 y versiones posteriores)**
    - **iOS &gt; Perfil de certificado SCEP (iOS 7.1 y versiones posteriores)**
    - **Mac OS X &gt; Perfil de certificado SCEP (Mac OS X 10.9 y versiones posteriores)**
    - **Windows &gt; Perfil de certificado SCEP (Windows 8.1 y versiones posteriores)**
    - **Windows &gt; Perfil de certificado SCEP (Windows Phone 8.1 y versiones posteriores)**

    Más información: [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Siga las instrucciones de la página de configuración de perfil para configurar las opciones de perfil de certificado SCEP.
    > [!NOTE]
    >
    > En **Formato de nombre de sujeto**, seleccione **Personalizado** para especificar un formato de nombre de sujeto personalizado.
    >
    > Las dos variables que se admiten actualmente para el formato personalizado son `Common Name (CN)` y `Email (E)`. Mediante una combinación de estas variables y cadenas estáticas, puede crear un formato de nombre de sujeto personalizado, como el siguiente:

    >     CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US

    > En este ejemplo, el administrador crea un formato de nombre de sujeto que, además de las variables `CN` y `E`, usa cadenas para los valores Unidad organizativa, Organización, Ubicación, Estado y País. [La función CertStrToName](https://msdn.microsoft.com/en-us/library/windows/desktop/aa377160.aspx) muestra las cadenas admitidas.

4.  Seleccione **Guardar directiva**.

La nueva directiva aparece en el área de trabajo **Directiva**. Ya puede implementarla.

### Para crear un perfil de certificado .PFX

1.  En la [consola de administración de Intune](https://manage.microsoft.com), seleccione **Directiva** &gt; **Agregar directiva**.
2.  Agregue uno de estos tipos de directivas:
  - **Android &gt; Perfil de certificado .PFX (Android 4 y versiones posteriores)**
  - **Windows &gt; Perfil de certificado PKCS #12 (.PFX) (Windows 10 y versiones posteriores)**
  - **Windows &gt; Perfil de certificado PKCS #12 (.PFX) (Windows Phone 10 y versiones posteriores)**
  - **iOS > Perfil de certificado PKCS #12 (.PFX) (iOS 7.1 y posterior)**    
    Más información: [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).
3.  Escriba la información solicitada en el formulario de directiva.
4.  Seleccione **Guardar directiva**.

La nueva directiva aparece en el área de trabajo **Directiva**. Ya puede implementarla.

## Implementar perfiles de certificado
Al implementar perfiles de certificado, el archivo de certificado del perfil de certificado de CA de confianza se instala en el dispositivo. El dispositivo usa el perfil de certificado SCEP o .PFX para crear una solicitud de certificado por el dispositivo.

Los perfiles de certificado solo se instalan en los dispositivos que ejecutan la plataforma usada al crear el perfil.

-   Puede implementar perfiles de certificado en recopilaciones de usuarios o en recopilaciones de dispositivos.

    > [!TIP]
    > Para publicar rápidamente un certificado en un dispositivo una vez inscrito el dispositivo, implemente el perfil de certificado en un grupo de usuarios (no en un grupo de dispositivos). Si lo implementa en un grupo de dispositivos, deberá efectuar un registro completo del dispositivo para que el dispositivo reciba directivas.

-   Aunque implemente cada perfil por separado, también deberá implementar la CA raíz de confianza y el perfil SCEP o .PFX. De lo contrario, se producirá un error en la directiva del certificado SCEP o .PFX.

Implemente los perfiles de certificado igual que cualquier otra directiva para Intune:

1.  En el área de trabajo **Directiva**, seleccione la directiva que quiera implementar y, después, elija **Administrar la implementación**.
2.  En el cuadro de diálogo **Administrar la implementación** :
    -   **Para implementar la directiva**, seleccione uno o varios grupos en los que quiera implementar la directiva y elija **Agregar** &gt; **Aceptar**.
    -   **Para cerrar el cuadro de diálogo sin implementarla**, seleccione **Cancelar**.

Al seleccionar una directiva implementada, puede ver más información sobre la implementación en la parte inferior de la lista de directivas.

### Pasos siguientes

Aprenda a usar los certificados para proteger los perfiles de VPN, el Wi-Fi y el correo electrónico.

-  [Configurar el acceso al correo electrónico corporativo mediante perfiles de correo electrónico](configure-access-to-corporate-email-using-email-profiles-with-Microsoft-Intune.md)
-  [Wi-Fi connections in Microsoft Intune (Conexiones Wi-Fi en Microsoft Intune)](wi-fi-connections-in-microsoft-intune.md)
-  [VPN connections in Microsoft Intune (Conexiones VPN en Microsoft Intune)](vpn-connections-in-microsoft-intune.md)



<!--HONumber=Aug16_HO5-->


