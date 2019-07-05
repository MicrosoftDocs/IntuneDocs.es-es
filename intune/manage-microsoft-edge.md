---
title: Administración del acceso web mediante Microsoft Edge con Microsoft Intune
titleSuffix: ''
description: Use las directivas de protección de aplicaciones de Intune con Microsoft Edge para garantizar que siempre se apliquen medidas de seguridad al acceder a los sitios web corporativos.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 06/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3fb2f050-ec94-42ab-be05-c3d4101148bb
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1ad8a3298a801b07e021b84bd5eea9c91f01f1a2
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/13/2019
ms.locfileid: "67044884"
---
# <a name="manage-web-access-using-microsoft-edge-with-microsoft-intune"></a>Administración del acceso web mediante Microsoft Edge con Microsoft Intune

Usar las directivas de protección de aplicaciones de Intune con Microsoft Edge puede garantizar que siempre se apliquen medidas de seguridad al acceder a los sitios web corporativos. Están disponibles las características empresariales de Microsoft Edge siguientes habilitadas por directivas de Intune. Estas características empresariales incluyen:

1.  **Identidad dual**: los usuarios pueden agregar una cuenta profesional, al igual que una cuenta personal, para realizar la exploración. Hay una separación total entre ambas identidades, que es similar a la arquitectura y experiencia existente en Office 365 y Outlook. Los administradores de Intune podrán establecer las directivas deseadas para lograr una experiencia de exploración protegida dentro de la cuenta profesional.
2.  **Integración de la directiva de protección de aplicaciones de Intune**: puesto que Microsoft Edge se integra con el SDK de Intune, puede aplicar directivas de protección de aplicaciones para garantizar la protección contra la pérdida de datos. Estas características incluyen el control de las funciones de cortar, copiar y pegar, impedir la obtención de capturas de pantalla y garantizar que los vínculos seleccionados por los usuarios se abran solo en otras aplicaciones administradas.
3.  **Integración del proxy de la aplicación de Azure**: puede controlar el acceso a las aplicaciones web y a las aplicaciones SaaS para garantizar que las aplicaciones basadas en el explorador solo se ejecuten en el explorador seguro de Microsoft Edge, tanto si los usuarios finales se conectan desde la red corporativa como si lo hacen desde Internet.
4.  **Configuración de la aplicación**: puede aprovechar los valores de configuración de la aplicación para reforzar el posicionamiento de seguridad de las organizaciones y configurar características fáciles de usar para los usuarios finales. Por ejemplo, puede definir marcadores, accesos directos en la página principal, sitios web permitidos y bloqueados, Azure Application Proxy y mucho más.
Las directivas de protección de Microsoft Intune para Microsoft Edge ayudan a proteger los datos y los recursos de su organización. Usar estas directivas con Microsoft Edge garantiza la protección de los recursos de la empresa no solo dentro de las aplicaciones instaladas de manera nativa, sino también cuando se accede a ellas desde el explorador web.

## <a name="getting-started"></a>Introducción

Tanto usted como los usuarios finales pueden descargar Microsoft Edge desde tiendas de aplicaciones públicas para usarlo en sus organizaciones. Requisitos del sistema operativo para las directivas de explorador:
- Android 4 y versiones posteriores
- iOS 8.0 y versiones posteriores

## <a name="application-protection-policies-for-microsoft-edge"></a>Directivas de protección de aplicaciones para Microsoft Edge

Como Microsoft Edge está integrado con el SDK de Intune, puede aplicar directivas de protección de aplicaciones, que incluyen:
- Controlar el uso de cortar, copiar y pegar
- Evitar las capturas de pantalla
- Garantizar que los vínculos corporativas se abren solo en aplicaciones y exploradores administrados

Para obtener detalles, vea "¿Qué son las directivas de protección de aplicaciones?".
Puede aplicar esta configuración a:
- Dispositivos móviles inscritos con Intune
- Inscritos con otro producto de MDM
- Dispositivos no administrados

Si la directiva de Intune no se dirige a Microsoft Edge, los usuarios no podrán usarlo para acceder a datos de otras aplicaciones administradas por Intune, como aplicaciones de Office. 

## <a name="conditional-access-for-microsoft-edge"></a>Acceso condicional para Microsoft Edge

