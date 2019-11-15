---
title: Suscribirse o iniciar sesión en Microsoft Intune
description: Procedimiento de registro para obtener una suscripción de Microsoft Intune o de inicio de sesión para comenzar una suscripción.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f3ce07a-b718-42a9-bace-f99a8b8abd94
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 78d38b72c9853a9eadaf71fcdff7567fc66d35ca
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73414669"
---
# <a name="sign-up-or-sign-in-to-microsoft-intune"></a>Suscribirse o iniciar sesión en Microsoft Intune

En este tema se explica a los administradores del sistema cómo pueden registrarse para obtener una cuenta de Intune.

Antes de registrarse en Intune, determine si ya tiene una cuenta de Microsoft Online Services, Contrato Enterprise o un contrato de licencias por volumen equivalente. Un contrato de licencias por volumen de Microsoft u otras suscripciones a servicios en la nube de Microsoft, como Office 365, suelen incluir una cuenta profesional o educativa.

Si ya dispone de una cuenta profesional o educativa, **inicie sesión** con dicha cuenta y agregue Intune a su suscripción. En caso contrario, puede **registrarse** para obtener una nueva cuenta y usar Intune para su organización.

>[!WARNING]
>No puede combinar una cuenta profesional o educativa existente después de registrarse con una cuenta nueva.

## <a name="how-to-sign-up-for-intune"></a>Cómo registrarse en Intune

1. Visite la [página de registro de Intune](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20).

   ![Captura de pantalla de la página web de registro de una cuenta de prueba de Microsoft Intune](./media/account-sign-up/account-sign-up-site.png)

2. En la página de registro, inicie sesión o regístrese para administrar una nueva suscripción de Intune.

## <a name="post-sign-up-considerations"></a>Consideraciones posteriores al registro

Cuando se haya registrado para obtener una nueva suscripción, recibirá un mensaje de correo electrónico con la información de la cuenta en la dirección de correo electrónico que haya proporcionado durante el proceso de registro. Este mensaje confirma que la suscripción está activa.

Una vez concluido el proceso de registro, se le dirigirá al Centro de administración de Microsoft 365, desde el que se pueden agregar usuarios y asignarles licencias. Si solo dispone de cuentas basadas en la nube con el nombre de dominio onmicrosoft.com predeterminado, puede continuar para agregar usuarios y asignar licencias. Pero si tiene pensado usar el [nombre de dominio personalizado](custom-domain-name-configure.md) de su organización o [sincronizar la información de la cuenta de usuario](users-add.md#sync-active-directory-and-add-users-to-intune) de Active Directory local, puede cerrar la ventana del explorador.

## <a name="sign-in-to-microsoft-intune"></a>Inicio de sesión en Microsoft Intune

Una vez que se haya registrado en Intune, puede usar cualquier dispositivo con un [explorador admitido](supported-devices-browsers.md#intune-supported-web-browsers) para iniciar sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) a fin de administrar el servicio.

De manera predeterminada, la cuenta debe tener uno de los siguientes permisos en Azure AD:

- Administrador global
- Administrador del servicio Intune (también conocido como Administrador de Intune)

Para conceder acceso para administrar el servicio para los usuarios con otros permisos, vea [Control de acceso basado en rol](role-based-access-control.md).

### <a name="intune-admin-portal-url"></a>Dirección URL del portal de administración de Intune

Centro de administración de Microsoft 365: https://devicemanagement.microsoft.com

Azure Portal en Intune: https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade

Intune para educación: https://intuneeducation.portal.azure.com

Portal de Intune clásico: https://manage.microsoft.com El portal de Intune clásico solo se usa para administrar dispositivos inscritos con el cliente de software de equipos de Intune.

### <a name="urls-for-intune-services-provided-by-office-365"></a>Direcciones URL para los servicios de Intune proporcionados por Office 365

Microsoft 365 Empresa: https://portal.microsoft.com/adminportal

Administración de dispositivos móviles de Office 365: https://portal.office.com/adminportal/home#/MifoDevices

## <a name="see-also"></a>Consulte también

[No puede iniciar sesión en Office 365, Azure o Intune](https://support.microsoft.com/help/2412085)
