---
title: Agregar directivas de configuración de aplicaciones para dispositivos iOS administrados
titleSuffix: Microsoft Intune
description: Obtenga más información sobre cómo usar directivas de configuración de aplicaciones para proporcionar datos de configuración a una aplicación de iOS cuando esta se ejecuta.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0d4bbd0a5b57391edad726c7e936d0072a791673
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755772"
---
# <a name="add-app-configuration-policies-for-managed-ios-devices"></a>Agregar directivas de configuración de aplicaciones para dispositivos iOS administrados

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Use las directivas de configuración de aplicaciones de Microsoft Intune para proporcionar valores de configuración personalizados para una aplicación para iOS. Estos valores de configuración permiten que una aplicación se personalice según la dirección de los proveedores de las aplicaciones. Debe obtener estos valores de configuración (claves y valores) del proveedor de la aplicación. Para configurar la aplicación, especifique la configuración, como claves y valores, o como XML que contiene las claves y valores.

Como administrador de Microsoft Intune, puede controlar qué cuentas de usuario se agregan a las aplicaciones de Microsoft Office en dispositivos administrados. Puede limitar el acceso solo a las cuentas de usuario de la organización permitidas y bloquear las cuentas personales en los dispositivos inscritos. Las aplicaciones auxiliares procesan la configuración de la aplicación y quitan y bloquean las cuentas no aprobadas. La configuración de directivas de configuración se usa cada vez que la aplicación comprueba dichas directivas, que suele ser la primera vez que se ejecuta.

Tras agregar una directiva de configuración de aplicación, podrá establecer las asignaciones de la directiva de configuración de aplicación. Al establecer las asignaciones de la directiva, puede elegir si quiere incluir o excluir los grupos de usuarios a los que se aplica la directiva. Si decide incluir uno o varios grupos, puede optar por seleccionar grupos específicos para incluir o seleccionar los grupos integrados. Los grupos integrados incluyen **Todos los usuarios**, **Todos los dispositivos** y **Todos los usuarios + todos los dispositivos**. 

> [!NOTE]
> Intune ofrece los grupos creados previamente **Todos los usuarios** y **Todos los dispositivos** en la consola con las optimizaciones integradas para su comodidad. Es muy recomendable utilizar estos grupos para segmentar todos los usuarios y todos los dispositivos en lugar de usar cualquier grupo "Todos los usuarios" o "Todos los dispositivos" que haya podido crear.

Una vez haya seleccionado los grupos incluidos para la directiva de configuración de la aplicación, también puede elegir los grupos específicos que quiera excluir. Para obtener más información, vea [Inclusión y exclusión de asignaciones de aplicaciones en Microsoft Intune](apps-inc-exl-assignments.md).

