---
title: Informe de cifrado y claves de BitLocker en Microsoft Intune
titleSuffix: Microsoft Intune
description: Vea un informe sobre el estado de cifrado del dispositivo y acceda a las claves de recuperación de BitLocker desde el portal de Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: bccfc952202ed9db5bdc5f68bbbba57c61b37b13
ms.sourcegitcommit: b3a1c5b0b24f0e52cf318defe10f3d27a2770009
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/21/2019
ms.locfileid: "67316932"
---
# <a name="monitor-bitlocker-and-device-encryption"></a>Supervisar BitLocker y el cifrado del dispositivo  
Intune ofrece un punto central desde el que poder identificar el estado de cifrado de los dispositivos Windows 10 y acceso a información importante de BitLocker desde los dispositivos, ya que se encuentra en Azure Active Directory (Azure AD).  

- El [Informe de cifrado](#encryption-report) proporciona detalles sobre el estado de cifrado de un dispositivo y si está listo. Con la información del informe es más fácil identificar problemas que impidan cifrar correctamente los dispositivos que quiere proteger.  
- Puede [ver detalles de BitLocker](#bitlocker-recovery-keys), como el identificador de clave y las claves de recuperación de los dispositivos desde el portal de Intune.  

## <a name="encryption-report"></a>Informe de cifrado
Puede usar el informe de cifrado para ver los detalles sobre el estado de cifrado de los dispositivos Windows 10.  

Para encontrar el informe, inicie sesión en [Intune](https://aka.ms/intuneportal) y vaya a **Configuración del dispositivo**. Después, en *Supervisión*, seleccione **Informe de cifrado**.  

### <a name="prerequisites"></a>Requisitos previos:
Para que aparezca en el informe de cifrado, un dispositivo debe ejecutar Windows versión 1607 o posterior.  

### <a name="report-details"></a>Detalles del informe
El informe muestra el **nombre de dispositivo** para los dispositivos Windows 10 y detalles de alto nivel sobre cada uno, incluidos:  
- **Versión del SO**: versión de Windows.  
- **Versión de TPM**: versión del chip del módulo de plataforma segura (TPM) en el dispositivo.  
- **Preparación de cifrado**: evaluación de la preparación de los dispositivos para admitir el cifrado de BitLocker. Los dispositivos se pueden identificar como:
  - **Listo**: El dispositivo se puede cifrar mediante el uso de la directiva MDM, que necesita que el dispositivo tenga un TPM y cumpla estos requisitos de SKU y de versión de Windows 10:
    - Versión 1703 o posterior, de Business, Enterprise, Education
    - Versión 1809 o posterior, de Pro  
  
    Para más información, vea el [proveedor de servicios de configuración (CSP) de BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) en la documentación de Windows.  

  - **No está listo**: El dispositivo no tiene capacidades de cifrado completo, pero admite el cifrado. Por ejemplo, el dispositivo podría cifrarse manualmente por un usuario o a través de la directiva de grupo que se puede establecer para permitir el cifrado sin TMP.
  - **No aplicable**: No hay suficiente información para clasificar este dispositivo.  

- **Estado de cifrado**: indica si la unidad del sistema operativo está cifrada. 


### <a name="device-encryption-status"></a>Estado de cifrado del dispositivo
Cuando se selecciona un dispositivo, Intune muestra el panel **Estado de cifrado del dispositivo**.

Este panel proporciona los siguientes detalles:  
- **Nombre de dispositivo**: contiene el nombre del dispositivo que está visualizando.  
- **Preparación de cifrado**: evaluación de la preparación de los dispositivos para admitir el cifrado de BitLocker. Un dispositivo podría tener el estado *Cifrado*, aunque su grado de preparación de cifrado sea *No está listo*, porque no tiene un TPM. (Vea Preparación de cifrado en la sección anterior para obtener más detalles).
- **Estado de cifrado**: indica si la unidad del sistema operativo está cifrada. Intune puede tardar hasta 24 horas en empezar a generar informes sobre un estado de cifrado de dispositivos o un cambio de ese estado.  
- **Perfiles**: una lista de los perfiles de *Configuración del dispositivo* que se aplican a este dispositivo e incluyen los siguientes tipos de perfil y configuración:  
  - Tipo de perfil = *Endpoint Protection*  
  - Configuración > Cifrado de Windows > Cifrar dispositivos = *necesario*  

  Esta lista puede ser útil en la localización de directivas individuales para revisarlas en caso de que el resumen de estado del perfil indique problemas.  

- **Resumen de estado de perfil**: resumen de los perfiles que se aplican a este dispositivo. El resumen representa la condición menos favorable entre todos los perfiles aplicables. Por ejemplo, si un perfil produce un error, se mostrará el resumen de estado de perfil *Error*.  
- **Detalles del estado**: detalles avanzados sobre el estado de cifrado del dispositivo. 
  > [!NOTE]  
  > Intune solo muestra *Detalles del estado* para dispositivos que ejecutan la *actualización de Windows 10 de abril de 2019* o una versión posterior.
  
  Este campo muestra la información de cada error aplicable que se puede detectar. Puede usar esta información para comprender por qué un dispositivo podría no estar listo para el cifrado.  

  Los siguientes son ejemplos de los detalles de estado que se pueden informar en Intune:  

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
   - No hay un TPM disponible para BitLocker, bien porque no hay, porque se ha deshabilitado en el Registro o porque el sistema operativo está en una unidad extraíble.  
   - El TPM no está listo para BitLocker.  
   - La red no está disponible y es necesaria para la copia de seguridad de clave de recuperación.  

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
Cree una directiva de [cumplimiento del dispositivo](compliance-policy-create-windows.md) para configurar BitLocker y el cifrado en dispositivos Windows 10.
