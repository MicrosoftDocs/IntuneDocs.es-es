---
title: Clasificar los dispositivos con la asignación de grupos de dispositivos
description: Use la asignación de grupos de dispositivos de Microsoft Intune para agrupar dispositivos en las categorías que haya definido y que, de este modo, sea más fácil administrarlos.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 06/06/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8b8c06a3-6b6c-4cf1-8646-b24fa9b1a39e
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5a346c321147656d748d3abde78575268b20e9ab
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="categorize-devices-with-device-group-mapping-in-microsoft-intune"></a>Clasificar los dispositivos con la asignación de grupos de dispositivos en Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Use la **asignación de grupos de dispositivos** de Microsoft Intune para agrupar dispositivos en las categorías basadas en grupos que haya definido y que, de este modo, sea más fácil administrarlos. 

En la asignación de grupos de dispositivos se produce el siguiente flujo de trabajo:
1. Crear categorías que los usuarios podrán elegir cuando inscriban sus dispositivos
2. Puede crear grupos, o usar grupos existentes, para cada categoría que quiera usar. Según la versión de Intune que esté utilizando, serán grupos de Intune o grupos de seguridad de Azure Active Directory.
2. Se configuran reglas que asignan la categoría que elija al grupo de dispositivos creado.
3. Cuando los usuarios finales de dispositivos iOS y Android inscriben sus dispositivos, deben elegir una categoría de la lista de categorías configuradas. Para asignar una categoría a un dispositivo Windows, los usuarios finales deben usar el sitio web del Portal de empresa (consulte **Después de configurar los grupos de dispositivos** en este tema para más información).
4. Después, puede implementar directivas y aplicaciones en esos grupos.

Puede crear las categorías de dispositivos que desee, por ejemplo:
* Dispositivo de punto de venta
* Dispositivo de demostración
* Ventas
* Cuentas
* Manager

## <a name="important-information-about-a-change-in-group-management-for-intune"></a>Información importante acerca de un cambio en la administración de grupos para Intune

En función de sus comentarios, estamos en proceso de unificar la experiencia de dirección y agrupación a través de Enterprise Mobility + Security. Por este motivo, pronto se convertirán grupos de Intune en grupos de seguridad basados en Azure Active Directory. Después de este cambio, ya no creará grupos mediante Intune. En su lugar, deberá crearlos en Azure Portal. Este cambio se realizará de forma gradual y puede leer los detalles completos acerca de este cambio y su escala de tiempo en [este tema](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).

### <a name="which-procedure-in-this-topic-should-you-use-to-configure-device-group-mapping"></a>¿Qué procedimiento de este tema se debe usar para configurar la asignación de grupos de dispositivos?

Debido a la implementación por fases de los grupos de seguridad de Azure Active Directory, debe abrir el área de trabajo **Grupos** en la [consola de administración de Intune](https://manage.microsoft.com) para identificar qué procedimiento utilizar:

-  Si ve un vínculo a Azure Portal, significa que no usa grupos de Intune. Siga el procedimiento que se describe en [Configuración de la asignación de grupos de dispositivos para grupos de Azure Active Directory](/intune-classic/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune#how-to-configure-device-group-mapping-for-azure-active-directory-groups) a continuación.
-  Si no ve un vínculo a Azure Portal, significa que sigue usando grupos de Intune. Siga el procedimiento que se describe en [Configuración de la asignación de grupos de dispositivos para grupos de Intune](/intune-classic/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune#how-to-configure-device-group-mapping-for-intune-groups) a continuación.

## <a name="how-to-configure-device-group-mapping-for-intune-groups"></a>Configuración de la asignación de grupos de dispositivos para grupos de Intune
1. Para cada categoría de dispositivo que quiera usar, cree un grupo de dispositivos de Intune o identifique un grupo existente. Para obtener más información sobre cómo crear grupos, vea [Usar grupos para administrar usuarios y dispositivos en Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).
2. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), seleccione **Administración**.
3. En el área de trabajo **Administración**, expanda **Administración de dispositivos móviles** y elija **Asignación de grupos de dispositivos**.
4. En la página **Asignación de grupos de dispositivos**, habilite la asignación de grupos de dispositivos.
5. Elija **Agregar** para crear una regla de asignación.
6. En el cuadro de diálogo **Agregar regla de asignación de grupos de dispositivos**, escriba el nombre de la categoría que quiere crear y, luego, en la lista desplegable, elija la colección de dispositivos que quiera asignar a esta categoría. Elija **Agregar** cuando haya acabado.
7. Cuando termine de agregar categorías y grupos, elija **Guardar**.



## <a name="how-to-configure-device-group-mapping-for-azure-active-directory-groups"></a>Configuración de la asignación de grupos de dispositivos para grupos de Azure Active Directory

### <a name="step-1---create-device-categories-in-the-intune-administration-console"></a>Paso 1: Crear categorías de dispositivos en la consola de administración de Intune
1. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), seleccione **Administración**.
2. En el área de trabajo **Administración**, expanda **Administración de dispositivos móviles** y elija **Categorías de dispositivos**.
3. En la página **Categorías de dispositivos**, verá una lista donde puede configurar las categorías de dispositivos: 
4. Puede escribir un nombre y después hacer clic en **Agregar**, para agregarlo como una nueva categoría de dispositivo.
5. Además, puede seleccionar una categoría y después **eliminarla**.

Usará el nombre de la categoría de dispositivo al crear grupos de seguridad de Azure Active Directory en el paso 2.

### <a name="step-2---create-azure-active-directory-security-groups"></a>Paso 2: Crear grupos de seguridad de Azure Active Directory

En este paso, creará grupos dinámicos en Azure Portal según la categoría del dispositivo y el nombre de la categoría del dispositivo.

Para continuar, consulte el tema [Uso de atributos para crear reglas avanzadas](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects) en la documentación de Azure Active Directory.
Utilice la información de este tema para crear un grupo de dispositivos con una regla avanzada mediante el atributo **deviceCategory**.
Por ejemplo (**device.deviceCategory -eq** "<*el nombre de la categoría de dispositivo que obtuvo desde la consola de administración de Intune*>")


## <a name="after-you-configure-device-groups"></a>Después de configurar grupos de dispositivos

Cuando los usuarios finales de dispositivos iOS y Android inscriben sus dispositivos, deben elegir una categoría de la lista de categorías configuradas. Tras elegir una categoría y finalizar la inscripción, sus dispositivos se agregarán al grupo de dispositivos de Intune, o al grupo de seguridad de Active Directory correspondiente a la categoría que eligieron.

Para asignar una categoría a un dispositivo Windows, los usuarios finales deben usar el sitio web del Portal de empresa (portal.manage.microsoft.com) después de inscribir el dispositivo. En un dispositivo Windows, acceda al sitio web y vaya a **Menú** > **Mis dispositivos**. Elija un dispositivo inscrito de la página y luego seleccione una categoría. 

Tras elegir una categoría, el dispositivo se agrega automáticamente al grupo correspondiente que ha creado. Si un dispositivo ya estaba inscrito antes de que configurara las categorías, el usuario final verá una notificación sobre el dispositivo en el sitio web del Portal de empresa y se le pedirá que seleccione una categoría la próxima vez que acceda a la aplicación del Portal de empresa en iOS o Android.



### <a name="see-also"></a>Vea también
[Usar grupos para administrar usuarios y dispositivos en Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)
