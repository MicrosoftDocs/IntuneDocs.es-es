---
title: Administrar aplicaciones iOS compradas por volumen | Microsoft Docs
description: "Use Intune para administrar las aplicaciones que compra por volumen a Apple importando la información de licencia desde la App Store, realizando el seguimiento de la cantidad de licencias usadas y evitando instalar más copias de la aplicación de las que posee."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1dafc28a-7f8b-4fe0-8619-f977c93d1140
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: b81228ccd1c515bfd82486475996eecf20655993
ms.lasthandoff: 04/24/2017


---

# <a name="manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Administrar aplicaciones de iOS compradas a través de un programa de compras por volumen con Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

La App Store de iOS permite comprar varias licencias de una aplicación que quiera ejecutar en la empresa. Esto ayuda a reducir la carga administrativa relacionada con el seguimiento de varias copias compradas de las aplicaciones.

Microsoft Intune ayuda a administrar las aplicaciones que se compran a través de este programa. Para ello, importa la información de licencia desde la App Store, realiza el seguimiento de la cantidad de licencias usadas y le impide instalar más copias de la aplicación de las que posee.

> [!Important]
> Actualmente, Intune asigna licencias de aplicación del Programa de Compras por Volumen (PCV) de iOS para empresas a los usuarios, no a los dispositivos. Por este motivo, los usuarios deben escribir la contraseña de su ID de Apple para instalar la aplicación.
> El Programa de Compras por Volumen de Apple para el sector educativo no es compatible con esta versión.

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Administrar aplicaciones compradas por volumen para dispositivos iOS
Puede comprar varias licencias para aplicaciones de iOS a través del [Programa de Compras por Volumen de Apple para empresas](http://www.apple.com/business/vpp/). Esto implica configurar una cuenta de PCV de Apple en el sitio web de Apple y cargar el token de PCV de Apple en Intune.  De este modo, puede sincronizar la información de compras por volumen con Intune y hacer el seguimiento del uso de aplicaciones compradas por volumen.

## <a name="before-you-start"></a>Antes de empezar
Antes de empezar, es necesario obtener un token de PCV de Apple y cargarlo en la cuenta de Intune. Además, debe comprender lo siguiente:

* Cada organización puede tener una sola cuenta de PCV y un solo token.
* Después de asociar una cuenta de PCV de Apple a Intune, no se puede asociar posteriormente una cuenta diferente. Por este motivo, es muy importante que varias personas tengan los detalles de la cuenta que se usa.
* Si usó anteriormente un token de PCV con otro producto, debe generar uno nuevo para usarlo con Intune.
* La validez de cada token es de un año.
* De forma predeterminada, Intune se sincroniza con el servicio PCV de Apple dos veces al día. Puede iniciar una sincronización manual en cualquier momento.
* Después de importar el token de PCV en Intune, no importe el mismo token en otra solución de administración de dispositivos. Si lo hace, podría perder la asignación de licencias y los registros de usuario.
* Antes de empezar a usar el PCV de iOS con Intune, quite todas las cuentas de usuario de PCV existentes creadas con otros proveedores de administración de dispositivos móviles (MDM). Intune no sincronizará esas cuentas de usuario en Intune como medida de seguridad. Intune solo sincronizará los datos del servicio PCV de Apple que se creó mediante Intune.
* Solo se pueden implementar aplicaciones de PCV para iOS en dispositivos de usuarios que se han inscrito con el protocolo de inscripción de dispositivos (DEP) si está configurada la afinidad del usuario con el dispositivo.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Para obtener y cargar un token de PCV de Apple

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Administración** &gt; **iOS y Mac OS X** &gt; **Programa de compras por volumen**.

2.  Elija el vínculo **Cuenta de PCV de Apple**. Si todavía no lo ha hecho, regístrese en el Programa de Compras por Volumen para Empresas. Después de registrarse, descargue el token de PCV de Apple para la cuenta.

3.  En la página **Administrar el Programa de Compras por Volumen (PCV) de Apple** de la consola de Intune, elija **Cargar el token de PCV**.

4.  En el cuadro de diálogo **Cargar el token de PCV**, escriba o pegue el nombre del token de PCV y su identificador de Apple y, después, elija **Cargar**.

5.  En el cuadro de diálogo de advertencia, active la casilla para indicar que comprende que no puede cambiar a otra cuenta de PCV más adelante y elija **Sí**.

En la página **Programa de Compras por Volumen**, ahora puede ver información sobre el token de PCV de Apple, que incluye la fecha de la última actualización, la fecha de expiración y la fecha de la última sincronización con Intune.

Puede sincronizar los datos que tiene Apple con Intune en cualquier momento al elegir **Sincronizar ahora**.

## <a name="to-deploy-a-volume-purchased-app"></a>Para implementar una aplicación comprada por volumen

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Aplicaciones** &gt; **Aplicaciones** &gt; **Aplicaciones compradas por volumen**. En esta lista se muestran todas las aplicaciones que se han sincronizado desde el servicio PCV de Apple.

2.  Seleccione la aplicación que quiera implementar, elija **Administrar implementación** y siga las instrucciones del tema [Implementar aplicaciones en Microsoft Intune](deploy-apps-in-microsoft-intune.md) para completar la carga, la creación y la implementación de la aplicación.

> [!TIP]
> Debe elegir una acción de implementación de **Requerida**. Las instalaciones disponibles no se admiten actualmente. Además, solo puede implementar la aplicación en grupos de usuarios.

Al implementar la aplicación como una instalación **Requerida**, cada usuario que instala dicha aplicación usa una licencia.

Para reclamar una licencia, se debe cambiar la acción de implementación a **Desinstalar**. La licencia se recupera cuando se desinstala la aplicación.

Si un usuario con un dispositivo elegible intenta primero instalar una aplicación de PCV, se le pedirá que se una al Programa de Compras por Volumen de Apple. Debe hacerlo para poder continuar con la instalación de la aplicación.

Si no hay más licencias disponibles, no se podrá realizar la implementación.

## <a name="to-monitor-apple-vpp-apps"></a>Para supervisar aplicaciones de PCV de Apple
Puede supervisar qué aplicaciones de PCV están implementadas y el número de licencias que se usan desde el área de trabajo **Aplicaciones**, en el nodo **Aplicaciones compradas por volumen**.

> [!TIP]
> También puede usar **Filtros** de aplicación para examinar el estado de la instalación de cada aplicación.

### <a name="see-also"></a>Consulte también
[Implementar aplicaciones en Microsoft Intune](deploy-apps-in-microsoft-intune.md)

