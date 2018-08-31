---
title: Administración de la transferencia de datos entre aplicaciones iOS
titlesuffix: Microsoft Intune
description: Descubra cómo usar directivas de administración de aplicaciones móviles en Microsoft Intune para administrar transferencias de datos entre aplicaciones.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2991aa947a693d2eb71a355047ed266838dd92a4
ms.sourcegitcommit: be67f8293b47cc08a46d328a44a50a7ab67c2052
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/13/2018
ms.locfileid: "40251555"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>Administración de transferencias de datos entre aplicaciones iOS en Microsoft Intune
## <a name="manage-ios-apps"></a>Administrar aplicaciones iOS
Como parte de la protección de los datos de la empresa es necesario asegurarse de que las transferencias de archivos se limiten a las aplicaciones que usted administra.  Puede administrar aplicaciones iOS de la siguiente manera:

-   Evite la pérdida de datos empresariales mediante la configuración de una directiva de protección de aplicaciones. Nos referiremos a estas aplicaciones como aplicaciones **administradas por directivas**. Vea [todas las aplicaciones administradas de Intune que puede administrar con la directiva de protección de aplicaciones](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)

-   También puede implementar y administrar aplicaciones a través del **canal de administración de dispositivos móviles (MDM)**.  Esto requiere la inscripción de los dispositivos en la solución de MDM. Se puede tratar de aplicaciones **administradas por directivas** u otras aplicaciones administradas.

La característica de **administración Open In** (o administración de "Abrir en") para dispositivos iOS puede limitar las transferencias de archivos para que solo se realicen entre las aplicaciones que se implementan en los dispositivos mediante el **canal de MDM**. Las restricciones de administración de Open In se establecen en los valores de configuración y se implementan con la solución MDM.  Cuando el usuario instala la aplicación implementada, se aplican las restricciones que usted defina.

##  <a name="using-app-protection-with-ios-apps"></a>Uso de la protección de aplicaciones con aplicaciones iOS
Las directivas de protección de aplicaciones se pueden usar con la característica de **administración Open In** de iOS para proteger los datos de la empresa de las siguientes formas:

-   **Dispositivos propiedad de los empleados no administrados por una solución MDM**: puede establecer la configuración de directivas de protección de aplicaciones en **Allow app to transfer data to only managed apps** (Permitir a la aplicación transferir datos solo a aplicaciones administradas por directivas). El comportamiento Open In en una aplicación administrada por directivas solo presentará otras aplicaciones administradas por directivas como opción en el uso compartido. Si un usuario intenta enviar un archivo protegido por directivas como datos adjuntos desde OneDrive en el correo nativo, el archivo será ilegible.

-   **Dispositivos administrados por Intune**: para los dispositivos inscritos en Intune, se permite automáticamente la transferencia de datos entre aplicaciones con directivas de protección de aplicaciones y otras aplicaciones iOS administradas que se hayan implementado mediante Intune. Para permitir la transferencia de datos entre aplicaciones con directivas de protección de aplicaciones, habilite la opción **Allow app to transfer data to only managed apps** (Permitir a la aplicación transferir datos solo a aplicaciones administradas). Puede usar la característica de **administración Open In** para controlar la transferencia de datos entre aplicaciones que estén implementadas a través de Intune.   