> [!TIP]
> Este tipo de directiva está disponible solo para dispositivos con iOS 8.0 y versiones posteriores. Admite los siguientes tipos de instalación de la aplicación:
>
> - **Aplicación iOS administrada desde la tienda de aplicaciones**
> - **Paquete de aplicación de iOS**
>
> Para más información sobre los tipos de instalación de aplicaciones, consulte [Adición de una aplicación a Microsoft Intune](apps-add.md). Para más información sobre cómo incorporar la configuración de la aplicación en el paquete de la aplicación .ipa para dispositivos administrados, consulte Configuración de aplicaciones administradas en la [documentación para desarrolladores de iOS](https://developer.apple.com/library/archive/samplecode/sc2279/Introduction/Intro.html).

## <a name="create-an-app-configuration-policy"></a>Crear una directiva de configuración de aplicaciones

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Elija **Aplicaciones** > **Directivas de configuración de aplicaciones** > **Agregar** > **Dispositivos administrados**. Observe que puede elegir entre **Dispositivos administrados** y **Aplicaciones administradas**. Para más información, consulte [Aplicaciones que admiten la configuración de aplicaciones](~/apps/app-configuration-policies-overview.md#apps-that-support-app-configuration).
3. En la página **Aspectos básicos**, establezca los detalles siguientes:
    - **Nombre**: nombre del perfil que aparece en Azure Portal.
    - **Descripción**: descripción del perfil que aparece en Azure Portal.
    - **Tipo de inscripción del dispositivo**: esta configuración está establecida en **Dispositivos administrados**.
4. En **Plataforma**, seleccione **iOS/iPadOS**.
5. Haga clic en **Seleccionar aplicación** junto a **Aplicación de destino**. Se muestra el panel **Aplicación asociada**. 
6. En el panel **Aplicación de destino**, elija la aplicación administrada para asociarla con la directiva de configuración y haga clic en **Aceptar**.
7. Haga clic en **Siguiente** para abrir la página **Configuración**.
8. En el cuadro desplegable, seleccione el **Formato de opciones de configuración**. Seleccione uno de los métodos siguientes para agregar información de la configuración:
    - **Uso del Diseñador de configuración**
    - **Especificar datos XML**<br><br>
    Para obtener más detalles sobre cómo usar el diseñador de configuraciones, vea [Uso del Diseñador de configuración](#use-configuration-designer). Para obtener más detalles sobre cómo escribir datos XML, vea [Especificar datos XML](#enter-xml-data). 
9. Haga clic en **Siguiente** para abrir la página **Asignaciones**.
10. En el cuadro desplegable junto a **Asignar a**, seleccione **Grupos seleccionados**, **Todos los usuarios**, **Todos los dispositivos** o **Todos los usuarios y dispositivos** a la que asignarle la directiva de configuración de aplicación.

    ![Captura de pantalla de la pestaña Incluir de la hoja Asignaciones de la directiva](./media/app-configuration-policies-use-ios/app-config-policy01.png)

11. Seleccione **Todos los usuarios** en el cuadro desplegable.

    ![Captura de pantalla de la opción Todos los usuarios de la lista desplegable de la hoja Asignaciones de la directiva](./media/app-configuration-policies-use-ios/app-config-policy02.png)

12. Haga clic en **Seleccionar grupos para excluir** para mostrar el panel relacionado.

    ![Captura de pantalla del panel Seleccionar grupos para excluir de la página Asignaciones de la directiva](./media/app-configuration-policies-use-ios/app-config-policy03.png)

13. Seleccione los grupos que quiera excluir y después haga clic en **Seleccionar**.

    >[!NOTE]
    >Al agregar un grupo, si ya se ha incluido otro a un tipo de asignación determinado, este se preselecciona y no se puede cambiar por otros tipos de asignación de inclusión. Por lo tanto, ese grupo que se ha usado no se puede usar como un grupo de exclusión.

14. Elija **Siguiente** para mostrar la página **Revisar y crear**.
15. Haga clic en **Crear** para agregar la Ddrectiva de configuración de aplicaciones a Intune.

## <a name="use-configuration-designer"></a>Uso del Diseñador de configuración

Microsoft Intune proporciona opciones de configuración que son únicas para una aplicación. El diseñador de configuración se puede usar con las aplicaciones de dispositivos inscritos o no en Microsoft Intune. El diseñador permite configurar valores y las claves de configuración específicos que le ayuda a crear el XML subyacente. También se debe especificar el tipo de datos para cada valor. Esta configuración se proporciona a las aplicaciones de forma automática cuando se instalan.

### <a name="add-a-setting"></a>Agregar una opción de configuración

1. Para cada clave y valor de la configuración, establezca lo siguiente:
   - **Clave de configuración**: clave con la que se identifica de manera única la configuración específica.
   - **Tipo de valor**: tipo de datos del valor de configuración. Los tipos pueden ser entero, real, cadena o booleano.
   - **Valor de configuración**: valor de la configuración.
2. Elija **Aceptar** para establecer las opciones de configuración.

### <a name="delete-a-setting"></a>Eliminar una opción de configuración

1. Elija los puntos suspensivos ( **...** ) junto a la opción de configuración.
2. Seleccione **Eliminar**.

Los caracteres \{\{ y \}\} solo se usan para los tipos de token y no deben usarse para otros fines.

### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>Permitir solo cuentas de organización configuradas en aplicaciones de varias identidades 

Para dispositivos iOS, use los siguientes pares de clave/valor:

| **Clave** | IntuneMAMAllowedAccountsOnly |
|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Valores** | <ul><li>**Habilitada**: la única cuenta permitida es la cuenta de usuario administrado definida por la clave [IntuneMAMUPN](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm).</li><li>**Deshabilitada** (o cualquier valor que no sea una coincidencia con **Habilitada**, sin distinguir mayúsculas de minúsculas): se permite cualquier cuenta.</li></ul> |.

   > [!NOTE]
   > Debe usar OneDrive para iOS 10.34 o posterior, Outlook para iOS 2.99.0 o posterior o Edge para iOS 44.8.7 o posterior y la aplicación debe ser objeto de [directivas de protección de aplicaciones de Intune](app-protection-policy.md) cuando se permitan solo cuentas de organización configuradas con varias identidades.

## <a name="enter-xml-data"></a>Especificar datos XML

Puede escribir o pegar una lista de propiedades XML que contenga las opciones de configuración de aplicaciones para dispositivos inscritos en Intune. El formato de la lista de propiedades XML varía según la aplicación que configure. Para obtener más información sobre el formato exacto que debe usar, póngase en contacto con el proveedor de la aplicación.

Intune valida el formato XML, pero no comprueba que la lista de propiedades XML (PList) funcione con la aplicación de destino.

Para obtener más información sobre listas de propiedades XML:

- Vea el artículo [Understand XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) (Descripción de listas de propiedades XML) en la biblioteca para desarrolladores de iOS.

### <a name="example-format-for-an-app-configuration-xml-file"></a>Ejemplo de formato de un archivo XML de configuración de aplicaciones

Cuando crea un archivo de configuración de aplicaciones, puede especificar uno o varios de los siguientes valores con este formato:

```xml
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
  <key>aaddeviceid</key>
  <string>{{aaddeviceid}}</string>
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
- \{\{userprincipalname\}\}: por ejemplo, **John\@contoso.com**
- \{\{mail\}\}: por ejemplo, **John\@contoso.com**
- \{\{partialupn\}\}**John**
- \{\{accountid\}\}**fc0dc142-71d8-4b12-bbea-bae2a8514c81**
- \{\{deviceid\}\}. Por ejemplo, **b9841cd9-9843-405f-be28-b2265c59ef97**
- \{\{userid\}\}. Por ejemplo, **3ec2c00f-b125-4519-acf0-302ac3761822**
- \{\{username\}\}. Por ejemplo, **John Doe**
- \{\{serialnumber\}\}. Por ejemplo, **F4KN99ZUG5V2** (en dispositivos iOS)
- \{\{serialnumberlast4digits\}\}. Por ejemplo, **G5V2** (en dispositivos iOS)
- \{\{aaddeviceid\}\}: por ejemplo, **ab0dc123-45d6-7e89-aabb-cde0a1234b56**

## <a name="configure-the-company-portal-app-to-support-ios-dep-devices"></a>Configuración de la aplicación Portal de empresa para que admita dispositivos iOS DEP

Las inscripciones de DEP (Programa de inscripción de dispositivos de Apple) no son compatibles con la versión de App Store de la aplicación Portal de empresa. Sin embargo, puede configurar la aplicación Portal de empresa para que admita dispositivos iOS DEP mediante los pasos siguientes.

1. En Intune, agregue la aplicación Portal de empresa de Intune si es necesario; para ello, vaya a **Intune** > **Aplicaciones** > **Todas las aplicaciones** > **Agregar**.
2. Vaya a **Aplicaciones** > **Directivas de configuración de aplicaciones** para crear una directiva de configuración de aplicaciones para la aplicación Portal de empresa.
3. Cree una directiva de configuración de aplicaciones con el código XML siguiente. Puede encontrar más información sobre cómo crear una directiva de configuración de aplicaciones y escribir datos XML en [Agregar directivas de configuración de aplicaciones para dispositivos iOS administrados](app-configuration-policies-use-ios.md).

    ``` xml
    <dict>
        <key>IntuneCompanyPortalEnrollmentAfterUDA</key>
        <dict>
            <key>IntuneDeviceId</key>
            <string>{{deviceid}}</string>
            <key>UserId</key>
            <string>{{userid}}</string>
        </dict>
    </dict>
    ```

3. Implemente el Portal de empresa en dispositivos con la directiva de configuración de aplicaciones destinada a grupos deseados. Asegúrese de implementar solo la directiva en grupos de dispositivos que ya están inscritos en DEP.
4. Indique a los usuarios finales que inicien sesión en la aplicación Portal de empresa cuando se instale automáticamente.

## <a name="monitor-ios--app-configuration-status-per-device"></a>Supervisar el estado de configuración de aplicaciones iOS por dispositivo 
Una vez que se ha asignado una directiva de configuración, puede supervisar el estado de configuración de aplicaciones iOS de cada dispositivo administrado. Desde **Microsoft Intune** en Azure Portal, seleccione **Dispositivos** > **Todos los dispositivos**. En la lista de dispositivos administrados, seleccione un dispositivo específico para mostrar un panel para el dispositivo. En el panel del dispositivo, seleccione **Configuración de aplicaciones**.  

## <a name="additional-information"></a>Información adicional

- [Implementación de las opciones de configuración de la aplicación de Outlook para iOS y Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)

## <a name="next-steps"></a>Pasos siguientes

Siga [asignando](apps-deploy.md) y [supervisando](apps-monitor.md) la aplicación.