Puede aprovechar el acceso condicional de Azure AD para redirigir a los usuarios para que accedan a contenido corporativo solo a través de Microsoft Edge. Esto restringiría el acceso del explorador móvil a únicamente las aplicaciones web conectadas a Azure AD para Microsoft Edge protegido por la directiva, y esto impediría el acceso desde cualquier otro explorador no protegido, como Safari o Chrome. El acceso condicional se puede aplicar a recursos de Azure como Exchange Online y SharePoint Online, el Centro de administración de Microsoft 365 e, incluso, a sitios locales que estén expuestos a usuarios externos a través de [Azure AD Application Proxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started).

Para restringir las aplicaciones web conectadas a Azure AD para que usen Microsoft Edge en iOS y Android, siga estos pasos:
1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. En el nodo de Intune, seleccione **Acceso condicional** > **Nueva directiva**.
3. Luego, seleccione **Conceder** en la sección **Controles de acceso** de la hoja.
4. Haga clic en **Requerir aplicación cliente aprobada**.
5. Haga clic en **Seleccionar** en la hoja **Conceder**. Esta directiva se debe asignar a las aplicaciones en la nube que quiera que estén accesibles a únicamente la aplicación Intune Managed Browser.

    ![Directiva de acceso condicional: concesión](./media/manage-microsoft-edge/manage-microsoft-edge-01.png)

6. En la sección Asignaciones, seleccione Condiciones > Aplicaciones cliente. Aparecerá la hoja Aplicaciones cliente.
7. En Configurar para aplicar la directiva a aplicaciones cliente específicas, haga clic en Sí.
8. Compruebe que la opción Explorador está seleccionada como aplicación cliente.

    ![Directiva de acceso condicional: selección de las aplicaciones cliente](./media/manage-microsoft-edge/manage-microsoft-edge-02.png)

    > [!NOTE]
    > Si quiere restringir qué aplicaciones nativas (aplicaciones que no son de explorador) pueden tener acceso a estas aplicaciones en la nube, también puede seleccionar **Aplicaciones móviles y aplicaciones de escritorio**.

9. En la sección **Asignaciones**, seleccione **Usuarios y grupos** y, después, elija los usuarios o grupos a los que quiera asignar esta directiva.

    > [!NOTE]
    > A los usuarios también se les deben asignar directivas de Intune App Protection para recibir directivas de configuración de aplicaciones. Para obtener más información sobre cómo crear directivas de Intune App Protection, vea [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md)

10. En la sección **Asignaciones**, seleccione **Aplicaciones en la nube** para elegir las aplicaciones que se van a proteger con esta directiva.

Una vez configurada la directiva, los usuarios deberán usar inexorablemente Microsoft Edge para acceder a las aplicaciones web conectadas a Azure AD que estén protegidas con dicha directiva. Si los usuarios intentan usar un explorador no administrado en este escenario, aparecerá un mensaje que les indica que deben usar Microsoft Edge.

> [!TIP]
> Acceso condicional es una tecnología de Azure Active Directory (Azure AD). El nodo de acceso condicional al que se accede desde Intune es el mismo nodo al que se accede desde Azure AD.

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>Inicio de sesión único en aplicaciones web conectadas a Azure AD en exploradores protegidos por directivas

Microsoft Edge en iOS y Android pueden aprovechar el inicio de sesión único en todas las aplicaciones web (SaaS y locales) que estén conectadas a Azure AD. Con el inicio de sesión único, los usuarios pueden acceder a aplicaciones web conectadas a Azure AD a través de Microsoft Edge sin tener que volver a introducir sus credenciales.

Para el inicio de sesión único es necesario que el dispositivo esté registrado con la aplicación Microsoft Authenticator para dispositivos iOS o con el Portal de empresa de Intune en Android. Cuando los usuarios tengan la aplicación Authenticator o el Portal de empresa de Intune deberán registrar su dispositivo siempre que vayan a una aplicación web conectada a Azure AD en un explorador protegido por directivas, si el dispositivo aún no se ha registrado. Una vez que el dispositivo esté registrado con la cuenta del usuario administrada por Intune, esa cuenta tendrá el inicio de sesión único habilitado en las aplicaciones web conectadas a Azure AD.

> [!NOTE]
> El registro de dispositivos consiste en un sencillo registro en el servicio de Azure AD. No se requiere una inscripción de dispositivo completa ni se otorga a TI ningún tipo de privilegio extra en el dispositivo.

## <a name="create-a-protected-browser-app-configuration"></a>Establecimiento de una configuración de aplicaciones de explorador protegido

Para que se apliquen las configuraciones de las aplicaciones, el explorador protegido del usuario u otra aplicación del dispositivo ya deben estar administrados mediante [directivas de aplicación de Intune](app-protection-policy.md).

