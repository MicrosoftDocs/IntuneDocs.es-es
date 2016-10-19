---
title: Nombres de dominio de Microsoft Intune | Microsoft Intune
description: agregar nombre de dominio para Intune
keywords: 
author: andredm7
manager: swadhwa
ms.date: 10/11/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c3c136f0-330d-432a-a91f-16f7dd097e55
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 38159f6dbcae2eeb4dca47141e60eed12cd7f6ee
ms.openlocfilehash: abcf37e7ec3150b5a2fe4cda910631f83d4c510a


---



# Nombres de dominios personalizados con Microsoft Intune

Cuando su organización se registra en un servicio en la nube de Microsoft como Intune, se le asigna un nombre de dominio inicial hospedado en Azure Active Directory que es similar al siguiente: **sudominio.onmicrosoft.com**. En este ejemplo, **sudominio** es el nombre de dominio que eligió al suscribirse y **onmicrosoft.com** es el sufijo asignado a las cuentas que agregue a su suscripción.

No puede cambiar el nombre o quitar ese nombre de dominio inicial. Sin embargo, puede agregar, comprobar o quitar sus propios nombres de dominio personalizados para usarlos con Intune, que es útil si quiere mantener la identidad de su negocio.

## Para agregar y comprobar el dominio personalizado 

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

## Para sincronizar usuarios locales con Azure AD##

1. [Agregue el sufijo UPN](https://technet.microsoft.com/en-us/library/cc772007.aspx) para su dominio personalizado en su Active Directory local.
2. Establezca el nuevo sufijo UPN para los usuarios locales que planea importar.
3. Ejecute la [sincronización de Azure AD Connect](https://azure.microsoft.com/en-us/documentation/articles/active-directory-aadconnect/) para integrar sus usuarios locales con Azure AD.
4. Una vez que la información de cuenta de usuario se haya sincronizado correctamente, puede asignar las licencias de Microsoft Intune mediante el [Portal de administración de Office 365](https://portal.office.com/Admin/Default.aspx).

### Consulte también

[Sobre su dominio inicial onmicrosoft.com en Office 365](https://support.office.com/en-us/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A?ui=en-US&rs=en-US&ad=US)

[What to know before you start Microsoft Intune (Información necesaria antes de iniciar Microsoft Intune)](what-to-know-before-you-start-microsoft-intune.md)



<!--HONumber=Oct16_HO2-->


