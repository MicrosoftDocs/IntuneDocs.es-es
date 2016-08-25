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
ms.sourcegitcommit: 6a7f2eeb0114f525890d1dcb61344d60a19943d1
ms.openlocfilehash: 14419092edc77b2229cf980a74e81048941a2c28


---

# Configurar perfiles de certificado de Intune
Después de configurar la infraestructura y los certificados según se describe en [Configurar la infraestructura de certificados para SCEP](configure-certificate-infrastructure-for-scep.md) o [Configurar la infraestructura de certificados para PFX](configure-certificate-infrastructure-for-pfx.md), puede pasar a configurar los perfiles de certificado:

**Tarea 1**: exportar el certificado de CA raíz de confianza **Tarea 2**: crear perfiles de certificado de CA de confianza **Tarea 3**: ya sea:

Crear perfiles de certificado SCEP

Crear perfiles de certificado .PFX

### Tarea 1: exportar el certificado raíz de confianza
Exporte el certificado de CA raíz de confianza como archivo **.cer** archivo desde la CA emisora o desde cualquier dispositivo que confíe en la CA emisora. No exporte la clave privada.

Volverá a importar este certificado al configurar un perfil de certificado de confianza.

### Tarea 2: crear perfiles de certificado de confianza
Debe crear un **perfil de certificado de confianza** para poder crear un perfil de certificado de SCEP o .PFX. Se necesita un perfil de certificado de confianza y un perfil de SCEP o .PFS para cada plataforma de dispositivo móvil.

##### Para crear un perfil de certificado de confianza

