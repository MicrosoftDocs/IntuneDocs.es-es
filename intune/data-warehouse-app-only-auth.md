---
title: Autenticación de solo aplicación de Almacenamiento de datos de Intune
titleSuffix: Microsoft Intune
description: En este tema se describe la autenticación de solo aplicación de Data Warehouse para Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: d7166563-6bb5-4624-b8c8-6b300a997c3a
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4edf6e1e2b0ed57ec221e445bc171895fb9e0072
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66042668"
---
# <a name="intune-data-warehouse-application-only-authentication"></a>Autenticación de solo aplicación de Almacenamiento de datos de Intune

Puede configurar una aplicación con Azure Active Directory (Azure AD) y autenticarla en el Almacenamiento de datos de Intune. Este proceso resulta útil para sitios web, aplicaciones y procesos en segundo plano en que la aplicación no debe tener acceso a las credenciales de usuario. Con los pasos siguientes, autoriza a la aplicación con Azure AD mediante OAuth 2.0.

## <a name="authorization"></a>Autorización

Azure Active Directory (Azure AD) usa OAuth 2.0 para permitir autorizar el acceso a aplicaciones web y API web en el inquilino de Azure AD. En esta guía se explica cómo autenticar la aplicación con C#. El flujo del código de autorización de OAuth 2.0 se describe en la sección 4.1 de la especificación de OAuth 2.0. Para obtener más información, vea [Autorización del acceso a aplicaciones web mediante OAuth 2.0 y Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code).


## <a name="azure-keyvault"></a>Azure Key Vault

