---
title: "Requisitos previos para la inscripción de dispositivos móviles | Microsoft Docs"
description: "Configure los requisitos previos de administración de dispositivos móviles (MDM) y prepárese para inscribir distintos sistemas operativos."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 44fd4af0-f9b0-493a-b590-7825139d9d40
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e7beff3bf4579d9fb79f0c3f2fb8fbf9bb1ea160
ms.openlocfilehash: fc97e1266c2e859104b21f3bf4ff24f33123f66a
ms.lasthandoff: 02/22/2017


---

# <a name="prerequisites-for-mobile-device-management-in-intune"></a>Requisitos previos para la administración de dispositivos móviles en Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Para permitir que los empleados inscriban sus dispositivos móviles con Intune, debe llevar a cabo los pasos siguientes. Estos mismos pasos son necesarios para administrar dispositivos de empresa.

|Pasos|Detalles|  
|-----------|-------------|  
|**Paso 1:** [Habilitar conexiones](#step-1-enable-connections)|Asegúrese de que el nombre de dominio personalizado está configurado y la comunicación de red está lista.|  
|**Paso 2:** [Configurar la entidad de MDM](#step-2-set-mdm-authority)|La entidad de administración de dispositivos móviles define el servicio asignado a los dispositivos.|
|**Paso 3:** [Crear grupos](#step-3-create-groups)|Configure las opciones orientadas al usuario de la aplicación de portal de empresa.|  
|**Paso 4:** [ Configurar el portal de empresa](#step-4-configure-company-portal)|Configure las opciones orientadas al usuario de la aplicación de portal de empresa.|  
|**Paso 5:** [Asignar licencias de usuario](#step-5-assign-user-licenses)|Asigne licencias de Intune a los usuarios para que puedan inscribir dispositivos.|
|**Paso 6:** [Habilitar la inscripción](#step-6-enable-enrollment)|Habilite la configuración específica de la plataforma para la administración de iOS y Windows. Los dispositivos Android no necesitan ninguna configuración adicional.|
|**Paso 7:** [Pasos siguientes](#step-7-next-steps)|Habilite la configuración específica de la plataforma para la administración de iOS y Windows. Los dispositivos Android no necesitan ninguna configuración adicional.|

¿Busca Intune con Configuration Manager?
> [!div class="button"]
[Consulte los documentos SCCM >](https://docs.microsoft.com/sccm/mdm/deploy-use/setup-hybrid-mdm)

## <a name="step-1-enable-connections"></a>Paso 1: Habilitar conexiones

Antes de habilitar la inscripción de dispositivos móviles, asegúrese de que ha hecho lo siguiente:
- [Ha revisado los puertos y las direcciones URL de red necesarios](../get-started/network-infrastructure-requirements-for-microsoft-intune.md)
- [Ha agregado y comprobado su nombre de dominio](../get-started/domain-names-for-microsoft-intune.md)

## <a name="step-2-set-mdm-authority"></a>Paso 2: Configurar entidad de MDM
La entidad de MDM define el servicio de administración que tiene permiso para administrar un conjunto de dispositivos. Las opciones para la entidad de MDM incluyen Intune y Configuration Manager con Intune. Si establece Configuration Manager como la entidad de administración, ningún otro servicio podrá usarse para la administración de dispositivos móviles.

>[!IMPORTANT]
> Considere detenidamente si quiere administrar los dispositivos móviles solo mediante Intune (servicio en línea) o mediante System Center Configuration Manager con Intune (solución de software local junto con el servicio en línea). Después de establecer la entidad de administración de dispositivos móviles, no puede cambiarla sin ayuda de Soporte técnico de Microsoft. Vea [Qué hacer si se elige la configuración incorrecta de la entidad de MDM](#what-to-do-if-you-choose-the-wrong-mdm-authority-setting) para obtener instrucciones.


1.  En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), haga clic en **Administración** &gt; **Administración de dispositivos móviles**.

2.  En la lista **Tareas** , haga clic en **Configurar entidad de administración de dispositivos móviles**. Se abre el cuadro de diálogo **Establecer entidad de administración de dispositivos móviles** .

    ![Cuadro de diálogo Establecer entidad de MDM](../media/intune-mdm-authority.png)

3.  Intune solicita confirmación de que desea que Intune sea su entidad de MDM. Seleccione la casilla y elija **Sí** si quiere usar Microsoft Intune para administrar dispositivos móviles.

## <a name="step-3-create-groups"></a>Paso 3: Crear grupos

Puede crear grupos de usuarios y dispositivos para simplificar la administración e identificar mejor el destino de las aplicaciones implementadas, las directivas y los recursos de la empresa. [Aprenda a crear grupos](use-groups-to-manage-users-and-devices-with-microsoft-intune.md#create-groups).

## <a name="step-4-configure-company-portal"></a>Paso 4: Configurar el Portal de empresa

El portal de empresa de Intune es el lugar donde los usuarios tienen acceso a los datos de la empresa y pueden realizar tareas habituales como, por ejemplo, inscribir dispositivos, instalar aplicaciones y buscar información de ayuda del departamento de TI.

> [!TIP]
> Al personalizar el portal de empresa, los valores de configuración se aplicarán tanto al sitio web como a las aplicaciones del portal de empresa.

Con la personalización del Portal de empresa, es más fácil ofrecer una experiencia conocida y útil a los usuarios finales. Para proceder a la personalización, inicie sesión en la [consola de administración de Microsoft Intune](https://manage.microsoft.com) como administrador de inquilinos o de servicios, elija **Administración** &gt; **Portal de empresa** y configure el Portal de empresa.

![admin-console-admin-workspace-comp-portal-settings](../media/cp_sa_cpsetup.PNG)

### <a name="company-contact-information-and-privacy-statement"></a>Información de contacto y declaración de privacidad de la empresa

El nombre de la empresa se muestra como título del portal de empresa. La información y los datos de contacto se muestran a los usuarios en la pantalla Contacto de TI del portal de empresa. La declaración de privacidad se muestra cuando el usuario hace clic en el vínculo de privacidad.

|Nombre de campo|Longitud máxima|Más información|
    |----------|------------------------|----------------|
    |Nombre de la empresa|40|Es el nombre que se muestra como título del portal de empresa. **Nota**: Solo caracteres alfanuméricos. Este campo no admite caracteres especiales.|
    |Nombre del contacto del departamento de TI|40|Es el nombre que se muestra en la página **Contacto de TI**.|
    |Número de teléfono del departamento de TI|20|Es el número de contacto que se muestra en la página **Contacto de TI**.|
    |Dirección de correo electrónico del departamento de TI|40|Es la dirección de contacto que se muestra en la página **Contacto de TI**. Debe especificar una dirección de correo electrónico válida en el formato **alias@domainname.com**.|
    |Información adicional|120|Esta información se muestra en la página **Contact IT** (Contacto de TI).|
    |Dirección URL de la declaración de privacidad de la empresa|79|Puede especificar su propia declaración de privacidad de la empresa, que aparece cuando los usuarios hacen clic en los vínculos de privacidad del portal de empresa. Debe escribir una dirección URL válida con el formato https://www.contoso.com.|

### <a name="support-contacts"></a>Contactos de soporte técnico
El sitio web de soporte se muestra a los usuarios en el portal de empresa para que puedan tener acceso al soporte en línea.

|Nombre del campo|Longitud máxima|Más información|
    |----------|------------------------|----------------|
    |Dirección URL del sitio web de soporte:|150|Si tiene un sitio web de soporte que desea que utilicen los usuarios finales, especifique la dirección URL aquí. La dirección URL debe tener el formato https://www.contoso.com. Si no especifica una dirección URL, no se mostrará ningún sitio web de soporte en la página **Contacto de TI** del portal de empresa.|
    |Nombre del sitio web|40|Este nombre es el nombre descriptivo que se muestra para la dirección URL del sitio web de soporte. Si solo especifica una dirección URL de sitio web de soporte sin nombre descriptivo, se mostrará **Ir a sitio web de TI** en la página **Contacto de TI** del portal de empresa.|


### <a name="company-branding-customization"></a>Personalización de la marca de empresa

Puede personalizar su Portal de empresa con su logotipo de empresa, nombre de empresa, color de tema y fondo.

|Nombre de campo|Más información|
    |----------|----------------|
    |Color del tema|Seleccione el color del tema que se aplicará al portal de empresa.|
    |Incluir el logotipo de la empresa|Si habilita esta opción, puede cargar el logotipo de su empresa para que se muestre en el portal de empresa. Puede cargar dos logotipos: uno que se mostrará cuando el fondo del portal de empresa sea de color blanco y otro que se mostrará cuando el fondo del portal de empresa use el color de tema seleccionado. El archivo del logotipo debe ser .png o .jpg, con una resolución máxima de 400 x 100 píxeles y un tamaño de 750 KB o menos.|
    |Elegir un fondo para la aplicación de portal de empresa|Esta opción de configuración solo afecta al fondo de la aplicación de portal de empresa.|


Después de guardar los cambios, puede usar los vínculos que aparecen en la parte inferior de la página del **Portal de empresa** de la consola de administración para ver el sitio web del Portal de empresa. Estos vínculos no se pueden cambiar. Cuando un usuario inicia sesión, estos vínculos muestran las suscripciones en el portal de empresa.

## <a name="step-5-assign-user-licenses"></a>Paso 5: Asignar licencias de usuario

El **portal de administración de Office 365** se usa para agregar manualmente usuarios basados en la nube y asignar licencias a las cuentas de usuario basadas en la nube y a las cuentas sincronizadas desde Active Directory local con Azure Active Directory (Azure AD). Puede [sincronizar usuarios locales con Azure AD](../get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3.md#how-to-sync-on-premises-users-with-azure-ad).

1.  Inicie sesión en el [portal de administración de Office 365](https://portal.office.com/Admin/Default.aspx) con las credenciales del administrador de inquilinos.

2.  Seleccione la cuenta de usuario a la que quiere asignar una licencia de usuario de Intune y seleccione la casilla **Microsoft Intune** en las propiedades de la cuenta de usuario.

3.  La cuenta de usuario se agregará al grupo de usuarios de Microsoft Intune que concede al usuario permisos para usar el servicio e inscribir sus dispositivos en la administración.

### <a name="to-synchronize-on-premises-users-with-azure-ad"></a>Para sincronizar usuarios locales con Azure AD

1. [Agregue el sufijo UPN](https://technet.microsoft.com/en-us/library/cc772007.aspx) para su dominio personalizado en su Active Directory local.
2. Establezca el nuevo sufijo UPN para los usuarios locales que planea importar.
3. Ejecute la [sincronización de Azure AD Connect](https://azure.microsoft.com/en-us/documentation/articles/active-directory-aadconnect/) para integrar sus usuarios locales con Azure AD.
4. Una vez que la información de cuenta de usuario se haya sincronizado correctamente, puede asignar las licencias de Microsoft Intune mediante el [Portal de administración de Office 365](https://portal.office.com/Admin/Default.aspx).

## <a name="step-6-enable-enrollment"></a>Paso 6: Habilitar la inscripción
Después de configurar la entidad de MDM, debe configurar la administración de dispositivos para los sistemas operativos que su organización quiere admitir. Los pasos necesarios para configurar la administración de dispositivos varían según el sistema operativo. Por ejemplo, el sistema operativo Android no necesita que haga nada en la consola de administración de Intune. Por otro lado, Windows y iOS necesitan una relación de confianza entre los dispositivos e Intune para permitir la administración.

Configurar la administración de las plataformas siguientes:
- [iOS y Mac](set-up-ios-and-mac-management-with-microsoft-intune.md)
- [Android](set-up-android-management-with-microsoft-intune.md)
- [Android for Work](set-up-android-for-work.md)
- [Equipos y portátiles con Windows](set-up-windows-device-management-with-microsoft-intune.md)
- [Windows 10 Mobile y Windows Phone](set-up-windows-phone-management-with-microsoft-intune.md)

También puede habilitar la [inscripción de dispositivos corporativos](manage-corporate-owned-devices.md).

## <a name="step-7-next-steps"></a>Paso 7: Pasos siguientes

Ahora que la inscripción está habilitada, debe configurar la administración para satisfacer las necesidades de su negocio. Las siguientes son algunas opciones de administración:

- [Implementar directivas que administren la configuración y las características de los dispositivos](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
- [Permitir el acceso a recursos de la empresa, como correo electrónico, Wi-Fi y VPN](enable-access-to-company-resources-with-microsoft-intune.md)
- [Agregar aplicaciones](add-apps.md) e [implementarlas](deploy-apps.md) en dispositivos administrados
- [Crear directivas de cumplimiento de dispositivo](introduction-to-device-compliance-policies-in-microsoft-intune.md) y [restringir el acceso basándose en el cumplimiento](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)

## <a name="what-to-do-if-you-choose-the-wrong-mdm-authority-setting"></a>Qué hacer si se elige la configuración incorrecta de la entidad de MDM

Si decide que ha elegido la configuración incorrecta de la entidad de MDM y necesita cambiarla, debe ponerse en contacto con Soporte técnico de Microsoft. No puede cambiarla por sí mismo. Antes de ponerse en contacto con Soporte técnico de Microsoft, lea la información siguiente, en la que se indican los datos que necesitará Soporte técnico de Microsoft para realizar el cambio.

Hay tres formas posibles de restablecer la entidad de MDM. En la solicitud de soporte técnico, tendrá que elegir la forma correspondiente a su situación. Si el escenario que va a solicitar no aparece, realice un seguimiento con Soporte técnico de Microsoft.

Soporte técnico de Microsoft le pedirá que confirme la información siguiente:

- Id. de inquilino: dominio usado para iniciar sesión en el servicio (por ejemplo, intune.onmicrosoft.com)
- La entidad de MDM a la que quiere cambiar
- Confirmación de los pasos de requisitos previos completados, como se muestra a continuación

Si usa la coexistencia, tiene que repasar las listas de comprobación de Intune y Office 365.

### <a name="reset-mdm-authority-from-intune-to-configuration-manager"></a>Restablecer la entidad de MDM de Intune a Configuration Manager

Realice estos pasos antes de ponerse en contacto con Soporte técnico de Microsoft para restablecer la entidad de MDM.

- Quite todos los dispositivos de la consola de administración de Intune. No intente quitar un dispositivo desde el propio dispositivo. 
- Elimine Service To Service Connector (en **Administración** > **Administración de dispositivos móviles** > **Microsoft Exchange**) o deshabilite Exchange Connector si lo tenía configurado. 
- Quite el rol Administrador de inscripción de dispositivos de **Administración** > **Administrador de inscripción de dispositivos**.
- Desactive Asignación de grupos de dispositivos en **Administración** > **Administración de dispositivos móviles** > **Asignación de grupos de dispositivos**.
- Elimine las claves de instalación de prueba en **Administración** > **Administración de dispositivos móviles** > **Windows** > **Claves de instalación de prueba**.
- Elimine el certificado de APNs de iOS en la página **Administración** > **Administración de dispositivos móviles** > **iOS**.
- Elimine el token de DEP de iOS en la página **Administración** > **Administración de dispositivos móviles** > **iOS**.
- Elimine todas las directivas para los dispositivos MDM en **Directivas** > **Directivas de configuración**.
- Elimine todas las aplicaciones publicadas para los dispositivos MDM en **Aplicaciones** > **Software administrado**.

### <a name="reset-mdm-authority-from-configuration-manager-to-intune"></a>Restablecer la entidad de MDM de Configuration Manager a Intune

Realice estos pasos antes de ponerse en contacto con Soporte técnico de Microsoft para restablecer la entidad de MDM.

- Quite todos los dispositivos (que se administren como dispositivos móviles) de la consola de Configuration Manager. No intente quitar un dispositivo desde el propio dispositivo. 
- Quite todos los usuarios del grupo de usuarios de Intune. Apunte la suscripción de Intune a una colección de usuarios vacía o quite todos los usuarios de la colección de destino.  En CloudUserSync.log, confirme que se han quitado los usuarios. 
- Desmarque la plataforma iOS para purgar el certificado de APNs.
- Elimine todas las aplicaciones publicadas para los dispositivos MDM.
- Elimine todas las directivas para los dispositivos MDM. 
- Quite el conector de Windows Intune de la consola de Configuration Manager (aplicable solo a R2 SP1 o inferior).
-Quite la suscripción de Intune al hacer clic con el botón derecho en la suscripción y seleccionar **Eliminar**.
- Reinicie el servicio SMS Executive.
- Proporcione algunos usuarios de ejemplo para que se pueda comprobar, una vez finalizado el proceso, que se han quitado las licencias de Configuration Manager.

### <a name="reset-mdm-authority-from-office-365-to-configuration-manager"></a>Restablecer la entidad de MDM de Office 365 a Configuration Manager

1. Vaya a [https://protection.office.com](https://protection.office.com).
2. Seleccione la pestaña **Directivas de seguridad** y luego **Administración de dispositivos**. 
3. Quite todos los dispositivos al elegir **Borrado selectivo**. No intente quitar un dispositivo desde el propio dispositivo. Si el borrado selectivo está deshabilitado, no hay que hacer nada más.
4. Seleccione la pestaña **Directivas de seguridad** y luego **Directivas de seguridad de dispositivos**. 
5. Seleccione **Eliminar** para todas las directivas existentes. Si las directivas están en un estado pendiente, no hay que hacer nada más.

>[!NOTE]
>El certificado de APNs de iOS no se puede eliminar y permanece unido a la cuenta. 

### <a name="next-steps-for-mdm-authority-resets"></a>Pasos siguientes para restablecimientos de la entidad de MDM

Una vez que Soporte técnico de Microsoft verifica los elementos de la lista de comprobación correspondiente, el restablecimiento de la entidad de MDM puede llevar hasta tres días laborables, aunque normalmente se realiza en un día. 

>[!IMPORTANT]
>No intente configurar la suscripción hasta que Soporte técnico de Microsoft confirme que el restablecimiento se ha realizado correctamente. Una configuración prematura puede causar daños o afectar a la posibilidad de usar el servicio Intune. 