Para crear una configuración de aplicación de explorador protegido, siga estos pasos:

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Seleccione **Aplicaciones cliente** > **Directivas de configuración de aplicaciones** > **Agregar**.
3. En la hoja **Agregar directiva de configuración**, escriba un **nombre** y una **descripción** opcional para las opciones de configuración de aplicaciones.
4. En **Tipo de inscripción del dispositivo**, elija **Aplicaciones administradas**.
5. Elija **Seleccionar la aplicación requerida** y, después, en la hoja **Aplicaciones de destino**, elija **Managed Browser** o **Edge** para iOS, para Android o para ambos.
6. Elija **Aceptar** para volver a la hoja **Agregar directiva de configuración**.
7. Elija **Opciones de configuración**. En la hoja **Configuración**, defina los pares clave-valor para proporcionar configuraciones para Microsoft Edge. Use las secciones posteriores de este artículo para obtener información sobre los diferentes pares de clave y valor que puede definir.

    > [!NOTE]
    > Microsoft Edge usa los mismos pares de clave y valor que Managed Browser. 

8.  Cuando haya terminado, haga clic en **Aceptar**.
9.  En la hoja **Agregar directiva de configuración**, elija **Agregar**.<br>
    Se crea la configuración y se muestra en la hoja **App Configuration**.

## <a name="assign-the-configuration-settings-you-created"></a>Asignación de las opciones de configuración creadas 

Debe asignar la configuración a los grupos de usuarios de Azure AD. Si ese usuario tiene instalada la aplicación de explorador protegido, esta se administra mediante la configuración especificada.

1. En la hoja **Aplicaciones cliente** del panel de administración de aplicaciones móviles de Intune, elija **Directivas de configuración de aplicaciones**.
2. En la lista de configuraciones de aplicación, seleccione la que desea asignar.
3. En la siguiente hoja, elija **Asignaciones**.
4. En la hoja **Asignaciones**, seleccione el grupo de Azure AD al que quiere asignar la configuración de aplicación y después elija **Aceptar**.

## <a name="how-to-configure-application-proxy-settings-for-protected-browsers"></a>Configuración del proxy de aplicación para exploradores protegidos

Microsoft Edge y [Azure AD Application Proxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) pueden usarse conjuntamente para proporcionar a los usuarios acceso a sitios de la intranet desde sus dispositivos móviles. 

Estos son algunos ejemplos de los escenarios que AD Application Proxy permite: 

- Un usuario está utilizando la aplicación móvil de Outlook, que está protegida por Intune. El usuario hace clic a un vínculo de un correo electrónico que dirige a un sitio de la intranet y Microsoft Edge reconoce que dicho sitio se ha expuesto al usuario a través del proxy de la aplicación. El usuario se enruta automáticamente a través del proxy de la aplicación para que se autentique con una autenticación multifactor y un acceso condicional antes de llegar al sitio de la intranet. Ahora los usuarios pueden acceder a sitios internos incluso desde sus dispositivos móviles y el vínculo de Outlook funciona según lo previsto.
- Un usuario abre Microsoft Edge en su dispositivo iOS o Android. Si Microsoft Edge está protegido con Intune y el proxy de la aplicación está habilitado, el usuario puede navegar a un sitio de la intranet mediante la URL interna como de costumbre. Microsoft Edge reconoce que este sitio de la intranet se ha expuesto al usuario a través del proxy de la aplicación y el usuario se enruta automáticamente a través del proxy de la aplicación para que se autentique antes de llegar al sitio en cuestión. 

### <a name="before-you-start"></a>Antes de empezar

- Configure las aplicaciones internas a través del proxy de aplicación de Azure AD.
    - Para configurar el proxy de aplicación y publicar aplicaciones, vea la [documentación de configuración](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).
- La aplicación de Microsoft Edge debe tener asignada la [directiva de protección de aplicaciones de Intune](app-protection-policy.md).

> [!NOTE]
> Los datos de redireccionamiento actualizados del proxy de la aplicación pueden tardar hasta 24 horas en aplicarse a Managed Browser y a Microsoft Edge.

#### <a name="step-1-enable-automatic-redirection-to-a-protected-browser-from-outlook"></a>Paso 1: Habilitar el redireccionamiento automático a un explorador protegido desde Outlook.
Outlook debe estar configurado con una directiva de protección de aplicaciones que permita el valor **Compartir contenido web con exploradores administrados por directivas**.

