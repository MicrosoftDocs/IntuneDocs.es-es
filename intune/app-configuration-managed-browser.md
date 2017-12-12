---
title: "Administración del acceso web con la aplicación Managed Browser"
titlesuffix: Azure portal
description: "Implemente la aplicación Managed Browser para restringir la exploración web y la transferencia de datos de web a otras aplicaciones."
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 11/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1feca24f-9212-4d5d-afa9-7c171c5e8525
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7619efc305881f1ad56a7c14e5d92c05fb0c6d77
ms.sourcegitcommit: 67ec0606c5440cffa7734f4eefeb7121e9d4f94f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2017
---
# <a name="manage-internet-access-using-managed-browser-policies-with-microsoft-intune"></a>Administrar el acceso a Internet mediante directivas de Managed Browser con Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Managed Browser es una aplicación de exploración web que se puede descargar en tiendas de aplicaciones públicas para su uso en una organización. Cuando se configura con Intune, Managed Browser se puede:
- Usar para acceder a sitios corporativos y aplicaciones SaaS con inicio de sesión único a través del servicio MyApps, al tiempo que se mantienen los datos web protegidos.
- Preconfigurar con una lista de direcciones URL y dominios para restringir los sitios a los que el usuario puede ir en el contexto corporativo.
- Preconfigurar con una página principal y los marcadores que especifique.

Como esta aplicación cuenta con integración con el SDK de Intune, también puede aplicarle directivas de protección de aplicaciones, lo que incluye:
- Controlar el uso de cortar, copiar y pegar
- Evitar las capturas de pantalla
- Asegurarse de que los vínculos a contenido que los usuarios seleccionan se abran solo en otras aplicaciones administradas.

Para obtener detalles, vea [¿Qué son las directivas de protección de aplicaciones?](/intune/app-protection-policy)

Puede aplicar esta configuración a:

- Dispositivos móviles inscritos con Intune
- Inscritos con otro producto de MDM
- Dispositivos no administrados

Si los usuarios instalan Managed Browser desde la tienda de aplicaciones y no lo administra Intune, se puede utilizar como un explorador web básico, con compatibilidad para el inicio de sesión único a través del sitio de Microsoft MyApps. A los usuarios se les remite directamente al sitio de MyApps, donde pueden ver todas las aplicaciones SaaS aprovisionadas.
Si Intune no administra Managed Browser, no puede acceder a los datos de otras aplicaciones administradas por Intune. 

Managed Browser no es compatible con el protocolo de cifrado de Capa de sockets seguros versión 3 (SSLv3).

Puede crear directivas de Managed Browser para los siguientes tipos de dispositivo:

-   Dispositivos que ejecutan Android 4 y versiones posteriores

-   Dispositivos que ejecutan iOS 8.0 y versiones posteriores

>[!IMPORTANT]
>A partir de octubre de 2017, la aplicación Intune Managed Browser en dispositivos Android admite solo los dispositivos con Android 4.4 y versiones posteriores. La aplicación Intune Managed Browser en iOS solo admitirá dispositivos con iOS 9.0 y versiones posteriores.
>Las versiones anteriores de iOS y Android podrán seguir usando Intune Managed Browser, pero no podrán instalar nuevas versiones de la aplicación y es posible que no puedan tener acceso a todas las funcionalidades de la aplicación. Le recomendamos que actualice la versión del sistema operativo de estos dispositivos a una que sea compatible.


Intune Managed Browser admite la apertura de contenido web de [partners de aplicaciones de Microsoft Intune](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx).

## <a name="create-a-managed-browser-app-configuration"></a>Establecimiento de una configuración de aplicaciones en Managed Browser

1.  Inicie sesión en el portal de Azure.
2.  Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3.  En la hoja **Aplicaciones móviles** de la lista Administrar, elija **Directivas de configuración de aplicaciones**.
4.  En la hoja **Directivas de configuración de aplicaciones**, elija **Agregar**.
5.  En la hoja **Agregar configuración de aplicaciones**, escriba un **nombre** y una **descripción** opcional para las opciones de configuración de aplicaciones.
6.  En **Tipo de inscripción del dispositivo**, elija **Aplicaciones administradas**.
7.  Seleccione **Elegir aplicaciones obligatorias** y, después, en la hoja **Aplicaciones de destino**, elija **Managed Browser** para iOS, para Android o para ambos.
8.  Elija **Aceptar** para volver a la hoja **Agregar configuración de aplicaciones**.
9.  Elija **Opciones de configuración**. En la hoja **Configuración**, defina los pares de clave y valor para proporcionar configuraciones para Managed Browser. Use las secciones posteriores de este artículo para obtener información sobre los diferentes pares de clave y valor que puede definir.
10. Cuando termine, elija **Aceptar**.
11. En la hoja **Agregar configuración de aplicaciones**, seleccione **Crear**.
12. Se crea la nueva configuración y se muestra en la hoja **Configuración de aplicación**.

