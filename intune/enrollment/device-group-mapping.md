---
title: Clasificación de los dispositivos en grupos en Intune
titleSuffix: Microsoft Intune
description: Descubra cómo clasificar los dispositivos en grupos para facilitar la administración.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7b668c37-40b9-4c69-8334-5d8344e78c24
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f0976ff8e6ec45f1f861fd4a4e0474255d701ae4
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414253"
---
# <a name="categorize-devices-into-groups"></a>Clasificar dispositivos en grupos

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Para facilitar la administración de los dispositivos, puede usar las categorías de dispositivos de Microsoft Intune para agregar automáticamente dispositivos a grupos en función de las categorías que defina.

Las categorías de dispositivos usan el siguiente flujo de trabajo:
1. Crean categorías que los usuarios pueden elegir cuando inscriban sus dispositivos.
2. Cuando los usuarios de dispositivos iOS/iPadOS y Android inscriben un dispositivo, deben elegir una categoría de la lista de categorías configuradas. Para asignar una categoría a un dispositivo Windows, los usuarios deben usar el sitio web del Portal de empresa.
3. Después, puede implementar directivas y aplicaciones en esos grupos.

Puede crear todas las categorías de dispositivo que quiera. Por ejemplo:
- Dispositivo de punto de venta
- Dispositivo de demostración
- Ventas
- Cuentas
- Manager

## <a name="how-to-configure-device-categories"></a>Configuración de las categorías de dispositivos

### <a name="step-1-create-device-categories-on-the-intune-blade-of-the-azure-portal"></a>Paso 1: Creación de categorías de dispositivos en la hoja de Intune de Azure Portal
1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), seleccione **Dispositivos** > **Categorías de dispositivos**.
2. En la página **Categorías de dispositivos**, elija **Crear** para agregar una nueva categoría.
3. En la hoja **Crear categoría de dispositivos**, escriba un **Nombre** para la nueva categoría y una **Descripción** opcional.
4. Cuando haya terminado, seleccione **Crear**. Puede ver la nueva categoría en la lista de categorías.

Usará el nombre de la categoría de dispositivo al crear grupos de seguridad de Azure Active Directory (Azure AD) en el paso 2.

### <a name="step-2-create-azure-active-directory-security-groups"></a>Paso 2: Creación de grupos de seguridad de Azure Active Directory
En este paso creará grupos dinámicos en Azure Portal según la categoría del dispositivo y el nombre de la categoría del dispositivo.

Para continuar, consulte [Uso de atributos para crear reglas avanzadas](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects) en la documentación de Azure AD.

Use la información de esta sección para crear un grupo de dispositivos con una regla avanzada mediante el atributo**deviceCategory**. Por ejemplo: **device.deviceCategory -eq** "*el nombre de la categoría de dispositivo que obtuvo de Azure Portal*".

Después de configurar grupos de dispositivos y de que los usuarios inscriban sus dispositivos, se les presenta una lista de las categorías que ha configurado. Tras elegir una categoría y finalizar la inscripción, sus dispositivos se agregan al grupo de seguridad de Active Directory correspondiente a la categoría que eligieron.

### <a name="view-the-categories-of-devices-that-you-manage"></a>Ver las categorías de los dispositivos que administra

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), seleccione **Dispositivos** > **Todos los dispositivos**.

2. En la lista de dispositivos, examine la columna **Categoría de dispositivo**.

Si no se muestra la columna **Categoría de dispositivo**, seleccione **Columnas** > **Categoría** > **Aplicar**.

### <a name="change-the-category-of-a-device"></a>Cambiar la categoría de un dispositivo

1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Dispositivos** > **Todos los dispositivos** > seleccione el dispositivo que quiera > **Propiedades**.
2. En la siguiente hoja, puede cambiar la **categoría del dispositivo** seleccionado por cualquiera de los nombres de categoría que configuró anteriormente.

## <a name="after-you-configure-device-groups"></a>Después de configurar grupos de dispositivos

Cuando los usuarios de dispositivos iOS/iPadOS y Android inscriben su dispositivo, deben elegir una categoría de la lista de categorías configuradas. Tras elegir una categoría y finalizar la inscripción, sus dispositivos se agregarán al grupo de dispositivos de Intune, o al grupo de seguridad de Active Directory correspondiente a la categoría que eligieron.

Los usuarios de Windows deben usar el sitio web de Portal de empresa para seleccionar una categoría.

Independientemente de la plataforma, los usuarios siempre pueden ir a portal.manage.microsoft.com después de inscribir el dispositivo. Haga que el usuario acceda al sitio web del Portal de empresa y vaya a **Mis dispositivos**. El usuario puede elegir un dispositivo inscrito de la página y seleccionar una categoría.

Tras elegir una categoría, el dispositivo se agrega automáticamente al grupo correspondiente que ha creado. Si ya hay un dispositivo inscrito antes de configurar las categorías, el usuario verá una notificación del dispositivo en el sitio web del Portal de empresa. De esta manera, el usuario sabrá que puede seleccionar una categoría la próxima vez que acceda a la aplicación Portal de empresa de iOS/iPadOS o Android.

## <a name="further-information"></a>Más información
- Puede editar una categoría de dispositivo en Azure Portal, pero debe actualizar manualmente los grupos de seguridad de Azure AD que hagan referencia a esta categoría.

- Si elimina una categoría, los dispositivos asignados a esta mostrarán el nombre de la categoría **Sin asignar**.
