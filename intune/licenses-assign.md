---
title: Asignar licencias de Microsoft Intune
description: Asignar licencias a los usuarios para que puedan inscribirse en Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bb4314ea-88b5-44d3-92ce-4c6aff0587a4
ms.reviewer: amyro
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 8f37c45945df460dabac60e5b06286c940728ba3
ms.sourcegitcommit: 3c4ea8d6809a63042705b5ed4f25ba80f522070e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2018
---
# <a name="assign-licenses-to-users-so-they-can-enroll-devices-in-intune"></a>Asignar licencias a los usuarios para que puedan inscribir dispositivos en Intune

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Tanto si quiere agregar usuarios manualmente como si quiere sincronizar desde Active Directory local, debe asignar primero a cada usuario una licencia de Intune para que los usuarios puedan inscribir sus dispositivos en Intune. Para obtener una lista de licencias, vea [Licencias que incluyen Intune](licenses.md).

## <a name="assign-an-intune-license-in-the-office-365-admin-center"></a>Asignar una licencia de Intune en el Centro de administración de Office 365

Puede usar el [Portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) para agregar manualmente usuarios basados en la nube y asignar licencias a las cuentas de usuario basadas en la nube y a las cuentas sincronizadas desde Active Directory local con Azure AD.

1. Inicie sesión en el [Portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) con las credenciales de administrador de inquilinos y luego elija **Contactos** > **Usuarios activos**.

2. Seleccione la cuenta de usuario a la que quiere asignar una licencia de usuario de Intune y luego elija **Licencias de producto** > **Editar**.

3. Alterne entre **Intune** o **Enterprise Mobility + Security** en **Activado** y elija **Guardar**.

   ![Captura de pantalla de la sección Licencias de producto del Portal de Office 365.](./media/office-assign-license.png)

4. Ahora, la cuenta de usuario tiene los permisos necesarios para usar el servicio e inscribir dispositivos en la administración.

> [!NOTE]
> Los usuarios solo aparecerán en la consola de administración cuando hayan inscrito un dispositivo. Además, puede seleccionar un grupo de usuarios para editarlos a la vez, ya sea seleccionando agregar o reemplazar una licencia para todos los usuarios seleccionados.

## <a name="assign-an-intune-license-by-using-azure-active-directory"></a>Asignación de una licencia de Intune con Azure Active Directory

También puede asignar licencias de Intune a los usuarios a través de Azure Active Directory. Para más información, consulte el artículo [Licencia de usuarios en Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-licensing-group-assignment-azure-portal). 

## <a name="use-school-data-sync-to-assign-licenses-to-users-in-intune-for-education"></a>Uso de School Data Sync para asignar licencias a los usuarios de Intune for Education
Si se trata de una organización educativa, puede utilizar School Data Sync (SDS) para asignar licencias de Intune for Education a los usuarios sincronizados. Active la casilla de Intune for Education al configurar el perfil de SDS.  

![Captura de pantalla de la configuración del perfil de SDS](./media/i4e-sds-profile-setup-setting.png)

Al asignar una licencia de Intune for Education, asegúrese de que también se asigne la licencia de Intune A Direct.

![Captura de pantalla de la configuración de la licencia del producto](./media/i4e-set-licenses.png)

Vea la [información general de School Data Sync](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91) para obtener más información sobre SDS.

## <a name="how-user-and-device-licenses-affect-access-to-services"></a>Cómo las licencias de usuario y dispositivo afectan el acceso a los servicios
* Cada **usuario** al que asigna una licencia de software de usuario puede acceder a los servicios en línea y al software relacionado (incluido software de System Center) y usarlos para administrar las aplicaciones y hasta 15 dispositivos.
* Cada **dispositivo** al que asigna una licencia de software de dispositivo puede acceder a los servicios en línea y al software relacionado (incluido software de System Center) y usarlos para que los use cualquier número de usuarios.
* Si más de un usuario usa un dispositivo, cada uno de ellos debe tener una licencia de software de dispositivos, o bien todos los usuarios deben tener una licencia de software de usuario.

## <a name="understanding-the-type-of-licenses-you-have-purchased"></a>Descripción del tipo de licencias adquiridas

El modo en el que haya adquirido Intune determina la información de la suscripción:

- Si ha adquirido Intune a través de un Contrato Enterprise, encontrará la información de suscripción en el portal de licencias por volumen, en **Suscripciones**.
- Si ha adquirido Intune a través de un Proveedor de soluciones en la nube, acuda a su distribuidor.
- Si ha adquirido Intune con una tarjeta de crédito o con factura, las licencias se basarán en el usuario.




## <a name="use-powershell-to-selectively-manage-ems-user-licenses"></a>Usar PowerShell para administrar de forma selectiva las licencias de usuario de EMS
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

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -LicenseOptions $CustomEMS

Realice la comprobación con lo siguiente:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

![PoSH-AddLic-Verify](./media/posh-addlic-verify.png)
