---
title: Configuración de diseño de la pantalla principal de Microsoft Intune para dispositivos que ejecutan iOS
titleSuffix: ''
description: Conozca la configuración de Microsoft Intune que puede usar para personalizar la pantalla principal y la base de los dispositivos que ejecutan iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3361ce41dfa95de0cb1a7a3bdbdbd74e7d6d5edf
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31832568"
---
# <a name="microsoft-intune-home-screen-layout-settings-for-devices-running-ios"></a>Configuración de diseño de la pantalla principal de Microsoft Intune para dispositivos que ejecutan iOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Use estos valores para configurar el diseño de aplicaciones y carpetas en la base y la pantalla principal de los dispositivos que ejecutan iOS.

Los dispositivos con iOS con un perfil asignado deben estar en modo supervisado y ejecutar iOS 9.3 o versiones posteriores.

1. Desde [Intune en Azure Portal](https://portal.azure.com), vaya a [**Características del dispositivo** en el área de configuración de dispositivos](device-features-configure.md).
2. En el panel **Características del dispositivo**, elija **Diseño de pantalla principal (solo supervisado)**.
3. En el panel **Diseño de pantalla principal (solo supervisado)**, elija si quiere configurar los diseños de la **Base** o las **Páginas**.

## <a name="add-items-to-the-dock"></a>Agregar elementos a la base

En el panel **Base**, puede agregar hasta seis elementos o carpetas a la base de la pantalla de iOS. En cambio, muchos dispositivos admiten menos elementos; por ejemplo, los dispositivos iPhone admiten hasta cuatro elementos. En este caso, en el dispositivo se muestran solo los primeros cuatro elementos que ha configurado.

1. Elija **Agregar** para agregar un elemento a la base.
2. En el panel **Agregar fila**, elija si quiere agregar una **Aplicación** o una **Carpeta**.
3. Con la información de este tema, configure las aplicaciones y las carpetas que quiere que aparezcan en la base.
4. Siga agregando elementos. Cuando termine, haga clic en **Aceptar** en cada página hasta que vuelva a la página **Crear perfil**. Elija **Crear**.

>[!TIP]
> Puede arrastrar y soltar elementos en cualquier lista de las páginas de la pantalla principal para reordenarlos.

### <a name="example"></a>Ejemplo

En este ejemplo, se configuró la pantalla de la base para mostrar solo las aplicaciones Safari, Correo y Acciones. En la imagen siguiente, se selecciona la aplicación Correo para mostrar sus propiedades:

![Configuración de base de iOS de ejemplo](./media/FfFiUcP.png)

Cuando asigna la directiva a un dispositivo iPhone, el resultado es una base similar a esta captura de pantalla:

![Diseño de base de iOS de ejemplo en iPhone](./media/bAgCe8F.png)

## <a name="add-home-screen-pages"></a>Agregar páginas de pantalla principal

Agregue las páginas que quiere que aparezcan en la pantalla principal y las aplicaciones que aparecen en cada página. Las aplicaciones que agrega a una página se organizan de izquierda a derecha, según el orden especificado en la lista. Si agrega más aplicaciones que las que caben en una página, se mueven a una página posterior.

1. En el panel **Páginas**, elija **Agregar**.
2. En el panel **Agregar fila**, escriba un **Nombre de página**. Este nombre se usa como referencia en Azure Portal y *no se muestra* en el dispositivo iOS.
3. Elija **Agregar** y, luego, elija si desea agregar una **aplicación** o una **carpeta** a la página.
4. Con la información de este tema, configure las aplicaciones y las carpetas que quiere que aparezcan en la página.

### <a name="example"></a>Ejemplo

En este ejemplo, configuró una página nueva llamada **Contoso**. En esta página solo se muestran las aplicaciones Buscar amigos y Configuración. En la imagen siguiente, se selecciona la aplicación Configuración para mostrar sus propiedades:

![Ejemplo de configuración de pantalla principal de iOS](./media/Jc2OxyX.png)

Cuando asigna la directiva a un dispositivo iPhone, el resultado es una página similar a esta captura de pantalla:

![Dispositivo iOS con la pantalla principal modificada](./media/Bd37PHa.png)

## <a name="how-to-add-an-app-to-the-list"></a>Cómo agregar una aplicación a la lista

1. Escriba el **nombre de la aplicación**. Este nombre se usa como referencia en Azure Portal y *no se muestra* en el dispositivo iOS.
2. Escriba el **Identificador del lote de aplicaciones** de la aplicación que quiere mostrar. Consulte **Bundle ID reference for built-in iOS apps** (Referencia de identificador de lote para aplicaciones iOS integrada) más adelante en este tema para obtener ayuda.
3. Haga clic en **Aceptar** y, luego, siga agregando hasta un máximo de **6** elementos en la base del dispositivo y **60** para una página del dispositivo.
4. Cuando haya terminado, haga clic en **Aceptar**.

## <a name="how-to-add-a-folder-to-the-list"></a>Cómo agregar una carpeta a la lista

Las aplicaciones que agrega a una página en una carpeta se organizan de izquierda a derecha, según el orden especificado en la lista. Si agrega más aplicaciones que las que caben en una página, se mueven a una página posterior.

1. Escriba el **nombre de la carpeta**. Este nombre aparece en el dispositivo de los usuarios.
2. Elija **Agregar** para crear una página en la carpeta. Puede agregar hasta 20 páginas.
3. En el panel **Agregar fila**, escriba un nombre para la página. Este nombre se usa como referencia en Azure Portal y *no se muestra* en el dispositivo iOS.
3. Escriba el **nombre de la aplicación**. Este nombre se usa como referencia en Azure Portal y *no se muestra* en el dispositivo iOS.
2. Escriba el **Identificador del lote de aplicaciones** de la aplicación que quiere mostrar. Consulte **Cómo agregar una aplicación a la lista** para obtener ayuda.
3. Seleccione **Agregar**. Puede agregar hasta 60 elementos.
4. Cuando haya terminado, haga clic en **Aceptar**.


## <a name="bundle-id-reference-for-built-in-ios-apps"></a>Referencia de identificador de lote para aplicaciones iOS integradas

En esta lista se muestra el identificador de lote de algunas aplicaciones iOS comunes integradas. Póngase en contacto con el proveedor de software para encontrar el identificador de lote de otras aplicaciones.

|||
|-|-|
|Nombre de la aplicación|Identificador de lote|
|Tienda de aplicaciones|com.apple.AppStore|
|Calculadora|com.apple.calculator|
|Calendario|com.apple.mobilecal|
|Cámara|com.apple.camera|
|Reloj|com.apple.mobiletimer|
|Compass|com.apple.compass|
|Contactos|com.apple.MobileAddressBook|
|FaceTime|com.apple.facetime|
|Buscar amigos|com.apple.mobileme.fmf1|
|Buscar mi iPhone|com.apple.mobileme.fmip1|
|Centro de juegos|com.apple.gamecenter|
|GarageBand|com.apple.mobilegarageband|
|Mantenimiento|com.apple.Health|
|iBooks|com.apple.iBooks|
|iTunes Store|com.apple.MobileStore|
|iTunes U|com.apple.itunesu|
|Keynote|com.apple.Keynote|
|Mail|com.apple.mobilemail|
|Asignaciones|com.apple.Maps|
|Mensajes|com.apple.MobileSMS|
|Música|com.apple.Music|
|Noticias|com.apple.news|
|Notas|com.apple.mobilenotes|
|Números|com.apple.Numbers|
|Páginas|com.apple.Pages|
|Photo Booth|com.apple.Photo-Booth|
|Fotos|com.apple.mobileslideshow|
|Podcasts|com.apple.podcasts|
|Recordatorios|com.apple.reminders|
|Safari|com.apple.mobilesafari|
|Configuración|com.apple.Preferences|
|Acciones|com.apple.stocks|
|Sugerencias|com.apple.tips|
|Vídeos|com.apple.videos|
|VoiceMemos|com.apple.VoiceMemos|
|Wallet|com.apple.Passbook|
|Inspección|com.apple.Bridge|
|Clima|com.apple.weather|


## <a name="next-steps"></a>Pasos siguientes

Ahora puede asignar el perfil de dispositivo a los grupos que elija. Para obtener más información, vea [Asignación de perfiles de dispositivo](device-profile-assign.md).
