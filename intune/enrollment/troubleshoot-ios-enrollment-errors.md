---
title: Solución de problemas con la inscripción de dispositivos iOS en Microsoft Intune
titleSuffix: Microsoft Intune
description: Sugerencias para solucionar algunos de los problemas más comunes al inscribir dispositivos iOS en Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/18/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 46b46cd4a407df686e094198c588371ed4a01bb6
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74832573"
---
# <a name="troubleshoot-ios-device-enrollment-problems-in-microsoft-intune"></a>Solución de problemas con la inscripción de dispositivos iOS en Microsoft Intune

Este artículo ayuda a los administradores de Intune a comprender y solucionar problemas relacionados con la inscripción de dispositivos iOS en Intune.

## <a name="prerequisites"></a>Requisitos previos

Antes de empezar a solucionar problemas, es importante recopilar información básica. Esta información puede ayudarle a entender mejor el problema y reducir el tiempo para encontrar una solución.

Recopile la siguiente información acerca del problema:

- ¿Cuál es el mensaje de error exacto?
- ¿Dónde ve el mensaje de error?
- ¿Cuándo empezó el problema? ¿Alguna vez ha funcionado la inscripción?
- ¿Qué plataforma (Android, iOS, Windows) tiene el problema?
- ¿Cuántos usuarios están afectados? ¿Todos los usuarios están afectados o solo algunos?
- ¿Cuántos dispositivos se ven afectados? ¿Todos los dispositivos se ven afectados o solo algunos?
- ¿Qué es la entidad de MDM? Si System Center Configuration Manager, ¿qué versión de Configuration Manager usa?
- ¿Cómo se realiza la inscripción? ¿Es "traiga su propio dispositivo" (BYOD) o Apple Programa de inscripción de dispositivos (DEP) con perfiles de inscripción?

## <a name="error-messages"></a>Mensajes de error

### <a name="profile-installation-failed-a-network-error-has-occurred"></a>Error en la instalación del perfil. Se produjo un error de red.

**Causa:** Hay un problema no especificado con iOS en el dispositivo.

#### <a name="resolution"></a>Solución

