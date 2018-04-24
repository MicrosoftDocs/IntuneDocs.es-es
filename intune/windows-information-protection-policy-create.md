---
title: Creación e implementación de una directiva de protección de aplicaciones de Windows Information Protection (WIP)
titlesuffix: Microsoft Intune
description: Creación e implementación de una directiva de protección de aplicaciones de Windows Information Protection (WIP) con Microsoft Intune
keywords: ''
author: Erikre
ms.author: erikre
manager: doubeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4e3627bd-a9fd-49bc-b95e-9b7532f0ed55
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 821ce2c9992d32195b95e766f96bea7322ec2e7e
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="create-and-deploy-windows-information-protection-wip-app-protection-policy-with-intune"></a>Creación e implementación de una directiva de protección de aplicaciones de Windows Information Protection (WIP) con Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Puede usar directivas de protección de aplicaciones con aplicaciones de Windows 10 para proteger las aplicaciones sin inscripción en dispositivos.

## <a name="before-you-begin"></a>Antes de comenzar

Antes de agregar una directiva de trabajo en curso, debe tener claros algunos conceptos:

### <a name="list-of-allowed-and-exempt-apps"></a>Lista de aplicaciones permitidas y exentas

-   **Aplicaciones permitidas**: estas son las aplicaciones que deben cumplir esta directiva.

-   **Aplicaciones exentas**: estas aplicaciones están exentas del cumplimiento de esta directiva y pueden acceder a los datos corporativos sin restricciones.

### <a name="types-of-apps"></a>Tipos de aplicaciones

-   **Aplicaciones recomendadas**: lista rellenada previamente de aplicaciones (en su mayoría de Microsoft Office) que permite una importación sencilla en la directiva.
-   **Aplicaciones de la Tienda**: puede agregar cualquier aplicación de la Tienda Windows a la directiva.
-   **Aplicaciones de escritorio de Windows**: puede agregar cualquier aplicación de escritorio tradicional de Windows a la directiva (por ejemplo, .exe, .dll, etc.).

## <a name="prerequisites"></a>Requisitos previos

Debe configurar el proveedor de MAM para poder crear una directiva de protección de la aplicación de WIP. Obtenga más información sobre [cómo configurar el proveedor de MAM con Intune](app-protection-policies-configure-windows-10.md).

Además, necesita la siguiente licencia y actualización:

-   Licencia de [Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium)
-   [Windows Creators Update](https://blogs.windows.com/windowsexperience/2017/04/11/how-to-get-the-windows-10-creators-update/#o61bC2PdrHslHG5J.97)

> [!IMPORTANT]
> WIP no admite varias identidades, solo puede existir una identidad administrada al mismo tiempo.

## <a name="to-add-a-wip-app-protection-policy"></a>Para agregar una directiva de protección de aplicaciones de WIP

Una vez configurado Intune en su organización, puede crear una directiva específica de WIP.

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Elija **Todos los servicios** > **Intune**.
3. Seleccione **Aplicaciones móviles** en la hoja **Microsoft Intune**.
4. Seleccione las **Directivas de protección de aplicaciones** en la hoja **Aplicaciones móviles**.
5. Haga clic en **Agregar directiva** para que se muestre la hoja **Agregar una directiva**.
6. Agregue los siguientes valores:
    - **Nombre:** escriba un nombre (necesario) para la nueva directiva.
    - **Descripción** (opcional): escriba una descripción.
    - **Plataforma:** elija **Windows 10** como plataforma admitida para la directiva de protección de aplicaciones.
    - **Estado de inscripción:** elija **Sin inscripción** como estado de inscripción para la directiva.
7.  Elija **Crear**. La directiva se crea y aparece en la tabla de la hoja **Directivas de protección de aplicaciones**.

## <a name="to-add-recommended-apps-to-your-allowed-apps-list"></a>Para agregar aplicaciones recomendadas a la lista de aplicaciones permitidas

1. Seleccione **Aplicaciones móviles** en la hoja **Microsoft Intune**.
2. Seleccione las **Directivas de protección de aplicaciones** en la hoja **Aplicaciones móviles**.
3. En la hoja **Directivas de protección de aplicaciones**, seleccione la directiva que quiera modificar. Se muestra la hoja **Intune App Protection**.
4. Elija **Aplicaciones protegidas** en la hoja **Intune App Protection**. Se abre la hoja **Aplicaciones protegidas**, que muestra todas las aplicaciones que ya están incluidas en la lista para esta directiva de protección de la aplicación.
5. Seleccione **Agregar aplicaciones**. La información **Agregar aplicaciones** muestra una lista filtrada de aplicaciones. La lista de la parte superior de la hoja le permite cambiar el filtro de la lista.
6. Seleccione cada una de las aplicaciones a las que quiera dar permiso para acceder a sus datos corporativos.
7. Haga clic en **Aceptar**. La hoja **Aplicaciones protegidas** se actualiza y muestra todas las aplicaciones seleccionadas.
8. Haga clic en **Guardar**.

## <a name="add-a-store-app-to-your-allowed-apps-list"></a>Agregar una aplicación de la Tienda a la lista de aplicaciones permitidas

**Para agregar una aplicación de la Tienda**
1. Seleccione **Aplicaciones móviles** en la hoja **Microsoft Intune**.
2. Seleccione las **Directivas de protección de aplicaciones** en la hoja **Aplicaciones móviles**.
3. En la hoja **Directivas de protección de aplicaciones**, seleccione la directiva que quiera modificar. Se muestra la hoja **Intune App Protection**.
4. Elija **Aplicaciones protegidas** en la hoja **Intune App Protection**. Se abre la hoja **Aplicaciones protegidas**, que muestra todas las aplicaciones que ya están incluidas en la lista para esta directiva de protección de la aplicación.
5. Seleccione **Agregar aplicaciones**. La información **Agregar aplicaciones** muestra una lista filtrada de aplicaciones. La lista de la parte superior de la hoja le permite cambiar el filtro de la lista.
6. En la lista, seleccione **Aplicaciones de la Tienda**.
7. Especifique los valores de **Nombre**, **Editor**, **Nombre de producto** y **Acción**. Asegúrese de establecer el valor **Acción** en **Permitir** para que la aplicación tenga acceso a los datos corporativos.
9. Haga clic en **Aceptar**. La hoja **Aplicaciones protegidas** se actualiza y muestra todas las aplicaciones seleccionadas.
10. Haga clic en **Guardar**.

## <a name="add-a-desktop-app-to-your-allowed-apps-list"></a>Agregar una aplicación de escritorio a la lista de aplicaciones permitidas

**Para agregar una aplicación de escritorio**
1. Seleccione **Aplicaciones móviles** en la hoja **Microsoft Intune**.
2. Seleccione las **Directivas de protección de aplicaciones** en la hoja **Aplicaciones móviles**.
3. En la hoja **Directivas de protección de aplicaciones**, seleccione la directiva que quiera modificar. Se muestra la hoja **Intune App Protection**.
4. Elija **Aplicaciones protegidas** en la hoja **Intune App Protection**. Se abre la hoja **Aplicaciones protegidas**, que muestra todas las aplicaciones que ya están incluidas en la lista para esta directiva de protección de la aplicación.
5. Seleccione **Agregar aplicaciones**. La información **Agregar aplicaciones** muestra una lista filtrada de aplicaciones. La lista de la parte superior de la hoja le permite cambiar el filtro de la lista.
6. En la lista, seleccione **Aplicaciones de escritorio**.
7. Introduzca los valores de **Nombre**, **Editor**, **Nombre de producto**, **Archivo**, **Versión mínima**, **Versión máxima** y **Acción**. Asegúrese de establecer el valor **Acción** en **Permitir** para que la aplicación tenga acceso a los datos corporativos.
9. Haga clic en **Aceptar**. La hoja **Aplicaciones protegidas** se actualiza y muestra todas las aplicaciones seleccionadas.
10. Haga clic en **Guardar**.

## <a name="wip-learning"></a>Aprendizaje de WIP
Después de agregar las aplicaciones que desea proteger con WIP, debe aplicar un modo de protección mediante **Aprendizaje de WIP**.

### <a name="before-you-begin"></a>Antes de comenzar

Aprendizaje de WIP es un informe que permite supervisar las aplicaciones que tengan WIP habilitado y las que sean desconocidas para WIP. Las aplicaciones desconocidas son las que no ha implementado el departamento de TI de su organización. Puede exportar estas aplicaciones desde el informe y agregarlas a sus directivas de WIP para evitar la interrupción de productividad antes de exigir WIP en modo "Bloquear".

<!-- 1631908 -->
Además de ver información sobre las aplicaciones habilitadas para WIP, puede ver un resumen de los dispositivos que han compartido datos de trabajo con sitios web. Con esta información, puede determinar qué sitios web se deben agregar a las directivas WIP de grupo y de usuario. En el resumen se muestra que las aplicaciones habilitadas para WIP han accedido a las direcciones URL del sitio web.

Al trabajar con aplicaciones que tengan WIP habilitado o que sean desconocidas para WIP, se recomienda que empiece con **Silencioso** o **Permitir invalidaciones** al realizar comprobaciones con un pequeño grupo que tenga las aplicaciones adecuadas en la lista de aplicaciones permitidas. Cuando haya terminado, puede cambiar a la directiva de aplicación final, **Bloquear**.

### <a name="what-are-the-protection-modes"></a>¿Cuáles son los modos de protección?

#### <a name="block"></a>Bloquear
WIP busca prácticas de uso compartido de datos inapropiadas y no permite al usuario completar la acción. Esto puede incluir el uso compartido de información entre aplicaciones protegidas no corporativas y el uso compartido de datos corporativos entre otras personas y dispositivos no pertenecientes a su organización.

#### <a name="allow-overrides"></a>Permitir invalidaciones
WIP busca el uso compartido de datos inadecuado, avisando a los usuarios si hacen algo que se considera potencialmente no seguro. Sin embargo, este modo permite al usuario reemplazar la directiva y compartir los datos, registrando la acción en el registro de auditoría.

#### <a name="silent"></a>Silencioso
WIP se ejecuta en modo silencioso, ya que registra el uso compartido de datos inadecuado sin bloquear nada que se hubiera solicitado en la interacción con el empleado en el modo Permitir invalidaciones. Las acciones no permitidas, como las aplicaciones que intentan de manera inapropiada obtener acceso a un recurso de red o a datos protegidos por WIP, se siguen deteniendo.

#### <a name="off-not-recommended"></a>Desactivado (no recomendado)
WIP está desactivado y no ayuda a proteger o auditar los datos.

Una vez desactivado WIP, se realiza un intento de descifrar los archivos etiquetados con WIP en las unidades conectadas localmente. Tenga en cuenta que la información anterior de descifrado y directiva no se vuelve a aplicar automáticamente si vuelve a activar la protección de WIP.

### <a name="add-a-protection-mode"></a>Agregar un modo de protección

1.  En la hoja **Directiva de aplicaciones**, seleccione el nombre de la directiva y elija **Valores obligatorios**.

    ![Captura de pantalla del modo de aprendizaje](./media/learning-mode-sc1.png)

1.  Seleccione un valor y elija **Guardar**.

### <a name="use-wip-learning"></a>Uso del aprendizaje de WIP

1. Abra [Azure Portal](https://portal.azure.com). Elija **Todos los servicios**. Escriba **Intune** en el filtro del cuadro de texto.

3. Elija **Intune** > **Aplicaciones móviles**.

4. Elija **Estado de protección de la aplicación** > **Informes** > **Aprendizaje de Windows Information Protection**.  

    Una vez que tenga las aplicaciones que se muestran en el informe de registro del aprendizaje de WIP, puede agregarlas a las directivas de protección de aplicaciones.

## <a name="allow-windows-search-indexer-to-search-encrypted-items"></a>Permitir que el indizador de Windows Search busque elementos cifrados
Permite o deniega la indexación de elementos. Este modificador es para el indizador de Windows Search, que controla si indexa los elementos que están cifrados, como los archivos protegidos de Windows Information Protection (WIP).

Esta opción de directiva de protección de aplicaciones está en la **Configuración avanzada** de la directiva de Windows Information Protection. La directiva de protección de aplicaciones debe establecerse en la plataforma *Windows 10* y la directiva de aplicación **Estado de inscripción** debe establecerse en **Con inscripción**.

Cuando la directiva está habilitada, los elementos protegidos por WIP se indexan y los metadatos sobre ellos se almacenan en una ubicación sin cifrar. Los metadatos incluyen elementos tales como la ruta de acceso de archivo y la fecha de modificación.

Cuando la directiva está deshabilitada, los elementos protegidos por WIP no se indexan y no se muestran en los resultados de Cortana o del explorador de archivos. También puede haber un impacto en el rendimiento de fotografías y aplicaciones de Groove si hay muchos archivos multimedia protegidos por WIP en el dispositivo.

## <a name="add-encrypted-file-extensions"></a>Agregar extensiones de archivo cifrado

Además de establecer la opción **Permitir que el indizador de Windows Search busque elementos cifrados**, puede especificar una lista de extensiones de archivo. Los archivos con estas extensiones se cifran cuando se copian desde un recurso compartido de bloque de mensajes del servidor (SMB) dentro de los límites corporativos, tal y como se define en la lista de ubicaciones de red. Cuando no se especifica esta directiva, se aplica el comportamiento de cifrado automático existente. Cuando se configura esta directiva, se cifrarán únicamente los archivos con las extensiones de la lista.

## <a name="deploy-your-wip-app-protection-policy"></a>Implementación de la directiva de protección de aplicaciones de WIP

> [!IMPORTANT]
> Esta información corresponde a WIP sin la inscripción de dispositivos.

<!---not sure why you need the Important note. Isn't this what the topic is about? app protection w/o enrollment?--->

Después de crear la directiva de protección de aplicaciones de WIP, debe implementarla en su organización mediante MAM.

1.  En la hoja **Directiva de aplicaciones**, seleccione la directiva de protección de aplicaciones recién creada y elija **Grupos de usuarios** > **Agregar grupo de usuarios**.

    Se abre una lista de grupos de usuarios, que consta de todos los grupos de seguridad de Azure Active Directory, en la hoja **Agregar grupo de usuarios**.

2.  Seleccione el grupo al que quiere que se aplique la directiva y, después, elija **Seleccionar** para implementar la directiva.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre Windows Information Protection, consulte [Protect your enterprise data using Windows Information Protection (WIP)](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) [Protección de los datos de su empresa mediante Windows Information Protection (WIP)].
