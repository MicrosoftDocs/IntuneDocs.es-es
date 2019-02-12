---
title: Configuración del acceso de dispositivos iOS a los recursos de la empresa | Microsoft Docs
description: Describe cómo hacer que Intune administre los dispositivos iOS
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2018
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
ms.collection: M365-identity-device-management
ms.openlocfilehash: e7db319586b9375b8c88f177197e2fdf15378ab4
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55847308"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>Configuración del acceso de dispositivos iOS a los recursos de la empresa

Inscriba el dispositivo iOS con la aplicación Portal de empresa de Intune para obtener acceso seguro a las aplicaciones, los archivos y el correo electrónico de la organización.

Antes de obtener permiso para acceder a datos de propiedad desde un dispositivo corporativo o personal, es necesario tener el dispositivo administrado. Una vez que el dispositivo esté administrado, la organización asignará directivas y aplicaciones al dispositivo a través de su proveedor de administración de dispositivos móviles (MDM). 

Para conservar el acceso a la información profesional o educativa desde el dispositivo, debe configurarlo para que coincida con la configuración preferida de la organización. En este artículo se describe cómo realizar la inscripción y la configuración del dispositivo con la aplicación Portal de empresa y lograr que el dispositivo siga cumpliendo estos requisitos.

> [!NOTE]
> Este artículo le interesará si ha intentado acceder al correo electrónico de la empresa en la aplicación Correo y se le ha pedido que administrara su dispositivo. Siga estas instrucciones para acceder a su correo electrónico y a otros recursos de la empresa en su dispositivo iOS.

## <a name="what-to-expect-from-the-company-portal-app"></a>Qué esperar de la aplicación Portal de empresa

### <a name="security"></a>Seguridad
Durante la instalación inicial, la aplicación requiere que se autentique con la organización. Después le informa de cualquier configuración del dispositivo que debe actualizar. Por ejemplo, las organizaciones suelen definir requisitos de caracteres mínimos o máximos para las contraseñas que tendrá que cumplir.    

### <a name="protection"></a>Protección
Una vez inscrito el dispositivo, la aplicación Portal de empresa continuará para asegurarse de que el dispositivo esté protegido. Por ejemplo, si instala una aplicación desde un origen que no sea de confianza, la aplicación le avisará y, en ocasiones, revocará el acceso a los datos de la empresa. Las directivas de protección de aplicaciones como esta son comunes en las organizaciones. A menudo piden que desinstale la aplicación de confianza para poder recuperar el acceso.

### <a name="setting-notifications"></a>Configuración de notificaciones
Si después de la inscripción, la organización exige un nuevo requisito de seguridad, como la autenticación multifactor, la aplicación Portal de empresa se lo notificará. Tendrá la oportunidad de ajustar la configuración para poder seguir trabajando desde su dispositivo.  

Para obtener más información sobre la inscripción, vea [¿Qué ocurre si instalo la aplicación de Portal de empresa e inscribo el dispositivo?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios). 

## <a name="before-you-start"></a>Antes de empezar

- Una vez que empieza la inscripción, asegúrese de completar todo el proceso. Si se detiene durante más de unos minutos, es posible que el programa de instalación finalice y tenga que empezar de nuevo.  
- En caso de que se produzca un error en este proceso, vuelva a la aplicación Portal de empresa e inténtelo de nuevo.  
- Compruebe que la Wi-Fi esté funcionando y de que Safari funciona en el dispositivo.
- Descargue e instale la [aplicación Portal de empresa de Intune](install-and-sign-in-to-the-intune-company-portal-app-ios.md).  


## <a name="using-the-company-portal-app-to-set-up-access-to-company-resources"></a>Uso de la aplicación Portal de empresa para configurar el acceso a los recursos de empresa

