---
title: Asignación de aplicaciones a grupos en Microsoft Intune
titlesuffix: ''
description: Aprenda a asignar una aplicación de Intune a grupos de usuarios o dispositivos.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 06/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1e6ffd31e35637cf722fc2af486be4bd9101c1db
ms.sourcegitcommit: 413d271b42a6d4396adc2f749e31eed782aaa9da
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2018
ms.locfileid: "38993758"
---
# <a name="assign-apps-to-groups-with-microsoft-intune"></a>Asignación de aplicaciones a grupos con Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Después de [agregar una aplicación](apps-add.md) a Microsoft Intune, puede asignarla a los usuarios y los dispositivos. Es importante que sepa que puede asignar una aplicación a un dispositivo tanto si el dispositivo está administrado por Intune como si no. 

En esta tabla se muestran las diversas opciones para asignar aplicaciones a usuarios y dispositivos:

||||
|-|-|-|-|
|&nbsp;|**Dispositivos inscritos en Intune**|**Dispositivos no inscritos en Intune**|
|Asignar a usuarios|Sí|Sí|
|Asignar a dispositivos|Sí|No|
|Asignar aplicaciones encapsuladas o aplicaciones que incorporan el SDK de Intune (para directivas de protección de aplicaciones)|Sí|Sí|
|Asignar aplicaciones como disponibles|Sí|Sí|
|Asignar aplicaciones como obligatorias|Sí|No|
|Desinstalar aplicaciones|Sí|No|
|Recibir actualizaciones de aplicaciones de Intune|Sí|No|
|Los usuarios finales instalan las aplicaciones disponibles desde la aplicación Portal de empresa|Sí|No|
|Los usuarios finales instalan las aplicaciones disponibles desde el Portal de empresa basado en web|Sí|Sí|

> [!NOTE]
> Actualmente, puede asignar aplicaciones iOS y Android (tanto de línea de negocio como compradas en la tienda) a dispositivos que no estén inscritos en Intune.
>
> Para recibir actualizaciones de aplicaciones en dispositivos que no están inscritos en Intune, los usuarios de los dispositivos deben dirigirse al Portal de empresa de su organización e instalar manualmente las actualizaciones de aplicaciones.

## <a name="to-assign-an-app"></a>Asignación de una aplicación

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el menú **Intune**, seleccione **Aplicaciones móviles**.
4. En la sección **Administrar** del menú, seleccione **Aplicaciones**.
5. En el panel **Aplicaciones**, seleccione la aplicación que quiere asignar.
6. En la sección **Administrar** del menú, seleccione **Asignaciones**.
7. Seleccione **Agregar grupo** para abrir el panel **Agregar grupo** que está relacionado con la aplicación.
8. Para la aplicación específica, seleccione un **tipo de asignación**:
   - **Available for enrolled devices** (Disponible para dispositivos inscritos): los usuarios instalan la aplicación desde la aplicación o el sitio web del Portal de empresa.
   - **Available with or without enrollment** (Disponible con o sin inscripción): se asigna esta aplicación a grupos de usuarios cuyos dispositivos no se han inscrito en Intune. Las aplicaciones de Google Play administrado no admiten esta opción. 
   - **Requerida**: la aplicación se instala en los dispositivos de los grupos seleccionados.
   - **Desinstalar**: la aplicación se desinstala de dispositivos de los grupos seleccionados.

     > [!NOTE]
     > **Solo para aplicaciones iOS**: si ha creado un perfil de VPN para iOS que contiene la configuración de VPN por aplicación, puede seleccionarlo en **VPN**. Cuando se ejecuta la aplicación, se abre la conexión VPN. Para obtener más información, vea [Configuración de VPN para dispositivos iOS](vpn-settings-ios.md).

9. Para seleccionar los grupos de usuarios que resultan afectados por esta asignación de aplicaciones, seleccione **Grupos incluidos**.
10. Después de haber seleccionado uno o varios grupos para incluir, seleccione **Seleccionar**.
11. En el panel **Asignar**, seleccione **Aceptar** para completar la selección de grupos incluidos.
12. Si quiere excluir algún grupo de usuarios para que no se vea afectado por esta asignación de aplicaciones, seleccione **Excluir grupos**.
13. Si ha elegido excluir algún grupo, en **Seleccionar grupos**, seleccione **Seleccionar**.
14. En el panel **Agregar grupo**, seleccione **Aceptar**.
15. En el panel **Asignaciones** de la aplicación, seleccione **Guardar**.

La aplicación ahora se asigna a los grupos que ha seleccionado. Para obtener más información sobre cómo incluir y excluir asignaciones de aplicaciones, vea [Inclusión y exclusión de asignaciones de aplicaciones](apps-inc-exl-assignments.md).

