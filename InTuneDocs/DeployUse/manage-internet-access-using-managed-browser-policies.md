---
title: Administrar el acceso a Internet mediante directivas de explorador administrado | Microsoft Intune
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc946303-e09b-4d73-8bf4-87742299bc54
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 2df44199ecd904dcfb6774a942244338c1384186
ms.openlocfilehash: c4462af584d54225084159dfa35f5e1d07c36397


---

# Administrar el acceso a Internet mediante directivas de explorador administrado con Microsoft Intune
El explorador administrado es una aplicación de exploración web que se puede implementar en su organización mediante Microsoft Intune. Una directiva de explorador administrado configura una lista de permitidos o una lista de bloqueados que restringe los sitios web que pueden visitar los usuarios del explorador administrado.

Dado que esta aplicación es una aplicación administrada, también puede aplicar las directivas de administración de aplicaciones móviles a la aplicación, tales como controlar el uso de cortar, copiar y pegar, impedir las capturas de pantalla y garantizar que los vínculos a contenido donde los usuarios pueden hacer clic solo se abran en aplicaciones administradas. Para obtener más información, vea [Configure and deploy mobile application management policies in the Microsoft Intune console (Configurar e implementar directivas de administración de aplicaciones móviles en la consola de Microsoft Intune)](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).

> [!IMPORTANT]
>Si los usuarios instalan el explorador administrado desde la tienda de aplicaciones y no se administra mediante Intune, se aplica el siguiente comportamiento: iOS: la aplicación del explorador administrado puede usarse como un explorador web básico, pero algunas características no estarán disponibles y no podrá tener acceso a los datos de otras aplicaciones administradas por Intune.
Android: no se puede usar la aplicación de explorador administrado.
Si los usuarios instalan el explorador administrado ellos mismos en un dispositivo iOS con una versión inferior a iOS 9, no se administrará con las directivas que cree. Para asegurarse de que el explorador se administra mediante Intune, estos deben desinstalar la aplicación para que se la pueda implementar como una aplicación administrada. En iOS 9 y versiones posteriores, si el usuario instala el explorador administrado se le pedirá que permita que sea administrado por la directiva.

Puede crear directivas de explorador administrado para los siguientes tipos de dispositivo:

-   Dispositivos que ejecutan Android 4 y versiones posteriores

-   Dispositivos que ejecutan iOS 7.1 y versiones posteriores

Intune Managed Browser admite la apertura de contenido web de [socios de aplicaciones de Microsoft Intune](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx).

## Crear una directiva de explorador administrado

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), haga clic en **Directiva** &gt; **Agregar directiva**.

