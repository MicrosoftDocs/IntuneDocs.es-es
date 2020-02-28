---
title: Sugerencias para la solución de problemas de directivas de BitLocker en Microsoft Intune
titleSuffix: Microsoft Intune
description: Aquí se explica cómo habilitar el cifrado de BitLocker en un dispositivo mediante una directiva de Intune y cómo comprobar que esta se ha implementado correctamente en un dispositivo.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/29/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f3b32268d0b04dee84a737b9a1c768bc4fab7202
ms.sourcegitcommit: 3964e6697b4d43e2c69a15e97c8d16f8c838645b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2020
ms.locfileid: "77556506"
---
# <a name="troubleshoot-bitlocker-policies-in-microsoft-intune"></a>Solución de problemas de directivas de BitLocker en Microsoft Intune

Este artículo puede ayudar a los administradores de Intune a entender cómo configuran BitLocker los dispositivos Windows 10 en función de una directiva de Intune. En él también se proporcionan instrucciones para solucionar problemas de configuración de BitLocker en los dispositivos administrados con Intune.  

## <a name="understanding-bitlocker"></a>Descripción de BitLocker

El cifrado de unidad BitLocker es un servicio ofrecido por los sistemas operativos Microsoft Windows que permite a los usuarios cifrar los datos de los discos duros. BitLocker admite el cifrado de unidades de sistema operativo, unidades de medios extraíbles y unidades de datos fijas. BitLocker también admite el uso de cifrado de 256 bits para una mejor protección de los datos confidenciales.  

Con Microsoft Intune, dispone de los siguientes métodos para administrar BitLocker en dispositivos Windows 10:

