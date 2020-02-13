---
title: 'Configuración de Optimización de distribución para Windows 10 en Microsoft Intune: Azure | Microsoft Docs'
description: Configure cómo los dispositivos Windows 10 usan la opción Optimización de distribución que administra con Intune. En Intune, cree un perfil de configuración de dispositivos para instalar actualizaciones desde Internet. Consulte también cómo reemplazar los círculos de actualizaciones existentes con un perfil de Optimización de distribución.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/10/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: kerimh
ms.openlocfilehash: 9fb4aab6b02c6ad6a5d2f18ca9d15beafc12d58a
ms.sourcegitcommit: e1ff157f692983b49bdd6e20cc9d0f93c3b3733c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124816"
---
# <a name="delivery-optimization-settings-in-microsoft-intune"></a>Configuración de la opción Optimización de distribución en Microsoft Intune

Con Intune, use la opción Optimización de distribución para los dispositivos Windows 10 con el fin de reducir el consumo de ancho de banda cuando estos dispositivos descarguen aplicaciones y actualizaciones. Configure la optimización de distribución como parte de los perfiles de configuración del dispositivo.  

En este artículo se describe cómo configurar las opciones de optimización de distribución como parte de un perfil de configuración de dispositivo. Después de crear un perfil, este se asigna o implementa en sus dispositivos Windows 10. 

Para ver una lista de las opciones de optimización de distribución que admite Intune, consulte [Configuración de optimización de entrega para Intune](../delivery-optimization-settings.md).  

Para obtener más información sobre la opción Optimización de distribución en Windows 10, consulte [Actualizaciones de optimización de Windows 10 de distribución](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) en la documentación de Windows.  

## <a name="create-the-profile"></a>Creación del perfil

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.

3. Escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre descriptivo para el nuevo perfil.
    - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
    - **Plataforma**: seleccione **Windows 10 y versiones posteriores**.
    - **Tipo de perfil**: seleccione **Optimización de distribución**.

4. Elija **Configuración** > **Configurar** y defina cómo quiere que se descarguen las actualizaciones y las aplicaciones. Para obtener más información sobre las opciones de configuración disponibles, consulte [Delivery optimization settings for Intune](../delivery-optimization-settings.md) (Configuración de la opción Optimización de distribución de Intune).

5. Cuando termine, seleccione **Aceptar** > **Crear** para guardar los cambios.

El perfil se crea y se muestra en la lista. Después, [asigne el perfil](device-profile-assign.md) y [supervise su estado](device-profile-monitor.md).

<!-- ## Move existing update rings to delivery optimization

**Delivery optimization** settings replace **Software updates – Windows 10 Update Rings**. Your existing update rings can be easily changed to use the **Delivery optimization** settings. To maintain the same settings when you create a delivery optimization profile, use the same *Delivery optimization download mode* and then set the same settings as you already use. However, you can choose to reconfigure delivery optimization settings to take advantage of the full range of addition settings that the Delivery Optimization profile can manage. 
-->

## <a name="remove-delivery-optimization-from-windows-10-update-rings"></a>Eliminación de la optimización de entrega de los anillos de actualización de Windows 10

Anteriormente, la optimización de entrega se configuraba como parte de los anillos de actualización de software. A partir de febrero de 2019, la configuración de la optimización de entrega se configura como parte de un perfil de configuración de dispositivo de optimización de entrega, que incluye opciones adicionales que afectan más que a la entrega de actualizaciones de software a los dispositivos. Si todavía no lo ha hecho, establezca *No configurado* para quitar la configuración de optimización de entrega de los anillos de actualización y, a continuación, use un perfil de optimización de distribución para administrar el mayor número de opciones disponibles.

1. Cree un perfil de configuración de dispositivos de optimización de distribución:

    1. En el Centro de administración del Administrador de puntos de conexión de Microsoft, seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.
    2. Escriba las propiedades siguientes:

        - **Nombre**: escriba un nombre descriptivo para el nuevo perfil.
        - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
        - **Plataforma**: seleccione **Windows 10 y versiones posteriores**.
        - **Tipo de perfil**: seleccione **Optimización de distribución**.
        - **Configuración**: para **Modo de descarga de Optimización de entrega**, elija el mismo modo que usa el anillo de actualización de software existente, a menos que quiera cambiar la configuración que se aplica a los dispositivos. Las opciones son:
            - **No configurado**.
            - **HTTP solo, sin emparejamiento**
            - **HTTP combinado con el emparejamiento que se encuentra en la misma NAT**
            - **HTTP combinado con el emparejamiento de un grupo privado**
            - **HTTP combinado con emparejamiento de Internet**
            - **Modo de descarga sencillo sin emparejamiento**
            - **Modo de omisión**
    3. Configure las opciones adicionales que pueda querer administrar.

2. Asigne este perfil nuevo a los mismos dispositivos y usuarios que el círculo de actualizaciones de software existente. [Asignar el perfil](device-profile-assign.md) muestra los pasos.

3. Quite la configuración del círculo de actualizaciones de software existente:
    1. En el Centro de administración del Administrador de puntos de conexión de Microsoft, vaya a **Actualizaciones de software** > Anillos de actualización de Windows 10.
    2. En la lista, seleccione el círculo de actualizaciones.
    3. En la configuración, establezca **Modo de descarga de optimización de distribución** en **No configurado**.
    4. **Aceptar** > **Guardar** los cambios.

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md) el estado.  
Consulte la [configuración de la optimización de distribución](../delivery-optimization-settings.md) para Intune.
