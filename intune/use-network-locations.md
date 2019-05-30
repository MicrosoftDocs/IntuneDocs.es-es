---
title: 'Enlazar dispositivos Android por ubicación de red en Microsoft Intune: Azure | Microsoft Docs'
description: Cree o configure las ubicaciones de red en Microsoft Intune para dispositivos Android. Puede marcar dispositivos como no conformes en función de la ubicación de red del dispositivo. Si el dispositivo está fuera de la ubicación de red, puede bloquear el acceso a los recursos de la empresa.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/21/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ayesham
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ddc58aed6e7a1efaecd8b7e7cf51a39e43d14e58
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66044343"
---
# <a name="use-locations-network-fence-in-intune"></a>Usar ubicaciones (límite de red) en Intune

Es preferible bloquear el acceso a una red corporativa si un dispositivo deja una ubicación. La característica **Ubicaciones** de Intune proporciona estas funciones. 

Puede crear una directiva de cumplimiento basada en la ubicación de red, también conocida como límite de red. Con esta directiva se garantiza que los dispositivos deben estar conectados a una red de trabajo para ser conformes. Esta directiva se puede usar junto con directivas de acceso condicional para que los dispositivos tengan acceso a recursos de trabajo *solo* cuando el dispositivo esté conectado a la red de trabajo. Cuando el dispositivo no está conectado a la red de trabajo, pasa a ser no conforme y pierde el acceso a los recursos de trabajo.

Considere el siguiente escenario:

En su centro de fabricación, algunos empleados usan dispositivos Android. Un empleado saca el dispositivo Android fuera de las instalaciones o la planta. Para evitar un acceso no autorizado, puede hacer esto:

1. Crear una ubicación con un intervalo de IPv4 denominado **nave de fábrica**.
2. Crear una directiva de cumplimiento que requiera estos dispositivos se conecten a la red corporativa y asígneles esta directiva.
3. Si el dispositivo sale fuera de la nave de la fábrica, se considera que el dispositivo no es conforme y no tiene acceso a los recursos corporativos.

Además, puede agregar [acciones de no cumplimiento](#configure-the-actions-for-noncompliance). Cuando el dispositivo vuelva a entrar en las instalaciones y en la ubicación de red, podrá volver a acceder a los recursos corporativos.

## <a name="prerequisites"></a>Requisitos previos

Para crear una directiva de cumplimiento basadas en ubicación:

- Cree una ubicación de red como rangos de redes IPV4 para el servidor de puerta de enlace, el servidor DHCP y/o el servidor DNS al que se conectan los dispositivos.
- Cree la directiva de cumplimiento que usa estas ubicaciones y define la acción realizada cuando el dispositivo ya no está conectado a la ubicación de red.
- Solo para dispositivos Android 6.0 y versiones posteriores, con la aplicación Portal de empresa actualizada.

## <a name="create-a-location"></a>Crear una ubicación

1. En Intune, seleccione **Conformidad de dispositivos** > **Ubicaciones** > **Crear**.

2. Escriba las propiedades siguientes:  

   - Obligatorio. Escriba un **Nombre** para la ubicación, como **Planta de fabricación** o **Nave 44-Protegida**.
   - Opcional. Escriba un **Rango IPv4** con notación CIDR (Enrutamiento entre dominios sin clase), como `aaa.bbb.ccc.ddd/n`.
   - Opcional. Escriba la dirección de **Puerta de enlace IPv4**, como `aaa.bbb.ccc.ddd`.
   - Opcional. Escriba la dirección de **Servidor DHCP IPv4**, como `aaa.bbb.ccc.ddd`.
   - Opcional. Escriba una lista de direcciones de **Servidores DNS IPv4**. Esta opción usa **coincidencia de subconjuntos**. Si los servidores DNS IPv4 en el dispositivo son subconjuntos de los valores definidos, se considera que el dispositivo está dentro de los límites. Asegúrese de especificar una dirección por línea, como:  
     `aaa.bbb.ccc.ddd`  
     `aaa.bbb.ccc.ddd`
   - Opcional. Escriba una lista de **Sufijos DNS**. Esta opción usa **coincidencia de subconjuntos**. Si los sufijos DNS en el dispositivo son subconjuntos de los valores definidos, se considera que el dispositivo está dentro de los límites. Asegúrese de escribir un nombre de dominio en cada línea, como:  
     `contoso.com`  
     `contoso.org`

3. Guarde los cambios mediante **Guardar**.

## <a name="create-the-location-compliance-policy"></a>Crear la directiva de cumplimiento de ubicación

Cuando cree la directiva de cumplimiento, seleccione **Android** para la **Plataforma**. En **Ubicaciones**, puede elegir una o varias de las ubicaciones de red que ha agregado. Estas ubicaciones forman parte de los límites de red que se van a crear para los dispositivos.

En el apartado [Ubicaciones](compliance-policy-create-android.md#locations) encontrará instrucciones para crear la directiva de cumplimiento basada en la ubicación de red.

## <a name="configure-the-actions-for-noncompliance"></a>Configurar las acciones de no conformidad

Después de crear la directiva de cumplimiento, se aplica la acción predeterminada para no conformidad en el dispositivo. Puede agregar más acciones. Por ejemplo, agregue una acción que envíe un correo electrónico al usuario cuando el dispositivo ya no sea conforme con las ubicaciones.

En [Automatización del correo electrónico y adición de acciones para dispositivos no compatibles: Intune](actions-for-noncompliance.md) se proporcionan algunas indicaciones.

## <a name="company-portal-app"></a>Aplicación de portal de empresa

Cuando el dispositivo está conectado a sus ubicaciones, el dispositivo se muestra como que es conforme en la aplicación Portal de empresa. Cuando el dispositivo no está conectado a una de las ubicaciones, el dispositivo se muestra como no conforme.

## <a name="next-steps"></a>Pasos siguientes
[Supervisión de las directivas de cumplimiento de dispositivos de Intune](compliance-policy-monitor.md)  
[Introducción a las directivas de cumplimiento de dispositivos de Intune](device-compliance-get-started.md)
