---
title: Configuración de un servicio de administración de gastos de telecomunicaciones en Microsoft Intune | Microsoft Docs
titleSuffix: ''
description: Integre Microsoft Intune con el servicio de administración de gastos de telecomunicaciones Saaswedo para supervisar el uso de datos y establecer umbrales o límites sobre dispositivos Android y iOS.
keywords: Saaswedo
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: sumitp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a3e459e4e22c7985e2e68e624c413ce967e1a8ba
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723858"
---
# <a name="set-up-a-telecom-expense-management-service-in-intune"></a>Configuración de un servicio de administración de gastos de telecomunicaciones en Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Con Intune, puede administrar gastos de telecomunicaciones a partir del uso de datos en dispositivos móviles propiedad de la organización. Intune se integra con el servicio de [administración de gastos de telecomunicaciones Datalert](http://datalert.biz/get-started) de Saaswedo. Datalert es una solución de administración de gastos de telecomunicaciones en tiempo real que le permite administrar el uso de datos de telecomunicaciones. Puede ayudarle a evitar costosos e inesperados cargos por datos e itinerancia en sus dispositivos administrados por Intune.

La integración con Datalert le permite establecer, supervisar y aplicar límites sobre el uso de datos nacionales y de itinerancia. Cuando los límites superan los umbrales definidos, se desencadenan alertas automáticamente. También se puede configurar el servicio para que aplique diferentes acciones, como deshabilitar la itinerancia o superar el umbral, a personas o grupos. La consola de administración Datalert incluye informes que muestran información sobre la supervisión y el uso de datos.

La siguiente imagen muestra cómo se integra Intune con Datalert:

  ![Diagrama de integración de Intune y Datalert](./media/telecom-expenses-monitor/tem-datalert-intune-solution-diagram.png)

Para utilizar el servicio Datalert con Intune, hay algunas opciones de configuración en Datalert e Intune. En este artículo se muestra cómo:

- Configurar las opciones de la consola de Datalert para conectar el servicio Datalert a Intune.
- Confirmar que esta conexión está activa y habilitada en Intune.
- Usar Intune para agregar la aplicación Datalert a los dispositivos.
- Desactivar el servicio Datalert e Intune (opcional).

## <a name="supported-platforms"></a>Plataformas compatibles

