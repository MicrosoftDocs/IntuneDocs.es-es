---
title: "Creación e implementación de una directiva de protección de aplicaciones de Windows Information Protection (WIP) con Intune"
titleSuffix: Intune on Azure
description: "Creación e implementación de una directiva de protección de aplicaciones de WIP con Intune"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4e3627bd-a9fd-49bc-b95e-9b7532f0ed55
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 17736751a6cd1813bd03f8092739d8433eb5d9dc
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="create-and-deploy-windows-information-protection-wip-app-protection-policy-with-intune"></a>Creación e implementación de una directiva de protección de aplicaciones de Windows Information Protection (WIP) con Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A partir de la versión de Intune 1704, puede usar las directivas de protección de aplicaciones con Windows 10 en la administración de aplicaciones móviles (MAM) sin el escenario de inscripción.

## <a name="before-you-begin"></a>Antes de comenzar

Hablemos sobre algunos conceptos que aparecen al agregar una directiva de WIP.

### <a name="list-of-allowed-and-exempt-apps"></a>Lista de aplicaciones permitidas y exentas

-   **Aplicaciones permitidas**: estas son las aplicaciones que deben cumplir esta directiva.

-   **Aplicaciones exentas**: estas aplicaciones están exentas del cumplimiento de esta directiva y pueden acceder a los datos corporativos sin restricciones.

### <a name="types-of-apps"></a>Tipos de aplicaciones

-   **Aplicaciones recomendadas**: una lista rellenada previamente de aplicaciones (en su mayoría de Microsoft Office) que permite una importación sencilla en la directiva por los administradores.

-   **Aplicaciones de la Tienda**: el administrador puede agregar cualquier aplicación de la Tienda Windows a la directiva.

-   **Aplicaciones de escritorio de Windows**: el administrador puede agregar cualquier aplicación de escritorio tradicional de Windows a la directiva (por ejemplo, exe, dll, etc.).

## <a name="pre-requisites"></a>Requisitos previos

Debe configurar el proveedor de MAM antes de poder crear una directiva de protección de la aplicación de WIP.

