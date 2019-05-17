---
title: Cómo obtener asistencia para Microsoft Intune
titleSuffix: Microsoft Intune
description: Obtenga soporte técnico en línea y telefónico para las suscripciones de prueba y de pago de Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/05/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7fc95d17-098e-4da5-8a09-a96476569dd9
ms.reviewer: cacamp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: cf1e87d40459d194f2c4aa0ff702a137e45504ab
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "59569758"
---
# <a name="how-to-get-support-for-microsoft-intune"></a>Cómo obtener asistencia para Microsoft Intune

[!INCLUDE [azure_portal](./includes/note-for-both-portals.md)]

Microsoft proporciona servicios globales de soporte técnico, preventa, facturación y suscripción para Microsoft Intune. El soporte técnico está disponible tanto en línea como por teléfono para las suscripciones de pago y de prueba. El soporte técnico en línea está disponible en inglés y japonés. La asistencia telefónica y la asistencia de facturación en línea están disponibles en idiomas adicionales.

Como administrador de Intune, puede usar la opción **Ayuda y soporte técnico** para registrar una incidencia de soporte técnico en línea sobre Intune desde Azure Portal. Para crear y administrar un incidente de soporte técnico, su cuenta debe tener asignado un rol de Azure Active Directory (Azure AD) que incluya la *acción* **microsoft.office365.supportTickets/allEntities/allTasks**. Para información sobre los permisos y roles de Azure AD que se necesitan para crear una incidencia de soporte técnico, consulte el artículo sobre los [roles de administrador en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal). 

**Problemas conocidos para crear incidentes de soporte técnico**

Si la cuenta tiene los permisos necesarios pero no puede acceder correctamente a Ayuda y soporte técnico ni tampoco crear ni administrar un incidente de soporte técnico, revise estos problemas conocidos y sus soluciones:  
- El token de usuario está obsoleto para la cuenta. Para resolver este problema, cierre sesión en todas las sesiones activas de la consola, vuelva a iniciar sesión e intente crear o administrar un incidente de soporte técnico. 
- Varias sesiones activas. Si inició sesión con más de un usuario o sesión, cierre la sesión en todas las consolas, menos en una. Luego, con una sola sesión activa, intente crear o administrar un incidente de soporte técnico.

Otras acciones que podrían ser necesarios para resolver los problemas de acceso:
- Borre todas las cookies de la sesión activa del explorador y vuelva a intentar crear o administrar un incidente de soporte técnico.
- Use una sesión de exploración InPrivate para iniciar sesión en Intune e intente crear o administrar un incidente de soporte técnico.  

