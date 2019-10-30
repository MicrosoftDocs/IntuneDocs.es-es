---
title: Creación de una directiva de protección de aplicaciones de Mobile Threat Defense (MTD) con Intune
titleSuffix: Microsoft Intune
description: Cree una directiva de protección de aplicaciones de Mobile Threat Defense (MTD) con Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 15d986bc5017a44571c6194f9c6b53167b671349
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2019
ms.locfileid: "72794425"
---
# <a name="create-mobile-threat-defense-app-protection-policy-with-intune"></a>Creación de una directiva de protección de aplicaciones de Mobile Threat Defense con Intune

> [!NOTE] 
> Este artículo sirve para cualquiera de los partners de Mobile Threat Defense que admiten directivas de protección de aplicaciones: Better Mobile (Android), Zimperium (iOS), Lookout for Work (Android/iOS).

Intune con MTD le ayuda a detectar amenazas y a evaluar el riesgo en dispositivos móviles. Puede crear una directiva de protección de aplicaciones de Intune que evalúe el riesgo para determinar si el dispositivo puede acceder a los datos corporativos o no. 

## <a name="before-you-begin"></a>Antes de comenzar

Como parte de la configuración de MTD, en la consola del partner de MTD se crea una directiva que clasifica las distintas amenazas como alta, media y baja. Ahora, lo que hay que hacer es establecer el nivel de Mobile Threat Defense en la directiva de protección de aplicaciones de Intune.

Requisitos previos de la directiva de protección de aplicaciones con MTD:

- Configurar la integración de MTD con Intune Sin esta integración, la directiva de protección de aplicaciones de MTD no tendrá ningún efecto.

## <a name="to-create-an-mtd-app-protection-policy"></a>Para crear una directiva de protección de aplicaciones de MTD

1. Vaya a [Azure Portal](https://portal.azure.com/) e inicie sesión con sus credenciales de Intune.

2. En el **panel de Azure**, elija **Todos los servicios** en el menú de la izquierda y, luego, escriba **Intune** en el filtro del cuadro de texto.

3. Pulse **Intune** y se abrirá el **panel de Intune**.

4. En el **panel de Intune**, seleccione **Aplicaciones cliente** y, luego, seleccione **Directivas de protección de aplicaciones** en la sección **Administrar**.

5. Elija **Crear directiva**, escriba un **Nombre** y una **Descripción** y seleccione la **Plataforma**. 

6. En el panel **Inicio condicional**, en la tabla **Condiciones de dispositivo**, elija el nivel de Mobile Threat de la lista desplegable en **Máximo nivel de amenaza del dispositivo permitido**.

    a.  **Protegido**: este nivel es el más seguro. El dispositivo no puede tener ninguna amenaza presente y aún puede tener acceso a los recursos de la empresa. Si se encuentra alguna amenaza, el dispositivo se clasificará como no conforme.

    b.  **Baja**: el dispositivo se evalúa como compatible si solo hay amenazas de nivel bajo. Cualquier valor por encima coloca al dispositivo en un estado de no conformidad.

    c.  **Media**: el dispositivo se evalúa como compatible si las amenazas que se encuentran en él son de nivel bajo o medio. Si se detectan amenazas de nivel alto, se determinará que el dispositivo no es compatible.

    d.  **Alta**: este nivel es el menos seguro. Permite todos los niveles de amenaza y usa Mobile Threat Defense solo con fines informativos. Los dispositivos deben tener activada la aplicación MTD con esta configuración.

7. Haga clic en **Guardar** dos veces y, después, seleccione **Crear**.

## <a name="to-assign-an-mtd-app-protection-policy"></a>Para asignar una directiva de protección de aplicaciones de MTD

Para asignar una directiva de cumplimiento de dispositivos a los usuarios, seleccione una directiva que haya configurado anteriormente. Las directivas existentes se pueden encontrar en el panel **Device compliance - Policies** (Conformidad de dispositivos: directivas).

1. Seleccione la directiva que quiere asignar a los usuarios y elija **Asignaciones**. Con esta acción se abre el panel donde puede seleccionar **Grupos de seguridad de Azure Active Directory** y asignarlos a la directiva.

2. Elija **Seleccionar grupos para incluir** para que se abra la página que muestra los grupos de seguridad de Azure AD. Al elegir **Seleccionar**, la directiva se implementa para los usuarios.

> [!NOTE] 
> Ya ha aplicado la directiva a los usuarios. Los dispositivos que utilicen los usuarios a los que se ha aplicado la directiva se evaluarán para determinar su acceso a los datos corporativos en las aplicaciones de destino a través de la protección de aplicaciones de Intune.

## <a name="next-steps"></a>Pasos siguientes  

- Más información sobre [Mobile Threat Defense ](~/protect/mobile-threat-defense.md) en Microsoft Intune.
