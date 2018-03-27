---
title: Administrar aplicaciones de la Tienda Microsoft para Empresas
description: Conecte Microsoft Intune a la Tienda Microsoft para Empresas si quiere administrar e implementar aplicaciones adquiridas por volumen desde la consola de Intune.
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 02/02/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8e38d47d-0c5e-40ce-b379-29d3657f5c28
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 50fc27efc34ab6c13fad714e41be0d87c5ab0df9
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="manage-apps-you-purchased-from-the-microsoft-store-for-business-with-microsoft-intune"></a>Administrar las aplicaciones adquiridas a través de la Tienda Microsoft para Empresas con Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

En la [Tienda Microsoft para Empresas](https://www.microsoft.com/business-store), puede buscar y comprar aplicaciones para su organización, tanto sueltas como por volumen. Si conecta la tienda a Microsoft Intune, puede administrar aplicaciones compradas por volumen desde la consola de Intune. Por ejemplo:
* Puede sincronizar la lista de aplicaciones que ha adquirido en la tienda con Intune.
* Las aplicaciones que se sincronizan aparecen en la consola de administración de Intune, y puede implementarlas igual que el resto de las aplicaciones.
* Puede controlar el número de licencias disponibles y las que se usan en la consola de administración de Intune.
* Intune bloquea la implementación e instalación de aplicaciones si el número de licencias disponibles es insuficiente.

## <a name="before-you-start"></a>Antes de empezar
Revise la información siguiente antes de iniciar la sincronización y la implementación de aplicaciones desde la Tienda Microsoft para Empresas:
* Debe configurar Intune como la entidad de administración de dispositivos móviles de su organización. Para obtener más información, consulte [Requisitos previos para la inscripción de dispositivos en Microsoft Intune](prerequisites-for-enrollment.md).
* Debe haber registrado una cuenta en la Tienda Microsoft para Empresas.
* Una vez que haya asociado una cuenta de la Tienda Windows para empresas con Intune, no podrá cambiar a otra cuenta en el futuro.
* Las aplicaciones adquiridas en la tienda no se pueden agregar ni eliminar manualmente en Intune. Solo se pueden sincronizar con la Tienda Microsoft para Empresas.
* Intune solo sincroniza las aplicaciones con licencia en línea que ha comprado en la Tienda Microsoft para Empresas.
* Para usar esta funcionalidad, los dispositivos deben estar unidos a Servicios de dominio de Active Directory o al área de trabajo.
* Los dispositivos inscritos deben usar la versión 1511 de Windows 10.

## <a name="associate-your-microsoft-store-for-business-account-with-intune"></a>Asociar su cuenta de la Tienda Microsoft para Empresas con Intune
Antes de habilitar la sincronización en la consola de Intune, debe configurar la cuenta de la tienda para usar Intune como herramienta de administración:
1. Asegúrese de que inicia sesión en la Tienda para empresas con la misma cuenta de inquilino que usa para iniciar sesión en Intune.
2. En la Tienda para empresas, seleccione **Configuración** > **Herramientas de administración**.
3. En la página de Herramientas de administración, elija primero **Agregar una herramienta de administración** y, después, **Microsoft Intune**.

> [!NOTE]
> Si usa más de una herramienta de administración para implementar las aplicaciones de la Tienda Microsoft para Empresas, anteriormente solo podía asociar una de ellas con la Tienda Microsoft para Empresas. Ahora puede asociar varias herramientas de administración con la tienda, por ejemplo, Intune y Configuration Manager.

Ya puede continuar y configurar la sincronización en la consola de Intune.

## <a name="configure-synchronization"></a>Configurar la sincronización

1. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), seleccione **Administración**.
2. En el área de trabajo **Administración**, expanda **Administración de dispositivos móviles** > **Windows** y, luego, elija **Tienda para empresas**.
3. En la página **Tienda Microsoft para Empresas**, haga lo siguiente:
 * Si aún no lo ha hecho, haga clic en el vínculo para registrarse en la Tienda Microsoft para Empresas.
 * Cuando se haya registrado, elija **Configurar sincronización**.
4. En el cuadro de diálogo **Configurar la sincronización de aplicaciones de la Tienda Windows para empresas**, seleccione **Habilitar la sincronización de la Tienda Windows para empresas**.
5. En la lista desplegable **Idioma**, elija el idioma en el que las aplicaciones de la Tienda Microsoft para Empresas se mostrarán en la consola de Intune. Independientemente del idioma en el que se muestren, se instalarán en el idioma del usuario final si esa versión está disponible.
6. Haga clic en **Aceptar**.

## <a name="synchronize-apps"></a>Sincronizar aplicaciones

1. En la página **Tienda Microsoft para Empresas**, elija **Sincronizar ahora** para sincronizar las aplicaciones que ha comprado en la tienda con Intune.
2. En el área de trabajo **Aplicaciones**, elija **Aplicaciones** > **Aplicaciones comparadas por volumen** para ver las aplicaciones que puede implementar y comprobar que las aplicaciones compradas se importaron correctamente. Las aplicaciones de este nodo se muestran con el número total de licencias que posee y la cantidad de licencias que tiene disponibles.
Por ejemplo, puede comprar la aplicación del Portal de empresa (con licencia en línea) desde la Tienda Microsoft para Empresas, sincronizarla con la consola de Intune y, después, implementarla como una aplicación necesaria en los dispositivos Windows 10 necesarios. 


## <a name="deploy-apps"></a>Implementación de aplicaciones

Las aplicaciones de la tienda se implementan igual que cualquier otra aplicación de Intune. Para obtener más información, consulte [Deploy apps in Microsoft Intune](deploy-apps-in-microsoft-intune.md) (Implementar aplicaciones en Microsoft Intune).
Al implementar una aplicación de la Tienda Microsoft para Empresas, cada usuario que instala la aplicación usa una licencia. Si usa todas las licencias disponibles para una aplicación implementada, no puede implementar más copias. Debe realizar una de las siguientes acciones:
* Desinstalar la aplicación de algunos dispositivos.
* Reducir el ámbito de la implementación actual y restringirla únicamente a los usuarios para los que haya suficientes licencias.
* Compre más copias de la aplicación en la Tienda Microsoft para Empresas.

> [!Important]
> Las aplicaciones implementadas solo están disponibles para el usuario que originalmente haya inscrito el dispositivo. Ningún otro usuario puede tener acceso a la aplicación.


### <a name="see-also"></a>Vea también
[Agregar aplicaciones para dispositivos móviles en Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md)
