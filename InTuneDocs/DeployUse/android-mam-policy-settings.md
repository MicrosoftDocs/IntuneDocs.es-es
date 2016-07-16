---
title: "Opciones de configuración de directiva de MAM de Android | Microsoft Intune"
description: 
keywords: 
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5dbb702a-1df5-4637-95c9-77a5f0b1a0e3
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5a445f06d6c2328f7689468ca4d68a969af1e825
ms.openlocfilehash: 3f43dc871dc0b0a81a6d0b05376a1254957fc35b


---

# Opciones de configuración de directiva de administración de aplicaciones móviles de Android en Microsoft Intune
Las opciones de configuración de directiva que se describen a continuación se pueden [configurar](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) para una directiva de MAM en la hoja **Configuración** del Portal de Azure.
Las dos categorías de configuración de directiva que hay son Reubicación de datos y Acceso:

##  Configuración de reubicación de datos
El término **aplicaciones administradas por directivas** hace referencia a las aplicaciones que están configuradas con directivas de MAM.
- **Impedir copias de seguridad de Android:** elija **Sí** para no permitir copias o **No** para permitir que se hagan copias de seguridad de los datos corporativos de aplicaciones administradas por directivas.

  **Valor predeterminado = Sí**
- **Permitir a la aplicación transferir datos a otras aplicaciones:** seleccione una de las opciones para indicar a las aplicaciones que pueden recibir datos de empresa de aplicaciones administradas por directivas:
  -   **Aplicaciones administradas por directivas:** permite la transferencia, pero solo a otras aplicaciones que tengan la directiva de MAM.
  -   **Todas las aplicaciones:** permite la transferencia a cualquier aplicación.
  -   **Ninguna:** no permite la transferencia de datos a ninguna aplicación.

  **Valor predeterminado = Aplicaciones administradas por directivas**
- **Permitir a la aplicación recibir datos de otras aplicaciones:** especifique las aplicaciones que tienen permiso para transferir datos a las aplicaciones administradas por directivas:
  -   **Aplicaciones administradas por directivas:** permite las transferencias de datos, pero solo desde otras aplicaciones administradas por directivas.
  -   **Todas las aplicaciones:** permite la transferencia de datos desde cualquier aplicación.
  -   **Ninguna:** no permite la transferencia de datos desde ninguna aplicación.

      **Valor predeterminado = Todas las aplicaciones**

-   **Impedir Guardar como:** elija **Sí** para impedir el uso de la opción Guardar como en cualquier aplicación que use esta directiva. Elija **No** si quiere permitir el uso de Guardar como.

  **Valor predeterminado = Sí**
- **Restringir cortar, copiar y pegar con otras aplicaciones:** especifique en qué casos las operaciones de cortar, copiar y pegar deben estar restringidas. Elija de entre las siguientes opciones:
  -   **Bloqueado:** no permite las operaciones de cortar, copiar y pegar entre aplicaciones administradas por directivas.
  -   **Aplicaciones administradas por directivas:** las operaciones de cortar, copiar y pegar solo se permiten entre aplicaciones administradas por directivas.
  -   **Aplicaciones administradas por directivas con pegar:** permite cortar o copiar datos entre aplicaciones administradas por directivas. Permite que los datos cortados o copiados desde cualquier aplicación se peguen en esta aplicación.
  -   **Cualquier aplicación:** no se aplican restricciones a las operaciones de cortar, copiar y pegar entre cualquier aplicación.

    **Valor predeterminado = Aplicaciones administradas por directivas con pegar**
-   **Restringir contenido web para mostrar en el Managed Browser:** cuando se habilita esta opción, los vínculos en la aplicación se abrirán en Managed Browser.

  En el caso de los dispositivos que no estén inscritos en Intune, los vínculos web en aplicaciones administradas por directivas solo se abrirán en la aplicación Managed Browser mediante la directiva de administración de aplicaciones móviles.

  Si usa Intune para administrar los dispositivos, vea [Administrar el acceso a Internet mediante directivas de explorador administrado con Microsoft Intune](manage-internet-access-using-managed-browser-policies.md).

    **Valor predeterminado = Sí**
