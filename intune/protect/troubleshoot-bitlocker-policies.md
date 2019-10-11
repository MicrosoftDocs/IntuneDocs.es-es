---
title: Sugerencias para la solución de problemas de las directivas de BitLocker en Microsoft Intune
titleSuffix: Microsoft Intune
description: Describe cómo habilitar el cifrado de BitLocker en un dispositivo mediante la Directiva de Intune y cómo comprobar que la Directiva se implementó correctamente en un dispositivo.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 197ad888dc8a07cc35efbaec538fde93c76c81c3
ms.sourcegitcommit: f04e21ec459998922ba9c7091ab5f8efafd8a01c
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71817630"
---
# <a name="troubleshoot-bitlocker-policies-in-microsoft-intune"></a>Solucionar problemas de directivas de BitLocker en Microsoft Intune

Este artículo puede ayudar a los administradores de Intune a entender cómo los dispositivos Windows 10 configuran BitLocker en función de la Directiva de Intune. En este artículo también se proporcionan instrucciones sobre cómo solucionar problemas con la configuración de BitLocker en los dispositivos que administra con Intune.  

## <a name="understanding-bitlocker"></a>Descripción de BitLocker

El cifrado de unidad BitLocker es un servicio ofrecido por los sistemas operativos de Microsoft Windows que permite a los usuarios cifrar datos en sus discos duros. BitLocker admite el cifrado de unidades de sistema operativo, unidades de medios extraíbles y unidades de datos fijas. BitLocker también admite el uso de cifrado de 256 bits para mejorar la protección de los datos confidenciales.  

Con Microsoft Intune, tiene los siguientes métodos para administrar BitLocker en dispositivos Windows 10:

- **Directivas de configuración de dispositivos** : algunas opciones de directiva integrada están disponibles en la consola de administración de Intune en **configuración de dispositivo** > **Endpoint Protection** **Directiva de cifrado de Windows** > . Puede encontrar todos los conmutadores y características disponibles aquí: [cifrado de Windows](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption).

- **Líneas base de seguridad** -  las[líneas de base de seguridad](security-baselines.md) son grupos conocidos de configuración y valores predeterminados recomendados por el equipo de seguridad relevante para ayudar a proteger los dispositivos Windows. Distintos orígenes de línea base, como la línea de base de *seguridad de MDM* o la línea de base de *ATP de Microsoft defender* , pueden administrar la misma configuración que la otra. También pueden administrar la misma configuración que administra con las directivas de configuración de dispositivos. 

Además de Intune, es posible que la configuración de BitLocker esté administrada por otros medios, como directiva de grupo, o que un usuario del dispositivo establezca manualmente.

Independientemente de la configuración que se aplique a un dispositivo, las directivas de BitLocker hacen uso del [CSP de BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) para configurar el cifrado en el dispositivo. El CSP de BitLocker está integrado en Windows y cuando Intune implementa una directiva de BitLocker en un dispositivo asignado, es el CSP de BitLocker en el dispositivo que escribe los valores adecuados en el registro de Windows para que la configuración de la Directiva surta efecto.

Si desea obtener más información acerca de BitLocker, consulte los recursos siguientes.

