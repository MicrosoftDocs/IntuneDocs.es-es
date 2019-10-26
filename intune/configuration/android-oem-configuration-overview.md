---
title: 'Uso de OEMConfig en dispositivos Android Enterprise en Microsoft Intune: Azure | Microsoft Docs'
description: Use Microsoft Intune para administrar y usar los dispositivos que ejecutan Android Enterprise con OEMConfig. Vea todos los pasos, incluida información general, vea los requisitos previos, crear el perfil de configuración en Intune y ver una lista de aplicaciones de OEMConfig compatibles.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: eb992747765ea087d5ef536c2da7c444bfa2d987
ms.sourcegitcommit: 4f979ba7030e72d820113fe23ac8521ddb2433bd
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72915726"
---
# <a name="use-and-manage-android-enterprise-devices-with-oemconfig-in-microsoft-intune"></a>Usar y administrar dispositivos empresariales Android con OEMConfig en Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

En Microsoft Intune, puede usar OEMConfig para agregar, crear y personalizar la configuración específica de OEM para dispositivos empresariales Android. OEMConfig se usa normalmente para configurar las opciones que no están integradas en Intune. Los diferentes fabricantes de equipos originales (OEM) incluyen configuraciones diferentes. La configuración disponible depende de lo que incluye el OEM en su aplicación OEMConfig.

Esta característica se aplica a:  

- Android Enterprise

En este artículo se describe OEMConfig, se enumeran los requisitos previos, se muestra cómo crear un perfil de configuración y se enumeran las aplicaciones OEMConfig compatibles en Intune.

## <a name="overview"></a>Introducción

