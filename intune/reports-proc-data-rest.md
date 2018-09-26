---
title: Obtener datos de la API de almacenamiento de datos con un cliente de REST
titlesuffix: Microsoft Intune
description: Recupere datos de almacenamiento de datos de Intune mediante la API de RESTful.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: D6D15039-4036-446C-A58F-A5E18175720A
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2a79bac39e6d5529196d63394d86922a6d57bda5
ms.sourcegitcommit: bea4a81d262607c6e9dd1e26f5cd1a2faf7d051b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/14/2018
ms.locfileid: "45602221"
---
# <a name="get-data-from-the-intune-data-warehouse-api-with-a-rest-client"></a>Obtener datos de la API de almacenamiento de datos de Intune con un cliente de REST

Puede acceder al modelo de datos de almacenamiento de datos de Intune a través de puntos de conexión RESTful. Para obtener acceso a los datos, el cliente debe realizar la autorización con Microsoft Azure Active Directory (Azure AD) mediante OAuth 2.0. Para habilitar el acceso, configure una aplicación nativa en Azure y conceda permisos a la API de Microsoft Intune. El cliente local obtiene la autorización y después el cliente puede comunicarse con los puntos de conexión de almacenamiento de datos mediante la aplicación nativa.

Para configurar un cliente y obtener los datos de la API de almacenamiento de datos, debe hacer lo siguiente:

1. Crear una aplicación cliente como una aplicación nativa en Azure
3. Conceder acceso a la API de Microsoft Intune a la aplicación cliente
3. Crear un cliente REST local para obtener los datos

