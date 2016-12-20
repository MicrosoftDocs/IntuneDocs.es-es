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
translationtype: Human Translation
ms.sourcegitcommit: d6ff74f0b46baf384dbdedf13ad75538dd33a089
ms.openlocfilehash: 416f200bdb72bae98897cb8d279dbdb767757da9


---

# <a name="troubleshoot-lookout-integration-with-intune"></a>Solucionar problemas de integración de Lookout con Intune
En este tema se describen algunos problemas comunes que pueden producirse durante la configuración de protección contra amenazas móviles (MTP) de Lookout.
## <a name="troubleshoot-login-errors"></a>Solucionar errores de inicio de sesión
### <a name="403-errors"></a>Errores 403
Al iniciar sesión en la [consola de Lookout MTP](https://aad.lookout.com) puede aparecer un error 403:  **No está autorizado a acceder al servicio**  Esto puede ocurrir si el nombre de usuario especificado no es miembro del grupo de Azure Active Directory (Azure AD) que está configurado para acceder a Lookout MTP.

Lookout MTP está configurado para permitir que accedan únicamente los usuarios de un grupo configurado de Azure AD. Si no está seguro de qué grupo está configurado con acceso a Lookout MTP, póngase en contacto con el soporte técnico de Lookout.

Puede ponerse en contacto con soporte técnico de Lookout mediante los métodos siguientes:

* Correo electrónico: enterprisesupport@lookout.com
* Inicie sesión en la [consola de MTP](http://aad.lookout.com) y vaya al módulo **Soporte técnico**.
* Vaya a: https://enterprise.support.lookout.com/hc/en-us/requests y solicite soporte técnico.

### <a name="unable-to-sign-in"></a>No es posible iniciar sesión
Puede ver el error siguiente si el usuario administrador global de Azure AD no ha aceptado la configuración inicial de Lookout.

![captura de pantalla de la pantalla de inicio de sesión de Lookout con un error de inicio de sesión](../media/mtp/lookout-mtp-consent-not-accepted-error.png)

Para solucionar este problema, el usuario administrador global debe iniciar sesión en https://aad.lookout.com/les?action=consent y aceptar el símbolo del sistema para iniciar el programa de instalación. Encontrará información más detallada en el tema [Set up your subscription with Lookout MTP (Configurar la suscripción con Lookout MTP)](../deploy-use/set-up-your-subscription-with-lookout-mtp.md)

## <a name="troubleshoot-device-status-issues"></a>Solucionar problemas de estado del dispositivo

### <a name="device-not-showing-up-in-the-lookout-mtp-console-device-list"></a>El dispositivo no aparece en la lista de dispositivos de la consola de Lookout MTP

Esto podría pasar en cualquiera de los siguientes casos:
* Si el usuario propietario de este dispositivo no está en el **grupo de inscripción** especificado en la **consola de Lookout MTP**.  En el módulo **Sistema**, vaya a la pestaña **Conector de Intune** y examine el valor de **Administración de inscripción**.  Debería ver uno o más grupos de Azure AD configurados para la inscripción.  Compruebe que el usuario propietario del dispositivo que falta forma parte de uno de los grupos de Azure AD especificados.  Una vez que se agrega un nuevo usuario al grupo de inscripción, el intervalo de sondeo configurado (5 minutos es el valor predeterminado) determina lo que tarda el dispositivo en aparecer en el módulo **Dispositivos** de la consola de Lookout MTP.

* Si el dispositivo no es compatible con Lookout MTP.  Los dispositivos que no son compatibles aparecen en la sección **Dispositivos administrados** de la configuración del conector en la consola de Lookout MTP.

### <a name="device-continues-to-be-reported-as-pending"></a>El dispositivo sigue apareciendo como **pendiente**

El que un dispositivo aparezca como **Pendiente** significa que el usuario final no ha abierto la aplicación Lookout for Work ni pulsado el botón **Activar**. Para obtener más detalles sobre la activación de dispositivos con la aplicación Lookout for Work, lea el tema siguiente:

[Se le pide instalar Lookout for Work en un dispositivo Android](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

### <a name="in-the-lookout-mtp-console-a-device-is-showing-as-active-but-does-not-have-a-device-id"></a>En la consola de Lookout MTP, un dispositivo se muestra como activo, pero no tiene un identificador de dispositivo.  
Esto significa que el usuario propietario de este dispositivo no está en el grupo de inscripción especificado en la consola de Lookout MTP.   Un dispositivo puede caer en este estado si se ha quitado el usuario propietario del dispositivo del grupo de inscripción o si se ha quitado el grupo de inscripción al que pertenece el usuario.

En el módulo **Sistema** de la consola de Lookout MTP, vaya a la pestaña **Conector de Intune** y revise el valor de **Inscripción**.  Debería ver uno o más grupos de Azure AD configurados para la inscripción.  Compruebe que el usuario propietario del dispositivo forma parte de uno de los grupos de Azure AD especificados.  

Mientras que un dispositivo está en este estado, Lookout sigue avisando al usuario de las amenazas detectadas, pero no envía ninguna información sobre ellas a Intune.

### <a name="device-shows-disconnected-state"></a>El dispositivo muestra el estado desconectado

Desconectado significa que Lookout MTP no ha oído al dispositivo durante un intervalo de tiempo preconfigurado (el valor predeterminado es de 30 días con un mínimo de 7 días). Esto significa que la aplicación Portal de empresa o Lookout for Work no está instalada en el dispositivo o se ha desinstalado. Volver a instalar las aplicaciones debería solucionar este problema. Si el usuario abre Lookout for Work y activa la aplicación, el dispositivo se vuelve a sincronizar con Lookout MTP e Intune.    

### <a name="forcing-a-resync-on-the-device"></a>Forzar una nueva sincronización en el dispositivo
En el módulo **Dispositivos** de la consola de Lookout MTP, el administrador puede seleccionar el dispositivo y optar por eliminarlo.   La siguiente vez que el propietario del dispositivo abra la aplicación Lookout for Work y pulse **Activar**, el estado del dispositivo hará una resincronización completa.

### <a name="the-owner-of-the-device-is-no-longer-using-this-device"></a>El propietario del dispositivo ya no está usando este dispositivo
Debe borrar el dispositivo y pedir al nuevo usuario que se inscriba.  En la [consola de administración de Intune](https://manage.microsoft.com), seleccione el dispositivo, haga clic con el botón derecho y seleccione **Retirar/Eliminar datos** para quitar el dispositivo de la administración. Puede eliminar el dispositivo una vez retirado.

![captura de pantalla del módulo de dispositivos de la consola de administración de Intune con la opción Retirar/Eliminar datos](../media/mtp/mtp-retire-device-intune-console.png)

También puede ir al módulo **Dispositivos** de la consola de Lookout MTP y seleccionar **Eliminar**.  

Siempre que el nuevo usuario esté en uno de los grupos de inscripción especificados en la consola de Lookout MTP, el dispositivo aparecerá una vez que Azure AD lo asocie al nuevo usuario.

## <a name="compliance-remediation-workflows"></a>Flujos de trabajo de corrección de compatibilidad
[Se le pide instalar Lookout for Work en un dispositivo Android]( http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

[Debe solucionar una amenaza detectada por Lookout for Work en el dispositivo Android](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)


### <a name="see-also"></a>Consulte también
[Configuración de la suscripción para la protección contra amenazas de dispositivo de Lookout](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-your-subscription-with-lookout-mtp)



<!--HONumber=Dec16_HO2-->


