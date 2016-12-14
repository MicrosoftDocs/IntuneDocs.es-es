---
title: Administrar licencias de Intune | Microsoft Intune
description: "Asignación de licencias a los usuarios de la suscripción de Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb4314ea-88b5-44d3-92ce-4c6aff0587a4
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: f0f9d60a27afa580aaba8a3c24fff6325ae53f08


---

# <a name="manage-intune-licenses"></a>Administración de licencias de Intune
Antes de que los usuarios puedan iniciar sesión para usar el servicio de Intune o inscriban sus dispositivos en la administración, primero debe asignar a cada usuario una licencia a su suscripción de Intune desde el [portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854).

Las organizaciones que usan Microsoft Enterprise Mobility + Security (EMS) pueden tener usuarios que solo necesiten Azure Active Directory Premium o los servicios de Intune en el paquete de EMS. Puede asignar un servicio o un subconjunto de servicios mediante los [cmdlets de PowerShell de Azure Active Directory](https://msdn.microsoft.com/library/jj151815.aspx). Para obtener más información, vea [licencias de Intune administrar con PowerShell](start-with-a-paid-subscription-to-microsoft-intune-step-4-posh.md).

## <a name="how-intune-licenses-are-assigned"></a>Cómo se asignan las licencias de Intune
Cuando las cuentas de usuario se sincronizan desde Active Directory local o se agregan manualmente a su suscripción de servicios en la nube a través del [portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854), no se les asigna automáticamente una licencia de Intune. En vez de ello, un administrador de inquilinos de Intune deberá editar posteriormente la cuenta de usuario para asignar una licencia al usuario desde el portal de Office 365.

Cuando la suscripción comparte Azure AD con otros servicios en la nube asociados a la suscripción, usted también debe tener acceso a los usuarios que se agregaron a esos servicios. Estos usuarios no tienen una licencia para [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] hasta que le asigne una licencia a cada uno de ellos.

> [!TIP]
> Si la opción de asignar o revocar una licencia de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] está deshabilitada, la suscripción podría incluir opciones de licencias por volumen, como las disponibles cuando se usa [Enterprise Mobility Suite + Security](https://www.microsoft.com/en-us/server-cloud/enterprise-mobility/overview.aspx). Para obtener información acerca de cómo asignar o revocar licencias, consulte la documentación de las opciones de licencia.

## <a name="assign-an-intune-user-license"></a>Asigne una licencia de usuario de Intune

El [portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) se usa para agregar manualmente usuarios basados en la nube y asignar licencias a las cuentas de usuario basadas en la nube y a las cuentas sincronizadas desde Active Directory local con Azure AD.

1.  Inicie sesión en el [portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) con las credenciales del administrador de inquilinos y, después, seleccione **Contactos** > **Todos los usuarios**.

2.  Seleccione la cuenta de usuario a la que desea asignar una licencia de Intune y, a continuación, seleccione **Microsoft Intune** (independiente) o **Enterprise Mobility Suite**.

3.  Ahora, la cuenta de usuario tiene los permisos necesarios para usar el servicio e inscribir dispositivos en la administración.

> [!NOTE]
> Los usuarios aparecerán en la consola cuando hayan inscrito un dispositivo.

### <a name="use-powershell-to-selectively-manage-ems-user-licenses"></a>Usar PowerShell para administrar de forma selectiva las licencias de usuario de EMS
Las organizaciones que usan Microsoft Enterprise Mobility + Security (anteriormente denominado Enterprise Mobility Suite) pueden tener usuarios que solo necesiten Azure Active Directory Premium o los servicios de Intune en el paquete de EMS. Puede asignar un servicio o un subconjunto de servicios mediante los [cmdlets de PowerShell de Azure Active Directory](https://msdn.microsoft.com/library/jj151815.aspx).

Para asignar licencias de usuario de forma selectiva a los servicios de EMS, abra PowerShell como administrador en un equipo que tenga instalado el [módulo de Azure Active Directory para Windows PowerShell](https://msdn.microsoft.com/library/jj151815.aspx#bkmk_installmodule). Puede instalar PowerShell en un equipo local o en un servidor de ADFS.

Debe crear una nueva definición de SKU de licencia que solo se aplique a los planes de servicio deseados. Para ello, deshabilite los planes que no quiera aplicar. Por ejemplo, podría crear una definición de SKU de licencia que no asigne una licencia de Intune. Para ver una lista con los servicios disponibles, escriba:

    (Get-MsolAccountSku | Where {$_.SkuPartNumber -eq "EMS"}).ServiceStatus

Puede ejecutar el comando siguiente para excluir el plan de servicio Intune. Puede usar el mismo método para realizar una expansión a todo un grupo de seguridad o puede usar filtros más pormenorizados.

**Ejemplo 1**<br>
Cree un nuevo usuario en la línea de comandos y asigne una licencia de EMS sin habilitar la parte de Intune de la licencia:

    Connect-MsolService

    New-MsolUser -DisplayName “Test User” -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS


Realice la comprobación con lo siguiente:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

**Ejemplo 2**<br>
Deshabilite la parte de Intune de la licencia de EMS de un usuario que ya tenga asignada una licencia:

    Connect-MsolService

    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -RemoveLicenses IAPProdPartnerTest:EMS

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS

Realice la comprobación con lo siguiente:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com" .Licenses.ServiceStatus

![PoSH-AddLic-Verify](./media/posh-addlic-verify.png)

>[!div class="step-by-step"]

>[&larr; **Sincronizar los usuarios con Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**Organizar usuarios y dispositivos** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)  



<!--HONumber=Dec16_HO2-->


