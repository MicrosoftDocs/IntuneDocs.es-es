---
# required metadata

title: Administrar aplicaciones de iOS compradas a través de un programa de compras por volumen | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 1dafc28a-7f8b-4fe0-8619-f977c93d1140

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Administrar aplicaciones de iOS compradas a través de un programa de compras por volumen con Microsoft Intune
Algunas tiendas de aplicaciones permiten comprar varias licencias de una aplicación que se quiere ejecutar en la compañía. Esto ayuda a reducir la carga administrativa relacionada con el seguimiento de varias copias compradas de las aplicaciones.

Microsoft Intune ayuda a administrar las aplicaciones que se compran a través de este tipo de programa. Para ello, importa la información de licencia desde la tienda de aplicaciones, realiza el seguimiento de la cantidad de licencias usadas y le impide instalar más copias de la aplicación de las que posee.

> [!Important]
> Actualmente, Intune asigna licencias de aplicación PCV iOS a los usuarios, no a los dispositivos. Por este motivo, los usuarios finales deben escribir su contraseña de ID de Apple para instalar la aplicación.

## Administrar aplicaciones compradas por volumen para dispositivos iOS
Puede comprar varias licencias para aplicaciones de iOS a través del [Programa de Compras por Volumen (PCV) de Apple para empresas](http://www.apple.com/business/vpp/). Esto implica configurar una cuenta de PCV de Apple en el sitio web de Apple y el token de PCV de Apple en Intune.  De este modo, puede sincronizar la información de compras por volumen con Intune y hacer el seguimiento del uso de aplicaciones compradas por volumen.

## Antes de empezar
Antes de empezar, es necesario obtener un token de PCV de Apple y cargarlo en la cuenta de Intune. Además, debe comprender lo siguiente:

* Cada organización puede tener una sola cuenta de PCV y un solo token.
* Una vez asociada una cuenta de PCV a Intune, no se puede asociar posteriormente una cuenta diferente. Por este motivo, es muy importante que varias personas tengan los detalles de la cuenta que se usa.
* Si usó anteriormente un token de PCV con otro producto, debe generar uno nuevo para usarlo con Intune.
* La validez de cada token es de un año.
* De forma predeterminada, Intune se sincroniza con el servicio PCV de Apple dos veces al día. Sin embargo, se puede iniciar una sincronización manual en cualquier momento.
* Después de importar el token de PCV en Intune, no importe el mismo token en ninguna otra solución de administración de dispositivos. Si lo hace, podría perder la asignación de licencias y los registros de usuario.
* Antes de comenzar a usar el PCV de iOS con Intune, quite todas las cuentas de usuario de PCV existentes creadas con otros proveedores de MDM. Intune no sincronizará esas cuentas de usuario en Intune como medida de seguridad. Intune solo sincronizará los datos del servicio PCV de Apple que se creó mediante Intune. 

## Para obtener y cargar un token de PCV de Apple

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), haga clic en **Administración** &gt; **iOS y Mac OS X** &gt; **Programa de compras por volumen**.

2.  Haga clic en el vínculo **Cuenta de PCV de Apple** y, si no lo hizo todavía, regístrese en el Programa de Compras por Volumen para empresas. Una vez que se registre, descargue el token de PCV de Apple para la cuenta.

3.  En la página **Administrar el Programa de Compras por Volumen (PCV) de Apple** de la consola de Intune, haga clic en **Cargar el token de PCV**.

4.  En el cuadro de diálogo **Cargar el token de PCV**, escriba o pegue el nombre del token de PCV y su identificador de Apple y, después, haga clic en **Cargar**.

5.  En el cuadro de diálogo de advertencia, active la casilla para indicar que comprende que no puede cambiar a otra cuenta de PCV más adelante y haga clic en **Sí**.

En la página **Programa de Compras por Volumen**, ahora puede ver información sobre el token de PCV de Apple, que incluye la fecha de la última actualización, la fecha de expiración y la fecha de la última sincronización con Intune.

Puede sincronizar los datos que tiene Apple con Intune en cualquier momento haciendo clic en **Sincronizar ahora**.

## Para implementar una aplicación comprada por volumen

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), haga clic en **Aplicaciones** &gt; **Software administrado** &gt; **Aplicaciones compradas por volumen**. En esta lista se muestran todas las aplicaciones que se han sincronizado desde el servicio PCV de Apple.

2.  Cierre la aplicación que quiera implementar, haga clic en **Administrar implementación** y siga las instrucciones del tema [Deploy apps in Microsoft Intune](deploy-apps-in-microsoft-intune.md) (Implementar aplicaciones en Microsoft Intune) para completar la carga, la creación y la implementación de la aplicación.

Al implementar la aplicación como una instalación **Requerida**, se usa una licencia por cada usuario que instala dicha aplicación.

Para reclamar una licencia, se debe cambiar la acción de implementación a **Desinstalar**. La licencia se recupera cuando se desinstala la aplicación.

Si un usuario con un dispositivo elegible intenta primero instalar una aplicación de PCV, se le pedirá que se una al Programa de Compras por Volumen de Apple. Debe hacerlo para poder continuar con la instalación de la aplicación.

> [!TIP] Observe la columna **Estado de los términos y condiciones de PCV** para ver el estado de aceptación para cada usuario para el que se implementó la aplicación.

Si no hay más licencias disponibles, no se podrá realizar la implementación.

## Para supervisar aplicaciones de PCV de Apple
Puede supervisar qué aplicaciones de PCV están implementadas y el número de licencias que se usan desde el área de trabajo **Aplicaciones**, en el nodo **Software administrado** &gt; **Aplicaciones compradas por volumen**.

> [!TIP] También puede usar la aplicación **Filtros** para examinar el estado de la instalación de cada aplicación.

### Véase también
[Deploy apps in Microsoft Intune (Implementar aplicaciones en Microsoft Intune)](deploy-apps-in-microsoft-intune.md)



<!--HONumber=May16_HO4-->


