---
title: "Configuración de un servicio de administración de gastos de telecomunicaciones | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: configure el servicio de administración de gastos de telecomunicaciones de Saaswedo para su integración con Intune."
keywords: Saaswedo
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: sumitp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 915d61344a3c1d388305dd51b1e2463bd2e32770
ms.openlocfilehash: 8d94fec099e1dc8918077062fb73b94a5973ea96

---

# <a name="set-up-a-telecom-expense-management-service-in-intune-azure-preview"></a>Configuración de un servicio de administración de gastos de telecomunicaciones en la versión preliminar de Intune Azure
[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune se integra con la solución de administración de gastos de telecomunicaciones Datalert de Saaswedo, un desarrollador de software de terceros. Datalert es un software de administración de gastos de telecomunicaciones que le permite administrar el uso de datos de telecomunicaciones y evitar los costosos e imprevistos sobrecargos de datos e itinerancia en los dispositivos administrados por Intune. La integración de Intune con Datalert le permite establecer, supervisar y aplicar de manera central límites para el uso de datos nacionales y de itinerancia mediante alertas automatizadas que se disparan cuando los límites superan los umbrales definidos. Puede configurar el servicio para que se apliquen diferentes acciones sobre individuos o grupos de usuarios finales, como deshabilitar la itinerancia cuando los usuarios superan el umbral. Además, en la consola de administración de Datalert se pueden encontrar informes que proporcionan información sobre supervisión del uso de datos.

Para poder usar el servicio Datalert con Intune, debe realizar configuraciones en la consola de Datalert y en Intune. La conexión debe estar activada para el servicio Datalert y para Intune. Si está habilitado el lado de la conexión de Datalert, pero no el de Intune, Intune recibe la comunicación pero la ignora.

>[!NOTE]
>Para habilitar esta característica en su inquilino de prueba, [póngase en contacto con el soporte técnico de Microsoft](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune) y con el soporte técnico de Datalert para que le proporcionen las licencias de software necesarias.

## <a name="supported-platforms"></a>Plataformas compatibles

- Samsung Knox
- iOS 8.0 y versiones posteriores

## <a name="prerequisites"></a>Requisitos previos

- Una suscripción a Microsoft Intune.
- Una suscripción al servicio de administración de gastos de telecomunicaciones de Datalert.

## <a name="list-of-telecom-expense-management-providers"></a>Lista de proveedores de administración de gastos de telecomunicaciones.

Intune se integra actualmente con los siguientes proveedores de administración de gastos de telecomunicaciones:

[Servicio de administración de gastos de telecomunicaciones Datalert de Saaswedo](http://www.datalert.biz/)

## <a name="configure-intune-to-work-with-the-datalert-service"></a>Configuración de Intune para que funcione con el servicio Datalert

 

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
3. En la hoja **Intune**, elija **Configurar dispositivos**.
2. En la hoja **Configuración del dispositivo**, elija **Configuración** > **Administración de gastos de telecomunicaciones**.
2. En **Administración de gastos de telecomunicaciones**, seleccione **Connection status** (Estado de la conexión).

3. Seleccione **Lista de proveedores de servicios TEM** y luego seleccione su proveedor de la lista que se muestra. Se abre una página que es específica de su proveedor. Para Saaswedo, se abre la página de Datalert. Deberá consultar con Saaswedo Datalert para adquirir una suscripción.

4. En la consola de administración de **Datalert**:

    a. Vaya a la pestaña **Settings** y luego vaya a la sección **MDM configuration**.

    b. Seleccione **Unlock** para que pueda especificar la configuración en la página.

    c. En **Server MDM**, elija **Microsoft Intune**.

    d. En **Tenant ID**, escriba su id. de inquilino de Intune y seleccione el botón **Connection**. Al seleccionar **Connection** el servicio Datalert comprueba con Intune para asegurarse de que no haya ninguna conexión ya existente de Datalert con Intune. Al cabo de unos segundos, aparece una página de inicio de sesión de Microsoft, seguida de la autenticación de Azure para Datalert.

    e. En la página de autenticación de Microsoft, seleccione **Accept** (Acepto). Se le redirigirá a una página de Datalert donde se le da las gracias, que se cierra después de unos segundos. Datalert valida la conexión y muestra marcas de verificación verdes junto a una lista de elementos que se han validado. Si la validación da error, verá un mensaje en rojo. Si esto sucede, póngase en contacto con el soporte técnico de Datalert para que le ayuden.

5. Espere unos minutos y, a continuación, vaya al portal de Azure y compruebe que el estado de conexión aparece como **Activo**. 

    >[!NOTE]
    >Para habilitar esta característica en su inquilino de prueba, [póngase en contacto con el soporte técnico de Microsoft](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

6. Vuelva a la consola de administración de Datalert y configure las líneas de datos:

    a. Vaya a la pestaña **Settings**.

    b. Vaya al asistente de **instalación** y siga los pasos que se indican.



El servicio Datalert ya está activo y comienza la supervisión del uso de datos y la deshabilitación de datos móviles y de itinerancia en los dispositivos que superan los límites de uso configurados.

## <a name="turning-off-the-datalert-service"></a>Desactivación del servicio Datalert

Si deshabilita el servicio Datalert en el portal de Azure:

- Todas las acciones que se hayan aplicado a los dispositivos, a consecuencia de las pasadas infracciones de los límites de uso, se desharán.
- Ya no se bloqueará para los usuarios el acceso a los datos y la itinerancia.
- Intune sigue recibiendo señales del servicio, pero las ignora.

**Para desactivar el servicio**

1. En la hoja **Administración de gastos de telecomunicaciones** del portal de Azure, seleccione **Deshabilitar**.

2. Seleccione **Guardar**.

## <a name="viewing-data-usage-and-roaming-reports"></a>Visualización de los informes de uso de datos e itinerancia

En este momento, los informes de uso de datos solo están disponibles en la consola de administración de Datalert de Saaswedo.



<!--HONumber=Feb17_HO2-->


