---
title: Integración de Jamf Pro con Microsoft Intune para cumplimiento
titleSuffix: Microsoft Intune
description: Use directivas de cumplimiento de Microsoft Intune con acceso condicional de Azure Active Directory para ayudar a proteger los dispositivos administrados por Jamf.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 57527d0b1825d0e8d3fefb63d1b960ab3fb5c676
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "59569485"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Integración de Jamf Pro con Intune para cumplimiento

Se aplica a: Intune en el portal de Azure

Si la organización usa [Jamf Pro](https://www.jamf.com) para administrar los equipos Mac de los usuarios finales, puede usar las directivas de cumplimiento de Microsoft Intune con acceso condicional de Azure Active Directory para garantizar que los dispositivos de la organización son compatibles.

## <a name="prerequisites"></a>Requisitos previos

Necesitará lo siguiente para configurar el acceso condicional con Jamf Pro:

- Jamf Pro 10.1.0 o versiones posteriores
- [Aplicación Portal de empresa para macOS](https://aka.ms/macoscompanyportal)
- Dispositivos macOS con OS X 10.11 Yosemite o versiones posteriores

## <a name="connecting-intune-to-jamf-pro"></a>Conexión de Intune a Jamf Pro

Para conectar Intune con Jamf Pro, siga estos pasos:

1. Creación de una aplicación en Azure.
2. Habilitación de Intune para su integración con Jamf Pro
3. Configuración del acceso condicional en Jamf Pro

## <a name="create-an-application-in-azure-active-directory"></a>Creación de una aplicación en Azure Active Directory

1. En [Azure Portal](https://portal.azure.com), vaya a **Azure Active Directory** > **Registros de aplicaciones**.
2. Haga clic en **+Nuevo registro de aplicaciones**.
3. Escriba un **nombre para mostrar**, como **Acceso condicional de Jamf**.
4. Seleccione **Web app / API** (API/aplicación web).
5. Especifique la **Dirección URL de inicio de sesión** con la dirección URL de la instancia de Jamf Pro.
6. Seleccione **Crear**. Se crea la aplicación y el portal presenta los detalles de esta.
7. Guarde una copia del **Identificador de la aplicación** de la nueva aplicación. Tendrá que especificar este identificador en un procedimiento posterior. Después, seleccione **Configuración** y vaya a **Acceso de API** > **Claves**.
8. En el panel *Claves*, especifique una **Descripción**, cuánto tiempo debe esperar antes de que **Expire** y, después, haga clic en **Guardar** para generar la clave de aplicación (valor).

   > [!IMPORTANT]
   > La clave de aplicación solo aparece una vez durante este proceso. Asegúrese de guardarla donde pueda recuperarla fácilmente.

8. En el panel *Configuración* de la aplicación, vaya a **Acceso de API** > **Permisos necesarios**. Seleccione los permisos existentes y después haga clic en **Eliminar** y elimínelos todos. Eliminar los permisos existentes es necesario, ya que agregará un nuevo permiso y la aplicación solo funciona si tiene un único permiso necesario.  
9. Para asignar un nuevo permiso, seleccione **+ Agregar** > **Seleccionar una API** > **Microsoft Intune API** (API de Microsoft Intune) y después haga clic en **Seleccionar**.
10. En el panel *Habilitar acceso*, seleccione **Send device attributes to Microsoft Intune** (Enviar atributos del dispositivo a Microsoft Intune), haga clic en **Seleccionar** y luego en **Listo**.
11. En el panel *Permisos necesarios*, haga clic en **Conceder permisos** y después en **Sí** para aplicar los permisos necesarios a la aplicación.

    > [!NOTE]
    > Si la clave de aplicación expira, debe crear una clave de aplicación nueva en Microsoft Azure y luego actualizar los datos del acceso condicional en Jamf Pro. Azure permite tener activa tanto la clave anterior como la clave nueva para evitar las interrupciones del servicio.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Habilitación de Intune para su integración con Jamf Pro

1. En [Azure Portal](https://portal.azure.com), vaya a **Microsoft Intune** > **Cumplimiento de dispositivos** > **Partner device management** (Administración de dispositivos de asociados).
2. Habilite el conector de cumplimiento para Jamf. Para ello, pegue el identificador de la aplicación que ha guardado en el procedimiento anterior en el campo **Jamf Azure Active Directory App ID** (Id. de aplicación de Azure Active Directory para Jamf).
3. Seleccione **Guardar**.

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Configurar la integración de Microsoft Intune en Jamf Pro

1. En Jamf Pro, navegue a **Administración global** > **Acceso condicional**. Haga clic en el botón **Editar** de la pestaña **Integración de Microsoft Intune**.
2. Active la casilla **Habilitar integración de Microsoft Intune**.
3. Proporcione la información necesaria sobre el inquilino de Azure, incluida la **ubicación**, el **nombre de dominio**, el **id. de aplicación** y la **clave de aplicación** que guardó de los pasos anteriores.
4. Seleccione **Guardar**. Jamf Pro probará la configuración y confirmará que sea correcta.

## <a name="set-up-compliance-policies-and-register-devices"></a>Configurar directivas de cumplimiento y registrar dispositivos

Después de configurar la integración entre Intune y Jamf, tiene que [aplicar directivas de cumplimiento en los dispositivos administrados por Jamf](conditional-access-assign-jamf.md).



## <a name="next-steps"></a>Pasos siguientes

- [Aplicación de directivas de cumplimiento en los dispositivos administrados por Jamf](conditional-access-assign-jamf.md)
- [Datos que Jamf envía a Intune](data-jamf-sends-to-intune.md)
