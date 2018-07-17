---
title: Borrar los datos de forma selectiva mediante acciones de acceso de la directiva de protección de aplicaciones
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo borrar los datos de forma selectiva mediante acciones de acceso de directiva de protección de aplicaciones en Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f5ca557e-a8e1-4720-b06e-837c4f0bc3ca
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2cfd426a0ae7165a7aae60a90d104852fd834db6
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909123"
---
# <a name="selectively-wipe-data-using-app-protection-policy-access-actions-in-intune"></a>Borrar los datos de forma selectiva mediante acciones de acceso de la directiva de protección de aplicaciones en Intune

Con las directivas de protección de aplicaciones de Intune, puede configurar valores para impedir que los usuarios finales accedan a una aplicación o a una cuenta corporativas. Estos valores de configuración afectan a la reubicación de datos y a los requisitos de acceso establecidos por su organización, por ejemplo, para dispositivos con jailbreak aplicado y versiones mínimas de sistema operativo.
 
Puede elegir explícitamente borrar los datos corporativos de su empresa desde el dispositivo del usuario final como una acción que se realizará mediante estos valores en caso de incumplimiento. En algunos valores, podrá configurar varias acciones, como bloquear el acceso y borrar los datos en función de diferentes valores especificados.

## <a name="create-an-app-protection-policy-using-access-actions"></a>Crear una directiva de protección de aplicaciones mediante acciones de acceso

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios** > **Intune**.  
    Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, seleccione **Aplicaciones móviles** > **Directivas de protección de aplicaciones**.
4. Haga clic en **Agregar una directiva** (también puede editar una directiva existente). 
5. Haga clic en **Configurar los valores obligatorios** para ver la lista de valores que se pueden configurar para la directiva. 
6. Si se desplaza hacia abajo en el panel **Configuración**, verá una sección titulada **Acciones de acceso** con una tabla editable.

    ![Captura de pantalla de las acciones de acceso de protección de aplicaciones de Intune](./media/apps-selective-wipe-access-actions01.png)

7. Seleccione **Configuración** y escriba el **Valor** que los usuarios deben cumplir para iniciar sesión en la aplicación de empresa. 
8. Seleccione la **Acción** que quiere llevar a cabo si los usuarios no cumplen los requisitos. En algunos casos, se pueden configurar varias acciones para una sola configuración. Para obtener más información, consulte [Creación y asignación de directivas de protección de aplicaciones](app-protection-policies.md).

>[!NOTE]
> Para usar el valor de configuración **Modelos de dispositivo**, indique una lista de identificadores de modelos separados por punto y coma. 

## <a name="policy-settings"></a>Configuraciones de directiva 

La tabla de configuración de la directiva de protección de aplicaciones tiene las columnas **Configuración**, **Valor** y **Acción**.

Para iOS, podrá configurar las acciones de las siguientes opciones desde el menú desplegable **Configuración**:
-  Intentos máximos de PIN
-  Período de gracia sin conexión
-  Dispositivos con jailbreak o liberados
-  Versión mínima de sistema operativo
-  Versión mínima de la aplicación
-  Versión mínima del SDK
-  Modelos de dispositivos

Para Android, podrá configurar las acciones de las siguientes opciones desde el menú desplegable **Configuración**:
-  Intentos máximos de PIN
-  Período de gracia sin conexión
-  Dispositivos con jailbreak o liberados
-  Versión mínima de sistema operativo
-  Versión mínima de la aplicación
-  Versión mínima del parche
-  Fabricantes de dispositivos

De forma predeterminada, la tabla tendrá filas rellenadas como valores configurados para **Período de gracia sin conexión** e **Intentos máximos de PIN**, siempre que el valor **Requerir PIN para acceder** esté establecido en **Sí**.
 
Para llevar a cabo la configuración, seleccione una opción de la lista desplegable en la columna **Configuración**. Cuando la opción esté seleccionada, se habilitará el cuadro de texto editable en la columna **Valor** de la misma fila, si es necesario establecer un valor. Además, se habilitará la lista desplegable en la columna **Acción** con el conjunto de acciones de inicio condicional aplicables a la configuración. 

En la siguiente lista aparece la lista de acciones más comunes:
-  **Bloquear el acceso**: impide que el usuario final acceda a la aplicación corporativa.
-  **Borrar datos**: borra los datos corporativos del dispositivo del usuario final.
-  **Advertir**: muestra un cuadro de diálogo al usuario final como mensaje de advertencia.

### <a name="additional-settings-and-actions"></a>Configuración y acciones adicionales 

En algunos casos, como el valor **Versión mínima del sistema operativo**, puede configurar la opción para realizar todas las acciones aplicables en función de los diferentes números de versión. 

![Captura de pantalla de las acciones de acceso de protección de aplicaciones de Intune (versión mínima de sistema operativo)](./media/apps-selective-wipe-access-actions05.png)

Cuando una opción está totalmente configurada, la fila aparecerá en la vista de solo lectura y estará disponible para editarse en cualquier momento. Además, la fila tendrá un menú desplegable para seleccionar en la columna **Configuración**. En el menú desplegable no podrá seleccionar las opciones que ya se hayan configurado y que no admitan varias acciones.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre las directivas de protección de aplicaciones de Intune, consulte:
- [Creación y asignación de directivas de protección de aplicaciones](app-protection-policies.md)
- [Configuración de directivas de protección de aplicaciones de iOS](app-protection-policy-settings-ios.md)
- [Configuración de directivas de protección de aplicaciones Android en Microsoft Intune](app-protection-policy-settings-android.md) 


