---
title: "Cómo agregar aplicaciones a Microsoft Intune"
titlesuffix: 
description: "Descubra cómo agregar aplicaciones a Microsoft Intune para que pueda asignar aplicaciones a usuarios y dispositivos. Intune admite una gran variedad de tipos diferentes de aplicaciones."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 91762eafbba5f96ce04f3ffd4d83f63434a3ac74
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2018
---
# <a name="how-to-add-an-app-to-microsoft-intune"></a>Agregar una aplicación a Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Para poder asignar, supervisar, configurar o proteger las aplicaciones, debe agregarlas a Intune. Intune admite una gran variedad de tipos diferentes de aplicaciones. Las opciones disponibles varían para cada tipo de aplicación.

Intune permite agregar y asignar estos tipos de aplicación:
| Tipo de aplicación                                  | Instalación                                                                  | Updates                       |
|------------------------------------------ |----------------------------------------------------------------------------   |---------------------------    |
| Aplicaciones en la web                           | Intune crea un acceso directo a la aplicación web en la pantalla principal del dispositivo          | Las actualizaciones de aplicaciones son automáticas     |
| Aplicaciones escritas internamente (línea de negocio)  | Intune instala la aplicación en el dispositivo (el usuario proporciona el archivo de instalación)    | Debe actualizar la aplicación       |
| Aplicaciones de la tienda                       | Intune instala la aplicación en el dispositivo                                       | Las actualizaciones de aplicaciones son automáticas     |
| Aplicaciones integradas                        | Intune instala la aplicación en el dispositivo                                       | Las actualizaciones de aplicaciones son automáticas     |


Además de las aplicaciones web, Intune admite las siguientes plataformas específicas para las aplicaciones de la tienda y las aplicaciones LOB:
- Aplicaciones de la Tienda
    - Aplicaciones de Google Play Store
    - Aplicaciones de App Store
    - Aplicaciones de la Tienda Windows Phone 8.1
    - Aplicaciones de la Tienda Windows
    - Aplicaciones de Android for Work
    - Aplicaciones de Office 365 para Windows
    - Aplicaciones de Office 365 para macOS
- Compilar la aplicación - línea de negocio (LOB)
    - Aplicaciones de línea de negocio (LOB) Android
    - Aplicaciones de línea de negocio (LOB) iOS
    - Aplicaciones de línea de negocio (LOB) de Windows Phone (archivos .xap)
    - Aplicaciones de línea de negocio (LOB) de Windows (solo archivos .msi)
- Aplicaciones integradas    

>[!TIP]
> Una aplicación de línea de negocio (LOB) es aquella que se agrega desde un archivo de instalación de la aplicación. Por ejemplo, para instalar una aplicación LOB de iOS, agregue la aplicación eligiendo **Aplicación de línea de negocio** como el **Tipo de aplicación** desde la hoja **Agregar aplicación**. Después, seleccione el archivo de paquete de aplicación (extensión .ipa). Estos tipos de aplicaciones normalmente se han escrito internamente.

## <a name="assess-application-requirements"></a>Evaluar los requisitos de aplicaciones 
Como administrador de TI, no solo debe determinar qué aplicaciones debe usar el grupo, sino que debe determinar las capacidades necesarias para cada grupo y subgrupo. Para cada aplicación, debe determinar las plataformas necesarias, los grupos de usuarios que necesitan la aplicación, las directivas de configuración para aplicar a todos los grupos y las directivas de protección que se aplicarán.  

Además, debe determinar si tiene que centrarse en la administración de dispositivos móviles (MDM) o solo en la administración de aplicaciones móviles (MAM). Usar Intune para administrar el dispositivo (administración de dispositivos móviles) resulta útil cuando:
- Los usuarios necesitan un perfil de conectividad corporativo de VPN o de red Wi-Fi para ser productivos.
- Los usuarios necesitan que se envíe un conjunto de aplicaciones a su dispositivo.
- Su organización debe cumplir con las directivas legales u otras que requieren controles de administración de dispositivos móviles (MDM) específicos, como seguridad o cifrado.

