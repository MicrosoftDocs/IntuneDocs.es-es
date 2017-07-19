---
title: "Uso de directivas de configuración de aplicaciones de Intune para iOS"
titleSuffix: Intune on Azure
description: "Aprenda a usar directivas de configuración de aplicaciones para proporcionar datos de configuración a una aplicación de iOS, cuando se ejecuta."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 112f60ff208c27825ddd0f4c812535b255894333
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2017
---
# <a name="how-to-use-microsoft-intune-app-configuration-policies-for-ios"></a>Uso de directivas de configuración de aplicaciones de Microsoft Intune para iOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Use directivas de configuración de aplicaciones de Microsoft Intune para proporcionar valores de configuración que podrían ser necesarios cuando los usuarios ejecutan una aplicación iOS. Por ejemplo, una aplicación puede requerir a los usuarios que especifiquen:

-   Un número de puerto personalizado.

-   Configuración de idioma.

-   Configuración de seguridad.

-   Configuración de marca, como un logotipo de empresa.

Si el usuario ha especificado esta configuración incorrectamente, puede aumentar la carga del departamento de soporte técnico y ralentizar la adopción de nuevas aplicaciones.

Las directivas de configuración de aplicaciones pueden ayudarle a eliminar estos problemas al permitirle asignar esta configuración a los usuarios en una directiva antes de ejecutar la aplicación. A continuación, la configuración se proporciona de forma automática y los usuarios no tienen que realizar ninguna acción.

No asigne estas directivas directamente a usuarios y dispositivos. Asocie la directiva con una aplicación y, a continuación, asigne la aplicación. La configuración de directiva se usará cada vez que la aplicación la compruebe (normalmente, la primera vez que se ejecuta).

> [!TIP]
> Este tipo de directiva está disponible solo para dispositivos con iOS 8.0 y versiones posteriores. Admite los siguientes tipos de instalación de la aplicación:
>
> -   **Aplicación iOS administrada desde la tienda de aplicaciones**
> -   **Paquete de aplicación de iOS**
>
> Para más información sobre los tipos de instalación de aplicaciones, consulte [Adición de una aplicación a Microsoft Intune](apps-add.md).

## <a name="create-an-app-configuration-policy"></a>Crear una directiva de configuración de aplicaciones

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Aplicaciones móviles**.
1.  En la carga de trabajo **Mobile apps**, elija **Administrar** > **Directivas de configuración de aplicaciones**.

2.  En la hoja de lista de directivas, elija **Agregar**.

3.  En la hoja **Agregar directiva de configuración**, proporcione un nombre y una descripción opcional para la directiva de configuración de aplicaciones.
4.  Elija **Aplicación asociada** y, en la hoja **Aplicación asociada**, elija la aplicación administrada a la que quiere aplicar la configuración.
5.  En la hoja **Agregar directiva de configuración**, elija **Configuration settings** (Opciones de configuración) y, luego, en la hoja Configuration Settings (Opciones de configuración), elija cómo quiere especificar los valores XML que conforman el perfil de configuración entre:
    - **Especificar datos XML**: escriba o pegue una lista de propiedades XML que contenga las opciones de configuración de aplicaciones que quiera. El formato de la lista de propiedades XML variará según la aplicación que configure. Para obtener más información sobre el formato exacto que debe usar, póngase en contacto con el proveedor de la aplicación.
    Intune comprueba que el XML especificado está en un formato válido. No comprueba que funcione con la aplicación asociada a la lista de propiedades XML.
    Para obtener más información acerca de las listas de propiedades XML, vea [Understanding XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) (Descripción de las listas de propiedades XML) en la biblioteca de desarrolladores de iOS.
    - **Usar diseñador de configuraciones**: permite especificar pares de clave y valor XML directamente en el portal.
8. Cuando haya terminado, vuelva a la hoja **Agregar directiva de configuración** y presione **Crear**.

La directiva se crea y aparece en la hoja de lista de directivas.

A continuación, siga [asignando](apps-deploy.md) y [supervisando](apps-monitor.md) la aplicación como de costumbre.

Cuando se ejecuta la aplicación asignada en un dispositivo, se ejecutará con las opciones configuradas en la directiva de configuración de aplicaciones.

> [!TIP]
> Si una o varias directivas de configuración de aplicaciones entran en conflicto, no se aplica ninguna directiva.

