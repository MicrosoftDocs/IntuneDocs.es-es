---
title: 'Configuración de Optimización de distribución para Windows 10 en Microsoft Intune: Azure | Microsoft Docs'
description: Configure cómo los dispositivos Windows 10 usan la opción Optimización de distribución que administra con Intune. En Intune, cree un perfil de configuración de dispositivos para instalar actualizaciones desde Internet. Consulte también cómo reemplazar los círculos de actualizaciones existentes con un perfil de Optimización de distribución.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: kerimh
ms.openlocfilehash: 4190d84fda46e4be3cdc4c4f7bfe4ac8a1852ebc
ms.sourcegitcommit: 78ae22b1a7cb221648fc7346db751269d9c898b1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66373946"
---
# <a name="delivery-optimization-settings-in-microsoft-intune"></a>Configuración de la opción Optimización de distribución en Microsoft Intune

Con Intune, se puede usar la opción Optimización de distribución para los dispositivos Windows 10 con el fin de reducir el consumo de ancho de banda cuando estos dispositivos descarguen aplicaciones y actualizaciones. La opción Optimización de distribución se configura como parte de los perfiles de configuración del dispositivo.  

En este artículo se describe cómo configurar las opciones de optimización de distribución como parte de un perfil de configuración de dispositivo. Después de crear un perfil, este se asigna o implementa en sus dispositivos Windows 10. 

Para obtener una lista de las opciones de configuración de Optimización de distribución que admite Intune, consulte [Delivery optimization settings for Intune](delivery-optimization-settings.md) (Configuración de la opción Optimización de distribución de Intune).  

Para obtener más información sobre la opción Optimización de distribución en Windows 10, consulte [Actualizaciones de optimización de Windows 10 de distribución](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) en la documentación de Windows.  


> [!NOTE]
> **Actualizaciones de software: los círculos de actualizaciones de Windows 10** los reemplaza la configuración **Optimización de distribución**. Los círculos de actualizaciones existentes se pueden cambiar para usar la configuración **Optimización de distribución**. [Traslado de los anillos de actualizaciones existentes a la optimización de distribución](#move-existing-update-rings-to-delivery-optimization) (en este artículo) 
## <a name="create-the-profile"></a>Creación del perfil

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.

3. Escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre descriptivo para el nuevo perfil.
    - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
    - **Plataforma**: seleccione la plataforma:  

        - **Windows 10 y versiones posteriores**

    - **Tipo de perfil**: seleccione **Optimización de distribución**.
    - **Configuración**: configure los valores que definen cómo quiere que se descarguen las actualizaciones y aplicaciones. Para obtener más información sobre las opciones de configuración disponibles, consulte [Delivery optimization settings for Intune](delivery-optimization-settings.md) (Configuración de la opción Optimización de distribución de Intune).

4. Cuando termine, seleccione **Aceptar** > **Crear** para guardar los cambios.

El perfil se crea y se muestra en la lista. Después, [asigne el perfil](device-profile-assign.md) y [supervise su estado](device-profile-monitor.md).

## <a name="move-existing-update-rings-to-delivery-optimization"></a>Traslado de los anillos de actualizaciones existentes a la optimización de distribución

La configuración **Optimización de distribución** reemplaza las **actualizaciones de Windows 10 mediante anillos de actualización de software**. Los círculos de actualizaciones existentes se pueden cambiar fácilmente para usar la configuración **Optimización de distribución**. Para mantener la misma configuración al crear un perfil de optimización de distribución, use la misma opción *Modo de descarga de optimización de entrega* y, luego, establezca la misma configuración que ya use. Sin embargo, se pueden volver a configurar las opciones de optimización de distribución para aprovechar la gran variedad de opciones de configuración adicionales que puede administrar el perfil de Optimización de distribución.

1. Cree un perfil de configuración de optimización de distribución:

    1. En Intune, seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
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
1. Asigne este perfil nuevo a los mismos dispositivos y usuarios que el círculo de actualizaciones de software existente. [Asignar el perfil](device-profile-assign.md) muestra los pasos.

3. Quite la configuración del círculo de actualizaciones de software existente:
    1. En Intune, vaya a **Actualizaciones de software** > Círculos de actualizaciones de Windows 10.
    2. En la lista, seleccione el círculo de actualizaciones.
    3. En la configuración, establezca **Modo de descarga de optimización de distribución** en **No configurado**.
    4. **Aceptar** > **Guardar** los cambios.

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md) el estado.  
Consulte la [configuración de la optimización de distribución](delivery-optimization-settings.md) para Intune.