Usar Intune para administrar las aplicaciones (administración de aplicaciones móviles) sin tener que administrar el dispositivo es útil cuando:
- Quiere permitir que los usuarios usen sus propios dispositivos (BYOD).
- Quiere proporcionar una ventana emergente de un solo uso para que los usuarios sepan qué protecciones de MAM se encuentran en contexto, en lugar una notificación continua a nivel de dispositivo.
- Quiere cumplir directivas que exigen menos capacidades de administración en dispositivos personales. Por ejemplo, quiere administrar los datos corporativos de las aplicaciones, en lugar de administrar los datos corporativos de todo el dispositivo.

Para obtener más información: [Comparar MDM y MAM](byod-technology-decisions.md).

### <a name="determine-who-will-use-the-app"></a>Determine quién va a usar la aplicación
Una vez haya agregado una aplicación a Intune, asigna un grupo de usuarios que pueden usar la aplicación. En primer lugar, debe determinar el grupo apropiado que debería tener acceso a la aplicación en función de la confidencialidad de los datos que contiene la aplicación. Puede que tenga incluir o excluir ciertos tipos de roles dentro de su organización. Por ejemplo, puede que solo se requieran determinadas aplicaciones LOB para el grupo de ventas, mientras que el personal centrado en ingeniería, finanzas, recursos humanos o legal puede que no necesiten usar las aplicaciones LOB. Además, el grupo de ventas podría necesitar protección de datos adicional y acceso a los servicios corporativos internos en sus dispositivos móviles. Debe determinar cómo se conectará este grupo a los recursos mediante la aplicación. ¿Los datos a los que accede la aplicación se encuentran en la nube o en el entorno local? Además, cómo se conectarán los usuarios a los recursos mediante la aplicación. Intune también permite el acceso a las aplicaciones móviles que requieren un acceso seguro a los datos locales, como servidores de aplicaciones de línea de negocio. Este tipo de acceso se suele llevar a cabo mediante [certificados administrados por Intune](certificates-configure.md) para el control de acceso, combinado con un proxy o una puerta de enlace de VPN estándar en el perímetro (como, por ejemplo, el Proxy de aplicación de Microsoft Azure Active Directory). El [SDK de aplicaciones y la herramienta de ajuste de aplicaciones](apps-prepare-mobile-application-management.md) de Intune pueden contener los datos a los que se ha tenido acceso dentro de la aplicación de línea de negocio, de forma que los datos corporativos no se puedan pasar a servicios o aplicaciones de consumidor.

Use la [Guía de planeamiento de la implementación, diseño e implementación de Intune](planning-guide.md) para ayudarle a determinar cómo identificar los grupos de la organización que están asociados a cada escenario de caso de uso y caso de subuso de la aplicación. Para obtener más información sobre cómo asignar aplicaciones a los grupos, consulte [Asignación de aplicaciones a grupos con Microsoft Intune](apps-deploy.md). 

### <a name="determine-the-type-of-app-for-your-solution"></a>Determinar el tipo de aplicación para la solución
Puede elegir entre los siguientes tipos de aplicación:
- **Aplicaciones en la web**: una aplicación web es una aplicación cliente-servidor. El servidor proporciona la aplicación web, que incluye la interfaz de usuario, el contenido y la funcionalidad. Además, las plataformas de hospedaje web modernas normalmente ofrecen seguridad, equilibrio de carga y otras ventajas. Este tipo de aplicación se mantiene por separado en la Web. Intune se usa para que apunte a este tipo de aplicación. También puede asignar qué grupos de usuarios pueden tener acceso a esta aplicación. Tenga en cuenta que Android no es compatible con las aplicaciones web.
- **Aplicaciones escritas internamente (línea de negocio)**: las aplicaciones creadas internamente son aplicaciones de línea de negocio (LOB). La funcionalidad de este tipo de aplicación se ha creado para una de las plataformas compatibles con Intune, por ejemplo, Windows, iOS y Android. Su organización crea y le proporciona actualizaciones como un archivo independiente. Puede proporcionar actualizaciones de la aplicación a los usuarios agregando e implementando las actualizaciones mediante Intune. 
- **Aplicaciones de la tienda**: una aplicación de la tienda es una aplicación que se ha cargado en la tienda Windows, la tienda iOS o la tienda Android. El proveedor de la aplicación de la tienda mantiene y proporciona las actualizaciones de la aplicación. Seleccione la aplicación de la lista de la tienda y agréguela mediante Intune como una aplicación disponible para los usuarios.

