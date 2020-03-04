---
title: Asignación de aplicaciones de Google Play administrado a dispositivos Android Enterprise
titleSuffix: Microsoft Intune
description: Descubra cómo sincronizar y asignar aplicaciones a dispositivos Android Enterprise desde Google Play Store administrado.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 126ea5a1798252f29e988553edfea462eff2fd7e
ms.sourcegitcommit: a25f556aa9df4fcd9fdacccd12c9029bc6c5fe20
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/03/2020
ms.locfileid: "78256465"
---
# <a name="add-managed-google-play-apps-to-android-enterprise-devices-with-intune"></a>Adición de aplicaciones de Google Play administrado a dispositivos Android Enterprise con Intune

Google Play administrado es la tienda de aplicaciones empresariales de Google y el único origen de aplicaciones para Android Enterprise. Puede usar Intune para orquestar la implementación de la aplicación mediante Google Play administrado para cualquier escenario de Android Enterprise (incluido el perfil de trabajo y las inscripciones dedicadas y completamente administradas). La forma de agregar aplicaciones de Google Play administrado a Intune es diferente de cómo se agregan las aplicaciones Android a un dispositivo que no es Android Enterprise. Las aplicaciones de la tienda, las de línea de negocio (LOB) y las aplicaciones web se aprueban o se agregan a Google Play administrado y después se sincronizan en Intune para que aparezcan en la lista de aplicaciones cliente. Cuando aparecen en la lista de aplicaciones de cliente, puede administrar la asignación de cualquier aplicación de Google Play administrado como lo haría con cualquier otra aplicación.