>[!IMPORTANT]
>Actualmente, Managed Browser se basa en la inscripción automática. Para que las configuraciones de aplicación se apliquen, ya debe haber otra aplicación administrada mediante directivas de protección de aplicaciones de Intune en el dispositivo.

## <a name="assign-the-configuration-settings-you-created"></a>Asignación de las opciones de configuración creadas

Debe asignar la configuración a los grupos de usuarios de Azure AD. Si ese usuario tiene instalada la aplicación Managed Browser, esta se administra mediante la configuración especificada.

1. En la hoja **Configuración** del panel de administración de aplicaciones móviles de Intune, elija **Configuración de aplicaciones**.
2. En la lista de configuraciones de aplicación, seleccione la que desea asignar.
3. En la siguiente hoja, elija **Grupos de usuarios**.
4. En la hoja **Grupos de usuarios**, seleccione el grupo de Azure AD al que desea asignar la configuración de aplicación y después elija **Aceptar**.


## <a name="how-to-configure-application-proxy-settings-for-the-managed-browser"></a>Cómo configurar el proxy de aplicación para Managed Browser

Intune Managed Browser y el [proxy de aplicación de Azure AD]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) pueden usarse conjuntamente para admitir los siguientes casos de usuarios de dispositivos iOS y Android:

- Un usuario descarga e inicia sesión en la aplicación Microsoft Outlook. Las directivas de protección de aplicaciones de Intune se aplican automáticamente. Cifran los datos guardados e impiden que el usuario transfiera archivos corporativos a ubicaciones o aplicaciones no administradas en el dispositivo. Cuando el usuario hace clic en un vínculo a un sitio de intranet en Outlook, puede especificar que el vínculo se abra en la aplicación Managed Browser en lugar de en otro explorador. Managed Browser reconoce que este sitio de intranet se ha expuesto al usuario a través del proxy de aplicación. El usuario se enruta automáticamente a través del proxy de aplicación, para la autenticación con cualquier autenticación multifactor aplicable, y el acceso condicional antes de llegar al sitio de intranet. Este sitio, que anteriormente no se podía encontrar mientras el usuario fuera remoto, ahora es accesible y el vínculo en Outlook funciona según lo previsto.
- Un usuario remoto abre la aplicación Managed Browser y se desplaza a un sitio de intranet con la dirección URL interna. Managed Browser reconoce que este sitio de intranet se ha expuesto al usuario a través del proxy de aplicación. El usuario se enruta automáticamente a través del proxy de aplicación, para la autenticación con cualquier autenticación multifactor aplicable, y el acceso condicional antes de llegar al sitio de intranet. Este sitio, que anteriormente no se podía encontrar mientras el usuario fuera remoto, ahora es accesible.

### <a name="before-you-start"></a>Antes de empezar

- Configure las aplicaciones internas a través del proxy de aplicación de Azure AD.
    - Para configurar el proxy de aplicación y publicar aplicaciones, vea la [documentación de configuración]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started#how-to-get-started). 
- Debe usar como mínimo la versión 1.2.0 de la aplicación Managed Browser.
- Los usuarios de la aplicación Managed Browser tienen una [directiva de protección de aplicaciones de Intune]( app-protection-policy.md) asignada a la aplicación.
Nota: Los datos de redireccionamiento actualizados del proxy de la aplicación pueden tardar hasta 24 horas en aplicarse en Managed Browser.

#### <a name="step-1-enable-automatic-redirection-to-the-managed-browser-from-outlook"></a>Paso 1: Habilitar el redireccionamiento automático de Managed Browser desde Outlook
Outlook debe configurarse con una directiva de protección de aplicaciones que habilite el valor **Restringir contenido web para mostrar en Managed Browser**.

