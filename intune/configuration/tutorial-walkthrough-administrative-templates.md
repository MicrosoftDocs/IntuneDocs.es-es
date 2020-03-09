---
title: 'Tutorial: Creación de plantillas administrativas en Microsoft Intune (Azure) | Microsoft Docs'
description: En este tutorial se usa Microsoft Intune para configurar plantillas de ADMX de Office, Windows y Microsoft Edge en dispositivos con Windows 10 y otros más recientes.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: tutorial
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
ms.openlocfilehash: a96f291203e1513ab89196b26a7802856f90e048
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77688095"
---
# <a name="tutorial-use-the-cloud-to-configure-group-policy-on-windows-10-devices-with-admx-templates-and-microsoft-intune"></a>Tutorial: Uso de la nube para configurar directivas de grupo en dispositivos con Windows 10 con plantillas de ADMX y Microsoft Intune

> [!NOTE]
> Este tutorial se ha creado como un taller técnico para Microsoft Ignite. Tiene más requisitos previos que los tutoriales habituales, ya que en él se comparan el uso y la configuración de directivas de ADMX en Intune y de forma local.

Las plantillas administrativas de directiva de grupo, también conocidas como plantillas de ADMX, incluyen opciones que se pueden configurar en dispositivos con Windows 10, incluidos los equipos de escritorio. La configuración de la plantilla de ADMX está disponible mediante diferentes servicios. Los proveedores de administración de dispositivos móviles (MDM), incluido Microsoft Intune, usan esa configuración. Por ejemplo, puede activar Ideas de diseño en PowerPoint, establecer una página principal en Microsoft Edge, bloquear controles ActiveX en Internet Explorer, etc.

Las plantillas de ADMX están disponibles para los siguientes servicios:

- **Microsoft Edge**: descárguelas de [Archivo de directiva de Microsoft Edge](https://www.microsoftedgeinsider.com/en-us/enterprise).
- **Office**: descárguelas de [Office 365 ProPlus, Office 2019 y Office 2016](https://www.microsoft.com/download/details.aspx?id=49030).
- **Windows**: integradas en el sistema operativo Windows 10.

Para obtener más información sobre las directivas de ADMX, vea [Descripción de las directivas respaldadas por ADMX](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies).

En Microsoft Intune, estas plantillas están integradas en el servicio Intune y están disponibles como perfiles de **plantillas administrativas**. En este perfil, configure los valores que quiere incluir y, luego, "asigne" este perfil a los dispositivos.

En este tutorial, aprenderá a:

> [!div class="checklist"]
> * Conocer el [Centro de administración de puntos de conexión](https://go.microsoft.com/fwlink/?linkid=2109431).
> * Crear grupos de usuarios y de dispositivos.
> * Comparar la configuración de Intune con la configuración de ADMX local.
> * Crear distintas plantillas administrativas y configurar los valores para los distintos grupos.

Al final de este laboratorio dispondrá de los conocimientos necesarios para empezar a usar Intune y Microsoft 365 para administrar a los usuarios e implementar plantillas administrativas.

Esta característica se aplica a:

- Windows 10, versión 1703, y más recientes

## <a name="prerequisites"></a>Requisitos previos

- Una suscripción de Microsoft 365 E3 o E5, que incluye Intune y Azure Active Directory (AD) Premium. Si no tiene una suscripción E3 o E5, [pruébela de forma gratuita](https://docs.microsoft.com/office365/admin/try-or-buy-microsoft-365?view=o365-worldwide).

  Para obtener más información sobre lo que se obtiene con las distintas licencias de Microsoft 365, vea [Transforma tu empresa con Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans).

- Microsoft Intune configurado como **entidad de MDM de Intune**. Para obtener más información, vea [Establecer la entidad de administración de dispositivos móviles](../fundamentals/mdm-authority-set.md).

  > [!div class="mx-imgBorder"]
  > ![Establecimiento de la entidad de MDM en Microsoft Intune en el estado de inquilino](./media/tutorial-walkthrough-administrative-templates/tenant-status.png)

- En un controlador de dominio (DC) local de Active Directory:

  1. Copie las siguientes plantillas de Office y Microsoft Edge en el [almacén central (carpeta SYSVOL)](https://support.microsoft.com/help/3087759/how-to-create-and-manage-the-central-store-for-group-policy-administra):

      - [Plantillas administrativas de Office](https://www.microsoft.com/download/details.aspx?id=49030)
      - [Plantillas administrativas de Microsoft Edge > Archivo de directiva](https://www.microsoftedgeinsider.com/en-us/enterprise)

  2. Cree una directiva de grupo para insertar estas plantillas en un equipo de administrador de Windows 10 Enterprise del mismo dominio que el controlador de dominio. En este tutorial:

      - La directiva de grupo creada con estas plantillas se denomina **OfficeandEdge**. Este nombre aparece en las imágenes.
      - El equipo de administrador de Windows 10 Enterprise usado se denomina **equipo de administración**.

      En algunas organizaciones, un administrador de dominio tiene dos cuentas: una cuenta de trabajo de dominio típica y otra cuenta de administrador de dominio que solo se usa para tareas de administración de dominios, como la directiva de grupo.

      El propósito de este **equipo de administración** es que los administradores inicien sesión con su cuenta de administrador de dominio y accedan a herramientas diseñadas para administrar la directiva de grupo.

- En este **equipo de administración**:

  - Inicie sesión con una cuenta de administrador de dominio.

  - Instale **RSAT: Herramientas de administración de directivas de grupo**:

    1. Abra la aplicación **Configuración** > **Aplicaciones** > **Características opcionales** > **Agregar característica**.
    2. Seleccione **RSAT: Herramientas de administración de directivas de grupo** > **Instalar**.

        Espere mientras Windows instala la característica. Al completar la instalación, esta se muestra en la aplicación **Herramientas administrativas de Windows**.

        > [!div class="mx-imgBorder"]
        > ![Aplicaciones de Herramientas administrativas de Windows, incluida la aplicación Administración de directivas de grupo](./media/tutorial-walkthrough-administrative-templates/windows-administrative-tools-app.png)

  - Asegúrese de tener acceso a Internet y derechos de administrador en la suscripción de Microsoft 365, lo que incluye el Centro de administración de puntos de conexión.

## <a name="open-the-endpoint-manager-admin-center"></a>Apertura del Centro de administración de puntos de conexión

1. Abra un explorador web Chromium, como Microsoft Edge, versión 77 y posteriores.
2. Vaya al [Centro de administración de puntos de conexión](https://go.microsoft.com/fwlink/?linkid=2109431) (https://devicemanagement.microsoft.com). Inicie sesión con la cuenta siguiente:

    **Usuario**: escriba la cuenta de administrador de la suscripción de inquilino de Microsoft 365.  
    **Contraseña**: escriba su contraseña.

Este centro de administración se centra en la administración de dispositivos e incluye servicios de Azure como Azure AD e Intune. Es posible que no vea la marca **Azure Active Directory** ni **Intune**, pero las está usando.

También puede abrir el Centro de administración de puntos de conexión desde el [Centro de administración de Microsoft 365](https://admin.microsoft.com):

1. Vaya a [https://admin.microsoft.com](https://admin.microsoft.com).
2. Inicie sesión con la cuenta de administrador de la suscripción de inquilino de Microsoft 365.
3. En **Centros de administración**, seleccione **Todos los centros de administración** > **Administración de puntos de conexión**. Se abre el Centro de administración de puntos de conexión.

    > [!div class="mx-imgBorder"]
    > ![Vista de todos los centros de administración en el Centro de administración de Microsoft 365](./media/tutorial-walkthrough-administrative-templates/microsoft365-admin-centers.png)

## <a name="create-groups-and-add-users"></a>Creación de grupos e incorporación de usuarios

Las directivas locales se aplican en el orden: local, sitio, dominio y unidad organizativa (UO). En esta jerarquía, las directivas de UO sobrescriben a las directivas locales, las directivas de dominio sobrescriben a las directivas de sitio, y así sucesivamente.

En Intune, las directivas se aplican a los usuarios y a los grupos que se crean. No existe ninguna jerarquía. Si dos directivas actualizan el mismo valor, este se muestra como un conflicto. Si hay dos directivas de cumplimiento en conflicto, se aplica la más restrictiva. Si hay dos perfiles de configuración en conflicto, no se aplica el valor. Para obtener más información, vea [Preguntas comunes, problemas y su solución con perfiles y directivas de dispositivos](device-profile-troubleshoot.md#if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied).

En los siguientes pasos se crean grupos de seguridad y se agregan usuarios a los grupos. Es posible agregar un usuario a varios grupos. Por ejemplo, es normal que un usuario tenga varios dispositivos, como un Surface Pro para el trabajo y un dispositivo móvil Android para uso personal. Además, es normal que una persona acceda a los recursos de la organización desde estos distintos dispositivos.

1. En el Centro de administración de puntos de conexión, seleccione **Grupos** > **Nuevo grupo**.

2. Escriba los valores siguientes:

    - **Tipo de grupo**: seleccione **Seguridad**.
    - **Nombre de grupo**: escriba **Todos los dispositivos de Windows 10 Student**.
    - **Tipo de pertenencia**: seleccione **Asignado**.

3. Seleccione **Miembros** y agregue algunos dispositivos.

    La adición de dispositivos es opcional. El objetivo es practicar la creación de grupos y saber cómo se agregan dispositivos. Si usa este tutorial en un entorno de producción, sea consciente de lo que está haciendo.

4. **Seleccione** > **Crear** para guardar los cambios.

    ¿No ve el grupo? Seleccione **Actualizar**.

5. Seleccione **Nuevo grupo** y escriba los siguientes valores:

    - **Tipo de grupo**: seleccione **Seguridad**.
    - **Nombre de grupo**: escriba **Todos los dispositivos Windows**.
    - **Tipo de pertenencia**: Seleccione **Dispositivo dinámico**.
    - **Miembros del dispositivo dinámico**: configure la consulta:

        - **Propiedad**: seleccione **deviceOSType**.
        - **Operador**: seleccione **Igual a**.
        - **Valor**: escriba **Windows**.

        1. Seleccione **Agregar expresión**. La expresión se muestra en la **sintaxis de la regla**:

            > [!div class="mx-imgBorder"]
            > ![Creación de una consulta dinámica e incorporación de una expresión en una plantilla administrativa de Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/dynamic-group-query.png)

            Si los usuarios o los dispositivos cumplen los criterios especificados, se agregan automáticamente a los grupos dinámicos. En este ejemplo, los dispositivos se agregan automáticamente a este grupo si el sistema operativo es Windows. Si usa este tutorial en un entorno de producción, tenga cuidado. El objetivo es practicar la creación de grupos dinámicos.

        2. **Guardar** > **Crear** para guardar los cambios.

6. Cree el grupo **Todos los profesores** con la siguiente configuración:

    - **Tipo de grupo**: seleccione **Seguridad**.
    - **Nombre de grupo**: escriba **Todos los profesores**.
    - **Tipo de pertenencia**: seleccione **Usuario dinámico**.
    - **Usuarios miembros dinámicos**: configure la consulta:

      - **Propiedad**: seleccione **departamento**.
      - **Operador**: seleccione **Igual a**.
      - **Valor**: escriba **Profesores**.

        1. Seleccione **Agregar expresión**. La expresión se muestra en la **sintaxis de la regla**.

            Si los usuarios o los dispositivos cumplen los criterios especificados, se agregan automáticamente a los grupos dinámicos. En este ejemplo, los usuarios se agregan automáticamente a este grupo si el departamento es Profesores. Puede especificar el departamento y otras propiedades al agregar usuarios a la organización. Si usa este tutorial en un entorno de producción, tenga cuidado. El objetivo es practicar la creación de grupos dinámicos.

        2. **Guardar** > **Crear** para guardar los cambios.

### <a name="talking-points"></a>Temas de discusión

- Los grupos dinámicos son una característica de Azure AD Premium. Si no tiene Azure AD Premium, solo tiene licencia para crear grupos asignados. Para obtener más información sobre los grupos dinámicos, vea:

  - [Pertenencia a grupos dinámicos en Azure Active Directory (parte 1)](https://blogs.technet.microsoft.com/pauljones/2017/08/28/dynamic-group-membership-in-azure-active-directory-part-1/)
  - [Pertenencia a grupos dinámicos en Azure Active Directory (parte 2)](https://blogs.technet.microsoft.com/pauljones/2017/08/29/dynamic-group-membership-in-azure-active-directory-part-2/)

- Azure AD Premium incluye otros servicios que se suelen usar al administrar aplicaciones y dispositivos, como la [autenticación multifactor (MFA)](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks) y el [acceso condicional](https://docs.microsoft.com/azure/active-directory/conditional-access/overview).

- Muchos administradores se preguntan cuándo usar grupos de usuarios y cuándo grupos de dispositivos. Para obtener instrucciones, vea [Grupos de usuarios y grupos de dispositivos](device-profile-assign.md#user-groups-vs-device-groups).

- Recuerde que un usuario puede pertenecer a varios grupos. Tenga en cuenta algunos de los otros grupos de dispositivos y usuarios dinámicos que puede crear, por ejemplo:

  - Todos los estudiantes
  - Todos los dispositivos Android
  - Todos los dispositivos iOS/iPadOS
  - Marketing
  - Recursos humanos
  - Todos los empleados de Charlotte
  - Todos los empleados de Redmond
  - Administradores de TI de la costa oeste
  - Administradores de TI de la costa este

Los usuarios y los grupos creados también pueden verse en el [Centro de administración de Microsoft 365](https://admin.microsoft.com), Azure AD en Azure Portal y [Microsoft Intune en Azure Portal](https://go.microsoft.com/fwlink/?linkid=2090973). Puede crear y administrar grupos en todas estas áreas de la suscripción de inquilino. **Si su objetivo es la administración de dispositivos, use el [Centro de administración de puntos de conexión](https://go.microsoft.com/fwlink/?linkid=2109431)** .

### <a name="review-group-membership"></a>Revisión de la pertenencia a grupos

1. En el Centro de administración de puntos de conexión, seleccione **Usuarios** y el nombre de cualquier usuario existente.

    > [!div class="mx-imgBorder"]
    > ![Selección de Usuarios en el Centro de administración de puntos de conexión](./media/tutorial-walkthrough-administrative-templates/select-users-endpoint-manager-admin-center.png)

2. Revise parte de la información que puede agregar o cambiar. Por ejemplo, examine las propiedades que puede configurar, como Puesto, Departamento, Ciudad, Ubicación, etc. Puede usar estas propiedades en las consultas dinámicas cuando cree grupos dinámicos.
3. Seleccione **Grupos** para ver la pertenencia de este usuario. También puede quitar al usuario de un grupo.
4. Seleccione algunas de las otras opciones para ver más información y lo que puede hacer. Por ejemplo, examine la licencia asignada, los dispositivos del usuario, etc.

### <a name="what-did-i-just-do"></a>Síntesis

En el Centro de administración de puntos de conexión, ha creado nuevos grupos de seguridad y ha agregado usuarios y dispositivos existentes a estos grupos. En los pasos siguientes de este tutorial se van a usar estos grupos.

## <a name="create-a-template-in-intune"></a>Creación de una plantilla en Intune

En esta sección se crea una plantilla administrativa en Intune, se examinan algunas opciones de **Administración de directivas de grupo** y se compara la misma opción en Intune. El objetivo es mostrar una opción en la directiva de grupo y la misma en Intune.

1. En el Centro de administración de puntos de conexión, seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.
2. Escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre descriptivo para el nuevo perfil. Asígnele un nombre a los perfiles para que pueda identificarlos de manera sencilla más adelante. Por ejemplo, escriba **Plantilla de administración: dispositivos de Windows 10 Student**.
    - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
    - **Plataforma**: seleccione **Windows 10 y versiones posteriores**.
    - **Tipo de perfil**: seleccione **Plantillas administrativas**.

3. Seleccione **Crear**. En la lista desplegable **Seleccionar una categoría**, seleccione **Todos los productos**. Se muestran todas las opciones. En estas opciones, observe las siguientes propiedades:

    - La **Ruta de acceso** a la directiva es la misma que Administración de directivas de grupo o GPEdit.
    - El valor se aplica a usuarios o dispositivos.

### <a name="open-group-policy-management"></a>Apertura de Administración de directivas de grupo

En esta sección se muestra una directiva en Intune y su directiva correspondiente en el Editor de administración de directivas de grupo.

#### <a name="compare-a-device-policy"></a>Comparación de una directiva de dispositivo

1. En el **equipo de administración**, abra la aplicación **Administración de directivas de grupo**.

    Esta aplicación se instala con **RSAT: Herramientas de administración de directivas de grupo**, que es una característica opcional que se instala en Windows. En [Requisitos previos](#prerequisites) (en este artículo) se enumeran los pasos necesarios para instalarla.

2. Expanda **Dominios** > seleccione el dominio. Por ejemplo, seleccione **contoso.net**.
3. Haga clic con el botón derecho en la directiva **OfficeandEdge** > **Editar**. Se abre la aplicación Editor de administración de directivas de grupo.

    > [!div class="mx-imgBorder"]
    > ![Clic con el botón derecho en la directiva de grupo de ADMX OfficeandEdge y selección de Editar](./media/tutorial-walkthrough-administrative-templates/open-group-policy-management.png)

    **OfficeandEdge** es una directiva de grupo que incluye las plantillas de ADMX de Office y Microsoft Edge. Esta directiva se describe en [Requisitos previos](#prerequisites) (en este artículo).

4. Expanda **Configuración del equipo** > **Directivas** > **Plantillas administrativas** > **Panel de control** > **Personalización**. Observe las opciones disponibles.

    > [!div class="mx-imgBorder"]
    > ![Expansión de Configuración del equipo en el Editor de administración de directivas de grupo y desplazamiento a Personalización](./media/tutorial-walkthrough-administrative-templates/open-group-policy-management-editor-admx-policy.png)

    Haga doble clic en **Evitar la activación de la cámara de la pantalla de bloqueo** y vea las opciones disponibles:

    > [!div class="mx-imgBorder"]
    > ![Vista de las opciones del valor Configuración del equipo en la directiva de grupo](./media/tutorial-walkthrough-administrative-templates/prevent-enabling-lock-screen-camera-admx-policy.png)

5. En el centro de administración de dispositivos, vaya a la plantilla **Plantilla de administración: dispositivos de Windows 10 Student**.
6. Seleccione **Todos los productos** en la lista desplegable y busque **personalización**:

    > [!div class="mx-imgBorder"]
    > ![Búsqueda de personalización en la plantilla administrativa en Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/search-personalization-administrative-template.png)

    Observe las opciones disponibles.

    El tipo de valor es **Dispositivo** y la ruta de acceso es **\Panel de control\Personalización**. Esta ruta de acceso es similar a la que acaba de observar en el Editor de administración de directivas de grupo. Si abre el valor, ve las mismas opciones **Sin configurar**, **Habilitado** y **Deshabilitado** que se ven en el Editor de administración de directivas de grupo.

#### <a name="compare-a-user-policy"></a>Comparación de una directiva de usuario

1. En la plantilla de administración, busque **exploración de InPrivate**. Tenga en cuenta la ruta de acceso y que la opción se aplica a usuarios y dispositivos.

2. En el **Editor de administración de directivas de grupo**, busque la opción de usuario y dispositivo coincidente:

    - Dispositivo: expanda **Configuración del equipo** > **Directivas** > **Plantillas administrativas** > **Componentes de Windows** > **Internet Explorer** > **Privacidad** > **Desactivar la exploración de InPrivate**.
    - Usuario: expanda **Configuración del usuario** > **Directivas** > **Plantillas administrativas** > **Componentes de Windows** > **Internet Explorer** > **Privacidad** > **Desactivar la exploración de InPrivate**.

    > [!div class="mx-imgBorder"]
    > ![Desactivación de la exploración de InPrivate en Internet Explorer mediante la plantilla de ADMX](./media/tutorial-walkthrough-administrative-templates/group-policy-turn-off-inprivate-browsing.png)

> [!TIP]
> Para ver las directivas integradas de Windows, también puede usar GPEdit (aplicación **Editar directiva de grupo**).

#### <a name="compare-an-edge-policy"></a>Comparación de una directiva de Edge

1. En el centro de administración de dispositivos, vaya a la plantilla **Plantilla de administración: dispositivos de Windows 10 Student**.
2. Seleccione **Edge, versión 77 y posteriores** en la lista desplegable.
3. Busque **inicio**. Observe las opciones disponibles.
4. En el Editor de administración de directivas de grupo, busque estas opciones:

    - Dispositivo: expanda **Configuración del equipo** > **Directivas** > **Plantillas administrativas** > **Microsoft Edge** > **Inicio, página principal y nueva página de pestañas**.
    - Usuario: expanda **Configuración del usuario** > **Directivas** > **Plantillas administrativas** > **Microsoft Edge** > **Inicio, página principal y nueva página de pestañas**.

### <a name="what-did-i-just-do"></a>Síntesis

Ha creado una plantilla administrativa en Intune. En esta plantilla se han visto algunos valores de ADMX y se han examinado los mismos valores de ADMX en Administración de directivas de grupo.

## <a name="add-settings-to-the-students-admin-template"></a>Incorporación de valores a la plantilla de administración de alumnos

En esta plantilla se configuran algunos valores de Internet Explorer para bloquear dispositivos compartidos con varios alumnos.

1. En la **Plantilla de administración: dispositivos de Windows 10 Student**, busque **Desactivar la exploración de InPrivate** y seleccione la directiva de dispositivo:

    > [!div class="mx-imgBorder"]
    > ![Desactivación de la directiva de dispositivo de exploración de InPrivate en la plantilla administrativa en Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/turn-off-inprivate-browsing-administrative-template.png)

2. En esta ventana, observe la descripción y los valores que se pueden establecer. Estas opciones son similares a lo que se ve en la directiva de grupo.
3. Seleccione **Habilitado** > **Aceptar** para guardar los cambios.
4. Además, configure las siguientes opciones de Internet Explorer. Asegúrese de seleccionar **Aceptar** para guardar los cambios.

    - **Permitir arrastrar y colocar o copiar y pegar archivos**
      - **Tipo**: Dispositivo
      - **Ruta de acceso**: \Componentes de Windows\Internet Explorer\Panel de control de Internet\Página Seguridad\Zona Internet
      - **Valor**: Deshabilitado

    - **Impedir omitir errores de certificado**
      - **Tipo**: Dispositivo
      - **Ruta de acceso**: \Componentes de Windows\Internet Explorer\Panel de control de Internet
      - **Valor**: Habilitado

    - **Deshabilitar el cambio de configuración de la página principal**
      - **Tipo**: Usuario
      - **Ruta de acceso**: \Componentes de Windows\Internet Explorer
      - **Valor**: Habilitado
      - **Página principal**: escriba una dirección URL, como `contoso.com`.

5. Borre el filtro de búsqueda. Observe que los valores que ha configurado se muestran en la parte superior:

    > [!div class="mx-imgBorder"]
    > ![Valores configurados en la parte superior de Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/configured-settings-administrative-template.png)

### <a name="assign-your-template"></a>Asignación de la plantilla

1. En la plantilla, seleccione **Asignaciones**. Es posible que tenga que cerrar la plantilla y, luego, seleccionarla en la lista **Dispositivos: Perfiles de configuración**:

    > [!div class="mx-imgBorder"]
    > ![Selección del perfil de plantilla administrativa en la lista Perfiles de configuración del dispositivo en Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/filter-administrative-template-device-configuration-profiles-list.png)

2. Seleccione **Seleccionar grupos para incluir**. Aparece una lista de usuarios y grupos existentes.
3. Seleccione el grupo **Todos los dispositivos de Windows 10 Student** creado anteriormente y **Seleccionar**.

    Si usa este tutorial en un entorno de producción, plantéese agregar grupos que estén vacíos. El objetivo es practicar la asignación de la plantilla.

4. Guarde los cambios mediante **Guardar**.

Al guardar el perfil, este se aplica a los dispositivos en cuanto se registran en Intune. Si los dispositivos están conectados a Internet, puede suceder de inmediato. Vea [¿Cuánto tiempo tardan los dispositivos en obtener una directiva, un perfil o una aplicación después de que se hayan asignado?](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) para obtener más información sobre los tiempos de actualización de directivas.

Al asignar directivas y perfiles estrictos o restrictivos, no se bloquee. Plantéese la posibilidad de crear un grupo que esté excluido de las directivas y los perfiles. La idea es tener acceso para solucionar problemas. Supervise este grupo para confirmar que se está usando según lo previsto.

### <a name="what-did-i-just-do"></a>Síntesis

En el centro de administración de puntos de conexión, ha creado un perfil de configuración de dispositivo de plantilla administrativa y ha asignado este perfil a un grupo creado.

## <a name="create-a-onedrive-template"></a>Creación de una plantilla de OneDrive

En esta sección se crea una plantilla de administración de OneDrive en Intune para controlar algunos valores. Se han elegido estos valores concretos porque las organizaciones los usan habitualmente.

1. Cree otro perfil (**Dispositivos** > **Perfiles de configuración** > **Crear perfil**).

2. Escriba las propiedades siguientes:

    - **Nombre**: escriba **Plantilla de administración: directivas de OneDrive que se aplican a todos los usuarios de Windows 10**.
    - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
    - **Plataforma**: seleccione **Windows 10 y versiones posteriores**.
    - **Tipo de perfil**: seleccione **Plantillas administrativas**.

3. Seleccione **Crear**.
4. Seleccione **Office** en la lista desplegable.
5. **Habilite** los siguientes valores. Asegúrese de seleccionar **Aceptar** para guardar los cambios.

    - **Registrar a usuarios silenciosamente en el cliente de sincronización de OneDrive con sus credenciales de Windows**
    - **Usar Archivos a petición de OneDrive**
    - **Impedir que los usuarios sincronicen cuentas de OneDrive personales**

La configuración tiene un aspecto similar a la siguiente:

> [!div class="mx-imgBorder"]
> ![Creación de una plantilla administrativa de OneDrive en Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/one-drive-administrative-template.png)

Para obtener más información sobre la configuración de cliente de OneDrive, vea [Usar la directiva de grupo para controlar la configuración de sincronización de OneDrive](https://docs.microsoft.com/onedrive/use-group-policy).

### <a name="assign-your-template"></a>Asignación de la plantilla

1. En la plantilla, seleccione **Asignaciones**.
2. Seleccione **Seleccionar grupos para incluir**. Aparece una lista de usuarios y grupos existentes.
3. Seleccione el grupo **Todos los dispositivos Windows** creado anteriormente y **Seleccionar**.

    Si usa este tutorial en un entorno de producción, plantéese agregar grupos que estén vacíos. El objetivo es practicar la asignación de la plantilla.

4. Guarde los cambios mediante **Guardar**.

En este punto ha creado algunas plantillas administrativas y las ha asignado a los grupos que ha creado. El siguiente paso consiste en crear una plantilla administrativa con Windows PowerShell y Microsoft Graph API para Intune.

## <a name="optional-create-a-policy-using-powershell-and-graph-api"></a>Opcional: Creación de una directiva con PowerShell y Graph API

En esta sección se usan los recursos siguientes. Estos recursos se instalan en esta sección.

- [SDK de PowerShell de Intune](https://github.com/microsoft/Intune-PowerShell-SDK)
- [Microsoft Graph API para Intune](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)

1. En el **equipo de administración**, abra **Windows PowerShell** como administrador:

    1. En la barra de búsqueda, escriba **powershell**.
    2. Haga clic con el botón derecho en **Windows PowerShell** > **Ejecutar como administrador**.

    > [!div class="mx-imgBorder"]
    > ![Ejecución de Windows PowerShell como administrador](./media/tutorial-walkthrough-administrative-templates/run-windows-powershell-administrator.png)

2. Obtenga y establezca la directiva de ejecución.

    1. Especifique: `get-ExecutionPolicy`.

        Anote en qué se ha establecido, que puede ser **Restringido**. Cuando termine el tutorial, vuelva a establecer el valor original.

    2. Especifique: `Set-ExecutionPolicy -ExecutionPolicy Unrestricted`.

    3. Escriba `Y` para cambiarlo.

    La directiva de ejecución de PowerShell ayuda a evitar la ejecución de scripts malintencionados. Para obtener más información, vea [Acerca de las directivas de ejecución](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies).

3. Especifique: `Install-Module -Name Microsoft.Graph.Intune`.

    Especifique `Y` si:

    - Se le pide instalar el proveedor de NuGet.
    - Se le pide instalar los módulos desde un repositorio que no es de confianza.

    Puede tardar varios minutos en terminar. Cuando termine, aparece un mensaje similar al siguiente:

    > [!div class="mx-imgBorder"]
    > ![Mensaje de Windows PowerShell después de instalar un módulo](./media/tutorial-walkthrough-administrative-templates/powershell-prompt.png)

4. En el explorador web, vaya a [https://github.com/Microsoft/Intune-PowerShell-SDK/releases](https://github.com/Microsoft/Intune-PowerShell-SDK/releases) y seleccione el archivo **Intune-PowerShell-SDK_v6.1907.00921.0001.zip**.

    1. Seleccione **Guardar como** y, luego, una carpeta que vaya a recordar. `c:\psscripts` es una buena elección.
    2. Abra la carpeta, haga clic con el botón derecho en el archivo. zip > **Extraer todo** > **Extraer**. La estructura de carpetas es similar a la siguiente carpeta:

        > [!div class="mx-imgBorder"]
        > ![Estructura de carpetas del SDK de PowerShell de Intune después de realizar la extracción](./media/tutorial-walkthrough-administrative-templates/psscripts-directory.png)

5. En la pestaña **Ver**, active **Extensiones de nombre de archivo**:

    > [!div class="mx-imgBorder"]
    > ![Activación de Extensiones de nombre de archivo en la pestaña Ver del explorador](./media/tutorial-walkthrough-administrative-templates/file-names-extension.png)

6. En la carpeta, vaya a `c:\psscripts\Intune-PowerShell-SDK_v6.1907.00921.0001\drop\outputs\build\Release\net471`. Haga clic con el botón derecho en cada archivo .dll > **Propiedades** > **Desbloquear**.

    > [!div class="mx-imgBorder"]
    > ![Desbloqueo de archivos .dll](./media/tutorial-walkthrough-administrative-templates/unblock-dll.png)

7. En la aplicación **Windows PowerShell**, escriba:

    ```powershell
    Import-Module c:\psscripts\Intune-PowerShell-SDK_v6.1907.00921.0001\drop\outputs\build\Release\net471\Microsoft.Graph.Intune.psd1
    ```

    Escriba `R` si se le pide que ejecute desde el publicador que no es de confianza.

8. Las plantillas administrativas de Intune usan la versión beta de Graph:

    1. Especifique: `Update-MSGraphEnvironment -SchemaVersion 'beta'`.

    2. Especifique: `Connect-MSGraph -AdminConsent`.

    3. Cuando se le pida, inicie sesión con la misma cuenta de administrador de Microsoft 365. Estos cmdlets crean la directiva en la organización de inquilino.

        **Usuario**: escriba la cuenta de administrador de la suscripción de inquilino de Microsoft 365.  
        **Contraseña**: escriba su contraseña.

    4. Seleccione **Aceptar**.

9. Cree el perfil de configuración de la **configuración de prueba**. Especifique:

    ```powershell
    $configuration = Invoke-MSGraphRequest -Url https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations -Content '{"displayName":"Test Configuration","description":"A test configuration created through PS"}' -HttpMethod POST
    ```

    Si estos cmdlets se ejecutan correctamente, se crea el perfil. Para confirmar, vaya al Centro de administración de puntos de conexión > **Perfiles de configuración**. Debe aparecer el perfil de la **configuración de prueba**.

10. Obtenga todos los valores SettingDefinitions. Especifique:

    ```powershell
    $settingDefinitions = Invoke-MSGraphRequest -Url https://graph.microsoft.com/beta/deviceManagement/groupPolicyDefinitions -HttpMethod GET
    ```

11. Busque el identificador de definición mediante el nombre para mostrar del valor. Especifique:

    ```powershell
    $desiredSettingDefinition = $settingDefinitions.value | ? {$_.DisplayName -Match "Silently sign in users to the OneDrive sync client with their Windows credentials"}
    ```

12. Configure un valor. Especifique:

    ```powershell
    $configuredSetting = Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues" -Content ("{""enabled"":""true"",""configurationType"":""policy"",""definition@odata.bind"":""https://graph.microsoft.com/beta/deviceManagement/groupPolicyDefinitions('$($desiredSettingDefinition.id)')""}") -HttpMethod POST
    ```

    ```powershell
    Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues('$($configuredSetting.id)')" -Content ("{""enabled"":""false""}") -HttpMethod PATCH
    ```

    ```powershell
    $configuredSetting = Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues('$($configuredSetting.id)')" -HttpMethod GET
    ```

### <a name="see-your-policy"></a>Visualización de la directiva

1. En el Centro de administración de puntos de conexión > **Perfiles de configuración** > **Actualizar**.
2. Seleccione el perfil de la **configuración de prueba** > **Configuración**.
3. En la lista desplegable, seleccione **Todos los productos**.

Ve que el valor **Registra a usuarios silenciosamente en el Cliente de sincronización de OneDrive con sus credenciales de Windows** está configurado.

## <a name="policy-best-practices"></a>Procedimientos recomendados de la directiva

Al crear directivas y perfiles en Intune, hay algunas recomendaciones y procedimientos recomendados que deben tenerse en cuenta. Para obtener más información, vea [Procedimientos recomendados para directivas y perfiles](device-profile-create.md#recommendations).

## <a name="clean-up-resources"></a>Limpieza de recursos

Cuando ya no sean necesarios, puede:

- Eliminar los grupos que haya creado:

  - **Todos los dispositivos de Windows 10 Student**
  - **Todos los dispositivos Windows**
  - **Todos los profesores**

- Eliminar las plantillas de administración que haya creado:

  - **Plantilla de administración: dispositivos de Windows 10 Student**
  - **Plantilla de administración: directivas de OneDrive que se aplican a todos los usuarios de Windows 10**
  - **Configuración de prueba**

- Volver a establecer la directiva de ejecución de Windows PowerShell en su valor original. En el ejemplo siguiente se establece la directiva de ejecución en Restringido:

  ```powershell
  Set-ExecutionPolicy -ExecutionPolicy Restricted
  ```

## <a name="next-steps"></a>Pasos siguientes

En este tutorial se ha familiarizado con el [Centro de administración de puntos de conexión](https://go.microsoft.com/fwlink/?linkid=2109431), ha usado el generador de consultas para crear grupos dinámicos y ha creado plantillas administrativas en Intune para configurar [valores de ADMX](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies). También ha comparado el uso de plantillas de ADMX en local y en la nube con Intune. Como bonus, ha usado cmdlets de PowerShell para crear una plantilla administrativa.

Para obtener más información sobre las plantillas administrativas en Intune, vea:

> [!div class="nextstepaction"]
> [Usar plantillas de Windows 10 para configurar opciones de directiva de grupo en Microsoft Intune](administrative-templates-windows.md)
