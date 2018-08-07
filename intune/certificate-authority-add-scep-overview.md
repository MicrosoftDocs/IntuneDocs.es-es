---
title: 'Uso de entidades de certificación de terceros con SCEP en Microsoft Intune: Azure | Microsoft Docs'
description: En Microsoft Intune, puede agregar una entidad de certificación (CA) de proveedor o terceros para emitir certificados para dispositivos móviles mediante el protocolo SCEP. En esta introducción, una aplicación de Azure Active Directory (Azure AD) proporciona permisos a Microsoft Intune para validar los certificados. Después, se usa el identificador de aplicación, la clave de autenticación y el identificador de inquilino de la aplicación de AAD en la configuración del servidor SCEP para emitir certificados.
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
ms.openlocfilehash: ee5a39ee8a146fbc6a85a9f4438b8e14a408a735
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321733"
---
# <a name="add-partner-certification-authority-in-intune-using-scep"></a>Adición de entidades de certificación de asociado en Intune mediante SCEP

En Microsoft Intune, se pueden agregar entidades de certificación (CA) de terceros. Estas entidades de certificación pueden proporcionar certificados a los dispositivos móviles mediante el Protocolo de inscripción de certificados simple (SCEP). Esta característica puede emitir certificados nuevos y renovar certificados en dispositivos Windows, iOS, Android y macOS.

El uso de esta característica tiene dos partes: la API de código abierto y las tareas de administrador de Intune.

**Parte 1: Uso de una API de código abierto**  
Microsoft ha creado una API que se integra con Intune para validar los certificados, enviar notificaciones correctas o de error, y usar SSL, en concreto el generador de sockets SSL, para comunicarse con Intune.

La API está disponible en el [repositorio público de GitHub de la API de SCEP de Intune](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation) para descargar y usar en las soluciones. Use esta API con otros servidores SCEP para ejecutar la validación de la comprobación personalizada en Intune antes de entregar un certificado a un dispositivo.

En [Integración con soluciones de administración SCEP de Intune](scep-libraries-apis.md) se proporcionan más detalles sobre cómo usar la API, sus métodos y probar la solución que se compila.

**Parte 2: Creación de la aplicación y el perfil**  
Con una aplicación de Azure Active Directory (Azure AD), se pueden delegar derechos a Intune para que controle las solicitudes SCEP procedentes de los dispositivos. En la aplicación de Azure AD se incluyen los valores de identificador de aplicación y clave de autenticación que se usan en la solución de API que crea el desarrollador. Después, los administradores pueden crear e implementar perfiles de certificados SCEP con Intune. También puede ver informes sobre el estado de implementación en los dispositivos.

En este artículo se proporciona información general de esta característica desde la perspectiva del administrador, incluida la creación de la aplicación de Azure AD.

## <a name="overview"></a>Introducción

Los pasos siguientes proporcionan una visión general de la emisión de certificados SCEP en Intune:

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

![Integración de SCEP de entidades de certificación de terceros con Microsoft Intune](./media/scep-certificate-vendor-integration.png)

## <a name="set-up-third-party-ca-integration"></a>Configurar la integración de la entidad de certificación de terceros

### <a name="validate-third-party-certification-authority"></a>Validar la entidad de certificación de terceros