Haga lo siguiente para obtener información sobre la autorización y acceso de la API con un cliente de REST. En primer lugar, veremos cómo usar un cliente de REST genérico con Postman. Postman es una herramienta usada con frecuencia para la solución de problemas y el desarrollo de los clientes REST para trabajar con las API. Para obtener más información sobre Postman, consulte el sitio de [Postman](https://www.getpostman.com). Luego, veremos un ejemplo de código de C#. Se proporciona un ejemplo para autorizar un cliente y obtener datos de la API.

## <a name="create-a-client-app-as-a-native-app-in-azure"></a>Crear una aplicación cliente como una aplicación nativa en Azure

Cree una aplicación nativa en Azure. Esta aplicación nativa es la aplicación cliente. El cliente que se ejecuta en el equipo local hace referencia a la API de almacenamiento de datos de Intune cuando el cliente local solicita las credenciales.

1. Inicie sesión en Azure Portal para su inquilino. Elija **Azure Active Directory** > **Registros de aplicaciones** para abrir el panel **Registros de aplicaciones**.
2. Seleccione **Registro de aplicación nuevo**.
3. Escriba los detalles de la aplicación.
    1.  Escriba un nombre descriptivo, como "Cliente de almacenamiento de datos de Intune", para el **nombre**.
    2.  Seleccione **Nativo** para el **tipo de aplicación**.
    3.  Escriba una dirección URL para la **dirección URL de inicio de sesión**. Esta dirección dependerá del escenario específico. Si planea usar Postman, escriba `https://www.getpostman.com/oauth2/callback`. Se usará la devolución de llamada para el paso de la autenticación del cliente en Azure AD.
4.  Seleccione **Crear**.

     ![API de Almacenamiento de datos de Intune](./media/reports-get_rest_data_client_overview.png)

5. Anote el valor de **Id. de la aplicación**. Se usará el id. en la sección siguiente.

## <a name="grant-the-client-app-access-to-the-microsoft-intune-api"></a>Conceder acceso a la API de Microsoft Intune a la aplicación cliente

Ahora tiene una aplicación definida en Azure. Conceda acceso a la API de Microsoft Intune a la aplicación nativa.

1.  Seleccione la aplicación nativa. La aplicación tendrá un nombre parecido a **Cliente de almacenamiento de datos de Intune**.
2.  Seleccione **Permisos necesarios** en el panel **Configuración**.
3.  Haga clic en **Agregar** en el panel **Permisos necesarios**.
4.  Elija **Seleccionar una API**.
5.  Busque el nombre de la aplicación web. Se llama **API de Microsoft Intune**.
6.  Seleccione la aplicación en la lista.
7.  Elija **Seleccionar**.
8.  Marque la casilla **Permisos delegados** para agregar la opción **Obtener información del almacén de datos de Microsoft Intune**.

    ![Autorización del acceso: API de Microsoft Intune](./media/reports-get_rest_data_client_access.png)

9.  Elija **Seleccionar**.
10.  Seleccione **Listo**.
11.  Opcionalmente, seleccione **Conceder permisos** en el panel Permisos necesarios. Esto concederá acceso a todas las cuentas del directorio actual. Se impedirá que el cuadro de diálogo de consentimiento se muestre para cada usuario del inquilino. Para obtener más información, consulte [Integración de aplicaciones con Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications).
12.  Seleccione **Sí**.

## <a name="get-data-from-the-microsoft-intune-api-with-postman"></a>Obtener datos de la API de Microsoft Intune con Postman

Puede trabajar con la API de almacenamiento de datos de Intune mediante un cliente REST genérico como Postman. Postman puede proporcionar información sobre las características de la API y el modelo de datos subyacente de OData, así como solucionar problemas de la conexión a los recursos de la API. En esta sección, encontrará información sobre cómo generar un token de Auth2.0 para el cliente local. El cliente necesitará el token para autenticarse con Azure AD y tener acceso a los recursos de la API.

### <a name="information-you-will-need-to-make-the-call"></a>Información que necesitará para realizar la llamada

Necesita la información siguiente para realizar una llamada REST mediante Postman:

| Atributo        | Descripción                                                                                                                                                                          | Ejemplo                                                                                       |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| Dirección URL de devolución de llamada     | Use este parámetro como la dirección URL de devolución de llamada en la página de configuración de la aplicación.                                                                                                                              | https://www.getpostman.com/oauth2/callback                                                    |
| Nombre del token       | Una cadena que se usa para pasar las credenciales a la aplicación de Azure. El proceso genera el token para que pueda realizar una llamada a la API de almacenamiento de datos.                          | Portador                                                                                        |
| Dirección URL de autenticación         | Se trata de la dirección URL usada para autenticación. | https://login.microsoftonline.com/common/oauth2/authorize?resource=https://api.manage.microsoft.com/ |
| Dirección URL del token de acceso | Se trata de la dirección URL usada para conceder el token.                                                                                                                                              | https://login.microsoftonline.com/common/oauth2/token |
| Identificador de cliente        | Se trata de un elemento que ha creado y anotado al crear la aplicación nativa en Azure.                                                                                               | 4184c61a-e324-4f51-83d7-022b6a81b991                                                          |
| Ámbito (opcional) | En blanco                                                                                                                                                                               | Puede dejar el campo en blanco.                                                                     |
| Tipo de concesión       | El token es un código de autorización.                                                                                                                                                  | Código de autorización                                                                            |

### <a name="odata-endpoint"></a>Punto de conexión de OData

También se necesita el punto de conexión. Para obtener el punto de conexión de almacenamiento de datos, necesitará la dirección URL de fuente personalizada. Puede obtener el punto de conexión de OData del panel Almacenamiento de datos.

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. Seleccione **Configurar el almacenamiento de datos de Intune** en **Otras tareas**.
4. Copie la dirección URL de fuente personalizada en **Usar servicios de informes de terceros**. Debería tener un aspecto parecido a este: `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`

El punto de conexión sigue este formato: `https://fef.{yourtenant}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{entity}?api-version={verson-number}`.

Por ejemplo, la entidad **dates** tiene el siguiente aspecto:`https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=beta`

Para obtener más información, vea [Punto de conexión de la API de Almacenamiento de datos de Intune](reports-api-url.md).

### <a name="make-the-rest-call"></a>Realizar la llamada de REST

Para obtener un nuevo token de acceso de Postman, debe agregar la dirección URL de autorización de Azure AD, el Id. de cliente y el secreto de cliente. Postman cargará la página de autorización en la que tendrá que escribir sus credenciales.

#### <a name="add-the-information-used-to-request-the-token"></a>Agregar la información usada para solicitar el token

1.  Si aún no lo ha instalado, descargue Postman. Para descargar Postman, vaya a [www.getpostman](https://www.getpostman.com).
2.  Abra Postman. Elija la operación HTTP **GET**.
3.  Pegue la dirección URL del punto de conexión en la dirección. Debería tener un aspecto parecido a este:  

    `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=beta`
4.  Seleccione la pestaña **Autorización** y elija **OAuth 2.0** en la lista **Tipo**.
5.  Seleccione **Obtener token de acceso nuevo**.
6.  Compruebe que ya haya agregado la dirección URL de devolución de llamada a la aplicación en Azure. La dirección URL de devolución de llamada es `https://www.getpostman.com/oauth2/callback`.
7.  Escriba Portador en el campo **Nombre del token**.
8.  Agregue la **dirección URL de autenticación**. Debería tener un aspecto parecido a este:  

    `https://login.microsoftonline.com/common/oauth2/authorize?resource=https://api.manage.microsoft.com/`
9.  Agregue la **dirección URL de token de acceso**. Debería tener un aspecto parecido a este:  

     `https://login.microsoftonline.com/common/oauth2/token`

10. Agregue el **Id. de cliente** desde la aplicación nativa que ha creado en Azure, que se llama `Intune Data Warehouse Client`. Debería tener un aspecto parecido a este:  

     `88C8527B-59CB-4679-A9C8-324941748BB4`

11. Seleccione **Código de autorización** y Solicitar token de acceso localmente.

12. Seleccione **Solicitar token**.

    ![Información para el token](./media/reports-postman_getnewtoken.png)

13. Escriba sus credenciales en la página de autorización de Azure AD. La lista de tokens en Postman contiene ahora el token con el nombre `Bearer`.
14. Seleccione **Usar token**. La lista de encabezados contiene el nuevo valor de clave de autorización y el valor `Bearer <your-authorization-token>`.

#### <a name="send-the-call-to-the-endpoint-using-postman"></a>Enviar la llamada al punto de conexión mediante Postman

1.  Seleccione **Enviar**.
2.  Los datos devueltos se muestran en el cuerpo de la respuesta de Postman.

    ![Postman 200OK](./media/reports-postman_200OK.png)

## <a name="create-a-rest-client-c-to-get-data-from-the-intune-data-warehouse"></a>Crear un cliente REST (C#) para obtener datos desde el almacén de datos de Intune

El ejemplo siguiente contiene un cliente REST simple. El código usa la clase **httpClient** de la biblioteca .NET. Una vez que el cliente obtenga las credenciales a Azure AD, el cliente construirá una llamada GET REST para recuperar la entidad de fechas de la API de almacenamiento de datos.

> [!Note]  
> Se puede acceder a la [muestra de código siguiente en GitHub](https://github.com/Microsoft/Intune-Data-Warehouse/blob/master/Samples/CSharp/Program.cs). Consulte el repositorio de GitHub para conocer los cambios más recientes y las actualizaciones del ejemplo.

1. Abra **Microsoft Visual Studio**.
2. Elija **Archivo** > **Proyecto nuevo**. Expanda **Visual C#** y elija **Aplicación de consola (.NET Framework)**.
3. Asigne el nombre ` IntuneDataWarehouseSamples` al proyecto, vaya a la ubicación donde quiera guardarlo y, después, seleccione **Aceptar**.
4. Haga clic con el botón derecho en el nombre de la solución en el Explorador de soluciones y después seleccione **Administrar paquetes de NuGet para la solución**. Seleccione **Examinar** y, después, escriba `Microsoft.IdentityModel.Clients.ActiveDirectory` en el cuadro de búsqueda.
5. Elija el paquete, seleccione el proyecto **IntuneDataWarehouseSamples** en Administrar paquetes para la solución y, luego, seleccione **Instalar**.
6. Seleccione **Acepto** para aceptar la licencia del paquete de NuGet.
7. Abra `Program.cs` desde el Explorador de soluciones.

    ![Proyecto en Visual Studio](./media/reports-get_rest_data_in.png)

8. Reemplace el código de Program.cs por el código siguiente:  
   ```csharp
   namespace IntuneDataWarehouseSamples
   {
   using System;
   using System.Net.Http;
   using System.Net.Http.Headers;
   using Microsoft.IdentityModel.Clients.ActiveDirectory;

   class Program
   {
    static void Main(string[] args)
   {
   /**
   * TODO: Replace the below values with your own.
   * emailAddress - The email address of the user that you will authenticate as.
   *
   * password  - The password for the above email address.
   *    This is inline only for simplicity in this sample. We do not
   *    recommend storing passwords in plaintext.
   *
   * applicationId - The application ID of the native app that was created in AAD.
   *
   * warehouseUrl   - The data warehouse URL for your tenant. This can be found in
   *      the Azure portal.
   *
   * collectionName - The name of the warehouse entity collection you would like to
   *      access.
   */
   var emailAddress = "intuneadmin@yourcompany.com";
   var password = "password_of(intuneadmin@yourcompany.com)";
   var applicationId = "<Application ID>";
   var warehouseUrl = "https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta";
   var collectionName = "dates";

   var adalContext = new AuthenticationContext("https://login.windows.net/common/oauth2/token");
   AuthenticationResult authResult = adalContext.AcquireTokenAsync(
   resource: "https://api.manage.microsoft.com/",
   clientId: applicationId,
   userCredential: new UserPasswordCredential(emailAddress, password)).Result;

   var httpClient = new HttpClient();
   httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", authResult.AccessToken);

   var uriBuilder = new UriBuilder(warehouseUrl);
   uriBuilder.Path += "/" + collectionName;

   HttpResponseMessage response = httpClient.GetAsync(uriBuilder.Uri).Result;

   Console.Write(response.Content.ReadAsStringAsync().Result);
   Console.ReadKey();
   }
   }
   ```

9. Actualice los elementos `TODO` en el ejemplo de código.
10. Presione **Ctrl + F5** para compilar y ejecutar el cliente de Intune.DataWarehouseAPIClient en modo de depuración.

    ![Entidad de fecha recuperada en formato JSON](./media/reports-get_rest_data_output.png)

11. Revise la salida de la consola. La salida contiene datos en un formato JSON extraído de la entidad **Fechas** en el inquilino de Intune.

## <a name="next-steps"></a>Pasos siguientes

Puede encontrar información sobre la autorización, la estructura de la dirección URL de la API y los puntos de conexión de OData en [Use the Intune Data Warehouse API (Usar la API de almacenamiento de datos de Intune)](reports-api-url.md).

También puede consultar el modelo de datos del almacenamiento de datos de Intune para buscar las entidades de datos contenidas en la API. Para obtener más información, consulte [Intune Data Warehouse API Data Model (Modelo de datos de la API de almacenamiento de datos de Intune)](reports-ref-data-model.md).
