---
title: Administrar la transferencia de datos entre aplicaciones iOS
description: Consulte este tema para entender cómo puede usar la característica Open In de iOS y las directivas de administración de aplicaciones móviles para administrar las transferencias de datos entre aplicaciones.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3a4515c1-b325-4ac1-9f0a-45ac27e00681
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: c27b191f8a0f9fbd298b820114f27acb4c31f966
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="manage-data-transfer-between-ios-apps-with-microsoft-intune"></a>Administrar la transferencia de datos entre aplicaciones iOS con Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

## <a name="manage-ios-apps"></a>Administrar aplicaciones iOS
Como parte de la protección de los datos de la empresa es necesario asegurarse de que las transferencias de archivos se limiten a las aplicaciones que usted administra.  Puede administrar aplicaciones iOS de la siguiente manera:

-   Evite la pérdida de datos empresariales mediante la configuración de una directiva de protección de aplicaciones. Nos referiremos a estas aplicaciones como aplicaciones **administradas por directivas**.

-   También puede implementar y administrar aplicaciones a través del **canal de administración de dispositivos móviles (MDM)**.  Esto requiere la inscripción de los dispositivos en la solución de MDM. Se puede tratar de aplicaciones **administradas por directivas** u otras aplicaciones administradas.

La característica de **administración de Open In** para dispositivos iOS puede limitar las transferencias de archivos para que solo se realicen entre las aplicaciones que se implementan en los dispositivos mediante el **canal de MDM**. Las restricciones de administración de Open In se establecen en los valores de configuración y se implementan con la solución MDM.  Cuando el usuario instala la aplicación implementada, se aplican las restricciones que usted defina.

##  <a name="manage-data-transfer-between-ios-apps"></a>Administrar la transferencia de datos entre aplicaciones iOS
Las directivas de protección de aplicaciones se pueden usar con la característica de **administración Open In** de iOS para proteger los datos de la empresa de las siguientes formas:

-   **Dispositivos propiedad de los empleados no administrados por una solución MDM:** puede establecer la [configuración de directiva de protección de aplicaciones](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) en **Allow app to transfer data to only managed apps** (Permitir a la aplicación transferir datos solo a aplicaciones administradas). Si el usuario final abre un archivo protegido en una aplicación no administrada por directivas, el archivo es ilegible.

-   **Dispositivos administrados por Intune**: para los dispositivos inscritos en Intune, se permite automáticamente la transferencia de datos entre aplicaciones con directivas de protección de aplicaciones y otras aplicaciones iOS administradas que se hayan implementado mediante Intune. Para permitir la transferencia de datos entre aplicaciones con directivas de protección de aplicaciones, habilite la opción **Allow app to transfer data to only managed apps** (Permitir a la aplicación transferir datos solo a aplicaciones administradas). Puede usar la característica de **administración Open In** para controlar la transferencia de datos entre aplicaciones que estén implementadas a través de Intune.   

