---
title: Solucionar problemas de instalación de aplicaciones
titleSuffix: Microsoft Intune
description: Use el panel de solución de problemas de Microsoft Intune, el cual le ayuda a solucionar problemas de instalación de aplicaciones.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: be66f99006b06dce9f9bfe21eafa9f2be302e7b9
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "76540986"
---
# <a name="troubleshoot-app-installation-issues"></a>Solucionar problemas de instalación de aplicaciones

En algunas ocasiones, las instalaciones de aplicaciones en los dispositivos administrados por MDM de Microsoft Intune pueden presentar errores. Cuando esto ocurre, puede ser complicado entender el motivo del error o cómo solucionarlo. Microsoft Intune proporciona detalles del error de instalación de aplicaciones que permiten a los operadores del departamento de soporte técnico y a los administradores de Intune ver información de la aplicación para atender las solicitudes de ayuda al usuario. En el panel de solución de problemas de Intune se proporcionan detalles del error, incluidos aquellos sobre las aplicaciones administradas en el dispositivo de un usuario. Se proporcionan detalles sobre el ciclo de vida de un extremo a otro en cada dispositivo individual del panel **Aplicaciones administradas**. Puede ver problemas de instalación, por ejemplo, al crearse, modificarse, dirigirse y entregarse la aplicación a un dispositivo. 

> [!NOTE]
> Para obtener información sobre el código de error de instalación de la aplicación, vea [Referencia de errores de instalación de aplicaciones de Intune](~/apps/app-install-error-codes.md).

## <a name="app-troubleshooting-details"></a>Detalles de solución de problemas de aplicaciones

Intune proporciona los detalles de solución de problemas de la aplicación en función de las aplicaciones instaladas en el dispositivo de un usuario específico.

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Seleccione **Solución de problemas y soporte técnico**.
4. Haga clic en **Seleccionar usuario** para seleccionar un usuario para solucionar problemas. Se mostrará el panel **Seleccionar usuarios**.
5. Seleccione un usuario escribiendo su nombre o dirección de correo electrónico. Haga clic en **Seleccionar** en la parte inferior del panel. La información de solución de problemas del usuario se muestra en el panel de **solución de problemas**. 
6. Seleccione el dispositivo del que desea solucionar problemas en la lista **Dispositivos**.
    ![El panel de solución de problemas de Intune.](./media/troubleshoot-app-install/troubleshoot-app-install-01.png)
7. Seleccione **Aplicaciones administradas** en el panel de dispositivo seleccionado. Se muestra una lista de aplicaciones administradas.
    ![Detalles de un dispositivo específico administrado por Intune.](./media/troubleshoot-app-install/troubleshoot-app-install-02.png)
