---
title: Integrar SandBlast MTD de Check Point
titleSuffix: Microsoft Intune
description: Cómo configurar SandBlast Mobile Threat Defense (MTD) de CheckPoint con Intune para controlar el acceso de los dispositivos móviles a los recursos corporativos.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1e9b1576-b239-48cc-a672-da6b5fb7be0a
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 514baf3395a2cad9682e6c070b8615f320cc214c
ms.sourcegitcommit: b5e719fb507b1bc4774674e76c856c435e69f68c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/08/2019
ms.locfileid: "73801454"
---
# <a name="integrate-check-point-sandblast-mobile-with-intune"></a>Integrar SandBlast Mobile de Check Point con Intune

Complete los pasos siguientes para integrar la solución Check Point SandBlast de Mobile Threat Defense con Intune.

> [!NOTE]
> Este proveedor de Mobile Threat Defense no es compatible con dispositivos no inscritos.

## <a name="before-you-begin"></a>Antes de comenzar

Las instrucciones de este artículo se realizan en la [consola de Check Point SandBlast Mobile](https://intune-4.eu1.locsec.net/). 

Antes de iniciar el proceso de integración de SandBlast Mobile de Check Point con Intune, asegúrese de que dispone de lo siguiente:

- Suscripción a Microsoft Intune

- Credenciales de administrador de Azure Active Directory para conceder los permisos siguientes:

  - Iniciar sesión y leer el perfil del usuario

  - Obtener acceso al directorio con el usuario que tiene la sesión iniciada

  - Leer datos de directorio

  - Enviar información del dispositivo a Intune

- Credenciales de administrador para obtener acceso a la consola Check Point SandBlast Mobile MTD

### <a name="check-point-sandblast-app-authorization"></a>Autorización de la aplicación SandBlast de Check Point

El proceso de autorización de la aplicación SandBlast de Check Point consta de los siguientes pasos:

- Permitir que el servicio de SandBlast Mobile de Check Point comunique a Intune la información relacionada con el estado de mantenimiento del dispositivo.

- SandBlast Mobile de Check Point se sincroniza con la pertenencia a grupos de inscripción de Azure AD para rellenar la base de datos de su dispositivo.

- Permitir que la consola de administración de SandBlast de Check Point use el inicio de sesión único (SSO) de Azure AD.

- Permitir que la aplicación SandBlast Mobile de Check Point inicie sesión con el SSO de Azure AD.

## <a name="to-set-up-check-point-sandblast-mobile-integration"></a>Para configurar la integración de SandBlast Mobile de Check Point

1. Vaya a la [consola Check Point SandBlast Mobile MTD](https://intune-4.eu1.locsec.net/) e inicie sesión con sus credenciales.

2. Haga clic en la pestaña **Settings** (Configuración).

3. Seleccione **Device management** (Administración de dispositivos) y luego **Settings** (Configuración).

4. Seleccione **Microsoft Intune** en la lista desplegable **MDM Service** (Servicio MDM).

5. Una vez configurado Microsoft Intune como servicio de MDM, aparecerá la ventana **Microsoft Intune Configuration** (Configuración de Microsoft Intune). Seleccione **Add to my organization** (Agregar a mi organización) para cada plataforma de dispositivo (iOS, Android y Windows) para autorizar a SandBlast Mobile de Check Point que se comunique con Intune y Azure AD.

    ![Imagen en la que se muestra la configuración de MTD de Check Point en Intune](./media/checkpoint-sandblast-mobile-mtd-connector-integration/checkpoint-MTD-1.PNG)

    > [!IMPORTANT]
    > Debe agregar todas las plataformas de dispositivo para poder continuar con el siguiente paso.

6. Seleccione **Accept** (Aceptar) para autorizar a la aplicación SandBlast Mobile de Check Point que se comunique con Intune y con Azure Active Directory.

7. Una vez habilitadas todas las plataformas de dispositivo, deberá indicar el grupo de seguridad de Azure AD.

8. Seleccione **Verify** (Comprobar) y, una vez comprobado correctamente el grupo de seguridad de Azure AD, seleccione **Save** (Guardar).

## <a name="next-steps"></a>Pasos siguientes

- [Configurar aplicaciones SandBlast Mobile de Check Point](mtd-apps-ios-app-configuration-policy-add-assign.md)
