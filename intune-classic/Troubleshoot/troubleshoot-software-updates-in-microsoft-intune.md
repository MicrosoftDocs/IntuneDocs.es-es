---
title: Solucionar problemas de actualizaciones de software
description: Resuelva problemas de actualizaciones de software en Microsoft Intune.
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d17b70f4-17b4-4d89-88fd-70fa4f34fbea
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 66cca236d2779fb9a7a01ad6aa10a57edf8ab657
ms.sourcegitcommit: 468480b61110ca81f737582ebbefd4efda6fd667
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/30/2018
---
# <a name="troubleshoot-software-updates-in-microsoft-intune"></a>Solucionar problemas de actualizaciones de software en Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Use la información de esta sección para resolver problemas con las actualizaciones de software en Microsoft Intune.

Si esta información no soluciona el problema, vea [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico para Microsoft Intune) para conocer otras formas de obtener ayuda.

## <a name="update-agent-error-codes"></a>Actualizar códigos de error del agente

En la tabla siguiente se muestran los códigos de error del **Agente de actualización** de Intune. Si no encuentra un código de error específico en esta tabla, vea [Windows Update Agent Result Codes (Códigos de resultado del Agente de Windows Update)](http://go.microsoft.com/fwlink/?LinkID=221542).

|Código de error|Nombre simbólico|Más información|
|--------------|-----------------|--------------------|
|**0x00cf0001**|OM_S_SERVICE_STOP|El agente se detuvo correctamente.|
|**0x00cf0003**|OM_S_UPDATE_ERROR|La operación se completó correctamente, pero se produjeron errores al aplicar las actualizaciones.|
|**0x00cf0004**|OM_S_MARKED_FOR_DISCONNECT|Se ha marcado una devolución de llamada para desconectarse más tarde porque la solicitud de desconectar la operación se produjo mientras se estaba ejecutando una devolución de llamada.|
|**0x00cf0005**|OM_S_REBOOT_REQUIRED|El sistema debe reiniciarse para completar la instalación de la actualización.|
|**0x00cf0006**|OM_S_ALREADY_INSTALLED|La actualización que se va a instalar ya está instalada en el sistema.|
|**0x00cf0007**|OM_S_ALREADY_UNINSTALLED|La actualización que se va a quitar no está instalada en el sistema.|
|**0x00cf2015**|OM_S_UH_INSTALLSTILLPENDING|La instalación de la actualización está en curso.|
|**0x80cf0001**|OM_E_NO_SERVICE|El agente no pudo proporcionar el servicio.|
|**0x80cf0002**|OM_E_MAX_CAPACITY_REACHED|Se superó la capacidad máxima del servicio.|
|**0x80cf0003**|OM_E_UNKNOWN_ID|No se encuentra un identificador.|
|**0x80cf0004**|OM_E_NOT_INITIALIZED|No se pudo inicializar el objeto.|
|**0x80cf0007**|OM_E_INVALIDINDEX|El índice de una colección no es válido.|
|**0x80cf0008**|OM_E_ITEMNOTFOUND|No se encontró la clave del elemento consultado.|
|**0x80cf0009**|OM_E_OPERATIONINPROGRESS|Había un conflicto con una operación en curso. Algunas operaciones (como, por ejemplo, varias instalaciones) no se pueden realizar simultáneamente.|
|**0x80cf000B**|OM_E_CALL_CANCELLED|Se canceló la operación.|
|**0x80cf000C**|OM_E_NOOP|No era necesaria ninguna operación.|
|**0x80cf000D**|OM_E_XML_MISSINGDATA|El agente no encontró la información necesaria en los datos XML de la actualización.|
|**0x80cf000E**|OM_E_XML_INVALID|El agente encontró información no válida en los datos XML de la actualización.|
|**0x80cf000F**|OM_E_CYCLE_DETECTED|Se detectaron relaciones circulares de actualización en los metadatos.|
|**0x80cf0010**|OM_E_TOO_DEEP_RELATION|No se pudieron evaluar las relaciones de actualización porque estaban anidadas en un nivel demasiado profundo.|
|**0x80cf0011**|OM_E_INVALID_RELATIONSHIP|Se encontró una relación de actualización que no es válida.|
|**0x80cf0012**|OM_E_REG_VALUE_INVALID|Se leyó un valor del Registro que no es válido.|
|**0x80cf0013**|OM_E_DUPLICATE_ITEM|La operación intentó agregar un elemento duplicado a una lista.|
|**0x80cf0014**|OM_E_INVALID_INSTALL_REQUESTED|El autor de la llamada no puede instalar las actualizaciones solicitadas.|
|**0x80cf0016**|OM_E_INSTALL_NOT_ALLOWED|La operación intentó instalar mientras se estaba realizando otra instalación o el sistema estaba pendiente de un reinicio obligatorio.|
|**0x80cf0017**|OM_E_NOT_APPLICABLE|No se realizó la operación porque no hay ninguna actualización aplicable.|
|**0x80cf0018**|OM_E_NO_USERTOKEN|Se produjo un error en la operación porque falta un token de usuario necesario.|
|**0x80cf0019**|OM_E_EXCLUSIVE_INSTALL_CONFLICT|Una actualización exclusiva no se puede instalar simultáneamente con otras actualizaciones.|
|**0x80cf001A**|OM_E_POLICY_NOT_SET|No se estableció un valor de directiva.|
|**0x80cf001D**|OM_E_INVALID_UPDATE|Una actualización contiene metadatos que no son válidos.|
|**0x80cf001E**|OM_E_SERVICE_STOP|No se pudo completar la operación porque se estaba cerrando el servicio o el sistema.|
|**0x80cf001F**|OM_E_NO_CONNECTION|No se pudo completar la operación porque la conexión de red no estaba disponible.|
|**0x80cf0020**|OM_E_NO_INTERACTIVE_USER|No se puede completar la operación porque no hay ningún usuario interactivo conectado.|
|**0x80cf0021**|OM_E_TIME_OUT|No se pudo completar la operación porque se agotó el tiempo de espera.|
|**0x80cf0022**|OM_E_ALL_UPDATES_FAILED|Error en la operación para todas las actualizaciones.|
|**0x80cf0024**|OM_E_NO_UPDATE|No hay actualizaciones.|
|**0x80cf0025**|OM_E_USER_ACCESS_DISABLED|La configuración de la directiva de grupo impidió el acceso a Windows Update.|
|**0x80cf0026**|OM_E_INVALID_UPDATE_TYPE|El tipo de actualización no es válido.|
|**0x80cf0028**|OM_E_UNINSTALL_NOT_ALLOWED|No se pudo desinstalar la actualización porque la solicitud no se originó en un servidor WSUS.|
|**0x80cf0029**|OM_E_INVALID_PRODUCT_LICENSE|Es posible que la búsqueda no haya encontrado algunas actualizaciones o puede haber una aplicación sin licencia en el sistema.|
|**0x80cf002C**|OM_E_BIN_SOURCE_ABSENT|No se puede instalar una actualización diferencial comprimida porque requería el origen.|
|**0x80cf002D**|OM_E_SOURCE_ABSENT|No se puede instalar una actualización de archivos completos porque requería el origen.|
|**0x80cf002E**|OM_E_WU_DISABLED|No se permite el acceso a un servidor no administrado.|
|**0x80cf002F**|OM_E_CALL_CANCELLED_BY_POLICY|No se pudo completar la operación porque se estableció la directiva **DisableWindowsUpdateAccess**.|
|**0x80cf0030**|OM_E_INVALID_PROXY_SERVER|El formato de la lista de servidores proxy no es válido.|
|**0x80cf0031**|OM_E_INVALID_FILE|El formato del archivo es incorrecto.|
|**0x80cf0032**|OM_E_INVALID_CRITERIA|La cadena de criterios de búsqueda no es válida.|
|**0x80cf0034**|OM_E_DOWNLOAD_FAILED|No se pudo descargar la actualización.|
|**0x80cf0035**|OM_E_UPDATE_NOT_PROCESSED|No se procesó la actualización.|
|**0x80cf0036**|OM_E_INVALID_OPERATION|El estado actual del objeto no permitió la operación.|
|**0x80cf0037**|OM_E_NOT_SUPPORTED|No se admite la operación.|
|**0x80cf0038**|OM_E_WINHTTP_INVALID_FILE|El archivo descargado tiene un tipo de contenido inesperado.|
|**0x80cf0039**|OM_E_TOO_MANY_RESYNC|El servidor envió al agente demasiadas solicitudes de resincronización.|
|**0x80cf0043**|OM_E_NO_UI_SUPPORT|No se admite la interfaz de usuario de WUA.|
|**0x80cf0044**|OM_E_PER_MACHINE_UPDATE_ACCESS_DENIED|Solo los administradores pueden realizar esta operación en actualizaciones por equipo.|
|**0x80cf0045**|OM_E_UNSUPPORTED_SEARCHSCOPE|Se intentó realizar una búsqueda con un alcance no admitido.|
|**0x80cf0046**|OM_E_BAD_FILE_URL|La dirección URL no apunta a un archivo.|
|**0x80cf0047**|OM_E_NOTSUPPORTED|No se admite la operación solicitada.|
|**0x80cf0049**|OM_E_OUTOFRANGE|Los datos están fuera del intervalo.|
|**0x80cf004A**|OM_E_INVALIDWUAVERSION|Los datos contienen una versión que no es válida.|
|**0x80cf004B**|OM_E_SEARCH_COMPLETED_WITH_SOME_FAILURES|Se completó la llamada de búsqueda, pero no se detectaron algunas de las actualizaciones.|
|**0x80cf004C**|OM_E_DOWNLOAD_COMPLETED_WITH_SOME_FAILURES|Se completó la llamada de descarga, pero no se descargaron algunas de las actualizaciones.|
|**0x80cf004D**|OM_E_INSTALL_COMPLETED_WITH_SOME_FAILURES|Se completó la llamada de instalación, pero no se instalaron algunas de las actualizaciones.|
|**0x80cf004E**|OM_E_WINUPDATE_CACHE_UNINITIALIZED|La caché de Windows Update está vacía porque no se ha inicializado.|
|**0x80cf0436**|OM_E_PT_CATALOG_SYNC_REQUIRED|El servidor no admite búsquedas específicas de categorías. En su lugar deben ejecutarse búsquedas de catálogo completo.|
|**0x80cf0437**|OM_E_PT_SECURITY_VERIFICATION_FAILURE|Hubo un problema al autorizar con el servicio.|
|**0x80cf0438**|OM_E_PT_ENDPOINT_UNREACHABLE|No hay conectividad de red o de ruta al extremo.|
|**0x80cf0439**|OM_E_PT_INVALID_FORMAT|Los datos recibidos no cumplen las expectativas del contrato de datos.|
|**0x80cf043A**|OM_E_PT_INVALID_URL|La dirección URL no es válida.|
|**0x80cf043B**|OM_E_PT_NWS_NOT_LOADED|No se puede cargar el entorno de tiempo de ejecución de NWS.|
|**0x80cf043C**|OM_E_PT_PROXY_AUTH_SCHEME_NOT_SUPPORTED|No se admite el esquema de autenticación de proxy.|
|**0x80cf043D**|OM_E_SERVICEPROP_NOTAVAIL|La propiedad de servicio solicitada no está disponible.|
|**0x80cf043E**|OM_E_PT_ENDPOINT_REFRESH_REQUIRED|El complemento de proveedor de extremo requiere una actualización en línea.|
|**0x80cf043F**|OM_E_PT_ENDPOINTURL_NOTAVAIL|No está disponible una dirección URL para el extremo de servicio solicitado.|
|**0x80cf0440**|OM_E_PT_ENDPOINT_DISCONNECTED|Se terminó la conexión al extremo de servicio.|
|**0x80cf0441**|OM_E_PT_INVALID_OPERATION|La operación no es válida porque el autor de llamadas de protocolo está en un estado inadecuado.|
|**0x80cf0FFF**|OM_E_UNEXPECTED|No se pudo completar la operación por razones que no se explican mediante otro código de error.|
|**0x80cf1001**|OM_E_MSI_WRONG_VERSION|La búsqueda no encontró algunas actualizaciones porque la versión de Windows Installer es anterior a la versión 3.1.|
|**0x80cf1002**|OM_E_MSI_NOT_CONFIGURED|La búsqueda no encontró algunas actualizaciones porque aún no se ha configurado Windows Installer.|
|**0x80cf1003**|OM_E_MSP_DISABLED|La búsqueda no encontró algunas actualizaciones porque la directiva deshabilitó la aplicación de revisiones de Windows Installer.|
|**0x80cf1004**|OM_E_MSI_WRONG_APP_CONTEXT|No se pudo aplicar una actualización porque la aplicación se instala por usuario.|
|**0x80cf2000**|OM_E_UH_REMOTEUNAVAILABLE|No se pudo completar una solicitud de controlador de actualización remota porque no hay ningún proceso remoto disponible.|
|**0x80cf2001**|OM_E_UH_LOCALONLY|No se pudo completar una solicitud de controlador de actualización remota porque el controlador es solo local.|
|**0x80cf2003**|OM_E_UH_REMOTEALREADYACTIVE|No se pudo crear un controlador de actualización remota porque ya existe uno.|
|**0x80cf2004**|OM_E_UH_DOESNOTSUPPORTACTION|No se pudo completar una solicitud al controlador para instalar (desinstalar) una actualización porque la actualización no es compatible con la instalación (desinstalación).|
|**0x80cf2005**|OM_E_UH_WRONGHANDLER|No se pudo completar una operación porque se especificó un controlador incorrecto.|
|**0x80cf2006**|OM_E_UH_INVALIDMETADATA|No se pudo completar una operación de controlador porque la actualización contiene metadatos que no son válidos.|
|**0x80cf2007**|OM_E_UH_INSTALLERHUNG|No se pudo completar una operación porque el instalador superó el límite de tiempo. Compruebe si se aprobó la implementación de una actualización que requiere la interacción con el usuario. En este caso deberá revisar los parámetros de instalación de la actualización para poder instalarla de forma silenciosa.|
|**0x80cf2008**|OM_E_UH_OPERATIONCANCELLED|Se canceló una operación que el controlador de actualización estaba realizando.|
|**0x80cf2009**|OM_E_UH_BADHANDLERXML|No se pudo completar una operación porque los metadatos específicos del controlador no son válidos.|
|**0x80cf200B**|OM_E_UH_INSTALLERFAILURE|El instalador no pudo instalar (desinstalar) una o varias actualizaciones.|
|**0x80cf200D**|OM_E_UH_NEEDANOTHERDOWNLOAD|El controlador de actualización no instaló la actualización porque debe volver a descargarse.|
|**0x80cf200E**|OM_E_UH_NOTIFYFAILURE|El controlador de actualización no pudo enviar la notificación de estado de la operación de instalación (desinstalación).|
|**0x80cf2014**|OM_E_UH_POSTREBOOTSTILLPENDING|La operación posterior al reinicio para la actualización sigue en curso.|
|**0x80cf2015**|OM_E_UH_POSTREBOOTRESULTUNKNOWN|No se pudo determinar el resultado de la operación posterior al reinicio para la actualización.|
|**0x80cf2016**|OM_E_UH_POSTREBOOTUNEXPECTEDSTATE|El estado de la actualización tras la operación posterior al reinicio se completó de manera inesperada.|
|**0x80cf2017**|OM_E_UH_NEW_SERVICING_STACK_REQUIRED|Hay que actualizar la pila de servicios del sistema operativo antes de poder descargar o instalar esta actualización.|
|**0x80cf2018**|OM_E_UH_CALLED_BACK_FAILURE|Un instalador de devolución de llamada devolvió una llamada con error.|
|**0x80cf2019**|OM_E_UH_CUSTOMINSTALLER_INVALID_SIGNATURE|La firma de instalador personalizada no coincide con la firma requerida por la actualización.|
|**0x80cf201A**|OM_E_UH_UNSUPPORTED_INSTALLCONTEXT|El instalador no admite la configuración de instalación.|
|**0x80cf201B**|OM_E_UH_INVALID_TARGETSESSION|La sesión de destino para la instalación no es válida.|
|**0x80cf2FFF**|OM_E_UH_UNEXPECTED|Un error de actualización de controlador no está cubierto por otro código de OM_E_UH_&#42;.|
|**0x80cf3FFD**|OM_E_NON_UI_MODE|No se puede mostrar la interfaz de usuario en modo de funcionamiento sin interfaz de usuario. Es posible que no estén instalados los módulos de interfaz de usuario del cliente de Windows Update.|
|**0x80cf3FFE**|OM_E_WUCLTUI_UNSUPPORTED_VERSION|No se admite esta versión de las funciones exportadas de la interfaz de usuario del cliente de WU.|
|**0x80cf3FFF**|OM_E_AUCLIENT_UNEXPECTED|Se produjo un error de interfaz de usuario que no está cubierto por otro código de error de OM_E_AUCLIENT_&#42;.|
|**0x80cf4007**|OM_E_PT_SOAPCLIENT_SOAPFAULT|Igual que **SOAPCLIENT_SOAPFAULT**. Error del cliente SOAP a causa de un error de SOAP con el tipo de código de error **OM_E_PT_SOAP_&#42;**.|
|**0x80cf4008**|OM_E_PT_SOAPCLIENT_PARSEFAULT|Igual que **SOAPCLIENT_PARSEFAULT_ERROR**.  El cliente SOAP no pudo analizar un error de SOAP.|
|**0x80cf400A**|OM_E_PT_SOAPCLIENT_PARSE|Igual que **SOAPCLIENT_PARSE_ERROR**.  El cliente SOAP no pudo analizar la respuesta del servidor.|
|**0x80cf400B**|OM_E_PT_SOAP_VERSION|Igual que **SOAP_E_VERSION_MISMATCH**. El cliente SOAP detectó un espacio de nombres no reconocible para la envoltura SOAP.|
|**0x80cf400C**|OM_E_PT_SOAP_MUST_UNDERSTAND|Igual que **SOAP_E_MUST_UNDERSTAND**. El cliente SOAP no pudo interpretar un encabezado.|
|**0x80cf400D**|OM_E_PT_SOAP_CLIENT|Igual que **SOAP_E_CLIENT**. El cliente SOAP detectó un formato incorrecto en el mensaje. Corríjalo antes de volver a enviarlo.|
|**0x80cf400E**|OM_E_PT_SOAP_SERVER|Igual que **SOAP_E_SERVER**. No se pudo procesar el mensaje SOAP a causa de un error de servidor. Vuelva a enviarlo más tarde.|
|**0x80cf4010**|OM_E_PT_EXCEEDED_MAX_SERVER_TRIPS|El número de viajes de ida y vuelta al servidor superó el límite máximo.|
|**0x80cf4012**|OM_E_PT_DOUBLE_INITIALIZATION|No se pudo inicializar porque el objeto ya estaba inicializado.|
|**0x80cf4013**|OM_E_PT_INVALID_COMPUTER_NAME|No se puede determinar el nombre del equipo.|
|**0x80cf4015**|OM_E_PT_REFRESH_CACHE_REQUIRED|La respuesta del servidor indica que se ha cambiado el servidor o que la cookie no es válida. Actualice la caché interna y reinténtelo.|
|**0x80cf4016**|OM_E_PT_HTTP_STATUS_BAD_REQUEST|Igual que **estado HTTP 400**. El servidor no pudo procesar la solicitud porque la sintaxis no es válida.|
|**0x80cf4017**|OM_E_PT_HTTP_STATUS_DENIED|Igual que **estado HTTP 401**. El recurso solicitado requiere autenticación de usuarios.|
|**0x80cf4018**|OM_E_PT_HTTP_STATUS_FORBIDDEN|Igual que **estado HTTP 403**. El servidor comprendió la solicitud pero la rechazó.|
|**0x80cf4019**|OM_E_PT_HTTP_STATUS_NOT_FOUND|Igual que **estado HTTP 404**. El servidor no encuentra el URI (identificador uniforme de recursos) solicitado.|
|**0x80cf401A**|OM_E_PT_HTTP_STATUS_BAD_METHOD|Igual que **estado HTTP 405**. El método HTTP no está permitido.|
|**0x80cf401B**|OM_E_PT_HTTP_STATUS_PROXY_AUTH_REQ|Igual que **estado HTTP 407**. Se requiere autenticación de proxy.|
|**0x80cf401C**|OM_E_PT_HTTP_STATUS_REQUEST_TIMEOUT|Igual que **estado HTTP 408**. El servidor agotó el tiempo de espera para la solicitud.|
|**0x80cf401D**|OM_E_PT_HTTP_STATUS_CONFLICT|Igual que **estado HTTP 409**. La solicitud no se completó debido a un conflicto con el estado actual del recurso.|
|**0x80cf401E**|OM_E_PT_HTTP_STATUS_GONE|Igual que **estado HTTP 410**. El recurso solicitado ya no está disponible en el servidor.|
|**0x80cf401F**|OM_E_PT_HTTP_STATUS_SERVER_ERROR|Igual que **estado HTTP 500**. No se pudo completar la solicitud a causa de un error interno en el servidor.|
|**0x80cf4020**|OM_E_PT_HTTP_STATUS_NOT_SUPPORTED|Igual que **estado HTTP 500**. El servidor no admite la funcionalidad necesaria para completar la solicitud.|
|**0x80cf4021**|OM_E_PT_HTTP_STATUS_BAD_GATEWAY|Igual que **estado HTTP 502**. Mientras actuaba como puerta de enlace o proxy, el servidor recibió una respuesta no válida del servidor precedente al que tenía acceso mientras intentaba completar la solicitud.|
|**0x80cf4022**|OM_E_PT_HTTP_STATUS_SERVICE_UNAVAIL|Igual que **estado HTTP 503**. El servicio está sobrecargado temporalmente.|
|**0x80cf4023**|OM_E_PT_HTTP_STATUS_GATEWAY_TIMEOUT|Igual que **estado HTTP 503**. Se agotó el tiempo de espera de una puerta de enlace para la solicitud.|
|**0x80cf4024**|OM_E_PT_HTTP_STATUS_VERSION_NOT_SUP|Igual que **estado HTTP 505**. El servidor no admite la versión del protocolo HTTP que se usa para la solicitud.|
|**0x80cf4025**|OM_E_PT_FILE_LOCATIONS_CHANGED|No se pudo completar la operación a causa de un cambio de ubicación de archivo. Actualice el estado interno y repita el envío.|
|**0x80cf4027**|OM_E_PT_NO_AUTH_PLUGINS_REQUESTED|El servidor devolvió una lista de información de autenticación vacía.|
|**0x80cf4028**|OM_E_PT_NO_AUTH_COOKIES_CREATED|El agente no pudo crear cookies de autenticación válidas.|
|**0x80cf4029**|OM_E_PT_INVALID_CONFIG_PROP|Un valor de propiedad de configuración no es correcto.|
|**0x80cf402A**|OM_E_PT_CONFIG_PROP_MISSING|Falta un valor de propiedad de configuración.|
|**0x80cf402B**|OM_E_PT_HTTP_STATUS_NOT_MAPPED|No se pudo completar la solicitud de HTTP y la razón no se correspondía con ninguno de los códigos de error **OM_E_PT_HTTP_&#42;**.|
|**0x80cf402C**|OM_E_PT_WINHTTP_NAME_NOT_RESOLVED|Igual que **ERROR_WINHTTP_NAME_NOT_RESOLVED**. No se puede resolver el nombre del servidor proxy o el servidor de destino.|
|**0x80cf402F**|OM_E_PT_ECP_SUCCEEDED_WITH_ERRORS|Se completó el procesamiento del archivo .CAB externo con algunos errores.|
|**0x80cf4030**|OM_E_PT_ECP_INIT_FAILED|No se completó la inicialización del procesador de archivos .CAB externos.|
|**0x80cf4031**|OM_E_PT_ECP_INVALID_FILE_FORMAT|El formato de un archivo de metadatos no es válido.|
|**0x80cf4032**|OM_E_PT_ECP_INVALID_METADATA|El procesador de archivos .CAB externos detectó metadatos no válidos.|
|**0x80cf4033**|OM_E_PT_ECP_FAILURE_TO_EXTRACT_DIGEST|No se pudo extraer el resumen de archivo de un archivo .CAB externo.|
|**0x80cf4034**|OM_E_PT_ECP_FAILURE_TO_DECOMPRESS_CAB_FILE|No se pudo descomprimir un archivo .CAB externo.|
|**0x80cf4035**|OM_E_PT_ECP_FILE_LOCATION_ERROR|El procesador de archivos. CAB externos no pudo obtener las ubicaciones de los archivos.|
|**0x80cf4FFF**|OM_E_PT_UNEXPECTED|Se produjo un error de comunicación que no está cubierto por otro código de error **OM_E_PT_&#42;**.|
|**0x80cf6001**|OM_E_DM_URLNOTAVAILABLE|No se pudo completar una operación del administrador de descargas porque el archivo solicitado no tiene una dirección URL.|
|**0x80cf6002**|OM_E_DM_INCORRECTFILEHASH|No se pudo completar una operación del administrador de descargas porque no se reconoció el resumen de archivo.|
|**0x80cf6003**|OM_E_DM_UNKNOWNALGORITHM|No se pudo completar una operación del administrador de descargas porque los metadatos del archivo solicitaron un algoritmo hash no reconocido.|
|**0x80cf6005**|OM_E_DM_NONETWORK|No se pudo completar la operación del administrador de descargas porque la conexión de red no estaba disponible.|
|**0x80cf6007**|OM_E_DM_NOTDOWNLOADED|No se descargó la actualización.|
|**0x80cf6008**|OM_E_DM_FAILTOCONNECTTOBITS|No se pudo completar una operación del administrador de descargas porque el administrador de descargas no se pudo conectar al Servicio de transferencia inteligente en segundo plano (BITS).|
|**0x80cf6009**|OM_E_DM_BITSTRANSFERERROR|No se pudo completar una operación del administrador de descargas a causa de un error no especificado de transferencia del Servicio de transferencia inteligente en segundo plano (BITS).|
|**0x80cf600a**|OM_E_DM_DOWNLOADLOCATIONCHANGED|Hay que reiniciar una descarga porque la ubicación de origen de la descarga ha cambiado.|
|**0x80cf600B**|OM_E_DM_CONTENTCHANGED|Debe reiniciar una descarga porque el contenido de actualización cambió en una nueva revisión.|
|**0x80cf6FFF**|OM_E_DM_UNEXPECTED|Se produjo un error del administrador de descargas que no está cubierto por otro código de error **OM_E_DM_&#42;**.|
|**0x80cf7003**|OM_E_INVALID_EVENT_PAYLOAD|Se especificó una carga de eventos que no es válida.|
|**0x80cf7004**|OM_E_INVALID_EVENT_PAYLOADSIZE|El tamaño de la carga de eventos enviado no es válido.|
|**0x80cf7005**|OM_E_SERVICE_NOT_REGISTERED|El servicio no está registrado.|
|**0x80cf8000**|OM_E_DS_SHUTDOWN|No se pudo completar una operación porque se está cerrando el agente.|
|**0x80cf8001**|OM_E_DS_INUSE|No se pudo completar una operación porque se estaba utilizando el almacén de datos.|
|**0x80cf8002**|OM_E_DS_INVALID|El estado actual y el esperado del almacén de datos no coinciden.|
|**0x80cf8003**|OM_E_DS_TABLEMISSING|Falta una tabla en el almacén de datos.|
|**0x80cf8004**|OM_E_DS_TABLEINCORRECT|El almacén de datos contiene una tabla con columnas inesperadas.|
|**0x80cf8005**|OM_E_DS_INVALIDTABLENAME|No se puede abrir una tabla porque no está en el almacén de datos.|
|**0x80cf8006**|OM_E_DS_BADVERSION|La versión actual y la esperada del almacén de datos no coinciden.|
|**0x80cf8007**|OM_E_DS_NODATA|La información solicitada no está en el almacén de datos.|
|**0x80cf8008**|OM_E_DS_MISSINGDATA|Falta información necesaria en el almacén de datos o tiene un valor nulo en una columna de tabla que requiere un valor no nulo.|
|**0x80cf8009**|OM_E_DS_MISSINGREF|Falta información necesaria en el almacén de datos o el almacén contiene una referencia a términos de licencia, un archivo, una propiedad localizada o una fila vinculada que faltan.|
|**0x80cf800A**|OM_E_DS_UNKNOWNHANDLER|No se procesó la actualización porque no se reconoció su controlador de actualización.|
|**0x80cf800B**|OM_E_DS_CANTDELETE|No se eliminó la actualización porque uno o más servicios aún hacen referencia a la misma.|
|**0x80cf800C**|OM_E_DS_LOCKTIMEOUTEXPIRED|No se pudo bloquear la sección del almacén de datos en el tiempo asignado.|
|**0x80cf800E**|OM_E_DS_ROWEXISTS|No se agregó la fila porque una fila existente tiene la misma clave principal.|
|**0x80cf800F**|OM_E_DS_STOREFILELOCKED|No se pudo inicializar el almacén de datos porque estaba bloqueado por otro proceso.|
|**0x80cf8010**|OM_E_DS_CANNOTREGISTER|No se puede registrar el almacén de datos en el proceso actual mediante COM.|
|**0x80cf8011**|OM_E_DS_UNABLETOSTART|Una operación no pudo crear un objeto de almacén de datos en otro proceso.|
|**0x80cf8013**|OM_E_DS_DUPLICATEUPDATEID|El servidor envió la misma actualización al cliente con dos identificadores de revisión distintos.|
|**0x80cf8014**|OM_E_DS_UNKNOWNSERVICE|No se pudo completar una operación porque el servicio no está en el almacén de datos.|
|**0x80cf8015**|OM_E_DS_SERVICEEXPIRED|No se pudo completar una operación porque el registro del servicio ha expirado.|
|**0x80cf8016**|OM_E_DS_DECLINENOTALLOWED|Se rechazó una solicitud para ocultar una actualización porque es una actualización obligatoria o porque se implementó con una fecha límite.|
|**0x80cf8017**|OM_E_DS_TABLESESSIONMISMATCH|No se cerró una tabla porque no está asociada a la sesión.|
|**0x80cf8018**|OM_E_DS_SESSIONLOCKMISMATCH|No se cerró una tabla porque no está asociada a la sesión.|
|**0x80cf8019**|OM_E_DS_NEEDWINDOWSSERVICE|Se rechazó la solicitud de eliminar o anular el registro del servicio porque es un servicio integrado o porque Actualizaciones automáticas no puede cambiar a otro servicio.|
|**0x80cf801A**|OM_E_DS_INVALIDOPERATION|Se rechazó la solicitud porque no se permite la operación.|
|**0x80cf801B**|OM_E_DS_SCHEMAMISMATCH|El esquema del almacén de datos actual y el esquema de una tabla de un documento XML de copia de seguridad no coinciden.|
|**0x80cf801C**|OM_E_DS_RESETREQUIRED|El almacén de datos requiere un reinicio de sesión. Libere la sesión y reinténtelo con una nueva sesión.|
|**0x80cf801D**|OM_E_DS_IMPERSONATED|No se pudo completar una operación de almacén de datos porque se solicitó con una identidad suplantada.|
|**0x80cf8FFF**|OM_E_DS_UNEXPECTED|Se produjo un error de almacén de datos que no está cubierto por otro código **OM_E_DS_&#42;**.|
|**0x80cfA000**|OM_E_AU_NOSERVICE|Actualizaciones automáticas no pudo atender las solicitudes entrantes.|
|**0x80cfA004**|OM_E_AU_PAUSED|Actualizaciones automáticas no pudo procesar las solicitudes entrantes porque estaba en pausa.|
|**0x80cfA005**|OM_E_AU_NO_REGISTERED_SERVICE|No hay ningún servicio no administrado registrado en Actualizaciones automáticas.|
|**0x80cfA006**|OM_E_AU_DETECT_SVCID_MISMATCH|Se cambió el servicio predeterminado registrado en Actualizaciones automáticas durante la búsqueda.|
|**0x80cfA007**|OM_E_AU_ALREADY_PROMPTING_FOR_REBOOT|Actualizaciones automáticas ya está pidiendo al usuario que reinicie el equipo.|
|**0x80cfAFFF**|OM_E_AU_UNEXPECTED|Se produjo un error de Actualizaciones automáticas que no está cubierto por otro código **OM_E_AU &#42;**.|
|**0x80cfE001**|OM_E_EE_UNKNOWN_EXPRESSION|No se pudo completar una operación del evaluador de expresiones porque no se reconoció una expresión.|
|**0x80cfE002**|OM_E_EE_INVALID_EXPRESSION|No se pudo completar una operación del evaluador de expresiones porque una expresión no era válida.|
|**0x80cfE003**|OM_E_EE_MISSING_METADATA|No se pudo completar una operación del evaluador de expresiones porque una expresión contenía un número incorrecto de nodos de metadatos.|
|**0x80cfE004**|OM_E_EE_INVALID_VERSION|No se pudo completar una operación del evaluador de expresiones porque la versión de los datos de expresión serializados no es válida.|
|**0x80cfE005**|OM_E_EE_NOT_INITIALIZED|No se pudo inicializar el evaluador de expresiones.|
|**0x80cfE006**|OM_E_EE_INVALID_ATTRIBUTEDATA|No se pudo completar una operación del evaluador de expresiones porque un atributo no es válido.|
|**0x80cfE007**|OM_E_EE_CLUSTER_ERROR|No se pudo completar una operación del evaluador de expresiones porque no se pudo determinar el estado del clúster del equipo.|
|**0x80cfEFFF**|OM_E_EE_UNEXPECTED|Se produjo un error del evaluador de expresiones que no está cubierto por otro código de error **OM_E_EE_&#42;**.|
|**0x80cfF001**|OM_E_REPORTER_EVENTCACHECORRUPT|El archivo de caché de eventos era defectuoso.|
|**0x80cfF002**|OM_E_REPORTER_EVENTNAMESPACEPARSEFAILED|No se pudieron analizar los datos XML del descriptor del espacio de nombres de eventos.|
|**0x80cfF003**|OM_E_INVALID_EVENT|Los datos XML del descriptor del espacio de nombres de eventos no son válidos.|
|**0x80cfF004**|OM_E_SERVER_BUSY|El servidor rechazó un evento porque estaba demasiado ocupado.|
|**0x80cfFFFF**|OM_E_REPORTER_UNEXPECTED|Se produjo un error de informador que no está cubierto por otro código de error.|
|**0x80af0005**|OMC_E_INSTALL_NOT_ALLOWED_REBOOT_REQUIRED|Se produjo un error en la instalación porque hay un reinicio obligatorio pendiente.|
|**0x80af0006**|OMC_E_DOWNLOAD_CANCELLED|Se canceló la descarga.|

## <a name="windows-7-based-computers-with-lots-of-superseded-updates-stop-reporting-to-the-microsoft-intune-console"></a>Los equipos basados en Windows 7 con numerosas actualizaciones reemplazadas dejan de informar a la consola de Microsoft Intune
**Problema**: puede encontrarse ante una situación en la que los clientes de Microsoft Intune experimentan uno o varios de los síntomas siguientes:
- Dejan de informar repentinamente a la consola de administración de Microsoft.  
- Experimentan un uso intensivo de la CPU.
- Las aplicaciones se instalan lentamente cuando la instalación se realiza a través del portal de Intune.
- Microsoft Intune Center desencadena el error siguiente: *Error al actualizar el equipo. Error detectado con el código 0x800705b4*.
- El campo de estado en la consola de administración de Intune > Grupos > Todos los dispositivos muestra: *Al menos un agente instalado en este equipo tiene errores. Es posible que la información de este equipo no sea exacta o no esté actualizada*.

Este problema puede producirse si las actualizaciones reemplazadas (las actualizaciones que reemplazó otra actualización) no se han rechazado durante un largo período. Durante ciertos procesos, como la instalación de una aplicación, Windows comprueba todas las actualizaciones reemplazadas de forma secuencial para que las actualizaciones y sus sucesores puedan asignarse correctamente. Si la lista de actualizaciones reemplazadas aumenta demasiado, esta tarea de comprobación puede hacer un uso intensivo de la CPU debido a la carga de procesamiento y el tiempo necesario. Este problema afecta principalmente a los clientes que ejecutan Windows 7, debido al elevado número de actualizaciones reemplazadas que están disponibles para Windows 7. Windows 8 y los sistemas operativos posteriores no tienen disponibles tantas actualizaciones reemplazadas y, por tanto, no son tan susceptibles de sufrir este problema.

**Solución**: para solucionar este problema, siga estos pasos:
1. Inicie sesión en la [consola de administración de Intune](https://manage.microsoft.com).
2. Seleccione **Actualizaciones** > **Todas las actualizaciones**.
3. Use la opción de filtro de la barra de herramientas superior para filtrar las actualizaciones reemplazadas.
4. Rechace todas las actualizaciones reemplazadas que se apliquen a Windows 7 o a las aplicaciones (como Microsoft Office) que se instalaron en los clientes afectados.
5. Reinicie los clientes afectados.

Además, si ejecuta Windows 7, asegúrese de que tiene instalada la actualización siguiente:[Cliente de Windows Update 3050265 para Windows 7: junio de 2015](https://support.microsoft.com/kb/3050265).

### <a name="next-steps"></a>Pasos siguientes
Si esta información para solucionar problemas no le ha ayudado, póngase en contacto con el servicio de soporte técnico de Microsoft como se indica en [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico de Microsoft Intune).
