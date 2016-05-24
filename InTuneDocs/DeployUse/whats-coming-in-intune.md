---
# required metadata

title: Próximas novedades | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 05/03/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Próximas novedades en Microsoft Intune
Esta información se proporciona conforme al NDA en una base extremadamente limitada y está vinculada a cambios. Algunas de las características enumeradas aquí corren el riesgo de no cumplir las fechas límite y pueden retrasarse hasta una versión futura. Otras características se están probando en una prueba piloto (distribución de paquetes piloto) para asegurarse de que están preparadas para el cliente. Póngase en contacto con su persona conocida de Intune/PM si tiene alguna pregunta o problema.

Esta página se actualiza periódicamente. Compruebe si hay actualizaciones nuevas en Próximas novedades.

Los siguientes cambios están en fase de desarrollo de Intune. Todas estas características también se admitirán para las implementaciones de clientes híbridos (Configuration Manager con Intune). Para obtener más información sobre las nuevas características híbridas, consulte nuestra [página híbrida de Próximas novedades](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx)..

## Incorporación del Centro de mensajes
Como parte de la migración de Intune al [Portal de administración de Office 365](https://portal.office.com/), nos aprovecharemos de su Centro de mensajes para comunicar las características nuevas y otras notificaciones.  Además, al instalar la aplicación móvil complementaria de administración de Office 365, puede recibir notificaciones en su teléfono móvil y reenviar fácilmente cualquier mensaje a los usuarios o a un alias de distribución.<br>  
Empezaremos a usar el Centro de Mensajes con nuestro lanzamiento de mayo para notificarle cuándo se completan las actualizaciones e incluiremos información sobre las características nuevas y mejoradas de Intune.  Consulte hoy el Centro de mensajes iniciando sesión en el [Portal de administración de Office 365](https://portal.office.com/) y elija la opción **Centro de mensajes** en el panel de navegación izquierdo.
<!---TFS 1242782--->


## Administración de aplicaciones
- **Acceso condicional para el explorador.** Podrá establecer una directiva de acceso condicional para Exchange Online y SharePoint Online de modo que solo se pueda acceder a ellos mediante dispositivos administrados y compatibles con iOS y Android. A los usuarios finales que intenten iniciar sesión en Outlook Web Access (OWA) y en los sitios de SharePoint con dispositivos iOS y Android, se les solicitará que inscriban su dispositivo con Intune así como que solucionen cualquier problema de incumplimiento antes de completar el inicio de sesión.
<!---TFS 1175844--->

- **SDK de MAM: Admite la configuración de longitud de PIN.** Podrá especificar la longitud del PIN para las aplicaciones de MAM como si fuera el PIN de un dispositivo. Esto requerirá que los usuarios finales cumplan con las nuevas restricciones que establezca. Verán una pantalla de PIN ligeramente modificada para tener en cuenta la entrada más larga.
<!--- TFS 1104753--->

- **Controles de MAM para evitar la sincronización de contactos de Outlook (iOS).** Hay una nueva opción de configuración disponible para la administración de aplicaciones móviles sin inscripción de dispositivos. Esta opción permite que el administrador de Intune evite que una aplicación sincronice contactos con la libreta de direcciones nativa en dispositivos iOS. Si esta opción está habilitada, la aplicación ya no podrá guardar contactos en la libreta de direcciones nativa. Si esta opción está deshabilitada, la aplicación podrá guardar contactos en la libreta de direcciones nativa. Cuando un administrador de Intune borra el contenido de un dispositivo de forma selectiva, se quitan todos los contactos que ya se hayan guardado en la libreta de direcciones nativa. Esta nueva opción es compatible ahora con la aplicación Outlook en dispositivos iOS.
<!---TFS item 1276166--->

- **Skype Empresarial para Android.** Los administradores de Intune ahora pueden abordar Skype Empresarial con MAM sin las directivas de inscripción.  Cuando los usuarios inician sesión, se aplican las directivas de MAM.
<!--- TFS item 1248444 --->

- **Skype Empresarial para iOS.** Los administradores de Intune ahora pueden abordar Skype Empresarial con MAM sin las directivas de inscripción.  Cuando los usuarios inician sesión, se aplican las directivas de MAM.
<!--- TFS item 1248443 --->

### Compatibilidad con Xamarin
El SDK de la aplicación de Microsoft Intune ahora es compatible con las aplicaciones de Xamarin en estos escenarios:

- Al escribir nuevas aplicaciones o modificar el código de la línea existente de aplicaciones empresariales con el SDK de Intune. Puede obtener el complemento en la página [Microsoft Intune Github](https://github.com/msintuneappsdk).
- Agregar compatibilidad de MAM a la línea existente de aplicaciones empresariales con la herramienta de ajuste de aplicaciones de Intune

Para obtener ayuda para elegir qué método usar, consulte [Decide how to prepare apps for mobile application management with Microsoft Intune (Decidir cómo preparar las aplicaciones para la administración de aplicaciones móviles con Microsoft Intune)](https://docs.microsoft.com/en-us/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)..
<!--- TFS 1061478 & TFS 1152340--->


## Administración de dispositivos
- **Sesiones de asistencia remota para equipos con Windows.** La integración de TeamViewer para equipos administrados por agente para escritorios le permitirá establecer sesiones de asistencia remota con equipos administrados por agente para escritorios de Windows en apoyo de los departamentos de soporte técnico del usuario final. Esto incluye Windows 7, 8, 8.1 y Windows 10.
<!--- TFS 1284856--->


<!--- TFS item 1274326 --->

## Control de acceso
* **Skype Empresarial Online admite el acceso condicional.** Los administradores de Intune podrá establecer una directiva de acceso condicional para Skype Empresarial Online de modo que solo se pueda acceder a él mediante dispositivos administrados y compatibles con iOS y Android. A los usuarios finales que intenten iniciar sesión en la aplicación móvil de Skype Empresarial en iOS y Android se les pedirá que se inscriban en Intune y que corrijan los problemas de cumplimiento para poder iniciar sesión.
<!---TFS item 1254499--->

## Portal de empresa
* **El banner de identificación de dispositivos proporcionará más información a los usuarios finales.** Los usuarios finales podrán identificar fácilmente el dispositivo que han seleccionado cuando están usando el sitio web de Portal de empresa. Si está seleccionado el dispositivo incorrecto, podrán seleccionar el dispositivo correcto al pulsar el vínculo "Pulsar aquí" en el banner de la página principal.
<!--- TFS 1231157--->

* **Paquetes de aplicaciones de Windows disponibles directamente desde el Portal de empresa**: Los usuarios de equipos con Windows 8, Windows 8.1 y Windows RT ya pueden instalar paquetes de aplicaciones de Windows (con la extensión .appx) directamente desde el sitio web del Portal de empresa. Anteriormente, los administradores de Intune tenían que implementar (o los usuarios tenían que instalar) la aplicación Portal de empresa en sus dispositivos para instalar aplicaciones.
<!--- TFS item 1082481 --->

* **Los usuarios pueden bloquear de forma remota el dispositivo desde el Portal de empresa** Se ha agregado una nueva opción de bloqueo remoto al sitio web del Portal de empresa para permitir que los usuarios finales bloqueen de forma remota su dispositivo desde el Portal en caso de pérdida o robo. En la tabla siguiente se muestra la compatibilidad de la plataforma con el bloqueo remoto para Intune y para Intune con Configuration Manager.
<!--- TFS item 1195661 --->

|Plataforma  |Detalles sobre compatibilidad|
|---------|---------|
|iOS | Compatible.|
|Android | Compatible.|
|Windows Phone 8,1 | Compatible.|
|Windows 10 Mobile | Compatible únicamente si el teléfono tiene establecido un código de acceso|
|PC (Windows 8.0 y anteriores) | No compatible|
|PC (Windows 8.1) | No compatible|
|Windows Phone 8.0 | No compatible.|
|Windows 10 Escritorio | No compatible|

## Degradación del servicio
* **Grupo personalizado de destino de retirada de reglas de notificación.** Próximamente a principios de junio de 2016, ya no podrá usar el Asistente para crear reglas de notificación para destinar reglas de notificación a los grupos creados por el usuario.

    Actualmente, para destinar un grupo creado por el usuario desde la consola de administración de Microsoft Intune, elija **Administrador** > **Reglas de notificación** > **Crear nueva regla**. En el paso dos del Asistente para crear reglas de notificación, debe seleccionar los grupos de dispositivos a los que destinará la regla. Este paso, **Seleccionar grupos de dispositivos**, se está quedando en desuso desde la consola de Intune.

    **Seleccionar grupos de dispositivos** ya no se admitirá después de la versión de junio de 2016 de Intune. Sin embargo, seguirá viendo esta opción hasta agosto de 2016. Después de agosto, empezaremos a trasladar a nuestros inquilinos a la nueva experiencia durante un periodo de dos meses. Para octubre de 2016, todos los clientes existentes deberían pasarse a la experiencia nueva. Después de migrar a la experiencia nueva, ya no aparecerá la opción de destinar reglas de notificación a un grupo específico.
<!---   TFS 1278864--->







### Consulte también
Consulte [Novedades en Microsoft Intune](whats-new-in-microsoft-intune.md) para obtener más información sobre los desarrollos recientes.


<!--HONumber=May16_HO1-->


