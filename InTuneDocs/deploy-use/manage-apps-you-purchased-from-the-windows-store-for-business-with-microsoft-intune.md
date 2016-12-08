---
title: Administrar aplicaciones de la Tienda Windows para empresas | Microsoft Intune
description: Conecte Microsoft Intune a la Tienda Windows para empresas si desea administrar e implementar aplicaciones adquiridas por volumen desde la consola de Intune.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e38d47d-0c5e-40ce-b379-29d3657f5c28
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 37044da4c7a58749c7b3423b1872b07d1673603d


---

# <a name="manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune"></a>Administrar las aplicaciones adquiridas a través de la Tienda Windows para empresas con Microsoft Intune
En la [Tienda Windows para empresas](https://www.microsoft.com/business-store) puede buscar y comprar aplicaciones para su organización, tanto sueltas como en lote. Si conecta la tienda a Microsoft Intune, puede administrar aplicaciones compradas por volumen desde la consola de Intune. Por ejemplo:
* Puede sincronizar la lista de aplicaciones que ha adquirido en la tienda con Intune.
* Las aplicaciones que se sincronizan aparecen en la consola de administración de Intune, y puede implementarlas igual que el resto de las aplicaciones.
* Puede controlar el número de licencias disponibles y las que se usan en la consola de administración de Intune.
* Intune bloquea la implementación e instalación de aplicaciones si el número de licencias disponibles es insuficiente.

## <a name="before-you-start"></a>Antes de empezar
Revise la información siguiente antes de iniciar la sincronización y la implementación de aplicaciones de la Tienda Windows para empresas:
* Debe configurar Intune como la entidad de administración de dispositivos móviles de su organización. Para obtener más información, consulte [Requisitos previos para la inscripción de dispositivos en Microsoft Intune](prerequisites-for-enrollment.md).
* Debe haber registrado una cuenta en la Tienda Windows para empresas.
* Una vez que haya asociado una cuenta de la Tienda Windows para empresas con Intune, no podrá cambiar a otra cuenta en el futuro.
* Las aplicaciones adquiridas en la tienda no se pueden agregar ni eliminar manualmente en Intune. Solo se pueden sincronizar con la Tienda Windows para empresas.
* Intune solo sincroniza las aplicaciones con licencia en línea que ha comprado en la Tienda Windows para empresas.
* Para usar esta funcionalidad, los dispositivos deben estar unidos a Servicios de dominio de Active Directory o al área de trabajo.
* Los dispositivos inscritos deben usar la versión 1511 de Windows 10.

## <a name="associate-your-windows-store-for-business-account-with-intune"></a>Asociar su cuenta de la Tienda Windows para empresas con Intune
Antes de habilitar la sincronización en la consola de Intune, debe configurar la cuenta de la tienda para usar Intune como herramienta de administración:
1. Asegúrese de que inicia sesión en la Tienda para empresas con la misma cuenta de inquilino que usa para iniciar sesión en Intune.
2. En la Tienda para empresas, seleccione **Configuración** > **Herramientas de administración**.
3. En la página de Herramientas de administración, elija primero **Agregar una herramienta de administración** y, después, **Microsoft Intune**.

Ya puede continuar y configurar la sincronización en la consola de Intune.

## <a name="configure-synchronization"></a>Configurar la sincronización

1. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), seleccione **Administración**.
2. En el área de trabajo **Administración**, expanda **Administración de dispositivos móviles** > **Windows** y, luego, elija **Tienda para empresas**.
3. En la página **Tienda Windows para empresas**, haga lo siguiente:
 * Si aún no lo ha hecho, haga clic en el vínculo para registrarse en la Tienda Windows para empresas.
 * Cuando se haya registrado, elija **Configurar sincronización**.
4. En el cuadro de diálogo **Configurar la sincronización de aplicaciones de la Tienda Windows para empresas**, seleccione **Habilitar la sincronización de la Tienda Windows para empresas**.
5. En la lista desplegable **Idioma**, elija el idioma en el que las aplicaciones de la Tienda Windows para empresas se mostrarán en la consola de Intune. Independientemente del idioma en el que se muestren, se instalarán en el idioma del usuario final si esa versión está disponible.
6. Haga clic en **Aceptar**.

## <a name="synchronize-apps"></a>Sincronizar aplicaciones

1. En la página **Tienda Windows para empresas**, elija **Sincronizar ahora** para sincronizar las aplicaciones que ha comprado en la tienda con Intune.
2. En el área de trabajo **Aplicaciones**, elija **Aplicaciones** > **Aplicaciones comparadas por volumen** para ver las aplicaciones que puede implementar y comprobar que las aplicaciones compradas se importaron correctamente. Las aplicaciones de este nodo se muestran con el número total de licencias que posee y la cantidad de licencias que tiene disponibles.
Por ejemplo, puede comprar la aplicación de Portal de empresa (en línea con licencia) desde la Tienda Windows para la empresa, sincronizarla con la consola de Intune y, a continuación, implementar esto como una aplicación necesaria en los dispositivos Windows 10 necesarios. 


## <a name="deploy-apps"></a>Implementación de aplicaciones

Las aplicaciones de la tienda se implementan igual que cualquier otra aplicación de Intune. Para obtener más información, consulte [Deploy apps in Microsoft Intune](deploy-apps-in-microsoft-intune.md) (Implementar aplicaciones en Microsoft Intune).
Al implementar una aplicación de la Tienda Windows para empresas, cada usuario que instala la aplicación utiliza una licencia. Si usa todas las licencias disponibles para una aplicación implementada, no puede implementar más copias. Debe realizar una de las siguientes acciones:
* Desinstalar la aplicación de algunos dispositivos.
* Reducir el ámbito de la implementación actual y restringirla únicamente a los usuarios para los que haya suficientes licencias.
* Comprar más copias de la aplicación en la Tienda Windows para empresas.

> [!Important]
> Las aplicaciones implementadas solo están disponibles para el usuario que originalmente haya inscrito el dispositivo. Ningún otro usuario puede tener acceso a la aplicación.


### <a name="see-also"></a>Consulte también
[Agregar aplicaciones para dispositivos móviles en Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md)



<!--HONumber=Nov16_HO5-->


