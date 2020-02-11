---
title: Códigos de error de instalación de aplicaciones
titleSuffix: Microsoft Intune
description: Use los códigos de error de instalación de aplicaciones para solucionar problemas de instalación.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/27/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3502b1c1a73a9e98ed2901fc24dc69ab09136427
ms.sourcegitcommit: b0d683917af83170f85022b270270d8ced8e301c
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76812435"
---
# <a name="intune-app-installation-error-reference"></a>Referencia de errores de instalación de aplicaciones de Intune

Además de seguir los pasos proporcionados para solucionar los errores de la aplicación, también puede obtener información basada en los códigos de error devueltos. Una vez que encuentre un código de error, use la descripción y la información adicionales para ayudar a resolver el error.

## <a name="android-app-installation-errors"></a>Errores de instalación de aplicaciones Android

En esta sección se menciona la inscripción de administrador de dispositivos (DA) y Samsung Knox. Para obtener más información, consulte [Inscripción del administrador de dispositivos Android](../enrollment/android-enroll-device-administrator.md) y [Inscripción automática de dispositivos Android mediante Knox Mobile Enrollment de Samsung](../enrollment/android-samsung-knox-mobile-enroll.md). 

| Código de error (Hex) | Código de error (Dec) | Mensaje o código de error | Descripción |
|--------------------|------------------|---------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0xC7D14FB5 | -942583883 | No se pudo instalar la aplicación.  | Este mensaje de error se muestra cuando Intune no puede determinar la causa del error de instalación de la aplicación de Android. Durante el error Android, no proporcionó ninguna información. Este error se devuelve cuando la descarga de APK se realiza correctamente, pero no se puede instalar la aplicación. Este error se puede producir con más frecuencia debido a un archivo APK incorrecto que no se puede instalar en el dispositivo. Una posible causa puede ser cuando Google Play Protect bloquea la instalación de la aplicación por motivos de seguridad.   Otra causa posible de este error es cuando un dispositivo no es compatible con la aplicación. Por ejemplo, si la aplicación requiere la versión 21+ de la API y el dispositivo actualmente tiene la versión 19. Intune devuelve este error para los dispositivos DA y KNOX y, aunque puede haber una notificación de que los usuarios pueden hacer clic para volverlo a intentar, si hay un problema con el APK, nunca seguirá generando un error. Si la aplicación es una aplicación disponible, la notificación se puede descartar. Pero si la aplicación es requerida, no se podrá descartar. |
| 0xC7D14FBA | -942583878 | La instalación de la aplicación se ha cancelado porque el archivo de instalación (APK) se ha eliminado después de la descarga, pero antes de la instalación.  | La descarga del archivo APK se realizó correctamente pero, antes de que el usuario instalara la aplicación, el archivo se quitó del dispositivo. Esto podría ocurrir si se ha producido una diferencia de tiempo considerable entre la descarga y la instalación. Por ejemplo, el usuario canceló la instalación original, esperó y, después, hizo clic en la notificación para intentarlo de nuevo.   Este mensaje de error solo se devuelve para escenarios de DA. Los escenarios de KNOX se pueden realizar en modo silencioso. Se presenta una notificación de reintento para que el usuario pueda aceptar en lugar de cancelar. Si la aplicación es una aplicación disponible, la notificación se puede descartar. Pero si la aplicación es requerida, no se podrá descartar. |
| 0xC7D14FBB | -942583877 | La instalación de la aplicación se ha cancelado porque el proceso se ha reiniciado durante la instalación.  | El dispositivo se ha reiniciado durante el proceso de instalación de APK, lo que resultó en una instalación cancelada. Este mensaje de error se devuelve para los dispositivos DA y KNOX. Intune presenta una notificación en la que los usuarios pueden hacer clic para volver a intentarlo. Si la aplicación es una aplicación disponible, la notificación se puede descartar. Pero si la aplicación es requerida, no se podrá descartar. |
| 0x87D1041C | -2016345060 | La aplicación no se encontró después de que la instalación se completara correctamente.  | El usuario desinstaló la aplicación de forma explícita. Este error no se devuelve desde el cliente. Es un error que se produce cuando la aplicación estaba instalada en algún momento pero que después el usuario desinstaló. Este error solo debería producirse para las aplicaciones necesarias. Los usuarios pueden desinstalar las aplicaciones que no son requeridas. Este error solo puede ocurrir en DA. KNOX bloquea la desinstalación de las aplicaciones administradas. En la sincronización siguiente se volverá a publicar la notificación en el dispositivo para que el usuario lo instale. El usuario puede ignorar la notificación. Este error se seguirá notificando hasta que el usuario instale la aplicación. |
| 0xC7D14FB2 | -942583886 | Error desconocido en la descarga.  | Este error aparece cuando se produce un error en la descarga. Normalmente, este error puede producirse debido a problemas de Wi-Fi o conexiones lentas. Este error solo se devuelve para escenarios de DA. Para escenarios de KNOX, no se le pide al usuario que realice la instalación; esto se puede hacer de forma silenciosa. Intune presenta una notificación en la que los usuarios pueden hacer clic para volver a intentarlo. Si la aplicación es una aplicación disponible, la notificación se puede descartar.   Pero si la aplicación es requerida, no se podrá descartar. |
| 0xC7D15078 | -942583688 | Error desconocido en la descarga. La directiva se reintentará la próxima vez que el dispositivo se sincronice.  | Este error aparece cuando se produce un error en la descarga. Normalmente, este error puede producirse debido a problemas de Wi-Fi o conexiones lentas. Este error solo se devuelve para escenarios de DA. Para escenarios de KNOX, no se le pide al usuario que realice la instalación; esto se puede hacer de forma silenciosa. |
| 0xC7D14FB1 | -942583887 | El usuario final canceló la instalación de la aplicación.  | El usuario desinstaló la aplicación de forma explícita. Este error se devuelve cuando la actividad de instalación del sistema operativo Android ha sido cancelada por el usuario. El usuario presionó el botón de cancelación cuando se presentó el mensaje de instalación del sistema operativo, o bien hizo clic fuera del mensaje. Este error solo se devuelve para escenarios de DA. Para escenarios de KNOX, no se le pide al usuario que realice la instalación; esto se puede hacer de forma silenciosa. Intune presenta una notificación en la que los usuarios pueden hacer clic para volver a intentarlo. Si la aplicación es una aplicación disponible, la notificación se puede descartar. Pero si la aplicación es requerida, no se podrá descartar. Pida al usuario que no cancele la instalación. |
| 0xC7D15015 | -942583787 | El proceso de descarga de archivo se detuvo de manera inesperada.  | El sistema operativo detuvo el proceso de descarga antes de que se completara. Este error se puede producir cuando el dispositivo tiene poca batería o la descarga está tardando demasiado. Este error solo se devuelve para escenarios de DA. Para escenarios de KNOX, no se le pide al usuario que realice la instalación, esto se puede hacer de forma silenciosa. Intune presenta una notificación en la que los usuarios pueden hacer clic para volver a intentarlo. Si la aplicación es una aplicación disponible, la notificación se puede descartar. Pero si la aplicación es requerida, no se podrá descartar. Asegúrese de que el dispositivo tiene una conexión de red confiable. |
| 0xC7D1507C | -942583684 | El servicio de descarga de archivo se detuvo de manera inesperada. La directiva se reintentará la próxima vez que el dispositivo se sincronice.  | El sistema operativo finalizó el proceso de descarga antes de que se completara. Este error se puede producir cuando el dispositivo tiene poca batería o la descarga está tardando demasiado. Este error solo se devuelve para escenarios de DA. Para escenarios de KNOX, no se le pide al usuario que realice la instalación, esto se puede hacer de forma silenciosa. Sincronice manualmente el dispositivo o espere 24 horas y compruebe el estado. |
| 0xc7d14fb8 | -942583880 | No se pudo desinstalar la aplicación.  | Este error es un error genérico de desinstalación. El sistema operativo no especificó el motivo por el que no se pudo desinstalar la aplicación. Algunas aplicaciones de administración no se pueden desinstalar sin más. Compruebe que la aplicación se puede desinstalar manualmente y recopile los registros de Portal de empresa si se produce un error en la desinstalación. |
| 0xc7d14fb7 | -942583881 | El archivo APK de instalación de la aplicación que se usa para la actualización no coincide con la firma de la aplicación actual en el dispositivo.  | El sistema operativo Android tiene la limitación de requerir que el certificado de firma para la versión de actualización sea exactamente el mismo que el certificado usado para firmar la versión existente. Si el desarrollador no puede usar el mismo certificado para firmar la nueva versión, tendrá que desinstalar la aplicación existente y volver a implementar la nueva aplicación en lugar de actualizar la aplicación existente. |
| 0xc7d14fb9 | -942583879 | El usuario final canceló la instalación de la aplicación.  | Instruya al usuario para que acepte la aplicación implementada de Intune e instale la aplicación cuando se le solicite. |
| 0xc7d14fbc | -942583876 | La desinstalación de la aplicación se ha cancelado porque el proceso se ha reiniciado durante la instalación.  | El sistema operativo finalizó el proceso de instalación de la aplicación o el dispositivo se reinició.   Vuelva a intentar la instalación y recopile los registros de Portal de empresa si se produce este error de nuevo. |
| 0xc7d14fb6 | -942583882 | No se puede instalar el archivo APK de instalación de la aplicación porque no estaba firmado.  | De forma predeterminada, el sistema operativo Android requiere que las aplicaciones estén firmadas. Asegúrese de que la aplicación está firmada antes de la implementación. |
| 0xC7D14FB1  | -942583887 | El usuario final canceló la instalación de la aplicación. | El usuario desinstaló la aplicación de forma explícita. Este error se devuelve cuando la actividad de instalación del sistema operativo Android ha sido cancelada por el usuario. El usuario presionó el botón de cancelación cuando se presentó el mensaje de instalación del sistema operativo, o bien hizo clic fuera del mensaje. Este error solo se devuelve para escenarios de DA. Para escenarios de KNOX, no se le pide al usuario que realice la instalación; esto se puede hacer de forma silenciosa. Intune presenta una notificación en la que los usuarios pueden hacer clic para volver a intentarlo. Si la aplicación es una aplicación disponible, la notificación se puede descartar. Pero si la aplicación es requerida, no se podrá descartar. Pida al usuario que no cancele la instalación. |
| 0xC7D14FB9 | -942583879 | El usuario final canceló la instalación de la aplicación. (En la solicitud de aceptación) | Instruya al usuario para que acepte la aplicación implementada de Intune e instale la aplicación cuando se le solicite. |

