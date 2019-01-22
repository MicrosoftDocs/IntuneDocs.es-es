---
title: 'Configuración de restricciones de dispositivos para Windows 10 en Microsoft Intune: Azure | Microsoft Docs'
description: Consulte una lista de todas las configuraciones y sus descripciones para crear restricciones de dispositivo en Windows 10 y dispositivos posteriores. Use estos valores en un perfil de configuración para controlar las capturas de pantalla, los requisitos de contraseña, la configuración de la pantalla completa, las aplicaciones de la tienda, el explorador Microsoft Edge, Windows Defender, el acceso a la nube, el menú de inicio y más en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.openlocfilehash: f2b75eb5a87dbfd7a17aee83f173d3d472920428
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203644"
---
# <a name="windows-10-and-newer-device-settings-to-allow-or-restrict-features-using-intune"></a>Configuración de dispositivos con Windows 10 y versiones posteriores para permitir o restringir características mediante Intune

En este artículo se enumeran y describen todos los diferentes valores de configuración que puede controlar en los dispositivos con Windows 10 y versiones posteriores. Como parte de la solución de administración de dispositivos móviles (MDM), use estos valores para habilitar o deshabilitar características, establecer reglas de contraseña, personalizar la pantalla de bloqueo, usar Windows Defender, etc.

Estos valores se agregan a un perfil de configuración de dispositivo en Intune y luego se asignan o implementan en los dispositivos con Windows 10.

> [!Note]
> No todas las opciones están disponibles en todas las ediciones de Windows

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración de dispositivo](device-restrictions-configure.md).

## <a name="app-store"></a>Tienda de aplicaciones

- **Tienda de aplicaciones (solo móvil)**: permita o bloquee el uso de la tienda de aplicaciones en dispositivos con Windows 10 Mobile.
- **Actualizar automáticamente las aplicaciones de la tienda**: permite que aplicaciones instaladas de Microsoft Store se actualicen automáticamente.
- **Instalación de aplicaciones de confianza**: permite realizar una instalación de prueba de las aplicaciones firmadas con un certificado de confianza.
- **Desbloqueo de desarrollador**: permite que un usuario final modifique la configuración de desarrollador de Windows, como permitir las aplicaciones con instalación de prueba.
- **Datos de aplicación compartidos entre usuarios**: se permite que las aplicaciones compartan datos entre distintos usuarios en el mismo dispositivo.
- **Usar solo una tienda privada**: habilite esta opción para permitir que solo los usuarios finales descarguen aplicaciones de su tienda privada.
- **Inicio de aplicaciones de la tienda**: se usa para deshabilitar todas las aplicaciones que se han instalado previamente en el dispositivo, o bien que se han descargado de Microsoft Store.
- **Instalar los datos de aplicación en el volumen del sistema**: esta opción hace que las aplicaciones dejen de almacenar datos en el volumen del sistema del dispositivo.
- **Instalar las aplicaciones en la unidad del sistema**: esta opción hace que las aplicaciones dejen de almacenar datos en la unidad del sistema del dispositivo.
- **Game DVR (solo escritorio)**: configura si se permite la grabación y difusión de los juegos.
- **Apps from the store only** (Solo aplicaciones de la tienda): configura si los usuarios pueden instalar aplicaciones de otros lugares que no sean la tienda de aplicaciones.

## <a name="cellular-and-connectivity"></a>Red de telefonía móvil y conectividad

- **Canal de datos móviles**: se impide que los usuarios usen datos, como la navegación por la web, cuando están conectados a una red móvil. 
- **Itinerancia de datos**: Permite movilidad entre redes al obtener acceso a datos.
- **VPN a través de la red de telefonía móvil**: Controla si el dispositivo puede tener acceso a las conexiones VPN cuando se conecta a una red móvil.
- **Itinerancia de VPN a través de la red de telefonía móvil**: Controla si el dispositivo puede tener acceso a las conexiones VPN cuando hay itinerancia a una red móvil.
- **Bluetooth**: controla si el usuario puede habilitar y configurar Bluetooth en el dispositivo.
- **Detectabilidad de Bluetooth**: permite que otros dispositivos habilitados para Bluetooth detecten el dispositivo.
- **Emparejamiento previo Bluetooth**: le permite configurar dispositivos Bluetooth específicos para que se emparejen de forma automática con un dispositivo de host.
- **Anuncios de Bluetooth**: permite que el dispositivo reciba anuncios a través de Bluetooth.
- **Servicio de dispositivos conectados**: le permite decidir si quiere permitir el servicio de dispositivos conectados, que habilita la detección de otros dispositivos Bluetooth y la conexión con estos.
- **NFC**: se permite al usuario habilitar y configurar características de transmisión de datos en proximidad (NFC) en el dispositivo.
- **Wi-Fi**: se permite al usuario habilitar y configurar la red Wi-Fi en el dispositivo (solo Windows 10 Mobile).
- **Conectar automáticamente a zonas Wi-Fi**: Permite que el dispositivo se conecte automáticamente a zonas Wi-Fi gratuitas y acepte automáticamente los términos y condiciones para la conexión.
- **Configuración manual de Wi-Fi**: se controla si el usuario puede configurar sus propias conexiones Wi-Fi o si solo puede usar conexiones configuradas mediante un perfil de Wi-Fi (solo Windows 10 Mobile).
- **Intervalo de detección de Wi-Fi**: se especifica con qué frecuencia los dispositivos detectan redes Wi-Fi. Especifique un valor de 1 (más frecuente) a 500 (menos frecuente).
- **Servicios Bluetooth permitidos**: se especifica, como cadenas hexadecimales, una lista de perfiles y servicios Bluetooth permitidos.

## <a name="cloud-and-storage"></a>Nube y almacenamiento

- **Cuenta Microsoft**: Permite al usuario asociar una cuenta de Microsoft con el dispositivo.
- **Cuenta que no es Microsoft**: se permite que los usuarios agreguen al dispositivo cuentas de correo electrónico que no estén asociadas a una cuenta Microsoft.
- **Sincronización de configuración de cuenta Microsoft**: se permite que la configuración de dispositivo y aplicación asociada a una cuenta Microsoft se sincronice entre los dispositivos.

## <a name="cloud-printer"></a>Impresora en la nube

- **URL de detección de impresoras**: especifique la URL para encontrar impresoras en la nube.
- **URL de autoridad de acceso a impresoras**: especifique la URL del punto de conexión de autenticación para obtener tokens de OAuth. Por ejemplo, escriba algo parecido a `https://login.microsoftonline.com/your Azure AD Tenant ID`.
- **GUID de aplicación cliente nativa de Azure**: especifique el GUID de una aplicación cliente autorizada para obtener tokens de OAuth desde OAuthAuthority.
- **URI de recurso de servicio de impresión**: indique el URI de recurso de OAuth del servicio de impresión configurado en Azure Portal. Por ejemplo, escriba algo parecido a `http://MicrosoftEnterpriseCloudPrint/CloudPrint`.
- **N.º máximo de impresoras para consultar (solo móviles)**: indique el número máximo de impresoras que quiere que se consulten. Por ejemplo, escriba `10`.
- **URI de recurso del servicio de detección de impresoras**: indique el URI de recurso de OAuth del servicio de detección de impresoras configurado en Azure Portal. Por ejemplo, escriba algo parecido a `http://MopriaDiscoveryService/CloudPrint`.

