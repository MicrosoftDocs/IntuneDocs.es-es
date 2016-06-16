---
# required metadata

title: Buscar un nombre de familia de paquete (PFN) para la VPN por aplicación | Microsoft Intune
description:
keywords:
author: nbigman
manager: [ALIAS]
ms.date: 05/10/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 74643d1d-4fd9-4cff-ac79-1a42281d2f76

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer: tycast
#ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Buscar un nombre de familia de productos (PFN) para la configuración de la VPN por aplicación

Hay dos formas de buscar un PFN para poder configurar una VPN por aplicación.

## Buscar un PFN para una aplicación instalada en un equipo Windows 10 

Si la aplicación con la que trabaja ya está instalada en un equipo Windows 10, puede usar el cmdlet [Get-AppxPackage](https://technet.microsoft.com/library/hh856044.aspx) de PowerShell para obtener el PFN.

La sintaxis de Get-AppxPackage es la siguiente:

` Parameter Set: __AllParameterSets`
` Get-AppxPackage [[-Name] <String> ] [[-Publisher] <String> ] [-AllUsers] [-User <String> ] [ <CommonParameters>]`

> Nota: podría tener que ejecutar PowerShell como administrador para poder recuperar el PFN.

Por ejemplo, para obtener información sobre todas las aplicaciones universales instaladas en el equipo, use `Get-AppxPackage`.

Para más información sobre una aplicación cuyo nombre conoce en su totalidad o en parte, use `Get-AppxPackage *<app_name>`. Observe el uso del carácter comodín, que resulta especialmente útil si no está seguro del nombre completo de la aplicación. Por ejemplo, para obtener la información de OneNote, use `Get-AppxPackage *OneNote`.


Esta es la información recuperada sobre OneNote:

`Name                   : Microsoft.Office.OneNote`

`Publisher              : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US`

`Architecture           : X64`

`ResourceId             :`

`Version                : 17.6769.57631.0`

`PackageFullName        : Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`InstallLocation        : C:\Program Files\WindowsApps`

`\Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`IsFramework            : False`

**`PackageFamilyName      : Microsoft.Office.OneNote_8wekyb3d8bbwe`**

`PublisherId            : 8wekyb3d8bbwe`



## Buscar un PFN si la aplicación no está instalada en un equipo

1.  Vaya a https://www.microsoft.com/es-es/store/apps.
2.  En la barra de búsqueda, escriba el nombre de la aplicación. En nuestro ejemplo, busque OneNote.
3.  Haga clic en el vínculo de la aplicación. Observe que la dirección URL a la que tiene acceso incluye una serie de letras al final. En nuestro ejemplo, la dirección URL tiene el siguiente aspecto:
`https://www.microsoft.com/en-us/store/apps/onenote/9wzdncrfhvjl`
4.  En una pestaña diferente, pegue la siguiente dirección URL, `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/<app id>/applockerdata`, reemplazando `<app id>` por el identificador de la aplicación que obtuvo en https://www.microsoft.com/es-es/store/apps, es decir, esa serie de letras al final de la dirección URL del paso 3. En nuestro ejemplo de OneNote, pegará lo siguiente: `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/9wzdncrfhvjl/applockerdata`.

En Edge, la información que le interesa se muestra directamente; en Internet Explorer, haga clic en **Abrir** para ver la información. El valor PFN se indica en la primera línea. En nuestro ejemplo, este es el aspecto de los resultados:
 

`{`
`  "packageFamilyName": "Microsoft.Office.OneNote_8wekyb3d8bbwe",`
`  "packageIdentityName": "Microsoft.Office.OneNote",`
`  "windowsPhoneLegacyId": "ca05b3ab-f157-450c-8c49-a1f127f5e71d",`
`  "publisherCertificateName": "CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"`
`}`



<!--HONumber=Jun16_HO1-->


