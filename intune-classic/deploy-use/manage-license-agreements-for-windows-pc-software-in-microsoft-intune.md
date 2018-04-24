---
title: Administración de contratos de licencia de software para equipos que ejecutan el software cliente de Intune
description: Intune permite administrar contratos de licencia de software adquiridos a través de los contratos de licencias por volumen de Microsoft, así como de software que se adquirió por otros medios.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c59d8635-3f66-40f5-824a-a71c738e0341
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f1d4eb8ea128ba453e555836289fb7d1ce8b34c4
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="manage-license-agreements-for-windows-pc-software-in-microsoft-intune"></a>Administrar contratos de licencia de software de equipos Windows en Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune permite agregar y administrar información de contratos de licencia para el software adquirido a través de contratos de licencias por volumen de Microsoft. También puede hacerlo para software de Microsoft o de terceros adquirido por otros medios. Además, puede organizar esta información en grupos lógicos.

> [!IMPORTANT]
> Esta característica se proporciona solo para su comodidad y no se puede garantizar su precisión. No debe basarse en ella para confirmar el cumplimento de los contratos de licencias por volumen de Microsoft. Microsoft no usará los datos recopilados para investigar posibles infracciones o el cumplimiento de los contratos de licencia que pudiera haber suscrito con nosotros.
>
> Las licencias que agregue a Intune no afectan a los contratos de licencia ni a sus derechos de uso del software. Por ejemplo, si se elimina un par de contrato y licencia de Intune, no se eliminan ni se anulan los contratos de licencia que existan entre el usuario y Microsoft.

En el área de trabajo **Licencias** de la consola de administrador de Intune, puede:

-   Agregar y editar contratos de licencias por volumen de Microsoft.

-   Agregar y editar otros contratos de licencias de software.

-   Administrar licencias y grupos.

-   Compare la información de derechos que Intune recupera del Centro de servicios de licencias por volumen (VLSC) con el inventario de software de Microsoft que Intune detecta en los equipos administrados de Windows.

Asimismo, puede generar informes que muestran recuentos de instalaciones y de licencias de títulos de software. Los informes de licencias pueden ayudarle a evaluar su posición completa respecto a las licencias para los títulos de software con licencia de Microsoft y de otros fabricantes.

> [!TIP]
> El área de trabajo **Licencias** no se muestra en la consola de administrador hasta que administre al menos un equipo Windows con el cliente para PC Windows de Intune.