> [!TIP]
> Después de configurar la solución [Hybrid Cloud Print de Windows Server](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-overview), puede configurar estas opciones e implementarlas en dispositivos Windows.

## <a name="control-panel-and-settings"></a>Panel de control y configuración

- **Aplicación Configuración**: se bloquea el acceso a la aplicación de configuración de Windows.
  - **Sistema**: se bloquea el acceso al área de sistema de la aplicación de configuración.
    - **Modificación de la configuración de inicio/apagado y suspensión (solo equipos de escritorio)**: Impide que el usuario final cambie la configuración de inicio/apagado y suspensión en el dispositivo.
  - **Dispositivos**: se bloquea el acceso al área de dispositivos de la aplicación de configuración.
  - **Red e Internet**: se bloquea el acceso al área de red e Internet de la aplicación de configuración.
  - **Personalización**: se bloquea el acceso al área de personalización de la aplicación de configuración.
  - **Cuentas**: se bloquea el acceso al área de cuentas de la aplicación de configuración.
  - **Hora e idioma**: se bloquea el acceso al área de hora e idioma de la aplicación de configuración.
    - **Modificación de la hora del sistema**: Impide que el usuario final cambia la fecha y hora del dispositivo.
    - **Modificación de la configuración regional (solo escritorio)**: Impide que el usuario final cambie la configuración de región en el dispositivo.
    - **Modificación de la configuración de idioma (solo equipos de escritorio)**: Impide que el usuario cambie la configuración de idioma en el dispositivo.
  - **Juegos**: se bloquea el acceso a la aplicación Juegos en la configuración.
  - **Accesibilidad**: se bloquea el acceso al área de accesibilidad de la aplicación de configuración.
  - **Privacidad**: se bloquea el acceso al área de privacidad de la aplicación de configuración.
  - **Actualización y seguridad**: se bloquea el acceso al área de actualización y seguridad de la aplicación de configuración.

## <a name="display"></a>Pantalla

- **Activar el ajuste de GDI para las aplicaciones**
- **Desactivar el ajuste de GDI para las aplicaciones**

  El ajuste de escala de PPP de GDI permite a las aplicaciones que no tienen en cuenta los PPP empezar a tenerlos en cuenta para cada monitor. Escriba las aplicaciones heredadas que tienen activado el ajuste de escala de PPP de GDI. Si el ajuste de escala de PPP de GDI está configurado tanto para activarse como desactivarse en una aplicación, el escalado estará desactivado para la aplicación.

## <a name="general"></a>General

- **Captura de pantalla (solo móviles)**: se permite al usuario capturar la pantalla del dispositivo como una imagen.
- **Copiar y pegar (solo móvil)**: se permiten acciones de copiar y pegar entre aplicaciones del dispositivo.
- **Cancelar suscripción manualmente**: Permite al usuario eliminar manualmente la cuenta del área de trabajo desde el dispositivo.
  - Esta configuración de directiva no se aplica si el equipo está unido a Azure AD y la inscripción automática está habilitada. 
  - Esta configuración de directiva no se aplica a equipos que ejecuten Windows 10 Home.
- **Instalación manual del certificado raíz (solo móviles)**: se impide que el usuario instale manualmente certificados raíz y certificados CAP intermedios.

- **Cámara**: se permite o bloquea el uso de la cámara en el dispositivo.
- **Sincronización de archivos de OneDrive**: se bloquea la sincronización de archivos de OneDrive en el dispositivo.
- **Almacenamiento extraíble**: se especifica si se pueden usar dispositivos de almacenamiento externo, como tarjetas SD, con el dispositivo.
- **Geolocalización**: Especifica si el dispositivo puede usar información de servicios de ubicación.
- **Conexión compartida**: Permite el uso compartido de una conexión de Internet en el dispositivo.
- **Restablecimiento del teléfono**: se controla si el usuario puede realizar un borrado en el dispositivo.
- **Conexión USB (solo móviles)**: Controla si los dispositivos pueden tener acceso a dispositivos de almacenamiento externo a través de una conexión USB.
- **Modo antirrobo (solo móviles)**: Permite habilitar el modo antirrobo de Windows.
- **Cortana**: Habilita o deshabilita el asistente de voz de Cortana.
- **Grabación de voz (solo móviles)**: se permite o bloquea el uso de la grabadora de voz del dispositivo.
- **Modificación del nombre del dispositivo**: se impide que el usuario final cambie el nombre del dispositivo (solo Windows 10 Mobile).
- **Agregar paquetes de aprovisionamiento**: se bloquea el agente de configuración de tiempo de ejecución que instala los paquetes de aprovisionamiento.
- **Quitar paquetes de aprovisionamiento**: se bloquea el agente de configuración de tiempo de ejecución que quita los paquetes de aprovisionamiento.
- **Detección de dispositivos**: se bloquea la detección de un dispositivo por parte de otros dispositivos.
- **Cambio de tarea (solo móviles)**: se bloquea el conmutador de tareas en el dispositivo.
- **Cuadro de diálogo de error de tarjeta SIM (sólo móviles)**: se impide que un mensaje de error se muestre en el dispositivo si no se detecta una tarjeta SIM.
- **Ink Workspace** (Área de trabajo de Ink): se impide que los usuarios accedan al área de trabajo de Ink. **No configurado** activa el área de trabajo de Ink y el usuario tiene permitido usarlo por encima de la pantalla de bloqueo.
- **Reimplementación automática**: se permite que los usuarios con derechos administrativos eliminen todos los datos de usuario y las configuraciones con **CTRL + Win + R** en la pantalla de bloqueo del dispositivo. En este caso, el dispositivo se vuelve a configurar e inscribir automáticamente para la administración.
- **Require users to connect to network during device setup (Windows Insider only)** [Exigir que los usuarios se conecten a la red durante la configuración del dispositivo (solo para Windows Insider)]: elija **Requerir** para que el dispositivo se conecte a una red antes de pasar de la página Red durante la configuración de Windows 10. Aunque esta característica está en versión preliminar, se requiere una compilación 1809 de Windows Insider o una versión posterior para usar esta configuración.
- **Finalizar procesos desde el Administrador de tareas**: esta configuración determina si los usuarios que no son administradores pueden usar el Administrador de tareas para finalizar tareas. Si selecciona **Bloquear**, se impide que los usuarios estándar (no administradores) usen el Administrador de tareas para finalizar un proceso o una tarea en el dispositivo. Si selecciona **Sin configurar** (valor predeterminado), se permite que los usuarios estándar finalicen un proceso o una tarea mediante el Administrador de tareas.

## <a name="kiosk-preview---obsolete"></a>Quiosco (versión preliminar): obsoleto

Estos valores son de solo lectura y no se pueden cambiar. Para habilitar la pantalla completa, vea [Configuración de quiosco para Windows 10 (y versiones posteriores) en Intune](kiosk-settings.md).

Un dispositivo de pantalla completa normalmente ejecuta una aplicación o un conjunto determinado de aplicaciones. A los usuarios no se les permite el acceso a características o funciones del dispositivo.

