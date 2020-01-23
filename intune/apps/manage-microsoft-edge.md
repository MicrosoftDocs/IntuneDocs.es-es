---
title: Administración de Microsoft Edge para iOS y Android con Intune
titleSuffix: ''
description: Use las directivas de protección de aplicaciones de Intune con Microsoft Edge para garantizar que siempre se apliquen medidas de seguridad al acceder a los sitios web corporativos.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3fb2f050-ec94-42ab-be05-c3d4101148bb
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e64741a92804ec4149b654480166720ff3092e35
ms.sourcegitcommit: 665be113b593c3bc7d46b99599e720f781037dcf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2020
ms.locfileid: "76258502"
---
# <a name="manage-web-access-by-using-microsoft-edge-with-microsoft-intune"></a>Administración del acceso web mediante Microsoft Edge con Microsoft Intune

Usar las directivas de protección de aplicaciones de Intune con Microsoft Edge puede garantizar que siempre se apliquen medidas de seguridad al acceder a los sitios web corporativos. Están disponibles las características empresariales de Microsoft Edge siguientes habilitadas por directivas de Intune:

- **Identidad dual.** Los usuarios pueden agregar una cuenta profesional, así como una cuenta personal, para realizar la exploración. Hay una separación total entre ambas identidades, que es similar a la arquitectura y experiencia existente en Office 365 y Outlook. Los administradores de Intune pueden establecer las directivas deseadas para lograr una experiencia de exploración protegida en de la cuenta profesional.
- **Integración de la directiva de protección de aplicaciones de Intune.** Como Microsoft Edge está integrado con el SDK de Intune, puede aplicar directivas de protección de aplicaciones para evitar la pérdida de datos. Estas características incluyen el control de las funciones de cortar, copiar y pegar, impedir la obtención de capturas de pantalla y garantizar que los vínculos seleccionados por los usuarios se abran solo en otras aplicaciones administradas.
- **Integración de Azure Application Proxy.** Puede controlar el acceso a las aplicaciones de software como servicio (SaaS) y las aplicaciones web. Esto ayuda a garantizar que las aplicaciones basadas en el explorador solo se ejecuten en el explorador seguro de Microsoft Edge, tanto si los usuarios finales se conectan desde la red corporativa como si lo hacen desde Internet.
- **Configuración de la aplicación.** Puede usar los valores de configuración de la aplicación para reforzar el posicionamiento de seguridad de su organización y configurar características fáciles de usar para los usuarios finales. Por ejemplo, puede definir marcadores, accesos directos en la página principal, sitios web permitidos y bloqueados, así como Azure Active Directory (Azure AD) Application Proxy.

Las directivas de protección de Microsoft Intune para Microsoft Edge ayudan a proteger los datos y los recursos de su organización. Usar estas directivas con Microsoft Edge garantiza la protección de los recursos de la empresa no solo dentro de las aplicaciones instaladas de manera nativa, sino también cuando se accede a ellas desde el explorador web.

## <a name="getting-started"></a>Introducción

Tanto usted como los usuarios finales pueden descargar Microsoft Edge desde tiendas de aplicaciones públicas para usarlo en sus organizaciones. Para cumplir con los requisitos de sistema operativo para las directivas de explorador, se ha de disponer de cualquiera de los siguientes:
- Android 4 y versiones posteriores
- iOS 8.0 y versiones posteriores

## <a name="application-protection-policies-for-microsoft-edge"></a>Directivas de protección de aplicaciones para Microsoft Edge

Como Microsoft Edge está integrado con el SDK de Intune, puede aplicarles directivas de protección de aplicaciones.

Puede aplicar esta configuración a:
- Dispositivos móviles inscritos con Intune.
- Dispositivos inscritos con otro producto de administración de dispositivos móviles.
- Dispositivos no administrados.

