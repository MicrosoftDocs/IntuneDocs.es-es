---
title: "Protección de aplicaciones LOB en dispositivos no inscritos | Microsoft Intune"
description: "En este tema se describe cómo puede preparar sus aplicaciones personalizadas de línea de negocios de manera que sea posible aplicar directivas de administración de aplicaciones móviles que le ayuden a evitar la pérdida de datos."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00219467-a62e-43b6-954b-3084f54c45ba
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9bf5764d1e1bd73fd62e5033b2309fc8d5a912e4
ms.openlocfilehash: bc5d1b429157e6a6b24f4eb319be50b635466317


---

# <a name="protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune"></a>Proteger aplicaciones y datos de línea de negocio en dispositivos no inscritos en Microsoft Intune

Las directivas de administración de aplicaciones móviles (MAM) ayudan a proteger los datos de la empresa al restringir las acciones que podrían provocar una pérdida de datos de la empresa e imponer requisitos de acceso a datos, como el PIN de aplicación. Para aplicar directivas de MAM a aplicaciones iOS y Android de línea de negocio, primero tiene que ajustar la aplicación con la herramienta de ajuste de aplicaciones de Microsoft Intune.  El ajuste de aplicaciones es el proceso de aplicar una capa de administración a una aplicación móvil sin necesidad de realizar cambios en la aplicación subyacente.  Una vez que la aplicación está ajustada, puede aplicarle directivas MAM y distribuirla a los usuarios finales.  

En este tema se explican los pasos necesarios para aplicar directivas MAM a las aplicaciones a las que se accede en **dispositivos no administrados propiedad de los empleados** y en dispositivos administrados por una **solución de administración de dispositivos móviles (MDM) de terceros**.  Para preparar las aplicaciones de línea de negocio que se ejecutan en **dispositivos inscritos en MDM de Intune**, consulte [Decidir cómo preparar las aplicaciones para la administración de aplicaciones móviles mediante Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md).


##  <a name="step-1-prepare-the-app"></a>Paso 1: preparar la aplicación
Antes de aplicar directivas MAM a una aplicación, tiene que ajustarla con la herramienta de ajuste de aplicaciones de Microsoft Intune.  Para obtener instrucciones sobre la descarga y el uso de la herramienta de ajuste de aplicaciones, consulte las páginas siguientes:

- [Preparar aplicaciones iOS para la administración de aplicaciones móviles con la Herramienta de ajuste de aplicaciones de Intune](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)
- [Preparar aplicaciones Android para la administración de aplicaciones móviles con la Herramienta de ajuste de aplicaciones de Intune](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)

>[!IMPORTANT]  
>Esta versión de la herramienta de ajuste de aplicaciones, que es compatible con dispositivos no inscritos en Intune, es compatible con iOS y está en vista previa pública para Android. Puede descargar la herramienta desde [este repositorio de GitHub](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) para iOS y desde [este repositorio de GitHub](https://github.com/msintuneappsdk/intune-app-wrapper-android-preview) para Android.

## <a name="step-2-add-the-app"></a>Paso 2: agregar la aplicación

Para asociar la aplicación de línea de negocio a las directivas MAM, debe agregar los detalles de la aplicación a la suscripción o al inquilino de Intune mediante estos pasos:

1. En el [portal de Azure](https://portal.azure.com/), vaya a **Administración de aplicaciones móviles de Intune > Configuración** y seleccione **Aplicaciones de línea de negocio**.

  ![Captura de pantalla de la hoja de configuración con la opción de línea de negocio](../media/mam-azure-portal-lob-on-settings.png)

2. En la hoja **Aplicaciones de línea de negocio**, seleccione **Agregar una aplicación personalizada**.

  ![Captura de pantalla de la hoja de aplicaciones de línea de negocio con el botón Agregar aplicación personalizada en la parte superior](../media/mam-azure-portal-add-lob-app-action.png)
3.  Proporcione un nombre para la aplicación, el identificador de la agrupación de trabajos en el campo Identificador de la aplicación y la plataforma (iOS o Android).

  ![Captura de pantalla de la hoja Agregar una aplicación personalizada ](../media/mam-azure-portal-add-app-details.png) Este paso ayuda a crear una descripción exclusiva de la aplicación.  La aplicación también se mostrará en la lista Aplicaciones de destino de una directiva MAM del inquilino, como se explica en el paso siguiente.

## <a name="step-3-apply-mam-policies"></a>Paso 3: aplicar directivas MAM
Una vez que los metadatos de la aplicación se han cargado en el servicio, la aplicación se mostrará en la lista de aplicaciones.  Ya puede [crear una nueva directiva o una directiva existente](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) y aplicarla a la aplicación de línea de negocio que agregó en el paso 2.

>[!IMPORTANT]
>Debe dirigir la directiva de MAM a los usuarios que van a usar la aplicación ajustada.  Los usuarios que no tengan esta directiva implementada no podrán usar la aplicación.


  ![Captura de pantalla de la hoja Aplicaciones de destino con la nueva aplicación de línea de negocio](../media/mam-azure-portal-lob-on-targeted-app-list.png)
## <a name="step-4-distribute-the-app"></a>Paso 4: distribuir la aplicación
Puede implementar aplicaciones para los usuarios finales de las maneras siguientes:
* En el caso de los dispositivos inscritos en una solución MDM de terceros, puede distribuir las aplicaciones a través de la solución MDM.
* En el caso de los dispositivos no administrados por ninguna solución MDM, necesitará una solución personalizada. Los usuarios finales deben descargar e instalar la aplicación en sus dispositivos.

## <a name="changing-the-metadata"></a>Modificación de los metadatos
Si necesita cambiar detalles de la aplicación como su nombre o el identificador de la agrupación de trabajos, tiene que [quitar la aplicación](#remove-apps) y [agregarla](#step-2-add-the-app) con los nuevos metadatos.

##  <a name="remove-apps"></a>Quitar aplicaciones
Puede quitar una aplicación de línea de negocio de la lista de aplicaciones.  Con esto se quitará la aplicación de la lista y también la asociación con las directivas MAM, pero no se quitará ni desinstalará la aplicación del dispositivo del usuario final.  

1.  En el [portal de Azure](https://portal.azure.com/), vaya a **Administración de aplicaciones móviles de Intune > Configuración**.  En la hoja **Configuración**, seleccione **Línea de negocio** para abrir la lista de aplicaciones existentes.  
2.  Seleccione la aplicación que quiere quitar y, luego, el menú **(...) contexto**.

  ![Captura de pantalla de la hoja de aplicaciones de línea de negocio con los puntos suspensivos](../media/mam-azure-portal-lob-context-menu.png)
3.  Seleccione **Eliminar aplicación** para eliminar la aplicación.

  ![Captura de pantalla de la hoja de línea de negocio con la opción de eliminar aplicación](../media/mam-azure-portal-delete-app.png)

  Esto quitará las aplicaciones de la lista de aplicaciones de línea de negocio y de la lista Aplicaciones de destino de la directiva MAM.



<!--HONumber=Nov16_HO2-->


