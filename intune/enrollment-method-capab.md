---
title: Capacidades de Intune por método de inscripción para dispositivos Windows
titlesuffix: Microsoft Intune
description: Vea qué capacidades admite cada método de inscripción para dispositivos Windows.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 457acdc212855767687f97f7d03b731f35afad46
ms.sourcegitcommit: 490f68479af814fbea1d9bd222011736fcbb1dd6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51811536"
---
# <a name="capabilities-by-enrollment-method-for-windows-devices"></a>Capacidades por método de inscripción para dispositivos Windows
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune permite administrar los dispositivos y las aplicaciones de sus recursos y su acceso a los datos de la empresa. Primero hay que inscribir los dispositivos en el servicio de Intune. Hay varios métodos para inscribir los dispositivos de los recursos. Cada método tiene diferentes procedimientos recomendados y funciones, como se muestra en estas tablas.

## <a name="best-practices-by-enrollment-method"></a>Procedimientos recomendados por método de inscripción
| **Best practices** (Procedimientos recomendados) | **[Unido a Azure AD](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Unido a Azure AD con Autopilot](enrollment-autopilot.md)** |**[Masivo](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Uso frecuente en EDU|![X](media/xmark.png)|![Marca de verificación](media/checkmark.png)|![Marca de verificación](media/checkmark.png)|![Marca de verificación](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Se pueden usar dispositivos como dispositivos compartidos|![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificación](media/checkmark.png)|![Marca de verificación](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Los dispositivos personales deben acceder a los recursos de la empresa|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificación](media/checkmark.png)|![X](media/xmark.png)|
|Mantenimiento automático de aplicaciones|![Marca de verificación](media/checkmark.png)|![Marca de verificación](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificación](media/checkmark.png)|![Marca de verificación](media/checkmark.png)|

## <a name="capabilities-by-enrollment-method"></a>Capacidades por método de inscripción

| **Capacidades** | **[Unido a Azure AD](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Unido a Azure AD con Autopilot](enrollment-autopilot.md)** |**[Masivo](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Acceso condicional                                      |![Marca de verificación](media/checkmark.png)|![Marca de verificación](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificación](media/checkmark.png)|![Marca de verificación](media/checkmark.png)|
|El usuario se asocia con el dispositivo                    |![Marca de verificación](media/checkmark.png)|![Marca de verificación](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificación](media/checkmark.png)|![Marca de verificación](media/checkmark.png)|
|Necesita Azure AD Premium                               |![X](media/xmark.png)|![Marca de verificación](media/checkmark.png)|![Marca de verificación](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificación](media/checkmark.png)|
|El dispositivo puede evaluar recursos protegidos por la entidad de certificación             |![Marca de verificación](media/checkmark.png)|![Marca de verificación](media/checkmark.png)|![Marca de verificación](media/checkmark.png)|![X](media/xmark.png)|![Marca de verificación](media/checkmark.png)|![Marca de verificación](media/checkmark.png)|
|Los usuarios no deben ser administradores en sus dispositivos               |![X](media/xmark.png)|![Marca de verificación](media/checkmark.png)|![Marca de verificación](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Capacidad de configurar la experiencia de instalación de dispositivos        |![X](media/xmark.png)|![Marca de verificación](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Capacidad de inscribir dispositivos sin interacción del usuario      |![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificación](media/checkmark.png)|![Marca de verificación](media/checkmark.png)|![X](media/xmark.png)|![Marca de verificación](media/checkmark.png)|
|Capacidad de ejecutar scripts de PowerShell                       |![Marca de verificación](media/checkmark.png)|![Marca de verificación](media/checkmark.png)|![Marca de verificación](media/checkmark.png)|![Marca de verificación](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)| 
|Admite la inscripción automática después de unirse a un dominio de AD      |![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificación](media/checkmark.png)|
|Admite la inscripción automática después de unirse a Hybrid Azure AD|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificación](media/checkmark.png)|
|Admite la inscripción automática después de unirse a Azure AD       |![Marca de verificación](media/checkmark.png)|![Marca de verificación](media/checkmark.png)|![Marca de verificación](media/checkmark.png)|![Marca de verificación](media/checkmark.png)|![Marca de verificación](media/checkmark.png)|![X](media/xmark.png)|

## <a name="next-steps"></a>Pasos siguientes

[Configuración de inscripción para Windows](windows-enroll.md)

