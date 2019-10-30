---
title: Inscripción de dispositivos dedicados o totalmente administrados de Android Enterprise en Intune
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo inscribir dispositivos Android dedicados o totalmente administrados en Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2ad96c80a2cad71feec2afdfa87da767aa72fdb1
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505616"
---
# <a name="enroll-your-android-enterprise-dedicated-devices-or-fully-managed-devices"></a>Inscripción de dispositivos dedicados o totalmente administrados de Android Enterprise

Después de configurar los [dispositivos Android Enterprise dedicados](android-kiosk-enroll.md) o [totalmente administrados](android-fully-managed-enroll.md) en Intune, puede inscribir los dispositivos. La inscripción de Intune tanto de dispositivos dedicados como de dispositivos totalmente administrados comienza con un restablecimiento de fábrica. La forma de inscribir los dispositivos Android Enterprise depende del sistema operativo.

| Método de inscripción | Versión mínima del SO Android para dispositivos dedicados y totalmente administrados |
| ----- | ----- |
| Transmisión de datos en proximidad | 5.1 |
| Entrada de token | 6.0 |
| Código QR | 7.0 |
| Zero Touch  | 8.0\* |

\* en los fabricantes participantes.

## <a name="enroll-by-using-near-field-communication-nfc"></a>Inscripción mediante Transmisión de datos en proximidad (NFC)

Para dispositivos que admitan NFC, puede aprovisionar los dispositivos mediante la creación de una etiqueta NFC con formato especial. Puede usar su propia aplicación o cualquier herramienta de creación de etiquetas NFC. Para más información, vea [NFC-based Android Enterprise device enrollment with Microsoft Intune](https://blogs.technet.microsoft.com/cbernier/2018/10/15/nfc-based-android-enterprise-device-enrollment-with-microsoft-intune/) (Inscripción de dispositivos de Android Enterprise basados en NFC) y la [Documentación de la API de administración de Android de Google](https://developers.google.com/android/management/provision-device#nfc_method).

## <a name="enroll-by-using-a-token"></a>Inscripción mediante token

En Android 6 y dispositivos posteriores, puede usar el token para inscribir el dispositivo. En Android 6.1 y versiones posteriores, también se puede digitalizar el código QR al usar el método de inscripción **afw#setup**.

1. Encienda el dispositivo borrado.
2. En la pantalla **Bienvenida**, seleccione su idioma.
3. Conéctese a la **Wi-Fi** y después elija **SIGUIENTE**.
4. Acepte los términos y condiciones de Google, y después elija **SIGUIENTE**.
5. En la pantalla de inicio de sesión de Google, escriba **afw#setup** en lugar de una cuenta de Gmail y después elija **SIGUIENTE**.
6. Elija **INSTALAR** para la aplicación **Directiva de dispositivos Android**.
7. Continúe con la instalación de esta directiva.  Algunos dispositivos pueden requerir la aceptación de términos adicionales.
8. En la pantalla **Inscribir este dispositivo**, permita que el dispositivo escanee el código QR o elija indicar el token manualmente.
9. Siga las indicaciones en pantalla para realizar la inscripción.

## <a name="enroll-by-using-a-qr-code"></a>Inscripción mediante código QR

En Android 7 y versiones posteriores, puede examinar el código QR desde el perfil de inscripción para inscribir el dispositivo.

> [!Note]
> El zoom del navegador puede impedir la digitalización del código QR en algunos dispositivos. Este problema puede solucionarse aumentando el zoom del navegador.

1. Para iniciar una lectura de código QR en el dispositivo Android, toque varias veces la primera pantalla que aparece después de un borrado.
2. En dispositivos Android 7 y 8, se le pedirá que instale a un lector de códigos QR. Los dispositivos Android 9 y posteriores ya llevan instalado un lector de códigos QR.
3. Use el lector de códigos QR para examinar el código QR del perfil de inscripción y siga las indicaciones en pantalla para inscribirse.

## <a name="enroll-by-using-google-zero-touch"></a>Inscripción mediante Zero Touch de Google

Para usar el sistema Zero Touch de Google, el dispositivo debe admitirlo y estar afiliado a un proveedor que forme parte del servicio.  Para obtener más información, consulte el [sitio web del programa Zero Touch de Google](https://www.android.com/enterprise/management/zero-touch/).

1. Cree una nueva configuración en la consola de Zero Touch.
2. Elija **Microsoft Intune** en el menú desplegable DPC de EMM.
3. En la consola Zero Touch de Google, copie y pegue el siguiente código JSON en el campo de extras DPC. Reemplace la cadena *YourEnrollmentToken* por el token de inscripción que ha creado como parte de su perfil de inscripción. No olvide colocar el token de inscripción entre comillas dobles.

    ```json
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


## <a name="next-steps"></a>Pasos siguientes
- [Implementar aplicaciones Android](../apps/apps-deploy.md)
- [Agregar directivas de configuración de Android](../configuration/device-profiles.md)

