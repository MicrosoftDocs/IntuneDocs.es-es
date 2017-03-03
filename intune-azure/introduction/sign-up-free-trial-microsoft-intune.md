---
title: "Suscríbase para disfrutar de una prueba gratuita de 30 días"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: cómo registrarse en Intune en Azure."
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 01/11/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 29b33341b136c8e8d76b666f94a9f620212944c5
ms.lasthandoff: 02/18/2017


---

# <a name="sign-up-for-a-microsoft-intune-free-trial-for-the-azure-portal-preview"></a>Registro para una evaluación gratuita de Microsoft Intune (versión preliminar del portal de Azure)

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Este artículo le guía por los pasos para registrarse en una versión de prueba de Intune independiente para la versión preliminar del portal de Azure. <!---and prepares your trial with some users so that you can then follow the associated evaluation guide to see how Intune manages mobile devices. ---> <!---or app data when devices are not enrolled in Intune.--->

<!--- ## Assumptions
This sign-up article and the evaluation guide assume you are using the trial for evaluation purposes only and intend to start with a clean environment when you subscribe.

To make it easy for you to get started with the trial, we are setting up a very simple environment that uses only Intune and assumes it will be your sole method of managing devices (known as the mobile device management authority). However, throughout the guide we will point you to deeper technical content if you want to explore farther.

You can do everything in the trial version that you can do in a subscription version; the only difference is you are limited to 100 user accounts in the trial.--->

