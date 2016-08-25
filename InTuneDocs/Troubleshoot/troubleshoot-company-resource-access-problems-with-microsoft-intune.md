---
title: Solucionar problemas de acceso a los recursos de la empresa | Microsoft Intune
description: "Códigos de error y estado en este tema para ayudarle a solucionar problemas de acceso a los recursos."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 08/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 40622ced-6029-4abf-873e-b51d2b51934c
ms.reviewer: tscott
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb0aeac2f94dfde50d9398b09c6b21c7ae40624
ms.openlocfilehash: 144fa2e18670805ef46cf2d3db86ec254cdfdf77


---

# Solucionar problemas de acceso a los recursos de la empresa con Microsoft Intune
Use los códigos de error y de estado de este tema para que le resulte más fácil solucionar problemas cuando una acción de Microsoft Intune devuelva un código de error.

Si esta información no soluciona el problema, vea [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico para Microsoft Intune) para conocer otras formas de obtener ayuda.

## Códigos de estado de dispositivos de Windows administrados mediante MDM

|Código de estado|Mensaje de error|Qué hacer|
|---------------|-----------------|--------------|
|10 (APP_CI_ENFORCEMENT_IN_PROGRESS)|Instalación en curso||
|20 (APP_CI_ENFORCEMENT_IN_PROGRESS_WAITING_CONTENT)|Esperando contenido||
|30 (APP_CI_ENFORCEMENT_IN_PROGRESS_WAITING_CONTENT)|Recuperando contenido|Causa probable: el estado de trabajo 30 indica un error de descarga de aplicación de un usuario.<br /><br />Las causas probables pueden ser:<br /><br />El dispositivo había perdido la conectividad de Internet mientras la descarga estaba en curso.<br /><br />Puede haber expirado el certificado emitido para el dispositivo en el momento de la inscripción.<br /><br />Mitigación:<br /><br />Inicie la aplicación Aplicaciones de empresa desde el Panel de Control del dispositivo para confirmar que el certificado del dispositivo no ha expirado; en caso afirmativo, deberá volver a inscribirlo.<br /><br />Compruebe que el dispositivo está conectado a Internet y pruebe a solicitar la aplicación de nuevo.|
|40 (APP_CI_ENFORCEMENT_IN_PROGRESS_CONTENT_DOWNLOADED)|Descarga de contenido completa||
|50 (APP_CI_ENFORCEMENT_IN_PROGRESS_INSTALLING)|Instalación en curso||
|60 (APP_CI_ENFORCEMENT_ERROR_INSTALLING)|InstalaciónSe produjo un error|Error en la instalación de la aplicación después de la descarga.<br /><br />El certificado de firma de código con el que se firmó la aplicación no está presente en el dispositivo.<br /><br />Una dependencia de marco de trabajo de la que depende la aplicación no se encuentra instalada en el dispositivo.<br /><br />Asegúrese de que el certificado de firma de código con el que se firmó la aplicación está presente en el dispositivo y confirme con el administrador que este certificado está destinado a todos los dispositivos de Windows RT inscritos de la empresa.<br /><br />Si el error de instalación se debe a la falta de una dependencia de marco de trabajo, el administrador tendrá que volver a publicar la aplicación y empaquetar el marco de trabajo junto con el paquete de aplicación.<br /><br />El paquete de aplicación descargado no es un paquete válido, puede estar dañado o no ser compatible con la versión del sistema operativo del dispositivo.|
|70 (APP_CI_ENFORCEMENT_SUCCEEDED)|Instalación correcta||
|80 (APP_CI_ENFORCEMENT_IN_PROGRESS)|Desinstalación en curso||
|90 (APP_CI_ENFORCEMENT_ERROR)|Se produjo un error de desinstalación||
|100 (APP_CI_ENFORCEMENT_SUCCEEDED)|Desinstalación correcta||
|110 (APP_CI_ENFORCEMENT_ERROR)|Error de coincidencia de hash de contenido||
|120 (APP_CI_ENFORCEMENT_ERROR)|SLK/instalación de prueba no habilitada||
|130 (APP_CI_ENFORCEMENT_ERROR)|Error de instalación de licencias MSADP||
|Ningún estado (APP_CI_ENFORCEMENT_UNKNOWN)|n/a|Se desconoce el estado actualmente.|

## Acceso a recursos de la compañía (errores comunes)

