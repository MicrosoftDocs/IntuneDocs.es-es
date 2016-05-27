---
# required metadata

title: Solucionar problemas de implementación de aplicaciones | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 28ac298e-fb73-4c1c-b3fd-8336639e05e6

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Solucionar problemas de implementación de aplicaciones en Microsoft Intune
Este tema le ayudará a solucionar problemas de implementación de aplicaciones con Microsoft Intune.

Si esta información no soluciona el problema, vea [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico para Microsoft Intune) para conocer otras formas de obtener ayuda.


## Problemas típicos de implementación de aplicaciones

### Si no puede iniciar sesión en el portal de empresa de Microsoft Intune

1.  Compruebe si su cuenta existe en el [portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) o si está deshabilitada.

2.  Asegúrese de que se ha aprovisionado en esta cuenta en el [portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)..

3.  En el [portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854), asegúrese de que usa el nombre de usuario y la contraseña correctos para iniciar sesión en Intune y de que tiene este formato: **joe@dominio.com**..

### Si falta la información de contacto de TI en el portal de empresa

1.  En la consola de administración de Intune, haga clic en **Administración** &gt; **Portal de empresa**..

2.  Establezca los detalles de **TI de contacto** .

### Si no puede ver aplicaciones específicas en la lista

1.  Asegúrese de que esté consultando la lista de aplicaciones para un usuario o dispositivo en el que se implementó la aplicación.

2.  Asegúrese de que el dispositivo cumple los requisitos de la aplicación.

### Si obtiene un error al descargar una aplicación

1.  Asegúrese de que no haya más de una descarga simultánea por usuario. Cada usuario puede descargar una aplicación a la vez.

2.  Asegúrese de que no existen demasiadas descargas simultáneas por cuenta. Espere unos minutos y, a continuación, vuelva a intentarlo.

3.  Si recibe un mensaje nativo de iOS indicándole que no puede realizar la instalación, que la instalación se ha cancelado o que debe volver a intentarlo, puede deberse a una sobrecarga. Espere unos minutos y, a continuación, vuelva a intentarlo.

4.  Si la barra de progreso de descarga de la aplicación de iOS se completa, pero se produce un error al instalarla, es posible que haya algún problema en los archivos de la aplicación que proporcionó.

### Si hacer clic en una aplicación de iOS le lleva a una ubicación anterior en iTunes App Store

1.  La sesión actual en iTunes App Store se está abriendo en la página de la aplicación anterior.

2.  Cierre iTunes App Store en el dispositivo y vuelva a probar el vínculo.

### Si recibe un error al iniciar una aplicación de iOS

1.  La fecha de expiración de la aplicación podría no ser válida.

### Si la aplicación se queda bloqueada con el estado "en curso" durante la carga

1.  Al cargar una aplicación, primero se agregan los metadatos y, a continuación, el paquete de la aplicación. Después de cargar los metadatos, la aplicación aparece con el estado "en curso". Si observa que la aplicación se encuentra en el estado "en curso" durante un período de tiempo excesivo, elimine la aplicación y cárguela de nuevo.

2.  Asegúrese de no administrar la implementación de la aplicación mientras se encuentra en el estado "en curso".

### Si detecta un error durante la instalación de una aplicación de iOS

1.  Asegúrese de que el servidor de seguridad de la organización permite el acceso a los sitios web de certificación y aprovisionamiento de Apple.

2.  Para obtener más información, consulte la documentación para desarrolladores de Apple.

### Error: El publicador no existe
Usa **Agregar otro contrato de software** para agregar un contrato de licencia de terceros e intenta agregar el publicador desde la página **Otro contrato de licencia de software**. La página le proporcionará una lista con los editores existentes en orden alfabético.
Cuando especifica el publicador que falta, recibe el error **El publicador no existe**.. 

Esto es así por diseño. Intune proporciona el seguimiento de licencias solo para los títulos de software más populares. Intune pide que al menos 4 cuentas independientes notifiquen el software antes de ofrecerlo como una opción en la carga de trabajo de licencias.

### Si las aplicaciones administradas no envían informes de estado de la instalación

El estado de la instalación no se recopilaba para las instalaciones de aplicaciones administradas antes de la actualización de servicio de Microsoft Intune en noviembre de 2014. Para los dispositivos en que se instalaron aplicaciones administradas antes de esta actualización de servicio, actualice cada implementación de aplicación asociada con la acción de implementación adecuada (por ejemplo, **Instalación disponible**). Cada dispositivo actualizará la aplicación durante la comprobación automática de aplicaciones disponibles. Para más información, vea [Update apps using Microsoft Intune](/intune/deploy-use/update-apps-using-microsoft-intune) (Actualizar aplicaciones con Microsoft Intune)..

## <a name="BKMK_SoftDistErrorCodes"></a>Códigos de error de implementación de aplicaciones
En la tabla siguiente se indican los errores comunes que se pueden producir durante la implementación de aplicaciones de Intune, las causas más probables y las soluciones posibles.

|Código de error|Posible problema|Solución recomendada|
|--------------|--------------------|------------------------|
|0x80073CFF<br /><br />0x80CF201C (error de cliente)|Para instalar esta aplicación, debe tener un sistema habilitado para instalación de prueba.|Asegúrese de que el paquete de la aplicación tenga una firma de confianza y se haya instalado en un dispositivo unido al dominio que tenga habilitada la directiva AllowAllTrustedApps o en un dispositivo que tenga una licencia de instalación de prueba de Windows con la directiva AllowAllTrustedApps habilitada (que se aplica cuando se inscribe un dispositivo Windows RT).|
|0x80073CF0|No se pudo abrir el paquete.|Posibles causas:<br /><br />-   El paquete no está firmado.<br />-   El nombre del publicador no coincide con el sujeto que firma el certificado.<br /><br />Compruebe el registro de eventos AppxPackagingOM para obtener más información.|
|0x80073CF3|Error de actualización, dependencia o validación de conflicto en el paquete.|Posibles causas:<br /><br />-   El paquete entrante tiene conflicto con un paquete instalado.<br />-   No se encuentra una dependencia del paquete especificado.<br />-   El paquete no es compatible con la arquitectura correcta del procesador.<br /><br />Compruebe el registro de eventos AppXDeployment-Server para obtener más información.|
|0x80073CFB|El paquete suministrado ya está instalado y se ha bloqueado la reinstalación del paquete|Podría recibir este error si está instalando un paquete que no es idéntico al paquete que ya está instalado. Confirme que la firma digital también forma parte del paquete. Cuando un paquete se vuelve a generar o a firmar, dicho paquete ya no es idéntico bit a bit al paquete instalado previamente. Dos opciones para corregir este error son:<br /><br />-   Incrementar el número de versión de la aplicación y luego recompilar y volver a firmar el paquete.<br />-   Quitar el paquete antiguo para todos los usuarios del sistema antes de instalar el nuevo paquete.|

### Pasos siguientes
Si esta información para solucionar problemas no le ha ayudado, póngase en contacto con el soporte técnico de Microsoft como se indica en [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico de Microsoft Intune)..


<!--HONumber=May16_HO1-->


