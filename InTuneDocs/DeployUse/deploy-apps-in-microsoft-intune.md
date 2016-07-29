---
title: "Implementación de aplicaciones | Microsoft Intune"
description: "Use la información de este tema como ayuda para implementar aplicaciones con Microsoft Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b42019e-73da-4538-a496-212f11d5bf9b
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6716a3d1fb53dc3de0189f637d5664d0a2023d05
ms.openlocfilehash: f3a8492532f01c576b1abf3c3228ba99dbd0d547

---
# Deploy apps in Microsoft Intune (Implementar aplicaciones en Microsoft Intune)

Use la información de este tema como ayuda para implementar aplicaciones con Microsoft Intune.


## Implementar una aplicación
En este procedimiento, implementará la aplicación en los grupos de dispositivos o usuarios seleccionados.

### Para implementar una aplicación

1. En la [consola de administrador de Microsoft Intune](https://manage.microsoft.com), haga clic en **Aplicaciones** &gt; **Aplicaciones** para ver la lista de aplicaciones que administra.

2.  Seleccione la aplicación que quiere implementar y haga clic en **Administrar la implementación**.

3.  En primer lugar, en el cuadro de diálogo *&lt;nombre de la aplicación&gt;*, en la página **Seleccionar grupos**, seleccione los grupos de usuarios o dispositivos en los que quiere implementar la aplicación.

4.  En la página **Acción de implementación**, configure lo siguiente:

    - **Aprobación:** elija una de las siguientes opciones para la implementación:
        - **Requerida** (instalación obligatoria)
        - **Disponible** (los usuarios la instalan desde el portal de empresa a petición)
        - **No aplicable** (la aplicación no se instala o no se muestra en el portal de empresa)
        - **Desinstalar** (la aplicación se desinstalará de los dispositivos de destino).
    - **Fecha límite:** en el caso de las instalaciones requeridas, elija cuándo se implementará la aplicación. Puede elegir entre los valores predefinidos, o bien seleccionar **Personalizado** para configurar su propia fecha límite.

5. Si la aplicación que va a implementar se puede configurar mediante una directiva de administración de aplicaciones móviles, se abrirá la página **Administración de aplicaciones móviles**. En esta página, seleccione la directiva de administración de aplicaciones móviles que desea asociar a esta aplicación.

    [Vea qué aplicaciones de Microsoft son compatibles con las directivas de administración de aplicaciones móviles.](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)

6. Si la aplicación que va a implementar es compatible con perfiles de VPN de Intune, se mostrará la página **Perfil de VPN**. En esta página, puede elegir asociar aplicaciones iOS con un perfil de VPN que haya implementado. La conexión VPN se abrirá automáticamente cuando se inicie la aplicación. Para disponer de un perfil de VPN, debe tener habilitada la configuración de perfil **VPN por aplicación**.
 Para obtener más información sobre cómo configurar perfiles de VPN, incluida la compatibilidad para asociar perfiles con aplicaciones, vea [Ayudar a los usuarios a conectarse a su trabajo con perfiles de VPN con Microsoft Intune](vpn-connections-in-microsoft-intune.md).

## Ejemplo

En este ejemplo ha implementado la aplicación como **Disponible** en un dispositivo iOS.
La aplicación se mostrará en el portal de empresa en el dispositivo de los usuarios, desde donde pueden instalarla. Por ejemplo, en esta captura de pantalla, se implementó la aplicación Bing para iOS usando el tipo de instalación **Vínculo externo** con un icono personalizado y se seleccionó la opción **Mostrar esta aplicación como destacada y resaltarla en el portal de empresa**.  
![Aplicación disponible para iOS](./media/available-install-on-iOS.png)

Si implementó la aplicación como **Requerida** en un dispositivo iOS, el usuario recibirá una notificación en la que se le informará de que la aplicación está preparada para la instalación. Por ejemplo, en esta captura de pantalla, se implementó la aplicación Carpetas de trabajo para iOS usando el tipo de instalación **Aplicación iOS administrada de la App Store**.  
![Aplicación requerida para Android](./media/iOS-Required-install.PNG)

## Pasos siguientes

Después de implementar una aplicación, probablemente le interese supervisar su progreso. Para obtener más información, vea [Monitor apps in Microsoft Intune](monitor-apps-in-microsoft-intune.md) (Supervisar aplicaciones en Microsoft Intune).



<!--HONumber=Jul16_HO4-->


