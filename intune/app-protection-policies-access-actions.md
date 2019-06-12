---
title: Borrar los datos mediante acciones de acceso de la directiva de protección de aplicaciones
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo borrar los datos de forma selectiva mediante acciones de acceso de directiva de protección de aplicaciones en Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f5ca557e-a8e1-4720-b06e-837c4f0bc3ca
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: cd323fce7f7bdbf17697c82935a9d2d5f47bb7ee
ms.sourcegitcommit: 6e07c35145f70b008cf170bae57143248a275b67
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2019
ms.locfileid: "66804689"
---
# <a name="selectively-wipe-data-using-app-protection-policy-access-actions-in-intune"></a>Borrar los datos de forma selectiva mediante acciones de acceso de la directiva de protección de aplicaciones en Intune

Con las directivas de protección de aplicaciones de Intune, puede configurar valores para impedir que los usuarios finales accedan a una aplicación o a una cuenta corporativas. Estos valores de configuración afectan a la reubicación de datos y a los requisitos de acceso establecidos por su organización, por ejemplo, para dispositivos con jailbreak aplicado y versiones mínimas de sistema operativo.
 
Puede elegir explícitamente borrar los datos corporativos de su empresa desde el dispositivo del usuario final como una acción que se realizará mediante estos valores en caso de incumplimiento. En algunos valores, podrá configurar varias acciones, como bloquear el acceso y borrar los datos en función de diferentes valores especificados.

## <a name="create-an-app-protection-policy-using-access-actions"></a>Crear una directiva de protección de aplicaciones mediante acciones de acceso

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. En el panel **Intune**, seleccione **Aplicaciones cliente** > **Directivas de protección de aplicaciones**.
4. Haga clic en **Agregar una directiva** (también puede editar una directiva existente). 
5. Haga clic en **Configurar los valores obligatorios** para ver la lista de valores que se pueden configurar para la directiva. 
6. Si se desplaza hacia abajo en el panel Configuración, verá una sección titulada **Acciones de acceso** con una tabla editable.

    ![Captura de pantalla de las acciones de acceso de protección de aplicaciones de Intune](./media/apps-selective-wipe-access-actions01.png)

7. Seleccione **Configuración** y escriba el **Valor** que los usuarios deben cumplir para iniciar sesión en la aplicación de empresa. 
8. Seleccione la **Acción** que quiere llevar a cabo si los usuarios no cumplen los requisitos. En algunos casos, se pueden configurar varias acciones para una sola configuración. Para obtener más información, consulte [Creación y asignación de directivas de protección de aplicaciones](app-protection-policies.md).

>[!NOTE]
> Para usar el valor **Modelos de dispositivo o Fabricantes de dispositivos**, escriba una lista de identificadores de modelo separados por punto y coma. Evite los espacios en las listas de varios valores. Estos valores no distinguen entre mayúsculas y minúsculas. 

## <a name="policy-settings"></a>Configuraciones de directiva 

La tabla de configuración de la directiva de protección de aplicaciones tiene las columnas **Configuración**, **Valor** y **Acción**.

### <a name="ios-policy-settings"></a>Configuración de directivas de iOS
Para iOS, podrá configurar las acciones de las siguientes opciones desde el menú desplegable **Configuración**:
-  Intentos máximos de PIN
-  Período de gracia sin conexión
-  Dispositivos con jailbreak o liberados
-  Versión mínima de sistema operativo
-  Versión mínima de la aplicación
-  Versión mínima del SDK
-  Modelos de dispositivos