- **Cifrar datos de aplicación:** elija **Sí** para permitir el cifrado. Si esta opción se habilita, Microsoft proporciona el cifrado en el caso de las aplicaciones asociadas a una directiva de administración de aplicaciones móviles de Intune. Los datos se cifran de forma sincrónica durante las operaciones de E/S de archivo. El contenido del almacenamiento del dispositivo estará siempre cifrado.
  >[!NOTE]
  >El método de cifrado no está certificado mediante FIPS 140-2.

  **Valor predeterminado = Sí**

- **Deshabilitar la sincronización de contactos:** elija **Sí** para evitar que la información de contacto se sincronice con la aplicación nativa de libreta de direcciones del dispositivo. Si elige **No**, la aplicación guardará la información de contacto en la aplicación nativa de libreta de direcciones del dispositivo.<br/>Al realizar una eliminación selectiva para quitar datos de la empresa, se quitan los contactos sincronizados directamente desde la aplicación a la libreta de direcciones nativa. No se pueden borrar los contactos de la libreta de direcciones nativa sincronizados con otro origen externo. Actualmente esto es válido únicamente para **Microsoft Outlook**.

  **Valor predeterminado = Sí**

##  Configuración de directiva de acceso de Android
El término **aplicaciones administradas por directiva** hace referencia a las aplicaciones que están configuradas con directivas de MAM.

- **Requerir PIN para el acceso:** elija **Sí** si quiere exigir un PIN para poder usar aplicaciones administradas por directivas. Se pedirá al usuario que lo configure la primera vez que ejecuta la aplicación en un contexto laboral.

 **Valor predeterminado = Sí**

 -  **Permitir el PIN simple:** especifique si quiere permitir que los usuarios usen secuencias de PIN simples como 1234 o 1111. **Valor predeterminado = Sí**.
 - **Longitud de PIN:**especifique el número mínimo de dígitos en un PIN. **Valor predeterminado = 4**
 - **Número de intentos antes del restablecimiento del PIN:** especifique el número de intentos de entrada de PIN que pueden realizarse antes de que el usuario deba restablecer el PIN. **No hay ningún valor predeterminado para esta configuración.**
- **Requerir credenciales corporativas para el acceso:** elija **Sí** para solicitar credenciales corporativas en lugar de un PIN para tener acceso a la aplicación.  Si se establece en **Sí**, se reemplazarán los requisitos de introducción de un PIN o un Touch ID.  Se le solicitará al usuario que proporcione sus credenciales corporativas.

  **Valor predeterminado = No**
- **Bloquear las aplicaciones administradas para que no se ejecuten en dispositivos con jailbreak o rooting:** elija **Sí** para impedir que las aplicaciones se ejecuten en dispositivos descodificados o descifrados. El usuario seguirá siendo capaz de usar las aplicaciones para las tareas personales, pero tendrá que usar un dispositivo distinto para el trabajo.

  **Valor predeterminado = Sí**
- **Volver a comprobar los requisitos de acceso tras (minutos)**-   **Tiempo de espera:** tiempo (en minutos) que debe transcurrir antes de que se vuelvan a comprobar los requisitos de acceso de la aplicación.
  -   **Período de gracia sin conexión:** si el dispositivo está desconectado, especifique el tiempo (en minutos) que debe transcurrir antes de que se vuelvan a comprobar los requisitos de acceso de la aplicación.

    **Valor predeterminado = Tiempo de espera de 30 minutos y 720 minutos de período de gracia sin conexión**

-   **Intervalo sin conexión (días) antes de que se borren los datos de la aplicación:** puede borrar los datos de empresa si un dispositivo ha estado desconectado durante un período determinado.  Especifique el número de días que un dispositivo puede estar sin conexión antes de que se eliminen los datos de la compañía del dispositivo. **Sugerencia:** Si introduce un valor de 0 esta opción se desactivará.

  **Valor predeterminado = 90 días**
- **Bloquear captura de pantalla y asistente de Android (Android 6 Marshmallow o posterior):** elija **Sí** para bloquear las capacidades de captura de pantalla y de **asistente de Android** del dispositivo cuando se use esta aplicación.



<!--HONumber=Jun16_HO4-->


