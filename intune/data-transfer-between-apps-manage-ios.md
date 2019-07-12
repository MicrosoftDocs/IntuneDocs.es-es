---
title: Administración de la transferencia de datos entre aplicaciones iOS
titleSuffix: Microsoft Intune
description: Descubra cómo usar directivas de administración de aplicaciones móviles en Microsoft Intune para administrar transferencias de datos entre aplicaciones.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 91633aee190b5fb5bda9495f66d4503042aa6a80
ms.sourcegitcommit: 63b55e81122e5c15893302b109ae137c30855b55
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67713323"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>Administración de transferencias de datos entre aplicaciones iOS en Microsoft Intune

Para ayudar a proteger los datos de la empresa, restrinja las transferencias de archivos a solo las aplicaciones que administre. Puede administrar aplicaciones iOS de la siguiente manera:

- Evite la pérdida de datos empresariales mediante la configuración de una directiva de protección de aplicaciones. Nos referiremos a estas aplicaciones como aplicaciones **administradas por directivas**. Vea [todas las aplicaciones administradas de Intune que puede administrar con la directiva de protección de aplicaciones](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)

- Implemente y administre aplicaciones a través del **canal MDM**, que requiere que los dispositivos se inscriban en una solución de administración de dispositivos móviles (MDM). Las aplicaciones que implemente se pueden **administrar con directivas** u otras aplicaciones administradas.

La característica de **administración Open In** (o administración de "Abrir en") para dispositivos iOS puede limitar las transferencias de archivos para que solo se realicen entre las aplicaciones que se implementan en los dispositivos mediante el **canal de MDM**. Establezca restricciones de *administración Open In* en las opciones de configuración e impleméntelas mediante una solución de MDM.  Cuando un usuario instala la aplicación implementada, se aplican las restricciones que ha establecido.

## <a name="use-app-protection-with-ios-apps"></a>Uso de la protección de aplicaciones con aplicaciones iOS
Use directivas de protección de aplicaciones con la característica de **administración Open In** de iOS para proteger los datos de la empresa de las siguientes formas:

- **Dispositivos propiedad de los empleados no administrados por una solución MDM:** puede establecer la configuración de directivas de protección de aplicaciones en **Allow app to transfer data to only managed apps** (Permitir a la aplicación transferir datos solo a aplicaciones administradas por directivas). El comportamiento *Open In* en una aplicación administrada por directivas solo presenta otras aplicaciones administradas por directivas como opción para el uso compartido. Si un usuario intenta enviar un archivo protegido por directivas como datos adjuntos desde OneDrive en la aplicación de correo nativa, el archivo será ilegible.

