---
title: Configuración de las líneas de base de seguridad de Intune para Microsoft Edge
titleSuffix: Microsoft Intune
description: Configuración de línea de base de seguridad compatible con Intune para administrar el explorador de Microsoft Edge
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/30/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8f4e56340d871ea5e0bcec7e541a418c32d021d0
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73415651"
---
# <a name="microsoft-edge-baseline-settings-for-intune"></a>Configuración de línea de base de Microsoft Edge para Intune

Vea la configuración de línea de base del explorador Web de Microsoft Edge compatible con Microsoft Intune. Los valores predeterminados de la línea de base de Microsoft Edge representan la configuración recomendada para los exploradores de Microsoft Edge y es posible que no coincidan con los valores predeterminados de línea de base de seguridad.

> [!NOTE]
> La línea de base de Microsoft Edge está en versión preliminar pública. 

## <a name="microsoft-edge"></a>Microsoft Edge

- **Impedir la omisión de mensajes de SmartScreen de Microsoft defender para sitios**  
  **Valor predeterminado**: Habilitado  
  CSP de Microsoft Edge: [Browser/PreventSmartScreenPromptOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)

  Esta configuración de directiva permite decidir si los usuarios pueden invalidar las advertencias de SmartScreen de Microsoft defender sobre sitios Web potencialmente malintencionados. 
  - Si habilita esta opción, los usuarios no podrán omitir las advertencias de SmartScreen de Microsoft defender y no podrán continuar con el sitio. 
  - Si deshabilita o no establece esta configuración, los usuarios pueden omitir las advertencias de SmartScreen de Microsoft defender y continuar con el sitio.

- **Versión mínima de SSL habilitada**  
  **Valor predeterminado**: Habilitado  

  Establezca una versión mínima compatible de SSL. Si establece esta directiva en *no configurado*, Microsoft Edge usa una versión mínima predeterminada de *TLS 1,0*. Cuando se establece en *habilitado*, puede seleccionar una versión mínima de los siguientes valores:

  - TLS 1.0
  - TLS 1.1
  - TLS 1.2

  - **Versión mínima de SSL habilitada**  
    **Valor predeterminado**: TLS 1,2

- **Impedir la omisión de las advertencias de SmartScreen de Microsoft defender acerca de las descargas**  
  **Valor predeterminado**: Habilitado  
  CSP de Microsoft Edge: [Browser/PreventSmartScreenPromptOverrideForFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)  

  Esta directiva le permite determinar si los usuarios pueden invalidar las advertencias de SmartScreen de Microsoft defender sobre las descargas no comprobadas.
  - Si habilita esta Directiva, los usuarios de su organización no podrán omitir las advertencias de SmartScreen de Microsoft defender y se les impedirá que completen las descargas no comprobadas.
  - Si deshabilita o no configura esta Directiva, los usuarios pueden omitir las advertencias de SmartScreen de Microsoft defender y completar las descargas no comprobadas.

- **Permitir a los usuarios continuar desde la página de advertencia de SSL**  
  **Valor predeterminado**: Deshabilitado  
  CSP de Microsoft Edge: [Browser/PreventCertErrorOverrides](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventcerterroroverrides)  

  Microsoft Edge muestra una página de advertencia cuando los usuarios visitan sitios que tienen errores de SSL. Si establece esta directiva en *habilitado* o *no configurado*, los usuarios pueden hacer clic en estas páginas de advertencia. Cuando se *deshabilita*esta Directiva, se impide que los usuarios haga clic en cualquier página de advertencia. 

