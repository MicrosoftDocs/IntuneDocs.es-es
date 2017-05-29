---
title: Retirar aplicaciones | Microsoft Docs
description: "Obtenga información sobre cómo retirar o desinstalar aplicaciones mediante Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6fbf0805-1144-4e08-bafd-4f181d932bf2
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 670e108fc4f672b4900f7cfb4e0127e16a377fa7
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="retire-apps-using-microsoft-intune"></a>Retirar aplicaciones mediante Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Para retirar una aplicación, simplemente desinstálela. Al implementar y administrar aplicaciones con Intune, el proceso de desinstalación de la aplicación es el mismo para dispositivos móviles y equipos PC con Windows. Para que este procedimiento se realice correctamente, la aplicación debe admitir el proceso de desinstalación.

## <a name="uninstall-an-app"></a>Desinstalar una aplicación

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Aplicaciones** &gt; **Aplicaciones**.

2.  Seleccione la aplicación que quiere desinstalar (una de las que ha implementado anteriormente) y, luego, elija **Administrar implementación**.

3.  En la página **Acción de implementación** , seleccione **Desinstalar** en la columna **Aprobación** .

Cuando el dispositivo o equipo vuelva a comprobar las aplicaciones, se desinstalará la aplicación.

### <a name="see-also"></a>Consulte también
[Agregar aplicaciones en Microsoft Intune](add-apps.md)

