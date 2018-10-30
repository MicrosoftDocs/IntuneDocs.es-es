---
title: Establecer la entidad de administración de dispositivos móviles
titlesuffix: Microsoft Intune
description: Establezca la entidad de administración de dispositivos móviles en Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 41296e2c5fd1bddfc65bb343d86f4891fff9452d
ms.sourcegitcommit: cff65435df070940da390609d6376af6ccdf0140
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2018
ms.locfileid: "49425196"
---
# <a name="set-the-mobile-device-management-authority"></a>Establecer la entidad de administración de dispositivos móviles

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

La configuración de la entidad de administración de dispositivos móviles (MDM) determina cómo se administran los dispositivos. Como administrador de TI, debe establecer una entidad de MDM antes de que los usuarios puedan inscribir dispositivos para la administración.

Las configuraciones posibles son:

- **Intune independiente**: administración solo en la nube, que se configura mediante el portal de Azure. Incluye el conjunto completo de funcionalidades que ofrece Intune. [Establecer la entidad de MDM en la consola de Intune](#set-mdm-authority-to-intune).

- **Intune híbrido**: integración de la solución de nube de Intune con System Center Configuration Manager. Intune se configura mediante la consola de Configuration Manager. [Establecer la entidad de MDM en Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription). 

    > [!Important]
    >La incorporación de nuevos clientes de la administración de dispositivos móviles (MDM) híbrida se desactivará en una próxima versión. Para más información, vea el [blog sobre el plan de cambios MC146431](https://blogs.technet.microsoft.com/intunesupport/2018/08/14/move-from-hybrid-mobile-device-management-to-intune-on-azure/).

- **Administración de dispositivos móviles para Office 365**: integración de Office 365 con la solución de nube de Intune. Intune se configura desde el Centro de administración de Office 365. Incluye un subconjunto de las funcionalidades que están disponibles con la versión independiente de Intune. Establecer la entidad de MDM en el Centro de administración de Office 365.

> [!IMPORTANT]
> En la versión 1610 o posterior de Configuration Manager y en la versión 1705 de Microsoft Intune, puede cambiar la entidad de MDM sin tener que ponerse en contacto con el soporte técnico de Microsoft y sin necesidad de anular la inscripción de los dispositivos administrados existentes e inscribirlos de nuevo. Para más información, consulte [Qué hacer si se elige la configuración incorrecta de la entidad de MDM](/intune-classic/deploy-use/prerequisites-for-enrollment#what-to-do-if-you-choose-the-wrong-mdm-authority-setting).

## <a name="set-mdm-authority-to-intune"></a>Establecimiento de la entidad de MDM en Intune

Haga lo siguiente si aún no ha establecido la entidad de MDM. Para cambiar de una entidad de MDM a otra, vea la sección [Cambio de la entidad de MDM](#prepare-to-change-the-mdm-authority-to-configuration-manager) más adelante.

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. Seleccione el banner de color naranja para abrir el ajuste **Entidad de administración de dispositivos móviles**. El banner naranja aparece únicamente si aún no ha establecido la entidad de MDM.
4. En **Entidad de administración de dispositivos móviles**, elija la entidad de MDM entre las opciones siguientes:
   - **Entidad de MDM de Intune**
   - **Entidad de MDM Configuration Manager**
   - **Ninguno**

   ![Captura de pantalla de la sección para configurar Intune como la entidad de administración de dispositivos móviles](media/set-mdm-auth.png)

   Un mensaje indica que ha configurado correctamente su entidad de MDM en Intune.

### <a name="workflow-of-intune-administration-ui"></a>Flujo de trabajo de UI de administración de Intune
Cuando se habilita la administración de dispositivos Android o Apple, Intune envía información del usuario y dispositivo para integrar con estos servicios de terceros a fin de administrar sus dispositivos correspondientes.

Los escenarios que agregan un consentimiento para compartir datos se incluyen cuando:
- Se habilitan perfiles de trabajo Android.
- Se habilitan y cargan certificados push MDM de Apple.
- Se habilita cualquiera de los servicios de Apple, por ejemplo, el Programa de inscripción de dispositivos, School Manager o el Programa de Compras por Volumen.

En cada caso, el consentimiento está estrictamente relacionado con la ejecución de un servicio de administración de dispositivos móviles. Por ejemplo, confirmar que un administrador de TI ha autorizado a dispositivos Google o Apple para que se inscriban. La documentación para tratar qué información se comparte cuando los nuevos flujos de trabajo se publican está disponible en las siguientes ubicaciones:
- [Datos que Intune manda a Google](https://aka.ms/Data-intune-sends-to-google)
- [Data que Intune manda a Apple](https://aka.ms/data-intune-sends-to-apple)

## <a name="key-considerations"></a>Principales consideraciones
Después de cambiar a la nueva entidad de MDM, habrá probablemente un tiempo de transición (hasta ocho horas) antes de que el dispositivo se compruebe y se sincronice con el servicio. Es necesario que configure los parámetros en la nueva entidad de MDM (híbrido) para asegurarse de que los dispositivos inscritos seguirán administrados y protegidos después del cambio. 
- Los dispositivos deben conectarse al servicio después del cambio para que la configuración de la nueva entidad de MDM (Intune independiente) reemplace la configuración existente en el dispositivo.
- Después de cambiar la entidad de MDM, algunas de las opciones básicas (como los perfiles) de la entidad de MDM anterior (Intune independiente) permanecerán en el dispositivo durante siete días o hasta que el dispositivo se conecte al servicio por primera vez. Se recomienda que configure aplicaciones y parámetros (directivas, perfiles, aplicaciones, etc.) en la nueva entidad de MDM (híbrida) tan pronto como sea posible y que implemente la configuración en los grupos de usuarios que contienen usuarios con dispositivos ya inscritos. En cuanto el dispositivo se conecte con el servicio tras el cambio en la entidad de MDM, recibirá la nueva configuración desde la nueva entidad de MDM, evitando así los tiempos de inactividad en administración y protección.
- Si se dan las mismas categorías de dispositivos en Intune y en Configuration Manager, no se transmite ninguna asignación de categoría de dispositivo después de cambiar a la nueva entidad de MDM. Para seguir usando las categorías de dispositivos, los dispositivos migrados se deben agregar manualmente a las colecciones adecuadas una vez cambiada la entidad de MDM, y los dispositivos se mostrarán en la consola de Configuration Manager.
- Los dispositivos sin usuarios asociados (normalmente al tener el Programa de inscripción de dispositivos iOS o escenarios de inscripción de forma masiva) no se migran a la nueva entidad de MDM. Para esos dispositivos, debe llamar al soporte técnico para solicitar ayuda para trasladarlos a la nueva entidad de MDM.

## <a name="prepare-to-change-the-mdm-authority-to-configuration-manager"></a>Preparación ante el cambio de la entidad de MDM a Configuration Manager

Revise la información siguiente para preparar el cambio de la entidad de MDM:
- Debe tener la versión 1610 de Configuration Manager o una posterior para que la opción para cambiar la entidad de MDM esté disponible.
- Un dispositivo puede tardar hasta ocho horas en conectarse al servicio después de cambiar a la nueva entidad de MDM.
- Cree una recopilación de usuarios de Configuration Manager con todos los usuarios que están administrados por Intune independiente que usará al configurar la suscripción de Intune en la consola de Configuration Manager. Esta colección ayuda a garantizar que el usuario y sus dispositivos tienen una licencia de Configuration Manager asignada y administrada en el entorno híbrido después del cambio a la entidad de MDM.
- Asegúrese de que el usuario Administrador de TI se encuentra también en la recopilación de usuarios.  
- Antes del cambio, la entidad de MDM aparecerá como **Establecer en Microsoft Intune** (independiente) en la consola de administración de Intune.
- La entidad de MDM debe mostrar **Establecer en Microsoft Intune** (inquilino independiente) en la consola de administración de Microsoft Intune antes del cambio en la entidad de MDM.
    > [!NOTE]    
    > Si la entidad de MDM muestra **Managed by Intune and Office 365** (Administrado por Intune y Office 365), los dispositivos de MDM administrados por Office 365 dejarán de administrarse cuando cambie la entidad de MDM a **Configuration Manager** (híbrido). Se recomienda asignar licencias a esos usuarios para Intune o Enterprise Mobility Suite antes de cambiar la entidad de MDM.   

- En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya al rol Administrador de inscripción de dispositivos. Para ver más información, consulte [Eliminar un administrador de inscripción de dispositivos de Intune](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune#delete-a-device-enrollment-manager-from-intune).
- Desactive las asignaciones de grupos de dispositivos que estén configuradas. Para obtener más información, consulte [Clasificar los dispositivos con la asignación de grupos de dispositivos en Microsoft Intune](/intune-classic/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune).
- No debería haber ningún impacto perceptible en los usuarios finales durante el cambio de entidad de MDM. Sin embargo, puede comunicar este cambio a los usuarios para asegurarse de que sus dispositivos están encendidos y de que se conectan al servicio pronto después del cambio. Esta precaución garantiza que se conectan tantos dispositivos como sea posible al servicio y que se registran en la nueva entidad lo antes posible.
- Si usa Intune independiente para administrar dispositivos iOS antes del cambio de la entidad de MDM, debe asegurarse de que el mismo certificado de servicio de Apple Push Notification Service que se había utilizado previamente en Intune se renueva y se utiliza para configurar el inquilino de nuevo en Configuration Manager (híbrido).    

    > [!IMPORTANT]  
    > Si se utiliza un certificado diferente de Apple Push Notification Service para el inquilino híbrido, se anula la inscripción de TODOS los dispositivos iOS y tiene que repetir su proceso de inscripción. Antes de realizar el cambio en la entidad de MDM, asegúrese de que sabe exactamente qué certificado de Apple Push Notification Service se utilizó para administrar dispositivos iOS en Intune. Busque el mismo certificado en el portal Apple Push Certificates Portal (https://identity.apple.com) y asegúrese de que el usuario cuyo ID de Apple se usó para crear el certificado original de Apple Push Notification Service está identificado y disponible para renovar el mismo certificado de Apple Push Notification Service como parte del cambio a la nueva entidad de MDM.

## <a name="change-the-mdm-authority-to-configuration-manager"></a>Cambio de la entidad de MDM a Configuration Manager

1. En la consola de Configuration Manager, vaya a **Administración** &gt; **Información general** &gt; **Cloud Services** &gt; **Suscripción a Microsoft Intune** y seleccione agregar una suscripción a Intune.
2. Inicie sesión en el inquilino de Intune que usó originalmente al configurar la entidad de MDM en Intune y haga clic en **Siguiente**.
3. Seleccione **Cambiar entidad de MDM a Configuration Manager** y haga clic en **Siguiente**.
4. Seleccione la recopilación de usuarios que va a contener todos los usuarios que siguen administrados por la nueva entidad de MDM híbrida.
5. Haga clic en **Siguiente** y complete el asistente. La entidad de MDM ahora se ha cambiado a **Configuration Manager**.
6. Inicie sesión en la [consola de administración de Microsoft Intune](http://manage.microsoft.com) con el mismo inquilino de Intune y confirme que la entidad de MDM se ha cambiado a **Configurar como Configuration Manager**.
7. Después de cambiar la entidad de MDM a Configuration Manager, puede configurar la [inscripción de iOS](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-ios-mac) y la [inscripción de Android](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-android).
8. En la consola de Configuration Manager, configure e implemente las nuevas opciones de configuración y aplicaciones desde la nueva entidad de MDM (híbrido).

La próxima vez que los dispositivos se conecten al servicio, se sincronizan y reciben la nueva configuración de la entidad de MDM.

## <a name="change-mdm-authority-to-office-365"></a>Cambio de la entidad de MDM a Office 365

Para activar Office 365 MDM, además del servicio de Intune existente, vaya a [https://protection.office.com](https://protection.office.com), elija **Prevención de pérdida de datos** > **Directivas de seguridad de dispositivos** > **View list of Managed Devices** (Ver lista de dispositivos administrados) > **Empezar**.

Para obtener más información, vea [Configurar la administración de dispositivos móviles (MDM) en Office 365](https://support.office.com/en-us/article/Set-up-Mobile-Device-Management-MDM-in-Office-365-dd892318-bc44-4eb1-af00-9db5430be3cd).

Si quiere que los usuarios finales solo se administren mediante Office 365 MDM, quite las licencias de Intune o de EMS asignadas después de activar Office 365 MDM.

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Limpieza de dispositivos móviles tras la expiración del certificado MDM

El certificado MDM se renueva automáticamente cuando los dispositivos móviles se comunican con el servicio de Intune. Si se borran los dispositivos móviles o estos no pueden comunicarse con el servicio de Intune durante un tiempo, el certificado MDM no se renovará. El dispositivo se quita del portal de Azure 180 días después de que expire el certificado MDM.

## <a name="remove-mdm-authority"></a>Eliminación de la entidad de MDM

No se puede cambiar la entidad de MDM a Desconocido. Los servidores de Microsoft usan la entidad de MDM para determinar a qué portal notifican los dispositivos inscritos (Configuration Manager, Azure Intune, Office 365 MDM).

## <a name="what-to-expect-after-changing-the-mdm-authority"></a>Qué esperar después de cambiar la entidad de MDM

- Cuando el servicio de Intune detecta que ha cambiado la entidad de MDM de un inquilino, envía un mensaje de notificación a todos los dispositivos inscritos para que inicien el proceso de comprobación y se sincronicen en el servicio (esta notificación no forma parte de la comprobación programada regularmente). Por lo tanto, una vez que cambie la entidad de MDM para el inquilino de Intune independiente a híbrido, todos los dispositivos que estén encendidos y en línea se conectarán en el servicio, recibirán la nueva entidad de MDM y serán administrados por el inquilino híbrido. No hay ninguna interrupción en el proceso de administración y protección de estos dispositivos.
- Incluso para los dispositivos que están encendidos y en línea durante el cambio en la entidad de MDM (o poco tiempo después), pasarán hasta ocho horas (según el tiempo de la siguiente comprobación periódica programada) hasta que los dispositivos se registren en el servicio bajo la nueva entidad de MDM.    

  > [!IMPORTANT]    
  > Entre el momento en que cambie la entidad MDM y se cargue el certificado de Apple Push Notification Service renovado en la nueva entidad, las inscripciones de nuevos dispositivos y las comprobaciones de dispositivos iOS darán error. Por lo tanto, es importante revisar y cargar el certificado de Apple Push Notification Service en la nueva entidad tan pronto como sea posible después del cambio de entidad de MDM.

- Los usuarios pueden cambiar rápidamente a la nueva entidad de MDM iniciando manualmente una comprobación desde el dispositivo en el servicio. Los usuarios pueden realizar este cambio con facilidad mediante la aplicación Portal de empresa e iniciando una comprobación de cumplimiento del dispositivo.
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

## <a name="next-steps"></a>Pasos siguientes

Con la entidad de MDM configurada, puede empezar a [inscribir dispositivos](device-enrollment.md).