- **Configuración predeterminada de Adobe Flash**  
  **Valor predeterminado**: Habilitado  
  CSP de Microsoft Edge: [Browser/AllowFlash](https://docs.microsoft.coms/windows/client-management/mdm/policy-csp-browser#browser-allowflash)y [Browser/AllowFlashClickToRun](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowflashclicktorun)  

  Determina si los sitios web que no están incluidos en "PluginsAllowedForUrls" o "PluginsBlockedForUrls" pueden ejecutar automáticamente el complemento de Adobe Flash. 

  - Seleccione "BlockPlugins" para bloquear Adobe Flash en todos los sitios
  - Seleccione "ClickToPlay" para permitir la ejecución de Adobe Flash, pero solicite al usuario que haga clic en el marcador de posición para iniciarlo.
  
   En cualquier caso, las directivas ' PluginsAllowedForUrls ' y ' PluginsBlockedForUrls ' tienen prioridad sobre ' DefaultPluginsSetting '. La reproducción automática solo se permite para los dominios enumerados explícitamente en la Directiva "PluginsAllowedForUrls". 
   Si desea habilitar la reproducción automática para todos los sitios, considere la posibilidad de agregar http://* y https://* a esta lista. 
   
   - Si establece esta directiva en *no configurado*, el usuario puede cambiar esta configuración manualmente. * 2 = bloquear el complemento de Adobe Flash * 3 = Haga clic para reproducir la opción "1" anterior set allow-All, pero esta funcionalidad solo la controla la Directiva "PluginsAllowedForUrls". Las directivas existentes con "1" funcionarán en modo de hacer clic y reproducir.  
 
  - **Configuración predeterminada de Adobe Flash**  
    **Valor predeterminado**: bloquear el complemento de Adobe Flash

- **Habilitar el aislamiento de sitio para todos los sitios**  
  **Valor predeterminado**: Habilitado  

  La Directiva ' SitePerProcess ' se puede usar para impedir que los usuarios opten por el comportamiento predeterminado de aislar todos los sitios. También puede usar la Directiva IsolateOrigins para aislar orígenes adicionales más precisos.

  - Cuando esta Directiva se establece en *habilitado*, los usuarios no pueden rechazar el comportamiento predeterminado, donde cada sitio se ejecuta en su propio proceso. 
  - Si usa *deshabilitado* o *no configurado*, un usuario puede rechazar el aislamiento del sitio. (Por ejemplo, mediante el uso de la entrada "deshabilitar aislamiento de sitio" en edge://flags). Deshabilitar la Directiva o no configurar la Directiva no desactiva el aislamiento del sitio.

- **Esquemas de autenticación admitidos**  
  **Valor predeterminado**: Habilitado  

  Especifica los esquemas de autenticación HTTP que se admiten. Puede configurar la Directiva con estos valores: "Basic", "Digest", "NTLM" y "Negotiate". Separe varios valores con comas. Si no configura esta Directiva, se usan los cuatro esquemas.
 
  - **Esquemas de autenticación admitidos**  
    Seleccione entre las siguientes opciones: 
    - Básica
    - Implícita
    - NTLM *(seleccionado de forma predeterminada)*
    - Negociar *(seleccionado de forma predeterminada)*

- **Habilitar guardar contraseñas en el administrador de contraseñas**  
  **Valor predeterminado**: Deshabilitado  
  CSP de Microsoft Edge: [Browser/AllowPasswordManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowpasswordmanager)  

  Habilite Microsoft Edge para guardar las contraseñas de usuario. 
  - Si habilita esta Directiva, los usuarios pueden guardar sus contraseñas en Microsoft Edge. La próxima vez que visiten el sitio, Microsoft Edge introducirá la contraseña automáticamente. 
  - Si deshabilita esta Directiva, los usuarios no podrán guardar contraseñas nuevas, pero podrán seguir usando contraseñas guardadas anteriormente. 
  
  Cuando se establece esta directiva en *habilitado* o *deshabilitado*, los usuarios no pueden cambiar o invalidar esta directiva en Microsoft Edge. 
  
  Si establece esta opción en *no configurado*, los usuarios pueden guardar las contraseñas, así como desactivar esta característica.

- **Controlar qué extensiones no se pueden instalar**  
  **Valor predeterminado**: Habilitado  

  Enumerar las extensiones específicas que los usuarios no pueden instalar en Microsoft Edge. Cuando se implementa esta Directiva, se deshabilitan las extensiones de esta lista que se instalaron previamente y el usuario no podrá habilitarlas. Si quita un elemento de la lista de extensiones bloqueadas, esa extensión se vuelve a habilitar automáticamente en cualquier lugar en el que se haya instalado previamente.
  
  Use **\*** para bloquear todas las extensiones que no aparecen explícitamente en la lista de permitidos. Si esta Directiva se establece en *no configurado*, los usuarios pueden instalar cualquier extensión en Microsoft Edge. 
  
  Valor de ejemplo: extension_id1 extension_id2.  
  <br>
  - **Identificadores de extensión en los que se debe impedir que el usuario instale (o * para todos)**  
    Seleccione **Agregar** y especifique extensiones adicionales. **\*** está seleccionado de forma predeterminada.

- **Configuración de SmartScreen de Microsoft defender**  
  **Valor predeterminado**: Habilitado  
  CSP de Microsoft Edge: [Browser/AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)  
  
  Esta configuración de directiva le permite configurar si activar SmartScreen de Microsoft defender. SmartScreen de Microsoft defender proporciona mensajes de advertencia para ayudar a proteger a los usuarios frente a posibles estafas de suplantación de identidad (phishing) y software malintencionado. 
  
  - De forma predeterminada, SmartScreen de Microsoft defender está activado. Si habilita esta configuración, SmartScreen de Microsoft defender está activado y los usuarios no pueden desactivarlo.
  - Si deshabilita esta configuración, SmartScreen de Microsoft defender se desactiva y los usuarios no pueden activarlo. 
  - Cuando se establece en *no configurado*, los usuarios pueden elegir si desea usar SmartScreen de Microsoft defender. 
  
  Esta directiva solo está disponible en las instancias de Windows que están unidas a un dominio de Microsoft Active Director o en instancias de Windows 10 Pro o Enterprise que están inscritos para la administración de dispositivos.

- **Permitir hosts de mensajería nativa de nivel de usuario (instalados sin permisos de administrador)**  
  **Valor predeterminado**: Deshabilitado  

  Habilita la instalación de nivel de usuario de hosts de mensajería nativa. 
  - Si deshabilita esta Directiva, Microsoft Edge solo usará los hosts de mensajería nativa instalados en el nivel del sistema. De forma predeterminada, si no configura esta Directiva, Microsoft Edge permitirá el uso de hosts de mensajería nativa de nivel de usuario.

## <a name="next-steps"></a>Pasos siguientes

[Uso de líneas de base de seguridad en Intune](security-baselines.md)
