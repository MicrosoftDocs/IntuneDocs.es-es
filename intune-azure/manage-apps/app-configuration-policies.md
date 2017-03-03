---
title: "Uso de directivas de configuración de aplicaciones de Intune"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda a usar directivas de configuración de aplicaciones para proporcionar datos de configuración a una aplicación de iOS, cuando se ejecuta."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 73360154765d53fe1f42e4e97699ad9385bfda6f
ms.lasthandoff: 02/18/2017

---

# <a name="how-to-use-microsoft-intune-app-configuration-policies"></a>Uso de directivas de configuración de aplicaciones de Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Use directivas de configuración de aplicaciones de Microsoft Intune para proporcionar valores de configuración que podrían ser necesarios cuando los usuarios ejecutan una aplicación. Por ejemplo, una aplicación puede requerir a los usuarios que especifiquen:

-   Un número de puerto personalizado.

-   Configuración de idioma.

-   Configuración de seguridad.

-   Configuración de marca, como un logotipo de empresa.

Si el usuario ha especificado esta configuración incorrectamente, puede aumentar la carga del departamento de soporte técnico y ralentizar la adopción de nuevas aplicaciones.

Las directivas de configuración de aplicaciones pueden ayudarle a eliminar estos problemas al permitirle asignar esta configuración a los usuarios en una directiva antes de ejecutar la aplicación. A continuación, la configuración se proporciona de forma automática y los usuarios no tienen que realizar ninguna acción.

No asigne estas directivas directamente a usuarios y dispositivos. Asocie la directiva con una aplicación y, a continuación, implemente la aplicación. La configuración de directiva se usará cada vez que la aplicación la compruebe (normalmente, la primera vez que se ejecuta).

> [!TIP]
> Este tipo de directiva está disponible solo para dispositivos con iOS 8.0 y versiones posteriores. Admite los siguientes tipos de instalación de la aplicación:
>
> -   **Aplicación iOS administrada desde la tienda de aplicaciones**
> -   **Paquete de aplicación de iOS**
>
> Para más información sobre los tipos de instalación de aplicaciones, consulte [Adición de una aplicación a Microsoft Intune](/intune-azure/manage-apps/add-apps).

## <a name="create-an-app-configuration-policy"></a>Crear una directiva de configuración de aplicaciones

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
3. En la hoja **Intune**, elija **Administrar aplicaciones**.
1.  En la carga de trabajo **Administrar aplicaciones**, elija **Administrar** > **Directivas de configuración de aplicaciones**.

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

A continuación, siga [asignando](deploy-apps.md) y [supervisando](monitor-apps.md) la aplicación como de costumbre.

Cuando se ejecuta la aplicación asignada en un dispositivo, se ejecutará con las opciones configuradas en la directiva de configuración de aplicaciones.

> [!TIP]
> Si una o varias directivas de configuración de aplicaciones entran en conflicto, no se aplica ninguna directiva.

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

