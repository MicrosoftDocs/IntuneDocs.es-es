---
title: Administrar aplicaciones de iOS compradas por volumen
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda cómo puede sincronizar aplicaciones compradas por volumen en la tienda de iOS en Intune y luego administrar y realizar el seguimiento de su uso."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: a981b0253f56d66292ce77639faf4beba8832a9e
ms.openlocfilehash: 1c13d39b8b193c56439602a6e9d9a34e547aef81
ms.lasthandoff: 04/19/2017

---

# <a name="how-to-manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Administrar aplicaciones de iOS compradas a través de un programa de compras por volumen con Microsoft Intune


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

La App Store de iOS permite comprar varias licencias de una aplicación que quiera ejecutar en la empresa. Esto ayuda a reducir la carga administrativa relacionada con el seguimiento de varias copias compradas de las aplicaciones.

Microsoft Intune ayuda a administrar las aplicaciones que se compran a través de este programa. Para ello, importa la información de licencia desde la App Store, realiza el seguimiento de la cantidad de licencias usadas y le impide instalar más copias de la aplicación de las que posee.

Además, puede sincronizar, administrar y asignar los libros que compró en la tienda del programa de compras por volumen de Apple con Intune, y asígnelos a los usuarios. Use la carga de trabajo **Libros** del portal de Intune para administrar los libros. Los procedimientos para administrar libros son iguales a los que usa para administrar aplicaciones.
Para ello, debe haber cargado un token del programa de comprar por volumen de Apple. Actualmente, solo puede asignar libros como una instalación **requerida**.
Cuando asigne un libro a un dispositivo, dicho dispositivo debe tener instalada la aplicación iBooks integrada. Si no es así, el usuario final deberá volver a instalar la aplicación para poder leer el libro. Actualmente no puede usar Intune para restaurar aplicaciones integradas que se hayan quitado.


## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Administrar aplicaciones compradas por volumen para dispositivos iOS
Puede comprar varias licencias para aplicaciones iOS mediante el [Programa de compras por volumen de Apple para empresas](http://www.apple.com/business/vpp/) o el [Programa de compras por volumen de Apple para educación](http://volume.itunes.apple.com/us/store). Esto implica configurar una cuenta de PCV de Apple en el sitio web de Apple y cargar el token de PCV de Apple en Intune.  De este modo, puede sincronizar la información de compras por volumen con Intune y hacer el seguimiento del uso de aplicaciones compradas por volumen.

## <a name="before-you-start"></a>Antes de empezar
Antes de empezar, es necesario obtener un token de PCV de Apple y cargarlo en la cuenta de Intune. Además, debe comprender lo siguiente:

* Puede asociar varios tokens de programa de compra por volumen con su cuenta de Intune.
* Si usó anteriormente un token de PCV con otro producto, debe generar uno nuevo para usarlo con Intune.
* La validez de cada token es de un año.
* De forma predeterminada, Intune se sincroniza con el servicio PCV de Apple dos veces al día. Puede iniciar una sincronización manual en cualquier momento.
* Después de importar el token de PCV en Intune, no importe el mismo token en otra solución de administración de dispositivos. Si lo hace, podría perder la asignación de licencias y los registros de usuario.
* Antes de empezar a usar el PCV de iOS con Intune, quite todas las cuentas de usuario de PCV existentes creadas con otros proveedores de administración de dispositivos móviles (MDM). Intune no sincronizará esas cuentas de usuario en Intune como medida de seguridad. Intune solo sincronizará los datos del servicio PCV de Apple que se creó mediante Intune.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Para obtener y cargar un token de PCV de Apple

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
3. En la hoja **Intune**, elija **Administrar aplicaciones**.
1.  En la carga de trabajo **Administrar aplicaciones**, elija **Configuración** > **Tokens de VPP de iOS**.
2.  En la hoja de la lista de tokens de VPP, haga clic en **Agregar**.
3.  En la hoja Nuevo token de VPP, especifique la siguiente información:
    - **Archivo de token de VPP**: si aún no lo ha hecho, regístrese en el Programa de compras por volumen para empresas o el Programa de compras por volumen para educación. Después de registrarse, descargue el token de VPP de Apple para la cuenta y selecciónelo aquí.
    - **Id. de Apple**: escriba el identificador de Apple de la cuenta asociada con el programa de compras por volumen.
    - **Tipo de cuenta de VPP**: elija **Empresa** o **Educación**.
4. Cuando haya terminado, haga clic en **Cargar**.

El token se muestra en la hoja de la lista de tokens.


Puede sincronizar los datos que tiene Apple con Intune en cualquier momento al elegir **Sincronizar ahora**.

## <a name="to-assign-a-volume-purchased-app"></a>Asignación de una aplicación comprada por volumen

1. En la carga de trabajo **Administrar aplicaciones**, elija **Administrar** > **Aplicaciones con licencia**.
2. En la hoja de lista de aplicaciones, elija la aplicación que quiere asignar y, luego, seleccione **...** > **Asignar grupos**.
3. En la hoja <*nombre de la aplicación*> - **Grupos asignados**, elija **Administrar** > **Grupos asignados**.
4. Elija **Asignar grupos** y, en la hoja **Seleccionar grupos**, elija los grupos de dispositivos o usuarios de Azure AD a los que quiere asignar la aplicación.
Debe elegir una acción de implementación de **Requerido**. Además, las asignaciones a grupos de dispositivos están disponibles para los nuevos inquilinos creados después de enero de 2017. Si el inquilino se ha creado antes de esa fecha y no tiene la opción de asignar aplicaciones de PCV a grupos de dispositivos, póngase en contacto con el soporte técnico de Intune.
5. Cuando termine, elija **Guardar**.

Consulte [Supervisión de aplicaciones](monitor-apps.md) para obtener información que le ayude a supervisar las asignaciones de aplicaciones.

## <a name="further-information"></a>Más información

Al asignar la aplicación como una instalación **requerida**, cada usuario que instala dicha aplicación usa una licencia.

Para reclamar una licencia, debe cambiar la acción de asignación a **Desinstalar**. La licencia se recupera cuando se desinstala la aplicación.

Si un usuario con un dispositivo elegible intenta primero instalar una aplicación de PCV, se le pedirá que se una al Programa de Compras por Volumen de Apple. Debe hacerlo para poder continuar con la instalación de la aplicación.

Cuando implementa una aplicación de VPP como disponible, la licencia y el contenido de la aplicación se implementan directamente desde la tienda de aplicaciones.

