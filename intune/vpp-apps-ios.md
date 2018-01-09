---
title: "Administración de aplicaciones iOS compradas por volumen | Microsoft Docs"
titlesuffix: Azure portal
description: "Obtenga información sobre cómo puede sincronizar aplicaciones compradas por volumen en la tienda de iOS en Intune y luego administrar y realizar el seguimiento de su uso\"."
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 12/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f820be41c532384f9f2db57e0e0e497a05307d73
ms.sourcegitcommit: 06abc5ccc8b868c9ff3ad3f8f62473a87b2da481
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="how-to-manage-ios-apps-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Administrar aplicaciones de iOS compradas a través de un programa de compras por volumen con Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La App Store de iOS permite comprar varias licencias de una aplicación que quiera ejecutar en la empresa. Comprar varias copias permite administrar de manera eficaz las aplicaciones de la empresa.

Microsoft Intune le ayuda a administrar varias copias de las aplicaciones que se adquirieron a través de este programa de las siguientes maneras:

- Informes sobre la información de licencia desde la tienda de aplicaciones.
- Realizando un seguimiento de cuántas licencias ha usado.
- Le ayudamos a no instalar más copias de la aplicación que las que tiene.

Existen dos métodos que puede usar para asignar aplicaciones compradas por volumen:

### <a name="device-licensing"></a>Licencias de dispositivo

Cuando asigna una aplicación a los dispositivos, se usa una licencia de aplicación y permanece asociada con el dispositivo al que se le ha asignado.

Cuando asigna aplicaciones compradas por volumen a un dispositivo, el usuario final del dispositivo no tiene que proporcionar un id. de Apple para tener acceso a la tienda.

### <a name="user-licensing"></a>Licencias de usuario

Cuando asigna una aplicación a un usuario, se usa una licencia de aplicación para el usuario y se asocia con este. La aplicación se puede ejecutar en varios dispositivos del usuario (con un límite controlado por Apple).

Cuando asigne una aplicación comprada por volumen a los usuarios, cada usuario final debe tener un ID de Apple válido y único para acceder al App Store.

Además, puede sincronizar, administrar y asignar los libros que haya adquirido a través de la tienda del Programa de Compras por Volumen (VPP) de Apple con Intune. Para obtener más información, consulte [Administración de libros electrónicos de iOS comprados a través de un programa de compras por volumen](vpp-ebooks-ios.md).

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Administrar aplicaciones compradas por volumen para dispositivos iOS

### <a name="supports-apple-volume-purchase-program-volume-purchased-apps-for-ios-devices"></a>Admite las aplicaciones compradas por volumen del Programa de Compras por Volumen de Apple para dispositivos iOS

