---
title: 'Uso de entidades de certificación (CA) de terceros con SCEP en Microsoft Intune: Azure | Microsoft Docs'
description: En Microsoft Intune, puede agregar una entidad de certificación (CA) del proveedor o de terceros para emitir certificados para dispositivos móviles mediante el protocolo SCEP. En esta introducción, una aplicación de Azure Active Directory (Azure AD) proporciona permisos a Microsoft Intune para validar los certificados. Después, se usa el identificador de aplicación, la clave de autenticación y el identificador de inquilino de la aplicación de AAD en la configuración del servidor SCEP para emitir certificados.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e8df5f46f411a6aee1c3040fa4a1a37fb49d5fb2
ms.sourcegitcommit: fca2670142c083d7562c0a36547a6a451863e315
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/08/2019
ms.locfileid: "72036432"
---
# <a name="add-partner-certification-authority-in-intune-using-scep"></a>Adición de entidades de certificación de asociado en Intune mediante SCEP

Uso de entidades de certificación de terceros (CA) con Intune. Las entidades de certificación de terceros pueden aprovisionar dispositivos móviles con certificados nuevos o renovados mediante el Protocolo de inscripción de certificados simple (SCEP) y pueden admitir dispositivos Windows, iOS, Android y macOS.

El uso de esta característica tiene dos partes: la API de código abierto y las tareas de administrador de Intune.

**Parte 1: Uso de una API de código abierto**  
Microsoft ha creado una API para integrarse con Intune. Mediante la API, puede validar los certificados, enviar notificaciones correctas o de error, y usar SSL, en concreto el generador de sockets SSL, para comunicarse con Intune.

La API está disponible en el [repositorio público de GitHub de la API de SCEP de Intune](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation) para descargar y usar en las soluciones. Use esta API con servidores SCEP de terceros para ejecutar la validación de la comprobación personalizada en Intune antes de entregar un certificado a un dispositivo.

En [Integración con soluciones de administración SCEP de Intune](scep-libraries-apis.md) se proporcionan más detalles sobre cómo usar la API, sus métodos y probar la solución que se compila.

**Parte 2: Creación de la aplicación y el perfil**  
Con una aplicación de Azure Active Directory (Azure AD), se pueden delegar derechos a Intune para que controle las solicitudes SCEP procedentes de los dispositivos. En la aplicación de Azure AD se incluyen los valores de identificador de aplicación y clave de autenticación que se usan en la solución de API que crea el desarrollador. Los administradores crean e implementan los perfiles de certificados de SCEP con Intune y pueden ver los informes sobre el estado de la implementación en los dispositivos.

En este artículo se proporciona información general de esta característica desde la perspectiva del administrador, incluida la creación de la aplicación de Azure AD.

## <a name="overview"></a>Introducción

Los pasos siguientes proporcionan una visión general del uso de SCEP para certificados en Intune:

1. En Intune, un administrador crea un perfil de certificado SCEP y, después, lo destina a los usuarios o dispositivos.
2. El dispositivo se registra con Intune.
3. Intune crea un desafío SCEP único. También agrega información de comprobación de integridad adicional, como por ejemplo cuál debe ser el asunto esperado y el SAN.
4. Intune cifra y firma el desafío y la información de comprobación de integridad y, después, la envía al dispositivo con la solicitud SCEP.
5. El dispositivo genera una solicitud de firma de certificado (CSR) y el par de clave pública o privada en el dispositivo según el perfil de certificado SCEP que se inserta desde Intune.
6. La CSR y el desafío cifrado y firmado se envían al punto de conexión del servidor SCEP de terceros.
7. El servidor SCEP envía la CSR y el desafío a Intune. Después, Intune valida la firma, descifra la carga y compara la CSR con la información de comprobación de integridad.
8. Intune devuelve una respuesta al servidor SCEP e indica si la validación de la comprobación es correcta o no.  
9. Si se ha comprobado correctamente el desafío, el servidor SCEP emite el certificado para el dispositivo.

En el diagrama siguiente se muestra un flujo detallado de la integración de SCEP de terceros con Intune:

![Integración de SCEP de entidades de certificación de terceros con Microsoft Intune](./media/certificate-authority-add-scep-overview/scep-certificate-vendor-integration.png)

## <a name="set-up-third-party-ca-integration"></a>Configurar la integración de la entidad de certificación de terceros

### <a name="validate-third-party-certification-authority"></a>Validar la entidad de certificación de terceros