Si la directiva de Intune no se dirige a Microsoft Edge, los usuarios no podrán usarlo para acceder a datos de otras aplicaciones administradas por Intune, como aplicaciones de Office. 

## <a name="conditional-access-for-microsoft-edge"></a>Acceso condicional para Microsoft Edge

Puede usar el acceso condicional de Azure AD para redirigir a los usuarios para que accedan a contenido corporativo solo a través de Microsoft Edge. Esto restringe el acceso de explorador móvil de las aplicaciones web conectadas a Azure AD a Microsoft Edge protegido por directivas. Esto bloquea el acceso desde cualquier otro explorador no protegido, como Safari o Chrome. Puede aplicar el acceso condicional a recursos de Azure como Exchange Online y SharePoint Online, el Centro de administración de Microsoft 365 e, incluso, a sitios locales que estén expuestos a usuarios externos a través de [Azure AD Application Proxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started).

Para restringir el uso de Microsoft Edge en iOS y Android por parte de las aplicaciones web conectadas a Azure AD, realice lo siguiente:
1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. En el nodo de Intune, seleccione **Acceso condicional** > **Nueva directiva**.
3. Seleccione **Conceder** en la sección **Controles de acceso** del panel.
4. Seleccione **Requerir aplicación cliente aprobada**.
5. Elija **Seleccionar** en el panel **Conceder**. Esta directiva se debe asignar a las aplicaciones en la nube que quiera que estén accesibles a únicamente la aplicación Intune Managed Browser.

    ![Captura de pantalla de la directiva de acceso condicional: concesión](./media/manage-microsoft-edge/manage-microsoft-edge-01.png)

6. En la sección Asignaciones, seleccione **Condiciones** > **Aplicaciones**. Aparece el panel **Aplicaciones**.
7. En **Configurar**, seleccione **Sí** para aplicar la directiva a aplicaciones cliente específicas.
8. Compruebe que **Explorador** está seleccionado como aplicación cliente.

    ![Captura de pantalla de la directiva de acceso condicional: selección de las aplicaciones cliente](./media/manage-microsoft-edge/manage-microsoft-edge-02.png)

    > [!NOTE]
    > Si quiere restringir qué aplicaciones nativas (aplicaciones que no son de explorador) pueden tener acceso a estas aplicaciones en la nube, también puede seleccionar **Aplicaciones móviles y aplicaciones de escritorio**.

9. En la sección **Asignaciones**, seleccione **Usuarios y grupos** y, después, elija los usuarios o grupos a los que quiera asignar esta directiva.

10. En la sección **Asignaciones**, seleccione **Aplicaciones en la nube** para elegir las aplicaciones que se van a proteger con esta directiva.

Una vez configurada la directiva, los usuarios deben usar obligatoriamente Microsoft Edge para acceder a las aplicaciones web conectadas a Azure AD que estén protegidas con dicha directiva. Si los usuarios intentan usar un explorador no administrado en este escenario, recibirán un mensaje en el que se les indicará que deben usar Microsoft Edge.

> [!TIP]
> Acceso condicional es una tecnología de Azure AD. El nodo de acceso condicional al que se accede desde Intune es el mismo nodo al que se accede desde Azure AD.

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>Inicio de sesión único en aplicaciones web conectadas a Azure AD en exploradores protegidos por directivas

Microsoft Edge en iOS y Android puede aprovechar el inicio de sesión único (SSO) en todas las aplicaciones web (SaaS y locales) que estén conectadas a Azure AD. Con el inicio de sesión único, los usuarios pueden acceder a aplicaciones web conectadas a Azure AD a través de Microsoft Edge sin tener que volver a introducir sus credenciales.

