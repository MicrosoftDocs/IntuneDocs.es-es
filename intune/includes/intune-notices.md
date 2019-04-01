---
title: archivo include
description: archivo include
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 073115d33f9a4f22fe3706ef15860c2a8d8a68ee
ms.sourcegitcommit: 69aaf89140f82f344404e75a69dc59d8a1585b10
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675500"
---
Estos avisos proporcionan importante información que puede ayudarle a prepararse para las características y los cambios futuros de Intune. 

### <a name="change-in-enrollment-workflow-with-intune-company-portal-on-corporate-ios-devices-authenticating-with-setup-assistant----1927359---"></a>Cambio en el flujo de trabajo de inscripción con el Portal de empresa de Intune en dispositivos iOS corporativos autenticar con el Asistente de configuración <!-- 1927359 -->
Hay un próximo cambio en el flujo de trabajo para la inscripción de dispositivos iOS mediante uno de los métodos de inscripción de dispositivos corporativos de Apple - Apple Configurator, gestor empresarial de Apple, Apple School Manager o el programa de Apple de inscripción de dispositivos (DEP), cuando se usa el programa de instalación Asistente para la autenticación. Este cambio se aplica solo a los dispositivos inscritos con afinidad de usuario.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Cuando este cambio se implemente en ~~marzo~~ abril, se actualizarán los perfiles de inscripción de Intune en Azure Portal para que pueda especificar cómo se autentican los dispositivos y si reciben la aplicación Portal de empresa. Habrá un flujo de trabajo mejorado para inscribir dispositivos iOS a través de los métodos enumerados anteriormente. 

- Al inscribir nuevos dispositivos y autenticarse con el Asistente de configuración, podrá elegir si desea implementar automáticamente la aplicación de Portal de empresa o no. Los usuarios finales ya no verá la pantalla "Identificar su dispositivo" y la pantalla "Confirmar el dispositivo" en el flujo de inscripción.  
- En los dispositivos ya inscritos mediante el Asistente de instalación a través de uno de los métodos de inscripción de dispositivos corporativos de Apple, debe tomar medidas si desea habilitar el acceso condicional. Tendrá que configurar una directiva de configuración de aplicación con un archivo xml específico para insertar el Portal de empresa a estos dispositivos. Instrucciones para hacerlo se encuentran en la entrada de blog en el vínculo información adicional. Si decide insertar el Portal de empresa de esta manera, los usuarios finales ya no verá la pantalla "Identificar su dispositivo" y la pantalla "Confirmar el dispositivo" en el flujo de inscripción. 
- Después de que se implanta este cambio, si aún no ha implementado el Portal de empresa con el perfil de configuración de la aplicación se ha mencionado anteriormente y si descarga los usuarios finales que almacena la aplicación de Portal de empresa desde la aplicación, pueden iniciar sesión, pero podrá obtención un mensaje de error. No podrá usar la aplicación para el acceso condicional. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Si planea usar el flujo de trabajo modificada, desea actualizar la Guía de usuario final para indicar que:

- Los usuarios finales ya no verá las dos pantallas que se mencionó anteriormente en el flujo de inscripción. 
- Deben iniciar sesión en el Portal de empresa cuando se implementa automáticamente y no descargarlo de la tienda de aplicaciones. 

Puede crear una directiva de configuración de la aplicación ahora, si es necesario, como preparación para este cambio. Cuando se implementa este nuevo flujo de trabajo, podrá ver los perfiles de inscripción actualizados en la consola. Se también le informa de esta implementación a través del centro de mensajes. Una vez hecho esto, deberá realizar la acción, por lo que los usuarios finales pueden inscribir mediante DEP mediante la autenticación con el Asistente de configuración y se puede usar el Portal de empresa para el acceso condicional.

Consulte nuestro blog de soporte técnico en el vínculo información adicional para obtener más detalles sobre este cambio.

