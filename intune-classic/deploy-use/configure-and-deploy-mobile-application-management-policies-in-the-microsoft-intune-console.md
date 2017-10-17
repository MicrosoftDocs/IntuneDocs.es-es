---
title: "Configuración de directivas de MAM en la consola de Intune"
description: "Las directivas de administración de aplicaciones móviles de Microsoft Intune permiten modificar la función de las aplicaciones que se implementan para que, de este modo, estén en consonancia con las directivas de seguridad y cumplimiento de la compañía."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 03/17/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b4fb33a8-a2fa-4353-bd89-5bda48b68e83
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 881180fec0fe4fca8b49106bcae6ea1ecd52c2eb
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2017
---
# <a name="configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console"></a>Configure and deploy mobile application management policies in the Microsoft Intune console

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Las directivas de administración de aplicaciones móviles (MAM) de Microsoft Intune permiten modificar la función de las aplicaciones que se implementan para que, de este modo, estén en consonancia con las directivas de seguridad y cumplimiento de la compañía. Por ejemplo, puede limitar las operaciones de cortar, copiar y pegar dentro de una aplicación administrada, o configurar una aplicación para abrir todos los vínculos web dentro de un explorador administrado.

Compatibilidad con las directivas de administración de aplicaciones móviles:

-   Dispositivos que ejecutan Android 4 y versiones posteriores.

-   Dispositivos que ejecutan iOS 8.0 y versiones posteriores.

> [!TIP]
> Las directivas de administración de aplicaciones móviles admiten dispositivos que están inscritos con Intune.
>
> Si busca información sobre cómo crear directivas de administración de aplicaciones para dispositivos que Intune no administra, vea [Proteger datos de aplicación mediante directivas de administración de aplicaciones móviles con Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).

A diferencia de otras directivas de Intune, las directivas de administración de aplicaciones móviles no se implementan directamente. En su lugar, se asocia la directiva con la aplicación que desea restringir. Cuando la aplicación se implementa e instala en dispositivos, se aplicará la configuración especificada.

Para restringir una aplicación, esta debe incorporar el SDK para aplicaciones de Microsoft Intune. Existen tres métodos de obtención de este tipo de aplicación:

-   **Usar una aplicación administrada por directiva**. Una aplicación administrada por directiva tiene integrado el SDK de la aplicación. Para agregar este tipo de aplicación, especifique un vínculo a la aplicación desde una tienda de aplicaciones como, por ejemplo, iTunes Store o Google Play. No es necesario ningún procesamiento adicional para este tipo de aplicación. Para obtener más información, vea la [lista de aplicaciones que puede usar con las directivas de administración de aplicaciones móviles de Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

-   **Usar una aplicación ajustada**. Una aplicación ajustada es una aplicación que se vuelve a empaquetar para incluir el SDK de la aplicación con la herramienta de ajuste de aplicaciones de Microsoft Intune. Esta herramienta se usa normalmente para procesar aplicaciones de empresa que se hayan creado internamente. No se puede usar para procesar aplicaciones que se hayan descargado desde la tienda de aplicaciones. Para obtener más información, vea [Preparar aplicaciones iOS para la administración de aplicaciones móviles con la herramienta de ajuste de aplicaciones de Microsoft Intune](/intune/app-wrapper-prepare-ios) y [Preparar aplicaciones de Android para la administración de aplicaciones móviles con la herramienta de ajuste de aplicaciones de Microsoft Intune](/intune/app-wrapper-prepare-android).

- **Escribir su propia aplicación que incorpora el SDK para aplicaciones de Intune**. El SDK para aplicaciones de Intune le permite incorporar características de administración de aplicaciones en una aplicación mientras la está escribiendo. Para obtener más información, vea [Información general del SDK para aplicaciones de Intune](/intune/app-sdk).
/intune/apps-prepare-mobile-application-management Para obtener ayuda para elegir entre la herramienta de ajuste de aplicaciones y el SDK para aplicaciones de Intune, consulte [Decidir cómo preparar las aplicaciones para la administración de aplicaciones móviles con Microsoft Intune](/intune/apps-prepare-mobile-application-management).

Algunas aplicaciones administradas, como la aplicación Outlook para iOS y Android admiten *identidades múltiples*. Esto significa que Intune solo aplica la configuración de administración a las cuentas corporativas o los datos de la aplicación.

Por ejemplo, mediante la aplicación de Outlook:

-   Si el usuario configura una cuenta de correo electrónico de trabajo y otra personal, Intune solo aplica la configuración de administración a la cuenta de trabajo y no administra la cuenta personal.

-   Si el dispositivo se retira o se cancela la inscripción, solo los datos corporativos de Outlook se quitan del dispositivo.

-   La cuenta de trabajo debe ser la misma cuenta que se usó para inscribir el dispositivo con Intune.

> [!TIP]
> Si usa Intune con Configuration Manager, vea [Cómo controlar aplicaciones mediante directivas de administración de aplicaciones móviles en Configuration Manager](https://technet.microsoft.com/library/mt131414.aspx).

## <a name="create-and-deploy-an-app-with-a-mobile-application-management-policy"></a>Crear e implementar una aplicación con una directiva de administración de aplicaciones móviles

-   **Paso 1:** obtenga el vínculo a una aplicación administrada por directiva, cree una aplicación ajustada o use el SDK para aplicaciones de Intune para escribir una aplicación habilitada para MAM.

-   **Paso 2:** publique la aplicación en su espacio de almacenamiento en la nube.

-   **Paso 3:** cree una directiva de administración de aplicaciones móviles.

-   **Paso 4:** Asocie la aplicación a una directiva de administración de aplicaciones móviles e implemente la aplicación.

-   **Paso 5:** supervise la implementación de la aplicación.

## <a name="step-1-get-the-link-to-a-policy-managed-app-create-a-wrapped-app-or-use-the-intune-app-sdk-to-write-a-mam-enabled-app"></a>Paso 1: Obtenga el vínculo a una aplicación administrada por directiva, cree una aplicación ajustada o use el SDK para aplicaciones de Intune para escribir una aplicación habilitada para MAM

Desde la tienda de aplicaciones, busque y anote la dirección URL de la aplicación administrada por directiva que quiere implementar. Por ejemplo, la dirección URL de Microsoft Word para la aplicación de iPad es **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**.


## <a name="step-2-publish-the-app-to-your-cloud-storage-space"></a>Paso 2: Publique la aplicación en su espacio de almacenamiento en la nube
Cuando se publica una aplicación administrada, los procedimientos difieren en función de si se publica una aplicación administrada por directiva o una aplicación que se procesó mediante la Microsoft Intune App Wrapping Tool para iOS.

#### <a name="to-publish-a-policy-managed-app"></a>Para publicar una aplicación administrada por directiva

1.  Cuando esté listo para cargar la aplicación en el espacio de almacenamiento de la nube, siga las instrucciones del tema [Add apps for mobile devices in Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md) (Agregar aplicaciones para dispositivos móviles en Microsoft Intune).

2.  En el caso de aplicaciones iOS, seleccione **Aplicación iOS administrada de la tienda de aplicaciones**en **Seleccione cómo debe ponerse a disposición de los dispositivos este software**.

    En el caso de aplicaciones Android, seleccione **Vínculo externo**.

3.  En **Especificar la dirección URL**, escriba la dirección URL a la aplicación administrada por directiva que anotó anteriormente.

Una vez finalizada la carga, verá **Sí** en **Directivas de administración de aplicaciones** en la página **Propiedades del software** de la aplicación cargada.

Una vez que haya comprobado que la aplicación se carga correctamente, continúe con el paso 3.

#### <a name="to-publish-an-app-that-was-processed-through-the-microsoft-intune-app-wrapping-tool"></a>Para publicar una aplicación procesada con la herramienta de ajuste de aplicaciones de Microsoft Intune

1.  Cuando esté listo para cargar la aplicación en el espacio de almacenamiento de la nube, siga las instrucciones del tema [Add apps for mobile devices in Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md) (Agregar aplicaciones para dispositivos móviles en Microsoft Intune).

2.  Seleccione **Software Installer**en **Seleccione cómo debe ponerse a disposición de los dispositivos este software**.

3.  Seleccione **Paquete de aplicación de iOS (archivo &#42;.ipa)** en **Tipo de archivo instalador de software**.

Una vez finalizada la carga, verá **Sí** en **Directivas de administración de aplicaciones** en la página **Propiedades del software** de la aplicación cargada.

Una vez que haya comprobado que la aplicación se carga correctamente, continúe con el paso 3.

## <a name="step-3-create-a-mobile-application-management-policy"></a>Paso 3: cree una directiva de administración de aplicaciones móviles

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Directiva** &gt; **Información general** &gt; **Agregar directiva**.

2.  Configure e implemente uno de las siguientes directivas de **Software** en función del tipo de dispositivo para el que desea configurar aplicaciones:

    -   **Directiva de administración de aplicaciones móviles (Android 4 y posterior)**

    -   **Directiva de administración de aplicaciones móviles (iOS 8.0 y versiones posteriores)**

    Puede usar la configuración recomendada o personalizar la configuración. Para obtener más detalles, vea [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Configure las siguientes opciones según sea necesario. Las opciones pueden diferir en función del tipo de dispositivo para el que va a configurar la directiva.

|Nombre de la configuración|Detalles|
    |---------|--------------------|
    |**Nombre**|Especifique un nombre para esta directiva.|
    |**Descripción**|Si lo desea, especifique una descripción para esta directiva.|
    |**Restringir contenido web para mostrar en un explorador administrado corporativo**|Cuando se habilita esta configuración, los vínculos en la aplicación se abrirán en el explorador administrado. Para que esta opción funcione, debe haber implementado esta aplicación en dispositivos.|
    |**Impedir copias de seguridad de Android** o **Impedir copias de seguridad de iTunes e iCloud**|Esta configuración deshabilita la copia de seguridad de cualquier información procedente de la aplicación.|
    |**Permitir que la aplicación transfiera datos a otras aplicaciones**|Esta configuración especifica las aplicaciones a las que esta aplicación puede enviar datos. Puede elegir no permitir la transferencia de datos a ninguna aplicación, permitir solo la transferencia a otras aplicaciones administradas o permitir la transferencia a cualquier aplicación. <br /><br />Por ejemplo, cuando no se permite la transferencia de datos, restringir la transferencia de datos a servicios, como mensajería SMS, asignar imágenes a los contactos y exponer en Facebook o Twitter.<br /><br />Para dispositivos iOS, para evitar la transferencia de documentos entre aplicaciones administradas y no administradas, debe también configurar e implementar una directiva de seguridad de dispositivos móviles que deshabilite la configuración **Permitir documentos administrados en otras aplicaciones no administradas**. Si elige permitir solo la transferencia a otras aplicaciones administradas, se usarán los visores Image Viewer y PDF Viewer de Intune (si se implementaron) para abrir el contenido de los tipos respectivos.<br /><br />Además, si establece esta opción en **Aplicaciones administradas por directivas** o **Ninguno**, la característica de iOS 9 que permite que la búsqueda de Spotlight busque datos dentro de las aplicaciones se bloqueará.<br><br>Esta configuración no controla el uso de la característica Open In en dispositivos móviles. Para administrar Abrir en, vea [Administrar la transferencia de datos entre aplicaciones iOS con Microsoft Intune](manage-data-transfer-between-ios-apps-with-microsoft-intune.md).|
    |**Permitir que la aplicación reciba datos de otras aplicaciones**|Esta configuración especifica las aplicaciones de las que esta aplicación puede recibir datos. Puede elegir no permitir la transferencia de datos desde ninguna aplicación, permitir solo la transferencia desde otras aplicaciones administradas o permitir la transferencia desde cualquier aplicación.<br /><br />Cuando un usuario obtiene acceso a datos desde una aplicación que no está administrada por una directiva de administración de aplicaciones móviles, los datos se tratan como datos de la empresa y se protegen mediante la directiva. Esto se aplica a aplicaciones iOS compatibles con identidad múltiple (donde Intune solo aplica la configuración de administración a las cuentas corporativas o a los datos de la aplicación). O bien, esto se aplica a un dispositivo inscrito con una directiva de administración de aplicaciones móviles aplicada.|
    |**Impedir "Guardar como..."**|Esta configuración deshabilita el uso de la opción **Guardar como** para guardar los datos en ubicaciones de almacenamiento personales en la nube (por ejemplo, el OneDrive o Dropbox) en cualquier aplicación que use esta directiva.|
    |**Restringir cortar, copiar y pegar con otras aplicaciones**|Esta configuración especifica cómo pueden usarse las operaciones de cortar, copiar y pegar con la aplicación. Elija de entre las siguientes opciones:<br /><br />**Bloqueado**. No permite las operaciones de cortar, copiar y pegar entre esta aplicación y otras aplicaciones.<br /><br />**Aplicaciones administradas por directivas**. Permite las operaciones de cortar, copiar y pegar solo entre esta aplicación y otras aplicaciones administradas.<br /><br />**Aplicaciones administradas por directivas con pegar**. Permite que los datos cortados o copiados desde esta aplicación se peguen solo en otras aplicaciones administradas. Permitir que los datos cortados o copiados desde cualquier aplicación se peguen en esta aplicación.<br /><br />**Cualquier aplicación**. No pone restricciones en cuanto a las operaciones de cortar, copiar y pegar en la aplicación o desde ella.<br /><br />Para copiar y pegar datos entre las aplicaciones administradas, ambas aplicaciones deben tener las opciones **Aplicaciones administradas por directivas** o **Aplicaciones administradas por directivas con pegar** configuradas.|
    |**Requerir PIN simple en acceso**|Esta configuración requiere que el usuario escriba un PIN que especifica al usar esta aplicación. Se pedirá al usuario que lo configure la primera vez que ejecuta la aplicación.|
    |**Número de intentos antes de restablecimiento del PIN**|Especifique el número de intentos de entrada de PIN que pueden realizarse antes de que el usuario deba restablecer el PIN.|
    |**Requerir credenciales corporativas en acceso**|Esta configuración requiere que el usuario especifique su información de inicio de sesión corporativa para tener acceso a la aplicación.|
    |**Requerir cumplimiento de dispositivos con la directiva corporativa en acceso**|Esta configuración solo permite que se use la aplicación cuando el dispositivo no está liberado ni modificado.|
    |**Volver a comprobar los requisitos de acceso después de (minutos)**|En el campo **Tiempo de espera** , especifique el período de tiempo que debe transcurrir antes de que se vuelvan a comprobar los requisitos de acceso de la aplicación una vez abierta la aplicación.|
    |**Período de gracia sin conexión**|Si el dispositivo está desconectado, especifique el período de tiempo que debe transcurrir antes de que se vuelvan a comprobar los requisitos de acceso de la aplicación.|
    |**Cifrar datos de aplicación**|Esta configuración especifica que se cifren todos los datos asociados a esta aplicación. Esto incluye datos almacenados externamente, como tarjetas SD.<br /><br />**Cifrado para iOS**<br /><br />En el caso de aplicaciones que están asociadas a una directiva de administración de aplicaciones móviles de Intune, los datos se cifran en reposo con el cifrado de nivel de dispositivo que proporciona el sistema operativo. Esta opción se habilita a través de la directiva de PIN del dispositivo que establece el administrador de TI. Cuando se requiere un PIN, los datos se cifrarán según la configuración de la directiva de administración de aplicaciones móviles. Como se indica en la documentación de Apple, [los módulos que usa iOS están certificados mediante FIPS 140-2](http://support.apple.com/HT202739).<br /><br />**Cifrado para Android**<br /><br />En el caso de aplicaciones que están asociadas a una directiva de administración de aplicaciones móviles de Intune, Microsoft proporciona el cifrado. Los datos se cifran de forma sincrónica durante las operaciones de E/S de archivo.  Siempre se cifrará el contenido del almacenamiento del dispositivo. El método de cifrado cumple con FIPS 140-2 solo para dispositivos Samsung KNOX.|
    |**Bloquear captura de pantalla** (solo en dispositivos Android)|Esta configuración especifica que las funciones de captura de pantalla del dispositivo se bloquean cuando alguien usa esta aplicación.|

4. Cuando termine, seleccione **Guardar directiva**.

La nueva directiva aparece en el nodo **Directivas de configuración** del área de trabajo **Directiva** .

## <a name="step-4-associate-the-app-with-a-mobile-application-management-policy-and-then-deploy-the-app"></a>Paso 4: Asocie la aplicación a una directiva de administración de aplicaciones móviles e implemente la aplicación
Asegúrese de seleccionar la directiva de administración de aplicaciones móviles de la página **Administración de aplicaciones móviles** del cuadro de diálogo **Administrar implementación** para asociar la directiva a la aplicación.

Para obtener más detalles, vea [Implementar aplicaciones en Microsoft Intune](deploy-apps.md).

> [!IMPORTANT]
> Si se anula la inscripción del dispositivo en Intune, las directivas no se quitan de las aplicaciones. Las aplicaciones que tenían directivas aplicadas conservarán la configuración de las directivas si la aplicación se desinstala y se vuelve a instalar.

### <a name="what-to-do-when-an-app-is-already-deployed-on-devices"></a>Qué hacer cuando ya se ha implementado una aplicación en dispositivos
Puede haber situaciones en que implemente una aplicación y uno de los usuarios o dispositivos de destino ya tenga una versión no administrada de la aplicación instalada. Por ejemplo, si el usuario ha instalado Microsoft Word desde la tienda de aplicaciones.

En este caso, debe pedir al usuario que desinstale manualmente la versión no administrada para que se pueda instalar la versión administrada que se ha configurado.

En cambio, en el caso de los dispositivos que ejecutan iOS 9 y versiones posteriores, Intune pedirá automáticamente al usuario permiso para ocuparse de la administración de la aplicación existente. Si acepta, Intune administrará la aplicación y también se aplicarán las directivas de administración de aplicaciones móviles asociadas a la aplicación.

> [!TIP]
> Si el dispositivo está en modo de supervisión, Intune se ocupará de la administración de la aplicación existente sin pedir permiso a los usuarios.

## <a name="step-5-monitor-the-app-deployment"></a>Paso 5: supervise la implementación de la aplicación
Cuando haya creado e implementado una aplicación asociada a una directiva de administración de aplicaciones móviles, use el procedimiento siguiente para supervisar la aplicación y resuelva los conflictos de directivas.

#### <a name="to-view-the-status-of-the-deployment"></a>Para ver el estado de la implementación

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Grupos** &gt; **Información general**.

2.  Realice uno de los siguientes pasos:

    -   Elija **Todos los usuarios** y luego haga doble clic en el usuario cuyo dispositivo quiera examinar. En la página **Propiedades del usuario**, elija **Dispositivos** y luego haga doble clic en el dispositivo que quiera examinar.

    -   Elija **Todos los dispositivos** &gt; **Todos los dispositivos móviles**. En la página **Propiedades del grupo de dispositivos**, elija **Dispositivos** y luego haga doble clic en el dispositivo que quiera examinar.

3.  En la página **Propiedades del dispositivo móvil** , elija **Directiva** para ver una lista de las directivas de administración de aplicaciones móviles que se hayan implementado en el dispositivo.

4.  Seleccione la directiva de administración de aplicaciones móviles cuyo estado desea ver. Puede ver los detalles de la directiva en el panel inferior y expandir el nodo para mostrar su configuración.

5.  En la columna **Estado** de cada una de las directivas de administración de aplicaciones móviles, aparecerá **Cumple**, **Cumplimiento (pendiente)**o **Error** . Si la directiva seleccionada tiene una o más configuraciones en conflicto, aparecerá **Error** en este campo.

6.  Cuando haya identificado un conflicto, puede modificar las configuraciones de directivas en conflicto para que usen la misma configuración o implementar una sola directiva para la aplicación y el usuario.

### <a name="how-policy-conflicts-are-resolved"></a>Cómo se resuelven los conflictos de directivas
Cuando hay un conflicto de directivas de administración de aplicaciones móviles en la primera implementación para el usuario o el dispositivo, el valor específico de la configuración en conflicto se quitará de la directiva implementada en la aplicación. La aplicación usará un valor de conflicto integrado.

Cuando hay un conflicto de directivas de administración de aplicaciones móviles en implementaciones posteriores para la aplicación o el usuario, el valor específico de la configuración en conflicto no se actualizará en la directiva de administración de aplicaciones móviles implementada para la aplicación. La aplicación usará el valor existente para dicha configuración.

En casos en los que el dispositivo o el usuario recibe dos directivas en conflicto, se aplica el comportamiento siguiente:

-   Si ya se implementó una directiva para el dispositivo, la configuración de directiva existente no se sobrescribe.

-   Si todavía no se implementó ninguna directiva para el dispositivo y se implementan dos configuraciones en conflicto, se usa la configuración predeterminada integrada en el dispositivo.
