---
title: "Uso de directivas de configuración de aplicaciones de Intune para iOS"
titlesuffix: Azure portal
description: "Aprenda a usar directivas de configuración de aplicaciones para proporcionar datos de configuración a una aplicación de iOS, cuando se ejecuta."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/26/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bc42f3cafa83b5f7ba053d03dbd066b725bb1fee
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-use-microsoft-intune-app-configuration-policies-for-ios"></a>Uso de directivas de configuración de aplicaciones de Microsoft Intune para iOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Utilice las directivas de configuración de aplicaciones de Microsoft Intune para proporcionar valores de configuración que se emplearán cuando los usuarios ejecuten una aplicación para iOS. Por ejemplo, una aplicación puede requerir a los usuarios que especifiquen:

-   Un número de puerto personalizado.

-   Configuración de idioma.

-   Configuración de seguridad.

-   Configuración de marca, como un logotipo de empresa.

Si los usuarios han especificado esta configuración incorrectamente, puede aumentar la carga del departamento de soporte técnico y ralentizar la adopción de nuevas aplicaciones.

Las directivas de configuración de aplicaciones pueden ayudarle a eliminar estos problemas al permitirle asignar esta configuración a los usuarios en una directiva antes de ejecutar la aplicación. A continuación, la configuración se proporciona de forma automática y los usuarios no tienen que realizar ninguna acción. Las aplicaciones deben haberse escrito para admitir el uso de configuraciones de aplicaciones. Consulte con el proveedor de su aplicación para obtener más información.

No asigne estas directivas directamente a usuarios y dispositivos. Asocie la directiva con una aplicación y, a continuación, asigne la aplicación. La configuración de directiva se usará cada vez que la aplicación la compruebe (normalmente, la primera vez que se ejecuta).

> [!TIP]
> Este tipo de directiva está disponible solo para dispositivos con iOS 8.0 y versiones posteriores. Admite los siguientes tipos de instalación de la aplicación:
>
> -   **Aplicación iOS administrada desde la tienda de aplicaciones**
> -   **Paquete de aplicación de iOS**
>
> Para más información sobre los tipos de instalación de aplicaciones, consulte [Adición de una aplicación a Microsoft Intune](apps-add.md).

## <a name="create-an-app-configuration-policy"></a>Crear una directiva de configuración de aplicaciones
1.  Inicie sesión en el portal de Azure.
2.  Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3.  En la hoja **Intune**, elija **Aplicaciones móviles**.
4.  En la carga de trabajo **Mobile apps**, elija **Administrar** > **Directivas de configuración de aplicaciones**.
5.  En la hoja de lista de directivas, elija **Agregar**.
6.  En la hoja **Agregar directiva de configuración**, proporcione un **nombre** y una **descripción** opcional para la directiva de configuración de aplicaciones.
7.  Elija una de las siguientes opciones para **Tipo de inscripción del dispositivo**:
    - **Inscrito en Intune**: para aplicaciones que se administran mediante Intune.
    - **No inscrito en Intune**: para las aplicaciones que no se administran mediante Intune, o que se administran mediante otra solución.
8.  Para **Plataforma**, elija **iOS** (solo para dispositivos inscritos en Intune).
9.  Elija **Aplicación asociada** y, en la hoja **Aplicación asociada**, elija la aplicación administrada a la que quiere aplicar la configuración.
10. En la hoja **Agregar directiva de configuración**, elija **Opciones de configuración**.
11. En la hoja **Opciones de configuración**, elija cómo quiere especificar los valores XML que conforman el perfil de configuración entre una de estas opciones:
    - **Especificar datos XML** (solo para dispositivos inscritos en Intune): escriba o pegue una lista de propiedades XML que contenga las opciones de configuración de aplicaciones que quiera. El formato de la lista de propiedades XML varía según la aplicación que configure. Para obtener más información sobre el formato exacto que debe usar, póngase en contacto con el proveedor de la aplicación.
Intune comprueba que el XML especificado está en un formato válido. No comprueba que funcione con la aplicación asociada a la lista de propiedades XML.
Para obtener más información acerca de las listas de propiedades XML, vea [Understanding XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) (Descripción de las listas de propiedades XML) en la biblioteca de desarrolladores de iOS.
    - **Usar diseñador de configuraciones** (no importa si el dispositivo está inscrito en Intune o no): permite especificar pares de clave y valor XML directamente en el portal.
11. Cuando haya terminado, vuelva a la hoja **Agregar directiva de configuración** y presione **Crear**.

La directiva se crea y aparece en la hoja de lista de directivas.



>[!Note]
>Puede usar [Intune App SDK](https://docs.microsoft.com/intune/app-sdk-ios) para preparar las aplicaciones de línea de negocio que se administrarán mediante las directivas de protección de aplicaciones de Intune y las directivas de configuración de aplicaciones, con independencia de que el dispositivo esté inscrito en Intune o no. Por ejemplo, puede usar una directiva de configuración de aplicaciones con el fin de configurar direcciones URL permitidas y bloqueadas para [Intune Managed Browser](app-configuration-managed-browser.md). Cuando una aplicación sea compatible con estas directivas, podrá configurarlas utilizando una directiva.


Cuando se ejecuta la aplicación asignada en un dispositivo, lo hará con las opciones configuradas en la directiva de configuración de aplicaciones.
Consulte la documentación de la aplicación que está configurando para obtener información sobre lo que ocurre si una o varias directivas de configuración de aplicaciones entra en conflicto.

>[!Tip]
>Además, puede usar API Graph para realizar estas tareas. Para obtener más información, consulte la [referencia sobre API Graph para la configuración de destino de MAM](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).


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

## <a name="next-steps"></a>Pasos siguientes

Siga [asignando](apps-deploy.md) y [supervisando](apps-monitor.md) la aplicación como de costumbre.