## <a name="ios-app-installation-errors"></a>Errores de instalación de aplicaciones iOS

Los siguientes mensajes de error y descripciones proporcionan detalles sobre los errores de instalación de iOS. 

| Código de error (Hex) | Código de error (Dec) | Mensaje o código de error | Descripción/Sugerencias de solución de problemas |
|--------------------|------------------|------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0x87D12906 | -2016335610 | Error del agente MDM de Apple: error del comando de instalación de la aplicación sin ningún motivo de error especificado. Vuelva a intentar instalar la aplicación. | El agente MDM de Apple ha devuelto que no se puede ejecutar el comando de instalación. |
| 0x87D1313C | -2016333508 | Se perdió o se interrumpió la conexión de red en el cliente. Los intentos posteriores no deberían tener problemas en un entorno de red mejor. | Se perdió la conexión de red mientras se enviaba la dirección URL del servicio de descarga actualizada al dispositivo. En concreto, no se encontró un servidor con el nombre de host especificado. |
| 0x87D11388 | -2016341112 | El dispositivo iOS está ocupado actualmente.  | El dispositivo iOS estaba ocupado, lo que provocó un error. El dispositivo estaba bloqueado. El usuario debe desbloquear el dispositivo para instalar la aplicación. |
| 0x87D13B64 | -2016330908 | Error al instalar la aplicación.  | Se ha producido un error de instalación de la aplicación. Para solucionar este error se necesitan los registros de la consola de iOS. |
| 0x87D13B66 | -2016330906 | La aplicación está administrada, pero ha expirado o el usuario la ha quitado.  | El usuario desinstaló explícitamente la aplicación o la aplicación expiró pero no se pudo descargar, o la detección de la aplicación no coincide con la respuesta del dispositivo.   Además, este error se puede producir debido a un error en la plataforma iOS 9.2.2. |
| 0x87D13B60 | -2016330912 | La aplicación está programada para la instalación, pero necesita un código de canje para completar la transacción.  | Este error se suele producir con las aplicaciones de la tienda iOS que son de pago. |
| 0x87D1041C | -2016345060 | La aplicación no se encontró después de que la instalación se completara correctamente.  | El proceso de detección de la aplicación no coincide con la respuesta del dispositivo. |
| 0x87D13B62 | -2016330910 | El usuario ha rechazado la oferta para instalar la aplicación.  | Durante la instalación de la aplicación inicial, el usuario hizo clic en Cancelar. Pida al usuario que acepte la solicitud de instalación la próxima vez. |
| 0x87D13B63 | -2016330909 | El usuario ha rechazado la oferta para actualizar la aplicación.  | El usuario final hizo clic en Cancelar durante el proceso de actualización. Implemente según sea necesario o instruya al usuario para que acepte la solicitud de actualización. |
| 0x87D103E8 | -2016345112 | Error desconocido  | Se ha producido un error desconocido durante la instalación de la aplicación. Este es el error resultante cuando no se han producido los otros. |
| 0x87D13B93 | -2016330861 | Solo se pueden instalar aplicaciones de VPP en iPad compartido. | Las aplicaciones deben obtenerse mediante el Programa de compras por volumen de Apple para instalarlas en un iPad compartido. |
| 0x87D13B94 | -2016330860 | No se pueden instalar las aplicaciones cuando la App Store está deshabilitada. | La App Store debe estar habilitada para que el usuario pueda instalar la aplicación. |
| 0x87D13B95 | -2016330859 | No se encuentra la licencia de VPP de la aplicación. | Pruebe a revocar y reasignar la licencia de aplicación. |
| 0x87D13B96 | -2016330858 | No se pueden instalar aplicaciones del sistema con el proveedor de MDM. | No se permite la instalación de aplicaciones que se instalaron previamente a través del sistema operativo iOS. |
| 0x87D13B97 | -2016330857 | No se pueden instalar aplicaciones cuando el dispositivo está en modo perdido. | En el modo perdido, se bloquea totalmente el uso del dispositivo. Para instalar aplicaciones, hay que deshabilitar el modo perdido. |
| 0x87D13B98 | -2016330856 | No se pueden instalar aplicaciones cuando el dispositivo está en pantalla completa. | Pruebe a agregar este dispositivo a un grupo de exclusión para que la directiva de configuración de pantalla completa instale las aplicaciones. |
| 0x87D13B9C | -2016330852 | No se pueden instalar aplicaciones de 32 bits en este dispositivo. | El dispositivo no admite la instalación de aplicaciones de 32 bits. Pruebe a implementar la versión de 64 bits de la aplicación. |
| 0x87D13B99 | -2016330855 | El usuario debe iniciar sesión en la App Store. | El usuario debe iniciar sesión en la App Store para que la aplicación se pueda instalar. |
| 0x87D13B9A | -2016330854 | Problema desconocido. Inténtelo de nuevo. | No se pudo instalar la aplicación debido a un motivo desconocido. Inténtelo de nuevo más tarde. |
| 0x87D13B9B | -2016330853 | Error al instalar la aplicación. Intune lo intentará de nuevo la próxima vez que el dispositivo se sincronice. | Se produjo un error de dispositivo en la instalación de la aplicación. Sincronice el dispositivo para intentar instalar la aplicación de nuevo. |
| 0x87d13b7e | -2016330882 | Error de asignación de licencia con el error de Apple "No hay licencias de VPP restantes".  | Este comportamiento es así por diseño. Para solucionarlo, adquiera licencias de VPP adicionales o recupere licencias de usuarios que ya no se usen. |
| 0x87d13b6e | -2016330898 | Error de instalación de la aplicación 12024: causa desconocida.  | Apple no nos ha proporcionado información suficiente para determinar por qué se produjo un error en la instalación.   No hay nada que notificar. |
| 0x87d13b7f | -2016330881 | Directiva de configuración de aplicaciones necesaria no presente. Asegúrese de que la directiva está destinada a los mismos grupos.  | La aplicación requiere la configuración de la aplicación, pero no hay ninguna configuración de aplicación de destino. El administrador debe asegurarse de que los grupos de destino de la aplicación también tienen la configuración de la aplicación necesaria destinada a los grupos. |
| 0x87d13b69 | -2016330903 | Las licencias de PCV de dispositivo solo se pueden aplicar a dispositivos iOS 9.0 +.  | Actualice los dispositivos iOS afectados a iOS 9.0 +. |
| 0x87d13b8f | -2016330865 | La aplicación se instala en el dispositivo, pero no está administrada.  | Este error solo se produce en aplicaciones LOB. La aplicación se instaló fuera de Intune. Para solucionar este error, desinstale la aplicación del dispositivo. La próxima vez que se produzca la sincronización del dispositivo, el dispositivo debería instalar la aplicación desde Intune. |
| 0x87d13b68 | -2016330904 | El usuario rechazó la administración de aplicaciones.  | Pida al usuario que acepte la administración de aplicaciones. |
| 0x87d1279d | -2016335971 | Error desconocido.  | Este error se produce en las aplicaciones de la tienda iOS, pero se desconoce el escenario de error. |
| 0x87D13B9D | -2016330851 | No se pudo actualizar a la versión más reciente de la aplicación desde una versión anterior.  | Este mensaje de error se muestra si la aplicación está instalada y administrada, pero con la versión incorrecta en el dispositivo. Esta situación incluye el momento en que un dispositivo ha recibido un comando para actualizar una aplicación, pero la nueva versión aún no se ha instalado y se ha comunicado un error. Este error se notificará durante la primera sincronización de un dispositivo después de la implementación de la actualización y se producirá hasta que el dispositivo informe de que la nueva versión está instalada, o el problema se debe a un error diferente. |
| 0x87D13B6F | -2016330897 | La conexión a Intune ha agotado el tiempo de espera.  | Error de validación del manifiesto de la aplicación debido a la conectividad de red (tiempo de espera). |
| 0x87D13B70 | -2016330896 | Se ha perdido la conexión a Internet.  | Error de validación del manifiesto de la aplicación debido a la conectividad de red (no se encuentra el host). |
| 0x87D13B72 | -2016330894 | Se ha perdido la conexión a Internet.  | Error de validación del manifiesto de la aplicación debido a la conectividad de red (pérdida de conexión). |
| 0x87D13B73 | -2016330893 | Se ha perdido la conexión a Internet.  | Error de validación del manifiesto de la aplicación debido a la conectividad de red (no hay conexión a Internet). |
| 0x87D13B77 | -2016330889 | Error de conexión segura.  | Error de validación del manifiesto de la aplicación debido a la conectividad de red (error de conexión segura) |
| 0x87D13B80 | -2016330880 | CannotConnectToITunesStoreError | Error en la instalación de la aplicación debido a un error al conectarse a iTunes Store. |
| 0x87D13B9F  | -2016330849 | Hay una actualización disponible para la aplicación VPP. | Este código se devuelve cuando se instala una aplicación VPP pero hay una versión más reciente disponible. |

