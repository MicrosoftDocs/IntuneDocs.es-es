---
title: Administrar scripts de PowerShell en Intune para dispositivos Windows 10
titlesuffix: Azure portal
description: "Obtenga información sobre cómo cargar scripts de PowerShell en Intune para ejecutarse en dispositivos Windows 10."
keywords: 
author: dougeby
manager: angrobe
ms.date: 11/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 237d6d090d0aae7f9a0853839b72d55618f4607e
ms.sourcegitcommit: af958afce3070a3044aafea490c8afc55301d9df
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="manage-powershell-scripts-in-intune-for-windows-10-devices"></a>Administrar scripts de PowerShell en Intune para dispositivos Windows 10
La extensión de administración de Intune permite cargar los scripts de PowerShell en Intune para ejecutarse en dispositivos Windows 10. La extensión de administración complementa las capacidades de administración de dispositivos móviles (MDM) de Windows 10 y facilita la transición a una administración moderna.

## <a name="moving-to-modern-management"></a>Transición hacia una administración moderna
La informática de usuario final está experimentando una transformación digital. La TI clásica y tradicional se centra en una plataforma de dispositivo único, en dispositivos propiedad de la empresa, en usuarios que trabajan desde la oficina y en diversos procesos de TI manuales y reactivos. Por el contrario, el área de trabajo moderna engloba varias plataformas de dispositivos tanto de particulares como de empresa, permite a los usuarios trabajar desde cualquier lugar, y sus procesos de TI son proactivos y automatizados. 

Los servicios MDM, como Microsoft Intune, pueden administrar dispositivos Windows 10 mediante el protocolo MDM. El cliente de administración integrado de Windows 10 es capaz de comunicarse con Intune para realizar tareas de administración de la empresa. Este cliente le ayuda en su transición hacia una administración moderna en dispositivos Windows 10. Sin embargo, hay ciertas capacidades que actualmente no está disponible en la MDM de Windows 10 y que puede necesitar, como pueden ser una configuración avanzada de los dispositivos, la competencia para solucionar problemas y la administración de aplicaciones de Win32 heredadas. Para estas capacidades, puede ejecutar al cliente de software de Intune en sus dispositivos Windows 10. Como resultado, no es posible usar las nuevas funciones que proporciona la administración de dispositivos móviles de Windows 10. [Compare las diferencias entre el cliente de software de Intune y Windows 10 MDM](https://docs.microsoft.com/intune-classic/deploy-use/pc-management-comparison).

La extensión de administración de Intune complementa las capacidades de administración de dispositivos móviles que Windows 10 incluye de fábrica. Puede crear scripts de PowerShell que proporcionen las capacidades que necesita para que se ejecuten en los dispositivos Windows 10. Por ejemplo, puede crear un script de PowerShell que instale una aplicación de Win32 heredada en sus dispositivos Windows 10, cargue el script en Intune, asigne el script a un grupo de Azure Active Directory (AD) y ejecute el script en dispositivos Windows 10. A continuación, puede supervisar de principio a fin el estado de ejecución del script en dispositivos Windows 10.

## <a name="prerequisites"></a>Requisitos previos
La extensión de administración de Intune tiene los siguientes requisitos previos:
- Los dispositivos deben estar unidos a Azure AD
- Los dispositivos deben ejecutar Windows 10, versión 1607 o posterior

## <a name="create-a-powershell-script-policy"></a>Crear una directiva de un script de PowerShell 
1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Configuración del dispositivo**.
4. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Scripts de PowerShell**.
5. En la hoja **Scripts de PowerShell**, elija **Agregar script**.
6. En la hoja **Agregar PowerShell Script**, escriba un **Nombre** y una **Descripción** para el script de PowerShell.
7. Para **Ubicación del script**, busque el script de PowerShell. El script debe ser inferior a 10 KB (ASCII) o 5 KB (Unicode).
8. Seleccione **Configurar** y luego elija si desea ejecutar el script con las credenciales del usuario en el dispositivo (**Sí**) o en el contexto del sistema (**No**). De forma predeterminada, el script se ejecuta en el contexto del sistema. Seleccione **Sí** a menos que el script se deba ejecutar en el contexto del sistema. 
  ![Hoja Agregar script de PowerShell](./media/mgmt-extension-add-script.png)
9. Elija si el script debe estar firmado por un editor de confianza (**Sí**). De forma predeterminada, no se exige que el script esté firmado. 
10. Haga clic en **Aceptar** y después en **Crear** para guardar el script.

## <a name="assign-a-powershell-script-policy"></a>Asignar una directiva de script de PowerShell
1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Configuración del dispositivo**.
4. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Scripts de PowerShell**.
5. En la hoja **Scripts de PowerShell**, seleccione el script que quiere asignar y luego elija **Administrar** > **Asignaciones**.
  ![Hoja Agregar script de PowerShell](./media/mgmt-extension-assignments.png)
 
6. Elija **Seleccionar grupos** para obtener una lista de los grupos de Azure AD disponibles. 
7. Seleccione los grupos y después haga clic en **Seleccionar** para asignar la directiva a los grupos seleccionados.

La extensión de administración de Intune se sincroniza con Intune una vez cada hora. Después de asignar la directiva a los grupos de Azure AD, se ejecuta el script de PowerShell y se notifican los resultados de la ejecución. 
 
## <a name="monitor-run-status-for-powershell-scripts"></a>Supervisar el estado de ejecución de scripts de PowerShell
Puede supervisar el estado de ejecución de scripts de PowerShell para usuarios y dispositivos en Azure Portal.
1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Configuración del dispositivo**.
4. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Scripts de PowerShell**.
5. En la hoja **Scripts de PowerShell**, seleccione el script que quiere supervisar y, a continuación, elija **Monitor** y uno de los siguientes informes:
   - **Estado del dispositivo**
   - **Estado del usuario**