## <a name="how-conflicts-between-app-intents-are-resolved"></a>Cómo se resuelven los conflictos entre las intenciones de aplicación

A veces, la misma aplicación se asigna a varios grupos, pero con diferentes intenciones. La información de la tabla siguiente puede ayudarle a comprender la intención resultante cuando esto sucede:

||||
|-|-|-|
|**Intención del grupo 1**|**Intención del grupo 2**|**Intención resultante**|
|Usuario Requerido|Usuario disponible|Requerido y Disponible|
|Usuario Requerido|Usuario no disponible|Requerido|
|Usuario Requerido|Desinstalar usuario|Requerido|
|Usuario disponible|Usuario no disponible|No disponible|
|Usuario disponible|Desinstalar usuario|Desinstalar|
|Usuario no disponible|Desinstalar usuario|Desinstalar
|Usuario Requerido|Dispositivo Requerido|Ambas existen, la puerta de enlace trata las Requeridas
|Usuario Requerido|Desinstalar dispositivo|Ambas existen, la puerta de enlace resuelve las Requeridas
|Usuario disponible|Dispositivo Requerido|Ambas existen, la puerta de enlace resuelve las Requeridas (Requeridas y Disponibles)
|Usuario disponible|Desinstalar dispositivo|Ambas existen, la puerta de enlace resuelve las Disponibles.<br><br>La aplicación se muestra en el Portal de empresa.<br><br>Si la aplicación ya está instalada (como una aplicación requerida con la intención anterior), entonces la aplicación se desinstala.<br><br>Si el usuario selecciona **Install from the Company Portal** (Instalar desde el Portal de empresa), la aplicación se instala y la intención de desinstalación no se respeta.|
|Usuario no disponible|Dispositivo Requerido|Requerido|
|Usuario no disponible|Desinstalar dispositivo|Desinstalar|
|Desinstalar usuario|Dispositivo Requerido|Ambas existen, la puerta de enlace resuelve las Requeridas|
|Desinstalar usuario|Desinstalar dispositivo|Ambos existen, se necesita resolver la puerta de enlace como Desinstalar|
|Dispositivo Requerido|Desinstalar dispositivo|Requerido|
|Usuario Requerido y Disponible|Usuario disponible|Requerido y Disponible|
|Usuario Requerido y Disponible|Desinstalar usuario|Requerido y Disponible|
|Usuario Requerido y Disponible|Usuario no disponible|Requerido y Disponible|
|Usuario Requerido y Disponible|Dispositivo Requerido|Ambas existen, Requeridas y Disponibles
|Usuario Requerido y Disponible|Dispositivo no disponible|Requerido y Disponible|
|Usuario Requerido y Disponible|Desinstalar dispositivo|Ambas existen, la puerta de enlace resuelve las Requeridas (Requeridas y Disponibles)
|Usuario no disponible|Dispositivo no disponible|No disponible|
|Usuario disponible|Dispositivo no disponible|Available|
|Usuario Requerido|Dispositivo no disponible|Requerido|
|Usuario disponible sin inscripción|Usuario Requerido y Disponible|Requerido y Disponible
|Usuario disponible sin inscripción|Usuario Requerido|Requerido
|Usuario disponible sin inscripción|Usuario no disponible|No disponible
|Usuario disponible sin inscripción|Usuario disponible|Available|
|Usuario disponible sin inscripción|Dispositivo Requerido|Requerido y Disponible sin inscripción|
|Usuario disponible sin inscripción|Dispositivo no disponible|Disponible sin inscripción|
|Usuario disponible sin inscripción|Desinstalar dispositivo|Desinstalar y Disponible sin inscripción.<br><br>Si el usuario no ha instalado la aplicación desde el Portal de empresa, entonces se respeta la desinstalación.<br><br>Si el usuario instala la aplicación desde el Portal de empresa, entonces la instalación tiene prioridad sobre la desinstalación.|

> [!NOTE]
> Solo en el caso de aplicaciones administradas de la tienda de iOS, cuando agrega estas aplicaciones a Microsoft Intune y las asigna como **Requeridas**, se crean automáticamente con las intenciones **Requerida** y **Disponible**.<br><br>
> Las aplicaciones de la tienda de iOS (distintas de las aplicaciones VPP de iOS) que se asignan como destino con intención necesaria se aplicarán en el dispositivo en el momento del registro del dispositivo en el repositorio y también se mostrarán en la aplicación Portal de empresa.

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre la supervisión de las asignaciones de aplicaciones, consulte [Supervisión de las aplicaciones](apps-monitor.md).
