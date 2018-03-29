---
title: Cambio de la entidad de MDM a Configuration Manager (MDM híbrido)
description: Obtenga información sobre cómo cambiar la entidad de MDM de Intune independiente a Configuration Manager (MDM híbrido).
keywords: ''
author: dougeby
manager: dougeby
ms.date: 10/04/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f1b4bce3-7932-4a0d-aa92-6dacc7060f42
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b5494e4b2b6a7983d05ac83d9bc495677ee1a1ab
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="change-the-mdm-authority"></a>Cambio de la entidad de MDM
A partir de la versión 1610 de Configuration Manager, puede cambiar la entidad de MDM sin tener que ponerse en contacto con el Soporte técnico de Microsoft y sin necesidad de anular y volver a crear la inscripción de sus dispositivos administrados existentes. En este tema se proporcionan los pasos para cambiar un inquilino de Microsoft Intune configurado desde Intune y con la entidad de MDM configurada en **Microsoft Intune** (independiente) a **Configuration Manager** (MDM híbrido) sin tener que anular y volver a crear la inscripción de los dispositivos administrados existentes.

> [!Note]    
> Si quiere cambiar un inquilino de Microsoft Intune existente configurado desde la consola de Configuration Manager (híbrido) y con la entidad de MDM establecida en **Configuration Manager** (híbrido) para **Microsoft Intune** independiente, consulte [Cambio de la entidad de MDM](https://docs.microsoft.com/sccm/mdm/deploy-use/change-mdm-authority). 


## <a name="key-considerations"></a>Principales consideraciones
Después de cambiar a la nueva entidad de MDM, habrá probablemente un tiempo de transición (hasta ocho horas) antes de que el dispositivo se compruebe y se sincronice con el servicio. Es necesario que configure los parámetros en la nueva entidad de MDM (híbrido) para asegurarse de que los dispositivos inscritos seguirán administrados y protegidos después del cambio. 
- Los dispositivos deben conectarse al servicio después del cambio para que la configuración de la nueva entidad de MDM (Intune independiente) reemplace la configuración existente en el dispositivo.
- Después de cambiar la entidad de MDM, algunas de las opciones básicas (como los perfiles) de la entidad de MDM anterior (Intune independiente) permanecerán en el dispositivo durante siete días o hasta que el dispositivo se conecte al servicio por primera vez. Se recomienda que configure aplicaciones y parámetros (directivas, perfiles, aplicaciones, etc.) en la nueva entidad de MDM (híbrida) tan pronto como sea posible y que implemente la configuración en los grupos de usuarios que contienen usuarios con dispositivos ya inscritos. En cuanto el dispositivo se conecte con el servicio tras el cambio en la entidad de MDM, recibirá la nueva configuración desde la nueva entidad de MDM, evitando así los tiempos de inactividad en administración y protección.
- Si se dan las mismas categorías de dispositivos en Intune y en Configuration Manager, no se transmite ninguna asignación de categoría de dispositivo después de cambiar a la nueva entidad de MDM. Para seguir usando las categorías de dispositivos, los dispositivos migrados se deben agregar manualmente a las colecciones adecuadas una vez cambiada la entidad de MDM, y los dispositivos se mostrarán en la consola de Configuration Manager.
- Los dispositivos sin usuarios asociados (normalmente al tener el Programa de inscripción de dispositivos iOS o escenarios de inscripción de forma masiva) no se migran a la nueva entidad de MDM. Para esos dispositivos, debe llamar al soporte técnico para solicitar ayuda para trasladarlos a la nueva entidad de MDM.

## <a name="prepare-to-change-the-mdm-authority-to-configuration-manager-hybrid"></a>Preparación del cambio de la entidad de MDM a Configuration Manager (híbrido)
Revise la información siguiente para preparar el cambio de la entidad de MDM:
- Debe tener la versión 1610 de Configuration Manager o una posterior para que la opción para cambiar la entidad de MDM esté disponible.
- Un dispositivo puede tardar hasta ocho horas en conectarse al servicio después de cambiar a la nueva entidad de MDM.
- Cree una recopilación de usuarios de Configuration Manager con todos los usuarios que están administrados por Intune independiente que usará al configurar la suscripción de Intune en la consola de Configuration Manager. De esta manera se asegurará de que el usuario y sus dispositivos tienen una licencia de Configuration Manager asignada y administrada en el entorno híbrido después del cambio a la entidad de MDM.
- Asegúrese de que el usuario Administrador de TI se encuentra también en la recopilación de usuarios.  
- Antes del cambio, la entidad de MDM aparecerá como **Establecer en Microsoft Intune** (independiente) en la consola de administración de Intune.
- La entidad de MDM debe mostrar **Establecer en Microsoft Intune** (inquilino independiente) en la consola de administración de Microsoft Intune antes del cambio en la entidad de MDM.
    > [!NOTE]    
    > Si la entidad de MDM muestra **Managed by Intune and Office 365** (Administrado por Intune y Office 365), los dispositivos de MDM administrados por Office 365 dejarán de administrarse cuando cambie la entidad de MDM a **Configuration Manager** (híbrido). Se recomienda asignar licencias a esos usuarios para Intune o Enterprise Mobility Suite antes de cambiar la entidad de MDM.   

- En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya al rol Administrador de inscripción de dispositivos. Para ver más información, consulte [Eliminar un administrador de inscripción de dispositivos de Intune](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune#delete-a-device-enrollment-manager-from-intune).
- Desactive las asignaciones de grupos de dispositivos que estén configuradas. Para obtener más información, consulte [Clasificar los dispositivos con la asignación de grupos de dispositivos en Microsoft Intune](/intune-classic/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune).
- No debería haber ningún impacto perceptible en los usuarios finales durante el cambio de entidad de MDM. Sin embargo, puede comunicar este cambio a los usuarios para asegurarse de que sus dispositivos están encendidos y de que se conectan al servicio pronto después del cambio. De este modo, se asegura de que se conectan tantos dispositivos como sea posible al servicio y de que se registran en la nueva entidad lo antes posible.
- Si usa Intune independiente para administrar dispositivos iOS antes del cambio de la entidad de MDM, debe asegurarse de que el mismo certificado de servicio de Apple Push Notification Service que se había utilizado previamente en Intune se renueva y se utiliza para configurar el inquilino de nuevo en Configuration Manager (híbrido).    

    > [!IMPORTANT]  
    > Si se utiliza un certificado diferente de Apple Push Notification Service para el inquilino híbrido, se anula la inscripción de TODOS los dispositivos iOS y tiene que repetir su proceso de inscripción. Antes de realizar el cambio en la entidad de MDM, asegúrese de que sabe exactamente qué certificado de Apple Push Notification Service se utilizó para administrar dispositivos iOS en Intune. Busque el mismo certificado en el portal Apple Push Certificates Portal (https://identity.apple.com) y asegúrese de que el usuario cuyo ID de Apple se usó para crear el certificado original de Apple Push Notification Service está identificado y disponible para renovar el mismo certificado de Apple Push Notification Service como parte del cambio a la nueva entidad de MDM.  

## <a name="change-the-mdm-authority-to-configuration-manager"></a>Cambio de la entidad de MDM a Configuration Manager
El proceso para cambiar la entidad de MDM a Configuration Manager (híbrido) incluye los siguientes pasos de alto nivel:  
- En la consola de Configuration Manager, agregue la inscripción de Microsoft Intune.
- Configure el certificado de Apple Push Notification Service con el mismo certificado de Apple Push Notification Service que ha renovado.
- En la consola de Configuration Manager, configure e implemente las nuevas opciones de configuración y aplicaciones desde la nueva entidad de MDM (híbrido).
- La próxima vez que los dispositivos se conecten al servicio, se sincronizan y reciben la nueva configuración de la entidad de MDM.

#### <a name="to-change-the-mdm-authority-to-configuration-manager"></a>Para cambiar la entidad de MDM a Configuration Manager
1. En la consola de Configuration Manager, vaya a **Administración** &gt; **Información general** &gt; **Cloud Services** &gt; **Suscripción a Microsoft Intune** y seleccione agregar una suscripción a Intune.
2. Inicie sesión en el inquilino de Intune que usó originalmente al configurar la entidad de MDM en Intune y haga clic en **Siguiente**.
3. Seleccione **Cambiar entidad de MDM a Configuration Manager** y haga clic en **Siguiente**.
4. Seleccione la recopilación de usuarios que va a contener todos los usuarios que siguen administrados por la nueva entidad de MDM híbrida.
5. Haga clic en **Siguiente** y complete el asistente. La entidad de MDM ahora se ha cambiado a **Configuration Manager**.
6. Inicie sesión en la [consola de administración de Microsoft Intune](http://manage.microsoft.com) con el mismo inquilino de Intune y confirme que la entidad de MDM se ha cambiado a **Configurar como Configuration Manager**.


## <a name="enable-ios-enrollment"></a>Habilitar la inscripción en iOS
Cuando tenga los dispositivos iOS, debe configurar el certificado de Apple Push Notification Service en Configuration Manager.

#### <a name="to-enable-ios-enrollment-and-configure-the-apns-certificate"></a>Para habilitar la inscripción de iOS y configurar el certificado de Apple Push Notification Service

1. **Descarga de una solicitud de firma de certificado**

    1. En la consola de Configuration Manager, vaya a **Administración** &gt; **Cloud Services** &gt; **Suscripciones a Microsoft Intune** y seleccione **Crear solicitud de certificado APN** para abrir el cuadro de diálogo **Solicitar petición de firma de certificado de Apple Push Notification Service**.  
    2. Utilice la función**Examinar** para seleccionar la ruta de acceso donde se guardará el nuevo archivo de solicitud de firma de certificado (.csr). Guarde la solicitud de firma de certificado (.csr) en el equipo local.  
    3. Haga clic en **Descargar**. El nuevo archivo .csr de Microsoft Intune se descarga y Configuration Manager lo guarda.   

    > [!IMPORTANT]
    > Debe descargar una nueva solicitud de firma de certificado. No use ningún archivo existente o se producirá un error.  

2.  Vaya al portal [Apple Push Certificates Portal](http://go.microsoft.com/fwlink/?LinkId=269844) e inicie sesión con el **mismo** ID de Apple que se usó para crear y renovar anteriormente el certificado de Apple Push Notification Service que usó en Intune independiente.

    ![Página de inicio de sesión de Apple Push Certificates Portal](../media/mdm-change-apns-portal.png)

3. Seleccione el certificado de Apple Push Notification Service que usó en Intune independiente y, a continuación, haga clic en **Renovar**.

    ![Cuadro de diálogo para renovar Apple Push Notification Service](../media/mdm-change-renew-apns.png)

4. Seleccione la solicitud de firma del certificado de Apple Push Notification Service (.csr) que ha descargado localmente y, a continuación, haga clic en **Cargar**.

    ![Página de inicio de sesión de Apple Push Certificates Portal](../media/mdm-change-renew-apns-upload.png)
 
5. Seleccione el mismo Apple Push Notification Service y, a continuación, haga clic en **Descargar**. Descargue el certificado de APNs (.pem) y guarde el archivo localmente.  

    ![Página de inicio de sesión de Apple Push Certificates Portal](../media/mdm-change-renew-apns-download.png)

6. Cargue el certificado de Apple Push Notification Service renovado en el inquilino híbrido con el mismo ID de Apple que antes.

    1.  En la consola de Configuration Manager, vaya a **Administración** &gt; **Cloud Services** &gt; **Suscripción a Microsoft Intune** y seleccione **Configurar plataformas** &gt; **iOS**.  
    2.  En el cuadro de diálogo **Propiedades de suscripción a Microsoft Intune**, seleccione la pestaña **Certificado de APN** y haga clic para seleccionar la casilla **Habilitar inscripción de iOS y Mac OS X (MDM)**.  
    3.  Haga clic en **Examinar**y vaya al archivo de certificado de APNs (.cer) que descargó de Apple. Manager Configuration muestra la información del certificado de APNs. Haga clic en **Aceptar** para guardar en Intune el certificado de APNs.  

        ![Página de propiedades de la suscripción a Intune - iOS](../media/mdm-change-subscription-properties-ios.png)

## <a name="enable-android-enrollment"></a>Habilitar la inscripción de Android
1. En la consola de Configuration Manager, vaya a **Administración** &gt; **Cloud Services** &gt; **Suscripción a Microsoft Intune** y seleccione **Configurar plataformas** &gt; **Android**.  
2. Seleccione **Habilitar inscripción de Android** y haga clic en **Aceptar**.

### <a name="enable-windows-enrollment"></a>Habilitación de la inscripción de Windows
1. En la consola de Configuration Manager, vaya a **Administración** &gt; **Cloud Services** &gt; **Suscripción a Microsoft Intune** y seleccione **Configurar plataformas** &gt; **Windows**.  
2. Seleccione **Habilitar la inscripción de Windows** y haga clic en **Aceptar**.

### <a name="enable-windows-phone-enrollment"></a>Habilitación de la inscripción de Windows Phone
1. En la consola de Configuration Manager, vaya a **Administración** &gt; **Cloud Services** &gt; **Suscripción a Microsoft Intune** y seleccione **Configurar plataformas** &gt; **Windows Phone**.  
2. Seleccione la plataforma que desea habilitar y haga clic en **Aceptar**.


## <a name="next-steps"></a>Pasos siguientes
Una vez completado el cambio en la entidad de MDM, revise los siguientes pasos:
- Cuando el servicio de Intune detecta que ha cambiado la entidad de MDM de un inquilino, envía un mensaje de notificación a todos los dispositivos inscritos para que inicien el proceso de comprobación y se sincronicen en el servicio (esto no forma parte de la comprobación programada regularmente). Por lo tanto, una vez que cambie la entidad de MDM para el inquilino de Intune independiente a híbrido, todos los dispositivos que estén encendidos y en línea se conectarán en el servicio, recibirán la nueva entidad de MDM y serán administrados por el inquilino híbrido. No hay ninguna interrupción en el proceso de administración y protección de estos dispositivos.
- Incluso para los dispositivos que están encendidos y en línea durante el cambio en la entidad de MDM (o poco tiempo después), pasarán hasta ocho horas (según el tiempo de la siguiente comprobación periódica programada) hasta que los dispositivos se registren en el servicio bajo la nueva entidad de MDM.    

  > [!IMPORTANT]    
  > Entre el momento en que cambie la entidad MDM y se cargue el certificado de Apple Push Notification Service renovado en la nueva entidad, las inscripciones de nuevos dispositivos y las comprobaciones de dispositivos iOS darán error. Por lo tanto, es importante revisar y cargar el certificado de Apple Push Notification Service en la nueva entidad tan pronto como sea posible después del cambio de entidad de MDM.

- Los usuarios pueden cambiar rápidamente a la nueva entidad de MDM iniciando manualmente una comprobación desde el dispositivo en el servicio. Pueden hacerlo fácilmente mediante la aplicación Portal de empresa e iniciando una comprobación de cumplimiento del dispositivo.
- Para validar que todo funciona correctamente después de que los dispositivos se hayan comprobado y sincronizado con el servicio tras el cambio de entidad de MDM, busque los dispositivos en la consola de Configuration Manager. Los dispositivos administrados anteriormente por Intune ahora aparecen como dispositivos administrados en la consola de Configuration Manager.    
- Existe un período transitorio entre el momento en que un dispositivo está sin conexión durante el cambio de entidad de MDM y el momento en que se comprueba la idoneidad de ese dispositivo para su registro en el servicio. Para garantizar que el dispositivo permanece protegido y funcional durante este período transitorio, los siguientes perfiles permanecen en el dispositivo hasta siete días (o hasta que el dispositivo se conecte con la nueva entidad de MDM y reciba la nueva configuración que sobrescribirá la actual):
    - Perfil de correo electrónico
    - Perfil de VPN
    - Perfil de certificado
    - Perfil de Wi-Fi
    - Perfiles de configuración
- Después de cambiar a la nueva entidad de MDM, los datos de cumplimiento de la consola de administración de Microsoft Intune pueden tardar hasta una semana en informar con exactitud. Pero los estados de cumplimiento de Azure Active Directory y en el dispositivo serán precisos para que el dispositivo siga estando protegido.
- Compruebe que la nueva configuración destinada a sobrescribir la configuración actual tiene el mismo nombre que la anterior para asegurarse de que efectivamente se sobrescribe. En caso contrario, los dispositivos podrían terminar con directivas y perfiles redundantes.    

  > [!TIP]    
  > Es recomendable que cree todas las configuraciones y parámetros de administración, así como las implementaciones, poco después de que se haya completado el cambio a la entidad de MDM. De esta manera se asegurará de que los dispositivos están protegidos y se administran de manera activa durante el período transitorio.

-  Después de cambiar la entidad de MDM, siga estos pasos para validar que los nuevos dispositivos se inscriben correctamente en la nueva entidad:   
    - Inscripción de un dispositivo nuevo
    - Asegúrese de que el dispositivo recién inscrito aparece en la consola de Configuration Manager.
    - Realice una acción, como el bloqueo remoto, desde la consola de administración en el dispositivo. Si se completa correctamente, el dispositivo se está administrando mediante la nueva entidad de MDM.
- Si tiene problemas con dispositivos concretos, puede anular la inscripción de esos dispositivos y realizarla de nuevo para que se conecten a la nueva entidad y se administren lo antes posible.