El siguiente proceso usa un método privado para procesar y convertir una clave de aplicación. Este método privado se ha denominado SecureString. Como alternativa, podría utilizar Azure Key Vault para almacenar la clave de la aplicación. Para más información, vea [Key Vault](https://azure.microsoft.com/services/key-vault/).

## <a name="create-a-web-app"></a>Creación de una aplicación web

En esta sección, se proporciona información sobre la aplicación web a la que le gustaría apuntar en Intune. Una aplicación web es una aplicación cliente-servidor. El servidor proporciona la aplicación web, que incluye la interfaz de usuario, el contenido y la funcionalidad. Este tipo de aplicación se mantiene por separado en la Web. Use Intune para conceder acceso a la aplicación web a Intune. La aplicación web inicia el flujo de datos. 

1.  Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2.  En el campo **Buscar recursos, servicios y documentos** situado en la parte superior de Azure Portal, busque **Azure Active Directory**.
3.  En el menú desplegable, seleccione **Azure Active Directory** en **Servicios**.
4.  Seleccione **Registros de aplicaciones**.
5.  Haga clic en **Nuevo registro de aplicaciones** para que se abra la hoja **Crear**.
6.  En la hoja **Crear**, agregue los detalles de la aplicación:

    - Un nombre de aplicación, como *Autenticación de solo aplicación de Intune*.
    - El **tipo de aplicación**. Elija **Aplicación web o API** para agregar una aplicación que represente una aplicación web, una API web o ambas.
    - La dirección **URL de inicio de sesión** de la aplicación. Esta es la ubicación a la que los usuarios navegan durante el proceso de autenticación. Esta información es necesaria para probar que los usuarios son quienes dicen ser. Para más información, vea [¿Qué es el acceso a aplicaciones y el inicio de sesión único con Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)

7.  Haga clic en **Crear** en la parte inferior de la hoja **Crear**.

    >[!NOTE] 
    > Copie el **Id. de la aplicación** de la hoja **Aplicación registrada** para usarlo más adelante.

## <a name="create-a-key"></a>Creación de una clave

En esta sección, Azure AD genera un valor de clave para la aplicación.

1.  En la hoja **Registros de aplicaciones**, seleccione la aplicación que acaba de crear para mostrar la hoja de la aplicación.
2.  Seleccione **Configuración** en la parte superior de la hoja para que se abra la hoja **Configuración**.
3.  Seleccione **Claves** en la hoja **Configuración**.
4.  Agregue la **descripción** de la clave, una fecha de **vencimiento** y el **valor** de la clave.
5.  Haga clic en **Guardar** para guardar y actualizar las claves de la aplicación.
6.  Debe copiar el valor de clave generado (con codificación Base64).

    >[!NOTE] 
    > El valor de clave desaparece cuando cierra la hoja de **claves**. No puede recuperar la clave de esta hoja más tarde. Cópiela para usarla más adelante.

## <a name="grant-application-permissions"></a>Concesión de permisos a las aplicaciones

En esta sección, se conceden permisos a las aplicaciones.

1.  Seleccione **Permisos necesarios** en la hoja **Configuración**.
2.  Haga clic en **Agregar**.
3.  Seleccione **Agregar una API** para mostrar la hoja **Seleccionar una API**.
4.  Seleccione **Microsoft Intune API (MicrosoftIntuneAPI)** y después haga clic en **Seleccionar** en la hoja **Seleccionar una API**. Se selecciona el paso **Seleccionar permisos** y se abre la hoja **Habilitar acceso**.
5.  Elija la opción **Get data warehouse information from Microsoft Intune** (Obtener información del almacenamiento de datos de Microsoft Intune) en la sección **Permisos de la aplicación**.
6.  Haga clic en **Seleccionar** en la hoja **Habilitar acceso**.
7.  Haga clic en **Seleccionar** en la hoja **Habilitar acceso**.
8.  Haga clic en **Conceder permisos** en la hoja **Permisos necesarios** y haga clic en **Sí** cuando se le pida que actualice los permisos existentes que esta aplicación tiene.

## <a name="generate-token"></a>Generación de tokens

Con Visual Studio, cree un proyecto de aplicación de consola (.NET Framework) que admita .NET Framework y use C# como lenguaje de codificación.

1.  Seleccione **Archivo** > **Nuevo** > **Proyecto** para mostrar el cuadro de diálogo **Nuevo proyecto**.
2.  En el lado izquierdo, seleccione **Visual C#** para mostrar todos los proyectos de .NET Framework.
3.  Seleccione **Aplicación de consola (.NET Framework)** , agregue un nombre para la aplicación y después haga clic en **Aceptar** para crear la aplicación.
4.  En el **Explorador de soluciones**, seleccione **Program.cs** para mostrar el código.
5.  En el menú emergente, seleccione **Agregar** > **Nuevo elemento**. Se abre el cuadro de diálogo **Agregar nuevo elemento**.
6.  A la izquierda, en **Visual C#** , seleccione **Código**.
7.  Seleccione **Clase**, cambie el nombre de la clase por *IntuneDataWarehouseClass.cs* y haga clic en **Agregar**.
8.  Agregue el código siguiente al método <code>Main</code>:

    ``` csharp
         var applicationId = ConfigurationManager.AppSettings["appId"].ToString();
         SecureString applicationSecret = ConvertToSecureStr(ConfigurationManager.AppSettings["appKey"].ToString()); // Load as SecureString from configuration file or secret store (i.e. Azure KeyVault)
         var tenantDomain = ConfigurationManager.AppSettings["tenantDomain"].ToString();
         var adalContext = new AuthenticationContext($"https://login.windows.net/" + tenantDomain + "/oauth2/token");
    
         AuthenticationResult authResult = adalContext.AcquireTokenAsync(
             resource: "https://api.manage.microsoft.com/",
             clientCredential: new ClientCredential(
                 applicationId,
                 new SecureClientSecret(applicationSecret))).Result;
    ``` 

9. Agregue espacios de nombres adicionales con la incorporación del código siguiente en la parte superior del archivo de código:

    ``` csharp
     using System.Security;
     using Microsoft.IdentityModel.Clients.ActiveDirectory;
     using System.Configuration;
    ``` 

10. Después del método <code>Main</code>, agregue el siguiente método privado al proceso y convierta la clave de aplicación:

    ``` csharp
    private static SecureString ConvertToSecureStr(string appkey)
    {
        if (appkey == null)
            throw new ArgumentNullException("AppKey must not be null.");
    
        var secureAppKey = new SecureString();
    
        foreach (char c in appkey)
            secureAppKey.AppendChar(c);
    
        secureAppKey.MakeReadOnly();
        return secureAppKey;
    }
    ```

11. En el **Explorador de soluciones**, haga clic con el botón derecho en **Referencias** y después seleccione **Administrar paquetes NuGet**.
12. Busque *Microsoft.IdentityModel.Clients.ActiveDirectory* e instale el paquete NuGet de Microsoft relacionado.
13. En el **Explorador de soluciones**, seleccione y abra el archivo *App.config*.
14. Agregue la sección <code>appSettings</code>, para que el archivo XML aparezca como sigue:

    ``` xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup> 
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <appSettings>
          <add key="appId" value="App ID created from 'Create a Web App' procedure"/>
          <add key="appKey" value="Key created from 'Create a key' procedure" />
          <add key="tenantDomain" value="contoso.onmicrosoft.com"/>
        </appSettings>
    </configuration>
    ``` 

15. Actualice los valores <code>appId</code>, <code>appKey</code> y <code>tenantDomain</code> para que coincidan con los valores únicos relacionados con la aplicación.
16. Cree la aplicación.

    >[!NOTE] 
    > Para ver código de implementación adicional, vea el [ejemplo de código Intune-Data-Warehouse](https://github.com/Microsoft/Intune-Data-Warehouse/tree/master/Samples/CSharp ).

## <a name="next-steps"></a>Pasos siguientes
Para obtener más información sobre Azure Key Vault, revise [¿Qué es Azure Key Vault?](https://docs.microsoft.com/azure/key-vault/key-vault-whatis)

