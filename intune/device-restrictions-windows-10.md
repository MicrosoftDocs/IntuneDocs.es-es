---
title: 'Configuración de restricciones de dispositivos para Windows 10 en Microsoft Intune: Azure | Microsoft Docs'
description: Consulte una lista de todas las configuraciones y sus descripciones para crear restricciones de dispositivo en Windows 10 y dispositivos posteriores. Use estos valores en un perfil de configuración para controlar las capturas de pantalla, los requisitos de contraseña, la configuración de la pantalla completa, las aplicaciones de la tienda, el explorador Microsoft Edge, Windows Defender, el acceso a la nube, el menú de inicio y más en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/08/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8957c8d8aad2eaa1741b1a625afd4b5a41a8bb51
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "59423703"
---
# <a name="windows-10-and-newer-device-settings-to-allow-or-restrict-features-using-intune"></a>Configuración de dispositivos con Windows 10 y versiones posteriores para permitir o restringir características mediante Intune

En este artículo se enumeran y describen todos los diferentes valores de configuración que puede controlar en los dispositivos con Windows 10 y versiones posteriores. Como parte de la solución de administración de dispositivos móviles (MDM), use estos valores para habilitar o deshabilitar características, establecer reglas de contraseña, personalizar la pantalla de bloqueo, usar Windows Defender, etc.

Estos valores se agregan a un perfil de configuración de dispositivo en Intune y luego se asignan o implementan en los dispositivos con Windows 10.