- **Pantalla completa**: identifica el tipo de modo de pantalla completa admitido por la directiva. Las opciones son:

  - **Sin configurar** (valor predeterminado): la directiva no habilita la pantalla completa en el dispositivo.
  - **Pantalla completa con una sola aplicación**: el perfil permite que el dispositivo solo ejecute una aplicación. Cuando el usuario inicia sesión, se inicia una aplicación concreta. Este modo también evita que el usuario abra nuevas aplicaciones o modifique la aplicación en ejecución.
  - **Pantalla completa con varias operaciones**: el perfil permite que el dispositivo ejecute varias aplicaciones. Solo las aplicaciones que agregue están disponibles para el usuario. La ventaja de una pantalla completa con varias aplicaciones, o un dispositivo de propósito fijo, es proporcionar una experiencia fácil de entender para los usuarios gracias al acceso únicamente a las aplicaciones que necesitan y la retirada de la vista de las aplicaciones que no necesitan.

#### <a name="single-app-kiosks"></a>Pantallas completas con una sola aplicación

Escriba los valores siguientes:

- **Cuenta de usuario**: especifique la cuenta de usuario local (en el dispositivo), una cuenta de dominio de AD o una cuenta de Azure AD asociada a la aplicación de pantalla completa.
  - Cuenta local: escríbala con los formatos `devicename\accountname`, `.\accountname` o `accountname`.
  - Cuenta de dominio: escríbala con el formato `domain\accountname`.
  - Cuenta de Azure AD: escríbala con el formato `AzureAD\emailaddress`. Asegúrese de escribir "AzureAD", ya que es un nombre de dominio fijo. Después, siga con la dirección de correo electrónico de Azure AD. Por ejemplo, escriba `AzureAD\user@contoso.onmicrosoft.com`.

    En el caso de las pantallas completas en entornos de uso público con inicio de sesión automático habilitado, se debe usar un tipo de usuario con los privilegios mínimos (por ejemplo, la cuenta de usuario estándar local). Si usa una cuenta de Azure AD para el modo de pantalla completa, asegúrese de especificar `AzureAD\user@yourorganization.com`.

- **Identificador de modelo de usuario de aplicación (AUMID) de la aplicación**: especifique el AUMID de la aplicación de pantalla completa. Para más información, vea [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Buscar el identificador de modelo de usuario de aplicación de una aplicación instalada).

#### <a name="multi-app-kiosks"></a>Pantallas completas con varias aplicaciones

