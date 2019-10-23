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
ms.openlocfilehash: 8ab720ffee3f468d3700558dfbde460ee8f712ea
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505488"
---
# <a name="categorize-devices-into-groups"></a>Clasificar dispositivos en grupos

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Para facilitar la administración de los dispositivos, puede usar las categorías de dispositivos de Microsoft Intune para agregar automáticamente dispositivos a grupos en función de las categorías que defina.

Las categorías de dispositivos usan el siguiente flujo de trabajo:
1. Crean categorías que los usuarios pueden elegir cuando inscriban sus dispositivos.
2. Cuando los usuarios de dispositivos iOS y Android inscriben un dispositivo, deben elegir una categoría de la lista de categorías configuradas. Para asignar una categoría a un dispositivo Windows, los usuarios deben usar el sitio web del Portal de empresa.
3. Después, puede implementar directivas y aplicaciones en esos grupos.

Puede crear todas las categorías de dispositivo que quiera. Por ejemplo:
- Dispositivo de punto de venta
- Dispositivo de demostración
- Ventas
- Cuentas
- Manager

## <a name="how-to-configure-device-categories"></a>Configuración de las categorías de dispositivos

### <a name="step-1-create-device-categories-on-the-intune-blade-of-the-azure-portal"></a>Paso 1: Creación de categorías de dispositivos en la hoja de Intune de Azure Portal
1. En [Intune en el portal de Azure](https://aka.ms/intuneportal), seleccione **Inscripción de dispositivos**.
2. En la hoja **Inscripción de dispositivos**, elija **Categorías de dispositivos**.
3. En la página **Categorías de dispositivos**, elija **Crear** para agregar una nueva categoría.
4. En la hoja **Crear categoría de dispositivos**, escriba un **Nombre** para la nueva categoría y una **Descripción** opcional.
5. Cuando haya terminado, seleccione **Crear**. Puede ver la nueva categoría en la lista de categorías.

Usará el nombre de la categoría de dispositivo al crear grupos de seguridad de Azure Active Directory (Azure AD) en el paso 2.

### <a name="step-2-create-azure-active-directory-security-groups"></a>Paso 2: Creación de grupos de seguridad de Azure Active Directory
En este paso creará grupos dinámicos en Azure Portal según la categoría del dispositivo y el nombre de la categoría del dispositivo.

Para continuar, consulte [Uso de atributos para crear reglas avanzadas](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects) en la documentación de Azure AD.

Use la información de esta sección para crear un grupo de dispositivos con una regla avanzada mediante el atributo**deviceCategory**. Por ejemplo: **device.deviceCategory -eq** "*el nombre de la categoría de dispositivo que obtuvo de Azure Portal*".

Después de configurar grupos de dispositivos y de que los usuarios inscriban sus dispositivos, se les presenta una lista de las categorías que ha configurado. Tras elegir una categoría y finalizar la inscripción, sus dispositivos se agregan al grupo de seguridad de Active Directory correspondiente a la categoría que eligieron.

### <a name="view-the-categories-of-devices-that-you-manage"></a>Ver las categorías de los dispositivos que administra

1. En [Intune en el portal de Azure](https://aka.ms/intuneportal), elija **Dispositivos**.

2. En **Administrar**, seleccione **Todos los dispositivos**.

3. En la lista de dispositivos, examine la columna **Categoría de dispositivo**.

Si no se muestra la columna **Categoría de dispositivo**, seleccione **Columnas**. Elija **Categoría de dispositivo** en la lista y seleccione **Aplicar**.

### <a name="change-the-category-of-a-device"></a>Cambiar la categoría de un dispositivo

1. En [Intune en el portal de Azure](https://aka.ms/intuneportal), elija **Dispositivos**.
2. En la hoja **Dispositivos**, en la sección **Administrar**, elija **Todos los dispositivos**.
3. En la lista de dispositivos, elija el dispositivo que quiera. Después, en la sección **Administrar** de la hoja de propiedades del dispositivo, elija **Propiedades**.
4. En la siguiente hoja, puede cambiar la **categoría del dispositivo** seleccionado por cualquiera de los nombres de categoría que configuró anteriormente.

## <a name="after-you-configure-device-groups"></a>Después de configurar grupos de dispositivos

Cuando los usuarios de dispositivos iOS y Android inscriben sus dispositivos, deben elegir una categoría de la lista de categorías configuradas. Tras elegir una categoría y finalizar la inscripción, sus dispositivos se agregarán al grupo de dispositivos de Intune, o al grupo de seguridad de Active Directory correspondiente a la categoría que eligieron.

Los usuarios de Windows deben usar el sitio web de Portal de empresa para seleccionar una categoría.

Independientemente de la plataforma, los usuarios siempre pueden ir a portal.manage.microsoft.com después de inscribir el dispositivo. Haga que el usuario acceda al sitio web del Portal de empresa y vaya a **Mis dispositivos**. El usuario puede elegir un dispositivo inscrito de la página y seleccionar una categoría.

Tras elegir una categoría, el dispositivo se agrega automáticamente al grupo correspondiente que ha creado. Si ya hay un dispositivo inscrito antes de configurar las categorías, el usuario verá una notificación del dispositivo en el sitio web del Portal de empresa. De esta manera, el usuario sabrá que puede seleccionar una categoría la próxima vez que acceda a la aplicación Portal de empresa de iOS o Android.

## <a name="further-information"></a>Más información
- Puede editar una categoría de dispositivo en Azure Portal, pero debe actualizar manualmente los grupos de seguridad de Azure AD que hagan referencia a esta categoría.

- Si elimina una categoría, los dispositivos asignados a esta mostrarán el nombre de la categoría **Sin asignar**.
