---
title: Administrar aplicaciones de la Tienda Windows para empresas | Microsoft Intune
description: Conecte Microsoft Intune a la Tienda Windows para empresas si desea administrar e implementar aplicaciones adquiridas por volumen desde la consola de Intune.
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e38d47d-0c5e-40ce-b379-29d3657f5c28
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6716a3d1fb53dc3de0189f637d5664d0a2023d05
ms.openlocfilehash: 07079b6566bec45593bb9ae49272aa7154a7174d


---

# Administrar las aplicaciones adquiridas a través de la Tienda Windows para empresas con Microsoft Intune
En la [Tienda Windows para empresas](https://www.microsoft.com/business-store) puede buscar y comprar aplicaciones para su organización, tanto sueltas como en lote. Si conecta la tienda a Microsoft Intune, podrá administrar aplicaciones adquiridas en lote desde la consola de Intune, por ejemplo:
* Puede sincronizar la lista de aplicaciones que ha adquirido en la tienda con Intune.
* Las aplicaciones que se sincronizan aparecen en la consola de administración de Intune y puede implementarlas igual que el resto de las aplicaciones.
* Puede controlar el número de licencias disponibles y las que se usan en la consola de administración de Intune.
* Intune bloquea la implementación e instalación de aplicaciones si no hay suficientes licencias disponibles.

## Antes de empezar
Revise la información siguiente antes de iniciar la sincronización y la implementación de aplicaciones de la Tienda Windows para empresas:
* Debe configurar Intune como la entidad de administración de dispositivos móviles de su organización. Para más información, consulte [Preparar la inscripción de dispositivos en Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md).
* Debe haber registrado una cuenta en la Tienda Windows para empresas.
* Una vez que haya asociado una cuenta de la Tienda Windows para empresas con Intune, no podrá cambiar a otra cuenta en el futuro.
* Las aplicaciones adquiridas en la tienda no se pueden agregar ni eliminar manualmente en Intune. Solo se pueden sincronizar con la Tienda Windows para empresas.
* Intune solo sincroniza las aplicaciones con licencia en línea que ha comprado en la Tienda Windows para empresas.
* Los dispositivos deben estar unidos al dominio de Active Directory o al área de trabajo para usar esta función.
* Los dispositivos inscritos deben usar la versión 1511 de Windows 10.

## Asociar su cuenta de la Tienda Windows para empresas con Intune
Antes de habilitar la sincronización en la consola de Intune, debe configurar la cuenta de la tienda para usar Intune como herramienta de administración:
1. Asegúrese de que inicia sesión en la Tienda para empresas con la misma cuenta de inquilino que usa para iniciar sesión en Intune.
2. En la Tienda para empresas, seleccione **Configuración** > **Herramientas de administración**.
3. En la página de herramientas de administración, seleccione **Add a management tool** (Agregar una herramienta de administración) y elija Microsoft Intune.

Ya puede continuar y configurar la sincronización en la consola de Intune.

## Configurar la sincronización

1. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), haga clic en **Administración**.
2. En el área de trabajo **Administración**, expanda **Administración de dispositivos móviles** y haga clic en **Tienda para empresas**.
3. En la página **Tienda Windows para empresas**, haga lo siguiente:
* Si aún no lo ha hecho, haga clic en el vínculo para registrarse en la Tienda Windows para empresas.
* Cuando se haya registrado, haga clic en **Configurar sincronización**.
4. En el cuadro de diálogo **Configurar la sincronización de aplicaciones de la Tienda Windows para empresas**, seleccione **Habilitar la sincronización de la Tienda Windows para empresas**.
5. En la lista desplegable **Idioma**, elija el idioma en el que las aplicaciones de la Tienda Windows para empresas se mostrarán en la consola de Intune. Independientemente del idioma en el que se muestren, se instalarán en el idioma del usuario final si esa versión está disponible.
6. Haga clic en **Aceptar**.

## Sincronizar aplicaciones

1. En la página **Tienda Windows para empresas**, haga clic en **Sincronizar ahora** para sincronizar las aplicaciones que ha comprado en la tienda con Intune.
2. En el área de trabajo **Aplicaciones**, haga clic en **Software administrado** > **Software con licencia** para ver las aplicaciones disponibles y comprobar que las aplicaciones adquiridas se importaron correctamente.
Las aplicaciones de este nodo se muestran con el número total de licencias que posee, junto con la cantidad de licencias que tiene disponibles.

## Implementación de aplicaciones

Las aplicaciones de la tienda se implementan igual que cualquier otra aplicación de Intune. Para obtener más información, consulte [Deploy apps in Microsoft Intune](deploy-apps-in-microsoft-intune.md) (Implementar aplicaciones en Microsoft Intune).
Al implementar una aplicación de la Tienda Windows para empresas, cada usuario que instala la aplicación utiliza una licencia. Si utiliza todas las licencias disponibles para una aplicación implementada, no podrá implementar más copias y deberá realizar una de las siguientes acciones:
* Desinstalar la aplicación de algunos dispositivos
* Reducir el ámbito de la implementación actual y restringirla a los usuarios para los que haya suficientes licencias
* Comprar más copias de la aplicación en la Tienda Windows para empresas


### Consulte también
[Agregar aplicaciones a dispositivos móviles en Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md)





<!--HONumber=Jul16_HO4-->


