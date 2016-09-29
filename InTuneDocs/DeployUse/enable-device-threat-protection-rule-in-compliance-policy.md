---
title: "Habilitar la regla de protección de dispositivos en la directiva de cumplimiento normativo | Microsoft Intune"
description: "Habilite la regla de protección contra amenazas móviles en la directiva de cumplimiento normativo del dispositivo."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: c951692d-6538-46c0-a9f0-d607ded189ae
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9c2ffb5fe497d56d8250fe3dec7db606c2067a1c
ms.openlocfilehash: 761372b2c8b81699bc2584ab1ef8d0f9d523abe9


---

# Habilitar la regla de protección contra amenazas móviles en la directiva de cumplimiento normativo
Intune con protección contra amenazas móviles de Lookout ofrece la posibilidad de detectar amenazas móviles y realizar una evaluación de riesgos en el dispositivo.  
La regla de directivas de cumplimiento normativo permite usar esta evaluación de riesgos para determinar si el dispositivo es conforme con la directiva. Luego puede usar la directiva de acceso condicional para permitir o bloquear a Exchange, SharePoint y otros servicios en función del cumplimiento del dispositivo.

Para que la detección de amenazas de Lookout MTP influya en la directiva de cumplimiento normativo del dispositivo:

1.  La regla **Protección contra amenazas de dispositivo** debe estar habilitada en la directiva de cumplimiento normativo.

2.  La página **Estado de Lookout** de la consola de administración de Intune debe mostrar **Activo**. Vea el tema [Enable Lookout MTP connection in Intune (Habilitar la conexión de Lookout MTP en Intune)](enable-lookout-mtp-connection-in-intune.md) para obtener más detalles e instrucciones sobre cómo activar la integración de Lookout.


## Configurar la regla de protección contra amenazas de dispositivo

Antes de crear la regla de protección contra amenazas de dispositivo en la directiva de cumplimiento normativo, se recomienda [configurar la suscripción con Lookout MTP](set-up-your-subscription-with-lookout-mtp.md), [habilitar la conexión de Lookout en Intune](enable-lookout-mtp-connection-in-intune.md) y [configurar la aplicación Lookout for Work](configure-and-deploy-lookout-for-work-apps.md). La regla de cumplimiento normativo solo se aplica una vez completada la instalación.

Para habilitar la regla de protección contra amenazas de dispositivo, puede usar una directiva de cumplimiento normativo existente o crear una nueva.

Como parte de la instalación de Lookout MTP, en la [consola de Lookout MTP](https://aad.lookout.com) se crea una directiva que clasifica las distintas amenazas en los niveles alto, medio y bajo. En la directiva de cumplimiento normativo de Intune usará el nivel de amenaza para establecer el nivel de amenaza permitido máximo.

En la consola de administración de Intune, en la página de directivas de cumplimiento normativo, vaya a **Estado de dispositivos** y habilite la regla **Protección contra amenazas de dispositivo** mediante la opción de alternancia. Luego, seleccione el nivel de amenaza máximo permitido, que es uno de los siguientes:
* **Ninguno (protegido)**: es la más segura.  Esto significa que el dispositivo no puede tener ninguna amenaza.  Si se detecta cualquier nivel de amenaza en el dispositivo, se evaluará como no conforme.  
* **Bajo**: el dispositivo se evalúa como conforme si solo hay amenazas de nivel bajo. Cualquier valor por encima coloca al dispositivo en un estado de no conformidad.
* **Medio**: el dispositivo se evalúa como conforme si las amenazas presentes en él son de nivel bajo o medio. Si se detecta que el dispositivo tiene amenazas de nivel alto, se determina como no conforme.
* **Alto**: esta opción es la menos segura. Básicamente, permite todos los niveles de amenaza y quizás solo sea útil si usa esta solución únicamente para fines informativos.

![captura de pantalla que muestra el valor de la regla de protección contra amenazas de dispositivo ](../media/mtp/mtp-compliance-policy-rule.png)

![captura de pantalla que muestra la opción de nivel de amenaza del valor de la regla de protección contra amenazas de dispositivo](../media/mtp/mtp-compliance-policy-setting.png)

Si crea directivas de acceso condicional para O365 y otros servicios, la evaluación de cumplimiento normativo anterior se toma en consideración y se bloquea el acceso a los dispositivos no conformes hasta que se resuelve la amenaza.

Puede ver el estado de cumplimiento normativo de un dispositivo en la página de dispositivos de la consola de administración de Intune.

![captura de pantalla de la página de dispositivos de la consola de administración de Intune que muestra el estado de cumplimiento normativo de un dispositivo](../media/mtp/mtp-device-status-intune-console.png)

## Pasos siguientes
* Crear una directiva de acceso condicional
  * [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  * [Exchange local](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  * [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  * [Skype Empresarial Online](restrict-access-to-skype-for-business-online-with-microsoft-intune,md)
  * [Dynamics CRM](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)



<!--HONumber=Sep16_HO2-->


