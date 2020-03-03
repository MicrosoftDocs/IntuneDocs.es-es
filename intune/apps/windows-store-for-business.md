---
title: Administración de aplicaciones de VPP desde Microsoft Store para Empresas
titleSuffix: Microsoft Intune
description: Aprenda a sincronizar aplicaciones en Intune desde Microsoft Store para Empresas.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6faaa800d8dedc53ab20f1dae2c3049132642b7d
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609164"
---
# <a name="how-to-manage-volume-purchased-apps-from-the-microsoft-store-for-business-with-microsoft-intune"></a>Administración de aplicaciones compradas por volumen en Microsoft Store para Empresas con Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

En la [Tienda Microsoft para Empresas](https://www.microsoft.com/business-store), puede buscar y comprar aplicaciones para su organización, tanto sueltas como por volumen. Si conecta la tienda a Microsoft Intune, puede administrar las aplicaciones adquiridas por volumen desde Azure Portal. Por ejemplo:
* Puede sincronizar la lista de aplicaciones que compró (o que son gratuitas) en la tienda con Intune.
* Las aplicaciones que se sincronizan aparecen en la consola de administración de Intune, y puede asignarlas igual que el resto de las aplicaciones.
* Las versiones de aplicaciones con licencia en línea y sin conexión se sincronizan con Intune. Junto a los nombres de las aplicaciones, se anexarán las palabras "En línea" o "Sin conexión" en el portal.
* Puede controlar el número de licencias disponibles y las que se usan en la consola de administración de Intune.
* Intune bloquea la asignación e instalación de aplicaciones si el número de licencias disponibles es insuficiente.
* Las aplicaciones administradas por Microsoft Store para Empresas revocarán automáticamente las licencias cuando un usuario deje la empresa, o bien cuando el administrador quite el usuario y sus dispositivos.

## <a name="before-you-start"></a>Antes de empezar

Revise la información siguiente antes de iniciar la sincronización y la asignación de aplicaciones desde la Tienda Microsoft para Empresas:

- Configure Intune como la entidad de administración de dispositivos móviles de su organización.
- Debe haber registrado una cuenta en la Tienda Microsoft para Empresas.
- Una vez que haya asociado una cuenta de Microsoft Store para Empresas con Intune, no podrá cambiar a otra cuenta en el futuro.
- Las aplicaciones adquiridas en la tienda no se pueden agregar ni eliminar manualmente en Intune. Solo se pueden sincronizar con la Tienda Microsoft para Empresas.
- Las aplicaciones con licencia en línea y sin conexión que haya adquirido en la Microsoft Store para Empresas se sincronizarán con el portal de Intune. Así, puede implementar estas aplicaciones en grupos de usuarios o grupos de dispositivos. 
- Las instalaciones de aplicaciones en línea las administra la tienda.
- Las aplicaciones sin conexión gratuitas también pueden sincronizarse con Intune. Estas aplicaciones las instala Intune, no la tienda.
- Para usar esta función, los dispositivos deben estar unidos a Active Directory Domain Services, a Azure AD o al área de trabajo.
- Los dispositivos inscritos deben usar la versión 1511 de Windows 10 o versiones posteriores.

Además, los conjuntos relacionados y las aplicaciones con licencia sin conexión de la Microsoft Store para Empresas se consolidarán ahora en una única entrada de aplicación en la interfaz de usuario. Los detalles de implementación de los paquetes individuales se migrarán a la entrada única. Para ver los conjuntos relacionados en Azure Portal, seleccione **Licencias de aplicaciones** en el panel **Aplicaciones**.

## <a name="associate-your-microsoft-store-for-business-account-with-intune"></a>Asociar su cuenta de la Tienda Microsoft para Empresas con Intune
Antes de habilitar la sincronización en la consola de Intune, debe configurar la cuenta de la tienda para usar Intune como herramienta de administración:
1. Asegúrese de que inicia sesión en [Microsoft Store para Empresas](https://www.microsoft.com/business-store) con la misma cuenta de inquilino que usa para iniciar sesión en Intune.
2. En Microsoft Store para Empresas, elija la pestaña **Administrar**, seleccione **Configuración** y elija la pestaña **Distribuir**.
3. Si no tiene específicamente **Microsoft Intune** disponible como una herramienta de administración de dispositivos móviles, elija **Add management tool** (Agregar herramienta de administración) para agregar **Microsoft Intune**. Si no tiene **Microsoft Intune** activado como su herramienta de administración de dispositivos móviles, haga clic en **Activar** junto a **Microsoft Intune**. Tenga en cuenta que debe activar **Microsoft Intune** en lugar de **Microsoft Intune Enrollment** (Inscripción a Microsoft Intune).

> [!NOTE]
> Anteriormente solo podía asociar una herramienta de administración para asignar aplicaciones con la Tienda Microsoft para Empresas. Ahora puede asociar varias herramientas de administración con la tienda, por ejemplo, Intune y Configuration Manager. 

Ya puede continuar y configurar la sincronización en la consola de Intune.

## <a name="configure-synchronization"></a>Configurar la sincronización

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Administración de inquilinos** > **Conectores y tokens** > **Microsoft Store para Empresas**.
3. Haga clic en **Habilitar**.
4. Si aún no lo ha hecho, haga clic en el vínculo para registrarse en la Tienda Microsoft para Empresas y asocie la cuenta como se ha descrito anteriormente.
5. En la lista desplegable **Idioma**, seleccione el idioma en el que las aplicaciones de Microsoft Store para Empresas se muestran en Azure Portal. Independientemente del idioma en el que se muestren, se instalan en el idioma del usuario final si esa versión está disponible.
6. Haga clic en **Sincronizar** para que las aplicaciones que ha adquirido en la Microsoft Store aparezcan en Intune.

## <a name="synchronize-apps"></a>Sincronizar aplicaciones

1. Seleccione **Administración de inquilinos** > **Conectores y tokens** > **Microsoft Store para Empresas**.
2. Haga clic en **Sincronizar** para que las aplicaciones que ha adquirido en la Microsoft Store aparezcan en Intune.

> [!NOTE]
> Actualmente, no se admiten las aplicaciones con paquetes de aplicación cifrados y no se sincronizarán con Intune.

## <a name="assign-apps"></a>Asignación de aplicaciones

Las aplicaciones de la tienda se asignan del mismo modo que cualquier otra aplicación de Intune. Para más información, consulte [Asignación de aplicaciones a grupos con Microsoft Intune](apps-deploy.md). 

Las aplicaciones sin conexión pueden dirigirse a grupos de usuarios, grupos de dispositivos o grupos con usuarios y dispositivos.
Las aplicaciones sin conexión pueden instalarse para un usuario determinado en un dispositivo o para todos los usuarios de un dispositivo. 


Al asignar una aplicación de la Tienda Microsoft para Empresas, cada usuario que instala la aplicación usa una licencia. Si usa todas las licencias disponibles para una aplicación asignada, no puede asignar más copias. Realice una de las acciones siguientes:
* Desinstalar la aplicación de algunos dispositivos.
* Reducir el ámbito de la asignación actual y restringirla únicamente a los usuarios para los que haya suficientes licencias.
* Compre más copias de la aplicación en la Tienda Microsoft para Empresas.

## <a name="remove-apps"></a>Quitar aplicaciones

Para quitar una aplicación que se sincroniza desde Microsoft Store para Empresas, debe iniciar sesión en Microsoft Store para Empresas y reembolsar la aplicación. El proceso es el mismo tanto si la aplicación es gratuita como si no lo es. Para una aplicación gratuita, la tienda reembolsará 0 $. En el ejemplo siguiente se muestra un reembolso por una aplicación gratuita. 

![Captura de pantalla de los detalles para quitar la aplicación](./media/windows-store-for-business/microsoft-store-for-business-01.png)

> [!NOTE]
> Quitar la visibilidad de una aplicación en la tienda privada no impedirá que Intune la sincronice. Debe reembolsar la aplicación para quitarla completamente.

## <a name="next-steps"></a>Pasos siguientes

- [Administración de aplicaciones y libros comprados por volumen con Microsoft Intune](../vpp-apps.md)
