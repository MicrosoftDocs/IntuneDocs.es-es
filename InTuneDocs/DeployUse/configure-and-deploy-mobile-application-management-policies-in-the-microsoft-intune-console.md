---
title: "Configurar e implementar directivas de administración de aplicaciones móviles en la consola de Microsoft Intune | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b4fb33a8-a2fa-4353-bd89-5bda48b68e83
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f33a86c51320c75ce74d20e0cac2b9581990ecec
ms.openlocfilehash: a140a2f634397440b35786e7afb3165dccc7d93e


---

# Configure and deploy mobile application management policies in the Microsoft Intune console
Las directivas de administración de aplicaciones móviles de Microsoft Intune permiten modificar la función de las aplicaciones que se implementan para que, de este modo, estén en consonancia con las directivas de seguridad y cumplimiento de la compañía. Por ejemplo, puede limitar las operaciones de cortar, copiar y pegar dentro de una aplicación administrada, o configurar una aplicación para abrir todos los vínculos web dentro de un explorador administrado.

Compatibilidad con las directivas de administración de aplicaciones móviles:

-   Dispositivos que ejecutan Android 4 y versiones posteriores.

-   Dispositivos que ejecutan iOS 7 y versiones posteriores.

> [!TIP]
> Las directivas de administración de aplicaciones móviles admiten dispositivos que están inscritos con Intune.
>
> Si busca información sobre cómo crear directivas de administración de aplicaciones para dispositivos no administrados por Intune, vea [Protect app data using mobile app management policies with Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md) (Proteger datos de aplicación mediante directivas de administración de aplicaciones móviles con Microsoft Intune).

A diferencia de otras directivas de Intune, las directivas de administración de aplicaciones móviles no se implementan directamente. En su lugar, se asocia la directiva con la aplicación que desea restringir. Cuando la aplicación se implementa e instala en dispositivos, se aplicará la configuración especificada.

Para restringir una aplicación, esta debe incorporar el SDK para aplicaciones de Microsoft Intune. Existen tres métodos de obtención de este tipo de aplicación:

-   **Usar una aplicación administrada por directiva**: tiene integrado el SDK de la aplicación. Para agregar este tipo de aplicación, especifique un vínculo a la aplicación desde una tienda de aplicaciones como, por ejemplo, iTunes Store o Google Play. No es necesario ningún procesamiento adicional para este tipo de aplicación. Consulte la lista del tema [Aplicaciones de Microsoft que puede usar con las directivas de administración de aplicaciones móviles de Microsoft Intune](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx).

-   **Usar una aplicación "ajustada"**: las aplicaciones se vuelven a empaquetar a fin de incluir el SDK de la aplicación con la **herramienta de ajuste de aplicaciones de Microsoft Intune**. Esta herramienta se usa normalmente para procesar aplicaciones de empresa que se hayan creado internamente. No se puede usar para procesar aplicaciones que se hayan descargado desde la tienda de aplicaciones. Vea [Preparar aplicaciones iOS para la administración de aplicaciones móviles con la herramienta de ajuste de aplicaciones de Microsoft Intune](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) y [Preparar aplicaciones de Android para la administración de aplicaciones móviles con la herramienta de ajuste de aplicaciones de Microsoft Intune](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md).

- **Escribir su propia aplicación que incorpora el SDK para aplicaciones de Intune**: el SDK para aplicaciones de Intune le permite incorporar características de administración de aplicaciones en una aplicación mientras la está escribiendo. Para obtener más información, vea [Información general del SDK para aplicaciones de Intune](/intune/develop/intune-app-sdk).

Para obtener ayuda para elegir entre la herramienta de ajuste de aplicaciones y el SDK para aplicaciones de Intune, vea [Decidir cómo preparar las aplicaciones para la administración de aplicaciones móviles con Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md).

Algunas aplicaciones administradas, como la aplicación Outlook para iOS y Android admiten **identidades múltiples**. Esto significa que Intune solo aplica la configuración de administración a las cuentas corporativas o los datos de la aplicación.

