---
title: Agregar aplicaciones | Microsoft Intune
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b770f4f-6d36-41e4-b535-514b46e29aaa
ms.reviewer: mghadial
ms.suite: ems
ms.sourcegitcommit: f85e91b985d9d30c71dff9e0d910293354fc40b7
ms.openlocfilehash: 119a795697feb0cdbc2b93293cd66df7e77147cf


---

# Agregar aplicaciones con Microsoft Intune
Antes de empezar a implementar aplicaciones con Microsoft Intune, dedique algo de tiempo a familiarizarse con los conceptos presentados en este tema. Así, le será más fácil saber qué aplicaciones se pueden implementar en la plataforma, así como conocer los requisitos previos que deben reunirse para poder hacerlo.

## Tipos de aplicación que se pueden implementar con Intune
Se pueden implementar aplicaciones en todos los tipos de dispositivo compatibles con Intune. Los procesos y dispositivos compatibles variarán dependiendo del tipo de aplicación que quiera implementar. Use la siguiente información para saber qué puede y qué no puede implementarse:


### **Windows Installer (&#42;.exe, &#42;.msi)**
- Este tipo de aplicación debe admitir la instalación silenciosa sin intervención del usuario. La documentación de la aplicación debe incluir las opciones de línea de comandos pertinentes para instalarla de forma silenciosa (por ejemplo, **/q**). Puede encontrar una lista de opciones de línea de comandos habituales [aquí](https://support.microsoft.com/en-us/kb/227091).
- Los archivos y las carpetas adicionales que requiera el programa de instalación de la aplicación deben estar disponibles en la ubicación que se especifique para los archivos de instalación de la aplicación.
- En la mayoría de los casos, los archivos de Windows Installer (.msi) y de revisión de Windows Installer (.msp) no requieren que Intune instale argumentos de línea de comandos. Consulte la documentación de la aplicación. Si es necesario especificar argumentos de línea de comandos, deben escribirse como pares nombre=valor (como, por ejemplo, TRANSFORMS=custom_transform.mst).

Este tipo de aplicación se carga en el espacio de almacenamiento en nube.
### **Paquete de aplicación de Android (archivo &#42;.apk)**
Este tipo de aplicación se carga en el espacio de almacenamiento en nube.
### **Paquete de aplicación de iOS (archivo &#42;.ipa)**
- Para implementar aplicaciones iOS, debe disponer de un paquete .ipa válido.
- El paquete .ipa debe estar firmado por Apple y la fecha de expiración indicada en el perfil de aprovisionamiento debe ser válida. Intune puede distribuir aplicaciones iOS de certificado de empresa. No todas las aplicaciones con certificación de desarrollador de Apple son compatibles.
- Su empresa debe estar registrada en el programa iOS Developer Enterprise Program.
- Asegúrese de que el servidor de seguridad de la organización permite el acceso a los sitios web de certificación y aprovisionamiento de iOS.
- No es necesario implementar un archivo de manifiesto (.plist) junto con la aplicación.

Este tipo de aplicación se carga en el espacio de almacenamiento en nube.

Actualmente, los usuarios finales no pueden instalar aplicaciones corporativas directamente desde la aplicación Portal de empresa de Intune para iOS. Esto es debido a restricciones en las aplicaciones que se publican en el almacén de aplicación de iOS (consulte [instrucciones de revisión de aplicación de tienda](https://developer.apple.com/app-store/review/guidelines/)). Para tener acceso a aplicaciones corporativas (incluidas las aplicaciones administradas del App Store y los paquetes de aplicaciones de línea de negocio), los usuarios pueden iniciar la aplicación Portal de empresa en su dispositivo y pulsar el icono Aplicaciones de la compañía. El explorador se abrirá y los redirigirá al portal web de Intune.

### **Paquete de aplicación de Windows Phone (&#42;.xap, .appx, .appxbundle)**
- Para implementar aplicaciones, necesitará un certificado de firma de código móvil de empresa. Pata obtener detalles, vea [Configurar la administración de Windows Phone con Microsoft Intune](set-up-windows-phone-management-with-microsoft-intune.md).

Este tipo de aplicación se carga en el espacio de almacenamiento en nube.

A continuación encontrará información sobre cómo instalar aplicaciones de línea de negocio de la Plataforma universal de Windows (UWP) con Intune.

### **Paquete de aplicación de Windows (.appx, .appxbundle)**
- Para implementar aplicaciones, necesitará un certificado de firma de código móvil de empresa. Pata obtener detalles, vea [Configurar la administración de dispositivos Windows con Microsoft Intune](set-up-windows-device-management-with-microsoft-intune.md).

Este tipo de aplicación se carga en el espacio de almacenamiento en nube.
### **Windows Installer a través de MDM (&#42;.msi)**
Este tipo de instalador le permite crear e implementar aplicaciones basadas en Windows Installer para PC inscritos que ejecutan Windows 10.<br /><br />Las consideraciones siguientes se aplican cuando se utiliza este tipo de instalador:
- Solo puede cargar un único archivo con la extensión .msi.
- El código de producto y la versión del producto del archivo se usan para la detección de la aplicación.
- Se utilizará el comportamiento de reinicio predeterminado de la aplicación. Intune no controla esto.
- Se instalarán paquetes MSI por usuario para un solo usuario.
- Se instalarán paquetes MSI por máquina para todos los usuarios del dispositivo.
- Actualmente, los paquetes MSI de modo dual solo se instalan para todos los usuarios del dispositivo.
- Se admiten actualizaciones de aplicaciones si el código de producto MSI de cada versión es el mismo.

Este tipo de aplicación se carga en el espacio de almacenamiento en nube.
### **Vínculo externo**
Se usa cuando se tiene:
- Una **dirección URL** que permite a los usuarios descargar una aplicación de la tienda de aplicaciones.
- Un **vínculo** a una aplicación basada en Web que se ejecuta desde el explorador web.

Las aplicaciones basadas en vínculos externos no se almacenan en el espacio de almacenamiento en nube de Intune.
### **Aplicación iOS administrada desde la tienda de aplicaciones**
Permite administrar e implementar aplicaciones iOS gratuitas desde la tienda de aplicaciones. También permite asociar [directivas de administración de aplicaciones móviles](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) a [aplicaciones compatibles](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) y revisar su estado en la consola del administrador.<br /><br />Las aplicaciones iOS administradas no se almacenan en el espacio de almacenamiento en nube de Intune.
> [!TIP] Las opciones para dispositivos móviles no estarán disponibles hasta que [establezca la entidad de administración de dispositivos móviles](get-ready-to-enroll-devices-in-microsoft-intune.md) en Intune.

## El editor de software de Intune
El **editor de software de Microsoft Intune** se inicia al agregar o modificar aplicaciones en la consola de administrador de Microsoft Intune. En este editor se selecciona y configura un tipo de instalador de software que permitirá cargar aplicaciones (programas si son equipos o aplicaciones si son dispositivos móviles) para almacenarlas en el almacenamiento en nube de Intune, o bien vincularlas a una tienda en línea o una aplicación web.

### Requisitos
Antes de empezar a usar el editor de software de Microsoft Intune, es necesario instalar la versión completa de [Microsoft .NET Framework 4.0](https://www.microsoft.com/download/details.aspx?id=17851). Tras instalarlo, puede que tenga que reiniciar el equipo para que el editor de software se abra correctamente.

## Espacio de almacenamiento en nube
Todas las aplicaciones que cree mediante el tipo de instalación del instalador de software (por ejemplo, una aplicación de línea de negocio) se deben empaquetar y cargar en el almacenamiento en la nube de Microsoft Intune. Una suscripción de prueba de Intune incluye 2 gigabytes (GB) de almacenamiento en nube destinados a almacenar actualizaciones y aplicaciones administradas. Una suscripción de pago incluye 20 GB y la posibilidad de adquirir más almacenamiento.

En el nodo **Uso del almacenamiento** del área de trabajo **Administración** puede ver la cantidad de espacio que está usando y adquirir más almacenamiento.

Las siguientes reglas rigen la compra de más almacenamiento en nube para Intune:

-   Debe tener una suscripción de pago activa para poder adquirir almacenamiento adicional.

-   Solo los administradores de facturación o los administradores globales de su servicio de Microsoft Online pueden adquirir almacenamiento adicional a través del portal de administración de Office 365. Para administrar, agregar o eliminar estos administradores, debe ser administrador global e iniciar sesión en el portal de administración de Office 365.

-   Si es un cliente de licencias por volumen que ha adquirido Intune o el complemento de Microsoft Intune a través de un Contrato Enterprise, póngase en contacto con su gestor de cuentas de Microsoft o su partner de Microsoft para obtener información relativa a los precios y para adquirir más almacenamiento.

#### Requisitos de espacio de almacenamiento en nube

-   Asegúrese de que todos los archivos de instalación de la aplicación se encuentran en la misma carpeta.

-   El tamaño máximo de archivo de cualquier archivo que se cargue es de 2 GB.


## Compatibilidad de las aplicaciones de la Plataforma universal de Windows (UWP)
Los equipos con Windows 10 no necesitan una clave de instalación de prueba para instalar las aplicaciones de línea de negocio. Pero la clave del Registro **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Appx\AllowAllTrustedApps** debe tener un valor de **1** para habilitar la instalación de prueba.

Si esta clave del Registro no está configurada, Intune establecerá automáticamente este valor en **1** la primera vez que implemente una aplicación en el dispositivo. Si estableció este valor en **0**, Intune no podrá cambiarlo automáticamente y se producirá un error en la implementación de las aplicaciones de línea de negocio.

Debe firmar las aplicaciones de línea de negocio de la Plataforma universal de Windows con un certificado de firma de código de confianza en cada dispositivo en el que implemente la aplicación. Puede usar certificados de una infraestructura PKI interna o un certificado procedente de un certificado raíz público de terceros instalado en el dispositivo.

En los dispositivos Windows 10 Mobile, puede usar un certificado de firma de código que no sea Symantec para firmar aplicaciones universales con la extensión **.appx**. En cuanto a las aplicaciones **.xap** y los paquetes **.appx** compilados para Windows Phone 8.1 que quiera instalar en dispositivos Windows 10 Mobile, debe usar un certificado de firma de código de Symantec.

## Pasos siguientes 

El siguiente paso será agregar aplicaciones en la consola de Intune para, luego, poder implementarlas. Puede agregar aplicaciones para [dispositivos inscritos](add-apps-for-mobile-devices-in-microsoft-intune.md) o para [PC Windows que se administren con el software cliente de Intune](add-apps-for-windows-pcs-in-microsoft-intune.md).



<!--HONumber=Jun16_HO3-->


