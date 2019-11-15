---
title: Habilitación de aplicaciones de Win32 en dispositivos en modo S
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo habilitar las aplicaciones de Win32 en dispositivos en modo S mediante Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a3a9eb45898102e9d5fcde88f69026467255c513
ms.sourcegitcommit: d2d18eef64bcf16eec1a48fcb67f1362537c0245
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/02/2019
ms.locfileid: "73445273"
---
# <a name="enable-win32-apps-on-s-mode-devices"></a>Habilitación de aplicaciones de Win32 en dispositivos en modo S

[Modo Windows 10 S](https://docs.microsoft.com/windows/deployment/s-mode) es un sistema operativo bloqueado que solo ejecuta aplicaciones de la tienda. De forma predeterminada, los dispositivos de modo Windows S no permiten la instalación y ejecución de aplicaciones Win32. Estos dispositivos incluyen una única *directiva base de Win 10S*, que bloquea el dispositivo del modo S para que no ejecute ninguna aplicación Win32 en él. Sin embargo, al crear y usar una **directiva complementaria del modo S** en Intune, puede instalar y ejecutar aplicaciones Win32 en dispositivos administrados en modo Windows 10 S. Mediante las herramientas de PowerShell de [Control de aplicaciones de Windows Defender (WDAC)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control), puede crear una o varias directivas complementarias para el modo Windows S. Debe firmar las directivas complementarias con el [servicio de firma de Device Guard (DGSS)](https://go.microsoft.com/fwlink/?linkid=2095629) o con [SignTool.exe](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/signing-policies-with-signtool) y, después, cargue y distribuya las directivas mediante Intune. Como alternativa, puede firmar las directivas complementarias con un certificado de codiseño de la organización; sin embargo, el método preferido es usar DGSS. En la instancia que usa el certificado de codiseño de la organización, el certificado raíz al que se encadena el certificado de codiseño debe estar presente en el dispositivo.

Al asignar la directiva complementaria del modo S en Intune, el dispositivo puede hacer una excepción a la directiva de modo S existente del dispositivo, que permite que el catálogo de aplicaciones firmado correspondiente esté cargado. La directiva establece una lista de permitidos de aplicaciones (el catálogo de aplicaciones) que se puede usar en el dispositivo de modo S.

> [!NOTE]
> Las aplicaciones Win32 en modo S solo se admiten en la actualización 2019 de noviembre de Windows 10 (compilación 18363) o versiones posteriores.

<!-- Add WDAC tooling diagram  -->

Los pasos para permitir que las aplicaciones Win32 se ejecuten en un dispositivo Windows 10 en modo S son los siguientes:

1. Habilite los dispositivos en modo S mediante Intune como parte del proceso de inscripción de Windows 10 S.
2. Cree una directiva complementaria para permitir aplicaciones Win32:
   - Puede usar las herramientas de [Control de aplicaciones de Windows Defender (WDAC)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) para crear una directiva complementaria. El identificador de directiva base dentro de la directiva debe coincidir con el identificador de directiva base del modo S (que está codificado de forma rígida en el cliente). Además, asegúrese de que la versión de la directiva es mayor que la versión anterior.
   - Use DGSS para firmar la directiva complementaria. Para más información, consulte [Firmar la directiva de integridad de código con las firmas de Device Guard](https://docs.microsoft.com/microsoft-store/sign-code-integrity-policy-with-device-guard-signing).
   - La directiva complementaria firmada se carga en Intune mediante la creación de una directiva complementaria del modo Windows 10 S (consulte a continuación).
3. Se pueden permitir catálogos de aplicaciones Win32 mediante Intune:
   - Puede crear archivos de catálogo (uno para cada aplicación) y firmarlos con DGSS u otra infraestructura de certificados.
   - El catálogo firmado se empaqueta en el archivo *.intunewin* mediante la [herramienta de preparación de contenido de Microsoft Win32](https://go.microsoft.com/fwlink/?linkid=2065730). Para más información, consulte [Administración de aplicaciones Win32: Preparar el contenido de la aplicación Win32 para la carga](~/apps/apps-win32-app-management.md#prepare-the-win32-app-content-for-upload).
   - Intune aplica el catálogo de aplicaciones firmadas para instalar la aplicación Win32 en el dispositivo del modo S con la [extensión de administración de Intune](~/apps/intune-management-extension.md).

> [!NOTE]
> Los paquetes de `.appx` y `.appx` de la aplicación de línea de negocio (LOB) en modo Windows 10 S se admitirán mediante la firma de Microsoft Store para Empresas (MSFB).
>
> **La directiva complementaria del modo S** para las aplicaciones deben entregarse mediante la extensión de administración de Intune.
>
> Las directivas del modo S se aplican en el nivel de dispositivo. Se combinarán varias directivas de destino en el dispositivo. La directiva combinada se aplicará en el dispositivo.

Para crear una directiva complementaria del modo Windows 10 S, siga estos pasos:

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. En el panel de **Intune**, seleccione **Aplicaciones cliente** > **Directivas complementarias del modo S** > **Crear directiva**.
3. Antes de agregar el **archivo de directiva**, debe crearlo y firmarlo. Para obtener más información, vea:
    - [Creación de una directiva WDAC mediante herramientas de PowerShell y convertirla a un formato binario](https://go.microsoft.com/fwlink/?linkid=2095387)
    - [Firma con el servicio de firma de Device Guard](https://go.microsoft.com/fwlink/?linkid=2095629) **(recomendado)**

4. En la página **Datos básicos**, agregue los siguientes valores:

    | Valor | Descripción |
    |--------------|------------------------------------------------|
    | Archivo de directiva | Archivo que contiene la directiva WDAC. |
    | Nombre | Nombre de esta directiva. |
    | Descripción | [Opcional] Descripción de esta directiva. |

5. Haga clic en **Siguiente: Etiquetas de ámbito**.<br>
   En la página **Etiquetas de ámbito** puede configurar opcionalmente etiquetas de ámbito para determinar quién puede ver la directiva de la aplicación en Intune. Para obtener más información sobre las etiquetas de ámbito, consulte [Use role-based access control and scope tags for distributed IT](~/fundamentals/scope-tags.md) (Uso del control de acceso basado en roles y de las etiquetas de ámbito para la TI distribuida).

6. Haga clic en **Siguiente: Asignaciones**.<br>
   En la página **Asignaciones** puede asignar la directiva a usuarios y dispositivos. Es importante saber que una directiva se puede asignar a un dispositivo, independientemente de si dicho dispositivo está administrado o no por Intune.
7. Haga clic en **Siguiente: Revisar + crear** para revisar los valores especificados en el perfil.
8. Cuando termine, haga clic en **Crear** para crear la directiva complementaria del modo S en Intune. 

Una vez creada la directiva, verá que se ha agregado a la lista de directivas complementarias del modo S en Intune. Una vez asignada la directiva, esta se implementa en los dispositivos. Tenga en cuenta que debe implementar la aplicación en el mismo grupo de seguridad que la directiva complementaria. Puede iniciar el destino y la asignación de aplicaciones a esos dispositivos. Esto permitirá que los usuarios finales instalen y ejecuten las aplicaciones en los dispositivos del modo S.

## <a name="removal-of-s-mode-policy"></a>Eliminación de la directiva del modo S

Actualmente, para quitar la directiva complementaria del modo S del dispositivo, debe asignar e implementar una directiva vacía para sobrescribir la directiva complementaria del modo S existente.

## <a name="policy-reporting"></a>Informes de directiva

La directiva complementaria del modo S, que se aplica en el nivel de dispositivo, solo tiene informes de nivel de dispositivo. Los informes de nivel de dispositivo están disponibles para las condiciones de estado correcto y error. 

Valores de informes que se muestran en la consola de Intune para las directivas de informes del modo S:
- **Correcto**: La directiva complementaria del modo S está en vigor.
- **Desconocido**: No se conoce el estado de la directiva complementaria del modo S.
- **TokenError**: La directiva complementaria del modo S está estructuralmente bien, pero hay un error al autorizar el token.
- **NotAuthorizedByToken**: El token no autoriza esta directiva complementaria del modo S.
- **PolicyNotFound**: No se encuentra la directiva complementaria del modo S.

## <a name="next-steps"></a>Pasos siguientes

- Para más información, consulte [Aplicaciones Win32 en modo S](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/lob-win32-apps-on-s).
- Para obtener más información sobre agregar aplicaciones en Intune, vea [Incorporación de aplicaciones a Microsoft Intune](apps-add.md).
- Para más información sobre las aplicaciones Win32, consulte [Administración de aplicaciones Win32 en Intune](~/apps/apps-win32-app-management.md).