> [!Note]
> No todas las opciones están disponibles en todas las ediciones de Windows. Para ver las ediciones admitidas, consulte el [directiva CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) (abre otro sitio web de Microsoft).

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración de dispositivo](device-restrictions-configure.md#create-the-profile).

## <a name="app-store"></a>Tienda de aplicaciones

- **Tienda de aplicaciones (solo dispositivos móviles)**: permitir o bloquear el uso de la tienda de aplicaciones en dispositivos Windows 10 Mobile.
- **Actualizar automáticamente las aplicaciones de la tienda**: permite que las aplicaciones instaladas de Microsoft Store se actualicen automáticamente.
- **Instalación de aplicaciones de confianza**: permite realizar una instalación de prueba de las aplicaciones firmadas con un certificado de confianza.
- **Desbloqueo de desarrollador**: permite que un usuario final modifique la configuración de desarrollador de Windows, como permitir las aplicaciones con instalación de prueba.
- **Datos de aplicación compartidos entre usuarios**: permite que las aplicaciones compartan datos entre distintos usuarios en el mismo dispositivo.
- **Usar solo una tienda privada**: habilite esta opción para permitir que los usuarios finales solo descarguen aplicaciones desde la tienda privada.
- **Inicio de aplicaciones de la tienda**: se usa para deshabilitar todas las aplicaciones instaladas previamente en el dispositivo o que se descargaron de Microsoft Store.
- **Instalar los datos de aplicación en el volumen del sistema**: esta opción hace que las aplicaciones dejen de almacenar datos en el volumen del sistema del dispositivo.
- **Instalar las aplicaciones en la unidad del sistema**: esta opción hace que las aplicaciones dejen de almacenar datos en la unidad del sistema del dispositivo.
- **Game DVR (solo equipos de escritorio)**: configura si se permite la grabación y difusión de los juegos.
- **Aplicaciones solo de la tienda**: configura si los usuarios pueden instalar aplicaciones de otros lugares distintos de la tienda de aplicaciones.

## <a name="cellular-and-connectivity"></a>Red de telefonía móvil y conectividad

- **Canal de datos móviles**: impide que los usuarios usen datos, como la navegación por la web, cuando están conectados a una red móvil. 
- **Itinerancia de datos**: permite la itinerancia entre redes al acceder a los datos.
- **VPN a través de la red de telefonía móvil**: controla si el dispositivo puede acceder a las conexiones VPN cuando se conecta a una red móvil.
- **Itinerancia de VPN a través de la red de telefonía móvil**: controla si el dispositivo puede acceder a conexiones VPN cuando está en itinerancia en una red móvil.
- **Bluetooth**: controla si el usuario puede habilitar y configurar Bluetooth en el dispositivo.
- **Detectabilidad de Bluetooth**: permite que otros dispositivos con Bluetooth habilitado detecten el dispositivo.
- **Emparejamiento previo Bluetooth**: permite que configure dispositivos Bluetooth específicos para emparejarse automáticamente con un dispositivo de host.
- **Anuncios de Bluetooth**: permite que el dispositivo reciba anuncios a través de Bluetooth.
- **Servicio de dispositivos conectados**: permite decidir si permitir el servicio de dispositivos conectados, que habilita la detección y la conexión a otros dispositivos Bluetooth.
- **NFC**: se permite al usuario habilitar y configurar características de transmisión de datos en proximidad (NFC) en el dispositivo.
- **Wi-Fi**: permite al usuario habilitar y configurar Wi-Fi en el dispositivo (solo Windows 10 Mobile).
- **Conectar automáticamente a zonas Wi-Fi**: permite que el dispositivo se conecte automáticamente a zonas Wi-Fi gratuitas y acepte automáticamente los términos y condiciones para la conexión.
- **Configuración manual de Wi-Fi**: controla si el usuario puede configurar sus propias conexiones Wi-Fi o si solo puede usar conexiones configuradas mediante un perfil Wi-Fi (solo Windows 10 Mobile).
- **Intervalo de detección de Wi-Fi**: permite especificar con qué frecuencia los dispositivos detectan redes Wi-Fi. Escriba un valor de 1 (más frecuente) a 500 (menos frecuente).
- **Servicios Bluetooth permitidos**: se indican como cadenas hexadecimales una lista de perfiles y servicios Bluetooth permitidos.

## <a name="cloud-and-storage"></a>Nube y almacenamiento

- **Cuenta Microsoft**: permite al usuario asociar una cuenta de Microsoft con el dispositivo.
- **Cuenta que no es Microsoft**: permite que los usuarios agreguen al dispositivo cuentas de correo electrónico que no estén asociadas a una cuenta de Microsoft.
- **Sincronización de configuración de cuenta Microsoft**: permite sincronizar la configuración de dispositivos y aplicaciones que están asociados con una cuenta de Microsoft entre dispositivos.
- **Ayudante para el inicio de sesión de cuentas Microsoft**: elija **Deshabilitar** para impedir que los usuarios finales controlen el servicio Ayudante para el inicio de sesión de Microsoft (wlidsvc), por ejemplo, que detengan o inicien manualmente el servicio. Cuando se establece en **No configurado**, el servicio wlidsvc NT usa el valor predeterminado del sistema operativo (SO), que puede permitir que los usuarios finales inicien y detengan el servicio. El sistema operativo usa este servicio para permitir que los usuarios inicien sesión en su cuenta Microsoft.

## <a name="cloud-printer"></a>Impresora en la nube

- **Dirección URL de detección de la impresora**: especifique la dirección URL para encontrar impresoras en la nube.
- **Dirección URL de autoridad de acceso a la impresora**: especifique la dirección URL del punto de conexión de autenticación para obtener tokens de OAuth. Por ejemplo, escriba algo parecido a `https://login.microsoftonline.com/your Azure AD Tenant ID`.
- **GUID de aplicación cliente nativa de Azure**: especifique el GUID de una aplicación cliente autorizada para obtener tokens de OAuth desde OAuthAuthority.
- **URI de recurso de servicio de impresión**: indique el URI de recurso de OAuth para el servicio de impresión configurado en Azure Portal. Por ejemplo, escriba algo parecido a `http://MicrosoftEnterpriseCloudPrint/CloudPrint`.
- **Máximo de impresoras para consultar (solo dispositivos móviles)**: indique el número máximo de impresoras que quiere que se consulten. Por ejemplo, escriba `10`.
- **URI de recurso de servicio de detección de impresora**: indique el URI de recurso de OAuth para el servicio de detección de impresora configurado en Azure Portal. Por ejemplo, escriba algo parecido a `http://MopriaDiscoveryService/CloudPrint`.

> [!TIP]
> Después de configurar la solución [Hybrid Cloud Print de Windows Server](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-overview), puede configurar estas opciones e implementarlas en dispositivos Windows.

## <a name="control-panel-and-settings"></a>Panel de control y configuración

- **Aplicación de configuración**: bloquea el acceso a la aplicación de configuración de Windows.
  - **Sistema**: bloquea el acceso al área de sistema de la aplicación de configuración.
    - **Modificación de la configuración de inicio/apagado y suspensión (solo equipos de escritorio)**: evita que el usuario final cambie la configuración de inicio/apagado y suspensión en el dispositivo.
  - **Dispositivos**: bloquea el acceso al área de dispositivos de la aplicación de configuración.
  - **Red e Internet**: bloquea el acceso al área de la red e Internet de la aplicación de configuración.
  - **Personalización**: bloquea el acceso al área de personalización de la aplicación de configuración.
  - **Cuentas**: bloquea el acceso al área de cuentas de la aplicación de configuración.
  - **Hora e idioma**: bloquea el acceso al área de hora e idioma de la aplicación de configuración.
    - **Modificación de la hora del sistema**: evita que el usuario final cambie la fecha y hora del dispositivo.
    - **Modificación de la configuración regional (solo equipos de escritorio)**: evita que el usuario final cambie la configuración regional en el dispositivo.
    - **Modificación de la configuración de idioma (solo equipos de escritorio)**: evita que el usuario cambie la configuración de idioma en el dispositivo.
  - **Juegos**: bloquea el acceso a la aplicación Juegos en la configuración.
  - **Accesibilidad**: bloquea el acceso al área de accesibilidad de la aplicación de configuración.
  - **Privacidad**: bloquea el acceso al área de privacidad de la aplicación de configuración.
  - **Actualización y seguridad**: bloquea el acceso al área de actualizaciones y seguridad de la aplicación de configuración.

## <a name="display"></a>Pantalla

- **Activar el ajuste de GDI para las aplicaciones**
- **Desactivar el ajuste de GDI para las aplicaciones**

  El ajuste de escala de PPP de GDI permite a las aplicaciones que no tienen en cuenta los PPP empezar a tenerlos en cuenta para cada monitor. Escriba las aplicaciones heredadas que tienen activado el ajuste de escala de PPP de GDI. Si el ajuste de escala de PPP de GDI está configurado tanto para activarse como desactivarse en una aplicación, el escalado estará desactivado para la aplicación.

## <a name="general"></a>General

- **Captura de pantalla (solo dispositivos móviles)**: permite que el usuario capture la pantalla del dispositivo como imagen.
- **Copiar y pegar (solo dispositivos móviles)**: permite acciones de copiar y pegar entre aplicaciones del dispositivo.
- **Cancelación manual de la suscripción**: permite al usuario eliminar manualmente la cuenta del área de trabajo desde el dispositivo.
  - Esta configuración de directiva no se aplica si el equipo está unido a Azure AD y la inscripción automática está habilitada. 
  - Esta configuración de directiva no se aplica a equipos que ejecuten Windows 10 Home.
- **Instalación manual del certificado raíz (solo dispositivos móviles)**: impide que el usuario instale manualmente certificados raíz y certificados CAP intermedios.

- **Cámara**: permite o bloquea el uso de la cámara en el dispositivo.
- **Sincronización de archivos de OneDrive**: bloquea la sincronización de archivos de OneDrive en el dispositivo.
- **Almacenamiento extraíble**: especifica si se pueden usar dispositivos de almacenamiento externo, como tarjetas SD, con el dispositivo.
- **Geolocalización**: especifica si el dispositivo puede usar la información de servicios de ubicación.
- **Conexión compartida**: permite el uso compartido de una conexión a Internet en el dispositivo.
- **Restablecimiento del teléfono**: controla si el usuario puede realizar un borrado en el dispositivo.
- **Conexión USB (solo dispositivos móviles)**: controla si los dispositivos pueden tener acceso a dispositivos de almacenamiento externo a mediante una conexión USB.
- **Modo antirrobo (solo dispositivos móviles)**: permite habilitar el modo antirrobo de Windows.
- **Cortana**: habilita o deshabilita el asistente de voz de Cortana.
- **Grabación de voz (solo dispositivos móviles)**: permite o bloquea el uso de la grabadora de voz del dispositivo.
- **Modificación del nombre del dispositivo**: evita que el usuario final cambie el nombre del dispositivo (solo para Windows 10 Mobile)
- **Agregar paquetes de aprovisionamiento**: bloquea el agente de configuración de tiempo de ejecución que instala los paquetes de aprovisionamiento.
- **Quitar paquetes de aprovisionamiento**: bloquea el agente de configuración de tiempo de ejecución que quita los paquetes de aprovisionamiento.
- **Detección de dispositivos**: bloquea la detección de un dispositivo por parte de otros dispositivos.
- **Conmutador de tareas (solo dispositivos móviles)**: bloquea el conmutador de tareas en el dispositivo.
- **Cuadro de diálogo de error de tarjeta SIM (solo dispositivos móviles)**: impide que un mensaje de error se muestre en el dispositivo si no se detecta una tarjeta SIM.
- **Área de trabajo de Ink**: impide que los usuarios accedan al área de trabajo de Ink. **No configurado** activa el área de trabajo de Ink y el usuario tiene permitido usarlo por encima de la pantalla de bloqueo.
- **Reimplementación automática**: permite a los usuarios con derechos administrativos eliminar todos los datos de usuario y las opciones de configuración con **Ctrl + Win + R** en la pantalla de bloqueo del dispositivo. En este caso, el dispositivo se vuelve a configurar e inscribir automáticamente para la administración.
- **Requerir que los usuarios se conecten a la red durante la instalación de dispositivos (solo Windows Insider)**: elija **Requerir** para que el dispositivo se conecte a una red antes de continuar más allá de la página Red durante la instalación de Windows 10.

  La configuración entre en vigor la próxima vez que se haya borrado o restablecer el dispositivo. Al igual que cualquier otra configuración de Intune, el dispositivo debe estar inscritos y administrado por Intune para recibir los valores de configuración. Pero una vez se ha inscrito y recibir las directivas, a continuación, restablecer el dispositivo aplica el valor durante la siguiente configuración de Windows.

- **Acceso directo a memoria**: **Bloquear** impide el acceso directo a memoria (DMA) a todos los puertos de bajada PCI de conexión instantánea hasta que un usuario inicia sesión en Windows. **Habilitado** (valor predeterminado) permite el acceso a DMA, incluso cuando un usuario no ha iniciado sesión.

  CSP: [DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess)

- **Finalizar los procesos del Administrador de tareas**: esta configuración determina si no sean administradores pueden utilizar el Administrador de tareas a las tareas de finalización. Si selecciona **Bloquear**, se impide que los usuarios estándar (no administradores) usen el Administrador de tareas para finalizar un proceso o una tarea en el dispositivo. Si selecciona **Sin configurar** (valor predeterminado), se permite que los usuarios estándar finalicen un proceso o una tarea mediante el Administrador de tareas.

## <a name="locked-screen-experience"></a>Experiencia de pantalla bloqueada

- **Notificaciones del centro de actividades (solo dispositivos móviles)**: permite que las notificaciones del centro de actividades aparezcan en la pantalla de bloqueo del dispositivo (solo Windows 10 Mobile).
- **URL de imagen de pantalla de bloqueo (solo equipos de escritorio)**: escriba la dirección URL de una imagen en formato JPEG que se usará como papel tapiz de la pantalla de bloqueo de Windows. Esta configuración bloquea la imagen. La imagen no se puede cambiar posteriormente.
- **Tiempo de espera de la pantalla configurable por el usuario (solo dispositivos móviles)**: permite que los usuarios configuren la cantidad de tiempo 
- **Cortana en pantalla bloqueada (solo equipos de escritorio)**: no permite que el usuario interactúe con Cortana cuando el dispositivo está en la pantalla de bloqueo (solo para equipos de escritorio de Windows 10).
- **Notificaciones del sistema en pantalla bloqueada**: impide que los mensajes de alerta se muestren en la pantalla de bloqueo del dispositivo.
- **Tiempo de espera de la pantalla (solo dispositivos móviles)**: especifica el tiempo en segundos después de que se bloquee la pantalla, cuando se apagará.

## <a name="messaging"></a>Mensajería

- **Sincronización de mensajes (solo móvil)**: deshabilita Mensajes en cualquier dispositivo y la copia de seguridad y restauración de los mensajes de texto.
- **MMS (solo dispositivos móviles)**: deshabilita la funcionalidad de envío y recepción de MMS en el dispositivo.
- **RCS (solo dispositivos móviles)**: deshabilita la funcionalidad de envío o recepción de Rich Communication Services en el dispositivo.

## <a name="microsoft-edge-browser"></a>Explorador Microsoft Edge

### <a name="use-microsoft-edge-kiosk-mode"></a>Usar el modo de pantalla completa de Microsoft Edge

Las opciones disponibles cambian en función de cuál sea su elección. Las opciones son:

- **No** (valor predeterminado): Microsoft Edge no se está ejecutando en modo de quiosco. Todas las configuraciones de Microsoft Edge están disponibles para cambiar y configurar.
- **Señalización digital/interactivo (quiosco con aplicación única)**: configuración de filtros de Microsoft Edge que se aplica para el modo de pantalla completa de Microsoft Edge de señalización Digital/interactivo para su uso únicamente en quioscos de aplicación sencilla de Windows 10. Elija esta opción para abrir una pantalla completa de la dirección URL y mostrar solo el contenido en dicho sitio Web. [Configurar la firma digital](https://docs.microsoft.com/windows/configuration/setup-digital-signage) proporciona más información sobre esta característica.
- **Pública la exploración de inPrivate (quiosco con aplicación única)**: configuración de filtros de Microsoft Edge que se aplica para el modo InPrivate exploración Microsoft Edge quiosco multimedia público para su uso en quioscos de aplicación sencilla de Windows 10. Ejecuta una versión de varias pestaña de Microsoft Edge.
- **Modo normal (quiosco con varias aplicaciones)**: configuración de filtros de Microsoft Edge que se aplica para el modo de quiosco de Normal Microsoft Edge. Se ejecuta una versión completa de Microsoft Edge con todas las características de exploración.
- **Exploración pública (quiosco con varias aplicaciones)**: configuración de filtros de Microsoft Edge que se aplica para la exploración pública en un quiosco con varias aplicaciones de Windows 10.  Ejecuta una versión de varias pestaña de InPrivate de Microsoft Edge.

> [!TIP]
> Para obtener más información sobre qué hacer estas opciones, consulte [tipos de configuración de modo de pantalla completa de Microsoft Edge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

Este perfil de restricciones de dispositivos está directamente relacionado con el perfil de quiosco que cree mediante el [configuración de pantalla de Windows](kiosk-settings-windows.md). En resumen:

1. Crear el [configuración de pantalla de Windows](kiosk-settings-windows.md) perfil para ejecutar el dispositivo en modo de quiosco. Seleccione Microsoft Edge que la aplicación y establezca el modo de pantalla completa de Microsoft Edge en el perfil de quiosco.
2. Crear el perfil de restricciones de dispositivo que se describe en este artículo y configurar características específicas y valores permitidos en Microsoft Edge. Asegúrese de elegir el mismo tipo de modo de pantalla completa de Microsoft Edge que seleccionado en el perfil de quiosco ([configuración de pantalla de Windows](kiosk-settings-windows.md)). 

    [Admite la configuración del modo de quiosco](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-policies-for-kiosk-mode) es un excelente recurso.

> [!IMPORTANT] 
> Asegúrese de asignar este perfil de Microsoft Edge a los mismos dispositivos de su perfil de quiosco ([configuración de pantalla de Windows](kiosk-settings-windows.md)).

[ConfigureKioskMode CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configurekioskmode)

### <a name="start-experience"></a>Inicio de la experiencia

- **Iniciar Microsoft Edge con**: elija qué páginas se abren cuando se inicia Microsoft Edge. Las opciones son:
  - **Start pages** (Páginas de inicio): Microsoft Edge empieza con la página de inicio predeterminada que define el SO
  - **New Tab page** (Página Pestaña nueva): Microsoft Edge carga todo lo que se define en la configuración **New Tab page URL** (Dirección URL de la página Pestaña nueva)
  - **Last session’s page** (Última página de la sesión): Microsoft Edge carga la última página de la sesión 
  - **Custom start page** (Página de inicio personalizada): Microsoft Edge carga la página de inicio definida por el administrador de TI
- **User can change Start pages** (El usuario puede cambiar las páginas de inicio): **Permitir** deja que los usuarios cambien las páginas de inicio. Los administradores pueden usar `EdgeHomepageUrls` para escribir las páginas de inicio que los usuarios ven de manera predeterminada al abrir Microsoft Edge. **No configurado** impide que los usuarios cambien las páginas de inicio.
- **New Tab page URL** (Dirección URL de la página Pestaña nueva): escriba la dirección URL para abrir la página Pestaña nueva. Por ejemplo, escriba `https://www.bing.com`.
- **Open web content on New Tab page** (Abrir contenido web en la página Pestaña nueva): elija **Bloquear** para evitar que Microsoft Edge abra un sitio web en una pestaña nueva. Cuando se bloquea, se abre una pestaña nueva en blanco. **No configurado** usa el comportamiento predeterminado del SO del dispositivo, el que puede permitir que los usuarios elijan lo que se muestra.
- **Botón Inicio**: elija lo que sucede al seleccionar el botón Inicio. Las opciones son:
  - **Start pages** (Páginas de inicio): se abre la opción que eligió en la configuración **Iniciar Microsoft Edge con**
  - **New Tab page** (Página Pestaña nueva): se abre la opción que eligió en la configuración **New Tab page URL** (Dirección URL de la página Pestaña nueva)
  - **Custom Home button URL** (Dirección URL del botón Inicio personalizado): se abre la opción que eligió en la configuración **Home button URL** (Dirección URL del botón Inicio)
  - **Hide Home button** (Ocultar el botón Inicio): oculta el botón Inicio
- **User can change Home button** (El usuario puede cambiar el botón Inicio): **Permitir** deja que los usuarios cambien el botón Inicio. Los cambios del usuario reemplazan cualquier configuración del administrador en el botón Inicio. **No configurado** usa el comportamiento predeterminado del SO del dispositivo, que puede impedir que los usuarios cambien la forma en que el administrador configuró el botón Inicio.
- **Show First Run Experience page** (Página Mostrar la primera experiencia de ejecución): **Bloquear** impide que la página de introducción muestre la primera vez que ejecutó Microsoft Edge. Esta característica permite que las empresas (por ejemplo, aquellas organizaciones que utilizan configuraciones de cero emisiones) bloqueen esta página. **No configurado** muestra la página de introducción.
  - **First Run Experience URL** (Dirección URL de la primera experiencia de ejecución): escriba la dirección URL de la página para mostrar la primera vez que un usuario ejecuta Microsoft Edge (solo Windows 10 Mobile).
- **Actualice el explorador después de tiempo de inactividad**: escriba el número de minutos de inactividad hasta que se actualiza el explorador, de 0 a 1440 minutos. El valor predeterminado es `5` minutos. Cuando se establece en `0` (cero), el explorador no se actualiza tras estar inactivo.

  Esta opción solo está disponible cuando se ejecuta en [exploración InPrivate pública (aplicación sencilla quiosco)](#use-microsoft-edge-kiosk-mode).

  CSP: [ConfigureKioskResetAfterIdleTimeout](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configurekioskresetafteridletimeout)

- **Elementos emergentes**: elija **Bloquear** para detener las ventanas emergentes en el explorador. Solo se aplica a Windows 10 Escritorio. **No configurado** permite los elementos emergentes en el explorador web.
- **Enviar el tráfico de la intranet a Internet Explorer**: **Permitir** deja que los usuarios abran sitios web de intranet en Internet Explorer en lugar de Microsoft Edge (solo Windows 10 Escritorio). **No configurado** permite que los usuarios utilicen Microsoft Edge.
- **Ubicación de la lista de sitios del Modo de empresa**: escriba la dirección URL que incluye una lista de los sitios web que se abren en el Modo de empresa. Los usuarios no pueden cambiar esta lista. Solo se aplica a Windows 10 Escritorio.
- **Message when opening sites in Internet Explorer** (Mensaje al abrir sitios en Internet Explorer): use este valor para configurar Microsoft Edge para que muestre una notificación antes de que un sitio se abra en Internet Explorer 11. Las opciones son:
  - **No configurado**: se usa el comportamiento predeterminado del sistema operativo, que no puede mostrar un mensaje.
  - **Show message without option to open sites in Microsoft Edge** (Mostrar mensaje si no hay opción de abrir sitios en Microsoft Edge): muestre el mensaje al abrir sitios en IE. Los sitios se abren en IE. No hay ninguna opción para abrir sitios en Microsoft Edge.
  - **Show message when opening sites in Microsoft Edge** (Mostrar mensaje al abrir sitios en Microsoft Edge): muestre el mensaje al abrir sitios en IE. El mensaje incluye un vínculo **Keep going in Microsoft Edge** (Seguir en Microsoft Edge) para que los usuarios puedan elegir Microsoft Edge en lugar de IE.

  > [!IMPORTANT]
  > Esta configuración requiere habilitar la configuración **Configure the Enterprise Mode Site List** (Configurar la lista de sitios del Modo de empresa), **Send all intranet sites to Internet Explorer 11** (Enviar todos los sitios de intranet a Internet Explorer 11) o ambas.

- **Microsoft compatibility list** (Lista de compatibilidad de Microsoft): **Bloquear** impide la lista de compatibilidad de Microsoft en Microsoft Edge. La lista de Microsoft ayuda a que Microsoft Edge muestre de manera correcta sitios con problemas de compatibilidad conocidos. **No configurado** permite usar una lista de compatibilidad de Microsoft.
- **Preload Start pages and New Tab page** (Precargar páginas de inicio y página Pestaña nueva): elija **Bloquear** para impedir que Microsoft Edge precargue las páginas de inicio y la página Pestaña nueva. La precarga minimiza el tiempo de inicio de Microsoft Edge y carga una pestaña nueva. **No configurado** usa el comportamiento predeterminado del sistema operativo, que puede ser precargar estas páginas.
- **Prelaunch Start pages and New Tab page** (Iniciar previamente las páginas de inicio y la página Pestaña nueva): elija **Bloquear** para impedir que Microsoft Edge inicie previamente las páginas de inicio y la página Pestaña nueva. El inicio previo ayuda al rendimiento de Microsoft Edge y minimiza el tiempo necesario para iniciar Microsoft Edge. **No configurado** usa el comportamiento predeterminado del sistema operativo, que puede ser iniciar previamente estas páginas.

### <a name="favorites-and-search"></a>Favoritos y búsqueda

- **Barra de favoritos**: elija qué le pasa a la barra de favoritos en cualquier página de Microsoft Edge. Las opciones son:
  - **No configurado**: usa el comportamiento predeterminado del sistema operativo, que puede ser ocultar la barra de favoritos en todas las páginas. El usuario puede cambiar esta configuración.
  - **Ocultar**: oculta la barra de favoritos en todas las páginas. El usuario no puede cambiar esta configuración.
  - **Mostrar**: muestra la barra de favoritos en todas las páginas. El usuario no puede cambiar esta configuración.
- **Lista de favoritos**: agrega una lista de las direcciones URL al archivo de favoritos. Por ejemplo, agregue `http://contoso.com/favorites.html`.
- **Restringir los cambios a Favoritos**: **Bloquear** impide que los usuarios agreguen, importen, ordenen o modifiquen la lista de favoritos. **No configurado** usa el valor predeterminado del sistema operativo, que puede permitir que los usuarios cambien la lista.
- **Sincronizar favoritos entre exploradores de Microsoft (solo equipos de escritorio)**: **Requerir** obliga a que Windows sincronice los favoritos entre Internet Explorer y Microsoft Edge. Las incorporaciones, eliminaciones, modificaciones y cambios de orden en los favoritos se comparten entre los distintos exploradores.  **No configurado** usa el valor predeterminado del sistema operativo, que puede dar a los usuarios la opción de sincronizar los favoritos entre los exploradores.
- **Motor de búsqueda predeterminado**: elija el motor de búsqueda predeterminado del dispositivo. Los usuarios finales pueden cambiar este valor en cualquier momento. Las opciones son:
  - Default
  - Bing
  - Google
  - Yahoo
  - Valor personalizado
- **Sugerencias de búsqueda**: **No configurado** permite que el motor de búsqueda sugiera sitios a medida que escribe las frases de búsqueda en la barra de direcciones. **Bloquear** impide esta característica.
- **Permitir cambios en el motor de búsqueda**: **Sí** (valor predeterminado) permite a los usuarios agregar nuevos motores de búsqueda o cambiar el motor de búsqueda predeterminado en Microsoft Edge. Elija **No** para impedir que los usuarios personalizar el motor de búsqueda.

  Esta opción solo está disponible cuando se ejecuta en [modo Normal (quiosco con varias aplicaciones)](#use-microsoft-edge-kiosk-mode).

  CSP: [AllowSearchEngineCustomization](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsearchenginecustomization)

### <a name="privacy-and-security"></a>Privacidad y seguridad

- **Exploración de InPrivate**: **Bloquear** impide que los usuarios finales abran sesiones de exploración de InPrivate. **No configurado** permite esta característica.
- **Guardar historial de exploración**: **Bloquear** impide que Microsoft Edge guarde el historial de exploración. **No configurado** permite guardar el historial de exploración.
- **Borrar datos de navegación al salir (solo equipos de escritorio)**: **Requerir** borra el historial y los datos de exploración cuando el usuario sale de Microsoft Edge. **No configurado** usa el valor predeterminado del sistema operativo, que puede almacenar en caché los datos de exploración.
- **Sync browser settings between user's devices** (Sincronizar la configuración del explorador entre los dispositivos del usuario): elija cómo quiere sincronizar la configuración del explorador entre los dispositivos. Las opciones son:
  - **Permitir**: permita la sincronización de la configuración del explorador Microsoft Edge entre los dispositivos del usuario
  - **Block and enable user override** (Bloquear y habilitar el reemplazo de usuario): bloquee la sincronización de la configuración del explorador de Microsoft Edge entre los dispositivos del usuario. Los usuarios pueden reemplazar esta configuración.
  - **Bloquear**: bloquee la sincronización de la configuración del explorador Microsoft Edge entre los dispositivos del usuario. Los usuarios no pueden reemplazar esta configuración.
- **Administrador de contraseñas**: **Bloquear** deshabilita la característica Administrador de contraseñas de Microsoft Edge. **No configurado** permite esta característica Administrador de contraseñas de Microsoft Edge.
- **Cookies**: elija cómo se administran las cookies en el dispositivo. Las opciones son:
  - **Permitir**: las cookies se almacenan en el dispositivo.
  - **Bloquear todas las cookies**: las cookies no se almacenan en el dispositivo.
  - **Bloquear solo cookies de terceros**: las cookies de terceros o de asociados no se almacenan en el dispositivo.
- **Autorrellenar**: **Bloquear** deshabilita la característica Autorrellenar del dispositivo. **No configurado** permite que los usuarios cambien la configuración de Autorrellenar en el explorador (solo Windows 10 Escritorio).
- **Enviar encabezados de no seguimiento**: **No configurado** requiere que los dispositivos envíen encabezados de no seguimiento a los sitios web que solicitan información de seguimiento (recomendado). Elija **Bloquear** para impedir que el dispositivo envíe estos encabezados, lo que permitirá que los sitios web hagan seguimiento del usuario.
- **Dirección IP de localhost para WebRTC**: **Bloquear** impide que la dirección IP de localhost de los usuarios se muestre cuando se hacen llamadas telefónicas a través del protocolo WebRTC. **No configurado** permite que la dirección IP de localhost de los usuarios se muestre cuando se hacen llamadas telefónicas a través de este protocolo.
- **Recopilación de datos para iconos dinámicos**: elija **Bloquear** para impedir que Windows recopile información de iconos dinámicos cuando se ancla un sitio al menú de inicio desde Microsoft Edge. **No configurado** permite recopilar esta información.
- **User can override certificate errors** (El usuario puede invalidar los errores de certificado): **Bloquear** evita que los usuarios accedan a sitios web con errores de SSL o TLS. **No configurado** permite que los usuarios accedan a estos sitios.

### <a name="additional"></a>Adicional

- **Explorador Microsoft Edge (solo dispositivos móviles)**: elija **Bloquear** para impedir el uso de Microsoft Edge en el dispositivo. Si bloquea Microsoft Edge, la configuración individual solo se aplica a los equipos de escritorio. **No configurado** permite usar el explorador web Microsoft Edge en el dispositivo.
- **Lista desplegable de la barra de direcciones (solo equipos de escritorio)**: **Bloquear** impide que Microsoft Edge muestre una lista de sugerencias en una lista desplegable cuando escriba. Esta opción ayuda a minimizar el ancho de banda de red entre Microsoft Edge y los servicios de Microsoft. **No configurado** permite que Microsoft Edge muestre una lista de sugerencias.
- **Pantalla completa**: elija **Bloquear** para evitar que Microsoft Edge solo muestre el contenido web, ocultando la interfaz de Microsoft Edge (modo de pantalla completa). **No configurado** usa el valor predeterminado del sistema operativo, que permite que Microsoft Edge use el modo de pantalla completa.
- **about:flags**: **Bloquear** impide que los usuarios finales accedan a la página `about:flags` en Microsoft Edge que incluye la configuración experimental y del desarrollador. **No configurado** usa el valor predeterminado del sistema operativo, que puede permitir el acceso a la página `about:flags`.
- **Herramientas de desarrollo**: **Bloquear** impide que los usuarios finales abran las herramientas de desarrollo de Microsoft Edge. **No configurado** permite que los usuarios abran las herramientas de desarrollo.
- **Extensiones**: **No configurado** permite que los usuarios finales instalen extensiones de Microsoft Edge en el dispositivo. **Bloquear** impide la instalación.
- **Sideloading developer extensions** (Instalación de prueba de extensiones de desarrollador): **Bloquear** impide que Microsoft Edge haga instalaciones de prueba, lo que instala y ejecuta versiones no comprobadas con la característica **Cargar extensiones**. **No configurado** usa el valor predeterminado del sistema operativo, que puede permitir la instalación de prueba.
- **Required extensions** (Extensiones necesarias): elija cuáles son las extensiones que los usuarios finales de Microsoft Edge no pueden desactivar. Escriba los nombres de familia de paquete y seleccione **Agregar**. [Buscar un nombre de familia de paquete (PFN)](https://docs.microsoft.com/sccm/protect/deploy-use/find-a-pfn-for-per-app-vpn) brinda algunas guías.

  También puede **Importar** un archivo .csv que incluya los nombres de familia de paquete.

- **JavaScript**: elija **Bloquear** para impedir que los scripts de Java del explorador se ejecuten en el dispositivo. **No configurado** permite la ejecución de scripts, como JavaScript, en el explorador Microsoft Edge.

## <a name="network-proxy"></a>Proxy de red

- **Detectar automáticamente configuración de proxy**: cuando esta opción está habilitada, el dispositivo intenta encontrar la ruta de acceso a un script de configuración automática del proxy.
- **Usar script de proxy**: seleccione esta opción para especificar una ruta de acceso a un script de configuración automática para configurar el servidor proxy.
  - **URL del script de configuración**: escriba la dirección URL de un script de configuración automática que desee usar para configurar el servidor proxy.
- **Usar servidor proxy manual**: seleccione esta opción si desea especificar manualmente información del servidor proxy.
  - **Dirección**: escriba el nombre o la dirección IP del servidor proxy.
  - **Número de puerto**: escriba el número de puerto del servidor proxy.
  - **Excepciones de proxy**: escriba las direcciones URL que no deben usar el servidor proxy. Use un punto y coma para separar cada elemento.
  - **Omitir el servidor proxy para direcciones locales**: si no quiere usar el servidor proxy para direcciones locales de la intranet, habilite esta opción.

## <a name="password"></a>Contraseña

- **Contraseña**: exige que el usuario final escriba una contraseña para acceder al dispositivo.
  - **Tipo de contraseña necesaria**: especifica si la contraseña debe ser solo numérica o alfanumérica.
  - **Minimum password length** (Longitud mínima de contraseña): solo se aplica a Windows 10 Mobile.
  - **Número de errores de inicio de sesión antes de borrar el dispositivo**: para dispositivos que ejecutan Windows 10: si el dispositivo tiene habilitado BitLocker, se pondrá en el modo de recuperación de BitLocker si el inicio de sesión produce error el número de veces especificado. Si el dispositivo no tiene habilitado BitLocker, no se aplica esta configuración. Para los dispositivos que ejecutan Windows 10 Mobile: si el inicio de sesión falla el número de veces especificado, el dispositivo se borrará.
  - **Máximo de minutos de inactividad hasta que se bloquea la pantalla**: especifique la longitud de tiempo que un dispositivo debe estar inactivo antes de que se bloquee la pantalla.
  - **Caducidad de la contraseña (días)**: especifica el período de tiempo transcurrido el cual debe cambiarse la contraseña del dispositivo.
  - **Impedir la reutilización de contraseñas anteriores**: especifica el número de contraseñas usadas anteriormente que se recuerdan el dispositivo.
  - **Requerir contraseña cuando el dispositivo vuelve de un estado de inactividad (solo dispositivos móviles)**: especifica que el usuario debe escribir una contraseña para desbloquear el dispositivo (solo Windows 10 Mobile).
  - **Contraseñas sencillas**: le permite el uso de contraseñas sencillas, como 1111 y 1234. Esta configuración también permite o bloquea el uso de contraseñas de imagen de Windows.
- **Cifrado automático durante AADJ**: **bloque** impide el cifrado automático de dispositivos de BitLocker cuando el dispositivo está preparado para el primer uso, cuando el dispositivo está unido a Azure AD. **No configurado** (valor predeterminado) usa el valor predeterminado del sistema operativo, que puede habilitar el cifrado. Más información sobre [el cifrado de BitLocker dispositivo](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-device-encryption-overview-windows-10#bitlocker-device-encryption).

  [Seguridad/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-security#security-preventautomaticdeviceencryptionforazureadjoineddevices)

- **Directiva de información de procesamiento estándar federal (FIPS)**: **permitir** usa la directiva de información de procesamiento estándar Federal (FIPS), que es un gobierno de Estados Unidos estándar para el cifrado, firma y operaciones hash. **No configurado** (valor predeterminado) usa el valor predeterminado del sistema operativo, que no usa FIPS.

  [Criptografía/AllowFipsAlgorithmPolicy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-cryptography#cryptography-allowfipsalgorithmpolicy)

- **Autenticación de Windows Hello dispositivos**: **permitir** a los usuarios usen un Windows Hello dispositivo complementario, como un teléfono, banda de fitness o dispositivo de IoT, para iniciar sesión en un equipo Windows 10. **No configurado** (valor predeterminado) usa el valor predeterminado del sistema operativo, que puede impedir que los dispositivos de Windows Hello complementarios desde la autenticación de Windows.

  [Autenticación/AllowSecondaryAuthenticationDevice CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowsecondaryauthenticationdevice)

- **Inicio de sesión Web**: inicio de sesión de Windows permite compatibilidad con proveedores de federada no ADFS (servicios de federación de Active Directory), como el lenguaje de marcado de aserción de seguridad (SAML). SAML usa tokens seguros que proporcionan la experimentan de los exploradores web un single sign-on (SSO). Las opciones son:

  - **No configurado** (valor predeterminado): usa el valor predeterminado de sistema operativo en el dispositivo.
  - **Habilitado**: proveedor de credenciales de la Web está habilitado para inicio de sesión.
  - **Deshabilitado**: proveedor de credenciales de la Web está deshabilitado para el inicio de sesión.

  [Autenticación/EnableWebSignIn CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-enablewebsignin)

- **Preferido de dominio del inquilino de Azure AD**: escriba un nombre de dominio de su organización de Azure AD. Cuando los usuarios de este dominio iniciar sesión, no tienen que escriba el nombre de dominio. Por ejemplo, escriba `contoso.com`. Los usuarios de la `contoso.com` dominio puede iniciar sesión con su nombre de usuario, como "abby", en lugar de "abby@contoso.com".

  [Authentication/PreferredAadTenantDomainName CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-preferredaadtenantdomainname)

## <a name="per-app-privacy-exceptions"></a>Excepciones de privacidad para cada aplicación

Puede agregar aplicaciones que deben tener un comportamiento de privacidad diferente del definido en "Privacidad determinada".

- **Nombre del paquete**: nombre de la familia del paquete de aplicaciones.
- **Nombre de la aplicación**: el nombre de la aplicación.

### <a name="exceptions"></a>Excepciones

- **Información de la cuenta**: define si esta aplicación puede tener acceso al nombre de usuario, las imágenes u otra información de contacto.
- **Aplicaciones en segundo plano**: define si esta aplicación puede ejecutarse en segundo plano.
- **Calendario**: define si esta aplicación puede tener acceso al calendario.
- **Historial de llamadas**: define si esta aplicación puede tener acceso al historial de llamadas.
- **Cámara**: define si esta aplicación puede tener acceso a la cámara.
- **Contactos**: define si esta aplicación puede tener acceso a los contactos.
- **Correo electrónico**: define si esta aplicación puede tener acceso al correo electrónico.
- **Ubicación**: define si esta aplicación puede tener acceso a información de ubicación.
- **Mensajería**: define si esta aplicación puede leer o enviar mensajes de texto o MMS.
- **Micrófono**: define si esta aplicación puede usar el micrófono.
- **Movimiento**: define si esta aplicación puede tener acceso a información de movimiento.
- **Notificaciones**: define si esta aplicación puede tener acceso a las notificaciones.
- **Teléfono**: define si esta aplicación puede tener acceso al teléfono.
- **Radios**: algunas aplicaciones usan radios (por ejemplo, Bluetooth) en el dispositivo para enviar y recibir datos y necesitan activar o desactivar estas radios. Define si esta aplicación puede controlar estas radios.
- **Tareas**: define si esta aplicación puede tener acceso a las tareas.
- **Dispositivos de confianza**: elija si esta aplicación puede usar dispositivos de confianza. Es decir, hardware ya conectado o que se proporciona con el dispositivo. Por ejemplo, use televisores, proyectores, etc. como dispositivos de confianza.
- **Comentarios y diagnóstico**: define si esta aplicación puede tener acceso a la información de diagnóstico.
- **Sincronización con dispositivos**: defina si esta aplicación puede compartir y sincronizar automáticamente información con dispositivos inalámbricos que no se emparejan explícitamente con el dispositivo.

## <a name="personalization"></a>Personalization

- **Dirección URL de imagen de fondo de escritorio (solo escritorio)**: indique la dirección URL de una imagen en formato JPEG que quiere usar como fondo de escritorio de Windows. Los usuarios no pueden cambiar la imagen.

## <a name="printer"></a>Impresora

- **Impresoras**: lista de impresoras locales que se han agregado.
- **Impresora predeterminada**: establezca la impresora predeterminada.
- **Acceso de usuario para agregar nuevas impresoras**: permita o bloquee el uso de las impresoras locales.

## <a name="privacy"></a>Privacidad

- **Personalización de entrada**: no permite el uso de servicios de voz basados en la nube para Cortana, Dictado o aplicaciones de Microsoft Store. Si permite estos servicios, Microsoft puede recopilar datos de voz para mejorar el servicio.
- **Aceptación automática de los mensajes de consentimiento del usuario sobre emparejamiento y privacidad**: permite que Windows acepte automáticamente los mensajes de consentimiento sobre emparejamiento y privacidad al ejecutar las aplicaciones.
- **Publicar las actividades del usuario**: **Bloquear** evita las experiencias compartidas y la detección de recursos usados recientemente en el selector de tareas.
- **Solo actividades locales**: **Bloquear** evita experiencias compartidas y la detección de recursos usados recientemente en el selector de tareas según la actividad local únicamente.

Puede configurar la información a la que pueden tener acceso todas las aplicaciones del dispositivo. También, puede definir excepciones para cada aplicación mediante **excepciones de privacidad de cada aplicación**.

### <a name="exceptions"></a>Excepciones

- **Información de la cuenta**: define si esta aplicación puede tener acceso al nombre de usuario, las imágenes u otra información de contacto.
- **Aplicaciones en segundo plano**: define si esta aplicación puede ejecutarse en segundo plano.
- **Calendario**: define si esta aplicación puede tener acceso al calendario.
- **Historial de llamadas**: define si esta aplicación puede tener acceso al historial de llamadas.
- **Cámara**: define si esta aplicación puede tener acceso a la cámara.
- **Contactos**: define si esta aplicación puede tener acceso a los contactos.
- **Correo electrónico**: define si esta aplicación puede tener acceso al correo electrónico.
- **Ubicación**: define si esta aplicación puede tener acceso a información de ubicación.
- **Mensajería**: define si esta aplicación puede leer o enviar mensajes de texto o MMS.
- **Micrófono**: define si esta aplicación puede usar el micrófono.
- **Movimiento**: define si esta aplicación puede tener acceso a información de movimiento.
- **Notificaciones**: define si esta aplicación puede tener acceso a las notificaciones.
- **Teléfono**: define si esta aplicación puede tener acceso al teléfono.
- **Radios**: algunas aplicaciones usan radios (por ejemplo, Bluetooth) en el dispositivo para enviar y recibir datos y necesitan activar o desactivar estas radios. Define si esta aplicación puede controlar estas radios.
- **Tareas**: define si esta aplicación puede tener acceso a las tareas.
- **Dispositivos de confianza**: elija si esta aplicación puede usar dispositivos de confianza. Es decir, hardware ya conectado o que se proporciona con el dispositivo. Por ejemplo, use televisores, proyectores, etc. como dispositivos de confianza.
- **Comentarios y diagnóstico**: elija si esta aplicación puede tener acceso a la información de diagnóstico.
- **Sincronización con dispositivos**: define si esta aplicación puede compartir y sincronizar información automáticamente con dispositivos inalámbricos que no se emparejan explícitamente con este PC, tableta o teléfono.

## <a name="projection"></a>Proyección

- **Entrada de usuario desde receptores de pantalla inalámbricos**: bloquea la entrada de usuario desde receptores de pantalla inalámbricos.
- **Proyección en este equipo**: impide que otros dispositivos encuentren el equipo para proyección.
- **Requerir PIN para emparejamiento**: se requiere un PIN cuando se conecta a un dispositivo de proyección.

## <a name="reporting-and-telemetry"></a>Informes y telemetría

- **Compartir datos de uso**: elija el nivel de datos de diagnóstico que se envía. Las opciones son:
  - Seguridad
  - Básica
  - Mejorado
  - Full
- **Send Microsoft Edge browsing data to Microsoft 365 Analytics** (Enviar datos de exploración de Microsoft Edge a Microsoft 365 Analytics): para usar esta característica, establezca la configuración **Compartir datos de uso** en **Mejorado** o **Completo**. Esta característica controla los datos que Microsoft Edge envía a Microsoft 365 Analytics para los dispositivos empresariales que tienen configurado un identificador comercial. Las opciones son:
  - **No configurado**: usa el valor predeterminado del sistema operativo, que no puede enviar ningún dato de navegación histórico.
  - **Only send intranet data** (Enviar solo datos de la intranet): permite que el administrador envíe el historial de datos de la intranet.
  - **Only send internet data** (Enviar solo datos de Internet): permite que el administrador envíe el historial de datos de Internet.
  - **Send intranet and internet data** (Enviar datos de la intranet y de Internet): permite que el administrador envíe el historial de datos de la intranet y de Internet.
- **Servidor proxy de telemetría**: especifique el nombre de dominio completo (FQDN) o la dirección IP de un servidor proxy para las solicitudes de Telemetría y experiencias del usuario conectado mediante una conexión de Capa de sockets seguros. El formato de esta configuración es *servidor*:*puerto*. Si se produce un error en el proxy mencionado o si no hay ningún proxy especificado cuando esta directiva está habilitada, los datos de Telemetría y experiencias del usuario conectado no se envían y permanecen en el dispositivo local.

  Formatos de ejemplo:

  ```
  IPv4: 192.246.246.106:100
  IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100
  FQDN: www.contoso.com:345
  ```

## <a name="search"></a>Buscar

- **Búsqueda segura (solo dispositivos móviles)**: controla cómo Cortana filtra contenido para adultos en los resultados de la búsqueda. Puede seleccionar **Strict** (Estricto), **Moderate** (Moderado) o permitir que el usuario final elija su propia configuración.
- **Mostrar resultados web en la búsqueda**: permita o no que aparezcan resultados web en las búsquedas realizadas en el dispositivo.

## <a name="start"></a>Start

- **Diseño del menú Inicio**: para personalizar el menú Inicio en los dispositivos de escritorio, puede cargar un archivo XML que incluya sus personalizaciones, así como el orden en que aparecen las aplicaciones, entre otras cosas. Los usuarios no pueden cambiar el diseño del menú Inicio que especifique usted.
- **Anclar los sitios web a iconos del menú Inicio**: puede importar imágenes desde Microsoft Edge que se muestran como vínculos en el menú Inicio de Windows de los dispositivos de escritorio.
- **Desanclar aplicaciones de la barra de tareas**: seleccione **Bloquear** para impedir que el usuario desancle aplicaciones de la barra de tareas.
- **Cambio rápido de usuario**: seleccione **Bloquear** para impedir el cambio de usuarios que han iniciado sesión al mismo tiempo sin cerrar la sesión.
- **Aplicaciones más usadas**: seleccione **Bloquear** para que las aplicaciones más usadas no se muestren en el menú Inicio. También deshabilita la alternancia correspondiente en la aplicación Configuración.
- **Aplicaciones agregadas recientemente**: seleccione **Bloquear** para que las aplicaciones agregadas recientemente no se muestren en el menú Inicio. También deshabilita la alternancia correspondiente en la aplicación Configuración.
- **Modo de pantalla de inicio**: elija cómo quiere que se muestre la pantalla de inicio. Puede elegir **Pantalla completa** o **Pantalla parcial**.
- **Elementos abiertos recientemente en listas de accesos directos**: seleccione **Bloquear** para que las listas de accesos directos recientes no se muestren en el menú Inicio ni en la barra de tareas. También deshabilita la alternancia correspondiente en la aplicación Configuración.
- **Lista de aplicaciones**: elija cómo quiere que se muestre la aplicación Configuración. Las opciones son: 
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
- **Opciones de reinicio**: seleccione **Bloquear** para que las opciones `Update and restart` y `Restart` no se muestren en el botón de encendido del menú Inicio.
- **Documentos en Inicio**: oculta o muestra la carpeta Documentos en el menú Inicio de Windows.
- **Descargas en Inicio**: oculta o muestra la carpeta Descargas en el menú Inicio de Windows.
- **Explorador de archivos en Inicio**: oculta o muestra la aplicación Explorador de archivos en el menú Inicio de Windows.
- **Grupo Hogar en Inicio**: oculta o muestra la carpeta Grupo Hogar en el menú Inicio de Windows.
- **Música en Inicio**: oculta o muestra la carpeta Música en el menú Inicio de Windows.
- **Red en Inicio**: oculta o muestra la carpeta Red en el menú Inicio de Windows.
- **Carpeta Personal en Inicio**: oculta o muestra la carpeta Personal en el menú Inicio de Windows.
- **Imágenes en Inicio**: oculta o muestra la carpeta de imágenes en el menú Inicio de Windows.
- **Configuración en Inicio**: oculta o muestra la aplicación Configuración en el menú Inicio de Windows.
- **Vídeos en Inicio**: oculta o muestra la carpeta de vídeos en el menú Inicio de Windows.

## <a name="windows-defender-smart-screen"></a>SmartScreen de Windows Defender

- **SmartScreen para Microsoft Edge**: permite a SmartScreen de Microsoft Edge el acceso al sitio y las descargas de archivos.
- **Acceso a sitio malintencionado**: impide que los usuarios omitan las advertencias del filtro SmartScreen de Windows Defender y no permite que vayan al sitio.
- **Descarga de archivos no comprobados**: impide que los usuarios omitan las advertencias del filtro SmartScreen de Windows Defender y no permite que descarguen los archivos no comprobados.

## <a name="windows-spotlight"></a>Contenido destacado de Windows

- **Contenido destacado de Windows**: use esta opción para bloquear todas las funciones de Contenido destacado de Windows en los dispositivos de Windows 10. Si bloquea esta configuración, las siguientes opciones no estarán disponibles:
  - **Contenido destacado de Windows en la pantalla de bloqueo**: impide que Contenido destacado de Windows muestre información en la pantalla de bloqueo del dispositivo.
  - **Sugerencias de terceros en Contenido destacado de Windows**: impide que Contenido destacado de Windows sugiera contenido que no ha sido publicado por Microsoft.
  - **Características de consumidor**: permite bloquear las características de consumidor, como sugerencias del menú Inicio y notificaciones de pertenencia.
  - **Sugerencias de Windows**: permite impedir que las sugerencias emergentes se muestren en Windows.
  - **Contenido destacado de Windows en el centro de actividades**: impide que las sugerencias de Contenido destacado de Windows como una nueva aplicación o contenido de seguridad aparezcan en el centro de actividades de Windows.
  - **Personalización de Contenido destacado de Windows**: impide que Contenido destacado de Windows personalice los resultados basándose en el uso de un dispositivo.
  - **Experiencia de bienvenida de Windows**: bloquea la experiencia de bienvenida de Windows que muestra la información de usuario sobre características nuevas o actualizadas.

## <a name="windows-defender-antivirus"></a>Antivirus de Windows Defender

- **Supervisión en tiempo real**: habilita el análisis en tiempo real de malware, spyware y otro software no deseado.
- **Supervisión de comportamiento**: permite a Defender comprobar determinados patrones conocidos de actividad sospechosa en los dispositivos.
- **Sistema de inspección de red (NIS)**: NIS ayuda a proteger los dispositivos contra las vulnerabilidades de seguridad basadas en red. Usa las firmas de vulnerabilidades conocidas de Microsoft Endpoint Protection Center para ayudar a detectar y bloquear el tráfico malintencionado.
- **Analizar todas las descargas**: controla si Defender examina todos los archivos descargados de Internet.
- **Examinar scripts cargados en exploradores web de Microsoft**: permite a Defender examinar scripts que se usan en Internet Explorer.
- **Acceso de usuario final a Defender**: controla si la interfaz de usuario de Windows Defender se oculta a los usuarios finales. Cuando se cambia esta configuración, surtirá efecto la próxima vez que se reinicie el equipo del usuario final.
- **Intervalo de actualización de firma (en horas)**: especifica el intervalo dentro del cual Defender comprobará nuevos archivos de firmas.
- **Supervisar la actividad de archivos y programas**: permite que Defender supervise la actividad de archivos y programas en los dispositivos.
- **Días antes de eliminar malware en cuarentena**: continuar realizando el seguimiento de malware resuelto durante el número de días especificado para que pueda comprobar manualmente los dispositivos previamente afectados. Si establece el número de días en **0**, el malware permanece en la carpeta de cuarentena y no se quita automáticamente.
- **Límite de uso de la CPU durante un examen**: limita la cantidad de CPU que pueden usar los exámenes (de **1** a **100**).
- **Examinar archivos de almacenamiento**: permite que Defender examine archivos almacenados, como archivos .zip o .cab.
- **Examinar mensajes de correo entrante**: permite que Defender examine mensajes de correo electrónico cuando llegan al dispositivo.
- **Examinar unidades extraíbles durante un examen completo**: permite que Defender examine unidades extraíbles, como llaves USB.
- **Examinar unidades de red asignadas durante un examen completo**: permite que Defender examine archivos en unidades de red asignadas.
  Si los archivos de la unidad son de solo lectura, Defender no puede quitar el malware que se encuentre en ellos.
- **Examinar archivos abiertos desde carpetas de red**: permite que Defender examine archivos en unidades de red compartidas (por ejemplo, los archivos a los que se tiene acceso desde una ruta de acceso UNC). Si los archivos de la unidad son de solo lectura, Defender no puede quitar el malware que se encuentre en ellos.
- **Protección de la nube**: permite o bloquea la recepción por parte de Microsoft Active Protection Service de información relativa a la actividad de malware de los dispositivos que administra. Esta información mejora el servicio en el futuro.
- **Preguntar a los usuarios antes de enviar muestras**: controla si los archivos potencialmente malintencionados que podrían requerir un análisis posterior se envían automáticamente a Microsoft.
- **Tiempo para realizar un examen rápido diario**: elija la hora para ejecutar un examen rápido diario. **No configurado** no se ejecuta un examen diario. Si desea personalizar aún más, configure el **tipo de examen del sistema para realizar** configuración.

  [Defender/ScheduleQuickScanTime CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime)
- **Tipo de examen del sistema para realizar**: programar un examen del sistema, incluido el nivel de exploración y el día y hora para ejecutar el examen. Las opciones son:
  - **No configurado**: no se programe un examen del sistema en el dispositivo. Los usuarios finales puede ejecutar manualmente exámenes según sea necesario o deseado en sus dispositivos.
  - **Deshabilitar**: deshabilita cualquier sistema de análisis en el dispositivo. Elija esta opción si usa una solución de partner antivirus que examina los dispositivos.
  - **Examen rápido**: examina ubicaciones comunes que podría haber malware registrado, como las claves del registro y conoce las carpetas de inicio de Windows.
    - **Día programado**: elija el día para ejecutar el examen.
    - **Hora programada**: elija la hora para ejecutar el examen.
  - **Examen completo**: examina ubicaciones comunes que podría haber malware registrado y también examina todos los archivos y carpetas en el dispositivo.
    - **Día programado**: elija el día para ejecutar el examen.
    - **Hora programada**: elija la hora para ejecutar el examen.

  Esta configuración podría entrar en conflicto con el **tiempo para realizar un examen rápido diario** configuración. Algunas recomendaciones:

  - Para ejecutar un examen rápido diario, configure el **tiempo para realizar un examen rápido diario** configuración.
  - Para ejecutar un examen rápido diario y un examen completo de cada semana, a continuación, configure el **tiempo para realizar un examen rápido diario**y establezca **tipo de examen del sistema para realizar** para un examen completo con el día y hora.
  - No configure el **tiempo para realizar un examen rápido diario** establecer simultáneamente con el **tipo de examen del sistema para realizar** establecido en **examen rápido**. Esta configuración podría entrar en conflicto y no se puede ejecutar un examen.
  - Para ejecutar un examen rápido todos los martes a las 6 A.M., configurar el **tipo de examen del sistema para realizar** configuración.

  [Defender/ScanParameter CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter)  
  [Defender/ScheduleScanDay CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday)  
  [Defender/ScheduleScanTime CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime)

- **Detectar aplicaciones potencialmente no deseadas**: elija el nivel de protección cuando Windows detecte aplicaciones potencialmente no deseadas entre:
  - **Bloquear**
  - **Auditoría** Para más información sobre aplicaciones potencialmente no deseadas, consulte [Detectar y bloquear aplicaciones potencialmente no deseadas](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus).
- **Acciones para amenazas de malware detectadas**: elija las acciones que quiere que Defender realice para cada nivel de amenaza que detecte: bajo, moderado, alto y grave. Las opciones son:
  - **Limpiar**
  - **Cuarentena**
  - **Quitar**
  - **Permitir**
  - **Definido por el usuario**
  - **Bloquear**

### <a name="windows-defender-antivirus-exclusions"></a>Exclusiones del antivirus de Windows Defender

- **Archivos y carpetas para excluir de exámenes y protección en tiempo real**: agrega uno o varios archivos y carpetas, como **C:\Path** o **%ProgramFiles%\Path\filename.exe** a la lista de exclusiones. Estos archivos y carpetas no se incluyen en los exámenes en tiempo real ni programados.
- **Extensiones de archivo para excluir de exámenes y protección en tiempo real**: agrega una o varias extensiones de archivo, como **jpg** o **txt** a la lista de exclusiones. Los archivos con estas extensiones no se incluyen en los exámenes en tiempo real ni programados.
- **Procesos para excluir de exámenes y protección en tiempo real**: agregar uno o varios procesos del tipo **.exe**, **.com** o **.scr** a la lista de exclusiones. Estos procesos no se incluyen en los exámenes en tiempo real ni programados.

## <a name="next-steps"></a>Pasos siguientes

Para obtener detalles técnicos adicionales sobre cada configuración y sobre las ediciones de Windows compatibles, consulte [Windows 10 Policy CSP Reference](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) (Referencia sobre el CSP de directivas de Windows 10).
