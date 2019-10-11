---
title: Administración de libros electrónicos de iOS comprados por volumen
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo puede sincronizar libros comprados por volumen en la tienda de iOS en Intune y luego administrar y realizar el seguimiento de su uso.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f5617074-2384-4812-b913-dc94f64c0818
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3f882272f200e8fc9aa81f36eb28e85893995f11
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724378"
---
# <a name="how-to-manage-ios-ebooks-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Administración de libros electrónicos de iOS comprados a través de un programa de compras por volumen con Microsoft Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

El Programa de Compras por Volumen de Apple (VPP) le permite comprar varias licencias de un libro que desea distribuir a usuarios de su empresa. Puede distribuir libros desde las tiendas para empresas o educación.

Microsoft Intune le ayuda a sincronizar, administrar y asignar libros comprados a través de este programa. Puede importar la información de licencia desde la tienda y hacer un seguimiento de cuántas licencias ha usado.

Los procedimientos para administrar libros son similares a la [administración de aplicaciones de VPP](../vpp-apps-ios.md).

## <a name="manage-volume-purchased-books-for-ios-devices"></a>Administración de libros comprados por volumen para dispositivos iOS
Puede comprar varias licencias de libros iOS mediante el [Programa de Compras por Volumen de Apple para empresas](https://www.apple.com/business/vpp/) o el [Programa de Compras por Volumen de Apple para educación](https://volume.itunes.apple.com/us/store). Este proceso implica configurar una cuenta de VPP de Apple en el sitio web de Apple y cargar el token de VPP de Apple en Intune.  De este modo, puede sincronizar la información de compras por volumen con Intune y hacer el seguimiento del uso de libros comprados por volumen.

## <a name="before-you-start"></a>Antes de empezar
Antes de empezar, obtenga un token de VPP de Apple y cárguelo en la cuenta de Intune. Además:

* Puede asociar hasta 256 tokens de VPP con la cuenta de Intune.
* Si usó anteriormente un token de PCV con otro producto, debe generar uno nuevo para usarlo con Intune.
* La validez de cada token es de un año.
* De forma predeterminada, Intune se sincroniza con el servicio PCV de Apple dos veces al día. Puede iniciar una sincronización manual en cualquier momento.
* Después de importar el token de PCV en Intune, no importe el mismo token en otra solución de administración de dispositivos. Si lo hace, podría perder la asignación de licencias y los registros de usuario.
* Antes de empezar a usar los libros de iOS con Intune, quite todas las cuentas de usuario de VPP existentes creadas con otros proveedores de administración de dispositivos móviles (MDM). Intune no sincroniza esas cuentas de usuario en Intune como medida de seguridad. Intune solo sincroniza los datos del servicio VPP de Apple que se creó mediante Intune.
* Cuando asigne un libro a un dispositivo, dicho dispositivo debe tener instalada la aplicación iBooks integrada. Si no es así, el usuario final deberá volver a instalar la aplicación antes de poder leer el libro. Actualmente no puede usar Intune para restaurar aplicaciones integradas que se hayan quitado.
* Solo se pueden asignar libros del sitio del Programa de Compras por Volumen de Apple. No puede cargar y luego asignar libros creados en la empresa.
* Actualmente no puede asignar libros a las categorías de usuarios finales del mismo modo en que lo hace con las aplicaciones.
* No puede reclamar una licencia una vez que se asigna un libro.
* Si un usuario con un dispositivo elegible intenta primero instalar un libro de VPP, primero debe unirse al Programa de Compras por Volumen de Apple antes de poder instalar un libro. También puede asignar licencias a grupos de seguridad con id. de Apple administrados. Si lo hace, no se pedirá el id. de Apple de los usuarios cuando se instale un libro.
* Los dispositivos deben estar inscritos con la afinidad de usuario, ya que los libros electrónicos solo pueden asignarse a grupos de usuarios.   


## <a name="to-get-and-upload-an-apple-vpp-token"></a>Para obtener y cargar un token de PCV de Apple

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. En el panel **Intune**, seleccione **Aplicaciones cliente**.
1. En la carga de trabajo **Aplicaciones cliente**, seleccione **Configuración** > **Tokens de VPP de iOS**.
2. En la lista del panel de tokens del VPP, haga clic en **Crear**.
3. En el panel **Nuevo token de VPP**, especifique la información siguiente:
    - **Archivo de token de VPP**: asegúrese de registrarse en el Programa de Compras por Volumen para empresas o en el Programa de Compras por Volumen para educación. Luego, descargue el token de VPP de Apple para la cuenta y selecciónelo aquí.
    - **Id. de Apple**: escriba el identificador de Apple de la cuenta asociada con el programa de compras por volumen.
    - **Tipo de cuenta de VPP**: elija **Empresa** o **Educación**.
4. Haga clic en **Crear** cuando acabe.

El token se muestra en el panel de la lista de tokens.


Puede sincronizar los datos que tiene Apple con Intune en cualquier momento al elegir **Sincronizar ahora**.

## <a name="to-assign-a-volume-purchased-app"></a>Para asignar una aplicación comprada por volumen

3. En el panel **Intune**, elija **eBooks**.
1. En la carga de trabajo **Libros electrónicos**, elija **Administrar** > **Todos los libros electrónicos**.
2. En el panel de la lista de libros, elija el libro que quiera asignar y, luego, seleccione " **...** " > **Asignar grupos**.
3. En el panel <*nombre del libro*> - **Grupos asignados**, elija **Administrar** > **Grupos asignados**.
4. Elija **Asignar grupos** y, en el panel **Seleccionar grupos**, elija los grupos de usuarios de Azure AD a los que quiere asignar el libro. Los grupos de dispositivos no son compatibles actualmente.
Elija una acción de asignación de **Disponible** o **Requerido**. 
5. Cuando termine, elija **Guardar**.

## <a name="next-steps"></a>Pasos siguientes

Consulte [Supervisión de aplicaciones](apps-monitor.md) para información que le ayude a supervisar las asignaciones de libros.






