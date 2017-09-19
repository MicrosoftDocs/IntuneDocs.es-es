---
title: "Implementación de aplicaciones"
description: "Use la información de este tema como ayuda para implementar aplicaciones con Microsoft Intune."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b42019e-73da-4538-a496-212f11d5bf9b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: fdabe983c4306bd7deba7cb600ff0bdb1c27e4a8
ms.sourcegitcommit: cf7f7e7c9e9cde5b030cf5fae26a5e8f4d269b0d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/14/2017
---
# <a name="deploy-apps-in-microsoft-intune"></a>Deploy apps in Microsoft Intune (Implementar aplicaciones en Microsoft Intune)

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Use la información de este tema como ayuda para implementar aplicaciones con Microsoft Intune.


## <a name="deploy-an-app"></a>Implementar una aplicación
En este procedimiento, se implementa una aplicación en los grupos de dispositivos o usuarios seleccionados.

### <a name="to-deploy-an-app"></a>Para implementar una aplicación

1. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), haga clic en **Aplicaciones** &gt; **Aplicaciones** para ver la lista de aplicaciones que administra.

2.  Seleccione la aplicación que quiere implementar y, después, haga clic en **Administrar la implementación**.

3.  En el cuadro de diálogo *&lt;Nombre de la aplicación&gt;*, en la página **Seleccionar grupos**, seleccione los grupos de usuarios o dispositivos en los que quiere implementar la aplicación.

4.  En la página **Acción de implementación**, configure lo siguiente:

    - **Aprobación:** elija una de las siguientes opciones para la implementación:
        - **Requerida** (instalación obligatoria)
        - **Disponible** (los usuarios la instalan desde el portal de empresa a petición)
        - **No aplicable** (la aplicación no se instala o no se muestra en el portal de empresa)
        - **Desinstalar** (la aplicación se desinstala de los dispositivos de destino)
    - **Fecha límite:** en el caso de las instalaciones requeridas, elija cuándo se debe implementar la aplicación. Puede elegir entre los valores predefinidos o seleccionar **Personalizado** para configurar su propia fecha límite.

5. Si la aplicación que va a implementar se puede configurar mediante una directiva de administración de aplicaciones móviles, se abrirá la página **Administración de aplicaciones móviles**. En esta página, seleccione la directiva de administración de aplicaciones móviles que quiere asociar a esta aplicación.

    [Vea qué aplicaciones de Microsoft son compatibles con las directivas de administración de aplicaciones móviles.](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx)

6. Si la aplicación que va a implementar es compatible con perfiles de VPN de Intune, se mostrará la página **Perfil de VPN**. En esta página, puede elegir asociar aplicaciones iOS a un perfil de VPN que haya implementado. La conexión VPN se abre automáticamente al iniciar la aplicación. Para disponer de un perfil de VPN, debe tener habilitada la configuración de perfil **VPN por aplicación**.
 Para obtener información sobre cómo configurar perfiles de VPN, incluida información sobre cómo asociar los perfiles con las aplicaciones, consulte [Conexiones VPN en Microsoft Intune](vpn-connections-in-microsoft-intune.md).

<!---
>[!TIP]
>If an end user previously installed an iOS app and you now deploy it with a deployment action of **Available**, Intune will automatically begin to manage that app with no further action required by you, or the end-user.
--->

## <a name="example"></a>Ejemplo

En este ejemplo ha implementado la aplicación como **Disponible** en un dispositivo iOS.
La aplicación se muestra en los dispositivos de los usuarios en Portal de empresa, y los usuarios pueden instalarla desde allí.

Por ejemplo, en esta captura de pantalla, la aplicación Bing para iOS se ha implementado mediante el tipo de instalación **Vínculo externo** con un icono personalizado. Se ha seleccionado la opción **Mostrar esta aplicación como destacada y resaltarla en Portal de empresa**.  
![Aplicación disponible para iOS](./media/available-install-on-iOS.png)

Si implementó la aplicación como **Requerida** en un dispositivo iOS, el usuario recibirá una notificación en la que se le informará de que la aplicación está preparada para la instalación. Por ejemplo, en esta captura de pantalla, la aplicación Carpetas de trabajo para iOS se ha implementado mediante el tipo de instalación **Aplicación iOS administrada de la App Store**.  
![Aplicación requerida para iOS](./media/iOS-Required-install.PNG)

## <a name="next-steps"></a>Pasos siguientes

Después de implementar una aplicación, probablemente le interese supervisar su progreso. Para obtener más información, vea [Monitor apps in Microsoft Intune](monitor-apps-in-microsoft-intune.md) (Supervisar aplicaciones en Microsoft Intune).