#### <a name="additional-information"></a>Información adicional 
[https://aka.ms/enrollment_setup_assistant](https://aka.ms/enrollment_setup_assistant)

### <a name="plan-for-change-user-experience-update-to-intune-company-portal-app-for-ios"></a>Plan de cambio: actualización de la experiencia del usuario a la aplicación de Portal de empresa de Intune para iOS
Nos complace compartir que Intune pronto lanzará una actualización importante de la experiencia de usuario para la aplicación de Portal de empresa de iOS. La actualización contará con un cambio de diseño visual de la página principal con filtros avanzados y un acceso más rápido a las aplicaciones y los libros electrónicos.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Esta experiencia mantendrá las funciones actuales de Portal de empresa de iOS y también incluirá:
- Una página principal con aspecto de iOS nativo 
- Funciones de filtrado en listas de contenido y búsqueda, incluida la capacidad de filtrar por tipo de contenido (aplicaciones o libros electrónicos) y disponibilidad (administración de dispositivos necesaria o disponible sin inscripción)
- Capacidad de buscar libros electrónicos
- Historial de búsqueda para las aplicaciones y libros electrónicos

Si forma parte del programa TestFlight de Apple, se le notificará cuando esté disponible y actualizada la versión preliminar de la aplicación Portal de empresa de Intune para iOS. Si no forma parte del programa TestFlight de Apple, aún está a tiempo de registrarse. Al registrarse podrá usar la aplicación de Portal de empresa actualizada antes de que esté disponible para los usuarios finales. También puede proporcionar comentarios directamente al equipo de Intune.  

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>¿Qué puedo hacer para prepararme para este cambio?
No es necesario realizar ninguna acción; estos cambios se publicarán en una próxima versión de la aplicación de Portal de empresa de iOS. 

#### <a name="additional-information"></a>Información adicional
[https://aka.ms/cp_update_iOS](https://aka.ms/cp_update_iOS)

### <a name="check-your-delay-visibility-of-software-updates-setting-in-intune"></a>Compruebe la configuración de "Retraso de visibilidad de las actualizaciones de Software" en Intune 

Se comparten en MC171466 que nos estamos trasladando algunas opciones de configuración en torno a en la consola de. Con la actualización de marzo a Intune, quitaremos completamente la configuración "Actualiza la visibilidad de retraso de Software" en la hoja Directiva de actualización de iOS. Esto no cambiará la manera en que se aplican las actualizaciones de software programadas, pero puede afectar a cuánto se retrasa la visibilidad de una actualización para los usuarios finales. Es posible que deba tomar medidas antes del final de marzo, si usa esta configuración. 

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Tras la actualización de servicio de Intune de febrero, observará que el valor aparecerá que tanto en los perfiles de restricción de dispositivo en la consola y en iOS actualizan directivas en la hoja de la actualización de Software. Cuando vea este cambio se reflejará en la consola, aquí es lo que es posible que deba hacer.

- Para las directivas de actualización existentes para iOS: si ha personalizado configurado esta opción en cualquier valor distinto del predeterminado 30 días y desea las configuraciones existentes para la configuración de visibilidad de retraso continuar con la aplicación después de finales de marzo, tendrá que crear un nuevo perfil de restricción de dispositivos iOS. En este caso, la configuración de visibilidad de retraso deberá tienen los mismos valores como se muestra en la directiva de actualización de iOS existente y dirigirá a los mismos grupos. Tras la actualización de servicio de marzo, ya no podrá modificar los valores de esta configuración en las directivas de actualización de iOS existentes puesto que ya no estará visible en esta hoja. En su lugar configurará esta configuración en los perfiles de nuevo.
  Si el valor de número de días puede retrasar visibilidad no coinciden en ambas ubicaciones para los valores de configuración personalizada, la visibilidad de retraso no funcionará la configuración, y los usuarios finales verán la actualización en sus dispositivos en cuanto está disponible. Esto puede tener un impacto mínimo para la mayoría de los clientes ya que los otros valores en la hoja Directiva de actualización de Software siempre han tenido prioridad sobre esta configuración en la consola.
- Para nuevas directivas de actualización para iOS: si intenta crear nuevas directivas en la hoja de actualizaciones de Software después de la actualización del servicio Intune febrero, verá esta opción atenuada. Verá una nota en la consola se le redirigirá a la hoja de configuración del dispositivo si desea retrasar la visibilidad de las actualizaciones.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>¿Qué puedo hacer para prepararme para este cambio?
No es necesario tomar medidas si no usa esta configuración o no desea retrasar la visibilidad de las actualizaciones de software para los usuarios finales.

Si desea retrasar la visibilidad de las actualizaciones, empezar a configurar la configuración de perfiles de nuevo en la hoja de configuración del dispositivo en restricciones de dispositivos > General. Si tiene este personalizado de configuración configurado en iOS existente de las directivas de actualización, crear un nuevo perfil de restricción de dispositivo equivalente con el mismo valor para "days" retrasar la visibilidad de las actualizaciones a los usuarios, implementa después de la versión de febrero y antes de marzo de la actualización. 

Es posible que desee actualizar la Guía de profesionales de TI e informar a su departamento de soporte técnico.

Consulte nuestro blog de soporte técnico en información adicional para obtener más información sobre cómo configurar esta opción.

#### <a name="additional-information"></a>Información adicional 
[https://aka.ms/Delay_visibility_setting_iOS](https://aka.ms/Delay_visibility_setting_iOS)

### <a name="plan-for-change-upcoming-fix-for-windows-10-email-profiles-in-intune---3904031--"></a>Plan de cambio: solución para perfiles de correo electrónico de Windows 10 en Intune <!--3904031-->
Estamos actualizando la manera en que Intune escribe correo electrónico actualización perfiles para Windows 10 de abril al servicio de Intune para corregir un error, así como para asegurarse de que los perfiles de correo electrónico siguen funcionando en futuras versiones de Windows 10. No hay acción que debe realizar después de implementa esta corrección.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Este cambio afecta a si usa perfiles de correo electrónico de Windows 10 con
- El cliente de correo electrónico nativo en equipos de escritorio de Windows 10 o
- El cliente de correo electrónico de Outlook en Windows 10 Mobile

Esto afecta a los clientes de administración de dispositivos móviles (MDM) de Intune independiente y híbrido.

Una vez que implementa la actualización de abril, deberá volver a crear estos perfiles en la consola de Intune (en la consola de administración de Configuration Manager si usas MDM híbrida).

Si no realiza la acción, aquí es lo que podrá ver para los perfiles creados antes de la actualización de abril:

- Los perfiles de correo electrónico existentes se mostrarán en el estado de error en la consola de administración de Configuration Manager o la consola de Intune, pero los usuarios finales seguirán teniendo acceso al correo electrónico. Sin embargo, una vez que implementa una actualización posterior de Windows, estos perfiles no funcionará. Los usuarios finales en los dispositivos de destino con estos perfiles perderán el acceso al correo electrónico.
- Modificaciones realizadas en estos perfiles después de abril no se reflejarán en los dispositivos de destino.
- No funcionará el borrado selectivo para quitar estos perfiles incluso después de la corrección se implanta en abril.

Si actuar y volver a crear perfiles de correo electrónico, los usuarios finales tendrán que seguir pasos similares a los que cuando se implementa un perfil de correo electrónico por primera vez. Su correo electrónico se bloqueará hasta que acepta la actualización que se aplica el nuevo perfil de la sincronización.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Deberá tomar medidas después de la corrección se implanta con la actualización de abril. Nos pondremos en contacto con para usted a través del centro de mensajes cuando este cambio entre en funcionamiento para que pueda empezar a volver a crear los perfiles de Intune.

Si usa perfiles de correo electrónico de Windows 10 en Intune, deberá realizar los pasos siguientes:

1. Capturar a configuración de perfil existente de Windows 10
2. Desasignar o eliminar perfiles existentes
3. Crear nuevos perfiles mediante los valores capturados y asignar los nuevos perfiles a los mismos grupos

Es posible que deba notificar a los usuarios finales y comentarle su departamento de soporte técnico de este cambio. Consulte la entrada de blog de soporte técnico en la información adicional para los detalles del error e instrucciones para volver a crear estos perfiles.

#### <a name="additional-information"></a>Información adicional
https://aka.ms/Win10EmailProfiles

