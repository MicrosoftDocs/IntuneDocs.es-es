---
title: Administrar la transferencia de datos entre aplicaciones iOS | Microsoft Intune
description: "Consulte este tema para entender cómo puede usar la característica Open In de iOS y las directivas de administración de aplicaciones móviles para administrar las transferencias de datos entre aplicaciones."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3a4515c1-b325-4ac1-9f0a-45ac27e00681
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: 94163d5f303b293da2301b81a5c96f6c9c2e5e5d


---

# <a name="manage-data-transfer-between-ios-apps-with-microsoft-intune"></a>Administrar la transferencia de datos entre aplicaciones iOS con Microsoft Intune
## <a name="manage-ios-apps"></a>Administrar aplicaciones iOS
Como parte de la protección de los datos de la empresa es necesario asegurarse de que las transferencias de archivos se limiten a las aplicaciones que usted administra.  Puede administrar aplicaciones iOS de la siguiente manera:

-   Evitar la pérdida de datos de empresa mediante una directiva MAM para las aplicaciones, a las que llamaremos aplicaciones **administradas por directivas**.

-   También puede implementar y administrar aplicaciones a través del **canal de administración de dispositivos móviles (MDM)**.  Esto requiere la inscripción de los dispositivos en la solución de MDM. Se puede tratar de aplicaciones **administradas por directivas** u otras aplicaciones administradas.

La característica de **administración Open In** (o administración de "Abrir en") para dispositivos iOS puede limitar las transferencias de archivos para que solo se realicen entre las aplicaciones que se implementan en los dispositivos mediante el **canal de MDM**. Las restricciones de administración de Open In se establecen en los valores de configuración y se implementan con la solución MDM.  Cuando el usuario instala la aplicación implementada, se aplican las restricciones que usted defina.
##  <a name="using-mam-with-ios-apps"></a>Uso de MAM con aplicaciones iOS
Las directivas de administración de aplicaciones móviles (MAM) se pueden usar con la característica de **administración Open In** de iOS para proteger los datos de la empresa en los siguientes escenarios:

-   **Dispositivos propiedad de los empleados no administrados por una solución MDM:** puede establecer la configuración de directiva MAM en **Allow app to transfer data to only managed apps** (Permitir a la aplicación transferir datos solo a aplicaciones administradas). Si el usuario final abre un archivo protegido en una aplicación no administrada por directivas, el archivo es ilegible.

-   **Dispositivos administrados por Intune:** para dispositivos inscritos en Intune, se permite automáticamente la transferencia de datos entre aplicaciones con directivas MAM y otras aplicaciones iOS administradas que se hayan implementado a través de Intune. Para permitir la transferencia de datos entre las aplicaciones con directivas MAM, habilite la opción **Allow app to transfer data to only managed apps** (Permitir a la aplicación transferir datos solo a aplicaciones administradas). Puede usar la característica de **administración Open In** para controlar la transferencia de datos entre aplicaciones que estén implementadas a través de Intune.   

-   **Dispositivos administrados por una solución MDM de terceros:** puede usar la característica de **administración Open In** para restringir la transferencia de datos a solo las aplicaciones administradas.
Para asegurarse de que las aplicaciones que se implementan mediante la solución MDM de otros fabricantes también están asociadas con las directivas MAM que ha configurado en Intune, debe configurar la opción de UPN de usuario como se describe en el tutorial [Configurar el valor de UPN de usuario](#configure-user-upn-setting).  Si se implementan aplicaciones con el valor de UPN de usuario, las directivas de MAM se aplican a la aplicación cuando el usuario final inicia sesión con su cuenta profesional.

> [!IMPORTANT]
> El valor de UPN de usuario solo se necesita para aplicaciones implementadas en dispositivos administrados por MDM de terceros.  Para dispositivos administrados por Intune, esta opción no es necesaria.

## <a name="configure-user-upn-setting"></a>Configurar el valor de UPN de usuario
Esta configuración es necesaria para los dispositivos que están administrados por una solución MDM de terceros. El procedimiento que se describe a continuación es un flujo general para la implementación del valor de UPN y la experiencia del usuario final resultante:


1.  En el Portal de Azure, [configure una directiva de administración de aplicaciones móviles](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) para la plataforma iOS. Configure las directivas según los requisitos de su empresa y seleccione las aplicaciones que deben tener esta directiva.

2.  Implemente las aplicaciones y el perfil de correo electrónico que quiere administrar **a través de la solución MDM de terceros** con la configuración descrita en los pasos 3 y 4.

3.  Implemente la aplicación con las siguientes opciones de configuración: key=IntuneMAMUPN, <username@company.com> [ejemplo: "IntuneMAMUPN", "jondoe@microsoft.com"]‘jondoe@microsoft.com’]

4.  Implemente la directiva de administración de Open In en los dispositivos inscritos.

### <a name="example-end-user-experience"></a>Ejemplo y experiencia de usuario

1.  El usuario final instala la aplicación Microsoft Word en el dispositivo.

2.  El usuario final inicia la aplicación administrada de correo nativo para tener acceso a su correo.

3.  El usuario final intenta abrir en Microsoft Word un documento desde el correo nativo.

4.  Cuando se inicia la aplicación Word, se solicita al usuario final que inicie sesión con su cuenta profesional.  Esta cuenta profesional que introduce el usuario debe coincidir con la cuenta especificada en las opciones de configuración de la aplicación Microsoft Word.

    > [!NOTE]
    > El usuario final puede agregar otras cuentas personales a Word para realizar su trabajo personal y no verse afectado por las directivas MAM cuando utilice la aplicación Word en un contexto personal.

5.  Cuando el inicio de sesión se realiza correctamente, la configuración de directivas de aplicaciones se aplica a Word.

6.  De este modo, la transferencia de datos se realiza correctamente y el documento se etiqueta como identidad corporativa en la aplicación. Además, los datos se tratan en un contexto de trabajo en el que la configuración de directivas se aplica en consecuencia.

### <a name="see-also"></a>Consulte también
[Proteger datos mediante las directivas de administración de aplicaciones móviles con Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