1. Para evitar la pérdida de datos en los pasos siguientes (la restauración de iOS elimina todos los datos del dispositivo), asegúrese de hacer una copia de seguridad de los datos.
2. Ponga el dispositivo en modo de recuperación y, a continuación, restáurelo. Asegúrese de que la configura como un dispositivo nuevo. Para obtener más información sobre cómo restaurar dispositivos iOS, consulte [https://support.apple.com/HT201263](https://support.apple.com/HT201263).
3. Vuelva a inscribir el dispositivo.

### <a name="profile-installation-failed-connection-to-the-server-could-not-be-established"></a>Error en la instalación del perfil. No se pudo establecer una conexión con el servidor.

**Causa:** El inquilino de Intune está configurado para permitir solo dispositivos corporativos. 

#### <a name="resolution"></a>Solución
1. Inicie sesión en Azure Portal.
2. Seleccione **Más servicios**, busque Intune y, luego, seleccione **Intune**.
3. Seleccione **Inscripción de dispositivos** > **Restricciones de inscripción**.
4. En **restricciones de tipo de dispositivo**, seleccione la restricción que desea establecer > **propiedades** > **Seleccione plataformas** > seleccione **permitir** para **iOS**y, a continuación, haga clic en **Aceptar**.
5. Seleccione **configurar plataformas**, seleccione **permitir** dispositivos iOS de propiedad personal y, a continuación, haga clic en **Aceptar**.
6. Vuelva a inscribir el dispositivo.

**Causa:** Los registros CNAME necesarios en DNS no existen.

#### <a name="resolution"></a>Solución
Cree registros de recursos DNS CNAME para el dominio de su empresa. Por ejemplo, si el dominio de la empresa es contoso.com, cree un CNAME en DNS que redirija EnterpriseEnrollment.contoso.com a EnterpriseEnrollment-s.manage.microsoft.com.

Aunque la creación de entradas DNS CNAME es opcional, los registros CNAME facilitan la inscripción para los usuarios. Si no se encuentra ningún registro CNAME de inscripción, se pedirá a los usuarios que escriban de forma manual el nombre del servidor MDM (enrollment.manage.microsoft.com).

Si hay más de un dominio comprobado, debe crear un registro CNAME para cada dominio. Los registros de recursos CNAME deben contener la siguiente información:

|TYPE|Nombre de host|Apunta a|TTL|
|------|------|------|------|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com|1 Hr|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 Hr|

Si su organización usa varios dominios para las credenciales de usuario, cree registros CNAME para cada dominio.

> [!NOTE]
> Los cambios en los registros DNS pueden tardar hasta 72 horas en propagarse. No se puede comprobar el cambio de DNS en Intune hasta que el registro DNS se propague.

**Causa:** Inscribe un dispositivo que se inscribió previamente con una cuenta de usuario diferente y el usuario anterior no se quitó correctamente de Intune.

#### <a name="resolution"></a>Solución
1. Cancele cualquier instalación de perfil actual.
2. Abra [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com) en Safari.
3. Vuelva a inscribir el dispositivo.

> [!NOTE]
> Si todavía se produce un error en la inscripción, quite las cookies en Safari (no bloquee las cookies) y, a continuación, vuelva a inscribir el dispositivo.

**Causa:** El dispositivo ya está inscrito con otro proveedor de MDM.

#### <a name="resolution"></a>Solución
1. Abra **configuración** en el dispositivo iOS, vaya a **General > administración de dispositivos**.
2. Quite cualquier perfil de administración existente.
3. Vuelva a inscribir el dispositivo.

**Causa:** El usuario que está intentando inscribir el dispositivo no tiene una licencia de Microsoft Intune.

#### <a name="resolution"></a>Solución
1. Vaya al [centro de administración de Office 365](https://portal.office.com/adminportal/home#/homepage)y, a continuación, elija **usuarios > usuarios activos**.
2. Seleccione la cuenta de usuario a la que quiere asignar una licencia de usuario de Intune y luego elija **Licencias de producto > Editar**.
3. Cambie la alternancia a la posición **activada** para la licencia que desea asignar a este usuario y, a continuación, elija **Guardar**.
4. Vuelva a inscribir el dispositivo.

### <a name="this-service-is-not-supported-no-enrollment-policy"></a>No se admite este servicio. No hay ninguna directiva de inscripción.

**Causa**: un certificado de extracción MDM de Apple no está configurado en Intune o el certificado no es válido. 

#### <a name="resolution"></a>Solución

- Si el certificado de extracción de MDM no está configurado, siga los pasos descritos en [obtener un certificado de extracción MDM de Apple](apple-mdm-push-certificate-get.md#steps-to-get-your-certificate).
- Si el certificado de extracción de MDM no es válido, siga los pasos descritos en [renovar el certificado de extracción MDM de Apple](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate).

### <a name="company-portal-temporarily-unavailable-the-company-portal-app-encountered-a-problem-if-the-problem-persists-contact-your-system-administrator"></a>El Portal de empresa no está disponible temporalmente. La aplicación Portal de empresa detectó un problema. Si el problema persiste, póngase en contacto con el administrador del sistema.

**Causa:** La aplicación Portal de empresa no está actualizada o está dañada.

#### <a name="resolution"></a>Solución
1. Quite la aplicación Portal de empresa del dispositivo.
2. Descargue e instale la aplicación **Portal de empresa de Microsoft Intune** en el **App Store**.
3. Vuelva a inscribir el dispositivo.
 > [!NOTE]
    > Este error también puede producirse si el usuario intenta inscribir más dispositivos que la inscripción de dispositivos configurada para permitir. Siga los pasos de resolución del **límite de dispositivos** que se alcanza a continuación si estos pasos no resuelven el problema.

### <a name="device-cap-reached"></a>Se alcanzó el límite de dispositivos

**Causa:** El usuario intenta inscribir más dispositivos que el límite de inscripción de dispositivos.

#### <a name="resolution"></a>Solución
1. En el [centro de administración de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), elija **dispositivos** > **todos los dispositivos**y compruebe el número de dispositivos que el usuario ha inscrito.
    > [!NOTE]
    > También debe tener el inicio de sesión de usuario afectado en el [portal de usuarios de Intune](https://portal.manage.microsoft.com/) y comprobar los dispositivos que se han inscrito. Puede haber dispositivos que aparecen en el [portal de usuarios de Intune](https://portal.manage.microsoft.com/) , pero no en el [portal de administración de Intune](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview), estos dispositivos también cuentan para el límite de inscripción de dispositivos.
2. En el [centro de administración de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), elija **dispositivos** > **restricciones de inscripción** > Compruebe el límite de inscripción de dispositivos. De forma predeterminada, el límite es 15. 
3. Si el número de dispositivos inscritos ha alcanzado el límite, quite los dispositivos innecesarios o aumente el límite de inscripción de dispositivos. Dado que todos los dispositivos inscritos consumen una licencia de Intune, se recomienda quitar siempre los dispositivos innecesarios primero.
4. Vuelva a inscribir el dispositivo.

### <a name="workplace-join-failed"></a>Error de Workplace Join

**Causa:** La aplicación Portal de empresa no está actualizada o está dañada.  

#### <a name="resolution"></a>Solución
1. Quite la aplicación Portal de empresa del dispositivo.
2. Descargue e instale la aplicación **Portal de empresa de Microsoft Intune** en el **App Store**.
3. Vuelva a inscribir el dispositivo.

### <a name="user-license-type-invalid"></a>Tipo de licencia de usuario no válido

**Causa:** El usuario que está intentando inscribir el dispositivo no tiene una licencia válida de Intune.

#### <a name="resolution"></a>Solución
1. Vaya al [centro de administración de Microsoft 365](https://portal.office.com/adminportal/home#/homepage)y, a continuación, elija **usuarios** > **usuarios activos**.
2. Seleccione la cuenta de usuario afectada > **licencias de producto** > **Editar**.
3. Compruebe que se ha asignado una licencia de Intune válida a este usuario.
4. Vuelva a inscribir el dispositivo.

### <a name="user-name-not-recognized-this-user-account-is-not-authorized-to-use-microsoft-intune-contact-your-system-administrator-if-you-think-you-have-received-this-message-in-error"></a>Nombre de usuario no reconocido. Esta cuenta de usuario no está autorizada para usar Microsoft Intune. Si cree que ha recibido este mensaje por error, póngase en contacto con el administrador del sistema.

**Causa:** El usuario que está intentando inscribir el dispositivo no tiene una licencia válida de Intune.

1. Vaya al [centro de administración de Microsoft 365](https://portal.office.com/adminportal/home#/homepage)y, a continuación, elija **usuarios** > **usuarios activos**.
2. Seleccione la cuenta de usuario afectada y, a continuación, elija **licencias de producto** > **Editar**.
3. Compruebe que se ha asignado una licencia de Intune válida a este usuario.
4. Vuelva a inscribir el dispositivo.

### <a name="profile-installation-failed-the-new-mdm-payload-does-not-match-the-old-payload"></a>Error en la instalación del perfil. La nueva carga de MDM no coincide con la carga antigua.

**Causa:** Ya hay un perfil de Administración instalado en el dispositivo.

#### <a name="resolution"></a>Solución

1. Abra **configuración** en el dispositivo iOS > **General** > **Administración de dispositivos**.
2. Puntee en el perfil de administración existente y en **quitar administración**.
3. Vuelva a inscribir el dispositivo.

### <a name="noenrollmentpolicy"></a>NoEnrollmentPolicy

**Causa:** Falta el certificado de Apple Push Notification Service (APNs), no es válido o ha expirado.

#### <a name="resolution"></a>Solución
Compruebe que se ha agregado un certificado de APNs válido a Intune. Para más información, consulte [Configurar la administración de dispositivos iOS y Mac](https://docs.microsoft.com/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune). 

### <a name="accountnotonboarded"></a>AccountNotOnboarded

**Causa:** Hay un problema con el certificado del servicio de notificaciones push de Apple (APNs) configurado en Intune.

#### <a name="resolution"></a>Solución
Renueve el certificado de APNs y, a continuación, vuelva a inscribir el dispositivo.

> [!IMPORTANT]
> Asegúrese de renovar el certificado de APNs. No reemplace el certificado de APNs. Si reemplaza el certificado, tendrá que volver a inscribir todos los dispositivos iOS en Intune. 

- Para renovar el certificado de APNs en Intune independiente, consulte [renovar el certificado Push MDM de Apple](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate).
- Para renovar el certificado de APNs en Intune híbrido con Configuration Manager, consulte Configuración de la [Administración de dispositivos híbridos de iOS con System Center Configuration Manager y Microsoft Intune](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-ios-mac).
- Para renovar el certificado de APNs en Office 365, consulte [crear un certificado de APNs para dispositivos iOS](https://support.office.com/article/Create-an-APNs-Certificate-for-iOS-devices-522b43f4-a2ff-46f6-962a-dd4f47e546a7).

### <a name="xpc_type_error-connection-invalid"></a>Conexión XPC_TYPE_ERROR no válida

Al activar un dispositivo administrado por DEP que tiene asignado un perfil de inscripción, se produce un error en la inscripción y recibe el mensaje de error siguiente:

```
asciidoc
mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" } }
iPhone mobileassetd[83] <Notice>: Client connection invalid (Connection invalid); terminating connection
iPhone com.apple.accessibility.AccessibilityUIServer(MobileAsset)[288] <Notice>: [MobileAssetError:29] Unable to copy asset information from https://mesu.apple.com/assets/ for asset type com.apple.MobileAsset.VoiceServices.CombinedVocalizerVoices
iPhone mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" }
```

**Causa:** Hay un problema de conexión entre el dispositivo y el servicio DEP de Apple.

#### <a name="resolution"></a>Solución
Corrija el problema de conexión o use una conexión de red diferente para inscribir el dispositivo. También puede que tenga que ponerse en contacto con Apple si el problema persiste.


## <a name="other-issues"></a>Otros problemas

### <a name="dep-enrollment-doesnt-start"></a>No se inicia la inscripción de DEP
Al activar un dispositivo administrado por DEP que tiene asignado un perfil de inscripción, no se inicia el proceso de inscripción de Intune.

**Causa:** El perfil de inscripción se crea antes de que se cargue el token de DEP en Intune.

#### <a name="resolution"></a>Solución

1. Edite el perfil de inscripción. Puede hacer cualquier cambio en el perfil. El propósito es actualizar la hora de modificación del perfil.
2. Sincronizar los dispositivos administrados por DEP: en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Dispositivos** > **iOS** > **Inscripción de iOS** > **Tokens del programa de inscripción** > elija un token de la lista > **Sincronizar ahora**. Se envía una solicitud de sincronización a Apple.

### <a name="dep-enrollment-stuck-at-user-login"></a>Inscripción de DEP atascada en el inicio de sesión de usuario
Al activar un dispositivo administrado por DEP que tiene asignado un perfil de inscripción, el programa de instalación inicial se adhiere después de escribir las credenciales.

**Causa:** La autenticación multifactor (MFA) está habilitada. Actualmente MFA no funciona durante la inscripción en dispositivos DEP.

#### <a name="resolution"></a>Solución
Deshabilite MFA y, a continuación, vuelva a inscribir el dispositivo.

## <a name="next-steps"></a>Pasos siguientes

- [Solucionar problemas con la inscripción de dispositivos en Intune](../troubleshoot-device-enrollment-in-intune.md)
- [Formule una pregunta en el foro de Intune](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Revise el blog del equipo de soporte técnico de Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Revise el blog de Enterprise Mobility and Security de Microsoft](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
