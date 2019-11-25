---
title: Cómo obtener asistencia para Microsoft Intune
titleSuffix: Microsoft Intune
description: Obtenga soporte técnico en línea y telefónico para las suscripciones de prueba y de pago de Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7fc95d17-098e-4da5-8a09-a96476569dd9
ms.reviewer: srik
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 14ff8ad2d41a6f2235c18f155e3a5b865e3a32e4
ms.sourcegitcommit: 01fb3d844958a0e66c7b87623160982868e675b0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74199309"
---
# <a name="how-to-get-support-for-microsoft-intune"></a>Cómo obtener asistencia para Microsoft Intune

Microsoft proporciona servicios globales de soporte técnico, preventa, facturación y suscripción para Microsoft Intune. El soporte técnico está disponible tanto en línea como por teléfono para las suscripciones de pago y de prueba. El soporte técnico en línea está disponible en inglés y japonés. La asistencia telefónica y la asistencia de facturación en línea están disponibles en idiomas adicionales.

Como administrador de Intune, puede usar la opción **Ayuda y soporte técnico** para registrar una incidencia de soporte técnico en línea sobre Intune desde Azure Portal. Para crear y administrar un incidente de soporte técnico, su cuenta debe tener un rol de Azure Active Directory (Azure AD) que incluya la *acción* **microsoft.office365.supportTickets/tickets/manage**. Para información sobre los permisos y roles de Azure AD que se necesitan para crear una incidencia de soporte técnico, consulte el artículo sobre los [roles de administrador en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal).

>[!IMPORTANT]
> Para obtener soporte técnico para productos de terceros que funcionan con Intune (por ejemplo, Saaswedo, Cisco o Lookout), póngase en contacto con el proveedor de ese producto en primer lugar. Asegúrese de que ha configurado el otro producto correctamente antes de abrir una solicitud con el soporte técnico de Intune.
>
> Para obtener información sobre cómo solucionar problemas relacionados con Microsoft Intune, consulte la [sección de solución de problemas](help-desk-operators.md) de la documentación de Intune.


## <a name="help-and-support-experience"></a>Experiencia de ayuda y soporte técnico

