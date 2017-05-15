---
title: "Solución de problemas de integración de Lookout | Microsoft Docs"
description: "En este tema se describen los problemas que se producen normalmente con la integración de Lookout."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbe0b5f4-b8bc-49f3-85a9-51fb2f226fca
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: e10453155343bb7fd91a4fd3874d393ef78d0b1a
ms.openlocfilehash: 0b5586a06af7658c0c7a328ae1a824f88129039f
ms.contentlocale: es-es
ms.lasthandoff: 05/15/2017


---

# <a name="troubleshoot-lookout-integration-with-intune"></a>Solucionar problemas de integración de Lookout con Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

En este tema se describen algunos problemas comunes que pueden producirse con la configuración de Lookout Mobile Threat Protection (MTP).

**Errores de inicio de sesión**

## <a name="403-errors"></a>Errores 403
Cuando inicie sesión en la [consola de Lookout MTP](https://aad.lookout.com) puede ver un error 403: **No está autorizado a acceder al servicio**. Esto puede suceder cuando el nombre de usuario especificado no es un miembro del grupo de Azure Active Directory (Azure AD) que está configurado para acceder a Lookout MTP.

Lookout MTP solo permite a los usuarios de un grupo de Azure AD configurado acceder al servicio. Para determinar qué grupo está configurado para acceder a Lookout MTP, póngase en contacto con el soporte técnico de Lookout:

* Correo electrónico: enterprisesupport@lookout.com
* Inicie sesión en la [Consola de MTP](http://aad.lookout.com) y vaya al módulo **Soporte técnico**.
* Vaya a https://enterprise.support.lookout.com/hc/requests y realice una solicitud de soporte técnico.

## <a name="unable-to-sign-in"></a>No se puede iniciar sesión
Verá el siguiente error cuando el usuario de administrador global de Azure AD no ha aceptado la configuración inicial de Lookout.

![captura de pantalla de la pantalla de inicio de sesión de Lookout que muestra un error de inicio de sesión](../media/mtp/lookout-mtp-consent-not-accepted-error.png)

Para resolver este problema, el usuario de administrador global debe iniciar sesión en https://aad.lookout.com/les?action=consent y aceptar la solicitud para iniciar la configuración. Puede encontrar más información detallada en el tema [Set up your subscription with Lookout MTP (Configurar su suscripción con Lookout MTP)](../deploy-use/set-up-your-subscription-with-lookout-mtp.md).

**Problemas de estado del dispositivo**

## <a name="device-missing-from-lookout-device-list"></a>Dispositivo ausente en la lista de dispositivos de Lookout

Esto puede suceder en alguno de los siguientes escenarios:
* Cuando el usuario del dispositivo no está en el **Grupo de inscripción** especificado en la **Consola de Lookout MTP**.  En la [Consola de Lookout](http://aad.lookout.com), vaya a **Sistema** > **Conector de Intune** > **Administración de inscripciones**.  Revise los grupos de Azure AD configurados para la inscripción y compruebe que el usuario del dispositivo forma parte de uno de los grupos de Azure AD.  Cuando un usuario se agrega al grupo de inscripción, el dispositivo puede tardar en aparecer en el módulo **Dispositivos** de la consola de Lookout MTP lo establecido en el intervalo de sondeo configurado (5 minutos es el valor predeterminado) .
* Si el dispositivo no es compatible con Lookout MTP.  Los dispositivos que no son compatibles aparecerán en la sección **Dispositivos administrados** de la configuración del conector en la consola de Lookout MTP.

### <a name="device-reported-as-pending"></a>Dispositivo notificado como **pendiente**

Un dispositivo se muestra como **Pendiente** si el usuario final no ha abierto la aplicación Lookout for Work y no ha pulsado el botón **Activar**. Para más detalles sobre la activación de dispositivos con la aplicación Lookout for Work, consulte [Necesita instalar Lookout for Work en su dispositivo Android](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android) o [Necesita instalar Lookout for Work en su dispositivo iOS](https://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-ios).

## <a name="device-whos-active-but-has-no-device-id"></a>Dispositivo que está activo, pero no tiene ningún identificador de dispositivo
En la consola de Lookout MTP, si un dispositivo activo no tiene ningún identificador de dispositivo, el usuario del dispositivo no está en el grupo de inscripción. Un dispositivo puede encontrarse en este estado si el usuario del dispositivo se ha quitado del grupo de inscripción o dicho grupo se ha quitado.

En la [Consola de Lookout](http://aad.lookout.com), vaya a **Sistema** > **Conector de Intune** > **Inscripción** y revise la configuración.  Revise los grupos de Azure AD y compruebe que el usuario del dispositivo forma parte de uno de los grupos de Azure AD.

Aunque un dispositivo se encuentre en este estado, Lookout seguirá notificando a los usuarios cualquier amenaza que detecte, pero no enviará ninguna información sobre amenazas a Intune.

## <a name="device-reported-as-disconnected"></a>El dispositivo aparece como **desconectado**

**Desconectado** significa que el dispositivo no se ha sincronizado con Lookout MTP en el intervalo configurado, que es de 30 días de forma predeterminada con un mínimo de 7 días. La aplicación Portal de empresa o Lookout for Work no está en el dispositivo. El problema se resolverá volviendo a instalar las aplicaciones. Cuando el usuario abre Lookout for Work y activa la aplicación, el dispositivo se vuelve a sincronizar con Lookout MTP e Intune.

### <a name="forcing-a-device-sync"></a>Exigir la sincronización de dispositivos
Desde el módulo **Dispositivos** de la consola de Lookout MTP, el administrador puede seleccionar el dispositivo y decidir eliminarlo.   La próxima vez que el propietario del dispositivo abra la aplicación Lookout for Work y pulse **Activar**, el estado del dispositivo realizará una resincronización completa.

## <a name="device-has-a-new-user"></a>El dispositivo tiene un nuevo usuario
Debe borrar el dispositivo y pedir al usuario nuevo que se inscriba.  Desde el [consola de administrador de Intune](https://manage.microsoft.com), seleccione el dispositivo, haga clic con el botón derecho y elija **Retirar/Eliminar datos** para quitar el dispositivo de la administración. Puede eliminar el dispositivo después de retirarlo.

![captura de pantalla del módulo de dispositivo en la consola de administrador de Intune con la opción Retirar/Eliminar datos mostrada](../media/mtp/mtp-retire-device-intune-console.png)

También puede ir al módulo **Dispositivos** de la [consola de Lookout MTP](http://aad.lookout.com) y elegir **Eliminar**.

Si el usuario nuevo se encuentra en un grupo de inscripción de Lookout MTP, el dispositivo aparecerá una vez que Azure AD asocie el dispositivo al usuario nuevo.

## <a name="compliance-remediation-workflows"></a>Flujos de trabajo de corrección de cumplimiento
- [Se le pide que instale Lookout for Work en un dispositivo Android]( http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)
- [Debe solucionar una amenaza detectada por Lookout for Work en el dispositivo Android](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)
- [Debe solucionar una amenaza detectada por Lookout for Work en el dispositivo iOS](https://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-ios)


### <a name="see-also"></a>Consulte también
[Configuración de la suscripción con Lookout MTP](https://docs.microsoft.com/intune/deploy-use/set-up-your-subscription-with-lookout-mtp)

