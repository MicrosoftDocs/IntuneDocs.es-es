---
title: Configurar un nombre de dominio personalizado | Microsoft Intune
description: "Agregue un nombre de dominio personalizado para su suscripción de Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 29b6e5a3d319c741482fcc2b600842e2e42b96e2
ms.openlocfilehash: 9fe78bca15ffee1e5e0e7e3758ff70b6bc92b619


---


# <a name="configure-a-custom-domain-name"></a>Configuración de un nombre de dominio personalizado

Cuando su organización se registra en un servicio en la nube de Microsoft como es Intune, se le asigna un nombre de dominio inicial hospedado en Azure Active Directory (AD) que es similar al siguiente: **sudominio.onmicrosoft.com**. En este ejemplo, **sudominio** es el nombre de dominio que eligió al suscribirse y **onmicrosoft.com** es el sufijo asignado a las cuentas que agregue a su suscripción. Si su organización posee un dominio personalizado, puede configurar la instancia de Intune para que use ese dominio en lugar del nombre de dominio proporcionado con la suscripción.

Le recomendamos encarecidamente que, antes de crear nuevas cuentas de usuario o de sincronizar su instancia de Active Directory local, decida si va a usar únicamente el dominio .onmicrosoft.com o si va a agregar uno o más nombres de dominio personalizados. Configurar un dominio personalizado antes de agregar usuarios puede ayudar a simplificar la administración de las identidades de usuario para la suscripción, ya que permite a los usuarios iniciar sesión con las credenciales que usan para acceder a otros recursos del dominio.

Al suscribirse a un servicio basado en la nube de Microsoft, la instancia de ese servicio se convierte en un [inquilino de Microsoft Azure AD](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant), que proporciona servicios de identidad y directorio al servicio basado en la nube. Además, como las tareas de configuración de Intune para que use el nombre de dominio personalizado de las organizaciones son las mismas que para otros inquilinos de Azure AD, puede usar la información y los procedimientos que se describen en [Agregar el dominio](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

> [!TIP]
> Para más información sobre el uso de un dominio personalizado con un servicio basado en la nube de Microsoft, consulte [Información general conceptual de nombres de dominio personalizado en Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/).

No puede cambiar el nombre o quitar ese nombre de dominio inicial. Sin embargo, puede agregar, comprobar o quitar sus propios nombres de dominio personalizados para usarlos con Intune, que es útil si quiere mantener la identidad de su negocio.

## <a name="to-add-and-verify-your-custom-domain"></a>Para agregar y comprobar el dominio personalizado

1. Vaya al [Portal de administración de Office 365](https://portal.office.com/Admin/Default.aspx) e inicie sesión en la cuenta del administrador.

2. En el panel de navegación, elija **Configuración** &gt; **Dominios**.

3. Elija **Agregar dominio** y escriba el nombre de su dominio personalizado.

4. El cuadro de diálogo **Comprobar dominio** se abre proporcionándole los valores para crear el registro TXT en su proveedor de host DNS.
    - **Usuarios de GoDaddy**: el Portal de administración de Office 365 le redirige a la página de inicio de sesión de GoDaddy. El registro TXT se crea automáticamente después de escribir sus credenciales y de aceptar el acuerdo del permiso de cambio de dominio. También puede [crear el registro TXT](https://support.office.com/en-us/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a?ui=en-US&rs=en-US&ad=US).
    - **Usuarios de Register.com**: siga las [instrucciones paso a paso](https://support.office.com/en-us/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e?ui=en-US&rs=en-US&ad=US#BKMK_verify) para crear el registro TXT.

    > [!TIP]
    > Asegúrese de crear un alias DNS (CNAME) para la [inscripción de dispositivos de Windows](/Intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune) mientras se realizan cambios en su proveedor de host DNS.

Los pasos para agregar y comprobar un dominio personalizado pueden [realizarse en Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-add-domain/) de forma alternativa.

En un escenario en la nube híbrido, después de agregar el nombre de dominio personalizado y de que se haya comprobado que pertenece a su organización, puede seguir administrando cuentas de usuario en su Active Directory local, puede sincronizarlo con Azure AD.

## <a name="to-synchronize-on-premises-users-with-azure-ad"></a>Para sincronizar usuarios locales con Azure AD##

1. [Agregue el sufijo UPN](https://technet.microsoft.com/en-us/library/cc772007.aspx) para su dominio personalizado en su Active Directory local.
2. Establezca el nuevo sufijo UPN para los usuarios locales que planea importar.
3. Ejecute la [sincronización de Azure AD Connect](https://azure.microsoft.com/en-us/documentation/articles/active-directory-aadconnect/) para integrar sus usuarios locales con Azure AD.
4. Una vez que la información de cuenta de usuario se haya sincronizado correctamente, puede asignar las licencias de Microsoft Intune mediante el [Portal de administración de Office 365](https://portal.office.com/Admin/Default.aspx).

### <a name="see-also"></a>Consulte también

[Sobre su dominio inicial onmicrosoft.com en Office 365](https://support.office.com/en-us/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A?ui=en-US&rs=en-US&ad=US)

[Información necesaria antes de iniciar Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md)
### <a name="next-steps"></a>Pasos siguientes
Enhorabuena. Acaba de completar el paso 2 de la *Guía de inicio rápido de Intune*.

>[!div class="step-by-step"]

>[&larr; **Iniciar sesión en Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-1.md)     [**Agregar usuarios a Intune** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-3.md)  



<!--HONumber=Nov16_HO4-->


