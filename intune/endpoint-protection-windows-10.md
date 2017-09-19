---
title: "Configuración de Intune Endpoint Protection para Windows 10"
titlesuffix: Azure portal
description: "Obtenga información sobre la configuración de Intune que puede usar para controlar los valores de Endpoint Protection como BitLocker en dispositivos Windows 10."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 19c20ac5dd73b45dc06d1df6a7d08cc6bac42982
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/15/2017
---
# <a name="endpoint-protection-settings-for-windows-10-and-later-in-microsoft-intune"></a>Configuración de Endpoint Protection para Windows 10 y versiones posteriores en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

El perfil de Endpoint Protection le permite controlar características de seguridad en dispositivos Windows 10, como BitLocker o Windows Defender.

Use la información de este tema para obtener información sobre cómo crear perfiles de Endpoint Protection.

## <a name="create-an-endpoint-protection-profile"></a>Crear un perfil de Endpoint Protection

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Configuración del dispositivo**.
2. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
3. En la hoja de perfiles, elija **Create Profile** (Crear perfil).
4. En la hoja **Crear perfil	**, escriba un **Nombre** y una **Descripción** para el perfil de características del dispositivo.
5. En la lista desplegable **Plataform** (Plataforma), elija **Windows 10 y versiones posteriores**.
6. En la lista desplegable de **Tipos de perfil**, pulse **Endpoint Protection**.
7. En la hoja **Cifrado de Windows**, configure las opciones que quiera. Use los detalles de este tema para ayudarle a entender lo que realiza cada opción de configuración. Cuando termine, elija **Aceptar**.
8. Vuelva a la hoja **Crear perfil** y seleccione **Crear**.

El perfil se crea y aparece en la hoja de la lista de perfiles.

## <a name="windows-defender-smartscreen-settings"></a>Configuración de SmartScreen de Windows Defender

- **SmartScreen para aplicaciones y archivos**: habilite Windows SmartScreen para la ejecución de archivos y aplicaciones.
- **Ejecución de archivos no comprobados**: evite que los usuarios finales puedan ejecutar archivos que no haya comprobado Windows SmartScreen.

## <a name="windows-encryption-settings"></a>Configuración de cifrado de Windows

### <a name="windows-settings"></a>Configuración de Windows

- **Exigir cifrado de dispositivo (solo escritorio)**: si está habilitado, a los usuarios se les pide que habiliten el cifrado de dispositivo. Además, se les pide que confirmen que el cifrado de otro proveedor no se ha habilitado. Si el cifrado de Windows se habilita mientras otro método de cifrado está activo, el dispositivo puede volverse inestable.
- **Exigir cifrado de tarjeta de almacenamiento (solo dispositivos móviles)**: habilite esta opción para cifrar cualquier tarjeta de almacenamiento extraíble que use el dispositivo.


### <a name="bitlocker-base-settings"></a>Configuración base de BitLocker

- **Configurar métodos de cifrado**: habilite esta opción para configurar algoritmos de cifrado para el sistema operativo, los datos y las unidades extraíbles.
    - **Cifrado para unidades de sistema operativo**: elija el método de cifrado para las unidades del sistema operativo. Se recomienda que use el algoritmo XTS-AES.
    - **Cifrado para unidades de datos fijas**: elija el método de cifrado para las unidades de datos fijas (integradas). Se recomienda que use el algoritmo XTS-AES.
    - **Cifrado para unidades de datos extraíbles**: elija el método de cifrado para las unidades de datos extraíbles. Si la unidad extraíble se usa con dispositivos que no ejecutan Windows 10, recomendamos que use el algoritmo AES-CBC.


### <a name="bitlocker-os-drive-settings"></a>Configuración de BitLocker para unidades de sistema operativo

- **Requerir autenticación adicional en el inicio** -
    - **BitLocker con un chip de TPM no compatible** -
    - **Inicio con TPM**: configurar si el chip TPM se permite, no se permite o se necesita.
    - **PIN de inicio con TPM**: configurar si usar un PIN de inicio con el chip TPM se permite, no se permite o se necesita.
    - **Clave de inicio con TPM**: configurar si usar una clave de inicio con el chip TPM se permite, no se permite o se necesita.
    - **Clave y PIN de inicio con TPM**: configurar si usar una clave de inicio y PIN con el chip TPM se permite, no se permite o se necesita.
- **Longitud mínima del PIN**: habilite esta opción para configurar una longitud mínima del PIN de inicio con TPM.
    - **Mínimo de caracteres**: escriba el número de caracteres necesarios para el PIN de inicio de **4**-**20**.