## <a name="other-installation-errors"></a>Otros errores de instalación

| Código de error (Hex) | Código de error (Dec) | Mensaje o código de error | Descripción |
|--------------------|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0x80073CFF | -2147009281 | (error de cliente) | Para instalar esta aplicación, debe tener un sistema habilitado para instalación de prueba. Asegúrese de que el paquete de la aplicación tenga una firma de confianza y se haya instalado en un dispositivo unido a un dominio que tenga habilitada la directiva AllowAllTrustedApps o en un dispositivo que tenga una licencia de instalación de prueba de Windows con la directiva AllowAllTrustedApps habilitada. Para más información, consulte Solución de problemas de empaquetado, implementación y consulta de aplicaciones de la Tienda Windows. |
| 0x80CF201C  | -2133909476 | (error de cliente) | Para instalar esta aplicación, debe tener un sistema habilitado para instalación de prueba. Asegúrese de que el paquete de la aplicación tenga una firma de confianza y se haya instalado en un dispositivo unido a un dominio que tenga habilitada la directiva AllowAllTrustedApps o en un dispositivo que tenga una licencia de instalación de prueba de Windows con la directiva AllowAllTrustedApps habilitada. Para más información, consulte Solución de problemas de empaquetado, implementación y consulta de aplicaciones de la Tienda Windows. |
| 0x80073CF0 | -2147009296 | El paquete no está firmado.     El nombre del publicador no coincide con el sujeto que firma el certificado.     Compruebe el registro de eventos AppxPackagingOM para más información. Para más información, consulte Solución de problemas de empaquetado, implementación y consulta de aplicaciones de la Tienda Windows. | No se pudo abrir el paquete. Posibles causas: |
| 0x80073CF3 | -2147009296 | El paquete entrante entra en conflicto con un paquete instalado.     No se encuentra una dependencia del paquete especificado.     El paquete no es compatible con la arquitectura correcta del procesador.     Compruebe el registro de eventos AppXDeployment-Server para obtener información. Para más información, consulte Solución de problemas de empaquetado, implementación y consulta de aplicaciones de la Tienda Windows. | Error de actualización, dependencia o validación de conflicto en el paquete. Posibles causas: |
| 0x80073CFB | -2147009285 | Incremente el número de versión de la aplicación y, después, vuelva a compilar y a firmar el paquete.     Quite el paquete antiguo para todos los usuarios del sistema antes de instalar el nuevo.     Para más información, consulte Solución de problemas de empaquetado, implementación y consulta de aplicaciones de la Tienda Windows.      | El paquete suministrado ya está instalado y se ha bloqueado la reinstalación del paquete. Podría recibir este error si está instalando un paquete que no es idéntico al paquete que ya está instalado. Confirme que la firma digital también forma parte del paquete. Cuando un paquete se vuelve a generar o a firmar, dicho paquete ya no es idéntico bit a bit al paquete instalado previamente. Dos opciones para corregir este error son: |
| 0x87D1041C | -2016345060 | El usuario final desinstaló la aplicación.     La información de identidad en el paquete no coincide con la información del dispositivo sobre aplicaciones incorrectas.     Para los MSI de actualización automática, la versión del producto no coincide con la información de la aplicación después de que se actualiza fuera de Intune.     Indique al usuario que vuelva a instalar la aplicación desde el portal de empresa. Tenga en cuenta que las aplicaciones necesarias se reinstalarán automáticamente cuando se vuelva a registrar el dispositivo. | La instalación de la aplicación se realizó correctamente, pero esta no se detecta. La aplicación se implementó correctamente mediante Intune y luego se desinstaló. Las razones por las que la aplicación se desinstala son: |
| 0x8000FFFF | -2147418113 |   | Error inesperado durante la instalación. Compruebe los registros de instalación para obtener más información. |

## <a name="next-steps"></a>Pasos siguientes

- Para obtener información adicional sobre la solución de problemas de Intune, consulte [Uso del portal de solución de problemas para ayudar a los usuarios de su empresa](../fundamentals/help-desk-operators.md). 
- Obtenga información sobre los problemas conocidos de Microsoft Intune. Para obtener más información, vea [Éxito de clientes de Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess).
- ¿Necesita más ayuda? Consulte [Cómo obtener asistencia para Microsoft Intune](../fundamentals/get-support.md).