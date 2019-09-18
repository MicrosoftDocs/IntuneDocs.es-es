---
title: Informe de cifrado para dispositivos cifrados en Microsoft Intune
titleSuffix: Microsoft Intune
description: Vea un informe sobre el estado de cifrado del dispositivo iOS o Windows y acceda a las claves de recuperación de BitLocker y FileVault desde el portal de Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 469bdc54385f943fd0c42ccfd921293970b03b64
ms.sourcegitcommit: 05139901411d14a85c2340c0ebae02d2c178a851
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70905039"
---
# <a name="monitor-device-encryption-with-intune"></a>Supervisión del cifrado de dispositivos con Intune   

El informe de cifrado de Microsoft Intune es una ubicación centralizada para ver los detalles sobre el estado de cifrado de un dispositivo y buscar opciones para administrar las claves de recuperación del mismo. Las opciones de clave de recuperación disponibles dependen del tipo de dispositivo que se está viendo.  

Para encontrar el informe, inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) y vaya a **Configuración del dispositivo**. Después, en *Supervisión*, seleccione **Informe de cifrado**.  

## <a name="view-encryption-details"></a>Visualización de detalles de cifrado  

El informe de cifrado muestra detalles comunes en los dispositivos compatibles que se administran. En las secciones siguientes se proporcionan detalles sobre la información que Intune presenta en el informe.  
 
### <a name="prerequisites"></a>Requisitos previos:  

El informe de cifrado admite la generación de informes en los dispositivos que ejecutan las versiones siguientes de sistema operativo:  
- macOS 10.13 o posterior  
- Windows, versión 1607 o posterior  

### <a name="report-details"></a>Detalles del informe  