Para el inicio de sesión único es necesario que el dispositivo esté registrado con la aplicación Microsoft Authenticator para dispositivos iOS o con el Portal de empresa de Intune en Android. Cuando los usuarios hayan realizado una de estas dos acciones, se les pedirá que registren su dispositivo cuando vayan a una aplicación web conectada a Azure AD en un explorador protegido por directivas. Esto solo ocurrirá si su dispositivo no se ha registrado ya. Una vez que el dispositivo esté registrado con la cuenta del usuario administrada por Intune, esa cuenta tendrá el inicio de sesión único habilitado en las aplicaciones web conectadas a Azure AD.

> [!NOTE]
> El registro de dispositivos consiste en un sencillo registro en el servicio de Azure AD. No se requiere una inscripción de dispositivo completa ni se otorga a TI ningún tipo de privilegio extra en el dispositivo.

## <a name="create-a-protected-browser-app-configuration"></a>Establecimiento de una configuración de aplicaciones de explorador protegido

Para crear la configuración de la aplicación para Microsoft Edge:

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Aplicaciones** > **Directivas de configuración de aplicaciones** > **Agregar**.
3. En el panel **Agregar directiva de configuración**, escriba un **nombre** y una **descripción** opcional para las opciones de configuración de aplicaciones.
4. En **Tipo de inscripción del dispositivo**, elija **Aplicaciones administradas**.
5. Elija **Seleccionar la aplicación requerida**. A continuación, en el panel **Aplicaciones de destino**, elija **Managed Browser** o **Edge** para iOS, para Android o para ambos.
6. Seleccione **Aceptar** para volver al panel **Agregar directiva de configuración**.
7. Seleccione **Opciones de configuración**. En el panel **Configuración**, defina los pares clave-valor para proporcionar configuraciones para Microsoft Edge. Use las secciones posteriores de este artículo para obtener información sobre los diferentes pares de clave y valor que puede definir.

    > [!NOTE]
    > Microsoft Edge usa los mismos pares de clave y valor que Managed Browser. En Android, Microsoft Edge debe ser el destino de las directivas de protección de aplicaciones para que las directivas de configuración de aplicaciones surtan efecto.

8. Cuando haya terminado, seleccione **Aceptar**.
9. En el panel **Agregar directiva de configuración**, elija **Agregar**.<br>
    Se crea la configuración y se muestra en el panel **Configuración de aplicaciones**.

## <a name="assign-the-configuration-settings-you-created"></a>Asignación de las opciones de configuración creadas 

Debe asignar la configuración a los grupos de usuarios en Azure AD. Si ese usuario tiene instalada la aplicación de explorador protegido, esta se administra mediante la configuración especificada.

1. En el panel **Aplicaciones** del panel de administración de aplicaciones móviles de Intune, seleccione **Directivas de configuración de aplicaciones**.
2. En la lista de configuraciones de aplicación, seleccione la que desea asignar.
3. En el siguiente panel, seleccione **Asignaciones**.
4. En el panel **Asignaciones**, seleccione el grupo de Azure AD al que quiere asignar la configuración de aplicación y, después, seleccione **Aceptar**.

## <a name="direct-users-to-microsoft-edge-instead-of-the-intune-managed-browser"></a>Dirección de los usuarios a Microsoft Edge en vez de a Intune Managed Browser 

Ahora, tanto Intune Managed Browser como Microsoft Edge se pueden usar como exploradores administrados por directivas. Para asegurarse de que se está dirigiendo a los usuarios para que usen la aplicación de explorador correcta, dirija todas las aplicaciones administradas por Intune (por ejemplo, Outlook, OneDrive y SharePoint) con la opción de configuración siguiente:

