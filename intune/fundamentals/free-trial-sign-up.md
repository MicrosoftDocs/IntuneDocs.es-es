---
title: 'Inicio rápido: Prueba gratuita de Microsoft Intune'
titleSuffix: ''
description: En este tutorial creará una suscripción de prueba gratuita, conocerá cuáles son las configuraciones admitidas y los requisitos de red y, opcionalmente, configurará un nombre de dominio.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b1264f5113ded280ed9d5cb9b9d4ece8e0187fe7
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502869"
---
# <a name="quickstart-try-microsoft-intune-for-free"></a>Inicio rápido: Prueba gratuita de Microsoft Intune

Microsoft Intune permite administrar los dispositivos y las aplicaciones para proteger los datos corporativos de los recursos. En este tutorial de inicio rápido, creará una suscripción gratuita para probar Intune en un entorno de prueba.

Intune proporciona administración de dispositivos móviles (MDM) y administración de aplicaciones móviles (MAM) desde un servicio seguro basado en la nube que se administra mediante Microsoft Azure Portal. Con Intune, se asegura de que los recursos corporativos de los empleados (datos, dispositivos y aplicaciones) están configurados correctamente y actualizados, se puede acceder a ellos y satisfacen las directivas de cumplimiento y los requisitos de su compañía.

## <a name="prerequisites"></a>Requisitos previos
Antes de configurar Microsoft Intune, revise los siguientes requisitos:

- [Exploradores y sistemas operativos compatibles](supported-devices-browsers.md)
- [Ancho de banda y requisitos de configuración de red de Intune](network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Suscríbase para disfrutar de una prueba gratuita de Microsoft Intune

Probar Intune es gratis durante 30 días. Si ya dispone de una cuenta profesional o educativa, **inicie sesión** con dicha cuenta y agregue Intune a su suscripción. En caso contrario, puede **registrarse** para obtener una nueva cuenta y usar Intune para su organización.

> [!IMPORTANT]
> No puede combinar una cuenta profesional o educativa existente después de registrarse con una cuenta nueva.

1. Vaya a la página de [prueba de Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2019088) y rellene el formulario.

    ![Captura de pantalla de la página web de registro de una cuenta de prueba de Microsoft Intune](./media/free-trial-sign-up/account-sign-up-site-full-browser.png)

    Si la configuración regional de la mayoría de las operaciones de TI y de los usuarios es diferente a la suya, puede que quiera seleccionar esa configuración regional en **País o región**. Azure usa la información regional para ofrecer los servicios adecuados. Puede modificar esta configuración posteriormente.

2. Cree una cuenta con el nombre de su compañía seguido de **.onmicrosoft.com**. 

    ![Captura de pantalla del nuevo proceso de credenciales de la cuenta de prueba de Intune](./media/free-trial-sign-up/account-sign-up-site-user-id.png)

    Si quiere usar el dominio personalizado de su organización sin **.onmicrosoft.com**, puede cambiarlo en el Centro de administración de Microsoft 365, tal como se describe más adelante en este artículo.

3. Al final del proceso de registro puede ver la información de la cuenta nueva.

    ![Imagen de la información de la cuenta](./media/free-trial-sign-up/intune-end-of-sign-up-process.png) 

## <a name="sign-in-to-the-azure-portal"></a>Iniciar sesión en Azure Portal

1. Abra una nueva ventana del explorador y escriba **https://portal.azure.com** en la barra de direcciones. 
2. Inicie sesión con las credenciales que se le concedieron en los pasos anteriores.

    ![Imagen de la página de inicio de sesión de Azure Portal](./media/free-trial-sign-up/azure-portal-signin.png)

3. Para ver Microsoft Intune en Azure Portal, seleccione **Todos los servicios** en la barra lateral de lado izquierdo de la página.
4. Busque **Microsoft Intune** en el cuadro de filtro y selecciónelo.
5. Seleccione la **estrella** para agregar Intune a la parte inferior de la lista de sus servicios favoritos y abra el panel de Intune.

Si se registra en una versión de prueba, recibirá también un mensaje de correo electrónico con la información de la cuenta en la dirección que haya proporcionado durante el proceso de registro. Este mensaje confirma que la versión de prueba está activa.

> [!TIP]
> Al trabajar con Azure Portal, puede que obtenga mejores resultados si trabaja con un explorador en modo normal en lugar de en modo privado.

## <a name="set-the-mdm-authority-to-intune"></a>Establecer la entidad de MDM en Intune

Después de iniciar sesión en Azure Portal y seleccionar Intune, puede ver un banner naranja que indica que aún no ha establecido la entidad de MDM. La configuración de la entidad de administración de dispositivos móviles (MDM) determina cómo se administran los dispositivos. La entidad de MDM debe establecerse antes de que los usuarios puedan inscribir dispositivos para la administración.

Para establecer la entidad de MDM en Intune, siga estos pasos.

1. Abra una nueva ventana del explorador y escriba **https://portal.azure.com** en la barra de direcciones. 
2. Elija **Todos los servicios** > **Microsoft Intune**.
3. Seleccione el banner que indica que no ha habilitado la administración de dispositivos o, si no ve el banner de inmediato, seleccione **Inscripción de dispositivos**. Se mostrará la hoja **Elegir entidad de MDM** si aún no ha habilitado la administración de dispositivos.

    > [!NOTE]
    > Si ha establecido la entidad de MDM, verá el valor de dicha entidad en la hoja **Inscripción de dispositivos**. El banner naranja aparece únicamente si aún no ha establecido la entidad de MDM. 

    ![Imagen de la hoja Elegir entidad de MDM](./media/free-trial-sign-up/choose-mdm-authority.png) 

4. Si esa entidad no se ha establecido, en **Elegir entidad de MDM**, establézcala en **Entidad de MDM de Intune**.

Para obtener más información sobre la entidad de MDM, vea [Establecer la entidad de administración de dispositivos móviles](mdm-authority-set.md).

## <a name="configure-your-custom-domain-name-optional"></a>Configurar el nombre de dominio personalizado (opcional)

Tal como se mencionó anteriormente, si quiere usar el dominio personalizado de su organización sin **.onmicrosoft.com**, puede cambiarlo en el Centro de administración de Microsoft 365. Puede agregar, comprobar y configurar un nombre de dominio personalizado siguiendo los pasos que se indican a continuación.  

> [!IMPORTANT]
> No es posible cambiar la parte del nombre de dominio **onmicrosoft.com** *inicial*, ni tampoco quitarla. Sin embargo, se puede agregar, comprobar o quitar los nombres de dominio *personalizado* usados en Intune para identificar claramente su negocio. Para obtener más información, vea [Configuración de un nombre de dominio personalizado](custom-domain-name-configure.md).

1. Vaya al [Centro de administración de Microsoft 365](https://admin.microsoft.com) e inicie sesión con su cuenta de administrador.

2. En el panel de navegación, seleccione **Configuración** > **Dominios** > **Agregar dominio**.

3. Escriba su nombre de dominio personalizado. A continuación, seleccione **Siguiente**.

   ![Captura de pantalla del Centro de administración de Microsoft 365: Agregar dominio](./media/free-trial-sign-up/domain-custom-add.png)

4. Compruebe que es el propietario del dominio que escribió en el paso anterior. 
    
    Si selecciona **enviar el código por correo electrónico**, recibirá un correo electrónico en la dirección de contacto registrada para el dominio. Después de recibir el correo electrónico, copie el código e introdúzcalo en el campo **Escriba aquí su código de verificación**. Si el código de verificación es correcto, el dominio se agregará a su inquilino. El correo electrónico que se muestra puede no resultarle familiar. Algunos registradores ocultan la dirección de correo electrónico real. Además, puede que la dirección de correo electrónico sea distinta de la que se proporcionó cuando se registró el dominio.

   ![Captura de pantalla del Centro de administración de Microsoft 365: Verificar dominio](./media/free-trial-sign-up/domain-custom-verify.png)

   > [!NOTE]
   > Para obtener detalles de la comprobación de registros TXT, consulte [Crear registros DNS en cualquier proveedor de hospedaje DNS para Office 365](https://support.office.com/article/Create-DNS-records-at-any-DNS-hosting-provider-for-Office-365-7B7B075D-79F9-4E37-8A9E-FB60C1D95166).

## <a name="admin-experiences"></a>Experiencias del administrador

Puede usar dos portales:
- El panel de Intune en Azure ([portal.azure.com](https://portal.azure.com)) es donde puede explorar las [funcionalidades de Intune](what-is-intune.md). Normalmente, realizará su trabajo en el panel de Intune.
- El Centro de administración de Microsoft 365 ([admin.microsoft.com](https://admin.microsoft.com)) es donde puede agregar y administrar usuarios si no usa Azure Active Directory para esta tarea. También puede administrar otros aspectos de su cuenta, como la facturación y el soporte técnico.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial de inicio rápido ha creado una suscripción gratuita para probar Intune en un entorno de prueba. Para obtener más información sobre cómo configurar Intune, vea [Configurar Intune](setup-steps.md).

Para seguir esta serie de tutoriales de inicio rápido de Intune, pase al siguiente tutorial de inicio rápido.

> [!div class="nextstepaction"]
> [Inicio rápido: Crear un usuario y asignarle una licencia](quickstart-create-user.md)