En el panel de informe de cifrado se muestra una lista de los dispositivos que se administran con detalles de alto nivel sobre dichos dispositivos. Puede seleccionar un dispositivo de la lista para profundizar y ver detalles adicionales en el panel [Estado de cifrado del dispositivo](#device-encryption-status).  

- **Nombre de dispositivo**: representa el nombre del dispositivo.  
- **SO**: contiene la plataforma del dispositivo, como Windows o macOS.  
- **Versión del SO**: versión de Windows o macOS del dispositivo.  
- **Versión de TPM**: *(se aplica solo a Windows 10)* : versión del chip del Módulo de plataforma segura (TPM) en el dispositivo Windows 10.  
- **Preparación del cifrado**: evaluación de la preparación de los dispositivos para admitir una tecnología de cifrado aplicable, como el cifrado de BitLocker o FileVault. Los dispositivos se identifican de la siguiente manera:  
  - **Listo**: el dispositivo se puede cifrar mediante el uso de la directiva MDM, que necesita que el dispositivo cumpla los requisitos siguientes:  
    
    **Para dispositivos macOS**:  
    - macOS 10.13 o versiones posteriores.  
    
    **Para dispositivos Windows 10**:  
    - Versión 1703 o posterior de *Business*, *Enterprise*, *Education*, o versión 1809 o posterior de *Pro*.  
    - El dispositivo debe tener un chip TPM.  
    
    Para más información, vea el [proveedor de servicios de configuración (CSP) de BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) en la documentación de Windows.  

  - **No está listo**: El dispositivo no tiene capacidades de cifrado completo, pero admite el cifrado. Por ejemplo, un dispositivo Windows lo podría cifrar un usuario de forma manual o también a través de la directiva de grupo que se puede establecer para permitir el cifrado sin TMP.
  - **No aplicable**: no hay suficiente información para clasificar este dispositivo.  

- **Estado de cifrado**: indica si la unidad del sistema operativo está cifrada.  

- **Nombre principal del usuario**: usuario primario del dispositivo.  

### <a name="device-encryption-status"></a>Estado de cifrado del dispositivo  

Cuando se selecciona un dispositivo desde el informe de cifrado, Intune muestra el panel **Estado de cifrado del dispositivo**. Este panel proporciona los siguientes detalles:  

- **Nombre de dispositivo**: contiene el nombre del dispositivo que está visualizando.  

- **Preparación de cifrado**: evaluación de la preparación de los dispositivos para admitir el cifrado a través de la directiva MDM.  
  
  Por ejemplo: cuando un dispositivo Windows 10 tiene una preparación de *No está listo*, es posible que aún sea compatible con el cifrado. Para que el dispositivo Windows 10 tenga la designación de *Listo*, debe contar con un chip TPM. No es necesario que los chips TPM sean compatibles con el cifrado. (Para obtener más información, consulte *Preparación de cifrado* en la sección anterior).  

- **Estado de cifrado**: indica si la unidad del sistema operativo está cifrada. Intune puede tardar hasta 24 horas en generar informes sobre el estado de cifrado de un dispositivo o un cambio de ese estado. En este tiempo se incluye el tiempo de cifrado del sistema operativo, así como el tiempo necesario para que el dispositivo informe a Intune.  

  Para acelerar la generación de informes del estado de cifrado de FileVault antes de que se produzca el registro del dispositivo con normalidad, haga que los usuarios sincronicen sus dispositivos una vez completado el cifrado.  

- **Perfiles**: una lista de los perfiles de *Configuración del dispositivo* que se aplican a este dispositivo y que se configuran con los valores siguientes:  

  - macOS:
    - Tipo de perfil = *Endpoint Protection*  
    - Configuración > FileVault > FileVault = *Habilitar*

  - Windows 10:
    - Tipo de perfil = *Endpoint Protection*  
    - Configuración > Cifrado de Windows > Cifrar dispositivos = *necesario*  

  Se puede usar esta lista de perfiles con el fin de identificar directivas individuales para revisarlas en caso de que el *resumen de estado del perfil* indique problemas.  

- **Resumen de estado de perfil**: resumen de los perfiles que se aplican a este dispositivo. El resumen representa la condición menos favorable entre los perfiles aplicables. Por ejemplo, aunque solo se produzca un error en un perfil aplicable de entre varios, el *resumen de estado de perfil* mostrará *Error*.  
  
  Para ver más detalles de un estado, vaya a **Intune** > **Configuración del dispositivo** > **Perfiles** y seleccione el perfil. Opcionalmente, seleccione **Estado del dispositivo** y, a continuación, seleccione un dispositivo.  

- **Detalles del estado**: detalles avanzados sobre el estado de cifrado del dispositivo.  

  > [!IMPORTANT]  
  > En dispositivos Windows 10, Intune solo muestra *Detalles del estado* para dispositivos que ejecutan la *actualización de Windows 10 de abril de 2019* o una versión posterior.  
  
  Este campo muestra la información de cada error aplicable que se puede detectar. Puede usar esta información para comprender por qué un dispositivo podría no estar listo para el cifrado.  

  Los siguientes son ejemplos de los detalles de estado que se pueden informar en Intune:  
  
  **macOS**:
  - La clave de recuperación todavía no se ha recuperado ni almacenado. Lo más probable es que el dispositivo no se haya desbloqueado o que no se haya protegido.  
 
    *Tenga en cuenta lo siguiente: este resultado no representa necesariamente una condición de error, sino un estado temporal que podría deberse a un momento en el dispositivo en el que se debe configurar la custodia de las claves de recuperación antes de que se envíe la solicitud de cifrado al dispositivo. Este estado también puede indicar que el dispositivo permanece bloqueado o no se ha registrado con Intune recientemente. Por último, dado que el cifrado de FileVault no se inicia hasta que un dispositivo está conectado (en carga), es posible que un usuario reciba una clave de recuperación para un dispositivo que todavía no esté cifrado*.  

  - El usuario está aplazando el cifrado o actualmente se encuentra en el proceso de cifrado.  
 
    *Tenga en cuenta lo siguiente: o el usuario todavía no ha cerrado sesión después de recibir la solicitud de cifrado, lo cual es necesario para que FileVault pueda cifrar el dispositivo, o bien ha descifrado manualmente el dispositivo. Intune no puede impedir que un usuario descifre su dispositivo.*  

  - El dispositivo ya está cifrado. El usuario del dispositivo debe descifrar el dispositivo para continuar.  
 
    *Tenga en cuenta lo siguiente: Intune no puede configurar FileVault en un dispositivo que ya está cifrado. En lugar de eso, el usuario debe descifrar de forma manual el dispositivo antes de que se pueda administrar mediante una directiva de configuración de dispositivo e Intune.* 
 
  - FileVault necesita que el usuario apruebe su perfil de administración en macOS Catalina y versiones posteriores.  
 
    *Tenga en cuenta lo siguiente: a partir de la versión de macOS 10.15 (Catalina), la configuración de inscripción aprobada por el usuario puede tener como resultado un requisito por el que los usuarios deban aprobar el cifrado de FileVault de forma manual. Para obtener más información, en la documentación de Intune consulte [Inscripción aprobada por el usuario](macos-enroll.md)* .  

  - Desconocido.  

    *Tenga en cuenta lo siguiente: Una posible causa de un estado desconocido es que el dispositivo está bloqueado e Intune no puede iniciar el proceso de custodia o de cifrado. Una vez desbloqueado el dispositivo, el progreso puede continuar*.  

  **Windows 10**:  
  - La directiva de BitLocker requiere el consentimiento del usuario para iniciar el Asistente para Cifrado de unidad BitLocker con el fin de iniciar el cifrado del volumen del sistema operativo, pero el usuario no ha dado su consentimiento.  
  
  - El método de cifrado del volumen del sistema operativo no coincide con la directiva de BitLocker.  
  
  - La directiva de BitLocker requiere protección con TPM para el volumen del sistema operativo, pero no se utiliza TPM.  
  
  - La directiva de BitLocker requiere protección solo con TPM para el volumen del sistema operativo, pero no se utiliza protección con TPM.  
  
  - La directiva de BitLocker requiere protección con TPM y PIN para el volumen del sistema operativo, pero no se utiliza protección con TPM y PIN.  
  
  - La directiva de BitLocker requiere protección con TPM y PIN para el volumen del sistema operativo, pero no se usa protección con TPM y PIN.  
  
  - La directiva de BitLocker requiere protección con TPM, PIN y clave de inicio para el volumen del sistema operativo, pero no se utiliza protección con TPM, PIN y clave de inicio.  
  
  - El volumen del sistema operativo no está protegido.  
  
  - Error de copia de seguridad de la clave de recuperación.  
  
  - Una unidad de disco fija no está protegida.  
  
  - El método de cifrado de la unidad de disco fija no coincide con la directiva de BitLocker.  
  
  - Para cifrar unidades, la directiva de BitLocker requiere que el usuario inicie sesión como administrador, o bien, si el dispositivo está unido a Azure AD, debe establecerse la directiva AllowStandardUserEncryption en 1.  
  
  - Entorno de recuperación de Windows (WinRE) no está configurado.  
  
  - No hay un TPM disponible para BitLocker, bien porque no existe, porque se ha deshabilitado en el registro o porque el sistema operativo está en una unidad extraíble.  
  
  - El TPM no está listo para BitLocker.  
  
  - La red no está disponible y es necesaria para la copia de seguridad de clave de recuperación.  

## <a name="export-report-details"></a>Exportación de detalles del informe 
Mientras ve el panel de informe de cifrado, puede seleccionar **Exportar** para crear una descarga de archivo *.csv* de los detalles del informe.  Este informe incluye los detalles de alto nivel del panel *Informe de cifrado* y los detalles del *Estado de cifrado* para cada dispositivo que administra.   
 
  
![Exportación de detalles](./media/encryption-monitor/export.png) 
 
Este informe se puede usar para identificar problemas en grupos de dispositivos. Por ejemplo, podría usar el informe para identificar una lista de todos los dispositivos macOS que informen *El usuario ya ha habilitado FileVault*, lo que indica qué dispositivos deben descifrarse de forma manual antes de que Intune pueda empezar a administrar su configuración de FileVault.  
 
## <a name="filevault-recovery-keys"></a>Claves de recuperación de FileVault   
Cuando Intune cifra por primera vez un dispositivo macOS con FileVault, se crea una clave de recuperación personal. Tras el cifrado, el dispositivo muestra la clave personal una sola vez al usuario final.  
 
En el caso de los dispositivos administrados, Intune puede custodiar una copia de la clave de recuperación personal. La custodia de las claves habilita a los administradores de Intune para girar claves con el fin de ayudar a proteger los dispositivos y a los usuarios para recuperar una clave de recuperación personal perdida o girada.  
 
Intune admite varias opciones para girar y recuperar claves de recuperación personales. Un motivo para girar una clave es si la clave personal actual se pierde o se considera que está en riesgo.  
 
> [!IMPORTANT]  
>  Intune no puede administrar los dispositivos que, en vez de cifrar Intune, son los usuarios quienes los cifran. Esto significa que Intune no puede custodiar la recuperación personal de estos dispositivos ni administrar el giro de la clave de recuperación.  Antes de que Intune pueda administrar FileVault y las claves de recuperación para el dispositivo, el usuario debe descifrar el dispositivo y, después, dejar que Intune cifre el dispositivo.  

### <a name="rotate-recovery-keys"></a>Giro de claves de recuperación  

- **Rotación automática**: como administrador, puede configurar el valor de la opción Giro de clave de recuperación personal de FileVault para que genere de forma automática nuevas claves de recuperación periódicamente.  Cuando se genera una nueva clave para un dispositivo, esta clave no se muestra al usuario. En lugar de eso, el usuario debe obtener la clave desde un administrador o mediante la aplicación de Portal de empresa.  

- **Rotación manual**: como administrador, puede ver la información de un dispositivo que administra con Intune y que está cifrado con FileVault. Luego, puede optar por girar manualmente la clave de recuperación de los dispositivos corporativos. No es posible girar las claves de recuperación de dispositivos personales.  

  Para girar una clave de recuperación, realice lo siguiente: 
  1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), vaya a  **Dispositivos**  y, después, en Administrar, seleccione  **Todos los dispositivos**.  
  2. En la lista de dispositivos, seleccione el dispositivo que está cifrado y para el que quiere girar la clave. Luego, en Supervisar, seleccione  **Claves de recuperación**.  
  3. En el panel Claves de recuperación, seleccione **Girar clave de recuperación de FileVault**.  
  
     La próxima vez que el dispositivo se registre con Intune, se girará la clave personal. Cuando sea necesario, el usuario final puede obtener la nueva clave a través del Portal de empresa. 


