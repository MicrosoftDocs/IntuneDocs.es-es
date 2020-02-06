---
title: 'Uso de OEMConfig en dispositivos Android Enterprise en Microsoft Intune: Azure | Microsoft Docs'
description: Use Microsoft Intune para administrar y usar dispositivos que ejecutan Android Enterprise con OEMConfig. Vea todos los pasos, incluida una introducción, vea los requisitos previos, cree el perfil de configuración en Intune y vea una lista de aplicaciones OEMConfig admitidas.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/16/2020
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
ms.openlocfilehash: 9cc568cbadb683f632ffd2365ab7023cd796f231
ms.sourcegitcommit: 5ad0ce27a30ee3ef3beefc46d2ee49db6ec0cbe3
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 01/30/2020
ms.locfileid: "76886695"
---
# <a name="use-and-manage-android-enterprise-devices-with-oemconfig-in-microsoft-intune"></a>Uso y administración de dispositivos Android Enterprise con OEMConfig en Microsoft Intune

En Microsoft Intune, puede usar OEMConfig para agregar, crear y personalizar la configuración específica de OEM para dispositivos Android Enterprise. OEMConfig se suele usar para configurar las opciones que no están integradas en Intune. Los diferentes fabricantes de equipos originales (OEM) incluyen distintas configuraciones. La configuración disponible depende de lo que incluya el OEM en su aplicación OEMConfig.

Esta característica se aplica a:  

- Android Enterprise

En este artículo se describe OEMConfig, se indican los requisitos previos, se muestra cómo crear un perfil de configuración y se enumeran las aplicaciones OEMConfig admitidas en Intune.

## <a name="overview"></a>Introducción