|Código de estado|Código de error hexadecimal|Mensaje de error|
|---------------|--------------------------|-----------------|
|-2016281101|0x87D1FDF3|Solicitud de CRP de MDM no encontrada|
|-2016281102|0x87D1FDF2|No se encontró la URL de NDES.|
|-2016281103|0x87D1FDF1|Certificado CRP de MDM no encontrado|
|-2016281104|0x87D1FDF0|Certificado CI de MDM no encontrado|
|-2016281105|0x87D1FDEF|No se pudo evaluar la Regla|
|-2016281106|0x87D1FDEE|No aplicable porque perdió en la resolución de conflictos|
|-2016281107|0x87D1FDED|Origen de detección de configuración no admitido|
|-2016281108|0x87D1FDEC|La configuración a la que se hace referencia no se encontró en el elemento de configuración|
|-2016281109|0x87D1FDEB|Error de conversión de tipo de datos|
|-2016281110|0x87D1FDEA|Parámetro no válido para la configuración de CIM|
|-2016281111|0x87D1FDE9|No se aplica a este dispositivo|
|-2016281112|0x87D1FDE8|Error de corrección|
|-2016330905|0x87D13B67|El estado de la aplicación es desconocido|
|-2016330906|0x87D13B66|La aplicación está administrada pero el usuario la ha quitado|
|-2016330907|0x87D13B65|El dispositivo está canjeando el código de canje|
|-2016330908|0x87D13B64|Error al instalar la aplicación|
|-2016330909|0x87D13B63|El usuario rechazó la oferta para actualizar la aplicación|
|-2016330910|0x87D13B62|El usuario rechazó la oferta para instalar la aplicación|
|-2016330911|0x87D13B61|El usuario ha instalado la aplicación antes de que se llevar a cabo la instalación de la aplicación administrada|
|-2016330912|0x87D13B60|La aplicación está programada para la instalación pero necesita un código de canje para completar la transacción|
|-2016341109|0x87D1138B|El dispositivo iOS ha devuelto un error|
|-2016341110|0x87D1138A|El dispositivo iOS ha rechazado el comando debido a un formato incorrecto|
|-2016341111|0x87D11389|El dispositivo iOS ha devuelto un estado Inactivo inesperado|
|-2016341112|0x87D11388|El dispositivo iOS está ocupado actualmente|

## Errores devueltos por dispositivos iOS