### <a name="recover-recovery-keys"></a>Recuperación de claves de recuperación  
- **Administrador**: los administradores no pueden ver las claves de recuperación personales de los dispositivos cifrados con FileVault.  

- **Usuario final**: los usuarios finales usan el sitio web de Portal de empresa desde cualquier dispositivo para ver la clave de recuperación personal actual de cualquiera de sus dispositivos administrados. No puede ver las claves de recuperación en la aplicación Portal de empresa.  

 
  Para ver una clave de recuperación, realice lo siguiente:  
  1. Inicie sesión en el sitio web *Portal de empresa de Intune* desde cualquier dispositivo.  
  2. En el portal, vaya a **Dispositivos** y seleccione el dispositivo macOS cifrado con FileVault.  
  3. Seleccione **Obtener clave de recuperación**. Se muestra la clave de recuperación actual.  
 

## <a name="bitlocker-recovery-keys"></a>Claves de recuperación de BitLocker  

Intune proporciona acceso la hoja de Azure AD para BitLocker, para que pueda ver los identificadores de clave de BitLocker y las claves de recuperación para los dispositivos Windows 10, desde el portal de Intune.  Para que sea accesible, el dispositivo debe tener sus claves custodiadas en Azure AD. 
1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), vaya a **Dispositivos** y, después, en *Administrar*, seleccione **Todos los dispositivos**.  

2. Seleccione un dispositivo de la lista y, en *Supervisión*, seleccione **Claves de recuperación**.  
  
Cuando las claves están disponibles en Azure AD, está disponible la siguiente información:
- Identificador de clave de BitLocker  
- Clave de recuperación de BitLocker  
- Tipo de unidad  

Cuando las claves no están en Azure AD, Intune mostrará *No se encontró ninguna clave de BitLocker para este dispositivo*.  

La información de BitLocker se obtiene mediante el [proveedor de servicios de configuración de BitLocker (CSP)](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp). El CSP de BitLocker se admite en Windows 10 versión 1703 y posteriores y en Windows 10 Pro versión 1809 y posteriores.  

## <a name="next-steps"></a>Pasos siguientes  

Crear una directiva de [cumplimiento de dispositivos](compliance-policy-create-windows.md).
