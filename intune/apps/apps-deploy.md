---
title: Asignación de aplicaciones a grupos en Microsoft Intune
titleSuffix: ''
description: Aprenda a asignar una aplicación de Intune a grupos de usuarios o dispositivos mediante Microsoft Intune.
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
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e990cd94c0f8622d07e59b4130566a1dc2953a1c
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563993"
---
# <a name="assign-apps-to-groups-with-microsoft-intune"></a>Asignación de aplicaciones a grupos con Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Después de [agregar una aplicación](apps-add.md) a Microsoft Intune, puede asignarla a los usuarios y los dispositivos. Es importante que sepa que puede asignar una aplicación a un dispositivo tanto si el dispositivo está administrado por Intune como si no.

> [!NOTE]
> No se admite el intento de implementación disponible para grupos de dispositivos; solo se admiten grupos de usuarios.

En esta tabla se muestran las diversas opciones para asignar aplicaciones a usuarios y dispositivos:

|   | Dispositivos inscritos en Intune | Dispositivos no inscritos en Intune |
|-------------------------------------------------------------------------------------------|------------------------------|----------------------------------|
| Asignar a usuarios | Sí | Sí |
| Asignar a dispositivos | Sí | No |
| Asignar aplicaciones encapsuladas o aplicaciones que incorporan el SDK de Intune (para directivas de protección de aplicaciones) | Sí | Sí |
| Asignar aplicaciones como disponibles | Sí | Sí |
| Asignar aplicaciones como obligatorias | Sí | No |
| Desinstalar aplicaciones | Sí | No |
| Recibir actualizaciones de aplicaciones de Intune | Sí | No |
| Los usuarios finales instalan las aplicaciones disponibles desde la aplicación Portal de empresa | Sí | No |
| Los usuarios finales instalan las aplicaciones disponibles desde el Portal de empresa basado en web | Sí | Sí |

> [!NOTE]
> Actualmente, puede asignar aplicaciones iOS y Android (tanto de línea de negocio como compradas en la tienda) a dispositivos que no estén inscritos en Intune.
>
> Para recibir actualizaciones de aplicaciones en dispositivos que no están inscritos en Intune, los usuarios de los dispositivos deben dirigirse al Portal de empresa de su organización e instalar manualmente las actualizaciones de aplicaciones.

