---
title: "Registrarse para obtener una prueba gratuita de 30 días de Microsoft Intune | Microsoft Docs"
description: "Regístrese y configure una evaluación gratuita de 30 días de Microsoft Intune."
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 11/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 619a1d11-3d22-4635-8f70-770eba3e1712
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 560765fa9d9afa4a1050515e1b2304c998f8c158
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Suscríbase para disfrutar de una prueba gratuita de Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Este artículo le guiará a través de una suscripción para una evaluación de Intune y prepara la versión de prueba con algunos usuarios de modo que puede seguir la guía de evaluación asociada para ver cómo Intune administra los dispositivos móviles. <!---or app data when devices are not enrolled in Intune.--->

>[!Note]
> A partir de diciembre de 2016, Microsoft Intune se traslada a Azure Portal, y algunas suscripciones de prueba gratuitas estarán en Intune en Azure Portal y otras estarán en Intune clásico. Si su versión de prueba está en Azure Portal, encontrará más útil el [contenido de la versión preliminar de Azure de Intune](/intune/what-is--intune) después de completar los pasos de este artículo.

## <a name="assumptions"></a>Suposiciones
Este artículo de suscripción y la guía de evaluación presuponen que está utilizando la versión de prueba solo con fines de evaluación y va a comenzar con un entorno limpio al suscribirse.

Para facilitar la introducción a la versión de prueba, estamos configurando un entorno muy simple que usa solo Intune y presupone que será el único método de administración de dispositivos (conocido como la entidad de administración de dispositivos móviles). Sin embargo, a lo largo de la guía se indicará contenido técnico más profundo si desea explorar más adelante.

Puede hacer todo en el contenido de la versión de prueba que pueda hacer en una versión de suscripción; la única diferencia es que está limitado a 100 cuentas de usuario en la versión de prueba.

## <a name="sign-up-for-your-trial"></a>Regístrese para obtener la versión de prueba
Visite la página [Registro de Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20) y rellene el formulario para suscribirse a una suscripción de prueba.

Si tiene una cuenta profesional o educativa y desea usarla para la versión de prueba de Intune, siga [estas instrucciones de inicio de sesión](/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-1) en su lugar. Sin embargo, este artículo y las guías de evaluación suponen que no utiliza este tipo de cuenta.

> [!TIP]
> Si la mayoría de sus operaciones de TI y los usuarios están en una configuración regional diferente a usted, puede establecer esa configuración regional de la versión para probar el rendimiento.

### <a name="post-sign-up-considerations"></a>Consideraciones posteriores al registro
Si se registra para obtener una versión de prueba, recibirá un mensaje de correo electrónico con la información de la cuenta en la dirección de correo electrónico que haya proporcionado durante el proceso de suscripción. Este mensaje confirma que la versión de prueba está activa.