- Dispositivos Android 4.4 y de versiones posteriores que sean compatibles con Knox (Samsung)

  [Versiones de Android que admiten Knox](https://seap.samsung.com/faq/what-versions-android-support-knox-standard-and-knox-premium-sdks-0) (se abre el sitio web de Samsung) indica las versiones compatibles de Knox.

- iOS 8.0 y versiones posteriores

## <a name="prerequisites"></a>Requisitos previos

- Una suscripción a Microsoft Intune y acceso a [Azure Portal](https://portal.azure.com)
- Una suscripción a [Datalert](http://www.datalert.biz/) (se abre el sitio web de Datalert)

## <a name="telecom-expense-management-providers"></a>Proveedores de administración de gastos de telecomunicaciones

Intune se integra con los siguientes proveedores de administración de gastos de telecomunicaciones:

- [Servicio de administración de gastos de telecomunicaciones Datalert de Saaswedo](http://www.datalert.biz/) (se abre el sitio web de Datalert)

## <a name="deploy-the-intune-and-datalert-solution"></a>Implementación de la solución integrada de Intune y Datalert

### <a name="step-1-connect-the-datalert-service-to-intune"></a>Paso 1: Conectar el servicio Datalert a Intune

1. Inicie sesión en la consola de administración de Datalert con sus credenciales de administrador.

2. En la consola, vaya a la pestaña **Configuración** > **Configuración de MDM**.

3. Seleccione **Desbloquear**. **Desbloquear** permite cambiar o actualizar la configuración de la página.

4. En **Intune / Datalert Connection** (Conexión de Intune/Datalert) > **Server MDM** (MDM del servidor), seleccione **Microsoft Intune**.

5. Como **Dominio de Azure AD**, escriba su identificador de inquilino de Azure. Seleccione **Conexión**.

    Al seleccionar **Conexión**, el servicio Datalert se registra en Intune. Confirma que no hay ninguna conexión Datalert existente. Después de unos momentos, aparece una página de inicio de sesión de Microsoft, seguida de la autenticación Azure para Datalert.

6. En la página de autenticación de Microsoft, seleccione **Aceptar**.

    Se le redirigirá a una página de **agradecimiento** de Datalert que se cierra transcurridos unos minutos. Datalert valida la conexión y muestra marcas de verificación verdes junto a los elementos que se han validado. Si se produce un error en la validación, verá un mensaje en rojo. Póngase en contacto con el soporte técnico de Datalert para solicitar ayuda.

    En la imagen siguiente se muestran las marcas de verificación verdes cuando la conexión se realiza correctamente:

      ![Página de Datalert en la que se muestra una conexión correcta](./media/telecom-expenses-monitor/tem-datalert-connection.png)

7. En **Datalert App / ADAL Consent** (Aplicación Datalert/Consentimiento ADAL), establezca el conmutador en **Activo**. En la página de autenticación de Microsoft, seleccione **Aceptar**.

    Se le redirigirá a una página de **agradecimiento** de Datalert que se cierra transcurridos unos minutos. Datalert valida la conexión y muestra marcas de verificación verdes junto a los elementos que se han validado. Si se produce un error en la validación, verá un mensaje en rojo. Póngase en contacto con el soporte técnico de Datalert para solicitar ayuda.

    En la imagen siguiente se muestran las marcas de verificación verdes cuando la conexión se realiza correctamente:

      ![Página de Datalert en la que se muestra una conexión correcta](./media/telecom-expenses-monitor/tem-datalert-adal-consent.png)

8. En la **administración de perfiles de MDM (opcional)** , establezca el modificador en **Activo**. Esta configuración permite a Datalert leer los perfiles disponibles en Intune para ayudarle a configurar las directivas. 

    En la página de autenticación de Microsoft, seleccione **Aceptar**.

    Se le redirigirá a una página de **agradecimiento** de Datalert que se cierra transcurridos unos minutos. Datalert valida la conexión y muestra marcas de verificación verdes junto a los elementos que se han validado. Si se produce un error en la validación, verá un mensaje en rojo. Póngase en contacto con el soporte técnico de Datalert para solicitar ayuda.

    En la imagen siguiente se muestran las marcas de verificación verdes cuando la conexión se realiza correctamente:

   ![Página de Datalert en la que se muestra una conexión correcta](./media/telecom-expenses-monitor/tem-datalert-mdm-profiles.png)

### <a name="step-2-confirm-telecom-expense-management-is-active-in-intune"></a>Paso 2: Confirmar que la administración de gastos de telecomunicaciones está activa en Intune

Después de completar el paso 1, la conexión se habilita automáticamente. En Intune, el estado de la conexión muestra **Activo**. Para confirmar que el estado es activo, siga estos pasos:

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

2. Seleccione **Configuración de dispositivo** > **Administración de gastos de telecomunicaciones**. Busque el estado de conexión **Activo**:

   ![Página de Intune en la que se muestra el estado de conexión Activo de Datalert](./media/telecom-expenses-monitor/tem-azure-portal-enable-service.png)

### <a name="step-3-deploy-the-datalert-app-to-devices"></a>Paso 3: Implementación de la aplicación Datalert en dispositivos

Para confirmar que solo se recopila el uso de datos de líneas propiedad de la organización, asegúrese de:

- Crear categorías de dispositivos en Intune.
- Dirigir la aplicación Datalert solo a teléfonos de la organización.

En esta sección se indican estos pasos.

#### <a name="create-device-categories-and-device-groups-mapped-to-your-categories"></a>Creación de categorías de dispositivos y grupos de dispositivos asignados a las categorías

En función de las necesidades de su organización, cree al menos dos categorías de dispositivos (tales como Organización y Personal). Después, cree grupos de dispositivos dinámicos para cada categoría. Puede crear más categorías para su organización, según resulte necesario.

Para crear categorías de dispositivos en Intune, consulte el artículo sobre [asignación de dispositivos a grupos](../enrollment/device-group-mapping.md).

Estas categorías se muestran a los usuarios durante la inscripción (artículo sobre [inscripción de dispositivos Android](../enrollment/android-enroll.md)). Dependiendo de la categoría que los usuarios elijan, el dispositivo inscrito se trasladará al grupo de dispositivos correspondiente.

  ![Captura de pantalla del panel Agregar directiva](./media/telecom-expenses-monitor/tem-dynamic-membership-rules.png)

#### <a name="add-the-datalert-app-to-intune"></a>Incorporación de la aplicación Datalert a Intune

En los pasos siguientes se agrega la aplicación Datalert. Por ejemplo, se usa iOS. Los artículos sobre la [incorporación de aplicaciones](../apps/apps-add.md) y el [uso de etiquetas de ámbito](../fundamentals/scope-tags.md) tienen información más específica sobre estos pasos.

1. En **[Intune](https://go.microsoft.com/fwlink/?linkid=2090973)** , seleccione **Aplicaciones cliente** > **Aplicaciones** > **Agregar**.

2. Seleccione el **tipo de aplicación**. Por ejemplo, para iOS, seleccione **Store app - iOS** (Aplicación de la tienda: iOS).

3. En **Buscar en App Store**, escriba **Datalert** para encontrar la aplicación Datalert.

4. Elija la aplicación **Datalert** > **Seleccionar**:

   ![Incorporación de la aplicación Datalert desde App Store a las aplicaciones cliente de Intune](./media/telecom-expenses-monitor/tem-select-app-from-apple-app-store.png)

5. Escriba las propiedades adicionales, como información de la aplicación y etiquetas de ámbito:

   ![Escriba las propiedades de la aplicación, incluido el nombre y la descripción, elija el sistema operativo y otras opciones de configuración para la aplicación en Intune.](./media/telecom-expenses-monitor/tem-steps-to-create-the-app.png)

6. Seleccione **Aceptar** > **Agregar** para guardar los cambios. La aplicación Datalert se muestra en la lista.

#### <a name="assign-the-datalert-app-to-the-corporate-device-group"></a>Asignar la aplicación Datalert al grupo de dispositivos empresariales

1. En **Aplicaciones cliente: aplicaciones**, seleccione la aplicación Datalert que agregó en el paso anterior.

2. Seleccione **Asignaciones** > **Agregar grupo**. Elija cómo se asigna la aplicación. El artículo sobre [asignación de aplicaciones a grupos en Intune](../apps/apps-deploy.md) incluye más detalles sobre esta configuración.

    En estos pasos, elegirá si quiere que sea obligatorio u opcional para el grupo instalar la aplicación. En el ejemplo siguiente se muestra la instalación según sea necesario. Cuando sea necesario, los usuarios deben instalar la aplicación Datalert después de inscribir el dispositivo.

   ![Captura de pantalla del panel Agregar directiva](./media/telecom-expenses-monitor/tem-assign-datalert-app-to-device-group.png)

### <a name="step-4-add-organization-phone-lines-to-the-datalert-console"></a>Paso 4: Incorporación de líneas de teléfono de la organización a la consola de Datalert

Los servicios Intune y Datalert están ahora configurados para comunicarse entre sí. A continuación, agregue las líneas de teléfono de la organización de pago a la consola de Datalert. Y especifique umbrales y acciones para las infracciones de uso de telefonía móvil o itinerancia. Puede agregar manualmente líneas telefónicas corporativas de pago a la consola de Datalert o puede agregarlas automáticamente una vez que el dispositivo se inscribe en Intune.

Para establecer estos elementos, vaya a la página de [configuración de Datalert para Microsoft Intune](http://www.datalert.fr/microsoft-intune/intune-setup) (se abre el sitio web de Datalert). En la pestaña **Configuración**, siga los pasos que se indican en el asistente de instalación.

  ![Captura de pantalla del panel Agregar directiva](./media/telecom-expenses-monitor/tem-add-phone-lines-to-datalert-console.png)

El servicio Datalert ya está activo. Comienza a supervisar el uso de datos y a deshabilitar los datos móviles y de itinerancia en los dispositivos que superan los límites de uso configurados.

## <a name="end-user-enrollment"></a>Inscripción de usuarios finales

En cuanto a la experiencia del usuario final, los siguientes artículos pueden resultar de ayuda:

- [Inscripción del dispositivo iOS en la administración de gastos de telecomunicaciones](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-ios)
- [Inscripción del dispositivo Android en la administración de gastos de telecomunicaciones](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-android)

## <a name="turn-off-the-datalert-service"></a>Desactivación del servicio Datalert

1. En **[Intune](https://go.microsoft.com/fwlink/?linkid=2090973)** , seleccione **Configuración de dispositivo** > **Administración de gastos de telecomunicaciones**.
2. Establezca **Habilitar la administración de gastos de telecomunicaciones y bloquear los datos móviles o de itinerancia en dispositivos que hayan excedido las cuotas de uso configuradas.** en **Deshabilitar**.
3. Guarde los cambios mediante **Guardar**.

> [!IMPORTANT]
> Si deshabilita el servicio Datalert en Intune:
>
> - Se anulan todas las acciones que se aplicaron a los dispositivos debido a infracciones anteriores de los límites de uso.
> - Ya no se bloqueará para los usuarios el acceso a los datos y la itinerancia.
> - Intune seguirá recibiendo señales del servicio, pero las ignorará.

## <a name="next-steps"></a>Pasos siguientes

Los informes de uso de datos están disponibles en la consola de administración de Datalert de Saaswedo.