Si las soluciones anteriores no funcionan, vay al [Centro de administración de Microsoft 365](https://admin.microsoft.com) y cree desde ahí una incidencia de soporte técnico. En estos momentos estamos trabajando en una corrección que estará disponible a finales del verano. 



>[!IMPORTANT]  
> Para obtener soporte técnico para productos de terceros que funcionan con Intune (por ejemplo, Saaswedo, Cisco o Lookout), póngase en contacto con el proveedor de ese producto en primer lugar. Asegúrese de que ha configurado el otro producto correctamente antes de abrir una solicitud con el soporte técnico de Intune.
>
> Para obtener información sobre cómo solucionar problemas relacionados con Microsoft Intune, consulte la [sección de solución de problemas](help-desk-operators.md) de la documentación de Intune.




## <a name="help-and-support-experience"></a>Experiencia de ayuda y soporte técnico
> [!TIP]   
> Una nueva experiencia de ayuda y soporte técnico está disponible para todos los inquilinos. Si no ve esta nueva experiencia en el inquilino, borrar la memoria caché del explorador y recargue la página.

La experiencia de ayuda y soporte técnico de Intune está disponible en el [portal de administración de dispositivos de Microsoft 365](http://devicemanagement.microsoft.com) y en todas las hojas (o páginas) en Intune, en Azure Portal. 

![Hojas de Intune](./media/get-support/intune-blades.png)


Esta nueva experiencia es similar a la observada en el [centro de administración de Microsoft 365](https://admin.microsoft.com/) y reemplaza a la experiencia anterior de Ayuda y soporte técnico. 

Para acceder a Ayuda y soporte técnico, use estas opciones:  
- **Panel de administración de dispositivos**:
   - Seleccione cualquier opción disponible de **Ayuda y soporte técnico**
   - Seleccione el icono **?** de la esquina superior derecha del portal

- **En Azure Portal:**
   - Seleccione **Ayuda y soporte técnico** desde cualquier hoja o página de Intune

   Al seleccionar el icono **?** de la esquina superior derecha o **Ayuda y soporte técnico** en el panel de navegación izquierdo desde cualquier ubicación de Azure Portal se abre *Ayuda y soporte técnico* para Azure. Para obtener la mejor experiencia posible, use *Ayuda y soporte técnico* desde la hoja de Intune.  

Con la nueva experiencia, se obtiene acceso a la vista **¿Necesita ayuda?**, como se ve en la siguiente imagen del panel de administración de dispositivos:  
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
En la página **¿Necesita ayuda?**, seleccione la opción que quiere usar.  

- Para una solicitud por correo electrónico, indique su dirección de correo y, opcionalmente, puede agregar datos adjuntos al envío. Seleccione **Enviar** para abrir la solicitud.  

  ![Solicitud por correo electrónico](./media/get-support/email-support.png)
  
- Para una solicitud por teléfono, indique su número de teléfono. Si quiere, puede incluir su dirección de correo electrónico y agregar datos adjuntos al envío. Seleccione Llamarme para enviar la solicitud.  

   ![Solicitud por teléfono](./media/get-support/phone-support.png)

### <a name="view-support-cases"></a>Consulta de casos de soporte técnico
Seleccione el botón del historial para ver los incidentes de soporte técnico que ha creado.  

![Consulta de casos de soporte técnico](./media/get-support/view-support-tickets.png)

- Solo los casos de soporte técnico que se abren mediante el nuevo flujo de trabajo son visibles desde este flujo de trabajo. Para verlos, use la vista Ayuda y soporte técnico desde la consola de administración de dispositivos o desde una hoja de Intune en Azure Portal. Estos casos tienen números de ocho dígitos. También puede ver estos casos desde el centro de administración de Microsoft 365.  

- Los casos abiertos sin usar la experiencia de ayuda y soporte técnico de Intune no se modifican. Para verlos, debe usar una vista Ayuda y soporte técnico que no forme parte de la experiencia de Intune, o el panel de administración de dispositivos. Estos casos tienen números que empiezan por **117** o **118** y tienen 15 dígitos. Para verlos:

    1. Inicie sesión en Azure (<https://portal.azure.com>) con sus credenciales de administrador de Intune y haga clic en el icono *?* situado en la esquina superior derecha del portal y, después, seleccione *Ayuda y soporte técnico* para ir a la página [Ayuda y soporte técnico de Azure](https://ms.portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

    2. En la página **Ayuda y soporte técnico** puede ver la lista **Solicitudes de soporte técnico recientes** y seleccionarlas para ver detalles adicionales.


## <a name="azure-help--support-experience"></a>Experiencia de ayuda y soporte técnico de Azure
La siguiente información describe la experiencia de ayuda y soporte técnico de Azure que sigue siendo accesible desde Azure Portal cuando se usa el panel de navegación izquierdo **Ayuda y soporte técnico**, o se usa la opción **?** de la esquina superior derecha de Azure Portal. A partir de enero de 2019, no se puede acceder a la experiencia *Ayuda y soporte técnico* de Azure desde *Ayuda y soporte técnico* disponible en las hojas de Intune.  

### <a name="create-an-online-support-ticket"></a>Creación de un vale de soporte en línea

1. Inicie sesión en Azure Portal (<https://portal.azure.com>) con sus credenciales de administrador de Intune y haga clic en el icono **?** situado en la esquina superior derecha del portal y, después, seleccione **Ayuda y soporte técnico** para ir a la página [Ayuda y soporte técnico de Azure](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

   ![Imagen del vínculo del signo de interrogación con el vínculo de Ayuda y soporte técnico resaltado](./media/azure-get-support.png)

2. En la página **Ayuda y soporte técnico** de Azure, seleccione **Nueva solicitud de soporte técnico**.

   ![Imagen del vínculo de Nueva solicitud de soporte técnico resaltado en la página de soporte y ayuda](media/azure-support-ticket-link.png)

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

<!--
  - **Support plan**: **Technical support - included** (for Intune technical issues, support is complimentary) or **Premier**
     >[!IMPORTANT]
     >- If you are a **Premier customer** and don't see **Support plan: Premier**, contact your Technical Account Manager for help linking your contract and tenant.
     >- Support for Intune, and for Intune when used with Configuration Manager, is free of charge. To review details of the Premier Support offering, see the [Description of Services](https://enterprise.microsoft.com/en-us/services/services-list/) documentation, section 5.3.3 "Advisory Services."

4. On the **Problem** blade, to make sure your request is addressed by the right subject matter expert for your problem, select the following options:

   - **Severity**
   - **Problem type**
   - **Category**

     These details also let us provide **Related help** that might solve your problem without filing a ticket.

     ![Screenshot of Azure portal help and support page with Problem items filled out and displaying solutions based on your problem](./media/support-need-solutions.png)

     To help the support team research and resolve your problem, enter the following information:
    
   - **Details**
   - **Date**
   - **Time**
   - **Supplemental data**

   Choose **Next**.

5. Provide **Contact information** for this support request. Microsoft support uses this information to contact you.
6. Choose **Create** to submit your support request.
-->
>[!IMPORTANT]
>Si tiene una pregunta sobre suscripciones o facturación, puede abrir un caso para obtener asistencia mediante el [Centro de administración de Microsoft 365](https://admin.microsoft.com/Support/SupportEntry.aspx).

### <a name="view-support-requests"></a>Ver las solicitudes de soporte técnico
Puede ver una solicitud de soporte técnico desde Azure Portal. Para ello:

1. Inicie sesión en Azure (<https://portal.azure.com>) con sus credenciales de administrador de Intune y haga clic en el icono **?** situado en la esquina superior derecha del portal y, después, seleccione **Ayuda y soporte técnico** para ir a la página [Ayuda y soporte técnico de Azure](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

2. En la página **Ayuda y soporte técnico** puede ver la lista **Solicitudes de soporte técnico recientes** y seleccionarlas para ver detalles adicionales.

## <a name="additional-resources"></a>Recursos adicionales
- [Soporte de facturación y administración de suscripciones](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)
- [Licencias por volumen](https://go.microsoft.com/fwlink/p/?LinkID=282015)
- [Solución de problemas de Intune](help-desk-operators.md)
