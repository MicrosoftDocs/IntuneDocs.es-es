---
# required metadata

title: Administrar contratos de licencia de software de equipos Windows en Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: c59d8635-3f66-40f5-824a-a71c738e0341

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Administrar contratos de licencia de software de equipos Windows en Microsoft Intune
Microsoft Intune le permite agregar y administrar la información del contrato de licencia para el software que haya adquirido mediante contratos de licencias por volumen de Microsoft y para el software de Microsoft (o de terceros que no sean Microsoft) que se adquirió por otros medios. Asimismo, también puede organizar esta información en grupos lógicos.

> [!IMPORTANT]
> Esta característica se proporciona solo para fines de comodidad, no se puede garantizar su precisión. No debe basarse en ella para confirmar el cumplimento de los contratos de licencias por volumen de Microsoft. Microsoft no usará los datos recopilados para investigar posibles infracciones o el cumplimiento de los contratos de licencia que pudiera haber suscrito con nosotros.
> 
> Las licencias que agregue a Intune no afectan a los contratos de licencia ni a sus derechos de uso del software.  Por ejemplo, cuando se elimina un par de contrato y licencia de Intune, no se eliminan ni se anulan los contratos de licencia que existan entre el usuario y Microsoft.

En el área de trabajo **Licencias** de la consola de administrador de Intune, puede:

-   Agregar y editar contratos de licencias por volumen de Microsoft

-   Agregar y editar otros contratos de licencias de software

-   Administrar licencias y grupos

-   Compare la información de derechos que Intune recupera del Centro de servicios de licencias por volumen (VLSC) con el inventario de software de Microsoft que Intune detecta en los equipos administrados de Windows.

Asimismo, puede generar informes que muestran recuentos de instalaciones y de licencias de títulos de software. Los informes de licencias pueden ayudarle a evaluar su posición completa respecto a las licencias para los títulos de software con licencia de Microsoft y de otros fabricantes.

> [!TIP]
> El área de trabajo **Licencias** no se muestra en la consola de administrador hasta que administre al menos un equipo Windows con el cliente para PC Windows de Intune.

