---
title: Establecer la entidad de administración de dispositivos móviles
titleSuffix: Microsoft Intune
description: Establezca la entidad de administración de dispositivos móviles en Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 43c5d0731736df193bf615391ad486a60dff6cdd
ms.sourcegitcommit: 2506cdbfccefd42587a76f14ee50c3849dad1708
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885908"
---
# <a name="set-the-mobile-device-management-authority"></a>Establecer la entidad de administración de dispositivos móviles

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

La configuración de la entidad de administración de dispositivos móviles (MDM) determina cómo se administran los dispositivos. Como administrador de TI, debe establecer una entidad de MDM antes de que los usuarios puedan inscribir dispositivos para la administración.

Las configuraciones posibles son:

- **Intune independiente**: administración solo en la nube, que se configura mediante el portal de Azure. Incluye el conjunto completo de funcionalidades que ofrece Intune. [Establecer la entidad de MDM en la consola de Intune](#set-mdm-authority-to-intune).

- **Administración conjunta de Intune**: integración de la solución de nube de Intune con Configuration Manager para dispositivos Windows 10. Intune se configura mediante la consola de Configuration Manager. [Configuración de la inscripción automática de dispositivos en Intune](https://docs.microsoft.com/configmgr/comanage/tutorial-co-manage-clients#configure-auto-enrollment-of-devices-to-intune). 

- **Administración de dispositivos móviles para Office 365**: integración de Office 365 con la solución de nube de Intune. Intune se configura desde el Centro de administración de Microsoft 365. Incluye un subconjunto de las funcionalidades que están disponibles con la versión independiente de Intune. Establezca la autoridad de MDM en el Centro de administración de Microsoft 365.

- **Coexistencia de MDM de Office 365** Puede activar y usar tanto MDM para Office 365 como Intune de manera simultánea en su inquilino y establecer la entidad de administración en Intune o en MDM para Office 365, de forma que cada usuario indique qué servicio usará para administrar sus dispositivos móviles. La entidad de administración del usuario se define en función de la licencia asignada al usuario. Para más información, consulte [Coexistencia de Microsoft Intune con MDM para Office 365](https://blogs.technet.microsoft.com/configmgrdogs/2016/01/04/microsoft-intune-co-existence-with-mdm-for-office-365).

## <a name="set-mdm-authority-to-intune"></a>Establecimiento de la entidad de MDM en Intune

Haga lo siguiente si aún no ha establecido la entidad de MDM.

1. En el [Centro de administración de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), seleccione el banner naranjo para abrir la configuración **Entidad de administración de dispositivos móviles**. El banner naranja aparece únicamente si aún no ha establecido la entidad de MDM.
2. En **Entidad de administración de dispositivos móviles**, elija la entidad de MDM entre las opciones siguientes:
   - **Entidad de MDM de Intune**
   - **Ninguno**

   ![Captura de pantalla de la sección para configurar Intune como la entidad de administración de dispositivos móviles](./media/mdm-authority-set/set-mdm-auth.png)

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
Después de cambiar a la nueva entidad de MDM, habrá probablemente un tiempo de transición (hasta ocho horas) antes de que el dispositivo se compruebe y se sincronice con el servicio. Es necesario que configure los parámetros en la nueva entidad de MDM para asegurarse de que los dispositivos inscritos seguirán administrados y protegidos después del cambio. 
- Los dispositivos deben conectarse al servicio después del cambio para que la configuración de la nueva entidad de MDM (Intune independiente) reemplace la configuración existente en el dispositivo.
- Después de cambiar la entidad de MDM, algunas de las opciones básicas (como los perfiles) de la entidad de MDM anterior permanecerán en el dispositivo durante siete días o hasta que el dispositivo se conecte al servicio por primera vez. Se recomienda que configure aplicaciones y parámetros (directivas, perfiles, aplicaciones, etc.) en la nueva entidad de MDM tan pronto como sea posible y que implemente la configuración en los grupos de usuarios que contienen usuarios con dispositivos ya inscritos. En cuanto el dispositivo se conecte con el servicio tras el cambio en la entidad de MDM, recibirá la nueva configuración desde la nueva entidad de MDM, evitando así los tiempos de inactividad en administración y protección.
- Los dispositivos sin usuarios asociados (normalmente al tener el Programa de inscripción de dispositivos iOS o escenarios de inscripción de forma masiva) no se migran a la nueva entidad de MDM. Para esos dispositivos, debe llamar al soporte técnico para solicitar ayuda para trasladarlos a la nueva entidad de MDM.

## <a name="change-mdm-authority-to-office-365"></a>Cambio de la entidad de MDM a Office 365

Para activar Office 365 MDM (o para habilitar la coexistencia de MDM además del servicio Intune existente), vaya a [https://protection.office.com](https://protection.office.com), elija **Prevención de pérdida de datos** > **Directivas de seguridad de dispositivos** > **Ver la lista de dispositivos administrados** > **Empecemos**.

Para obtener más información, vea [Configurar la administración de dispositivos móviles (MDM) en Office 365](https://support.office.com/en-us/article/Set-up-Mobile-Device-Management-MDM-in-Office-365-dd892318-bc44-4eb1-af00-9db5430be3cd).

Si quiere que los usuarios finales solo se administren mediante Office 365 MDM, quite las licencias de Intune o de EMS asignadas después de activar Office 365 MDM.

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Limpieza de dispositivos móviles tras la expiración del certificado MDM

El certificado MDM se renueva automáticamente cuando los dispositivos móviles se comunican con el servicio de Intune. Si se borran los dispositivos móviles o estos no pueden comunicarse con el servicio de Intune durante un tiempo, el certificado MDM no se renovará. El dispositivo se quita del portal de Azure 180 días después de que expire el certificado MDM.

## <a name="remove-mdm-authority"></a>Eliminación de la entidad de MDM

No se puede cambiar la entidad de MDM a Desconocido. El servicio usa la entidad de MDM para determinar qué dispositivos inscritos en el portal informan a (Microsoft Intune u Office 365 MDM).

## <a name="what-to-expect-after-changing-the-mdm-authority"></a>Qué esperar después de cambiar la entidad de MDM

- Cuando el servicio de Intune detecta que ha cambiado la entidad de MDM de un inquilino, envía un mensaje de notificación a todos los dispositivos inscritos para que inicien el proceso de comprobación y se sincronicen en el servicio (esta notificación no forma parte de la comprobación programada regularmente). Por lo tanto, una vez que cambie la entidad de MDM para el inquilino de Intune independiente, todos los dispositivos que estén encendidos y en línea se conectarán en el servicio, recibirán la nueva entidad de MDM y serán administrados por esta. No hay ninguna interrupción en el proceso de administración y protección de estos dispositivos.
- Incluso para los dispositivos que están encendidos y en línea durante el cambio en la entidad de MDM (o poco tiempo después), pasarán hasta ocho horas (según el tiempo de la siguiente comprobación periódica programada) hasta que los dispositivos se registren en el servicio bajo la nueva entidad de MDM.    

  > [!IMPORTANT]    
  > Entre el momento en que cambie la entidad MDM y se cargue el certificado de Apple Push Notification Service renovado en la nueva entidad, las inscripciones de nuevos dispositivos y las comprobaciones de dispositivos iOS darán error. Por lo tanto, es importante revisar y cargar el certificado de Apple Push Notification Service en la nueva entidad tan pronto como sea posible después del cambio de entidad de MDM.

- Los usuarios pueden cambiar rápidamente a la nueva entidad de MDM iniciando manualmente una comprobación desde el dispositivo en el servicio. Los usuarios pueden realizar este cambio con facilidad mediante la aplicación Portal de empresa e iniciando una comprobación de cumplimiento del dispositivo.
- Para validar que todo funciona correctamente después de que los dispositivos se hayan comprobado y sincronizado con el servicio tras el cambio de entidad de MDM, busque los dispositivos en la entidad de MDM.
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

- Después de cambiar la entidad de MDM, siga estos pasos para validar que los nuevos dispositivos se inscriben correctamente en la nueva entidad:   
  - Inscripción de un dispositivo nuevo
  - Asegúrese de que el dispositivo recién inscrito aparece en la entidad de MDM.
  - Realice una acción, como el bloqueo remoto, desde la consola de administración en el dispositivo. Si se completa correctamente, el dispositivo se está administrando mediante la nueva entidad de MDM.
- Si tiene problemas con dispositivos concretos, puede anular la inscripción de esos dispositivos y realizarla de nuevo para que se conecten a la nueva entidad y se administren lo antes posible.

## <a name="next-steps"></a>Pasos siguientes

Con la entidad de MDM configurada, puede empezar a [inscribir dispositivos](../enrollment/device-enrollment.md).
