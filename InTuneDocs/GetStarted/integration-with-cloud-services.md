---
title: "Integración de Intune con productos y servicios en la nube de Microsoft | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 49675811-08a3-408f-810b-89552ff404bd
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: e58b295bf89e200c7c986902c9b4408d23e67c64


---

# Integración de Intune con productos y servicios en la nube de Microsoft

Antes de configurar [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)], repase este tema y los requisitos que aparecen en [What to know before you start Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md) (Información necesaria antes de iniciar Microsoft Intune).
##Integración con otros servicios en la nube de Microsoft


[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] comparte una base común con otros servicios de nube de Microsoft. Cuando se utiliza la misma cuenta para suscribirse a varios servicios de nube, dichos servicios utilizan la misma infraestructura de Microsoft Azure AD y son inquilinos de Azure AD. Azure AD proporciona las principales capacidades de administración de identidades y directorios para servicios de nube de Microsoft.

Obtenga más información sobre cómo [administrar Azure AD](http://technet.microsoft.com/library/hh967611.aspx) en la biblioteca de TechNet.

## Integración con otros productos de Microsoft
Puede usar [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] como un servicio en la nube independiente o como un servicio en la nube que está integrado con otros productos. Actualmente, solo [!INCLUDE[cmshort](../includes/cmshort_md.md)] se puede integrarse directamente con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

La decisión de integrar [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] con [!INCLUDE[cmshort](../includes/cmshort_md.md)] es una opción permanente que requiere el establecimiento de la entidad de administración de dispositivos móviles desde la consola de [!INCLUDE[cmshort](../includes/cmshort_md.md)] y no desde el [!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)]. Una vez se ha establecido la entidad de administración de dispositivos móviles, no se puede cambiar o revertir esta configuración.

Cuando se usa [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] con [!INCLUDE[cmshort](../includes/cmshort_md.md)], no se usa la [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] para administrar [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] y se emplea la consola de [!INCLUDE[cmshort](../includes/cmshort_md.md)] en su lugar. [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Sigue usando su almacenamiento en la nube en Azure para hospedar software que se implementa en dispositivos que se administran con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

Para más información, consulte [Administrar dispositivos móviles con Configuration Manager y Microsoft Intune](http://msdn.microsoft.com/library/2c6bd0e5-d436-41c8-bf38-30152d76be10) en la documentación de [!INCLUDE[cm5short](../includes/cm5short_md.md)] SP1.

### Consulte también
[What to know before you start Microsoft Intune (Información necesaria antes de iniciar Microsoft Intune)](what-to-know-before-you-start-microsoft-intune.md)


<!--HONumber=Jun16_HO4-->


