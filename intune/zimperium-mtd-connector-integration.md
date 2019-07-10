---
title: Integración de Zimperium MTD con Microsoft Intune
titleSuffix: Microsoft Intune
description: Cómo configurar la solución Zimperium Mobile Threat Defense (MTD) con Microsoft Intune para controlar el acceso de los dispositivos móviles a los recursos corporativos.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/04/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 363fd280-1865-4a61-855b-eb75c3c62753
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e78c9034058a5f60f01056711465b28deca77d83
ms.sourcegitcommit: ede86a3cb094c12e3e218b956abb9935bec76902
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2019
ms.locfileid: "67572166"
---
# <a name="integrate-zimperium-with-intune"></a>Integrar Zimperium con Intune

Complete estos pasos para integrar la solución Zimperium Mobile Threat Defense con Intune.

## <a name="before-you-begin"></a>Antes de comenzar

> [!NOTE]
> Los pasos siguientes debe completarlos en la [consola Zimperium MTD](https://www.zimperium.com/platform).

Antes de iniciar el proceso de integración de Zimperium con Intune, asegúrese de que tiene las siguientes credenciales y suscripción:

- Suscripción a Microsoft Intune

- Credenciales de administrador de Administrador global de Azure Active Directory para conceder los permisos siguientes:

    - Iniciar sesión y leer el perfil del usuario

    - Obtener acceso al directorio con el usuario que tiene la sesión iniciada

    - Leer datos de directorio

    - Enviar información del dispositivo a Intune

- Credenciales de administrador para obtener acceso a la consola MTD de Zimperium.

### <a name="zimperium-app-authorization"></a>Autorización de la aplicación Zimperium

El proceso de autorización de la aplicación Zimperium es el siguiente:

- Conceder los permisos del servicio Zimperium para comunicar a Intune la información relacionada con el estado de mantenimiento del dispositivo. Para conceder estos permisos, debe usar las credenciales de Administrador global. La concesión de permisos es una operación única. Después de concederse los permisos, las credenciales de Administrador global no son necesarias para la actividad diaria.

- Zimperium se sincroniza con la pertenencia a grupos de inscripción de Azure Active Directory (AD) para rellenar la base de datos de su dispositivo.

- Permitir que la consola de administración de Zimperium use el inicio de sesión único (SSO) de Azure AD.

- Permitir que la aplicación de Zimperium inicie sesión con el SSO de Azure AD.

Para obtener más información sobre el consentimiento y las aplicaciones de Azure Active Directory, consulte [Request the permissions from a directory admin](https://docs.microsoft.com/azure/active-directory/develop/v2-permissions-and-consent#request-the-permissions-from-a-directory-admin) (Solicitar los permisos desde un administrador del directorio) en el artículo de Azure Active Directory *Permissions and consent in the Azure Active Directory v2.0 endpoint* (Permisos y consentimiento en el punto de conexión de Azure Active Directory v2.0).


## <a name="to-set-up-zimperium-integration"></a>Para configurar la integración de Zimperium

1. Vaya a la [consola MTD de Zimperium](https://www.zimperium.com/platform) e inicie sesión con sus credenciales. Para llevar a cabo el proceso de configuración de integración de Zimperium, debe iniciar sesión con un usuario de Azure Active Directory con el rol de Administrador global. Esta operación de configuración única usa los derechos de Administrador global para conceder permiso en su organización para que las aplicaciones de Zimperium se comuniquen con Intune. 

2. Seleccione **Management** (Administración) en el menú izquierdo.

3. Seleccione la pestaña **MDM settings** (Configuración de MDM).

4. Seleccione **Add MDM** (Agregar MDM) y, luego, seleccione **Microsoft Intune** en la lista **MDM provider** (Proveedor MDM).

5. Cuando haya establecido Microsoft Intune como servicio MDM, aparecerá la ventana **Configuración de Microsoft Intune**. A continuación, elija **Agregar Azure Active Directory** para cada opción: **zConsole de Zimperium** y **aplicaciones zIPS para iOS y Android** para autorizar a Zimperium para comunicarse con Intune y Azure AD a través del inicio de sesión único de Azure AD.

    > [!IMPORTANT]  
    > Debe agregar la consola zConsole de Zimperium y las aplicaciones zIPS para iOS y Android para completar el proceso de integración con Intune.

6. Seleccione **Accept** (Aceptar) para autorizar a la aplicación de Zimperium que se comunique con Intune y con Azure Active Directory.

7. Una vez agregadas a Azure AD la consola **zConsole de Zimperium** y las aplicaciones **zIPS para iOS y Android**, agregue los grupos de seguridad de Azure AD. De esta forma, Zimperium puede sincronizar el grupo de seguridad de Azure AD con su servicio.

8. Seleccione **Finish** (Finalizar) para guardar la configuración e iniciar la primera sincronización de grupo de seguridad de Azure AD.

9. Cierre la sesión de la consola de Zimperium MTD.

## <a name="next-steps"></a>Pasos siguientes

- [Configurar aplicaciones Zimperium](mtd-apps-ios-app-configuration-policy-add-assign.md)
