---
title: "Habilitar la regla de protección de dispositivos en la directiva de cumplimiento normativo | Microsoft Intune"
description: "Habilite la regla de protección contra amenazas móviles en la directiva de cumplimiento normativo del dispositivo."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c951692d-6538-46c0-a9f0-d607ded189ae
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9bf5764d1e1bd73fd62e5033b2309fc8d5a912e4
ms.openlocfilehash: ec287d49910a72c22122f45a01850bcbd3a7d203


---

# <a name="enable-device-threat-protection-rule-in-the-compliance-policy"></a>Habilitar la regla de protección contra amenazas móviles en la directiva de cumplimiento normativo
Intune con protección contra amenazas móviles de Lookout ofrece la posibilidad de detectar amenazas móviles y realizar una evaluación de riesgos en el dispositivo. Puede crear una regla de directivas de cumplimiento a fin de incluir la evaluación de riesgos para determinar si el dispositivo es conforme. Luego puede usar la directiva de acceso condicional para permitir o bloquear el acceso a Exchange, SharePoint y otros servicios en función del cumplimiento del dispositivo.

Para que la detección de amenazas de dispositivo de Lookout influya en la directiva de cumplimiento del dispositivo:

* La regla **Protección contra amenazas de dispositivo** debe estar habilitada en la directiva de cumplimiento normativo.

* La página **Estado de Lookout** de la **consola de administrador de Intune** debe mostrar **Activo**. Vea el tema [Enable Lookout MTP connection in Intune (Habilitar la conexión de Lookout MTP en Intune)](enable-lookout-mtp-connection-in-intune.md) para obtener más detalles e instrucciones sobre cómo activar la integración de Lookout.


Antes de crear la regla de protección contra amenazas de dispositivo en la directiva de cumplimiento, se recomienda [configurar la suscripción con la protección contra amenazas de dispositivo de Lookout](set-up-your-subscription-with-lookout-mtp.md), [habilitar la conexión de Lookout en Intune](enable-lookout-mtp-connection-in-intune.md) y [configurar la aplicación Lookout for Work](configure-and-deploy-lookout-for-work-apps.md). La regla de cumplimiento solo se aplica una vez completada la configuración.

Para habilitar la regla de protección contra amenazas de dispositivo, puede usar una directiva de cumplimiento normativo existente o crear una nueva.

Como parte de la configuración de la protección contra amenazas de dispositivo de Lookout, en la [consola de Lookout](https://aad.lookout.com) se crea una directiva que clasifica las distintas amenazas en los niveles alto, medio y bajo. En la directiva de cumplimiento normativo de Intune usará el nivel de amenaza para establecer el nivel de amenaza permitido máximo.

En la página **Directivas de cumplimiento** de la **consola de administrador de Intune**, vaya a **Estado de dispositivos** y habilite la regla **Protección contra amenazas de dispositivo** mediante la opción de alternancia. Luego, seleccione el nivel de amenaza máximo permitido, que es uno de los siguientes:
* **Ninguno (protegido)**: es la más segura.  Esto significa que el dispositivo no puede tener ninguna amenaza.  Si no se encuentra ningún nivel de amenaza, el dispositivo se evalúa como no conforme.  
* **Bajo:** el dispositivo se evalúa como conforme si solo hay amenazas de nivel bajo. Cualquier valor por encima coloca al dispositivo en un estado de no conformidad.
* **Medio:** el dispositivo se evalúa como conforme si las amenazas que se encuentran en él son de nivel bajo o medio. Si se detectan amenazas de nivel alto, se determina que el dispositivo no es conforme.
* **Alto**: esta opción es la menos segura. Básicamente, permite todos los niveles de amenaza y quizás solo sea útil si usa esta solución únicamente para fines informativos.

![captura de pantalla que muestra el valor de la regla de protección contra amenazas de dispositivo ](../media/mtp/mtp-compliance-policy-rule.png)

![captura de pantalla que muestra la opción de nivel de amenaza del valor de la regla de protección contra amenazas de dispositivo](../media/mtp/mtp-compliance-policy-setting.png)

Si crea directivas de acceso condicional para Office 365 y otros servicios, la evaluación de cumplimiento anterior se toma en consideración y se bloquea el acceso de los dispositivos no conformes a los recursos de la empresa hasta que se resuelva la amenaza.

Puede ver el estado de cumplimiento de un dispositivo en la página **Todos los dispositivos** de la **consola de administrador de Intune**.

![captura de pantalla de la página de dispositivos de la consola de administración de Intune que muestra el estado de cumplimiento normativo de un dispositivo](../media/mtp/mtp-device-status-intune-console.png)

## <a name="next-steps"></a>Pasos siguientes
* Crear una directiva de acceso condicional
  * [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  * [Exchange local](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  * [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  * [Skype Empresarial Online](restrict-access-to-skype-for-business-online-with-microsoft-intune,md)
  * [Dynamics CRM](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)



<!--HONumber=Nov16_HO2-->