Antes de integrar las entidades de certificación de terceros con Intune, confirme que la entidad de certificación que se usa es compatible con Intune. En [Asociados de entidad de certificación de terceros](#third-party-certification-authority-partners) (en este artículo) se incluye una lista. También puede consultar las instrucciones de la entidad de certificación para obtener más información. Es posible que la entidad de certificación incluya instrucciones de configuración específicas de su implementación.

### <a name="authorize-communication-between-ca-and-intune"></a>Autorizar la comunicación entre Intune y la entidad de certificación

Para permitir que un servidor SCEP de terceros ejecute la validación de desafío personalizada con Intune, cree una aplicación en Azure AD. Esta aplicación otorga derechos delegados a Intune para validar las solicitudes SCEP.

Asegúrese de que tiene los permisos necesarios para registrar una aplicación de Azure AD. Consulte [Permisos necesarios](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions) en la documentación de Azure AD.

#### <a name="create-an-application-in-azure-active-directory"></a>Creación de una aplicación en Azure Active Directory  

1. En [Azure Portal](https://portal.azure.com), vaya a **Azure Active Directory** > **Registros de aplicaciones** y seleccione **Nuevo registro**.  

2. En la página **Registrar una aplicación**, especifique estos detalles:  
   - En la sección **Nombre**, escriba un nombre significativo para la aplicación.  
   - Para la sección **Supported account types** (Tipos de cuenta admitidos), seleccione **Accounts in any organizational directory** (Cuentas en cualquier directorio organizativo).  
   - En **URI de redireccionamiento**, deje el valor predeterminado de Web y, luego, especifique la dirección URL de inicio de sesión para el servidor SCEP de terceros.  

3. Seleccione **Registrar** para crear la aplicación y abrir la página de información general de la aplicación nueva.  

4. En la página **Información general** de la aplicación, copie el valor de **Application (client) ID** (Identificador de aplicación [cliente]) y anótelo para usarlo más adelante. Lo necesitará más adelante.  

5. En el panel de navegación de la aplicación, vaya a **Certificates & secrets** (Certificados y secretos) en **Administrar**. Seleccione el botón **Nuevo secreto de cliente**. Escriba un valor en Descripción, seleccione cualquier opción para **Expira** y elija **Agregar** para generar un *valor* para el secreto de cliente. 
   > [!IMPORTANT]  
   > Antes de salir de la página, copie el valor del secreto de cliente y anótelo para usarlo más adelante con la implementación de la CA de terceros. Este valor no se volverá a mostrar. No olvide revisar las instrucciones correspondientes a la CA de terceros sobre cómo se configuran el identificador de la aplicación, la clave de autenticación y el identificador de inquilino.  

6. Anote el **identificador de inquilino**. El identificador de inquilino es el texto de dominio después del signo @ de la cuenta. Por ejemplo, si la cuenta es *admin@name.onmicrosoft.com* , entonces el identificador de inquilino es **name.onmicrosoft.com**.  

7. En el panel de navegación de la aplicación, vaya a **Permisos de API** en **Administrar** y seleccione **Agregar un permiso**.  

8. En la página **Request API permissions** (Solicitar permisos de API), seleccione **Intune** y, luego, **Permisos de aplicación**. Active la casilla **scep_challenge_provider** (validación del desafío SCEP).  

   Seleccione **Agregar permisos** para guardar esta configuración.  

9. Permanezca en la página **Permisos de API**, seleccione **Grant admin consent for Microsoft** (Conceder el consentimiento del administrador para Microsoft) y seleccione **Sí**.  
   
   El proceso de registro de la aplicación en Azure AD se completó.





### <a name="configure-and-deploy-a-scep-certificate-profile"></a>Configurar e implementar un perfil de certificado SCEP
Como administrador, cree un perfil de certificado SCEP destinado a los usuarios o dispositivos. Después, asigne el perfil.

- [Creación de un perfil de certificado SCEP](certificates-profile-scep.md#create-a-scep-certificate-profile)

- [Asignar el perfil de certificado](certificates-profile-scep.md#assign-the-certificate-profile)

## <a name="removing-certificates"></a>Eliminación de certificados

Al anular la inscripción o borrar el dispositivo, se quitan los certificados. Los certificados no se revocan.

## <a name="third-party-certification-authority-partners"></a>Asociados de entidad de certificación de terceros
Las entidades de certificación de terceros siguientes son compatibles con Intune:

- [Entrust Datacard](https://info.entrustdatacard.com/pki-eval-tool)
- [Versión de código abierto de GitHub EJBCA](https://github.com/agerbergt/intune-ejbca-connector)
- [EverTrust](https://evertrust.fr/en/products/)
- [GlobalSign](https://downloads.globalsign.com/acton/attachment/2674/f-6903f60b-9111-432d-b283-77823cc65500/1/-/-/-/-/globalsign-aeg-microsoft-intune-integration-guide.pdf)
- [IDnomic](https://www.idnomic.com/)
- [Sectigo](https://sectigo.com/products)
- [DigiCert](https://knowledge.digicert.com/tutorials/microsoft-intune.html)
- [Venafi](https://www.venafi.com/platform/enterprise-mobility)
- [SCEPman](https://azuremarketplace.microsoft.com/marketplace/apps/gluckkanja.scepman)

Si es una entidad de certificación de terceros interesada en la integración de su producto con Intune, revise las instrucciones de la API:

- [Repositorio de la API de SCEP de Intune en GitHub](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Instrucciones de la API de SCEP de Intune para las entidades de certificación de terceros](scep-libraries-apis.md)

## <a name="see-also"></a>Consulte también

- [Configuración de perfiles de certificado](certificates-scep-configure.md)
- [Repositorio de la API de SCEP de Intune en GitHub](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Instrucciones de la API de SCEP de Intune para las entidades de certificación de terceros](scep-libraries-apis.md)
