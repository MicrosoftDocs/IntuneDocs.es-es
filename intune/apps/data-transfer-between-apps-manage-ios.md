---
title: Administración de la transferencia de datos entre aplicaciones iOS
titleSuffix: Microsoft Intune
description: Descubra cómo usar directivas de administración de aplicaciones móviles en Microsoft Intune para administrar transferencias de datos entre aplicaciones.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ef9810f9414af4d1f57fa71189a6960b491800c0
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414882"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>Administración de transferencias de datos entre aplicaciones iOS en Microsoft Intune

Para ayudar a proteger los datos de la empresa, restrinja las transferencias de archivos a solo las aplicaciones que administre. Puede administrar aplicaciones iOS de la siguiente manera:

- Proteja los datos de la organización para las cuentas profesionales o educativas mediante la configuración de una directiva de protección de aplicaciones para las aplicaciones, a las que llamamos *aplicaciones administradas por directiva*.  Vea [todas las aplicaciones administradas de Intune que puede administrar con la directiva de protección de aplicaciones](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)

- Implemente y administre aplicaciones a través de la administración de dispositivos iOS, que requiere que los dispositivos se inscriban en una solución de administración de dispositivos móviles (MDM). Las aplicaciones que implemente pueden ser *aplicaciones administradas por directiva* u otras aplicaciones administradas iOS.

La característica de **administración de Open In** para dispositivos iOS inscritos puede limitar las transferencias de archivos entre aplicaciones administradas iOS. Establezca restricciones de *administración Open In* en las opciones de configuración e impleméntelas mediante una solución de MDM.  Cuando un usuario instala la aplicación implementada, se aplican las restricciones que ha establecido.

## <a name="use-app-protection-with-ios-apps"></a>Uso de la protección de aplicaciones con aplicaciones iOS
Use directivas de protección de aplicaciones con la característica de **administración Open In** de iOS para proteger los datos de la empresa de las siguientes formas:

- **Dispositivos no administrados por una solución MDM:** Puede establecer la configuración de la directiva de protección de aplicaciones para controlar el uso compartido de datos con otras aplicaciones mediante *Open in* o *Extensiones de recurso compartido*.  Para ello, configure el valor**Enviar datos de la organización a otras aplicaciones** en el valor **Filtrado de aplicaciones administradas por directivas con Open-In/Recurso compartido**.  El comportamiento *Open-in/Share* (Open-In/Recurso compartido) en una *aplicación administrada por directivas* solo presenta otras *aplicaciones administradas por directivas* como opción para el uso compartido. 