- **Habilitar recuperación de unidades de sistema operativo**: habilite esta opción para controlar cómo se recuperan las unidades de sistema operativo protegidas mediante BitLocker cuando la información de inicio necesaria no está disponible.
    - **Agente de recuperación de datos basada en el certificado**: habilite esta opción si quiere que los agentes de recuperación de datos puedan usarse con las unidades de sistema operativo protegidas mediante BitLocker.
    - **Creación de contraseña de recuperación por el usuario**: configure si los usuarios pueden, necesitan o no pueden generar una contraseña de recuperación de 48 dígitos.
    - **Creación de clave de recuperación por el usuario**: configure si los usuarios pueden, necesitan o no pueden generar una clave de recuperación de 256 bits.
    - **Ocultar opciones de recuperación en el asistente para configuración de BitLocker**: habilite esta opción para evitar que los usuarios vean o cambien las opciones de recuperación cuando activen BitLocker.
    - **Guardar la información de recuperación de BitLocker en AD DS**: habilita el almacenamiento de la información de recuperación de BitLocker en Active Directory.
    - **Configurar el almacenamiento de información de recuperación de BitLocker en AD DS**: configure qué partes de la información de recuperación de BitLocker se almacenan en Active Directory. Elija de entre las siguientes opciones:
        - **Realizar copia de seguridad de contraseñas de recuperación y paquetes de claves**
        - **Realizar copia de seguridad solo de contraseñas de recuperación**
    - **Requerir que la información de recuperación se almacene en AD DS antes de habilitar BitLocker**: habilite esta opción para impedir que los usuarios activen BitLocker a no ser que el dispositivo esté unido a dominio y la información de recuperación de BitLocker esté almacenada correctamente en Active Directory.
- **Habilitar URL y mensaje de recuperación previos al arranque**: habilite esta opción para configurar el mensaje y la dirección URL que se muestra en la pantalla de recuperación previa al arranque.
    - **Mensaje de recuperación previo al arranque**: configure cómo se muestra el mensaje de recuperación previo al arranque a los usuarios. Elija de entre las siguientes opciones:
        - **Usar la dirección URL y el mensaje de recuperación predeterminados**
        - **Usar URL y mensaje de recuperación vacíos**
        - **Usar un mensaje de recuperación personalizado**
        - **Usar una dirección URL de recuperación personalizada**


### <a name="bitlocker-fixed-data-drive-settings"></a>Configuración de BitLocker para unidades de datos fijas

- **Denegar acceso de escritura a unidad de datos fija no protegida con BitLocker**: si está habilitada, la protección de BitLocker debe habilitarse en todas las unidades de datos fijas o integradas para poder escribir en ellas.
- **Habilitar la recuperación de unidades fijas**: habilite esta opción para controlar cómo se recuperan las unidades fijas protegidas mediante BitLocker cuando la información de inicio necesaria no está disponible.
    - **Agente de recuperación de datos**: habilite esta opción si quiere que los agentes de recuperación de datos puedan usarse con las unidades fijas protegidas mediante BitLocker.
    - **Creación de contraseña de recuperación por el usuario**: configure si los usuarios pueden, necesitan o no pueden generar una contraseña de recuperación de 48 dígitos.  
    - **Creación de clave de recuperación por el usuario**: configure si los usuarios pueden, necesitan o no pueden generar una clave de recuperación de 256 bits.
    - **Ocultar opciones de recuperación en el asistente para configuración de BitLocker**: habilite esta opción para evitar que los usuarios vean o cambien las opciones de recuperación cuando activen BitLocker.
    - **Guardar la información de recuperación de BitLocker en AD DS**: habilita el almacenamiento de la información de recuperación de BitLocker en Active Directory.
    - **Configurar el almacenamiento de información de recuperación de BitLocker en AD DS**: configure qué partes de la información de recuperación de BitLocker se almacenan en Active Directory. Elija de entre las siguientes opciones:
        - **Realizar copia de seguridad de contraseñas de recuperación y paquetes de claves**
        - **Realizar copia de seguridad solo de contraseñas de recuperación**
    - **Requerir que la información de recuperación se almacene en AD DS antes de habilitar BitLocker**: habilite esta opción para impedir que los usuarios activen BitLocker a no ser que el dispositivo esté unido a dominio y la información de recuperación de BitLocker se haya almacenado correctamente en Active Directory.


### <a name="bitlocker-removable-data-drive-settings"></a>Configuración de BitLocker para unidades de datos extraíbles

- **Denegar acceso de escritura a discos de datos extraíbles no protegidos con BitLocker**: especifique si se necesita el cifrado de BitLocker para las unidades de almacenamiento extraíbles.
    - **Bloquear acceso de escritura a dispositivos configurados en otra organización**: especifique si se puede escribir en las unidades de datos extraíbles que pertenecen a otra organización.



## <a name="next-steps"></a>Pasos siguientes

Si desea continuar y asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).