-   Obtenga más información sobre [cómo configurar el proveedor de MAM con Intune](https://docs.microsoft.com/app-protection-policies-configure-windows-10.md).

Además, necesita lo siguiente:

-   Una licencia de [Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium).
-   [Windows Creators Update](https://blogs.windows.com/windowsexperience/2017/04/11/how-to-get-the-windows-10-creators-update/#o61bC2PdrHslHG5J.97)

> [!IMPORTANT]
> WIP no admite varias identidades, solo puede existir una identidad administrada al mismo tiempo.

## <a name="to-add-a-wip-policy"></a>Para agregar una directiva de WIP

Una vez configurado Intune en su organización, puede crear una directiva específica de WIP a través de [Azure Portal](https://docs.microsoft.com/intune-classic/deploy-use/azure-portal-for-microsoft-intune-mam-policies).

1.  Vaya al **panel de administración de aplicaciones móviles de Intune**, elija **Toda la configuración** y, a continuación, elija **Directiva de aplicaciones**.

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

## <a name="add-a-store-app-to-your-allowed-apps-list"></a>Adición de una aplicación de la Tienda a la lista de aplicaciones permitidas

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

## <a name="add-a-desktop-app-to-your-allowed-apps-list"></a>Adición de una aplicación de escritorio a la lista de aplicaciones permitidas

**Para agregar una aplicación de escritorio**

1.  En la hoja **Directiva de aplicaciones**, elija el nombre de la directiva y luego elija **Aplicaciones permitidas**. Se abre la hoja de **Aplicaciones permitidas**, que muestra todas las aplicaciones que ya están incluidas en la lista para esta directiva de protección de la aplicación.

2.  En la hoja **Aplicaciones permitidas**, elija **Agregar aplicaciones**.

3.  En la hoja **Agregar aplicaciones**, elija **Aplicaciones de escritorio** en la lista desplegable.

4.  Después de haber especificado la información en los campos, elija **Aceptar** para agregar la aplicación a la lista de **Aplicaciones permitidas**.

> [!NOTE]
> Para agregar varias **aplicaciones de escritorio** a la vez, puede hacer clic en el menú **(…)** al final de la fila de aplicaciones y luego seguir agregando más aplicaciones. Cuando haya terminado, elija **Aceptar**.

## <a name="windows-information-protection-wip-learning"></a>Aprendizaje de Windows Information Protection (WIP)

Después de agregar las aplicaciones que desea proteger con WIP, debe aplicar un modo de protección mediante **Aprendizaje de WIP**.

### <a name="before-you-begin"></a>Antes de comenzar

Aprendizaje de Windows Information Protection (WIP) es un informe que permite a los administradores supervisar sus aplicaciones desconocidas de WIP. Las aplicaciones desconocidas son las que no ha implementado el departamento de TI de su organización. El administrador puede exportar estas aplicaciones desde el informe y agregarlas a sus directivas de WIP para evitar la interrupción de productividad antes de exigir WIP en modo "Ocultar invalidaciones".

Se recomienda que empiece con **Silencioso** o **Permitir invalidaciones** al comprobar con un pequeño grupo que tiene las aplicaciones adecuadas en la lista de aplicaciones permitidas. Cuando haya terminado, puede cambiar a la directiva de aplicación final, **Ocultar invalidaciones**.

#### <a name="what-the-protection-modes-are"></a>¿Cuáles son los modos de protección?

- **Ocultar invalidaciones:**
    - WIP busca prácticas de uso compartido de datos inapropiadas y no permite al usuario completar la acción.
    - Esto puede incluir el uso compartido de información entre aplicaciones protegidas no corporativas y el uso compartido de datos corporativos entre otras personas y dispositivos no pertenecientes a su organización.
<br></br>

- **Ocultar invalidaciones:**
    - WIP busca el uso compartido de datos inapropiado, avisando a los usuarios si hacen algo que se considera potencialmente no seguro.
    - Sin embargo, este modo permite al usuario reemplazar la directiva y compartir los datos, registrando la acción en el registro de auditoría.
<br></br>
- **Silencioso:**
    - WIP se ejecuta en modo silencioso, registrando el uso compartido de datos inadecuado, sin bloquear nada que se hubiera solicitado en la interacción con el empleado en el modo Permitir invalidaciones.
    - Las acciones no permitidas, como las aplicaciones que intentan de manera inapropiada obtener acceso a un recurso de red o a datos protegidos por WIP, se siguen deteniendo.
<br></br>
- **Desactivado (no recomendado):**
    - WIP está desactivado y no ayuda a proteger o auditar los datos.
    - Una vez desactivado WIP, se realiza un intento de descifrar los archivos etiquetados con WIP en las unidades conectadas localmente. Tenga en cuenta que la información anterior de descifrado y directiva no se vuelve a aplicar automáticamente si vuelve a activar la protección de WIP.

### <a name="to-add-a-protection-mode"></a>Para agregar un modo de protección

1.  En la hoja **Directiva de aplicaciones**, elija el nombre de la directiva y luego haga clic en **Valores obligatorios** desde la hoja **Agregar directiva**.

    ![Captura de pantalla del modo de aprendizaje](./media/learning-mode-sc1.png)

1.  Elija **Guardar**.

### <a name="to-use-wip-learning"></a>Para utilizar el aprendizaje de WIP

1. Vaya al panel de Azure.

2. Elija **Más servicios** en el menú izquierdo y, luego, escriba **Intune** en el filtro del cuadro de texto.

3. Elija **Intune** y, cuando se abra el **panel de Intune**, seleccione **Mobile Apps**.

4. Elija **WIP Learning** (Aprendizaje de WIP) en la sección **Supervisar**. Verá las aplicaciones desconocidas etiquetadas por el aprendizaje de WIP.

> [!IMPORTANT]
> Una vez que tenga las aplicaciones que se muestran en el informe de registro del aprendizaje de WIP, puede trasladarlas a las directivas de protección de aplicaciones.

## <a name="to-deploy-your-wip-app-protection-policy"></a>Para implementar la directiva de protección de aplicaciones de WIP

> [!IMPORTANT]
> Esto se aplica a WIP con la administración de aplicaciones móviles (MAM) sin el escenario de inscripción.

Después de crear la directiva de protección de aplicaciones de WIP, debe implementarla en su organización mediante MAM.

1.  En la hoja **Directiva de aplicaciones**, seleccione la directiva de protección de aplicaciones recién creada, elija **Grupos de usuarios** y, a continuación, elija **Agregar grupo de usuarios**.

    Se abre una lista de grupos de usuarios, que consta de todos los grupos de seguridad de Azure Active Directory, en la hoja **Agregar grupo de usuarios**.

1.  Elija el grupo al que desea que se aplique la directiva y, a continuación, haga clic en **Seleccionar** para implementar la directiva.