Antes de integrar las entidades de certificación de terceros con Intune, confirme que la entidad de certificación que se usa es compatible con Intune. En [Asociados de entidad de certificación de terceros](#third-party-certification-authority-partners) (en este artículo) se incluye una lista. También puede consultar las instrucciones de la entidad de certificación para obtener más información. Es posible que la entidad de certificación incluya instrucciones de configuración específicas de su implementación.

### <a name="authorize-communication-between-ca-and-intune"></a>Autorizar la comunicación entre Intune y la entidad de certificación

Para permitir que un servidor SCEP de terceros ejecute la validación de desafío personalizada con Intune, cree una aplicación en Azure AD. Esta aplicación otorga derechos delegados a Intune para validar las solicitudes SCEP.

Asegúrese de que tiene los permisos necesarios para registrar una aplicación de Azure AD. En [Permisos necesarios](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions) se enumeran los pasos.

**Paso 1: Crear una aplicación de Azure AD**

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Azure Active Directory** > **Registros de aplicaciones** > **Nuevo registro de aplicaciones**.
3. Escriba un nombre y una dirección URL de inicio de sesión. Seleccione **Aplicación web o API** para el tipo de aplicación.
4. Seleccione **Crear**.

En [Integrar aplicaciones con Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) se incluyen algunas instrucciones sobre cómo crear una aplicación, incluidos consejos sobre la dirección URL y el nombre.

**Paso 2: Conceder permisos**

Después de crear la aplicación, asigne a la API de Microsoft Intune los permisos necesarios:

1. En la aplicación de Azure AD, abra **Configuración** > **Permisos necesarios**.  
2. Seleccione **Agregar** > **Seleccionar una API** > seleccione **API de Microsoft Intune** > **Seleccionar**.
3. En **Seleccionar permisos**, elija **Validación de la comprobación SCEP** > **Seleccionar**.
4. Haga clic en **Listo** para guardar los cambios.

**Paso 3: Obtener el identificador de aplicación y la clave de autenticación**

A continuación, obtenga los valores de identificador y clave de la aplicación de Azure AD. Se necesitan los valores siguientes:

- Id. de la aplicación
- Clave de autenticación
- Id. de inquilino

**Para obtener el identificador de aplicación y la clave de autenticación**:

1. En Azure AD, seleccione la aplicación nueva (**Registros de aplicaciones**).
2. Copie el **Id. de aplicación** y almacénelo en el código de la aplicación.
3. A continuación, genere una clave de autenticación. En la aplicación de Azure AD, abra **Configuración** > **Claves**.
4. En **Contraseñas**, escriba una descripción y elija la duración de la clave. Guarde los cambios mediante **Guardar**. Copie y guarde el valor que se muestra.

    > [!IMPORTANT]
    > Copie y guarde esta clave inmediatamente, ya que no se volverá a mostrar. Este valor de clave es necesario con la implementación de la entidad de certificación de terceros. No olvide revisar las instrucciones sobre cómo se configuran el identificador de la aplicación, la clave de autenticación y el identificador de inquilino.

El **Id. de inquilino** es el texto de dominio después del signo @ en la cuenta. Por ejemplo, si la cuenta es `admin@name.onmicrosoft.com`, entonces el identificador de inquilino es **name.onmicrosoft.com**.

En [Obtener el identificador de aplicación y la clave de autenticación](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#get-application-id-and-authentication-key) se enumeran los pasos para obtener estos valores y se proporcionan más detalles sobre las aplicaciones de Azure AD.

### <a name="configure-and-deploy-a-scep-certificate-profile"></a>Configurar e implementar un perfil de certificado SCEP
Como administrador, cree un perfil de certificado SCEP destinado a los usuarios o dispositivos. Después, asigne el perfil.

- [Creación de un perfil de certificado SCEP](certificates-scep-configure.md#create-a-scep-certificate-profile)

- [Asignar el perfil de certificado](certificates-scep-configure.md#assign-the-certificate-profile)

## <a name="removing-certificates"></a>Eliminación de certificados

Al anular la inscripción o borrar el dispositivo, se quitan los certificados. Los certificados no se revocan.

## <a name="third-party-certification-authority-partners"></a>Asociados de entidad de certificación de terceros
Las entidades de certificación de terceros siguientes son compatibles con Intune:

- [Entrust Datacard](http://www.entrustdatacard.com/resource-center/documents/documentation)

Si es una entidad de certificación de terceros interesada en la integración de su producto con Intune, revise las instrucciones de la API:

- [Repositorio de la API de SCEP de Intune en GitHub](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Instrucciones de la API de SCEP de Intune para las entidades de certificación de terceros](scep-libraries-apis.md)

## <a name="see-also"></a>Vea también

- [Configuración de perfiles de certificado](certificates-scep-configure.md)
- [Repositorio de la API de SCEP de Intune en GitHub](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Instrucciones de la API de SCEP de Intune para las entidades de certificación de terceros](scep-libraries-apis.md)
