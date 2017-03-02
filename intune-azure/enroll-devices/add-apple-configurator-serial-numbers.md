---
title: "Adición de números de serie de Apple Configurator | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: aprenda a agregar números de serie a dispositivos iOS corporativos mediante Apple Configurator."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d408aa38-7d1e-40df-9067-246e53f6e26f
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 37c56d0c219c61c345874b24e8ba9ac640f1ef76
ms.openlocfilehash: 4c2ebe535935518127a799ae0518c43a2e53de72
ms.lasthandoff: 02/17/2017


---

# <a name="add-apple-configurator-serial-numbers"></a>Adición de números de serie de Apple Configurator

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Siga estos pasos para agregar números de serie a Intune cuando quiera [inscribir dispositivos iOS corporativos mediante Apple Configurator con el Asistente de configuración](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md). Puede agregar números de serie de uno en uno o cargar un archivo de valores separados por comas (CSV) de números de serie. Después de agregar números de serie, puede asignarles un perfil. El perfil contiene la configuración de administración específica que quiere aplicar a los dispositivos.

En [Choose how to enroll iOS devices in Intune](choose-ios-enrollment-method.md) (Selección del método para inscribir dispositivos iOS en Intune), se describen otros métodos de inscripción de dispositivos iOS).

**Adición de números de serie de Apple Configurator a Intune**

1. Cree una lista de valores separados por comas (.csv), con dos columnas, sin un encabezado. Agregue el identificador IMEI en la columna izquierda y los detalles en la columna derecha. El número máximo actual de filas de la lista es 500. En un editor de texto, la lista .csv tiene este aspecto:

    F7TLWCLBX196,detalles de dispositivo</br>
    DLXQPCWVGHMJ,detalles de dispositivo

2. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

3.  En la hoja de Intune, elija **Inscribir dispositivos** y luego elija **Inscripción de Apple**.

4. En **Administrar la configuración de inscripción de Apple Configurator**, seleccione **Números de serie de Apple Configurator**.

5. En la hoja **Números de serie de Apple Configurator**, seleccione **Agregar**.

6. En la hoja **Agregar números de serie**, seleccione un perfil para aplicar a los números de serie que se van a importar. Si va a importar un archivo con nuevos detalles que sobrescribirán los existentes, seleccione Sobrescribir detalles de identificadores existentes para que los nuevos detalles sustituyan a los existentes.

7. Desplácese hasta el archivo .csv de números de serie y seleccione **Agregar**.

## <a name="assign-a-profile-to-specific-serial-numbers"></a>Asignación de un perfil específico a números de serie

Intune permite asignar perfiles de dos sitios diferentes en el portal de Azure. Puede usar los pasos siguientes o puede asignar perfiles de la hoja Perfiles de inscripción de Apple Configurator, que es donde se crea el perfil (consulte [Enroll iOS devices with Apple Configurator by using Setup Assistant](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md) (Inscripción de dispositivos iOS con Apple Configurator mediante el Asistente de configuración). Puede usar los pasos siguientes para asignar el perfil solo si ya lo ha creado.

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

2. En la hoja de Intune, elija **Inscribir dispositivos** y luego elija **Inscripción de Apple**.

3. En la hoja **Números de serie de Apple Configurator**, seleccione los números de serie a los que quiere asignar un perfil y luego seleccione **Asignar perfil**.

4. En la hoja **Asignar perfil**, seleccione el perfil que quiere asignar y luego seleccione **Asignar**.

## <a name="delete-serial-numbers"></a>Eliminación de números de serie
Puede eliminar los números de serie que haya importado anteriormente. Solo se pueden eliminar números de serie si primero se ha anulado la inscripción del dispositivo. Después de quitar un número de serie, no puede usar Apple Configurator mediante el Asistente de configuración a menos que vuelva a agregar el número de serie.

## <a name="view-the-state-of-a-device"></a>Visualización del estado de un dispositivo
Los números de serie del dispositivo pueden tener dos estados:

- Inscrito: el dispositivo está inscrito y se ha conectado al servicio Intune.
- Sin contacto: el dispositivo nunca se ha conectado al servicio Intune.
- Restablecimiento pendiente: el dispositivo está inscrito, pero se ha realizado un cambio (por ejemplo, la configuración de inscripción o el perfil DEP aplicado han cambiado). Si cambia el perfil DEP de un dispositivo, los cambios no se aplican hasta que se anula la inscripción del dispositivo y luego se inscribe de nuevo.

**Visualización del estado de un número de serie**

En la hoja **Números de serie de Apple Configurator**, seleccione el número de serie cuyo estado quiere ver y mire bajo el elemento **Estado**.

