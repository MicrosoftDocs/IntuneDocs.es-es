---
title: 'Tutorial: Tutorial de Intune en Microsoft Endpoint Manager'
titleSuffix: Microsoft Intune
description: En este tutorial, realizará una visita por Microsoft Intune en el Centro de administración del Administrador de puntos de conexión de Microsoft para entender mejor cómo realizar las tareas.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/06/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to learn where to find the different features in Intune from the Microsoft Endpoint Manager admin center.
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1d8950e57c2427c522d337807d315ed5c399c0d5
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514088"
---
# <a name="tutorial-walkthrough-intune-in-microsoft-endpoint-manager"></a>Tutorial: Tutorial de Intune en el Administrador de puntos de conexión de Microsoft

[Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) contiene más de 100 servicios para ayudarle con una variedad de escenarios y posibilidades de informática en la nube. Microsoft Intune es uno de los distintos servicios disponibles en Azure. Intune ayuda a asegurarse de que los dispositivos, aplicaciones y datos empresariales cumplen los requisitos de seguridad de la empresa. Tiene el control para establecer qué requisitos se deben comprobar y qué sucede cuando no se cumplen. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) puede encontrar el servicio Microsoft Intune, así como otras opciones relacionadas con la administración de dispositivos. Comprender las características disponibles en Intune le ayudará a realizar diferentes tareas de administración de dispositivos móviles (MDM) y administración de aplicaciones móviles (MAM).

> [!NOTE]
> El Administrador de puntos de conexión de Microsoft es una plataforma de administración de puntos de conexión única e integrada para la administración de todos los puntos de conexión. Este Centro de administración del Administrador de puntos de conexión de Microsoft integra ConfigMgr y Microsoft Intune.

En este tutorial, aprenderá a:
> [!div class="checklist"]
> * Recorrer el Centro de administración del Administrador de puntos de conexión de Microsoft
> * Personalizar la vista del Centro de administración del Administrador de puntos de conexión de Microsoft

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](free-trial-sign-up.md).

## <a name="prerequisites"></a>Requisitos previos
Antes de configurar Microsoft Intune, revise los siguientes requisitos:

- [Exploradores y sistemas operativos compatibles](../supported-devices-browsers.md) 
- [Ancho de banda y requisitos de configuración de red de Intune](../network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Suscríbase para disfrutar de una prueba gratuita de Microsoft Intune

Probar Intune es gratis durante 30 días. Si ya dispone de una cuenta profesional o educativa, **inicie sesión** con dicha cuenta y agregue Intune a su suscripción. En caso contrario, puede [registrarse para obtener una cuenta de evaluación gratuita](free-trial-sign-up.md) para usar Intune en la organización.

> [!IMPORTANT]
> No puede combinar una cuenta profesional o educativa existente después de registrarse con una cuenta nueva.

## <a name="tour-microsoft-intune-in-the-microsoft-endpoint-manager-admin-center"></a>Paseo por el Centro de administración del Administrador de puntos de conexión de Microsoft Intune

Siga los pasos que se indican a continuación para comprender mejor Intune en el Centro de administración del Administrador de puntos de conexión de Microsoft. Cuando haya completado el paseo, comprenderá mejor algunas de las áreas principales de Intune.

1. Abra un explorador e inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431). Si es nuevo en Intune, use la suscripción de prueba gratuita.

    ![Captura de pantalla del Centro de administración del Administrador de puntos de conexión de Microsoft: Página de inicio](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-01.png)

    Cuando abra el Administrador de puntos de conexión de Microsoft o cualquier otro servicio en Azure, ese servicio se muestra en un panel. Algunas de las primeras cargas de trabajo que es posible que use en Intune incluyen **Dispositivos**, **Aplicaciones**, **Usuarios** y **Grupos**. Una carga de trabajo es simplemente una subárea de un servicio. Al seleccionar la carga de trabajo, el panel se abre como una página completa. Los demás paneles emergen del lado derecho del panel al abrirlos y se cierran para mostrar el panel anterior. 

    De forma predeterminada, al abrir el Administrador de puntos de conexión de Microsoft, verá el panel **Página principal**. En este panel se proporciona una instantánea visual general del estado y cumplimiento de los inquilinos, así como otros vínculos relacionados muy útiles.

