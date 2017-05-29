---
title: Administrar el acceso web con Managed Browser | Microsoft Docs
description: "Implemente la aplicación del explorador administrado para restringir la exploración web y la transferencia de datos de web a otras aplicaciones."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc946303-e09b-4d73-8bf4-87742299bc54
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 49ad005846265deb7d4b34b52a1c139e8f61372b
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="manage-internet-access-using-managed-browser-policies-with-microsoft-intune"></a>Administrar el acceso a Internet mediante directivas de explorador administrado con Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

El explorador administrado es una aplicación de exploración web que puede implementar en su organización mediante Microsoft Intune. Una directiva de explorador administrado configura una lista de permitidos o una lista de bloqueados que restringe los sitios web que pueden visitar los usuarios del explorador administrado.

Como esta aplicación cuenta con integración con el SDK de Intune, también puede aplicarle directivas de protección de aplicaciones. Estas directivas pueden controlar el uso de las funciones de cortar, copiar y pegar, impedir la obtención de capturas de pantalla y garantizar que los vínculos al contenido que los usuarios seleccionan se abran solo en otras aplicaciones administradas. Para obtener más información, vea [Configure and deploy mobile application management policies in the Microsoft Intune console (Configurar e implementar directivas de administración de aplicaciones móviles en la consola de Microsoft Intune)](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).

>[!IMPORTANT]
>La aplicación Managed Browser solo recupera y aplica las directivas de protección de aplicaciones de Intune cuando otra aplicación del dispositivo recuperó una directiva de protección de aplicaciones.<br><br> Además, si los usuarios instalan Managed Browser desde la tienda de aplicaciones e Intune no lo administra, se aplica el comportamiento siguiente:<br /><br />
>**iOS**: la aplicación Managed Browser puede usarse como un explorador web básico, pero algunas características no estarán disponibles y no podrá acceder a los datos de otras aplicaciones administradas por Intune.<br />
**Android**: no se puede usar la aplicación Managed Browser.<br /><br />
Si los usuarios instalan el explorador administrado ellos mismos en un dispositivo iOS con una versión anterior a iOS 9, ninguna directiva que usted cree administrará el explorador. Para asegurarse de que Intune administra el explorador, los usuarios deben desinstalar la aplicación antes de que usted pueda implementársela como una aplicación administrada. En iOS 9 y versiones posteriores, si los usuarios instalan el explorador administrado ellos mismos, se les pedirá que permitan que la directiva lo administre.

Puede crear directivas de explorador administrado para los siguientes tipos de dispositivo:

-   Dispositivos que ejecutan Android 4 y versiones posteriores

-   Dispositivos que ejecutan iOS 8.0 y versiones posteriores

Intune Managed Browser admite la apertura de contenido web de [Microsoft Intune application partners](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx) (Partners de aplicaciones de Microsoft Intune).

## <a name="create-a-managed-browser-policy"></a>Crear una directiva de explorador administrado

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), seleccione **Directiva** &gt; **Agregar directiva**.

