---
# required metadata

title: Resolver conflictos de directivas de Intune y GPO | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e76af5b7-e933-442c-a9d3-3b42c5f5868b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Resolver conflictos de directivas de Microsoft Intune y objetos de directiva de grupo (GPO)
Intune usa directivas que le ayudan a administrar la configuración de los equipos que administra. Por ejemplo, podría utilizar una directiva para controlar la configuración del Firewall de Windows en los equipos. Muchas de las opciones de Intune son similares a las opciones que se pueden configurar con la directiva de grupo de Windows. Sin embargo, es posible que, en ocasiones, los dos métodos entren en conflicto.

Cuando se producen conflictos, la directiva de grupo de nivel de dominio tiene prioridad sobre la directiva de Intune, a menos que el equipo no pueda iniciar sesión en el dominio. En este caso, la directiva de Intune se aplica al equipo cliente.

## Qué hacer si se utiliza la directiva de grupo
Compruebe que las directivas que aplica no se administran mediante la directiva de grupo. Para evitar conflictos, podría emplear uno o más de los siguientes métodos:

-   Mueva los equipos a una unidad organizativa (UO) de Active Directory que no tenga aplicada la configuración de la directiva de grupo antes de instalar el cliente de Intune. También es posible bloquear la herencia de directivas de grupo en las UO que contienen equipos inscritos en Intune a los que no quiere aplicar la configuración de la directiva de grupo.

-   Use un filtro WMI o un filtro de seguridad para restringir los GPO únicamente a los equipos que no se administran mediante Intune. Para obtener información y ejemplos sobre cómo hacerlo, vea más adelante la sección [Cómo filtrar los GPO existentes para evitar conflictos con la directiva de Microsoft Intune](resolve-gpo-and-microsoft-intune-policy-conflicts.md#BKMK_Filter).

-   Deshabilite o quite los objetos de directiva de grupo que entran en conflicto con las directivas de Intune.

Para obtener más información acerca de Active Directory y la directiva de grupo de Windows, consulte la documentación de Windows Server.

## Cómo filtrar los GPO existentes para evitar conflictos con la directiva de Intune
Si ha identificado GPO cuya configuración entra en conflicto con las directivas de Intune, puede usar cualquiera de los métodos de filtrado siguientes para restringir esos GPO únicamente a los equipos que no se administran mediante Intune.

### Usar filtros WMI
Los filtros WMI aplican selectivamente los GPO a los equipos que cumplen las condiciones de una consulta. Para aplicar un filtro WMI, implemente una instancia de clase WMI en todos los equipos de la empresa antes de inscribir ningún equipo en el servicio Intune.

#### Para aplicar filtros WMI a un GPO

1.  Cree un archivo de objeto de administración. Para ello, copie y pegue lo siguiente en un archivo de texto y, a continuación, guarde este archivo en una ubicación adecuada como **WIT.mof**. Este archivo contiene la instancia de clase WMI que deberá implementar en los equipos que quiere inscribir en el servicio de Intune.

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

2.  Para implementar el archivo puede utilizar tanto una secuencia de comandos de inicio, como la directiva de grupo. A continuación se indica el comando de implementación de la secuencia de comandos de inicio. Es necesario implementar la instancia de clase WMI antes de inscribir un equipo cliente en el servicio de Intune.

    **C:/Windows/System32/Wbem/MOFCOMP &lt;ruta de acceso al archivo MOF&gt;\wit.mof**

3.  Ejecute cualquiera de los comandos siguientes para crear los filtros WMI, en función de si el GPO que quiere filtrar se aplica a equipos administrados mediante Intune o a equipos que no se administran mediante Intune.

    -   Para los GPO que se aplican a equipos no administrados mediante Intune, use lo siguiente:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=0
        ```

    -   Para los GPO que se aplican a equipos administrados mediante Intune, use lo siguiente:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=1
        ```

4.  Edite el GPO en la Consola de administración de directivas de grupo para aplicar el filtro WMI que creó en el paso anterior.

    -   Para los GPO que solo deberían aplicarse a los equipos que quiere administrar mediante Intune, aplique el filtro **WindowsIntunePolicyEnabled=1**..

    -   Para los GPO que solo deberían aplicarse a los equipos que no quiere administrar mediante Intune, aplique el filtro **WindowsIntunePolicyEnabled=0**..

Para más información sobre cómo aplicar filtros WMI en la directiva de grupo, vea la entrada de blog [Security Filtering, WMI Filtering, and Item-level Targeting in Group Policy Preferences](http://go.microsoft.com/fwlink/?LinkId=177883) (Filtrado de seguridad, filtrado WMI y destinatarios en el ámbito del elemento en las preferencias de directiva de grupo)..

### Utilizar filtros de grupo de seguridad
La directiva de grupo le permite aplicar los GPO únicamente a los grupos de seguridad especificados en el área **Filtrado de seguridad** de la Consola de administración de directivas de grupo para un GPO seleccionado. De forma predeterminada, los GPO se aplican a **Usuarios autenticados**..

-   En el complemento **Usuarios y equipos de Active Directory**, cree un nuevo grupo de seguridad que contenga los equipos y las cuentas de usuario que no quiere administrar mediante Intune. Por ejemplo, el nombre del grupo podría ser **No en Microsoft Intune**..

-   En la Consola de administración de directivas de grupo, en la pestaña **Delegación** del GPO seleccionado, haga clic con el botón derecho en el nuevo grupo de seguridad para delegar los permisos **Lectura** y **Aplicar directiva de grupo** apropiados en los usuarios y equipos del grupo de seguridad. (Los permisos**Aplicar directiva de grupo** están disponibles en el cuadro de diálogo **Avanzadas** ).

-   A continuación, aplique el nuevo filtro de grupo de seguridad a un GPO seleccionado y quite el filtro predeterminado **Usuarios autenticados** .

El nuevo grupo de seguridad debe mantenerse inscrito en los cambios del servicio de Intune.

### Consulte también
[Administrar equipos Windows con Microsoft Intune](manage-windows-pcs-with-microsoft-intune.md)


<!--HONumber=May16_HO1-->