#### <a name="step-2-assign-an-app-configuration-policy-assigned-for-the-managed-browser"></a>Paso 2: Asignar una directiva de configuración de aplicaciones para Managed Browser.
Este procedimiento configura la aplicación Managed Browser para usar el redireccionamiento del proxy de aplicación. Mediante el procedimiento para establecer una configuración de aplicaciones de Managed Browser, proporcione el siguiente par de clave y valor:

|||
|-|-|
|Key|Valor|
|**com.microsoft.intune.mam.managedbrowser.AppProxyRedirection**|**true**|


## <a name="how-to-configure-the-homepage-for-the-managed-browser"></a>Cómo configurar la página principal de Managed Browser

Este valor permite configurar la página principal que ven los usuarios cuando inician Managed Browser o crean una nueva pestaña. Mediante el procedimiento para establecer una configuración de aplicaciones de Managed Browser, proporcione el siguiente par de clave y valor:

|||
|-|-|
|Key|Valor|
|**com.microsoft.intune.mam.managedbrowser.homepage**|Especifique una dirección URL válida. Las direcciones URL incorrectas se bloquean como medida de seguridad.<br>Ejemplo: **https://www.bing.com**|


## <a name="how-to-configure-bookmarks-for-the-managed-browser"></a>Cómo configurar marcadores de Managed Browser

Este valor permite configurar un conjunto de marcadores disponible para los usuarios de Managed Browser.

- Los usuarios no pueden eliminar ni modificar estos marcadores
- Se muestran en la parte superior de la lista. Los marcadores creados por los usuarios aparecen debajo de estos marcadores.
- Si ha habilitado el redireccionamiento del proxy de aplicación, puede agregar aplicaciones web de proxy de aplicación mediante su dirección URL interna o externa.

Mediante el procedimiento para establecer una configuración de aplicaciones de Managed Browser, proporcione el siguiente par de clave y valor:

|||
|-|-|
|Key|Valor|
|**com.microsoft.intune.mam.managedbrowser.bookmarks**|El valor de esta configuración es una lista de marcadores. Cada marcador consta del título y de la dirección URL del marcador. Separe el título y la dirección URL con el carácter **&#124;**.<br><br>Ejemplo: **Microsoft Bing&#124;https://www.bing.com**<br><br>Para configurar varios marcadores, separe cada par con el carácter doble **&#124;&#124;**<br><br>Ejemplo: **Bing&#124;https://www.bing.com&#124;&#124;Contoso&#124;https://www.contoso.com**|

## <a name="how-to-specify-allowed-and-blocked-urls-for-the-managed-browser"></a>Especificación de direcciones URL permitidas y bloqueadas para Managed Browser

Mediante el procedimiento para establecer una configuración de aplicaciones de Managed Browser, proporcione el siguiente par de clave y valor:

|||
|-|-|
|Key|Valor|
|Elija de entre las siguientes opciones:<br><br>- Especificar direcciones URL permitidas (solo se permiten estas direcciones URL; no se puede acceder a otros sitios): **com.microsoft.intune.mam.managedbrowser.AllowListURLs**<br><br>- Especificar direcciones URL bloqueadas (se puede acceder a todos los demás sitios): <br><br>**com.microsoft.intune.mam.managedbrowser.BlockListURLs**|El valor correspondiente de la clave es una lista de direcciones URL. Escriba todas las direcciones URL que quiera permitir o bloquear como un valor único, separadas por un carácter de barra vertical **&#124;**.<br><br>Ejemplos:<br><br>**URL1&#124;URL2&#124;URL3**<br>**http://*.contoso.com/*&#124;https://*.bing.com/*&#124;https://expenses.contoso.com**|

>[!IMPORTANT]
>No especifique ambas claves. Si las dos claves están destinadas al mismo usuario, se usa la clave permitida, ya que se trata de la opción más restrictiva.
>Además, asegúrese de no bloquear páginas importantes como los sitios web de la empresa.

### <a name="url-format-for-allowed-and-blocked-urls"></a>Formato de dirección URL para las direcciones URL permitidas y bloqueadas
Use la siguiente información para conocer los formatos permitidos y los caracteres comodín que puede usar al especificar direcciones URL en las listas de permitidos y bloqueados:

-   Puede usar el carácter comodín (**&#42;**) según las reglas de la siguiente lista de patrones permitidos:

-   Asegúrese de anteponer **http** o **https** a todas las direcciones URL al introducirlas en la lista.

-   Puede especificar números de puerto en la dirección. Si no especifica un número de puerto, los valores usados son:

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
|http://www.contoso.com:80|Coincide con una sola página, con un número de puerto|http://www.contoso.com:80|
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

## <a name="how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios"></a>Cómo tener acceso a los registros de aplicación administrada con Managed Browser en iOS

Los usuarios finales que tengan Managed Browser instalado en el dispositivo iOS pueden ver el estado de administración de todas las aplicaciones publicadas de Microsoft. También pueden enviar registros para solucionar problemas con sus aplicaciones iOS administradas.

1. Abra la **Configuración** de iOS.
2. Seleccione la configuración de aplicación de del **explorador** administrado.
3. Cambie a **Habilitar diagnósticos de Intune** para establecer el explorador en modo de solución de problemas.
4. Abra el **explorador** administrado. Haga clic en **Ver estado de aplicación Intune** para revisar la configuración de directiva de aplicación individual.
5. Presione **Introducción** y **Compartir registros** o **Enviar registros a Microsoft** para enviar los registros de solución de problemas al administrador de TI o a Microsoft.

También puede abrir el explorador en modo de solución de problemas desde dentro de la aplicación.

1. Abra Managed Browser.
2. Escriba `about:intunehelp` en el cuadro de dirección.
El explorador se abre en modo de solución de problemas.

Para obtener una lista de las opciones de configuración almacenadas en los registros de la aplicación, consulte [Revisión de los registros de protección de aplicaciones en Managed Browser](app-protection-policy-settings-log.md).

## <a name="security-and-privacy-for-the-managed-browser"></a>Seguridad y privacidad de Managed Browser

-   Managed Browser no usa la configuración que realizan los usuarios para el explorador integrado en sus dispositivos. Managed Browser no puede acceder a esta configuración.

-   Si configura las opciones **Requerir PIN sencillo para el acceso** o **Requerir credenciales corporativas para el acceso** en una directiva de protección de aplicaciones asociada a Managed Browser, cuando un usuario seleccione el vínculo de ayuda en la página de autenticación, podrá ir a cualquier sitio de Internet independientemente de si se ha agregado a una lista de bloqueados de la directiva.

-   Managed Browser puede bloquear el acceso a sitios solo cuando se accede a estos directamente. No bloquea el acceso cuando se usan servicios intermedios (por ejemplo, un servicio de traducción) para acceder al sitio.

-   Para permitir la autenticación y acceder a la documentación de Intune, **&#42;.microsoft.com** está exento de la configuración de permitidos o bloqueados. Siempre está permitida.

### <a name="turn-off-usage-data"></a>Desactivar los datos de uso
Microsoft recopila automáticamente datos anónimos sobre el rendimiento y el uso de Managed Browser para mejorar sus productos y servicios. Los usuarios pueden usar en sus dispositivos la configuración de **Datos de uso** para desactivar la recopilación de datos. No tiene ningún control sobre la recopilación de estos datos.


-   En dispositivos iOS, no se pueden abrir los sitios web que visitan los usuarios y que tienen un certificado expirado o que no es de confianza.
-   Managed Browser no usa la configuración que realizan los usuarios para el explorador integrado en sus dispositivos. Managed Browser no puede acceder a esta configuración.

-   Si configura las opciones **Requerir PIN sencillo para el acceso** o **Requerir credenciales corporativas para el acceso** en una directiva de protección de aplicaciones asociada a Managed Browser, cuando un usuario seleccione el vínculo de ayuda en la página de autenticación, podrá ir a cualquier sitio de Internet independientemente de si se ha agregado a una lista de bloqueados de la directiva.

-   Managed Browser puede bloquear el acceso a sitios solo cuando se accede a estos directamente. No bloquea el acceso cuando se usan servicios intermedios (por ejemplo, un servicio de traducción) para acceder al sitio.

-   Para permitir la autenticación y acceder a la documentación de Intune, **&#42;.microsoft.com** está exento de la configuración de permitidos o bloqueados. Siempre está permitida.

### <a name="turn-off-usage-data"></a>Desactivar los datos de uso
Microsoft recopila automáticamente datos anónimos sobre el rendimiento y el uso de Managed Browser para mejorar sus productos y servicios. Los usuarios pueden usar en sus dispositivos la configuración de **Datos de uso** para desactivar la recopilación de datos. No tiene ningún control sobre la recopilación de estos datos.
