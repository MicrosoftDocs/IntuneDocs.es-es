---
title: Integrar Zimperium con Intune
titleSuffix: Intune on Azure
description: Integrar Intune con Zimperium
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 12/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 363fd280-1865-4a61-855b-eb75c3c62753
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4759bab0c302f758f3f0a4af5ca333a5f560f3b3
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="integrate-zimperium-with-intune"></a>Integrar Zimperium con Intune

Complete estos pasos para integrar la solución Zimperium Mobile Threat Defense con Intune.

## <a name="before-you-begin"></a>Antes de comenzar

> [!NOTE]
> Los pasos siguientes debe completarlos en la [consola Zimperium MTD](https://staging2-console.zimperium.com).

Antes de iniciar el proceso de integración de Zimperium con Intune, asegúrese de que dispone de lo siguiente:

-   Suscripción a Microsoft Intune

-   Credenciales de administrador de Azure Active Directory para conceder los permisos siguientes:

    -   Iniciar sesión y leer el perfil del usuario

    -   Obtener acceso al directorio con el usuario que tiene la sesión iniciada

    -   Leer datos de directorio

    -   Enviar información del dispositivo a Intune

-   Credenciales de administrador para obtener acceso a la consola MTD de Zimperium.

### <a name="zimperium-app-authorization"></a>Autorización de la aplicación Zimperium

El proceso de autorización de la aplicación Zimperium es el siguiente:

-   Permitir que el servicio de Zimperium comunique a Intune la información relacionada con el estado de mantenimiento del dispositivo.

-   Zimperium se sincroniza con la pertenencia a grupos de inscripción de Azure AD para rellenar la base de datos de su dispositivo.

-   Permitir que la consola de administración de Zimperium use el inicio de sesión único (SSO) de Azure AD.

-   Permitir que la aplicación de Zimperium inicie sesión con el SSO de Azure AD.

## <a name="to-set-up-zimperium-integration"></a>Para configurar la integración de Zimperium

1.  Vaya a la [consola MTD de Zimperium](https://staging2-console.zimperium.com) e inicie sesión con sus credenciales.

2.  Seleccione **Management** (Administración) en el menú izquierdo.

3.  Seleccione la pestaña **MDM settings** (Configuración de MDM).

4.  Seleccione **Add MDM** (Agregar MDM) y, luego, seleccione **Microsoft Intune** en la lista **MDM provider** (Proveedor MDM).

5.  Una vez que haya establecido Microsoft Intune como servicio MDM, aparecerá la ventana **Microsoft Intune Configuration** (Configuración de Microsoft Intune). Seleccione la opción **Add Azure Active Directory** (Agregar Azure Active Directory) para todas las opciones, **Zimperium zConsole** (consola zConsole de Zimperium) y **zIPS iOS and Android apps** (aplicaciones zIPS para iOS y Android), para autorizar a Zimperium para que se comunique con Intune y Azure AD mediante el inicio de sesión único de Azure AD.

    > [!IMPORTANT]
    > Debe agregar la consola zConsole de Zimperium y las aplicaciones zIPS para iOS y Android para completar el proceso de integración con Intune.

6.  Seleccione **Accept** (Aceptar) para autorizar a la aplicación de Zimperium que se comunique con Intune y con Azure Active Directory.

7.  Una vez agregadas a Azure AD la consola **zConsole de Zimperium** y las **aplicaciones zIPS para iOS y Android**, agregue los grupos de seguridad de Azure AD para que Zimperium pueda sincronizar el grupo de seguridad de Azure AD con su servicio.

8.  Seleccione **Finish** (Finalizar) para guardar la configuración e iniciar la primera sincronización de grupo de seguridad de Azure AD.

## <a name="next-steps"></a>Pasos siguientes

-   [Configurar aplicaciones Zimperium](mtd-apps-ios-app-configuration-policy-add-assign.md)
