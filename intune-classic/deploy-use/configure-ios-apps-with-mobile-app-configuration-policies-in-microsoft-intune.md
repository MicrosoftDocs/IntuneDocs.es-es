---
title: "Uso de directivas de configuración de aplicaciones móviles de iOS"
description: "Use las directivas de configuración de aplicaciones móviles de Intune para proporcionar los valores de configuración que podrían ser necesarios cuando los usuarios ejecutan una aplicación iOS."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fc6b645a-e837-4b2a-a10f-144065cbd8dd
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7dd73ecbba6c10cbbec92bdf4e856bf15434aea9
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/15/2017
---
# <a name="configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune"></a>Configurar aplicaciones de iOS con directivas de configuración de aplicaciones móviles en Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Use las directivas de configuración de aplicaciones móviles de Microsoft Intune para proporcionar los valores de configuración que podrían ser necesarios cuando los usuarios ejecutan una aplicación. Por ejemplo, una aplicación puede requerir a los usuarios que especifiquen:

-   Un número de puerto personalizado.

-   Configuración de idioma.

-   Configuración de seguridad.

-   Configuración de marca, como un logotipo de empresa.

Si el usuario ha especificado esta configuración incorrectamente, puede aumentar la carga del departamento de soporte técnico y ralentizar la adopción de nuevas aplicaciones.

Las directivas de configuración de aplicaciones móviles pueden ayudarle a eliminar estos problemas al permitirle implementar esta configuración para los usuarios en una directiva antes de ejecutar la aplicación. A continuación, la configuración se proporciona de forma automática y los usuarios no tienen que realizar ninguna acción.

No implemente estas directivas directamente en usuarios y dispositivos. Asocie la directiva con una aplicación y, a continuación, implemente la aplicación. La configuración de directiva se usará cada vez que la aplicación la compruebe (normalmente, la primera vez que se ejecuta).

> [!TIP]
> Este tipo de directiva está disponible solo para dispositivos con iOS 8.0 y versiones posteriores. Admite los siguientes tipos de instalación de la aplicación:
>
> -   **Aplicación iOS administrada desde la tienda de aplicaciones**
> -   **Paquete de aplicación de iOS**
>
> Para obtener más información sobre los tipos de instalación de aplicaciones, consulte [Deploy apps with Microsoft Intune (Implementar aplicaciones con Microsoft Intune)](deploy-apps.md).

## <a name="configure-a-mobile-app-configuration-policy"></a>Configurar directivas de configuración de aplicaciones móviles

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Directiva** &gt; **Información general** &gt; **Agregar directiva**.

2.  En la lista de directivas, expanda **iOS**, elija **Configuración de la aplicación móvil**, y, a continuación, elija **Crear directiva**.

    > [!TIP]
    > Solo puede configurar una configuración personalizada para este tipo de directiva. La configuración recomendada no está disponible.

3.  En la sección **General** de la página **Crear directiva** , proporcione un nombre y una descripción opcional para la directiva de configuración de aplicaciones móviles.

4.  En la sección **Directiva de configuración de aplicaciones móviles** de la página, en el cuadro, escriba o pegue una lista de propiedades XML que contenga los parámetros de configuración de la aplicación que quiera. El formato de la lista de propiedades XML variará según la aplicación que configure. Para obtener más información sobre el formato exacto que debe usar, póngase en contacto con el proveedor de la aplicación.

    > [!TIP]
    > Para obtener más información acerca de las listas de propiedades XML, vea [Understanding XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) (Descripción de las listas de propiedades XML) en la biblioteca de desarrolladores de iOS.

5.  Haga clic en **Validar** para asegurarse de que el XML que ha escrito tiene un formato de lista de propiedades válido.

    > [!IMPORTANT]
    > Al hacer clic en **Validar**, Intune comprueba que el XML escrito tiene un formato válido. No comprueba que funcione con la aplicación asociada a la lista de propiedades XML.

6.  Cuando haya terminado, haga clic en **Guardar directiva**.

La nueva directiva se muestra en el nodo **Directivas de configuración** .

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

## <a name="associate-a-mobile-app-configuration-policy-with-an-app"></a>Asociar una directiva de configuración de aplicaciones móviles con una aplicación
Después de crear una directiva de configuración de aplicaciones móviles, debe asociarla con la aplicación de iOS a la que desea que se aplique la configuración de la directiva de configuración.

Para ello, siga los pasos para crear una implementación de aplicaciones en [Agregar aplicaciones para dispositivos móviles en Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md) e [Implementar aplicaciones con Microsoft Intune](deploy-apps-in-microsoft-intune.md). Cuando llegue a la página **Configuración de aplicaciones móviles** del asistente, seleccione la directiva que desee asociar a la aplicación de la lista desplegable **Directiva de configuración de aplicaciones**.

A continuación, proceda a implementar y supervisar la implementación de aplicaciones como de costumbre.

Cuando se ejecuta la aplicación implementada en un dispositivo, se ejecutará con los valores configurados en la directiva de configuración de la aplicación móvil.

> [!TIP]
> Si una o varias directivas de configuración de aplicación móvil entra en conflicto, no se aplica ninguna directiva. Se informará del conflicto en el **panel** de la consola de administración de Intune.

## <a name="example-format-for-a-mobile-app-configuration-xml-file"></a>Ejemplo de formato de archivo XML de configuración de aplicaciones móviles

Cuando cree un archivo de configuración de aplicaciones móviles, puede especificar uno o varios de los siguientes valores con este formato:

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
