---
title: Uso de API para incorporar entidades de certificación de terceros - Microsoft Intune - Azure | Microsoft Docs
description: Agregue o integre la solución de GitHub de SCEP para que las entidades de certificación (CA) de terceros emitan certificados SCEP para dispositivos de Microsoft Intune. En esta solución se incluyen las API de Java y C# que validan, envían notificaciones correctas y de error a Intune, y usan el generador de sockets SSL al comunicarse con Intune. También se proporciona una introducción de los pasos para probar la configuración de la entidad de certificación SCEP.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5278b631d581c892f68e8ba08c2bc7893cd3782a
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321747"
---
# <a name="use-apis-to-add-third-party-cas-for-scep-to-intune"></a>Uso de API para agregar entidades de certificación de terceros para SCEP en Intune

En Microsoft Intune, puede agregar entidades de certificación (CA) de terceros y hacer que emitan y validen certificados mediante el Protocolo de inscripción de certificados simple (SCEP). En [Add third-party certification authority](certificate-authority-add-scep-overview.md) (Adición de entidades de certificación de terceros) se proporciona información general sobre esta característica y se describen las tareas de administrador en Intune.

También hay algunas tareas para desarrolladores que usan una biblioteca de código abierto que Microsoft ha publicado en GitHub.com. En la biblioteca se incluye una API que:

- Valida la contraseña SCEP que se genera de forma dinámica mediante Intune.
- Notifica a Intune los certificados creados en los dispositivos que envían solicitudes de SCEP.

Con esta API, el servidor SCEP de terceros se integra con la solución de administración de SCEP de Intune para dispositivos de MDM. La biblioteca abstrae de sus usuarios aspectos como la autenticación, la ubicación del servicio y la API del servicio OData de Intune.

## <a name="scep-management-solution"></a>Solución de administración de SCEP

![Integración de SCEP de entidades de certificación de terceros con Microsoft Intune](./media/scep-certificate-vendor-integration.png)

Con Intune, los administradores crean perfiles SCEP y, después, los asignan a dispositivos MDM. Los perfiles SCEP incluyen parámetros como:

- La dirección URL del servidor SCEP.
- El Certificado raíz de confianza de la entidad de certificación.
- Atributos de certificado y más.

El perfil SCEP se asigna a los dispositivos que se registran en Intune, y se configuran con estos parámetros. Intune crea una contraseña de SCEP generada de forma dinámica y, después, la asigna al dispositivo.

Esta contraseña contiene detalles sobre los parámetros que se esperan en la solicitud de firma de certificado (CSR) que el dispositivo emite al servidor SCEP. La contraseña también incluye la hora de expiración del desafío. Intune cifra la información, firma el blob cifrado y, después, empaqueta estos detalles en la contraseña de SCEP.

Los dispositivos que se ponen en contacto con el servidor SCEP para solicitar un certificado proporcionan después esta contraseña de SCEP. Esta contraseña debe pasar la validación para que el servidor SCEP emita un certificado para el dispositivo. Cuando se valida una contraseña de SCEP, se producen las comprobaciones siguientes:

- Se valida la firma del blob cifrado.
- Se valida que el desafío no haya expirado.
- Se valida que el perfil todavía está destinado al dispositivo.
- Se valida que las propiedades del certificado solicitadas por el dispositivo en la CSR coincidan con los valores esperados.

La solución de administración de SCEP también incluye informes. Un administrador puede obtener información sobre el estado de implementación del perfil SCEP y sobre los certificados emitidos para los dispositivos.

## <a name="integrate-with-intune"></a>Integración con Intune

El código de la biblioteca para integrarla con el SCEP de Intune está disponible para descargarlo en el [repositorio Microsoft/Intune-Resource-Access de GitHub](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation).

La integración de la biblioteca en los productos incluye los pasos que se indican a continuación. Estos pasos requieren conocimientos sobre cómo trabajar con repositorios de GitHub y crear soluciones y proyectos en Visual Studio.

