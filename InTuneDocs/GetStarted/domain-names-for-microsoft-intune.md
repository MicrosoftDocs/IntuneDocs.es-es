---
# required metadata

title: Nombres de dominio de Microsoft Intune | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: c3c136f0-330d-432a-a91f-16f7dd097e55

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---



# Nombres de dominio de Microsoft Intune

Antes de configurar Microsoft Intune, repase este tema y los requisitos que aparecen en [What to know before you start Microsoft Intune ](what-to-know-before-you-start-microsoft-intune.md) (Información necesaria antes de iniciar Microsoft Intune)..

Cuando su organización se suscribe a un servicio en la nube de Microsoft como Intune, se le asigna un nombre de dominio inicial similar al siguiente: **contoso.onmicrosoft.com**. En este ejemplo, **contoso** es el nombre de dominio que eligió al suscribirse y **onmicrosoft.com** es el sufijo asignado a las cuentas que agregue a su suscripción. Después de completar el proceso de suscripción, no puede cambiar ese nombre de dominio. Sin embargo, como administrador global, puede agregar sus propios nombres de dominio personalizados para que su organización los utilice con el servicio o quitar los dominios que haya agregado anteriormente.

De forma predeterminada, cuando utiliza el dominio onmicrosoft, cada usuario que importe recibe el sufijo **onmicrosoft.com** para su nombre principal de usuario (UPN).

Para usar un nombre de dominio de su propiedad en lugar del que se le asignó al suscribirse, puede agregar dicho nombre de dominio a Azure Active Directory. Después de agregar el dominio y de que se compruebe que es de su propiedad, puede crear cuentas y grupos que incluyan el nombre de dominio si cambia los registros de recurso DNS en el proveedor de host DNS. A fin de simplificar la administración de las cuentas de usuario si planea usar un dominio personalizado, configure un nombre de dominio personalizado en su suscripción antes de empezar a sincronizar usuarios desde su Active Directory local.

Configurar nombres de dominio y registros de recursos DNS para Intune es igual que para otros inquilinos de Azure Active Directory. Vea [Uso de nombres de dominio personalizados para simplificar el inicio de sesión mediante Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/) para obtener instrucciones.

### Consulte también
[What to know before you start Microsoft Intune (Información necesaria antes de iniciar Microsoft Intune)](what-to-know-before-you-start-microsoft-intune.md)


<!--HONumber=May16_HO1-->


