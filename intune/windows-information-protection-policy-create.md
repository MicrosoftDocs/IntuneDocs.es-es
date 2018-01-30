---
title: "Creación e implementación de una directiva de protección de aplicaciones de Windows Information Protection (WIP) con Intune"
titlesuffix: Azure portal
description: "Creación e implementación de una directiva de protección de aplicaciones de WIP con Intune"
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 12/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4e3627bd-a9fd-49bc-b95e-9b7532f0ed55
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 97f9407c8ba93307059e44c8becf4f7a36c6861a
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="create-and-deploy-windows-information-protection-wip-app-protection-policy-with-intune"></a>Creación e implementación de una directiva de protección de aplicaciones de Windows Information Protection (WIP) con Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A partir de la versión de Intune 1704, puede usar las directivas de protección de aplicaciones con Windows 10 para proteger aplicaciones sin la inscripción de dispositivos.

## <a name="before-you-begin"></a>Antes de comenzar

Hablemos sobre algunos conceptos que aparecen al agregar una directiva de WIP.

### <a name="list-of-allowed-and-exempt-apps"></a>Lista de aplicaciones permitidas y exentas

-   **Aplicaciones permitidas**: estas son las aplicaciones que deben cumplir esta directiva.

-   **Aplicaciones exentas**: estas aplicaciones están exentas del cumplimiento de esta directiva y pueden acceder a los datos corporativos sin restricciones.

### <a name="types-of-apps"></a>Tipos de aplicaciones

-   **Aplicaciones recomendadas**: lista rellenada previamente de aplicaciones (en su mayoría de Microsoft Office) que permite una importación sencilla en la directiva. <!---I really don't know what you mean by "easily import into policy"--->

-   **Aplicaciones de la Tienda**: puede agregar cualquier aplicación de la Tienda Windows a la directiva.

-   **Aplicaciones de escritorio de Windows**: puede agregar cualquier aplicación de escritorio tradicional de Windows a la directiva (por ejemplo, .exe, .dll, etc.).

## <a name="pre-requisites"></a>Requisitos previos

