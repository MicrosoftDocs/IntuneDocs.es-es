---
title: "Configurar aplicaciones de iOS con directivas de configuración de aplicaciones móviles | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fc6b645a-e837-4b2a-a10f-144065cbd8dd
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 42e21b802fb605c98f688485c3b77703b3950e94
ms.openlocfilehash: a1b2fb7f2938939725465a18efb594dda91d16bd


---

# Configurar aplicaciones de iOS con directivas de configuración de aplicaciones móviles en Microsoft Intune
Use las directivas de configuración de aplicaciones móviles de Microsoft Intune para proporcionar los valores de configuración que podrían ser necesarios cuando el usuario ejecuta una aplicación. Por ejemplo, una aplicación puede requerir al usuario que especifique:

-   Un número de puerto personalizado cuando se ejecuta

-   Configuración de idioma

-   Configuración de seguridad

-   Configuración de marca, como un logotipo de empresa

Si el usuario ha introducido esta configuración incorrectamente, puede aumentar la carga del servicio de asistencia técnica y ralentizar la adopción de nuevas aplicaciones.

Las directivas de configuración de aplicaciones móviles pueden ayudarle a eliminar estos problemas al permitirle implementar esta configuración para los usuarios en una directiva antes de ejecutar la aplicación. A continuación, la configuración se proporciona de forma automática y el usuario tiene que realizar ninguna acción.

No implemente estas directivas directamente en usuarios y dispositivos. Asocie la directiva con una aplicación y, a continuación, implemente la aplicación. La configuración de directiva se usará cada vez que la aplicación la compruebe (normalmente, la primera vez que se ejecuta).

> [!TIP]
> Actualmente, este tipo de directiva solo está disponible en dispositivos que ejecutan iOS 7.1 y posterior y admite los siguientes tipos de instalación de aplicaciones:
> 
> -   **Aplicación iOS administrada desde la tienda de aplicaciones**
> -   **Paquete de aplicación de iOS**
> 
> Para obtener más información sobre los tipos de instalación de aplicaciones, consulte [Deploy apps with Microsoft Intune (Implementar aplicaciones con Microsoft Intune)](deploy-apps.md).

## Configurar directivas de configuración de aplicaciones móviles

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), haga clic en **Directiva** &gt; **Información general** &gt; **Agregar directiva**.

2.  En la lista de directivas, expanda **iOS**, haga clic en **Configuración de la aplicación móvil**, y, a continuación, haga clic en **Crear directiva**.

    > [!TIP]
    > Sólo puede configurar una configuración personalizada para este tipo de directiva. La configuración recomendada no está disponible.

3.  En la sección **General** de la página **Crear directiva** , proporcione un nombre y una descripción opcional para la directiva de configuración de aplicaciones móviles.

4.  En la sección **Directiva de configuración de aplicaciones móviles** de la página, escriba o pegue una lista de propiedades XML que contenga los parámetros de configuración de la aplicación que quiera en el cuadro.

    > [!TIP]
    > Para obtener más información acerca de las listas de propiedades XML, vea [Understanding XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) (Descripción de las listas de propiedades XML) en la biblioteca de desarrolladores de iOS.
    > 
    > El formato de la lista de propiedades XML variará según la aplicación que configure. Para obtener más información sobre el formato exacto que debe usar, póngase en contacto con el proveedor de la aplicación.
    > 
    > Intune admite los siguientes tipos de datos en una lista de propiedades:
    > 
    > &lt;integer&gt;
    > &lt;real&gt;
    > &lt;string&gt;
    > &lt;array&gt;
    > &lt;dict&gt;
    > &lt;true /&gt; o &lt;false /&gt;
    > 
    > Para obtener más información acerca de los tipos de datos, vea [About Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/AboutPropertyLists/AboutPropertyLists.html) (Acerca de las listas de propiedades) en la biblioteca de desarrolladores de iOS.
    >
        > Además, Intune admite los siguientes tipos de token en la lista de propiedades:
    >    
    > \{\{userprincipalname\}\} - (Ejemplo: **John@contoso.com**) \{\{mail\}\} - (Ejemplo: **John@contoso.com**) \{\{partialupn\}\} - (Ejemplo: **John**) \{\{accountid\}\} - (Ejemplo: **fc0dc142-71d8-4b12-bbea-bae2a8514c81**) \{\{deviceid\}\} - (Ejemplo: **b9841cd9-9843-405f-be28-b2265c59ef97**) \{\{userid\}\} - (Ejemplo: **3ec2c00f-b125-4519-acf0-302ac3761822**) \{\{username\}\} - (Ejemplo: **John Doe**) \{\{serialnumber\}\} - (Ejemplo: **F4KN99ZUG5V2**) para dispositivos iOS \{\{serialnumberlast4digits\}\} - (Ejemplo: **G5V2**) para dispositivos iOS
>
> Los caracteres \{\{ y \}\} solo se usan para los tipos de token y no deben usarse para otros fines.




5.  Haga clic en **Validar** para asegurarse de que el XML que ha escrito tiene un formato de lista de propiedades válido.

    > [!IMPORTANT]
    > Al hacer clic en **Validar**, Intune comprueba que el XML escrito tiene un formato válido. No comprueba que funcione con la aplicación asociada a la lista de propiedades XML.

6.  Cuando haya terminado, haga clic en **Guardar directiva**.

La nueva directiva se muestra en el nodo **Directivas de configuración** .

## Asociar una directiva de configuración de aplicaciones móviles con una aplicación
Después de crear una directiva de configuración de aplicaciones móviles, debe asociarla con la aplicación de iOS a la que desea que se aplique la configuración de la directiva de configuración.

Para ello, siga los pasos para crear una implementación de aplicaciones en [Add apps for mobile devices in Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md) (Agregar aplicaciones para dispositivos móviles en Microsoft Intune) e [(Deploy apps with Microsoft Intune) Implementar aplicaciones con Microsoft Intune](deploy-apps-in-microsoft-intune.md). Cuando llegue a la página **Configuración de aplicaciones móviles** del asistente, seleccione la directiva que desee asociar a la aplicación de la lista desplegable **Directiva de configuración de aplicaciones**.

A continuación, proceda a implementar y supervisar la implementación de aplicaciones como de costumbre.

Cuando se ejecuta la aplicación implementada en un dispositivo, se ejecutará con los valores configurados en la directiva de configuración de la aplicación móvil.

> [!TIP]
> Si una o varias directivas de configuración de aplicaciones móviles entran en conflicto, no se aplica ninguna de ellas y el conflicto se notifica en el **Panel** de la consola de administración de Intune.

## Ejemplo de formato de archivo XML de configuración de aplicaciones móviles

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





<!--HONumber=Jun16_HO4-->


