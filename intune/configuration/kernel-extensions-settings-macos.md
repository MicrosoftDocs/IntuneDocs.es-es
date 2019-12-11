---
title: configuración de la extensión de kernel de macOS en Microsoft Intune-Azure | Microsoft Docs
titleSuffix: ''
description: Agregue, configure o cree configuraciones en dispositivos macOS para usar las extensiones de kernel. Además, permita a los usuarios invalidar las extensiones aprobadas, permitir todas las extensiones de un identificador de equipo o permitir extensiones o aplicaciones específicas en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8632f5b8df0f483de3bb4d06a6823639ba52c604
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506700"
---
# <a name="macos-device-settings-to-configure-and-use-kernel-extensions-in-intune"></a>configuración de dispositivos macOS para configurar y usar las extensiones de kernel en Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

En este artículo se enumeran y describen los diferentes valores de configuración de la extensión kernel que se pueden controlar en los dispositivos macOS. Como parte de la solución de administración de dispositivos móviles (MDM), use esta configuración para agregar y administrar extensiones de kernel en los dispositivos.

Para obtener más información sobre las extensiones de kernel en Intune y los requisitos previos, consulte [Agregar extensiones de kernel de MacOS](../kernel-extensions-overview-macos.md).

Estos valores se agregan a un perfil de configuración de dispositivo en Intune y luego se asignan o implementan en los dispositivos macOS.

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración de extensiones de kernel de dispositivo](../kernel-extensions-overview-macos.md).

> [!NOTE]
> Esta configuración se aplica a diferentes tipos de inscripción. Para obtener más información sobre los diferentes tipos de inscripción, consulte [inscripción de MacOS](../macos-enroll.md).

## <a name="kernel-extensions"></a>Extensiones de kernel

### <a name="settings-apply-to-user-approved-automated-device-enrollment"></a>La configuración se aplica a: inscripción de dispositivos automatizada y aprobados por el usuario

- **Permitir invalidaciones de usuario**: **permitir** permite a los usuarios aprobar extensiones de kernel no incluidas en el perfil de configuración. **No configurado** (valor predeterminado) impide que los usuarios permitan extensiones no incluidas en el perfil de configuración. Es decir, solo se permiten las extensiones incluidas en el perfil de configuración.

  Consulte [carga de extensión de kernel aprobada](https://developer.apple.com/library/archive/technotes/tn2459/_index.html) por el usuario (abre el sitio web de Apple) para obtener más información sobre esta característica.

- **Identificadores de equipo permitidos**: Use esta opción para permitir uno o varios identificadores de equipo. Todas las extensiones de kernel firmadas con los identificadores de equipo que especifique están permitidas y son de confianza. En otras palabras, use esta opción para permitir todas las extensiones de kernel dentro del mismo ID. de equipo, que puede ser un desarrollador o asociado específico.

  **Agregue** un identificador de equipo de extensiones de kernel válidas y firmadas que desee cargar. Puede agregar varios identificadores de equipo. El identificador de equipo debe ser alfanumérico (letras y números) y tener 10 caracteres. Por ejemplo, escriba `ABCDE12345`.

  Después de agregar un identificador de equipo, también se puede eliminar.

  [Busque el identificador del equipo](https://help.apple.com/developer-account/#/dev55c3c710c) (abre el sitio web de Apple).

- **Extensiones de kernel permitidas**: Use esta opción para permitir extensiones de kernel específicas. Solo se permite o se confía en las extensiones de kernel que especifique. 

  **Agregue** el identificador de lote y el identificador de equipo de una extensión de kernel que desee cargar. En el caso de las extensiones de kernel heredadas sin firmar, use un identificador de equipo vacío. Puede agregar varias extensiones de kernel. El identificador de equipo debe ser alfanumérico (letras y números) y tener 10 caracteres. Por ejemplo, escriba `com.contoso.appname.macos` para **ID**. de paquete y `ABCDE12345` para el **identificador del equipo**.

  > [!TIP]
  > Para obtener el identificador de paquete de una extensión de kernel (kext) en un dispositivo macOS, puede:
  >
  > 1. En el terminal, ejecute `kextstat | grep -v com.apple`y anote el resultado. Instale el software o kext que desee. Vuelva a ejecutar `kextstat | grep -v com.apple` y busque los cambios.
  >
  >    En el terminal, `kextstat` enumera todas las extensiones de kernel del sistema operativo. 
  >
  > 2. En el dispositivo, abra el archivo de lista de propiedades de información (info. plist) de un kext. Se muestra el identificador de la agrupación. Cada kext tiene un archivo info. plist almacenado dentro de. 

> [!NOTE]
> No tiene que agregar identificadores de equipo ni extensiones de kernel. Puede configurar uno u otro.

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](../device-profile-assign.md) y [supervise el estado](../device-profile-monitor.md).