- **Dispositivos administrados por soluciones MDM**: Para los dispositivos inscritos en las soluciones MDM de Intune o de terceros, el uso compartido de datos entre las aplicaciones con directivas de protección de aplicaciones y otras aplicaciones iOS administradas que se implementan mediante MDM está controlado por las directivas de Intune App y la característica de iOS de **administración Open in**. Para asegurarse de que las aplicaciones que implementa mediante una solución de MDM también están asociadas a las directivas de protección de aplicaciones de Intune, configure el valor de UPN de usuario como se describe en la sección siguiente, [Configurar el valor de UPN de usuario](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm). Para especificar cómo quiere permitir la transferencia de datos a otras aplicaciones, habilite **Enviar datos de la organización a otras aplicaciones** y elija el nivel de uso compartido que prefiera. Para especificar cómo quiere permitir que una aplicación reciba datos de otras aplicaciones, habilite **Recibir datos de otras aplicaciones** y elija el nivel de recepción de datos que prefiera. Para obtener más información sobre cómo recibir y compartir datos de la aplicación, vea [Configuración de reubicación de datos](app-protection-policy-settings-ios.md#data-protection).

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Configurar el valor de UPN de usuario para Microsoft Intune o para una solución EMM de terceros
La configuración del valor de UPN de usuario es **necesaria** para los dispositivos administrados por Intune o por una solución EMM de terceros para identificar la cuenta de usuario inscrita. La configuración de UPN funciona con las directivas de protección de aplicaciones que implementa desde Intune. El procedimiento siguiente es un flujo general para la configuración del valor de UPN y la experiencia del usuario resultante:

1. En [Azure Portal](https://portal.azure.com), [cree y asigne una directiva de protección de aplicaciones](app-protection-policies.md) para iOS/iPadOS. Configure las directivas según los requisitos de su empresa y seleccione las aplicaciones iOS que debe tener esta directiva.

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
   |Microsoft Intune| IntuneMAMUPN | String | {{UserPrincipalName}}|
   |VMware AirWatch| IntuneMAMUPN | String | {UserPrincipalName}|
   |MobileIron | IntuneMAMUPN | String | ${userUPN} **o** ${userEmailAddress} |
   |Citrix Endpoint Management | IntuneMAMUPN | String | ${user.userprincipalname} |
   |Administrador de dispositivos móviles ManageEngine | IntuneMAMUPN | String | %upn% |

> [!NOTE]  
> Para la aplicación de Outlook para iOS, si implementa una directiva de configuración de aplicaciones de dispositivos administrados con la opción "Usar diseñador de configuraciones" y activa **Permitir solo cuentas profesionales o educativas**, la clave de configuración de IntuneMAMUPN se configura automáticamente en segundo plano para la directiva. Para más información, consulte la sección de preguntas más frecuentes de [Experiencia de la directiva de configuración de aplicaciones para el nuevo Outlook para iOS y Android: configuración general de aplicaciones](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Outlook-for-iOS-and-Android-App-Configuration-Policy/ba-p/370481). 


### <a name="example-2-end-user-experience"></a>Ejemplo 2: Experiencia del usuario final

*Uso compartido desde una* aplicación administrada por directiva *a otras aplicaciones con uso compartido de SO*

1. Un usuario abre la aplicación de Microsoft OneDrive en un dispositivo iOS inscrito e inicia sesión en su cuenta profesional.  La cuenta que especifica el usuario debe coincidir con el UPN de la cuenta indicado en las opciones de configuración de aplicación para Microsoft OneDrive.

2. Después del inicio de sesión, la configuración de la aplicación establecida para el administrador se aplica a la cuenta de usuario de Microsoft OneDrive.  Esto incluye la configuración del ajuste **Enviar datos de la organización a otras aplicaciones** en el valor **Aplicaciones administradas por directivas con uso compartido del SO**.

3. El usuario recibe una vista previa de un archivo de trabajo e intenta compartirlo a través de Open-In a una aplicación administrada de iOS.  

4. La transferencia de datos se realiza correctamente y los datos ahora están protegidos por la característica de **administración de Open-in** en la aplicación administrada de iOS.  La aplicación de Intune no se aplica a las aplicaciones que no están *administradas por directiva*.

*Uso compartido de una* aplicación administrada de iOS*a una*aplicación administrada por directivas *con datos de organización entrantes*

1. Un usuario abre la aplicación nativa de correo en un dispositivo iOS inscrito con un perfil de correo electrónico administrado.  

1. El usuario abre los datos adjuntos de un documento de trabajo desde la aplicación nativa de correo a Microsoft Word.

1. Cuando se inicia la aplicación Word, se produce una de estas dos experiencias:
   1. Los datos están protegidos por la aplicación de Intune cuando:
      - El usuario ha iniciado sesión en su cuenta de trabajo que coincide con el UPN de la cuenta indicada en las opciones de configuración de aplicación para Microsoft Word. 
      - La configuración de la aplicación establecida para el administrador se aplica a la cuenta de usuario de Microsoft Word.  Esto incluye la configuración de **Recibir datos de otras aplicaciones** en **Todas las aplicaciones con datos entrantes de la organización**.
      - La transferencia de datos se realiza correctamente y el documento se etiqueta con una identidad de trabajo en la aplicación.  La aplicación de Intune protege las acciones del usuario para el documento.
   1. Los datos **no** están protegidos por la aplicación de Intune cuando:
      - El usuario **no** ha iniciado sesión en su cuenta profesional.
      - Los valores configurados por el administrador **no** se aplican a Microsoft Word porque el usuario no ha iniciado sesión.
      - La transferencia de datos se realiza correctamente y el documento **no** se etiqueta con una identidad de trabajo en la aplicación.  La aplicación de Intune **no** protege las acciones del usuario para el documento porque no está activo.

    > [!NOTE]
    > El usuario puede agregar y usar sus cuentas personales con Word. Las directivas de protección de aplicaciones no se aplican cuando el usuario utiliza Word fuera de un contexto profesional. 

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Validar el valor de UPN de usuario para EMM de terceros

Después de configurar el valor de UPN de usuario, valide la capacidad de la aplicación iOS para recibir y cumplir la directiva de protección de aplicaciones de Intune.

Por ejemplo, la configuración de directivas **Require app PIN** (Requerir el PIN de aplicación) resulta muy fácil de probar. Si el valor de la directiva es **Requerir**, el usuario debe ver un aviso para establecer o escribir un PIN para poder acceder a los datos de la empresa.

Primero, [cree y asigne una directiva de protección de aplicaciones](app-protection-policies.md) para la aplicación iOS. Para obtener más información sobre cómo probar la directiva de protección de aplicaciones, vea [Validación de la configuración de la directiva de protección de aplicaciones](app-protection-policies-validate.md).


## <a name="see-also"></a>Vea también
[¿Qué es la directiva de protección de aplicaciones de Intune?](app-protection-policy.md)