Para usar el valor de configuración **Modelos de dispositivo**, indique una lista de identificadores de modelos de iOS separados por punto y coma. Puede encontrar un identificador de modelo de iOS en la columna Tipo de dispositivo en la [documentación de soporte técnico de HockeyApp](https://support.hockeyapp.net/kb/client-integration-ios-mac-os-x-tvos/ios-device-types).<br>
Entrada de ejemplo: *iPhone5,2;iPhone5,3*

En los dispositivos del usuario final, el cliente de Intune tomaría medidas en función de una coincidencia simple de las cadenas de modelo de dispositivo que se especifican en Intune para las directivas de protección de aplicaciones. La coincidencia depende por completo de lo que informa el dispositivo. A usted (administrador de TI) se le anima a garantizar que se produzca el comportamiento deseado mediante la comprobación de esta configuración en función de una variedad de modelos y fabricantes de dispositivos, y destinado a un grupo de usuarios pequeño. El valor predeterminado es **Sin configurar**.<br>
Establezca una de las acciones siguientes: 
- Permitir especificados (bloquear no especificados)
- Permitir especificados (borrar no especificados)

**¿Qué ocurre si el administrador de TI introduce una lista diferente de identificadores de modelo de iOS entre directivas destinadas a las mismas aplicaciones para el mismo usuario de Intune?**<br>
Cuando surgen conflictos entre dos directivas de protección para los valores configurados, Intune suele tomar el enfoque más restrictivo. Por lo tanto, la directiva resultante que se manda a la aplicación de destino que el usuario de Intune de destino está abriendo sería una intersección de los identificadores de modelo de iOS enumerados en *Directiva A* y *Directiva B* con destino a la misma combinación de aplicación y usuario. Por ejemplo, si *Directiva A* especifica "iPhone5,2;iPhone5,3", mientras que *Directiva B* especifica "iPhone5,3", la directiva resultante que el usuario de Intune usará según *Directiva A* y *Directiva B* será "iPhone5,3". 

### <a name="android-policy-settings"></a>Configuración de directivas de Android

Para Android, podrá configurar las acciones de las siguientes opciones desde el menú desplegable **Configuración**:
-  Intentos máximos de PIN
-  Período de gracia sin conexión
-  Dispositivos con jailbreak o liberados
-  Versión mínima de sistema operativo
-  Versión mínima de la aplicación
-  Versión mínima del parche
-  Fabricantes de dispositivos
-  Atestación de dispositivo SafetyNet
-  Examen de amenazas en las aplicaciones

Para usar el valor de configuración **Fabricantes de dispositivos**, indique una lista de fabricantes de Android separados por punto y coma. Puede encontrar el fabricante de Android de un dispositivo en la configuración del dispositivo.<br>
Entrada de ejemplo: *Fabricante A; Fabricante B* 

>[!NOTE]
> Estos son algunos fabricantes habituales sobre los que se ha informado de dispositivos con Intune, y se pueden usar como entrada: Asus; Blackberry; Bq; Gionee; Google; Hmd global; Htc; Huawei; Infinix; Kyocera; Lemobile; Lenovo; Lge; Motorola; Oneplus; Oppo; Samsung; Sharp; Sony; Tecno; Vivo; Vodafone; Xiaomi; Zte; Zuk.

En los dispositivos del usuario final, el cliente de Intune tomaría medidas en función de una coincidencia simple de las cadenas de modelo de dispositivo que se especifican en Intune para las directivas de protección de aplicaciones. La coincidencia depende por completo de lo que informa el dispositivo. A usted (administrador de TI) se le anima a garantizar que se produzca el comportamiento deseado mediante la comprobación de esta configuración en función de una variedad de modelos y fabricantes de dispositivos, y destinado a un grupo de usuarios pequeño. El valor predeterminado es **Sin configurar**.<br>
Establezca una de las acciones siguientes: 
- Permitir especificados (bloquear no especificados)
- Permitir especificados (bloquear no especificados)

**¿Qué ocurre si el administrador de TI introduce una lista diferente de fabricantes de Android entre directivas destinadas a las mismas aplicaciones para el mismo usuario de Intune?**<br>
Cuando surgen conflictos entre dos directivas de protección para los valores configurados, Intune suele tomar el enfoque más restrictivo. Por lo tanto, la directiva resultante que se manda a la aplicación de destino que el usuario de Intune de destino está abriendo sería una intersección de los fabricantes de Android enumerados en *Directiva A* y *Directiva B* con destino a la misma combinación de aplicación y usuario. Por ejemplo, si *Directiva A* especifica "Google;Samsung", mientras que *Directiva B* especifica "Google", la directiva resultante que el usuario de Intune usará según *Directiva A* y *Directiva B* será "Google". 

### <a name="additional-settings-and-actions"></a>Configuración y acciones adicionales 

De forma predeterminada, la tabla tendrá filas rellenadas como valores configurados para **Período de gracia sin conexión** e **Intentos máximos de PIN**, siempre que el valor **Requerir PIN para acceder** esté establecido en **Sí**.
 
Para llevar a cabo la configuración, seleccione una opción de la lista desplegable en la columna **Configuración**. Cuando la opción esté seleccionada, se habilitará el cuadro de texto editable en la columna **Valor** de la misma fila, si es necesario establecer un valor. Además, se habilitará la lista desplegable en la columna **Acción** con el conjunto de acciones de inicio condicional aplicables a la configuración. 

En la siguiente lista aparece la lista de acciones más comunes:
-  **Bloquear el acceso**: impide que el usuario final acceda a la aplicación corporativa.
-  **Borrar datos**: borra los datos corporativos del dispositivo del usuario final.
-  **Advertir**: muestra un cuadro de diálogo al usuario final como mensaje de advertencia.

En algunos casos, como el valor **Versión mínima del sistema operativo**, puede configurar la opción para realizar todas las acciones aplicables en función de los diferentes números de versión. 

![Captura de pantalla de las acciones de acceso de protección de aplicaciones (versión mínima de sistema operativo)](./media/apps-selective-wipe-access-actions05.png)

Cuando una opción está totalmente configurada, la fila aparecerá en la vista de solo lectura y estará disponible para editarse en cualquier momento. Además, la fila tendrá un menú desplegable para seleccionar en la columna **Configuración**. En el menú desplegable no podrá seleccionar las opciones que ya se hayan configurado y que no admitan varias acciones.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre las directivas de protección de aplicaciones de Intune, consulte:
- [Creación y asignación de directivas de protección de aplicaciones](app-protection-policies.md)
- [Configuración de directivas de protección de aplicaciones de iOS](app-protection-policy-settings-ios.md)
- [Configuración de directivas de protección de aplicaciones Android en Microsoft Intune](app-protection-policy-settings-android.md) 
