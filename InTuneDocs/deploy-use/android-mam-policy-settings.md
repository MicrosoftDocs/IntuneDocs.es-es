---
title: "Opciones de configuración de directiva de MAM de Android | Microsoft Intune"
description: "En este tema se describe la configuración de directiva de administración de aplicaciones móviles para dispositivos Android."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5dbb702a-1df5-4637-95c9-77a5f0b1a0e3
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: d0a1a2b3f4e5dbac8b333db3a5cc4bb32c0d61ef


---

# <a name="android-mobile-app-management-policy-settings-in-microsoft-intune"></a>Opciones de configuración de directiva de administración de aplicaciones móviles de Android en Microsoft Intune
La configuración de directiva que se describe en este tema puede [configurarse](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) para una directiva de administración de aplicaciones móviles (MAM) en la hoja **Configuración** de Azure Portal.
Existen dos categorías de configuración de directiva: configuración de acceso y configuración de reubicación de datos. En este tema, el término *aplicaciones administradas por directivas* hace referencia a las aplicaciones que están configuradas con directivas de MAM.

##  <a name="data-relocation-settings"></a>Configuración de reubicación de datos

- **Impedir copias de seguridad de Android:** elija **Sí** para no permitir copias o **No** para permitir que se hagan copias de seguridad de los datos corporativos de aplicaciones administradas por directivas.

  Valor predeterminado = **Sí**.
- **Permitir a la aplicación transferir datos a otras aplicaciones**: elija una de las opciones para indicar qué tipo de aplicaciones pueden recibir datos de empresa de aplicaciones administradas por directivas:
  -   **Aplicaciones administradas por directivas:** permite la transferencia únicamente a otras aplicaciones que tengan la directiva de MAM.
  -   **Todas las aplicaciones**: permite la transferencia a cualquier aplicación.
  -   **Ninguna**: no permite la transferencia de datos a ninguna aplicación.

 Valor predeterminado = **Aplicaciones administradas por directivas**.
- **Permitir a la aplicación recibir datos de otras aplicaciones**: especifique qué aplicaciones pueden transferir datos a las aplicaciones administradas por directivas:
  -   **Aplicaciones administradas por directivas**: permite las transferencias de datos únicamente desde otras aplicaciones administradas por directivas.
  -   **Todas las aplicaciones**: permite la transferencia de datos desde cualquier aplicación.
  -   **Ninguna**: no permite la transferencia de datos desde ninguna aplicación.

  Valor predeterminado = **Todas las aplicaciones**.

-   **Impedir Guardar como**: elija **Sí** para impedir el uso de la opción Guardar como en cualquier aplicación que use esta directiva. Elija **No** si quiere permitir el uso de Guardar como.

  Valor predeterminado = **Sí**.
- **Restringir cortar, copiar y pegar con otras aplicaciones**: especifique en qué casos las acciones de cortar, copiar y pegar deben estar restringidas. Elija de entre las siguientes opciones:
  -   **Bloqueado**: no permite las acciones de cortar, copiar y pegar entre aplicaciones administradas por directivas.
  -   **Aplicaciones administradas por directivas**: las acciones de cortar, copiar y pegar solo se permiten entre aplicaciones administradas por directivas.
  -   **Aplicaciones administradas por directivas con pegar**: permite cortar o copiar datos entre aplicaciones administradas por directivas. Permite que los datos cortados o copiados desde cualquier aplicación se peguen en esta aplicación.
  -   **Cualquier aplicación**: no existen restricciones para las acciones de cortar, copiar y pegar entre cualesquiera aplicaciones.

  Valor predeterminado = **Aplicaciones administradas por directivas con pegar**.
-   **Restringir contenido web para mostrar en Managed Browser:** elija **Sí** para especificar que todos los vínculos de la aplicación se abrirán en la aplicación Managed Browser.

  En el caso de los dispositivos que no estén inscritos en Intune, los vínculos de aplicaciones administradas por directivas solo se abrirán en la aplicación Managed Browser si se usa la directiva de MAM.

  Si usa Intune para administrar los dispositivos, vea [Administrar el acceso a Internet mediante directivas de explorador administrado con Microsoft Intune](manage-internet-access-using-managed-browser-policies.md).

  Valor predeterminado = **Sí**.
- **Cifrar datos de aplicación**: elija **Sí** para permitir el cifrado. Si esta opción se habilita, Microsoft proporciona cifrado para las aplicaciones asociadas a una directiva de MAM. Los datos se cifran de forma sincrónica durante las tareas de E/S de archivo. El contenido del almacenamiento del dispositivo estará siempre cifrado.
  >[!NOTE]
  >El método de cifrado no está certificado mediante FIPS 140-2.

  Valor predeterminado = **Sí**.

