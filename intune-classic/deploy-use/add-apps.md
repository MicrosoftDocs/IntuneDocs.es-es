---
title: Agregar aplicaciones
description: Antes de empezar a implementar aplicaciones con Intune, dedique algo de tiempo a familiarizarse con los conceptos presentados en este tema.
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 07/13/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2b770f4f-6d36-41e4-b535-514b46e29aaa
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4c455d590c693893edc5e82c01095b9751a8e357
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="add-apps-with-microsoft-intune"></a>Agregar aplicaciones con Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Antes de empezar a implementar aplicaciones con Microsoft Intune, dedique algo de tiempo a familiarizarse con los conceptos presentados en este tema. Estos conceptos le ayudarán a comprender qué aplicaciones puede implementar en cada plataforma. También le ayudarán a comprender los requisitos previos que deben cumplirse antes de implementar las aplicaciones.

## <a name="app-types-that-you-can-deploy"></a>Tipos de aplicación que se pueden implementar

### <a name="software-installer"></a>Instalador de software

|                                  Tipo de aplicación                                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                    Detalles                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|----------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         <strong>Windows Installer (&#42;.exe, &#42;.msi)</strong>          | Este tipo de aplicación debe admitir la instalación silenciosa sin intervención del usuario. La documentación de la aplicación debe incluir las opciones de línea de comandos pertinentes para instalarla de forma silenciosa (por ejemplo, <strong>/q</strong>). Puede encontrar una lista de opciones de línea de comandos comunes en [Modificadores de línea de comandos para la herramienta Microsoft Windows Installer](https://support.microsoft.com/kb/227091).<br><br>Los archivos y las carpetas adicionales que requiere el programa de instalación de la aplicación deben estar disponibles en la ubicación que se especifique para los archivos de instalación de la aplicación.<br><br>En la mayoría de los casos, los archivos de Windows Installer (.msi) y de revisión de Windows Installer (.msp) no requieren que Intune instale argumentos de línea de comandos. Consulte la documentación de la aplicación.<br><br>Si es necesario especificar argumentos de línea de comandos, deben escribirse como pares nombre=valor (como, por ejemplo, TRANSFORMS=custom_transform.mst).<br><br>Este tipo de aplicación solo se aplica a PC que ejecutan el cliente de software de Intune. |
|            <strong>Paquete de aplicación de Android (&#42;.apk)</strong>            |                                                                                                                                                                                                                                                                                                                                                                                                                                          Para implementar aplicaciones Android, debe disponer de un paquete .apk válido.                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|              <strong>Paquete de aplicación de iOS (&#42;.ipa)</strong>              |                                                                                                                                                                            Para implementar aplicaciones iOS, debe disponer de un paquete .ipa válido.<br><br>El paquete .ipa debe estar firmado por Apple y la fecha de expiración en el perfil de aprovisionamiento debe ser válida. Intune puede distribuir aplicaciones iOS de certificado de empresa.<br><br>No todas las aplicaciones con certificación de desarrollador de Apple son compatibles.<br><br>Su empresa debe estar registrada en el programa iOS Developer Enterprise Program.<br><br>Asegúrese de que el servidor de seguridad de la organización permite el acceso a los sitios web de certificación y aprovisionamiento de iOS.<br><br>No es necesario implementar un archivo de manifiesto (.plist) con la aplicación.                                                                                                                                                                             |
| <strong>Paquete de aplicación de Windows Phone (&#42;.xap, .appx, .appxbundle)</strong> |                                                                                                                                                                                                                                                                                                                                                                  Para implementar aplicaciones, necesita un certificado de firma de código móvil de empresa. Para obtener más detalles, consulte [Configurar la administración de Windows Phone con Microsoft Intune](set-up-windows-device-management-with-microsoft-intune.md).                                                                                                                                                                                                                                                                                                                                                                  |
|         <strong>Paquete de aplicación de Windows (.appx, .appxbundle)</strong>          |                                                                                                                                                                                                                                                                                                                                                                 Para implementar aplicaciones, necesita un certificado de firma de código móvil de empresa. Para obtener más detalles, consulte [Configurar la administración de dispositivos Windows con Microsoft Intune](set-up-windows-device-management-with-microsoft-intune.md).                                                                                                                                                                                                                                                                                                                                                                  |
|         <strong>Windows Installer a través de MDM (&#42;.msi)</strong>         |                                                                                             Use esta aplicación para crear e implementar aplicaciones basadas en Windows Installer para PC inscritos que ejecuten Windows 10. Estos equipos se administran a través de la administración de dispositivos móviles (MDM).<br /><br />Solo puede cargar un único archivo con la extensión .msi.<br><br>El código de producto y la versión del producto del archivo se usan para la detección de la aplicación.<br><br>Se utilizará el comportamiento de reinicio predeterminado de la aplicación. Intune no controla este comportamiento.<br><br>Se instalarán paquetes MSI por usuario para un solo usuario.<br><br>Se instalarán paquetes MSI por máquina para todos los usuarios del dispositivo.<br><br>Actualmente, los paquetes MSI de modo dual solo se instalan para todos los usuarios del dispositivo.<br><br>Se admiten actualizaciones de aplicaciones si el código de producto MSI de cada versión es el mismo.<br>                                                                                             |

Todos los tipos de aplicación del instalador de software se cargan en el espacio de almacenamiento en nube.

### <a name="external-link"></a>**Vínculo externo**
Use un vínculo externo cuando tenga:
- Una dirección URL que permite a los usuarios descargar una aplicación de la tienda de aplicaciones.
- Un vínculo a una aplicación basada en Web que se ejecuta desde el explorador web.

Las aplicaciones basadas en vínculos externos no se almacenan en el espacio de almacenamiento en nube de Intune.
### <a name="managed-ios-app-from-the-app-store"></a>**Aplicación iOS administrada desde la tienda de aplicaciones**
Puede usar aplicaciones iOS administradas para administrar e implementar aplicaciones iOS gratuitas desde la tienda de aplicaciones. También puede usar aplicaciones iOS administradas para asociar [directivas de administración de aplicaciones móviles](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) a [aplicaciones compatibles](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx) y revisar su estado en la consola del administrador.<br /><br />Las aplicaciones iOS administradas no se almacenan en el espacio de almacenamiento en nube de Intune.

> [!TIP]
> Las opciones para dispositivos móviles no estarán disponibles hasta que [establezca la entidad de MDM ](prerequisites-for-enrollment.md) en Intune.

## <a name="intune-software-publisher"></a>Editor de software de Intune
El editor de software de Microsoft Intune se inicia al agregar o modificar aplicaciones en la consola de administrador de Intune. En el editor, seleccione y configure un tipo de instalador de software que podrá:

- Cargar aplicaciones (programas para equipos o aplicaciones para dispositivos móviles) para almacenarse en el almacenamiento en nube de Intune.
- Vincular a una tienda en línea o una aplicación web.

Antes de empezar a utilizar el editor de software, debe instalar la versión completa de [Microsoft .NET Framework 4.0](https://www.microsoft.com/download/details.aspx?id=17851). Tras instalarlo, puede que tenga que reiniciar el equipo para que el editor de software se abra correctamente.

## <a name="cloud-storage-space"></a>Espacio de almacenamiento en nube
Todas las aplicaciones que cree con el tipo de instalación del instalador de software se cargan en el almacenamiento en nube de Microsoft Intune. Una suscripción de prueba de Intune incluye 2 gigabytes (GB) de almacenamiento en nube que sirve para almacenar actualizaciones y aplicaciones administradas. Una suscripción completa incluye 20 GB de espacio de almacenamiento.

En el nodo **Uso del almacenamiento** del área de trabajo **Administración** puede ver la cantidad de espacio que está usando. Puede adquirir almacenamiento adicional para Intune mediante el método de compra original.  Si el importe se le ha facturado o lo ha abonado con tarjeta de crédito, visite el [portal de administración de suscripciones](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions).  De lo contrario, póngase en contacto con su asociado o agente de ventas.

Estos son los requisitos de espacio de almacenamiento en la nube:

-   Todos los archivos de instalación deben encontrarse en la misma carpeta.
-   El tamaño máximo de archivo de cualquier archivo que se cargue es de 2 GB.


## <a name="support-for-universal-windows-platform-uwp-apps"></a>Compatibilidad de las aplicaciones de la Plataforma universal de Windows (UWP)
Los equipos con Windows 10 no necesitan una clave de instalación de prueba para instalar las aplicaciones de línea de negocio. Pero la clave del Registro **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Appx\AllowAllTrustedApps** debe tener un valor de **1** para habilitar la instalación de prueba.

Si esta clave del Registro no está configurada, Intune establecerá automáticamente este valor en **1** la primera vez que implemente una aplicación en el dispositivo. Si establece este valor en **0**, Intune no podrá cambiar el valor automáticamente y se producirá un error en la implementación de las aplicaciones de línea de negocio.

Debe firmar las aplicaciones de línea de negocio de la Plataforma universal de Windows con un certificado de firma de código de confianza en cada dispositivo en el que implemente la aplicación. Puede usar certificados de una infraestructura de clave pública interna (PKI) interna o un certificado procedente de un certificado raíz público de terceros instalado en el dispositivo.

En los dispositivos Windows 10 Mobile, puede usar un certificado de firma de código que no sea Symantec para firmar aplicaciones universales con la extensión **.appx**. En cuanto a las aplicaciones **.xap** y los paquetes **.appx** compilados para Windows Phone 8.1 que quiera instalar en dispositivos Windows 10 Mobile, debe usar un certificado de firma de código de Symantec.

### <a name="dependencies-for-uwp-apps"></a>Dependencias de las aplicaciones UWP

Cuando agrega un paquete appxbundle de Windows 10 Universal, también debe asegurarse de que se carguen todas las dependencias de la aplicación.
Para cargar las dependencias, asegúrese de que la carpeta **Dependencias** que se creó cuando se compiló la aplicación están en la misma carpeta que el archivo .appxbundle.
De ese modo, cuando cargue la aplicación en Intune, también se cargarán todos los archivos existentes en la carpeta **Dependencias**. Este proceso se ilustra en la siguiente captura de pantalla:


![Cómo seleccionar dependencias de appxbundle de Windows 10 UWP](./media/w10-dependencies.png)


## <a name="next-steps"></a>Pasos siguientes

Debe agregar aplicaciones a la consola de Intune para poder implementarlas. Puede agregar aplicaciones para [dispositivos inscritos](add-apps-for-mobile-devices-in-microsoft-intune.md) o para [PC Windows que se administren con el software cliente de Intune](add-apps-for-windows-pcs-in-microsoft-intune.md).
