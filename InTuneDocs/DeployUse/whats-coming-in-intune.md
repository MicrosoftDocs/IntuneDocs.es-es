---
# required metadata

title: Próximas novedades | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 06/10/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d

# optional metadata

ROBOTS: noindex,nofollow
#audience:
#ms.devlang:
ms.reviewer: mamoriss
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Próximas novedades en Microsoft Intune
Esta información se proporciona conforme al NDA en una base extremadamente limitada y está vinculada a cambios. Algunas de las características enumeradas aquí corren el riesgo de no cumplir las fechas límite y pueden retrasarse hasta una versión futura. Otras características se están probando en una prueba piloto (distribución de paquetes piloto) para asegurarse de que están preparadas para el cliente. Póngase en contacto con su persona conocida de Intune/PM si tiene alguna pregunta o problema.

Esta página se actualiza periódicamente. Compruebe si hay actualizaciones nuevas en Próximas novedades.

Los siguientes cambios están en fase de desarrollo de Intune. Todas estas características también se admitirán para las implementaciones de clientes híbridos (Configuration Manager con Intune). Para más información sobre las nuevas características híbridas, vea nuestra [página sobre novedades de las implementaciones híbridas](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).


## Administración de aplicaciones
- **Mejoras en la experiencia de configuración de la política de datos de empresa de Windows 10.** Hemos realizado mejoras en la experiencia de configuración de la política de datos de empresa de Windows 10 en relación con la creación de reglas de aplicaciones, la especificación de la definición de límite de red y otras opciones de protección de datos de empresa.
<!---TFS 1303011--->

- **Acceso condicional para el explorador.** Podrá establecer una directiva de acceso condicional para Exchange Online y SharePoint Online de modo que solo se pueda acceder a ellos mediante dispositivos administrados y compatibles con iOS y Android. A los usuarios finales que intenten iniciar sesión en Outlook Web Access (OWA) y en los sitios de SharePoint con dispositivos iOS y Android, se les solicitará que inscriban su dispositivo con Intune así como que solucionen cualquier problema de incumplimiento antes de completar el inicio de sesión.
<!---TFS 1175844--->

- **Dynamics CRM Online admite el acceso condicional.** Los clientes podrán establecer una directiva de acceso condicional para Dynamics CRM Online de modo que solo se pueda tener acceso a este con dispositivos administrados y compatibles con iOS y Android. Los usuarios finales que intenten iniciar sesión en la aplicación móvil de Dynamics CRM en iOS y Android tendrán que inscribirse en Intune y corregir cualquier problema de cumplimiento para poder iniciar sesión.
<!---TFS1295358--->

### Compatibilidad con Xamarin
El SDK de la aplicación de Microsoft Intune admite las aplicaciones de Xamarin en estos escenarios:

- Al escribir nuevas aplicaciones o modificar el código de la línea existente de aplicaciones empresariales con el SDK de Intune. Podrá obtener el complemento en la página de [Github de Microsoft Intune](https://github.com/msintuneappsdk).
- Agregar compatibilidad de MAM a la línea existente de aplicaciones empresariales con la herramienta de ajuste de aplicaciones de Intune

Para obtener ayuda para elegir qué método usar, vea [Decidir cómo preparar las aplicaciones para la administración de aplicaciones móviles con Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune).
<!--- TFS 1061478 & TFS 1152340--->

## Administración de dispositivos
- **Configuración de directiva de Windows Defender para la protección ante aplicaciones potencialmente no deseadas.** Se ha agregado una nueva configuración de Windows Defender denominada **Detección de aplicaciones potencialmente no deseadas** a la directiva de configuración general para Windows 10 Escritorio y Mobile. Puede usar esta configuración para proteger los equipos de escritorio de Windows inscritos ante la ejecución de software que Windows Defender ha clasificado como potencialmente no deseado. Puede protegerse contra la ejecución de estas aplicaciones o puede usar el modo auditoría para informar cuando se instale una aplicación potencialmente no deseada.
<!---TFS 1244478--->

## Acceso condicional
**Directiva de control de acceso de red de Cisco ISE.**  Los clientes que usen Cisco Identity Service Engine (ISE) 2.1 y también usen Microsoft Intune pueden establecer una directiva de control de acceso de red en ISE.

Al usar esta directiva, los dispositivos que necesiten conectarse a la red mediante WiFi o VPN deben cumplir las siguientes condiciones antes de que se les permita el acceso:

* Deben administrarse mediante Intune
* Deben cumplir todas las directivas de cumplimiento de Intune implementadas

A los usuarios finales de los dispositivos no conformes se les solicitará que se inscriban y que solucionen cualquier problema de cumplimiento para obtener acceso.
<!---TFS 1299144--->

## Portal de empresa
**Cambios en las cuentas de administradores de inscripción de dispositivos en la aplicación de portal de empresa de iOS.** Para mejorar el rendimiento y la escalabilidad, Intune ya no mostrará todos los dispositivos de Administradores de inscripción de dispositivos (DEM) en el panel Mis dispositivos de la aplicación de portal de empresa para iOS. Solo se mostrará el dispositivo local que está ejecutando la aplicación y solo si está inscrito a través de la aplicación de portal de empresa. El usuario de DEM puede realizar acciones en el dispositivo local, pero la administración remota de los demás dispositivos inscritos solo podrá realizarse desde la consola de administración de Intune.  Además, Intune está dejando de usar las cuentas de DEM con el Programa de inscripción de dispositivos de Apple o con la herramienta Apple Configurator. Estos métodos de inscripción ya admiten la inscripción sin usuarios para los dispositivos iOS compartidos. Use las cuentas de DEM solo cuando no esté disponible la inscripción sin usuarios para los dispositivos compartidos.
<!---TFS 1233681--->

## Degradación del servicio
**A partir del 8 de septiembre de 2016, las aplicaciones de portal de empresa para Windows 8 y Windows Phone estarán en desuso.** A partir de septiembre de 2016, Microsoft Intune dejará de proporcionar soporte para las aplicaciones de portal de empresa de Microsoft Intune para las plataformas Windows Phone 8 y Windows 8. Actualice los dispositivos a Windows 8.1 y Windows Phone 8.1 y use las aplicaciones de portal de empresa de Windows 8.1 y Windows Phone 8.1 correspondientes para poder seguir con la distribución de aplicaciones en estos dispositivos.
<!---TFS 1255391--->

**Grupo personalizado de destino de retirada de reglas de notificación.**
Las reglas de notificación de Intune definen a quién se enviará una alerta de correo electrónico a través de Intune. Actualmente, puede configurar reglas de notificación para enviar mensajes de correo electrónico a todos los usuarios de dispositivos de un grupo de dispositivos de Intune que haya creado. Aproximadamente a partir del 1 de junio de 2016, ya no se admitirán los grupos creados por el usuario de destino.

La escala de tiempo preliminar de este cambio es la siguiente:
- En agosto de 2016, los nuevos inquilinos no verán el paso dos del Asistente para crear reglas de notificación. Los inquilinos existentes no se verán afectados.
- Aproximadamente en septiembre de 2016, algunos inquilinos existentes no verán la opción "Seleccionar grupos de dispositivos" en el asistente.
- Aproximadamente en noviembre de 2016, se espera que ningún inquilino vea la opción "Seleccionar grupos de dispositivos" en el asistente.
<!---   TFS 1278864--->

**Cambios en la compatibilidad de la aplicación de portal de empresa de iOS.**
En julio, todos los usuarios de la aplicación de portal de empresa de Microsoft Intune para iOS deberán usar la versión más reciente. Los nuevos usuarios solo podrán descargar la versión más reciente y se pedirá a los usuarios actuales que la actualicen. La versión más reciente requiere iOS 8.0 o posterior, de modo que los dispositivos que ejecuten versiones anteriores de iOS no podrán usar el portal de empresa ni inscribirse hasta que se actualicen a iOS 8.0 o posterior y, luego, se actualice la aplicación de portal de empresa a la versión más reciente. Los dispositivos inscritos que ejecuten versiones anteriores a iOS 8.0 seguirán administrándose y apareciendo en la consola de administración de Intune.  

**Aplicaciones de visor de Intune.** Con el lanzamiento de la nueva aplicación RMS sharing, quitaremos las siguientes aplicaciones de visor de Intune a partir de agosto de 2016:
- Visor de AV de Intune
- Visor de PDF de Intune
- Visor de imágenes de Intune para Android de Google Play

En lugar de usar las aplicaciones de visor de Intune, se recomienda usar la nueva aplicación Rights Management (RMS sharing) para Android, que permite implementar una aplicación en lugar de tres aplicaciones independientes para ver archivos corporativos de forma segura en dispositivos Android. Obtenga más información sobre la aplicación RMS sharing (con un vínculo a documentación).


### Consulte también
Consulte [Novedades en Microsoft Intune](whats-new-in-microsoft-intune.md) para obtener más información sobre los desarrollos recientes.


<!--HONumber=Jun16_HO3-->