Las [pantallas completas con varias aplicaciones](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#configure-a-kiosk-in-microsoft-intune) usan una configuración de pantalla completa que muestra las aplicaciones permitidas y otras opciones. 

Use el botón **Agregar** para crear una configuración de pantalla completa (o seleccionar una existente). Luego, escriba los valores siguientes:

- **Nombre de la configuración de quiosco**: escriba un nombre descriptivo que se use para identificar la configuración.

- **Aplicaciones de quiosco**: especifique las aplicaciones que están disponibles en el menú Inicio. Las aplicaciones que agregue son las únicas que el usuario puede abrir.

  - **Tipo de aplicación**: elija el tipo de la aplicación de pantalla completa:
    - **Aplicación Win32**: una aplicación de escritorio tradicional. Necesita el nombre/ruta de acceso completo del archivo ejecutable correspondiente al dispositivo.
    - **Aplicación para UWP**: una aplicación universal de Windows. Necesita el [AUMID de la aplicación](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

  - **Identificador**: especifique el nombre de la ruta de acceso completa del archivo ejecutable (aplicaciones Win32) o el [AUMID de la aplicación](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (aplicaciones para UWP).

- **Barra de tareas**: elija **Habilitar** (mostrar) la barra de tareas o mantenerla **No configurada** (oculta) en la pantalla completa.

- **Diseño del menú Inicio**: especifique un archivo XML que describa el modo en que las aplicaciones aparecen en el menú Inicio. [Personalizar y exportar el diseño de la pantalla Inicio](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) proporciona algunas instrucciones y XML de ejemplo.

  [Create a Windows 10 kioks that runs apps](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#create-xml-file) (Crear una pantalla completa de Windows 10 que ejecute aplicaciones) proporciona más detalles sobre cómo usar y crear archivos XML.

- **Usuarios asignados**: agregue una o varias cuentas de usuario que puedan usar las aplicaciones que agregue. Cuando la cuenta inicia sesión, solo están disponibles las aplicaciones definidas en la configuración. La cuenta de usuario puede ser local en el dispositivo o una cuenta de Azure AD asociada a la aplicación de pantalla completa.

    En el caso de las pantallas completas en entornos de uso público con inicio de sesión automático habilitado, se debe usar un tipo de usuario con los privilegios mínimos (por ejemplo, la cuenta de usuario estándar local). Para configurar una cuenta de Azure Active Directory (AD) para el modo de pantalla completa, use el formato `domain\user@tenant.com`.

## <a name="locked-screen-experience"></a>Experiencia de pantalla bloqueada

- **Notificaciones del centro de actividades (solo móviles)**: se permite que las notificaciones del centro de actividades aparezcan en la pantalla de bloqueo del dispositivo (solo Windows 10 Mobile).
- **URL de imagen de pantalla de bloqueo (solo equipos de escritorio)**: escriba la URL de una imagen en formato JPEG que se usa como papel tapiz de la pantalla de bloqueo de Windows. Los usuarios no pueden cambiar esta configuración.
- **Tiempo de espera de la pantalla configurable por el usuario (solo dispositivos móviles)**: se permite que los usuarios configuren el período de tiempo. 
- **Cortana en pantalla bloqueada (solo escritorio)**: no se permite que el usuario interactúe con Cortana cuando el dispositivo está en la pantalla de bloqueo (solo Windows 10 Escritorio).
- **Notificaciones del sistema en pantalla bloqueada**: se impide que los mensajes de alerta aparezcan en la pantalla de bloqueo del dispositivo.
- **Tiempo de espera de la pantalla (solo dispositivos móviles)**: se especifica el tiempo en segundos después de que se bloquee la pantalla, cuando se apagará.

## <a name="messaging"></a>Mensajería

- **Sincronización de mensajes (solo móvil)**: se deshabilitan Mensajes en cualquier dispositivo y la copia de seguridad y restauración de los mensajes de texto.
- **MMS (solo móvil)**: se deshabilita la funcionalidad de envío y recepción de MMS en el dispositivo.
- **RCS (solo móvil)**: se deshabilita la funcionalidad de envío o recepción de Rich Communication Services en el dispositivo.

## <a name="microsoft-edge-browser"></a>Explorador Microsoft Edge

### <a name="start-experience"></a>Inicio de la experiencia

- **Iniciar Microsoft Edge con**: elija qué páginas se abren cuando se inicia Microsoft Edge. Las opciones son:
  - **Páginas de inicio**: Microsoft Edge empieza con la página de inicio predeterminada que define el SO.
  - **Página Nueva pestaña**: Microsoft Edge carga todo lo que se define en la configuración **Dirección URL de la página Nueva pestaña**.
  - **Página de última sesión**: Microsoft Edge carga la página de la última sesión. 
  - **Custom start page** (Página de inicio personalizada): Microsoft Edge carga la página de inicio que ha definido el administrador de TI.
- **El usuario puede cambiar las páginas de inicio**: al seleccionar **Permitir**, los usuarios pueden cambiar las páginas de inicio. Los administradores pueden usar `EdgeHomepageUrls` para escribir las páginas de inicio que los usuarios ven de manera predeterminada al abrir Microsoft Edge. **No configurado** impide que los usuarios cambien las páginas de inicio.
- **Dirección URL de la página Nueva pestaña**: escriba la dirección URL que quiera abrir en la página Nueva pestaña. Por ejemplo, escriba `https://www.bing.com`.
- **Abrir contenido web en la página Nueva pestaña**: elija **Bloquear** para impedir que Microsoft Edge abra un sitio web en una pestaña nueva. Cuando se bloquea, se abre una pestaña nueva en blanco. **No configurado** usa el comportamiento predeterminado del SO del dispositivo, el que puede permitir que los usuarios elijan lo que se muestra.
- **Botón Inicio**: elija lo que sucede al seleccionar el botón Inicio. Las opciones son:
  - **Páginas de inicio**: se abre la opción que ha elegido en la configuración **Iniciar Microsoft Edge con**.
  - **Página Nueva pestaña**: se abre la opción que ha elegido en la configuración **Dirección URL de la página Nueva pestaña**.
  - **Dirección URL personalizada del botón Inicio**: se abre la opción que ha elegido en la configuración **Dirección URL del botón de inicio**.
  - **Ocultar botón Inicio**: se oculta el botón Inicio.
- **El usuario puede cambiar el botón Inicio**: al seleccionar **Permitir**, los usuarios pueden cambiar el botón Inicio. Los cambios del usuario reemplazan cualquier configuración del administrador en el botón Inicio. **No configurado** usa el comportamiento predeterminado del SO del dispositivo, que puede impedir que los usuarios cambien la forma en que el administrador configuró el botón Inicio.
- **Mostrar la página Primera experiencia de ejecución**: si selecciona **Bloquear**, se impide que se muestre la página de introducción la primera vez que ejecuta Microsoft Edge. Esta característica permite que las empresas (por ejemplo, aquellas que utilizan configuraciones de cero emisiones) bloqueen esta página. **No configurado** muestra la página de introducción.
  - **Dirección URL de la primera experiencia de ejecución**: escriba la dirección URL de la página que se mostrará la primera vez que un usuario ejecute Microsoft Edge (solo Windows 10 Mobile).
- **Elementos emergentes**: elija **Bloquear** para detener las ventanas emergentes en el explorador. Solo se aplica a Windows 10 Escritorio. **No configurado** permite los elementos emergentes en el explorador web.
- **Enviar el tráfico de la intranet a Internet Explorer**: si elige **Permitir**, los usuarios pueden abrir sitios web de la intranet en Internet Explorer en lugar de Microsoft Edge (solo Windows 10 Escritorio). **No configurado** permite que los usuarios utilicen Microsoft Edge.
- **Ubicación de la lista de sitios en Modo de empresa**: escriba la dirección URL que incluye una lista de los sitios web que se abren en el Modo de empresa. Los usuarios no pueden cambiar esta lista. Solo se aplica a Windows 10 Escritorio.
- **Mensaje al abrir sitios en Internet Explorer**: use este valor para configurar Microsoft Edge de modo que muestre una notificación antes de que se abra un sitio en Internet Explorer 11. Las opciones son:
  - **No configurado**: se usa el comportamiento predeterminado del sistema operativo, que puede que no muestre un mensaje.
  - **Show message without option to open sites in Microsoft Edge** (Mostrar el mensaje sin la opción para abrir sitios en Microsoft Edge): se muestra el mensaje al abrir sitios en Internet Explorer. Los sitios se abren en IE. No hay ninguna opción para abrir sitios en Microsoft Edge.
  - **Show message when opening sites in Microsoft Edge** (Mostrar un mensaje cuando se abran sitios en Microsoft Edge): se muestra el mensaje al abrir sitios en Internet Explorer. El mensaje incluye un vínculo **Keep going in Microsoft Edge** (Seguir en Microsoft Edge) para que los usuarios puedan elegir Microsoft Edge en lugar de IE.

  > [!IMPORTANT]
  > Esta configuración requiere habilitar la configuración **Configure the Enterprise Mode Site List** (Configurar la lista de sitios del Modo de empresa), **Send all intranet sites to Internet Explorer 11** (Enviar todos los sitios de intranet a Internet Explorer 11) o ambas.

- **Lista de compatibilidad de Microsoft**: si elige **Bloquear**, se impide la lista de compatibilidad de Microsoft en Microsoft Edge. La lista de Microsoft ayuda a que Microsoft Edge muestre de manera correcta sitios con problemas de compatibilidad conocidos. **No configurado** permite usar una lista de compatibilidad de Microsoft.
- **Precarga de páginas de inicio y página Nueva pestaña**: elija **Bloquear** para impedir que Microsoft Edge precargue las páginas de inicio y la página Nueva pestaña. La precarga minimiza el tiempo de inicio de Microsoft Edge y carga una pestaña nueva. **No configurado** usa el comportamiento predeterminado del sistema operativo, que puede ser precargar estas páginas.
- **Inicio previo de páginas de inicio y página Nueva pestaña**: elija **Bloquear** para impedir que Microsoft Edge inicie previamente las páginas de inicio y la página Nueva pestaña. El inicio previo ayuda al rendimiento de Microsoft Edge y minimiza el tiempo necesario para iniciar Microsoft Edge. **No configurado** usa el comportamiento predeterminado del sistema operativo, que puede ser iniciar previamente estas páginas.

### <a name="favorites-and-search"></a>Favoritos y búsqueda

- **Barra de favoritos**: elija qué le ocurre a la barra de favoritos en cualquier página de Microsoft Edge. Las opciones son:
  - **No configurado**: se usa el comportamiento predeterminado del sistema operativo, que puede ser ocultar la barra de favoritos en todas las páginas. El usuario puede cambiar esta configuración.
  - **Ocultar**: se oculta la barra de favoritos en todas las páginas. El usuario no puede cambiar esta configuración.
  - **Mostrar**: se muestra la barra de favoritos en todas las páginas. El usuario no puede cambiar esta configuración.
- **Lista de favoritos**: agregue una lista de direcciones URL al archivo de favoritos. Por ejemplo, agregue `http://contoso.com/favorites.html`.
- **Restringir los cambios a Favoritos**: elija **Bloquear** para impedir que los usuarios agreguen, importen, ordenen o modifiquen la lista de favoritos. **No configurado** usa el valor predeterminado del sistema operativo, que puede permitir que los usuarios cambien la lista.
- **Sincronizar favoritos entre exploradores de Microsoft (solo escritorio)**: si elige **Requerir**, se obliga a Windows a sincronizar los favoritos entre Internet Explorer y Microsoft Edge. Las incorporaciones, eliminaciones, modificaciones y cambios de orden en los favoritos se comparten entre los distintos exploradores.  **No configurado** usa el valor predeterminado del sistema operativo, que puede dar a los usuarios la opción de sincronizar los favoritos entre los exploradores.
- **Motor de búsqueda predeterminado**: elija el motor de búsqueda predeterminado del dispositivo. Los usuarios finales pueden cambiar este valor en cualquier momento. Las opciones son:
  - Default
  - Bing
  - Google
  - Yahoo
  - Valor personalizado
- **Sugerencias de búsqueda**: si elige **No configurado**, se permite que el motor de búsqueda sugiera sitios a medida que escribe las frases de búsqueda en la barra de direcciones. **Bloquear** impide esta característica.

### <a name="privacy-and-security"></a>Privacidad y seguridad

- **Exploración de InPrivate**: si elige **Bloquear**, se impide que los usuarios finales abran sesiones de exploración de InPrivate. **No configurado** permite esta característica Administrador de contraseñas de Microsoft Edge.
- **Guardar historial de exploración**: si elige **Bloquear**, se impide que Microsoft Edge guarde el historial de exploración. **No configurado** permite guardar el historial de exploración.
- **Borrar datos de navegación al salir (solo escritorio)**: si elige **Requerir**, se borran el historial y los datos de exploración cuando el usuario sale de Microsoft Edge. **No configurado** usa el valor predeterminado del sistema operativo, que puede almacenar en caché los datos de exploración.
- **Sincronizar la configuración del explorador entre los dispositivos del usuario**: elija cómo quiere sincronizar la configuración del explorador entre dispositivos. Las opciones son:
  - **Permitir**: permita la sincronización de la configuración del explorador Microsoft Edge entre los dispositivos del usuario.
  - **Bloquear y habilitar el reemplazo de usuarios**: bloquee la sincronización de la configuración del explorador Microsoft Edge entre los dispositivos del usuario. Los usuarios pueden reemplazar esta configuración.
  - **Bloquear**: bloquee la sincronización de la configuración del explorador Microsoft Edge entre los dispositivos del usuario. Los usuarios no pueden reemplazar esta configuración.
- **Administrador de contraseñas**: si elige **Bloquear**, se deshabilita la característica Administrador de contraseñas de Microsoft Edge. **No configurado** permite esta característica Administrador de contraseñas de Microsoft Edge.
- **Cookies**: elija cómo se administran las cookies en el explorador web. Las opciones son:
  - **Permitir**: las cookies se almacenan en el dispositivo.
  - **Bloquear todas las cookies**: las cookies no se almacenan en el dispositivo.
  - **Bloquear solo cookies de terceros**: las cookies de terceros o de asociados no se almacenan en el dispositivo.
- **Autorrelleno**: si elige **Bloquear**, se deshabilita la característica Autorrelleno en el dispositivo. **No configurado** permite que los usuarios cambien la configuración de Autorrellenar en el explorador (solo Windows 10 Escritorio).
- **Enviar encabezados de no seguimiento**: **No configurado** requiere que los dispositivos envíen encabezados de no seguimiento a los sitios web que solicitan información de seguimiento (recomendado). Elija **Bloquear** para impedir que el dispositivo envíe estos encabezados, lo que permitirá que los sitios web hagan seguimiento del usuario.
- **Dirección IP de Localhost para WebRTC**: si elige **Bloquear**, se impide que la dirección IP de localhost de los usuarios se muestre cuando se hacen llamadas telefónicas a través del protocolo WebRTC. **No configurado** permite que la dirección IP de localhost de los usuarios se muestre cuando se hacen llamadas telefónicas a través de este protocolo.
- **Recopilación de datos para iconos dinámicos**: elija **Bloquear** para impedir que Windows recopile información de iconos dinámicos cuando se ancla un sitio al menú Inicio desde Microsoft Edge. **No configurado** permite recopilar esta información.
- **User can override certificate errors** (El usuario puede invalidar los errores de certificado): si elige **Bloquear**, se impide que los usuarios accedan a sitios web con errores de SSL o TLS. **No configurado** permite que los usuarios accedan a estos sitios.

### <a name="additional"></a>Adicional

- **Explorador de Microsoft Edge (solo móvil)**: elija **Bloquear** para impedir el uso de Microsoft Edge en el dispositivo. Si bloquea Microsoft Edge, la configuración individual solo se aplica a los equipos de escritorio. **No configurado** permite usar el explorador web Microsoft Edge en el dispositivo.
- **Lista desplegable de la barra de direcciones (solo escritorio)**: si elige **Bloquear**, se impide que Microsoft Edge muestre una lista de sugerencias en una lista desplegable cuando escriba. Esta opción ayuda a minimizar el ancho de banda de red entre Microsoft Edge y los servicios de Microsoft. **No configurado** permite que Microsoft Edge muestre una lista de sugerencias.
- **Pantalla completa**: elija **Bloquear** para impedir que Microsoft Edge solo muestre el contenido web y oculte la interfaz de Microsoft Edge (modo de pantalla completa). **No configurado** usa el valor predeterminado del sistema operativo, que permite que Microsoft Edge use el modo de pantalla completa.
- **Acerca de los indicadores**: si elige **Bloquear**, se impide que los usuarios finales accedan a la página `about:flags` en Microsoft Edge, que incluye la configuración experimental y del desarrollador. **No configurado** usa el valor predeterminado del sistema operativo, que puede permitir el acceso a la página `about:flags`.
- **Herramientas de desarrollo**: si elige **Bloquear**, se impide que los usuarios finales abran las herramientas de desarrollo de Microsoft Edge. **No configurado** permite que los usuarios abran las herramientas de desarrollo.
- **Extensiones**: si elige **No configurado**, se permite que los usuarios finales instalen extensiones de Microsoft Edge en el dispositivo. **Bloquear** impide la instalación.
- **Transfiriendo localmente extensiones para desarrolladores**: si elige **Bloquear**, se impide que Microsoft Edge transfiera localmente, lo que instala y ejecuta versiones no comprobadas con la característica **Cargar extensiones**. **No configurado** usa el valor predeterminado del sistema operativo, que puede permitir la instalación de prueba.
- **Required extensions** (Extensiones obligatorias): elija cuáles son las extensiones que los usuarios finales no pueden desactivar en Microsoft Edge. Escriba los nombres de familia de paquete y seleccione **Agregar**. [Buscar un nombre de familia de paquete (PFN)](https://docs.microsoft.com/sccm/protect/deploy-use/find-a-pfn-for-per-app-vpn) brinda algunas guías.

  También puede **Importar** un archivo .csv que incluya los nombres de familia de paquete.

- **JavaScript**: elija **Bloquear** para impedir que los scripts de Java del explorador se ejecuten en el dispositivo. **No configurado** permite la ejecución de scripts, como JavaScript, en el explorador Microsoft Edge.

## <a name="network-proxy"></a>Proxy de red

- **Detectar automáticamente configuración de proxy**: cuando esta opción está habilitada, el dispositivo intenta encontrar la ruta de acceso a un script de configuración automática del proxy.
- **Usar script de proxy**: seleccione esta opción para especificar una ruta de acceso a un script de configuración automática para configurar el servidor proxy.
  - **URL del script de configuración**: escriba la URL de un script de configuración automática que quiera usar para configurar el servidor proxy.
- **Usar un servidor proxy manual**: seleccione esta opción si quiere especificar la información del servidor proxy de forma manual.
  - **Dirección**: escriba el nombre o la dirección IP del servidor proxy.
  - **Número de puerto**: escriba el número de puerto del servidor proxy.
  - **Excepciones del proxy**: escriba las direcciones URL que no deben usar el servidor proxy. Use un punto y coma para separar cada elemento.
  - **Omitir el servidor proxy para direcciones locales**: si no quiere usar el servidor proxy para direcciones locales de la intranet, habilite esta opción.

## <a name="password"></a>Contraseña

- **Contraseña**: Exige que el usuario final escriba una contraseña para acceder al dispositivo.
  - **Tipo de contraseña requerida**: se especifica si la contraseña debe ser solo numérica o alfanumérica.
  - **Longitud mínima de la contraseña**: Solo se aplica a Windows 10 Mobile.
  - **Número de errores de inicio de sesión antes de borrar el dispositivo**: para los dispositivos que ejecutan Windows 10: si el dispositivo tiene BitLocker habilitado, se pondrá en el modo de recuperación de BitLocker cuando el inicio de sesión falle el número de veces especificado. Si el dispositivo no tiene habilitado BitLocker, no se aplica esta configuración. Para los dispositivos que ejecutan Windows 10 Mobile: cuando el inicio de sesión falle el número de veces especificado, el dispositivo se borrará.
  - **Máximo de minutos de inactividad hasta que se bloquea la pantalla**: Especifica el tiempo durante el que un dispositivo debe estar inactivo antes de que se bloquee la pantalla.
  - **Expiración de la contraseña (días)**: Especifica el período de tiempo tras el que debe cambiarse la contraseña del dispositivo.
  - **Impedir la reutilización de contraseñas anteriores**: Especifica el número de contraseñas usadas anteriormente que recuerda el dispositivo.
  - **Requerir contraseña cuando el dispositivo vuelve de un estado de inactividad (solo móviles)**: Especifica que el usuario debe escribir una contraseña para desbloquear el dispositivo (solo Windows 10 Mobile).
  - **Contraseñas sencillas**: le permite el uso de contraseñas sencillas, como 1111 y 1234. Esta configuración también permite o bloquea el uso de contraseñas de imagen de Windows.
- **Cifrado**: Habilita el cifrado en dispositivos de destino

## <a name="per-app-privacy-exceptions"></a>Excepciones de privacidad para cada aplicación

Puede agregar aplicaciones que deben tener un comportamiento de privacidad diferente del definido en "Privacidad determinada".

- **Nombre del paquete**: nombre de familia de paquete de la aplicación.
- **Nombre de la aplicación**: nombre de la aplicación.

### <a name="exceptions"></a>Excepciones

- **Información de la cuenta**: defina si esta aplicación puede acceder al nombre de usuario, la imagen y otra información de contacto.
- **Aplicaciones en segundo plano**: defina si esta aplicación puede ejecutarse en segundo plano.
- **Calendario**: defina si esta aplicación puede acceder al calendario.
- **Historial de llamadas**: defina si esta aplicación puede acceder al historial de llamadas.
- **Cámara**: defina si esta aplicación puede acceder a la cámara.
- **Contactos**: defina si esta aplicación puede acceder a los contactos.
- **Correo electrónico**: defina si esta aplicación puede acceder al correo electrónico.
- **Ubicación**: defina si esta aplicación puede acceder a información de ubicación.
- **Mensajería**: defina si esta aplicación puede leer o enviar mensajes de texto o MMS.
- **Micrófono**: defina si esta aplicación puede usar el micrófono.
- **Movimiento**: defina si esta aplicación puede acceder a la información de movimiento del dispositivo.
- **Notificaciones**: defina si esta aplicación puede acceder a las notificaciones.
- **Teléfono**: defina si esta aplicación puede acceder al teléfono.
- **Radios**: algunas aplicaciones usan radios (por ejemplo, Bluetooth) en el dispositivo para enviar y recibir datos, y necesitan activar o desactivar estas radios. Define si esta aplicación puede controlar estas radios.
- **Tareas**: defina si esta aplicación puede acceder a las tareas.
- **Dispositivos de confianza**: elija si esta aplicación puede usar dispositivos de confianza (es decir, hardware ya conectado o que se proporciona con el dispositivo). Por ejemplo, use televisores, proyectores, etc. como dispositivos de confianza.
- **Comentarios y diagnósticos**: defina si esta aplicación puede acceder a la información de diagnóstico.
- **Sincronizar con dispositivos**: elija si esta aplicación puede compartir y sincronizar automáticamente información con dispositivos inalámbricos que no se emparejan explícitamente con el dispositivo.

## <a name="personalization"></a>Personalization

- **URL de imagen de fondo de escritorio (solo equipos de escritorio)**: escriba la URL de una imagen en formato JPEG que quiera usar como fondo de escritorio de Windows. Los usuarios no pueden cambiar la imagen.

## <a name="printer"></a>Impresora

- **Impresoras**: lista de impresoras locales que se han agregado.
- **Impresora predeterminada**: establezca la impresora predeterminada.
- **User access to add new printers** (Acceso de usuarios para agregar nuevas impresoras): permita o bloquee el uso de las impresoras locales.

## <a name="privacy"></a>Privacidad

- **Personalización de entrada**: no se permite el uso de servicios de voz basados en la nube para Cortana, Dictado o aplicaciones de Microsoft Store. Si permite estos servicios, Microsoft puede recopilar datos de voz para mejorar el servicio.
- **Aceptación automática de los mensajes de consentimiento del usuario sobre emparejamiento y privacidad**: permita que Windows acepte automáticamente los mensajes de consentimiento de privacidad y emparejamiento al ejecutar las aplicaciones.
- **Publicar las actividades del usuario**: si elige **Bloquear**, se impiden las experiencias compartidas y la detección de recursos usados recientemente en el conmutador de tareas.
- **Solo actividades locales**: si elige **Bloquear**, se impiden las experiencias compartidas y la detección de recursos usados recientemente en el conmutador de tareas, según la actividad local únicamente.

Puede configurar la información a la que pueden tener acceso todas las aplicaciones del dispositivo. Puede definir excepciones para cada aplicación mediante **excepciones de privacidad de cada aplicación**.

### <a name="exceptions"></a>Excepciones

- **Información de la cuenta**: defina si esta aplicación puede acceder al nombre de usuario, la imagen y otra información de contacto.
- **Aplicaciones en segundo plano**: defina si esta aplicación puede ejecutarse en segundo plano.
- **Calendario**: defina si esta aplicación puede acceder al calendario.
- **Historial de llamadas**: defina si esta aplicación puede acceder al historial de llamadas.
- **Cámara**: defina si esta aplicación puede acceder a la cámara.
- **Contactos**: defina si esta aplicación puede acceder a los contactos.
- **Correo electrónico**: defina si esta aplicación puede acceder al correo electrónico.
- **Ubicación**: defina si esta aplicación puede acceder a información de ubicación.
- **Mensajería**: defina si esta aplicación puede leer o enviar mensajes de texto o MMS.
- **Micrófono**: defina si esta aplicación puede usar el micrófono.
- **Movimiento**: defina si esta aplicación puede acceder a la información de movimiento del dispositivo.
- **Notificaciones**: defina si esta aplicación puede acceder a las notificaciones.
- **Teléfono**: defina si esta aplicación puede acceder al teléfono.
- **Radios**: algunas aplicaciones usan radios (por ejemplo, Bluetooth) en el dispositivo para enviar y recibir datos, y necesitan activar o desactivar estas radios. Define si esta aplicación puede controlar estas radios.
- **Tareas**: defina si esta aplicación puede acceder a las tareas.
- **Dispositivos de confianza**: elija si esta aplicación puede usar dispositivos de confianza. Es decir, hardware ya conectado o que se proporciona con el dispositivo. Por ejemplo, use televisores, proyectores, etc. como dispositivos de confianza.
- **Comentarios y diagnósticos**: elija si esta aplicación puede acceder a la información de diagnóstico.
- **Sincronización con dispositivos**: define si esta aplicación puede compartir y sincronizar información automáticamente con dispositivos inalámbricos que no se emparejan explícitamente con este PC, tableta o teléfono.

## <a name="projection"></a>Proyección

- **Entrada de usuario desde receptores de pantalla inalámbricos**: se bloquea la entrada de usuario desde receptores de pantalla inalámbricos.
- **Proyección en este equipo**: se impide que otros dispositivos encuentren el equipo para proyección.
- **Requerir PIN para emparejamiento**: se requiere un PIN cuando se conecta a un dispositivo de proyección.

## <a name="reporting-and-telemetry"></a>Informes y telemetría

- **Compartir los datos de uso**: elija el nivel de datos de diagnóstico que se envía. Las opciones son:
  - Seguridad
  - Basic
  - Mejorado
  - Full
- **Send Microsoft Edge browsing data to Microsoft 365 Analytics** (Enviar los datos de exploración de Microsoft Edge a Microsoft 365 Analytics): para usar esta característica, establezca la configuración **Share usage data** (Compartir los datos de uso) en **Mejorado** o **Completo**. Esta característica controla los datos que Microsoft Edge envía a Microsoft 365 Analytics para los dispositivos empresariales que tienen configurado un identificador comercial. Las opciones son:
  - **No configurado**: se usa el valor predeterminado del sistema operativo, que puede que no envíe ningún dato del historial de exploración.
  - **Only send intranet data** (Solo enviar datos de la intranet): se permite que el administrador envíe el historial de datos de la intranet.
  - **Only send internet data** (Solo enviar datos de Internet): se permite que el administrador envíe el historial de datos de Internet.
  - **Send intranet and internet data** (Enviar datos de la intranet e Internet): se permite que el administrador envíe el historial de datos de la intranet e Internet.
- **Servidor proxy de telemetría**: escriba el nombre de dominio completo (FQDN) o la dirección IP de un servidor proxy para reenviar las solicitudes de Telemetría y experiencias del usuario conectado mediante una conexión de Capa de sockets seguros (SSL). El formato de esta configuración es *servidor*:*puerto*. Si se produce un error en el proxy mencionado o si no hay ningún proxy especificado cuando esta directiva está habilitada, los datos de Telemetría y experiencias del usuario conectado no se envían y permanecen en el dispositivo local.

  Formatos de ejemplo:

  ```
  IPv4: 192.246.246.106:100
  IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100
  FQDN: www.contoso.com:345
  ```

## <a name="search"></a>Buscar

- **Búsqueda segura (solo móvil)**: se controla cómo Cortana filtra el contenido para adultos en los resultados de la búsqueda. Puede seleccionar **Strict** (Estricto), **Moderate** (Moderado) o permitir que el usuario final elija su propia configuración.
- **Mostrar los resultados de los sitios web en la búsqueda**: bloquee o permita que aparezcan resultados de sitios web en las búsquedas realizadas en el dispositivo.

## <a name="start"></a>Start

- **Diseño del menú Inicio**: para personalizar el menú Inicio en los dispositivos de escritorio, puede cargar un archivo XML que incluya sus personalizaciones, así como el orden en que aparecen las aplicaciones, entre otras opciones. Los usuarios no pueden cambiar el diseño del menú Inicio que especifique usted.
- **Anclar los sitios web a iconos del menú Inicio**: importe imágenes desde Microsoft Edge que se muestran como vínculos en el menú Inicio de Windows de los dispositivos de escritorio.
- **Desanclar aplicaciones de la barra de tareas**: elija **Bloquear** para impedir que el usuario desancle aplicaciones del menú Inicio.
- **Cambio rápido de usuario**: elija **Bloquear** para impedir el cambio de usuarios que han iniciado sesión al mismo tiempo sin cerrar la sesión.
- **La mayoría de las aplicaciones usadas**: seleccione **Bloquear** para que las aplicaciones más usadas no se muestren en el menú Inicio. También deshabilita la alternancia correspondiente en la aplicación Configuración.
- **Aplicaciones agregadas recientemente**: seleccione **Bloquear** para que las aplicaciones agregadas recientemente no se muestren en el menú Inicio. También deshabilita la alternancia correspondiente en la aplicación Configuración.
- **Modo de pantalla de inicio**: elija cómo se muestra la pantalla de inicio. Puede elegir **Pantalla completa** o **Pantalla parcial**.
- **Elementos abiertos recientemente en listas de accesos directos**: seleccione **Bloquear** para que las listas de accesos directos recientes no se muestren en el menú Inicio ni en la barra de tareas. También deshabilita la alternancia correspondiente en la aplicación Configuración.
- **Lista de aplicaciones**: elija cómo se muestra la aplicación Configuración. Las opciones son: 
  - Contraer
  - Contraer y deshabilitar la aplicación Configuración 
  - Quitar y deshabilitar la aplicación Configuración
- **Botón de encendido**: seleccione **Bloquear** para que el botón de encendido no se muestre en el menú Inicio.
- **Icono del usuario**: seleccione **Bloquear** para que el icono del usuario no se muestre en el menú Inicio.
  - **Bloquear**: seleccione **Bloquear** para que la opción `Lock` no se muestre en el icono del usuario del menú Inicio.
  - **Cerrar sesión**: seleccione **Bloquear** para que la opción `Sign out` no se muestre en el icono del usuario del menú Inicio.
- **Apagar**: seleccione **Bloquear** para que las opciones `Update and shut down` y `Shut down` no se muestren en el botón de encendido del menú Inicio.
- **Suspender**: seleccione **Bloquear** para que la opción `Sleep` no se muestre en el botón de encendido del menú Inicio.
- **Hibernar**: seleccione **Bloquear** para que la opción `Hibernate` no se muestre en el botón de encendido del menú Inicio.
- **Cambiar cuenta**: seleccione **Bloquear** para que la opción `Switch account` no se muestre en el icono del usuario del menú Inicio.
- **Opciones de reinicio**:  seleccione **Bloquear** para que las opciones `Update and restart` y `Restart` no se muestren en el botón de encendido del menú Inicio.
- **Documentos en Inicio**: oculte o muestre la carpeta Documentos en el menú Inicio de Windows.
- **Descargas en Inicio**: oculte o muestre la carpeta Descargas en el menú Inicio de Windows.
- **Explorador de archivos en Inicio**: oculte o muestre la aplicación Explorador de archivos en el menú Inicio de Windows.
- **Grupo Hogar en Inicio**: oculte o muestre la carpeta Grupo Hogar en el menú Inicio de Windows.
- **Música en Inicio**: oculte o muestre la carpeta Música en el menú Inicio de Windows.
- **Red en Inicio**: oculte o muestre la carpeta Red en el menú Inicio de Windows.
- **Carpeta Personal en Inicio**: oculte o muestre la carpeta Personal en el menú Inicio de Windows.
- **Imágenes en Inicio**: oculte o muestre la carpeta de imágenes en el menú Inicio de Windows.
- **Configuración en Inicio**: oculte o muestre la aplicación Configuración en el menú Inicio de Windows.
- **Vídeos en Inicio**: oculte o muestre la carpeta de vídeos en el menú Inicio de Windows.

## <a name="windows-defender-smart-screen"></a>SmartScreen de Windows Defender

- **SmartScreen para Microsoft Edge**: permite a SmartScreen de Microsoft Edge el acceso al sitio y las descargas de archivos.
- **Acceso a sitios malintencionados**: impida que los usuarios omitan las advertencias del filtro SmartScreen de Windows Defender, así como que vayan al sitio.
- **Descarga de archivos no comprobados**: impida que los usuarios omitan las advertencias del filtro SmartScreen de Windows Defender, así como que descarguen archivos no comprobados.

## <a name="windows-spotlight"></a>Contenido destacado de Windows

- **Contenido destacado de Windows**: use esta configuración para bloquear todas las funciones de Contenido destacado de Windows en los dispositivos con Windows 10. Si bloquea esta configuración, las siguientes opciones no estarán disponibles:
  - **Contenido destacado de Windows en la pantalla de bloqueo**: impida que Contenido destacado de Windows muestre información en la pantalla de bloqueo del dispositivo.
  - **Sugerencias de terceros en Contenido destacado de Windows**: impida que Contenido destacado de Windows sugiera contenido que no haya publicado Microsoft.
  - **Características de consumidor**: le permite bloquear las características de consumidor, como las sugerencias del menú Inicio y las notificaciones de pertenencia.
  - **Sugerencias de Windows**: le permite impedir que las sugerencias emergentes se muestren en Windows.
  - **Contenido destacado de Windows en el centro de actividades**: impida que las sugerencias de Contenido destacado de Windows, como una nueva aplicación o contenido de seguridad, aparezcan en el centro de actividades de Windows.
  - **Personalización de Contenido destacado de Windows**: impida que Contenido destacado de Windows personalice los resultados en función del uso de un dispositivo.
  - **Experiencia de bienvenida de Windows**: bloquee la experiencia de bienvenida de Windows que muestra al usuario información sobre características nuevas o actualizadas.

## <a name="windows-defender-antivirus"></a>Antivirus de Windows Defender

- **Supervisión en tiempo real**: Habilita el análisis en tiempo real de malware, spyware y otro software no deseado.
- **Supervisión de comportamiento**: Permite a Defender comprobar determinados patrones conocidos de actividad sospechosa en los dispositivos.
- **Sistema de inspección de red (NIS)**: NIS ayuda a proteger los dispositivos contra las vulnerabilidades de seguridad basadas en red. Usa las firmas de vulnerabilidades conocidas de Microsoft Endpoint Protection Center para ayudar a detectar y bloquear el tráfico malintencionado.
- **Examinar todas las descargas**: Controla si Defender analiza todos los archivos descargados de Internet.
- **Examinar scripts cargados en exploradores web de Microsoft**: Permite que Defender examine scripts que se usan en Internet Explorer.
- **Acceso de usuario final a Defender**: Controla si la interfaz de usuario de Windows Defender se oculta a los usuarios finales. Cuando se cambia esta configuración, surtirá efecto la próxima vez que se reinicie el equipo del usuario final.
- **Intervalo de actualización de firma (en horas)**: especifique el intervalo durante el que Defender buscará nuevos archivos de firma.
- **Supervisar la actividad de archivos y programas**: Permite que Defender supervise la actividad de archivos y programas en los dispositivos.
- **Días antes de eliminar el malware en cuarentena**: Permite que Defender continúe realizando el seguimiento de malware resuelto durante el número de días especificado para que pueda comprobar de forma manual los dispositivos previamente afectados. Si establece el número de días en **0**, el malware permanece en la carpeta de cuarentena y no se quita automáticamente.
- **Límite de uso de la CPU durante un examen**: Permite limitar la cantidad de CPU que pueden usar los exámenes (de **1** a **100**).
- **Examinar archivos de almacenamiento**: Permite que Defender examine archivos almacenados, como archivos Zip o Cab.
- **Examinar mensajes de correo entrante**: Permite que Defender analice los mensajes de correo electrónico cuando llegan al dispositivo.
- **Examinar unidades extraíbles durante un examen completo**: Permite que Defender analice unidades extraíbles, como sticks USB.
- **Examinar unidades de red asignadas durante un examen completo**: Permite que Defender examine archivos en unidades de red asignadas.
  Si los archivos de la unidad son de solo lectura, Defender no puede quitar el malware que se encuentre en ellos.
- **Examinar archivos abiertos desde carpetas de red**: permita que Defender examine archivos en unidades de red compartidas (por ejemplo, archivos a los que se accede desde una ruta de acceso UNC). Si los archivos de la unidad son de solo lectura, Defender no puede quitar el malware que se encuentre en ellos.
- **Protección de la nube**: Permite o bloquea la recepción por parte de Microsoft Active Protection Service de información relativa a la actividad de malware de los dispositivos que administra. Esta información se usa para mejorar el servicio en el futuro.
- **Preguntar a los usuarios antes de enviar muestras**: se controla si los archivos potencialmente malintencionados que podrían requerir un análisis en mayor profundidad se envían automáticamente a Microsoft.
- **Hora a la que se realizará un examen rápido diario**: Permite programar un examen rápido que se lleva a cabo diariamente a la hora que seleccione.
- **Tipo de examen del sistema para realizar**: escriba el nivel de examen que se ejecuta cuando se programa un examen del sistema.
- **Detectar aplicaciones potencialmente no deseadas**: elija el nivel de protección cuando Windows detecte aplicaciones potencialmente no deseadas entre los siguientes:
  - **Bloquear**
  - **Auditoría** Para más información sobre aplicaciones potencialmente no deseadas, consulte [Detectar y bloquear aplicaciones potencialmente no deseadas](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus).
- **Acciones para amenazas de malware detectadas**: use esta opción para elegir las acciones que quiere que Defender realice para cada nivel de amenaza que detecte (Bajo, Moderado, Alto y Grave). Las opciones son:
  - **Limpiar**
  - **Cuarentena**
  - **Quitar**
  - **Permitir**
  - **Definido por el usuario**
  - **Bloquear**

### <a name="windows-defender-antivirus-exclusions"></a>Exclusiones del antivirus de Windows Defender

- **Archivos y carpetas para excluir de exámenes y protección en tiempo real**: Agrega uno o varios archivos y carpetas como **C:\Path** o **%ProgramFiles%\Path\filename.exe** a la lista de exclusiones. Estos archivos y carpetas no se incluyen en los exámenes en tiempo real ni programados.
- **Extensiones de archivo para excluir de exámenes y protección en tiempo real**: Agrega una o varias extensiones de archivo como **jpg** o **txt** a la lista de exclusiones. Los archivos con estas extensiones no se incluyen en los exámenes en tiempo real ni programados.
- **Procesos para excluir de exámenes y protección en tiempo real**: Agrega uno o varios procesos del tipo **.exe**, **.com** o **.scr** a la lista de exclusiones. Estos procesos no se incluyen en los exámenes en tiempo real ni programados.

## <a name="next-steps"></a>Pasos siguientes

Para obtener detalles técnicos adicionales sobre cada configuración y sobre las ediciones de Windows compatibles, consulte [Windows 10 Policy CSP Reference](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) (Referencia sobre el CSP de directivas de Windows 10).