|    Key    |    Valor    |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.useEdge`    |    El valor `true` dirigirá a los usuarios a descargar y usar Microsoft Edge.<br>El valor `false` permitirá que los usuarios usen Intune Managed Browser.    |

Si **no** se establece este valor de configuración de la aplicación, la lógica siguiente definirá qué explorador se usará para abrir vínculos corporativos.

En Android:
- Intune Managed Browser se inicia si un usuario tiene Intune Managed Browser y Microsoft Edge descargados en el dispositivo. 
- Microsoft Edge se inicia solo si Intune Microsoft Edge se descarga en el dispositivo y es el objetivo de la directiva.
- Managed Browser se inicia solo si se encuentra en el dispositivo y es el objetivo de la directiva de Intune.

En iOS, para aplicaciones que tienen integrado el SDK de Intune para iOS versión 9.0.9+:
- Intune Managed Browser se inicia si Intune Managed Browser y Microsoft Edge se encuentran en el dispositivo.  
- Microsoft Edge se inicia solo si Microsoft Edge se encuentra en el dispositivo y es el objetivo de la directiva de Intune.
- Managed Browser se inicia solo si se encuentra en el dispositivo y es el objetivo de la directiva de Intune.

## <a name="configure-application-proxy-settings-for-microsoft-edge"></a>Configuración de los valores del proxy de aplicación para Microsoft Edge

Puede usar Microsoft Edge y [Azure AD Application Proxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) conjuntamente para proporcionar a los usuarios acceso a sitios de la intranet desde sus dispositivos móviles. 

Estos son algunos ejemplos de los escenarios que Azure AD Application Proxy permite: 

- Un usuario está utilizando la aplicación móvil de Outlook, que está protegida por Intune. El usuario hace clic en un vínculo de un correo electrónico que dirige a un sitio de la intranet y Microsoft Edge reconoce que dicho sitio se ha expuesto al usuario a través del proxy de aplicación. El usuario se enruta automáticamente a través del proxy de aplicación para que se autentique con una autenticación multifactor y un acceso condicional antes de llegar al sitio de la intranet. Ahora el usuario puede acceder a sitios internos incluso desde sus dispositivos móviles y el vínculo de Outlook funciona según lo previsto.
- Un usuario abre Microsoft Edge en su dispositivo iOS o Android. Si Microsoft Edge está protegido con Intune y el proxy de aplicación está habilitado, el usuario puede ir a un sitio de la intranet mediante la URL interna como de costumbre. Microsoft Edge reconoce que este sitio de intranet se ha expuesto al usuario a través del proxy de aplicación. El usuario se enruta automáticamente a través del proxy de aplicación para autenticarse antes de llegar al sitio de la intranet. 

### <a name="before-you-start"></a>Antes de empezar

- Configure las aplicaciones internas a través de Azure AD Application Proxy.
  - Para configurar el proxy de aplicación y publicar aplicaciones, vea la [documentación de configuración](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).
- La aplicación de Microsoft Edge debe tener asignada la [directiva de protección de aplicaciones de Intune](app-protection-policy.md).

> [!NOTE]
> Los datos de redireccionamiento actualizados del proxy de la aplicación pueden tardar hasta 24 horas en aplicarse a Managed Browser y a Microsoft Edge.

#### <a name="step-1-enable-automatic-redirection-to-microsoft-edge-from-outlook"></a>Paso 1: Habilitación del redireccionamiento automático a Microsoft Edge desde Outlook.
Configure Outlook con una directiva de protección de aplicaciones que permita el valor **Compartir contenido web con exploradores administrados por directivas**.

![Captura de pantalla de la directiva de protección de aplicaciones: compartir contenido web con exploradores administrados por directivas](./media/manage-microsoft-edge/manage-microsoft-edge-03.png)

#### <a name="step-2-set-the-app-configuration-setting-to-enable-app-proxy"></a>Paso 2: Establecer la opción de configuración de la aplicación para habilitar el proxy de la aplicación
Dirige Microsoft Edge con el siguiente par clave-valor para habilitar el proxy de aplicación para Microsoft Edge:

|    Key    |    Valor    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.AppProxyRedirection    |    true    |

Para más información sobre cómo usar Microsoft Edge y Azure AD Application Proxy conjuntamente para acceder sin problemas (y de forma segura) a las aplicaciones web locales, vea [Better together: Intune and Azure Active Directory team up to improve user access](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access) (Juntos mejor: Intune y Azure Active Directory unen fuerzas para mejorar el acceso de usuario). En esta entrada de blog se hace referencia a Intune Managed Browser, pero el contenido también se aplica a Microsoft Edge.

## <a name="configure-a-homepage-shortcut-for-microsoft-edge"></a>Configuración de un acceso directo a Microsoft  Edge en la página principal

Esta opción de configuración permite configurar un acceso directo a Microsoft  Edge en la página principal. El acceso directo que configure en la página principal aparecerá como el primer icono debajo de la barra de búsqueda cuando el usuario abra una nueva pestaña en Microsoft Edge. El usuario no puede editar ni eliminar este acceso directo en su contexto administrado. El acceso directo a la página principal muestra el nombre de la organización para distinguirla. 

Use el siguiente par clave-valor para configurar un acceso directo en la página principal:

|    Key    |    Valor    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.homepage   |    Especifique una dirección URL válida. Las direcciones URL incorrectas se bloquean como medida de seguridad.<br>**Ejemplo:** <`https://www.bing.com`>

