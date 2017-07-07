---
title: "Administración de libros electrónicos de iOS comprados por volumen"
titleSuffix: Intune on Azure
description: "Obtenga información sobre cómo puede sincronizar libros comprados por volumen en la tienda de iOS en Intune y luego administrar y realizar el seguimiento de su uso\"."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5617074-2384-4812-b913-dc94f64c0818
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e23c40eb4c13fd0d2593742c72086fc943fe2b54
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-manage-ios-ebooks-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Administración de libros electrónicos de iOS comprados a través de un programa de compras por volumen con Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

El Programa de Compras por Volumen de Apple (VPP) le permite comprar varias licencias de un libro que desea distribuir a usuarios de su empresa. Puede distribuir libros desde las tiendas para empresas o educación.

Microsoft Intune le ayuda a sincronizar, administrar y asignar libros comprados a través de este programa. Puede importar la información de licencia desde la tienda y hacer un seguimiento de cuántas licencias ha usado.

Los procedimientos para administrar libros son similares a la [administración de aplicaciones de VPP](vpp-apps-ios.md).

## <a name="manage-volume-purchased-books-for-ios-devices"></a>Administración de libros comprados por volumen para dispositivos iOS
Puede comprar varias licencias de libros iOS mediante el [Programa de Compras por Volumen de Apple para empresas](http://www.apple.com/business/vpp/) o el [Programa de Compras por Volumen de Apple para educación](http://volume.itunes.apple.com/us/store). Este proceso implica configurar una cuenta de VPP de Apple en el sitio web de Apple y cargar el token de VPP de Apple en Intune.  De este modo, puede sincronizar la información de compras por volumen con Intune y hacer el seguimiento del uso de libros comprados por volumen.

## <a name="before-you-start"></a>Antes de empezar
Antes de empezar, obtenga un token de VPP de Apple y cárguelo en la cuenta de Intune. Además:

* Puede asociar hasta 256 tokens de VPP con la cuenta de Intune.
* Si usó anteriormente un token de PCV con otro producto, debe generar uno nuevo para usarlo con Intune.
* La validez de cada token es de un año.
* De forma predeterminada, Intune se sincroniza con el servicio PCV de Apple dos veces al día. Puede iniciar una sincronización manual en cualquier momento.
* Después de importar el token de PCV en Intune, no importe el mismo token en otra solución de administración de dispositivos. Si lo hace, podría perder la asignación de licencias y los registros de usuario.
* Antes de empezar a usar los libros de iOS con Intune, quite todas las cuentas de usuario de VPP existentes creadas con otros proveedores de administración de dispositivos móviles (MDM). Intune no sincroniza esas cuentas de usuario en Intune como medida de seguridad. Intune solo sincroniza los datos del servicio VPP de Apple que se creó mediante Intune.
* Actualmente, solo puede asignar libros como una instalación **requerida**. Al asignar el libro como una instalación **requerida**, cada usuario que instala dicho libro usa una licencia.
* Cuando asigne un libro a un dispositivo, dicho dispositivo debe tener instalada la aplicación iBooks integrada. Si no es así, el usuario final deberá volver a instalar la aplicación antes de poder leer el libro. Actualmente no puede usar Intune para restaurar aplicaciones integradas que se hayan quitado.
* Solo se pueden asignar libros del sitio del Programa de Compras por Volumen de Apple. No puede cargar y luego asignar libros creados en la empresa.
* Actualmente no puede asignar libros a las categorías de usuarios finales del mismo modo en que lo hace con las aplicaciones.
* No puede reclamar una licencia una vez que se asigna un libro.
* Si un usuario con un dispositivo elegible intenta primero instalar un libro de VPP, primero debe unirse al Programa de Compras por Volumen de Apple antes de poder instalar un libro. También puede asignar licencias a grupos de seguridad con id. de Apple administrados. Si lo hace, no se pedirá el id. de Apple de los usuarios cuando se instale un libro.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Para obtener y cargar un token de PCV de Apple

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Aplicaciones móviles**.
1.  En la carga de trabajo **Aplicaciones móviles**, elija **Instalación** > **Tokens de VPP de iOS**.
2.  En la lista de la hoja de tokens del PCV, haga clic en **Agregar**.
3.  En la hoja **Nuevo token de VPP**, especifique la información siguiente:
    - **Archivo de token de VPP**: asegúrese de registrarse en el Programa de Compras por Volumen para empresas o en el Programa de Compras por Volumen para educación. Luego, descargue el token de VPP de Apple para la cuenta y selecciónelo aquí.
    - **Id. de Apple**: escriba el identificador de Apple de la cuenta asociada con el programa de compras por volumen.
    - **Tipo de cuenta de VPP**: elija **Empresa** o **Educación**.
4. Cuando haya terminado, haga clic en **Cargar**.

El token se muestra en la hoja de la lista de tokens.


Puede sincronizar los datos que tiene Apple con Intune en cualquier momento al elegir **Sincronizar ahora**.

## <a name="to-assign-a-volume-purchased-app"></a>Para asignar una aplicación comprada por volumen

1. En la carga de trabajo **Libros electrónicos**, elija **Administrar** > **Todos los libros electrónicos**.
2. En la hoja de la lista de libros, elija el libro que desea asignar y, luego, elija "**...**" > **Asignar grupos**.
3. En la hoja <*nombre del libro*> - **Grupos asignados**, elija **Administrar** > **Grupos asignados**.
4. Elija **Asignar grupos** y, en la hoja **Seleccionar grupos**, elija los grupos de usuarios de Azure AD a los que quiere asignar el libro. Los grupos de dispositivos no son compatibles actualmente.
Elija una acción de asignación de **Requerido**. 
5. Cuando termine, elija **Guardar**.

## <a name="next-steps"></a>Pasos siguientes

Consulte [Supervisión de aplicaciones](apps-monitor.md) para información que le ayude a supervisar las asignaciones de libros.






