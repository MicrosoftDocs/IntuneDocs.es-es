---
title: "Administración de aplicaciones iOS adquiridas por volumen"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune en Azure: Obtenga información sobre cómo sincronizar aplicaciones adquiridas por volumen App Store de iOS en Intune y,luego, administrarlas y realizar un seguimiento de su uso."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: ff43a0be6ebc124bb7e52e5be31e89985ce32166
ms.contentlocale: es-es
ms.lasthandoff: 04/24/2017

---

# <a name="how-to-manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Administración de aplicaciones iOS compradas a través de un programa de compras por volumen con Microsoft Intune


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

La App Store de iOS permite comprar varias licencias de una aplicación que quiera ejecutar en la empresa. Esto ayuda a reducir la carga administrativa relacionada con el seguimiento de varias copias compradas de las aplicaciones.

Microsoft Intune ayuda a administrar las aplicaciones que se compran a través de este programa. Para ello, importa la información de licencia desde la App Store, realiza el seguimiento de la cantidad de licencias usadas y le impide instalar más copias de la aplicación de las que posee.

Adicionalmente, puede sincronizar, administrar y asignar los libros que haya adquirido a través de la tienda del programa de compras por volumen de Apple con Intune y asignarlos a los usuarios. Utilice la carga de trabajo **Libros** del portal de Intune para administrar libros. Los procedimientos para administrar libros son los mismos que utiliza para administrar aplicaciones.
Para ello, debe haber cargado un token del Programa de Compras por Volumen de Apple. Actualmente, solo se pueden asignar libros como una instalación **Requerida**.
Al asignar un libro a un dispositivo, este debe tener instalada la aplicación iBooks integrada instalada. Si no es así, el usuario final debe volver a instalar la aplicación para poder leer el libro. Actualmente no se puede usar Intune para restaurar aplicaciones integradas quitadas.


## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Administrar aplicaciones compradas por volumen para dispositivos iOS
Puede comprar varias licencias para aplicaciones de iOS a través del [Programa de Compras por Volumen para Empresa de Apple](http://www.apple.com/business/vpp/) o el [Programa de Compras por Volumen para Educación de Apple](http://volume.itunes.apple.com/us/store). Esto implica configurar una cuenta de PCV de Apple en el sitio web de Apple y cargar el token de PCV de Apple en Intune.  De este modo, puede sincronizar la información de compras por volumen con Intune y hacer el seguimiento del uso de aplicaciones compradas por volumen.

## <a name="before-you-start"></a>Antes de empezar
Antes de empezar, es necesario obtener un token de PCV de Apple y cargarlo en su cuenta de Intune. Además, debe comprender lo siguiente:

* Puede asociar varios tokens del programa de compras por volumen con la cuenta de Intune.
* Si anteriormente usó un token del PCV con otro producto, debe generar un nuevo token para usar con Intune.
* La validez de cada token es de un año.
* De forma predeterminada, Intune se sincroniza con el servicio PCV de Apple dos veces al día. Puede iniciar una sincronización manual en cualquier momento.
* Después de haber importado el token de PCV a Intune, no importe el mismo token a cualquier otra solución de administración de dispositivos. Si lo hace, se podría producir la pérdida de registros de usuario y asignación de licencias.
* Antes de empezar a usar PCV de iOS con Intune, quite todas las cuentas de usuario de PCV existentes creadas con otros proveedores de administración (MDM) de dispositivos móviles (MDM). Como medida de seguridad, Intune no sincronizará esas cuentas de usuario en Intune. Intune solo sincronizará datos del servicio de PCV de Apple que Intune creó.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Para obtener y cargar un token del PCV de Apple

1. Inicie sesión en Azure Portal.
2. Elija **Más servicios** > **Otros** > **Intune**.
3. En la hoja **Intune**, elija **Aplicaciones móviles**.
1.  En la carga de trabajo **Aplicaciones móviles**, elija **Instalación** > **Tokens de VPP de iOS**.
2.  En la lista de la hoja de tokens del PCV, haga clic en **Agregar**.
3.  En la hoja Nuevo token de VPP, especifique la siguiente información:
    - **Archivo de token de PCV**: si todavía no lo ha hecho, regístrese en el Programa de Compras por Volumen para Empresa o en el Programa de Compras por Volumen para Educación. Después de registrarse, descargue el token del PCV de Apple para la cuenta u selecciónelo aquí.
    - **Id. de Apple**: escriba el identificador de Apple de la cuenta asociada al programa de compras por volumen.
    - **Tipo de cuenta de VPP**: elija **Empresa** o **Educación**.
4. Cuando haya terminado, haga clic en **Cargar**.

El token se mostrará en la hoja de la lista de tokens.


Puede sincronizar los datos que tiene Apple con Intune en cualquier momento eligiendo **Sincronizar ahora**.

## <a name="to-assign-a-volume-purchased-app"></a>Para asignar una aplicación comprada por volumen

1. En la carga de trabajo **Aplicaciones móviles**, elija **Administrar** > **Aplicaciones con licencia**.
2. En la hoja de la lista de aplicaciones, elija la aplicación que desea asignar y luego elija '**...** ' > **Asignar grupos**.
3. En la hoja <*nombre de la aplicación*>- **Grupos asignados**, elija **Administrar** > **Grupos asignados**.
4. Elija **Asignar los grupos** y luego, en la hoja **Seleccionar grupos**, elija los grupos de usuarios o dispositivos de Azure AD a los que desea asignar la aplicación.
Debe elegir una acción de asignación en **Requerida**. Además, las asignaciones a grupos de dispositivos están disponibles para los inquilinos nuevos creados después de enero de 2017. Si el inquilino se ha creado antes y no tiene la opción para asignar aplicaciones de PCV a grupos de dispositivos, póngase en contacto con el soporte técnico de Intune.
5. Cuando termine, elija **Guardar**.

Consulte [Supervisión de asignaciones de aplicaciones con Microsoft Intune](monitor-apps.md) para información para ayudarle a supervisar las asignaciones de aplicaciones.

## <a name="further-information"></a>Más información

Al asignar la aplicación como un **Requerida**, cada usuario que instala la aplicación utiliza una licencia.

Para recuperar una licencia, se debe cambiar la acción de asignación a **Desinstalar**. La licencia se recuperará una vez desinstalada la aplicación.

Cuando un usuario con un dispositivo que cumple los requisitos primero intenta instalar una aplicación de PCV, se le pedirá que se una al Programa de Compras por Volumen de Apple. Debe hacerlo antes de que continúe la instalación de la aplicación.

Al implementar una aplicación de PCV como Disponible, el contenido de la aplicación y la licencia se implementan directamente desde App Store.