1.  Abra la [consola de administración de Intune](https://manage.microsoft.com) y haga clic en **Directiva** &gt; **Agregar directiva**.

2.  Configure uno de los siguientes tipos de directivas:

    **Android &gt; Perfil de certificado de confianza (Android 4 y versiones posteriores)**

    **iOS &gt; Perfil de certificado de confianza (iOS 7.1 y versiones posteriores)**

    **Mac OS X &gt; Perfil de certificado de confianza (Mac OS X 10.9 y versiones posteriores)**

    **Windows &gt; Perfil de certificado de confianza (Windows 8.1 y versiones posteriores)**

    **Windows &gt; Perfil de certificado de confianza (Windows Phone 8.1 y versiones posteriores)**

    Más información: [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Suministre la información que se le pide para configurar las opciones del perfil de certificado de confianza para Android, iOS, Mac OS X, Windows 8.1 o Windows Phone 8.1. 

    - En la opción **Archivo de certificado**, importe el certificado de CA raíz de confianza (**.cer**) que exportó desde la CA emisora. La opción **Almacén de destino** es válida únicamente para dispositivos que ejecutan Windows 8.1 y versiones posteriores y solo si el dispositivo tiene más de un almacén de certificados.

    
    - En **Formato de nombre de sujeto**, seleccione **Personalizado** para proporcionar un formato de nombre de sujeto personalizado.  

        Las dos variables que se admiten actualmente para el formato personalizado son **nombre común (CN)** y **correo electrónico (E)**. Mediante una combinación de estas variables y cadenas estáticas, puede crear un formato de nombre de sujeto personalizado, como se muestra en este ejemplo:  

        `CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US`  

        En el ejemplo, el administrador crea un formato de nombre de sujeto que, además de las variables de CN y E, usa cadenas de unidad organizativa, organización, ubicación, estado y país. Se proporciona una lista de cadenas admitidas en el tema [Función CertStrToName](https://msdn.microsoft.com/en-us/library/windows/desktop/aa377160.aspx).  


4.  Cuando haya terminado haga clic en **Guardar directiva**.

La nueva directiva se muestra en el área de trabajo **Directiva** y ahora puede implementarse.

### Tarea 3: crear perfiles de certificado .PFX o SCEP
Después de haber creado un perfil de certificado de CA de confianza, cree perfiles de certificado SCEP o .PFX para cada plataforma que desee usar. Al crear un perfil de certificado SCEP, debe especificar un perfil de certificado de confianza para esa misma plataforma. Esto vincula los dos perfiles de certificado, aunque aún debe implementar cada perfil por separado.

##### Para crear un perfil de certificado SCEP

1.  Abra la [consola de administración de Microsoft Intune](https://manage.microsoft.com), haga clic en **Directiva** &gt; **Agregar directiva**.

2.  Configure uno de los siguientes tipos de directivas:

    **Android &gt; Perfil de certificado SCEP (Android 4 y versiones posteriores)**

    **iOS &gt; Perfil de certificado SCEP (iOS 7.1 y versiones posteriores)**

    **Mac OS X &gt; Perfil de certificado SCEP (Mac OS X 10.9 y versiones posteriores)**

    **Windows &gt; Perfil de certificado SCEP (Windows 8.1 y versiones posteriores)**

    **Windows &gt; Perfil de certificado SCEP (Windows Phone 8.1 y versiones posteriores)**

    Más información: [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Siga las instrucciones de la página de configuración de perfil para configurar las opciones de perfil de certificado SCEP.
    > [!NOTE]
    > 
    > En **Formato de nombre de sujeto**, seleccione **Personalizado** para proporcionar un formato de nombre de sujeto personalizado.
    > 
    >  Las dos variables que se admiten actualmente para el formato personalizado son el nombre común (CN) y el correo electrónico (E). Mediante una combinación de estas variables y cadenas estáticas, puede crear un formato de nombre de sujeto personalizado, como se muestra en este ejemplo:
    
    >     CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US
    
    >    En el ejemplo, el administrador crea un formato de nombre de sujeto que, además de las variables de *CN* y *E* usa cadenas de unidad organizativa, organización, ubicación, estado y país. Se proporciona una lista de cadenas admitidas en el tema [Función CertStrToName](https://msdn.microsoft.com/en-us/library/windows/desktop/aa377160.aspx).

4.  Cuando haya terminado haga clic en **Guardar directiva**.

La nueva directiva se muestra en el área de trabajo **Directiva** y ahora puede implementarse.

##### Para crear un perfil de certificado .PFX

1.  Abra la [consola de administración de Microsoft Intune](https://manage.microsoft.com), haga clic en **Directiva** &gt; **Agregar directiva**.

2.  Configure uno de los siguientes tipos de directivas:



-   **Android &gt; Perfil de certificado .PFX (Android 4 y versiones posteriores)**

    -   **Windows &gt; Perfil de certificado PKCS #12 (.PFX) (Windows 10 y posterior)**

    -   **Windows &gt; Perfil de certificado PKCS #12 (.PFX) (Windows Phone 10 y posterior)**

    -    **iOS > Perfil de certificado PKCS #12 (.PFX) (iOS 7.1 y posterior)**    

    Más información: [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Proporcione la información solicitada en el formulario de directiva.

4.  Cuando haya terminado haga clic en **Guardar directiva**.

La nueva directiva se muestra en el área de trabajo **Directiva** y ahora puede implementarse.

## Implementar perfiles de certificado
Al implementar perfiles de certificado, el archivo de certificado del perfil de certificado de CA de confianza se instala en los dispositivos y el dispositivo usa el perfil de certificado SCEP o .PFX para crear una solicitud de certificado.

Los perfiles de certificado solo se instalan en dispositivos aplicables en función de la plataforma que use al crear el perfil.

-   Puede implementar perfiles de certificado en recopilaciones de usuarios o en recopilaciones de dispositivos.

    > [!TIP]
    > Para permitir que los certificados se publiquen en dispositivos rápidamente después de inscribir el dispositivo, implemente el perfil de certificado en un grupo de usuarios (no en un grupo de dispositivos). Si se implementa en un grupo de dispositivos, debe realizarse un registro de todos los dispositivos antes de que el dispositivo reciba la directiva.

-   Aunque cada perfil se implementa por separado, debe implementarse tanto el perfil de raíz de confianza como el perfil SCEP o .PFX o, de lo contrario, se producirá un error en la directiva de certificado SCEP o .PFX.

Los perfiles de certificado se implementan igual que cualquier otra directiva para Intune:

1.  En el área de trabajo **Directiva** , seleccione la directiva que quiera implementar y, a continuación, haga clic en **Administrar implementación**.

2.  En el cuadro de diálogo **Administrar la implementación** :

    -   **Para implementar la directiva**: seleccione uno o más grupos en los que quiera implementar la directiva y haga clic en **Agregar** &gt; **Aceptar**.

    -   **Para cerrar el cuadro de diálogo sin implementarla**: haga clic en **Cancelar**.

Cuando se selecciona una directiva implementada, puede ver más información acerca de la implementación en la parte inferior de la lista de directivas.
###  Pasos siguientes

Ya puede usar certificados para proteger los perfiles de VPN, Wi-Fi y correo electrónico:

-  [Configurar el acceso al correo electrónico corporativo mediante perfiles de correo electrónico](configure-access-to-corporate-email-using-email-profiles-with-Microsoft-Intune.md)
-  [Wi-Fi connections in Microsoft Intune (Conexiones Wi-Fi en Microsoft Intune)](wi-fi-connections-in-microsoft-intune.md)
-  [VPN connections in Microsoft Intune (Conexiones VPN en Microsoft Intune)](vpn-connections-in-microsoft-intune.md)



<!--HONumber=Jul16_HO4-->


