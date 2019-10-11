---
title: Incorporación de aplicaciones a Microsoft Intune
titleSuffix: ''
description: Descubra cómo agregar aplicaciones a Microsoft Intune para que pueda asignar aplicaciones a usuarios y dispositivos. Intune admite una gran variedad de tipos de aplicaciones.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40bb96000513bb1de09ec8f8865735d70bddcd43
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725223"
---
# <a name="add-apps-to-microsoft-intune"></a>Incorporación de aplicaciones a Microsoft Intune 

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Para poder asignar, supervisar, configurar o proteger las aplicaciones, debe agregarlas a Microsoft Intune.

Los usuarios de aplicaciones y dispositivos de su empresa (empleados de su empresa) podrían tener requisitos de aplicaciones diferentes. Antes de agregar aplicaciones a Intune y de ponerlas a disposición de los trabajadores, debe evaluar y comprender algunos conceptos básicos de la aplicación. Debe comprender los distintos tipos de aplicaciones que están disponibles para Intune. Debe evaluar los requisitos de la aplicación, como las plataformas y las funcionalidades que los trabajadores necesitan. Debe determinar si va a utilizar Intune para administrar los dispositivos (incluidas las aplicaciones) o si dejará que Intune administre las aplicaciones sin administrar los dispositivos. Por último, debe determinar las aplicaciones y funcionalidades que necesitan los trabajadores y quién las necesita. La información de este artículo le ayuda a ponerse en marcha.

## <a name="app-types-in-microsoft-intune"></a>Tipos de aplicaciones en Microsoft Intune

Intune admite una gran variedad de tipos de aplicaciones. Las opciones disponibles varían para cada tipo de aplicación. Intune permite agregar y asignar los siguientes tipos de aplicación:

| Tipos de aplicación | Instalación | Updates |
|---|---|---|
| Aplicaciones de la tienda (aplicaciones de la tienda) | Intune instala la aplicación en el dispositivo.  | Las actualizaciones de aplicaciones son automáticas. |
| Aplicaciones escritas internamente (línea de negocio) | Intune instala la aplicación en el dispositivo (el usuario proporciona el archivo de instalación). | Debe actualizar la aplicación. |
| Aplicaciones integradas (aplicaciones integradas) | Intune instala la aplicación en el dispositivo.  | Las actualizaciones de aplicaciones son automáticas. |
| Aplicaciones en la web (vínculo web) | Intune crea un acceso directo a la aplicación web en la pantalla principal del dispositivo. | Las actualizaciones de aplicaciones son automáticas. |

### <a name="specific-app-type-details"></a>Detalles del tipo de aplicación específico
 
En la tabla siguiente se enumeran los tipos de aplicaciones específicas y cómo puede agregarlos en el panel **Agregar aplicación** de Intune:

| **Tipo específico de la aplicación** | **Tipo general** | **Procedimientos específicos de la aplicación** |
| --- | --- | --- |
| Aplicaciones de Google Play Store  | Aplicación de la tienda  | Seleccione **Android** como el **tipo de aplicación** y escriba la dirección URL de Google Play Store de la aplicación. |
| Aplicaciones de Android Enterprise  | Aplicación de la tienda  | Seleccione **Android** como **tipo de aplicación** y escriba la dirección URL de Google Play Store administrado de la aplicación. <sup>1</sup> |
| Aplicaciones de App Store  | Aplicación de la tienda  | Seleccione **iOS** como el **tipo de aplicación**, busque la aplicación y selecciónela en Intune. |
| Aplicaciones de la Tienda Windows Phone 8.1  | Aplicación de la tienda  | Seleccione **Windows Phone 8.1** como el **tipo de aplicación** y escriba la dirección URL de Microsoft Store de la aplicación. |
| Aplicaciones de Microsoft Store  | Aplicación de la tienda  | Seleccione **Windows** como el **tipo de aplicación** y escriba la dirección URL de Microsoft Store de la aplicación. |
| Aplicaciones administradas de Google Play | Aplicación de la tienda  | Seleccione **Google Play administrado** para **Tipo de aplicación**, busque la aplicación y selecciónela en Intune. |
| Aplicaciones de Office 365 para Windows 10  | Aplicación de la tienda (Office 365) | Seleccione **Windows 10** en el **conjunto de aplicaciones de Office 365** como el **tipo de aplicación** y después seleccione la aplicación de Office 365 que quiera instalar.  |
| Aplicaciones de Office 365 para macOS | Aplicación de la tienda (Office 365) | Seleccione **macOS** en el **conjunto de aplicaciones de Office 365** como el **tipo de aplicación** y después seleccione el paquete de aplicación de Office 365. |
| Aplicaciones de línea de negocio (LOB) Android | Aplicación LOB | Seleccione la aplicación de **línea de negocio** como **tipo de aplicación**, seleccione el **archivo de paquete de aplicación** y después introduzca un archivo de instalación de Android con la extensión **.apk** .  |
| Aplicaciones de LOB para iOS | Aplicación LOB | Seleccione la aplicación de **línea de negocio** como **tipo de aplicación**, seleccione el **archivo de paquete de aplicación** y después introduzca un archivo de instalación de iOS con la extensión **.ipa**.  |
| Aplicaciones de LOB para Windows Phone | Aplicación LOB | Seleccione la aplicación de **línea de negocio** como **tipo de aplicación**, seleccione el **archivo del paquete de aplicaciones** y, después, indique un archivo de instalación de Windows Phone con la extensión **.xap**.  |
| Aplicaciones de LOB de Windows | Aplicación LOB | Seleccione la aplicación de **línea de negocio** como el tipo de aplicación, seleccione el **archivo del paquete de aplicaciones** y, después, escriba un archivo de instalación de Windows con la extensión **.msi**, **.appx**, **.appxbundle**, **.msix** y **.msixbundle**. |
| Aplicación de iOS integrada  | Aplicación integrada | Seleccione **Aplicación integrada** como el **tipo de aplicación** y después seleccione la aplicación integrada en la lista de aplicaciones proporcionadas.  |
| Aplicación de Android integrada  | Aplicación integrada | Seleccione **Aplicación integrada** como el **tipo de aplicación** y después seleccione la aplicación integrada en la lista de aplicaciones proporcionadas.  |
| Aplicaciones web  | Aplicación web  | Seleccione **Vínculo web** como el **tipo de aplicación** y escriba una dirección URL válida que apunte a la aplicación web.  |
| Aplicaciones del sistema de Android Enterprise  | Aplicación de la tienda  | Seleccione **Aplicación del sistema Android Enterprise** como **tipo de aplicación** y escriba el nombre de la aplicación, el publicador y el archivo de paquete.  |
| Aplicación Windows (Win32)  | Aplicación LOB  | Seleccione **Aplicación Windows (Win32)** como el **tipo de aplicación**, elija **Archivo de paquete de aplicación** y seleccione un archivo de instalación con la extensión **.intunewin**.  |
| Aplicaciones de LOB para macOS | Aplicación LOB  | Seleccione **Línea de negocio** como **tipo de aplicación**, elija **Archivo de paquete de aplicación** y seleccione un archivo de instalación con la extensión **.intunemac**.  |