Después de completar el proceso de registro, se le dirigirá a una página que se usa para agregar usuarios y asignarles licencias a través del centro de administración de Office 365. La próxima vez que inicie sesión en **Intune clásico** (https://manage.microsoft.com), irá automáticamente a la consola de administración de Intune.

Si su versión de prueba está en **Azure Portal**, vaya a https://portal.azure.com e inicie sesión con sus credenciales de prueba de Intune.

## <a name="add-users"></a>Agregar usuarios
Antes de abandonar el centro de administración de Office 365 para Intune, debe agregar algunos usuarios a su cuenta de prueba.

En el centro de administración de Office 365, puede agregar los usuarios individualmente o de forma masiva cargando un archivo .csv. Haremos ambas tareas para configurar la versión de prueba. Sin embargo, en el entorno de producción, probablemente deseará aprovechar las ventajas de las cuentas de usuario de Azure Active Directory, puede obtener más información en nuestra [Guía de inicio](/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3) y, en la sección [Pasos siguientes](#Next-steps) de este artículo.

### <a name="add-an-individual-user"></a>Adición de un usuario individual
1. Elija cualquiera de las opciones para agregar un uso y abrir un formulario que le permita crear un usuario. Solo los elementos marcados con un asterisco (\*) son obligatorios.
![Imagen de las opciones del botón para agregar usuario](./media/sign-up/add-user.png)


2.  Al agregar el usuario, el paso final será enviar al usuario un correo electrónico con su contraseña de Intune temporal. Para fines de esta evaluación, use su propia dirección de correo electrónico del trabajo, por lo que recibirá la información de inicio de sesión y verá el correo electrónico que recibirán los usuarios. A continuación, puede utilizar estas identidades de usuario para inscribir los dispositivos de prueba.<br/>

 ![Imagen del paso final para agregar usuario](./media/sign-up/new-user-2.png)

3. Si desea asignar un rol de administrador a un usuario después de crearlo, puede editar el rol en el centro de administración de Office 365 seleccionando el nombre de usuario de la lista de usuarios y eligiendo **Editar** en la línea de rol para ver la lista de roles de usuario seleccionables y asignar uno a ese usuario.

 ![Imagen de las opciones del rol de usuario](./media/sign-up/change-user-role.png)

### <a name="import-multiple-users"></a>Importar varios usuarios
1. Encontrará el asistente para importar varios usuarios en la lista **Más**.

 ![Imagen de la opción para agregar varios usuarios](./media/sign-up/add-multiple-users.png)

2. Para ayudarle a configurar correctamente el archivo .csv, puede descargar un archivo de plantilla que se rellenará con los datos de usuario. Descargue el archivo .csv que contiene los encabezados e información de usuario de ejemplo para ver exactamente el tipo de datos para cada campo.

 ![Imagen del primer paso del asistente para la inscripción masiva](./media/sign-up/bulk-enroll-step-1.png)


3. Una vez que haya creado y guardado el archivo .csv, elija **Examinar** para seleccionar el archivo. Compruebe y elija **Siguiente**. Los usuarios se cargarán y agregarán a la lista de usuarios activos.

> [!NOTE]
> Los usuarios no se mostrarán en Intune hasta que hayan inscrito un dispositivo para administrarlos.

Ahora es el momento de dirigirse a Intune para empezar a administrar los usuarios, sus dispositivos y sus aplicaciones.

## <a name="keeping-the-admin-experiences-straight"></a>Mantener en orden las experiencias de administración
### <a name="classic-intune"></a>Intune clásico
Existen dos portales que usará en Intune clásico:
- El Centro de administración de Office 365 ([portal.office.com](https://portal.office.com))
- La consola de administración de Intune ([manage.microsoft.com](https://manage.microsoft.com))

Normalmente, llevará a cabo su trabajo en la consola de administración de Intune que se muestra a continuación. Este es el sitio donde configurar y administrar grupos, directivas, dispositivos y aplicaciones.

![Imagen de la consola de administración de Intune](./media/sign-up/intune-admin-console.png)

Sin embargo, usará el centro de administración de Office 365, que aparece a continuación, para agregar y administrar los usuarios y otros aspectos de su cuenta, incluida la facturación y el soporte técnico.

![Imagen del centro de administración de Office 365](./media/sign-up/office-admin-center.png)

Puede navegar desde el centro de administración de Office 365 a la consola de administración de Intune. Los centros de administración están en el último elemento en el panel de navegación izquierdo. Elija **Intune** para abrir la consola de administración de Intune en una nueva ficha.

![Imagen del vínculo a la consola de administración de Intune](./media/sign-up/link-to-intune.png)

Para volver de Intune al centro de administración de Office 365, elija la tarea **Agregar usuarios** en la página de información general de grupos.

![Imagen del vínculo de vuelta al centro de administración de Office 365](./media/sign-up/task-add-users.png)

### <a name="intune-azure-preview"></a>Versión preliminar de Azure de Intune
Existen tres portales que usará para la versión preliminar de Azure de Intune:
- El Centro de administración de Office 365 ([portal.office.com](https://portal.office.com))
- El panel de Intune en Azure ([portal.azure.com](https://portal.azure.com))
- La consola de administración de Intune clásico ([manage.microsoft.com](https://manage.microsoft.com))

La primera vez que inicie sesión en Intune en Azure, puede que no lo vea en su panel de Azure. Para agregar el servicio de Intune a su panel de Azure:
1. Pulse **Más servicios >** en la lista de servicios de Azure situada a la izquierda del panel y escriba Intune en el cuadro de búsqueda.
2. Pulse **Intune** en la lista y seleccione la estrella para agregar el servicio a la lista de servicios.<br/> ![Imagen de la selección de Intune de la lista de servicios](./media/sign-up/azure-add-intune1.png)
3. Pulse **Intune** en la lista de servicios para abrir el panel de Intune.

Normalmente, realizará su trabajo en el panel de Intune que se muestra a continuación. Este es el sitio donde configurar y administrar grupos, directivas, dispositivos y aplicaciones. Puede ir a la consola de administración de Intune clásico desde el panel pulsando el icono **Abrir el portal clásico de Intune**. Para volver a la versión preliminar de Azure de Intune, escriba https://portal.azure.com en la barra de direcciones del explorador y, después, pulse **Intune** de nuevo en la lista de servicios.

 ![Imagen del panel de Intune](./media/sign-up/intune-azure-dashboard.png)


Sin embargo, usará el centro de administración de Office 365, que aparece a continuación, para agregar y administrar los usuarios y otros aspectos de su cuenta, incluida la facturación y el soporte técnico.

![Imagen del centro de administración de Office 365](./media/sign-up/office-admin-center.png)

Para ir desde el Centro de administración de Office 365 al panel de Intune, escriba https://portal.azure.com en la barra de direcciones del explorador. Pulse **Intune** en la lista de servicios.

Para ir de Intune al Centro de administración de Office 365 de nuevo, escriba https://portal.office.com en la barra de direcciones del explorador. Si ya ha iniciado sesión en Intune, se le dirigirá directamente al Centro de administración de Office 365.

## <a name="next-steps"></a>Pasos siguientes
### <a name="classic-intune"></a>Intune clásico
Escenario de evaluación: [Evaluar la administración de dispositivos móviles en Microsoft Intune](mobile-device-management-trial-guide-microsoft-intune.md)

### <a name="intune-azure-preview"></a>Versión preliminar de Azure de Intune
Más información sobre [Intune en la versión preliminar de Azure Portal](/intune/what-is-intune)

### <a name="integration-with-other-products"></a>Integración con otros productos
Obtenga más información sobre el uso de las cuentas de usuario de Azure Active Directory con Intune:
- [¿Requisitos de identidad?](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)
- [Requisitos de sincronización de directorios](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)
- [Requisitos de Multi-factor Authentication:](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)

Obtenga más información sobre [Intune con System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/understand/hybrid-mobile-device-management)

