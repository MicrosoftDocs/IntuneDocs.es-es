---
title: Cómo usar Azure AD para acceder a las API de Intune en Microsoft Graph
titleSuffix: Microsoft Intune
description: Describe los pasos necesarios para que las aplicaciones que usan Azure AD accedan a las API de Intune en Microsoft Graph.
keywords: intune graphapi c# powershell roles permiso
author: dougeby
manager: dougeby
ms.author: dougeby
ms.date: 03/08/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 79A67342-C06D-4D20-A447-678A6CB8D70A
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1a5381d139247424d976b6b510d62681f623203a
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490510"
---
# <a name="how-to-use-azure-ad-to-access-the-intune-apis-in-microsoft-graph"></a>Cómo usar Azure AD para acceder a las API de Intune en Microsoft Graph

La [API de Microsoft Graph](https://developer.microsoft.com/graph/) ahora es compatible con Microsoft Intune con las API específicas y los roles de permiso.  La API de Microsoft Graph usa Azure Active Directory (Azure AD) para la autenticación y el control de acceso.  
El acceso a las API de Intune en Microsoft Graph requieren lo siguiente:

- Un identificador de la aplicación con:

  - Permiso para llamar a Azure AD y a las API de Microsoft Graph.
  - Ámbitos de permiso pertinentes a tareas de aplicación específicas.

- Credenciales de usuario con:

  - Permiso para acceder al inquilino de Azure AD asociado a la aplicación.
  - Permisos de rol necesarios para admitir los ámbitos de permiso de aplicación.

- Usuario final al que se concede permiso a la aplicación para realizar tareas de aplicaciones para su inquilino de Azure.

En este artículo:

- Se muestra cómo registrar una aplicación con acceso a las API de Microsoft Graph y los roles de permiso pertinentes.

- Se describen los roles de permiso de la API de Intune.

- Se proporcionan ejemplos de autenticación de la API de Intune para C# y PowerShell.

- Se describe cómo admitir varios inquilinos.

Para obtener más información, vea:

- [Autorización del acceso a aplicaciones web mediante OAuth 2.0 y Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code)
- [Getting start with Azure AD authentication](https://www.visualstudio.com/docs/integrate/get-started/auth/oauth) (Introducción a la autenticación de Azure AD)
- [Integración de aplicaciones con Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)
- [Comprender OAuth 2.0](https://oauth.net/2/)

## <a name="register-apps-to-use-the-microsoft-graph-api"></a>Registro de aplicaciones para usar la API de Microsoft Graph

Para registrar una aplicación para usar la API de Microsoft Graph:

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) con credenciales administrativas.

    Según corresponda, puede usar:
    - La cuenta de administrador de inquilinos.
    - Una cuenta de usuario de inquilino con la configuración **Los usuarios pueden registrar aplicaciones** habilitada.

2. En el menú, elija **Azure Active Directory** &gt; **Registros de aplicaciones**.

    <img src="../media/azure-ad-app-reg.png" width="157" height="170" alt="The App registrations menu command" />

3. Elija **Nuevo registro de aplicaciones** para crear una nueva aplicación o elija una aplicación existente.  (Si elige una aplicación existente, omita el paso siguiente).

4. En la hoja **Crear**, especifique lo siguiente:

    1. Un **nombre** para la aplicación (que se muestra cuando los usuarios inician sesión).

    2. Los valores de **Tipo de aplicación** y **URI de redireccionamiento**.

        Pueden variar en función de sus requisitos. Por ejemplo, si usa [Biblioteca de autenticación](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) de Azure AD (ADAL), establezca **Tipo de aplicación** en `Native` y **URI de redireccionamiento** en `urn:ietf:wg:oauth:2.0:oob`.

        <img src="../media/azure-ad-app-new.png" width="209" height="140" alt="New app properties and values" />

        Para más información, consulte [Escenarios de autenticación para Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios).

5. En la hoja de la aplicación:

    1. Anote el valor de **Id. de la aplicación** .

    2. Elija **Configuración** &gt; **Acceso de API** &gt; **Permisos necesarios**.

    <img src="../media/azure-ad-req-perm.png" width="483" height="186" alt="The Required permissions setting" />

6. En la hoja **Permisos necesarios**, elija **Agregar** &gt; **Agregar acceso de API** &gt; **Seleccionar una API**.

    <img src="../media/azure-ad-add-graph.png" width="436" height="140" alt="The Microsoft Graph setting" />

7. Desde la hoja **Seleccionar una API**, elija **Microsoft Graph** &gt; **Seleccionar**.  Se abre la hoja **Habilitar acceso** que muestra los ámbitos de permiso disponibles para la aplicación.

    <img src="../media/azure-ad-perm-scopes.png" width="489" height="248" alt="Intune Graph API permission scopes" />

    Elija los roles necesarios para la aplicación mediante la colocación de una marca de verificación a la izquierda de los nombres correspondientes.  Para más información sobre los ámbitos de permiso específicos de Intune, consulte [Ámbitos de permiso de Intune](#intune-permission-scopes).  Para obtener más información sobre los otros ámbitos de permiso de Graph API, consulte [Referencia de permisos de Microsoft Graph](https://developer.microsoft.com/graph/docs/concepts/permissions_reference).

    Para obtener mejores resultados, elija la menor cantidad de roles necesarios para implementar la aplicación.

    Cuando termine, elija **Seleccionar** y **Listo** para guardar los cambios.

En este punto, también puede:

- Elegir la opción de conceder permiso a todas las cuentas de inquilinos para usar la aplicación sin proporcionar credenciales.  

    Para ello, elija **Conceder permisos** y aceptar el mensaje de confirmación.

    Cuando se ejecuta la aplicación por primera vez, se le pedirá que conceda el permiso de aplicación para realizar las funciones seleccionadas.

    <img src="../media/azure-ad-grant-perm.png" width="351" height="162" alt="The Grant permissions button" />

- Ponga la aplicación a disposición de los usuarios fuera de su inquilino.  (Esto solo se suele requerir a asociados que admiten varios inquilinos u organizaciones).  

    Para ello:

  1. Elija **Manifiesto** en la hoja de la aplicación, que abre la hoja **Editar manifiesto**.

     <img src="../media/azure-ad-edit-mft.png" width="295" height="114" alt="The Edit manifest blade" />

  2. Cambie el valor de la configuración `availableToOtherTenants` a `true`.

  3. Guarde los cambios.

## <a name="intune-permission-scopes"></a>Ámbitos de permiso de Intune

Azure AD y Microsoft Graph usan los ámbitos de permiso para controlar el acceso a los recursos corporativos.  

Los ámbitos de permiso (también denominados _ámbitos de OAuth_) controlan el acceso a entidades específicas de Intune y sus propiedades. En esta sección se resumen los ámbitos de permiso para las características de la API de Intune.

Para más información:
- [Autenticación de Azure AD](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication)
- [Ámbitos de permiso de aplicaciones](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-scopes)

Al conceder permiso a Microsoft Graph, puede especificar los ámbitos siguientes para controlar el acceso a las características de Intune. En la tabla siguiente se resumen los ámbitos de permiso de la API de Intune.  En la primera columna se muestra el nombre de la característica, tal como aparece en Azure Portal y en la segunda columna se proporciona el nombre del ámbito de permiso.

Configuración _Habilitar acceso_ | Nombre de ámbito
:--|:--
__Realizar acciones remotas que influyen en el usuario en dispositivos de Microsoft Intune__ | [DeviceManagementManagedDevices.PrivilegedOperations.All](#mgd-po)
__Leer y escribir en dispositivos de Microsoft Intune__ | [DeviceManagementManagedDevices.ReadWrite.All](#mgd-rw)
__Leer en dispositivos de Microsoft Intune__ | [DeviceManagementManagedDevices.Read.All](#mgd-ro)
__Leer y escribir en la configuración RBAC de Microsoft Intune__ | [DeviceManagementRBAC.ReadWrite.All](#rac-rw)
__Leer en la configuración RBAC de Microsoft Intune__ | DeviceManagementRBAC.Read.All
__Leer y escribir en aplicaciones de Microsoft Intune__ | [DeviceManagementApps.ReadWrite.All](#app-rw)
__Leer en aplicaciones de Microsoft Intune__ | [DeviceManagementApps.Read.All](#app-ro)
__Leer y escribir en la configuración de dispositivos y directivas de Microsoft Intune__ | DeviceManagementConfiguration.ReadWrite.All
__Leer en la configuración de dispositivos y directivas de Microsoft Intune__ | [DeviceManagementConfiguration.Read.All](#cfg-ro)
__Leer y escribir en la configuración de Microsoft Intune__ | [DeviceManagementServiceConfig.ReadWrite.All](#svc-rw)
__Leer en la configuración de Microsoft Intune__ | DeviceManagementServiceConfig.Read.All

En la tabla se muestra la configuración según aparece en Azure Portal. En las siguientes secciones se describen los ámbitos en orden alfabético.

En este momento, todos los ámbitos de permiso de Intune requieren acceso de administrador.  Esto significa que se necesitan las credenciales correspondientes al ejecutar aplicaciones o scripts que acceden a recursos de la API de Intune.

### <a name="app-ro"></a>DeviceManagementApps.Read.All

- Configuración **Habilitar acceso**: __Leer en aplicaciones de Microsoft Intune__

- Permite el acceso de lectura a las siguientes propiedades de entidades y estado:
  - Aplicaciones de cliente
  - Categorías de aplicaciones móviles
  - Directivas de protección de aplicaciones
  - Configuraciones de aplicaciones

### <a name="app-rw"></a>DeviceManagementApps.ReadWrite.All

- Configuración **Habilitar acceso**: __Leer y escribir en aplicaciones de Microsoft Intune__

- Permite las mismas operaciones que __DeviceManagementApps.Read.All__.

- También permite cambios en las siguientes entidades:

  - Aplicaciones de cliente
  - Categorías de aplicaciones móviles
  - Directivas de protección de aplicaciones
  - Configuraciones de aplicaciones

### <a name="cfg-ro"></a>DeviceManagementConfiguration.Read.All

- Configuración **Habilitar acceso**: __Leer en la configuración de dispositivos y directivas de Microsoft Intune__

- Permite el acceso de lectura a las siguientes propiedades de entidades y estado:
  - Configuración de dispositivos
  - Directiva de cumplimiento de dispositivos
  - Mensajes de notificación

### <a name="cfg-ra"></a>DeviceManagementConfiguration.ReadWrite.All

- Configuración **Habilitar acceso**: __Leer y escribir en la configuración de dispositivos y directivas de Microsoft Intune__

- Permite las mismas operaciones que __DeviceManagementConfiguration.Read.All__.

- Las aplicaciones también pueden crear, asignar, eliminar y cambiar las siguientes entidades:
  - Configuración de dispositivos
  - Directiva de cumplimiento de dispositivos
  - Mensajes de notificación

### <a name="mgd-po"></a>DeviceManagementManagedDevices.PrivilegedOperations.All

- Configuración **Habilitar acceso**: __Realizar acciones remotas que influyen en el usuario en dispositivos de Microsoft Intune__

- Permite las acciones remotas siguientes en un dispositivo administrado:
  - Retirar
  - Eliminación de datos
  - Restablecimiento y recuperación de código de acceso
  - Bloqueo remoto
  - Habilitar o deshabilitar el modo de pérdida
  - Limpiar PC
  - Reiniciar
  - Eliminar usuario de dispositivo compartido

### <a name="mgd-ro"></a>DeviceManagementManagedDevices.Read.All

- Configuración **Habilitar acceso**: __Leer en dispositivos de Microsoft Intune__

- Permite el acceso de lectura a las siguientes propiedades de entidades y estado:
  - Dispositivo administrado
  - Categoría de dispositivo
  - Aplicación detectada
  - Acciones remotas
  - Información de malware

### <a name="mgd-rw"></a>DeviceManagementManagedDevices.ReadWrite.All

- Configuración **Habilitar acceso**: __Leer y escribir en dispositivos de Microsoft Intune__

- Permite las mismas operaciones que __DeviceManagementManagedDevices.Read.All__.

- Las aplicaciones también pueden crear, eliminar y cambiar las siguientes entidades:
  - Dispositivo administrado
  - Categoría de dispositivo

- También se admiten las siguientes acciones remotas:
  - Buscar dispositivo
  - Omitir el bloqueo de activación
  - Solicitar asistencia remota

### <a name="rac-ro"></a>DeviceManagementRBAC.Read.All

- Configuración **Habilitar acceso**: __Leer en la configuración RBAC de Microsoft Intune__

- Permite el acceso de lectura a las siguientes propiedades de entidades y estado:
  - Asignaciones de roles
  - Definiciones de roles
  - Operaciones de recursos

### <a name="rac-rw"></a>DeviceManagementRBAC.ReadWrite.All

- Configuración **Habilitar acceso**: __Leer y escribir en la configuración RBAC de Microsoft Intune__

- Permite las mismas operaciones que __DeviceManagementRBAC.Read.All__.

- Las aplicaciones también pueden crear, asignar, eliminar y cambiar las siguientes entidades:
  - Asignaciones de roles
  - Definiciones de roles

### <a name="svc-ro"></a>DeviceManagementServiceConfig.Read.All

- Configuración **Habilitar acceso**: __Leer en la configuración de Microsoft Intune__

- Permite el acceso de lectura a las siguientes propiedades de entidades y estado:
  - Inscripción de dispositivos
  - Certificado de notificaciones push de Apple
  - Programa de inscripción de dispositivos de Apple
  - Programa de Compras por Volumen de Apple
  - Exchange Connector
  - Términos y condiciones
  - Administración de gastos de telecomunicaciones
  - PKI de nube
  - Personalización de marca
  - Mobile Threat Defense

### <a name="svc-rw"></a>DeviceManagementServiceConfig.ReadWrite.All

- Configuración **Habilitar acceso**: __Leer y escribir en la configuración de Microsoft Intune__

- Permite las mismas operaciones que DeviceManagementServiceConfig.Read.All_

- Las aplicaciones también pueden configurar las características de Intune siguientes:
  - Inscripción de dispositivos
  - Certificado de notificaciones push de Apple
  - Programa de inscripción de dispositivos de Apple
  - Programa de Compras por Volumen de Apple
  - Exchange Connector
  - Términos y condiciones
  - Administración de gastos de telecomunicaciones
  - PKI de nube
  - Personalización de marca
  - Mobile Threat Defense

## <a name="azure-ad-authentication-examples"></a>Ejemplos de autenticación de Azure AD

En esta sección se muestra cómo incorporar Azure AD a los proyectos C# y PowerShell.

En cada ejemplo, tendrá que especificar un identificador de aplicación que tenga al menos el ámbito de permiso `DeviceManagementManagedDevices.Read.All` (descrito anteriormente).

Al probar cualquier ejemplo, puede recibir errores de estado HTTP 403 (prohibido) similares al siguiente:

``` javascript
{
  "error": {
    "code": "Forbidden",
    "message": "Application is not authorized to perform this operation - Operation ID " +
       "(for customer support): 00000000-0000-0000-0000-000000000000 - " +
       "Activity ID: cc7fa3b3-bb25-420b-bfb2-1498e598ba43 - " +
       "Url: https://example.manage.microsoft.com/" +
       "Service/Resource/RESTendpoint?" +
       "api-version=2017-03-06 - CustomApiErrorPhrase: ",
    "innerError": {
      "request-id": "00000000-0000-0000-0000-000000000000",
      "date": "1980-01-0112:00:00"
    }
  }
}
```

Si esto ocurre, compruebe lo siguiente:

- Ha actualizado el identificador de aplicación a uno autorizado para usar la API de Microsoft Graph y el ámbito de permiso `DeviceManagementManagedDevices.Read.All`.

- Las credenciales de inquilino admiten funciones administrativas.

- El código es similar a los ejemplos mostrados.


### <a name="authenticate-azure-ad-in-c"></a>Autenticación de Azure AD en C\#

En este ejemplo se muestra cómo usar C# para recuperar una lista de dispositivos asociados a su cuenta de Intune.

1. Inicie Visual Studio y cree un nuevo proyecto de aplicación de consola de Visual C# (.NET Framework).

2. Escriba un nombre para el proyecto y proporcione otros detalles según sea necesario.

    <img src="../media/aad-auth-cpp-new-console.png" width="624" height="433" alt="Creating a C# console app project in Visual Studio"  />

3. Utilice el Explorador de soluciones para agregar el paquete NuGet de ADAL de Microsoft para el proyecto.

    1. Haga clic con el botón derecho en el Explorador de soluciones.
    2. Elija **Administrar paquetes NuGet...** &gt; **Examinar**.
    3. Seleccione `Microsoft.IdentityModel.Clients.ActiveDirectory` y después elija **Instalar**.

    <img src="../media/aad-auth-cpp-install-package.png" width="624" height="458" alt="Selecting the Azure AD identity model module" />

4. Agregue las instrucciones siguientes en la parte superior de **Program.cs**:

    ``` csharp
    using Microsoft.IdentityModel.Clients.ActiveDirectory;</p>
    using System.Net.Http;
    ```

5. Agregue un método para crear el encabezado de autorización:

    ``` csharp
    private static async Task<string> GetAuthorizationHeader()
    {
        string applicationId = "<Your Application ID>";
        string authority = "https://login.microsoftonline.com/common/";
        Uri redirectUri = new Uri("urn:ietf:wg:oauth:2.0:oob");
        AuthenticationContext context = new AuthenticationContext(authority);
        AuthenticationResult result = await context.AcquireTokenAsync(
            "https://graph.microsoft.com",
            applicationId, redirectUri,
            new PlatformParameters(PromptBehavior.Auto));
        return result.CreateAuthorizationHeader();
    ```

    No se olvide de cambiar el valor de `application_ID` para que coincida con alguno que conceda al menos el ámbito de permiso `DeviceManagementManagedDevices.Read.All`, tal como se describió anteriormente.

6. Agregue un método para recuperar la lista de dispositivos:

    ``` csharp
    private static async Task<string> GetMyManagedDevices()
    {
        string authHeader = await GetAuthorizationHeader();
        HttpClient graphClient = new HttpClient();
        graphClient.DefaultRequestHeaders.Add("Authorization", authHeader);
        return await graphClient.GetStringAsync(
            "https://graph.microsoft.com/beta/me/managedDevices");
    }
    ```

7. Actualice **Main** para llamar **GetMyManagedDevices**:

    ``` csharp
    string devices = GetMyManagedDevices().GetAwaiter().GetResult();
    Console.WriteLine(devices);
    ```

8. Compile y ejecute el programa.  

Cuando ejecuta el programa por primera vez, debería recibir dos avisos.  El primero solicita las credenciales y el segundo concede los permisos para la solicitud `managedDevices`.  

Como referencia, este es el programa completado:

``` csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using System;
using System.Net.Http;
using System.Threading.Tasks;

namespace IntuneGraphExample
{
    class Program
    {
        static void Main(string[] args)
        {
            string devices = GetMyManagedDevices().GetAwaiter().GetResult();
            Console.WriteLine(devices);
        }

        private static async Task<string> GetAuthorizationHeader()
        {
            string applicationId = "<Your Application ID>";
            string authority = "https://login.microsoftonline.com/common/";
            Uri redirectUri = new Uri("urn:ietf:wg:oauth:2.0:oob");
            AuthenticationContext context = new AuthenticationContext(authority);
            AuthenticationResult result = await context.AcquireTokenAsync("https://graph.microsoft.com", applicationId, redirectUri, new PlatformParameters(PromptBehavior.Auto));
            return result.CreateAuthorizationHeader();
        }

        private static async Task<string> GetMyManagedDevices()
        {
            string authHeader = await GetAuthorizationHeader();
            HttpClient graphClient = new HttpClient();
            graphClient.DefaultRequestHeaders.Add("Authorization", authHeader);
            return await graphClient.GetStringAsync("https://graph.microsoft.com/beta/me/managedDevices");
        }
    }
}
```

### <a name="authenticate-azure-ad-powershell"></a>Autenticación de Azure AD (PowerShell)

El siguiente script de PowerShell usa el módulo Azure AD PowerShell para la autenticación.  Para más información, consulte [Azure Active Directory PowerShell versión 2](https://docs.microsoft.com/powershell/azure/install-adv2?view=azureadps-2.0) y [Ejemplos de PowerShell de Intune](https://github.com/microsoftgraph/powershell-intune-samples).

En este ejemplo, actualice el valor de `$clientID` para que coincida con un identificador de aplicación válido.

``` powershell
function Get-AuthToken {
    [cmdletbinding()]
    param
    (
        [Parameter(Mandatory = $true)]
        $User
    )

    $userUpn = New-Object "System.Net.Mail.MailAddress" -ArgumentList $User
    $tenant = $userUpn.Host

    Write-Host "Checking for AzureAD module..."

    $AadModule = Get-Module -Name "AzureAD" -ListAvailable
    if ($AadModule -eq $null) {
        Write-Host "AzureAD PowerShell module not found, looking for AzureADPreview"
        $AadModule = Get-Module -Name "AzureADPreview" -ListAvailable
    }

    if ($AadModule -eq $null) {
        write-host
        write-host "AzureAD Powershell module not installed..." -f Red
        write-host "Install by running 'Install-Module AzureAD' or 'Install-Module AzureADPreview' from an elevated PowerShell prompt" -f Yellow
        write-host "Script can't continue..." -f Red
        write-host
        exit
    }

    # Getting path to ActiveDirectory Assemblies
    # If the module count is greater than 1 find the latest version

    if ($AadModule.count -gt 1) {
        $Latest_Version = ($AadModule | select version | Sort-Object)[-1]
        $aadModule = $AadModule | ? { $_.version -eq $Latest_Version.version }
        $adal = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.dll"
        $adalforms = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.Platform.dll"
    }

    else {
        $adal = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.dll"
        $adalforms = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.Platform.dll"
    }

    [System.Reflection.Assembly]::LoadFrom($adal) | Out-Null
    [System.Reflection.Assembly]::LoadFrom($adalforms) | Out-Null

    $clientId = "<Your Application ID>"
    $redirectUri = "urn:ietf:wg:oauth:2.0:oob"
    $resourceAppIdURI = "https://graph.microsoft.com"
    $authority = "https://login.microsoftonline.com/$Tenant"

    try {
        $authContext = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.AuthenticationContext" -ArgumentList $authority
        # https://msdn.microsoft.com/library/azure/microsoft.identitymodel.clients.activedirectory.promptbehavior.aspx
        # Change the prompt behaviour to force credentials each time: Auto, Always, Never, RefreshSession
        $platformParameters = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.PlatformParameters" -ArgumentList "Auto"
        $userId = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.UserIdentifier" -ArgumentList ($User, "OptionalDisplayableId")
        $authResult = $authContext.AcquireTokenAsync($resourceAppIdURI, $clientId, $redirectUri, $platformParameters, $userId).Result
        # If the accesstoken is valid then create the authentication header
        if ($authResult.AccessToken) {
            # Creating header for Authorization token
            $authHeader = @{
                'Content-Type' = 'application/json'
                'Authorization' = "Bearer " + $authResult.AccessToken
                'ExpiresOn' = $authResult.ExpiresOn
            }
            return $authHeader
        }
        else {
            Write-Host
            Write-Host "Authorization Access Token is null, please re-run authentication..." -ForegroundColor Red
            Write-Host
            break
        }
    }
    catch {
        write-host $_.Exception.Message -f Red
        write-host $_.Exception.ItemName -f Red
        write-host
        break
    }   
}

$authToken = Get-AuthToken -User "<Your AAD Username>"

try {
    $uri = "https://graph.microsoft.com/beta/me/managedDevices"
    Write-Verbose $uri
    (Invoke-RestMethod -Uri $uri –Headers $authToken –Method Get).Value
}
catch {
    $ex = $_.Exception
    $errorResponse = $ex.Response.GetResponseStream()
    $reader = New-Object System.IO.StreamReader($errorResponse)
    $reader.BaseStream.Position = 0
    $reader.DiscardBufferedData()
    $responseBody = $reader.ReadToEnd();
    Write-Host "Response content:`n$responseBody" -f Red
    Write-Error "Request to $Uri failed with HTTP Status $($ex.Response.StatusCode) $($ex.Response.StatusDescription)"
    write-host
    break
}
```

## <a name="support-multiple-tenants-and-partners"></a>Compatibilidad con varios inquilinos y asociados

Si su organización admite organizaciones con sus propios inquilinos de Azure AD, puede que desee permitir que los clientes usen su aplicación con sus respectivos inquilinos.

Para ello:

1. Compruebe que existe la cuenta de cliente en el inquilino de Azure AD de destino.

2. Compruebe que su cuenta de inquilino permite a los usuarios registrar aplicaciones (consulte **Configuración de usuario**).

3. Establezca una relación entre cada inquilino.  

    Para ello, elija una de estas opciones:

    a. Use el [Centro de asociados de Microsoft](https://partnercenter.microsoft.com/) para definir una relación con el cliente y su dirección de correo electrónico.

    b. Invite al usuario a convertirse en invitado de su inquilino.

Para invitar al usuario a convertirse en invitado de su inquilino:

1. Elija **Agregar un usuario invitado** en el panel **Tareas rápidas**.

    <img src="../media/azure-ad-add-guest.png" width="448" height="138" alt="Use Quick Tasks to add a guest user" />

2. Escriba la dirección de correo electrónico del cliente y, opcionalmente, agregue un mensaje personalizado para la invitación.

    <img src="../media/azure-ad-guest-invite.png" width="203" height="106" alt="Inviting an external user as a guest" />

3. Elija **Invitar**.

De esta forma se envía una invitación al usuario.

   <img src="../media/aad-multiple-tenant-invitation.png" width="624" height="523" alt="A sample guest invitation" />

   El usuario tiene que elegir el vínculo **Introducción** para aceptar la invitación.

Cuando se establece la relación (o se ha aceptado su invitación), agregue la cuenta de usuario al **rol de directorio**.

No se olvide agregar el usuario a otros roles según sea necesario. Por ejemplo, para permitir al usuario administrar la configuración de Intune, debe ser un **administrador global** o un **administrador del servicio de Intune**.

Además:

- Use https://admin.microsoft.com para asignar una licencia de Intune a su cuenta de usuario.

- Actualice el código de aplicación para autenticarse en el dominio de inquilino de Azure AD del cliente, en lugar de al suyo propio.

    Por ejemplo, si el dominio del inquilino es `contosopartner.onmicrosoft.com` y el dominio del inquilino de su cliente es `northwind.onmicrosoft.com`, actualice el código para autenticarse en el inquilino de su cliente.

    Para ello, en una aplicación C# basada en el ejemplo anterior, debería cambiar el valor de la variable `authority`:

    ``` csharp
    string authority = "https://login.microsoftonline.com/common/";
    ```

    en

    ``` csharp
    string authority = "https://login.microsoftonline.com/northwind.onmicrosoft.com/";
    ```