## <a name="assign-an-app"></a>Asignación de una aplicación

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Aplicaciones** > **Todas las aplicaciones**.
3. En el panel **Aplicaciones**, seleccione la aplicación que quiere asignar.
4. En la sección **Administrar** del menú, seleccione **Asignaciones**.
5. Seleccione **Agregar grupo** para abrir el panel **Agregar grupo** que está relacionado con la aplicación.
6. Para la aplicación específica, seleccione un **tipo de asignación**:
   - **Disponible para dispositivos inscritos**: se asigna la aplicación a grupos de usuarios que pueden instalar la aplicación desde la aplicación o el sitio web Portal de empresa.
   - **Disponible con o sin inscripción**: se asigna esta aplicación a grupos de usuarios cuyos dispositivos no se han inscrito en Intune. Se debe asignar a los usuarios una licencia de Intune; consulte [Licencias que incluyen Intune](../fundamentals/licenses.md).
   - **Requerido**: la aplicación se instala en los dispositivos de los grupos seleccionados. Algunas plataformas pueden tener mensajes adicionales para el usuario final para confirmar antes de que comience la instalación de la aplicación.
   - **Desinstalar**: La aplicación se desinstala de los dispositivos de los grupos seleccionados si Intune ha instalado la aplicación anteriormente en el dispositivo a través de una asignación "Disponible para dispositivos inscritos" o "Requerido" utilizando la misma implementación. Los vínculos web no se puede quitar después de la implementación.

     > [!NOTE]
     > **Solo para aplicaciones iOS**:
     > - Para configurar lo que sucede con las aplicaciones administradas cuando los dispositivos ya no se administran, puede seleccionar el valor previsto en **Desinstalar al eliminar el dispositivo**. Para más información, consulte [Configuración de desinstalación de aplicación para aplicaciones administradas de iOS](apps-deploy.md#app-uninstall-setting-for-ios-managed-apps).
     > - si ha creado un perfil de VPN para iOS que contiene la configuración de VPN por aplicación, puede seleccionarlo en **VPN**. Cuando se ejecuta la aplicación, se abre la conexión VPN. Para obtener más información, vea [Configuración de VPN para dispositivos iOS](../vpn-settings-ios.md).
     >
     > **Solo para aplicaciones Android**: si implementa una aplicación Android como **Disponible con o sin inscripción**, el estado de notificación solo estará disponible en los dispositivos inscritos.
     >
     > En **Disponible para dispositivos inscritos**: La aplicación solo se muestra como disponible si el usuario que inició sesión en el Portal de empresa es el usuario primario que inscribió el dispositivo y la aplicación es aplicable al dispositivo.

7. Para seleccionar los grupos de usuarios que resultan afectados por esta asignación de aplicaciones, seleccione **Grupos incluidos**.
8. Después de haber seleccionado uno o varios grupos para incluir, seleccione **Seleccionar**.
9. En el panel **Asignar**, seleccione **Aceptar** para completar la selección de grupos incluidos.
10. Si quiere excluir algún grupo de usuarios para que no se vea afectado por esta asignación de aplicaciones, seleccione **Excluir grupos**.
11. Si ha elegido excluir algún grupo, en **Seleccionar grupos**, seleccione **Seleccionar**.
12. En el panel **Agregar grupo**, seleccione **Aceptar**.
13. En el panel **Asignaciones** de la aplicación, seleccione **Guardar**.

La aplicación ahora se asigna a los grupos que ha seleccionado. Para obtener más información sobre cómo incluir y excluir asignaciones de aplicaciones, vea [Inclusión y exclusión de asignaciones de aplicaciones](apps-inc-exl-assignments.md).

## <a name="how-conflicts-between-app-intents-are-resolved"></a>Cómo se resuelven los conflictos entre las intenciones de aplicación

Se evita que un solo grupo se convierta en objetivo de múltiples intenciones de asignación de aplicaciones, pero si un usuario o un dispositivo es miembro de varios grupos a los que se les asignan diferentes intentos, se producirá un conflicto. No se recomienda crear conflictos de asignación entre aplicaciones.
La información de la tabla siguiente puede ayudarle a comprender la intención resultante cuando esto sucede:

| Intención del grupo 1 | Intención del grupo 2 | Intención resultante |
|-----------------------------------|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|Usuario Requerido|Usuario disponible|Requerido y Disponible|
|Usuario Requerido|Desinstalar usuario|Requerido|
|Usuario disponible|Desinstalar usuario|Desinstalar|
|Usuario Requerido|Dispositivo Requerido|Ambos existen, Intune trata los Requeridos
|Usuario Requerido|Desinstalar dispositivo|Ambos existen, Intune resuelve los Requeridos
|Usuario disponible|Dispositivo Requerido|Ambos existen, Intune resuelve los Requeridos (Requeridos y Disponibles)
|Usuario disponible|Desinstalar dispositivo|Ambos existen, Intune resuelve los Disponibles.<br><br>La aplicación se muestra en el Portal de empresa.<br><br>Si la aplicación ya está instalada (como una aplicación requerida con la intención anterior), entonces la aplicación se desinstala.<br><br>Si el usuario selecciona **Install from the Company Portal** (Instalar desde el Portal de empresa), la aplicación se instala y la intención de desinstalación no se respeta.|
|Desinstalar usuario|Dispositivo Requerido|Ambos existen, Intune resuelve los Requeridos|
|Desinstalar usuario|Desinstalar dispositivo|Ambos existen, se necesita resolver Intune como Desinstalar|
|Dispositivo Requerido|Desinstalar dispositivo|Requerido|
|Usuario Requerido y Disponible|Usuario disponible|Requerido y Disponible|
|Usuario Requerido y Disponible|Desinstalar usuario|Requerido y Disponible|
|Usuario Requerido y Disponible|Dispositivo Requerido|Ambas existen, Requeridas y Disponibles
|Usuario Requerido y Disponible|Desinstalar dispositivo|Ambos existen, Intune resuelve los Requeridos (Requeridos y Disponibles)
|Usuario disponible sin inscripción|Usuario Requerido y Disponible|Requerido y Disponible
|Usuario disponible sin inscripción|Usuario Requerido|Requerido
|Usuario disponible sin inscripción|Usuario disponible|Available|
|Usuario disponible sin inscripción|Dispositivo Requerido|Requerido y Disponible sin inscripción|
|Usuario disponible sin inscripción|Desinstalar dispositivo|Desinstalar y Disponible sin inscripción.<br><br>Si el usuario no ha instalado la aplicación desde el Portal de empresa, entonces se respeta la desinstalación.<br><br>Si el usuario instala la aplicación desde el Portal de empresa, entonces la instalación tiene prioridad sobre la desinstalación.|

> [!NOTE]
> Solo en el caso de aplicaciones administradas de la tienda de iOS, cuando agrega estas aplicaciones a Microsoft Intune y las asigna como **Requeridas**, se crean automáticamente con las intenciones **Requerida** y **Disponible**.<br><br>
> Las aplicaciones de la tienda de iOS (distintas de las aplicaciones VPP de iOS) que se asignan como destino con intención necesaria se aplicarán en el dispositivo en el momento del registro del dispositivo en el repositorio y también se mostrarán en la aplicación Portal de empresa.<br><br>
> Cuando se producen conflictos con el valor de **Desinstalar al eliminar el dispositivo**, la aplicación no se elimina del dispositivo cuando este ya no se administra.

## <a name="managed-google-play-app-deployment-to-unmanaged-devices"></a>Implementación de aplicaciones de Google Play administrado en dispositivos no administrados
En dispositivos Android, en un escenario de implementación de directiva de protección de aplicaciones sin inscripción (APP-WE), ahora puede usar Google Play administrado para implementar aplicaciones de la tienda y de línea de negocio (LOB) en los usuarios. Las aplicaciones de Google Play administrado dirigidas como **Disponible con o sin inscripción** aparecerán en la aplicación Play Store en el dispositivo del usuario final y no en la aplicación del Portal de empresa. El usuario final examinará e instalará las aplicaciones implementadas de esta manera desde la aplicación Play. Como las aplicaciones se instalan desde Google Play administrado, el usuario final no tiene que modificar la configuración del dispositivo para permitir la instalación de aplicaciones desde orígenes desconocidos, lo que significa que los dispositivos serán más seguros. Si el desarrollador de aplicaciones publica una nueva versión de una aplicación en Play que se instaló en el dispositivo de un usuario, Play actualizará la aplicación automáticamente. 

Pasos para asignar una aplicación de Google Play administrado a dispositivos no administrados:

1. Conecte su inquilino de Intune a Google Play administrado. Si ya lo ha hecho para administrar perfiles de trabajo de Android Enterprise o dispositivos dedicados o completamente administrados, omita este paso.
2. Agregue las aplicaciones de Google Play administrado a la consola de Intune.
3. Dirija las aplicaciones de Google Play administrado como **Disponible con o sin inscripción** al grupo de usuarios deseado. Los destinos de aplicaciones **Requerido** y **Desinstalar** no se admiten en dispositivos no inscritos.
4. Asigne una directiva de protección de aplicaciones al grupo de usuarios.
5. La próxima vez que los usuarios finales abran la aplicación del Portal de empresa, verán un mensaje que indica que hay aplicaciones disponibles para ellos en la aplicación Play Store.  El usuario puede pulsar sobre esta notificación para ir directamente a la aplicación Play y ver las aplicaciones corporativas, o puede desplazarse a la aplicación Play Store de forma independiente.
6. Los usuarios finales pueden expandir el menú contextual dentro de la aplicación Play Store y cambiar entre su cuenta personal de Google (donde verán sus aplicaciones personales) y su cuenta profesional (donde verán la tienda y las aplicaciones LOB dirigidas a ellos). Para instalar las aplicaciones, los usuarios finales pulsan Instalar en la aplicación Play Store.

Cuando se emite un borrado selectivo de aplicaciones en la consola de Intune, la cuenta profesional se quita automáticamente de la aplicación Play Store y, desde ese momento, el usuario final deja de ver aplicaciones de trabajo en el catálogo de aplicaciones de Play Store. Cuando se quita la cuenta profesional de un dispositivo, las aplicaciones instaladas desde Play Store seguirán instaladas en el dispositivo y no se desinstalarán. 

## <a name="app-uninstall-setting-for-ios-managed-apps"></a>Configuración de desinstalación de aplicación para aplicaciones administradas de iOS
En el caso de los dispositivos iOS, puede elegir lo que sucede con las aplicaciones administradas al anular la inscripción del dispositivo de Intune o quitar el perfil de administración con el valor de **Desinstalar al eliminar el dispositivo**. Este valor solo se aplica a las aplicaciones después de que el dispositivo se haya inscrito y las aplicaciones se hayan instalado como administradas. El valor no se puede configurar para aplicaciones web ni vínculos web. 

Los valores de configuración predeterminados se rellenan automáticamente para las nuevas asignaciones de la siguiente manera:

|Tipo de aplicación iOS | Valor predeterminado de la opción "Desinstalar al eliminar el dispositivo" |
|--------------------|----------------|
| Aplicación de línea de negocio | Sí |
| Aplicación de la tienda | No |
| Aplicación VPP | No |
| Aplicación integrada | No |

>[!NOTE]
>**Tipos de asignación "disponibles":** si actualiza esta configuración para los grupos "disponible para dispositivos inscritos" o "disponible con o sin inscripción", los usuarios que ya tienen la aplicación administrada no obtendrán la configuración actualizada hasta que no hayan sincronizado el dispositivo con Intune y vuelto a instalar la aplicación. 
>
>**Asignaciones ya existentes:** las asignaciones que existían antes de la introducción de esta configuración no se modifican y todas las aplicaciones administradas se quitarán de la administración del dispositivo.

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre la supervisión de las asignaciones de aplicaciones, consulte [Supervisión de las aplicaciones](apps-monitor.md).
