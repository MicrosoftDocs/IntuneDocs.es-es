---
title: "¿Qué es el acceso condicional?"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda a definir las condiciones que deben cumplir usuarios y dispositivos para acceder a los recursos de la empresa en la versión preliminar de Microsoft Intune Azure."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 8ab6d782460a857a0901abd9bd567365ee2e3f70
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="what-is-conditional-access"></a>¿Qué es el acceso condicional?


[!INCLUDE[azure_preview](./includes/azure_preview.md)]


En este tema se describe el acceso condicional que se aplica a Enterprise Mobility + Security y, seguidamente, las funcionalidades de acceso condicional en Intune.

El acceso condicional de Enterprise Mobility + Security (EMS) emplea el poder de Azure Active Directory Premium y Microsoft Intune para proporcionar el control que necesita para proteger los datos de empresa, al tiempo que ofrece a los empleados una experiencia que les permite realizar su trabajo desde cualquier dispositivo.

Con el acceso condicional, puede definir condiciones que limiten el acceso a los datos corporativos en función de la ubicación, el estado del dispositivo y del usuario y el carácter confidencial de la aplicación.

Desde la perspectiva del dispositivo, Intune y Azure Active Directory trabajan juntos para garantizar que solo los dispositivos administrados y compatibles pueden acceder al correo electrónico y los servicios de Office 365. Por ejemplo, puede establecer una directiva en Azure Active Directory que permita que solo los equipos que están unidos a un dominio o los dispositivos móviles que están inscritos en una aplicación de administración de dispositivos móviles, como Intune, tengan la posibilidad de acceder a servicios de Office 365. Puede usar Intune para establecer un perfil de cumplimiento de dispositivo que evalúe su estado de cumplimiento. El estado de cumplimiento se notifica a Azure Active Directory para que lo use en la aplicación de la directiva en Azure Active Directory cuando el usuario intenta acceder a los recursos de empresa. Para más información sobre el cumplimiento de dispositivos en Intune, consulte [¿Qué es el cumplimiento de los dispositivos?](device-compliance.md)

El acceso condicional para aplicaciones de nube como Exchange Online puede configurarse mediante Azure Active Directory. Para más información, consulte este [artículo](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

## <a name="on-premises-conditional-access-in-intune"></a>Acceso condicional local en Intune

El acceso condicional en Intune se puede usar para permitir o bloquear el acceso al **entorno local de Exchange** en función de la administración y la inscripción de dispositivos.

La configuración de un perfil de cumplimiento de dispositivo se usa para evaluar la conformidad del dispositivo. El acceso condicional usa la evaluación para permitir o bloquear el acceso al entorno local de Exchange. Cuando el acceso condicional se utiliza en combinación con un perfil de cumplimiento de dispositivo, solo los dispositivos compatibles pueden acceder al entorno local de Exchange. Puede configurar opciones avanzadas en el acceso condicional para un mayor control, como, permitir o bloquear determinadas plataformas, o bloquear inmediatamente dispositivos que ya no se administren con Intune.

El perfil de cumplimiento de dispositivo y el acceso condicional se asignan al usuario. Se compruebe el cumplimiento de cualquier dispositivo que use el usuario para acceder al entorno local de Exchange. Tenga en cuenta que el usuario que usa el dispositivo debe tener asignado un perfil de cumplimiento para que se pueda evaluar el cumplimiento del dispositivo. Si no se implementa ninguna directiva de cumplimiento en el usuario, el dispositivo se considera conforme y no se aplicarán restricciones de acceso.

Cuando los dispositivos no cumplen las condiciones, se indica al usuario final el proceso para registrar el dispositivo y corregir el problema que impide que el dispositivo sea compatible.

## <a name="next-steps"></a>Pasos siguientes

[Creación de una directiva de acceso condicional para el entorno local de Exchange](conditional-access-exchange-create.md)

[Configuración del acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

