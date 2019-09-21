---
title: ¿Dónde está mi característica de Intune en Azure?
titleSuffix: Microsoft Intune
description: Le ayuda a encontrar características de Microsoft Intune en Azure Portal.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 1/4/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ac74cc547d13e92b87a8e148845ff1bc7be8efe4
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 09/20/2019
ms.locfileid: "71166988"
---
# <a name="where-did-my-intune-feature-go-in-azure"></a>¿Dónde está mi característica de Intune en Azure?
Hemos aprovechado la oportunidad para organizar algunas tareas de forma más lógica durante el traslado de Intune a Azure Portal. Pero, como ocurre con todas las mejoras, deberá aprender la nueva organización. Esta guía de referencia está dirigida a aquellos que están familiarizados con Intune en el portal clásico y se preguntan dónde se encuentra una determinada función en Intune en Azure Portal. Si en este artículo no se incluye una característica que intenta encontrar, deje un comentario al final para que podamos actualizarlo.
## <a name="quick-reference-guide"></a>Guía de referencia rápida

|Característica |Ruta de acceso del portal clásico|Ruta de acceso en Intune en Azure Portal|
|------------|---------------|---------------|
|Programa de inscripción de dispositivos (DEP) [solo iOS]|Administración > Administración de dispositivos móviles > iOS > Programa de inscripción de dispositivos|[Inscripción de dispositivos > Inscripción de Apple > Token del Programa de inscripción](#where-did-apple-dep-go) |
|Programa de inscripción de dispositivos (DEP) [solo iOS]| Administración > Administración de dispositivos móviles > iOS y Mac OS X > Programa de inscripción de dispositivos |[Inscripción de dispositivos > Inscripción de Apple > Números de serie del Programa de inscripción](#where-did-apple-dep-go) |
|Reglas de inscripción |Administración > Administración de dispositivos móviles > Reglas de inscripción|[Inscripción de dispositivos > Restricciones de inscripción](#where-did-enrollment-rules-go) |
|Grupos mediante número de serie de iOS |Grupos > Todos los dispositivos > Dispositivos corporativos inscritos previamente > Mediante número de serie de iOS|[Inscripción de dispositivos > Inscripción de Apple > Números de serie del Programa de inscripción](#where-did-corporate-pre-enrolled-devices-go) |
|Grupos mediante número de serie de iOS |Grupos > Todos los dispositivos > Dispositivos corporativos inscritos previamente > Mediante número de serie de iOS| [Inscripción de dispositivos > Inscripción de Apple > Números de serie de AC](#where-did-corporate-pre-enrolled-devices-go)|
|Grupos mediante IMEI (todas las plataformas)| Grupos > Todos los dispositivos > Dispositivos corporativos inscritos previamente > Mediante IMEI (todas las plataformas) | [Inscripción de dispositivos > Identificadores de dispositivo corporativos](#by-imei-all-platforms)|
| Perfil de inscripción de dispositivos corporativos| Directiva > Inscripción de dispositivos corporativos | [Inscripción de dispositivos > Inscripción de Apple > Perfiles del Programa de inscripción](#where-did-corporate-pre-enrolled-devices-go) |
| Perfil de inscripción de dispositivos corporativos | Directiva > Inscripción de dispositivos corporativos | [Inscripción de dispositivos > Inscripción de Apple > Perfiles de AC](#where-did-corporate-pre-enrolled-devices-go) |
| Android for Work | Administración > Administración de dispositivos móviles > Android for Work | Inscripción de dispositivos > Inscripción en Android |
| Términos y condiciones | Directiva > Términos y condiciones | Inscripción de dispositivos > Términos y condiciones |
Configuración del Portal de empresa|Admin > Portal de empresa|**Administrar** > Aplicaciones móviles<br> **Configurar** > Personalización de marca del Portal de empresa


## <a name="where-do-i-manage-groups"></a>¿Dónde se administran los grupos?
Intune en Azure Portal usa [Azure Active Directory (AD)](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal) para administrar grupos.

## <a name="where-did-enrollment-rules-go"></a>¿Dónde están las reglas de inscripción?
En el portal clásico, podía establecer reglas que controlaran la inscripción de MDM de dispositivos macOS y Windows móviles y modernos.

![Imagen de reglas de inscripción de dispositivos móviles clásicas](./media/01-classic-rules.png)

Estas reglas se aplicaban a todos los usuarios de su cuenta de Intune sin excepciones. En Azure Portal estas reglas aparecen ahora en dos tipos de directivas distintas: Restricciones de tipo de dispositivo y Restricciones de límite de dispositivos.

![Imagen de restricciones de inscripción de dispositivos móviles de Azure](./media/02-azure-enroll-restrictions.png)

El valor predeterminado de Restricción de límite de dispositivos corresponde al Límite de inscripción de dispositivos del portal clásico.

![Imagen de restricciones de límite de dispositivos de Azure](./media/03-azure-device-limit.png)

El valor predeterminado de Restricciones de tipo de dispositivo corresponde a las Restricciones de la plataforma del portal clásico.

![Imagen de restricciones de tipo de dispositivo de Azure](./media/04-azure-platform-restrictions.png)

La capacidad de permitir o bloquear dispositivos de propiedad personal se administra ahora en las Configuraciones de plataforma de Restricciones de tipo de dispositivo.

![Imagen de la configuración de bloqueo de dispositivos personales de Azure](./media/05-azure-personal-block.png)

Se agregarán nuevas capacidades de restricción únicamente a Azure Portal.

## <a name="where-did-my-conditional-access-policies-go"></a>¿Dónde puedo encontrar mis directivas de acceso condicional?
Las directivas de acceso condicional del inquilino se seguirán aplicando cuando el inquilino se haya migrado a Azure Portal. Sin embargo, no podrá ver o modificarlas desde Intune en Azure Portal.

Si quiere ver y modificar las directivas de acceso condicional desde Azure Portal, deberá quitar del portal clásico las directivas anteriores. Después, deberá volver a crearlas en Azure Portal. Para obtener más información sobre la migración de directivas de acceso condicional, vea [Migración de directivas clásicas en Azure Portal](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-migration). 

## <a name="where-did-my-compliance-policies-go"></a>¿Dónde puedo encontrar mis directivas de cumplimiento?
Las directivas de cumplimiento del inquilino se seguirán aplicando cuando el inquilino se haya migrado a Azure Portal. Sin embargo, no podrá ver o modificarlas desde Intune en Azure Portal.

Si quiere ver y modificar las directivas de cumplimiento desde Azure Portal, deberá quitar del portal clásico las directivas anteriores. Después, deberá volver a crearlas en Azure Portal. Para obtener más información sobre las directivas de cumplimiento de dispositivos, consulte la [introducción a las directivas de cumplimiento de dispositivos en Intune](device-compliance-get-started.md). 

## <a name="where-did-apple-dep-go"></a>¿Dónde está el servicio DEP de Apple?
En el portal clásico, podía configurar Intune para que se integrara con el Programa de inscripción de dispositivos de Apple y solicitar manualmente la sincronización con el servicio de Apple:

![Imagen del token de DEP clásico](./media/06-classic-dep-token.png)

En Azure Portal, configure el Programa de inscripción de dispositivos de Apple siguiendo los mismos pasos que en la consola clásica de Intune:

![Imagen del token de DEP de Azure](./media/07-azure-dep-token.png)

En cambio, la opción **Sincronizar** del portal clásico se ha movido al flujo de trabajo de administración de número de serie, puesto que los resultados de una sincronización manual aparecen ahí:

![Imagen de la sincronización de DEP de Azure](./media/08-azure-dep-sync.png)

## <a name="where-did-corporate-pre-enrolled-devices-go"></a>¿Dónde están los dispositivos corporativos inscritos previamente?
### <a name="by-ios-serial-number"></a>Mediante número de serie de iOS
En el portal clásico, puede inscribir dispositivos iOS mediante el Programa de inscripción de dispositivos (DEP) de Apple y la herramienta Apple Configurator. Ambos métodos ofrecen la inscripción previa de dispositivos mediante número de serie e implican la asignación de perfiles de inscripción de dispositivos corporativos especiales. Antes de la inscripción, se puede administrar la asignación de perfiles de inscripción a través del grupo de dispositivos **Dispositivos corporativos inscritos previamente mediante número de serie de iOS**:

![Imagen de números de serie de Apple clásicos](./media/09-classic-apple-serials.png)

Este enumera los números de serie para la inscripción de DEP de Apple y Configurator en una sola lista. Para reducir los errores de coincidencia en la asignación de perfiles (de perfil DEP al número de serie de CA y viceversa), hemos separado los números de serie en dos listas en Azure Portal:

**Números de serie de DEP**
![Imagen de números de serie de DEP de Azure](./media/10-azure-dep-serials.png)

**Números de serie de Apple Configurator**
![Imagen de números de serie de Apple Configurator de Azure](./media/11-azure-ac-serials.png)

### <a name="by-imei-all-platforms"></a>Mediante IMEI (todas las plataformas)

En el portal clásico, puede enumerar previamente los números IMEI de los dispositivos para marcarlos como corporativos cuando se inscriben en Intune:

![Imagen de la lista clásica de números IMEI](./media/12-classic-corp-imei.png)

En Azure Portal, debe cargar los mismos IMEI a la lista Identificadores de dispositivo corporativos con un archivo de valores separados por comas (CSV). El nuevo portal no admite la entrada manual de números IMEI:

![Imagen de la lista de Azure de números IMEI](./media/13-azure-corp-imei.png)

Intune en Azure Portal está preparado para el futuro, puesto que será compatible con otros tipos de identificadores aparte de IMEI, aunque actualmente solo admite números IMEI en las listas previas.

## <a name="where-did-corporate-device-enrollment-profiles-go"></a>¿Dónde están los perfiles de inscripción de dispositivos corporativos?
Para inscribir dispositivos iOS a través del Programa de inscripción de dispositivos de Apple o con la herramienta Apple Configurator, debe proporcionar un perfil de inscripción de dispositivos corporativos para asignar al dispositivo. En el portal clásico, la creación y administración de estos perfiles se encontraba en una sola lista:

![Imagen de perfiles de inscripción de dispositivos clásicos](./media/14-classic-corp-profiles.png)

En esta lista se muestran los perfiles habilitados para su uso con el Programa de inscripción de dispositivos de Apple (**DEP Activado**) y los perfiles habilitados solo para su uso con la herramienta Apple Configurator (**DEP Desactivado**).

Para reducir la confusión entre los dos tipos de perfiles y los posibles errores de coincidencia de asignaciones (perfil de DEP a dispositivos de Configurator y viceversa), hemos separado la creación y la administración de los perfiles del programa de inscripción (compatible con el Programa de inscripción de dispositivos de Apple y Apple School Manager) y los perfiles de Apple Configurator:

**Perfiles de DEP**
![Imagen de perfiles de DEP de Azure](./media/15-azure-dep-profiles.png)

**Perfiles de Apple Configurator**
![Imagen de perfiles de Apple Configurator de Azure](./media/16-azure-ac-profiles.png)