|Lo que verá|Explicación|
|---|---|
|![Pantalla de inicio de sesión de Portal de empresa, con el botón "Iniciar sesión" en la parte inferior.](./media/ios-01-cp-enroll-1802.PNG)|Abra la aplicación Portal de empresa y pulse **Iniciar sesión**.|
|![Solicitud de inicio de sesión de Azure AD.](./media/ios-02-cp-enroll-1802.PNG)|Escriba su dirección de correo electrónico de la empresa y, luego, pulse **Siguiente**.|
|![Solicitud de contraseña de Azure AD.](./media/ios-03-cp-enroll-1802.PNG)|Escriba la contraseña y pulse **Iniciar sesión**.|
|![Carga de la pantalla de presentación de los recursos de empresa.](./media/ios-04-cp-enroll-1802.PNG)|Espere a que se cargue esta pantalla.|
|![Página de términos y condiciones.](./media/ios-05-cp-enroll-1802.PNG)|Debe leer y **aceptar todos** los términos y condiciones.|
|![Pantalla de configuración del acceso a la empresa. En estos momentos debe solucionar tanto la administración como la configuración.](./media/ios-06-cp-enroll-1802.PNG)|Pulse **Empezar** para comenzar el proceso que permitirá al dispositivo acceder a los recursos de la empresa. Si no puede hacerlo ahora mismo, puede **Posponer** el proceso, pero eso significa que no podrá recibir correo electrónico, documentos, etc.|
|![Pantalla Qué puede ver mi empresa.](./media/ios-07-cp-enroll-1802.PNG)|Puede **obtener más información** sobre el contenido que puede ver la empresa si pulsa en el vínculo que aparece en la parte inferior. De lo contrario, pulse **Continuar**.|
|![Pantalla ¿Qué viene a continuación?](./media/ios-08-cp-enroll-1802.PNG)|Esta pantalla le guía por lo que sucede en el programa de instalación. Pasará por Safari, la aplicación Ajustes y la aplicación Portal de empresa. Pulse **Continuar**.|
|![Carga de la pantalla después de pulsar Siguiente en ¿Qué viene a continuación?.](./media/ios-09-cp-enroll-1802.PNG)|Espere a que se cargue esta pantalla.|
|![Dirigido a Safari para la inscripción.](./media/ios-cp-sent-to-safari-1808.png)|Se le envía a Safari para administrar la información de administración para el dispositivo.|
|![Aviso del sistema para pedir que se abra la aplicación Configuración.](./media/ios-8-cp-enroll-1711.PNG)|Pulse **Permitir** para abrir la aplicación Configuración para descargar el perfil de configuración. Instálelo para permitir que la empresa administre la información corporativa en el dispositivo.|
|![Captura de la pantalla Instalar perfil en la configuración del dispositivo.](./media/ios-9-cp-enroll-1711.PNG)|Pulse **Instalar**.|
|![Diálogo modal de instalación del perfil en la parte inferior de la pantalla.](./media/ios-10-cp-enroll-1711.PNG)|Pulse **Instalar**.|
|![Carga de la pantalla de instalación del perfil.](./media/ios-11-cp-enroll-1711.PNG)|Espere a que se cargue esta pantalla.|
|![Pantalla de advertencia de administración de perfil.](./media/ios-12-cp-enroll-1711.PNG)|Esta advertencia escrita por Apple le permite obtener más información sobre qué tipos de acciones se pueden realizar en un dispositivo bajo administración. Obtenga más información sobre la [información que puede ver la empresa](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).|
|![Aviso del sistema que pregunta sobre la confianza en la administración remota.](./media/ios-13-cp-enroll-1711.PNG)|Pulse **Confiar** para permitir que la empresa administre la información corporativa y la configuración del dispositivo.|
|![Pantalla de carga de finalización de la instalación del perfil.](./media/ios-14-cp-enroll-1711.PNG)|Espere a que se cargue esta pantalla.|
|![Pantalla de perfil instalado.](./media/ios-15-cp-enroll-1711.PNG)|El perfil se instaló y la configuración y la información corporativa del dispositivo están a punto de ser administradas.|
|![Dirigido a Safari para la inscripción.](./media/ios-16-cp-enroll-1711.PNG)|Se le envía nuevamente a Safari para finalizar la obtención de la información de administración para el dispositivo. |
|![Aviso del sistema para abrir el portal de empresa.](./media/ios-17-cp-enroll-1711.PNG)|Pulse **Abrir**.|
|![Carga de la pantalla de los recursos de empresa.](./media/ios-21-cp-enroll-1802.PNG)|Espere a que se cargue esta pantalla.|
|![Seleccione la categoría de dispositivo en la aplicación de portal de empresa.](./media/ios-22-cp-enroll-1802.PNG)|Seleccione la mejor categoría para el dispositivo. Habitualmente, esto tiene relación con el propietario del dispositivo o su ubicación la mayoría del tiempo.|
|![Categoría seleccionada.](./media/ios-23-cp-enroll-1802.PNG)||
|![Administración de dispositivos correcta, ahora necesita actualizar la configuración.](./media/ios-24-cp-enroll-1802.PNG)|Logró que se administre el dispositivo. Es probable que su empresa todavía tenga que actualizar algunas configuraciones, como la longitud de la contraseña. Para proceder, haga clic en **Continuar**.|
|![Confirmación de la configuración del dispositivo.](./media/ios-25-cp-enroll-1802.PNG)|Portal de empresa comprobará si es necesario actualizar parte de la configuración.|
|![Comprobación de la configuración finalizada, con una versión de SO incorrecta](./media/ios-26-cp-enroll-1802.PNG)|Portal de empresa proporcionará instrucciones sobre cómo puede corregir cualquier problema de configuración. Cuando termine de corregir los problemas, pulse **Comprobar la configuración**.|
|![Pantalla de carga de confirmación de la configuración de dispositivo](./media/ios-27-cp-enroll-1802.PNG)|El dispositivo comprobará si la configuración es suficientemente segura para acceder a los recursos de empresa.|
|![La configuración se inscribió y actualizó correctamente](./media/ios-28-cp-enroll-1802.PNG)|Enhorabuena. El dispositivo ya está inscrito en Intune.|

> [!Note]
> Es posible que deba seguir unos pocos pasos más para que el dispositivo esté totalmente administrado. Obtenga más información sobre cómo [inscribir el dispositivo mediante la administración de gastos de telecomunicaciones](enroll-your-device-with-telecom-expense-management-ios.md). Si su organización usa el Programa de inscripción de dispositivos de Apple, obtenga más información [aquí](enroll-your-device-dep-ios.md).

¿Sigue necesitando ayuda? Póngase en contacto con el equipo de soporte técnico de su empresa. Puede encontrar su información de contacto en el [sitio web del Portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  
