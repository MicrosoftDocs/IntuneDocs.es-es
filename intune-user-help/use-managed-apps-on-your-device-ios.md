---
title: Usar aplicaciones administradas en el dispositivo iOS | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/09/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3232c5c1-cb9f-45ca-806f-7e74eeb3533e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 35d77c9aa739096f36f4dbf4b75a4186e55a3381
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55835070"
---
# <a name="use-managed-apps-on-your-ios-device"></a>Usar aplicaciones administradas en el dispositivo iOS

Las aplicaciones administradas son aplicaciones que el equipo de soporte técnico de su empresa puede configurar para ayudar a proteger los datos de la empresa a los que se puede obtener acceso en esa aplicación. Al acceder a los datos de la empresa en una aplicación administrada en el dispositivo iOS, es posible que observe que funciona de una forma un poco diferente a la esperada. Por ejemplo, es posible que no pueda copiar y pegar los datos protegidos de la compañía o no pueda guardar dichos datos en determinadas ubicaciones.

Las distintas aplicaciones administradas también pueden trabajar juntas en el dispositivo para que pueda realizar las tareas diarias, a la vez que mantiene los datos corporativos protegidos. Por ejemplo, si abre un archivo de la empresa en una aplicación administrada y se requiere otra aplicación administrada para ver ese archivo, la aplicación administrada que le permite ver el archivo se abre automáticamente. Si una aplicación requerida no está disponible, ciertas operaciones, como la apertura de un documento o el acceso a un vínculo web desde dentro de un documento administrado, pueden no estar disponibles.

Cuando accede a datos de la empresa en una aplicación administrada, verá un mensaje como el siguiente, que le permite saber que la aplicación que está abriendo está administrada.

![managed-apps-message-ios](./media/managed-apps-message.png)

## <a name="how-do-i-get-managed-apps"></a>¿Cómo se pueden obtener aplicaciones administradas?  
Las aplicaciones administradas se obtienen de dos maneras distintas:

-   Cuando el dispositivo está inscrito en Microsoft Intune, puede instalar la aplicación desde la aplicación Portal de empresa o un sitio web del Portal de empresa, o bien el equipo de soporte técnico de su empresa puede instalarla en el dispositivo. Para más información sobre la inscripción, consulte [Inscribir un dispositivo iOS en Intune](enroll-your-device-in-intune-ios.md) o [Inscribir un dispositivo macOS en Intune](enroll-your-device-in-intune-macos.md).

-   Instale una aplicación desde App Store y después inicie sesión con la cuenta de usuario corporativo que administra Intune.

Es posible que el equipo de soporte técnico de su empresa a veces compre varias licencias de una aplicación que instale. Si aparece un mensaje donde se le pide aceptar el contrato de Programas de Compras por Volumen de Apple, es normal y puede aceptarlo. Si no lo hace, no podrá instalar la aplicación.

## <a name="available-apps"></a>Aplicaciones disponibles   
 Una organización selecciona las aplicaciones que resultan útiles y adecuadas para los usuarios en el ámbito laboral o académico. Estas aplicaciones son las únicas que se encuentran en el Portal de empresa.   

 Las aplicaciones también están disponibles para los usuarios según el tipo de dispositivo. Por ejemplo, si un usuario usa la aplicación Portal de empresa para iOS, tiene acceso a aplicaciones de iOS, pero no de Android.   

## <a name="request-an-app-for-work-or-school"></a>Solicitud de una aplicación para el ámbito laboral o académico   
 Si necesita una aplicación, pero no la ve en el Portal de empresa, puede solicitarla. Vea los detalles de contacto del **departamento de soporte técnico** en la pestaña **Soporte técnico** de la aplicación Portal de empresa. La misma información de contacto aparece en el [sitio web de Portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).   
 

## <a name="what-can-my-company-support-manage-in-an-app"></a>¿Qué puede administrar el equipo de soporte técnico de mi empresa en una aplicación?  
Estos son algunos ejemplos de opciones que el equipo de soporte técnico de su empresa puede administrar en una aplicación y que pueden afectar a las interacciones con los datos de la empresa en el dispositivo:

-   Acceso a sitios Web específicos

-   Transferencias de datos entre las aplicaciones

-   Almacenamiento de archivos

-   Operaciones de copiado y pegado

-   Requisitos de acceso PIN

-   El inicio de sesión con credenciales corporativas

-   La capacidad de realizar una copia de seguridad en la nube

-   La capacidad de realizar capturas de pantalla

-   Requisitos de cifrado de datos

Para más información sobre las aplicaciones administradas en el dispositivo, póngase en contacto con el equipo de soporte técnico de su empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
