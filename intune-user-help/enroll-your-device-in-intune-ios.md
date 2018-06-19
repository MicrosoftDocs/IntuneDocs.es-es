---
title: Configuración del acceso a los recursos de empresa | Microsoft Docs
description: Describe cómo hacer que Intune administre los dispositivos iOS
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: c29c01169483b408528db71b1e9bb2b718220ddc
ms.sourcegitcommit: 7f46e9990797bdfa669ccba2077721f1bc70c07e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/04/2018
ms.locfileid: "30755256"
---
# <a name="set-up-access-to-your-company-resources"></a>Configuración del acceso a los recursos de empresa

Una empresa tiene grandes cantidades de información confidencial, desde correos electrónicos hasta archivos, redes y mucho más. La empresa usa Microsoft Intune para proteger esa información cuando se accede a ella desde un dispositivo iOS. Esto permite administrar esos recursos, mantenerlos más seguros y tener la libertad de usar el dispositivo de su preferencia para llevar a cabo su trabajo.

> [!NOTE]
> Si está tratando de acceder al correo electrónico de la empresa en la aplicación Mail, es probable que se le haya solicitado permiso para administrar su dispositivo por motivos de seguridad. Siga estas instrucciones para acceder a su correo electrónico y a otros recursos de la empresa en su dispositivo iOS.

## <a name="before-you-start"></a>Antes de empezar

- Asegúrese de finalizar todo el proceso una vez que comience a hacerlo. Hacer una pausa durante más de unos minutos suele detener el proceso y requiere que vuelva a iniciarlo.
- Si este proceso presenta un error, debe volver a la aplicación Portal de empresa para volver a intentarlo.
- Asegúrese de que su Wi-Fi esté funcionando y de que Safari funciona en el dispositivo.
- Descargue e instale la [aplicación Portal de empresa de Intune](install-and-sign-in-to-the-intune-company-portal-app-ios.md).


## <a name="using-the-company-portal-app-to-set-up-access-to-company-resources"></a>Uso de la aplicación Portal de empresa para configurar el acceso a los recursos de empresa