Compre varias licencias para aplicaciones iOS mediante el [Programa de compras por volumen de Apple para empresas](http://www.apple.com/business/vpp/) o el [Programa de compras por volumen de Apple para educación](http://volume.itunes.apple.com/us/store). Este proceso implica configurar una cuenta de VPP de Apple en el sitio web de Apple y cargar el token de VPP de Apple en Intune.  De este modo, puede sincronizar la información de compras por volumen con Intune y hacer el seguimiento del uso de aplicaciones compradas por volumen.

### <a name="supports-business-to-business-volume-purchased-apps-for-ios-devices"></a>Admite las aplicaciones compradas por volumen de negocio a negocio para dispositivos iOS

Además, los desarrolladores de terceros también pueden distribuir aplicaciones de forma privada a miembros autorizados del Programa de Compras por Volumen para Empresas, especificados en iTunes Connect. Estos miembros pueden iniciar sesión en la tienda de aplicaciones del Programa de Compras por Volumen y comprar aplicaciones. Las aplicaciones del VPP para empresas que haya comprado el usuario final se sincronizarán con sus inquilinos de Intune.

## <a name="before-you-start"></a>Antes de empezar
Antes de empezar, necesita obtener un token de VPP de Apple y cargarlo en la cuenta de Intune. Además, debe comprender los siguientes criterios:

* Puede asociar varios tokens de VPP con la cuenta de Intune.
* Si usó anteriormente un token de PCV con otro producto, debe generar uno nuevo para usarlo con Intune.
* La validez de cada token es de un año.
* De forma predeterminada, Intune se sincroniza con el servicio PCV de Apple dos veces al día. Puede iniciar una sincronización manual en cualquier momento.
* Antes de empezar a usar el VPP de Apple con Intune, quite todas las cuentas de usuario de VPP existentes creadas con otros proveedores de administración de dispositivos móviles (MDM). Intune no sincroniza esas cuentas de usuario en Intune como medida de seguridad. Intune solo sincroniza los datos del servicio VPP de Apple que se ha creado mediante Intune.
* Intune admite la adición de hasta 256 tokens de VPP.
* El Programa Perfil de inscripción de dispositivos (DEP) de Apple automatiza la inscripción de la administración de dispositivos móviles (MDM). Puede usar DEP para configurar dispositivos corporativos sin tocarlos. Puede inscribirse en el programa DEP con la misma cuenta de agente de programa que usó con el VPP de Apple. El identificador del programa de implementación de Apple es único para los programas que aparecen en el sitio web [Deployment Programmes](https://deploy.apple.com) (Programas de implementación) de Apple y no se puede usar para iniciar sesión en los servicios de Apple, como la tienda iTunes.
* Cuando asigne aplicaciones de VPP con el modelo de licencias de usuario a los usuarios o dispositivos (con la afinidad de usuario), cada usuario de Intune necesita asociarse con un único id. de Apple o una dirección de correo electrónico cuando acepte los términos y condiciones de Apple en su dispositivo. Asegúrese de que cuando configure un dispositivo para un nuevo usuario de Intune, lo configura con esa dirección de correo electrónico o con el Id. de Apple únicos del usuario. La dirección de correo electrónico o el id. de Apple y el usuario de Intune forman un único par y pueden usarse en hasta cinco dispositivos.
* Un token de VPP solo se admite para su uso en una cuenta de Intune a la vez. No vuelva a usar el mismo token de VPP para varios inquilinos de Intune.
* Cuando asigne aplicaciones de VPP con el modelo de licencias de usuario a los usuarios o dispositivos (con la afinidad de usuario), cada usuario de Intune necesita asociarse con un único id. de Apple o una dirección de correo electrónico cuando acepte los términos y condiciones de Apple en su dispositivo.
Asegúrese de que cuando configure un dispositivo para un nuevo usuario de Intune, lo configura con esa dirección de correo electrónico o id. de Apple únicos del usuario. La dirección de correo electrónico o el ID de Apple y el usuario de Intune forman un único par y pueden usarse en hasta cinco dispositivos.

>[!IMPORTANT]
>Después de importar el token de PCV en Intune, no importe el mismo token en otra solución de administración de dispositivos. Si lo hace, podría perder la asignación de licencias y los registros de usuario.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Para obtener y cargar un token de PCV de Apple

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
1.  En la hoja **Intune**, elija **Aplicaciones móviles** > **Tokens de VPP de iOS** en **Configuración**.
2.  En la lista de la hoja de tokens del VPP, seleccione **Crear**.
4. En la hoja **Crear token de VPP**, especifique la información siguiente:
    - **Archivo de token de VPP**: si aún no lo ha hecho, regístrese en el Programa de compras por volumen para empresas o el Programa para educación. Después de registrarse, descargue el token de VPP de Apple para la cuenta y selecciónelo aquí.
    - **Id. de Apple**: escriba el identificador de Apple de la cuenta asociada con el programa de compras por volumen.
    - **País o región**: seleccione el país de la tienda del VPP.  Intune sincroniza las aplicaciones de VPP para todas las configuraciones regionales desde la instancia de App Store del país de VPP especificada.
        > [!WARNING]  
        > Al cambiar el país, los metadatos de las aplicaciones se actualizarán y almacenarán la dirección URL en la siguiente sincronización con el servicio de Apple para las aplicaciones creadas con ese token. La aplicación no se actualizará si no existe en la tienda del nuevo país.

    - **Tipo de cuenta de VPP**: elija **Empresa** o **Educación**.
    - **Actualizaciones automáticas de la aplicación**: Active la opción para habilitar las actualizaciones automáticas. Si está habilitada, Intune actualiza todas las aplicaciones compradas para el token especificado a través del servicio de Intune cuando se registra el dispositivo.
Se detectarán las actualizaciones de la aplicación de VPP dentro del App Store y se insertarán automáticamente en el dispositivo cuando este se registre.
4. Cuando haya terminado, seleccione **Cargar**.

El token se muestra en la hoja de la lista de tokens.

Puede sincronizar los datos que tiene Apple con Intune en cualquier momento al elegir **Sincronizar ahora**.

## <a name="to-assign-a-volume-purchased-app"></a>Para asignar una aplicación comprada por volumen

1.  En la hoja **Intune**, elija **Aplicaciones móviles** > **Aplicaciones** en **Administrar**.
2.  En la hoja de la lista de aplicaciones, elija la aplicación que quiera asignar y seleccione **Asignaciones**.
3.  En la hoja ***Nombre de la aplicación*** - **Asignaciones**, elija **Seleccionar grupos** y, en la hoja **Seleccionar grupos**, elija los grupos de dispositivos o de usuarios de Azure AD a los que quiere asignar la aplicación.
5.  Para cada grupo que ha seleccionado, pulse las opciones siguientes:
    - **Tipo**: elija si la aplicación estará **disponible** (los usuarios finales pueden instalar la aplicación desde el Portal de empresa) o será **necesaria** (la aplicación se instalará automáticamente para los usuarios finales).
    - **Tipo de licencia**: elija **Licencias de usuario** o **Licencias de dispositivo**.
6.  Cuando termine, elija **Guardar**.


>[!NOTE]
>La lista de aplicaciones mostradas está asociada con un token. Si tiene una aplicación que está asociada con varios tokens de VPP, verá la misma aplicación mostrándose varias veces; una por cada token.

## <a name="end-user-prompts-for-vpp"></a>Solicitudes de VPP al usuario final

El usuario final recibirá solicitudes para que instale la aplicación de VPP en diferentes situaciones. En la tabla siguiente se explica cada condición:

| # | Escenario                                | Invitar al programa VPP de Apple                              | Solicitud de instalación de la aplicación | Solicitud del ID de Apple |
|---|--------------------------------------------------|-------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------------|
| 1 | BYOD: usuario con licencia                             | esté                                                                                               | esté                                           | esté                                 |
| 2 | Corp: usuario con licencia (dispositivo no supervisado)     | esté                                                                                               | esté                                           | esté                                 |
| 3 | Corp: usuario con licencia (dispositivo supervisado)         | esté                                                                                               | N                                           | esté                                 |
| 4 | BYOD: dispositivo con licencia                           | N                                                                                               | esté                                           | N                                 |
| 5 | Corp: dispositivo con licencia (dispositivo no supervisado)                           | N                                                                                               | esté                                           | N                                 |
| 6 | Corp: dispositivo con licencia (dispositivo supervisado)                           | N                                                                                               | N                                           | N                                 |
| 7 | Pantalla completa (dispositivo supervisado): dispositivo con licencia | N                                                                                               | N                                           | N                                 |
| 8 | Pantalla completa (dispositivo supervisado): usuario con licencia   | --- | ---                                          | ---                                |

> [!Note]  
> No se recomienda asignar aplicaciones de VPP a dispositivos en modo de pantalla completa que usen licencias de usuario de VPP.

## <a name="further-information"></a>Más información

Para reclamar una licencia, debe cambiar la acción de asignación a **Desinstalar**. La licencia se recupera cuando se desinstala la aplicación. Si quita una aplicación que se ha asignado a un usuario, Intune intentará reclamar todas las licencias de aplicación que estaban asociadas al usuario.

<!-- 820879 -->You can delete a iOS Volume Purchasing Program (VPP) token using the console. This may be necessary when you have duplicate instances of a VPP token. Deleting a token will also delete any associated apps and assignment. However, deleting a token does not revoke app licenses. Intune cannot revoke app licenses after a token has been deleted. 

Si un usuario con un dispositivo válido intenta primero instalar una aplicación de VPP en un dispositivo, se le pedirá que se una al Programa de Compras por Volumen de Apple. Debe unirse para poder continuar con la instalación de la aplicación. La invitación para unirse al Programa de Compras por Volumen de Apple requiere que el usuario pueda usar la aplicación iTunes en el dispositivo iOS. Si ha configurado una directiva para deshabilitar la aplicación iTunes Store, las licencias de aplicaciones VPP basadas en usuario no funcionan. La solución es quitar la directiva para permitir la aplicación iTunes o usar licencias basadas en dispositivos.

## <a name="next-steps"></a>Pasos siguientes

Consulte [Supervisión de aplicaciones](apps-monitor.md) para obtener información que le ayude a supervisar las asignaciones de aplicaciones.
