---
title: "Configuración de directiva MAM de iOS | Microsoft Intune"
description: "En este tema se describe la configuración de directiva de administración de aplicaciones móviles para dispositivos iOS."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 673ff872-943c-4076-931c-0be90363aea9
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: 126974152c638fc4bc69ef92b5fa79beeb0eed0c


---

#  <a name="ios-mobile-app-management-policy-settings"></a>Configuración de directiva de administración de aplicaciones móviles iOS
La configuración de directiva que se describe en este tema puede [configurarse](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) para una directiva de administración de aplicaciones móviles (MAM) en la hoja **Configuración** de Azure Portal.

Existen dos categorías de configuración de directiva: configuración de acceso y configuración de reubicación de datos. En este tema, el término *aplicaciones administradas por directivas* hace referencia a las aplicaciones que están configuradas con directivas de MAM.

##  <a name="data-relocation-settings"></a>Configuración de reubicación de datos

- **Impedir copias de seguridad de iTunes y iCloud**: elija **Sí** para deshabilitar esta opción, o **No** para permitir que se hagan copias de seguridad de los datos corporativos de las aplicaciones administradas por directivas.

  Valor predeterminado = **Sí**.

- **Permitir a la aplicación transferir datos a otras aplicaciones**: seleccione una de las opciones para indicar a las aplicaciones que pueden recibir datos de aplicaciones administradas por directivas:
  - **Aplicaciones administradas por directivas:** permite la transferencia, pero solo a otras aplicaciones que tengan la directiva MAM.
  - **Todas las aplicaciones**: permite la transferencia a cualquier aplicación.
  - **Ninguna**: no permite la transferencia de datos a ninguna aplicación, incluidas otras aplicaciones administradas por directivas.

  Además, si establece esta opción en **Aplicaciones administradas por directivas** o **Ninguno**, la característica de iOS 9 que permite que la búsqueda de Spotlight busque datos dentro de las aplicaciones se bloqueará.

  >[!NOTE]
  >Esta configuración no controla el uso de la característica Open In en dispositivos móviles. Para administrar Abrir en, vea [Administrar la transferencia de datos entre aplicaciones iOS con Microsoft Intune](manage-data-transfer-between-ios-apps-with-microsoft-intune.md).

  Valor predeterminado = **Aplicaciones administradas por directivas**.

- **Permitir a la aplicación recibir datos de otras aplicaciones**: especifique las aplicaciones que tienen permiso para transferir datos a las aplicaciones administradas por directivas:
  -  **Aplicaciones administradas por directivas**: permite las transferencias de datos, pero solo desde otras aplicaciones administradas por directivas.
  -  **Todas las aplicaciones**: permite la transferencia de datos desde cualquier aplicación.
  -  **Ninguna**: no permite la transferencia de datos desde ninguna aplicación.

  Valor predeterminado = **Todas las aplicaciones**.

- **Impedir Guardar como**: elija **Sí** para impedir el uso de la opción Guardar como en cualquier aplicación que use esta directiva. Elija **No** si quiere permitir el uso de Guardar como.

  Valor predeterminado = **Sí**.

- **Restringir cortar, copiar y pegar con otras aplicaciones**: especifique en qué casos las acciones de cortar, copiar y pegar deben estar restringidas. Elija de entre las siguientes opciones:
  -   **Bloqueado**: no permite las acciones de cortar, copiar y pegar entre aplicaciones administradas por directivas.
  -   **Aplicaciones administradas por directivas**: las acciones de cortar, copiar y pegar solo se permiten entre aplicaciones administradas por directivas.
  -   **Aplicaciones administradas por directivas con pegar**: permite cortar o copiar datos entre aplicaciones administradas por directivas. Permite que los datos cortados o copiados desde cualquier aplicación se peguen en esta aplicación.
  - **Cualquier aplicación**: no existen restricciones para las acciones de cortar, copiar y pegar entre cualesquiera aplicaciones.

  Valor predeterminado = **Aplicaciones administradas por directivas con pegar**.

- **Restringir contenido web para mostrar en Managed Browser:** cuando se habilita esta opción, los vínculos en la aplicación se abrirán en la aplicación Managed Browser.

  En el caso de los dispositivos que no estén inscritos en Intune, los vínculos web en aplicaciones administradas por directivas solo se pueden abrir en la aplicación Managed Browser.

  Si usa Intune para administrar los dispositivos, vea [Administrar el acceso a Internet mediante directivas de explorador administrado con Microsoft Intune](manage-internet-access-using-managed-browser-policies.md).

  Valor predeterminado = **Sí**.