- [BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [Información general de BitLocker y preguntas más frecuentes](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview-and-requirements-faq)

Ahora que tiene una descripción general de lo que hacen estas directivas y cómo funcionan, consulte Cómo puede comprobar si la configuración de BitLocker se aplica correctamente a un cliente de Windows.

## <a name="verify-the-source-of-bitlocker-settings"></a>Comprobar el origen de la configuración de BitLocker

Al investigar un problema de BitLocker en un dispositivo Windows 10, es importante determinar primero si el problema está relacionado con Intune o con Windows. Una vez conocido el posible origen de errores, puede centrar sus esfuerzos de solución de problemas en el lugar adecuado y, si es necesario, obtener soporte técnico del equipo correcto.  

Como primer paso, determine si la Directiva de Intune se ha implementado correctamente en el dispositivo de destino. En el ejemplo siguiente, tiene una directiva de configuración de dispositivo que implementa la configuración de cifrado de Windows (BitLocker), como se muestra a continuación: 

![Directiva de configuración de dispositivos de cifrado de Windows con la configuración](./media/troubleshooting-bitlocker-policies/settings.png)

¿Cómo se confirma que se ha aplicado la configuración al dispositivo de destino? A continuación se indican algunas formas de hacerlo.

### <a name="device-configuration-policy-device-status"></a>Estado del dispositivo de directiva de configuración de dispositivos  

Al usar la Directiva de configuración de dispositivos para configurar BitLocker, puede comprobar el estado de la Directiva en el portal de Intune. En el portal, vaya a **configuración de dispositivo** > **perfiles** > seleccione el perfil que contiene la configuración de BitLocker y, a continuación, seleccione **Estado del dispositivo**. Los dispositivos asignados al perfil aparecen en la lista y la columna *Estado del dispositivo* indica si un dispositivo ha implementado correctamente el perfil. 

Recuerde que puede haber un retraso entre un dispositivo que recibe una directiva de BitLocker y que la unidad está totalmente cifrada.  

 
### <a name="use-control-panel-on-the-client"></a>Usar el panel de control en el cliente  

En un dispositivo que ha habilitado BitLocker y cifrado una unidad, puede ver el estado de BitLocker desde un panel de control de dispositivos. En el dispositivo, abra el **Panel de Control** > **sistema y seguridad** > **cifrado de unidad BitLocker**. La confirmación aparece como se muestra en la siguiente imagen.  

![BitLocker está activado en el panel de control](./media/troubleshooting-bitlocker-policies/control-panel.png)

### <a name="use-a-command-prompt"></a>Uso de un símbolo del sistema  

En un dispositivo que haya habilitado BitLocker y que haya cifrado una unidad, inicie el símbolo del sistema con credenciales de administrador y, a continuación, ejecute `manage-bde -status`. Los resultados deberían ser similares al ejemplo siguiente:  
![A resultado del comando de estado](./media/troubleshooting-bitlocker-policies/command.png)

En el ejemplo: 
- La **protección de BitLocker** está **activada**,  
- El **porcentaje cifrado** es **100%**  
- El **método de cifrado** es **XTS-AES 256**.  

También puede comprobar los **protectores de clave** mediante la ejecución del siguiente comando:

```cmd
Manage-bde -protectors -get c:
```

O bien con PowerShell:

```powershell
Confirm-SecureBootUEFI
```

### <a name="review-the-devices-registry-key-configuration"></a>Revisar la configuración de la clave del registro de dispositivos   

Una vez que la Directiva de BitLocker se implementa correctamente en un dispositivo, consulte la siguiente clave del registro en el dispositivo, donde puede revisar la configuración de la configuración de BitLocker: *HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\current\device\BitLocker* . Este podría ser un ejemplo:

![Clave del registro de BitLocker](./media/troubleshooting-bitlocker-policies/registry.png)

Estos valores los configura el CSP de BitLocker. Compruebe que los valores de las claves coinciden con los valores especificados en el origen de la Directiva de cifrado de Windows de Intune. Para obtener más información sobre cada una de estas opciones, consulte [CSP de BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

> [!NOTE]
> La Visor de eventos de Windows también contendrá diversa información relacionada con BitLocker. Hay demasiados para enumerar aquí, pero la búsqueda de la **API de BitLocker** le proporcionará una gran cantidad de información útil.

### <a name="check-the-mdm-diagnostics-report"></a>Comprobación del informe de diagnóstico de MDM  

En un dispositivo que tenga habilitado BitLocker, puede generar y ver un informe de diagnóstico de MDM desde el dispositivo de destino para confirmar que la Directiva de BitLocker está presente. Si puede ver la configuración de la Directiva en el informe, es otra indicación de que la Directiva se implementó correctamente. El vídeo de *Microsoft ayuda* en el siguiente vínculo explica cómo capturar un informe de diagnóstico de MDM desde un dispositivo Windows. 

> [!VIDEO https://www.youtube.com/embed/WKxlcjV4TNE]

Al analizar el informe de diagnóstico de MDM, el contenido puede parecer un poco confuso al principio. A continuación se muestra un ejemplo que muestra cómo poner en correlación lo que hay en el informe con la configuración de una directiva:

![Ejemplo de informe de diagnóstico de MDM](./media/troubleshooting-bitlocker-policies/report.png)

El resultado de salida muestra los valores que corresponden a los valores de la Directiva de BitLocker:

![Resultado de salida muestra los valores ](./media/troubleshooting-bitlocker-policies/output.png)

Resultados de salida de diagnóstico de MDM:

```asciidoc
EncryptionMethodWithXtsOsDropDown: 7 (The value 7 refers to the 256 bit encryption)
EncryptionMethodWithXtsFdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
EncryptionMethodWithXtsRdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
```

Puede hacer referencia a la [documentación de BITLOCKER CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) para ver el significado de cada valor. En este ejemplo, se comparte un fragmento de código en la siguiente imagen.

![Propósitos de los valores](./media/troubleshooting-bitlocker-policies/shared-example.png)

 Del mismo modo, puede ver todos los valores y comprobarlos desde el vínculo CSP de BitLocker.

> [!TIP]
> El propósito principal del informe de diagnóstico de MDM es ayudar a Soporte técnico de Microsoft a la hora de solucionar problemas. Si abre un caso de soporte técnico para Intune y el problema implica a los clientes de Windows, siempre es una buena idea recopilar este informe e incluirlo en la solicitud de soporte técnico.

## <a name="troubleshooting-bitlocker-policy"></a>Solución de problemas de la Directiva de BitLocker

Ahora debería tener una buena idea de cómo confirmar que Intune ha implementado correctamente la Directiva de BitLocker, que desaprovecha la configuración de BitLocker en el CSP de BitLocker en WIndows.  

**La Directiva no puede acceder al dispositivo** : cuando la Directiva de Intune no está presente en ninguna capacidad:  
- **¿El dispositivo está inscrito correctamente en Microsoft Intune?** Si no es así, deberá solucionarlo antes de solucionar cualquier problema específico de la Directiva. Puede encontrar ayuda para solucionar problemas de inscripción de Windows [aquí](../enrollment/troubleshoot-windows-enrollment-errors.md).  
- **¿Hay una conexión de red activa en el dispositivo?** Si el dispositivo está en modo de avión o desactivado, o si el usuario tiene el dispositivo en una ubicación sin servicio, la Directiva no se entregará ni se aplicará hasta que se restaure la conectividad de red.  
- **¿La Directiva de BitLocker se implementó en el grupo de usuarios o dispositivos correcto?** Compruebe que el usuario o el dispositivo correcto es miembro de los grupos de destino.  

La **Directiva está presente pero no toda la configuración se configuró correctamente** : cuando la Directiva de Intune llega al dispositivo, pero no se establecen todas las configuraciones:  
- **¿Se produce un error en la implementación de toda la Directiva o se trata solo de algunas opciones que no se aplican?** Si ve que se enfrenta a un escenario en el que solo no se aplican algunas configuraciones de Directiva, compruebe las siguientes consideraciones:

  1. **No todas las configuraciones de BitLocker se admiten en todas las versiones de Windows**.  
  La Directiva se refiere a un dispositivo como una sola unidad, por lo que si se aplican algunas opciones de configuración y otras no, puede estar seguro de que se recibe la propia Directiva. En este escenario, es posible que la versión de Windows del dispositivo no admita la configuración problemática. Consulte [CSP de BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) en la documentación de Windows para obtener más información sobre los requisitos de versión de cada opción.  

  1. **BitLocker no se admite en todo el hardware**.  
  Incluso si tiene la versión correcta de Windows, es posible que el hardware del dispositivo subyacente no cumpla los requisitos del cifrado de BitLocker. Puede encontrar los [requisitos del sistema para BitLocker (https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements) en la documentación de Windows, pero lo principal que debe comprobar es que el dispositivo tiene un chip TPM compatible (1,2 o posterior) y un BIOS compatible con Trusted Computing Group (TCG) o firmware UEFI.

**Ejemplo de investigación** : puede implementar una directiva de BitLocker en un dispositivo de Windows 10 y la configuración **cifrar dispositivos** muestra un estado de **error** en el portal.

- Como sugiere su nombre, esta configuración permite a un administrador requerir que el cifrado se active mediante el *cifrado de dispositivo > BitLocker*. Con las sugerencias de solución de problemas que se mencionan anteriormente, primero se comprueba el informe de diagnóstico de MDM. El informe confirma que se ha implementado la Directiva correcta en el dispositivo:

  ![El informe confirma que la Directiva correcta está implementada en el dispositivo](./media/troubleshooting-bitlocker-policies/mdm-report.png)

- También se comprueba que la operación se ha realizado correctamente en el registro:

  ![El valor del registro RequiredDeviceEncryption muestra 1](./media/troubleshooting-bitlocker-policies/registry-confirm.png)

- A continuación, compruebe el estado de TPM con PowerShell y busque que TPM no está disponible en el dispositivo:

  ![Estado de TPM activado mediante PowerShell](./media/troubleshooting-bitlocker-policies/tpm-command.png)

- Dado que BitLocker se basa en TPM, podría concluir que BitLocker no genera un error debido a un problema con Intune o la Directiva, pero en lugar de que el dispositivo no tenga un chip TPM o TPM esté deshabilitado en el BIOS.

  Como sugerencia adicional, puede confirmar lo mismo en el Visor de eventos de Windows en el **registro de aplicaciones y servicios** > **Windows** > **API de BitLocker**. En el registro de eventos de la **API de BitLocker** , encontrará un identificador de evento 853 que significa que TPM no está disponible:

  ![Id. de evento 853](./media/troubleshooting-bitlocker-policies/event-error.png)

  > [!NOTE]
  > También puede comprobar el estado de TPM ejecutando **TPM. msc** en el dispositivo.



## <a name="summary"></a>Resumen

Al solucionar problemas de directivas de BitLocker con Intune y puede confirmar que la Directiva alcanza el dispositivo previsto, es seguro asumir que el problema no está directamente relacionado con Intune. Lo más probable es que el problema esté relacionado con el sistema operativo Windows o el hardware. En este caso, empiece a buscar en otras áreas, como la configuración de TPM o UEFI y el arranque seguro.

<!-- Unable to Verify this: 
You can try to isolate the issue by enabling BitLocker manually. If you can turn on BitLocker manually, Intune won't be able to turn it on through policy. Also, the Windows Recovery Environment (WinRE) must be enabled on the client for BitLocker to work. When organizations use using custom images, WinRE is a common cause that is often overlooked. 
-->

## <a name="next-steps"></a>Pasos siguientes  

A continuación se muestran más recursos que pueden ayudar al trabajar con BitLocker:

- [Documentación del producto de BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [Requisitos del sistema de BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements)
- [Preguntas más frecuentes sobre BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions)
- [Documentación de BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)
- [Configuración de directivas de cifrado de Windows de Intune](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)
- [Cifrado automático de BitLocker de hardware independiente mediante AAD/MDM](https://blogs.technet.microsoft.com/home_is_where_i_lay_my_head/2017/06/07/hardware-independent-automatic-bitlocker-encryption-using-aadmdm/)
- [Directiva de CSP para el cifrado de BitLocker en dispositivos piloto automáticos](https://techcommunity.microsoft.com/t5/Windows-10-security/CSP-policy-for-bitLocker-encryption-on-autopilot-devices/m-p/284537)
- [Tutorial para crear e implementar una directiva de BitLocker con Intune](https://blogs.technet.microsoft.com/cbernier/2017/07/11/windows-10-intune-windows-bitlocker-management-yes/)