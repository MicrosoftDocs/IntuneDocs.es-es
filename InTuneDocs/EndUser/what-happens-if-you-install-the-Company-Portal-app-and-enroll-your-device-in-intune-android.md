---
# required metadata

title: ¿Qué ocurre si instala la aplicación Portal de empresa e inscribe el dispositivo en Intune? | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: d22f5aea-7be4-419b-b51b-a522ca037b69

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: arnab
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# ¿Qué ocurre si instala la aplicación Portal de empresa e inscribe el dispositivo en Intune?

Al instalar la aplicación Portal de empresa e inscribir su dispositivo Android en Intune, puede usar la aplicación Portal de empresa para:

-   Acceder a la red, el correo electrónico y los archivos de trabajo de la empresa

-   Obtener aplicaciones de empresa desde el portal de la empresa

-   Configurar automáticamente su cuenta de correo electrónico de la empresa

-   Restablecer su teléfono a la configuración de fábrica si lo pierde o se lo roban

Al agregar un dispositivo Android, da permiso al administrador de TI para acceder al dispositivo. El administrador puede hacer cosas como:

-   Restablecer la configuración predeterminada de fábrica del dispositivo. Esto es útil en caso de pérdida o robo del dispositivo.

-   Quitar todos los datos relacionados con la empresa. Los datos personales y la configuración no se quitan.

-   Forzarle a establecer una contraseña o un PIN para el dispositivo, lo que podría bloquear el dispositivo o restablecer la configuración predeterminada del dispositivo (operación que podría incluir la eliminación de datos) tras varios intentos incorrectos de introducir la contraseña.

-   Debe aceptar los términos y condiciones.

-   Habilitar o deshabilitar la cámara en el dispositivo.

-   Forzar el cifrado de todos los datos, incluidos los datos empresa y los personales, en el dispositivo. Esto ayuda a proteger los datos en caso de pérdida o robo del dispositivo.

-   Una vez agregado el dispositivo al Portal de empresa, este hará lo siguiente cada 8 horas aproximadamente:

    -   Descargar las actualizaciones de directivas o aplicaciones proporcionadas por el administrador de TI.

    -   Enviar actualizaciones de inventario de hardware (estas actualizaciones no contienen información personal).

    -   Enviar actualizaciones de inventario de aplicaciones de empresa (estas actualizaciones no contienen información personal).

Si tiene alguna pregunta y no encuentra la información de contacto del administrador de TI, vea si aparece en el [sitio web del portal de empresa](http://portal.manage.microsoft.com).

### Consulte también
[Uso de un dispositivo Android con Intune](using-your-android-device-with-intune.md)

<!--HONumber=Jun16_HO1-->


