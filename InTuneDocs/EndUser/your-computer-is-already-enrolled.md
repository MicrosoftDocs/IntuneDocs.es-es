---
# required metadata

title: El equipo ya está inscrito | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8d3a40f5-99e9-48dc-9706-f7a3a23e5704

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# El equipo ya está inscrito
Está viendo esta página porque ejecutó el programa de instalación del software cliente de Intune. Sin embargo, el software ya está instalado en el equipo y el programa de instalación no puede continuar.

Esto puede deberse a:

-   El software cliente se instaló anteriormente y el programa de instalación se ejecutó de nuevo.

-   El programa de instalación se ejecutó en el equipo después de que un administrador de TI retirara el dispositivo de Intune. Después de retirar el dispositivo, puede pasar varias horas hasta que se quite el software cliente del equipo.

-   El programa de instalación ha detectado una instalación o eliminación incorrecta reciente del software cliente.

## Qué instala el programa de instalación en el equipo
El programa de instalación instala el cliente de Intune. Una vez finalizada la instalación, el software cliente continúa ejecutándose en segundo plano cuando configura el equipo para su uso con Intune. Este proceso puede tardar algún tiempo en completarse e incluye:

-   Inscribir el equipo con Intune

-   El envío del inventario del hardware del equipo y del software instalado

-   Configurar la directiva de Intune, incluida la instalación de Endpoint Protection (si está configurado)

-   Instalar Intune Center

Después de instalar Intune Center, puede usarlo para acceder al portal de empresa donde puede vincular su equipo con la cuenta profesional.

## Microsoft Intune Center
Intune Center se instala como una aplicación en el equipo después de que el equipo instale correctamente el software cliente e inscriba el equipo en Intune. Puede usar Intune Center para:

-   **Obtener aplicaciones del portal de empresa**: busque e instale las aplicaciones que el administrador de TI implementa. Al iniciar sesión por primera vez en el portal de empresa de un equipo recién inscrito, tendrá la opción de vincular la cuenta de trabajo con ese equipo.

-   **Buscar actualizaciones de software**: busque las actualizaciones de software que el administrador de Intune implementa.

-   **Iniciar un análisis del equipo con Endpoint Protection**: puede iniciar un análisis para buscar software malintencionado en el equipo.

-   **Solicitar asistencia remota**: esta opción está disponible solo cuando el sistema operativo de los equipos admite la asistencia remota.

## Validar que el software cliente está instalado o se ha quitado
**Validar si el cliente está instalado:**
La instalación del cliente de Intune está completa cuando las aplicaciones siguientes están disponibles en el equipo:

-   **Intune Center**

-   **Intune Endpoint Protection** (si el administrador de TI ha habilitado Endpoint Protection)

Si está familiarizado con el Administrador de tareas, puede buscar el servicio de cliente de Intune, que debe estar en ejecución:

-   **OmcSvc**

**Validar si se ha quitado el cliente:**
Después de desinstalar el cliente de Intune de un equipo, se quitan las aplicaciones que se instalaron cuando se instaló el cliente, incluido Intune Center.

Se quita el servicio de cliente de Intune, **OmcSvc**.

## Cómo quitar el software cliente del equipo
De forma predeterminada, varias horas después de que el administrador de TI retire el equipo de la consola de administración de Intune, se desinstalará el software cliente de Intune.

Para desinstalar manualmente el software cliente de Intune de un equipo, puede usar los siguientes pasos para forzar la desinstalación:

1.  En el equipo, abra un símbolo del sistema en modo de administrador.

2.  Vaya a la carpeta **%programfiles%\Microsoft\OnlineManagement\Common**

3.  Ejecute el comando siguiente: **ProvisioningUtil.exe /UninstallAgents /MicrosoftIntune**

Esto programará la eliminación del software cliente.



<!--HONumber=May16_HO1-->


