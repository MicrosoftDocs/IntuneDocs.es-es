---
title: Adición de aplicaciones de Office 365 a dispositivos Windows 10 mediante Microsoft Intune
titleSuffix: ''
description: Obtenga información sobre cómo usar Microsoft Intune para instalar aplicaciones de Office 365 en dispositivos Windows 10.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: b566dd58b01a411126ffabb46d526e4480c2ba0a
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2019
ms.locfileid: "75205979"
---
# <a name="add-office-365-apps-to-windows-10-devices-with-microsoft-intune"></a>Adición de aplicaciones de Office 365 a dispositivos Windows 10 con Microsoft Intune

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
- Actualmente no se admiten las implementaciones de varias instancias de Office 365. Solo se entregará una implementación al dispositivo.
- **Versión de Office**: elija si quiere asignar la versión de 32 o 64 bits de Office. Puede instalar la versión de 32 bits en dispositivos de 32 y 64 bits, pero en los dispositivos de 64 bits solo puede instalar la versión de 64 bits.
- **Remove MSI from end-user devices** (Quitar MSI de los dispositivos de usuario final): elija si quiere quitar las aplicaciones .MSI preexistentes de Office de los dispositivos de usuario final. La instalación no funcionará si hay aplicaciones .MSI preexistentes en los dispositivos de usuario final. Las aplicaciones que se deben desinstalar no se limitan a las seleccionadas para la instalación en **Configure App Suite** (Configurar App Suite), ya que quitarán todas las aplicaciones de Office (MSI) del dispositivo del usuario final. Para obtener más información, vea [Remove existing MSI versions of Office when upgrading to Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version) (Quitar las versiones de MSI de Office al actualizar a Office 365 ProPlus). Cuando Intune reinstala Office en los equipos de los usuarios finales, estos recibirán automáticamente los mismos paquetes de idioma que tenían con las instalaciones de Office .MSI anteriores.

## <a name="get-started"></a>Introducción

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Aplicaciones** > **Todas las aplicaciones** > **Agregar**.
3. En el panel **Agregar aplicaciones**, en la lista **Tipo de aplicación**, vaya a **Office 365 Suite** y seleccione **Windows 10**.

## <a name="select-settings-format"></a>Selección del formato de configuración

Si quiere elegir un método para configurar la configuración de la aplicación, seleccione un **formato de configuración**. Entre las opciones de formatos de configuración se incluyen las siguientes:
- Diseñador de configuraciones
- Especificar datos XML

Cuando se elige el **Diseñador de configuraciones**, el panel **Agregar aplicación** cambiará para ofrecer otras dos opciones de configuración:
- Configurar conjunto de aplicaciones
- Configuración del conjunto de aplicaciones

<img alt="Add Office 365 - Configuration designer" src="./media/apps-add-office365/apps-add-office365-02.png" width="700">

Cuando se elige **Especificar datos XML**, el panel **Agregar aplicación** mostrará la opción **Especificar datos XML**. Selecciónela para mostrar el panel **Archivo de configuración**. 

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

Si ha seleccionado la opción **Diseñador de configuraciones** en el cuadro desplegable **Formato de configuración**, verá la opción **Configurar conjunto de aplicaciones** en el panel **Agregar aplicación**. Seleccione las aplicaciones de Office que quiere asignar a los dispositivos.

1. En el panel **Agregar aplicación**, seleccione **Configure App Suite** (Configurar conjunto de aplicaciones).
2. En el panel **Configure App Suite** (Configurar conjunto de aplicaciones), elija las aplicaciones de Office estándar que quiere asignar a los dispositivos.  
    Además, puede instalar aplicaciones para el cliente de escritorio de Microsoft Project Online y Microsoft Visio Online Plan 2, si posee sus licencias.
3. Seleccione **Aceptar**.

## <a name="configure-app-suite-settings"></a>Configuración del conjunto de aplicaciones