2. Desde el panel de navegación, seleccione **Panel** para mostrar los detalles generales sobre los dispositivos y las aplicaciones cliente en el inquilino de Intune. Si está empezando con un inquilino de Intune nuevo, todavía no tendrá ningún dispositivo inscrito. 

    ![Captura de pantalla del Centro de administración del Administrador de puntos de conexión de Microsoft: Panel](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-02.png)
    
    Intune permite administrar los dispositivos y las aplicaciones de sus recursos, incluida la forma de acceder a los datos de la empresa. Para usar este servicio de administración de dispositivos móviles (MDM), primero es necesario inscribir los dispositivos en Intune. Al inscribir un dispositivo, se emite un certificado MDM. Dicho certificado se usa para la comunicación con el servicio de Intune. 

    Hay varios métodos para inscribir los dispositivos de los recursos en Intune. Cada método depende de la propiedad del dispositivo (personal o corporativo), el tipo de dispositivo (iOS/iPadOS, Windows o Android) y los requisitos de administración (restablecimiento, afinidad o bloqueo). Pero antes de poder habilitar la inscripción de dispositivos, debe configurar la infraestructura de Intune. En concreto, la inscripción de dispositivos requiere que [establezca su autoridad de MDM](mdm-authority-set.md). Para más información sobre cómo preparar el entorno de Intune (el inquilino), vea [Configurar Intune](setup-steps.md). Una vez que el inquilino de Intune esté listo, puede inscribir los dispositivos. Para obtener más información sobre la inscripción de dispositivos, consulte [¿Qué es la inscripción de dispositivos?](../enrollment/device-enrollment.md)

3. Desde el panel de navegación, seleccione **Dispositivos** para mostrar detalles sobre los dispositivos inscritos en el inquilino de Intune. 

    > [!TIP]
    > Si ya ha usado Intune en Azure Portal antes, encontraría los detalles anteriores en Azure Portal al iniciar sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) y seleccionar **Dispositivos**.

    El panel **Dispositivos - Información general** tiene varias pestañas que permiten ver un resumen de los siguientes estados y alertas:
    - **Estado de inscripción**: revise los detalles de los dispositivos inscritos en Intune por plataforma e inscripción.
    - **Alertas de inscripción**: busque más detalles sobre los dispositivos sin asignar por plataforma. 
    - **Estado de cumplimiento**: revise el estado de cumplimiento en función del dispositivo, la directiva, la configuración, las amenazas y la protección. Además, en este panel se proporciona una lista de dispositivos sin una directiva de cumplimiento.
    - **Estado de la configuración**: revise el estado de configuración de los perfiles de dispositivo, así como la implementación del perfil, y 
    - **Estado de actualización de software**: vea una representación visual del estado de implementación para todos los dispositivos y usuarios.

    ![Captura de pantalla del Centro de administración del Administrador de puntos de conexión de Microsoft: Dispositivos](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-03.png)

4. Desde el panel **Dispositivos: Información general**, seleccione **Directivas de cumplimiento** para mostrar detalles sobre el cumplimiento de los dispositivos administrados por Intune. Verá información similar a la de la imagen siguiente.

    ![Captura de pantalla del Centro de administración del Administrador de puntos de conexión de Microsoft: Directivas de cumplimiento](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-04.png)
    
    > [!TIP]
    > Si ya ha usado Intune en Azure Portal antes, encontraría los detalles anteriores en Azure Portal al iniciar sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) y seleccionar **Cumplimiento de dispositivos**.

    Los requisitos de cumplimiento son básicamente reglas, como requerir un PIN de dispositivo o el cifrado del dispositivo. Las directivas de cumplimiento de dispositivos definen las reglas y configuraciones que debe seguir un dispositivo para que se considere compatible. Para usar la conformidad de dispositivos, debe tener lo siguiente:
    - Una suscripción a Intune y a Azure Active Directory (Azure AD) Premium.
    - Dispositivos que ejecuten una plataforma admitida.
    - Dispositivos inscritos en Intune.
    - Dispositivos inscritos en un usuario o ningún usuario primario.
    
    Para más información, vea [Introducción a las directivas de cumplimiento de dispositivos de Intune](../protect/device-compliance-get-started.md).