Al determinar las aplicaciones necesarias para su organización, tenga en cuenta cómo se integran estas aplicaciones con los servicios en la nube, a qué datos pueden acceder las aplicaciones, si las aplicaciones están disponibles para los usuarios BYOD y si las aplicaciones requieren acceso a internet.

Para obtener más información sobre cómo determinar qué tipo de aplicaciones necesita la organización, consulte **Aplicaciones** dentro de la sección **Requisitos de características** de [Crear un diseño](planning-guide-design.md#feature-requirements).

### <a name="understanding-app-management-and-protection-policies"></a>Información de las directivas de protección y administración de aplicaciones
Intune le permite modificar la funcionalidad de las aplicaciones que implementa para ayudarle a que se ajusten a los requisitos de cumplimiento y las directivas de seguridad de su empresa. Este control le permite determinar cómo se protegen los datos de su compañía. Las aplicaciones administradas de Intune están habilitadas con un amplio conjunto de directivas de protección de aplicaciones móviles, como por ejemplo:

- Restricción de las funciones Copiar y pegar y Guardar como
- Configuración de vínculos web para que se abran dentro de la aplicación Intune Managed Browser
- Habilitación del uso de varias identidades y el acceso condicional de nivel de aplicación

Las aplicaciones administradas de Intune también pueden habilitar la protección de aplicaciones sin necesidad de una inscripción, lo que le ofrece la posibilidad de aplicar directivas de prevención de pérdida de datos sin tener que administrar el dispositivo del usuario. Además, puede incorporar la administración de aplicaciones móviles en las aplicaciones de línea de negocio y móviles mediante el kit de desarrollo de software de aplicaciones de Intune y la herramienta de ajuste de aplicaciones. Para obtener más información sobre estas herramientas, consulte [Guía para desarrolladores de Android acerca del SDK para aplicaciones de Microsoft Intune](app-sdk.md).

### <a name="understanding-licensed-apps"></a>Información sobre el uso de aplicaciones con licencia
Además de las aplicaciones web, las aplicaciones de la tienda y las aplicaciones LOB, también debe conocer las diferencias de las aplicaciones del programa de compras por volumen y las aplicaciones con licencia, como por ejemplo:     
- **Programa de Compras por Volumen de Apple para empresas (iOS y MacOS)**: la App Store de iOS permite comprar varias licencias de una aplicación que quiera ejecutar en la empresa. Comprar varias copias permite administrar de manera eficaz las aplicaciones de la empresa. Para obtener más información, consulte [Administrar aplicaciones de iOS compradas a través de un programa de compras por volumen con Microsoft Intune](vpp-apps-ios.md).
- **Android for Work**: puede asignar aplicaciones para dispositivos Android for Work de forma diferente a cuando las asigna en dispositivos Android estándar. Todas las aplicaciones que instale en Android for Work proceden de Google Play for Work Store. Inicie sesión en la tienda, busque las aplicaciones que desee y apruébelas. La aplicación aparecerá en el nodo Aplicaciones con licencia de Azure Portal. Desde aquí, puede administrar la asignación de la aplicación de la misma manera que asignaría cualquier otra aplicación.
- **Tienda Windows para empresas (Windows 10)**: en Microsoft Store para Empresas puede buscar y comprar aplicaciones para su organización, tanto sueltas como por volumen. Si conecta la tienda a Microsoft Intune, puede administrar las aplicaciones adquiridas por volumen desde Azure Portal. Para más información, vea [Administrar las aplicaciones de Microsoft Store para Empresas](windows-store-for-business.md). 

## <a name="before-you-start"></a>Antes de empezar
Considere los puntos siguientes antes de empezar a agregar y asignar aplicaciones.

- Al agregar y asignar una aplicación desde un almacén, los usuarios finales deben tener una cuenta con el almacén para poder instalar la aplicación.
- Algunas aplicaciones o elementos que asigna pueden depender de aplicaciones iOS integradas. Por ejemplo, si asigna un libro desde la tienda iOS, la aplicación iBooks debe existir en el dispositivo. Si quitó la aplicación integrada iBooks, no puede usar Intune para restablecerla.

## <a name="cloud-storage-space"></a>Espacio de almacenamiento en nube
Todas las aplicaciones que cree mediante el tipo de instalación del instalador de software (por ejemplo, una aplicación de línea de negocio) se empaquetan y cargan en el almacenamiento en la nube de Intune. Una suscripción de prueba de Intune incluye 2 gigabytes (GB) de almacenamiento en nube que sirve para almacenar actualizaciones y aplicaciones administradas. Una suscripción completa incluye 20 GB de espacio de almacenamiento.

Puede adquirir almacenamiento adicional para Intune mediante el método de compra original.  Si el importe se le ha facturado o lo ha abonado con tarjeta de crédito, visite el [portal de administración de suscripciones](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions).  De lo contrario, póngase en contacto con su asociado o agente de ventas.

Estos son los requisitos de espacio de almacenamiento en la nube:

-   Todos los archivos de instalación deben encontrarse en la misma carpeta.
-   El tamaño máximo de archivo para cualquier archivo que cargue es de 2 GB.

## <a name="how-to-create-and-edit-categories-for-apps"></a>Creación y edición de categorías de aplicaciones

Se pueden usar categorías de aplicaciones para ordenar las aplicaciones de forma que sea más fácil para los usuarios encontrarlas en el portal de empresa. Puede asignar una o varias categorías a una aplicación, por ejemplo, **Desarrollador de aplicaciones** o **Communication apps** (Aplicaciones de comunicación).
Al agregar una aplicación a Intune, tiene la opción de seleccionar la categoría que quiera. Use los temas específicos de la plataforma para agregar una aplicación y asignar categorías. Para crear y editar sus propias categorías, use el procedimiento siguiente:

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services (Todos los servicios)** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En la hoja **Intune**, elija **Aplicaciones móviles**.
4. En la carga de trabajo **Mobile Apps**, elija **Configuración** > **Categorías de aplicaciones**.
5. En la hoja **Categorías de aplicaciones**, se muestra una lista de las categorías actuales. Elija una de las acciones siguientes:
    - **Crear una categoría**: seleccione **Agregar** para mostrar la hoja **Crear categoría** y escriba un nombre para la nueva categoría. Los nombres solo pueden escribirse en un solo idioma, Intune no los traduce. Haga clic en **Crear** cuando acabe.
    - **Editar una categoría**: para cualquier categoría de la lista, elija '**...**'. Esta opción muestra un menú emergente que le permite **Anclar al panel** o **Eliminar** la categoría.

## <a name="apps-added-automatically-by-intune"></a>Aplicaciones que Intune agrega automáticamente

Anteriormente, Intune tenía numerosas aplicaciones integradas que se podían asignar rápidamente. Basándonos en los comentarios de los usuarios, se ha quitado esta lista y ya no se verán las aplicaciones integradas.
Sin embargo, si las aplicaciones integradas ya están asignadas, estas seguirán mostrándose en la lista de aplicaciones. Las aplicaciones podrán seguir asignándose según se necesite.
En una versión posterior, vamos a agregar un método sencillo para seleccionar y asignar aplicaciones integradas de Azure Portal.

## <a name="next-steps"></a>Pasos siguientes

Elija uno de los siguientes temas para obtener información sobre cómo agregar aplicaciones ara cada plataforma a Intune:

- [Aplicaciones de Google Play Store](store-apps-android.md)
- [Aplicaciones LOB para Android](lob-apps-android.md)
- [Aplicaciones de App Store](store-apps-ios.md)
- [Aplicaciones LOB para iOS](lob-apps-ios.md)
- [Aplicaciones web (para todas las plataformas)](web-app.md)
- [Aplicaciones de la Tienda de Windows Phone 8.1](store-apps-windows-phone-8-1.md)
- [Aplicaciones de línea de negocio de Windows Phone](lob-apps-windows-phone.md)
- [Aplicaciones de la Tienda Windows](store-apps-windows.md)
- [Aplicación de línea de negocio de Windows](lob-apps-windows.md)
- [Aplicaciones de Office 365 para Windows 10](apps-add-office365.md)
- [Aplicaciones integradas](apps-add-built-in.md)

