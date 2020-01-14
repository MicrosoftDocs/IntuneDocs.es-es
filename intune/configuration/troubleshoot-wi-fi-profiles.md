---
title: Solución de problemas y revisión de registros de perfiles de dispositivos de Wi-Fi en Microsoft Intune - Azure | Microsoft Docs
description: Comprenda y solucione problemas de los perfiles de configuración de dispositivos de Wi-Fi en dispositivos Android, iOS y Windows en Microsoft Intune. Revise los registros y vea algunos problemas comunes y sus posibles soluciones.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 70f471e7f4db7ddce89d8956474822375c684944
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/31/2019
ms.locfileid: "75547965"
---
# <a name="troubleshoot-wi-fi-device-configuration-profiles-in-microsoft-intune"></a>Solución de problemas de perfiles de configuración de dispositivos de Wi-Fi en Microsoft Intune

En Intune, puede crear perfiles de configuración de dispositivos que incluyan la configuración de conexión de la red WiFi. Use esta configuración para conectar los dispositivos Android, iOS y Windows de los usuarios a la red de la organización.

En este artículo se muestra el aspecto de un perfil de Wi-Fi cuando se aplica correctamente a los dispositivos. También incluye información de registro, problemas comunes y mucho más. Solucione los problemas de los perfiles de Wi-Fi con la ayuda de este artículo.

Para obtener más información sobre los perfiles de Wi-Fi en Intune, consulte [Adición y uso de la configuración de Wi-Fi en los dispositivos](wi-fi-settings-configure.md).

## <a name="before-you-begin"></a>Antes de comenzar

En los ejemplos de este artículo se usa la autenticación de certificados SCEP para los perfiles de Intune. También se supone que los perfiles de SCEP y raíz de confianza funcionan correctamente en el dispositivo.

## <a name="android"></a>Android

En esta sección, se detallará la experiencia del usuario final al instalar los perfiles de configuración en un dispositivo Android.

### <a name="end-user-experience-example"></a>Ejemplo de experiencia del usuario final

En este escenario se usa un dispositivo Nokia 6.1. Antes de instalar el perfil de Wi-Fi en el dispositivo, instale los perfiles de SCEP y raíz de confianza.

1. Los usuarios finales reciben una notificación para instalar el perfil de certificado raíz de confianza:

    > [!div class="mx-imgBorder"]
    > ![Ejemplo de notificación de la aplicación Portal de empresa en Android para instalar el perfil de certificado raíz de confianza](./media/troubleshoot-wi-fi-profiles/android-end-user-company-portal-trusted-root.png)