-   **Dispositivos administrados por una solución MDM de terceros:** puede usar la característica de **administración Open In** para restringir la transferencia de datos a solo las aplicaciones administradas.
Para asegurarse de que las aplicaciones que se implementan mediante la solución MDM de otros fabricantes también están asociadas con las directivas de protección de aplicaciones que ha configurado en Intune, debe configurar el valor de UPN de usuario como se describe en el tutorial [Configurar el valor de UPN de usuario](#configure-user-upn-setting-for-third-party-emm).  Si se implementan aplicaciones con el valor de UPN de usuario, las directivas de protección de aplicaciones se aplican a la aplicación cuando el usuario final inicia sesión con su cuenta profesional.

> [!IMPORTANT]
> El valor de UPN de usuario solo se necesita para aplicaciones implementadas en dispositivos administrados por MDM de terceros.  Para dispositivos administrados por Intune, este valor no es necesario.

## <a name="configure-user-upn-setting-for-third-party-emm"></a>Configurar el valor de UPN de usuario para EMM de terceros
La configuración del valor de UPN de usuario es **necesaria** para los dispositivos administrados por una solución EMM de terceros. El procedimiento que se describe a continuación es un flujo general para la configuración del valor de UPN y la experiencia del usuario final resultante:


1. En Azure Portal, [configure una directiva de protección de aplicaciones](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) para la plataforma iOS. Configure las directivas según los requisitos de su empresa y seleccione las aplicaciones que deben tener esta directiva.

2. Implemente las aplicaciones y el perfil de correo electrónico que quiera administrar **a través de la solución MDM de terceros** siguiendo los pasos generalizados que se indican a continuación. Esto también se aborda en el Ejemplo 1.

   1. Implemente la aplicación con las siguientes opciones de configuración de la aplicación:

      **clave** = IntuneMAMUPN, **valor** = <username@company.com>

      Ejemplo: [‘IntuneMAMUPN’, ‘jondoe@microsoft.com’]

   2. Implemente la directiva de administración Open In mediante su proveedor de MDM externo en los dispositivos inscritos.


### <a name="example-1-admin-experience-in-third-party-mdm-console"></a>Ejemplo 1: Experiencia de administración en la consola MDM de terceros

1. Vaya a la consola de administración de su proveedor de MDM externo. Vaya a la sección de la consola en la que se implementan las opciones de configuración de la aplicación en los dispositivos iOS inscritos.

2. En la sección Configuración de la aplicación, escriba lo siguiente:

   **clave** = IntuneMAMUPN, **valor** = <username@company.com>

   La sintaxis exacta del par clave-valor puede diferir en función del proveedor de MDM externo. En la siguiente tabla se incluyen ejemplos de proveedores de MDM externos y los valores exactos que debe escribir para el par clave-valor.

|Proveedor de MDM externo| Configuration Key | Tipo de valor | Valor de configuración|
| ------- | ---- | ---- | ---- |
| VMware AirWatch | IntuneMAMUPN | String | {UserPrincipalName}|
| MobileIron Core | IntuneMAMUPN | String | $EMAIL$ **o** $USER_UPN$ |
| MobileIron Cloud | IntuneMAMUPN | String | ${userUPN} **o** ${userEmailAddress} |
| Administrador de dispositivos móviles ManageEngine | IntuneMAMUPN | String | %upn% |

### <a name="example-2-end-user-experience"></a>Ejemplo 2: Experiencia del usuario final

1.  El usuario final instala la aplicación Microsoft Word en el dispositivo.

2.  El usuario final inicia la aplicación administrada de correo nativo para tener acceso a su correo.

3.  El usuario final intenta abrir en Microsoft Word un documento desde el correo nativo.

4.  Cuando se inicia la aplicación Word, se solicita al usuario final que inicie sesión con su cuenta profesional.  Esta cuenta profesional que introduce el usuario debe coincidir con la cuenta especificada en las opciones de configuración de la aplicación Microsoft Word.

    > [!NOTE]
    > El usuario final puede agregar otras cuentas personales a Word para realizar su trabajo particular y no verse afectado por las directivas de protección de aplicaciones cuando utilice la aplicación Word en un contexto personal.

5.  Cuando el inicio de sesión se realiza correctamente, la configuración de directivas de protección de aplicaciones se aplica a Word.

6.  Ahora la transferencia del archivo se ha realizado correctamente y el documento se etiqueta como identidad corporativa en la aplicación. Además, el archivo se trata en un contexto de trabajo en el que la configuración de directivas se aplica en consecuencia.

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Validar el valor de UPN de usuario para EMM de terceros

Después de configurar el valor de UPN de usuario, debe validar la capacidad de la aplicación iOS para recibir y cumplir la directiva de protección de aplicaciones de Intune.

Por ejemplo, la configuración de directivas **Require app PIN** (Requerir el PIN de aplicación) resulta muy fácil de probar visualmente en un dispositivo. Si la configuración de directivas se establece en **Sí**, el usuario final debe ver un aviso para establecer o escribir un PIN cuando intente acceder a datos de la compañía.

Primero, [cree e implemente una directiva de protección de aplicaciones](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) para la aplicación iOS. Consulte [Validate app protection policies](validate-mobile-application-management.md) (Validar directivas de protección de aplicaciones) para obtener más información sobre cómo probar la directiva de protección de aplicaciones.



### <a name="see-also"></a>Vea también
[Protección de datos de aplicaciones con directivas de protección de aplicaciones mediante Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)
