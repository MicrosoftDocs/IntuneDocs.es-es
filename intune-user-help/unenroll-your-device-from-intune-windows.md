---
title: Quitar el dispositivo Windows de Intune | Microsoft Docs
description: Describe cómo quitar un dispositivo Windows de Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 018bda65-7238-41f5-b92a-e5f67b7fe085
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 9f9051fb393c82031d581f7fec731a3b148cbf2e
ms.sourcegitcommit: 7f46e9990797bdfa669ccba2077721f1bc70c07e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/04/2018
---
# <a name="remove-your-windows-device-from-intune"></a>Quitar el dispositivo Windows de Intune

Si su dispositivo Windows está registrado en Intune, pero ya no quiere usarlo para acceder al correo electrónico, a las aplicaciones o a otros recursos del trabajo o la escuela, debe dejar de administrarlo. Una vez que quite el dispositivo de Intune, ya no podrá acceder a estos recursos. Para obtener más información sobre lo que ocurre cuando se deja de administrar un dispositivo, vea [¿Qué ocurre cuando se anula la inscripción de un dispositivo de Intune?](what-happens-if-you-unenroll-your-device-from-intune-windows.md)

## <a name="remove-your-windows-10-device"></a>Quitar un dispositivo con Windows 10

1.  Desde la lista de aplicaciones, pulse en la aplicación **Portal de empresa** .

2.  Inicie sesión con las credenciales de su trabajo o escuela.

3.  En **Mis dispositivos**, seleccione el dispositivo cuya inscripción desee anular.

4.  Pulse en **Quitar** &gt; **Quitar**.

## <a name="remove-your-windows-81-computer"></a>Quitar un equipo con Windows 8.1

1.  Vaya a **Configuración de PC** &gt; **Red** &gt; **Área de trabajo**.

2.  En **Workplace Join**, seleccione **Salir**.

3.  En **Activar la administración de dispositivos**, seleccione **Desactivar**.

4.  En la ventana emergente que se abre, seleccione **Desactivar**.

## <a name="remove-your-windows-phone-81-mobile-device"></a>Quitar un dispositivo móvil con Windows Phone 8.1

1.  Pulse en **Configuración** &gt; **Área de trabajo**.

2.  Pulse la cuenta de trabajo cuya inscripción quiere anular.

3.  Pulse en **Eliminar** en la parte inferior de la pantalla.

4.  En el cuadro de diálogo **Eliminar cuenta**, pulse en **Eliminar**.

## <a name="removing-your-personal-information-after-removing-the-company-portal"></a>Eliminar la información personal después de quitar el Portal de empresa

Hay dos tipos de datos que el Portal de empresa almacena en el dispositivo Windows:

-   **Registros de diagnóstico**: los datos estándar recopilados por Microsoft acerca de la actividad de la aplicación (por ejemplo, cuánto tiempo estuvo abierta la aplicación o si se ha bloqueado) se borran automáticamente cuando el dispositivo se quita del Portal de empresa.
-   **Caché de la aplicación**: almacenamiento de determinados archivos auxiliares necesarios para el funcionamiento de la aplicación, como iconos y valores de configuración.

Para eliminar por completo esta información, deben seguirse una serie de pasos.

### <a name="uninstall-the-company-portal"></a>Desinstalar el Portal de empresa  

La [desinstalación de la aplicación Portal de empresa](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs) quitará algunos de los datos de la aplicación almacenados en el dispositivo.  

### <a name="reset-the-company-portal"></a>Restablecer el Portal de empresa

Para restablecer el resto de los datos de la aplicación Portal de empresa, se puede restablecer la aplicación en Configuración. Abra **Configuración** > **Aplicaciones y características** > **Portal de empresa** > **Opciones avanzadas** > **Restablecer**.

¿Sigue necesitando ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://portal.manage.microsoft.com#HelpDeskDialog).