<!--- ## Sign up for your trial--->
1. Visite la página [Registro de Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20) y rellene el formulario para suscribirse a una suscripción de prueba.

 <!--- If you have a work or school account and want to use that for your Intune trial, follow [these sign-in instructions](https://docs.microsoft.com/en-us/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-1) instead. However, this article assumes that you are not using such an account.---><br/> ![Imagen de la página de registro](./media/1-clicking-try.png)

 > [!TIP]
> Si la configuración regional de la mayoría de las operaciones de TI y de los usuarios es diferente a la suya, puede que quiera seleccionar esa configuración regional en **Where's your company located?** (¿Dónde se encuentra su empresa?).

2. Al final del proceso de registro, recibirá un mensaje con la información de la nueva cuenta. <br/> ![Imagen de la información de cuenta](./media/2-end-of-sign-up-process.png) <br/>En este punto, si hace clic en **You're ready to go** (Está listo para comenzar), llegará al Centro de administración de Office 365, donde puede agregar usuarios al entorno de prueba. <br/><br/>Sin embargo, si quiere ir directamente a la versión preliminar del portal de Azure, abra una nueva ventana de explorador y escriba **https://portal.azure.com** en la barra de direcciones. Irá a la página de inicio de sesión de Azure donde puede usar las credenciales que se le asignaron para iniciar sesión. Use esta dirección siempre que quiera iniciar sesión en la versión de prueba de Intune. <br/> ![Imagen de la página de inicio de sesión del portal Azure](./media/azure-portal-signin.png)

La primera vez que inicie sesión en la versión preliminar de Intune Azure, no verá Intune en el panel de Azure. Para agregar el servicio de Intune a su panel de Azure:
1. Elija **More services >** (Más servicios) en la lista de servicios de Azure situada a la izquierda del panel y escriba **Intune** en el cuadro de búsqueda.
2. Pulse **Intune** en la lista y seleccione la estrella para agregar el servicio a la lista de servicios.<br/> ![Imagen de la selección de Intune de la lista de servicios](./media/azure-add-intune1.png)
3. Pulse **Intune** en la lista de servicios para abrir el panel de Intune.

Si se registra en una versión de prueba, recibirá también un mensaje de correo electrónico con la información de la cuenta en la dirección que haya proporcionado durante el proceso de registro. Este mensaje confirma que la versión de prueba está activa.


<!--- ## Add users
Before you leave the Office 365 Admin center for Intune, you need to add some users to your trial account.

In the Office 365 Admin center, you can add users individually or in bulk by uploading a .csv file. We will do both to set up your trial. However, in your production environment, you will probably want to take advantage of your Azure Active Directory user accounts, which you can learn more about in our [Getting Started guide](https://docs.microsoft.com/en-us/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3) and in the [Next steps](#Next-steps) section of this article.

### Add an individual user
1. Choose either of the options to add a use to open a form that allows you to create a user. Only the items starred with an asterisk (\*) are required.
![Image of add user button options](./media/sign-up/add-user.png)


2.  When you add the user, the final step will be to send the user an email with their temporary Intune password. For the purposes of this evaluation, use your own work email address so you will receive the log-on information and see the email your users will get. You can then use these user identities to enroll test devices.<br/>

 ![Image of add user final step](./media/sign-up/new-user-2.png)

3. If you want to assign a user an admin role after you create it, you can edit the role in the Office 365 Admin center by selecting the user name from your list of users, and then choosing **Edit** in the Role line to see the list of user roles you can select from and assign to that user.

 ![Image of user  role options](./media/sign-up/change-user-role.png)

### Import multiple users
1. You will find the wizard for importing multiple users in the **More** list.

 ![Image of option to add multiple users](./media/sign-up/add-multiple-users.png)

2. To help you set up your .csv file correctly, you can download a template file to populate with your user data. Download the .csv file that contains headers and sample user information to see exactly the kind of data is needed for each field.

 ![Image of first step in bulk enrollment wizard](./media/sign-up/bulk-enroll-step-1.png)


3. After you’ve created and saved your .csv file, choose **Browse** to select the file. Verify, and choose **Next**. Your users will be uploaded and added to your list of active users.

> [!NOTE]
> Your users won't show up in Intune until they've enrolled a device to be managed.

Now it’s time to head over to Intune to start managing your users, their devices, and their apps.--->

## <a name="keeping-the-admin-experiences-straight"></a>Mantener en orden las experiencias de administración
<!---### Classic Intune
There are two portals you will use for classic Intune:
- The Office 365 Admin center ([portal.office.com](https://portal.office.com))
- The Intune administration console ([manage.microsoft.com](https://manage.microsoft.com))

Normally, you’ll do your work in the Intune administration console, shown below. This is the site where you set up and manage your groups, policies, devices, and apps.

![Image of Intune administration console](./media/sign-up/intune-admin-console.png)

However, you will use the Office 365 Admin center, shown below, to add and manage your users and other aspects of your account, including billing and support.

![Image of Office 365 Admin center](./media/sign-up/office-admin-center.png)

You can navigate from the Office 365 Admin center to the Intune admin console. The admin centers are under the last item in the left navigation pane. Choose **Intune** to open the Intune admin console in a new tab.

![Image of link to Intune administration console](./media/sign-up/link-to-intune.png)

To get from Intune back to the Office 365 Admin center, choose the **Add Users** task on the Groups Overview page.

![Image of link back to Office 365  Admin center](./media/sign-up/task-add-users.png)--->

<!---### Intune Azure preview--->
Existen tres portales que usará para la versión preliminar de Azure de Intune:
- El panel de Intune en Azure ([portal.azure.com](https://portal.azure.com)) donde puede explorar el [funcionalidades de Intune en el portal de Azure](what-is-microsoft-intune.md).
- El Centro de administración de Office 365 ([portal.office.com](https://portal.office.com)) donde puede agregar y administrar usuarios si no usa Azure Active Directory para esa tarea. También puede administrar otros aspectos de su cuenta, como la facturación y el soporte técnico.
- La consola de administración clásica de Intune ([manage.microsoft.com](https://manage.microsoft.com)) donde puede explorar características que todavía no se han agregado a Azure.

Normalmente, realizará su trabajo en el panel de Intune que se muestra a continuación. Este es el sitio donde configurar y administrar grupos, directivas, dispositivos y aplicaciones.

Puede ir a la consola de administración de Intune clásico desde el panel pulsando el icono **Abrir el portal clásico de Intune**.

Para volver a la versión preliminar de Azure de Intune, escriba https://portal.azure.com en la barra de direcciones del explorador y, después, pulse **Intune** de nuevo en la lista de servicios.

 ![Imagen del panel de Intune](./media/intune-azure-dashboard.png)


Sin embargo, usará el centro de administración de Office 365, que aparece a continuación, para agregar y administrar los usuarios y otros aspectos de su cuenta, incluida la facturación y el soporte técnico.

![Imagen del centro de administración de Office 365](./media/office-admin-center.png)

Para ir desde el Centro de administración de Office 365 al panel de Intune, escriba https://portal.azure.com en la barra de direcciones del explorador. Pulse **Intune** en la lista de servicios.

Para ir de Intune al Centro de administración de Office 365 de nuevo, escriba https://portal.office.com en la barra de direcciones del explorador. Si ya ha iniciado sesión en Intune, se le dirigirá directamente al Centro de administración de Office 365.

## <a name="next-steps"></a>Pasos siguientes

### <a name="intune-azure-preview"></a>Versión preliminar de Azure de Intune
Más información sobre [Intune en la versión preliminar de Azure Portal](what-is-microsoft-intune.md)
### <a name="classic-intune"></a>Intune clásico
Escenario de evaluación: [Evaluar la administración de dispositivos móviles en Microsoft Intune](https://docs.microsoft.com/intune/understand-explore/mobile-device-management-trial-guide-microsoft-intune)

### <a name="integration-with-other-products"></a>Integración con otros productos
Obtenga más información sobre el uso de las cuentas de usuario de Azure Active Directory con Intune:
- [¿Requisitos de identidad?](https://docs.microsoft.com/en-us/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)
- [Requisitos de sincronización de directorios](https://docs.microsoft.com/en-us/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)
- [Requisitos de Multi-factor Authentication:](https://docs.microsoft.com/en-us/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)

Obtenga más información sobre [Intune con System Center Configuration Manager](https://docs.microsoft.com/en-us/sccm/mdm/understand/hybrid-mobile-device-management)