![Directiva de protección de aplicaciones: compartir contenido web con exploradores administrados por directivas](./media/manage-microsoft-edge/manage-microsoft-edge-03.png)

#### <a name="step-2-set-the-app-configuration-setting-to-enable-app-proxy"></a>Paso 2: Establecer la opción de configuración de la aplicación para habilitar el proxy de la aplicación
Dirige Microsoft Edge con el siguiente par clave-valor para habilitar el proxy de la aplicación para Microsoft Edge:

|    Key    |    Valor    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.AppProxyRedirection    |    true    |

Para más información sobre cómo usar Microsoft Edge y Azure AD Application Proxy conjuntamente para acceder sin problemas (y de forma segura) a las aplicaciones web locales, vea la entrada de blog de Enterprise Mobility + Security [Better together: Intune and Azure Active Directory team up to improve user access](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access) (Juntos mejor: Intune y Azure Active Directory unen fuerzas para mejorar el acceso de usuario). En esta entrada de blog se hace referencia a Intune Managed Browser, pero el contenido también se aplica a Microsoft Edge.

## <a name="how-to-configure-a-homepage-shortcut-for-microsoft-edge"></a>Cómo se configura un acceso directo a Microsoft  Edge en la página principal

Esta opción de configuración permite configurar un acceso directo a Microsoft  Edge en la página principal.  El acceso directo que configure en la página principal aparecerá como el primer icono debajo de la barra de búsqueda cuando se abra una nueva pestaña en Microsoft Edge. El usuario no podrá editar ni eliminar este acceso directo en su contexto administrado. El acceso directo a la página principal mostrará el nombre de la organización para distinguirla. 

Use el siguiente par clave-valor para configurar un acceso directo en la página principal:

|    Key    |    Valor    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.homepage   |    Especifique una dirección URL válida. Las direcciones URL incorrectas se bloquean como medida de seguridad.<br>**Ejemplo:** `<https://www.bing.com`>
    |

## <a name="how-to-configure-managed-bookmarks-for-microsoft-edge"></a>Cómo configurar marcadores administrados para Microsoft Edge

Para facilitar el acceso, puede configurar los marcadores que quiera que los usuarios tengan disponibles cuando usen Microsoft Edge. Estos son algunos detalles:

- Los usuarios solo verán estos marcadores cuando usen el modo de empresa de Microsoft Edge. 
- Los usuarios no pueden eliminar ni modificar estos marcadores.
- Se muestran en la parte superior de la lista. Los marcadores creados por los usuarios aparecen debajo de estos marcadores.
- Si ha habilitado el redireccionamiento del proxy de aplicación, puede agregar aplicaciones web de proxy de aplicación mediante su dirección URL interna o externa.

Use el siguiente par clave-valor para configurar marcadores administrados:

|    Key    |    Valor    |
|---------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.bookmarks    |    El valor de esta configuración es una lista de marcadores. Cada marcador consta del título y de la URL del marcador. Separe el título y la dirección URL con el carácter `|`.      **Ejemplo:**<br>`Microsoft Bing|https://www.bing.com`<p>Para configurar varios marcadores, separe cada par con el carácter doble `||`.<p>**Ejemplo:**<br>`Microsoft Bing|https://www.bing.com||Contoso|https://www.contoso.com`    |

## <a name="how-to-display-myapps-within-microsoft-edge-bookmarks"></a>Cómo mostrar MyApps en los marcadores de Microsoft Edge

De forma predeterminada, los usuarios verán los sitios de MyApps que tengan configurados en una carpeta situada dentro de los marcadores de Microsoft Edge. La carpeta estará etiquetada con el nombre de su organización.

|    Key    |    Valor    |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.MyApps    |    **True** muestra MyApps en los marcadores de Microsoft Edge.<p>**False** oculta MyApps en Microsoft Edge.    |

## <a name="how-to-specify-allowed-or-blocked-sites-list-for-microsoft-edge"></a>Cómo especificar una lista de sitios permitidos o bloqueados para Microsoft Edge
Puede usar la configuración de la aplicación para definir a qué sitios pueden acceder los usuarios al usar su perfil de trabajo. Si usa una lista de permitidos, los usuarios solo podrán acceder a los sitios que indique explícitamente. Si usa una lista de bloqueados, los usuarios podrán acceder a todos los sitios excepto los que haya bloqueado explícitamente. Solo puede imponer una lista de permitidos o bien una de bloqueados, pero no ambas a la vez. Si ambas se destinan al dispositivo, se respetará la lista de permitidos.  