## <a name="create-a-mam-targeted-configuration-policy"></a>Creación de una directiva de configuración de MAM de destino
La configuración de destino de MAM permite que una aplicación reciba datos de configuración mediante Intune App SDK. El formato y las variantes de estos datos deben definirse y comunicarse a los clientes de Intune mediante el desarrollador o el propietario de la aplicación. Los administradores de Intune pueden dirigirse e implementar los datos de configuración mediante la consola de Azure de Intune. Los datos de configuración de MAM de destino pueden proporcionarse a través del servicio MAM a las aplicaciones con MAM-WE habilitado. Por ejemplo, [Intune Managed Browser](https://docs.microsoft.com/intune/app-configuration-managed-browser) tiene una lista de URL bloqueadas y permitidas. Los datos de configuración de la aplicación se insertan a través del servicio MAM directamente en la aplicación, y no a través del canal de MDM. [Las directivas de configuración de aplicaciones de MDM](https://docs.microsoft.com/intune/app-configuration-policies-use-ios#create-an-app-configuration-policy) son la solución nativa a través de MDM. La diferencia principal con la configuración de MAM de destino es que el dispositivo en que se ejecuta la aplicación no necesita estar inscrito en MDM. La configuración de MAM de destino está disponible en iOS y Android. Para iOS, la aplicación debe haber incorporado Intune APP SDK para iOS (v 7.0.1) y participar en las opciones de configuración de la aplicación. Los pasos para crear una directiva de configuración de MAM de destino son los siguientes: 

1. Inicie sesión en **Azure Portal**.

2. Seleccione **Intune > Mobile Apps - Directivas de configuración de aplicaciones**.

3. En la hoja **Directivas de configuración de aplicaciones**, elija **Agregar**.

4. Escriba un **nombre** y una **descripción** opcional para las opciones de configuración de aplicaciones y seleccione **No inscrito en Intune**.

5. Elija **Elegir aplicaciones obligatorias** y, después, en la hoja de aplicaciones **de destino**, seleccione las aplicaciones para las plataformas deseadas. <br>
**Nota:** Para aplicaciones LOB, seleccione **Más aplicaciones**. Escriba el identificador de paquete para la aplicación.

6. Elija **Aceptar** para volver a la hoja **Agregar configuración de aplicaciones**.

7. Elija **Definir configuración**. En la hoja **Configuración**, defina los pares de clave y valor para proporcionar configuraciones.

8. Cuando termine, elija **Aceptar**.

9. En la hoja **Agregar configuración de aplicaciones**, seleccione **Crear**.

Se crea la nueva configuración y se muestra en la hoja Configuración de aplicación.

A continuación, siga [asignando](apps-deploy.md) y [supervisando](apps-monitor.md) la aplicación como de costumbre.

Cuando se ejecuta la aplicación asignada (integrada en el SDK de aplicaciones de Intune) en un dispositivo, se ejecutará con las opciones configuradas en la directiva de configuración de MAM de destino. La aplicación asignada debe tener integrada la versión compatible del SDK de aplicaciones de Intune. Para obtener más información sobre los requisitos de desarrollo de aplicaciones para usar directivas de configuración de MAM de destino, vea la [guía sobre la integración del SDK de aplicaciones de Intune para iOS](https://docs.microsoft.com/intune/app-sdk-ios).

Para obtener más información sobre las funcionalidades de Graph API en relación con los valores de configuración de destino de MAM, vea la [referencia sobre Graph API para la configuración de destino de MAM](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

## <a name="information-about-the-xml-file-format"></a>Información sobre el formato de archivo XML

Intune admite los siguientes tipos de datos en una lista de propiedades:

- &lt;entero&gt;
- &lt;real&gt;
- &lt;cadena&gt;
- &lt;matriz&gt;
- &lt;dict&gt;
- &lt;true /&gt; o &lt;false /&gt;

Para obtener más información acerca de los tipos de datos, vea [About Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/AboutPropertyLists/AboutPropertyLists.html) (Acerca de las listas de propiedades) en la biblioteca de desarrolladores de iOS.

Además, Intune admite los siguientes tipos de token en la lista de propiedades:
- \{\{userprincipalname\}\} - (Ejemplo: **John@contoso.com**)
- \{\{mail\}\} - (Ejemplo: **John@contoso.com**)
- \{\{partialupn\}\} - (Ejemplo: **Alberto**)
- \{\{accountid\}\} - (Ejemplo: **fc0dc142-71d8-4b12-bbea-bae2a8514c81**)
- \{\{deviceid\}\} - (Ejemplo: **b9841cd9-9843-405f-be28-b2265c59ef97**)
- \{\{userid\}\} - (Ejemplo: **3ec2c00f-b125-4519-acf0-302ac3761822**)
- \{\{username\}\} - (Ejemplo: **Alberto Tercedor**)
- \{\{serialnumber\}\} - (Ejemplo: **F4KN99ZUG5V2**) para dispositivos iOS
- \{\{serialnumberlast4digits\}\} - (Ejemplo: **G5V2**) para dispositivos iOS

Los caracteres \{\{ y \}\} solo se usan para los tipos de token y no deben usarse para otros fines.

## <a name="example-format-for-an-app-configuration-xml-file"></a>Ejemplo de formato de un archivo XML de configuración de aplicaciones

Cuando crea un archivo de configuración de aplicaciones, puede especificar uno o varios de los siguientes valores con este formato:

```
<dict>
  <key>userprincipalname</key>
  <string>{{userprincipalname}}</string>
  <key>mail</key>
  <string>{{mail}}</string>
  <key>partialupn</key>
  <string>{{partialupn}}</string>
  <key>accountid</key>
  <string>{{accountid}}</string>
  <key>deviceid</key>
  <string>{{deviceid}}</string>
  <key>userid</key>
  <string>{{userid}}</string>
  <key>username</key>
  <string>{{username}}</string>
  <key>serialnumber</key>
  <string>{{serialnumber}}</string>
  <key>serialnumberlast4digits</key>
  <string>{{serialnumberlast4digits}}</string>
  <key>udidlast4digits</key>
  <string>{{udidlast4digits}}</string>
</dict>

```