La experiencia de ayuda y soporte técnico de Intune está disponible en el [portal de administración de dispositivos de Microsoft 365](https://devicemanagement.microsoft.com) y en todas las hojas (o páginas) en Intune, en Azure Portal.

La experiencia de *Ayuda y soporte técnico* es similar a la observada en el [centro de administración de Microsoft 365](https://admin.microsoft.com/) y reemplaza a la experiencia anterior de *Ayuda y soporte técnico*, que permanece vigente para otros servicios en Azure.

> [!TIP]
> A partir del 18 de noviembre de 2019, se está implantando en los inquilinos una experiencia en la consola actualizada y simplificada para obtener ayuda y soporte técnico para Intune. Si esta experiencia todavía no está disponible para usted, lo estará pronto.

### <a name="options-to-access-help-and-support"></a>Opciones para obtener acceso a ayuda y soporte técnico

- **En Azure Portal:**

  - Seleccione **Ayuda y soporte técnico** desde cualquier hoja o página de Intune.

  > [!NOTE]  
  > Si la instancia de Intune se hospeda en la nube privada de organismos públicos, también conocida como nube soberana de tipo Azure Government, consulte [Compatibilidad de Intune con la nube privada para organismos públicos](#intune-support-for-private-cloud-for-government), más adelante en este artículo. La experiencia de *Ayuda y soporte técnico* de Intune no estará disponible en la nube privada para organismos públicos hasta el próximo año.

- **En el panel de administración de dispositivos:**
  - Después de seleccionar un área de características para Intune, seleccione la opción de **Ayuda y soporte técnico**.
  - En cualquier nodo del portal de administración de dispositivos, seleccione el icono **?** en la esquina superior derecha del portal y, a continuación, use la lista desplegable para seleccionar el servicio con el que desea ayuda. El icono **?** del portal de administración de dispositivos es compatible con varios servicios, y debe seleccionar el servicio específico para el que desea obtener ayuda.  

    ![Selección del servicio](./media/get-support/select-a-service.png)

    Después de seleccionar un servicio, verá su página de *Ayuda y soporte técnico*, donde puede especificar detalles para [encontrar soluciones](#find-solutions) sobre un problema específico.

    Si los resultados de la búsqueda no parecen coincidir con las expectativas del servicio, asegúrese de que se ha seleccionado el servicio correcto. La selección del servicio aparece justo después de *Ayuda y soporte técnico*.  En caso de que no se haya seleccionado el servicio adecuado, haga clic en *Seleccione un servicio* para volver al menú desplegable de selección de servicio.

    ![Confirmación del servicio](./media/get-support/confirm-your-service-selection.png)

###  <a name="the-support-experience"></a>Experiencia de soporte técnico

  Al abrir Ayuda y soporte técnico, el portal muestra la ventana **¿Necesita ayuda?** :

  ![Visualización de la ventana ¿Necesita ayuda?](./media/get-support/need-help.png)

  En la esquina superior izquierda hay tres iconos que puede seleccionar para abrir diferentes paneles de la ventana *¿Necesita ayuda?* . El panel que está viendo se identifica con el subrayado.

  Los clientes con un contrato de soporte técnico **Premier** o **Unified** tienen [opciones adicionales](#premier-and-unified-support-customers) de soporte técnico y verán un banner en la ventana *¿Necesita ayuda?* que recuerda a la siguiente imagen: ![Banner Premier](./media/get-support/premier-banner.png)

  La ventana *¿Necesita ayuda?* se abre en el panel *Buscar soluciones*. Sin embargo, si tiene un caso de soporte técnico activo, la ventana se abre en el panel *Solicitudes de servicio*, donde puede ver los detalles de los casos de soporte técnico activos y cerrados.

#### <a name="find-solutions"></a>Buscar soluciones

![Selección del panel Buscar soluciones](./media/get-support/find-solutions.png)

En el panel *Buscar soluciones*, especifique algunos detalles sobre una incidencia en el cuadro de texto proporcionado. En función del texto que se proporcione sobre una incidencia, el panel se rellena con posibles coincidencias. También obtendrá vínculos a artículos recomendados que pueden ayudarle a resolver el problema.

Cuando se encuentra una coincidencia segura con los datos que se describen, pueden aparecer sugerencias de solución de problemas justo en la ventana *¿Necesita ayuda?* .

Por ejemplo, puede escribir **errores de sincronización de contraseñas**. Los resultados incluyen una guía de solución de problemas directamente en el panel y vínculos a artículos recomendados de nuestra biblioteca de documentación.

![Visualización de información detallada de solución de problemas](./media/get-support/troubleshooting-insights.png)

#### <a name="contact-support"></a>Póngase en contacto con el soporte técnico.

![Selección del panel de contacto con el soporte técnico](./media/get-support/contact-support.png)

En el panel *Contacto con soporte técnico*, puede enviar una solicitud de asistencia. Este panel está disponible después de proporcionar algunas palabras clave básicas en el panel *Buscar soluciones*.

Al solicitar asistencia, proporcione una descripción del problema con tantos detalles como sea necesario.  Después de confirmar la información de contacto de teléfono y correo electrónico, seleccione el método de contacto preferido. La ventana muestra un tiempo de respuesta para cada método de contacto, lo que le permite estimar cuándo se pondrán en contacto con usted. Antes de enviar la solicitud, adjunte archivos como registros o capturas de pantallas que puedan ayudar a rellenar los detalles del problema.

![Formulario de contacto con el soporte técnico](./media/get-support/contact-support-form.png)

Después de rellenar la información necesaria, seleccione **Ponerse en contacto conmigo**.

#### <a name="service-requests"></a>Solicitudes de servicio

![Selección del panel Solicitudes de servicio](./media/get-support/service-requests.png)

El panel *Solicitudes de servicio* muestra el historial de casos. Los casos activos se encuentran arriba de la lista, con las incidencias cerradas que también están disponibles para revisión.

![Visualización de la lista de solicitudes de servicio](./media/get-support/service-requests-pane.png)

Si tiene un número de caso de soporte técnico activo, puede escribirlo aquí para ir a ese problema o puede seleccionar un incidente de la lista de incidentes activos y cerrados para ver más información sobre él.

Cuando haya terminado de ver los detalles de un incidente, seleccione la flecha izquierda que aparece en la parte superior de la ventana de la solicitud de servicio, justo encima de los tres iconos del panel *¿Necesita ayuda?* . La flecha atrás vuelve a la lista de incidentes de soporte técnico que ha abierto.

#### <a name="premier-and-unified-support-customers"></a>Clientes de soporte técnico Premier y Unified

Los clientes con un contrato de soporte técnico **Premier** o **Unified** pueden especificar la gravedad del problema y programar una devolución de llamada de soporte técnico a una hora y en un día concretos. Estas opciones están disponibles al abrir o enviar una nueva incidencia y al editar un caso de soporte activo.

**Gravedad**: las opciones para especificar la gravedad de una incidencia dependen del contrato de soporte técnico:

- *Premier*: gravedad de A, B o C.
- *Unified*: crítico o no crítico.

La selección de un problema con una gravedad **A** o **Crítica** le limita a un caso de soporte técnico por teléfono, que proporciona la opción más rápida para recibir asistencia.

**Callback schedule** (Programación de devolución de llamada): puede solicitar una devolución de llamada a una hora y en un día determinados.

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
   > Las nubes privadas para organismos públicos solo pueden ver el número de caso de soporte técnico de 15 y el estado de los incidentes. Todas las comunicaciones de casos y el seguimiento de trabajos o alertas se envían por correo electrónico y hacen referencia al número de caso de soporte técnico de 8 dígitos que se crea como un reflejo del caso de soporte abierto desde la consola de Intune.

## <a name="additional-resources"></a>Recursos adicionales  

- [Soporte de facturación y administración de suscripciones](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)
- [Licencias por volumen](https://go.microsoft.com/fwlink/p/?LinkID=282015)
- [Solución de problemas de Intune](help-desk-operators.md)