- **Deshabilitar la sincronización de contactos**: elija **Sí** para evitar que la información de contacto se sincronice con la aplicación nativa de libreta de direcciones del dispositivo. Si elige **No**, la aplicación guardará la información de contacto en la aplicación nativa de libreta de direcciones del dispositivo.

  Al realizar un borrado selectivo para quitar datos de la empresa, se quitan los contactos sincronizados directamente desde la aplicación a la libreta de direcciones nativa. No se pueden borrar los contactos sincronizados desde la libreta de direcciones nativa en otro origen externo. Actualmente esto se aplica únicamente para la aplicación Microsoft Outlook.

  Valor predeterminado = **Sí**.
- **Deshabilitar la impresión**: elija **Sí** para impedir que se impriman datos de la empresa desde aplicaciones asociadas a la directiva de MAM.

  Valor predeterminado = **Sí**.

##  <a name="access-settings"></a>Configuración de acceso

- **Requerir PIN para el acceso**: elija **Sí** si quiere exigir un PIN para poder usar aplicaciones administradas por directivas. Se pedirá al usuario que lo configure la primera vez que ejecuta la aplicación en un contexto laboral.

 Valor predeterminado = **Sí**.

 -  **Permitir el PIN sencillo**: especifique si quiere permitir que los usuarios usen secuencias de PIN sencillas como 1234 o 1111. Valor predeterminado = **Sí**.
 - **Longitud de PIN**: especifique el número mínimo de dígitos en un PIN. Valor predeterminado = **4**.
 - **Número de intentos antes del restablecimiento del PIN**: especifique el número de intentos de entrada de PIN que pueden realizarse antes de que el usuario deba restablecer el PIN. No hay ningún valor predeterminado para esta configuración.
 - **Require fingerprint instead of PIN (iOS 6.0+):** (Requerir huella digital en lugar de PIN [iOS 8.0+]) elija **Sí** para solicitar la identificación mediante huella digital en lugar de un número PIN para el acceso a la aplicación.
 En dispositivos Android, puede permitir que los usuarios se identifiquen mediante huella digital en lugar de un número PIN. Cuando el usuario intenta acceder a esta aplicación mediante su cuenta profesional, se le solicita que indique su identidad mediante huella digital en lugar de escribir un número PIN.
 - **Requerir credenciales corporativas para el acceso**: elija **Sí** para solicitar credenciales corporativas en lugar de un PIN o una huella digital para el acceso a la aplicación. Si se establece en **Sí**, se reemplazarán los requisitos de introducción de un PIN o un Touch ID. Se le solicitará al usuario que proporcione sus credenciales corporativas. Valor predeterminado = **No**.


- **Bloquear las aplicaciones administradas para que no se ejecuten en dispositivos con jailbreak o rooting**: elija **Sí** para impedir que las aplicaciones se ejecuten en dispositivos descodificados o descifrados. El usuario puede seguir usando las aplicaciones para tareas personales, pero tiene que usar un dispositivo distinto para el trabajo.

  Valor predeterminado = **Sí**.
- **Volver a comprobar los requisitos de acceso después de (minutos)**
  -   **Tiempo de espera**: especifique el tiempo (en minutos) que debe transcurrir antes de que se vuelvan a comprobar los requisitos de acceso de la aplicación.
  -   **Período de gracia sin conexión**: si el dispositivo está desconectado, especifique el tiempo (en minutos) que debe transcurrir antes de que se vuelvan a comprobar los requisitos de acceso de la aplicación.

  Valor predeterminado = Tiempo de espera de **30** minutos y **720** minutos de período de gracia sin conexión.

-   **Intervalo sin conexión (días) antes de que se borren los datos de la aplicación**: borre los datos de la empresa si un dispositivo ha estado desconectado durante un período determinado.  Especifique el número de días que un dispositivo puede estar sin conexión antes de que se eliminen los datos de la compañía del dispositivo.

    >[!TIP]
    >Escribir un valor de **0** desactiva esta opción.

  Valor predeterminado = **90** días.
- **Bloquear captura de pantalla y asistente de Android (Android 6 Marshmallow o posterior)**: elija **Sí** para bloquear las funcionalidades de captura de pantalla y de **asistente de Android** del dispositivo cuando se use esta aplicación.



<!--HONumber=Dec16_HO2-->


