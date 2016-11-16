---
title: Archivo de novedades | Microsoft Intune
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/11/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 861b5ea3bb0772d2853942e2b3f11f607dad3774
ms.openlocfilehash: 25128cfe93280e38a03779a7e6f38ddeb3c15612


---
# <a name="whats-new-archive"></a>Archivo de novedades

Esta página es un archivo de anuncios recientes realizados en [Novedades de Microsoft Intune](whats-new-in-microsoft-intune.md).

## <a name="september-2016"></a>Septiembre de 2016
### <a name="new-features-announcements-and-information"></a>Nuevas características, anuncios e Información
* [Acceso condicional de Windows](#windows-conditional-access)
* [Compatibilidad con iOS 10](#ios-10-support)
* [La herramienta de ajuste de aplicaciones es compatible con MAM sin la inscripción de dispositivos para Android e iOS](#app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios)
* [Los grupos de Intune comienzan la transición a Azure Active Directory en septiembre](#intune-groups-begin-transitioning-to-azure-active-directory-in-september)
* [Integración de Lookout para proteger los dispositivos Android](#lookout-integration-to-protect-android-devices)
* [Actualizaciones del portal de empresa para Android, iOS y Windows](#company-portal-updates)
* [Glosario de Intune](#intune-glossary)
* [Próximas novedades](#whats-coming)

### <a name="windows-conditional-access"></a>Acceso condicional de Windows
Ahora puede crear directivas de acceso condicional a través de la consola de administración de Intune para impedir que los equipos Windows tengan acceso a Exchange Online y SharePoint Online. También puede crear directivas de acceso condicional para bloquear el acceso a aplicaciones de escritorio y universales de Office.

### <a name="ios-10-support"></a>Compatibilidad con iOS 10
Los escenarios MDM y MAM existentes de Intune son compatibles con iOS 10. Para obtener sugerencias, consulte el [log del equipo de soporte técnico de Intune](https://blogs.technet.microsoft.com/intunesupport/2016/09/13/support-tip-intune-support-for-ios-10/).

### <a name="app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios"></a>La herramienta de ajuste de aplicaciones es compatible con MAM sin la inscripción de dispositivos para Android e iOS
La herramienta de ajuste de aplicaciones de Intune es una herramienta de línea de comandos que se usa para habilitar MAM de Intune en las aplicaciones de línea de negocio (LOB) para iOS y Android. Esta es la manera más sencilla de incorporar el SKU de MAM de Intune en su aplicación, de forma que su aplicación pueda aplicar directivas de MAM que se han implementado mediante Intune. Con las directivas de MAM puede:

1. Cifrar los datos de la aplicación.
2. Requerir que el trabajador de la información escriba un PIN al iniciar la aplicación.
3. Permitir que la aplicación transfiera datos solo a otras aplicaciones administradas.
4. Evitar que la aplicación realice una copia de seguridad de los datos en Android, iTunes e iCloud.
5. Permitir solo las opciones Cortar, Copiar y Pegar dentro y fuera de otras aplicaciones administradas.

La versión preliminar pública y actualizada de la herramienta de ajuste de aplicaciones de Intune ahora admite MAM sin inscripción de dispositivos en aplicaciones de LOB internas en iOS y Android. Esto significa que los usuarios finales no necesitan inscribir sus dispositivos con Intune para usar aplicaciones de LOB habilitadas para MAM.

Cualquier usuario puede probar el software de la versión preliminar pública y leer la documentación útil, situada en GitHub de msintuneappsdk:

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-ios-preview

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-android-preview

Antes de que instale y use la versión preliminar de Microsoft Intune App Wrapper para Android y iOS, debe:

* Revisar los Términos de licencia de Microsoft para la versión preliminar de la herramienta de ajuste de aplicaciones de Microsoft Intune para Android e iOS
* Imprimir y conservar una copia de los términos de licencia para sus archivos. Al descargar y usar la versión preliminar de la herramienta de ajuste de aplicaciones de Microsoft Intune para Android, acepta dichos términos de licencia. Si no los acepta, no use el software.
<!---TFS 1235607--->

### <a name="intune-groups-begin-transitioning-to-azure-active-directory-in-september"></a>Los grupos de Intune comienzan la transición a Azure Active Directory en septiembre
Algunas cuentas nuevas de Intune usarán los grupos de seguridad de Azure Active Directory en lugar de los grupos de usuarios de Intune. Sabrá que está trabajando con grupos de seguridad, ya que la página de grupos del portal de Intune tendrá un vínculo que le dirigirá al Portal de administración de Azure.

### <a name="lookout-integration-to-protect-android-devices"></a>Integración de Lookout para proteger los dispositivos Android
Microsoft se está integrando en la solución de protección de amenazas móviles de Lookout para proteger los dispositivos móviles Android mediante la detección de malware y aplicaciones de riesgo, entre otros, en los dispositivos. La solución de Lookout le ayuda a determinar el nivel de amenaza, que es configurable. Puede crear una regla de directivas de cumplimiento en Intune para terminar el cumplimiento de dispositivo basándose en la evaluación de riesgos mediante Lookout. Con las directivas de acceso condicional, puede permitir o bloquear el acceso a los recursos empresariales basándose en el estado de cumplimiento del dispositivo.

A los usuarios finales de los dispositivos no compatibles se les solicitará que se inscriban; necesitarán instalar la aplicación Lookout for Work en los dispositivos Android, activar la aplicación y corregir las amenazas que se mencionan en la aplicación Lookout for Work para obtener acceso. Para obtener más información, vea [Restrict access based on device, network, and application risk](restrict-access-based-on-device-network-app-risk.md) (Restringir el acceso basándose en el riesgo del dispositivo, de la red y de la aplicación).


### <a name="company-portal-updates"></a>Actualizaciones del portal de empresa

__Android__

<p style="margin-left: 40px">**Adición de "Notificaciones" al portal de empresa para Android**<br/>
<p style="margin-left: 40px">Se ha agregado un nuevo icono Notificaciones al portal de empresa para Android en la página principal. Al pulsar este icono, tendrá acceso a la página Notificaciones, que mostrará al usuario final todos los elementos que requieren atención en la aplicación de portal de empresa, como el no cumplimiento de dispositivos, la actualización de inscripciones y la activación de inscripciones. La aplicación de portal de empresa para iOS ya tiene esta experiencia de notificaciones. Tener la nueva página Notificaciones significa que el usuario no verá la página Configuración de acceso a la empresa cada vez que inicie o reanude el portal de empresa, siempre que el dispositivo ya esté inscrito. Si crea sus propias instrucciones de usuario final, puede que quiera actualizar su documentación para reflejar este cambio. Puede encontrar capturas de pantalla actualizadas [aquí](https://aka.ms/androidcpupdate).  

__iOS__
<p style="margin-left: 40px">**Cambios en la compatibilidad de la aplicación de portal de empresa de iOS**<br/>
<p style="margin-left: 40px">Todos los usuarios de la aplicación de portal de empresa de Microsoft Intune ahora necesitan usar la última versión. Los usuarios nuevos pueden descargar solo la última versión, y los usuarios actuales necesitan actualizarla. La versión más reciente requiere iOS 8.0 o posterior, de modo que los dispositivos que ejecuten versiones anteriores de iOS no pueden usar el portal de empresa ni inscribirse hasta que se actualicen a iOS 8.0 o posterior y, luego, se actualice la aplicación de portal de empresa a la versión más reciente. Los dispositivos inscritos que ejecuten versiones anteriores a iOS 8.0 seguirán administrándose y apareciendo en la consola de administración de Intune.
<!---TFS 1283165--->

<p style="margin-left: 40px">**Mejoras en cómo los usuarios finales de iOS obtienen sus aplicaciones**<br/>
<p style="margin-left: 40px">Los siguientes cambios se han realizado en los iconos de aplicaciones en la aplicación de portal de empresa para iOS para que apunte a los usuarios a distintas vistas en una única ubicación, el sitio web de portal de empresa, para todas sus aplicaciones. Las restricciones de Apple prohíben que se muestren la línea de negocio y las aplicaciones de la tienda de aplicaciones administrada en la aplicación de portal de empresa de la tienda y requieren a los usuarios visitar vistas diferentes para encontrar todas sus aplicaciones.

<p style="margin-left: 40px">El icono **Aplicaciones de la empresa** anteriormente apuntaba a una lista de todas las aplicaciones de la pestaña TODAS del sitio web de Portal de empresa, y seguirá funcionando del mismo modo. El nombre del icono ha cambiado a **Todas las aplicaciones**.

<p style="margin-left: 40px">El icono **Otras aplicaciones** antes apuntaba a una vista, dentro de la aplicación de portal de empresa, que enumera todas las aplicaciones que Apple permite mostrar a la aplicación de portal de empresa. El nombre del icono ha cambiado a **Aplicaciones destacadas** y, si pulsa en él, se le dirigirá a la pestaña Destacadas del sitio web de portal de empresa.

<p style="margin-left: 40px">El icono **Categorías** anteriormente apuntaba a una vista, dentro de la aplicación de portal de empresa, que enumera las categorías de aplicaciones. El nombre del icono no ha cambiado, pero ahora apunta a la pestaña Categorías del sitio web de portal de empresa. Puede encontrar las capturas de pantalla actualizadas [aquí](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186).
  <!---TFS 1317133--->

<p style="margin-left: 40px">**Preguntar para instalar la aplicación del explorador administrado de iOS si el profesional de TI establece ese requisito para una aplicación**<br/>
<p style="margin-left: 40px">Si ha configurado un clip de web para abrirlo solo en el explorador administrado y este no está instalado en un dispositivo, la aplicación de portal de empresa en el dispositivo le solicitará al usuario que instale el explorador administrado para poder instalar el clip web.
  <!---TFS 1228570--->

__Windows__
<p style="margin-left: 40px">**Botón Comentarios agregado a la aplicación de portal de empresa para Windows Phone 8.1**<br/>
<p style="margin-left: 40px">La aplicación de portal de empresa para Windows Phone 8.1 permite que los usuarios finales envíen comentarios sobre la aplicación mediante un nuevo botón "Enviar comentarios". Para encontrar el botón, los usuarios pulsan el menú "tres puntos" en la parte inferior derecha de la pantalla de la aplicación de portal de empresa y, después, **Enviar comentarios**. Los comentarios recopilados y anónimos ayudan a Microsoft a mejorar la experiencia de los usuarios en la aplicación de portal de empresa.
<!---TFS 1317806--->

### <a name="intune-glossarybr"></a>Glosario de Intune</br>
Hemos agregado un nuevo [tema de glosario](https://docs.microsoft.com/intune/understand-explore/intune-glossary) a la biblioteca para que entienda algunos de los términos usados en el producto de Intune.

### <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new-in-microsoft-intune.md) para obtener más información sobre los desarrollos recientes.



<!--HONumber=Nov16_HO2-->


