---
title: Solución de problemas del uso de perfiles de certificados SCEP para aprovisionar certificados con Microsoft Intune | Microsoft Docs
description: Solucione el uso de SCEP por parte de los dispositivos para solicitar certificados para usarlos con Intune, incluida la comunicación desde dispositivos a NDES, desde NDES a entidades de certificación y desde Intune Certificate Connector hasta el servicio Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/30/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 38bc86b1b9ba85eb7885a0e00673e551821063c1
ms.sourcegitcommit: 459b0ee01eb6e69cc0ce66d4c4b81d73f510f96d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2020
ms.locfileid: "77034250"
---
# <a name="overview-for-troubleshooting-scep-certificate-profiles-with-microsoft-intune"></a>Información general para solucionar problemas de los perfiles de certificados SCEP con Microsoft Intune

El uso de perfiles de certificados Protocolo de inscripción de certificados simple (SCEP) puede ser un desafío para solucionar problemas en Intune. En este artículo se proporciona información general para ayudarlo a solucionar problemas, que incluye:

- Una explicación de la arquitectura y el flujo de comunicación del proceso SCEP
- Ayuda para reducir el lugar donde existe un problema en ese flujo de comunicación
- La identificación de los archivos de registro de clave a los que se hace referencia en artículos subsiguientes para solucionar problemas con los perfiles de certificado

La información en este y otros artículos relacionados sobre la solucionar problemas de los certificados SCEP se aplica al uso de los perfiles de certificados SCEP con dispositivos Android, iOS/iPAD y Windows. En este momento no hay disponible información similar para macOS.

Para solucionar problemas del Servicio de inscripción de dispositivos de red (NDES), consulte los artículos siguientes de support.microsoft.com:

- [Comprobar la configuración local de NDES para los certificados SCEP en Intune](https://support.microsoft.com/help/4490130/ndes-configuration-on-premises-for-scep-certificates-in-intune)
- [Troubleshooting NDES configuration for use with Microsoft Intune certificate profiles]( https://support.microsoft.com/help/4459540/troubleshoot-ndes-configuration-for-use-with-intune) (Solución de problemas de configuración de NDES para su uso con perfiles de certificados de Microsoft Intune)

Antes de continuar, asegúrese de haber cumplido los [requisitos previos para usar perfiles de certificados SCEP](certificates-scep-configure.md#prerequisites-for-using-scep-for-certificates), incluida la implementación de un certificado raíz a través de un perfil de certificado de confianza.

## <a name="scep-communication-flow-overview"></a>Información general del flujo de comunicación de SCEP

En el gráfico siguiente se muestra información básica del proceso de comunicación de SCEP en Intune.

![Flujo del perfil de certificado SCEP](../protect/media/troubleshoot-scep-certificate-profiles/scep-certificate-profile-flow.png)

1. [Implementación de un perfil de certificado SCEP](troubleshoot-scep-certificate-profile-deployment.md). Intune genera una cadena de desafío, que requiere un usuario específico, un propósito del certificado y un tipo de certificado.

2. [Comunicación del dispositivo al servidor NDES](troubleshoot-scep-certificate-device-to-ndes.md). El dispositivo usa el URI para NDES desde el perfil para ponerse en contacto con el servidor NDES a fin de que pueda presentar un desafío.

3. [Comunicación de NDES al módulo de directivas](troubleshoot-scep-certificate-ndes-policy-module.md). NDES reenvía el desafío al módulo de directivas de Intune Certificate Connector en el servidor, el que valida la solicitud.

4. [NDES a la entidad de certificación](troubleshoot-scep-certificate-ndes-policy-module.md). NDES pasa solicitudes válidas para emitir un certificado a la entidad de certificación (CA).

5. [Entrega del certificado al dispositivo](troubleshoot-scep-certificate-delivery.md). El certificado se entrega al dispositivo.

6. [Informes de la implementación en Intune](troubleshoot-scep-certificate-reporting.md). Intune Certificate Connector informa del evento de emisión de certificados a Intune.

## <a name="log-files"></a>Archivos de registro

Para identificar los problemas del flujo de trabajo de comunicación y aprovisionamiento de certificados, revise los archivos de registro de la infraestructura del servidor y de los servidores. Secciones posteriores de la solución de problemas de perfiles de certificado SCEP hacen referencia a los archivos de registro mencionados en esta sección.

- [Registros de infraestructura y servidor](#logs-for-on-premises-infrastructure)

Los registros de dispositivos dependen de la plataforma del dispositivo:  

- [iOS e iPadOS](#logs-for-ios-and-ipados-devices)
- [Android](#logs-for-android-devices)
- [Windows](#logs-for-windows-devices)

### <a name="logs-for-on-premises-infrastructure"></a>Registros para la infraestructura local
  
La infraestructura local que admite el uso de perfiles de certificados SCEP para las implementaciones de certificados incluye Microsoft Intune Certificate Connector, NDES que se ejecuta en una instancia de Windows Server y la entidad de certificación.

Los archivos de registro de estos roles incluyen el Visor de eventos de Windows, consolas de certificado y varios archivos de registro específicos de Intune Certificate Connector, NDES u otros roles y operaciones que forman parte de la infraestructura local.

En la lista siguiente se incluyen consolas o registros a los que se hace referencia en los artículos de solución de problemas de SCEP posteriores. 

- **NDESConnector_date_time.svclog**:

  Este registro muestra la comunicación desde Microsoft Intune Certificate Connector al servicio en la nube de Intune. Puede usar la [herramienta del visor de seguimiento de servicio](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) para ver este archivo de registro.

  Clave del Registro relacionada: *HKLM\SW\Microsoft\MicrosoftIntune\NDESConnector\ConnectionStatus*

  Ubicación: en el servidor que hospeda NDES en *%program_files%\Microsoft intune\ndesconnectorsvc\logs\logs*

- **CertificateRegistrationPoint_date_time.svclog**:

  este registro muestra el módulo de directivas de NDES que recibe y comprueba las solicitudes de certificado. Puede usar la [herramienta del visor de seguimiento de servicio](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) para ver este archivo de registro.

  Ubicación: en el servidor que hospeda NDES en *%program_files%\Microsoft intune\ndesconnectorsvc\logs\logs*

- **NDESPlugin.log**:

  este registro muestra el paso de las solicitudes de certificado al punto de registro de certificados y la comprobación que resulta de esas solicitudes.

  Ubicación: en el servidor que hospeda NDES en *%program_files%\Microsoft Intune\NDESPolicyModule\logs*

- **Registros de IIS**:

  los registros de IIS muestran las solicitudes de certificado de los dispositivos móviles que entran en NDES.

  Ubicación: en el servidor que hospeda NDES en *c:\inetpub\logs\LogFiles\W3SVC1*

- **Registro de aplicaciones para Windows**:

  este registro es útil cuando se investigan problemas de IIS, como el grupo de aplicaciones de SCEP.

  Ubicación: En el servidor que hospeda NDES: ejecute **eventvwr.msc** para abrir el Visor de eventos de Windows




### <a name="logs-for-android-devices"></a>Aplicaciones para dispositivos Android

En el caso de los dispositivos que ejecutan Android, use el archivo de registro de la aplicación **Portal de empresa de Android**, **OMADM.log**. Antes de recopilar y revisar registros, asegúrese de que la opción [Registro detallado](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android) esté habilitada y, luego, reproduzca el problema.

Para recopilar OMADM.logs desde un dispositivo, consulte [Carga y envío por correo electrónico de los registros mediante un cable USB](/intune-user-help/send-logs-to-your-it-admin-using-cable-android).

También puede consultar la sección sobre [carga y envío por correo electrónico de los registros](/intune-user-help/send-logs-to-your-it-admin-by-email-android#upload-and-email-logs-from-microsoft-intune-app) para más ayuda.

### <a name="logs-for-ios-and-ipados-devices"></a>Registros para dispositivos iOS e iPadOS

En el caso de los dispositivos que ejecutan iOS o iPadOS, puede usar registros de depuración y **Xcode** que se ejecuta en un equipo Mac:

1. Conecte el dispositivo iOS con el equipo Mac y, luego, vaya a **Aplicaciones** > **Utilidades** para abrir la aplicación de consola. 

2. En **Acción**, seleccione **Incluir mensajes de información** e **Incluir mensajes de depuración**.

   ![Selección de opciones de registro](../protect/media/troubleshoot-scep-certificate-profiles/message-options.png)

3. Reproduzca el problema y, a continuación, guarde los registros en un archivo de texto:
   1. Seleccione **Editar** > **Seleccionar todo** para seleccionar todos los mensajes de la pantalla actual y, luego, seleccione **Editar** > **Copiar** para copiar los mensajes en el Portapapeles. 
   2. Abra la aplicación TextEdit, pegue los registros copiados en un archivo de texto nuevo y, a continuación, guarde el archivo.


El registro de Portal de empresa para dispositivos iOS e iPadOS no contiene información sobre los perfiles de certificado SCEP.

### <a name="logs-for-windows-devices"></a>Registros para dispositivos Windows

En el caso de los dispositivos que ejecutan Windows, use los registros de eventos de Windows para diagnosticar problemas de inscripción o de administración de dispositivos en los dispositivos que administra con Intune.

En el dispositivo, abra **Visor de eventos** > **Registros de aplicaciones y servicios-**  > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider**

![Registros de eventos de Windows](../protect/media/troubleshoot-scep-certificate-profiles/windows-event-log.png)

## <a name="next-steps"></a>Pasos siguientes

Revise la [implementación de perfiles de certificado SCEP](troubleshoot-scep-certificate-profile-deployment.md) 
