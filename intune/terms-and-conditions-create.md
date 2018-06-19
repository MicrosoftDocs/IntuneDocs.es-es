---
title: Definir los términos y condiciones en Microsoft Intune
titlesuffix: ''
description: Establezca los términos y condiciones que los usuarios ven en el Portal de empresa de Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 550d9c457335f212f0b60c16249e45f22f5baaf5
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31033307"
---
# <a name="manage-your-companys-terms-and-conditions-for-user-access"></a>Administrar los términos y condiciones de acceso de los usuarios de su empresa

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Como administrador de Intune, puede requerir que los usuarios acepten los términos y condiciones de la empresa antes de que puedan usar Portal de empresa para inscribir sus dispositivos y tener acceso a recursos, como correo electrónico y aplicaciones de la empresa. La configuración de términos y condiciones es opcional.

Puede crear varios conjuntos de términos y asignarlos a grupos distintos, como para admitir distintos lenguajes.

## <a name="create-terms-and-conditions"></a>Creación de términos y condiciones
Complete estos pasos para crear los términos y condiciones. El nombre para mostrar y la descripción son para uso administrativo mientras las propiedades de términos se muestran a los usuarios en el Portal de empresa.

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, elija **Inscripción de dispositivos** y, luego, **Términos y condiciones**.
2. Seleccione **Crear**.
![Captura de pantalla de Azure Portal que muestra el botón Crear para los términos y condiciones](media/terms-create-terms.png)
3. Especifique la información siguiente en el panel expandido:

   - **Nombre para mostrar**: nombre de los términos en Azure Portal. Los usuarios no ven este nombre.

   - **Descripción**: detalles opcionales que le ayudan a identificar este conjunto de términos en Azure Portal.

4. Seleccione la flecha situada junto a **Define terms of use** (Definir términos de uso) para abrir el panel Términos y condiciones y, luego, escriba la siguiente información:

   ![Captura de pantalla de la pantalla de aceptación de los Términos y condiciones por parte del usuario final, con un resumen de los términos](./media/terms-summary-create.png)

   - **Título**: el nombre de los términos que los usuarios ven en Portal de empresa de Intune sobre el **resumen**.
   - **Resumen de los términos**: texto que explica lo que significa que los usuarios acepten los términos. Por ejemplo, "Al inscribir el dispositivo, acepta los términos de uso establecidos por Contoso. Lea los términos detenidamente antes de continuar".
   - **Términos y condiciones**: los términos y condiciones que los usuarios ven y deben aceptar o rechazar.

5. Seleccione **Aceptar** y, luego, **Crear**.

## <a name="see-how-terms-are-displayed-to-your-users"></a>Cómo los usuarios ven los términos
El ejemplo siguiente muestra el **título** y el **resumen de términos** en la consola de administración y Portal de empresa de Intune.

![Captura de pantalla del título y el resumen de términos en la consola de administración y Portal de empresa de Intune.](./media/terms-summary-terms.png)

Los ejemplos siguientes muestran los términos y condiciones en la consola de administración y Portal de empresa de Intune.

![Captura de pantalla de los términos y condiciones en la consola de administración y Portal de empresa de Intune.](./media/terms-properties-terms.png)

## <a name="assign-terms-and-conditions"></a>Asignación de los términos y condiciones

Puede asignar términos y condiciones a grupos de usuarios que deben aceptarlos antes de usar el Portal de empresa.

1. En Azure Portal, elija **Inscripción de dispositivos** y, luego, elija **Términos y condiciones**.
2. En la lista de términos y condiciones, seleccione los términos que quiera asignar y, luego, seleccione **Administrar** > **Asignaciones**.
![Captura de pantalla del panel Asignar grupo de Azure Portal en la que se muestran los botones Seleccionar grupo y Seleccionar para la asignación de términos y condiciones](media/terms-assign-groups.png)
3. Haga clic en **Seleccionar grupos para incluir**, seleccione los grupos a los que quiera asignar los términos y, luego, haga clic en **Seleccionar**. No se pueden asignar términos y condiciones a los grupos dinámicos.
4. En el panel **Grupos asignados**, haga clic en **Guardar**.  Los términos y condiciones ahora están asociados a usuarios en los grupos seleccionados. La próxima vez que los usuarios accedan al portal de la empresa deberán aceptar los términos. Los términos y condiciones solo se deben aceptar una vez. No es necesario que los usuarios con varios dispositivos los acepten en cada uno de ellos.


## <a name="monitor-terms-and-conditions"></a>Supervisión de términos y condiciones

1. En Azure Portal, elija **Todos los servicios** > **Supervisión y administración** > **Intune**. 
1. En el panel Intune, elija **Inscripción de dispositivos** y, luego, **Términos y condiciones**.
2. En la lista de términos y condiciones, seleccione los términos para los que quiere ver la aceptación y, luego, seleccione **Informes de aceptación**.

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>Trabajar con varias versiones de los términos y las condiciones
Puede editar los términos y condiciones y administrar sus versiones. Se recomienda aumentar el número de versión y exigir aceptación cada vez que realice cambios importantes en los términos y condiciones. Si va a corregir errores tipográficos o cambiar el formato, por ejemplo, mantenga el número de versión actual.

1. En Azure Portal, elija **Todos los servicios** > **Supervisión y administración** > **Intune**.

2. En el panel Intune, elija **Inscripción de dispositivos**, **Términos y condiciones**, seleccione los términos y condiciones que quiera modificar y, luego, **Propiedades**.

4. En el panel **Propiedades**, seleccione **Términos y condiciones** y, luego, modifique el **Título**, el **Resumen de los términos** y los **Términos y condiciones**, según corresponda. Si los cambios hechos hacen que los usuarios tengan que volver a aceptar los términos nuevos, haga clic en **Solicite a los usuarios que acepten de nuevo los términos e incremente el número de versión a** 

4.  Seleccione **Aceptar** y, luego, **Guardar**.

Los usuarios solo deben aceptar una vez los términos y condiciones actualizados. No es necesarios que los usuarios con varios dispositivos acepten los términos y condiciones en cada uno de los dispositivos.