|Código de estado|Código de error hexadecimal|Mensaje de error|
|---------------|--------------------------|-----------------|
|-2016299111|0x87D1B799|Error interno|
|-2016299112|0x87D1B798|Error interno|
|-2016300111|0x87D1B3B1|36001: (error interno)|
|-2016300112|0x87D1B3B0|36000: La red de telefonía móvil ya está configurada|
|-2016301110|0x87D1AFCA|35002: Varias fuentes en una única carga|
|-2016301111|0x87D1AFC9|35001: Error al instalar las fuentes|
|-2016301112|0x87D1AFC8|35000: Datos de fuente no válidos|
|-2016302109|0x87D1ABE3|34003: El nombre principal Kerberos no es válido|
|-2016302110|0x87D1ABE2|34002: Falta el nombre principal Kerberos|
|-2016302111|0x87D1ABE1|34001: Modelo de coincidencia de dirección URL no válido|
|-2016302112|0x87D1ABE0|34000: Modelo de coincidencia de identificador de la aplicación no válido|
|-2016304112|0x87D1A410|32000: Demasiadas aplicaciones|
|-2016305111|0x87D1A029|31001: No se puede aplicar la configuración|
|-2016305112|0x87D1A028|31000: No se puede aplicar la credencial|
|-2016306111|0x87D19C41|30001: Tiempo de espera agotado|
|-2016306112|0x87D19C40|30000: Error en la autentificación|
|-2016307109|0x87D1985B|29003: Datos de certificado incorrectos|
|-2016307110|0x87D1985A|29002:|
|-2016307111|0x87D19859|29001:|
|-2016307112|0x87D19858|29000: El dispositivo no está supervisado|
|-2016308110|0x87D19472|28002: No se puede establecer el papel tapiz|
|-2016308111|0x87D19471|28001: Imagen de papel tapiz incorrecta|
|-2016308112|0x87D19470|28000: Elemento desconocido|
|-2016310111|0x87D18CA1|26001: Cifrado de nivel de archivos no admitido|
|-2016310112|0x87D18CA0|26000: Cifrado de nivel de bloque no admitido|
|-2016311110|0x87D188BA|25002: No se puede quitar|
|-2016311111|0x87D188B9|25001: No se puede instalar|
|-2016311112|0x87D188B8|25000: Perfil incorrecto|
|-2016312109|0x87D184D3|24003: Perfil final incorrecto|
|-2016312110|0x87D184D2|24002: Carga de identidad incorrecta|
|-2016312111|0x87D184D1|24001: No se puede firmar el diccionario de atributos|
|-2016312112|0x87D184D0|24000: No se puede crear el diccionario de atributos|
|-2016313110|0x87D180EA|23002: Certificado de servidor no válido|
|-2016313111|0x87D180E9|23001: Respuesta del servidor incorrecta|
|-2016313112|0x87D180E8|23000: Identidad incorrecta|
|-2016314099|0x87D17D0D|22013: Respuesta de la operación PKI no válida|
|-2016314100|0x87D17D0C|22012: No se puede almacenar el certificado de CA|
|-2016314101|0x87D17D0B|22011: No se puede generar el CSR|
|-2016314102|0x87D17D0A|22010: No se puede almacenar la identidad temporal|
|-2016314103|0x87D17D09|22009: No se puede crear la identidad temporal|
|-2016314104|0x87D17D08|22008: No se puede crear la identidad|
|-2016314105|0x87D17D07|22007: Certificado firmado no válido|
|-2016314106|0x87D17D06|22006: CAP de CA insuficientes|
|-2016314107|0x87D17D05|22005: Error de red|
|-2016314108|0x87D17D04|22004: Configuración de certificado no admitida|
|-2016314109|0x87D17D03|22003: Respuesta de RA no válida|
|-2016314110|0x87D17D02|22002: Respuesta de CA no válida|
|-2016314111|0x87D17D01|22001: No se puede generar el par de claves|
|-2016314112|0x87D17D00|22000: Uso de clave no válido|
|-2016315105|0x87D1791F|21007: No se puede verificar la cuenta|
|-2016315106|0x87D1791E|21006: No se puede descifrar el certificado|
|-2016315107|0x87D1791D|21005: La cuenta no es única|
|-2016315108|0x87D1791C|21004: No se puede crear la cuenta|
|-2016315109|0x87D1791B|21003: Sin nombre de host|
|-2016315110|0x87D1791A|21002: No se puede cumplir con la directiva de cifrado del servidor|
|-2016315111|0x87D17919|21001: No se puede cumplir con la directiva del servidor|
|-2016315112|0x87D17918|21000: No se puede obtener la directiva del servidor|
|-2016316110|0x87D17532|20002: La cuenta no es única|
|-2016316111|0x87D17531|20001: Sin nombre de host|
|-2016316112|0x87D17530|20000: No se puede crear la cuenta|
|-2016317110|0x87D1714A|19002: La cuenta no es única|
|-2016317111|0x87D17149|19001: Sin nombre de host|
|-2016317112|0x87D17148|19000: No se puede crear la cuenta|
|-2016318110|0x87D16D62|18002: Credenciales no válidas|
|-2016318111|0x87D16D61|18001: El host es inalcanzable|
|-2016318112|0x87D16D60|18000: Error desconocido|
|-2016319110|0x87D1697A|17002: La cuenta no es única|
|-2016319111|0x87D16979|17001: Sin nombre de host|
|-2016319112|0x87D16978|17000: No se puede crear la cuenta|
|-2016320110|0x87D16592|16002: La cuenta no es única|
|-2016320111|0x87D16591|16001: Sin nombre de host|
|-2016320112|0x87D16590|16000: No se puede crear la suscripción|
|-2016321109|0x87D161AB|15003: Certificado no válido|
|-2016321110|0x87D161AA|15002: No se puede bloquear la configuración de red|
|-2016321111|0x87D161A9|15001: No se puede quitar la VPN|
|-2016321112|0x87D161A8|15000: No se puede instalar la VPN|
|-2016322110|0x87D15DC2|14002: La configuración de la nube ya existe|
|-2016322111|0x87D15DC1|14001: Dispositivo bloqueado|
|-2016322112|0x87D15DC0|14000: Campo no válido|
|-2016323107|0x87D159DD|13005: No se puede configurar el proxy|
|-2016323108|0x87D159DC|13004: No se puede configurar EAP|
|-2016323109|0x87D159DB|13003: No se puede crear la configuración de Wi-Fi|
|-2016323110|0x87D159DA|13002: Se necesita una contraseña|
|-2016323111|0x87D159D9|13001: Se necesita un nombre de usuario|
|-2016323112|0x87D159D8|13000: No se puede instalar|
|-2016324070|0x87D1561A|12042: Código de config. regional desconocido|
|-2016324071|0x87D15619|12041: Código de idioma desconocido|
|-2016324072|0x87D15618|12040: Se necesita iniciar sesión en iTunes Store|
|-2016324073|0x87D15617|12039: (sin usar)|
|-2016324074|0x87D15616|12038: Aplicación no administrada|
|-2016324075|0x87D15615|12037: Código de canje no válido|
|-2016324076|0x87D15614|12036: No se puede quitar la aplicación en el estado actual|
|-2016324077|0x87D15613|12035: No se puede comprar la aplicación|
|-2016324078|0x87D15612|12034: La dirección URL no es HTTPS|
|-2016324079|0x87D15611|12033: Manifiesto no válido|
|-2016324080|0x87D15610|12032: Demasiadas aplicaciones en el manifiesto|
|-2016324081|0x87D1560F|12031: Instalación de la aplicación deshabilitada|
|-2016324082|0x87D1560E|12030: Dirección URL no válida|
|-2016324083|0x87D1560D|12029: Aplicación no administrada|
|-2016324084|0x87D1560C|12028: Sin esperar al canje|
|-2016324085|0x87D1560B|12027: No es una aplicación|
|-2016324086|0x87D1560A|12026: La aplicación ya está en cola|
|-2016324087|0x87D15609|12025: La aplicación ya está instalada|
|-2016324088|0x87D15608|12024: No se puedo validar el manifiesto de la aplicación|
|-2016324089|0x87D15607|12023: No se pudo validar el Id. de la aplicación|
|-2016324090|0x87D15606|12022: Tema no válido|
|-2016324091|0x87D15605|12021: Tipo de solicitud no válida|
|-2016324092|0x87D15604|12020: Sin autorización del servidor|
|-2016324093|0x87D15603|12019: No se puede copiar el secreto de Escrow|
|-2016324094|0x87D15602|12018: No se pueden copiar los datos del contenedor de claves de Escrow|
|-2016324095|0x87D15601|12017: No se puede crear el contenedor de claves de Escrow|
|-2016324096|0x87D15600|12016: Falta la identidad|
|-2016324097|0x87D155FF|12015: No se puede obtener el token de inserción|
|-2016324098|0x87D155FE|12014: El perfil de aprovisionamiento no está administrado|
|-2016324099|0x87D155FD|12013: El perfil no está administrado|
|-2016324100|0x87D155FC|12012: Error de coincidencia del reemplazo de MDM|
|-2016324101|0x87D155FB|12011: Configuración de MDM no válida|
|-2016324102|0x87D155FA|12010: Error de incoherencia interna|
|-2016324103|0x87D155F9|12009: Perfil de reemplazo no válido|
|-2016324104|0x87D155F8|12008: solicitud con formato incorrecto|
|-2016324105|0x87D155F7|12007: No autorizado|
|-2016324106|0x87D155F6|12006: Redireccionamiento rechazado|
|-2016324107|0x87D155F5|12005: No se puede encontrar el certificado|
|-2016324108|0x87D155F4|12004: Certificado de inserción no válido|
|-2016324109|0x87D155F3|12003: Respuesta de desafío no válida|
|-2016324110|0x87D155F2|12002: No se puede proteger|
|-2016324111|0x87D155F1|12001: Varias instancias MDM|
|-2016324112|0x87D155F0|12000: Derechos de acceso no válidos|
|-2016325111|0x87D15209|11001: El APN personalizado ya está instalado|
|-2016325112|0x87D15208|11000: No se puede instalar el APN|
|-2016326111|0x87D14E21|10001: Firmante no válido|
|-2016326112|0x87D14E20|10000: No se pueden instalar los valores predeterminados|
|-2016327106|0x87D14A3E|9006: El certificado no es una identidad|
|-2016327107|0x87D14A3D|9005: El certificado tiene un formato incorrecto|
|-2016327108|0x87D14A3C|9004: No se puede almacenar el certificado raíz|
|-2016327109|0x87D14A3B|9003: No se pueden almacenar los datos WAPI|
|-2016327110|0x87D14A3A|9002: No se puede almacenar el certificado|
|-2016327111|0x87D14A39|9001: Hay demasiados certificados en una carga|
|-2016327112|0x87D14A38|9000: Contraseña no válida|
|-2016328112|0x87D14650|8000: No se puede instalar la imagen de web|
|-2016329105|0x87D1426F|7007: La cuenta SMTP no está configurada correctamente|
|-2016329106|0x87D1426E|7006: La cuenta POP no está configurada correctamente|
|-2016329107|0x87D1426D|7005: La cuenta IMAP no está configurada correctamente|
|-2016329108|0x87D1426C|7004: El certificado SMIME es incorrecto|
|-2016329109|0x87D1426B|7003: Falta el certificado SMIME|
|-2016329110|0x87D1426A|7002: Ocurrió un error desconocido durante la validación|
|-2016329111|0x87D14269|7001: Credenciales no válidas|
|-2016329112|0x87D14268|7000: El host es inalcanzable|
|-2016330110|0x87D13E82|6002: No se puede crear la consulta|
|-2016330111|0x87D13E81|6001: Cadena vacía|
|-2016330112|0x87D13E80|6000: Error del sistema en la cadena de claves|
|-2016331097|0x87D13AA7|5015: No se puede establecer el período de gracia|
|-2016331098|0x87D13AA6|5014: No se puede establecer código de acceso|
|-2016331099|0x87D13AA5|5013: No se puede borrar el código de acceso|
|-2016331100|0x87D13AA4|5012: (sin usar)|
|-2016331101||5011: Código de acceso incorrecto|
|-2016331102||5010: Dispositivo bloqueado|
|-2016331103|0x87D13AA4|5009: (sin usar)|
|-2016331104|0x87D13AA0|5008: El código de acceso es demasiado reciente|
|-2016331105|0x87D13A9F|5007: Código de acceso expirado|
|-2016331106|0x87D13AA3|5006: El código de acceso necesita caracteres alfabéticos|
|-2016331107|0x87D13A9D|5005: El código de acceso necesita un número|
|-2016331108|0x87D13A9C|5004: El código de acceso tiene caracteres ascendentes y descendentes|
|-2016331109|0x87D13A9B|5003: El código de acceso tiene caracteres repetidos|
|-2016331110|0x87D13A9A|5002: Muy pocos caracteres complejos|
|-2016331111|0x87D13A99|5001: Muy pocos caracteres únicos|
|-2016331112|0x87D13A98|5000: El código de acceso es demasiado corto|
|-2016332093|0x87D136C3|4019: Varias cargas de bloqueo de aplicaciones|
|-2016332094|0x87D136C2|4018: Varias cargas APN o de red de telefonía móvil|
|-2016332095|0x87D136C1|4017: Varias cargas de proxy HTTP global|
|-2016332096|0x87D136C0|4016: (Error interno)|
|-2016332097|0x87D136BF|4015: El perfil de sustitución no contiene una carga MDM|
|-2016332098|0x87D136BE|4014: No hay ninguna identidad de dispositivo disponible|
|-2016332099|0x87D136BD|4013: Error al actualizar|
|-2016332100|0x87D136BC|4012: El perfil no se puede actualizar|
|-2016332101|0x87D136BB|4011: El perfil final no es un perfil de configuración|
|-2016332102|0x87D136BA|4010: El perfil actualizado no tiene el mismo identificador|
|-2016332103|0x87D136B9|4009: Dispositivo bloqueado|
|-2016332104|0x87D136B8|4008: Certificados no coincidentes|
|-2016332105|0x87D136B7|4007: Formato de archivo no reconocido|
|-2016332106|0x87D136B6|4006: La fecha de eliminación del perfil está en el pasado|
|-2016332107|0x87D136B5|4005: El código de acceso no es compatible|
|-2016332108|0x87D136B4|4004: El usuario canceló la instalación|
|-2016332109|0x87D136B3|4003: El perfil no está en cola para la instalación|
|-2016332110|0x87D136B2|4002: UUID duplicado|
|-2016332111|0x87D136B1|4001: Error al instalar|
|-2016332112|0x87D136B0|4000: No se puede analizar el perfil|
|-2016333111|0x87D132C9|3001: El sensor de comparación de valor no es coherente (error interno)|
|-2016333112|0x87D132C8|3000: El sensor de restricción no es coherente (error interno)|
|-2016334108|0x87D12EE4|2004: Valor de campo no admitido|
|-2016334109|0x87D12EE3|2003: Tipo de datos incorrectos en el campo|
|-2016334110|0x87D12EE2|2002: Falta el campo obligatorio|
|-2016334111|0x87D12EE1|2001: Versión de carga no admitida|
|-2016334112|0x87D12EE0|2000: Carga con formato incorrecto|
|-2016335102|0x87D12B02|1010: Valor de campo no admitido|
|-2016335103|0x87D12B01|1009: Error en la instalación del perfil|
|-2016335104|0x87D12B00|1008: Los identificadores de carga no son únicos|
|-2016335105|0x87D12AFF|1007: Los UUID no son únicos|
|-2016335106|0x87D12AFE|1006: No se puede descifrar|
|-2016335107|0x87D12AFD|1005: Perfil vacío|
|-2016335108|0x87D12AFC|1004: Firma incorrecta|
|-2016335109|0x87D12AFB|1003: Tipo de datos incorrectos en el campo|
|-2016335110|0x87D12AFA|1002: Falta el campo obligatorio|
|-2016335111|0x87D12AF9|1001: Versión de perfil no admitido|
|-2016335112|0x87D12AF8|1000: Perfil con formato incorrecto|

