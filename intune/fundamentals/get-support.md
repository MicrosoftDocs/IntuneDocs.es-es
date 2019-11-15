---
title: Cómo obtener asistencia para Microsoft Intune
titleSuffix: Microsoft Intune
description: Obtenga soporte técnico en línea y telefónico para las suscripciones de prueba y de pago de Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7fc95d17-098e-4da5-8a09-a96476569dd9
ms.reviewer: cacamp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1049bfeaf3840e1e6a711fd4df10b0a29a88b6b8
ms.sourcegitcommit: 85c894cb4df34a5ff558e3b45e28a8b91054d9e6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73432550"
---
# <a name="how-to-get-support-for-microsoft-intune"></a>Cómo obtener asistencia para Microsoft Intune  
  
Microsoft proporciona servicios globales de soporte técnico, preventa, facturación y suscripción para Microsoft Intune. El soporte técnico está disponible tanto en línea como por teléfono para las suscripciones de pago y de prueba. El soporte técnico en línea está disponible en inglés y japonés. La asistencia telefónica y la asistencia de facturación en línea están disponibles en idiomas adicionales.

Como administrador de Intune, puede usar la opción **Ayuda y soporte técnico** para registrar una incidencia de soporte técnico en línea sobre Intune desde Azure Portal. Para crear y administrar un incidente de soporte técnico, su cuenta debe tener un rol de Azure Active Directory (Azure AD) que incluya la *acción* **microsoft.office365.supportTickets/tickets/manage**. Para información sobre los permisos y roles de Azure AD que se necesitan para crear una incidencia de soporte técnico, consulte el artículo sobre los [roles de administrador en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal).  

>[!IMPORTANT]  
> Para obtener soporte técnico para productos de terceros que funcionan con Intune (por ejemplo, Saaswedo, Cisco o Lookout), póngase en contacto con el proveedor de ese producto en primer lugar. Asegúrese de que ha configurado el otro producto correctamente antes de abrir una solicitud con el soporte técnico de Intune.
>
> Para obtener información sobre cómo solucionar problemas relacionados con Microsoft Intune, consulte la [sección de solución de problemas](help-desk-operators.md) de la documentación de Intune.

## <a name="known-issues-for-creating-support-incidents"></a>Problemas conocidos para crear incidentes de soporte técnico

Si la cuenta tiene los permisos necesarios pero no puede acceder correctamente a Ayuda y soporte técnico ni tampoco crear ni administrar un incidente de soporte técnico, revise estos problemas conocidos y sus soluciones:

- El token de usuario está obsoleto para la cuenta. Para resolver este problema, cierre sesión en todas las sesiones activas de la consola, vuelva a iniciar sesión e intente crear o administrar un incidente de soporte técnico.
- Varias sesiones activas. Si inició sesión con más de un usuario o sesión, cierre la sesión en todas las consolas, menos en una. Luego, con una sola sesión activa, intente crear o administrar un incidente de soporte técnico.

Otras acciones que podrían ser necesarios para resolver los problemas de acceso:

- Borre todas las cookies de la sesión activa del explorador y vuelva a intentar crear o administrar un incidente de soporte técnico.
- Use una sesión de exploración InPrivate para iniciar sesión en Intune e intente crear o administrar un incidente de soporte técnico.