Si ha seleccionado la opción **Diseñador de configuraciones** en el cuadro desplegable **Formato de configuración**, verá la opción **Configuración del conjunto de aplicaciones** en el panel **Agregar aplicación**. En este paso, configure las opciones de instalación para el conjunto de aplicaciones. La configuración se aplica a todas las aplicaciones que agregó al conjunto.

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
    Puede implementar idiomas adicionales para las aplicaciones Office 365 Pro Plus administradas mediante Intune. La lista de idiomas disponibles incluye el **Tipo** de paquete de idioma (núcleo, parcial y corrección). En Azure Portal, seleccione **Microsoft Intune** > **Aplicaciones** > **Todas las aplicaciones** > **Agregar**. En la lista **Tipo de aplicación** del panel **Agregar aplicación**, seleccione **Windows 10** en **Conjunto de aplicaciones de Office 365**. Seleccione **Idiomas** en el panel **Configuración del conjunto de aplicaciones**. Para más información, vea [Información general acerca de la implementación de idiomas en Office 365 ProPlus](https://docs.microsoft.com/deployoffice/overview-of-deploying-languages-in-office-365-proplus).

## <a name="select-scope-tags-optional"></a>Selección de Etiquetas de ámbito (opcional)
Puede usar las etiquetas de ámbito para determinar quién puede ver información de la aplicación cliente en Intune. Para obtener más información sobre las etiquetas de ámbito, consulte [Use role-based access control and scope tags for distributed IT](../fundamentals/scope-tags.md) (Uso del control de acceso basado en roles y de las etiquetas de ámbito para la TI distribuida).

1. Seleccione **Ámbito (Etiquetas)**  > **Agregar**.
2. Use el cuadro **Seleccionar** para buscar las etiquetas de ámbito.
3. Seleccione la casilla de verificación situada junto a las etiquetas de ámbito que desea asignar a esta aplicación.
4. Elija **Seleccionar** > **Aceptar**.

## <a name="enter-xml-format"></a>Especificar formato XML

Si ha seleccionado la opción **Especificar datos XML** en el cuadro desplegable **Formato de configuración**, verá la opción **Enter XML format** (Especificar formato XML) en el panel **Agregar aplicación**. Para obtener más información, vea [Opciones de configuración de la Herramienta de implementación de Office](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

## <a name="finish-up"></a>Finalizar

Cuando haya terminado, en el panel **Agregar aplicación**, seleccione **Agregar**. La aplicación que ha creado aparece en la lista de aplicaciones. El siguiente paso consiste en asignar las aplicaciones a los grupos que elija. Para más información, consulte [Asignación de aplicaciones a grupos con Microsoft Intune](~/apps/apps-deploy.md).

## <a name="deployment-details"></a>Detalles de implementación

Cuando la directiva de implementación de Intune está asignada a los equipos de destino mediante el [proveedor de servicios de configuración (CSP) de Office](https://docs.microsoft.com/windows/client-management/mdm/office-csp), el dispositivo final descargará automáticamente el paquete de instalación desde la ubicación *officecdn.microsoft.com*. Verá dos directorios que aparecen en el directorio *Archivos de programa*:

![Paquetes de instalación de Office en el directorio Archivos de programa](./media/apps-add-office365/office-folder.png)

En el directorio *Microsoft Office*, se crea una nueva carpeta donde se almacenan los archivos de instalación:

![Nueva carpeta creada en el directorio Microsoft Office](./media/apps-add-office365/created-folder.png)

En el directorio *Microsoft Office 15*, se almacenan los archivos del iniciador de instalación de Hacer clic y ejecutar de Office. La instalación se iniciará automáticamente si se requiere el tipo de asignación:

![Archivos del iniciador de instalación de hacer clic y ejecutar](./media/apps-add-office365/clicktorun-files.png)

La instalación se realizará en modo silencioso si la asignación del conjunto de O365 se configura según sea necesario. Los archivos de instalación descargados se eliminarán una vez que la instalación se haya realizado correctamente. Si la asignación se configura como **disponible**, las aplicaciones de Office aparecerán en la aplicación Portal de empresa para que los usuarios finales puedan desencadenar la instalación manualmente.

## <a name="troubleshooting"></a>Solución de problemas
Intune utiliza la [Herramienta de implementación de Office](https://docs.microsoft.com/DeployOffice/overview-of-the-office-2016-deployment-tool) para descargar e implementar Office 365 ProPlus en los equipos cliente mediante la red [CDN de Office 365](https://docs.microsoft.com/office365/enterprise/content-delivery-networks). Consulte los procedimientos recomendados que se describen en [Administración de puntos de conexión de Office 365](https://docs.microsoft.com/office365/enterprise/managing-office-365-endpoints) para asegurarse de que la configuración de red permite a los clientes tener acceso a la red CDN directamente en lugar de enrutar el tráfico de la red CDN a través de servidores proxy centrales para evitar la introducción de una latencia innecesaria.

Ejecute el [Asistente de soporte y recuperación para Office 365 de Microsoft](https://diagnostics.office.com) en un dispositivo específico si tiene problemas de instalación o de ejecución.

### <a name="additional-troubleshooting-details"></a>Detalles adicionales de solución de problemas

Si no puede instalar las aplicaciones de O365 en un dispositivo, debe identificar si el problema está relacionado con Intune o con Office o sistema operativo. Si puede ver las dos carpetas *Microsoft Office* y *Microsoft Office 15* aparecen en el directorio *Archivos de programa* del dispositivo, puede confirmar que Intune ha iniciado la implementación correctamente. Si no puede ver las dos carpetas en *Archivos de programa*, debe confirmar los casos siguientes:

- El dispositivo está inscrito correctamente en Microsoft Intune. 
- Hay una conexión de red activa en el dispositivo. Si el dispositivo está en modo avión, está desactivado o se encuentra en una ubicación sin servicio, la directiva no se aplicará hasta que se establezca la conectividad de red.
- Se cumplen los requisitos de red de Intune y Office 365 y se puede obtener acceso a los intervalos de IP relacionados en función de los siguientes artículos:

  - [Ancho de banda y requisitos de configuración de red de Intune](https://docs.microsoft.com/intune/network-bandwidth-use)
  - [Intervalos de direcciones IP y URL de Office 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)

- A los grupos correctos se les ha asignado el conjunto de aplicaciones de O365. 

Además, supervise el tamaño del directorio *C:\Archivos de programa\Microsoft Office\Updates\Download*. El paquete de instalación descargado de la nube de Intune se almacenará en esta ubicación. Si el tamaño no aumenta o solo aumenta muy lentamente, se recomienda comprobar la conectividad de red y el ancho de banda.

Cuando pueda concluir que tanto Intune como la infraestructura de red funcionan según lo previsto, debe analizar aún más el problema desde la perspectiva del sistema operativo. Considere las condiciones siguientes:

- El dispositivo de destino debe ejecutarse en Windows 10 Creators Update o posterior.
- No se abre ninguna aplicación de Office existente mientras Intune implementa las aplicaciones.
- Las versiones existentes de MSI de Office se han quitado correctamente del dispositivo. Intune emplea Hacer clic y ejecutar de Office, que no es compatible con MSI de Office. Este comportamiento se menciona en este documento:<br>
  [No se admite en el mismo equipo Office instalado con Hacer clic y ejecutar y Windows Installer](https://support.office.com/article/office-installed-with-click-to-run-and-windows-installer-on-same-computer-isn-t-supported-30775ef4-fa77-4f47-98fb-c5826a6926cd).
- El usuario de inicio de sesión debe tener permiso para instalar aplicaciones en el dispositivo.
- Confirme que no hay ningún problema basado en **Registros de Windows** -> **Aplicaciones** del registro del Visor de eventos de Windows.
- Capture los registros detallados de la instalación de Office durante la instalación. Para ello, siga estos pasos:<br>
    1. Active el registro detallado para la instalación de Office en las máquinas de destino. Para ello, ejecute el siguiente comando para modificar el registro:<br>
        `reg add HKLM\SOFTWARE\Microsoft\ClickToRun\OverRide /v LogLevel /t REG_DWORD /d 3`<br>
    2. Vuelva a implementar el conjunto de Office 365 en los dispositivos de destino.<br>
    3. Espere aproximadamente de 15 a 20 minutos y vaya a la carpeta **%temp%** y la carpeta **%windir%\temp**, ordene por la **fecha de modificación**, seleccione los archivos *{nombre de la máquina}-{TimeStamp}.log* que se modifican según el tiempo de reproducción.<br>
    4. Ejecute el siguiente comando para deshabilitar el registro detallado:<br>
        `reg delete HKLM\SOFTWARE\Microsoft\ClickToRun\OverRide /v LogLevel /f`<br>
        Los registros detallados pueden proporcionar información más detallada sobre el proceso de instalación.

## <a name="errors-during-installation-of-the-app-suite"></a>Errores durante la instalación del conjunto de aplicaciones

Consulte [How to enable Office 365 ProPlus ULS logging](/office/troubleshoot/diagnostic-logs/how-to-enable-office-365-proplus-uls-logging) (Habilitación del registro de ULS de Office 365 ProPlus) para obtener información sobre cómo ver los registros de instalación detallados.

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