1. Regístrese para recibir notificaciones del repositorio.
2. Clone o descargue el repositorio.
3. Vaya a la implementación de biblioteca que necesita en la carpeta `\src\CsrValidation` (https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation).
4. Compile la biblioteca con las instrucciones del archivo Léame.
5. Incluya la biblioteca en el proyecto que genera el servidor SCEP.
6. Complete las tareas siguientes en el servidor SCEP:

    - Permita que el administrador configure el [identificador de aplicación de Azure, la clave de aplicación de Azure y el identificador de inquilino](#onboard-scep-server-in-azure) (en este artículo) que la biblioteca usa para la autenticación. Se debe permitir a los administradores actualizar la clave de aplicación de Azure.
    - Identifique las solicitudes SCEP que incluyen una contraseña de SCEP generada por Intune.
    - Use la biblioteca de la **API Validate Request** para validar las contraseñas de SCEP generadas por Intune.
    - Use las API de notificación de biblioteca para notificar a Intune los certificados emitidos para las solicitudes SCEP que tienen las contraseñas de SCEP generadas por Intune. También debe notificar a Intune los errores que puedan producirse al procesar estas solicitudes SCEP.
    - Confirme que el servidor registra la información suficiente para ayudar a los administradores a solucionar problemas.

7. Complete las [pruebas de integración](#integration-testing) (en este artículo) y solucione cualquier problema.
8. Proporcione instrucciones escritas al cliente en las que se explique:

    - Cómo se debe incorporar el servidor SCEP a Azure Portal.
    - Cómo obtener el identificador de aplicación de Azure y la clave de aplicación de Azure necesarios para configurar la biblioteca.

### <a name="onboard-scep-server-in-azure"></a>Incorporar el servidor SCEP en Azure

Para autenticarse en Intune, el servidor SCEP requiere un identificador de aplicación de Azure, una clave de aplicación de Azure y un identificador de inquilino. El servidor SCEP también necesita autorización para acceder a la API de Intune.

Para obtener estos datos, el administrador del servidor SCEP inicia sesión en Azure Portal, registra la aplicación, le proporciona el permiso **API de Microsoft Intune/validación de desafío de SCEP**, crea una clave para la aplicación y, después, descarga el identificador de aplicación, su clave y el identificador del inquilino.

Para obtener instrucciones sobre cómo registrar una aplicación y obtener los identificadores y las claves, vea [Uso del portal para crear una aplicación de Azure Active Directory y una entidad de servicio con acceso a los recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).

### <a name="java-library-api"></a>API de bibliotecas de Java

La biblioteca de Java se implementa como un proyecto de Maven que extrae sus dependencias cuando se compila. La API se implementa por la clase `IntuneScepServiceClient` en el espacio de nombres `com.microsoft.intune.scepvalidation`.

#### <a name="intunescepserviceclient-class"></a>Clase IntuneScepServiceClient

La clase `IntuneScepServiceClient` incluye los métodos que usa el servicio SCEP para validar las contraseñas de SCEP, para notificar a Intune los certificados que se crean y para mostrar los errores.

##### <a name="intunescepserviceclient-constructor"></a>Constructor IntuneScepServiceClient

Firma:

```java
IntuneScepServiceClient(
    Properties configProperties)
```

Descripción:

Crea una instancia de un objeto `IntuneScepServiceClient` y lo configura.

Parámetros:

    - configProperties    Objeto de propiedades que contiene información de configuración de cliente

La configuración debe incluir las propiedades siguientes:

    - AAD_APP_ID="El Id. de aplicación de Azure se obtiene durante el proceso de incorporación"
    - AAD_APP_KEY="La clave de aplicación de Azure se obtiene durante el proceso de incorporación"
    - TENANT="El Id. de inquilino se obtiene durante el proceso de incorporación"
    - PROVIDER_NAME_AND_VERSION="Información que se usa para identificar el producto y su versión"

Inicia:

    - IllegalArgumentException    Se inicia si el constructor se ejecuta sin un objeto de propiedad adecuado.

> [!IMPORTANT]
> Es mejor crear una instancia de esta clase y usarla para procesar varias solicitudes SCEP. Al hacerlo se reduce la sobrecarga, dado que los tokens de autenticación y la información de ubicación de servicio se almacenan en caché.

**Notas de seguridad**  
El implementador del servidor SCEP debe proteger contra la divulgación y la alteración los datos escritos en las propiedades de configuración guardadas en el almacenamiento. Se recomienda usar las listas de control de acceso adecuadas y el cifrado para proteger la información.

##### <a name="validaterequest-method"></a>Método ValidateRequest

Firma:

```java
void ValidateRequest(
    String transactionId,
    String certificateRequest)
```

Descripción:

Valida una solicitud de certificado SCEP.

Parámetros:

    - transactionId         El Id. de transacción de SCEP
    - certificateRequest    Cadena codificada en Base64 de solicitud de certificado PKCS #10 con codificación DER

Inicia:

    - IllegalArgumentException      Se inicia si se llama con un parámetro que no es válido
    - IntuneScepServiceException    Se inicia si se comprueba que la solicitud de certificado no es válida
    - Exception                     Se inicia si se produce un error inesperado.

> [!IMPORTANT]
> El servidor debe registrar las excepciones iniciadas por este método. Tenga en cuenta que las propiedades `IntuneScepServiceException` disponen de información detallada sobre el motivo del error de validación de la solicitud de certificado.

**Notas de seguridad**  

  - Si este método inicia una excepción, el servidor SCEP **no debe** emitir un certificado para el cliente.
  - Los errores de validación de solicitud de certificado SCEP pueden indicar un problema en la infraestructura de Intune. O bien, podrían indicar que un atacante está intentando obtener un certificado.

##### <a name="sendsuccessnotification-method"></a>Método SendSuccessNotification

Firma:

```java
void SendSuccessNotification(
    String transactionId,
    String certificateRequest,
    String certThumbprint,
    String certSerialNumber,
    String certExpirationDate,
    String certIssuingAuthority)
```

Descripción:

Notifica a Intune que se crea un certificado como parte del procesamiento de una solicitud SCEP.

Parámetros:

    - transactionId           Id. de transacción de SCEP
    - certificateRequest     Cadena codificada en Base64 de solicitud de certificado PKCS #10 con codificación DER
    - certThumprint          Huella digital del certificado aprovisionado
    - certSerialNumber       Número de serie del certificado aprovisionado
    - certExpirationDate     Fecha de expiración del certificado aprovisionado La cadena de fecha y hora debe tener el formato web de hora UTC (AAAA-MM-DDThh:mm:ss.sssTZD) ISO 8601.
    - certIssuingAuthority    Nombre de la entidad que ha emitido el certificado

Inicia:

    - IllegalArgumentException      Se inicia si se llama con un parámetro que no es válido.
    - IntuneScepServiceException    Se inicia si se comprueba que la solicitud de certificado no es válida.
    - Exception                     Se inicia si se produce un error inesperado.

> [!IMPORTANT]
> El servidor debe registrar las excepciones iniciadas por este método. Tenga en cuenta que las propiedades `IntuneScepServiceException` disponen de información detallada sobre el motivo del error de validación de la solicitud de certificado.

**Notas de seguridad**

  - Si este método inicia una excepción, el servidor SCEP **no debe** emitir un certificado para el cliente.
  - Los errores de validación de solicitud de certificado SCEP pueden indicar un problema en la infraestructura de Intune. O bien, podrían indicar que un atacante está intentando obtener un certificado.

##### <a name="sendfailurenotification-method"></a>Método SendFailureNotification

Firma:

```java
void SendFailureNotification(
    String transactionId,
    String certificateRequest,
    long  hResult,
    String errorDescription)
```

Descripción:

Notifica a Intune que se ha producido un error al procesar una solicitud SCEP. Este método no se debe invocar para las excepciones iniciadas por los métodos de esta clase.

Parámetros:

    - transactionId         Id. de transacción de SCEP
    - certificateRequest    Cadena codificada en Base64 de solicitud de certificado PKCS #10 con codificación DER
    - hResult               Código de error Win32 que mejor describe el error detectado Vea [Win32 Error Codes](https://msdn.microsoft.com/library/cc231199.aspx) (Códigos de error Win32)
    - errorDescription     Descripción del error encontrado

Inicia:

    - IllegalArgumentException      Se inicia si se llama con un parámetro que no es válido.
    - IntuneScepServiceException    Se inicia si se comprueba que la solicitud de certificado no es válida.
    - Exception                     Se inicia si se produce un error inesperado.

> [!IMPORTANT]
> El servidor debe registrar las excepciones iniciadas por este método. Tenga en cuenta que las propiedades `IntuneScepServiceException` disponen de información detallada sobre el motivo del error de validación de la solicitud de certificado.

**Notas de seguridad**

  - Si este método inicia una excepción, el servidor SCEP **no debe** emitir un certificado para el cliente.
  - Los errores de validación de solicitud de certificado SCEP pueden indicar un problema en la infraestructura de Intune. O bien, podrían indicar que un atacante está intentando obtener un certificado.

##### <a name="setsslsocketfactory-method"></a>Método SetSslSocketFactory

Firma:

```java
void SetSslSocketFactory(
    SSLSocketFactory factory)
```

Descripción:

Use este método para informar al cliente que debe usar el generador de sockets SSL especificado (en lugar del predeterminado) cuando se comunique con Intune.

Parámetros:

    - factory    Generador de sockets SSL que el cliente debe usar para las solicitudes HTTPS

Inicia:

    - IllegalArgumentException     Se inicia si se llama con un parámetro que no es válido

> [!NOTE]
> El generador de sockets SSL se debe establecer si es necesario antes de ejecutar los otros métodos de esta clase.

## <a name="integration-testing"></a>Pruebas de integración

Es obligatorio validar y comprobar que la solución se integra correctamente con Intune. A continuación se muestra una introducción de los pasos:

1. Configure una [cuenta de evaluación de Intune](account-sign-up.md).
2. Incorpore el [servidor SCEP en Azure Portal](#onboard-scep-server-in-azure) (en este artículo).
3. [Configure el servidor SCEP](certificates-scep-configure.md) con los identificadores y la clave creados al incorporar el servidor SCEP.
4. [Inscriba dispositivos](device-enrollment.md) para probar los escenarios en la [matriz de pruebas de escenarios](https://github.com/Microsoft/Intune-Resource-Access/blob/develop/src/CsrValidation/doc/TestMatrix.csv).
5. [Cree un perfil de certificado raíz de confianza](certificates-scep-configure.md) para probar la entidad de certificación.
6. Cree perfiles SCEP para probar los escenarios enumerados en la [matriz de pruebas de escenarios](https://github.com/Microsoft/Intune-Resource-Access/blob/develop/src/CsrValidation/doc/TestMatrix.csv).
7. [Asigne los perfiles](device-profile-assign.md) a los usuarios que inscribieron sus dispositivos.
8. Espere a que los dispositivos se sincronicen con Intune. O bien, [sincronice los dispositivos](device-sync.md) de forma manual.
9. Confirme que el certificado raíz de confianza y los [perfiles SCEP se implementan en los dispositivos](device-profile-monitor.md).
10. Confirme que el certificado raíz de confianza está instalado en todos los dispositivos.
11. Confirme que los certificados SCEP para los perfiles asignados están instalados en todos los dispositivos.
12. Confirme que las propiedades de los certificados instalados coinciden con las propiedades establecidas en el perfil SCEP.
13. Confirme que los certificados emitidos aparecen correctamente en la consola de Intune.

## <a name="see-also"></a>Vea también

- [Información general para agregar entidades de certificación de terceros](certificate-authority-add-scep-overview.md)
- [Configuración de Intune](setup-steps.md)
- [Inscripción de dispositivos](device-enrollment.md)
- [Configurar perfiles de certificado SCEP](certificates-scep-configure.md#create-a-scep-certificate-profile) (el programa de instalación de Microsoft NDES Server\Connector no se usa para este escenario)