Las directivas de OEMConfig son un tipo especial de directiva de configuración de dispositivos similar a una [directiva de configuración de aplicaciones](../apps/app-configuration-policies-overview.md). OEMConfig es un estándar definido por Google que usa la configuración de aplicaciones de Android para enviar la configuración de dispositivo a las aplicaciones escritas por OEM (fabricantes de equipos originales). Este estándar permite a los OEM y a las instancias de EMM (Enterprise Mobility Management) compilar y admitir características específicas de OEM de forma normalizada. [Obtenga más información sobre OEMConfig](https://blog.google/products/android-enterprise/oemconfig-supports-enterprise-device-features/).

Históricamente, las instancias de EMM, como Intune, compilan manualmente la compatibilidad con características específicas de OEM una vez incorporadas estas por el OEM. Este enfoque se traduce en esfuerzos duplicados y una adopción lenta.

Con OEMConfig, un OEM crea un esquema que define las características de administración específicas de ese OEM. El OEM inserta el esquema en una aplicación y, luego, coloca esa aplicación en Google Play. La instancia de EMM lee el esquema de la aplicación y lo expone en la consola de administrador de EMM. La consola permite a los administradores de Intune configurar los valores del esquema.

Cuando la aplicación OEMConfig se instala en un dispositivo, usa los valores configurados en el administrador de EMM para administrar el dispositivo. La aplicación OEMConfig ejecuta la configuración del dispositivo, en lugar de un agente MDM compilado por EMM.

Cuando el OEM agrega y mejora las características de administración, también actualiza la aplicación en Google Play. El administrador obtiene estas nuevas características y actualizaciones (incluidas las correcciones) sin esperar a que se incluyan en la instancia de EMM.

> [!TIP]
> Solo se puede usar OEMConfig con dispositivos que admiten esta característica y que tienen una aplicación OEMConfig correspondiente. Consulte al OEM para obtener detalles específicos.

## <a name="before-you-begin"></a>Antes de comenzar

Al usar OEMConfig, tenga en cuenta la siguiente información:

- Intune expone el esquema de la aplicación OEMConfig para que pueda configurarlo. Intune no valida ni cambia el esquema proporcionado por la aplicación. Por tanto, si el esquema es incorrecto o tiene datos inexactos, estos datos se siguen enviando a los dispositivos. Si detecta un problema que se origina en el esquema, póngase en contacto con el OEM para obtener instrucciones.
- Intune no influye en el contenido del esquema de la aplicación ni lo controla. Por ejemplo, Intune no tiene ningún control sobre las cadenas, el lenguaje, las acciones permitidas, etc. Se recomienda ponerse en contacto con el OEM para obtener más información sobre la administración de los dispositivos con OEMConfig.
- Los OEM pueden actualizar las características y los esquemas admitidos y cargar una nueva aplicación en Google Play en cualquier momento. Intune siempre se sincroniza con la versión más reciente de la aplicación OEMConfig de Google Play. Intune no mantiene las versiones anteriores del esquema ni la aplicación. Si se experimentan conflictos de versiones, se recomienda ponerse en contacto con el OEM para obtener más información.
- Asigne un perfil de OEMConfig a un dispositivo. Si hay varios perfiles asignados al mismo dispositivo, puede que observe un comportamiento incoherente. El modelo OEMConfig solo admite una única directiva por dispositivo.

## <a name="prerequisites"></a>Requisitos previos

Para usar OEMConfig en los dispositivos, asegúrese de cumplir los siguientes requisitos:

- Dispositivo Android Enterprise inscrito en Intune.
- Aplicación OEMConfig compilada por el OEM y cargada en Google Play. Si no está en Google Play, póngase en contacto con el OEM para obtener más información.
- El administrador de Intune tiene permisos de control de acceso basado en rol (RBAC) para **Aplicaciones móviles** y **Configuraciones de dispositivos**, y permiso de "lectura" en **Android for Work**. Estos permisos son necesarios porque los perfiles de OEMConfig usan configuraciones de aplicaciones administradas para administrar las configuraciones de dispositivos.

## <a name="prepare-the-oemconfig-app"></a>Preparación de la aplicación OEMConfig

Asegúrese de que el dispositivo admite OEMConfig, de que se ha agregado la aplicación OEMConfig correcta a Intune y de que la aplicación está instalada en el dispositivo. Póngase en contacto con el OEM para obtener esta información.

> [!TIP] 
> Las aplicaciones OEMConfig son específicas del OEM. Por ejemplo, una aplicación OEMConfig de Sony instalada en un dispositivo de Zebra Technologies no hace nada.

1. Obtenga la aplicación OEMConfig de la instancia administrada de Google Play Store. En [Incorporación de aplicaciones de Google Play administrado a dispositivos de Android Enterprise](../apps/apps-add-android-for-work.md) se muestran los pasos.
2. Algunos OEM pueden enviar dispositivos con la aplicación OEMConfig preinstalada. Si la aplicación no está preinstalada, use Intune para [agregar e implementar la aplicación en los dispositivos](../apps/apps-deploy.md).

## <a name="create-an-oemconfig-profile"></a>Creación de un perfil de OEMConfig

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.
3. Escriba las propiedades siguientes:

    - **Plataforma**: seleccione **Android Enterprise**.
    - **Tipo de perfil**: seleccione **OEMConfig**.

4. Seleccione **Crear**.
5. En **Básico**, escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre descriptivo para el nuevo perfil.
    - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
    - **Aplicación OEMConfig**: seleccione **Seleccionar una aplicación OEMConfig**.

6. En **Aplicación asociada**, seleccione una aplicación OEMConfig existente que haya agregado previamente > **Seleccionar**. Asegúrese de elegir la aplicación OEMConfig correcta para los dispositivos a los que va a asignar la directiva.

    Si no ve ninguna aplicación en la lista, configure la instancia administrada de Google Play y obtenga aplicaciones de ella. En [Adición de aplicaciones de Google Play administrado a dispositivos Android Enterprise con Intune](../apps/apps-add-android-for-work.md) se indican los pasos.

    > [!IMPORTANT]
    > Si ha agregado una aplicación OEMConfig y la ha sincronizado en Google Play, pero no aparece como **Aplicación asociada**, puede que tenga que ponerse en contacto con Intune para incorporar la aplicación. Vea cómo [agregar una nueva aplicación](#supported-oemconfig-apps), en este artículo.

7. Seleccione **Siguiente**.
8. En **Definir configuración**, seleccione **Diseñador de configuración** o **Editor JSON**:

    > [!TIP]
    > Lea la documentación del OEM para asegurarse de que está configurando las propiedades correctamente. Estas propiedades de aplicación son incluidas por el OEM, no Intune. Intune realiza una validación mínima de las propiedades o de lo que especifique. Por ejemplo, si especifica `abcd` como número de puerto, el perfil se guarda tal cual y se implementa en los dispositivos con los valores configurados. Asegúrese de especificar la información correcta.

    - **Diseñador de configuración**: al seleccionar esta opción, se muestran las propiedades disponibles en el esquema de la aplicación para su configuración.

      - Los menús contextuales del Diseñador de configuración indican que hay más opciones disponibles. Por ejemplo, el menú contextual puede permitirle agregar, eliminar y reordenar la configuración. El OEM incluye estas opciones. Asegúrese de leer la documentación de la aplicación del OEM para obtener información sobre cómo se deben usar estas opciones para crear perfiles.

      - Muchas opciones tienen valores predeterminados proporcionados por el OEM. Para ver si hay un valor predeterminado, mantenga el mouse sobre el icono de información situado junto a la opción. La información sobre herramientas muestra los valores predeterminados para esa opción (si los hubiera) y más detalles proporcionados por el OEM.

      - Al hacer clic en **Borrar**, se elimina una opción del perfil. Si una opción no está en el perfil, su valor en el dispositivo no cambia cuando este se aplica.

      - Si crea un conjunto vacío (sin configurar) en el Diseñador de configuración, se elimina al cambiar al Editor JSON.

    - **Editor JSON**: al seleccionar esta opción, se abre un editor JSON con una plantilla para el esquema de configuración completo insertado en la aplicación. En el editor, personalice la plantilla con valores para las distintas opciones. Si usa el **Diseñador de configuración** para cambiar los valores, el Editor JSON sobrescribe la plantilla con los valores del Diseñador de configuración.

      - Si va a actualizar un perfil existente, el Editor JSON muestra la configuración guardada por última vez con el perfil.

      - Los esquemas de OEMConfig pueden ser grandes y complejos. Si prefiere actualizar esta configuración con otro editor, seleccione el botón **Descargar plantilla JSON**. Use el editor que prefiera para agregar los valores de configuración a la plantilla. Luego, copie y pegue el archivo JSON actualizado en la propiedad **Editor JSON**.

      - Puede usar el Editor JSON para crear una copia de seguridad de la configuración. Después de configurar las opciones, use esta característica para obtener la configuración del archivo JSON con sus valores. Copie y pegue el JSON en un archivo y guárdelo. Ahora tiene un archivo de copia de seguridad.

    Cualquier cambio realizado en el Diseñador de configuración también se efectúa automáticamente en el Editor JSON. Del mismo modo, los cambios efectuados en el Editor JSON se realizan automáticamente en el Diseñador de configuración. Si la entrada contiene valores no válidos, no puede cambiar entre el Diseñador de configuración y el Editor JSON hasta que corrija los problemas.

9. Seleccione **Siguiente**.
10. En **Etiquetas de ámbito** (opcional), asigne una etiqueta para filtrar el perfil por grupos de TI específicos, como `US-NC IT Team` o `JohnGlenn_ITDepartment`. Para obtener más información sobre las etiquetas de ámbito, vea [Usar control de acceso basado en rol (RBAC) y etiquetas de ámbito](../fundamentals/scope-tags.md).

    Seleccione **Siguiente**.

11. En **Asignaciones**, seleccione los usuarios o grupos que van a recibir el perfil. Asigne un perfil a cada dispositivo. El modelo OEMConfig solo admite una directiva por dispositivo.

    Para obtener más información sobre la asignación de perfiles, vea [Asignación de perfiles de usuario y dispositivo](device-profile-assign.md).

    Seleccione **Siguiente**.

12. En **Revisar y crear**, revise la configuración. Si selecciona **Crear**, se guardan los cambios y se asigna el perfil. La directiva también se muestra en la lista de perfiles.

La siguiente vez que el dispositivo busca actualizaciones de configuración, se aplica la configuración específica del OEM que ha configurado a la aplicación OEMConfig.

> [!NOTE]
> El estándar OEMConfig no incluye actualmente informes de estado. Así, de forma predeterminada, los perfiles muestran el estado **Pendiente**.

## <a name="supported-oemconfig-apps"></a>Aplicaciones OEMConfig admitidas

En comparación con las aplicaciones estándar, las aplicaciones OEMConfig expanden los privilegios de configuración administrados concedidos por Google para admitir esquemas más complejos. Intune admite actualmente las siguientes aplicaciones OEMConfig:

-----------------

| OEM | Identificador de lote | Documentación de OEM (si la hubiera) |
| --- | --- | ---|
| Samsung | com.samsung.android.knox.kpu | [Guía de administración de Knox Service Plugin](https://docs.samsungknox.com/knox-service-plugin/admin-guide/index.htm) |
| Zebra Technologies | com.zebra.oemconfig.common | [Información general sobre Zebra OEMConfig](http://techdocs.zebra.com/oemconfig ) |
| Datalogic | com.datalogic.oemconfig | [Documentación de usuario de Datalogic OEMConfig](https://datalogic.github.io/oemconfig/) |
| Honeywell | com.honeywell.oemconfig |  |
| Kyocera | jp.kyocera.enterprisedeviceconfig |  |
| Spectralink: códigos de barras | com.spectralink.barcode.service |  |
| Spectralink: botones | com.spectralink.buttons |  |
| Spectralink: dispositivo | com.spectralink.slnkdevicesettings  |  |
| Spectralink: registro | com.spectralink.slnklogger |  |
| Spectralink: VQO | com.spectralink.slnkvqo |  |
| HMD Global | com.hmdglobal.app.oemconfig.ironman |  |

-----------------

Si existe una aplicación OEMConfig para el dispositivo, pero no aparece en la tabla anterior ni en la consola de Intune, envíe un correo electrónico a `IntuneOEMConfig@microsoft.com`.

> [!NOTE]
> Las aplicaciones OEMConfig deben ser incorporadas por Intune para que se puedan configurar con perfiles de OEMConfig. Una vez que una aplicación se ha admitido, no es necesario ponerse en contacto con Microsoft al respecto de su configuración en el inquilino. Solo tiene que seguir las instrucciones que aparecerán en esta página.

## <a name="next-steps"></a>Pasos siguientes

[Supervisión del estado del perfil](device-profile-monitor.md).
