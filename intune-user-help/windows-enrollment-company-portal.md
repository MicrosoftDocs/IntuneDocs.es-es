---
title: Inscripción de dispositivos Windows en Portal de empresa de Intune | Microsoft Docs
description: Aprenda a inscribir un dispositivo Windows en Portal de empresa
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/24/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 36250832-c6fd-4e8d-b681-de735023ebc3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86aeb2b54d45f111864d71e65b8c90fce7205868
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508029"
---
# <a name="windows-device-enrollment-in-intune-company-portal"></a>Inscripción de dispositivos Windows en Portal de empresa de Intune  

Inscriba un dispositivo Windows en la aplicación Portal de empresa de Intune para obtener acceso seguro a aplicaciones, correos electrónicos y archivos profesionales y educativos. Si la organización necesita o recomienda determinadas aplicaciones, como Office o OneDrive, o bien las recibe durante la inscripción, o bien están disponibles en Portal de empresa tras esta.  

Puede inscribir dispositivos Windows 10 mediante el sitio web *o* la aplicación Portal de empresa. Si va a inscribir un dispositivo con una versión anterior de Windows, debe hacerlo a través del sitio web Portal de empresa.  

## <a name="install-company-portal-app"></a>Instalar la aplicación Portal de empresa  
Es posible que ya tenga la aplicación Portal de empresa instalada en el dispositivo. Búsquela en la lista __Todas las aplicaciones__.  Si no ve el Portal de empresa en la lista de aplicaciones, siga estos pasos para instalarlo.  

1. Abra **Microsoft Store** en el dispositivo.

2. En el campo **Buscar**, escriba **Portal de empresa**.

3. En la lista de resultados, seleccione **Portal de empresa** > **Instalar**.

4. Seleccione **Instalar** o **Gratis**. No hay ninguna diferencia entre estas dos opciones; las palabras aparecen en función de cómo configure la aplicación la organización.  

## <a name="find-windows-10-version-number"></a>Buscar el número de versión de Windows 10  
Los pasos de inscripción varían para las distintas versiones de los dispositivos Windows 10. En los pasos siguientes se explica cómo encontrar el número de versión en dispositivos de escritorio y móviles de Windows 10. Una vez que conozca la versión, continúe con los pasos de inscripción recomendados.  

### <a name="windows-10-desktop-devices"></a>Dispositivos con Windows 10 Escritorio  

1. Vaya a **Inicio**.

2. En la barra de búsqueda, escriba la frase "acerca de tu PC". Seleccione __Acerca de tu PC__ en los resultados.  


   ![configuración para la búsqueda de acerca de tu pc](media/searching_for_about_your_pc.png)  

3. Desplácese hacia abajo hasta **Especificaciones de Windows** para encontrar la **Versión** de Windows 10 instalada en el equipo.  


   ![Acerca del PC en Windows 10 Escritorio](media/settings_about_pc.png)  

4. Si la versión es  

    * __1607 o posteriores__: inscriba el dispositivo mediante la ruta [**Configuración** > **Cuenta** > **Obtener acceso a trabajo o escuela**](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device).   
    * __1511 o anteriores__: inscriba el dispositivo mediante la ruta [**Configuración** > **Cuenta** > **Sus cuentas**](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device).  

### <a name="windows-10-mobile-devices"></a>Dispositivos Windows 10 Mobile

1. Vaya a __Todas las aplicaciones__ y seleccione la aplicación __Configuración__.
2. Seleccione __Sistema__ > __Acerca de__.
3. En __Información del dispositivo__, busque la __Versión__.  
4. Si la versión es  

    * __1607 o posteriores__: inscriba el dispositivo mediante la ruta [**Configuración** > **Obtener acceso a trabajo o escuela**](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device).   
    * __1511 o anteriores__: inscriba el dispositivo mediante la ruta [**Configuración** > **Cuentas**](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device).  

## <a name="enroll-non-windows-10-devices"></a>Inscribir dispositivos que no son Windows 10  
Use los siguientes artículos para inscribir otros dispositivos compatibles con Windows a través del sitio web Portal de empresa:   
* [Dispositivo Windows 8.1 o Windows RT 8.1](enroll-your-W81-or-rt81-windows.md)  
* [Dispositivo Windows Phone 8.1](enroll-your-wp81-windows.md)    

## <a name="it-administrator-support"></a>Soporte técnico para administradores de TI  
Si es administrador de TI y detecta problemas al inscribir dispositivos, vea [Solucionar problemas de inscripción de dispositivos de Windows de Microsoft Intune](https://support.microsoft.com/help/4469913). En este artículo se enumeran errores habituales, sus causas y los pasos para resolverlos.  

## <a name="next-steps"></a>Pasos siguientes  
Ahora que conoce los dispositivos compatibles y el número de versión de Windows 10, continúe con el artículo de inscripción recomendado.  
 
Para obtener más información sobre la administración de dispositivos, Portal de empresa y cómo se usan ambos en organizaciones educativas y profesionales, vea los artículos siguientes:  
* [Uso de dispositivos administrados para acceder a recursos de trabajo o educativos](use-managed-devices-to-get-work-done.md)  
* [¿Qué ocurre si instala la aplicación de Portal de empresa e inscribe el dispositivo Windows en Intune?](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md)  
* [¿Qué información puede ver mi organización cuando inscribo mi dispositivo?](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)  

¿Necesita ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. [Vaya al sitio web Portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980) para buscar la información de contacto de TI de la empresa.  