## <a name="configure-your-organizations-logo-and-brand-color-for-new-tab-pages-in-microsoft-edge"></a>Configuración del color de marca y del logotipo de la organización para nuevas páginas de pestañas en Microsoft Edge

Esta configuración permite personalizar la Página Nueva pestaña para Microsoft Edge para mostrar el logotipo de la organización y el color de la marca como fondo de la página.

Para cargar el logotipo y el color de la organización, complete primero los siguientes pasos:
- En Azure Portal, vaya a Intune -> Aplicaciones cliente -> Personalización de marca y personalización-> Personalización de marca de identidad de empresa
- Para establecer el logotipo de la marca, en "Mostrar", elija solo "Logotipo de la empresa". Se recomienda usar logotipos con un fondo transparente. 
- Para establecer el color de fondo de la marca, en "Mostrar" elija "Color de tema". Microsoft Edge aplica una sombra más clara del color en Página Nueva pestaña, lo que garantiza que la página tenga una gran legibilidad. 

A continuación, use los siguientes pares clave/valor para extraer la marca de la organización en Microsoft Edge:

|    Key    |    Valor    |
|--------------------------------------------------------------------|------------|
|    com.microsoft.intune.mam.managedbrowser.NewTabPage.BrandLogo    |    True    |
|    com.microsoft.intune.mam.managedbrowser.NewTabPage.BrandColor    |    True    |

## <a name="display-relevant-industry-news-on-new-tab-pages"></a>Visualización de noticias importantes del sector en las páginas Nueva pestaña

Puede configurar la experiencia de las páginas Nueva pestaña en Microsoft Edge para dispositivos móviles para mostrar noticias del sector importantes para su organización. Cuando se habilita esta característica, Microsoft Edge para dispositivos móviles usa el nombre de dominio de la organización para agregar noticias de la Web de su organización, el sector de la organización y la competencia, para que los usuarios puedan encontrar noticias externas importantes en las páginas Nueva pestaña centralizadas dentro de Microsoft Edge. Las noticias del sector están desactivadas de forma predeterminada y puede activarlas para su organización. 

|    Key    |    Valor    |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.ShowIndustryNews    |    **True** mostrará las noticias del sector en la página Nueva pestaña de Microsoft Edge para dispositivos móviles.<p>**False** (valor predeterminado) ocultará las noticias del sector en la página Nueva pestaña.    |

## <a name="configure-managed-bookmarks-for-microsoft-edge"></a>Configuración de marcadores administrados para Microsoft Edge

Para facilitar el acceso, puede configurar los marcadores que quiera que los usuarios tengan disponibles cuando usen Microsoft Edge. 

Estos son algunos detalles:

- Los usuarios solo verán estos marcadores cuando usen el [modo de empresa](https://docs.microsoft.com/intune/apps/app-configuration-managed-browser#how-to-configure-bookmarks-for-a-protected-browser) de Microsoft Edge. 
- Los usuarios no pueden eliminar ni modificar estos marcadores.
- Aparecen en la parte superior de la lista. Los marcadores creados por los usuarios aparecen debajo de estos marcadores.
- Si ha habilitado el redireccionamiento del proxy de aplicación, puede agregar aplicaciones web de proxy de aplicación mediante su dirección URL interna o externa.
- Asegúrese de anteponer **http://** o **https://** a todas las direcciones URL al introducirlas en la lista.

Use el siguiente par clave-valor para configurar marcadores administrados:

|    Key    |    Valor    |
|---------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.bookmarks    |    El valor de esta configuración es una lista de marcadores. Cada marcador consta del título y de la URL del marcador. Separe el título y la dirección URL con el carácter `|`.      Ejemplo:<br>`Microsoft Bing|https://www.bing.com`<br>Para configurar varios marcadores, separe cada par con el carácter doble `||`.<p>Ejemplo:<br>`Microsoft Bing|https://www.bing.com||Contoso|https://www.contoso.com`    |

## <a name="display-myapps-within-microsoft-edge-bookmarks"></a>Visualización de MyApps en los marcadores de Microsoft Edge

De forma predeterminada, los usuarios verán los sitios de MyApps que tengan configurados en una carpeta situada dentro de los marcadores de Microsoft Edge. La carpeta está etiquetada con el nombre de su organización.

|    Key    |    Valor    |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.MyApps    |    **True** muestra MyApps en los marcadores de Microsoft Edge.<p>**False** oculta MyApps en Microsoft Edge.    |

## <a name="specify-allowed-or-blocked-sites-list-for-microsoft-edge"></a>Especificación de una lista de sitios permitidos o bloqueados para Microsoft Edge
Puede usar la configuración de la aplicación para definir a qué sitios pueden acceder los usuarios al usar su perfil de trabajo. Si usa una lista de permitidos, los usuarios solo podrán acceder a los sitios que indique explícitamente. Si usa una lista de bloqueados, los usuarios podrán acceder a todos los sitios excepto los que haya bloqueado explícitamente. Solo puede imponer una lista de permitidos o bien una de bloqueados, pero no ambas a la vez. Si se imponen ambas, se priorizará la lista de permitidos.  

Use los siguientes pares clave-valor para configurar una lista de sitios permitidos o bloqueados para Microsoft Edge. 

|    Key    |    Valor    |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Elija de entre las siguientes opciones:<p>1. Especifique direcciones URL permitidas (solo se permiten estas direcciones URL; no se puede acceder a ningún otro sitio):<br>`com.microsoft.intune.mam.managedbrowser.AllowListURLs`<p>2. Especifique direcciones URL bloqueadas (se puede acceder a todos los demás sitios):<br>`com.microsoft.intune.mam.managedbrowser.BlockListURLs`    |    El valor correspondiente de la clave es una lista de direcciones URL. Escriba todas las direcciones URL que quiera permitir o bloquear como un valor único, separadas por un carácter de barra vertical `|`.<br>**Ejemplos:**<br>`URL1|URL2|URL3`<br>`http://.contoso.com/|https://.bing.com/|https://expenses.contoso.com`  |

### <a name="url-formats-for-allowed-and-blocked-site-list"></a>Formatos de URL para la lista de sitios permitidos y bloqueados 
Puede usar diferentes formatos de URL para crear listas de sitios permitidos o bloqueados. Estos patrones permitidos se detallan en la tabla siguiente. Algunas notas antes de empezar: 
- Asegúrese de anteponer **http://** o **https://** a todas las direcciones URL al introducirlas en la lista.
- Puede usar el carácter comodín (\*) según las reglas de la siguiente lista de patrones permitidos.
- Un carácter comodín solo puede coincidir con un componente entero del nombre de host (separado por puntos) o partes completas de la ruta de acceso (separadas por barras diagonales). Por ejemplo, `http://*contoso.com`**no** es compatible.
- Puede especificar números de puerto en la dirección. Si no especifica un número de puerto, los valores usados son:
  - Puerto 80 para http
  - Puerto 443 para https
- **No** se admite el uso de caracteres comodín para el número de puerto. Por ejemplo, `http://www.contoso.com:*` y `http://www.contoso.com:*/` no se admiten. 

    |    Dirección URL    |    Detalles    |    Coincide    |    No coincide    |
    |-------------------------------------------|--------------------------------------------------------|-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
    |    `http://www.contoso.com`    |    Coincide con una sola página    |    `www.contoso.com`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`contoso.com/`    |
    |    `http://contoso.com`    |    Coincide con una sola página    |    `contoso.com/`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com`    |
    |    `http://www.contoso.com/*;`   |    Coincide con todas las direcciones URL que comienzan por `www.contoso.com`    |    `www.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com/videos/tvshows`    |    `host.contoso.com`<br>`host.contoso.com/images`    |
    |    `http://*.contoso.com/*`    |    Coincide con todos los subdominios en `contoso.com`    |    `developer.contoso.com/resources`<br>`news.contoso.com/images`<br>`news.contoso.com/videos`    |    `contoso.host.com`
    |    `http://*contoso.com/*`    |    Coincide con todos los subdominios que terminan en `contoso.com/`    |    `http://news-contoso.com`<br>`http://news-contoso.com.com/daily`    |    `http://news-contoso.host.com`    |
    `http://www.contoso.com/images`    |    Coincide con una sola carpeta    |    `www.contoso.com/images`    |    `www.contoso.com/images/dogs`    |
    |    `http://www.contoso.com:80`    |    Coincide con una sola página, con un número de puerto    |    `http://www.contoso.com:80`    |         |
    |    `https://www.contoso.com`    |    Coincide con una sola página segura    |    `https://www.contoso.com`    |    `http://www.contoso.com`    |
    |    `http://www.contoso.com/images/*`    |    Coincide con una sola carpeta y todas sus subcarpetas    |    `www.contoso.com/images/dogs`<br>`www.contoso.com/images/cats`    |    `www.contoso.com/videos`    |
  
- Los siguientes son ejemplos de algunas de las entradas que no se pueden especificar:
  - `*.com`
  - `*.contoso/*`
  - `www.contoso.com/*images`
  - `www.contoso.com/*images*pigs`
  - `www.contoso.com/page*`
  - Direcciones IP
  - `https://*`
  - `http://*`
  - `https://*contoso.com`
  - `http://www.contoso.com:*`
  - `http://www.contoso.com: /*`

## <a name="transition-users-to-their-personal-context-when-trying-to-access-a-blocked-site"></a>Transición de usuarios a su contexto personal al intentar tener acceso a un sitio bloqueado

Con el modelo de identidad dual integrado en Microsoft Edge, puede habilitar una experiencia más flexible para los usuarios finales, algo que no se podía hacer con Intune Managed Browser. Cuando los usuarios visitan un sitio bloqueado en Microsoft Edge, puede pedirles que abran el vínculo en su contexto personal en lugar de su contexto laboral. Esto les permitirá estar protegidos y, a la vez, proteger los recursos de la empresa. Por ejemplo, si un usuario recibe un vínculo a un artículo de noticias a través de Outlook, puede abrir el vínculo en su contexto personal o en una pestaña InPrivate. Su contexto laboral no permite sitios web de noticias. Estas transiciones están permitidas de forma predeterminada.

Use el siguiente par clave-valor para configurar si se permiten estas transiciones suaves:

|    Key    |    Valor    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    "com.microsoft.intune.mam.managedbrowser.openInPrivateIfBlock"    |    **True** hará que los vínculos restringidos se abran directamente en la exploración de InPrivate.<p>**False** (valor predeterminado) presentará a los usuarios una opción para abrir un vínculo restringido con la exploración de InPrivate o con su cuenta personal (MSA).    |

## <a name="open-restricted-links-directly-in-inprivate-tab-pages"></a>Apertura de vínculos restringidos directamente en páginas de pestañas de InPrivate

Puede configurar si los vínculos restringidos deben abrirse directamente en la exploración de InPrivate, lo que proporciona a los usuarios una experiencia de exploración más fluida. Esto ahorraría a los usuarios el tener que realizar una transición a su contexto personal para ver un sitio. La exploración de InPrivate se considera no administrada, por lo que los usuarios no podrán obtener acceso al usar el modo de exploración de InPrivate. 

|    Key    |    Valor    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock`    |    **True** permite a Microsoft Edge pasar a los usuarios a su contexto personal para que puedan abrir sitios bloqueados.<p>La opción **Bloquear** impide que Microsoft Edge realice la transición de los usuarios. A los usuarios simplemente se les muestra un mensaje en el que se indica que el sitio al que intentan acceder está bloqueado.    |


## <a name="use-microsoft-edge-on-ios-to-access-managed-app-logs"></a>Uso de Microsoft Edge en iOS para acceder a los registros de aplicaciones administradas 

Los usuarios que tengan Microsoft Edge instalado en el dispositivo iOS pueden ver el estado de administración de todas las aplicaciones publicadas de Microsoft. También pueden enviar registros para solucionar problemas con sus aplicaciones iOS administradas. Le mostramos cómo:
1. Abra Microsoft Edge en el dispositivo iOS.
2. Escriba `about:intunehelp` en el cuadro de dirección. 
3. Microsoft Edge se abre en modo de solución de problemas.

Para obtener una lista de las opciones de configuración almacenadas en los registros de la aplicación, consulte [Revisión de los registros de protección de aplicaciones en Managed Browser](app-protection-policy-settings-log.md).

Para ver cómo se pueden consultar los registros en dispositivos Android, vea [Enviar registros al administrador de TI por correo electrónico](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). 

## <a name="security-and-privacy-for-microsoft-edge"></a>Seguridad y privacidad para Microsoft Edge

Las siguientes son consideraciones de seguridad y privacidad adicionales para Microsoft Edge:

- Microsoft Edge no utiliza la configuración establecida por los usuarios para el explorador nativo en sus dispositivos, porque Microsoft Edge no puede acceder a esta configuración.
- Puede configurar la opción **Requerir PIN sencillo para el acceso** o **Requerir credenciales corporativas para el acceso** en una directiva de protección de aplicaciones asociada a Microsoft Edge. Si un usuario selecciona el vínculo de ayuda en la página de autenticación, podrá navegar a cualquier sitio de Internet, independientemente de si este se ha agregado o no a una lista de bloqueados en la directiva.
- Microsoft Edge puede bloquear el acceso a sitios solo cuando se accede a estos directamente. No bloquea el acceso cuando los usuarios usan servicios intermedios (por ejemplo, un servicio de traducción) para acceder al sitio.
- Para permitir la autenticación y acceder a la documentación de Intune, ***.microsoft.com** está exento de la configuración de permitidos o bloqueados. Se permite siempre.
- Los usuarios pueden desactivar la recopilación de datos. Microsoft recopila automáticamente datos anónimos sobre el rendimiento y el uso de Managed Browser para mejorar sus productos y servicios. Los usuarios pueden usar en sus dispositivos la configuración de **Datos de uso** para desactivar la recopilación de datos. No tiene ningún control sobre la recopilación de estos datos. En dispositivos iOS, no se pueden abrir los sitios web que visitan los usuarios y que tienen un certificado expirado o que no es de confianza.

## <a name="next-steps"></a>Pasos siguientes

- [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md) 
