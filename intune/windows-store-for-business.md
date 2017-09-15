---
title: "Administración de aplicaciones desde la Tienda Microsoft para Empresas"
titlesuffix: Azure portal
description: "Obtenga información sobre cómo puede sincronizar aplicaciones en Intune desde la Tienda Microsoft para Empresas y luego asignarlas y realizar un seguimiento de ellas."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 649766b26a1061c4bce11235c04dcbe8570fcdc4
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-manage-apps-you-purchased-from-the-microsoft-store-for-business-with-microsoft-intune"></a>Cómo administrar las aplicaciones adquiridas a través de la Tienda Microsoft para Empresas con Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


En la [Tienda Microsoft para Empresas](https://www.microsoft.com/business-store), puede buscar y comprar aplicaciones para su organización, tanto sueltas como por volumen. Si conecta la tienda a Microsoft Intune, puede administrar las aplicaciones adquiridas por volumen desde Azure Portal. Por ejemplo:
* Puede sincronizar la lista de aplicaciones que ha adquirido en la tienda con Intune.
* Las aplicaciones que se sincronizan aparecen en la consola de administración de Intune, y puede asignarlas igual que el resto de las aplicaciones.
* Puede controlar el número de licencias disponibles y las que se usan en la consola de administración de Intune.
* Intune bloquea la asignación e instalación de aplicaciones si el número de licencias disponibles es insuficiente.

## <a name="before-you-start"></a>Antes de empezar

Revise la información siguiente antes de iniciar la sincronización y la asignación de aplicaciones desde la Tienda Microsoft para Empresas:

- Configure Intune como la entidad de administración de dispositivos móviles de su organización.
- Debe haber registrado una cuenta en la Tienda Microsoft para Empresas.
- Una vez que haya asociado una cuenta de la Tienda Windows para empresas con Intune, no podrá cambiar a otra cuenta en el futuro.
- Las aplicaciones adquiridas en la tienda no se pueden agregar ni eliminar manualmente en Intune. Solo se pueden sincronizar con la Tienda Microsoft para Empresas.
- Intune sincroniza las aplicaciones con licencia en línea y sin conexión que ha comprado en la Tienda Microsoft para Empresas.
- Solo las aplicaciones sin conexión gratuitas pueden sincronizarse en Intune.
- Para usar esta función, los dispositivos deben estar unidos a Active Directory Domain Services o al área de trabajo.
- Los dispositivos inscritos deben usar la versión 1511 de Windows 10 o versiones posteriores.

## <a name="associate-your-microsoft-store-for-business-account-with-intune"></a>Asociar su cuenta de la Tienda Microsoft para Empresas con Intune
Antes de habilitar la sincronización en la consola de Intune, debe configurar la cuenta de la tienda para usar Intune como herramienta de administración:
1. Asegúrese de que inicia sesión en la Tienda para empresas con la misma cuenta de inquilino que usa para iniciar sesión en Intune.
2. En la Tienda para empresas, seleccione **Configuración** > **Herramientas de administración**.
3. En la página de Herramientas de administración, elija primero **Agregar una herramienta de administración** y, después, **Microsoft Intune**.

> [!NOTE]
> Anteriormente solo podía asociar una herramienta de administración para asignar aplicaciones con la Tienda Microsoft para Empresas. Ahora puede asociar varias herramientas de administración con la tienda, por ejemplo, Intune y Configuration Manager.

Ya puede continuar y configurar la sincronización en la consola de Intune.

## <a name="configure-synchronization"></a>Configurar la sincronización

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Aplicaciones móviles**.
1. En la hoja **Aplicaciones móviles**, seleccione **Configuración** > **Tienda Microsoft para Empresas**.
2. Haga clic en **Habilitar**.
3. Si aún no lo ha hecho, haga clic en el vínculo para registrarse en la Tienda Microsoft para Empresas y asocie la cuenta como se ha descrito anteriormente.
5. En la lista desplegable **Idioma**, seleccione el idioma en el que las aplicaciones de la Tienda Microsoft para Empresas se muestran en Azure Portal. Independientemente del idioma en el que se muestren, se instalan en el idioma del usuario final si esa versión está disponible.
6. Haga clic en **Sincronizar** para que las aplicaciones que ha adquirido en la Microsoft Store aparezcan en Intune.

## <a name="synchronize-apps"></a>Sincronizar aplicaciones

1. En la carga de trabajo **Aplicaciones móviles**, seleccione **Configuración** > **Tienda Microsoft para Empresas**.
2. Haga clic en **Sincronizar** para que las aplicaciones que ha adquirido en la Microsoft Store aparezcan en Intune.

## <a name="assign-apps"></a>Asignación de aplicaciones

Las aplicaciones de la tienda se asignan del mismo modo que cualquier otra aplicación de Intune. Para más información, consulte [Asignación de aplicaciones a grupos con Microsoft Intune](apps-deploy.md). Sin embargo, en lugar de asignar aplicaciones desde la página **Todas las aplicaciones**, asígnelas desde la página **Aplicaciones con licencia**.

Las aplicaciones sin conexión pueden dirigirse a grupos de usuarios, grupos de dispositivos o grupos con usuarios y dispositivos.
Las aplicaciones sin conexión pueden instalarse para un usuario determinado en un dispositivo o para todos los usuarios de un dispositivo. 


Al asignar una aplicación de la Tienda Microsoft para Empresas, cada usuario que instala la aplicación usa una licencia. Si usa todas las licencias disponibles para una aplicación asignada, no puede asignar más copias. Realice una de las acciones siguientes:
* Desinstalar la aplicación de algunos dispositivos.
* Reducir el ámbito de la asignación actual y restringirla únicamente a los usuarios para los que haya suficientes licencias.
* Compre más copias de la aplicación en la Tienda Microsoft para Empresas.


