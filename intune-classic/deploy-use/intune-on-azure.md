---
title: Consideraciones al administrar dispositivos Windows con Intune en Azure
description: "Consideraciones al usar Intune en Azure para administrar los dispositivos Windows de la organización."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 11/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f4018f505626b05dc84be509ca1e42cefff94b90
ms.sourcegitcommit: dc2595bec05206a826cd10cb834bf6043145c917
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/14/2017
---
# <a name="intune-on-azure-console-and-legacy-intune-pc-client"></a>Consola de Intune en Azure y cliente de equipo de Intune heredado

Recientemente, Intune migró a una arquitectura de servicios de aplicación SaaS basada en Azure. Azure ofrece importantes mejoras en términos de escala, capacidad y rendimiento. Esta transición también ofrece mejores experiencias de administrador de Intune y flujos de trabajo optimizados en Azure Portal. 

Considere estos puntos cuando use Intune en Azure para administrar los dispositivos Windows de la organización:

## <a name="legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>Las características del cliente de equipo heredado solo están disponibles en la consola Silverlight

Los flujos de trabajo de administración del cliente de equipo de Intune usan la [consola de administración de Intune basada en Silverlight](https://manage.microsoft.com/), lo que tiene estas consecuencias:

- Para todas las tareas de administración que no están agrupadas con el cliente de equipo de Intune, debe usar la consola Silverlight.
- Cuando administre los grupos, debe usar el [portal de Intune en Azure](https://portal.azure.com/). Este requisito existe porque ahora Intune usa grupos de Azure AD en lugar de los grupos de Intune heredados. 

Debido al cambio a los grupos de Azure AD, el filtrado "basado en grupo" de las vistas del panel de la consola de Silverlight cambió levemente. Para filtrar en la interfaz de usuario actualizada de Silverlight, siga estos pasos:

1. Seleccione una vista.
2. En el cuadro **Filtros**, escriba el nombre del grupo por el que desea filtrar y presione Entrar. Con esto se filtrará la vista de lista de los dispositivos de ese grupo determinado.

   ![](media/intune_on_azure/image01.png)

## <a name="manage-windows-10-devices-by-using-mdm"></a>Administración de dispositivos Windows 10 mediante MDM

Se recomienda que use la [administración de dispositivos móviles (MDM) para administrar los dispositivos Windows 10](https://docs.microsoft.com/intune/device-restrictions-windows-10) en lugar de usar el cliente de equipo de Intune heredado. La capacidad de administrar Windows 10 mediante MDM está disponible en el portal Intune en Azure. Windows 10 MDM proporciona muchas funcionalidades de administración y seguridad nuevas que no están disponibles a través del cliente de equipo de Intune heredado.

## <a name="continue-to-manage-windows-7-by-using-intune-pc-client"></a>Continuación de la administración de Windows 7 mediante el cliente de equipo de Intune

En el caso de Windows 7, que no se puede administrar mediante MDM, se seguirán admitiendo las funcionalidades existentes del cliente de equipo de Intune solo en la consola de Silverlight. Considere la posibilidad de migrar a la administración de MDM cuando actualice a Windows 10.

## <a name="mdm-capabilities"></a>Funcionalidades de MDM

Para una comparación detallada entre las funcionalidades del cliente de equipo y las de MDM, consulte [Comparación de la administración de equipos con Windows como dispositivos móviles o equipos](https://docs.microsoft.com/intune-classic/deploy-use/pc-management-comparison). Las actualizaciones de MDM seguirán incorporando nuevas funcionalidades de administración a los dispositivos de Windows 10 inscritos en MDM, incluida la evaluación de opciones para aplicaciones de Win 32. Consulte las [novedades](https://docs.microsoft.com/intune/whats-new) para conocer las adiciones de las versiones más recientes al servicio.

## <a name="switch-from-pc-client-to-mdm"></a>Cambio desde el cliente de equipo a MDM

Para pasar de administrar los dispositivos Windows 10 con el cliente de equipo de Intune a administrarlos con MDM, siga estos pasos:

1. En la consola de Silverlight, realice una **eliminación de datos selectiva** para cancelar la inscripción del dispositivo desde el cliente de equipo.
  ![](media/intune_on_azure/image02.png)
2. Vuelva a inscribir el dispositivo con [MDM (o con combinación de Azure AD)](https://docs.microsoft.com/intune/windows-enroll). 

## <a name="next-steps"></a>Pasos siguientes
[Inscribir dispositivos Windows](https://docs.microsoft.com/intune/windows-enroll)

 