Por ejemplo, mediante la aplicación de Outlook:

-   Si el usuario configura una cuenta de correo electrónico de trabajo y otra personal, Intune solo aplica la configuración de administración a la cuenta de trabajo y no administra la cuenta personal.

-   Si el dispositivo se retira o se cancela la inscripción, solo los datos corporativos de Outlook se quitan del dispositivo.

-   La cuenta de trabajo empleada debe ser la misma cuenta que se usó para inscribir el dispositivo con Intune.

> [!TIP]
> Si usa Intune con Configuration Manager, vea [Cómo controlar aplicaciones mediante directivas de administración de aplicaciones móviles en Configuration Manager](https://technet.microsoft.com/library/mt131414.aspx).

## Crear e implementar una aplicación con una directiva de administración de aplicaciones móviles

-   **Paso 1:** obtenga el vínculo a una aplicación administrada por directiva, cree una aplicación ajustada o use el SDK para aplicaciones de Intune para escribir una aplicación habilitada para MAM.

-   **Paso 2:** publique la aplicación en su espacio de almacenamiento en la nube.

-   **Paso 3:** cree una directiva de administración de aplicaciones móviles.

-   **Paso 4:** implemente la aplicación seleccionando la opción para asociar la aplicación a una directiva de administración de aplicaciones móviles.

-   **Paso 5:** supervise la implementación de la aplicación.

## **Paso 1:** obtenga el vínculo a una aplicación administrada por directiva, cree una aplicación ajustada o use el SDK para aplicaciones de Intune para escribir una aplicación habilitada para MAM.

-   **Para obtener un vínculo a una aplicación administrada por directiva en una tienda de aplicaciones**: desde la tienda de aplicaciones, busque y anote la dirección URL de la aplicación administrada por directiva que quiere implementar.

    Por ejemplo, la dirección URL de Microsoft Word para la aplicación de iPad es **https://itunes.apple.com/es/app/microsoft-word-for-ipad/id586447913?mt=8**


## **Paso 2:** publique la aplicación en su espacio de almacenamiento en la nube
Cuando se publica una aplicación administrada, los procedimientos difieren en función de si se publica una aplicación administrada por directiva o una aplicación que se procesó mediante la Microsoft Intune App Wrapping Tool para iOS.

#### Para publicar una aplicación administrada por directiva

1.  Cuando esté listo para cargar la aplicación en el espacio de almacenamiento de la nube, siga las instrucciones del tema [Add apps for mobile devices in Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md) (Agregar aplicaciones para dispositivos móviles en Microsoft Intune).

2.  En el caso de aplicaciones iOS, seleccione **Aplicación iOS administrada de la tienda de aplicaciones**en **Seleccione cómo debe ponerse a disposición de los dispositivos este software**.

    En el caso de aplicaciones Android, seleccione **Vínculo externo**.

3.  En **Especificar la dirección URL**, escriba la dirección URL a la aplicación administrada por directiva que anotó anteriormente.

Una vez finalizada la carga, verá **Sí** en **Directivas de administración de aplicaciones** en la página **Propiedades del software** de la aplicación cargada.

Una vez que haya comprobado que la aplicación se carga correctamente, continúe con el paso 3.

#### Para publicar una aplicación procesada con la herramienta de ajuste de aplicaciones de Microsoft Intune

1.  Cuando esté listo para cargar la aplicación en el espacio de almacenamiento de la nube, siga las instrucciones del tema [Add apps for mobile devices in Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md) (Agregar aplicaciones para dispositivos móviles en Microsoft Intune).

2.  Seleccione **Software Installer**en **Seleccione cómo debe ponerse a disposición de los dispositivos este software**.

3.  Seleccione **Paquete de aplicación de iOS (archivo &#42;.ipa)** en **Tipo de archivo instalador de software**.

Una vez finalizada la carga, verá **Sí** en **Directivas de administración de aplicaciones** en la página **Propiedades del software** de la aplicación cargada.

Una vez que haya comprobado que la aplicación se carga correctamente, continúe con el paso 3.

## **Paso 3:** cree una directiva de administración de aplicaciones móviles

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Directiva** &gt; **Información general** &gt; **Agregar directiva**.

2.  Configure e implemente uno de las siguientes directivas de **Software** en función del tipo de dispositivo para el que desea configurar aplicaciones:

    -   **Directiva de administración de aplicaciones móviles (Android 4 y posterior)**

    -   **Directiva de administración de aplicaciones móviles (iOS 7 y posterior)**

    Puede usar la configuración recomendada o personalizar la configuración. Para obtener más detalles, vea [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Configure las siguientes opciones según sea necesario. Las opciones pueden diferir en función del tipo de dispositivo para el que va a configurar la directiva.

|Nombre de la configuración|Detalles|
    |---------|--------------------|
    |**Nombre**|Especifique un nombre para esta directiva.|
    |**Descripción**|Si lo desea, especifique una descripción para esta directiva.|
    |**Restringir contenido web para mostrar en un explorador administrado corporativo**|Cuando se habilita esta configuración, los vínculos en la aplicación se abrirán en el explorador administrado. Debe haber implementado esta aplicación en dispositivos para que esta opción funcione.|
    |**Impedir copias de seguridad de Android** o **Impedir copias de seguridad de iTunes e iCloud**|Deshabilita la copia de seguridad de cualquier información procedente de la aplicación.|
    |**Permitir que la aplicación transfiera datos a otras aplicaciones**|Especifica las aplicaciones a las que esta aplicación puede enviar datos. Puede elegir no permitir la transferencia de datos a ninguna aplicación, permitir solo la transferencia a otras aplicaciones administradas o permitir la transferencia a cualquier aplicación. Esta configuración no controla el uso de la característica **Abrir en** en dispositivos móviles.<br /><br />Por ejemplo, cuando no se permite la transferencia de datos, restringir la transferencia de datos a servicios, como mensajería SMS, asignar imágenes a los contactos y exponer en Facebook o Twitter.<br /><br />En el caso de dispositivos iOS, para evitar la transferencia de documentos entre aplicaciones administradas y no administradas, también debe configurar e implementar una directiva de seguridad de dispositivos móviles que deshabilite la opción **Permitir documentos administrados en otras aplicaciones no administradas**. Si selecciona la opción para permitir solo la transferencia a otras aplicaciones administradas, se usarán los visores de PDF e imágenes de Intune (si se implementaron) para abrir el contenido de los tipos respectivos...<br /><br />Además, si establece esta opción en **Aplicaciones administradas por directivas** o **Ninguno**, la característica de iOS 9 que permite que la búsqueda de Spotlight busque datos dentro de las aplicaciones se bloqueará.|
    |**Permitir que la aplicación reciba datos de otras aplicaciones**|Especifica las aplicaciones de las que esta aplicación puede recibir datos. Puede elegir no permitir la transferencia de datos desde ninguna aplicación, permitir solo la transferencia desde otras aplicaciones administradas o permitir la transferencia desde cualquier aplicación.<br /><br />En las aplicaciones iOS que admiten varias identidades (donde Intune solo aplica la configuración de administración a las cuentas corporativas o los datos de la aplicación), en el caso de un dispositivo inscrito con una directiva de administración de aplicaciones móviles aplicada, cuando un usuario tenga acceso a los datos desde una aplicación no administrada por una directiva de administración de aplicaciones móviles, los datos se tratarán como datos corporativos y la directiva los protegerá.|
    |**Impedir "Guardar como..."**|Deshabilita el uso de la opción **Guardar como** para guardar los datos en ubicaciones de almacenamiento personales en la nube (por ejemplo, el OneDrive Personal o Dropbox) en cualquier aplicación que use esta directiva.|
    |**Restringir cortar, copiar y pegar con otras aplicaciones**|Especifica cómo pueden usarse las operaciones de cortar, copiar y pegar con la aplicación. Elija de entre las siguientes opciones:<br /><br />**Bloqueado**: no permite las operaciones de cortar, copiar y pegar entre esta aplicación y otras aplicaciones.<br /><br />**Aplicaciones administradas por directivas**: permite solo las operaciones de cortar, copiar y pegar entre esta aplicación y otras aplicaciones administradas.<br /><br />**Aplicaciones administradas por directivas con pegar**: permite que los datos cortados o copiados desde esta aplicación se peguen solo en otras aplicaciones administradas. Permitir que los datos cortados o copiados desde cualquier aplicación se peguen en esta aplicación.<br /><br />**Cualquier aplicación**: no se aplican restricciones a las operaciones de cortar, copiar y pegar en esta aplicación ni desde ella.<br /><br />Para copiar y pegar datos entre las aplicaciones administradas, ambas aplicaciones deben tener las opciones **Aplicaciones administradas por directivas** o **Aplicaciones administradas por directivas con pegar** configuradas.|
    |**Requerir PIN simple en acceso**|Requiere que el usuario escriba un número PIN que especifica al usar esta aplicación. Se pedirá al usuario que lo configure la primera vez que ejecuta la aplicación.|
    |**Número de intentos antes de restablecimiento del PIN**|Especifique el número de intentos de entrada de PIN que pueden realizarse antes de que el usuario deba restablecer el PIN.|
    |**Requerir credenciales corporativas en acceso**|Requiere que el usuario deba introducir su información de inicio de sesión corporativa para tener acceso a la aplicación.|
    |**Requerir cumplimiento de dispositivos con la directiva corporativa en acceso**|Solo permite que se use la aplicación cuando el dispositivo no está liberado ni modificado.|
    |**Volver a comprobar los requisitos de acceso después de (minutos)**|En el campo **Tiempo de espera** , especifique el período de tiempo que debe transcurrir antes de que se vuelvan a comprobar los requisitos de acceso de la aplicación una vez iniciada la aplicación.|
    |**Período de gracia sin conexión**|Si el dispositivo está desconectado, especifique el período de tiempo que debe transcurrir antes de que se vuelvan a comprobar los requisitos de acceso de la aplicación.|
    |**Cifrar datos de aplicación**|Especifica que se cifren todos los datos asociados a esta aplicación, incluidos los datos almacenados externamente como, por ejemplo, tarjetas SD.<br /><br />**Cifrado para iOS**<br /><br />En el caso de aplicaciones que están asociadas a una directiva de administración de aplicaciones móviles de Intune, los datos se cifran en reposo con el cifrado de nivel de dispositivo proporcionado por el sistema operativo. Esta opción se habilita a través de la directiva de PIN del dispositivo que debe establecer el administrador de TI. Cuando se requiere un PIN, los datos se cifrarán según la configuración de la directiva de administración de aplicaciones móviles. Como se indica en la documentación de Apple, [los módulos usados por iOS 7 están certificados mediante FIPS 140-2](http://support.apple.com/en-us/HT202739).<br /><br />**Cifrado para Android**<br /><br />En el caso de aplicaciones que están asociadas a una directiva de administración de aplicaciones móviles de Intune, Microsoft proporciona el cifrado. Los datos se cifran de forma sincrónica durante las operaciones de E/S de archivo.  Siempre se cifrará el contenido del almacenamiento del dispositivo. El método de cifrado no está certificado mediante FIPS 140-2.|
    |**Bloquear captura de pantalla** (solo en dispositivos Android)|Especifica que las funciones de captura de pantalla del dispositivo se bloquean cuando se usa esta aplicación.|

4.  Cuando termine, seleccione **Guardar directiva**.

La nueva directiva se muestra en el nodo **Directivas de configuración** del área de trabajo **Directiva** .

## **Paso 4:** asocie la aplicación a una directiva de administración de aplicaciones móviles e implemente la aplicación.
Implemente la aplicación, asegurándose de seleccionar la directiva de administración de aplicaciones móviles de la página **Administración de aplicaciones móviles** para asociar la directiva a la aplicación.

Para obtener más detalles, vea [Implementar aplicaciones en Microsoft Intune](deploy-apps.md).

> [!IMPORTANT]
> En el caso de dispositivos que ejecutan sistemas operativos anteriores a iOS 7.1, las directivas asociadas no se quitarán al desinstalar la aplicación.
>
> Si se anula la inscripción del dispositivo en Intune, no se eliminan las directivas de las aplicaciones; las aplicaciones que tenían directivas aplicadas conservarán la configuración de las directivas, aunque la aplicación se desinstale y reinstale.

### Qué hacer cuando ya se ha implementado una aplicación en dispositivos
Puede haber situaciones en que implemente una aplicación y uno de los usuarios o dispositivos de destino ya tenga una versión no administrada de la aplicación instalada, por ejemplo, si el usuario ha instalado Microsoft Word desde la tienda de aplicaciones.

En este caso, debe pedir al usuario que desinstale manualmente la versión no administrada para que se pueda instalar la versión administrada que se ha configurado.

En cambio, en el caso de los dispositivos que ejecutan iOS 9 y versiones posteriores, Intune pedirá automáticamente al usuario permiso para ocuparse de la administración de la aplicación existente. Si acepta, Intune administrará la aplicación y también se aplicarán las directivas de administración de aplicaciones móviles asociadas a la aplicación.

> [!TIP]
> Si el dispositivo está en modo de supervisión, Intune se ocupará de la administración de la aplicación existente sin pedir permiso a los usuarios.

## **Paso 5:** supervise la implementación de la aplicación.
Cuando haya creado e implementado una aplicación asociada a una directiva de administración de aplicaciones móviles, use los procedimientos siguientes para supervisar la aplicación y resuelva los conflictos de directivas.

#### Para ver el estado de la implementación

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Grupos** &gt; **Información general**.

2.  Realice uno de los siguientes pasos:

    -   Elija **Todos los usuarios** y luego haga doble clic en el usuario cuyos dispositivos quiera examinar. En la página **Propiedades del usuario**, elija **Dispositivos** y luego haga doble clic en el dispositivo que quiera examinar.

    -   Elija **Todos los dispositivos** &gt; **Todos los dispositivos móviles**. En la página **Propiedades del grupo de dispositivos**, elija **Dispositivos** y luego haga doble clic en el dispositivo que quiera examinar.

3.  En la página **Propiedades del dispositivo móvil** , elija **Directiva** para ver una lista de las directivas de administración de aplicaciones móviles que se hayan implementado en el dispositivo.

4.  Seleccione la directiva de administración de aplicaciones móviles cuyo estado desea ver. Puede ver los detalles de la directiva en el panel inferior y expandir el nodo para mostrar su configuración.

5.  En la columna **Estado** de cada una de las directivas de administración de aplicaciones móviles, se mostrará **Cumple**, **Cumplimiento (pendiente)**o **Error** . Si la directiva seleccionada tiene una o más configuraciones en conflicto, se mostrará **Error** en este campo.

6.  Cuando haya identificado un conflicto, puede modificar las configuraciones de directivas en conflicto para que usen la misma configuración o implementar una sola directiva para la aplicación y el usuario.

### Cómo se resuelven los conflictos de directivas
Cuando hay un conflicto de directivas de administración de aplicaciones móviles en la primera implementación para el usuario o el dispositivo, el valor específico de la configuración en conflicto se quitará de la directiva implementada en la aplicación y la aplicación usará un valor de conflicto integrado.

Cuando hay un conflicto de directivas de administración de aplicaciones móviles en implementaciones posteriores para la aplicación o el usuario, el valor específico de la configuración en conflicto no se actualizará en la directiva de administración de aplicaciones móviles implementada para la aplicación y la aplicación usará el valor existente para dicha configuración.

En casos en los que el dispositivo o el usuario recibe dos directivas en conflicto, se aplica el comportamiento siguiente:

-   Si ya se implementó una directiva para el dispositivo, la configuración de directiva existente no se sobrescribe.

-   Si todavía no se implementó ninguna directiva para el dispositivo y se implementan dos configuraciones en conflicto, se usa la configuración predeterminada integrada en el dispositivo.



<!--HONumber=Jun16_HO4-->