Si las soluciones anteriores no funcionan, vay al [Centro de administración de Microsoft 365](https://admin.microsoft.com) y cree desde ahí una incidencia de soporte técnico. En estos momentos estamos trabajando en una corrección que estará disponible a finales del verano.

## <a name="help-and-support-experience"></a>Experiencia de ayuda y soporte técnico  

La experiencia de ayuda y soporte técnico de Intune está disponible en el [portal de administración de dispositivos de Microsoft 365](https://devicemanagement.microsoft.com) y en todas las hojas (o páginas) en Intune, en Azure Portal. 

![Hojas de Intune](./media/get-support/intune-blades.png)


La experiencia de *Ayuda y soporte técnico* es similar a la observada en el [centro de administración de Microsoft 365](https://admin.microsoft.com/) y reemplaza a la experiencia anterior de *Ayuda y soporte técnico*, que permanece vigente para otros servicios en Azure. 

Para acceder a Ayuda y soporte técnico, use estas opciones:  
- **Panel de administración de dispositivos**:
  - Después de seleccionar un área de características para Intune, seleccione la opción de **Ayuda y soporte técnico**.
  - En cualquier nodo del portal de administración de dispositivos, seleccione el icono **?** en la esquina superior derecha del portal y, a continuación, use la lista desplegable para seleccionar el servicio con el que desea ayuda. El icono **?** del portal de administración de dispositivos es compatible con varios servicios, y debe seleccionar el servicio específico para el que desea obtener ayuda.  

    ![Selección del servicio](./media/get-support/select-a-service.png)

    Después de seleccionar un servicio, verá la página de *Ayuda y soporte técnico* para ese servicio, donde puede entonces [especificar detalles](#specify-details-about-an-issue) sobre el problema específico con el que necesita ayuda.  

    Si los resultados de la búsqueda no parecen coincidir con las expectativas del servicio, asegúrese de que se ha seleccionado el servicio correcto. La selección del servicio aparece justo después de *Ayuda y soporte técnico*.  En caso de que no se haya seleccionado el servicio adecuado, haga clic en *Seleccione un servicio* para volver al menú desplegable de selección de servicio.   

    ![Confirmación del servicio](./media/get-support/confirm-your-service-selection.png) 


- **En Azure Portal:**
  - Seleccione **Ayuda y soporte técnico** desde cualquier hoja o página de Intune

  En Azure Portal, si selecciona el icono **?** de la esquina superior derecha o **Ayuda y soporte técnico** en el panel de navegación izquierdo, se abre *Ayuda y soporte técnico* para Azure. Desde la *Ayuda y soporte técnico* de Azure, no puede abrir directamente un incidente de soporte técnico de Intune, pero puede acceder a la página de *Ayuda y soporte técnico* de Intune realizando las siguientes acciones: 
  1. Seleccione Nueva solicitud de soporte técnico.
  2. En Tipo de problema, especifique Técnico.
  3. En Servicio, especifique Microsoft Intune.
  4. Seleccione el vínculo de la página de ayuda y soporte técnico de Intune.

> [!NOTE]  
> Si la instancia de Intune se hospeda en la nube privada de organismos públicos, también conocida como nube soberana de tipo Azure Government, consulte [Compatibilidad de Intune con la nube privada para organismos públicos](#intune-support-for-private-cloud-for-government), más adelante en este artículo. La experiencia de *Ayuda y soporte técnico* de Intune no estará disponible en la nube privada para organismos públicos hasta el próximo año. 


Al abrir *Ayuda y soporte técnico*, el portal muestra una vista u otra en función de si tiene o no incidentes de soporte técnico activos y, en caso de tener soporte técnico Premier, aparecerán también algunos elementos y opciones adicionales:
- **No hay incidentes de soporte técnico activos**: Verá la página **¿Necesita ayuda?** , como se ve en la siguiente imagen del panel de administración de dispositivos.  
- **Incidentes de soporte activos**: Verá la página de [incidencias de soporte técnico](#view-support-cases), que muestra la lista de incidentes activos.  
- **Contrato de soporte técnico Premier**: Su experiencia es la misma que en las dos primeras opciones, aunque verá los siguientes elementos adicionales en la página ¿Necesita ayuda?: 
  - Después del título de la página **¿Necesita ayuda?** , verá el banner de soporte técnico Premier:  
    ![Banner de soporte técnico Premier](./media/get-support/premier-banner.png)
  - En la sección **Obtener soporte técnico** de la página, puede establecer el nivel de **Gravedad** inicial al crear una solicitud de servicio por teléfono.


![Panel de administración de dispositivos y página ¿Necesita ayuda?](./media/get-support/help-support-dashboard.png)

En esta vista se pueden realizar estas acciones:

1. [Especificar detalles](#specify-details-about-an-issue) sobre el problema específico para que necesita ayuda.  
2. [Ver ayuda contextual](#view-context-sensitive-help) y soluciones relacionadas que estén basadas en los detalles especificados.  
3. [Obtener soporte técnico](#get-support) por correo electrónico o teléfono.  
4. [Ver casos de soporte técnico](#view-support-cases) que se hayan abierto antes mediante con este nuevo flujo de trabajo.  

### <a name="specify-details-about-an-issue"></a>Especificación de los detalles sobre un problema 

Cuando se abre Ayuda y soporte técnico desde una ubicación que es compatible con la nueva experiencia, se abre la página **¿Necesita ayuda?** En esta página, puede especificar los detalles sobre un problema. A medida que escribe los detalles, la consola ofrece consultas comunes en función de las palabras clave que usa. Seleccione entre una descripción ofrecida o rellenar su propia descripción del problema. Si escribe su propia descripción, seleccione **Obtener ayuda** para enviarlo. Después de enviar una consulta, la consola devuelve información contextual que puede ser útil para solucionar el problema.

Los siguientes son ejemplos de consultas que podría enviar:
  
- *No se puede restaurar el dispositivo iOS*  
- *No se puede crear una directiva de acceso condicional*  

![Especificar el problema en la página ¿Necesita ayuda?](./media/get-support/describe-the-issue.png)

### <a name="view-context-sensitive-help"></a>Consulta de ayuda contextual 

Después de seleccionar una descripción ofrecida o enviar su propia consulta, los resultados contextuales aparecen debajo de **Ver soluciones**. Estos resultados incluyen instrucciones de autoayuda específicos de Intune y resultados adicionales devueltos de una búsqueda web según los criterios de la consulta.  
![Ver resultados](./media/get-support/view-results.png)

### <a name="get-support"></a>Obtención de soporte técnico 

Si no consigue resolver el problema con la autoayuda o las instrucciones basadas en web, use la consola para abrir una incidencia de soporte técnico por correo electrónico o por teléfono.  
En la página **¿Necesita ayuda?** , seleccione la opción que quiere usar.  

  > [!NOTE] 
  > Las solicitudes de soporte técnico por correo electrónico no están disponibles para todos los inquilinos.  

- Para una solicitud por correo electrónico, indique su dirección de correo y, opcionalmente, puede agregar datos adjuntos al envío. Seleccione **Enviar** para abrir la solicitud. 

  ![Solicitud por correo electrónico](./media/get-support/email-support.png)
  
- Para una solicitud por teléfono, indique su número de teléfono. Si quiere, puede incluir su dirección de correo electrónico y agregar datos adjuntos al envío. Seleccione Llamarme para enviar la solicitud.  



   ![Solicitud por teléfono](./media/get-support/phone-support.png)

**Soporte técnico Premier**:  
Si tiene un contrato de soporte técnico Premier, tiene las mismas opciones para crear un incidente de soporte técnico por teléfono. También puede especificar la **Gravedad** para la devolución de llamada de soporte, y optar por crear la incidencia de soporte técnico en su contrato crítico.  

![Opciones de soporte técnico Premier](./media/get-support/premier-phone-support-options.png)


### <a name="view-support-cases"></a>Consulta de casos de soporte técnico  

Seleccione el botón del historial para ver los incidentes de soporte técnico que ha creado.  

![Consulta de casos de soporte técnico](./media/get-support/view-support-tickets.png)

- Solo los casos de soporte técnico que se abren mediante el nuevo flujo de trabajo son visibles desde este flujo de trabajo. Para verlos, use la vista Ayuda y soporte técnico desde la consola de administración de dispositivos o desde una hoja de Intune en Azure Portal. Estos casos tienen números de ocho dígitos. También puede ver estos casos desde el centro de administración de Microsoft 365.  

- Los casos abiertos sin usar la experiencia de ayuda y soporte técnico de Intune no se modifican. Para verlos, debe usar una vista Ayuda y soporte técnico que no forme parte de la experiencia de Intune, o el panel de administración de dispositivos. Estos casos tienen números que empiezan por **117** o **118** y tienen 15 dígitos. Para verlos:

    1. Inicie sesión en Azure (<https://portal.azure.com>) con sus credenciales de administrador de Intune y haga clic en el icono *?* situado en la esquina superior derecha del portal y, después, seleccione *Ayuda y soporte técnico* para ir a la página [Ayuda y soporte técnico de Azure](https://ms.portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

    2. En la página **Ayuda y soporte técnico** puede ver la lista **Solicitudes de soporte técnico recientes** y seleccionarlas para ver detalles adicionales.
 

## <a name="azure-help--support-experience"></a>Experiencia de ayuda y soporte técnico de Azure 

Ya no puede usar la experiencia de *Ayuda y soporte técnico* de Azure para obtener ayuda con Intune, a menos que la suscripción esté en una nube privada para organismos públicos.
Si la instancia de Intune no se ejecuta en una nube privada para organismos públicos, al desplazarse a *Ayuda y soporte técnico* de Azure se le redirigirá a la experiencia de *Ayuda y soporte técnico* de Intune para crear y administrar incidentes de soporte técnico.

Cuando usa el panel de navegación izquierdo **Ayuda y soporte técnico** o usa el icono **?** para abrir el panel *Ayuda* y, después, seleccione **Ayuda y soporte técnico**, abra la página *Ayuda y soporte técnico* de Azure. 


En esta página, seleccione **+ Nueva solicitud de soporte técnico** para abrir la pestaña *Datos básicos* de la página *Ayuda y soporte técnico + Nueva solicitud de soporte técnico*.

![Ayuda y soporte técnico](./media/get-support/help-plus-support.png)

En esta página:

- En *Tipo de problema*, especifique **Técnico**.
- En *Servicio*, seleccione **Microsoft Intune**.

  A continuación, se le mostrará un vínculo que le redirigirá a la página de [ayuda y soporte técnico de Intune](https://aka.ms/intunehelpsupport).
  
  ![Nueva solicitud de soporte técnico](./media/get-support/new-request.png)


## <a name="intune-support-for-private-cloud-for-government"></a>Compatibilidad de Intune con la nube privada para organismos públicos  

Con la suscripción de Intune hospedada en la nube privada para organismos públicos, que también se conoce como nube soberana de tipo Azure Government, todavía no tiene acceso a la nueva experiencia de ayuda y soporte técnico de Intune.  En su lugar, use la siguiente información para obtener soporte técnico de Intune.


### <a name="create-an-online-support-ticket"></a>Creación de un vale de soporte en línea 

>[!IMPORTANT]    
> En la transición de *Ayuda y soporte técnico* a un nuevo sistema que todavía no está disponible para la nube privada para organismos públicos, cuando se crea un incidente de soporte técnico, el portal identifica un caso de soporte técnico en el que se usa un número de identificación de 15 dígitos. Cuando se crea el caso de 15 dígitos, se crea un reflejo de ese caso para que lo use el Soporte técnico de Microsoft. Este caso reflejado se crea en un nuevo sistema de soporte técnico, utiliza un identificador de caso de 8 dígitos y lo usan los servicios de soporte técnico para realizar el seguimiento de todos los trabajos y las comunicaciones de su incidente de soporte técnico. Poco después de crear el caso de 15 dígitos, recibirá un correo electrónico que identifica el número de 8 dígitos del caso de soporte reflejado que usan los servicios de soporte técnico.  
> 
> Apoye el trabajo personal y comuníquese con el caso de soporte técnico de 8 dígitos, y use solo el caso de soporte de 8 dígitos para registrar las comunicaciones y realizar un seguimiento del progreso de los incidentes. De este modo, recibirá actualizaciones por correo electrónico de ese caso de soporte técnico de 8 dígitos que sirven como registro de seguimiento del trabajo en el caso. No se registran detalles en el incidente de soporte técnico de 15 dígitos. Cuando concluye el soporte técnico y se cierra el caso de soporte de 8 dígitos, este estado se refleja en el caso de soporte técnico de 15 dígitos que puede ver desde Azure Portal.  No se deben esperar otras actualizaciones ni cambios de estado para el caso de soporte técnico de 15 dígitos.  
> 
> Cuando se completen las transiciones entre las herramientas de soporte técnico más adelante este año, la experiencia de soporte técnico de Intune hospedada en la nube de administración pública se asemejará a la experiencia predeterminada de *Ayuda y soporte técnico* que está disponible actualmente para las suscripciones de Intune hospedadas en la nube pública.  


1. Inicie sesión en Azure Portal (<https://portal.azure.us>) con sus credenciales de administrador de Intune y haga clic en el icono **?** situado en la esquina superior derecha del portal y, después, seleccione **Ayuda y soporte técnico** para ir a la página [Ayuda y soporte técnico de Azure](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

   ![Imagen del vínculo del signo de interrogación con el vínculo de Ayuda y soporte técnico resaltado](./media/get-support/azure-get-support.png)

2. En la página **Ayuda y soporte técnico** de Azure, seleccione **Nueva solicitud de soporte técnico**.

   ![Imagen del vínculo de Nueva solicitud de soporte técnico resaltado en la página de soporte y ayuda](./media/get-support/azure-support-ticket-link.png)

3. En la pestaña **Básico**, para la mayoría de los problemas de soporte técnico de Intune, seleccione las opciones siguientes:
   - **Tipo de problema**: **Técnico**
   - **Suscripción**: <*su suscripción*>
   - **Servicio**: **Microsoft Intune**
   - **Tipo de problema**: elija el tipo de problema en el menú desplegable.
   - **Subtipo de problema**: elija el subtipo de problema en el menú desplegable.
   - **Asunto**: Describa brevemente el problema que quiere solucionar.

   ![Imagen de la pestaña Básico de la página Ayuda y soporte técnico: nueva solicitud de soporte técnico](./media/get-support/help-new-support-case-basics.png)

   Seleccione **Siguiente: Soluciones** para continuar.
4. En la pestaña **Soluciones** pestaña, revise los pasos recomendados que pueden ayudarle a resolver el problema sin presentar un vale. Si todavía desea crear una solicitud de soporte técnico después de revisar los pasos, haga clic en **Siguiente: Details**.

   ![Imagen de la pestaña Soluciones de la página Ayuda y soporte técnico: nueva solicitud de soporte técnico](./media/get-support/help-new-support-case-solutions.png)
5. En la pestaña **Detalles**, rellene los detalles del problema, el método de soporte técnico, la información de contacto y haga clic en **Siguiente: Revisar y crear**.

   ![Imagen de la pestaña Detalles de la página Ayuda y soporte técnico: nueva solicitud de soporte técnico](./media/get-support/help-new-support-case-details.png)
6. Revise la información, compruebe que es correcta y elija **Crear** para enviar la solicitud de soporte técnico.

   ![Imagen de la pestaña Revisar y crear de la página Nueva solicitud de soporte técnico](./media/get-support/help-new-support-case-create.png)

>[!IMPORTANT]
>Si tiene una pregunta sobre suscripciones o facturación, puede abrir un caso para obtener asistencia mediante el [Centro de administración de Microsoft 365](https://admin.microsoft.com/Support/SupportEntry.aspx).

### <a name="view-support-requests"></a>Ver las solicitudes de soporte técnico  

Puede ver sus solicitudes de soporte técnico desde Azure Portal. Sin embargo, no toda la información está disponible.  Para ver los incidentes: 

1. Inicie sesión en Azure (<https://portal.azure.com>) con sus credenciales de administrador de Intune y haga clic en el icono **?** situado en la esquina superior derecha del portal y, después, seleccione **Ayuda y soporte técnico** para ir a la página [Ayuda y soporte técnico de Azure](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

2. En la página **Ayuda y soporte técnico** puede ver la lista **Solicitudes de soporte técnico recientes**.

   > [!IMPORTANT]  
   > Los clientes de Government Compute Cloud solo pueden ver el número de caso de soporte técnico de 15 dígitos y el estado de los incidentes. Todas las comunicaciones de casos y el seguimiento de trabajos o alertas se envían por correo electrónico y hacen referencia al número de caso de soporte técnico de 8 dígitos que se crea como un reflejo del caso de soporte abierto desde la consola de Intune.   

## <a name="additional-resources"></a>Recursos adicionales  

- [Soporte de facturación y administración de suscripciones](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)
- [Licencias por volumen](https://go.microsoft.com/fwlink/p/?LinkID=282015)
- [Solución de problemas de Intune](help-desk-operators.md)
