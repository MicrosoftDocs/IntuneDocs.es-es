---
title: "Uso de categorías de dispositivos en Intune | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: aprenda a usar las categorías de dispositivos que los usuarios pueden elegir cuando inscriben sus dispositivos en Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7b668c37-40b9-4c69-8334-5d8344e78c24
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1609ed2f127fe9d7d1f1c3b3e923bd12f1088200
ms.openlocfilehash: 41b3cfb8006a7390094d01b4f0fdc38417e858be


---

# <a name="map-device-groups"></a>Asignación de grupos de dispositivos


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Use las categorías de dispositivos de Microsoft Intune para agregar dispositivos automáticamente a los grupos en función de las categorías que defina, a fin de facilitar la administración de dichos dispositivos.

Las categorías de dispositivos usan el siguiente flujo de trabajo:
1.    Crear categorías que los usuarios podrán elegir cuando inscriban sus dispositivos
4.    Cuando los usuarios finales inscriben sus dispositivos, deben elegir una categoría en la lista de categorías configuradas. Si un dispositivo ya está inscrito, se pedirá al usuario final que seleccione una categoría la próxima vez que tenga acceso a la aplicación Portal de empresa.


Puede crear las categorías de dispositivos que desee, por ejemplo:
- Dispositivo de punto de venta
- Dispositivo de demostración
- Ventas
- Cuentas
- Manager

## <a name="how-to-configure-device-categories"></a>Configuración de las categorías de dispositivos

### <a name="step-1---create-device-categories-in-the-intune-blade-of-the-azure-portal"></a>Paso 1: Creación de categorías de dispositivos en la hoja de Intune del portal de Azure
1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
3. En la hoja **Intune**, elija **Inscribir dispositivos**.
3. En la hoja **Inscripción**, elija **Categorías de dispositivos**.
4. En la página **Categorías de dispositivos**, elija **Crear** para agregar una nueva categoría.
5. En la siguiente hoja, escriba un**nombre** para la nueva categoría y una **descripción**opcional.
6. Haga clic en **Crear** cuando acabe. Verá la categoría que acaba de crear en la lista de categorías.

Usará el nombre de la categoría de dispositivo al crear grupos de seguridad de Azure Active Directory en el paso 2.

### <a name="step-2---create-azure-active-directory-security-groups"></a>Paso 2: Crear grupos de seguridad de Azure Active Directory
En este paso, creará grupos dinámicos en Azure Portal según la categoría del dispositivo y el nombre de la categoría del dispositivo.

Para continuar, consulte el tema [Uso de atributos para crear reglas avanzadas](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects) en la documentación de Azure Active Directory. 

Use la información de esta sección para crear un grupo de dispositivos con una regla avanzada mediante el atributo**deviceCategory**. Por ejemplo (**device.deviceCategory -eq** "*<the device category name you got from the Intune portal>*").

Después de configurar grupos de dispositivos y de que los usuarios inscriban sus dispositivos, se les presenta una lista de las categorías que ha configurado. Tras elegir una categoría y finalizar la inscripción, sus dispositivos se agregan al grupo de seguridad de Active Directory correspondiente a la categoría que eligieron.

### <a name="how-to-view-the-categories-of-devices-you-manage"></a>Visualización de las categorías de los dispositivos administrados
1.    En la hoja de Intune del portal de Azure, elija **Dispositivos y grupos**.

2.    En **Administrar**, haga clic en **Todos los dispositivos**.

3.    En la lista de dispositivos, examine la columna **Categoría**.

Si la columna **Categoría**no se muestra, haga clic en **Columnas**, elija **Categoría** en la lista y, a continuación, haga clic en **Aplicar**.

### <a name="to-change-the-category-of-a-device"></a>Cambio de la categoría de un dispositivo

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
3. En la hoja **Intune**, elija **Dispositivos y grupos**.
4. En la hoja **Dispositivos y grupos**, elija **Administrar** > **Todos los dispositivos**.
5. En la lista de dispositivos, elija el dispositivo que desee, y después, en la hoja de propiedades del dispositivo, elija **Administrar** > **Propiedades**.
6. En la siguiente hoja, puede cambiar la **categoría del dispositivo** seleccionado por cualquiera de los nombres de categoría que configuró anteriormente.



## <a name="further-information"></a>Más información
- Puede editar una categoría de dispositivo en Azure Portal, pero si lo hace, debe actualizar manualmente los grupos de seguridad de Azure Active Directory que hagan referencia a esta categoría.

- Si elimina una categoría, los dispositivos que posteriormente se asignen a esta mostrarán el nombre de la categoría **Sin asignar**.





<!--HONumber=Feb17_HO2-->


