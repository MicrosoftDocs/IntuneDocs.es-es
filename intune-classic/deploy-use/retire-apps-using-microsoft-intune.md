---
title: Retirar aplicaciones
description: Obtenga información sobre cómo retirar o desinstalar aplicaciones mediante Intune.
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6fbf0805-1144-4e08-bafd-4f181d932bf2
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: a3fadf497e5db147d12ecf1e32343e94222c65e9
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="retire-apps-using-microsoft-intune"></a>Retirar aplicaciones mediante Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Para retirar una aplicación, simplemente desinstálela. Al implementar y administrar aplicaciones con Intune, el proceso de desinstalación de la aplicación es el mismo para dispositivos móviles y equipos PC con Windows. Para que este procedimiento se realice correctamente, la aplicación debe admitir el proceso de desinstalación.

## <a name="uninstall-an-app"></a>Desinstalar una aplicación

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Aplicaciones** &gt; **Aplicaciones**.

2.  Seleccione la aplicación que quiere desinstalar (una de las que ha implementado anteriormente) y, luego, elija **Administrar implementación**.

3.  En la página **Acción de implementación** , seleccione **Desinstalar** en la columna **Aprobación** .

Cuando el dispositivo o equipo vuelva a comprobar las aplicaciones, se desinstalará la aplicación.

### <a name="see-also"></a>Vea también
[Agregar aplicaciones en Microsoft Intune](add-apps.md)