5. Desde el panel **Dispositivos - Información general**, seleccione **Acceso condicional** para mostrar detalles sobre las directivas de acceso.

    ![Captura de pantalla del Centro de administración del Administrador de puntos de conexión de Microsoft: Acceso condicional](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-05.png)

    > [!TIP]
    > Si ya ha usado Intune en Azure Portal antes, encontraría los detalles anteriores en Azure Portal al iniciar sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) y seleccionar **Acceso condicional**.

    El acceso condicional hace referencia a las formas en que puede controlar los dispositivos y las aplicaciones que pueden conectarse a los recursos del correo electrónico y la empresa. Para información sobre el acceso condicional basado en dispositivos y aplicaciones y buscar escenarios comunes para usar el acceso condicional con Intune, consulte [¿Qué es el acceso condicional?](../protect/conditional-access.md)

6. Desde el panel de navegación, seleccione **Dispositivos** > **Perfiles de configuración** para mostrar detalles sobre los perfiles de dispositivo en Intune.

    ![Captura de pantalla del Centro de administración del Administrador de puntos de conexión de Microsoft: Perfiles de configuración](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-06.png)
    
    > [!TIP]
    > Si ya ha usado Intune en Azure Portal antes, encontraría los detalles anteriores en Azure Portal al iniciar sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) y seleccionar **Configuración de dispositivos**.

    Intune incluye opciones y características que se pueden habilitar o deshabilitar en distintos dispositivos dentro de la organización. Estas características y opciones de configuración se agregan a los "perfiles de configuración". Puede crear perfiles para otros dispositivos y plataformas, incluidas iOS/iPadOS, Android, macOS y Windows. Después, puede usar Intune para aplicar el perfil a los dispositivos de la organización.   

    Para más información sobre la configuración de dispositivos, vea [Aplicación de la configuración de características en dispositivos con perfiles de dispositivos Microsoft Intune](../configuration/device-profiles.md).

7. Desde el panel de navegación, seleccione **Dispositivos** > **Todos los dispositivos** para mostrar detalles sobre los dispositivos inscritos en el inquilino de Intune. Si está empezando con una inscripción de Intune nueva, todavía no tendrá dispositivos inscritos.

    ![Captura de pantalla del Centro de administración del Administrador de puntos de conexión de Microsoft: Todos los dispositivos](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-07.png)

    En esta lista de dispositivos se muestran detalles clave sobre el cumplimiento, la versión del sistema operativo y la última fecha de inserción en el repositorio.

    > [!TIP]
    > Si ya ha usado Intune en Azure Portal antes, encontraría los detalles anteriores en Azure Portal al iniciar sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) y seleccionar **Dispositivos** > **Todos los dispositivos**.
 
8. En el panel de navegación, seleccione **Aplicaciones** para mostrar información general sobre el estado de la aplicación. En este panel se proporciona el estado de instalación de la aplicación en función de las pestañas siguientes:

    > [!TIP]
    > Si ya ha usado Intune en Azure Portal antes, encontraría los detalles anteriores en Azure Portal al iniciar sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) y seleccionar **Aplicaciones cliente**.

    El panel **Aplicaciones - Información general** tiene dos pestañas que le permiten ver un resumen de los siguientes estados:
    - **Estado de la instalación**: puede ver los principales errores de instalación por dispositivo, así como las aplicaciones con errores de instalación.  
    - **Estado de la directiva de protección de aplicaciones**: encuentre detalles sobre los usuarios asignados a las directivas de protección de aplicaciones, así como los usuarios marcados.

    ![Captura de pantalla del Centro de administración del Administrador de puntos de conexión de Microsoft: Aplicaciones](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-08.png)

    Como administrador de TI, puede usar Microsoft Intune para administrar las aplicaciones cliente que usan los trabajadores de su empresa. Esta funcionalidad se suma a la administración de dispositivos y la protección de datos. Una de las prioridades de un administrador es garantizar que los usuarios finales tengan acceso a las aplicaciones que necesitan para hacer su trabajo. Aparte de todo esto, puede que quiera asignar y administrar aplicaciones en dispositivos que no están inscritos en Intune. Intune ofrece diversas funcionalidades para ayudarle a conseguir las aplicaciones que necesita y en los dispositivos de su elección. 

    > [!NOTE]
    > En el panel **Aplicaciones - Información general** también se proporcionan detalles sobre el estado y la cuenta del inquilino.

    Para más información sobre cómo agregar y asignar aplicaciones, vea [Incorporación de aplicaciones a Microsoft Intune](../apps/apps-add.md) y [Asignación de aplicaciones a grupos con Microsoft Intune](../apps/apps-deploy.md).