Las directivas de OEMConfig son un tipo especial de directiva de configuración de dispositivos similar a la [Directiva de configuración de aplicaciones](../apps/app-configuration-policies-overview.md). OEMConfig es un estándar definido por Google que aprovecha la configuración de la aplicación en Android para enviar la configuración del dispositivo a las aplicaciones escritas por OEM (fabricantes de equipos originales). Esta norma permite a los OEM y a la EMMs (administración de movilidad empresarial) crear y admitir características específicas del OEM de forma estandarizada. [Más información sobre OEMConfig](https://blog.google/products/android-enterprise/oemconfig-supports-enterprise-device-features/).

Históricamente, EMMs, como Intune, compilaba manualmente la compatibilidad con características específicas del OEM después de que las haya introducido el OEM. Este enfoque conduce a esfuerzos duplicados y a una adopción lenta.

Con OEMConfig, un OEM crea un esquema que define las características de administración específicas del OEM. El OEM incrusta el esquema en una aplicación y, a continuación, coloca esta aplicación en Google Play. El EMM lee el esquema de la aplicación y expone el esquema en la consola de administrador de EMM. La consola permite a los administradores de Intune configurar los valores en el esquema.

Cuando la aplicación OEMConfig se instala en un dispositivo, usa las opciones configuradas en la consola de administrador de EMM para administrar el dispositivo. La aplicación OEMConfig ejecuta la configuración en el dispositivo, en lugar de un agente MDM compilado por el EMM.

Cuando el OEM agrega y mejora las características de administración, el OEM también actualiza la aplicación en Google Play. Como administrador, obtiene estas nuevas características y actualizaciones (incluidas las correcciones) sin esperar a que se incluyan en la EMMs.

> [!TIP]
> Solo puede usar OEMConfig con dispositivos que admiten esta característica y tienen una aplicación OEMConfig correspondiente. Consulte a su OEM para obtener detalles específicos.

## <a name="before-you-begin"></a>Antes de comenzar

Al utilizar OEMConfig, tenga en cuenta la siguiente información:

- Intune expone el esquema de la aplicación OEMConfig para que pueda configurarlo. Intune no valida ni cambia el esquema proporcionado por la aplicación. Por tanto, si el esquema es incorrecto o tiene datos inexactos, estos datos se envían a los dispositivos. Si encuentra un problema que se origina en el esquema, póngase en contacto con el OEM para obtener instrucciones.
- Intune no influye ni controla el contenido del esquema de la aplicación. Por ejemplo, Intune no tiene ningún control sobre las cadenas, el lenguaje, las acciones permitidas, etc. Se recomienda ponerse en contacto con el OEM para obtener detalles y procedimientos recomendados para administrar sus dispositivos con OEMConfig.
- En cualquier momento, los OEM pueden actualizar sus características y esquemas compatibles y cargar una nueva aplicación en Google Play. Intune siempre sincroniza la versión más reciente de la aplicación OEMConfig desde Google Play. Intune no mantiene las versiones anteriores del esquema o la aplicación. Si tiene conflictos de versiones, se recomienda ponerse en contacto con el OEM para obtener más información.
- Asigne un perfil de OEMConfig a un dispositivo. Si hay varios perfiles asignados al mismo dispositivo, puede que vea un comportamiento incoherente. El modelo OEMConfig solo admite una única directiva por dispositivo.

## <a name="prerequisites"></a>Requisitos previos

Para usar OEMConfig en los dispositivos, asegúrese de que tiene los siguientes requisitos:

- Un dispositivo de Android Enterprise inscrito en Intune.
- Una aplicación OEMConfig compilada por el OEM y cargada en Google Play. Si no está en Google Play, póngase en contacto con el OEM para obtener más información.
- El administrador de Intune tiene permisos de control de acceso basado en rol (RBAC) para las **aplicaciones móviles**, las **configuraciones de dispositivos**y el permiso de "lectura" en **Android for work**. Estos permisos son necesarios porque los perfiles de OEMConfig usan configuraciones de aplicaciones administradas para administrar las configuraciones de dispositivos.

## <a name="prepare-the-oemconfig-app"></a>Preparación de la aplicación OEMConfig

Asegúrese de que el dispositivo es compatible con OEMConfig, que se ha agregado la aplicación OEMConfig correcta a Intune y que la aplicación está instalada en el dispositivo. Póngase en contacto con el OEM para obtener esta información.

> [!TIP] 
> Las aplicaciones OEMConfig son específicas del OEM. Por ejemplo, una aplicación Sony OEMConfig instalada en un dispositivo de tecnología Zebra no hace nada.

1. Obtenga la aplicación OEMConfig de la Google Play Store administrada. En [Incorporación de aplicaciones de Google Play administrado a dispositivos de Android Enterprise](../apps/apps-add-android-for-work.md) se muestran los pasos.
2. Algunos OEM pueden enviar dispositivos con la aplicación OEMConfig preinstalada. Si la aplicación no está preinstalada, use Intune para [Agregar e implementar la aplicación en los dispositivos](../apps/apps-deploy.md).

## <a name="create-an-oemconfig-profile"></a>Creación de un perfil de OEMConfig

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre descriptivo para el nuevo perfil.
    - **Descripción**: escriba una descripción para el perfil Esta configuración es opcional pero recomendada.
    - **Plataforma**: seleccione **Android Enterprise**.
    - **Tipo de perfil**: seleccione **OEMConfig**.

4. Seleccione **aplicación asociada**, seleccione una aplicación existente de OEMConfig que haya agregado anteriormente > **Aceptar**. Asegúrese de elegir la aplicación OEMConfig correcta para los dispositivos a los que va a asignar la Directiva.

    Si no ve ninguna aplicación en la lista, configure Google Play administrados y obtenga aplicaciones del almacén de Google Play administrado. En [Incorporación de aplicaciones de Google Play administrado a dispositivos de Android Enterprise](../apps/apps-add-android-for-work.md) se muestran los pasos.

    > [!IMPORTANT]
    > Si agregó una aplicación de OEMConfig y la sincronizó en Google Play, pero no aparece como una **aplicación asociada**, puede que tenga que ponerse en contacto con Intune para incorporar la aplicación. Consulte [Agregar una nueva aplicación](#supported-oemconfig-apps) (en este artículo).

5. En **configurar opciones con**, elija usar el **Diseñador de configuración** o el **Editor de JSON**:

    > [!TIP]
    > Lea la documentación del OEM para asegurarse de que está configurando las propiedades correctamente. Estas propiedades de la aplicación se incluyen en el OEM, no en Intune. Intune realiza la validación mínima de las propiedades o lo que escriba. Por ejemplo, si escribe `abcd` para un número de puerto, el perfil se guarda tal cual y se implementa en los dispositivos con los valores que configure. Asegúrese de escribir la información correcta.

    - **Diseñador de configuración**: cuando se selecciona esta opción, se muestran las propiedades disponibles en el esquema de la aplicación para que se configure.

      - Los menús contextuales del diseñador de configuración indican que hay más opciones disponibles. Por ejemplo, el menú contextual puede permitirle agregar, eliminar y reordenar la configuración. Estas opciones las incluye el OEM. Asegúrese de leer la documentación de la aplicación OEM para obtener información sobre cómo se deben usar estas opciones para crear perfiles.

      - Muchas opciones de configuración tienen valores predeterminados proporcionados por el OEM. Para ver si hay un valor predeterminado, mantenga el mouse sobre el icono de información situado junto al valor. La información sobre herramientas muestra los valores predeterminados para esa configuración (si es aplicable) y más detalles proporcionados por el OEM.

      - Al hacer clic en **Borrar** se elimina un valor del perfil. Si un valor no está en el perfil, su valor en el dispositivo no cambiará cuando se aplique el perfil.
        
      - Si crea un paquete vacío (no configurado) en el diseñador de configuración, se elimina al cambiar al editor de JSON.

    - **Editor de JSON**: cuando se selecciona esta opción, se abre un editor de JSON con una plantilla para el esquema de configuración completo insertado en la aplicación. En el editor, personalice la plantilla con valores para las distintas configuraciones. Si usa el **Diseñador de configuración** para cambiar los valores, el editor de JSON sobrescribe la plantilla con los valores del diseñador de configuración.
    
      - Si va a actualizar un perfil existente, el editor de JSON muestra la configuración que se guardó por última vez con el perfil.

      - Los esquemas de OEMConfig pueden ser grandes y complejos. Si prefiere actualizar esta configuración con un editor diferente, seleccione el botón **Descargar plantilla JSON** . Use un editor de su elección para agregar los valores de configuración a la plantilla. A continuación, copie y pegue el archivo JSON actualizado en la propiedad del **Editor de JSON** .

      - Puede usar el editor de JSON para crear una copia de seguridad de la configuración. Después de configurar los valores, use esta característica para obtener la configuración de JSON con sus valores. Copie y pegue el archivo JSON en un archivo y guárdelo. Ahora tiene un archivo de copia de seguridad.

    Cualquier cambio realizado en el diseñador de configuración también se realiza automáticamente en el editor de JSON. Del mismo modo, los cambios realizados en el editor de JSON se realizan automáticamente en el diseñador de configuración. Si la entrada contiene valores no válidos, no puede cambiar entre el diseñador de configuración y el editor de JSON hasta que corrija los problemas.

6. Seleccione **Aceptar** > **Agregar** para guardar los cambios. La directiva se crea y se muestra en la lista.

Asegúrese de [asignar el perfil](device-profile-assign.md) y [supervise su estado](device-profile-monitor.md).

 > [!NOTE]
 > Asigne un perfil a cada dispositivo. El modelo OEMConfig solo admite una directiva por dispositivo.

La próxima vez que el dispositivo Compruebe las actualizaciones de la configuración, se aplicará la configuración específica del OEM que haya configurado a la aplicación OEMConfig.

> [!NOTE]
> El estándar OEMConfig no incluye actualmente informes de estado. De forma predeterminada, los perfiles muestran el estado **pendiente** .

## <a name="supported-oemconfig-apps"></a>Aplicaciones OEMConfig compatibles

En comparación con las aplicaciones estándar, las aplicaciones de OEMConfig expanden los privilegios de configuración administrados concedidos por Google para admitir esquemas más complejos. Intune admite actualmente las siguientes aplicaciones de OEMConfig:

-----------------

| OEM | Identificador de lote | Documentación de OEM (si está disponible) |
| --- | --- | ---|
| Samsung | com. Samsung. Android. Knox. KPU | [Guía de administración del complemento del servicio Knox](https://docs.samsungknox.com/knox-service-plugin/admin-guide/welcome.htm) |
| Tecnologías Zebra | com. Zebra. oemconfig. Common | [Información general de Zebra OEMConfig](http://techdocs.zebra.com/oemconfig ) |
| Lógica de los | com. oemconfig | [Documentación de usuario para OEMConfig de la lógica de los usuarios](https://datalogic.github.io/oemconfig/) |
| Honeywell | com. Honeywell. oemconfig |  |
| Kyocera | JP. Kyocera. enterprisedeviceconfig |  |

-----------------

Si existe una aplicación OEMConfig para el dispositivo, pero no se encuentra en la tabla anterior, o no aparece en la consola de Intune, envíe un correo electrónico a `IntuneOEMConfig@microsoft.com`.

> [!NOTE]
> Las aplicaciones de OEMConfig deben estar integradas en Intune antes de que se puedan configurar con perfiles de OEMConfig. Una vez que se admite una aplicación, no es necesario que se ponga en contacto con Microsoft para configurarla en su inquilino. Solo tiene que seguir las instrucciones que aparecerán en esta página.

## <a name="next-steps"></a>Pasos siguientes

- [Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).
