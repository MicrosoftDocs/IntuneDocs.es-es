---
title: Asignación de aplicaciones de Office 365 a dispositivos Windows 10 mediante el uso de Microsoft Intune
titleSuffix: ''
description: Obtenga información sobre cómo usar Microsoft Intune para instalar aplicaciones de Office 365 en dispositivos Windows 10.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 38cc8ebc7be09d6ca0322a916d71f1fc86d3e49b
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725210"
---
# <a name="assign-office-365-apps-to-windows-10-devices-with-microsoft-intune"></a>Asignación de aplicaciones de Office 365 a dispositivos Windows 10 con Microsoft Intune

Para poder asignar, supervisar, configurar o proteger las aplicaciones, debe agregarlas a Intune. Uno de los [tipos de aplicaciones](apps-add.md#app-types-in-microsoft-intune) disponibles son las aplicaciones de Office 365 para dispositivos Windows 10. Al seleccionar este tipo de aplicación en Intune, puede asignar e instalar aplicaciones de Office 365 en los dispositivos que administra y que ejecutan Windows 10. También puede asignar e instalar aplicaciones para el cliente de escritorio de Microsoft Project Online y Microsoft Visio Online Plan 2, si posee sus licencias. Las aplicaciones de Office 365 disponibles se muestran como una única entrada en la lista de aplicaciones de la consola de Intune en Azure.

> [!NOTE]
> Debe usar las licencias de Office 365 ProPlus para activar las aplicaciones de Office 365 ProPlus implementadas a través de Microsoft Intune. Actualmente, la edición para empresas de Office 365 no es compatible con Intune.

## <a name="before-you-start"></a>Antes de empezar

> [!IMPORTANT]
> Si hay aplicaciones de Office .msi en el dispositivo del usuario final, debe usar la característica **Remove MSI** (Quitar MSI) para desinstalar estas aplicaciones de forma segura. En caso contrario, no se podrán instalar las aplicaciones de Office 365 entregadas por Intune.

- Los dispositivos en los que implementa estas aplicaciones deben ejecutar Windows 10 Creator Update o una versión posterior.
- Intune solo admite agregar aplicaciones de Office desde el conjunto de aplicaciones de Office 365.
- Si alguna aplicación de Office está abierta cuando Intune instala el conjunto de aplicaciones, puede ser que la instalación no se realice correctamente y que los usuarios finales pierdan los datos de los archivos no guardados.
- Este método de instalación no se admite en dispositivos Windows Home, Windows Team, Windows Holographic o Windows Holographic for Business.
- Intune no admite la instalación de aplicaciones de escritorio de Office 365 desde Microsoft Store (estas aplicaciones se conocen como Office Centennial) en un dispositivo al que ya haya implementado aplicaciones de Office 365 con Intune. Si instala esta configuración, puede provocar daños o la pérdida de datos.
- Las diferentes asignaciones de aplicaciones requeridas o disponibles no son acumulativas. Cualquier asignación de aplicación que se haga más adelante sustituirá las asignaciones de aplicaciones instaladas previamente. Por ejemplo, si el primer conjunto de aplicaciones de Office contiene Word y el más reciente no, Word se desinstala. Esta condición no se aplica a ninguna aplicación de Visio ni de Project.
- Actualmente no se admiten las implementaciones de varios Office 365. Solo se entregará una implementación al dispositivo.
- **Versión de Office**: elija si quiere asignar la versión de 32 o 64 bits de Office. Puede instalar la versión de 32 bits en dispositivos de 32 y 64 bits, pero en los dispositivos de 64 bits solo puede instalar la versión de 64 bits.
- **Remove MSI from end-user devices** (Quitar MSI de los dispositivos de usuario final): elija si quiere quitar las aplicaciones .MSI preexistentes de Office de los dispositivos de usuario final. La instalación no funcionará si hay aplicaciones .MSI preexistentes en los dispositivos de usuario final. Las aplicaciones que se deben desinstalar no se limitan a las seleccionadas para la instalación en **Configure App Suite** (Configurar App Suite), ya que quitarán todas las aplicaciones de Office (MSI) del dispositivo del usuario final. Para obtener más información, vea [Remove existing MSI versions of Office when upgrading to Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version) (Quitar las versiones de MSI de Office al actualizar a Office 365 ProPlus). Cuando Intune reinstala Office en los equipos de los usuarios finales, estos recibirán automáticamente los mismos paquetes de idioma que tenían con las instalaciones de Office .MSI anteriores.

## <a name="get-started"></a>Introducción

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. En el panel **Intune**, seleccione **Aplicaciones cliente**.
4. En el panel de la carga de trabajo **Aplicaciones cliente**, en **Administrar**, seleccione **Aplicaciones**.
5. Seleccione **Agregar**.
6. En el panel **Agregar aplicaciones**, en la lista **Tipo de aplicación**, vaya a **Office 365 Suite** y seleccione **Windows 10**.

## <a name="select-settings-format"></a>Selección del formato de configuración

Si quiere elegir un método para configurar la configuración de la aplicación, seleccione un **formato de configuración**. Entre las opciones de formatos de configuración se incluyen las siguientes:
- Diseñador de configuraciones
- Especificar datos XML

Cuando se elige el **Diseñador de configuraciones**, la hoja **Agregar aplicación** cambiará para ofrecer otras dos opciones de configuración:
- Configurar conjunto de aplicaciones
- Configuración del conjunto de aplicaciones

<img alt="Add Office 365 - Configuration designer" src="./media/apps-add-office365/apps-add-office365-02.png" width="700">

Cuando se elige **Especificar datos XML**, la hoja **Agregar aplicación** mostrará la opción **Especificar datos XML**. Selecciónela para mostrar la hoja **Archivo de configuración**. 

![Diseñador de configuraciones para agregar Office 365](./media/apps-add-office365/apps-add-office365-01.png)
    
Para obtener más información sobre la opción **Especificar datos XML**, vea más adelante la sección [Especificar datos XML](apps-add-office365.md#enter-xml-format).

## <a name="configure-app-suite-information"></a>Configuración de la información del conjunto de aplicaciones

En este paso, proporcionará información sobre el conjunto de aplicaciones. Esta información le ayuda a identificar el conjunto de aplicaciones en Intune y, además, ayuda a los usuarios finales a encontrarlo en el Portal de empresa.

1. En el panel **Agregar aplicación**, seleccione **App Suite Information** (Información del conjunto de aplicaciones).
2. En el panel **App Suite Information** (Información del conjunto de aplicaciones), haga lo siguiente:
    - **Nombre del conjunto de aplicaciones**: escriba el nombre del conjunto tal como se muestra en el Portal de empresa. Asegúrese de que todos los nombres de conjuntos de aplicaciones que use sean únicos. Si el mismo nombre del conjunto ya existe, solo se muestra una de las aplicaciones a los usuarios en el portal de empresa.
    - **Descripción del conjunto de aplicaciones** : escriba una descripción del conjunto de aplicaciones. Por ejemplo, podría mostrar las aplicaciones que seleccionó para incluir.
    - **Publicador**: Microsoft aparece como publicador.
    - **Categoría**: de manera opcional, seleccione una o varias de las categorías de aplicaciones integradas o una categoría que haya creado. Este valor facilita que los usuarios encuentren el conjunto de aplicaciones cuando exploren el portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa** : seleccione esta opción para mostrar el conjunto de aplicaciones de forma destacada en la página principal del Portal de empresa cuando los usuarios busquen aplicaciones.
    - **Dirección URL de información**: Opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Dirección URL de privacidad**: Opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Desarrollador**: Microsoft aparece como desarrollador.
    - **Propietario**: Microsoft aparece como propietario.
    - **Notas**: escriba las notas que desea asociar a esta aplicación.
    - **Logotipo**: el logotipo de Office 365 se muestra con la aplicación cuando los usuarios buscan en el Portal de empresa.
3. Seleccione **Aceptar**.

## <a name="configure-app-suite"></a>Configurar conjunto de aplicaciones

Si ha seleccionado la opción **Diseñador de configuraciones** en el cuadro desplegable **Formato de configuración**, verá la opción **Configurar conjunto de aplicaciones** en la hoja **Agregar aplicación**. Seleccione las aplicaciones de Office que quiere asignar a los dispositivos.

1. En el panel **Agregar aplicación**, seleccione **Configure App Suite** (Configurar conjunto de aplicaciones).
2. En el panel **Configure App Suite** (Configurar conjunto de aplicaciones), elija las aplicaciones de Office estándar que quiere asignar a los dispositivos.  
    Además, puede instalar aplicaciones para el cliente de escritorio de Microsoft Project Online y Microsoft Visio Online Plan 2, si posee sus licencias.
3. Seleccione **Aceptar**.

## <a name="configure-app-suite-settings"></a>Configuración del conjunto de aplicaciones

Si ha seleccionado la opción **Diseñador de configuraciones** en el cuadro desplegable **Formato de configuración**, verá la opción **Configuración del conjunto de aplicaciones** en la hoja **Agregar aplicación**. En este paso, configure las opciones de instalación para el conjunto de aplicaciones. La configuración se aplica a todas las aplicaciones que agregó al conjunto.

1. En el panel **Agregar aplicación**, seleccione **App Suite Settings** (Configuración del conjunto de aplicaciones).
2. En el panel **App Suite Settings** (Configuración del conjunto de aplicaciones), haga lo siguiente:
    - **Versión de Office**: elija si quiere asignar la versión de 32 o 64 bits de Office. Puede instalar la versión de 32 bits en dispositivos de 32 y 64 bits, pero en los dispositivos de 64 bits solo puede instalar la versión de 64 bits.
    - **Canal de actualización**: elija cómo Office se actualiza en los dispositivos. Para más información sobre los distintos canales de actualización, consulte [Información general de los canales de actualización para Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus). Elija de entre las siguientes opciones:
        - **Mensual**
        - **Mensual (dirigido)**
        - **Semianual**
        - **Semianual (dirigido)**

        Después de elegir un canal, puede seleccionar **Específico** para instalar una versión específica de Office del canal seleccionado en los dispositivos del usuario final. A continuación, seleccione la **versión específica** de Office que quiera usar.
        
        Las versiones disponibles cambiarán con el tiempo. Por lo tanto, al crear una nueva implementación, las versiones disponibles pueden ser más recientes y no tener determinadas versiones anteriores disponibles. Las implementaciones actuales seguirán implementando la versión anterior, pero la lista de versiones se actualizará continuamente por canal.
        
        En el caso de los dispositivos que actualicen su versión anclada (o cualquier otra propiedad) y se implementen a medida que estén disponibles, el estado de informe se mostrará como Instalado si han instalado la versión anterior hasta que se registre el dispositivo. Una vez que se registre, el estado cambiará de forma temporal a Desconocido. Sin embargo, este estado no se mostrará a los usuarios. Cuando un usuario inicie la instalación de la versión más reciente disponible, este verá el estado cambiado a Instalado.
        
        Para más información, vea [Información general de los canales de actualización para Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

    - **Remove MSI from end-user devices** (Quitar MSI de los dispositivos de usuario final): elija si quiere quitar las aplicaciones .MSI preexistentes de Office de los dispositivos de usuario final. La instalación no funcionará si hay aplicaciones .MSI preexistentes en los dispositivos de usuario final. Las aplicaciones que se deben desinstalar no se limitan a las seleccionadas para la instalación en **Configure App Suite** (Configurar App Suite), ya que quitarán todas las aplicaciones de Office (MSI) del dispositivo del usuario final. Para obtener más información, vea [Remove existing MSI versions of Office when upgrading to Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version) (Quitar las versiones de MSI de Office al actualizar a Office 365 ProPlus). Cuando Intune reinstala Office en los equipos de los usuarios finales, estos recibirán automáticamente los mismos paquetes de idioma que tenían con las instalaciones de Office .MSI anteriores. 
    - **Aceptar automáticamente el contrato de licencia para el usuario final de la aplicación**: seleccione esta opción si no necesita que los usuarios finales acepten el contrato de licencia. De ese modo, Intune aceptará automáticamente el contrato.
    - **Usar activación en equipos compartidos**: seleccione esta opción cuando varios usuarios compartan un equipo. Para obtener más información, vea [Introducción a la activación de equipos compartidos para Office 365](https://docs.microsoft.com/DeployOffice/overview-of-shared-computer-activation-for-office-365-proplus).
    - **Idiomas**: Office se instala automáticamente en cualquier idioma compatible que se instale con Windows en el dispositivo de los usuarios finales. Seleccione esta opción si desea instalar más idiomas con el conjunto de aplicaciones. <p></p>
    Puede implementar idiomas adicionales para las aplicaciones Office 365 Pro Plus administradas mediante Intune. La lista de idiomas disponibles incluye el **Tipo** de paquete de idioma (núcleo, parcial y corrección). En Azure Portal, seleccione **Microsoft Intune** > **Aplicaciones cliente** > **Aplicaciones** > **Agregar**. En la lista **Tipo de aplicación** de la hoja **Agregar aplicación**, seleccione **Windows 10** en **Conjunto de aplicaciones de Office 365**. Seleccione **Idiomas** en la hoja **Configuración del conjunto de aplicaciones**. Para más información, vea [Información general acerca de la implementación de idiomas en Office 365 ProPlus](https://docs.microsoft.com/deployoffice/overview-of-deploying-languages-in-office-365-proplus).

## <a name="select-scope-tags-optional"></a>Selección de Etiquetas de ámbito (opcional)
Puede usar las etiquetas de ámbito para determinar quién puede ver información de la aplicación cliente en Intune. Para obtener más información sobre las etiquetas de ámbito, consulte [Use role-based access control and scope tags for distributed IT](../fundamentals/scope-tags.md) (Uso del control de acceso basado en roles y de las etiquetas de ámbito para la TI distribuida).

1. Seleccione **Ámbito (Etiquetas)**  > **Agregar**.
2. Use el cuadro **Seleccionar** para buscar las etiquetas de ámbito.
3. Seleccione la casilla de verificación situada junto a las etiquetas de ámbito que desea asignar a esta aplicación.
4. Elija **Seleccionar** > **Aceptar**.

## <a name="enter-xml-format"></a>Especificar formato XML

Si ha seleccionado la opción **Especificar datos XML** en el cuadro desplegable **Formato de configuración**, verá la opción **Enter XML format** (Especificar formato XML) en la hoja **Agregar aplicación**. Para obtener más información, vea [Opciones de configuración de la Herramienta de implementación de Office](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

## <a name="finish-up"></a>Finalizar

Cuando haya terminado, en el panel **Agregar aplicación**, seleccione **Agregar**. La aplicación que ha creado aparece en la lista de aplicaciones.

## <a name="troubleshooting"></a>Solucionar problemas
Intune utiliza la [Herramienta de implementación de Office](https://docs.microsoft.com/DeployOffice/overview-of-the-office-2016-deployment-tool) para descargar e implementar Office 365 ProPlus en los equipos cliente mediante la red [CDN de Office 365](https://docs.microsoft.com/office365/enterprise/content-delivery-networks). Consulte los procedimientos recomendados que se describen en [Administración de puntos de conexión de Office 365](https://docs.microsoft.com/office365/enterprise/managing-office-365-endpoints) para asegurarse de que la configuración de red permite a los clientes tener acceso a la red CDN directamente en lugar de enrutar el tráfico de la red CDN a través de servidores proxy centrales para evitar la introducción de una latencia innecesaria.

Ejecute el [Asistente de soporte y recuperación para Office 365 de Microsoft](https://diagnostics.office.com) en un dispositivo específico si tiene problemas de instalación o de ejecución.

## <a name="errors-during-installation-of-the-app-suite"></a>Errores durante la instalación del conjunto de aplicaciones

Consulte [How to enable Office 365 ProPlus ULS logging](https://blogs.technet.microsoft.com/odsupport/2018/06/18/how-to-enable-office-365-proplus-uls-logging) (Habilitación del registro de ULS de Office 365 ProPlus) para obtener información sobre cómo ver los registros de instalación detallados.

En la tabla siguiente se muestran los códigos de error comunes que podría encontrar y su significado.

### <a name="status-for-office-csp"></a>Estado de Office CSP

| Estado | Fase | Descripción |
|--------------------------------------------------|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1460 (ERROR_TIMEOUT) | Descarga | No se pudo descargar la Herramienta de implementación de Office |
| 13 (ERROR_INVALID_DATA) | - | No se puede comprobar la firma de la Herramienta de implementación de Office descargada |
| Código de error de CertVerifyCertificateChainPolicy | - | No se pudo comprobar la certificación de la Herramienta de implementación de Office descargada |
| 997 | WIP | Instalación |
| 0 | Después de la instalación | La instalación se realizó correctamente |
| 1603 (ERROR_INSTALL_FAILURE) | - | Error de cualquier comprobación de requisitos previos, como: SxS (se intentó instalar cuando MSI 2016 está instalado), versiones no coincidentes u otros |
| 0x8000ffff (E_UNEXPECTED) | - | Se intentó desinstalar sin Hacer clic y ejecutar de Office en el equipo. |
| 17002 | - | No se pudo completar el escenario (instalación). Posibles razones: instalación cancelada por el usuario, instalación cancelada por otra instalación, espacio en disco insuficiente durante la instalación o identificador de idioma desconocido |
| 17004 | - | SKU desconocidas |


### <a name="office-deployment-tool-error-codes"></a>Códigos de error de la Herramienta de implementación de Office

| Escenario | Código de retorno | UI | Nota |
|------------------------------------------------------------------------------------------------------------------|---------------------------------------|----------------------------------------------------|------------------------------------|
| Trabajo de desinstalación sin una instalación de Hacer clic y ejecutar activa | -2147418113, 0x8000ffff o 2147549183 | Código de error: Código de error 30088 1008: 30125-1011 (404) | Herramienta de implementación de Office |
| Instalación cuando hay instalada una versión de MSI | 1603 | - | Herramienta de implementación de Office |
| El usuario u otra instalación canceló la instalación | 17002 | - | Hacer clic y ejecutar |
| Intentar instalar 64 bits en un dispositivo con 32 bits instalados. | 1603 | - | Código de devolución de la Herramienta de implementación de Office |
| Intentar instalar una SKU desconocida (no es un caso de uso legítimo de Office CSP porque solo podemos pasar SKU válidas) | 17004 | - | Hacer clic y ejecutar |
| Falta de espacio | 17002 | - | Hacer clic y ejecutar |
| El cliente Hacer clic y ejecutar no se pudo iniciar (inesperado) | 17000 | - | Hacer clic y ejecutar |
| El cliente Hacer clic y ejecutar no pudo poner el escenario en cola (inesperado) | 17001 | - | Hacer clic y ejecutar |

## <a name="next-steps"></a>Pasos siguientes

- Para asignar las aplicaciones a los grupos que elija, consulte [Asignación de aplicaciones a grupos](/intune-azure/manage-apps/deploy-apps).
