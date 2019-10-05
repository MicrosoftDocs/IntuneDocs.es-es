---
title: Resolver conflictos de directivas de Intune y GPO
titleSuffix: Microsoft Intune
description: Obtenga información acerca de cómo resolver los conflictos entre las directivas de configuración de directiva de grupo e Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e76af5b7-e933-442c-a9d3-3b42c5f5868b
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9834181d4b6c010cc5ca83eadfb424d036ab13d6
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736187"
---
# <a name="resolve-group-policy-objects-gpo-and-microsoft-intune-policy-conflicts"></a>Resolver conflictos de directivas de Microsoft Intune y objetos de directiva de grupo (GPO)

[!INCLUDE [classic-portal](../../intune-classic/includes/classic-portal.md)]

> [!NOTE]
> La información de este tema se aplica solo a equipos de escritorio de Windows que está administrando como PC mediante el cliente de software de Intune.

Intune usa directivas que le ayudan a administrar la configuración en equipos Windows. Por ejemplo, puede usar una directiva para controlar la configuración de Firewall de Windows en los equipos. Muchas de las opciones de Intune son similares a las opciones que se pueden configurar con la directiva de grupo de Windows. Pero es posible que, en ocasiones, los dos métodos entren en conflicto.

Cuando se producen conflictos, la directiva de grupo de nivel de dominio tiene prioridad sobre la directiva de Intune, a menos que el equipo no pueda iniciar sesión en el dominio. En este caso, la directiva de Intune se aplica al equipo cliente.

## <a name="what-to-do-if-you-are-using-group-policy"></a>Qué hacer si se utiliza la directiva de grupo
Asegúrese de que las directivas que aplica no se administran mediante la directiva de grupo. Para evitar conflictos, puede usar uno o más de los siguientes métodos:

- Mueva los equipos a una unidad organizativa (UO) de Active Directory que no tenga aplicada la configuración de la directiva de grupo antes de instalar el cliente de Intune. También es posible bloquear la herencia de directivas de grupo en las UO que contienen equipos inscritos en Intune a los que no quiere aplicar la configuración de la directiva de grupo.

- Use un filtro de grupo de seguridad para restringir los GPO únicamente a los equipos que no se administran mediante Intune.

- Deshabilite o quite los objetos de directiva de grupo que entran en conflicto con las directivas de Intune.

Para obtener más información acerca de Active Directory y la directiva de grupo de Windows, consulte la documentación de Windows Server.

## <a name="how-to-filter-existing-gpos-to-avoid-conflicts-with-intune-policy"></a>Cómo filtrar los GPO existentes para evitar conflictos con la directiva de Intune
Si ha identificado GPO cuya configuración entra en conflicto con las directivas de Intune, puede usar filtros de grupo de seguridad para restringir esos GPO únicamente a los equipos que no se administran mediante Intune.

<!--- ### Use WMI filters
WMI filters selectively apply GPOs to computers that satisfy the conditions of a query. To apply a WMI filter, deploy a WMI class instance to all PCs in the enterprise before you enroll any PCs in the Intune service.

#### To apply WMI filters to a GPO

1. Create a management object file by copying and pasting the following into a text file, and then saving it to a convenient location as **WIT.mof**. The file contains the WMI class instance that you deploy to PCs that you want to enroll in the Intune service.

    ```
    //Beginning of MOF file.
    #pragma classflags("forceupdate")
    #pragma namespace ("\\\\.\\Root")
    instance of __Namespace
    {
       Name = "WindowsIntune";
    };

    #pragma namespace ("\\\\.\\Root\\WindowsIntune")
    [
       Description("This class defines Microsoft Intune common properties")
    ]
    class WindowsIntune_ManagedNode
    {
       [ read, Description("This defines whether Microsoft Intune Policy is enabled"): DisableOverride ToSubClass ]
       boolean WindowsIntunePolicyEnabled;
       [ read, key, Description("This property defines the version." "Example: 1.0"): ToSubClass ]
       string Version;
    };

    instance of WindowsIntune_ManagedNode
    {
       Version = "1.0";
       WindowsIntunePolicyEnabled = 1;
    };
    ```

2. Use either a startup script or Group Policy to deploy the file. The following is the deployment command for the startup script. The WMI class instance must be deployed before you enroll client PCs in the Intune service.

    **C:/Windows/System32/Wbem/MOFCOMP &lt;path to MOF file&gt;\wit.mof**

3. Run either of the following commands to create the WMI filters, depending on whether the GPO you want to filter applies to PCs that are managed by using Intune or to PCs that are not managed by using Intune.

    - For GPOs that apply to PCs that are not managed by using Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=0
        ```

    - For GPOs that apply to PCs that are managed by Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=1
        ```

4. Edit the GPO in the Group Policy Management console to apply the WMI filter that you created in the previous step.

    - For GPOs that should apply only to PCs that you want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=1**.

    - For GPOs that should apply only to PCs that you do not want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=0**.

For more information about how to apply WMI filters in Group Policy, see the blog post [Security Filtering, WMI Filtering, and Item-level Targeting in Group Policy Preferences](http://go.microsoft.com/fwlink/?LinkId=177883). --->


Puede aplicar los GPO únicamente a los grupos de seguridad especificados en el área **Filtrado de seguridad** de la Consola de administración de directivas de grupo para un GPO seleccionado. De forma predeterminada, los GPO se aplican a *usuarios autenticados*.

- En el complemento **Usuarios y equipos de Active Directory**, cree un grupo de seguridad que contenga los equipos y las cuentas de usuario que no quiere administrar mediante Intune. Por ejemplo, el nombre del grupo podría ser *No en Microsoft Intune*.

- En la Consola de administración de directivas de grupo, en la pestaña **Delegación** del GPO seleccionado, haga clic con el botón derecho en el nuevo grupo de seguridad para delegar los permisos **Lectura** y **Aplicar directiva de grupo** apropiados en los usuarios y equipos del grupo de seguridad. (Los permisos**Aplicar directiva de grupo** están disponibles en el cuadro de diálogo **Avanzadas** ).

- Después, aplique el nuevo filtro de grupo de seguridad a un GPO seleccionado y quite el filtro predeterminado **Usuarios autenticados**.

El nuevo grupo de seguridad debe mantenerse inscrito en los cambios del servicio de Intune.

## <a name="see-also"></a>Consulte también
[Administrar equipos Windows con Microsoft Intune](../manage-windows-pcs-with-microsoft-intune.md)