- **Cifrar datos de aplicación:** en el caso de aplicaciones que están asociadas a una directiva MAM de Intune, los datos se cifran en reposo con el cifrado de nivel de dispositivo proporcionado por el sistema operativo. Cuando se requiere un PIN, los datos se cifran según la configuración de la directiva MAM. Como se indica en la documentación de Apple, [los módulos que usa iOS 7 están certificados mediante FIPS 140-2](http://support.apple.com/en-us/HT202739).

  En la configuración de directiva, puede especificar valores de cifrado de PIN. Estos valores determinan cuándo se cifran los datos. Las opciones son:
  -   **Cuando el dispositivo esté bloqueado**: todos los datos de la aplicación asociados a esta directiva se cifran mientras el dispositivo está bloqueado.
  -   **Cuando el dispositivo esté bloqueado (excepto archivos abiertos)**: todos los datos de la aplicación asociados a esta directiva se cifran mientras el dispositivo está bloqueado, excepto los datos de los archivos que están abiertos en la aplicación.
  -   **Después de reiniciar el dispositivo**: todos los datos de la aplicación asociados a esta directiva se cifran al reiniciar el dispositivo, hasta que el dispositivo se desbloquea por primera vez.
  -   **Usar la configuración del dispositivo**: los datos de la aplicación se cifran en función de la configuración predeterminada del dispositivo.
  Si habilita esta configuración, se solicita al usuario que configure y use un PIN para acceder a su dispositivo.  Si no hay ningún PIN, las aplicaciones no se abren y se le solicita al usuario que establezca un PIN con un mensaje: "Su compañía solicita que primero habilite un PIN de dispositivo para acceder a esta aplicación".

  Valor predeterminado = la opción de cifrado no está seleccionada.
- **Deshabilitar la sincronización de contactos**: elija **Sí** para evitar que la información de contacto se sincronice con la aplicación nativa de libreta de direcciones del dispositivo. Si elige **No**, la aplicación guardará la información de contacto en la aplicación nativa de libreta de direcciones del dispositivo.

  Al realizar una eliminación selectiva para quitar datos de la empresa, se quitan los contactos sincronizados directamente desde la aplicación a la libreta de direcciones nativa. No se pueden borrar los contactos de la libreta de direcciones nativa sincronizados con otro origen externo. Actualmente esto se aplica únicamente para la aplicación Microsoft Outlook.

  Valor predeterminado = **Sí**.

- **Deshabilitar la impresión**: elija **Sí** para impedir los datos de la compañía de impresión desde aplicaciones que están asociadas a la directiva de MAM.

    Valor predeterminado = **Sí**.

##  <a name="access-settings"></a>Configuración de acceso

- **Requerir PIN para el acceso**: elija **Sí** si quiere exigir un PIN para poder usar aplicaciones administradas por directivas. Se pedirá al usuario que lo configure la primera vez que ejecuta la aplicación en un contexto laboral.

  Valor predeterminado = **Sí**.
    -  **Permitir el PIN sencillo**: especifique si quiere permitir que los usuarios usen secuencias de PIN sencillas como 1234 o 1111. Valor predeterminado = **Sí**.
    - **Longitud de PIN**: especifique el número mínimo de dígitos en un PIN. Valor predeterminado = **4**.
    - **Número de intentos antes del restablecimiento del PIN**: especifique el número de intentos de entrada de PIN que pueden realizarse antes de que el usuario deba restablecer el PIN. No hay ningún valor predeterminado para esta configuración.

- **Require fingerprint instead of PIN (iOS 8.0+):** (Requerir huella digital en lugar de PIN [iOS 8.0+]) elija **Sí** para solicitar la identificación mediante huella digital en lugar de un número PIN para el acceso a la aplicación.
En dispositivos iOS, puede dejar que el usuario se identifique con una huella digital en lugar de un PIN. Cuando el usuario intenta abrir esta aplicación mediante su cuenta profesional, se le solicita que indique su identidad mediante huella digital en lugar de escribir un número PIN.

  Valor predeterminado = **Sí**.
- **Requerir credenciales corporativas para el acceso**: elija **Sí** para solicitar credenciales corporativas en lugar de un PIN para el acceso a la aplicación. Si se establece en **Sí**, se reemplazarán los requisitos de introducción de un PIN o un Touch ID. Se le solicitará al usuario que proporcione sus credenciales corporativas.

  Valor predeterminado = **No**.
- **Bloquear las aplicaciones administradas para que no se ejecuten en dispositivos con jailbreak o rooting**: elija **Sí** para impedir que las aplicaciones se ejecuten en dispositivos descodificados o descifrados. El usuario seguirá siendo capaz de usar las aplicaciones para las tareas personales, pero tendrá que usar un dispositivo distinto para el trabajo.

  Valor predeterminado = **Sí**.
- **Volver a comprobar los requisitos de acceso después de (minutos)**
  -   **Tiempo de espera**: especifique el tiempo (en minutos) que debe transcurrir antes de que se vuelvan a comprobar los requisitos de acceso de la aplicación.
  -   **Período de gracia sin conexión**: si el dispositivo está desconectado, especifique el tiempo (en minutos) que debe transcurrir antes de que se vuelvan a comprobar los requisitos de acceso de la aplicación.

  Valor predeterminado = Tiempo de espera de **30** minutos y **720** minutos de período de gracia sin conexión.
- **Intervalo sin conexión (días) antes de que se borren los datos de la aplicación**: puede borrar los datos de la compañía si un dispositivo ha estado desconectado durante un período determinado. Especifique el número de días que un dispositivo puede estar sin conexión antes de que se eliminen los datos de la compañía del dispositivo.

  >[!TIP]
  >Escribir un valor de **0** desactiva esta opción.

  Valor predeterminado = **90** días.



<!--HONumber=Dec16_HO2-->


