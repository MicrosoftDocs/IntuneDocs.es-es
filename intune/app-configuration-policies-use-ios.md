---
title: "Agregar directivas de configuración de aplicaciones para dispositivos iOS administrados | Microsoft Docs"
titlesuffix: Azure portal
description: "Obtenga más información sobre cómo usar directivas de configuración de aplicaciones para proporcionar datos de configuración a una aplicación de iOS cuando esta se ejecuta."
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 01/30/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b64d8b60a4c577acc2f6ef161f6de37ac529e7ac
ms.sourcegitcommit: a6fd6b3df8e96673bc2ea48a2b9bda0cf0a875ae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2018
---
# <a name="add-app-configuration-policies-for-managed-ios-devices"></a>Agregar directivas de configuración de aplicaciones para dispositivos iOS administrados

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Use las directivas de configuración de aplicaciones de Microsoft Intune para proporcionar valores de configuración que se emplearán cuando los usuarios ejecuten una aplicación para iOS. No asigne estas directivas directamente a usuarios y dispositivos. Asocie la directiva con una aplicación y, a continuación, asigne la aplicación. La configuración de directivas se usa cada vez que la aplicación la comprueba, que suele ser la primera vez que se ejecuta.

Puede asignar una directiva de configuración de aplicación a un grupo de usuarios y dispositivos mediante una combinación de asignaciones de inclusión y exclusión. Tras agregar una directiva de configuración de aplicación, podrá establecer las asignaciones de la directiva de configuración de aplicación. Al establecer las asignaciones para la directiva, puede elegir si quiere incluir o excluir los grupos de usuarios a los que se aplicará la directiva. Si decide incluir uno o varios grupos, puede optar por seleccionar grupos específicos para incluir o seleccionar los grupos integrados. Los grupos integrados incluyen **Todos los usuarios**, **Todos los dispositivos** y **Todos los usuarios + todos los dispositivos**. 

>[!NOTE]
>Intune ofrece los grupos creados previamente **Todos los usuarios** y **Todos los dispositivos** en la consola con las optimizaciones integradas para su comodidad. Es muy recomendable utilizar estos grupos para segmentar todos los usuarios y todos los dispositivos en lugar de usar cualquier grupo "Todos los usuarios" o "Todos los dispositivos" que haya podido crear.

Una vez haya seleccionado los grupos incluidos para la directiva de configuración de la aplicación, también puede elegir los grupos específicos que quiera excluir.

> [!TIP]
> Este tipo de directiva está disponible solo para dispositivos con iOS 8.0 y versiones posteriores. Admite los siguientes tipos de instalación de la aplicación:
>
> -   **Aplicación iOS administrada desde la tienda de aplicaciones**
> -   **Paquete de aplicación de iOS**
>
> Para más información sobre los tipos de instalación de aplicaciones, consulte [Adición de una aplicación a Microsoft Intune](apps-add.md).

## <a name="create-an-app-configuration-policy"></a>Crear una directiva de configuración de aplicaciones

1. Inicie sesión en Azure Portal.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** + **Intune**.
3. Elija la carga de trabajo **Aplicaciones móviles**.
4. En el grupo **Administrar**, elija **Directivas de configuración de aplicaciones** y **Agregar**.
5. Especifique los siguientes detalles:
    - **Nombre**<br>
      Nombre del perfil que aparecerá en Azure Portal.
    - **Descripción**<br>
      Descripción del perfil que aparecerá en Azure Portal.
    - **Tipo de inscripción del dispositivo**<br>
      Elija **Dispositivos administrados**.