## Códigos de respuesta OMA

|Código de estado|Código de error hexadecimal|Mensaje de error|
|---------------|--------------------------|-----------------|
|-2016344008|0x87D10838|(1404): se ha denegado el acceso al certificado|
|-2016344009|0x87D10837|(1403): no se encuentra el certificado|
|-2016344010|0x87D10836|DCMO(1402): error de la operación|
|-2016344011|0x87D10835|DCMO(1401): el usuario eligió no aceptar la operación cuando se le solicitó|
|-2016344012|0x87D10834|DCMO(1400): error de cliente|
|-2016344108|0x87D107D4|DCMO(1204): la funcionalidad del dispositivo está deshabilitada y el usuario puede volver a habilitarla|
|-2016344109|0x87D107D3|DCMO(1203): la funcionalidad del dispositivo está deshabilitada y el usuario no puede volver a habilitarla|
|-2016344110|0x87D107D2|DCMO(1202): la operación de habilitación finalizó correctamente pero la funcionalidad del dispositivo está desconectada|
|-2016344111|0xF3FB4D95|DCMO(1201): la operación de habilitación finalizó correctamente y la funcionalidad del dispositivo está asociada|
|-2016344112|0x87D107D0|DCMO(1200): la operación finalizó correctamente|
|-2016345595|0x87D10205|Syncml(517): la respuesta a un comando atómico fue demasiado grande para un único mensaje.|
|-2016345596|0x87D10204|Syncml(516): el comando estaba dentro de un elemento atómico y se produjo un error del mismo. El comando no se revirtió correctamente.|
|-2016345598|0x87D10202|Syncml(514): el comando SyncML no se completó correctamente porque la operación se canceló antes de procesar el comando.|
|-2016345599|0x87D10201|Syncml(513): el destinatario no admite o rechaza la versión especificada del protocolo de sincronización de SyncML que se usa en el mensaje de solicitud de SyncML.|
|-2016345600|0x87D10200|Syncml(512): error de aplicación durante la sesión de sincronización.|
|-2016345601|0x87D101FF|Syncml(511): error grave en el servidor al procesar la solicitud.|
|-2016345602|0x87D101FE|Syncml(510): error al procesar la solicitud. El error está relacionado con un error en el almacén de datos del destinatario.|
|-2016345603|0x87D101FD|Syncml(509): reservado para uso en el futuro.|
|-2016345604|0x87D101FC|Syncml(508): se produjo un error que necesita una actualización del estado de sincronización actual del cliente con el servidor.|
|-2016345605|0x87D101FB|Syncml(507): el error hizo que todos los comandos de SyncML en un tipo de elemento atómico finalizaran incorrectamente.|
|-2016345606|0x87D101FA|Syncml(506): error de aplicación al procesar la solicitud.|
|-2016345607|0x87D101F9|Syncml(505): el destinatario no admite o rechaza admitir la versión especificada del DTD de SyncML que se usa en el mensaje de solicitud de SyncML.|
|-2016345608|=0x87D101F8|Syncml(504): el destinatario, mientras actuaba como puerta de enlace o proxy, no recibió una respuesta puntual del destinatario ascendente especificado por el URI (por ejemplo, HTTP, FTP o LDAP) u otro destinatario auxiliar (por ejemplo, DNS) al que necesitaba obtener acceso para satisfacer la solicitud.|
|-2016345609|0x87D101F7|Syncml(503): el destinatario no puede controlar la solicitud porque está temporalmente sobrecargado o se está realizando el mantenimiento del mismo.|
|-2016345610|0x87D101F6|Syncml(502): el destinatario, mientras actuaba como puerta de enlace o proxy, recibió una respuesta no válida del destinatario ascendente al que obtuvo acceso para satisfacer la solicitud.|
|-2016345611|0x87D101F5|Syncml(501): el destinatario no admite el comando requerido para satisfacer la solicitud.|
|-2016345612|0x87D101F4|Syncml(500): el destinatario detectó una condición inesperada que le impidió satisfacer la solicitud|
|-2016345684|0x87D101AC|Syncml(428): no se pudo mover|
|-2016345685|0x87D101AB|Syncml(427): el elemento primario no se puede eliminar porque contiene elementos secundarios.|
|-2016345686|0x87D101AA|Syncml:(426) elemento parcial no aceptado.|
|-2016345687|0x87D101A9|Syncml(425): error del comando solicitado porque el remitente no tiene permisos de control de acceso (ACL) adecuados en el destinatario.|
|-2016345688|0x87D101A8|Syncml(424): el objeto fragmentado se recibió, pero el tamaño del objeto recibido no coincidió con el tamaño declarado en el primer fragmento.|
|-2016345689|0x87D101A7|Syncml(423): error del comando solicitado porque el elemento que se eliminó temporalmente se había eliminado permanentemente previamente en el servidor.|
|-2016345690|0x87D101A6|Syncml(422): error en el servidor del comando solicitado porque el formato de script CGI en LocURI era incorrecto.|
|-2016345691|0x87D101A5|Syncml(421): error en el servidor del comando solicitado porque la gramática de búsqueda especificada era desconocida.|
|-2016345692|0x87D101A4|Syncml(420): el destinatario no dispone de más espacio de almacenamiento para los datos de sincronización restantes.|
|-2016345693|0x87D101A3|Syncml(419): la solicitud de cliente creó un conflicto que se resolvió al imponerse el comando del servidor.|
|-2016345694|0x87D101A2|Syncml(418): error del comando Put o Add porque el destino ya existe.|
|-2016345695|0x87D101A1|Syncml(417): error de solicitud. El originador debe reintentar la solicitud más tarde.|
|-2016345696|0x87D101A0|Syncml(416): error de la solicitud porque el tamaño de bytes especificado en la solicitud es demasiado grande.|
|-2016345697|0x87D1019F|Syncml(415): tipo o formato de soporte no admitido.|
|-2016345698|0x87D1019E|Syncml(414): error del comando solicitado porque la longitud del URI de destino es mayor que la que el destinatario puede o desea procesar.|
|-2016345699|0x87D1019D|Syncml(413): el destinatario rechaza realizar el comando solicitado porque el tamaño del elemento solicitado es mayor que el que el destinatario puede o desea procesar.|
|-2016345700|0x87D1019C|Syncml(412): error del comando solicitado en el destinatario porque estaba incompleto o su formato era incorrecto.|
|-2016345701|0x87D1019B|Syncml(411): información de longitud o tamaño de bytes en el tipo de elemento Meta debe acompañar al comando solicitado.|
|-2016345702|0x87D1019A|Syncml(410): el destino solicitado ya no está en el destinatario y no se conoce ningún URI de reenvío.|
|-2016345703|0x87D10199|Syncml(409): error de solicitud porque se produjo un conflicto de actualizaciones entre las versiones de datos de cliente y servidor.|
|-2016345704|0x87D10198|Syncml(408): no se recibió un mensaje previsto en el periodo de tiempo necesario.|
|-2016345705|0x87D10197|Syncml(407): error del comando solicitado debido a que el originador debe proporcionar la autenticación correcta.|
|-2016345706|0x87D10196|Syncml(406): error del comando solicitado porque una característica opcional en la solicitud no se admite.|
|-2016345707|0x87D10195|Syncml(405): el comando solicitado no se admite en el destino.|
|-2016345708|0x87D10194|Syncml(404): el destino solicitado no se encontró.|
|-2016345709|0x87D10193|Syncml(403): error del comando solicitado, pero el destinatario entendió el comando solicitado.|
|-2016345710|0x87D10192|Syncml(402): error del comando solicitado porque es preciso realizar el pago correspondiente.|
|-2016345711|0x87D10191|Syncml(401): error del comando solicitado porque el solicitante debe proporcionar la autenticación correcta.|
|-2016345712|0x87D10190|Syncml(400): el comando solicitado no se pudo realizar porque el formato de la sintaxis del comando es incorrecto.|
|-2016345807|0x87D10131|Syncml(305): se debe obtener acceso al destino solicitado mediante el proxy de URI especificado.|
|-2016345808|0x87D10130|Syncml(304): el comando SyncML solicitado no se ejecutó en el destino.|
|-2016345809|0x87D1012F|Syncml(303): el destino solicitado se puede encontrar en otro URI.|
|-2016345810|0x87D1012E|Syncml(302): el destino solicitado se ha movido temporalmente a otro URI.|
|-2016345811|0x87D1012D|Syncml(301): el destino solicitado tiene un nuevo URI.|
|-2016345812|0x87D1012C|Syncml(300): el destino solicitado es uno de varios destinos solicitados alternativos.|
|-2016345896|0x87D100D8|Syncml(216): error de Atomic debido a un comando que estaba dentro del elemento Atomic. El comando se revirtió correctamente.|
|-2016345897|0x87D100D7|Syncml(215): no se ejecutó un comando debido a la interacción del usuario, que decidió no aceptar la elección.|
|-2016345898|0x87D100D6|Syncml(214): operación cancelada. El comando SyncML se realizó correctamente, pero no se procesarán más comandos en esta sesión.|
|-2016345899|0x87D100D5|Syncml(213): se aceptó y se almacenó en búfer el elemento fragmentado.|
|-2016345900|0x87D100D4|Syncml(212): autenticación aceptada; no será necesario autenticarse de nuevo durante el resto de la sesión de sincronización. Este código de respuesta solo se puede usar para responder a una solicitud en la que se proporcionan credenciales.|
|-2016345901|0x87D100D3|Syncml(211): elemento no eliminado. No se encontró el elemento solicitado. Es posible que se haya eliminado previamente.|
|-2016345902|0x87D100D2|Syncml(210): eliminación sin archivar. La respuesta indica que los datos solicitados se eliminaron correctamente pero que no se archivaron antes de su eliminación porque esta característica OPCIONAL no es compatible con la implementación.|
|-2016345903|0x87D100D1|conflicto resuelto con duplicado. La respuesta indica que la solicitud generó un conflicto de actualización que se resolvió con una duplicación de los datos del cliente que se estaban creando en la base de datos del servidor. La respuesta incluye el URI de destino del duplicado en el elemento del estado. Además, en el caso de una sincronización bidireccional, se devuelve un comando Add con la definición de datos duplicados.|
|-2016345904|0x87D100D0|conflicto resuelto a favor del comando del cliente. La respuesta indica que se produjo un conflicto de actualización que se resolvió a favor del comando del cliente.|
|-2016345905|0x87D100CF|conflicto resuelto con combinación. La respuesta indica que la solicitud ha generado un conflicto que se ha resuelto con la combinación de las instancias de datos del cliente y del servidor. La respuesta incluye las URL de destino y origen del elemento de estado. Además, se devuelve un comando Replace con los datos combinados.|
|-2016345906|0x87D100CE|la respuesta indica que solo se completó parte del comando. Si el resto del comando se puede completar más tarde, una vez que finalice se DEBE crear un código apropiado de estado de solicitud de finalización.|
|-2016345907|0x87D100CD|el origen DEBE actualizar su contenido. Se informa al originador de la solicitud de que su contenido DEBE sincronizarse para obtener una versión actualizada.|
|-2016345908|0x87D100CC|la solicitud se completó correctamente, pero no se devolvieron datos. El código de respuesta también se devuelve como respuesta a un comando Get cuando el destino carece de contenido.|
|-2016345909|0x87D100CB|respuesta no autoritativa. La entidad que responde a la solicitud no es la de destino. La respuesta solo se devolverá cuando la solicitud genere un código de respuesta 200 por parte del destino autoritativo.|
|-2016345910|0x87D100CA|aceptado para procesamiento. La solicitud para ejecutar una aplicación de forma remota o para alertar a un usuario o aplicación se realizó correctamente.|
|-2016345911|0x87D100C9|se agregó el elemento solicitado.|
|-2016345912|0x87D100C8|el comando SyncML se realizó correctamente.|
|-2016346011|0x87D10065|el comando SyncML se está realizando, pero todavía no ha finalizado.|

### Pasos siguientes
Si esta información para solucionar problemas no le ha ayudado, póngase en contacto con el servicio de soporte técnico de Microsoft como se indica en [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico de Microsoft Intune).



<!--HONumber=Aug16_HO1-->