9. En el panel **Aplicaciones - Información general**, seleccione **Todas las aplicaciones** para ver una lista de las aplicaciones que se han agregado a Intune.

    > [!TIP]
    > Si ya ha usado Intune en Azure Portal antes, encontraría los detalles anteriores en Azure Portal al iniciar sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) y seleccionar **Aplicaciones cliente** > **Aplicaciones**.

    Puede agregar a Intune una variedad de tipos de aplicación diferentes en función de la plataforma. Una vez que se ha agregado una aplicación, puede asignarla a grupos de usuarios. 

    ![Captura de pantalla del Centro de administración del Administrador de puntos de conexión de Microsoft: Todas las aplicaciones](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-09.png)

    Para más información, vea [Agregar aplicaciones a Microsoft Intune](~/apps/apps-add.md). 

10. Desde el panel de navegación, seleccione **Usuarios** para mostrar detalles sobre los usuarios que haya incluido en Intune. Estos usuarios son los recursos de la empresa.

    ![Captura de pantalla del Centro de administración del Administrador de puntos de conexión de Microsoft: Usuarios](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-10.png)

    > [!TIP]
    > Si ya ha usado Intune en Azure Portal antes, encontraría los detalles anteriores en Azure Portal al iniciar sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) y seleccionar **Usuarios**.

    Puede agregar usuarios directamente a Intune o sincronizarlos desde la instancia local de Active Directory. Una vez agregados, los usuarios pueden inscribir dispositivos y obtener acceso a los recursos de la empresa. También puede asignar permisos adicionales a los usuarios para que accedan a Intune. Para más información, vea [Adición de usuarios y concesión de permiso administrativo a Intune](users-add.md).

11. Desde el panel de navegación, seleccione **Grupos** para mostrar detalles sobre los grupos de Azure Active Directory (Azure AD) incluidos en Intune. Como administrador de Intune, los grupos se usan para administrar usuarios y dispositivos.

    ![Captura de pantalla del Centro de administración del Administrador de puntos de conexión de Microsoft: Grupos](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-11.png)

    > [!TIP]
    > Si ya ha usado Intune en Azure Portal antes, encontraría los detalles anteriores en Azure Portal al iniciar sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) y seleccionar **Grupos**.

    Puede configurar grupos para satisfacer sus necesidades organizativas. Cree grupos para organizar a los usuarios o dispositivos por ubicación geográfica, departamento o características de hardware. Use los grupos para administrar tareas a escala. Por ejemplo, puede establecer directivas para muchos usuarios o implementar aplicaciones para un conjunto de dispositivos. Para más información sobre los grupos, vea [Agregar grupos para organizar usuarios y dispositivos](../groups-add.md).

12. Desde el panel de navegación, seleccione **Administración de inquilinos** para mostrar detalles sobre el inquilino de Intune.

    > [!TIP]
    > Si ya ha usado Intune en Azure Portal antes, encontraría los detalles anteriores en Azure Portal al iniciar sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) y seleccionar **Estado de inquilino**.

    En el panel **Administración de inquilinos - Estado de inquilino** se proporcionan pestañas para **Detalles del inquilino**, **Estado del conector** y **Panel de Service Health**. Si hay problemas con el inquilino o propios de Intune, encontrará los detalles en este panel. 

    ![Captura de pantalla del Centro de administración del Administrador de puntos de conexión de Microsoft: Estado de inquilino](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-12.png)

    Para más información, vea [Estado del inquilino de Intune](../tenant-status.md).

13. Desde el panel de navegación, seleccione **Solución de problemas + soporte técnico** > **Solucionar problemas** para comprobar los detalles de estado de un usuario específico. 

    > [!TIP]
    > Si ya ha usado Intune en Azure Portal antes, encontraría los detalles anteriores en Azure Portal al iniciar sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) y seleccionar **Solucionar problemas**.

    En la lista desplegable **Asignaciones**, puede elegir ver las asignaciones de destino de las aplicaciones cliente, las directivas, los anillos de actualización y las restricciones de inscripción. Además, en este panel se proporcionan detalles del dispositivo, el estado de protección de la aplicación y los errores de inscripción para un usuario específico.

    ![Captura de pantalla del Centro de administración del Administrador de puntos de conexión de Microsoft: Solucionar problemas](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-13.png)

    Para más información sobre la solución de problemas con Intune, vea [Uso del portal de solución de problemas para ayudar a los usuarios de su empresa](../help-desk-operators.md).