Puede usar los siguientes pares clave-valor para configurar una lista de sitios permitidos o bloqueados para Microsoft Edge. Siga leyendo para obtener más información sobre los formatos de URL válidos. 

|    Key    |    Valor    |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Elija de entre las siguientes opciones:<p>1. Especifique direcciones URL permitidas (solo se permiten estas direcciones URL; no se puede acceder a ningún otro sitio):<br>`com.microsoft.intune.mam.managedbrowser.AllowListURLs`<p>2. Especifique direcciones URL bloqueadas (se puede acceder a todos los demás sitios):<br>`com.microsoft.intune.mam.managedbrowser.BlockListURLs`    |    El valor correspondiente de la clave es una lista de direcciones URL. Escriba todas las direcciones URL que quiera permitir o bloquear como un valor único, separadas por un carácter de barra vertical `|`.<p>**Ejemplos:**<br>`URL1|URL2|URL3`<br>`http://.contoso.com/|https://.bing.com/|https://expenses.contoso.com`  |

### <a name="url-formats-for-allowed-and-blocked-site-list"></a>Formatos de URL para la lista de sitios permitidos y bloqueados 
Puede usar diferentes formatos de URL para crear listas de sitios permitidos o bloqueados. Estos patrones permitidos se detallan en la tabla siguiente. Algunas notas antes de empezar: 
- Asegúrese de anteponer **http** o **https** a todas las direcciones URL al introducirlas en la lista.
- Puede usar el carácter comodín (*) según las reglas de la siguiente lista de patrones permitidos.
- Puede especificar números de puerto en la dirección. Si no especifica un número de puerto, los valores usados son:
    - Puerto 80 para http
    - Puerto 443 para https
- **No** se admite el uso de caracteres comodín para el número de puerto. Por ejemplo, `http://www.contoso.com:*` y `http://www.contoso.com:*/` no se admiten.

    |    Dirección URL    |    Detalles    |    Coincide    |    No coincide    |
    |-------------------------------------------|--------------------------------------------------------|-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
    |    `http://www.contoso.com`    |    Coincide con una sola página    |    `www.contoso.com`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`contoso.com/`    |
    |    `http://contoso.com`    |    Coincide con una sola página    |    `contoso.com/`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com`    |
    |    `http://www.contoso.com/&#42;`   |    Coincide con todas las direcciones URL que comienzan por `www.contoso.com`    |    `www.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com/videos/tvshows`    |    `host.contoso.com`<br>`host.contoso.com/images`    |
    |    `http://*.contoso.com/*`    |    Coincide con todos los subdominios en `contoso.com`    |    `developer.contoso.com/resources`<br>`news.contoso.com/images`<br>`news.contoso.com/videos`    |    `contoso.host.com`    |
    |    `http://www.contoso.com/images`    |    Coincide con una sola carpeta    |    `www.contoso.com/images`    |    `www.contoso.com/images/dogs`    |
    |    `http://www.contoso.com:80`    |    Coincide con una sola página, con un número de puerto    |    http://www.contoso.com:80    |         |
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
    - `http://www.contoso.com:*`
    - `http://www.contoso.com: /*`
  
## <a name="defining-behavior-when-users-try-to-access-a-blocked-site"></a>Definición del comportamiento cuando los usuarios intentan acceder a un sitio bloqueado

Con el modelo de identidad dual integrado en Microsoft Edge, puede habilitar una experiencia más flexible para los usuarios finales, algo que no se podía hacer con Intune Managed Browser. Cuando los usuarios visitan un sitio bloqueado en Microsoft Edge, se les puede pedir que abran el vínculo en su contexto personal en lugar de hacerlo en su contexto de trabajo, para que puedan seguir protegidos y, al mismo tiempo, mantener los recursos corporativos protegidos. Por ejemplo, si un usuario recibe un vínculo a un artículo de noticias a través de Outlook, podrá abrirlo en su contexto personal o en una pestaña InPrivate en lugar de hacerlo en su contexto de trabajo, que no permite sitios web de noticias. Estas transiciones están permitidas de forma predeterminada.

Use el siguiente par clave-valor para configurar si se permiten estas transiciones suaves:

