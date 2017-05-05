---
title: "Administración de aplicaciones de la Tienda Windows para empresas"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda cómo sincronizar aplicaciones en Intune desde la Tienda Windows para empresas y luego asignarlas y realizar el seguimiento de ellas."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: 6e410a37f91e0828d5f6b205acb4d340dae86c6d
ms.lasthandoff: 04/24/2017

---

# <a name="how-to-manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune"></a>Administración de aplicaciones adquiridas a través de la Tienda Windows para empresas con Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


En la [Tienda Windows para empresas](https://www.microsoft.com/business-store) puede buscar y comprar aplicaciones para su organización, tanto sueltas como en lote. Si conecta la tienda a Microsoft Intune, puede administrar aplicaciones compradas por volumen desde la consola de Intune. Por ejemplo:
* Puede sincronizar la lista de aplicaciones que ha adquirido en la tienda con Intune.
* Las aplicaciones que se sincronizan aparecen en la consola de administración de Intune, y puede asignarlas igual que el resto de las aplicaciones.
* Puede controlar el número de licencias disponibles y las que se usan en la consola de administración de Intune.
* Intune bloquea la implementación e instalación de aplicaciones si el número de licencias disponibles es insuficiente.

## <a name="before-you-start"></a>Antes de empezar
Revise la información siguiente antes de iniciar la sincronización y la implementación de aplicaciones de la Tienda Windows para empresas:
* Debe configurar Intune como la entidad de administración de dispositivos móviles de su organización.
* Debe haber registrado una cuenta en la Tienda Windows para empresas.
* Una vez que haya asociado una cuenta de la Tienda Windows para empresas con Intune, no podrá cambiar a otra cuenta en el futuro.
* Las aplicaciones adquiridas en la tienda no se pueden agregar ni eliminar manualmente en Intune. Solo se pueden sincronizar con la Tienda Windows para empresas.
* Intune solo sincroniza las aplicaciones con licencia en línea que ha comprado en la Tienda Windows para empresas.
* Para usar esta funcionalidad, los dispositivos deben estar unidos a Active Directory Domain Services o al área de trabajo.
* Los dispositivos inscritos deben usar la versión 1511 de Windows 10 o versiones posteriores.

## <a name="associate-your-windows-store-for-business-account-with-intune"></a>Asociar su cuenta de la Tienda Windows para empresas con Intune
Antes de habilitar la sincronización en la consola de Intune, debe configurar la cuenta de la tienda para usar Intune como herramienta de administración:
1. Asegúrese de que inicia sesión en la Tienda para empresas con la misma cuenta de inquilino que usa para iniciar sesión en Intune.
2. En la Tienda para empresas, seleccione **Configuración** > **Herramientas de administración**.
3. En la página de Herramientas de administración, elija primero **Agregar una herramienta de administración** y, después, **Microsoft Intune**.

> [!NOTE]
> Si usa más de una herramienta de administración para implementar las aplicaciones de la Tienda Windows para empresas, anteriormente solo podía asociar una de ellas con la Tienda Windows para empresas. Ahora puede asociar varias herramientas de administración con la tienda, por ejemplo, Intune y Configuration Manager.

Ya puede continuar y configurar la sincronización en la consola de Intune.

## <a name="configure-synchronization"></a>Configurar la sincronización

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
3. En la hoja **Intune**, elija **Mobile apps**.
1. En la hoja **Mobile Apps**, elija **Configuración** > **Tienda Windows para empresas**.
2. Haga clic en **Habilitar**.
3. Si aún no lo ha hecho, haga clic en el vínculo para registrarse en la Tienda Windows para empresas y asocie la cuenta como se ha descrito anteriormente.
5. En la lista desplegable **Idioma**, elija el idioma en el que las aplicaciones de la Tienda Windows para empresas se mostrarán en la consola de Intune. Independientemente del idioma en el que se muestren, se instalarán en el idioma del usuario final si esa versión está disponible.
6. Haga clic en **Sincronizar** para que las aplicaciones que ha adquirido en la Tienda Windows aparezcan en Intune.

## <a name="synchronize-apps"></a>Sincronizar aplicaciones

1. En la carga de trabajo **Mobile apps**, elija **Configuración** > **Tienda Windows para empresas**.
2. Haga clic en **Sincronizar** para que las aplicaciones que ha adquirido en la Tienda Windows aparezcan en Intune.

## <a name="assign-apps"></a>Asignación de aplicaciones

Las aplicaciones de la tienda se asignan del mismo modo que se implementa cualquier otra aplicación de Intune. Para más información, consulte [Asignación de aplicaciones a grupos con Microsoft Intune](deploy-apps.md). Sin embargo, en lugar de asignar aplicaciones desde la página **Todas las aplicaciones**, asígnelas desde la página **Aplicaciones con licencia**.

Al asignar una aplicación de la Tienda Windows para empresas, cada usuario que instala la aplicación usa una licencia. Si usa todas las licencias disponibles para una aplicación implementada, no puede implementar más copias. Debe realizar una de las siguientes acciones:
* Desinstalar la aplicación de algunos dispositivos.
* Reducir el ámbito de la implementación actual y restringirla únicamente a los usuarios para los que haya suficientes licencias.
* Comprar más copias de la aplicación en la Tienda Windows para empresas.

> [!Important]
> Las aplicaciones implementadas solo están disponibles para el usuario que originalmente haya inscrito el dispositivo. Ningún otro usuario puede tener acceso a la aplicación.

