---
title: "Integración de Jamf Pro con Intune para cumplimiento"
titlesuffix: Azure portal
description: Use el cumplimiento para ayudar a proteger los dispositivos administrados por Jamf.
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6b37ffd23f8cf8764ba457b0803dfc308cf1c071
ms.sourcegitcommit: 82088d297eef629e3da6011681ead442ae7e25f7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2017
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Integración de Jamf Pro con Intune para cumplimiento

|Se aplica a: Intune en Azure Portal |
|--|
|¿Busca información sobre Intune en el portal clásico? [Vaya aquí](/intune/introduction-intune?toc=/intune-classic/toc.json).|
| |

|Actualmente en versión preliminar privada|
|--|
|Las características que se describen en este tema solo están disponibles para los clientes que dispongan actualmente de la versión preliminar privada. Este mensaje se eliminará cuando se haya publicado para todos los clientes.|
| |

Si la organización usa [Jamf Pro](https://www.jamf.com) para administrar los equipos Mac de los usuarios finales, puede usar las directivas de cumplimiento de Microsoft Intune con acceso condicional de Azure Active Directory para garantizar que los dispositivos de la organización son compatibles.

## <a name="prerequisites"></a>Requisitos previos

Necesitará lo siguiente para configurar el acceso condicional con Jamf Pro:

- Acceso a la versión preliminar privada de Intune para el acceso condicional de macOS
- Jamf Pro 10.1.0 o versiones posteriores
- [Aplicación Portal de empresa para macOS](https://aka.ms/macoscompanyportal)
- Dispositivos macOS con OS X 10.11 Yosemite o versiones posteriores

## <a name="connecting-intune-to-jamf-pro"></a>Conexión de Intune a Jamf Pro

Puede conectar Intune con Jamf Pro mediante la:

1. Creación de una aplicación nueva en Azure
2. Habilitación de Intune para su integración con Jamf Pro
3. Configuración del acceso condicional en Jamf Pro

## <a name="create-a-new-application-in-azure-active-directory"></a>Creación de una aplicación en Azure Active Directory

1. Abra **Azure Active Directory** > **Registro de aplicaciones**.
2. Haga clic en **+Nuevo registro de aplicaciones**.
3. Escriba un **nombre para mostrar**, como **Acceso condicional de Jamf**.
4. Seleccione **Web app / API** (API/aplicación web).
5. Especifique la **Dirección URL de inicio de sesión** de Jamf Pro.
6. Haga clic en **Crear aplicación**.
7. Guarde el **id. de aplicación** recién creado y, luego, abra **Toda la configuración** > **Claves** para crear una clave de aplicación nueva. Guarde la clave de aplicación.

  > [!NOTE]
  > La clave de aplicación solo aparece una vez durante este proceso. Asegúrese de guardarla donde pueda recuperarla fácilmente.

8. Navegue a **Toda la configuración** > **Acceso de API** > **Permisos necesarios** y elimine todos los permisos.

  > [!NOTE]
  > Agregue un permiso necesario nuevo. La aplicación solo puede funcionar correctamente si tiene el permiso necesario.

9.  Seleccione **API de Microsoft Intune** y haga clic en **Seleccionar**.
10. Elija **Send device attributes to Microsoft Intune** (Enviar atributos de dispositivo a Microsoft Intune) y haga clic en **Seleccionar**.
11. Haga clic en el botón **Conceder permisos** después de guardar los permisos necesarios para la aplicación.

  > [!NOTE]
  > Si la clave de aplicación expira, debe crear una clave de aplicación nueva en Microsoft Azure y luego actualizar los datos del acceso condicional en Jamf Pro. Azure permite tener activa tanto la clave anterior como la clave nueva para evitar las interrupciones del servicio.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Habilitación de Intune para su integración con Jamf Pro

1. En el portal de Microsoft Azure, abra **Microsoft Intune** > **Cumplimiento de dispositivos** > **Compliance Connector for Jamf** (Conector de cumplimiento para Jamf).
2. Habilite el conector de cumplimiento para Jamf. Para ello, pegue el id. de aplicación en el campo **Jamf Azure Active Directory App ID** (Id. de aplicación de Azure Active Directory para Jamf).
3. Haga clic en **Guardar**.

## <a name="configure-conditional-access-in-jamf-pro"></a>Configuración del acceso condicional en Jamf Pro

1. En Jamf Pro, navegue a **Administración global** > **Acceso condicional**. Haga clic en el botón **Editar** de la pestaña **Microsoft**.
2. Active la casilla de verificación para **habilitar el acceso condicional con Microsoft**.
3. Proporcione la información necesaria sobre el inquilino de Azure, incluida la **ubicación**, el **nombre de dominio**, el **id. de aplicación** y la **clave de aplicación** que guardó de los pasos anteriores.
4. Haga clic en **Guardar**. Jamf Pro proporcionará la configuración y comprobará el éxito.

## <a name="information-shared-from-jamf-pro-to-intune"></a>Información compartida de Jamf Pro a Intune

Jamf Pro captura la información de inventario sobre los dispositivos macOS administrados. Jamf Pro informa lo siguiente a Intune:

* Id. de Azure AD del dispositivo
* Estado del inventario JAMF (el estado de inventario de un equipo registrado con Jamf Pro en las últimas 24 horas)
* Versión del SO
* Id. de Azure AD del usuario
* Cifrado (FileVault 2)
* Estado del equipo selector
* Contraseña: número mínimo de conjuntos de caracteres
* Caducidad de contraseña (días)
* Tipo de contraseña: simple, alfanumérico o desconocido
* Evitar inicio de sesión automático
* Longitud necesaria del código de acceso
* Contraseña: número de contraseñas anteriores para impedir su reutilización
* Protección de la integridad del sistema
* Hora de última comprobación
* Tipo de arquitectura
* Ranuras de RAM disponibles
* Capacidad de la batería
* ROM de arranque
* Velocidad de bus
* Tamaño de caché
* Nombre del dispositivo
* Unión al dominio
* Id. de Jamf
* Dirección MAC
* Marca
* Modelo
* Identificador de modelo
* Velocidad de NIC
* Número de núcleos
* Número de procesadores
* Sistema operativo
* Plataforma
* Velocidad del procesador
* Tipo de procesador
* Dirección MAC secundaria
* Número de serie
* Versión de SMC
* RAM total
* UDID
* Correo electrónico del usuario

## <a name="next-steps"></a>Pasos siguientes

- [Aplicación de directivas de cumplimiento en los dispositivos administrados por Jamf](conditional-access-assign-jamf.md)