2. La siguiente notificación solicita la instalación del perfil de certificado SCEP:

    > [!div class="mx-imgBorder"]
    > ![Ejemplo de notificación de la aplicación Portal de empresa en Android para instalar el perfil de certificado SCEP](./media/troubleshoot-wi-fi-profiles/android-end-user-company-portal-scep-certificate.png)

    > [!TIP]
    > Al usar un dispositivo Android administrado por el administrador de dispositivos, puede que aparezcan varios certificados. Cuando se revoca o se quita un perfil de certificado, el certificado permanece en el dispositivo. En este escenario, seleccione el certificado más reciente. Normalmente es el último certificado que se muestra en la lista.
    >
    > Esta situación no se produce en dispositivos Android Enterprise y Samsung Knox. Para obtener más información, consulte [Administrar dispositivos de perfil de trabajo Android](../enrollment/android-enterprise-overview.md) y [Eliminación de certificados SCEP y PKCS](../protect/remove-certificates.md#android-knox-devices).

3. A continuación, los usuarios reciben una notificación para instalar el perfil de Wi-Fi:

    > [!div class="mx-imgBorder"]
    > ![Ejemplo de notificación de la aplicación Portal de empresa en Android para instalar el perfil de certificado SCEP](./media/troubleshoot-wi-fi-profiles/android-end-user-install-wifi-profile.png)

4. Cuando haya finalizado, la conexión Wi-Fi se muestra como una red guardada:

    > [!div class="mx-imgBorder"]
    > ![La conexión Wi-Fi se muestra como una red guardada](./media/troubleshoot-wi-fi-profiles/android-end-user-saved-networks.png)

### <a name="review-company-portal-app-logs"></a>Revisión de registro de la aplicación Portal de empresa

En Android, el archivo **Omadmlog.log** detalla las actividades del perfil de Wi-Fi cuando se instala en el dispositivo. Puede tener hasta cinco archivos de registro de Omadmlog. Asegúrese de obtener la marca de tiempo de la última sincronización, ya que le ayudará a encontrar las entradas de registro relacionadas.

En el ejemplo siguiente, use [CMTrace](https://docs.microsoft.com/configmgr/core/support/cmtrace) para leer los registros y busque "wifimgr":

> [!div class="mx-imgBorder"]
> ![La conexión Wi-Fi se muestra como una red guardada](./media/troubleshoot-wi-fi-profiles/android-cmtrace-filter-wifimgr.png)

En el registro siguiente se muestran los resultados de la búsqueda, así como el perfil de Wi-Fi aplicado correctamente:

```log
2019-08-01T19:22:46.7340000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Starting to parse Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:46.7490000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:46.8100000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:46.8209999    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Completed parsing Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:46.8240000    INFO    com.microsoft.omadm.utils.CertificateSelector    15118    04142    Selected ca certificate with alias: 'user:205xxxxx.0' and thumbprint '<thumbprint>'.
2019-08-01T19:22:47.0990000    VERB    com.microsoft.omadm.platforms.android.certmgr.CertificateChainBuilder    15118    04142    Complete certificate chain built with Complete certs.
2019-08-01T19:22:47.1010000    VERB    com.microsoft.omadm.utils.CertUtils    15118    04142    1 cert(s) matched criteria: User<ID>[i:<ID>,17CECEA1D337FAA7D167AD83A8CC7A8FCBF9xxxx;eku:1.3.6.1.5.5.7.3.1,1.3.6.1.5.5.7.3.2]
2019-08-01T19:22:47.1090000    VERB    com.microsoft.omadm.utils.CertUtils    15118    04142    0 cert(s) excluded by criteria:
2019-08-01T19:22:47.1110000    INFO    com.microsoft.omadm.utils.CertificateSelector    15118    04142    Selected client cert with alias 'User<ID>' and requestId 'ModelName=<ModelName>%2FLogicalName_<LogicalName>;Hash=-912418295'.
2019-08-01T19:22:47.4120000    VERB    com.microsoft.omadm.Services    15118    04142    Successfully applied, enabled and saved wifi profile '<profile ID>'
2019-08-01T19:22:47.4240000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:47.4910000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:47.4970000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Starting to parse Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:47.5080000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:47.5820000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:47.5900000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Completed parsing Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:47.5910000    INFO    com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager    15118    04142    Applied profile <profile ID>

```

## <a name="ios"></a>iOS

Después de instalar el perfil de Wi-Fi en el dispositivo, se muestra en el **Perfil de administración**:

> [!div class="mx-imgBorder"]
> ![Perfil de administración en dispositivo iOS](./media/troubleshoot-wi-fi-profiles/ios-management-profile.png)

> [!div class="mx-imgBorder"]
> ![La conexión Wi-Fi se muestra como una red Wi-Fi en el dispositivo iOS](./media/troubleshoot-wi-fi-profiles/ios-wifi-connection-in-management-profile.png)

### <a name="review-the-ios-console-and-device-logs"></a>Revisión de los registros del dispositivo y la consola iOS

En los dispositivos iOS, el registro de la aplicación Portal de empresa no incluye información sobre los perfiles de Wi-Fi. Para ver los detalles de la instalación de los perfiles de Wi-Fi, use los registros de consola/dispositivo:

1. Conecte el dispositivo iOS a Mac. Vaya a **Aplicaciones** > **Utilidades**y abra la aplicación Consola.
2. En **Acción**, seleccione **Incluir mensajes de información** e **Incluir mensajes de depuración**:

    > [!div class="mx-imgBorder"]
    > ![Incluir mensajes de información e Incluir mensajes de depuración en la aplicación de consola de iOS](./media/troubleshoot-wi-fi-profiles/ios-console-app-include-info-messages-debug-messages.png)

3. Reproduzca el escenario y guarde los registros en un archivo de texto:

    1. Seleccione todos los mensajes en la pantalla actual: **Editar** > **Seleccionar todo**.
    2. Copie los mensajes: **Editar** > **Copiar**.
    3. Pegue los datos de registro en un editor de texto y guarde el archivo.

4. Busque en el archivo de registro guardado para ver información detallada. Cuando el perfil se instala correctamente, el resultado es similar al siguiente registro:

    ```log
    Line 390870: debug    11:19:58.994815 -0400    profiled    Adding dependent www.windowsintune.com.wifi.Contoso to parent Microsoft.Profiles.MDM in domain ManagingProfileToManagedProfile to system\
    Line 390872: debug    11:19:58.995210 -0400    profiled    Adding dependent Microsoft.Profiles.MDM to parent www.windowsintune.com.wifi.Contoso in domain ManagedProfileToManagingProfile to system\
    Line 392346: default    11:19:59.360460 -0400    profiled    Profile \'93www.windowsintune.com.wifi.Contoso\'94 installed.\
    ```

## <a name="windows"></a>Windows

Después de instalar el perfil de Wi-Fi en el dispositivo, vaya a **Configuración** > **Cuentas** > **Obtener acceso a trabajo o escuela**. Seleccione su cuenta > **Información**:

> [!div class="mx-imgBorder"]
> ![Obtener acceso a trabajo o escuela y selección de Información en un dispositivo Windows](./media/troubleshoot-wi-fi-profiles/windows-access-work-school-info.png)

En las **áreas administradas por Microsoft**, se muestra **Wi-Fi**:

> [!div class="mx-imgBorder"]
> ![En las áreas administradas por Microsoft, vea qué Wi-Fi aparece en Windows](./media/troubleshoot-wi-fi-profiles/windows-wifi-areas-managed-by-microsoft.png)

Para ver la conexión Wi-Fi, vaya a **Configuración** > **Red e Internet**  > **Wi-Fi**:

> [!div class="mx-imgBorder"]
> ![En Windows, consulta de la conexión Wi-Fi como red conocida en la configuración](./media/troubleshoot-wi-fi-profiles/windows-wifi-connection-known-networks.png)

### <a name="review-event-viewer-logs"></a>Revisión de los registros del visor de eventos

En los dispositivos Windows, los detalles acerca de los perfiles de Wi-Fi se registran en el Visor de eventos:

1. Abra la aplicación **Visor de eventos**.
2. En el menú **Ver**, seleccione **Mostrar registros de análisis y depuración**.
3. Expanda **Registros de aplicaciones y servicios** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostic-Provider** > **Administración**.

El resultado será similar a los registros siguientes:

```log
Log Name:      Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
Source:        Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider
Date:          8/7/2019 8:01:41 PM
Event ID:      1506
Task Category: (1)
Level:         Information
Keywords:      (2)
User:          SYSTEM
Computer:      <Computer Name>
Description:
WiFiConfigurationServiceProvider: Node set value, type: (0x4), Result: (The operation completed successfully.).
```

## <a name="common-issues"></a>Problemas comunes

### <a name="issue-1-the-wi-fi-profile-isnt-deployed-to-the-device"></a>Problema 1: El perfil de Wi-Fi no está implementado en el dispositivo.

- Confirme que el perfil de Wi-Fi está asignado al grupo correcto:

    1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), seleccione **Dispositivos** > **Perfiles de configuración**.
    2. Seleccione su perfil > **Asignaciones**. Confirme que los grupos seleccionados son correctos.
    3. En el Administrador de puntos de conexión, seleccione **Solución de problemas + soporte técnico**. Revise la información sobre las **Asignaciones**.

- En el Administrador de puntos de conexión, seleccione **Solución de problemas + soporte técnico**. Confirme que el dispositivo puede sincronizarse con Intune. Para ello, compruebe **Última conexión**.

- Si el perfil de Wi-Fi está vinculado a los perfiles de SCEP y raíz de confianza, confirme que ambos perfiles estén implementados en el dispositivo. El perfil de Wi-Fi tiene una dependencia en estos perfiles.

- En los dispositivos Windows 10 y versiones más recientes, revise el registro de información de diagnóstico de MDM:

  1. Vaya a **Configuración** > **Cuentas** > **Obtener acceso a trabajo o escuela**.
  2. Seleccione su cuenta profesional o educativa > **Información**.
  3. En la parte inferior de la página **Configuración**, seleccione **Crear informe**.
  4. Se abre una ventana que muestra la ruta de acceso a los archivos de registro. Seleccione **Exportar**.
  5. Vaya a la ruta de acceso `\Users\Public\Documents\MDMDiagnostics` y vea el informe:

      > [!div class="mx-imgBorder"]
      > ![Información de diagnóstico de MDM de ejemplo que muestra la configuración del perfil de Wi-Fi en dispositivos Windows 10](./media/troubleshoot-wi-fi-profiles/windows-mdm-diagnostic-info.png)

  > [!TIP]
  > Para obtener más información, consulte [Diagnosticar errores de MDM en Windows 10](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10).

- En dispositivos Android, si los perfiles de SCEP y raíz de confianza no están instalados en el dispositivo, verá la siguiente entrada en el archivo Omadmlog de la aplicación Portal de empresa:

  ``` log
  2019-08-01T19:18:13.5120000    INFO    com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager    15118    04105    Skipping Wifi profile <profile ID> because it is pending certificates.
  ```

  - Si los perfiles de SCEP y raíz de confianza se encuentran en el dispositivo Android y están conformes, es posible que el perfil de Wi-Fi no esté en el dispositivo. Este problema se produce cuando el proveedor **CertificateSelector** de la aplicación Portal de empresa no encuentra un certificado que coincida con los criterios especificados. Los criterios específicos pueden estar en la plantilla de certificado o en el perfil de SCEP.

    Si no se encuentra el certificado coincidente, los certificados del dispositivo no se instalan. El perfil de Wi-Fi no se aplica porque no tiene el certificado correcto. En este escenario, verá la siguiente entrada en el archivo Omadmlog de la aplicación Portal de empresa:

    ` Skipping Wifi profile <profile ID> because it is pending certificates.`

    En el siguiente registro de ejemplo se muestran los certificados que se excluyen porque se especificó el criterio de uso mejorado de clave (EKU) **Cualquier propósito**. Sin embargo, los certificados asignados al dispositivo no tienen ese EKU:

    ```log
    2018-11-27T21:10:37.6390000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    Excluding cert with alias User<ID1> and requestId <requestID1> as it does not have any purpose EKU.
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    Excluding cert with alias User<ID2> and requestId <requestID2> as it does not have any purpose EKU.
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    0 cert(s) matched criteria:
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    2 cert(s) excluded by criteria:
    2018-11-27T21:10:37.6400000    INFO       com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager       14210                00948     Skipping Wifi profile <profile ID> because it is pending certificates.
    ```

    En el ejemplo siguiente se muestra el perfil de SCEP especificado en el EKU **Cualquier propósito**. Sin embargo, no se especifica en la plantilla de certificado de la entidad de certificación (CA). Para solucionar el problema, agregue la opción **Cualquier propósito** a la plantilla de certificado. O bien, quite la opción **Cualquier propósito** del perfil de SCEP.

    > [!div class="mx-imgBorder"]
    > ![En Android, adición de Cualquier propósito a la plantilla de certificado en la entidad de certificación](./media/troubleshoot-wi-fi-profiles/android-add-any-purpose-eku.png)

    > [!div class="mx-imgBorder"]
    > ![En Android, adición de Cualquier propósito al perfil de configuración de certificado SCEP en Intune](./media/troubleshoot-wi-fi-profiles/android-any-purpose-scep-device-config-profile.png)

  - Confirme que todos los certificados necesarios en toda la cadena de certificados están en el dispositivo Android. De lo contrario, no se podrá instalar el perfil de Wi-Fi en el dispositivo. Para obtener más información, vea [Falta de autoridad de certificación intermedia](https://developer.android.com/training/articles/security-ssl#MissingCa) (se abre el sitio web de Android).
  - Filtre Omadmlog con palabras clave para buscar información, como qué certificado se usa en el perfil de Wi-Fi y si el perfil se aplicó correctamente.

    Por ejemplo, use [CMTrace](https://docs.microsoft.com/configmgr/core/support/cmtrace) para leer los registros. Use la cadena de búsqueda para filtrar "wifimgr":

    > [!div class="mx-imgBorder"]
    > ![Filtrado de CMTrace para buscar perfiles de configuración de WiFiMgr en dispositivos Android](./media/troubleshoot-wi-fi-profiles/cmtrace-filter-wifimgr.png)

    El resultado es similar al registro siguiente:

    > [!div class="mx-imgBorder"]
    > ![Ejemplo de salida de registro CMTrace que muestra el perfil de configuración de Intune de Wi-Fi aplicado correctamente en los dispositivos](./media/troubleshoot-wi-fi-profiles/cmtrace-sample-log-output.png)

    Si ve un error en el registro, copie la marca de tiempo del error y anule el filtrado del registro. A continuación, use la opción de buscar con la marca de tiempo para ver lo que sucedió justo antes del error.

### <a name="issue-2-the-wi-fi-profile-is-deployed-to-the-device-but-the-device-cant-connect-to-the-network"></a>Problema 2: El perfil de Wi-Fi se implementa en el dispositivo, pero el dispositivo no se puede conectar a la red.

Normalmente, este problema se debe a algo ajeno a Intune. Las tareas siguientes pueden ayudarle a comprender y solucionar problemas de conectividad:

- Conéctese manualmente a la red mediante un certificado con los mismos criterios que se encuentran en el perfil de Wi-Fi.

  Si puede conectarse, examine las propiedades del certificado en la conexión manual. A continuación, actualice el perfil de Wi-Fi de Intune con las mismas propiedades de certificado.
- Normalmente, los errores de conectividad se registran en el registro del servidor Radius. Por ejemplo, debería mostrar si el dispositivo intentó conectarse con el perfil de Wi-Fi.

## <a name="need-more-help"></a>¿Necesita más ayuda?

- Use los [foros de usuarios de Intune](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc) o [obtenga soporte técnico de Microsoft](../fundamentals/get-support.md).

- Para obtener más información sobre los perfiles de Wi-Fi en Microsoft Intune, consulte los siguientes artículos:

  - Adición de la configuración de Wi-Fi para dispositivos que ejecutan [Android](wi-fi-settings-android.md), [iOS](wi-fi-settings-ios.md) y [Windows 10 y versiones posteriores](wi-fi-settings-windows.md).
  - [Sugerencia de soporte técnico: configuración de NDES para implementaciones de certificados SCEP en Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-How-to-configure-NDES-for-SCEP-certificate/ba-p/455125)
  - Solucione los problemas de la [implementación del perfil de certificado SCEP](https://support.microsoft.com/help/4526725/troubleshooting-scep-profile-deployment-to-android-devices-in-intune) y [configuración de NDES](https://support.microsoft.com/help/4459540/troubleshoot-ndes-configuration-for-use-with-intune).

- Para obtener las últimas noticias, informaciones y consejos técnicos, consulte los blogs oficiales:
  - [Blog del equipo de soporte técnico de Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
  - [Blog de Enterprise Mobility and Security de Microsoft](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/bg-p/enterprisemobilityandsecurity)

## <a name="next-steps"></a>Pasos siguientes

[Supervisar perfiles de dispositivo](device-profile-monitor.md).