-   **Dispositivos administrados por una solución MDM de terceros:** puede usar la característica de **administración Open In** para restringir la transferencia de datos a solo las aplicaciones administradas.
Para asegurarse de que las aplicaciones que se implementan mediante la solución MDM de otros fabricantes también están asociadas con las directivas de protección de aplicaciones que ha configurado en Intune, debe configurar el valor de UPN de usuario como se describe en el tutorial [Configurar el valor de UPN de usuario](#configure-user-upn-setting-for-third-party-emm).  Si se implementan aplicaciones con el valor de UPN de usuario, las directivas de protección de aplicaciones se aplican a la aplicación cuando el usuario final inicia sesión con su cuenta profesional.

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Configurar el valor de UPN de usuario para Microsoft Intune o para una solución EMM de terceros
La configuración del valor de UPN de usuario es **necesaria** para los dispositivos administrados por Intune o por una solución EMM de terceros. El procedimiento que se describe a continuación es un flujo general para la configuración del valor de UPN y la experiencia del usuario final resultante:

1.  En [Azure Portal](https://portal.azure.com), [cree y asigne una directiva de protección de aplicaciones](app-protection-policies.md) para iOS. Configure las directivas según los requisitos de su empresa y seleccione las aplicaciones iOS que debe tener esta directiva.

2.  Implemente las aplicaciones y el perfil de correo electrónico que quiera administrar a través de Intune o de la solución MDM de terceros siguiendo los pasos generales que se indican a continuación. Esto también se aborda en el Ejemplo 1.

3.  Implemente la aplicación con las siguientes opciones de configuración de la aplicación:

      **clave** = IntuneMAMUPN, **valor** = <username@company.com>

      Ejemplo: [‘IntuneMAMUPN’, ‘jondoe@microsoft.com’]

4.  Implemente la directiva de **administración Open In**  con Intune o a través de su proveedor de MDM externo en los dispositivos inscritos.


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>Ejemplo 1: Experiencia de administración en Intune o en la consola MDM de terceros

1. Vaya a la consola de administración de Intune o de su proveedor de MDM externo. Vaya a la sección de la consola en la que se implementan las opciones de configuración de la aplicación en los dispositivos iOS inscritos.

2. En la sección Configuración de la aplicación, escriba lo siguiente:

   **clave** = IntuneMAMUPN, **valor** = <username@company.com>

   La sintaxis exacta del par clave-valor puede diferir en función del proveedor de MDM externo. En la siguiente tabla se incluyen ejemplos de proveedores de MDM externos y los valores exactos que debe escribir para el par clave-valor.

|Proveedor de MDM externo| Configuration Key | Tipo de valor | Valor de configuración|
| ------- | ---- | ---- | ---- |
|Microsoft Intune| IntuneMAMUPN | String | {{UserPrincipalName}}|
|VMware AirWatch| IntuneMAMUPN | String | {UserPrincipalName}|
|MobileIron | IntuneMAMUPN | String | ${userUPN} **o** ${userEmailAddress} |
|Administrador de dispositivos móviles ManageEngine | IntuneMAMUPN | String | %upn% |


### <a name="example-2-end-user-experience"></a>Ejemplo 2: Experiencia del usuario final

1.  El usuario final instala la aplicación Microsoft Word en el dispositivo.

2.  El usuario final inicia la aplicación administrada de correo nativo para tener acceso a su correo.

3.  El usuario final intenta abrir en Microsoft Word un documento desde el correo nativo.

4.  Cuando se inicia la aplicación Word, se solicita al usuario final que inicie sesión con su cuenta profesional.  Esta cuenta profesional que introduce el usuario debe coincidir con la cuenta especificada en las opciones de configuración de la aplicación Microsoft Word.

    > [!NOTE]
    > El usuario final puede agregar otras cuentas personales a Word para realizar su trabajo particular y no verse afectado por las directivas de protección de aplicaciones cuando utilice la aplicación Word en un contexto personal.

5.  Cuando el inicio de sesión se realiza correctamente, la configuración de directivas de protección de aplicaciones se aplica a Word.

6.  Ahora, la transferencia de datos se realiza correctamente y el documento se etiqueta con una identidad corporativa en la aplicación. Además, los datos se tratan en un contexto de trabajo en el que la configuración de directivas se aplica en consecuencia.

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Validar el valor de UPN de usuario para EMM de terceros

Después de configurar el valor de UPN de usuario, debe validar la capacidad de la aplicación iOS para recibir y cumplir la directiva de protección de aplicaciones de Intune.

Por ejemplo, la configuración de directivas **Require app PIN** (Requerir el PIN de aplicación) resulta muy fácil de probar visualmente en un dispositivo. Si la configuración de directivas se establece en **Sí**, el usuario final debe ver un aviso para establecer o escribir un PIN cuando intente acceder a datos de la compañía.

Primero, [cree y asigne una directiva de protección de aplicaciones](app-protection-policies.md) para la aplicación iOS. Consulte [Validate app protection policies](app-protection-policies-validate.md) (Validar directivas de protección de aplicaciones) para obtener más información sobre cómo probar la directiva de protección de aplicaciones.


### <a name="see-also"></a>Consulte también
[¿Qué es la directiva de protección de aplicaciones de Intune?](app-protection-policy.md)