<sup>1</sup> Para obtener más información sobre los perfiles de trabajo de Android Enterprise y Android, consulte [Información sobre el uso de aplicaciones con licencia](apps-add.md#understanding-licensed-apps) a continuación.

Puede agregar una aplicación en Microsoft Intune seleccionando **Aplicaciones cliente** > **Aplicaciones** > **Agregar**. Se mostrará el panel **Agregar aplicación** y podrá seleccionar el **tipo de aplicación**. 

>[!TIP]
> Una aplicación de línea de negocio es aquella que se agrega desde un archivo de instalación de la aplicación. Por ejemplo, para instalar una aplicación de línea de negocio de iOS, agregue la aplicación seleccionando **Aplicación de línea de negocio** como el **Tipo de aplicación** en el panel **Agregar aplicación**. Después, seleccione el archivo de paquete de aplicación (extensión .ipa). Estos tipos de aplicaciones normalmente se han escrito internamente.

## <a name="assess-app-requirements"></a>Acceso a los requisitos de la aplicación
Como administrador de TI, determine qué aplicaciones debe usar el grupo, así como las capacidades necesarias para cada grupo y subgrupo. Para cada aplicación, determine las plataformas necesarias, los grupos de usuarios que necesitan la aplicación, las directivas de configuración para aplicar a todos los grupos y las directivas de protección que se aplicarán.  

Además, debe determinar si se va a centrar en la administración de dispositivos móviles (MDM) o solo en la administración de aplicaciones móviles (MAM). 

Usar Intune para administrar el dispositivo con administración de dispositivos móviles resulta útil cuando:
- Los usuarios necesitan un perfil de conectividad corporativo de VPN o de red Wi-Fi para ser productivos.
- Los usuarios necesitan que se envíe un conjunto de aplicaciones a su dispositivo.
- Su organización debe cumplir con las directivas legales u otras que requieren controles de administración de dispositivos móviles específicos, como seguridad o cifrado.

Usar Intune para administrar las aplicaciones con administración de aplicaciones móviles sin tener que administrar el dispositivo es útil cuando:
- Quiere permitir que los usuarios usen sus propios dispositivos (BYOD).
- Quiere proporcionar un mensaje emergente de un solo uso para que los usuarios sepan qué protecciones de administración de aplicaciones móviles se encuentran en contexto, en lugar de una notificación continua a nivel de dispositivo.
- Quiere cumplir directivas que exigen menos capacidad de administración en dispositivos personales. Por ejemplo, quiere administrar los datos corporativos de las aplicaciones, en lugar de administrar los datos corporativos de todo el dispositivo.

Para obtener más información: [Comparar MDM y MAM](../fundamentals/byod-technology-decisions.md).

### <a name="determine-who-will-use-the-app"></a>Determine quién va a usar la aplicación

A medida que determina qué aplicaciones necesitan sus trabajadores, tenga en cuenta los distintos grupos de usuarios y las diversas aplicaciones que utilizan. También es útil conocer estos grupos después de haber agregado una aplicación. Después de agregar una aplicación, asigne un grupo de usuarios que puedan usar la aplicación. 

En primer lugar, debe determinar qué grupo debe tener acceso a la aplicación en función de la confidencialidad de los datos que contiene la aplicación. Podría tener que incluir o excluir ciertos tipos de roles dentro de su organización. Por ejemplo, puede que solo se requieran determinadas aplicaciones LOB para el grupo de ventas, mientras que el personal centrado en ingeniería, finanzas, recursos humanos o legal puede que no necesiten usar las aplicaciones LOB. Además, el grupo de ventas podría necesitar protección de datos adicional y acceso a los servicios corporativos internos en sus dispositivos móviles. Debe determinar cómo se conectará este grupo a los recursos mediante la aplicación. ¿Los datos a los que accede la aplicación se encontrarán en la nube o en el entorno local? Además, ¿cómo se conectarán los usuarios a los recursos mediante la aplicación? 

Intune también permite el acceso a las aplicaciones cliente que requieren un acceso seguro a los datos locales, como servidores de aplicaciones de línea de negocio. Normalmente proporciona este tipo de acceso mediante [certificados administrados por Intune](../protect/certificates-configure.md) para el control de acceso, combinado con un proxy o una puerta de enlace de VPN estándar en el perímetro, como, por ejemplo, Azure Active Directory Application Proxy. El [SDK de aplicaciones y la herramienta de ajuste de aplicaciones](../developer/apps-prepare-mobile-application-management.md) de Intune pueden contener los datos a los que se ha tenido acceso dentro de la aplicación de línea de negocio, de forma que los datos corporativos no se puedan pasar a servicios o aplicaciones de consumidor.

Use la [Guía de planeamiento de la implementación, diseño e implementación de Intune](../fundamentals/planning-guide.md) para ayudarle a determinar cómo identificar los grupos de la organización que están asociados a cada escenario de caso de uso y caso de subuso de la aplicación. Para más información sobre cómo asignar aplicaciones a los grupos, consulte [Asignación de aplicaciones a grupos con Microsoft Intune](apps-deploy.md).

### <a name="determine-the-type-of-app-for-your-solution"></a>Determinar el tipo de aplicación para la solución

Puede elegir entre los siguientes tipos de aplicaciones:
- **Aplicaciones de la tienda**: aplicaciones que se han cargado en Microsoft Store, App Store o Google Play Store. El proveedor de una aplicación de la tienda mantiene y proporciona las actualizaciones de la aplicación. Seleccione la aplicación en la lista de la tienda y agréguela mediante Intune como una aplicación disponible para los usuarios.
- **Aplicaciones escritas internamente (línea de negocio)** : las aplicaciones que se crean internamente son aplicaciones de línea de negocio (LOB). La funcionalidad de este tipo de aplicación se ha creado para una de las plataformas compatibles con Intune, por ejemplo, Windows, iOS, macOS o Android. Su organización crea y le proporciona actualizaciones como un archivo independiente. Puede proporcionar actualizaciones de la aplicación a los usuarios agregando e implementando las actualizaciones mediante Intune.
- **Aplicaciones en la Web**: las aplicaciones web son aplicaciones cliente-servidor. El servidor proporciona la aplicación web, que incluye la interfaz de usuario, el contenido y la funcionalidad. Además, las plataformas de hospedaje web modernas normalmente ofrecen seguridad, equilibrio de carga y otras ventajas. Este tipo de aplicación se mantiene por separado en la Web. Intune se usa para que apunte a este tipo de aplicación. También puede asignar qué grupos de usuarios pueden tener acceso a la aplicación. Tenga en cuenta que Android no es compatible con las aplicaciones web.

A medida que determina qué aplicaciones necesita su organización, tenga en cuenta cómo se integran las aplicaciones con los servicios en la nube, a qué datos pueden acceder las aplicaciones, si las aplicaciones están disponibles para los usuarios BYOD y si las aplicaciones requieren acceso a internet.

Para más información sobre los tipos de aplicaciones que necesita la organización, consulte la sección "Aplicaciones" dentro de la sección "Requisitos de características" de [Creación de un diseño](../fundamentals/planning-guide-design.md#feature-requirements).

### <a name="understanding-app-management-and-protection-policies"></a>Información de las directivas de protección y administración de aplicaciones
Intune le permite modificar la funcionalidad de las aplicaciones que implementa para ayudarle a que se ajusten a los requisitos de cumplimiento y las directivas de seguridad de su empresa. Este control le permite determinar cómo se protegen los datos de su compañía. Las aplicaciones administradas de Intune están habilitadas con un amplio conjunto de directivas de protección de aplicaciones móviles, como por ejemplo:

- Restricción de las funciones Copiar y pegar y Guardar como.
- Configuración de vínculos web para que se abran dentro de la aplicación Intune Managed Browser.
- Habilitación del uso de varias identidades y el acceso condicional de nivel de aplicación.

Las aplicaciones administradas de Intune también pueden habilitar la protección de aplicaciones sin necesidad de una inscripción, lo que le ofrece la posibilidad de aplicar directivas de prevención de pérdida de datos sin tener que administrar el dispositivo del usuario. Además, puede incorporar la administración de aplicaciones móviles en las aplicaciones de línea de negocio y móviles mediante Intune App SDK y la herramienta de ajuste de aplicaciones. Para obtener más información sobre estas herramientas, consulte [Información general del SDK para aplicaciones de Intune](../developer/app-sdk.md).

### <a name="understanding-licensed-apps"></a>Información sobre el uso de aplicaciones con licencia
Además de comprender las aplicaciones web, las aplicaciones de la tienda y las aplicaciones LOB, también debe conocer las diferencias de las aplicaciones del programa de compras por volumen y las aplicaciones con licencia, como, por ejemplo: 
- **Programa de Compras por Volumen (VPP) de Apple para empresas (iOS)** : la App Store de iOS permite comprar varias licencias de una aplicación que quiera ejecutar en la empresa. Comprar varias copias permite administrar de manera eficaz las aplicaciones de la empresa. Para obtener más información, consulte [Administrar aplicaciones de iOS compradas a través de un programa de compras por volumen con Microsoft Intune](vpp-apps-ios.md).
- **Perfil de trabajo Android**: La forma de asignar aplicaciones a dispositivos de perfil de trabajo Android es diferente a cómo las asigna a dispositivos Android estándar. Todas las aplicaciones que se instalen para perfiles de trabajo Android proceden de Google Play Store administrado. Utilice Intune para buscar las aplicaciones que desee y apruébelas. La aplicación, a continuación, aparece en el nodo **Aplicaciones con licencia** de Azure Portal y puede administrar la asignación de las aplicaciones como lo haría con cualquier otra aplicación.
- **Microsoft Store para Empresas (Windows 10)** : en Microsoft Store para Empresas puede buscar y comprar aplicaciones para su organización, tanto sueltas como por volumen. Si conecta la tienda a Microsoft Intune, puede administrar las aplicaciones adquiridas por volumen en Azure Portal. Para más información, vea [Administrar las aplicaciones de Microsoft Store para Empresas](windows-store-for-business.md).

    > [!NOTE]
    > Las extensiones de archivo de las aplicaciones de Windows incluyen **.msi**, **.appx**, **.appxbundle**, **.msix** y **.msixbundle**.  

## <a name="before-you-add-apps"></a>Antes de agregar aplicaciones
Antes de empezar a agregar y asignar aplicaciones, considere los puntos siguientes:

- Al agregar y asignar una aplicación desde una tienda, los usuarios finales deben tener una cuenta con la tienda para poder instalar la aplicación.
- Algunas aplicaciones o elementos que asigna podrían depender de aplicaciones iOS integradas. Por ejemplo, si asigna un libro de App Store, la aplicación iBooks debe existir en el dispositivo. Si quitó la aplicación integrada iBooks, no puede usar Intune para restablecerla.

> [!IMPORTANT]
> Si cambia el nombre de la aplicación a través de Azure Portal de Intune una vez que ha implementado e instalado la aplicación, ya no se podrá llegar a la aplicación mediante comandos.

## <a name="cloud-storage-space"></a>Espacio de almacenamiento en nube
Todas las aplicaciones que cree mediante el tipo de instalación del instalador de software (por ejemplo, una aplicación de línea de negocio) se empaquetan y cargan en el almacenamiento en la nube de Intune. Una suscripción de prueba de Intune incluye 2 gigabytes (GB) de almacenamiento en nube que sirve para almacenar actualizaciones y aplicaciones administradas. Una suscripción completa no limita la cantidad total de espacio de almacenamiento.

Los requisitos de espacio de almacenamiento en nube son los siguientes:

- Todos los archivos de instalación deben encontrarse en la misma carpeta.
- El tamaño máximo de archivo de cualquier archivo que se cargue es de 8 GB.

  > [!NOTE]
  > Las aplicaciones de línea de negocio (LOB) de Windows tienen un límite de tamaño máximo de 8 GB por aplicación. Las aplicaciones LOB de iOS tienen un límite de tamaño máximo de 4 GB por aplicación.

## <a name="create-and-edit-categories-for-apps"></a>Creación y edición de categorías de aplicaciones

Se pueden usar categorías de aplicaciones para ordenar las aplicaciones de forma que sea más fácil para los usuarios encontrarlas en el portal de empresa. Puede asignar una o varias categorías a una aplicación, por ejemplo, *Desarrollador de aplicaciones* o *Aplicaciones de comunicación*.

Al agregar una aplicación a Intune, tiene la opción de seleccionar la categoría que quiera. Use los temas específicos de la plataforma para agregar una aplicación y asignar categorías. Para crear y editar sus propias categorías, use el procedimiento siguiente:

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. En el panel **Intune**, seleccione **Aplicaciones cliente**.
4. En el panel de la carga de trabajo **Aplicaciones cliente**, en **Configuración**, elija **Categorías de aplicaciones**.  
    El panel **Categorías de aplicaciones** muestra una lista de las categorías actuales. 
5. Realice alguna de las acciones siguientes:
    - Para agregar una categoría, en el panel **Crear categoría**, seleccione **Agregar** y escriba un nombre para la categoría.  
    Los nombres solo pueden escribirse en un solo idioma e Intune no los traduce.
    - Para editar una categoría, seleccione los puntos suspensivos ( **...** ) situados junto a la categoría y luego seleccione **Anclar al panel** o **Eliminar**.
6. Seleccione **Crear**.

## <a name="apps-that-are-added-automatically-by-intune"></a>Aplicaciones que Intune agrega automáticamente

Anteriormente, Intune tenía numerosas aplicaciones integradas que se podían asignar rápidamente. Según los comentarios de los clientes de Intune, hemos quitado esta lista y las aplicaciones integradas ya no se muestran. Sin embargo, si las aplicaciones integradas ya están asignadas, seguirán mostrándose en la lista de aplicaciones. Las aplicaciones podrán seguir asignándose según se necesite.

> [!NOTE]
> Para la instalación de una aplicación que no sea de línea de negocio, Intune intentará instalar la aplicación enviando un comando de instalación cada vez que el dispositivo se inserte en el repositorio, siempre que la aplicación no se detecte y el estado de instalación de la aplicación no sea *Instalación pendiente*.

## <a name="installing-updating-or-removing-required-apps"></a>Instalación, actualización o eliminación de aplicaciones necesarias

Intune reinstala, actualiza o quita automáticamente una aplicación necesaria en 24 horas, en lugar de esperar al ciclo de reevaluación de siete días.

Intune reinstala, actualiza o quita automáticamente una aplicación necesaria en función de las condiciones siguientes:
- Si un usuario final desinstala una aplicación cuya instalación en el dispositivo del usuario final se ha exigido, Intune reinstala automáticamente la aplicación cuando transcurre este periodo.
- Si se produce un error de instalación de una aplicación necesaria o de algún modo la aplicación no está presente en el dispositivo, Intune evalúa el cumplimiento y reinstala la aplicación cuando transcurre este periodo.  
- Un administrador destina una aplicación como disponible para un grupo de usuarios y un usuario final instala la aplicación desde el Portal de empresa en el dispositivo. Más adelante, el administrador actualiza la aplicación de v1 a v2. Intune actualiza la aplicación cuando transcurre este periodo, siempre que haya cualquier versión anterior de la aplicación en el dispositivo.
- Si el administrador realiza un intento de desinstalación y la aplicación está presente en el dispositivo y no se desinstala, Intune evalúa el cumplimiento y desinstala la aplicación cuando transcurre este periodo.   

## <a name="app-installation-errors"></a>Errores de instalación de la aplicación

Para obtener más información acerca de errores de instalación de aplicaciones de Intune, consulte [App installation errors](troubleshoot-app-install.md#app-installation-errors) (Errores de instalación de aplicaciones).

## <a name="next-steps"></a>Pasos siguientes

Para información sobre cómo agregar aplicaciones para cada plataforma a Intune, consulte:

- [Aplicaciones de Google Play Store](store-apps-android.md)
- [Aplicaciones LOB para Android](lob-apps-android.md)
- [Aplicaciones de App Store](store-apps-ios.md)
- [Aplicaciones LOB para iOS](lob-apps-ios.md)
- [Aplicaciones de LOB para macOS](lob-apps-macos.md)
- [Aplicaciones web (para todas las plataformas)](web-app.md)
- [Aplicaciones de la Tienda de Windows Phone 8.1](store-apps-windows-phone-8-1.md)
- [Aplicaciones de línea de negocio de Windows Phone](lob-apps-windows-phone.md)
- [Aplicaciones de Microsoft Store](store-apps-windows.md)
- [Aplicación de línea de negocio de Windows](lob-apps-windows.md)
- [Aplicaciones de Office 365 para Windows 10](apps-add-office365.md)
- [Aplicaciones de Office 365 para macOS](apps-add-office365-macos.md)
- [Aplicaciones integradas](apps-add-built-in.md)
- [Aplicaciones del sistema de Android Enterprise](apps-ae-system.md)
- [Aplicaciones Win32](app-management.md)
