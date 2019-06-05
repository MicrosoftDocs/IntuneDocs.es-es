---
title: 'Habilitación de conexiones de datos de eSIM en Microsoft Intune: Azure | Microsoft Docs'
description: Agregue o use eSIM para obtener acceso a Internet y a datos con otros planes de datos. En Intune, agregue o importe códigos de activación y, después, asígnelos mediante un perfil de configuración. También puede supervisar los perfiles de eSIM y comprobar el estado de los dispositivos habilitados para eSIM.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/31/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 68a0372180cf516f5a0111cd8fdb7cbd9535f075
ms.sourcegitcommit: a97b6139770719afbd713501f8e50f39636bc202
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402728"
---
# <a name="configure-esim-cellular-profiles-in-intune---public-preview"></a>Configurar perfiles de telefonía móvil eSIM en Intune: versión preliminar pública

> [!NOTE]
> A Microsoft le gustaría conocer su opinión. Envíe preguntas o inicie una discusión por medio de un correo electrónico a `eSIMonIntune@microsoft.com`.

## <a name="introduction"></a>Introducción

eSIM es un chip SIM incrustado y permite conectarse a Internet a través de una conexión de datos móviles en un dispositivo compatible con eSIM, como [LTE Surface Pro](https://www.microsoft.com/surface/business/surface-pro). Con un eSIM, no es necesario obtener una tarjeta SIM del operador de telefonía móvil. Como viajero global, también puede cambiar entre los operadores de telefonía móviles y los planes de datos para estar siempre conectado.

Por ejemplo, tiene un plan de datos móviles para el trabajo y otro con un operador de telefonía móvil distinto para uso personal. Cuando viaja, puede obtener acceso a Internet mediante la búsqueda de operadores de telefonía móvil con planes de datos en esa zona.

En Intune, puede importar códigos de activación de un solo uso proporcionados por el operador de telefonía móvil. Para configurar los planes de datos móviles en el módulo eSIM, implemente esos códigos de activación en los dispositivos compatibles con eSIM. Cuando Intune instala el código de activación, el módulo de hardware de eSIM usa los datos del código de activación para ponerse en contacto con el operador de telefonía móvil. Al finalizar, el perfil de eSIM se descarga en el dispositivo y se configura para la activación de telefonía móvil.

Para implementar eSIM en los dispositivos mediante Intune, se necesita lo siguiente:

- **Dispositivos compatibles con eSIM**, como Surface LTE: vea si [el dispositivo admite eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data). O bien, vea una lista de [algunos de los dispositivos compatibles con eSIM conocidos](#esim-capable-devices) (en este artículo).
- **PC con Windows 10 Fall Creators Update** (1709 o posterior) inscrito y administrado mediante MDM por Intune.
- **Códigos de activación** proporcionados por el operador de telefonía móvil. Estos códigos de activación de un solo uso se agregan a Intune y se implementan en los dispositivos compatibles con eSIM. Póngase en contacto con su operador de telefonía móvil para obtener los códigos de activación de eSIM.

## <a name="deploy-esim-to-devices---overview"></a>Implementar eSIM en dispositivos: Introducción

Para implementar eSIM en los dispositivos, un administrador realiza las tareas siguientes:

1. Importa los códigos de activación proporcionados por el operador de telefonía móvil.
2. Crea un grupo de dispositivos de Azure Active Directory (Azure AD) que incluye los dispositivos compatibles con eSIM.
3. Asigna al grupo de Azure AD al grupo de suscripciones importadas.
4. Supervisa la implementación.

Este artículo le guiará a través de estos pasos.

## <a name="esim-capable-devices"></a>Dispositivos compatibles con eSIM

Los dispositivos siguientes se han anunciado como compatibles con eSIM, o bien están en el mercado en la actualidad. Además, compruebe si [el dispositivo admite eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

- Acer Swift 7
- Asus NovoGo TP370QL
- Asus TP401
- Asus Transformer Mini T103
- HP Elitebook G5
- HP Envy x2
- HP Probook G5
- Lenovo Miix 630
- Lenovo T480
- Samsung Galaxy Book
- Surface Pro LTE
- HP Spectre Folio 13
- Lenovo Yoga C630

## <a name="step-1-add-cellular-activation-codes"></a>Paso 1: Agregar códigos de activación de telefonía móvil

El operador de telefonía móvil proporciona los códigos de activación de telefonía móvil en un archivo separado por comas (.csv). Cuando tenga este archivo, agréguelo a Intune mediante los pasos siguientes:

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com/).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Configuración del dispositivo** > **Perfiles de telefonía móvil eSIM** > **Agregar**.
4. Seleccione el archivo CSV que tenga los códigos de activación.
5. Haga clic en **Aceptar** para guardar los cambios.

#### <a name="csv-file-requirements"></a>Requisitos del archivo CSV

Cuando trabaje con el archivo .csv con los códigos de activación, asegúrese de que usted o el operador de telefonía móvil cumple los requisitos siguientes:

- El archivo debe estar en formato .csv (nombrearchivo.csv).
- La estructura del archivo debe adherirse a un formato estricto. De lo contrario, se produce un error en la importación. Intune comprueba el archivo durante la importación y, si se detectan errores, se produce un error.
- Los códigos de activación se usan una vez. No se recomienda importar códigos de activación que se hayan importado previamente, ya que se pueden producir problemas al implementar en el mismo dispositivo o en otro.
- Cada archivo debe ser específico de un único operador de telefonía móvil y todos los códigos de activación específicos del mismo plan de facturación. Intune distribuye de forma aleatoria los códigos de activación a los dispositivos de destino. No hay ninguna garantía de qué dispositivo obtiene un código de activación específico.
- En un archivo .csv se puede importar un máximo de 1000 códigos de activación.

#### <a name="csv-file-example"></a>Ejemplo de archivo CSV

1. La primera fila y la primera celda del archivo .csv es la dirección URL del servicio de activación de eSIM del operador de telefonía móvil, lo que se denomina SM-DP+ (servidor de preparación de datos de administrador de suscripción). La dirección URL debe ser un nombre de dominio completo (FQDN) sin comas.
2. La segunda fila y todas las posteriores son códigos de activación únicos de un solo uso que incluyen dos valores:

    1. La primera columna es el ICCID (identificador del chip SIM) único.
    2. La segunda columna es el identificador de coincidencia con solo una coma de separación (no hay coma al final). Vea el ejemplo siguiente:

        ![Archivo .csv de ejemplo de código de activación de operador de telefonía móvil](./media/esim-device-configuration/url-activation-code-examples.png)

3. El nombre del archivo .csv se convierte en el nombre del grupo de suscripción de telefonía móvil en Azure Portal. En la imagen anterior, el nombre de archivo es `UnlimitedDataSkynet.csv`. Por tanto, Intune asigna el nombre `UnlimitedDataSkynet.csv` al grupo de suscripciones:

    ![El grupo de suscripciones de telefonía móvil se denomina con el nombre del archivo .csv de código de activación de ejemplo](./media/esim-device-configuration/subscription-pool-name-csv-file.png)

## <a name="step-2-create-an-azure-ad-device-group"></a>Paso 2: Crear un grupo de dispositivos de Azure AD

Cree un grupo de dispositivos que incluya los dispositivos compatibles con eSIM. En [Agregar grupos](groups-add.md) se enumeran los pasos.

> [!NOTE]
> - Solo se seleccionan dispositivos como destino, no usuarios.
> - Se recomienda crear un grupo de dispositivos de Azure AD estático que incluya los dispositivos eSIM. Al usar un grupo se confirma que solo se seleccionan como destino los dispositivos eSIM.

## <a name="step-3-assign-esim-activation-codes-to-devices"></a>Paso 3: Asignar los códigos de activación eSIM a los dispositivos

Asigne el perfil al grupo de Azure AD que incluye los dispositivos eSIM.

1. En [Azure Portal](https://portal.azure.com/), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Configuración del dispositivo** > **Perfiles de telefonía móvil eSIM** > **Perfiles**.
3. En la lista de perfiles, seleccione el grupo de suscripciones de telefonía móvil eSIM que quiera asignar y, luego, **Asignaciones**.
4. Elija **Incluir** para incluir grupos o **Excluir** para excluirlos y, después, seleccione los grupos.

    ![Incluir el grupo de dispositivos para asignar el perfil](./media/esim-device-configuration/include-exclude-groups.png)

5. Al seleccionar los grupos, se elige un grupo de Azure AD. Para seleccionar varios grupos, presione la tecla **Ctrl** y seleccione los grupos.
6. Cuando termine, seleccione **Guardar** para guardar los cambios.

Los códigos de activación de eSIM se usan una vez. Después de que Intune instale un código de activación en un dispositivo, el módulo eSIM se pone en contacto con el operador de telefonía móvil para descargar el perfil de telefonía móvil. Este contacto finaliza con el registro del dispositivo con la red del operador de telefonía móvil.

## <a name="step-4-monitor-deployment"></a>Paso 4: Supervisar la implementación

#### <a name="review-the-deployment-status"></a>Revisar el estado de la implementación

Después de asignar el perfil, puede supervisar el estado de implementación de un grupo de suscripciones.

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com/).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Configuración del dispositivo** > **Perfiles de telefonía móvil eSIM**. Se muestran todos los grupos de suscripción de telefonía móvil eSIM existentes.
4. Seleccione una suscripción y revise el **Estado de implementación**.

#### <a name="check-the-profile-status"></a>Comprobación del estado del perfil
Después de crear el perfil de dispositivo, Intune proporciona gráficos. Estos gráficos muestran el estado de un perfil, por ejemplo, si se asignó correctamente a los dispositivos, o si el perfil muestra un conflicto.

1. Seleccione **Configuración del dispositivo** > **Perfiles de telefonía móvil eSIM** > seleccione una suscripción existente.
2. En la pestaña **Información general**, el gráfico superior muestra el número de dispositivos asignados a la implementación de grupo de suscripción de telefonía móvil eSIM específico.

    También muestra el número de dispositivos de otras plataformas que se asignan al mismo perfil de dispositivo.

    Intune muestra el estado de entrega e instalación del código de activación destinado a los dispositivos.

    - **Dispositivo no sincronizado:** el dispositivo de destino no ha contactado con Intune desde que se creó la directiva de implementación de eSIM.
    - **Activación pendiente**: un estado transitorio cuando Intune está instalando de forma activa el código de activación en el dispositivo.
    - **Activo**: instalación correcta del código de activación.
    - **Error de activación**: no se pudo instalar el código de activación: vea la guía de solución de problemas.

#### <a name="view-the-detailed-device-status"></a>Ver el estado detallado del dispositivo

Puede supervisar y ver una lista detallada de dispositivos que puede ver en Estado del dispositivo.**

1. Seleccione **Configuración del dispositivo** > **Perfiles de telefonía móvil eSIM** > seleccione una suscripción existente.
2. Seleccione **Estado del dispositivo**. Intune muestra detalles adicionales sobre el dispositivo:

  - **Nombre del dispositivo**: nombre del dispositivo de destino.
  - **Usuario**: usuario del dispositivo inscrito.
  - **ICCID**: código único proporcionado por el operador de telefonía móvil dentro del código de activación instalado en el dispositivo.
  - **Estado de activación**: estado de entrega e instalación de Intune del código de activación en el dispositivo.
  - **Estado de la red de telefonía móvil**: estado proporcionado por el operador de telefonía móvil. Realice el seguimiento con el operador de telefonía móvil para solucionar problemas.
  - **Última inserción en el repositorio**: fecha de la última comunicación del dispositivo con Intune.

#### <a name="monitor-esim-profile-details-on-the-actual-device"></a>Supervisar los detalles del perfil de eSIM en el dispositivo

1. En el dispositivo, abra **Configuración** > vaya a **Red e Internet**.
2. Seleccione **Móvil** > **Administrar perfiles de eSIM**
3. Se enumeran los perfiles de eSIM:

    ![Ver los perfiles de eSIM en la configuración del dispositivo](./media/esim-device-configuration/device-settings-cellular-profiles.png)

## <a name="remove-the-esim-profile-from-device"></a>Quitar el perfil de eSIM del dispositivo

Cuando se quita el dispositivo del grupo de Azure AD, también se quita el perfil de eSIM. No olvide:

1. Confirmar que usa el grupo de Azure AD de dispositivos eSIM.
2. Ir al grupo de Azure AD y quitar el dispositivo del grupo.
3. Cuando el dispositivo que se ha quitado se pone en contacto con Intune, se evalúa la directiva actualizada y se quita el perfil de eSIM.

El perfil de eSIM también se quita cuando el usuario [retira](devices-wipe.md#retire) o anula la inscripción del dispositivo, o bien cuando se ejecuta la [acción remota Restablecer dispositivo](devices-wipe.md#wipe) en el dispositivo.

> [!NOTE]
> Es posible que quitar el perfil no detenga la facturación. Póngase en contacto con su operador de telefonía móvil para comprobar el estado de facturación del dispositivo.

## <a name="best-practices--troubleshooting"></a>Procedimientos recomendados y solución de problemas

- Asegúrese de que el archivo .csv tiene el formato apropiado. Confirme que el archivo no incluye códigos duplicados, varios operadores de telefonía móvil ni otros planes de datos. Recuerde que cada archivo debe ser único para un operador de telefonía móvil y un plan de datos móviles.
- Cree un grupo de dispositivos estáticos de Azure AD que solo incluya los dispositivos de eSIM de destino.
- Si hay un problema con el estado de implementación, compruebe lo siguiente:
  - **El archivo no tiene el formato adecuado**: Consulte **Paso 1: Agregar códigos de activación de telefonía móvil** (en este artículo) sobre cómo aplicar el formato correcto al archivo.
  - **Error de activación de telefonía móvil, póngase en contacto con el operador de telefonía móvil**: no se puede activar el código de activación dentro de su red. O bien, se ha producido un error en la descarga del perfil y la activación de telefonía móvil.

## <a name="next-steps"></a>Pasos siguientes
[Configurar perfiles de dispositivo](device-profiles.md)
