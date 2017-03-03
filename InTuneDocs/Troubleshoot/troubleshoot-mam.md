---
title: "Solucionar problemas de la administración de aplicaciones móviles | Microsoft Docs"
description: En este tema se describen algunas sugerencias para solucionar problemas en las implementaciones de acceso condicional.
keywords: 
author: oydang
ms.author: oydang
manager: angerobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd5a0a3b-0013-4be3-a233-ce6e9083149f
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: a2e43444bff3b189c1516c6ca7131771035313ea
ms.openlocfilehash: 6258917de60bdbf8efde4720c17ec6fc643154bd


---

# <a name="troubleshoot-mobile-application-management"></a>Solucionar problemas de la administración de aplicaciones móviles

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Si tiene problemas con la administración de aplicaciones móviles de Intune, empiece por aquí. En este tema se describen algunos problemas y preguntas comunes que podría tener y se proporcionan soluciones y respuestas.

Si esta información no soluciona el problema, vea [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico para Microsoft Intune) para conocer otras formas de obtener ayuda.


## <a name="common-it-administrator-issues"></a>Problemas comunes para el administrador de TI

Estos son problemas comunes que puede experimentar un administrador de TI al usar la directiva de protección de aplicaciones de Intune.

| Problema | Descripción | Solución |
| -- | -- | -- |
| La directiva no se aplica a Skype Empresarial | La directiva de protección de aplicaciones sin inscripción de dispositivo, realizada en Azure Portal, no se aplica a la aplicación Skype Empresarial en dispositivos iOS y Android. | Debe configurar Skype Empresarial para la autenticación moderna.  Siga las instrucciones que se indican en [Enable your tenant for modern authentication](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) (Habilitar el inquilino para la autenticación moderna) para configurar la autenticación moderna de Skype. |
| La directiva de aplicaciones de Office no se aplica | Las directivas de protección de aplicaciones no se aplican a ninguna [aplicación de Office compatible](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners) para ningún usuario. | Confirme que el usuario tiene licencia para Intune y que hay una directiva de protección de aplicaciones implementada que apunta a las aplicaciones de Office. La aplicación de una directiva de protección de implementación recientemente implementada puede demorar hasta 8 horas. |
| El administrador no puede configurar la directiva de protección de aplicaciones en Azure Portal | El usuario administrador de TI no puede configurar directivas de protección de aplicaciones en Azure Portal. | Los roles siguientes tienen acceso a Azure Portal: <ul><li>El administrador global, que puede configurar en el [Portal de Office](http://portal.office.com/).</li><li>El propietario, que puede configurar en [Azure Portal](https://portal.azure.com/).</li><li>El colaborador, que puede configurar en [Azure Portal](https://portal.azure.com/).</li></ul>  Consulte [Preparación para configurar directivas de administración de aplicaciones móviles con Microsoft Intune](../deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md) para obtener ayuda sobre cómo configurar estos roles.|
|Cuentas de usuario que faltan en los informes de la directiva de protección de aplicaciones | Los informes de la consola de administración no muestran las cuentas de usuario en las que se implementó recientemente la directiva de protección de aplicaciones. | Si se acaba de aplicar a un usuario una directiva de protección de aplicaciones, dicho usuario puede tardar hasta 24 horas en aparecer en los informes como usuario de destino. |
| Los cambios de directiva no funcionan | Los cambios y las actualizaciones de la directiva de protección de aplicaciones pueden tardar hasta 8 horas en aplicarse. | Si procede, el usuario final puede cerrar sesión en la aplicación y volver a iniciarla para forzar la sincronización con el servicio. |
| La directiva de protección de aplicaciones no funciona con DEP | La directiva de protección de aplicaciones no se aplica a dispositivos DEP de Apple. | Asegúrese de que usa la afinidad de usuario con el Programa de inscripción de dispositivos (DEP) de Apple. La afinidad de usuario es necesaria para todas las aplicaciones que requieran la autenticación de usuario en DEP. <br><br>Consulte [Inscribir dispositivos iOS de la empresa mediante el Programa de inscripción de dispositivos](../deploy-use/ios-device-enrollment-program-in-microsoft-intune.md) para obtener más información sobre la inscripción de DEP de iOS.|
| La directiva de transferencia de datos no funciona con iOS | Las directivas **Permitir a la aplicación transferir datos a otras aplicaciones** y **Permitir a la aplicación recibir datos de otras aplicaciones** no administran correctamente la transferencia de datos en iOS. | Vea [Administrar la transferencia de datos entre aplicaciones iOS con Microsoft Intune](/deploy-use/manage-data-transfer-between-ios-apps-with-microsoft-intune.md). |






## <a name="common-end-user-issues"></a>Problemas comunes del usuario final

Los problemas comunes del usuario final se desglosan en las siguientes categorías:

* **Escenarios de uso normal**: un usuario final puede experimentar estos escenarios en aplicaciones que tienen la directiva de protección de aplicaciones de Intune. Estos no son problemas reales, pero pueden percibirse como errores.

* **Cuadros de diálogo de uso normal**: estos son cuadros de diálogo de uso que un usuario final puede ver en aplicaciones que tienen la directiva de protección de aplicaciones de Intune. Estos mensajes y cuadros de diálogo **no** indican un error.

* **Cuadros de diálogo y mensajes de error**: estos son cuadros de diálogo y mensajes de error que un usuario final puede ver en aplicaciones que tienen la directiva de protección de aplicaciones de Intune. Estos suelen indicar un error que ha realizado el administrador de TI o un error de la protección de aplicaciones de Intune.



### <a name="normal-usage-scenarios"></a>Escenarios de uso normal

Plataforma | Escenario | Explicación |
---| --- | --- |
iOS | El usuario final puede usar la extensión de recursos compartidos de iOS para abrir los datos profesionales o educativos en aplicaciones no administradas, incluso con la directiva de transferencia de datos establecida en **Solo aplicaciones administradas** o **Ninguna aplicación**. ¿No es esto una pérdida de datos? | La directiva de protección de aplicaciones de Intune no puede controlar la extensión de recursos compartidos de iOS sin administrar el dispositivo. Por tanto, **Intune cifra los datos "corporativos" antes de compartirlos fuera de la aplicación**. Puede validar esto intentando abrir el archivo "corporativo" fuera de la aplicación administrada. El archivo debe estar cifrado y no debe poder abrirse fuera de la aplicación administrada.
Android | ¿Por qué el usuario final **necesita instalar la aplicación de portal de empresa** aunque esté usando la protección de aplicaciones de MAM sin la inscripción de dispositivos?  | En Android, la mayor parte de la función de protección de aplicaciones se integra en la aplicación de portal de empresa. **La inscripción de dispositivos no se requiere aunque la aplicación de portal de empresa se requiera siempre**. Para la protección de aplicaciones sin inscripción, el usuario final solo necesita tener la aplicación de portal de empresa instalada en el dispositivo.

### <a name="normal-usage-dialogs"></a>Cuadros de diálogo de uso normal

Plataforma | Mensaje o cuadro de diálogo | Explicación |
--- | --- | --- |
iOS, Android | **Inicio de sesión**: para proteger sus datos, la organización necesita administrar esta aplicación. Para completar esta acción, inicie sesión con su cuenta profesional o educativa. | El usuario final debe iniciar sesión con su cuenta profesional o educativa para usar esta aplicación, que requiere la directiva de protección de aplicaciones. Para que se aplique la directiva, el usuario debe autenticarse en Azure Active Directory.
iOS, Android |**Reinicio requerido**: ahora su organización está protegiendo sus datos en esta aplicación. Necesita reiniciar la aplicación para continuar. | La aplicación acaba de recibir la directiva de protección de aplicaciones de Intune y debe reiniciarse para que se aplique la directiva.
iOS, Android |**Acción no permitida**: la organización solo le permite abrir datos profesionales o educativos en esta aplicación. | El administrador de TI ha establecido la directiva **Permitir a la aplicación recibir datos de otras aplicaciones** en **Solo aplicaciones administradas**. Por tanto, el usuario final solo puede transferir datos en esta aplicación desde otras aplicaciones que tengan la directiva de protección de aplicaciones.
iOS, Android |**Acción no permitida**: la organización solo le permite transferir sus datos a otras aplicaciones administradas. | El administrador de TI ha establecido la directiva **Permitir a la aplicación transferir datos a otras aplicaciones** en **Solo aplicaciones administradas**. Por tanto, el usuario final solo puede transferir datos fuera de esta aplicación a otras aplicaciones que tengan la directiva de protección de aplicaciones.
iOS, Android |**Alerta de borrado**: la organización ha quitado los datos asociados a esta aplicación. Para continuar, reinicie la aplicación. | El administrador de TI ha iniciado un borrado de la aplicación con la protección de aplicaciones de Intune.
Android | **Portal de empresa requerido**: para usar su cuenta profesional o educativa con esta aplicación, tiene que instalar la aplicación de portal de empresa de Intune. Pulse "Ir a la tienda" para continuar. | En Android, la mayor parte de la función de protección de aplicaciones se integra en la aplicación de portal de empresa. **La inscripción de dispositivos no se requiere aunque la aplicación de portal de empresa se requiera siempre**. Para la protección de aplicaciones sin inscripción, el usuario final solo necesita tener la aplicación de portal de empresa instalada en el dispositivo.


### <a name="error-messages-and-dialogs-on-ios"></a>Cuadros de diálogo y mensajes de error en iOS


Cuadro de diálogo o mensaje de error | Causa | Corrección |
-- | --- | --- |
**Aplicación no configurada**: esta aplicación no se configuró para uso. Póngase en contacto con el administrador de TI para obtener ayuda. | Error al detectar la directiva de protección de aplicación requerida para la aplicación. |Asegúrese de que haya una directiva de protección de aplicación iOS implementada en el grupo de seguridad del usuario y que se dirige a esta aplicación.
**Bienvenido a Intune Managed Browser**: esta aplicación funciona mejor cuando se administra con Microsoft Intune. Puede usar la aplicación en cualquier momento para navegar por Internet. Además, si la administra Microsoft Intune, podrá tener acceso a más características de protección de datos. | Error al detectar la directiva de protección de aplicación requerida para la aplicación Intune Managed Browser. <br><br>El usuario todavía podrá usar la aplicación para navegar por Internet, pero Intune no administrará la aplicación. | Asegúrese de que haya una directiva de protección de aplicación iOS implementada en el grupo de seguridad del usuario y que se dirige a la aplicación Intune Managed Browser.
**Error de inicio de sesión**: no podemos iniciar su sesión en este momento. Vuelva a intentarlo más tarde. | Error al inscribir al usuario con el servicio MAM después de que intenta iniciar sesión con su cuenta profesional o educativa. | Asegúrese de que haya una directiva de protección de aplicación iOS implementada en el grupo de seguridad del usuario y que se dirige a esta aplicación.
**Cuenta con configurada**: la organización no ha configurado la cuenta para obtener acceso a datos profesionales o educativos. Póngase en contacto con el administrador de TI para obtener ayuda. | La cuenta de usuario no tiene una licencia de Intune A Direct. | Asegúrese de que la cuenta del usuario tiene asignada una licencia de Intune en el [portal de Office](http://portal.office.com).
**Dispositivo no compatible**: no se puede usar esta aplicación porque está usando un dispositivo con Jailbreak. Póngase en contacto con el administrador de TI para obtener ayuda. | Intune detectó que el usuario usa un dispositivo con Jailbreak. | Restablezca los valores de fábrica predeterminados del dispositivo. Siga [estas instrucciones](https://support.apple.com/en-us/HT201274) desde el sitio de soporte de Apple.
**Se requiere conexión a Internet**: debe conectarse a Internet para comprobar si puede usar esta aplicación. | El dispositivo no está conectado a Internet. | Conecte el dispositivo a una red de datos o WiFi.
**Error desconocido**: intente reiniciar esta aplicación. Si el problema persiste, póngase en contacto con el administrador de TI para obtener ayuda. | Error desconocido. | Espere un momento y vuelva a intentarlo. Si el error persiste, cree una incidencia de soporte técnico con Intune [aquí](how-to-get-support-for-microsoft-intune.md).
**Acceso a los datos de la organización**: la cuenta profesional o educativa que especificó no tiene acceso a esta aplicación. Puede que tenga que iniciar sesión con otra cuenta. Póngase en contacto con el administrador de TI para obtener ayuda. | Intune detecta que el usuario intentó iniciar sesión con una segunda cuenta profesional o educativa distinta de la cuenta inscrita en MAM para el dispositivo. MAM solo puede administrar una cuenta profesional o educativa por dispositivo a la vez. | Indíquele al usuario que inicie sesión con la cuenta cuyo nombre de usuario aparece rellenada previamente en la pantalla de inicio de sesión. <br> <br> O bien indíquele que inicie sesión con la cuenta profesional o educativa nueva y quite la cuenta inscrita en MAM existente.
**Problema de conexión**: error de conexión inesperado. Compruebe la conexión y vuelva a intentarlo.  |  Error inesperado. | Espere un momento y vuelva a intentarlo. Si el error persiste, cree una incidencia de soporte técnico con Intune [aquí](how-to-get-support-for-microsoft-intune.md).
**Alerta**: ya no se puede usar esta aplicación. Para obtener más información, póngase en contacto con su administrador de TI. | Error al validar el certificado de la aplicación. | Asegúrese de que la versión de la aplicación esté actualizada. <br><br> Vuelva a instalar la aplicación.
**Error**: se encontró un problema con esta aplicación y debe cerrarse. Si el error persiste, póngase en contacto con el administrador de TI. | Error al leer el PIN de la aplicación de MAM desde la cadena de claves Apple iOS. | Reinicie el dispositivo. Asegúrese de que la versión de la aplicación esté actualizada. <br><br> Vuelva a instalar la aplicación.


### <a name="error-messages-and-dialogs-on-android"></a>Cuadros de diálogo y mensajes de error en Android

Cuadro de diálogo/mensaje de error | Causa | Corrección |
-- | --- | --- |
**Aplicación no configurada**: esta aplicación no se configuró para uso. Póngase en contacto con el administrador de TI para obtener ayuda. | Error al detectar la directiva de protección de aplicación requerida para la aplicación. |Asegúrese de que haya una directiva de protección de aplicaciones Android implementada en el grupo de seguridad del usuario y que se dirige a esta aplicación.
**Error al iniciar la aplicación**: se produjo un error en el inicio de la aplicación. Intente actualizar la aplicación o la aplicación Portal de empresa de Intune. Si necesita ayuda, póngase en contacto con el Administrador de TI. | Intune detectó una directiva de protección de aplicación válida para la aplicación, pero la aplicación se bloquea cuando se inicializa MAM. | Asegúrese de que la versión de la aplicación esté actualizada. <br><br> Asegúrese de que la aplicación Portal de empresa de Intune esté instalada y actualizada en el dispositivo. <br><br> Si el error persiste, use la aplicación Portal de empresa para enviar registros a Intune o cree una incidencia de soporte técnico [aquí](how-to-get-support-for-microsoft-intune.md).
**No se encontraron aplicaciones**: no hay ninguna aplicación en este dispositivo que su organización admita para abrir este contenido. Póngase en contacto con el administrador de TI para obtener ayuda. | El usuario intentó abrir datos profesionales o educativos con otra aplicación, pero Intune no puede encontrar ninguna otra aplicación administrada que pueda abrir los datos. | Asegúrese de que haya una directiva de protección de aplicación de Android implementada para la seguridad del usuario y que se dirija al menos a otra aplicación habilitada para MAM que pueda abrir los datos en cuestión.
**Error de inicio de sesión**: vuelva a intentar iniciar la sesión. Si este problema persiste, póngase en contacto con el administrador de TI para obtener ayuda. | Error al autenticar la cuenta con la que el usuario intentó iniciar sesión. | Asegúrese de que el usuario inicia sesión con la cuenta profesional o educativa que ya está inscrita con el servicio MAM de Intune (la primera cuenta profesional o educativa con que se inició sesión correctamente en esta aplicación). <br><br> Borre los datos de la aplicación. <br><br> Asegúrese de que la versión de la aplicación esté actualizada. <br><br> Asegúrese de que la versión de Portal de empresa está actualizada.
**Se requiere conexión a Internet**: debe conectarse a Internet para comprobar si puede usar esta aplicación. | El dispositivo no está conectado a Internet. | Conecte el dispositivo a una red de datos o WiFi.
**Dispositivo no compatible**: no se puede usar esta aplicación porque está usando un dispositivo liberado. Póngase en contacto con el administrador de TI para obtener ayuda. | Intune detectó que el usuario usa un dispositivo liberado. | Restablezca los valores de fábrica predeterminados del dispositivo.
**Cuenta no configurada**: esta aplicación se debe administrar con Microsoft Intune, pero su cuenta no se configuró. Póngase en contacto con el administrador de TI para obtener ayuda. | La cuenta de usuario no tiene una licencia de Intune A Direct. | Asegúrese de que la cuenta del usuario tiene asignada una licencia de Intune en el [portal de Office](http://portal.office.com).
**No se puede registrar la aplicación**: esta aplicación se debe administrar con Microsoft Intune, pero no fue posible registrarla en este momento. Póngase en contacto con el administrador de TI para obtener ayuda. | Error al inscribir automáticamente la aplicación con el servicio MAM cuando se requiere la directiva de protección de aplicación. | Borre los datos de la aplicación. <br><br> Envíe registros a Intune a través de la aplicación Portal de empresa o presente una incidencia de soporte técnico [aquí](how-to-get-support-for-microsoft-intune.md).




### <a name="see-also"></a>Consulte también
- [Validar la configuración de administración de aplicaciones móviles](../deploy-use/validate-mobile-application-management.md)
- [Preparación para configurar directivas de administración de aplicaciones móviles con Microsoft Intune](../deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)
- [Cómo obtener soporte técnico para Microsoft Intune](how-to-get-support-for-microsoft-intune.md)



<!--HONumber=Dec16_HO5-->