## <a name="add-microsoft-volume-licensing-agreements"></a>Agregar contratos de licencias por volumen de Microsoft
Los contratos de licencias por volumen de Intune proporcionan información de licencias del software adquirido a través de contratos de licencias por volumen de Microsoft. Puede agregar contratos de licencias por volumen de Microsoft a Intune mediante pares coincidentes de números de contrato. Los números de autorización o contrato deben coincidir con los números de inscripción o licencia correctos. Los pares de números de contrato se obtienen al adquirir los contratos de licencia del [Volume Licensing Service Center (VLSC)](http://go.microsoft.com/fwlink/?LinkID=223842).

1.  En la [consola de administrador de Microsoft Intune](https://account.manage.microsoft.com/admin/default.aspx), elija **Licencias**.

2.  En la página **Agregar contratos** , en **Elegir tipo de contrato**, seleccione **Contrato de licencias por volumen**.

3.  En la sección **Agregar detalles del contrato**, elija si quiere cargar un archivo o agregar manualmente los detalles.

    -   **Cargar un archivo CSV que contiene detalles del contrato**. Elija **Examinar** y seleccione el archivo CSV que quiere cargar.

        -   El archivo puede contener dos o tres columnas: dos para los pares de contratos solos, o tres si desea agregar un nombre descriptivo para cada par de contratos.

        -   El número total de caracteres en un par de números de contrato no puede superar los 16 caracteres ASCII.

        -   Únicamente se admiten caracteres ASCII.

        -   No se admiten los siguientes caracteres en el nombre del contrato: **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. Se permiten espacios en el nombre.

        -   El nombre de archivo no debe tener más de 128 caracteres.

        -   El archivo debe contener al menos un par de contratos y no puede contener más de 5000 pares de contratos.

        **Formato del archivo**

        Para crear este archivo puede agregar los pares de contratos en un documento de texto sin formato con uno de los siguientes formatos, en función del tipo de organización que registrase en el VLSC. Especifique un par de números de contrato por línea.

        -   **Clientes de Open Value:** *número de contrato*, *repetir número de contrato*, *nombre del contrato*

        -   **Clientes de Open:** *número de autorización*, *número de licencia relacionado*, *nombre del contrato*

        -   **Clientes de Select y Enterprise:** *número de contrato*, *número de inscripción relacionado*, *nombre del contrato*

        El formulario **Agregar contratos** le solicitará que busque este archivo cuando agregue un nuevo contrato.

        A continuación se muestra un ejemplo de contenido de un archivo .csv de un cliente de Open Value.

        `01-07001, 01-07001, Office agreements`

    -   **Agregar manualmente detalles del contrato**. Proporcione la información siguiente y escriba los pares de números de contrato en los cuadros **Número de autorización/contrato** y **Número de licencia/inscripción/cliente**. Después de escribir los dos números, elija el icono **Agregar par de números** para guardar los números y, después, agregue un par nuevo de forma opcional.

        -   **Nombre del contrato**: especifique un nombre único para el contrato.

            El nombre del contrato puede tener 256 caracteres como máximo y no puede contener los caracteres siguientes: **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. Se permiten espacios en el nombre.

        -   **Número de autorización/contrato**: especifique el número de autorización/contrato del par de licencia.

        -   **Número de licencia/inscripción/cliente**: especifique el número de licencia/inscripción/cliente del par de licencia.

        > [!NOTE]
        > Si agrega varios pares de números de contrato, Intune creará un contrato con el nombre que especifique, y todos los pares que haya agregado formarán parte de ese contrato.

    Puede elegir **+** para agregar otro par de números de contrato, o bien **-** para quitar un par de números de contrato que ya haya escrito.

4.  En el área **Seleccionar grupo de licencias** , realice alguna de las acciones siguientes:

    -   **Agregar los contratos a un grupo de contratos sin asignar**. Seleccione esta opción si no quiere agregar los contratos nuevos a un grupo de licencias.

    -   **Agregar los contratos a un nuevo grupo de licencias**. Escriba un nombre para el nuevo grupo de licencias.

    -   **Agregar los contratos a un grupo de licencias existentes**. En la lista **Nombre del grupo** , seleccione el grupo de licencias al que desea agregar los contratos.

5.  Elija **Aceptar**.

Se muestra la vista **Todos los contratos** e Intune se conecta al VLSC de Microsoft para validar los pares de números de contrato proporcionados.

Para actualizar la información de licencias por volumen después de haber agregado contratos de licencias a Intune, en la página **Información general sobre licencias**, elija **Actualizar ahora**. Esta acción permite recuperar la información actual de las licencias del [Microsoft Volume Licensing Service Center (VLSC) (Centro de servicios de licencias por volumen (VLSC) de Microsoft)](http://go.microsoft.com/fwlink/?LinkId=223842).

> [!IMPORTANT]
> Hasta que actualice la información de licencias por volumen, es posible que vea una información diferente en la lista de contratos y en la información de derechos de la página **Información general sobre contratos** .

Después de actualizar la información de licencias por volumen, puede comparar la información de licencias con el software de Microsoft detectado en el área de trabajo **Aplicaciones** . Igualmente, también puede ejecutar los siguientes informes de licencia:

-   **Informes de adquisición de licencias**: le permiten ver el software con licencia en los grupos de licencias que seleccione para ayudarle a encontrar deficiencias en la cobertura.

-   **Informes de instalación de licencias**: le ayudan a determinar si los contratos de licencia proporcionan una cobertura suficiente.

> [!NOTE]
> El **Título del producto** que se muestra para todos los contratos de licencias por volumen de Microsoft es **No disponible**.

## <a name="add-and-edit-other-software-licensing-agreements"></a>Agregar y editar otros contratos de licencias de software
También puede agregar otros tipos de contratos de licencias a Intune, además de los contratos de licencias por volumen de Microsoft. Estos contratos pueden incluir software que no sea de Microsoft o software de Microsoft adquirido a través de un distribuidor.

> [!IMPORTANT]
> Debe tener al menos un equipo Windows inscrito en Intune para poder agregar un contrato.  De igual manera, al menos un equipo inscrito debe tener cargado el paquete de software sujeto a licencia que desee usar para agregar un contrato de licencia.

### <a name="to-add-other-software-agreements"></a>Para agregar otros contratos de software

1.  En la [consola de administrador de Microsoft Intune](https://account.manage.microsoft.com/admin/default.aspx), elija **Licencias**.

2.  Elija **Agregar contratos** en la sección **Otros contratos de licencias de software**.

3.  Seleccione **Otro contrato de licencias de software** en la sección **Elegir tipo de contrato** de la página **Agregar contratos** .

4.  En el área **Agregar detalles del contrato** , especifique lo siguiente:

    -   **Agreement name** (obligatorio). El nombre del contrato puede tener 256 caracteres como máximo y no puede contener los caracteres siguientes: **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. Se permiten espacios en el nombre.

    -   **Publicador** (obligatorio). Cuando empiece a escribir el nombre de un publicador, el servicio recupera todos los nombres de publicador que contienen las letras que escribe. Por ejemplo, si escribe "soft", el servicio recupera todos los nombres de editor que contienen "soft" como parte del nombre, tal como "Microsoft" y "Microsoft Research". Los nombres de publicador se recuperan del catálogo de activos de software. Debe seleccionar el publicador para poder especificar el título del producto.

        > [!IMPORTANT]
        > La empresa que desea agregar podría no aparecer en esta lista. Solo puede agregar contratos de software de empresas que ya están presentes en el catálogo de activos de software. De todos modos, Microsoft trabaja sin descanso para agregar los títulos de software más populares. Si quiere enviar una solicitud para agregar una empresa a esta lista, puede hacerlo en el [sitio de Intune UserVoice](https://microsoftintune.uservoice.com/).

    -   **Título del producto** (obligatorio). Cuando empiece a escribir el título del producto, el servicio recupera todos los títulos de producto que contienen las letras que escribe. Debe especificar un **Publicador** para poder especificar un **Título del producto**.

    -   **Número de licencias** (obligatorio). Especifique el número de licencias adquiridas.

    -   **Fecha de inicio de la licencia**. Especifique la fecha de inicio de la cobertura de la licencia.

    -   **Fecha final de la licencia**. Especifique la fecha final de la cobertura de la licencia.

    -   **Detalles del contrato**. Opcionalmente, puede especificar información de contacto, las claves de registro y otros datos.

5.  En el área **Seleccionar grupo de licencias** , realice alguna de las acciones siguientes:

    -   Si no desea agregar los nuevos contratos a un grupo de licencias nuevo o existente, seleccione **Agregar los contratos a un grupo de contratos sin asignar** . Puede agregar los contratos a grupos de licencias definidos por el usuario en cualquier momento.

    -   Para agregar los nuevos contratos a un nuevo grupo de licencias, seleccione **Agregar los contratos a un nuevo grupo de licencias** . Se le solicitará que indique un nombre para el nuevo grupo de licencias.

    -   Para agregar los nuevos contratos a un grupo de licencias existente, seleccione **Agregar los contratos a un grupo de licencias existente** . En la lista **Nombre del grupo** , seleccione el grupo de licencias al que desea agregar los contratos.

6.  Elija **Aceptar**.

Se muestra la vista de lista **Todos los contratos** .

## <a name="manage-license-agreements"></a>Administrar contratos de licencia
Los contratos de licencias de software pueden agregarse a grupos de licencias. Puede utilizar grupos de licencias para organizar los contratos de licencias en unidades lógicas para la organización. Igualmente, puede eliminar los contratos de licencia que haya creado anteriormente.


|                            |                                                                                                                                                                                                                                                                                                                                                                          |
|----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            Tarea            |                                                                                                                                                                                 Detalles                                                                                                                                                                                  |
|   Crear un grupo de licencias   |                                                            En la página <strong>Información general</strong> del área de trabajo <strong>Licencias</strong>, elija <strong>Crear grupo de licencias</strong> en el menú <strong>Tareas</strong>. <strong>Nota:</strong> Puede crear como máximo 500 grupos de licencias.                                                             |
|   Cambiar el nombre de un grupo de licencias   |                                                                                                      En el área de trabajo <strong>Licencias</strong>, elija un grupo de licencias y, después, elija <strong>Editar grupo de licencias</strong> en el menú <strong>Tareas</strong>.                                                                                                       |
|   Eliminar un grupo de licencias   |                                 En el área de trabajo <strong>Licencias</strong>, elija un grupo de licencias y, después, elija <strong>Eliminar grupo de licencias</strong> en el menú <strong>Tareas</strong>. <strong>Sugerencia:</strong> Todas las licencias que se encontraban en el grupo eliminado se llevan al grupo de licencias <strong>Contratos sin asignar</strong>.                                 |
| Eliminar un contrato de licencia | En el área de trabajo <strong>Licencias</strong>, elija un contrato y, después, elija <strong>Eliminar</strong>. <strong>Sugerencia:</strong> Después de eliminar los contratos de licencias por volumen, para actualizar la información de licencia, elija <strong>Actualizar ahora</strong> en la página <strong>Información general sobre licencias</strong> o en la pestaña <strong>General</strong> para un grupo de licencias determinado. |