Para facilitarle la configuración y el uso de la administración de Android Enterprise, tras conectarse el inquilino de Intune a Google Play administrado, Intune agregará automáticamente cuatro aplicaciones comunes relacionadas con Android Enterprise a la consola de administración de Intune. Las cuatro aplicaciones son las siguientes:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** : se usa para escenarios totalmente administrados de Android Enterprise. Esta aplicación se instala automáticamente en los dispositivos totalmente administrados durante su proceso de inscripción.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** : ayuda a iniciar sesión en las cuentas si se usa la verificación de dos fases. Esta aplicación se instala automáticamente en los dispositivos totalmente administrados durante su proceso de inscripción.
- **[Portal de empresa de Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** : se usa para las directivas de protección de aplicación y escenarios de perfil de trabajo de Android Enterprise.
- **[Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise)** : se usa en los escenarios de pantalla completa o de varias aplicaciones dedicados de Android Enterprise. Los administradores de TI deben crear una asignación para instalar esta aplicación en dispositivos dedicados que se van a usar en escenarios de pantalla completa de varias aplicaciones.

>[!NOTE]
>Cuando un usuario final inscribe su dispositivo de Android Enterprise totalmente administrado, la aplicación Portal de empresa de Intune se instala automáticamente y el icono de la aplicación puede estar visible para el usuario final. Si el usuario final intenta iniciar la aplicación Portal de empresa de Intune, se redirigirá a la aplicación Microsoft Intune y el icono de la aplicación Portal de empresa se ocultará posteriormente.

## <a name="before-you-start"></a>Antes de empezar
- Asegúrese de que ha conectado el inquilino de Intune a Google Play administrado.  Para más información, consulte [Conexión de una cuenta de Intune a una cuenta de Google Play administrado](../enrollment/connect-intune-android-enterprise.md).
- Si tiene previsto inscribir dispositivos de perfil de trabajo, asegúrese de que ha configurado Intune y perfiles de trabajo Android para que funcionen juntos en la carga de trabajo **Inscripción de dispositivo** de Azure Portal. Para obtener más información, vea [Inscripción de dispositivos Android](../enrollment/android-work-profile-enroll.md).

>[!NOTE]
>Cuando trabaja con Microsoft Intune, se recomienda usar el explorador Microsoft Edge o Google Chrome.

## <a name="managed-google-play-app-types"></a>Tipos de aplicación de Google Play administrado
Hay tres tipos de aplicaciones que están disponibles con Google Play administrado:

- **Aplicación de Google Play Store administrado**: aplicaciones públicas que están disponibles con carácter general en Play Store. Para administrar estas aplicaciones en Intune, busque las aplicaciones que quiera administrar, apruébelas y, después, sincronícelas en Intune.
- **Aplicación privada de Google Play administrado**: son aplicaciones de línea de negocio publicadas en Google Play administrado por administradores de Intune.  Estas aplicaciones son privadas y solo están disponibles para el inquilino de Intune. Así es cómo se administran e implementan las aplicaciones de línea de negocio con Google Play administrado y Android Enterprise.
- **Vínculo web de Google Play administrado**: vínculos web con iconos definidos por el administrador de TI que se pueden implementar en dispositivos Android Enterprise. Aparecen en los dispositivos de la lista de aplicaciones del dispositivo, al igual que las aplicaciones normales.

## <a name="managed-google-play-store-apps"></a>Aplicaciones de Google Play Store administrado
Hay dos maneras de examinar y aprobar las aplicaciones de Google Play Store administrado con Intune:

1. Directamente en la consola de Intune: examine y apruebe las aplicaciones de la tienda en una vista hospedada en Intune. Se abre directamente en la consola de Intune y no requiere que se vuelva a autenticar con una cuenta diferente.
1. En la consola de Google Play administrado: abra si lo desea la consola de Google Play administrado directamente y apruebe allí las aplicaciones. Consulte [Sincronización de una aplicación de Google Play administrado con Intune](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune) para más información.  Esto requiere un inicio de sesión independiente con la cuenta que usó para conectar el inquilino de Intune a Google Play administrado.

### <a name="add-a-managed-google-play-store-app-directly-in-the-intune-console"></a>Adición de una aplicación de Google Play Store administrado directamente en la consola de Intune

1. Inicie sesión en el [Centro de administración de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Aplicaciones** > **Todas las aplicaciones** > **Agregar**.
3. En el panel **Seleccionar tipo de aplicación**, en los tipos de **Aplicación de la Tienda** disponibles, seleccione la **Aplicación de Google Play administrado**.
4. Haga clic en **Seleccionar**. Se muestra la aplicación de la Tienda **Google Play administrado**.

    > [!NOTE]
    > La cuenta de inquilino de Intune debe estar conectada a su cuenta de Android Enterprise para examinar las aplicaciones de la Tienda de Google Play administrado. Para más información, consulte [Conexión de una cuenta de Intune a una cuenta de Google Play administrado](../enrollment/connect-intune-android-enterprise.md).

5. Seleccione una aplicación para ver sus detalles.
6. En la página que muestra la aplicación, haga clic en **Aprobar**. Se abre una ventana de la aplicación que le pide que conceda permisos a la aplicación para realizar diversas operaciones.
7. Seleccione **Aprobar** para aceptar los permisos de la aplicación y continuar.
8. Seleccione **Keep approved when app requests new permissions** (Mantener aprobada cuando la aplicación solicite nuevos permisos) en la pestaña **Configuración de aprobación** y haga clic en **Listo**. 

    > [!IMPORTANT]
    > Si no elige esta opción, deberá aprobar manualmente los nuevos permisos si el desarrollador de la aplicación publica una actualización. Como consecuencia, las instalaciones y actualizaciones de la aplicación se detendrán hasta que se aprueben los permisos. Por este motivo, se recomienda seleccionar la opción para aprobar automáticamente los nuevos permisos. 

9. Haga clic en **Seleccionar** para seleccionar la aplicación.
10. Haga clic en **Sincronizar** en la parte superior de la hoja para sincronizar la aplicación con el servicio de Google Play administrado.
11. Haga clic en **Actualizar** para actualizar la lista de aplicaciones y mostrar la aplicación recién agregada.

### <a name="add-a-managed-google-play-store-app-in-the-managed-google-play-console-alternative"></a>Adición de una aplicación de Google Play Store administrado en la consola de Google Play administrado (alternativa)
Si prefiere sincronizar una aplicación de Google Play administrado con Intune, en lugar de agregarla directamente mediante Intune, use los pasos siguientes.

> [!IMPORTANT]
> La información proporcionada a continuación es un método alternativo para agregar una aplicación de Google Play administrado mediante Intune, como se describió anteriormente.

1. Vaya a [Google Play Store administrado](https://play.google.com/work). Inicie sesión con la misma cuenta que usó para configurar la conexión entre Intune y Android Enterprise.
2. Busque en la tienda y seleccione la aplicación que desea asignar mediante Intune.
3. En la página que muestra la aplicación, haga clic en **Aprobar**.  
    En el ejemplo siguiente, ha elegido la aplicación Microsoft Excel.

    ![Botón Aprobar de Google Play Store administrado](./media/apps-add-android-for-work/approve.png)

   Se abre una ventana de la aplicación que le pide que conceda permisos a la aplicación para realizar diversas operaciones.

4. Seleccione **Aprobar** para aceptar los permisos de la aplicación y continuar.

    ![El botón Aprobar para permisos de aplicación](./media/apps-add-android-for-work/approve-app-permissions.png)

5. Seleccione una opción para controlar nuevas solicitudes de permisos de aplicación y luego seleccione **Guardar**.

    ![Opciones para controlar las nuevas solicitudes de permisos de aplicación](./media/apps-add-android-for-work/approve-app-settings.png)

    La aplicación se aprueba y se muestra en la consola de administración de TI. Después, puede [sincronizar la aplicación de perfil de trabajo Android con Intune](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune).

## <a name="managed-google-play-private-lob-apps"></a>Aplicaciones de línea de negocio privadas de Google Play administrado

Hay dos maneras de agregar aplicaciones de línea de negocio a Google Play administrado:

1. Directamente en la consola de Intune: esto le permite agregar aplicaciones de línea de negocio mediante el envío solo del APK de la aplicación y un título, directamente en Intune. Este método no requiere tener una cuenta de desarrollador de Google y no requiere que pague la tarifa por registrarse en Google como desarrollador.  Este método es más sencillo y tiene un número significativamente reducido de pasos y hace que las aplicaciones de línea de negocio estén disponibles para la administración en tan solo diez minutos.
1. En la consola para desarrolladores de Google Play: si tiene una cuenta de desarrollador de Google o desea configurar características de distribución avanzadas que solo están disponibles en la consola para desarrolladores de Google Play (como agregar capturas de pantallas de aplicaciones adicionales), puede usar la [consola para desarrolladores de Google Play](https://play.google.com/apps/publish). 

### <a name="managed-google-play-private-lob-app-publishing-directly-in-the-intune-console"></a>Publicación de aplicaciones privadas (LOB) de Google Play administrado directamente en la consola de Intune

1. Inicie sesión en el [Centro de administración de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Aplicaciones** > **Todas las aplicaciones** > **Agregar**.
3. En el panel **Seleccionar tipo de aplicación**, en los tipos de **Aplicación de la Tienda** disponibles, seleccione la **Aplicación de Google Play administrado**.
4. Haga clic en **Seleccionar**. Se muestra la aplicación de la Tienda **Google Play administrado** dentro de Intune.
5. Seleccione **Aplicaciones privadas** (junto al icono de *candado*) en la ventana de Google Play. 
6. Haga clic en el botón **"+"** en la esquina inferior derecha para agregar una aplicación nueva.
7. Agregue un **Título** de aplicación y haga clic en **Cargar APK** para agregar el paquete de aplicación APK.
8. Haga clic en **Crear**.
9. Cierre el panel de Google Play administrado si ha terminado de agregar aplicaciones.
10. Haga clic en **Sincronizar** en el panel **Aprobar aplicación** para realizar la sincronización con el servicio de Google Play administrado. 

    > [!NOTE]
    > Las aplicaciones privadas pueden tardar varios minutos en estar disponibles para la sincronización. Si la aplicación no aparece la primera vez que realiza una sincronización, espere un par de minutos e inicie una nueva sincronización.

Para más información sobre las aplicaciones privadas de Google Play administrado, incluidas las preguntas más frecuentes, consulte el artículo de soporte técnico de Google: https://support.google.com/googleplay/work/answer/9146439.

>[!IMPORTANT]
>Las aplicaciones privadas agregadas mediante este método nunca se pueden hacer públicas. Utilice esta opción de publicación solo si está seguro de que esta aplicación siempre será privada para la organización.

### <a name="managed-google-play-private-lob-app-publishing-using-the-google-developer-console"></a>Publicación de aplicaciones privadas (LOB) de Google Play administrado con la consola para desarrolladores de Google

1. Inicie sesión en la [consola para desarrolladores Google Play](https://play.google.com/apps/publish) con la misma cuenta que usó para configurar la conexión entre Intune y Android Enterprise.  
    Si inicia sesión por primera vez, debe registrar y pagar una cuota para participar en el programa para desarrolladores de Google.
2. En la consola, seleccione **Agregar nueva aplicación**.
3. Puede cargar y proporcionar información sobre la aplicación de la misma manera que publica cualquier aplicación en Google Play Store. Sin embargo, debe seleccionar **Solo hacer que esta aplicación esté disponible para mi organización (<*nombre de la organización*>)** .

    ![Hacer que la aplicación esté disponible solo para su organización](./media/apps-add-android-for-work/restrict.png)

    Con esta operación, la aplicación solo estará disponible para su organización, y no en Google Play Store público.

    Para más información sobre la carga y publicación de aplicaciones Android, consulte la [Ayuda de la consola para desarrolladores de Google](https://support.google.com/googleplay/android-developer/answer/113469).
4. Después de haber publicado la aplicación, inicie sesión en [Google Play Store administrado](https://play.google.com/work) con la misma cuenta que usó para configurar la conexión entre Intune y Android Enterprise.
5. En el nodo **Aplicaciones** de la tienda, compruebe que se muestra la aplicación publicada.  
    La sincronización de la aplicación con Intune se ha aprobado automáticamente.

## <a name="managed-google-play-web-links"></a>Vínculos web de Google Play administrado

Los vínculos web de Google Play administrado se pueden instalar y administrar como otras aplicaciones Android. Cuando se instala en un dispositivo, aparecerán en la lista de aplicaciones del usuario junto con las demás aplicaciones que se hayan instalado. Cuando se pulsan, se iniciarán en el explorador del dispositivo.

Los vínculos web se abrirán con Microsoft Edge o con cualquier otra aplicación del explorador que decida implementar. Asegúrese de implementar al menos una aplicación de explorador en los dispositivos para que los vínculos web puedan abrirse correctamente. Sin embargo, todas las opciones de **presentación** disponibles para vínculos web (interfaz de usuario de pantalla completa, independiente y mínima) solo funcionarán con el explorador Chrome. 

1. Inicie sesión en el [Centro de administración de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Aplicaciones** > **Todas las aplicaciones** > **Agregar**.
3. En el panel **Seleccionar tipo de aplicación**, en los tipos de **Aplicación de la Tienda** disponibles, seleccione la **Aplicación de Google Play administrado**.
4. Haga clic en **Seleccionar**. Se muestra la aplicación de la Tienda **Google Play administrado** dentro de Intune.
5. Seleccione **Aplicaciones web** (junto al icono de *globo terráqueo*) en la ventana de Google Play.
6. Haga clic en el botón **"+"** en la esquina inferior derecha para agregar una aplicación nueva.
7. Agregue un **Título** de aplicación, la dirección **URL** de la aplicación web, seleccione cómo se debe mostrar la aplicación y, luego, seleccione un icono de aplicación.
8. Haga clic en **Crear**.
9. Cierre el panel de Google Play administrado si ha terminado de agregar aplicaciones.
10. Haga clic en **Sincronizar** en el panel **Aprobar aplicación** para realizar la sincronización con el servicio de Google Play administrado. 

    > [!NOTE]
    > Las aplicaciones web pueden tardar varios minutos en estar disponibles para la sincronización. Si la aplicación no aparece la primera vez que realiza una sincronización, espere un par de minutos e inicie una nueva sincronización.

## <a name="sync-a-managed-google-play-app-with-intune"></a>Sincronizar una aplicación administrada en Google Play con Intune

Si se ha aprobado una aplicación desde la tienda y todavía no la ve en la carga de trabajo **Aplicaciones**, fuerce una sincronización inmediata como sigue:

1. Inicie sesión en el [Centro de administración de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Seleccione **Aplicaciones** > **Administración de inquilinos** > **Conectores y tokens** > **Google Play administrado**.
5. En el panel **Google Play administrado**, elija **Actualizar**.  
    En la página actualiza la hora y el estado de la última sincronización.
6. En el Centro de administración de Microsoft Endpoint Manager, seleccione **Aplicaciones** > **Todas las aplicaciones**.  
    Se muestra la aplicación Google Play administrado que se ha publicado recientemente.

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices"></a>Asignación de una aplicación de Google Play administrado para dispositivos de perfil de trabajo de Android Enterprise

Cuando la aplicación se muestre en el nodo **Licencias de aplicación** del panel de la carga de trabajo **Aplicaciones**, podrá [asignarla igual que haría con cualquier otra aplicación](/intune-azure/manage-apps/deploy-apps) asignando la aplicación a grupos de usuarios.

Después de asignar la aplicación, se instala (o está disponible para su instalación) en los dispositivos de los usuarios que ha especificado. Al usuario del dispositivo no se le pide que apruebe la instalación. Para más información sobre los dispositivos de perfil de trabajo de Android Enterprise, consulte [Configuración de la inscripción de dispositivos de perfil de trabajo de Android Enterprise](../enrollment/android-work-profile-enroll.md). 

> [!NOTE] 
> Solo se mostrarán las aplicaciones que se han asignado en el almacén de Google Play administrado para un usuario final. Por lo tanto, este es un paso fundamental para que el administrador realice la configuración de aplicaciones con Google Play administrado.

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-fully-managed-devices"></a>Asignación de una aplicación de Google Play administrado a dispositivos Android Enterprise totalmente administrados

Los [dispositivos Android Enterprise totalmente administrados](../enrollment/android-fully-managed-enroll.md) son dispositivos de propiedad corporativa que están asociados a un solo usuario y se usan exclusivamente para el trabajo y no para uso personal. Los usuarios de dispositivos totalmente administrados pueden obtener sus aplicaciones de empresa disponibles desde la aplicación de Google Play administrado en el dispositivo.

De forma predeterminada, el dispositivo Android Enterprise totalmente administrado no permitirá a los empleados instalar ninguna aplicación que no esté aprobada por la organización. Además, los empleados no podrán quitar las aplicaciones instaladas por la directiva. Si quiere permitir que los usuarios accedan a la tienda completa de Google Play Store para instalar aplicaciones en lugar de tener acceso solo a las aplicaciones aprobadas en el almacén de Google Play administrado, puede establecer el acceso de **Permitir el acceso a todas las aplicaciones en Google Play Store** en **Permitir**. Con esta configuración, el usuario puede tener acceso a todas las aplicaciones de Google Play Store con la cuenta corporativa; sin embargo, las compras pueden estar limitadas. Puede quitar la restricción de compras limitadas si permite a los usuarios agregar cuentas nuevas al dispositivo. Al hacerlo, los usuarios finales podrán comprar aplicaciones de Google Play Store mediante cuentas personales, así como realizar compras desde la aplicación. Para más información, consulte [Configuración de dispositivos Android Enterprise para permitir o restringir características mediante Intune](../configuration/device-restrictions-android-for-work.md). 

> [!NOTE]
> La aplicación Microsoft Intune y la aplicación Microsoft Authenticator se instalarán como aplicaciones requeridas en todos los dispositivos totalmente administrados durante la incorporación. Si estas aplicaciones se instalan automáticamente, se ofrece compatibilidad con el acceso condicional y Microsoft Intune los usuarios de la aplicación pueden ver y resolver problemas de cumplimiento. 

## <a name="manage-android-enterprise-app-permissions"></a>Administración de permisos de aplicaciones Android Enterprise
Android Enterprise requiere que apruebe las aplicaciones en la consola web de Google Play antes de sincronizarlas con Intune y asignarlas a los usuarios. Como Android Enterprise le permite insertar de forma silenciosa y automáticamente las aplicaciones en los dispositivos de los usuarios, debe aceptar los permisos de aplicación en nombre de todos los usuarios. Los usuarios no ven ningún permiso de aplicación cuando instalan las aplicaciones, por lo que es importante que comprenda los permisos.

Cuando un desarrollador de la aplicación actualiza los permisos con una nueva versión de la aplicación, los permisos no se aceptan automáticamente, incluso si se han aprobado los permisos anteriores. Todavía se pueden usar los dispositivos que ejecutan la versión anterior de la aplicación. Sin embargo, la aplicación no se actualiza hasta que se aprueban los nuevos permisos. Los dispositivos que no tienen instalada la aplicación no la instalan hasta que se aprueben los nuevos permisos de la aplicación. 

### <a name="update-app-permissions"></a>Actualización de los permisos de la aplicación

Visite periódicamente la consola de Google Play administrada para buscar nuevos permisos. Puede configurar Google Play para que le envíe a usted o a otros usuarios un correo electrónico cuando se requieren nuevos permisos para una aplicación aprobada. Si asigna una aplicación y observa que no está instalada en los dispositivos, compruebe si existen los nuevos permisos siguiendo estos pasos:

1. Vaya a [Google Play](https://play.google.com/work).
2. Inicie sesión con la cuenta de Google que usó para publicar y aprobar las aplicaciones.
3. Seleccione la pestaña **Actualizaciones** y compruebe si las aplicaciones requieren una actualización.  
    Las aplicaciones de la lista requieren permisos nuevos y no se asignarán hasta que se apliquen.

Como alternativa, puede configurar Google Play para que vuelva a aprobar automáticamente los permisos de las aplicaciones por cada aplicación.

## <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices"></a>Otros informes de aplicaciones de Google Play administrado para dispositivos de perfil de trabajo de Android Enterprise

En las aplicaciones de Google Play administrado implementadas en dispositivos de perfil de trabajo de Android Enterprise, puede usar Intune para ver el estado y el número de versión de la aplicación instalada en un dispositivo. 

## <a name="delete-managed-google-play-apps"></a>Eliminación de aplicaciones de Google Play administrado
Cuando sea necesario, podrá eliminar aplicaciones de Google Play administrado desde Microsoft Intune. Para eliminar una aplicación de Google Play administrado, abra Microsoft Intune en Azure Portal y seleccione **Aplicaciones** > **Todas las aplicaciones**. En la lista de aplicaciones, seleccione los puntos suspensivos (...) a la derecha de la aplicación de Google Play administrado y luego seleccione **Eliminar** en la lista que aparece. Cuando se elimina una aplicación de Google Play administrada de la lista de aplicaciones, automáticamente se desactiva la aprobación de la aplicación administrada de Google Play.

> [!NOTE]
> Si una aplicación no está aprobada o se ha eliminado de Google Play Store administrado, no se quitará de la lista de aplicaciones cliente de Intune. Esto le permite seguir dirigiendo una directiva de desinstalación a los usuarios, incluso si la aplicación no está aprobada.

## <a name="android-enterprise-system-apps"></a>Aplicaciones del sistema de Android Enterprise

Puede habilitar una aplicación del sistema de Android Enterprise para los [servicios dedicados de Android Enterprise](../enrollment/android-kiosk-enroll.md) o [dispositivos totalmente administrados](../enrollment/android-fully-managed-enroll.md). Para más información sobre cómo agregar una aplicación del sistema de Android Enterprise, consulte [Adición de aplicaciones del sistema de Android Enterprise a Microsoft Intune](apps-ae-system.md).

## <a name="next-steps"></a>Pasos siguientes

- [Asignar aplicaciones a grupos](apps-deploy.md)