2.  Configure uno de los siguientes tipos de directivas de **software** :

    -   **Managed Browser (Android 4 y versiones posteriores)**

    -   **Managed Browser (iOS 8.0 y versiones posteriores)**

    Para más información sobre cómo crear e implementar directivas, consulte el tema [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Para configurar las opciones de directiva de explorador administrado, use lo siguiente:

    - **Nombre**. Escriba un nombre único para la directiva de explorador administrado que le ayude a identificarla en la consola de Intune.
    - **Descripción**. Proporcione una descripción que le ofrezca una visión general de la directiva y otra información relevante que le ayude a encontrarla.
    - **Habilitar una lista de permitidos o bloqueados para restringir las direcciones URL que el explorador administrado puede abrir**. Seleccione una de las siguientes opciones:
        - **Permitir al explorador administrado abrir únicamente las direcciones URL siguientes**. Especifique una lista de direcciones URL que el explorador administrado puede abrir.
        - **Bloquear el explorador administrado para que no pueda abrir las direcciones URL siguientes**. Especifique una lista de direcciones URL para las cuales el explorador administrado está bloqueado para que no pueda abrirlas.
**Nota:** No puede incluir direcciones URL permitidas y bloqueadas en la misma directiva de explorador administrado.
Para obtener más información acerca de los formatos de dirección URL que puede especificar, vea **Formato de dirección URL para las direcciones URL permitidas y bloqueadas** en este tema.

4.  Cuando termine, seleccione **Guardar directiva**.

La nueva directiva aparece en el nodo **Directivas de configuración** del área de trabajo **Directiva** .

## <a name="create-a-deployment-for-the-managed-browser-app"></a>Crear una implementación para la aplicación de explorador administrado
Después de crear la directiva de explorador administrado, puede crear una implementación de software para la aplicación de explorador administrado y asociarla a la directiva de explorador administrado que ha creado.

> [!IMPORTANT]
> Las directivas de explorador administrado no se implementan de la misma manera que otras directivas de Intune. Este tipo de directiva debe asociarse con el paquete de software de explorador administrado.

Implemente la aplicación y asegúrese de seleccionar la directiva de explorador administrado en la página **Administración de aplicaciones móviles** para asociar la directiva a la aplicación.

Para obtener más información sobre cómo implementar aplicaciones, vea [Deploy apps in Microsoft Intune (Implementar aplicaciones en Microsoft Intune)](deploy-apps-in-microsoft-intune.md).

## <a name="security-and-privacy-for-the-managed-browser"></a>Seguridad y privacidad del explorador administrado

-   En dispositivos iOS, no se pueden abrir los sitios web que visitan los usuarios y que tienen un certificado expirado o que no es de confianza.

-   El explorador administrado no usa la configuración que realizan los usuarios para el explorador integrado en sus dispositivos. Esto se debe a que el explorador administrado no tiene acceso a esta configuración.

-   Si configura las opciones **Requerir PIN sencillo para el acceso** o **Requerir credenciales corporativas para el acceso** en una directiva de administración de aplicaciones móviles asociada al explorador administrado, cuando un usuario seleccione el vínculo de ayuda en la página de autenticación, dicho usuario podrá examinar los sitios de Internet independientemente de si se han agregado a una lista de bloqueados en la directiva de explorador administrado.

-   El explorador administrado puede bloquear el acceso a sitios solo cuando se accede a estos directamente. No puede bloquear el acceso cuando se usan servicios intermedios (por ejemplo, un servicio de traducción) para acceder al sitio.

-   Para permitir la autenticación y garantizar el acceso a la documentación de Intune, **&#42;.microsoft.com** está exento de la configuración de permitidos o bloqueados. Siempre está permitida.

### <a name="turn-off-usage-data"></a>Desactivar los datos de uso
Microsoft recopila automáticamente datos anónimos sobre el rendimiento y el uso del explorador administrado para mejorar sus productos y servicios. Los usuarios pueden usar en sus dispositivos la configuración de **Datos de uso** para desactivar la recopilación de datos. No tiene ningún control sobre la recopilación de estos datos.

## <a name="reference-information"></a>Información de referencia

### <a name="url-format-for-allowed-and-blocked-urls"></a>Formato de dirección URL para las direcciones URL permitidas y bloqueadas
Use la siguiente información para conocer los formatos permitidos y los caracteres comodín que puede usar al especificar direcciones URL en las listas de permitidos y bloqueados:

-   Puede usar el carácter comodín (**&#42;**) según las reglas de la siguiente lista de patrones permitidos.

-   Asegúrese de anteponer **http** o **https** a todas las direcciones URL al introducirlas en la lista.

-   Puede especificar números de puerto en la dirección. Si no especifica un número de puerto, los valores usados serán:

    -   Puerto 80 para http

    -   Puerto 443 para https

    No se admite el uso de caracteres comodín para el número de puerto. Por ejemplo, **http&colon;//www&period;contoso&period;com:*;** y **http&colon;//www&period;contoso&period;com: /*;** no son compatibles.

-   Use la siguiente tabla para obtener información sobre los patrones permitidos que puede usar al especificar direcciones URL:

|Dirección URL|Detalles|Coincide|No coincide|
    |-------|---------------|-----------|------------------|
    |http://www.contoso.com|Coincide con una sola página|www.contoso.com|host.contoso.com<br /><br />www.contoso.com/images<br /><br />contoso.com/|
    |http://contoso.com|Coincide con una sola página|contoso.com/|host.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com|
    |http://www.contoso.com/&#42;|Coincide con todas las direcciones URL que comienzan con www.contoso.com|www.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com/videos/tvshows|host.contoso.com<br /><br />host.contoso.com/images|
    |http://&#42;.contoso.com/&#42;|Coincide con todos los subdominios en contoso.com|developer.contoso.com/resources<br /><br />news.contoso.com/images<br /><br />news.contoso.com/images|contoso.host.com|
    |http://www.contoso.com/images|Coincide con una sola carpeta|www.contoso.com/images|www.contoso.com/images/dogs|
    |http://www.contoso.com:80|Coincide con una sola página, con un número de puerto|http://www.contoso.com:80||
    |https://www.contoso.com|Coincide con una sola página segura|https://www.contoso.com|http://www.contoso.com|
    |http://www.contoso.com/images/&#42;|Coincide con una sola carpeta y todas sus subcarpetas|www.contoso.com/images/dogs<br /><br />www.contoso.com/images/cats|www.contoso.com/videos|

-   Los siguientes son ejemplos de algunas de las entradas que no se pueden especificar:

    -   &#42;.com

    -   &#42;.contoso/&#42;

    -   www.contoso.com/&#42;images

    -   www.contoso.com/&#42;images&#42;pigs

    -   www.contoso.com/page&#42;

    -   Direcciones IP

    -   https://&#42;

    -   http://&#42;

    -   http://www.contoso.com:&#42;

    -   http://www.contoso.com: /&#42;

### <a name="how-conflicts-between-the-allow-and-block-list-are-resolved"></a>Cómo se resuelven los conflictos entre las listas de permitidos y bloqueados
Si se implementan varias directivas de explorador administrado en un dispositivo y la configuración presenta conflictos, tanto el modo (permitir o bloquear) como las listas de direcciones URL se evalúan para detectar conflictos. En caso de conflicto, se aplica el comportamiento siguiente:

-   Si los modos de cada directiva son iguales, pero las listas de direcciones URL son diferentes, las direcciones URL no se aplicarán en el dispositivo.

-   Si los modos de cada directiva son diferentes, pero las listas de direcciones URL son iguales, las direcciones URL no se aplicarán en el dispositivo.

-   Si un dispositivo está recibiendo las directivas de explorador administrado por primera vez y dos directivas están en conflicto, las direcciones URL no se aplicarán en el dispositivo. Utilice el nodo **Conflictos de directivas** del área de trabajo **Directiva** para ver los conflictos.

-   Si un dispositivo ya ha recibido una directiva de explorador administrado y se implementa una segunda directiva con la configuración en conflicto, la configuración original permanece en el dispositivo. Utilice el nodo **Conflictos de directivas** del área de trabajo **Directiva** para ver los conflictos.