Debe configurar el proveedor de MAM para poder crear una directiva de protección de la aplicación de WIP. Obtenga más información sobre [cómo configurar el proveedor de MAM con Intune](https://docs.microsoft.com/app-protection-policies-configure-windows-10.md).

Además, necesita lo siguiente:

-   Una licencia de [Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium).
-   [Windows Creators Update](https://blogs.windows.com/windowsexperience/2017/04/11/how-to-get-the-windows-10-creators-update/#o61bC2PdrHslHG5J.97)

> [!IMPORTANT]
> WIP no admite varias identidades, solo puede existir una identidad administrada al mismo tiempo.
<!---Should you be linking to a topic that explains what multi-identity is?--->

## <a name="to-add-a-wip-policy"></a>Para agregar una directiva de WIP

Una vez configurado Intune en su organización, puede crear una directiva específica de WIP a través de [Azure Portal](https://docs.microsoft.com/intune-classic/deploy-use/azure-portal-for-microsoft-intune-mam-policies). <!---Is there an azure topic you can use instead of a classic? if not, should this topic be moved into the azure docset?--->

1.  Vaya al **panel de administración de aplicaciones móviles de Intune**, elija **Toda la configuración** > **Directiva de aplicaciones**.

2.  En la hoja **Directiva de aplicaciones**, elija **Agregar una directiva** y, a continuación, escriba los siguientes valores:

    a.  **Nombre:** escriba un nombre (necesario) para la nueva directiva.

    b.  **Descripción**: escriba una descripción opcional.

    c.  **Plataforma:** elija **Windows 10** como plataforma admitida para la directiva de protección de aplicaciones.

    d.  **Estado de inscripción:** elija **Sin inscripción** como estado de inscripción para la directiva.

3.  Elija **Crear**. La directiva se crea y aparece en la tabla de la hoja **Directiva de aplicaciones**.

## <a name="to-add-recommended-apps-to-your-allowed-apps-list"></a>Para agregar aplicaciones recomendadas a la lista de aplicaciones permitidas

1.  En la hoja **Directiva de aplicaciones**, elija el nombre de la directiva y luego elija **Aplicaciones permitidas** desde la hoja **Agregar una directiva**. Se abre la hoja de **Aplicaciones permitidas**, que muestra todas las aplicaciones que ya están incluidas en la lista para esta directiva de protección de aplicaciones.

2.  En la hoja **Aplicaciones permitidas**, elija **Agregar aplicaciones**. Se abre la hoja **Agregar aplicaciones**, que muestra todas las aplicaciones que forman parte de esta lista.

3.  Seleccione cada aplicación a la que desea conceder acceso a los datos corporativos y, a continuación, seleccione **Aceptar**. La hoja **Aplicaciones permitidas** se actualiza y muestra todas las aplicaciones seleccionadas.

## <a name="add-a-store-app-to-your-allowed-apps-list"></a>Agregar una aplicación de la Tienda a la lista de aplicaciones permitidas

**Para agregar una aplicación de la Tienda**

1.  En la hoja **Directiva de aplicaciones**, elija el nombre de la directiva y luego elija **Aplicaciones permitidas** en el menú que aparece con todas las aplicaciones que ya están incluidas en la lista para esta directiva de protección de aplicaciones.

2.  En la hoja **Aplicaciones permitidas**, elija **Agregar aplicaciones**.

3.  En la hoja **Agregar aplicaciones**, elija **Aplicaciones de la Tienda** en la lista desplegable. La hoja cambia para mostrar cuadros que le permiten agregar un **publicador** y el **nombre** de una aplicación.

4.  Escriba el nombre de la aplicación y el nombre de su publicador y, a continuación, elija **Aceptar**.

    > [!TIP]
    > Este es un ejemplo de aplicación, donde el **Publicador** es *CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US* y el **nombre** del producto es *Microsoft.MicrosoftAppForWindows*.

5.  Después de haber especificado la información en los campos, elija **Aceptar** para agregar la aplicación a la lista de **Aplicaciones permitidas**.

> [!NOTE]
> Para agregar varias aplicaciones de la Tienda a la vez, puede hacer clic en el menú **(…)** al final de la fila de aplicaciones y luego seguir agregando más aplicaciones. Cuando haya terminado, elija **Aceptar**.

## <a name="add-a-desktop-app-to-your-allowed-apps-list"></a>Agregar una aplicación de escritorio a la lista de aplicaciones permitidas

**Para agregar una aplicación de escritorio**

1.  En la hoja **Directiva de aplicaciones**, elija el nombre de la directiva y luego elija **Aplicaciones permitidas**. Se abre la hoja de **Aplicaciones permitidas**, que muestra todas las aplicaciones que ya están incluidas en la lista para esta directiva de protección de la aplicación.

2.  En la hoja **Aplicaciones permitidas**, elija **Agregar aplicaciones**.

3.  En la hoja **Agregar aplicaciones**, elija **Aplicaciones de escritorio** en la lista desplegable.

4.  Después de haber especificado la información en los campos, elija **Aceptar** para agregar la aplicación a la lista de **Aplicaciones permitidas**.

> [!NOTE]
> Para agregar varias **aplicaciones de escritorio** a la vez, puede hacer clic en el menú **(…)** al final de la fila de aplicaciones y luego seguir agregando más aplicaciones. Cuando haya terminado, elija **Aceptar**.

## <a name="wip-learning"></a>Aprendizaje de WIP
<!---You've already defined WIP earlier in the topic. You don't need to keep doing so. --->
Después de agregar las aplicaciones que desea proteger con WIP, debe aplicar un modo de protección mediante **Aprendizaje de WIP**.

### <a name="before-you-begin"></a>Antes de comenzar

El Aprendizaje de WIP es un informe que permite supervisar las aplicaciones desconocidas de WIP. Las aplicaciones desconocidas son las que no ha implementado el departamento de TI de su organización. Puede exportar estas aplicaciones desde el informe y agregarlas a sus directivas de WIP para evitar la interrupción de productividad antes de exigir WIP en modo "Bloquear".

Se recomienda que empiece con **Silencioso** o **Permitir invalidaciones** al comprobar con un pequeño grupo que tiene las aplicaciones adecuadas en la lista de aplicaciones permitidas. Cuando haya terminado, puede cambiar a la directiva de aplicación final, **Bloquear**.

### <a name="what-are-the-protection-modes"></a>¿Cuáles son los modos de protección?

#### <a name="block"></a>Bloquear
WIP busca prácticas de uso compartido de datos inapropiadas y no permite al usuario completar la acción. Esto puede incluir el uso compartido de información entre aplicaciones protegidas no corporativas y el uso compartido de datos corporativos entre otras personas y dispositivos no pertenecientes a su organización.

#### <a name="allow-overrides"></a>Permitir invalidaciones
WIP busca el uso compartido de datos inapropiado, avisando a los usuarios si hacen algo que se considera potencialmente no seguro. Sin embargo, este modo permite al usuario reemplazar la directiva y compartir los datos, registrando la acción en el registro de auditoría.

#### <a name="silent"></a>Silencioso
WIP se ejecuta en modo silencioso, ya que registra el uso compartido de datos inadecuado sin bloquear nada que se hubiera solicitado en la interacción con el empleado en el modo Permitir invalidaciones. Las acciones no permitidas, como las aplicaciones que intentan de manera inapropiada obtener acceso a un recurso de red o a datos protegidos por WIP, se siguen deteniendo.

#### <a name="off-not-recommended"></a>Desactivado (no recomendado)
WIP está desactivado y no ayuda a proteger o auditar los datos.

Una vez desactivado WIP, se realiza un intento de descifrar los archivos etiquetados con WIP en las unidades conectadas localmente. Tenga en cuenta que la información anterior de descifrado y directiva no se vuelve a aplicar automáticamente si vuelve a activar la protección de WIP.

### <a name="add-a-protection-mode"></a>Agregar un modo de protección

1.  En la hoja **Directiva de aplicaciones**, seleccione el nombre de la directiva y elija **Valores obligatorios**.

    ![Captura de pantalla del modo de aprendizaje](./media/learning-mode-sc1.png)

1.  Elija **Guardar**.

### <a name="use-wip-learning"></a>Uso del aprendizaje de WIP

1. Abra Azure Portal. Elija **Más servicios**. Escriba **Intune** en el filtro del cuadro de texto.

3. Elija **Intune** > **Aplicaciones móviles**.

4. Elija **Estado de protección de la aplicación** > **Informes** > **Aprendizaje de Windows Information Protection**.  
 
    Una vez que tenga las aplicaciones que se muestran en el informe de registro del aprendizaje de WIP, puede agregarlas a las directivas de protección de aplicaciones.

## <a name="deploy-your-wip-app-protection-policy"></a>Implementación de la directiva de protección de aplicaciones de WIP

> [!IMPORTANT]
> Este contenido corresponde a WIP sin la inscripción de dispositivos.

<!---not sure why you need the Important note. Isn't this what the topic is about? app protection w/o enrollment?--->

Después de crear la directiva de protección de aplicaciones de WIP, debe implementarla en su organización mediante MAM.

1.  En la hoja **Directiva de aplicaciones**, seleccione la directiva de protección de aplicaciones recién creada y elija **Grupos de usuarios** > **Agregar grupo de usuarios**.

    Se abre una lista de grupos de usuarios, que consta de todos los grupos de seguridad de Azure Active Directory, en la hoja **Agregar grupo de usuarios**.

1.  Seleccione el grupo al que quiere que se aplique la directiva y, después, elija **Seleccionar** para implementar la directiva.