2.  Configure uno de los siguientes tipos de directivas de **software** :

    -   **Directiva de explorador administrado (Android 4 y posterior)**

    -   **Directiva de explorador administrado (iOS 7.1 y versiones posteriores)**

    Para más información sobre cómo crear e implementar directivas, consulte el tema [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  La tabla siguiente le facilitará la configuración de directivas de explorador administrado:

|Nombre de la configuración|Detalles|
    |----------------|--------------------|
    |**Nombre**|Escriba un nombre único para la directiva de explorador administrado que le ayude a identificarla en la consola de Intune.|
    |**Descripción**|Proporcione una descripción que le ofrezca una visión general de la directiva y otra información relevante que le ayude a encontrarla.|
    |**Habilitar una lista de permitidos o bloqueados para restringir las direcciones URL que el explorador administrado puede abrir**|Seleccione una de las siguientes opciones:<br /><br />**Permitir al explorador administrado abrir únicamente las direcciones URL de la lista siguiente**: especifique una lista de las direcciones URL que el explorador administrado podrá abrir.<br /><br />**Bloquear el explorador administrado para que no pueda abrir las direcciones URL de la lista siguiente**: especifique una lista de las direcciones URL que el explorador administrado no podrá abrir. **Nota:** No puede incluir direcciones URL permitidas y bloqueadas en la misma directiva de explorador administrado.<br />Para obtener más información acerca de los formatos de dirección URL que puede especificar, vea **Formato de dirección URL para las direcciones URL permitidas y bloqueadas** en este tema.|

4.  Cuando haya terminado haga clic en **Guardar directiva**.

La nueva directiva se muestra en el nodo **Directivas de configuración** del área de trabajo **Directiva** .

## Crear una implementación para la aplicación de explorador administrado
Después de crear la directiva de explorador administrado, puede crear una implementación de software para la aplicación de explorador administrado y asociarla a la directiva de explorador administrado que ha creado.

> [!IMPORTANT]
> Las directivas de explorador administrado no se implementan de la misma manera que otras directivas de Intune. Este tipo de directiva debe asociarse con el paquete de software de explorador administrado.

Implemente la aplicación y asegúrese de seleccionar la directiva de explorador administrado en la página **Administración de aplicaciones móviles** para asociar la directiva a la aplicación.

Para obtener más información sobre cómo implementar aplicaciones, vea [Deploy apps in Microsoft Intune (Implementar aplicaciones en Microsoft Intune)](deploy-apps-in-microsoft-intune.md).

## Seguridad y privacidad del explorador administrado

-   En dispositivos iOS, no se pueden abrir los sitios web que visitan los usuarios y que tienen un certificado expirado o que no es de confianza.

-   El explorador administrado no usa la configuración que realizan los usuarios para el explorador integrado en sus dispositivos. Esto se debe a que el explorador administrado no tiene acceso a esta configuración.

-   Si configura las opciones **Requerir PIN sencillo para el acceso** o **Requerir credenciales corporativas para el acceso** en una directiva de administración de aplicaciones móviles asociada con el explorador administrado, cuando un usuario haga clic en el vínculo de ayuda en la página autenticación, podrá examinar los sitios de Internet independientemente de si se agregaron a una lista de bloqueados en la directiva de explorador administrado.

-   El explorador administrado solo puede bloquear el acceso a sitios cuando se accede a estos directamente. No puede bloquear el acceso cuando se usan servicios intermedios (por ejemplo, un servicio de traducción) para acceder al sitio.

-   Para permitir la autenticación y garantizar el acceso a la documentación de Intune, **&#42;.microsoft.com** está exento de la configuración de permitidos o bloqueados: siempre se permite.

### Desactivar los datos de uso
Microsoft recopila automáticamente datos anónimos sobre el rendimiento y el uso del explorador administrado para mejorar sus productos y servicios, pero los usuarios pueden desactivar la recopilación de datos con la opción **Datos de uso** del dispositivo. No tiene ningún control sobre la recopilación de estos datos.

## Información de referencia

### Formato de dirección URL para las direcciones URL permitidas y bloqueadas
Utilice la siguiente información para conocer los formatos permitidos y los caracteres comodín que puede usar al especificar direcciones URL en las listas de permitidos y bloqueados.

-   Puede usar el carácter comodín "**&#42;**" según las reglas de la siguiente lista de patrones permitidos.

-   Asegúrese de anteponer **http** o **https** a todas las direcciones URL al introducirlas en la lista.

-   Puede especificar números de puerto en la dirección. Si no especifica un número de puerto, los valores usados serán:

    -   Puerto 80 para http

    -   Puerto 443 para https

    No se admite el uso de caracteres comodín para el número de puerto como, por ejemplo, **http&colon;//www&period;contoso&period;com:*;** y **http&colon;//www&period;contoso&period;com: /*;**

-   Utilice la siguiente tabla para obtener información acerca de los patrones permitidos que puede usar al especificar direcciones URL:

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

### Cómo se resuelven los conflictos entre las listas de permitidos y bloqueados
Si se implementan varias directivas de explorador administrado en un dispositivo y la configuración presenta conflictos, tanto el modo (permitir o bloquear) como las listas de direcciones URL se evalúan para detectar conflictos. En caso de conflicto, se aplica el comportamiento siguiente:

-   Si los modos de cada directiva son iguales, pero las listas de direcciones URL son diferentes, las direcciones URL no se aplicarán en el dispositivo.

-   Si los modos de cada directiva son diferentes, pero las listas de direcciones URL son iguales, las direcciones URL no se aplicarán en el dispositivo.

-   Si un dispositivo está recibiendo las directivas de explorador administrado por primera vez y dos directivas están en conflicto, las direcciones URL no se aplicarán en el dispositivo. Utilice el nodo **Conflictos de directivas** del área de trabajo **Directiva** para ver los conflictos.

-   Si un dispositivo ya ha recibido una directiva de explorador administrado y se implementa una segunda directiva con la configuración en conflicto, la configuración original permanece en el dispositivo. Utilice el nodo **Conflictos de directivas** del área de trabajo **Directiva** para ver los conflictos.



<!--HONumber=Jun16_HO4-->


