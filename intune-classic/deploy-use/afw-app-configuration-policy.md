---
title: "Directiva de configuración de aplicaciones Android for Work"
description: "Use las directivas de configuración de aplicaciones móviles de Intune para proporcionar los valores de configuración que podrían ser necesarios cuando los usuarios ejecutan una aplicación Android for Work."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 02/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fc6b645a-e837-4b2a-a10f-144065cbd8dd
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 3fd5e2891eb628fe84fae8842791b4ac4e883d21
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2017
---
# <a name="configure-android-for-work-apps-with-mobile-app-configuration-policies-in-microsoft-intune"></a>Configuración de aplicaciones Android for Work con directivas de configuración de aplicaciones móviles en Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Use las directivas de configuración de aplicaciones móviles de Microsoft Intune para proporcionar los valores de configuración que podrían ser necesarios cuando los usuarios ejecutan una aplicación. Por ejemplo, una aplicación puede requerir a los usuarios que especifiquen:

-   Un número de puerto personalizado
-   Configuración de idioma
-   Configuración de marca, como un logotipo de empresa

Si el usuario ha especificado la configuración incorrectamente, puede aumentar la carga del departamento de soporte técnico y ralentizar la adopción de nuevas aplicaciones.

Las directivas de configuración de aplicaciones móviles permiten implementar la configuración en dispositivos antes de que los usuarios ejecuten la aplicación. La configuración se proporciona de forma automática y los usuarios no tienen que realizar ninguna acción.

Para usar las directivas de configuración de aplicaciones, el desarrollador de la aplicación debe haber expuesto las configuraciones de aplicación de empresa al crearlas. Por ejemplo, Google Chrome expone la configuración que le permite establecer marcadores predeterminados, sitios permitidos y denegados, y mucho más. Póngase en contacto con el desarrollador de la aplicación para ver si se admite esta configuración y cómo especificarla en la directiva.

Puede implementar la directiva de configuración de aplicación en los mismos usuarios en los que se ha implementado la aplicación que desea configurar. La configuración de la aplicación se aplica cuando se ejecuta la aplicación.

## <a name="configure-a-mobile-app-configuration-policy"></a>Configurar directivas de configuración de aplicaciones móviles

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Directiva** &gt; **Información general** &gt; **Agregar directiva**.

2.  En la lista de directivas, expanda **Android for Work**, elija **Directiva de configuración de aplicaciones móviles (Android for Work)** y, después, elija **Crear directiva**.

    > [!TIP]
    > Solo puede configurar una configuración personalizada para este tipo de directiva. La configuración recomendada no está disponible.

3.  En la sección **General** de la página **Crear directiva** , proporcione un nombre y una descripción opcional para la directiva de configuración de aplicaciones móviles.

4. En la sección **Directiva de configuración de aplicaciones móviles** de la página, especifique la siguiente información:
    - **Id. del paquete para la aplicación a la que se aplica esta configuración**: el identificador del paquete se puede encontrar en la sección 'id =' de la dirección URL de la aplicación en su página de Google Play. Por ejemplo, el identificador del paquete de la aplicación Microsoft Excel es **com.microsoft.office.excel**.
    - En el cuadro de texto, escriba los datos de los valores de la aplicación que desea configurar. Puede obtener esta configuración del proveedor de la aplicación. No todas las aplicaciones admiten esta configuración.
5.  Haga clic en **Validar** para asegurarse de que los datos que ha escrito tienen un formato de lista de propiedades válido.

    > [!IMPORTANT]
    > Al hacer clic en **Validar**, Intune comprueba que los datos de configuración escritos tiene un formato válido. No comprueba que funcionen los datos con la aplicación asociada.

6.  Cuando haya terminado, haga clic en **Guardar directiva**.

La nueva directiva se muestra en el nodo **Directivas de configuración** .


## <a name="deploy-the-app-configuration-policy"></a>Implementación de la directiva de configuración de la aplicación
Después de haber creado una directiva de configuración de aplicaciones móviles, debe implementarla en los mismos usuarios en los que se implementará la aplicación a la que se aplica la configuración.

Para más información sobre cómo implementar las directivas, consulte [Implementar una directiva de configuración](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#deploy-a-configuration-policy).

Para obtener información acerca de cómo implementar aplicaciones para dispositivos Android for Work, consulte [Implementación de aplicaciones para Android for Work con Intune](android-for-work-apps.md).

Cuando se ejecuta la aplicación implementada en un dispositivo, se ejecutará con los valores configurados en la directiva de configuración de la aplicación móvil.

> [!TIP]
> Solo puede implementar una directiva de configuración de aplicación para cada aplicación en un usuario.