6. En **Plataforma**, seleccione **iOS**.
7.  Elija **Aplicación asociada**. Luego, en la hoja **Aplicación asociada**, elija la aplicación administrada a la que quiera aplicar la configuración.
8.  En la hoja **Agregar directiva de configuración**, elija **Opciones de configuración**.
9. Seleccione **Formato de opciones de configuración**. Seleccione una de las acciones siguientes:
    - **[Usar diseñador de configuraciones](#use-configuration-designer)**
    - **[Especificar datos XML](#enter-xml-data)**
10. Cuando haya agregado la información XML, elija **Aceptar**y elija **Agregar** para agregar la directiva de configuración. Se mostrará la hoja de introducción de la directiva de configuración.
11. Seleccione **Asignaciones** para mostrar las opciones de inclusión y exclusión. 

    ![Asignaciones de directivas](./media/app-config-policy01.png)
12. Seleccione **Todos los usuarios** en la pestaña **Incluir**.

    ![Asignaciones de directivas: todos los usuarios](./media/app-config-policy02.png)
13. Seleccione la pestaña **Excluir**. 
14. Haga clic en **Seleccionar grupos para excluir** para mostrar la hoja relacionada.

    ![Asignaciones de directivas: seleccionar grupos para excluir](./media/app-config-policy03.png)
15. Seleccione los grupos que quiera excluir y después haga clic en **Seleccionar**.

    >[!NOTE]
    >Al agregar un grupo, si ya se ha incluido otro a un tipo de asignación determinado, este se preseleccionará y no se podrá cambiar por otros tipos de asignación de inclusión. Por lo tanto, ese grupo que se ha usado no se puede usar como un grupo de exclusión.
16. Haga clic en **Guardar**.

## <a name="use-configuration-designer"></a>Uso del Diseñador de configuración

El diseñador de configuración se puede usar con las aplicaciones de dispositivos inscritos o no en Intune. El diseñador permite configurar valores y las claves de configuración específicos. También se debe especificar el tipo de datos para cada valor. La configuración se proporciona a las aplicaciones de forma automática cuando se instalan.

### <a name="add-a-setting"></a>Agregar una opción de configuración

1. Para cada clave y valor de la configuración, establezca lo siguiente:
   - **Clave de configuración**<br>
     Clave con la que se identifica de manera única la configuración específica.
   - **Tipo de valor**<br>
     Tipo de datos del valor de configuración. Los tipos pueden ser entero, real, cadena o booleano.
   - **Valor de configuración**<br>
     Se trata del valor de la configuración.
2. Elija **Aceptar** para establecer las opciones de configuración.

### <a name="delete-a-setting"></a>Eliminar una opción de configuración

1. Elija los puntos suspensivos (**...**) junto a la opción de configuración.
2. Seleccione **Eliminar**.

Los caracteres \{\{ y \}\} solo se usan para los tipos de token y no deben usarse para otros fines.

## <a name="enter-xml-data"></a>Especificar datos XML

Puede escribir o pegar una lista de propiedades XML que contenga las opciones de configuración de aplicaciones para dispositivos inscritos en Intune. El formato de la lista de propiedades XML varía según la aplicación que configure. Para obtener más información sobre el formato exacto que debe usar, póngase en contacto con el proveedor de la aplicación.

Intune valida el formato XML, pero no comprueba que la lista de propiedades XML (PList) funcione con la aplicación de destino.

Para obtener más información sobre listas de propiedades XML:

  -  Lea [Configurar aplicaciones de iOS con directivas de configuración de aplicaciones móviles en Microsoft Intune](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).
  -  Vea el artículo [Understand XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) (Descripción de listas de propiedades XML) en la biblioteca para desarrolladores de iOS.

### <a name="example-format-for-an-app-configuration-xml-file"></a>Ejemplo de formato de un archivo XML de configuración de aplicaciones

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
### <a name="supported-xml-plist-data-types"></a>Tipos de datos XML PList admitidos

Intune admite los siguientes tipos de datos en una lista de propiedades:

- &lt;entero&gt;
- &lt;real&gt;
- &lt;cadena&gt;
- &lt;matriz&gt;
- &lt;dict&gt;
- &lt;true /&gt; o &lt;false /&gt;

### <a name="tokens-used-in-the-property-list"></a>Tokens usados en la lista de propiedades

Además, Intune admite los siguientes tipos de token en la lista de propiedades:
- \{\{userprincipalname\}\}. Por ejemplo, **John@contoso.com**
- \{\{mail\}\}**John@contoso.com**
- \{\{partialupn\}\}**John**
- \{\{accountid\}\}**fc0dc142-71d8-4b12-bbea-bae2a8514c81**
- \{\{deviceid\}\}. Por ejemplo, **b9841cd9-9843-405f-be28-b2265c59ef97**
- \{\{userid\}\}. Por ejemplo, **3ec2c00f-b125-4519-acf0-302ac3761822**
- \{\{username\}\}. Por ejemplo, **John Doe**
- \{\{serialnumber\}\}. Por ejemplo, **F4KN99ZUG5V2** (en dispositivos iOS)
- \{\{serialnumberlast4digits\}\}. Por ejemplo, **G5V2** (en dispositivos iOS)

## <a name="next-steps"></a>Pasos siguientes

Siga [asignando](apps-deploy.md) y [supervisando](apps-monitor.md) la aplicación como de costumbre.