|Lo que verá|Explicación|
|---|---|
|![Pantalla de inicio de sesión de Portal de empresa, con el botón "Iniciar sesión" en la parte inferior.](./media/ios-01-cp-enroll-1802.png)|Abra la aplicación Portal de empresa y pulse **Iniciar sesión**.|
|![Solicitud de inicio de sesión de Azure AD.](./media/ios-02-cp-enroll-1802.png)|Escriba su dirección de correo electrónico de la empresa y, luego, pulse **Siguiente**.|
|![Solicitud de contraseña de Azure AD.](./media/ios-03-cp-enroll-1802.png)|Escriba la contraseña y pulse **Iniciar sesión**.|
|![Carga de la pantalla de presentación de los recursos de empresa.](./media/ios-04-cp-enroll-1802.png)|Espere a que se complete la carga.|
|![Página de términos y condiciones.](./media/ios-05-cp-enroll-1802.png)|Debe leer y **aceptar todos** los términos y condiciones.|
|![Pantalla de configuración del acceso a la empresa. En estos momentos debe solucionar tanto la administración como la configuración.](./media/ios-06-cp-enroll-1802.png)|Pulse **Empezar** para comenzar el proceso que permitirá al dispositivo acceder a los recursos de la empresa. Si no puede hacerlo ahora mismo, puede **Posponer** el proceso, pero eso significa que no podrá recibir correo electrónico, documentos, etc.|
|![Pantalla Qué puede ver mi empresa.](./media/ios-07-cp-enroll-1802.png)|Puede **obtener más información** sobre el contenido que puede ver la empresa si pulsa en el vínculo que aparece en la parte inferior. De lo contrario, pulse **Continuar**.|
|![Pantalla ¿Qué viene a continuación?](./media/ios-08-cp-enroll-1802.png)|Esta pantalla le guía por lo que sucede en el programa de instalación. Pasará por Safari, la aplicación Configuración y la aplicación Portal de empresa para completar este proceso. Pulse **Continuar**.|
|![Carga de la pantalla después de pulsar Siguiente en ¿Qué viene a continuación?.](./media/ios-09-cp-enroll-1802.png)|Espere a que se complete la carga.|
|![Dirigido a Safari para la inscripción.](./media/ios-7-cp-enroll-1711.png)|Se le envía a Safari para administrar la información de administración para el dispositivo.|
|![Aviso del sistema para pedir que se abra la aplicación Configuración.](./media/ios-8-cp-enroll-1711.png)|Pulse **Permitir** para abrir la aplicación Configuración para descargar el perfil de configuración. Instálelo para permitir que la empresa administre la información corporativa en el dispositivo.|
|![Perfil abierto en la configuración.](./media/ios-9-cp-enroll-1711.png)|Pulse **Instalar**.|
|![Diálogo modal de instalación del perfil en la parte inferior de la pantalla.](./media/ios-10-cp-enroll-1711.png)|Pulse **Instalar**.|
|![Carga de la pantalla de instalación del perfil.](./media/ios-11-cp-enroll-1711.png)|Espere a que se complete la carga.|
|![Pantalla de advertencia de administración de perfil.](./media/ios-12-cp-enroll-1711.png)|Esta advertencia escrita por Apple le permite obtener más información sobre qué tipos de acciones se pueden realizar en un dispositivo bajo administración. Obtenga más información sobre la [información que puede ver la empresa](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).|
|![Aviso del sistema que pregunta sobre la confianza en la administración remota.](./media/ios-13-cp-enroll-1711.png)|Pulse **Confiar** para permitir que la empresa administre la información corporativa y la configuración del dispositivo.|
|![Pantalla de carga de finalización de la instalación del perfil.](./media/ios-14-cp-enroll-1711.png)|Espere a que se complete la carga.|
|![Pantalla de perfil instalado.](./media/ios-15-cp-enroll-1711.png)|El perfil se instaló y la configuración y la información corporativa del dispositivo están a punto de ser administradas.|
|![Dirigido a Safari para la inscripción.](./media/ios-16-cp-enroll-1711.png)|Se le envía nuevamente a Safari para finalizar la obtención de la información de administración para el dispositivo. |
|![Aviso del sistema para abrir el portal de empresa.](./media/ios-17-cp-enroll-1711.png)|Pulse **Abrir**.|
|![Carga de la pantalla de los recursos de empresa.](./media/ios-21-cp-enroll-1802.png)|Espere a que se complete la carga.|
|![Seleccione la categoría de dispositivo en la aplicación de portal de empresa.](./media/ios-22-cp-enroll-1802.png)|Seleccione la mejor categoría para el dispositivo. Habitualmente, esto tiene relación con el propietario del dispositivo o su ubicación la mayoría del tiempo.|
|![Categoría seleccionada.](./media/ios-23-cp-enroll-1802.png)||
|![Administración de dispositivos correcta, ahora necesita actualizar la configuración.](./media/ios-24-cp-enroll-1802.png)|Logró que se administre el dispositivo. Es probable que su empresa todavía tenga que actualizar algunas configuraciones, como la longitud de la contraseña. Para proceder, haga clic en **Continuar**.|
|![Confirmación de la configuración del dispositivo.](./media/ios-25-cp-enroll-1802.png)|Portal de empresa comprobará si es necesario actualizar parte de la configuración.|
|![Comprobación de la configuración finalizada, con una versión de SO incorrecta](./media/ios-26-cp-enroll-1802.png)|Portal de empresa proporcionará instrucciones sobre cómo puede corregir cualquier problema de configuración. Cuando termine de corregir los problemas, pulse **Comprobar la configuración**.|
|![Pantalla de carga de confirmación de la configuración de dispositivo](./media/ios-27-cp-enroll-1802.png)|El dispositivo comprobará si la configuración es suficientemente segura para acceder a los recursos de empresa.|
|![La configuración se inscribió y actualizó correctamente](./media/ios-28-cp-enroll-1802.png)|Enhorabuena. El dispositivo ya está inscrito en Intune.|

> [!Note]
> Es posible que deba seguir unos pocos pasos más para que el dispositivo esté totalmente administrado. Obtenga más información sobre cómo [inscribir el dispositivo mediante la administración de gastos de telecomunicaciones](enroll-your-device-with-telecom-expense-management-ios.md). Si su organización usa el Programa de inscripción de dispositivos de Apple, obtenga más información [aquí](enroll-your-device-dep-ios.md).

¿Sigue necesitando ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://portal.manage.microsoft.com#HelpDeskDialog).
