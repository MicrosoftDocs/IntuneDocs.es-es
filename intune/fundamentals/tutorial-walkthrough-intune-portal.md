---
title: Tutorial de Intune en Azure Portal
titleSuffix: Microsoft Intune
description: En este tutorial, realizará una visita por Microsoft Intune para entender mejor cómo realizar las tareas.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/06/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e892d8a3-7f74-498c-98d5-e968a8fbb049
Customer intent: As an Intune admin, I want to learn where to find the different features in Intune.
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9197d4f96eae1041b00b07110ef421a12a4fe338
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "73712992"
---
# <a name="tutorial-walkthrough-of-microsoft-intune-in-the-azure-portal"></a>Tutorial: Tutorial de Microsoft Intune en Azure Portal

[Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) contiene más de 100 servicios para ayudarle con una variedad de escenarios y posibilidades de informática en la nube. Microsoft Intune es uno de los distintos servicios disponibles en Azure. Intune ayuda a asegurarse de que los dispositivos, aplicaciones y datos empresariales cumplen los requisitos de seguridad de la empresa. Tiene el control para establecer qué requisitos se deben comprobar y qué sucede cuando no se cumplen. [Azure Portal](https://portal.azure.com) es la ubicación en la que se encuentra el servicio Microsoft Intune. Comprender las características disponibles en Intune le ayudará a realizar diferentes tareas de administración de dispositivos móviles (MDM) y administración de aplicaciones móviles (MAM).

En este tutorial, aprenderá a:
> [!div class="checklist"]
> * Realizar un recorrido por Microsoft Intune
> * Configurar Azure Portal

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](free-trial-sign-up.md).

## <a name="prerequisites"></a>Requisitos previos
Antes de configurar Microsoft Intune, revise los siguientes requisitos:

- [Exploradores y sistemas operativos compatibles](../supported-devices-browsers.md) 
- [Ancho de banda y requisitos de configuración de red de Intune](../network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Suscríbase para disfrutar de una prueba gratuita de Microsoft Intune

Probar Intune es gratis durante 30 días. Si ya dispone de una cuenta profesional o educativa, **inicie sesión** con dicha cuenta y agregue Intune a su suscripción. En caso contrario, puede [registrarse para obtener una cuenta de evaluación gratuita](free-trial-sign-up.md) para usar Intune en la organización.

> [!IMPORTANT]
> No puede combinar una cuenta profesional o educativa existente después de registrarse con una cuenta nueva.

## <a name="tour-microsoft-intune"></a>Realizar un recorrido por Microsoft Intune

Siga estos pasos para comprender mejor Intune en Azure Portal. Cuando haya completado el paseo, comprenderá mejor algunas de las áreas principales de Intune.

1. Abra un explorador e inicie sesión en el [portal de Intune](https://aka.ms/intuneportal). Si es nuevo en Intune, use la suscripción de prueba gratuita.

    ![Captura de pantalla del portal de Microsoft Intune](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-01.png)

    Cuando abra Intune o cualquier otro servicio en Azure, ese servicio se muestra en un panel. Algunas de las primeras cargas de trabajo que es posible que use en Intune incluyen **Dispositivos**, **Aplicaciones cliente**, **Usuarios** y **Grupos**. Una carga de trabajo es simplemente una subárea de un servicio. Al seleccionar la carga de trabajo, el panel se abre como una página completa. Los demás paneles emergen del lado derecho del panel al abrirlos y se cierran para mostrar el panel anterior. Un panel también se conoce como una hoja. 

    De forma predeterminada, al abrir Intune verá el panel **Información general**. En este panel se proporciona una instantánea visual general del estado de asignación y cumplimiento de los dispositivos, así como del estado de instalación de las aplicaciones.

2. Desde [Intune](https://aka.ms/intuneportal), haga clic en **Inscripción de dispositivos** para mostrar detalles sobre los dispositivos inscritos en el inquilino de Intune. Si está empezando con un inquilino de Intune nuevo, todavía no tendrá ningún dispositivo inscrito. 

    ![Captura de pantalla del panel de inscripción de dispositivos](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-02.png)
    
    Intune permite administrar los dispositivos y las aplicaciones de sus recursos, incluida la forma de acceder a los datos de la empresa. Para usar este servicio de administración de dispositivos móviles (MDM), primero es necesario inscribir los dispositivos en Intune. Al inscribir un dispositivo, se emite un certificado MDM. Dicho certificado se usa para la comunicación con el servicio de Intune. 

    Hay varios métodos para inscribir los dispositivos de los recursos en Intune. Cada método depende de la propiedad del dispositivo (personal o corporativo), el tipo de dispositivo (iOS, Windows o Android) y los requisitos de administración (restablecimiento, afinidad o bloqueo). Pero antes de poder habilitar la inscripción de dispositivos, debe configurar la infraestructura de Intune. En concreto, la inscripción de dispositivos requiere que [establezca su autoridad de MDM](mdm-authority-set.md). Para más información sobre cómo preparar el entorno de Intune (el inquilino), vea [Configurar Intune](setup-steps.md). Una vez que el inquilino de Intune esté listo, puede inscribir los dispositivos. Para obtener más información sobre la inscripción de dispositivos, consulte [¿Qué es la inscripción de dispositivos?](../enrollment/device-enrollment.md)

3. Desde [Intune](https://aka.ms/intuneportal), haga clic en **Conformidad de dispositivos** para mostrar detalles sobre el cumplimiento de los dispositivos administrados por Intune. Verá información similar a la de la imagen siguiente.

    ![Captura de pantalla del panel Conformidad de dispositivos](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-03.png)
    
    Los requisitos de cumplimiento son básicamente reglas, como requerir un PIN de dispositivo o el cifrado del dispositivo. Las directivas de cumplimiento de dispositivos definen las reglas y configuraciones que debe seguir un dispositivo para que se considere compatible. Para usar la conformidad de dispositivos, debe tener lo siguiente:
    - Una suscripción a Intune y a Azure Active Directory (Azure AD) Premium.
    - Dispositivos que ejecuten una plataforma admitida.
    - Dispositivos inscritos en Intune.
    - Dispositivos inscritos en un usuario o ningún usuario primario.
    
    Para más información, vea [Introducción a las directivas de cumplimiento de dispositivos de Intune](../protect/device-compliance-get-started.md).

4. Desde [Intune](https://aka.ms/intuneportal), haga clic en **Configuración del dispositivo** para mostrar detalles sobre los perfiles de dispositivo en Intune.

    ![Captura de pantalla del panel Configuración del dispositivo](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-04.png)
    
    Intune incluye opciones y características que se pueden habilitar o deshabilitar en distintos dispositivos dentro de la organización. Estas características y opciones de configuración se agregan a los "perfiles de configuración". Puede crear perfiles para diferentes dispositivos y plataformas, incluidas iOS, Android y Windows. Después, puede usar Intune para aplicar el perfil a los dispositivos de la organización.   

    Para más información sobre la configuración de dispositivos, vea [Aplicación de la configuración de características en dispositivos con perfiles de dispositivos Microsoft Intune](../configuration/device-profiles.md).

5. Desde [Intune](https://aka.ms/intuneportal), haga clic en **Dispositivos** para mostrar detalles sobre los dispositivos inscritos en el inquilino de Intune. Si está empezando con una inscripción de Intune nueva, todavía no tendrá dispositivos inscritos.

    ![Captura de pantalla del panel de inscripción de dispositivos](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-05.png)

    En el panel **Dispositivos** se proporcionan detalles sobre los dispositivos inscritos del inquilino. Puede hacer clic en **Todos los dispositivos** para mostrar una lista de los dispositivos del inquilino de Intune.

6. Desde [Intune](https://aka.ms/intuneportal), haga clic en **Aplicaciones cliente** para mostrar el estado de instalación de la aplicación.

    ![Captura de pantalla del panel Aplicaciones cliente](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-06.png)

    Como administrador de TI, puede usar Microsoft Intune para administrar las aplicaciones cliente que usan los trabajadores de su empresa. Esta funcionalidad se suma a la administración de dispositivos y la protección de datos. Una de las prioridades de un administrador es garantizar que los usuarios finales tengan acceso a las aplicaciones que necesitan para hacer su trabajo. Aparte de todo esto, puede que quiera asignar y administrar aplicaciones en dispositivos que no están inscritos en Intune. Intune ofrece diversas funcionalidades para ayudarle a conseguir las aplicaciones que necesita y en los dispositivos de su elección. Para más información sobre cómo agregar y asignar aplicaciones, vea [Incorporación de aplicaciones a Microsoft Intune](../apps/apps-add.md) y [Asignación de aplicaciones a grupos con Microsoft Intune](../apps/apps-deploy.md).

7. Desde [Intune](https://aka.ms/intuneportal), haga clic en **Acceso condicional** para mostrar detalles sobre las directivas de acceso.

    ![Captura de pantalla del panel Acceso condicional](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-07.png)

    El acceso condicional hace referencia a las formas en que puede controlar los dispositivos y las aplicaciones que pueden conectarse a los recursos del correo electrónico y la empresa. Para información sobre el acceso condicional basado en dispositivos y aplicaciones y buscar escenarios comunes para usar el acceso condicional con Intune, consulte [¿Qué es el acceso condicional?](../protect/conditional-access.md)

8. Desde [Intune](https://aka.ms/intuneportal), haga clic en **Usuarios** para mostrar detalles sobre los usuarios que haya incluido en Intune. Estos usuarios son los recursos de la empresa.

    ![Captura de pantalla del panel Usuarios](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-08.png)

    Puede agregar usuarios directamente a Intune o sincronizarlos desde la instancia local de Active Directory. Una vez agregados, los usuarios pueden inscribir dispositivos y obtener acceso a los recursos de la empresa. También puede asignar permisos adicionales a los usuarios para que accedan a Intune. Para más información, vea [Adición de usuarios y concesión de permiso administrativo a Intune](users-add.md).

9. Desde [Intune](https://aka.ms/intuneportal), haga clic en **Grupos** para mostrar detalles sobre los grupos de Azure Active Directory (Azure AD) incluidos en Intune. Como administrador de Intune, los grupos se usan para administrar usuarios y dispositivos.

    ![Captura de pantalla del panel Grupos](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-09.png)

    Puede configurar grupos para satisfacer sus necesidades organizativas. Cree grupos para organizar a los usuarios o dispositivos por ubicación geográfica, departamento o características de hardware. Use los grupos para administrar tareas a escala. Por ejemplo, puede establecer directivas para muchos usuarios o implementar aplicaciones para un conjunto de dispositivos. Para más información sobre los grupos, vea [Agregar grupos para organizar usuarios y dispositivos](../groups-add.md).

10. Desde [Intune](https://aka.ms/intuneportal), haga clic en **Ayuda y soporte técnico** para solicitar ayuda. Como administrador de TI, puede usar la opción **Ayuda y soporte técnico** para buscar y ver soluciones, y también para registrar una incidencia de soporte técnico en línea sobre Intune. 

    ![Captura de pantalla del panel Ayuda y soporte técnico](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-10.png)

    Para crear una incidencia de soporte técnico, la cuenta debe tener asignado un rol de administrador en Azure Active Directory. Los roles de administrador incluyen **Administrador de Intune**, **Administrador Global** y **Administrador de servicios**. Para obtener más información, vea [Cómo obtener asistencia para Microsoft Intune](../get-support.md).

11. Desde [Intune](https://aka.ms/intuneportal), haga clic en **Estado de inquilino** para mostrar detalles sobre el inquilino de Intune.

    ![Captura de pantalla del panel Estado de inquilino](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-11.png)

    Los detalles de estado de inquilino incluyen el estado del conector, el estado del servicio de Intune y noticias de Intune. Si hay problemas con el inquilino o propios de Intune, encontrará los detalles en el panel **Estado de inquilino**. Para más información, vea [Estado del inquilino de Intune](../tenant-status.md).

12. Desde [Intune](https://aka.ms/intuneportal), haga clic en **Solucionar problemas** para obtener un acceso directo sobre sugerencias de solución de problemas, solicitar soporte técnico o comprobar el estado de Intune. Esta información es específica del usuario de Intune que seleccione.

    ![Captura de pantalla del panel Solución de problemas](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-12.png)

Para más información sobre la solución de problemas con Intune, vea [Uso del portal de solución de problemas para ayudar a los usuarios de su empresa](../help-desk-operators.md).

## <a name="configure-the-azure-portal"></a>Configurar Azure Portal

Azure permite personalizar y configurar la vista del portal.

### <a name="change-the-sidebar"></a>Cambiar la barra lateral

La **barra lateral** en el lado izquierdo de Azure Portal muestra una lista de todos los servicios de Azure disponibles. Esta lista completa se puede modificar desde la vista predeterminada, por lo que puede mantener una vista permanente de los servicios que considere más importantes. En la siguiente información, se usa Intune como ejemplo de servicio que se agrega a la parte superior de la lista.

![Un usuario busca Microsoft Intune en la lista "Más servicios".](./media/tutorial-walkthrough-intune-portal/azure-add-intune1.png)

1. Seleccione **Todos los servicios** en la barra lateral de lado izquierdo de la página.
2. Busque **Intune** en el cuadro de filtro.
3. Seleccione la **estrella** para agregar Intune a la parte inferior de la lista de sus servicios favoritos.
4. Mantenga el mouse sobre el servicio de Intune. Seleccione y arrastre Intune mediante los **tres puntos verticales** situados a la derecha del nombre del servicio.

### <a name="change-the-dashboard"></a>Cambiar el panel

La página de inicio predeterminada es el **panel**. En esta página puede personalizar los iconos para mostrar la información que considere más importante.

![Imagen del nuevo panel genérico. Muestra la barra lateral con todos los servicios a la izquierda, y el panel principal en el centro. Los botones de modificación del panel están en la parte superior; son los iconos que permiten acceder a todos los recursos, a los tutoriales de inicio rápido, al estado del servicio y a Azure Marketplace.](./media/tutorial-walkthrough-intune-portal/azure-default-dashboard.png)

Para modificar el panel actual, seleccione el botón **Editar panel**. Si no quiere modificar el panel predeterminado, también puede crear un **panel nuevo**. Al crear un panel, se obtiene un panel vacío y privado que incluye la **Galería de iconos**, que le permite agregar o reorganizar iconos. Puede buscar iconos por su **categoría general** o **tipo**, mediante la **búsqueda** o por su **grupo de recursos** o **etiqueta**.

También puede agregar iconos directamente al panel desde cualquier botón de **puntos suspensivos** y seleccionando **Anclar al panel**.

![Un primer plano de la sección Usuarios y grupos > Todas las ubicaciones de grupos en Intune, que muestra la opción "Anclar al panel" en el extremo derecho de un grupo.](./media/tutorial-walkthrough-intune-portal/azure-pin-to-dashboard.png)

Esta funcionalidad será más importante después de agregar más contenido a Intune, como grupos y usuarios.

## <a name="next-steps"></a>Pasos siguientes

Para empezar a trabajar rápidamente en Microsoft Intune, puede consultar los inicios rápidos de Intune si primero configura una cuenta gratuita de Intune.

> [!div class="nextstepaction"]
> [Inicio rápido: Prueba gratuita de Microsoft Intune](free-trial-sign-up.md)