14. Desde el panel de navegación, seleccione **Solución de problemas + soporte técnico** > **Ayuda y soporte técnico** para solicitar ayuda. 

    > [!TIP]
    > Si ya ha usado Intune en Azure Portal antes, encontraría los detalles anteriores en Azure Portal al iniciar sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) y seleccionar **Ayuda y soporte técnico**.

    Como administrador de TI, puede usar la opción **Ayuda y soporte técnico** para buscar y ver soluciones, y también para registrar una incidencia de soporte técnico en línea sobre Intune. 

    ![Captura de pantalla del Centro de administración del Administrador de puntos de conexión de Microsoft: Ayuda y soporte técnico](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-14.png)

    Para crear una incidencia de soporte técnico, la cuenta debe tener asignado un rol de administrador en Azure Active Directory. Los roles de administrador incluyen **Administrador de Intune**, **Administrador Global** y **Administrador de servicios**. 

    Para obtener más información, vea [Cómo obtener asistencia para Microsoft Intune](../get-support.md).

15. Desde el panel de navegación, seleccione **Solución de problemas + soporte técnico** > **Escenarios guiados** para mostrar los escenarios de Intune disponibles. 

    Un escenario guiado es una serie personalizada de pasos en torno a un caso de uso completo. Los escenarios más habituales se basan en el rol que un administrador, un usuario o un dispositivo desempeñan en la organización. Estos roles suelen requerir una colección de perfiles, opciones, aplicaciones y controles de seguridad cuidadosamente organizados para proporcionar la mejor experiencia de usuario y seguridad.

    Si no está familiarizado con todos los pasos y recursos necesarios para implementar un determinado escenario de Intune, los escenarios guiados pueden servir de punto de partida. 

    ![Captura de pantalla del Centro de administración del Administrador de puntos de conexión de Microsoft: Escenarios guiados](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-15.png)

    Para más información sobre los escenarios guiados, vea [Introducción a los escenarios guiados de Intune](~/fundamentals/guided-scenarios-overview.md).

## <a name="configure-the-microsoft-endpoint-manager-admin-center"></a>Configuración del Centro de administración del Administrador de puntos de conexión de Microsoft

Azure permite personalizar y configurar la vista del portal.

### <a name="change-the-dashboard"></a>Cambio del panel

El **Panel** para mostrar los detalles generales sobre los dispositivos y las aplicaciones cliente en el inquilino de Intune. Los paneles proporcionan una manera de crear una vista centrada y organizada en el Centro de administración del Administrador de puntos de conexión de Microsoft. Use los paneles como un área de trabajo donde puede iniciar rápidamente tareas para las operaciones cotidianas y supervisar los recursos. Cree paneles personalizados basados en proyectos, tareas o roles de usuario, por ejemplo. El Centro de administración del Administrador de puntos de conexión de Microsoft proporciona un panel predeterminado como punto de partida. Puede editar el panel predeterminado, crear y personalizar paneles adicionales, y publicar y compartir paneles para ponerlos a disposición de otros usuarios. 

   ![Captura de pantalla del Centro de administración del Administrador de puntos de conexión de Microsoft: Panel](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-16.png)

Para modificar el panel actual, seleccione **Editar**. Si no quiere modificar el panel predeterminado, también puede crear un **panel nuevo**. Al crear un panel, se obtiene un panel vacío y privado que incluye la **Galería de iconos**, que le permite agregar o reorganizar iconos. Puede buscar iconos por categoría o tipo de recurso. También puede buscar iconos concretos. Seleccione **Mi panel** para seleccionar cualquiera de los paneles personalizados existentes.

### <a name="change-the-portal-settings"></a>Cambio de la configuración del portal

Puede personalizar el Centro de administración del Administrador de puntos de conexión de Microsoft si selecciona la vista predeterminada, el tema y el período de tiempo de expiración de las credenciales, así como la configuración de idioma y región.

   <img alt="Screenshot of the Microsoft Endpoint Manager admin center - Portal settings" src="./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-17.png" width="250">

## <a name="next-steps"></a>Pasos siguientes

Para empezar a trabajar rápidamente en Microsoft Intune, puede consultar los inicios rápidos de Intune si primero configura una cuenta gratuita de Intune.

> [!div class="nextstepaction"]
> [Inicio rápido: Prueba gratuita de Microsoft Intune](free-trial-sign-up.md)
