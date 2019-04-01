---
title: Guía de pruebas para desarrolladores de Android sobre del SDK para aplicaciones de Microsoft Intune
description: Microsoft Intune App SDK para Android Guía de pruebas le ayuda a probar la aplicación Android administrados por Intune.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/14/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4ef8f421-9610-4d34-a464-cc02eb1578a9
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4203f424c395399cb0ed1e7472b006602aa0b210
ms.sourcegitcommit: db7a6b8fc9e82dae4f2111ca0b2d3c14e33658f9
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2019
ms.locfileid: "58072476"
---
# <a name="microsoft-intune-app-sdk-for-android-developers-testing-guide"></a>Guía de pruebas para desarrolladores de Android sobre del SDK para aplicaciones de Microsoft Intune

Microsoft Intune App SDK para Android Guía de pruebas está diseñado para ayudarle a probar la aplicación Android administrados por Intune.  

## <a name="prerequisite-test-accounts"></a>Cuentas de prueba de requisitos previos
Con y sin datos generados previamente, se pueden crear nuevas cuentas. Para crear una cuenta:
1. Navegue hasta la [Microsoft demostraciones](https://demos.microsoft.com/environments/create/tenant) sitio. 
2. [Configurar Intune](https://docs.microsoft.com/intune/setup-steps) para habilitar la administración de dispositivos móviles (MDM).
3. [Crear usuarios](https://docs.microsoft.com/intune/users-add).
4. [Crear grupos](https://docs.microsoft.com/intune/groups-add).
5. [Asignar licencias](https://docs.microsoft.com/intune/licenses-assign) según corresponda para las pruebas.


## <a name="azure-portal-policy-configuration"></a>Configuración de directiva de Azure portal
[Crear y asignar directivas de protección](https://docs.microsoft.com/intune/app-protection-policies) en el [hoja de Intune del portal de Azure](https://portal.azure.com/?feature.customportal=false#blade/Microsoft_Intune_Apps/MainMenu/14/selectedMenuItem/Overview). Su [directiva de configuración](https://docs.microsoft.com/intune/app-configuration-policies-overview) también se pueden crear y asignar en la hoja de Intune.

> [!NOTE]
> Si la aplicación no aparece en el portal de Azure, puede dirigirse a una directiva seleccionando el **más aplicaciones** opción y proporcionando el nombre del paquete en el cuadro de texto.

> [!IMPORTANT]
> Para que una directiva de configuración aplicar, la inscripción de usuario debe tener como destino un [directiva de protección de aplicaciones de Intune](https://docs.microsoft.com/intune/app-protection-policy).

## <a name="test-cases"></a>Casos de prueba

Los siguientes casos de prueba se proporcionan los pasos de configuración y la confirmación. Use esta guía para ayudar a solucionar problemas de la aplicación Android administrada por Intune.

### <a name="required-pin-and-corporate-credentials"></a>PIN requerido y las credenciales corporativas

Puede requerir un pin para acceder a recursos corporativos. Además, puede exigir autenticación de la organización antes de que los usuarios pueden usar aplicaciones administradas. Use los pasos siguientes para establecer estos requisitos:

1. Configurar **requerir PIN para acceder** y **requerir credenciales corporativas para el acceso** a **Sí**. Para más información, vea [Configuración de directivas de protección de aplicaciones Android en Microsoft Intune](app-protection-policy-settings-android.md#access-requirements).
2. Confirme las condiciones siguientes:
    - Inicio de la aplicación debe presentar una solicitud de entrada/configuración del PIN o el usuario de producción que se usó durante la inscripción con el Portal de empresa.
    - Error al presentar una solicitud de inicio de sesión válida podría ser debido a un manifiesto de android está configurado incorrectamente, específicamente los valores para la integración de ADAL (SkipBroker, ClientID y entidad).
    - Error al presentar ningún símbolo del sistema puede deberse a un incorrectamente integrado `MAMActivity` valor. Para obtener más información acerca de `MAMActivity`, consulte [Microsoft Intune App SDK para la guía para desarrolladores de Android](app-sdk-android.md).

> [!NOTE] 
> Si la prueba anterior no funciona, las pruebas siguientes se probablemente también producirá un error. Revisión [SDK](app-sdk-android.md##sdk-integration) y [ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal) integración.

### <a name="restrict-transferring-and-receiving-data-with-other-apps"></a>Restringir la transferencia y recibir datos con otras aplicaciones
Puede controlar la transferencia de datos entre aplicaciones administradas corporativas como sigue:

1. Establecer **permitir a la aplicación transferir datos a otras aplicaciones** a **aplicaciones administradas por directivas**.
2. Establezca **Permitir a la aplicación recibir datos de otras aplicaciones** en **Todas las aplicaciones**. Uso de intenciones y proveedores de contenido se verán afectado por estas directivas.
3. Confirme las condiciones siguientes:
    - Abrir desde una aplicación no administrada a las funciones de la aplicación correctamente.
    - Se permite compartir contenido entre las aplicaciones administradas.
    - Se bloquea el uso compartido de las aplicaciones administradas con aplicaciones no administradas (por ejemplo, Chrome).

### <a name="restrict-cut-copy-and-paste"></a>Limitar funciones Cortar, Copiar y Pegar
Puede restringir el Portapapeles del sistema a las aplicaciones administradas como sigue:

1. Establecer **restringir cortar, copiar y pegar con otras aplicaciones** a **administradas por directivas con pegar**.
2. Confirme las condiciones siguientes:
    - Copie texto de la aplicación en un administrado se bloquea una aplicación no administrada (por ejemplo, los mensajes).

### <a name="prevent-save-as"></a>Impedir **Guardar como**
Puede controlar **Guardar como** funcionalidad como sigue:

1. Si su aplicación requiere [integrado "Guardar como" controles](app-sdk-android.md#example-determine-if-saving-to-device-or-cloud-storage-is-permitted), establezca **impedir "Guardar como"** a **Sí**.
2. Confirme las condiciones siguientes:
    - Guardar está restringido a solo las ubicaciones administradas adecuadas.

### <a name="file-encryption"></a>Cifrado de archivos
Puede cifrar los datos en el dispositivo como sigue:

1. Establecer **cifrar datos de aplicación** a **Sí**.
2. Confirme las condiciones siguientes:
    - Comportamiento normal de la aplicación no se ve afectada.

### <a name="prevent-android-backups"></a>Impedir copias de seguridad de Android
Puede controlar la copia de seguridad de aplicación como sigue:

1. Si ha establecido [integra las restricciones de copia de seguridad](app-sdk-android.md#protecting-backup-data), configurar **Android impedir copias de seguridad** a **Sí**.
2. Confirme las condiciones siguientes:
    - Las copias de seguridad están restringidas.

### <a name="unenrollment"></a>Cancelar suscripción
Puede borrar de forma remota aplicaciones administradas desde que contiene los documentos y correos electrónicos corporativos y los datos personales se descifran cuando ya no se administra de manera:

1. Desde el portal de Azure, [emitir un borrado](https://docs.microsoft.com/intune/apps-selective-wipe).
2. Si la aplicación no se registra para los controladores de borrado confirmación las condiciones siguientes:
    - Se produce una eliminación completa de la aplicación.
3. Si la aplicación se ha registrado para `WIPE_USER_DATA` o `WIPE_USER_AUXILARY_DATA`, confirme las condiciones siguientes:
    - El contenido administrado se quita de la aplicación. Para obtener más información, consulte [guía para desarrolladores de Android - borrado selectivo de Intune App SDK](app-sdk-android.md#selective-wipe).

### <a name="multi-identity"></a>Varias identidades
La integración de [compatibilidad con varias identidades](app-sdk-android.md#multi-identity-optional) es un cambio de alto riesgo que deberá probarse detenidamente. Los problemas más comunes que estarán preparados para una configuración incorrecta de la identidad (contexto frente a nivel de amenaza) y también los archivos de seguimiento (`MAMFileProtectionManager`).

Como mínimo se deben volver a validar los siguientes escenarios de identidades múltiples:

- **Guardar como** directiva funciona correctamente para las identidades administradas.
- Copiar pegar restricciones se aplican correctamente desde código administrado a personal.
- Se cifran únicamente los datos que pertenecen a la identidad administrada y no se modifican los archivos personales.
- El borrado selectivo durante la anulación de inscripción solo quita los datos de identidad administrada.
- Se solicita al usuario final para el inicio condicional al cambiar de no administrado a la cuenta administrada (solo la primera vez).

### <a name="app-configuration-optional"></a>Configuración de la aplicación (opcional)
Puede configurar el comportamiento de las aplicaciones administradas como sigue:

1. Si la aplicación consume los parámetros de configuración de aplicación, debe probar que la aplicación controla correctamente todos los valores que puede establecer (como administrador). [Directivas de configuración](https://docs.microsoft.com/intune/app-configuration-policies-overview) se pueden crear y asignar en mediante Intune.

## <a name="next-steps"></a>Pasos siguientes

- [Incorporación de una aplicación de línea de negocio de Android a Microsoft Intune](lob-apps-android.md).
