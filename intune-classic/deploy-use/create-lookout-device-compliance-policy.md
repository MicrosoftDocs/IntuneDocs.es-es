---
title: Habilitación de la regla de protección de dispositivos
description: Habilite la regla de protección contra amenazas móviles en la directiva de cumplimiento normativo del dispositivo.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 03/21/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c951692d-6538-46c0-a9f0-d607ded189ae
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 8f19318256dc4480207097d2f4ab393b799e207a
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="create-lookout-device-compliance-policy-in-intune"></a>Creación de la directiva de cumplimiento de dispositivos de Lookout en Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune con Mobile Threat Defense de Lookout le permite detectar amenazas en dispositivos móviles y evaluar el riesgo en esos dispositivos. Puede crear una regla de directivas de cumplimiento que evalúe el riesgo para determinar si el dispositivo es compatible. Luego puede usar la directiva de acceso condicional para bloquear el acceso a servicios en función del cumplimiento del dispositivo.

Requisitos previos de la directiva de cumplimiento con Mobile Threat Defense de Lookout :

- [Configurar la suscripción de Mobile Threat Defense de Lookout](setup-your-lookout-mtd-subscription.md)
- [Habilitar la conexión de Lookout MTP en la consola de administración de Intune](enable-lookout-mtd-connection.md)
- [Configurar e implementar las aplicaciones de trabajo de Lookout](configure-deploy-lookout-for-work-app.md)

Como parte de la configuración de Mobile Threat Defense de Lookout, en la [consola de Lookout](https://aad.lookout.com) se crea una directiva que clasifica las distintas amenazas como alta, media y baja. En la directiva de cumplimiento normativo de Intune establecerá el máximo nivel de amenaza permitido.

1. En la [consola de administrador de Intune](https://manage.microsoft.com), vaya a la página **Directivas de cumplimiento**. Puede usar una directiva de cumplimiento existente o crear una nueva. Vaya a **Estado de dispositivos** y habilite **Protección contra amenazas de dispositivo**.
  ![captura de pantalla que muestra el valor de la regla de protección contra amenazas de dispositivo](../media/mtp/mtp-compliance-policy-rule.png)

2. Seleccione el **Máximo nivel de amenaza permitido**:
  * **Ninguno (protegido)**: es el más seguro.  El dispositivo no puede tener ninguna amenaza presente y aún puede tener acceso a los recursos de la empresa.  Si se encuentra alguna amenaza, el dispositivo se clasificará como no conforme.  
  * **Bajo**: el dispositivo se evalúa como compatible si solo hay amenazas de nivel bajo. Cualquier valor por encima coloca al dispositivo en un estado de no conformidad.
  * **Medio**: el dispositivo se evalúa como compatible si las amenazas que se encuentran en él son de nivel bajo o medio. Si se detectan amenazas de nivel alto, se determinará que el dispositivo no es conforme.
  * **Alto**: esta opción es la menos segura. Esto permite todos los niveles de amenaza y usa Lookout Mobile Threat Protection solo con fines informativos.

![captura de pantalla que muestra la opción de nivel de amenaza del valor de la regla de protección contra amenazas de dispositivo](../media/mtp/mtp-compliance-policy-setting.png)

Si crea directivas de acceso condicional para Office 365 u otros servicios, se efectuará esta evaluación de cumplimiento y se bloqueará el acceso de los dispositivos no conformes a dichos servicios hasta que se resuelva la amenaza.

## <a name="monitor-device-threats"></a>Supervisión de las amenazas del dispositivo
Para ver el estado de cumplimiento de un dispositivo, vaya a la [consola de administrador de Intune](https://manage.microsoft.com) y vea **Todos los dispositivos**.

![captura de pantalla de la página de dispositivos de la consola de administración de Intune que muestra el estado de cumplimiento normativo de un dispositivo](../media/mtp/mtp-device-status-intune-console.png)

## <a name="next-steps"></a>Pasos siguientes
* Crear una directiva de acceso condicional
  * [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  * [Exchange local](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  * [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  * [Skype Empresarial Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
  * [Dynamics CRM](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)
