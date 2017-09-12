---
title: Administrar aplicaciones de iOS compradas por volumen
titlesuffix: Azure portal
description: "Obtenga información sobre cómo puede sincronizar aplicaciones compradas por volumen en la tienda de iOS en Intune y luego administrar y realizar el seguimiento de su uso\"."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: addcc2c9a939b8dc62d708b3f9f000cb7c09cef3
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Administrar aplicaciones de iOS compradas a través de un programa de compras por volumen con Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La App Store de iOS permite comprar varias licencias de una aplicación que quiera ejecutar en la empresa. Comprar varias copias de una aplicación le ayuda a reducir la carga administrativa relacionada con el seguimiento de varias copias compradas de las aplicaciones.

Microsoft Intune le ayuda a administrar las aplicaciones que ha adquirido a través de este programa de las maneras siguientes:

- Informes sobre la información de licencia desde el App Store
- Realizando un seguimiento de cuántas licencias ha usado
- Le ayudamos a no instalar más copias de la aplicación que las que tiene

Existen dos métodos que puede usar para asignar aplicaciones compradas por volumen:

### <a name="device-licensing"></a>Licencias de dispositivo

Cuando asigna una aplicación a los dispositivos, se usa una licencia de aplicación y permanece asociada con el dispositivo al que se le ha asignado.
Cuando asigna aplicaciones compradas por volumen a un dispositivo, el usuario final del dispositivo no tiene que proporcionar un id. de Apple para tener acceso a la tienda. 



### <a name="user-licensing"></a>Licencias de usuario

Cuando asigna una aplicación a los usuarios, se usa una licencia de aplicación para el usuario y se asocia con este. La aplicación se puede ejecutar en varios dispositivos del usuario (con un límite controlado por Apple).
Cuando asigne una aplicación comprada por volumen a los usuarios, cada usuario final debe tener un ID de Apple válido y único para acceder al App Store.


Además, puede sincronizar, administrar y asignar los libros que haya adquirido a través de la tienda del Programa de Compras por Volumen de Apple con Intune. Para obtener más información, consulte [Administración de libros electrónicos de iOS comprados a través de un programa de compras por volumen](vpp-ebooks-ios.md).


## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Administrar aplicaciones compradas por volumen para dispositivos iOS
Compre varias licencias para aplicaciones iOS mediante el [Programa de compras por volumen de Apple para empresas](http://www.apple.com/business/vpp/) o el [Programa de compras por volumen de Apple para educación](http://volume.itunes.apple.com/us/store). Este proceso implica configurar una cuenta de VPP de Apple en el sitio web de Apple y cargar el token de VPP de Apple en Intune.  De este modo, puede sincronizar la información de compras por volumen con Intune y hacer el seguimiento del uso de aplicaciones compradas por volumen.

## <a name="before-you-start"></a>Antes de empezar
Antes de empezar, necesita obtener un token de VPP de Apple y cargarlo en la cuenta de Intune. Además, debe comprender los siguientes criterios:

* Puede asociar varios tokens de programa de compra por volumen con su cuenta de Intune.
* Si usó anteriormente un token de PCV con otro producto, debe generar uno nuevo para usarlo con Intune.
* La validez de cada token es de un año.
* De forma predeterminada, Intune se sincroniza con el servicio PCV de Apple dos veces al día. Puede iniciar una sincronización manual en cualquier momento.
* Antes de empezar a usar el PCV de iOS con Intune, quite todas las cuentas de usuario de PCV existentes creadas con otros proveedores de administración de dispositivos móviles (MDM). Intune no sincroniza esas cuentas de usuario en Intune como medida de seguridad. Intune solo sincroniza los datos del servicio VPP de Apple que se ha creado mediante Intune.
* Intune admite la adición de hasta 256 tokens de VPP.
* Si asigna una aplicación comprada por volumen para un dispositivo inscrito mediante un perfil de inscripción de dispositivo o Apple Configurator, solo las aplicaciones que están destinadas a los dispositivos funcionan. No puede asignar aplicaciones compradas por volumen a los usuarios de un dispositivo de DEP, que no tiene ninguna afinidad de usuario.
Esto se debe a que las licencias de usuario VPP de iOS permiten que miles de dispositivos puedan inscribirse usando la misma cuenta de usuario. Las licencias de usuario VPP de iOS permiten que un usuario final instale una aplicación en entre 5 y 10 dispositivos.
Esto significa que los primeros dispositivos inscritos mediante DEM recibirán la instalación de la aplicación de VPP mediante una licencia de usuario, mientras que los demás dispositivos no podrán obtener la aplicación.
* Un token de VPP solo se admite para su uso en una cuenta de Intune a la vez. No vuelva a usar el mismo token de VPP para varios inquilinos de Intune.
* Cuando asigne aplicaciones de VPP con el modelo de licencias de usuario a los usuarios o dispositivos (con la afinidad de usuario), cada usuario de Intune necesita asociarse con un único id. de Apple o una dirección de correo electrónico cuando acepte los términos y condiciones de Apple en su dispositivo.
Asegúrese de que cuando configure un dispositivo para un nuevo usuario de Intune, lo configura con esa dirección de correo electrónico o id. de Apple únicos del usuario. La dirección de correo electrónico o el id. de Apple y el usuario de Intune forman un único par y pueden usarse en hasta 5 dispositivos.

>[!IMPORTANT]
>Después de importar el token de PCV en Intune, no importe el mismo token en otra solución de administración de dispositivos. Si lo hace, podría perder la asignación de licencias y los registros de usuario.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Para obtener y cargar un token de PCV de Apple

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Aplicaciones móviles**.
1.  En la carga de trabajo **Aplicaciones móviles**, elija **Instalación** > **Tokens de VPP de iOS**.
2.  En la lista de la hoja de tokens del PCV, haga clic en **Agregar**.
3.  En la hoja **Nuevo token de VPP**, especifique la información siguiente:
    - **Archivo de token de VPP**: si aún no lo ha hecho, regístrese en el Programa de compras por volumen para empresas o el Programa para educación. Después de registrarse, descargue el token de VPP de Apple para la cuenta y selecciónelo aquí.
    - **Id. de Apple**: escriba el identificador de Apple de la cuenta asociada con el programa de compras por volumen.
    - **Tipo de cuenta de VPP**: elija **Empresa** o **Educación**.
4. Cuando haya terminado, haga clic en **Cargar**.

El token se muestra en la hoja de la lista de tokens.


Puede sincronizar los datos que tiene Apple con Intune en cualquier momento al elegir **Sincronizar ahora**.

> [!NOTE]
> Microsoft Intune solo sincroniza la información de las aplicaciones, que están disponibles públicamente en iTunes Store. Las **aplicaciones B2B personalizadas para iOS** todavía no son compatibles. Si el escenario tiene como destino esas aplicaciones, no se sincroniza la información de las aplicaciones.

## <a name="to-assign-a-volume-purchased-app"></a>Para asignar una aplicación comprada por volumen

1.  En la carga de trabajo **Mobile Apps**, pulse **Administrar** > **Licencias de aplicaciones**.
2.  En la hoja de la lista de aplicaciones, elija la aplicación que quiera asignar y seleccione "**...**" > **Asignar grupos**.
3.  En la hoja *<app name>* - **Asignaciones**, pulse **Administrar** > **Asignaciones**.
4.  Pulse **Seleccionar grupos** y, en la hoja **Seleccionar grupos**, pulse los grupos de dispositivos o usuarios de Azure AD a los que quiere asignar la aplicación.
5.  Para cada grupo que ha seleccionado, pulse las opciones siguientes:
    - **Tipo**: elija si la aplicación estará **Disponible** (los usuarios finales pueden instalar la aplicación del portal de empresa) o será **Necesaria** (los usuarios finales tendrán automáticamente la aplicación instalada).
    - **Tipo de licencia**: elija **Licencias de usuario** o **Licencias de dispositivo**.
6.  Cuando termine, elija **Guardar**.


>[!NOTE]
>La lista de aplicaciones mostradas está asociada con un token. Si tiene una aplicación que está asociada con varios tokens de VPP, verá la misma aplicación mostrándose varias veces; una por cada token.

## <a name="further-information"></a>Más información

Para reclamar una licencia, debe cambiar la acción de asignación a Desinstalar. La licencia se recupera cuando se desinstala la aplicación. Si quita una aplicación que se ha asignado a un usuario, Intune intentará reclamar todas las licencias de aplicación que estaban asociadas al usuario.

Si un usuario con un dispositivo válido intenta primero instalar una aplicación de VPP en un dispositivo, se le pedirá que se una al Programa de Compras por Volumen de Apple. Debe unirse para poder continuar con la instalación de la aplicación. La invitación para unirse al Programa de Compras por Volumen de Apple requiere que el usuario pueda usar la aplicación iTunes en el dispositivo iOS. Si ha configurado una directiva para deshabilitar la aplicación iTunes Store, las licencias de aplicaciones VPP basadas en usuario no funcionan. La solución es quitar la directiva para permitir la aplicación iTunes o usar licencias basadas en dispositivos.



## <a name="next-steps"></a>Pasos siguientes

Consulte [Supervisión de aplicaciones](apps-monitor.md) para obtener información que le ayude a supervisar las asignaciones de aplicaciones.