- **Directivas de configuración de dispositivos**: hay determinadas opciones de directivas integradas disponibles en Intune cuando se crea un perfil de configuración de dispositivo para administrar Endpoint Protection. Para encontrar estas opciones, debe [crear un perfil de dispositivo que contenga la configuración de Endpoint Protection](endpoint-protection-configure.md#create-a-device-profile-containing-endpoint-protection-settings), seleccionar **Windows 10 y versiones posteriores** como *Plataforma* y, luego, la categoría **Cifrado de Windows** como *Configuración*. 

   Puede obtener información sobre las opciones y características disponibles en: [Cifrado de Windows](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption).

- **Líneas base de seguridad**: las [líneas base de seguridad](security-baselines.md) son grupos conocidos de opciones y valores predeterminados que el equipo de seguridad correspondiente recomienda para ayudar a proteger los dispositivos Windows. Distintos orígenes de líneas base, como la *línea base de seguridad de MDM* o la *línea base de ATP de Microsoft Defender*, pueden administrar la misma configuración u otra distinta. También pueden administrar la misma configuración que administra con directivas de configuración de dispositivos. 

Además de Intune, para el hardware compatible con el modo de espera moderno y HSTI, cuando se usa cualquiera de estas características, el cifrado de dispositivos con BitLocker se activa automáticamente cada vez que el usuario une un dispositivo a Azure AD. Azure AD proporciona un portal en el que también se realiza una copia de seguridad de las claves de recuperación, para que los usuarios puedan recuperar su propia clave de recuperación para autoservicio, si es necesario.

Es posible que la configuración de BitLocker esté administrada por otros medios, como directivas de grupo, o que un usuario del dispositivo la establezca de forma manual.

Independientemente de cómo se aplique la configuración a un dispositivo, las directivas de BitLocker usan el [CSP de BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) para configurar el cifrado en el dispositivo. El CSP de BitLocker está integrado en Windows y, cuando Intune implementa una directiva de BitLocker en un dispositivo asignado, es el CSP de BitLocker del dispositivo el que escribe los valores adecuados en el Registro de Windows para que la configuración de la directiva surta efecto.

Si quiere obtener más información sobre BitLocker, vea los siguientes recursos:

- [BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [Preguntas más frecuentes sobre BitLocker y requisitos](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview-and-requirements-faq)

Ahora que comprende lo que hacen estas directivas y cómo funcionan, vea cómo puede comprobar si la configuración de BitLocker se aplica correctamente a un cliente Windows.

## <a name="verify-the-source-of-bitlocker-settings"></a>Comprobación del origen de la configuración de BitLocker

Al investigar un problema de BitLocker en un dispositivo Windows 10, es importante determinar en primer lugar si el problema está relacionado con Intune o con Windows. Una vez conocido el posible origen del error, se pueden centrar los esfuerzos de solución de problemas en el lugar adecuado y, si fuera necesario, obtener soporte técnico del equipo correcto.  

Como primer paso, determine si la directiva de Intune se ha implementado correctamente en el dispositivo de destino. En el ejemplo siguiente, tiene una directiva de configuración de dispositivo que implementa la configuración de cifrado de Windows (BitLocker), como se muestra:

![Directiva de configuración de dispositivo de cifrado de Windows con la configuración](./media/troubleshooting-bitlocker-policies/settings.png)

¿Cómo se confirma que se ha aplicado la configuración al dispositivo de destino? A continuación se indican algunas formas de hacerlo.

### <a name="device-configuration-policy-device-status"></a>Estado del dispositivo de la directiva de configuración de dispositivo  

Al usar la directiva de configuración de dispositivos para configurar BitLocker, puede comprobar el estado de la directiva en el portal de Intune.

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Seleccione **Dispositivos** > **Perfiles de configuración** y, luego, el perfil que contiene la configuración de BitLocker.

3. Después de seleccionar el perfil que quiere ver, seleccione **Estado del dispositivo**. Aparecen los dispositivos asignados al perfil y la columna *Estado del dispositivo* indica si un dispositivo ha implementado correctamente el perfil.

Recuerde que puede haber un retraso entre el momento de recepción de una directiva de BitLocker por parte de un dispositivo y el cifrado total de la unidad.  

### <a name="use-control-panel-on-the-client"></a>Uso del Panel de control en el cliente  

En un dispositivo que ha habilitado BitLocker y ha cifrado una unidad, puede ver el estado de BitLocker desde el Panel de control del dispositivo. En el dispositivo, abra **Panel de control** > **Sistema y seguridad** > **Cifrado de unidad BitLocker**. Aparece una confirmación, como se muestra en la siguiente imagen.  

![BitLocker activado en el Panel de control](./media/troubleshooting-bitlocker-policies/control-panel.png)

### <a name="use-a-command-prompt"></a>Uso de un símbolo del sistema  

En un dispositivo que ha habilitado BitLocker y ha cifrado una unidad, inicie el símbolo del sistema con credenciales de administrador y ejecute `manage-bde -status`. El resultado debería ser similar al ejemplo siguiente:  
![Resultado del comando status](./media/troubleshooting-bitlocker-policies/command.png)

En el ejemplo:

- La **protección de BitLocker** está **activada**.
- El **porcentaje cifrado** es del **100 %** .
- El **método de cifrado** es **XTS-AES 256**.

También puede comprobar los **protectores de clave** ejecutando el siguiente comando:

```cmd
Manage-bde -protectors -get c:
```

O bien con PowerShell:

```powershell
Confirm-SecureBootUEFI
```

### <a name="review-the-devices-registry-key-configuration"></a>Revisión de la configuración de la clave del Registro de dispositivos

Una vez que la directiva de BitLocker se implementa correctamente en un dispositivo, vea la siguiente clave del Registro en el dispositivo, donde puede revisar la configuración de BitLocker:  *HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\current\device\BitLocker*. Este podría ser un ejemplo:

![Clave del Registro de BitLocker](./media/troubleshooting-bitlocker-policies/registry.png)

Estos valores los configura el CSP de BitLocker. Compruebe que los valores de las claves coinciden con los especificados en el origen de la directiva de cifrado de Windows de Intune. Para obtener más información sobre cada uno de estos valores, vea [CSP de BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

> [!NOTE]
> El Visor de eventos de Windows también contiene diversa información relacionada con BitLocker. Hay demasiada para enumerarla aquí, pero, si busca **API de BitLocker**, encontrará una gran cantidad de información de utilidad.

### <a name="check-the-mdm-diagnostics-report"></a>Comprobación del informe de diagnóstico de MDM

En un dispositivo que tenga habilitado BitLocker, puede generar y ver un informe de diagnóstico de MDM del dispositivo de destino para confirmar que la directiva de BitLocker está presente. Si puede ver la configuración de la directiva en el informe, es otra indicación de que esta se ha implementado correctamente. El vídeo *Microsoft Helps* del siguiente vínculo explica cómo capturar un informe de diagnóstico de MDM desde un dispositivo Windows.

> [!VIDEO https://www.youtube.com/embed/WKxlcjV4TNE]

Al analizar el informe de diagnóstico de MDM, el contenido puede parecer un poco confuso al principio. A continuación hay un ejemplo que muestra cómo poner en correlación el contenido del informe con la configuración de una directiva:

![Ejemplo de informe de diagnóstico de MDM](./media/troubleshooting-bitlocker-policies/report.png)

El resultado muestra los valores que corresponden a los de la directiva de BitLocker:

![Resultado que muestra los valores ](./media/troubleshooting-bitlocker-policies/output.png)

Resultados de diagnóstico de MDM:

```asciidoc
EncryptionMethodWithXtsOsDropDown: 7 (The value 7 refers to the 256 bit encryption)
EncryptionMethodWithXtsFdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
EncryptionMethodWithXtsRdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
```

Puede ir a la [documentación del CSP de BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) para ver qué significa cada valor. En este ejemplo se comparte un fragmento de código en la siguiente imagen.

![Propósitos de los valores](./media/troubleshooting-bitlocker-policies/shared-example.png)

Del mismo modo, puede ver todos los valores y comprobarlos desde el vínculo del CSP de BitLocker.

> [!TIP]
> El propósito principal del informe de diagnóstico de MDM es ayudar al equipo de soporte técnico de Microsoft a la hora de solucionar problemas. Si abre un caso de soporte técnico de Intune y el problema afecta a clientes Windows, siempre es buena idea recopilar este informe e incluirlo en la solicitud de soporte técnico.

## <a name="troubleshooting-bitlocker-policy"></a>Solución de problemas de la directiva de BitLocker

Ahora debería tener una buena idea de cómo confirmar que Intune ha implementado correctamente la directiva de BitLocker, que traspasa la configuración de BitLocker al CSP de BitLocker en Windows.

**La directiva no llega al dispositivo**: cuando la directiva de Intune no está presente en ninguna capacidad:

- **¿El dispositivo está inscrito correctamente en Microsoft Intune?** Si no es así, debe solucionarlo antes de solucionar cualquier problema específico de la directiva. Puede encontrar ayuda para solucionar problemas de inscripción de Windows [aquí](../enrollment/troubleshoot-windows-enrollment-errors.md).

- **¿Hay una conexión de red activa en el dispositivo?** Si el dispositivo está en modo avión o desactivado, o si el usuario lo tiene en una ubicación sin servicio, la directiva no se entrega ni se aplica hasta que se restaura la conectividad de red.

- **¿La directiva de BitLocker se ha implementado en el grupo de usuarios o dispositivos correcto?** Compruebe que el usuario o dispositivo correcto es miembro de los grupos de destino.

**La directiva está presente, pero no todos los valores se han configurado correctamente**: cuando la directiva de Intune llega al dispositivo, pero no se ha establecido toda la configuración:

- **¿El error afecta a la implementación de toda la directiva o son solo algunas opciones las que no se aplican?** Si se enfrenta a un escenario en el que no se aplican únicamente algunas opciones de la directiva, compruebe las siguientes consideraciones:

  1. **No todas las opciones de BitLocker se admiten en todas las versiones de Windows**.
     La directiva llega a un dispositivo como una sola unidad, por lo que si se aplican algunas opciones y otras no, puede tener la certeza de que se ha recibido. En este escenario, es posible que la versión de Windows del dispositivo no admita la opción problemática. Vea [CSP de BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) en la documentación de Windows para obtener más información sobre los requisitos de versión de cada opción.

  2. **BitLocker no se admite en todo el hardware**.
     Aunque tenga la versión correcta de Windows, es posible que el hardware del dispositivo subyacente no cumpla los requisitos de cifrado de BitLocker. Puede encontrar los [requisitos del sistema de BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements) en la documentación de Windows, pero lo principal que debe comprobar es que el dispositivo tenga un chip TPM compatible (1.2 o posterior) y un firmware UEFI o BIOS compatible con Trusted Computing Group (TCG).
     
El **cifrado de BitLocker no se realiza de forma silenciosa**: ha configurado una directiva de Endpoint Protection con la opción "Advertencia para otro cifrado de disco" establecida en bloquear, y el asistente para cifrado sigue apareciendo:

- **Confirmar que la versión de Windows admite el cifrado silencioso**: esto requiere la versión mínima 1803. Si el usuario no es un administrador del dispositivo, se requiere la versión mínima 1809. Además, la versión 1809 agrega compatibilidad con dispositivos que no admiten el modo de espera moderno.

El **dispositivo cifrado con BitLocker se muestra como no compatible con las directivas de cumplimiento de Intune**: el problema se produce cuando el cifrado de BitLocker no finaliza. En función de factores como el tamaño del disco, el número de archivos y la configuración de BitLocker, el cifrado de BitLocker puede tardar mucho tiempo. Una vez completado el cifrado, el dispositivo se mostrará como compatible. Los dispositivos también pueden dejar de ser compatibles temporalmente justo después de una instalación reciente de actualizaciones de Windows.

**Los dispositivos se cifran con un algoritmo de 128 bits cuando la directiva especifica 256 bits**: de forma predeterminada, Windows 10 cifrará una unidad con el cifrado XTS-AES de 128 bits. Vea esta guía para [establecer el cifrado de 256 bits para BitLocker durante Autopilot](https://techcommunity.microsoft.com/t5/intune-customer-success/setting-256-bit-encryption-for-bitlocker-during-autopilot-with/ba-p/323791#).


**Ejemplo de investigación**

- Al implementar una directiva de BitLocker en un dispositivo Windows 10, la opción **Cifrar los dispositivos** muestra un estado de **Error** en el portal.

- Como su propio nombre sugiere, esta opción permite a un administrador exigir que el cifrado se active mediante *BitLocker > Cifrado del dispositivo*. Con las sugerencias de solución de problemas mencionadas anteriormente, primero se comprueba el informe de diagnóstico de MDM. El informe confirma que se ha implementado la directiva correcta en el dispositivo:

  ![Informe que confirma que la directiva correcta se ha implementado en el dispositivo](./media/troubleshooting-bitlocker-policies/mdm-report.png)

- También se comprueba que la operación se ha realizado correctamente en el Registro:

  ![Valor del Registro RequiredDeviceEncryption que muestra 1](./media/troubleshooting-bitlocker-policies/registry-confirm.png)

- Luego, se comprueba el estado de TPM con PowerShell y se detecta que TPM no está disponible en el dispositivo:

  ![Estado de TPM comprobado mediante PowerShell](./media/troubleshooting-bitlocker-policies/tpm-command.png)

- Dado que BitLocker se basa en TPM, se podría concluir que BitLocker no experimenta un error debido a un problema con Intune o la directiva, sino que el propio dispositivo no tiene un chip TPM o TPM está deshabilitado en el BIOS.

  Como sugerencia adicional, puede confirmar lo mismo en el Visor de eventos de Windows en **Registros de aplicaciones y servicios** > **Microsoft** > **Windows** > **BitLocker API**. En el registro de eventos de **BitLocker API** hay un identificador de evento 853 que significa que TPM no está disponible:

  ![Id. de evento 853](./media/troubleshooting-bitlocker-policies/event-error.png)

  > [!NOTE]
  > También puede comprobar el estado de TPM ejecutando **tpm.msc** en el dispositivo.

## <a name="summary"></a>Resumen

Al solucionar problemas de directivas de BitLocker con Intune y confirmar que una directiva llega al dispositivo previsto, se puede asumir que el problema no está directamente relacionado con Intune. Lo más probable es que el problema esté relacionado con el sistema operativo Windows o el hardware. En este caso, empiece a buscar en otras áreas, como la configuración de TPM o UEFI y el arranque seguro.

## <a name="next-steps"></a>Pasos siguientes  

A continuación se ofrecen más recursos que pueden ayudar al trabajar con BitLocker:

- [Documentación del producto BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [Requisitos del sistema de BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements)
- [Preguntas más frecuentes sobre BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions)
- [Documentación del CSP de BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)
- [Configuración de directivas de cifrado de Windows de Intune](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)
- [Cifrado automático de BitLocker independiente del hardware mediante AAD/MDM](https://blogs.technet.microsoft.com/home_is_where_i_lay_my_head/2017/06/07/hardware-independent-automatic-bitlocker-encryption-using-aadmdm/)
- [Directiva de CSP para el cifrado de BitLocker en dispositivos Auto Pilot](https://techcommunity.microsoft.com/t5/Windows-10-security/CSP-policy-for-bitLocker-encryption-on-autopilot-devices/m-p/284537)
- [Tutorial para crear e implementar una directiva de BitLocker con Intune](https://blogs.technet.microsoft.com/cbernier/2017/07/11/windows-10-intune-windows-bitlocker-management-yes/)
