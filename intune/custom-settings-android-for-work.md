---
title: Configuración personalizada de perfil de Intune para perfiles de trabajo Android
titlesuffix: Microsoft Intune
description: Aprenda a crear configuraciones de perfil personalizadas de Microsoft Intune para dispositivos de perfil de trabajo Android.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/12/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 109c50acf194598017aa507a0979ad3b9298de9e
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905298"
---
# <a name="create-intune-custom-profile-settings-for-android-work-profile-devices"></a>Creación de una configuración personalizada de perfil de Intune para dispositivos de perfil de trabajo Android

Use la directiva de configuración personalizada del perfil de trabajo Android de Intune para asignar las opciones de configuración de OMA-URI, que sirven para controlar características en dispositivos de perfil de trabajo Android. Se trata de una configuración estándar que muchos fabricantes de dispositivos móviles usan para controlar las características del dispositivo.

Esta funcionalidad está pensada para que se puedan asignar las opciones de configuración de Android que no se pueden definir con directivas de Intune. Intune admite un número limitado de directivas personalizadas de Android en este momento. Vea los ejemplos de este artículo para averiguar qué directivas puede configurar.

## <a name="create-a-custom-profile"></a>Creación de un perfil personalizado

1. Siga las instrucciones que se indican en [Configuración personalizada de dispositivos](custom-settings-configure.md) para comenzar. En **Plataforma**, elija **Android Enterprise** y en **Tipo de perfil** elija **Personalizado**.
2. En la hoja **Configuración OMA-URI personalizada**, elija **Agregar** para agregar un nuevo valor.
3. En la hoja **Agregar fila**, configure lo siguiente:
    - **Name**: escriba un nombre único para la configuración personalizada del perfil de trabajo Android que permita identificarla en Azure Portal.
    - **Description**: proporcione una descripción que ofrezca una visión general de la directiva personalizada de Android y otra información relevante que le ayude a encontrarla.
    - **OMA-URI**: escriba la configuración OMA-URI para la que quiere suministrar un valor.
    - **Tipo de datos**: seleccione el tipo de datos en el que especificará este valor OMA-URI. Elija entre **Cadena**, **Cadena (archivo XML)**, **Fecha y hora**, **Entero**, **Punto flotante**, **Booleano** o **Base64 (archivo)**.
    - **Valor**: especifique el valor que desea asociar con el OMA-URI que especificó anteriormente. El método que usa para suministrar este valor variará según el tipo de datos que seleccionó. Por ejemplo, si eligió **Fecha y hora**, seleccionará el valor de un selector de fecha.
4. Cuando termine, elija Aceptar para volver a **Configuración OMA-URI personalizada** y, luego, agregue más configuraciones, o bien elija **Crear** para crear el perfil personalizado.


## <a name="example"></a>Ejemplo

En este ejemplo, creará un perfil personalizado que se puede usar para restringir si se permiten las acciones de copiar y pegar entre aplicaciones profesionales y aplicaciones personales en dispositivos de perfil de trabajo Android.

1. Use el procedimiento que se indica en este artículo para crear un perfil personalizado para dispositivos de perfil de trabajo Android con los valores siguientes:
    - **Name**: escriba "Bloqueo de la función de copiar y pegar" o un texto de su preferencia.
    - **Description**: escriba "Bloqueo de la función de copiar y pegar entre aplicaciones profesionales y personales" o un texto de su preferencia.
    - **OMA-URI**: escriba **./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste**.
    - **Data type**: seleccione **Booleano** para indicar que el valor de este OMA-URI es **True** o **False**.
    - **Value**: seleccione **True**.
2. Debe terminar con una configuración similar a esta imagen.
![Bloquee la función de copiar y pegar para un perfil de trabajo Android](./media/custom-policy-afw-copy-paste.png).
3. Ahora, cuando asigne este perfil personalizado a dispositivos de perfil de trabajo Android que administre, la función de copiar y pegar estará bloqueada entre aplicaciones de los perfiles profesional y personal.