---
title: Configuración de opciones de protección de identidad en Microsoft Intune - Azure | Microsoft Docs
description: Agregue un perfil de dispositivo para configurar opciones de Windows Hello para empresas en dispositivos Windows 10 en Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: f9d0db8e15e6de1241984f98bf651fcff1578033
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52188652"
---
# <a name="configure-identity-protection-settings-in-microsoft-intune"></a>Configuración de opciones de protección de identidad en Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Los perfiles de protección de identidad controlan cómo se aprovisiona y configura Windows Hello para empresas en dispositivos Windows 10 administrados. Cree este perfil para configurar lo siguiente:  
* Disponibilidad de Windows Hello para empresas para dispositivos y usuarios.
* Requisitos de PIN de dispositivo.
* Los gestos que los usuarios pueden y no pueden utilizar para iniciar sesión en sus dispositivos.  

 Puede asignar este perfil a usuarios y grupos de dispositivos concretos, o bien a todos los usuarios y todos los dispositivos. Los grupos recibirán el perfil de protección de identidad al registrarse en Intune.    

Use la información de este artículo para crear un perfil de protección de identidad. Después, [asigne el perfil](device-profile-assign.md) a los grupos de usuarios y dispositivos.

Esta característica se aplica a los dispositivos que ejecutan:  
- Windows 10 y versiones posteriores
- Windows Holographic for Business  

## <a name="create-a-device-profile-with-identity-protection-settings"></a>Creación de un perfil de dispositivo con opciones de protección de identidad

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
4. Escriba un **Nombre** y una **Descripción** para el perfil de protección de identidad.
5. En la lista desplegable **Plataform** (Plataforma), elija **Windows 10 y versiones posteriores**. Windows Hello para empresas solo es compatible con dispositivos que ejecutan Windows 10 y versiones posteriores.
6. En la lista desplegable **Tipo de perfil**, seleccione **Protección de identidad**.
7. En el panel de Windows Hello para empresas, elija entre las opciones siguientes para Configurar Windows Hello para empresas:
    * Deshabilitado. Si no quiere usar Windows Hello para empresas, seleccione esta opción. De esta manera, todas las demás configuraciones en pantalla se deshabilitan.
    * Habilitado. Seleccione esta opción si quiere configurar Windows Hello para empresas.  

8. Si ha seleccionado **Habilitado** en el paso anterior, configure las opciones necesarias que se van a aplicar a los dispositivos Windows 10 y Windows 10 Mobile inscritos y a los usuarios seleccionados como destino.

> [!NOTE]
> Al asignar perfiles de protección de identidad solo a los usuarios, el contexto de dispositivo tiene como valor predeterminado **Sin configurar**.  

   - **Longitud mínima de PIN**/**Longitud máxima de PIN**. Configura los dispositivos para que usen las longitudes de PIN mínima y máxima que se especifiquen, lo cual garantiza un inicio de sesión seguro. La longitud predeterminada del PIN es de seis caracteres, pero se puede aplicar una longitud mínima de cuatro. La longitud de PIN máxima es de 127 caracteres.  

   - **Letras minúsculas en el PIN**/**Letras mayúsculas en el PIN**/**Caracteres especiales en el PIN**. Si quiere aplicar un PIN más seguro, puede requerir el uso de letras mayúsculas, letras minúsculas y caracteres especiales en el PIN. Elija de entre las siguientes opciones:

     - **Permitido**. Los usuarios pueden usar el tipo de carácter en el PIN, pero no es obligatorio.

     - **Requerido**. Los usuarios deben incluir al menos uno de los tipos de carácter en el PIN. Por ejemplo, una práctica habitual consiste en obligar a usar como mínimo una mayúscula y un carácter especial.

     - **No permitido** (valor predeterminado). Los usuarios no deben usar estos tipos de caracteres en el PIN. (Este comportamiento también se produce si la opción no está configurada).<br>Entre los caracteres especiales se incluyen los siguientes: **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**

   - **Expiración del PIN (días)**. Se recomienda especificar un período de expiración del PIN, transcurrido el cual hay que cambiarlo. El valor predeterminado es 41 días.

   - **Recordar historial de PIN**. Restringe la reutilización de los PIN usados anteriormente. De forma predeterminada, no se pueden volver a usar los últimos cinco PIN.  
   - **Habilitar la recuperación del PIN**: permite al usuario cambiar el PIN mediante el servicio de recuperación de PIN de Windows Hello para empresas. 
       - **Habilitar**. El servicio en la nube cifra un secreto de recuperación del PIN que se almacenará en el dispositivo. El usuario puede cambiar su PIN si es necesario.  
       - **Sin configurar** (valor predeterminado). No se crea o se almacena un secreto de recuperación del PIN. Si el usuario olvida el PIN, la única forma de obtener uno nuevo consiste es eliminar el PIN existente y crear otro. El usuario tendrá que volver a registrar todos los servicios a los que el PIN anterior proporcionaba acceso.  
   
   - **Usar un Módulo de plataforma segura (TPM)**. Un chip de TPM ofrece una capa adicional de seguridad de datos. Elija uno de los siguientes valores:  
     - **Habilitar**. Solo los dispositivos que tengan un TPM accesible pueden aprovisionar Windows Hello para empresas.
     - **No configurado**. Todos los dispositivos pueden aprovisionar Windows Hello para empresas, incluso cuando no hay ningún TPM utilizable. En primer lugar, los dispositivos intentarán usar un TPM, pero si no hay ninguno disponible, los dispositivos pueden usar el cifrado de software.  

   - **Permitir autenticación biométrica**. Habilita la autenticación biométrica, como el reconocimiento facial o la huella digital, como alternativa a un PIN para Windows Hello para empresas. Los usuarios todavía deben configurar un PIN de trabajo por si produce un error en la autenticación biométrica. Elija de entre las siguientes opciones:

     - **Habilitar**. Windows Hello para empresas permite la autenticación biométrica.
     - **Sin configurar** (valor predeterminado). Windows Hello para empresas impide la autenticación biométrica (en todos los tipos de cuenta).

   - **Usar tecnología mejorada contra la suplantación de identidad, cuando esté disponible**. Establece si se van a usar las características contra la suplantación de identidad de Windows Hello en los dispositivos que lo permitan (por ejemplo, cuando se detecte una fotografía de un rostro en lugar de un rostro real).
       - **Habilitar**. Windows requiere que, cuando se admita, todos los usuarios usen tecnología contra la suplantación de identidad para las características faciales.  
       - **Sin configurar** (valor predeterminado). Windows respeta las configuraciones de suplantación de identidad en el dispositivo.

   - **Certificado para recursos locales**. 
       - **Habilitar**. Permite que Windows Hello para empresas use certificados para autenticarse en los recursos locales.
       - **Sin configurar** (valor predeterminado). Impide que Windows Hello para empresas use certificados para autenticarse en los recursos locales.  
9. Haga clic en **Aceptar** para guardar el perfil.  

El perfil se crea y aparece en la lista **Configuración del dispositivo - Perfiles**. Para continuar y asignar este perfil a los grupos, vea [Asignación de perfiles de dispositivo](device-profile-assign.md).  

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