## Agregar contratos de licencias por volumen de Microsoft
Los contratos de licencias por volumen de Intune proporcionan información de licencias del software adquirido a través de contratos de licencias por volumen de Microsoft. Puede agregar contratos de licencias por volumen de Microsoft a Intune mediante pares coincidentes de números de contrato. Los números de autorización o contrato deben coincidir con los números de inscripción o licencia correctos. Los pares de números de contrato se obtienen al adquirir los contratos de licencia del [Centro de servicios de licencias por volumen de Microsoft (VLSC)](http://go.microsoft.com/fwlink/?LinkID=223842)..

1.  En la [consola de administración de Microsoft Intune](https://account.manage.microsoft.com/admin/default.aspx), haga clic en **Licencias**..

2.  En la página **Agregar contratos**, en **Elegir tipo de contrato**, seleccione **Contrato de licencias por volumen**..

3.  En la sección **Agregar detalles del contrato** , elija una de las siguientes opciones:

    -   **Cargar un archivo CSV que contiene detalles del contrato**: haga clic en Buscar y seleccione el archivo CSV que desea cargar.

        -   El archivo puede contener dos o tres columnas: dos para los pares de contratos solos, o tres si desea agregar un nombre descriptivo para cada par de contratos.

        -   El número total de caracteres en un par de números de contrato no puede superar los 16 caracteres ASCII.

        -   Únicamente se admiten caracteres ASCII.

        -   No se admiten los siguientes caracteres en el nombre del contrato: **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. Se permiten espacios en el nombre.

        -   El nombre de archivo no debe tener más de 128 caracteres.

        -   El archivo debe contener al menos un par de contratos y no puede contener más de 5.000 pares de contratos.

        **Formato del archivo**

        Para crear este archivo puede agregar los pares de contratos en un documento de texto sin formato con uno de los siguientes formatos, en función del tipo de organización que registrase en el VLSC. Especifique un par de números de contrato por línea.

        -   **Clientes de Open Value:** *Número de contrato*, *repetir número de contrato*, *nombre del contrato*

        -   **Clientes de Open:** *Número de autorización*, *número de licencia relacionado*, *nombre del contrato*

        -   **Clientes de Select y Enterprise:** *Número de contrato*, *número de inscripción relacionado*, *nombre del contrato*

        El formulario **Agregar contratos** le solicitará que busque este archivo cuando agregue un nuevo contrato.

        A continuación se muestra un ejemplo de contenido de un archivo .csv de un cliente de Open Value.

        `01-07001, 01-07001, Office agreements`

    -   **Agregar manualmente detalles del contrato**: proporcione la información siguiente y escriba los pares de números de contrato en los cuadros **Número de autorización/contrato** y **Número de licencia/inscripción/cliente**. Después de escribir los dos números, haga clic en el icono **Agregar par de números** para guardar los números y, a continuación, agregue un par nuevo si lo desea.

        -   **Nombre del contrato**: especifique un nombre único para el contrato.

            El nombre del contrato puede tener 256 caracteres como máximo y no puede contener los caracteres siguientes: **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. Se permiten espacios en el nombre.

        -   **Número de autorización/contrato**: especifique el número de autorización/contrato del par de licencia.

        -   **Número de licencia/inscripción/cliente**: especifique el número de licencia/inscripción/cliente del par de licencia.

        > [!NOTE]
        > Si agrega varios pares de números de contrato, Intune creará un contrato con el nombre que especifique, y todos los pares que agregó formarán parte de ese contrato.

    Puede hacer clic en **+** para agregar otro par de números de contrato, o en **-** para quitar un par de números de contrato que ya haya escrito.

4.  En el área **Seleccionar grupo de licencias** , realice alguna de las acciones siguientes:

    -   **Agregar los contratos a un grupo de contratos sin asignar**: seleccione esta opción si no desea agregar los nuevos contratos a un grupo de licencias.

    -   **Agregar los contratos a un nuevo grupo de licencias**: proporcione un nombre para el nuevo grupo de licencias.

    -   **Agregar los contratos a un grupo de licencias existentes**: en la lista **Nombre de grupo**, seleccione el grupo de licencias al que desea agregar los contratos.

5.  Haga clic en **Aceptar**..

Se muestra la vista **Todos los contratos** e Intune se conecta al Centro de servicios de licencias por volumen de Microsoft para validar los pares de números de contrato proporcionados.

Para actualizar la información de licencias por volumen después de haber agregado contratos de licencias a Intune, en la página **Información general sobre licencias**, haga clic en **Actualizar ahora**. Esta acción permite recuperar la información actual de las licencias del [Centro de servicios de licencias por volumen de Microsoft (VLSC)](http://go.microsoft.com/fwlink/?LinkId=223842)..

> [!IMPORTANT]
> Hasta que actualice la información de licencias por volumen, es posible que vea una información diferente en la lista de contratos y en la información de derechos de la página **Información general sobre contratos** .

Después de actualizar la información de licencias por volumen, puede comparar la información de licencias con el software de Microsoft detectado en el área de trabajo **Aplicaciones** . Igualmente, también puede ejecutar los siguientes informes de licencia:

-   **Informes de adquisición de licencias**: le permiten ver el software con licencia en los grupos de licencias que seleccione para ayudarle a encontrar deficiencias en la cobertura.

-   **Informes de instalación de licencias**: le ayudan a determinar si los contratos de licencia proporcionan una cobertura suficiente.

> [!NOTE]
> El **Título del producto** que se muestra para todos los contratos de licencias por volumen de Microsoft es **No disponible**..

## Agregar y editar otros contratos de licencias de software
También puede agregar otros tipos de contratos de licencias a Intune, además de los contratos de licencias por volumen de Microsoft. Estos contratos pueden incluir software que no sea de Microsoft o software de Microsoft adquirido a través de un distribuidor.

> [!IMPORTANT]
> Debe tener al menos un equipo Windows inscrito en Intune para poder agregar un contrato.  De igual manera, al menos un equipo inscrito debe tener cargado el paquete de software sujeto a licencia que desee usar para agregar un contrato de licencia.

### Para agregar otros contratos de software

1.  En la [consola de administración de Microsoft Intune](https://account.manage.microsoft.com/admin/default.aspx), haga clic en **Licencias**..

2.  Haga clic en **Agregar contratos** en la sección **Otros contratos de licencias de software** .

3.  Seleccione **Otro contrato de licencias de software** en la sección **Elegir tipo de contrato** de la página **Agregar contratos** .

4.  En el área **Agregar detalles del contrato** , especifique lo siguiente:

    -   **Agreement name** (obligatorio). El nombre del contrato puede tener 256 caracteres como máximo y no puede contener los caracteres siguientes: **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. Se permiten espacios en el nombre.

    -   **Publicador** (obligatorio). Cuando empiece a escribir el nombre de un publicador, el servicio recupera todos los nombres de publicador que contienen las letras que escribe. Por ejemplo, si escribe "soft", el servicio recupera todos los nombres de editor que contienen "soft" como parte del nombre, tal como "Microsoft" y "Microsoft Research". Los nombres de publicador se recuperan del catálogo de activos de software. Debe seleccionar el publicador para poder especificar el título del producto.

        > [!IMPORTANT]
        > La empresa que desea agregar podría no aparecer en esta lista. Solo puede agregar contratos de software de empresas que ya están presentes en el catálogo de activos de software. De todos modos, Microsoft trabaja sin descanso para agregar los títulos de software más populares. Si desea enviar una solicitud para agregar una empresa a esta lista, puede hacerlo en el [sitio de Intune Uservoice](https://microsoftintune.uservoice.com/)..

    -   **Título del producto** (obligatorio). Cuando empiece a escribir el título del producto, el servicio recupera todos los títulos de producto que contienen las letras que escribe. Debe especificar un **Publicador** para poder especificar un **Título del producto**..

    -   **Número de licencias** (obligatorio). Especifique el número de licencias adquiridas.

    -   **Fecha de inicio de la licencia**. Especifique la fecha de inicio de la cobertura de la licencia.

    -   **Fecha final de la licencia**. Especifique la fecha final de la cobertura de la licencia.

    -   **Detalles del contrato**. Opcionalmente, puede especificar información de contacto, las claves de registro y otros datos.

5.  En el área **Seleccionar grupo de licencias** , realice alguna de las acciones siguientes:

    -   Si no desea agregar los nuevos contratos a un grupo de licencias nuevo o existente, seleccione **Agregar los contratos a un grupo de contratos sin asignar** . Puede agregar los contratos a grupos de licencias definidos por el usuario en cualquier momento.

    -   Para agregar los nuevos contratos a un nuevo grupo de licencias, seleccione **Agregar los contratos a un nuevo grupo de licencias** . Se le solicitará que indique un nombre para el nuevo grupo de licencias.

    -   Para agregar los nuevos contratos a un grupo de licencias existente, seleccione **Agregar los contratos a un grupo de licencias existente** . En la lista **Nombre del grupo** , seleccione el grupo de licencias al que desea agregar los contratos.

6.  Haga clic en **Aceptar**..

Se muestra la vista de lista **Todos los contratos** .

## Administrar contratos de licencia
Los contratos de licencias de software pueden agregarse a grupos de licencias. Puede utilizar grupos de licencias para organizar los contratos de licencias en unidades lógicas para la organización. Igualmente, puede eliminar los contratos de licencia que creó anteriormente.

|||
|-|-|
|Tarea|Detalles|
|Crear un grupo de licencias|En la página **Información general** , del área de trabajo **Licencias** , haga clic en **Crear grupo de licencias** en el menú **Tareas** . **Nota:** Puede crear como máximo 500 grupos de licencias.|
|Cambiar el nombre de un grupo de licencias|En el área de trabajo **Licencias** , elija un grupo de licencias y haga clic en **Editar grupo de licencias** en el menú **Tareas** .|
|Eliminar un grupo de licencias|En el área de trabajo **Licencias** , elija un grupo de licencias y haga clic en **Eliminar grupo de licencias** en el menú **Tareas** . **Sugerencia:** Todas las licencias que se encontraban en el grupo eliminado se llevan al grupo de licencias **Contratos sin asignar**.|
|Eliminar un contrato de licencia|En el área de trabajo **Licencias**, seleccione un contrato y haga clic en **Eliminar**. **Sugerencia:** Después de eliminar los contratos de licencias por volumen, para actualizar la información de licencia, haga clic en **Actualizar ahora** en la página **Información general sobre licencias** o en la pestaña **General** para un grupo de licencias determinado.|





<!--HONumber=May16_HO1-->


