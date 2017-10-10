---
title: "Inscripción del dispositivo iOS en la administración de gastos de telecomunicaciones con Intune"
description: "Obtenga información sobre cómo inscribir un dispositivo iOS en la administración de gastos de telecomunicaciones."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 04/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d8c6372-f2ce-4558-8886-1d7c1966699c
searchScope: User help
ROBOTS: 
ms.reviewer: sumitp
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 525e2024246946c9fd9fadefbe42d10dee5c2932
ms.sourcegitcommit: db7a7bbead3a3fa78c4d643607f709a2909eb608
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/28/2017
---
# <a name="enroll-your-ios-device-in-telecom-expense-management"></a>Inscripción del dispositivo iOS en la administración de gastos de telecomunicaciones

Su organización puede estar usando software de administración de gastos de telecomunicaciones para asegurarse de que sus planes de voz y datos se utilizan dentro de límites aceptables. Cuando haya completado la inscripción del dispositivo, se le pedirá que seleccione la categoría más apropiada para dicho dispositivo.

  ![Captura de la pantalla "selección de la categoría más apropiada para un dispositivo" en un dispositivo iOS. Muestra una selección de inscripciones personales o corporativas.](./media/ios-enroll-10-tem-select-best-category.png)

Seleccione la opción adecuada y recibirá una notificación para instalar la aplicación [__Datalert__](https://itunes.apple.com/app/datalert/id771029268?mt=8) en App Store. Con la aplicación Datalert su organización puede medir el uso de datos. Si la organización configuró la opción de inscripción profesional o educativa de Microsoft, se le pedirá que inicie sesión con su cuenta profesional o educativa. Si no se ha habilitado, deberá proporcionar información, como su número de teléfono, y verificar el dispositivo con un código para inscribirse en el servicio Datalert desde la aplicación.

  ![Captura de la pantalla de bienvenida de la aplicación Datalert, que le pregunta si desea pasar a la siguiente pantalla después de proporcionar una breve explicación sobre cómo Datalert puede ayudarle a sacar el máximo provecho de su plan de datos.](./media/ios-enroll-11-tem-datalert-setup.png)

## <a name="enroll-into-datalert-using-your-microsoft-work-or-school-account"></a>Inscripción en Datalert con su cuenta profesional o educativa de Microsoft

> [!NOTE]
> Debe tener la aplicación [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) instalada y activa en el teléfono para inscribirse de esta manera.

1. Seleccione __Enroll with Microsoft account__ (Inscribirse con cuenta Microsoft).

  ![Una imagen de la pantalla Configuración de la aplicación Datalert, que ofrece un campo de número de teléfono para inscribir un dispositivo en la mitad superior de la pantalla e "Inscribirse con cuenta Microsoft" en la parte inferior, siempre que tenga una cuenta de Microsoft Office 365 y una suscripción de Intune.](./media/ios-enroll-11a-tem-datalert-enroll-msft-account.png)

2. Recibirá una notificación que indica que __"Datalert" desea abrir "Authenticator"__. Seleccione __Abrir__.

  ![Una imagen de la ventana emergente que le pide al usuario que abra la aplicación Authenticator a solicitud de la aplicación Datalert.](./media/ios-enroll-11b-tem-datalert-open-authenticator.png)

3. Inicie sesión con su __cuenta profesional o educativa de Microsoft__. La configuración de Datalert se ejecutará durante unos momentos y, luego, se debe completar. Pulse __Finalizar__ cuando se complete.

## <a name="enroll-into-datalert-using-your-phone-number"></a>Inscripción en Datalert con su número de teléfono

1. Indique el número de teléfono de su dispositivo.

  ![Captura de pantalla de la aplicación Datalert donde se solicita el número de teléfono.](./media/ios-enroll-12-tem-datalert-phone-number.png)

2. Después, recibirá un código de comprobación a través de un mensaje SMS. Escriba el código y pulse __Aceptar__.

  ![Captura de pantalla de la aplicación Datalert donde se solicita el código de verificación SMS.](./media/ios-enroll-13-tem-datalert-sms.png)

3. Una vez que haya proporcionado el código de comprobación, se completará la instalación de Datalert. Pulse __Finalizar__ y podrá supervisar los datos desde la aplicación Datalert.

  ![Captura de pantalla de la aplicación Datalert con la supervisión del uso de datos de hoy en día.](./media/ios-enroll-14-tem-datalert-monitoring-active.png)

Una vez inscrito, puede empezar a ver su uso de datos en la aplicación Datalert.

¿Sigue necesitando ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://portal.manage.microsoft.com).