|    Key    |    Valor    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock`    |    **True** permite a Microsoft Edge pasar a los usuarios a su contexto personal para que puedan abrir sitios bloqueados.<p>**Block** impide que Microsoft Edge pase a los usuarios, que simplemente verán un mensaje en el que se les indicará que el sitio al que están intentando acceder está bloqueado.    |

## <a name="directing-users-to-microsoft-edge-instead-of-the-intune-managed-browser"></a>Dirigir a los usuarios a Microsoft Edge en vez de a Intune Managed Browser 

Tanto Intune Managed Browser como Microsoft Edge ahora se pueden usar como exploradores administrados por directivas. Para asegurarse de que se está guiando a los usuarios para que usen la aplicación de explorador correcta, dirija todas las aplicaciones administradas por Intune (por ejemplo, Outlook y OneDrive) con la opción de configuración siguiente:

|    Key    |    Valor    |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.useEdge`    |    El valor `true` dirigirá a los usuarios a usar Microsoft Edge.<p>El valor `false` dirigirá a los usuarios a usar Intune Managed Browser.    |

Si no se establece este valor de configuración de la aplicación, la lógica siguiente definirá qué explorador se usará para abrir vínculos corporativos.

En Android:
- Intune Managed Browser se iniciará si un usuario tiene Intune Managed Browser y Microsoft Edge descargados en el dispositivo. 
- Microsoft Edge se abrirá solo si Intune Microsoft Edge se descarga en el dispositivo y es el objetivo de la directiva.
- Managed Browser se abrirá solo si Managed Browser se encuentra en el dispositivo y es el objetivo de la directiva de Intune.

En iOS, para aplicaciones que tienen integrado el SDK de Intune para iOS versión 9.0.9+:
- Intune Managed Browser se iniciará si Intune Managed Browser y Microsoft Edge se encuentran en el dispositivo.  
- Microsoft Edge se iniciará solo si Microsoft Edge se encuentra en el dispositivo y es el objetivo de la directiva de Intune.
- Managed Browser solo si Managed Browser se encuentra en el dispositivo y es objeto de la directiva de Intune.

## <a name="using-microsoft-edge-on-ios-to-access-managed-app-logs"></a>Uso de Microsoft Edge en iOS para acceder a los registros de aplicaciones administradas 

Los usuarios finales que tengan Microsoft Edge instalado en el dispositivo iOS pueden ver el estado de administración de todas las aplicaciones publicadas de Microsoft. También pueden enviar registros para solucionar problemas con sus aplicaciones iOS administradas.
1. Abra Microsoft Edge en el dispositivo iOS.
2. Escriba `about:intunehelp` en el cuadro de dirección. 
3. El modo de solución de problemas se iniciará desde Microsoft Edge.

Para obtener una lista de las opciones de configuración almacenadas en los registros de la aplicación, consulte [Revisión de los registros de protección de aplicaciones en Managed Browser](app-protection-policy-settings-log.md).

Para ver cómo se pueden consultar los registros en dispositivos Android, vea [Enviar registros al administrador de TI por correo electrónico](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). 

## <a name="security-and-privacy-for-microsoft-edge"></a>Seguridad y privacidad para Microsoft Edge

Consideraciones de seguridad y privacidad adicionales para Microsoft Edge:

- Microsoft Edge no utiliza la configuración establecida por los usuarios para el explorador nativo en sus dispositivos, porque Microsoft Edge no puede acceder a esta configuración.
- Si configura las opciones **Requerir PIN sencillo para el acceso** o **Requerir credenciales corporativas para el acceso** en una directiva de protección de aplicaciones asociada a Microsoft Edge, cuando un usuario seleccione el vínculo de ayuda en la página de autenticación, podrá ir a cualquier sitio de Internet independientemente de si se ha agregado a una lista de bloqueados de la directiva.
- Microsoft Edge puede bloquear el acceso a sitios solo cuando se accede a estos directamente. No bloquea el acceso cuando se usan servicios intermedios (por ejemplo, un servicio de traducción) para acceder al sitio.
- Para permitir la autenticación y acceder a la documentación de Intune, * **.microsoft.com** está exento de la configuración de permitidos o bloqueados. Siempre está permitida.
Desactive los datos de uso. Microsoft recopila automáticamente datos anónimos sobre el rendimiento y el uso del explorador administrado para mejorar sus productos y servicios. Los usuarios pueden usar en sus dispositivos la configuración de **Datos de uso** para desactivar la recopilación de datos. No tiene ningún control sobre la recopilación de estos datos. En dispositivos iOS, no se pueden abrir los sitios web que visitan los usuarios y que tienen un certificado expirado o que no es de confianza.

## <a name="next-steps"></a>Pasos siguientes

- [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md) 