8. Seleccione una aplicación en la lista donde **Estado de la instalación** indica un error.
    ![Una aplicación seleccionada que muestra detalles del error de instalación.](./media/troubleshoot-app-install/troubleshoot-app-install-03.png)

    > [!Note]  
    > La misma aplicación podría asignarse a varios grupos, pero con diferentes acciones previstas (intenciones) para la aplicación. Por ejemplo, una intención resuelta para una aplicación se mostrará como **excluida** si la aplicación se excluye para un usuario durante la asignación de aplicaciones. Para obtener más información, consulte [Cómo se resuelven los conflictos entre las intenciones de aplicación](apps-deploy.md#how-conflicts-between-app-intents-are-resolved).<br><br>
    > Si se produce un error de instalación para una aplicación requerida, usted o su departamento de soporte técnico podrán sincronizar el dispositivo y volver a intentar instalar la aplicación.

Los detalles del error de instalación de la aplicación indicarán el problema. Puede usar estos detalles para determinar cuál es la mejor acción para resolver el problema. Para obtener más información sobre cómo solucionar problemas de instalación de aplicaciones, vea [Errores de instalación de aplicaciones Android](app-install-error-codes.md#android-app-installation-errors) y [Errores de instalación de aplicaciones iOS](app-install-error-codes.md#ios-app-installation-errors).

> [!Note]  
> También puede acceder al panel de **solución de problemas** visitando la página [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting) desde el explorador.

## <a name="user-group-targeted-app-installation-does-not-reach-device"></a>La instalación de la aplicación de destino del grupo de usuarios no llega al dispositivo
Si se tienen problemas para instalar aplicaciones, se deben tener en cuenta las siguientes acciones:
- Si la aplicación no aparece en Portal de empresa, asegúrese de que se ha implementado con la intención **Disponible** y de que el usuario accede a Portal de empresa con el tipo de dispositivo admitido por la aplicación.
- En el caso de los dispositivos BYOD de Windows, el usuario debe agregar una cuenta profesional al dispositivo.
- Compruebe si el usuario está por encima del límite de dispositivos de AAD:
  1. Vaya a [Configuración de dispositivos de Azure Active Directory](https://portal.azure.com/#pane/Microsoft_AAD_IAM/DevicesMenupane/DeviceSettings/menuId).
  2. Anote el valor establecido en **Máximo de dispositivos por usuario**.
  3. Vaya a [Usuarios de Azure Active Directory](https://portal.azure.com/#pane/Microsoft_AAD_IAM/UsersManagementMenupane/AllUsers).
  4. Seleccione el usuario afectado y haga clic en **Dispositivos**.
  5. Si el usuario supera el límite establecido, elimine los registros obsoletos que ya no sean necesarios.
- En el caso de los dispositivos DEP de iOS, asegúrese de que el usuario aparece como **Inscritos por el usuario** en el panel Información general del dispositivo de Intune. Si muestra NA, implemente una directiva de configuración para Portal de empresa de Intune. Para obtener más información, vea [Configuración de la aplicación Portal de empresa](app-configuration-policies-use-ios.md#configure-the-company-portal-app-to-support-ios-dep-devices).

## <a name="win32-app-installation-troubleshooting"></a>Solución de problemas de instalación de aplicaciones Win32

Seleccione la aplicación Win32 que se implementó mediante la extensión de administración de Intune. Puede seleccionar la opción **Recopilar registros** cuando se produce un error de instalación de la aplicación Win32. 

> [!IMPORTANT]
> La opción **Recopilar registros** no se habilitará cuando la aplicación Win32 se haya instalado correctamente en el dispositivo.<p>Para poder recopilar información de registro de la aplicación Win32, debe instalarse la extensión de administración de Intune en el cliente de Windows. La extensión de administración de Intune se instala cuando se implementa un script de PowerShell o una aplicación Win32 en un grupo de seguridad de dispositivos o usuarios. Para más información, vea [Requisitos previos de la extensión de administración de Intune](intune-management-extension.md#prerequisites).

### <a name="collect-log-file"></a>Recopilar archivos de registro

Para recopilar los registros de instalación de la aplicación Win32, primero siga los pasos indicados en la sección [Detalles de solución de problemas de la aplicación](troubleshoot-app-install.md#app-troubleshooting-details). Después, siga con estos pasos:

1. Haga clic en la opción **Recopilar registros**, en el panel **Detalles de la instalación**.

    <image alt="Win32 app installation details - Collect log option" src="./media/troubleshoot-app-install/troubleshoot-app-install-04.png" width="500" />

2. Proporcione rutas de acceso de archivo con nombres de archivo de registro para iniciar el proceso de recopilación de archivos de registro y haga clic en **Aceptar**.

    > [!NOTE]
    > La recopilación de registros tardará menos de dos horas. Tipos de archivo admitidos: *.log, .txt, .dmp, .cab, .zip, .xml, .evtx y .evtl*. Se permite un máximo de 25 rutas de acceso de archivo.

3. Una vez que se han recopilado los archivos de registro, puede seleccionar el vínculo **Registros** para descargarlos.

    <image alt="Win32 app log details - Download logs" src="./media/troubleshoot-app-install/troubleshoot-app-install-05.png" width="500" />

    > [!NOTE]
    > Se mostrará una notificación que indica que la recopilación de registros de la aplicación se ha realizado correctamente.

#### <a name="win32-log-collection-requirements"></a>Requisitos de recopilación de registros de Win32

Para recopilar archivos de registro, es necesario seguir unos requisitos específicos:

- Debe especificar la ruta completa del archivo de registro. 
- Puede especificar variables de entorno para la recopilación de registros, como las siguientes:<br>
  *%PROGRAMFILES%, %PROGRAMDATA% %PUBLIC%, %WINDIR%, %TEMP%, %TMP%*
- Solo se permiten extensiones de archivo exactas, como:<br>
  *.log, .txt, .dmp, .cab, .zip, .xml*
- Se puede cargar un máximo de 25 archivos de registro o de 60 MB, lo que ocurra primero. 
- La recopilación de registros de instalación de la aplicación Win32 está habilitada para las aplicaciones que cumplen la intención de asignación de aplicación necesaria, disponible y de instalación.
- Los registros almacenados se cifran para proteger cualquier información de identificación personal incluida en los registros.
- Si se produce un error al abrir incidencias de soporte técnico para aplicaciones Win32, adjunte los registros de error relacionados siguiendo los pasos arriba indicados.

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>Solucionar problemas de aplicaciones de la Microsoft Store

La información contenida en el tema [Troubleshooting packaging, deployment, and query of Microsoft Store apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) (Solucionar problemas de empaquetado, implementación y consulta de aplicaciones de la Microsoft Store) le ayuda a solucionar problemas comunes que pueden surgir al instalar aplicaciones desde la Microsoft Store, tanto si usa Intune como otros medios.

## <a name="app-troubleshooting-resources"></a>Recursos de solución de problemas de aplicaciones
- [Implementación de Visio y Project como parte de la implementación de Office Pro Plus](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Deploying-Visio-and-Project-as-part-of-your-Office/ba-p/701795)
- [Medidas para garantizar que las aplicaciones de MSfB implementadas mediante Intune se instalan en Windows 10 1903](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Take-Action-to-Ensure-MSfB-Apps-deployed-through/ba-p/658864)
- [Solución de problemas de implementaciones de aplicaciones MSI en Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-MSI-App-deployments-in-Microsoft/ba-p/359125)
- [Procedimientos recomendados para la distribución de software al agente de PC de Windows clásico de Intune](https://support.microsoft.com/en-us/help/2583929/best-practices-for-intune-software-distribution-to-windows-pc)

## <a name="next-steps"></a>Pasos siguientes

- Para obtener información adicional sobre la solución de problemas de Intune, consulte [Uso del portal de solución de problemas para ayudar a los usuarios de su empresa](../fundamentals/help-desk-operators.md). 
- Obtenga información sobre los problemas conocidos de Microsoft Intune. Para obtener más información, vea [Éxito de clientes de Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess).
- ¿Necesita más ayuda? Consulte [Cómo obtener asistencia para Microsoft Intune](../fundamentals/get-support.md).
