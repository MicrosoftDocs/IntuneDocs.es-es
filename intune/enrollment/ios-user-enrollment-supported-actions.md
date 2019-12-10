---
title: Acciones y opciones de Intune compatibles con la inscripción de usuarios de Apple
titleSuffix: Microsoft Intune
description: Obtenga información sobre qué acciones y opciones de Intune son compatibles con la inscripción de usuarios de Apple.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/2/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ffabcace189efd60e9d532172ecd1f2a048eec2c
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2019
ms.locfileid: "74562409"
---
# <a name="intune-actions-and-options-supported-with-apple-user-enrollment"></a>Acciones y opciones de Intune compatibles con la inscripción de usuarios de Apple

La inscripción de usuarios admite un subconjunto de opciones de administración de dispositivos. Si se aplica un perfil de configuración existente a un dispositivo de inscripción de usuarios, solo se aplicarán a ese dispositivo los valores de configuración admitidos por la inscripción de usuarios.

> [!NOTE]
> La compatibilidad con la inscripción de usuario de Apple en Intune se encuentra actualmente en versión preliminar.

## <a name="password-settings"></a>Configuración de contraseña

En los dispositivos de inscripción de usuarios, si configura cualquier opción de contraseña, la configuración de **Contraseñas sencillas** se establece automáticamente en **Bloquear** y se aplica un PIN de 6 dígitos.

Por ejemplo, configura el valor **Caducidad de la contraseña** e inserta esta directiva en dispositivos con usuarios inscritos. En los dispositivos, ocurre lo siguiente:
- Se omite el valor de **Caducidad de la contraseña**.
- No se permiten contraseñas sencillas, como `1111` o `1234`.
- Se aplica un PIN de 6 dígitos.

## <a name="administrator-remote-device-actions-and-options"></a>Opciones y acciones de dispositivo remoto de administrador
Los administradores pueden realizar las siguientes acciones y opciones en los dispositivos de inscripción de usuarios:
- Retirar
- Eliminar
- Bloqueo remoto
- Sincronización

No se admite ninguna de las demás acciones.

## <a name="end-user-actions"></a>Acciones del usuario final
En los dispositivos de inscripción de usuarios, los usuarios finales pueden realizar estas acciones en sus dispositivos desde la aplicación Portal de empresa y el sitio web:
- Cambiar nombre. Esta acción solo se aplica al nombre para el usuario en el Portal de empresa. No cambiará completamente el nombre del dispositivo fuera de ese contexto.
- Quitar
- Bloqueo remoto
- Comprobar estado.

## <a name="app-deployment-options"></a>Opciones de implementación de aplicaciones
Los siguientes tipos de aplicaciones se pueden implementar en dispositivos de Inscripción de usuario:
- Aplicaciones del plan de compras por volumen con licencia de usuario (VPP), incluidas las aplicaciones personalizadas
- Aplicaciones de línea de negocio (LOB)
- Aplicaciones web

## <a name="other-supported-options"></a>Otras opciones admitidas

Las siguientes opciones se admiten en Intune para dispositivos inscritos mediante la inscripción de usuarios de Apple:
- VPN por aplicación. Esta compatibilidad excluye los dominios de Safari, ya que la inscripción de usuarios no admite la configuración de Safari.
- Wi-Fi 
- Eliminación de la aplicación corporativa tras la anulación de la inscripción
- Detección de jailbreak

Se admiten las siguientes restricciones:
- Ver documentos corporativos en aplicaciones no administradas
- Ver documentos no corporativos en aplicaciones corporativas
- Permitir que las aplicaciones no administradas lean en cuentas de contactos administradas
- Tratar AirDrop como destino no administrado
- Requerir copia de seguridad cifrada
- Sincronización de aplicaciones administradas con la nube
- Acceso a Centro de control con dispositivo bloqueado
- Acceso a Centro de notificaciones con dispositivo bloqueado
- Vista Hoy con dispositivo bloqueado
- Bloquear las capturas de pantalla
- Bloquear la copia de seguridad de libros empresariales
- Bloquear la sincronización de metadatos de libros empresariales
- Requerir copia de seguridad cifrada
- Requerir detección de reloj de pulsera
- Bloquear Siri
- Bloquear Siri con el dispositivo bloqueado
- Requerir advertencias de fraude de Safari
- Bloquear el envío de diagnósticos a Apple


## <a name="options-not-supported"></a>Opciones no admitidas
Las siguientes opciones no se admiten en los dispositivos inscritos con la inscripción de usuario. Si necesita estas opciones, consulte la inscripción de dispositivos para dispositivos de propiedad personal o la inscripción automática de dispositivos para dispositivos corporativos.
- Recopilar el inventario de aplicaciones para aplicaciones fuera del volumen APFS administrado.
- Recopilar el inventario de los certificados y perfiles de aprovisionamiento fuera del volumen APFS administrado.
- Recopilar UDID y otros identificadores de dispositivo persistentes.
- La inscripción de usuarios admite un identificador de inscripción único para cada dispositivo inscrito, pero este identificador no se conserva después de la anulación de la inscripción.
- No se admiten las siguientes características de Intune debido a esta limitación:
- Perfiles de usuario de SCEP con formato de nombre del sujeto de número de serie.
- VPN de nivel de dispositivo.
- Implementación de aplicaciones VPP con licencia de dispositivos.
- Instalar aplicaciones de App Store como aplicaciones administradas.
- Control MDM de aplicaciones fuera del volumen APFS administrado.
- Las directivas de protección de aplicaciones se seguirán aplicando a estas aplicaciones. Sin embargo, no podrá asumir la administración ni implementar una versión administrada de estas aplicaciones a menos que el usuario las elimine de su dispositivo.
- Acciones, configuraciones, ajustes y comandos que requieren supervisión. 

## <a name="options-not-supported-in-preview"></a>Opciones no admitidas en la versión preliminar
- Restricciones de tipo de dispositivo de inscripción para permitir o bloquear dispositivos personales 

## <a name="known-issues-in-preview"></a>Problemas conocidos de la versión preliminar
- Revocación de licencia de VPP: No aparece una notificación de que la licencia se ha revocado. El comportamiento actual es que la revocación se realiza correctamente, pero no se notifica al usuario final. 
- Informes de aplicaciones de VPP: En el informe ubicado en Aplicaciones cliente > Aplicaciones > [nombre de la aplicación] > Estado de instalación del dispositivo, las aplicaciones VPP implementadas en los dispositivos inscritos por el usuario se notifican como "con errores", incluso cuando la aplicación se implementa correctamente en el dispositivo. 
- Informes de aplicaciones: En el caso de los tipos de aplicaciones no compatibles con la inscripción de usuarios, los informes pueden proporcionar mensajes de error irrelevantes. 
- Experiencia de las aplicaciones del Portal de empresa: Los usuarios ven todas las aplicaciones destinadas a ellos, independientemente de si se admiten para dispositivos inscritos por el usuario. 
- Experiencia de las aplicaciones del Portal de empresa: Los usuarios ven el mismo texto que indica lo que las organizaciones pueden y no pueden ver para el registro de usuarios y dispositivos.
- Si el usuario selecciona que la organización es propietaria del dispositivo durante la inscripción, el dispositivo todavía se identifica como personal en Intune, a menos que se modifique en la consola de administración o mediante Graph. 
- Destinatarios de inscripción: iPadOS no aparece en el selector de plataforma. iPadOS se admite en la versión preliminar, pero no se indica explícitamente en la consola de administración. 


## <a name="next-steps"></a>Pasos siguientes

[Configuración de la inscripción de usuarios de iOS y iPadOS](ios-user-enrollment.md)
