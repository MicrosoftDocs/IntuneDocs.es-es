---
title: "Solucionar problemas de integración de Lookout | Microsoft Docs"
description: "En este tema se describen los problemas que se suelen presentar durante la integración de Lookout"
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
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 2529c5b247b90775a99e47c73f93d80be33646d7
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="troubleshoot-lookout-integration-with-intune"></a>Solucionar problemas de integración de Lookout con Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

En este tema se describen algunos problemas comunes que pueden producirse durante la configuración de protección contra amenazas móviles (MTP) de Lookout.

**Errores de inicio de sesión**

## <a name="403-errors"></a>Errores 403
Cuando inicia sesión en la [consola de Lookout MTP](https://aad.lookout.com) puede ver un error 403: **No está autorizado a acceder al servicio**. Esto puede ocurrir si el nombre de usuario especificado no es miembro del grupo de Azure Active Directory (AD) que está configurado para acceder a Lookout MTP.

Lookout MTP solo permite que los usuarios de un grupo de Azure AD configurado tengan acceso al servicio. Para determinar qué grupo está configurado con acceso a Lookout MTP, póngase en contacto con el soporte técnico de Lookout:

* Correo electrónico: enterprisesupport@lookout.com
* Inicie sesión en la [consola de MTP](http://aad.lookout.com) y vaya al módulo **Soporte técnico**.
* Vaya a: https://enterprise.support.lookout.com/hc/requests y solicite soporte técnico.

## <a name="unable-to-sign-in"></a>No es posible iniciar sesión
Verá el error siguiente si el usuario administrador global de Azure AD no ha aceptado la configuración inicial de Lookout.

![captura de pantalla de la pantalla de inicio de sesión de Lookout que muestra un error de inicio de sesión](../media/mtp/lookout-mtp-consent-not-accepted-error.png)

Para resolver este problema, el usuario de administrador global debe iniciar sesión en https://aad.lookout.com/les?action=consent y aceptar la solicitud para iniciar la configuración. Puede encontrar más información detallada en el tema [Set up your subscription with Lookout MTP (Configurar su suscripción con Lookout MTP)](../deploy-use/setup-your-lookout-mtd-subscription.md).

**Problemas de estado del dispositivo**

## <a name="device-missing-from-lookout-device-list"></a>El dispositivo no se encuentra en la lista de dispositivos de Lookout

Esto podría pasar en cualquiera de los siguientes casos:
* El usuario del dispositivo no está en el **Grupo de inscripción** especificado en la **consola de Lookout MTP**.  En la [Consola de Lookout](http://aad.lookout.com), vaya a **Sistema** > **Conector de Intune** > **Administración de inscripciones**.  Revise los grupos de Azure AD configurados para la inscripción y compruebe que el usuario del dispositivo forma parte de uno de los grupos de Azure AD.  Una vez que se agrega un usuario al grupo de inscripción, el intervalo de sondeo configurado (5 minutos es el valor predeterminado) determina lo que tarda el dispositivo en aparecer en el módulo **Dispositivos** de la consola de Lookout MTP.
* Si el dispositivo no es compatible con Lookout MTP.  Los dispositivos que no son compatibles aparecen en la sección **Dispositivos administrados** de la configuración del conector en la consola de Lookout MTP.

### <a name="device-reported-as-pending"></a>El dispositivo se ha considerado como **pendiente**

Un dispositivo se muestra como **Pendiente** si el usuario final no ha abierto la aplicación Lookout for Work ni ha pulsado el botón **Activar**. Para más información sobre la activación del dispositivo con la aplicación Lookout for Work, vea [Se le pide que instale Lookout for Work en su dispositivo Android](http://docs.microsoft.com/intune-user-help/you-are-prompted-to-install-lookout-for-work-android) o [Se le pide que instale Lookout for Work en su dispositivo iOS](https://docs.microsoft.com/intune-user-help/you-are-prompted-to-install-lookout-for-work-ios).

## <a name="device-whos-active-but-has-no-device-id"></a>El dispositivo está activo, pero no tiene id. de dispositivo
En la consola de Lookout MTP, si un dispositivo activo no tiene id. de dispositivo, el usuario de dispositivo no se encuentra en el grupo de inscripción. Un dispositivo puede tener este estado si se ha quitado el usuario del dispositivo del grupo de inscripción o si se ha quitado el grupo de inscripción.

En la [Consola de Lookout](http://aad.lookout.com), vaya a **Sistema** > **Conector de Intune** > **Inscripción** y revise la configuración.  Revise los grupos de Azure AD y compruebe que el usuario del dispositivo forma parte de uno de los grupos de Azure AD.

Mientras que un dispositivo está en este estado, Lookout sigue avisando al usuario de las amenazas detectadas, pero no envía ninguna información sobre ellas a Intune.

## <a name="device-reported-as-disconnected"></a>El dispositivo se ha considerado como **desconectado**

**Desconectado** significa que el dispositivo no se ha sincronizado con Lookout MTP en el intervalo configurado, 30 días de manera predeterminada con un mínimo de 7 días. La aplicación de portal de empresa o la aplicación Lookout for Work no se encuentra en el dispositivo. Volver a instalar las aplicaciones debería solucionar este problema. Si el usuario abre Lookout for Work y activa la aplicación, el dispositivo se vuelve a sincronizar con Lookout MTP e Intune.

### <a name="forcing-a-device-sync"></a>Forzar la sincronización de un dispositivo
En el módulo **Dispositivos** de la consola de Lookout MTP, el administrador puede seleccionar el dispositivo y optar por eliminarlo.   La siguiente vez que el propietario del dispositivo abra la aplicación Lookout for Work y pulse **Activar**, el estado del dispositivo hará una resincronización completa.

## <a name="device-has-a-new-user"></a>El dispositivo tiene un usuario nuevo
Debe borrar el dispositivo y pedir al nuevo usuario que se inscriba.  En la [consola de administración de Intune](https://manage.microsoft.com), seleccione el dispositivo, haga clic con el botón derecho y seleccione **Retirar/Eliminar datos** para quitar el dispositivo de la administración. Puede eliminar el dispositivo una vez retirado.

![captura de pantalla del módulo de dispositivos de la consola de administración de Intune con la opción Retirar/Eliminar datos](../media/mtp/mtp-retire-device-intune-console.png)

También puede ir al módulo **Dispositivos** de la [consola de Lookout](http://aad.lookout.com) y seleccionar **Eliminar**.

Si el nuevo usuario está en uno de los grupos de inscripción de Lookout MTP, el dispositivo aparecerá una vez que Azure AD lo asocie al nuevo usuario.

## <a name="compliance-remediation-workflows"></a>Flujos de trabajo de corrección de compatibilidad
- [Se le pide instalar Lookout for Work en un dispositivo Android]( http://docs.microsoft.com/intune-user-help/you-are-prompted-to-install-lookout-for-work-android)
- [Debe solucionar una amenaza detectada por Lookout for Work en el dispositivo Android](http://docs.microsoft.com/intune-user-help/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)
- [Debe solucionar una amenaza detectada por Lookout for Work en el dispositivo iOS](https://docs.microsoft.com/intune-user-help/you-need-to-resolve-a-threat-found-by-lookout-for-work-ios)


### <a name="see-also"></a>Consulte también
[Configuración de la suscripción para la protección contra amenazas de dispositivo de Lookout](/intune-classic/deploy-use/set-up-your-subscription-with-lookout-mtp)

