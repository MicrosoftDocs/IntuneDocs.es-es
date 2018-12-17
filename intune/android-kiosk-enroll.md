---
title: Inscribir dispositivos Android Enterprise en modo de quiosco multimedia en Intune
titlesuffix: Microsoft Intune
description: Obtenga información sobre cómo inscribir dispositivos Android Enterprise en modo de quiosco multimedia en Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 637fe2d2c764cf78e67e728bfa77567cf12e88ce
ms.sourcegitcommit: fff179f59bd542677cbd4bf3bacc24bb880e2cb6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53032000"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-kiosk-devices"></a>Configurar la inscripción de Intune de dispositivos Android Enterprise en modo de pantalla completa

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android admite dispositivos en modo de quiosco multimedia con su solución de un solo uso y propiedad corporativa. Estos dispositivos tienen un solo fin, que puede ser la señalización digital, la impresión de vales o la administración de inventario, por nombrar solo algunos. Los administradores bloquean el uso de un dispositivo para un conjunto limitado de aplicaciones y vínculos web. También impide que los usuarios agreguen otras aplicaciones o lleven a cabo otras acciones en el dispositivo.

Intune le ayuda a implementar aplicaciones y configuraciones en dispositivos Android de quiosco multimedia. Para obtener detalles específicos sobre Android Enterprise, consulte [Requisitos para usar dispositivos Android en una empresa](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

Los dispositivos que administre de esta forma se inscriben en Intune sin una cuenta de usuario y no están asociados a ningún usuario final. No están pensadas para aplicaciones de uso personal o aplicaciones que tengan un requisito importante de datos concretos de la cuenta del usuario, como Outlook o Gmail.

## <a name="device-requirements"></a>Requisitos de los dispositivos

Los dispositivos deben cumplir estos requisitos para administrarse como un dispositivo de quiosco multimedia de Android Enterprise:

- Android OS versión 5.1 y versiones posteriores.
- Los dispositivos deben ejecutar una versión de Android que tenga conectividad con Servicios de Google para móviles (GMS). Los dispositivos deben tener GMS disponible y deben ser capaces de conectarse a GMS.

## <a name="set-up-android-kiosk-management"></a>Configurar la administración del quiosco multimedia Android

Para configurar la administración del quiosco multimedia Android, siga estos pasos:

1. Para prepararse para administrar dispositivos móviles, debe [establecer la entidad de administración de dispositivos móviles (MDM) en **Microsoft Intune**](mdm-authority-set.md) para obtener instrucciones. Este elemento solo se establece una vez, la primera vez que configura Intune para la administración de dispositivos móviles.
2. [Conecte su cuenta de inquilino de Intune a su cuenta de Android Enterprise](connect-intune-android-enterprise.md).
3. [Cree un perfil de inscripción](#create-an-enrollment-profile).
4. [Cree un grupo de dispositivos](#create-a-device-group).
5. [Inscriba los dispositivos de quiosco multimedia](#enroll-the-kiosk-devices).

### <a name="create-an-enrollment-profile"></a>Crear un perfil de inscripción

Debe crear un perfil de inscripción para poder inscribir sus dispositivos de quiosco multimedia. Al crear el perfil, obtiene un token de inscripción (cadena aleatoria) y un código QR. Según el sistema operativo Android y la versión del dispositivo, puede usar el token o un código QR para [inscribir el dispositivo de quiosco multimedia](#enroll-the-kiosk-devices).

1. Vaya al [portal de Intune](https://portal.azure.com) y elija **Inscripción de dispositivos** > **Inscripción de Android** > **Inscripciones de dispositivos de tareas y quiosco multimedia**.
2. Elija **Crear** y rellene los campos obligatorios.
    - **Nombre**: escriba el nombre que va a usar al asignar el perfil al grupo de dispositivos dinámicos.
    - **Fecha de expiración del token**: la fecha en que caduca el token. Google exige un máximo de 90 días.
3. Elija **Crear** para guardar el perfil.

### <a name="create-a-device-group"></a>Creación de un grupo de dispositivos

Puede dirigir las aplicaciones y directivas a grupos de dispositivos dinámicos o asignados. Puede configurar grupos de dispositivos de AAD dinámicos para que los dispositivos que están inscritos con un perfil de inscripción determinada se rellenen automáticamente. Para ello, siga estos pasos:

1. Vaya al [portal de Intune](https://portal.azure.com) y elija **Grupos** > **Todos los grupos** > **Grupo nuevo**.
2. En la hoja **Grupo**, rellene los campos obligatorios, como se indica a continuación:
    - **Tipo de grupo**: Seguridad
    - **Nombre de grupo**: escriba un nombre intuitivo (como Dispositivos de fábrica 1)
    - **Tipo de pertenencia**: dispositivo dinámico
3. Elija **Agregar una consulta dinámica**.
4. En la hoja **Reglas de pertenencia dinámica**, rellene los campos del modo siguiente:
    - **Agregar regla de pertenencia dinámica**: regla simple
    - **Add devices where** (Agregar dispositivos aquí): enrollmentProfileName
    - En el cuadro central, elija **Coincidencia**.
    - En el último campo, escriba el nombre del perfil de inscripción que creó anteriormente.
    Para más información sobre las reglas de pertenencia dinámica, vea [Reglas de pertenencia dinámica a grupos de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership). 
5. Elija **Agregar consulta** > **Crear**.

### <a name="replace-or-remove-tokens"></a>Reemplazar o quitar tokens

Puede reemplazar o quitar los tokens y los códigos QR.

- **Reemplazar el token**: al acercarse el momento de expiración de un token, puede generar uno nuevo o un código QR usando Reemplazar el token.
- **Revocar token**: puede hacer que el token o el código QR expire inmediatamente. A partir de este momento, el código QR o token ya no se puede usar. Puede usar esta opción si:
    - comparte accidentalmente el código QR o token con un tercero no autorizado,
    - finaliza todas las inscripciones y ya no necesita el token o código QR.

El reemplazo o la revocación de un código QR o token no tendrán ningún efecto en los dispositivos que ya estén inscritos.

1. Vaya al [portal de Intune](https://portal.azure.com) y elija **Inscripción de dispositivos** > **Inscripción de Android** > **Inscripciones de dispositivos de tareas y quiosco multimedia**.
2. Elija el perfil con el que quiera trabajar.
3. Elija **Token**.
4. Para reemplazar el token, elija **Reemplazar el token**.
5. Para revocar el token, elija **Revocar el token**.

## <a name="enroll-the-kiosk-devices"></a>Inscripción de los dispositivos de quiosco multimedia

Después de crear el perfil de inscripción y el grupo de dispositivos dinámicos, puede inscribir los dispositivos de quiosco multimedia. La forma de inscribir los dispositivos Android depende del sistema operativo.

| Método de inscripción | Versión mínima admitida del sistema operativo Android |
| ----- | ----- |
| Transmisión de datos en proximidad | 5.1 |
| Entrada de token | 6.0 |
| Código QR | 7.0 |
| Zero Touch | 8.0 en los fabricantes participantes |

### <a name="enroll-by-using-near-field-communication-nfc"></a>Inscripción mediante Transmisión de datos en proximidad (NFC)

En Android 5.1 y dispositivos posteriores que admitan NFC, puede aprovisionar los dispositivos mediante la creación de una etiqueta NFC con formato especial. Puede usar su propia aplicación o cualquier herramienta de creación de etiquetas NFC. Para obtener más información, consulte la [documentación de la API Android Management de Google](https://developers.google.com/android/management/provision-device#nfc_method).

### <a name="enroll-by-using-a-token"></a>Inscripción mediante token

En Android 6 y dispositivos posteriores, puede usar el token para inscribir el dispositivo. En Android 6.1 y versiones posteriores, también se puede digitalizar el código QR al usar el método de inscripción **aft#setup**.

1. Encienda el dispositivo borrado.
2. En la pantalla **Bienvenida**, seleccione su idioma.
3. Conéctese a la **Wi-Fi** y después elija **SIGUIENTE**.
4. Acepte los términos y condiciones de Google, y después elija **SIGUIENTE**.
5. En la pantalla de inicio de sesión de Google, escriba **afw#setup** en lugar de una cuenta de Gmail y después elija **SIGUIENTE**.
6. Elija **INSTALAR** para la aplicación **Directiva de dispositivos Android**.
7. Continúe con la instalación de esta directiva.  Algunos dispositivos pueden requerir la aceptación de términos adicionales. 
8. En la pantalla **Inscribir este dispositivo**, permita que el dispositivo escanee el código QR o elija indicar el token manualmente.
9. Siga las indicaciones en pantalla para realizar la inscripción. 

### <a name="enroll-by-using-a-qr-code"></a>Inscripción mediante código QR

En Android 7 y versiones posteriores, puede examinar el código QR desde el perfil de inscripción para inscribir el dispositivo.

> [!Note]
> El zoom del navegador puede impedir la digitalización del código QR en algunos dispositivos. Este problema puede solucionarse aumentando el zoom del navegador.

1. Para iniciar una lectura de código QR en el dispositivo Android, toque varias veces la primera pantalla que aparece después de un borrado.
2. En dispositivos Android 7 y 8, se le pedirá que instale a un lector de códigos QR. Los dispositivos Android 9 y posteriores ya llevan instalado un lector de códigos QR.
3. Use el lector de códigos QR para examinar el código QR del perfil de inscripción y siga las indicaciones en pantalla para inscribirse.

### <a name="enroll-by-using-google-zero-touch"></a>Inscripción mediante Zero Touch de Google

Para usar el sistema Zero Touch de Google, el dispositivo debe admitirlo y estar afiliado a un proveedor que forme parte del servicio.  Para obtener más información, consulte el [sitio web del programa Zero Touch de Google](https://www.android.com/enterprise/management/zero-touch/). 


1. Cree una nueva configuración en la consola de Zero Touch.
2. Elija **Microsoft Intune** en el menú desplegable DPC de EMM.
3. En la consola Zero Touch de Google, copie y pegue el siguiente código JSON en el campo de extras DPC. Reemplace la cadena *YourEnrollmentToken* por el token de inscripción que ha creado como parte de su perfil de inscripción. No olvide colocar el token de inscripción entre comillas dobles.

```
{ 
    "android.app.extra.PROVISIONING_DEVICE_ADMIN_COMPONENT_NAME": "com.google.android.apps.work.clouddpc/.receivers.CloudDeviceAdminReceiver", 

    "android.app.extra.PROVISIONING_DEVICE_ADMIN_SIGNATURE_CHECKSUM": "I5YvS0O5hXY46mb01BlRjq4oJJGs2kuUcHvVkAPEXlg", 

    "android.app.extra.PROVISIONING_DEVICE_ADMIN_PACKAGE_DOWNLOAD_LOCATION": "https://play.google.com/managed/downloadManagingApp?identifier=setup", 

    "android.app.extra.PROVISIONING_ADMIN_EXTRAS_BUNDLE": { 
        "com.google.android.apps.work.clouddpc.EXTRA_ENROLLMENT_TOKEN": "YourEnrollmentToken" 
    } 
} 
```
4. Elija **Aplicar**.

## <a name="managing-apps-on-android-kiosk-devices"></a>Administración de aplicaciones en dispositivos Android de quiosco multimedia

Solo las aplicaciones que tienen como tipo de asignación [Establecer en obligatorio](apps-deploy.md#to-assign-an-app) se pueden instalar en dispositivos Android de quiosco multimedia. Las aplicaciones se instalan desde Google Play Store administrado del mismo modo que en los dispositivos de perfil de trabajo Android.

Cuando el desarrollador de aplicaciones publica una actualización en Google Play, las aplicaciones se actualizan automáticamente en los dispositivos administrados.

Para quitar una aplicación de dispositivos Android de quiosco multimedia, puede realizar una de las siguientes acciones:
-   Eliminar la implementación obligatoria de la aplicación.
-   Crear una implementación de desinstalación de la aplicación.


## <a name="next-steps"></a>Pasos siguientes
- [Implementar aplicaciones de quiosco multimedia Android](apps-deploy.md)
- [Agregar directivas de configuración de quiosco multimedia Android](device-profiles.md)