- **Dispositivos administrados por soluciones MDM**: Para los dispositivos inscritos en las soluciones MDM de Intune o de terceros, el uso compartido de datos entre las aplicaciones con directivas de protección de aplicaciones y otras aplicaciones iOS administradas que se implementan mediante MDM está controlado por las directivas de Intune App y la característica de iOS de **administración Open in**. Para asegurarse de que las aplicaciones que implementa mediante una solución de MDM también están asociadas a las directivas de protección de aplicaciones de Intune, configure el valor de UPN de usuario como se describe en la sección siguiente, [Configurar el valor de UPN de usuario](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm). Para especificar cómo quiere permitir la transferencia de datos a otras aplicaciones, habilite **Enviar datos de la organización a otras aplicaciones** y elija el nivel de uso compartido que prefiera. Para especificar cómo quiere permitir que una aplicación reciba datos de otras aplicaciones, habilite **Recibir datos de otras aplicaciones** y elija el nivel de recepción de datos que prefiera. Para obtener más información sobre cómo recibir y compartir datos de la aplicación, vea [Configuración de reubicación de datos](app-protection-policy-settings-ios.md#data-protection).

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Configurar el valor de UPN de usuario para Microsoft Intune o para una solución EMM de terceros
La configuración del valor de UPN de usuario es **necesaria** para los dispositivos administrados por Intune o por una solución EMM de terceros. La configuración de UPN funciona con las directivas de protección de aplicaciones que implementa desde Intune. El procedimiento siguiente es un flujo general para la configuración del valor de UPN y la experiencia del usuario resultante:

1. En [Azure Portal](https://portal.azure.com), [cree y asigne una directiva de protección de aplicaciones](app-protection-policies.md) para iOS. Configure las directivas según los requisitos de su empresa y seleccione las aplicaciones iOS que debe tener esta directiva.

2. Implemente las aplicaciones y el perfil de correo electrónico que quiera administrar a través de Intune o de la solución MDM de terceros siguiendo los pasos generales siguientes. Esto también se aborda en el *Ejemplo 1*.

3. Implemente la aplicación con las siguientes opciones de configuración de la aplicación en el dispositivo administrado:

      **clave** = IntuneMAMUPN, **valor** = <username@company.com>

      Ejemplo: [‘IntuneMAMUPN’, ‘janellecraig@contoso.com’]
      
     > [!NOTE]
     > En Intune, la directiva de App Configuration debe ser del tipo de inscripción **Dispositivos administrados**.
     > Además, la aplicación se debe instalar desde el Portal de empresa de Intune si se ha establecido como disponible o se ha insertado según los requisitos en el dispositivo. 

4. Implemente la directiva de **administración Open In**  con Intune o a través de su proveedor de MDM externo en los dispositivos inscritos.


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>Ejemplo 1: Experiencia de administración en Intune o en la consola MDM de terceros

1. Vaya a la consola de administración de Intune o de su proveedor de MDM externo. Vaya a la sección de la consola en la que se implementan las opciones de configuración de la aplicación en los dispositivos iOS inscritos.

2. En la sección Configuración de la aplicación, escriba lo siguiente:

   **clave** = IntuneMAMUPN, **valor** = <username@company.com>

   La sintaxis exacta del par clave-valor puede diferir en función del proveedor de MDM externo. En la tabla siguiente se incluyen ejemplos de proveedores de MDM externos y los valores exactos que debe escribir para el par clave-valor.

   |Proveedor de MDM externo| Configuration Key | Tipo de valor | Valor de configuración|
   | ------- | ---- | ---- | ---- |
   |Microsoft Intune| IntuneMAMUPN | String | {{UserPrincipalName}}|
   |VMware AirWatch| IntuneMAMUPN | String | {UserPrincipalName}|
   |MobileIron | IntuneMAMUPN | String | ${userUPN} **o** ${userEmailAddress} |
   |Citrix Endpoint Management | IntuneMAMUPN | String | ${user.userprincipalname} |
   |Administrador de dispositivos móviles ManageEngine | IntuneMAMUPN | String | %upn% |

> [!NOTE]  
> Para la aplicación de Outlook en iOS, si implementa una directiva de configuración de la aplicación con la opción "Usar diseñador de configuraciones", la clave de configuración de IntuneMAMUPN se configura automáticamente en segundo plano para la directiva. Para más información, consulte la sección de preguntas más frecuentes de [New Outlook for iOS and Android App Configuration Policy Experience – General App Configuration](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Outlook-for-iOS-and-Android-App-Configuration-Policy/ba-p/370481) (Experiencia de la directiva de configuración de aplicaciones para el nuevo Outlook para iOS y Android: configuración general de aplicaciones). 


### <a name="example-2-end-user-experience"></a>Ejemplo 2: Experiencia del usuario final

1. Un usuario instala la aplicación Microsoft Word en un dispositivo.

2. El usuario final inicia la aplicación administrada de correo nativo para acceder a su correo.

3. El usuario intenta abrir un documento desde el correo nativo en Microsoft Word.

4. Cuando se inicia la aplicación Word, se solicita al usuario que inicie sesión con su cuenta profesional. La cuenta que especifica el usuario debe coincidir con la cuenta indicada en las opciones de configuración de aplicación para Microsoft Word.

    > [!NOTE]
    > El usuario puede agregar y usar sus cuentas personales con Word. Las directivas de protección de aplicaciones no se aplican cuando el usuario utiliza Word fuera de un contexto profesional. 

5. Después de iniciar sesión, la configuración de la directiva de protección de aplicaciones se aplica a la aplicación Word.

6. Ahora, la transferencia de datos se realiza correctamente y el documento se etiqueta con una identidad corporativa en la aplicación.  Los datos se tratan en un contexto profesional y se aplica la configuración de la directiva. 

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Validar el valor de UPN de usuario para EMM de terceros

Después de configurar el valor de UPN de usuario, valide la capacidad de la aplicación iOS para recibir y cumplir la directiva de protección de aplicaciones de Intune.

Por ejemplo, la configuración de directivas **Require app PIN** (Requerir el PIN de aplicación) resulta muy fácil de probar. Si el valor de la directiva es **Sí**, el usuario debe ver un aviso para establecer o escribir un PIN para poder acceder a los datos de la empresa.

Primero, [cree y asigne una directiva de protección de aplicaciones](app-protection-policies.md) para la aplicación iOS. Para obtener más información sobre cómo probar la directiva de protección de aplicaciones, vea [Validación de la configuración de la directiva de protección de aplicaciones](app-protection-policies-validate.md).


### <a name="see-also"></a>Consulte también
[¿Qué es la directiva de protección de aplicaciones de Intune?](app-protection-policy.md)
