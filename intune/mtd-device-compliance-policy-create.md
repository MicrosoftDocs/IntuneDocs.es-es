---
title: Creación de una directiva de cumplimiento de dispositivos MTD con Microsoft Intune
titleSuffix: Microsoft Intune
description: Cree una directiva de cumplimiento de dispositivo de Intune que utilice sus niveles de amenazas de partners MTD asociados para determinar si un dispositivo móvil puede tener acceso a recursos de la empresa.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5d12254f-ffab-4792-b19c-ab37f5e02f35
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d200c8d56dbbe60dd331081537154951f5e5591d
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66041553"
---
# <a name="create-mobile-threat-defense-mtd-device-compliance-policy-with-intune"></a>Creación de directiva de cumplimiento de dispositivos de Mobile Threat Defense (MTD) con Intune

> [!NOTE] 
> Este tema se aplica a todos los partners de Mobile Threat Defense.

Intune con MTD le ayuda a detectar amenazas y a evaluar el riesgo en dispositivos móviles. Puede crear una regla de directivas de cumplimiento de dispositivos de Intune que evalúe el riesgo para determinar si el dispositivo cumple con la directiva o no lo hace. Luego puede usar una [directiva de acceso condicional](create-conditional-access-intune.md) para bloquear el acceso a servicios en función del cumplimiento del dispositivo.

## <a name="before-you-begin"></a>Antes de comenzar

Como parte de la configuración de MTD, en la consola del partner de MTD se crea una directiva que clasifica las distintas amenazas como alta, media y baja. En la directiva de cumplimiento de dispositivos de Intune, ahora debe establecer el nivel de Mobile Threat Defense.

Requisitos previos de la directiva de cumplimiento de dispositivos con MTD:

-   Configuración de la integración de MTD con Intune

## <a name="to-create-an-mtd-device-compliance-policy"></a>Creación de una directiva de cumplimiento de dispositivos de MTD

1.  Vaya a [Azure Portal](https://portal.azure.com/) e inicie sesión con sus credenciales de Intune.

2.  En el **panel de Azure**, elija **Todos los servicios** en el menú de la izquierda y, luego, escriba **Intune** en el filtro del cuadro de texto.

3.  Pulse **Intune** y se abrirá el **panel de Intune**.

4. En el **panel de Intune**, seleccione **Cumplimiento de dispositivos** y, luego, seleccione **Directivas** en la sección **Administrar**.

5.  Pulse **Crear directiva**, escriba el **nombre** y la **descripción** de cumplimiento del dispositivo, seleccione la **Plataforma** y, después, seleccione **Configurar** en la sección **Configuración**.

6.  En el panel **Directiva de cumplimiento**, seleccione **Estado de dispositivos**.

7.  En el panel **Estado de dispositivos**, pulse el nivel de Mobile Threat en la lista desplegable en **Requerir que el dispositivo tenga el nivel de amenaza del dispositivo**.

    a.  **Protegido**: este nivel es el más seguro. El dispositivo no puede tener ninguna amenaza presente y aún puede tener acceso a los recursos de la empresa. Si se encuentra alguna amenaza, el dispositivo se clasificará como no conforme.

    b.  **Baja**: el dispositivo se evalúa como compatible si solo hay amenazas de nivel bajo. Cualquier valor por encima coloca al dispositivo en un estado de no conformidad.

    c.  **Media**: el dispositivo se evalúa como compatible si las amenazas que se encuentran en él son de nivel bajo o medio. Si se detectan amenazas de nivel alto, se determinará que el dispositivo no es compatible.

    d.  **Alta**: este nivel es el menos seguro. Permite todos los niveles de amenaza y usa Mobile Threat Defense solo con fines informativos. Los dispositivos deben tener activada la aplicación MTD con esta configuración.

8.  Haga clic en **Aceptar** dos veces, después seleccione **Crear**.

> [!IMPORTANT]
> Si crea directivas de acceso condicional para Office 365 u otros servicios, se efectuará esta evaluación de cumplimiento de dispositivo y se bloqueará el acceso de los dispositivos no conformes a los recursos corporativos hasta que se resuelva la amenaza en el dispositivo.

## <a name="to-assign-an-mtd-device-compliance-policy"></a>Asignación de una directiva de cumplimiento de dispositivos de MTD

Para asignar una directiva de cumplimiento de dispositivos a los usuarios, seleccione una directiva que haya configurado anteriormente. Las directivas existentes se pueden encontrar en el panel **Device compliance - Policies** (Conformidad de dispositivos: directivas).

1. Seleccione la directiva que quiere asignar a los usuarios y elija **Asignaciones**. Con esta acción se abre el panel donde puede seleccionar **Grupos de seguridad de Azure Active Directory** y asignarlos a la directiva.

2. Elija **Seleccionar grupos que incluir** para que se abra la página que muestra los grupos de seguridad de Azure AD.  Al elegir **Seleccionar** la directiva se implementa para los usuarios.

    > [!NOTE] 
    > Ya ha aplicado la directiva a los usuarios. Se evalúa el cumplimiento por parte de los dispositivos usados por los usuarios a los que se aplique la directiva.

## <a name="next-steps"></a>Pasos siguientes

- [Habilitar MTD con Intune](mtd-connector-enable.md)
