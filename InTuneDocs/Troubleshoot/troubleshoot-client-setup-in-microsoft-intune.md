---
title: "Solucionar los problemas de configuración del cliente | Microsoft Docs"
description: "Solucione los problemas comunes de configuración de cliente."
keywords: 
author: staciebarker
ms.author: staciebarker
manager: angrobe
ms.date: 08/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e46d292b-1d16-46db-a87f-d53eefa4d22a
ms.reviewer: tscott
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 2d5c7d4800e1140efb502c47151ea8cc87548acd


---

# <a name="troubleshoot-client-setup-in-microsoft-intune"></a>Solucionar los problemas de configuración del cliente en Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Use la información siguiente como ayuda para solucionar problemas comunes de configuración del cliente. Si esta información no soluciona el problema, vea [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico para Microsoft Intune) para conocer otras formas de obtener ayuda.

## <a name="client-installation-fails"></a>Error en la instalación de cliente

-   Si no se muestra ninguna alerta de implementación del software cliente para el equipo en la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), compruebe la conectividad a Internet y la configuración proxy del equipo y asegúrese de que el equipo se puede comunicar con la dirección URL del servicio [https://manage.microsoft.com](https://manage.microsoft.com/). Posteriormente vuelva a intentar la instalación del software cliente.

-   Mediante la configuración de una regla de notificación en el área de trabajo **Administración** , puede enviar un correo electrónico a los destinatarios seleccionados cuando se produzca una alerta de error de implementación del software cliente. Para más información, consulte [Recibir notificaciones mediante alertas de Microsoft Intune](/intune/deploy-use/get-notified-by-alerts).

-   Intune muestra la alerta crítica **Error de implementación del software cliente** si se produce un error en la implementación del software cliente. Esto se mostrará en las páginas **Información general del sistema** y **Alertas** de la [consola de administración de Microsoft Intune](https://manage.microsoft.com/). Aquí se indica cómo buscar alertas:

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), haga clic en **Alertas** &gt; **Información general**.

2.  En la página **Información general de alertas** puede revisar la información siguiente:

    -   Las tres primeras alertas, que se pueden ordenar por fecha, categoría o gravedad

    -   El número total de alertas activas

3.  Seleccione **Todas las alertas** para mostrar la información siguiente en la página **Alertas**. Las alertas críticas se muestran en primer lugar:

    -   **Nombre** : el nombre del tipo de alerta que generó la alerta.

    -   **Origen** : el vínculo al origen de la alerta.  Si el umbral para mostrar del tipo de alerta se configura como **Todo**, este vínculo permitirá ver un único dispositivo afectado.  Si el umbral para mostrar del tipo de alerta se configura como un valor, este vínculo permitirá ver una lista de todos los dispositivos afectados por la alerta en cuestión.

    -   **Última actualización** : indica el momento de la última modificación de la alerta. Si una alerta está cerrada, se muestra el momento en el que se cerró.

    -   **Gravedad** : indica la gravedad de la alerta

## <a name="computer-enrollment-package-doesnt-download"></a>El paquete de inscripción del equipo no se descarga
**Problema:** al intentar inscribir un equipo sucede lo siguiente:
-  El paquete de inscripción no se puede descargar.
-  Aparece el cuadro de diálogo de descarga pero se agota el tiempo de espera.

**Solución:** en el explorador que usa para la descarga asegúrese de que, durante el proceso de descarga, se permiten las descargas y pueden guardarse archivos cifrados en el disco local.

## <a name="client-installation-hangs-with-error-code-0x80040154"></a>La instalación de cliente se bloquea con el código de error 0x80040154
**Problema:**

-  La instalación de cliente durante la inscripción se bloquea.

-  No se puede inscribir el dispositivo.

-  Error 0x80040154 en WindowsUpdate.log.

Esto puede deberse a la ausencia de actualizaciones de software imprescindibles en el equipo.

**Solución:** asegúrese de que la directiva de actualización de software permite la instalación de actualizaciones imprescindibles, como se describe en [Keep Windows PCs up to date with software updates in Microsoft Intune (Mantener los equipos de Windows al día con actualizaciones de software en Microsoft Intune)](/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)


## <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>Errores relacionados con las directivas de Microsoft Intune en policyplatform.log
Para los dispositivos de Windows que no sean de MDM, los errores de directivas del archivo policyplatform.log pueden ser el resultado de opciones de configuración no predeterminadas en el Control de cuentas de usuario (UAC) de Windows en el dispositivo. Algunas opciones de configuración de UAC no predeterminadas pueden afectar a las instalaciones de cliente de Microsoft Intune y a la ejecución de directivas.

### <a name="to-resolve-uac-issues"></a>Para resolver problemas de UAC

1.  Retire el equipo, como se describe en [Retire data and devices from Microsoft Intune management (Retirar datos y dispositivos de la administración de Microsoft Intune)](/intune/deploy-use/retire-devices-from-microsoft-intune-management).

2.  Espere 20 minutos a que se quite el software de cliente.

    > [!NOTE]
    > No intente quitar el cliente desde Programas y características.

3.  En el menú Inicio, escriba **UAC** para abrir Configuración del Control de cuentas de usuario.

4.  Mueva el control deslizante de la notificación a la opción de configuración predeterminada.

## <a name="what-to-do-if-the-client-will-not-uninstall-from-the-microsoft-intune-administrator-console"></a>Qué hacer si el cliente no se desinstala de la consola de administrador de Microsoft Intune

### <a name="to-remove-the-client-software-by-using-the-microsoft-intune-command-line-tool"></a>Para quitar el software cliente mediante la herramienta de línea de comandos de Microsoft Intune

1.  Abra un símbolo del sistema en modo de administrador.

2.  Vaya a la carpeta *%programfiles%\Microsoft\OnlineManagement\Common*

3.  Ejecute el siguiente comando ``ProvisioningUtil.exe /UninstallAgents /MicrosoftIntune``

## <a name="client-installation-error-codes"></a>Códigos de error de instalación del cliente
En la siguiente tabla se describen los códigos de error que se muestran en **Alertas** si se produce un error en la instalación del software cliente. Se incluyen sugerencias para resolver el problema representado por cada código de error.

|Código de error|Posible problema|Solución recomendada|
|--------------|--------------------|------------------------|
|**0x80CF0437**|El reloj del equipo cliente no está configurado en la hora correcta.|Asegúrese de que el reloj y la zona horaria del equipo cliente se hayan configurado en la hora y la zona horaria correctas.|
|**0x80240438**, **0x80CF0438**, **0x80CF401B**|No se puede conectar con el servicio de Intune. Compruebe la configuración del proxy del cliente.|Compruebe que la configuración del proxy del equipo cliente sea compatible con Intune y que el equipo cliente tenga acceso a Internet. Para obtener más información sobre las configuraciones de proxy compatibles, consulte [Help secure Windows PCs with Endpoint Protection for Microsoft Intune (Ayudar a proteger los equipos de Windows con Endpoint Protection para Microsoft Intune)](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune).|
|**0x80CF402C**|No se puede conectar con el servicio de Intune. Compruebe la conectividad de red.|Compruebe que el equipo tiene conectividad de red. Asegúrese de que el cable de red está conectado o que la red inalámbrica está activa.|
|**0x80240438, 0x80CF0438**|La configuración del proxy en Internet Explorer y el sistema local no se ha establecido.|Compruebe la configuración del proxy del cliente y confirme que la configuración del proxy en el equipo cliente sea compatible con Intune y que el equipo cliente tiene acceso a Internet. Para obtener más información sobre las configuraciones de proxy compatibles, consulte [Help secure Windows PCs with Endpoint Protection for Microsoft Intune (Ayudar a proteger los equipos de Windows con Endpoint Protection para Microsoft Intune)](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune).|
|**0x80043001**|El paquete de inscripción no está actualizado.|Descargue e instale el paquete de software cliente actual del área de trabajo **Administración** . Para obtener instrucciones, vea el tema [Install the Windows PC client with Microsoft Intune](/intune/deploy-use/install-the-windows-pc-client-with-microsoft-intune) (Instalar el cliente de equipos de Windows con Microsoft Intune).|
|**0x80043004**|La suscripción no existe o está deshabilitada.|Compruebe que su cuenta y la suscripción a Intune todavía están activas. Para ver la configuración de la cuenta, inicie sesión con su cuenta en el [Centro de administración de Office 365](http://go.microsoft.com/fwlink/?LinkId=698854%20).|
|**0x80043002**|La cuenta está en modo de mantenimiento.|No es posible inscribir nuevos equipos cliente cuando la cuenta está en modo de mantenimiento. Para ver la configuración de la cuenta, inicie sesión con su cuenta en el [Centro de administración de Office 365](http://go.microsoft.com/fwlink/?LinkId=698854%20).|
|**0x80043003**|Se ha eliminado la cuenta.|Compruebe que su cuenta y la suscripción a Intune todavía están activas. Para ver la configuración de la cuenta, inicie sesión en la cuenta.|
|**0x80043005**|Se ha retirado el equipo cliente.|Espere unas pocas horas, quite cualquier versión anterior del software cliente del equipo y, a continuación, intente instalar de nuevo el software cliente. Para obtener instrucciones, consulte el tema anterior titulado **Qué hacer si el cliente no se desinstala de la consola de administrador de Microsoft Intune**.|
|**0x80043006**|Se alcanzó el máximo número de puestos permitido para la cuenta.|Su organización debe adquirir puestos adicionales antes de inscribir más equipos cliente en el servicio.|
|**0x80043007**|No se encontró el archivo de certificado en la misma carpeta que el programa de instalación.|Extraiga todos los archivos antes de iniciar la instalación. No cambie el nombre ni la ubicación de los archivos extraídos: todos los archivos deben existir en la misma carpeta o de lo contrario, la instalación será errónea. Para obtener más información, consulte [Install the Windows PC client with Microsoft Intune (Instalar el cliente de equipos de Windows con Microsoft Intune)](/intune/deploy-use/install-the-windows-pc-client-with-microsoft-intune).|
|**0x8024D015**, **0x00240005**, **0x80070BC2**, **0x80070BC9**, **0x80CFD015**|No se puede instalar el software porque el equipo cliente está pendiente de reiniciarse.|Reinicie el equipo y, a continuación, intente instalar de nuevo el software cliente.|
|**0x80070032**|No se encontró uno o más requisitos previos para instalar el software cliente en el equipo cliente.|Asegúrese de que las actualizaciones necesarias están instaladas en el equipo cliente y, a continuación, intente instalar de nuevo el software cliente. Para obtener más información sobre los requisitos previos para instalar el software cliente, consulte [Network infrastructure requirements for Microsoft Intune (Requisitos de infraestructura de red para Microsoft Intune)](/intune/get-started/network-infrastructure-requirements-for-microsoft-intune).|
|**0x80043008**|No se pudo iniciar el servicio Microsoft Online Management Updates.|Póngase en contacto con el servicio de soporte técnico como se describe en [How to get support for Microsoft Intune (Cómo obtener soporte técnico de Microsoft Intune)](how-to-get-support-for-microsoft-intune.md).|
|**0x80043009**|El equipo cliente ya está inscrito en el servicio.|Debe retirar el equipo cliente para poder volver a inscribirlo en el servicio. Para obtener instrucciones, consulte [Retire devices from Microsoft Intune management (Retirar dispositivos de la administración de Microsoft Intune)](/intune/deploy-use/retire-devices-from-microsoft-intune-management).|
|**0x8004300B**|No se puede ejecutar el paquete de instalación del software cliente porque no se admite la versión de Windows que se está ejecutando en el cliente.|Intune no es compatible con la versión de Windows que se está ejecutando en el equipo cliente. Para obtener una lista de sistemas operativos compatibles, consulte [Network infrastructure requirements for Microsoft Intune (Requisitos de infraestructura de red para Microsoft Intune)](/intune/get-started/network-infrastructure-requirements-for-microsoft-intune).|
|**0xAB2**|Windows Installer no pudo tener acceso al tiempo de ejecución de VBScript para una acción personalizada.|Este error está causado por una acción personalizada basada en Bibliotecas de vínculos dinámicos (DLL). Cuando solucione problemas de DLL, quizás deba usar las herramientas que se describen en [INFO: Herramientas útiles para el paquete y los problemas de implementación ](http://go.microsoft.com/fwlink/?LinkID=234255).|
|**0x8004300f**|No se puede instalar el software porque ya está instalado el cliente de System Center Configuration Manager.|Quite el cliente de Configuration Manager y, a continuación, vuelva a intentar la instalación del software cliente.|
|**0x80043010**|El software no se puede instalar porque ya está instalado el cliente de Open Mobile Alliance Device Management (OMADM).|Anule la inscripción del cliente de OMADM y vuelva a intentar instalar el software cliente.|
Si los problemas de instalación continúan, póngase en contacto con el soporte técnico como se indica en [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico para Microsoft Intune). Tenga a mano el registro de inscripción del equipo cliente (que se encuentra en %*programfiles*%\Microsoft\OnlineManagement\Logs\Enrollment.log y %*userprofile*%\AppData\Local\Microsoft\OnlineManagement\Logs\Enrollement.log) y el registro de Windows Update (%*windir*%\windowsupdate.log) para mostrarlos a los ingenieros de soporte técnico.

### <a name="next-steps"></a>Pasos siguientes
Si esta información para solucionar problemas no le ha ayudado, póngase en contacto con el servicio de soporte técnico de Microsoft como se indica en [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico de Microsoft Intune).



<!--HONumber=Dec16_HO2-->


