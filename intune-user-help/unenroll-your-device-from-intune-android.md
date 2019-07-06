---
title: Cómo quitar un dispositivo Android de Intune | Microsoft Docs
description: Quitar un dispositivo Android del Portal de empresa de Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f40aab26-7613-48cc-a74e-de83df9465a4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: b68ea31a6c5d902e66c0eda8127e0f68383910f8
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2019
ms.locfileid: "67529128"
---
# <a name="unenroll-your-android-device-from-management"></a>Anular la inscripción del dispositivo Android de la administración  

Quite un dispositivo Android inscrito para que ya no lo administre la organización. En este artículo se describe cómo quitar un dispositivo de la aplicación Portal de empresa. Una vez que se ha quitado el dispositivo:  

* El dispositivo pierde el acceso a datos y recursos protegidos de la organización.
* El dispositivo ya no aparece en el Portal de empresa.
* Usted no podrá instalar aplicaciones desde el Portal de empresa.
* Dejará de aplicarse cualquier configuración que se modificara en el dispositivo al agregarlo, por ejemplo, deshabilitar la cámara o exigir una determinada longitud de la contraseña.  

> [!NOTE]
> No se puede anular la inscripción o quitar un dispositivo de empresa de la aplicación de Microsoft Intune. El dispositivo se inscribió durante la instalación inicial del dispositivo y debe inscribirse para obtener acceso a recursos de su organización.  

1. En el Portal de empresa, vaya a la esquina superior derecha y pulse los tres puntos verticales. El menú de acción se abre.

   ![Captura de pantalla de la aplicación Portal de empresa de Android con el menú de acciones abierto en la esquina superior derecha. La nueva opción "quitar portal de empresa" está disponible como la tercera opción, debajo de "mi perfil" y "configuración" y sobre "términos y condiciones", "ayuda y comentarios" e "información".](./media/android_remove_cp_menu_action_after_1705.png)

2. Pulse **Quitar Portal de empresa**.  

3. Aparece un mensaje en el que se proporciona información sobre lo que sucede cuando se anula la inscripción del dispositivo. Pulse **Aceptar** para confirmar que quiere quitar el dispositivo del Portal de empresa.

   ![Captura de pantalla de la confirmación que está disponible después de seleccionar la nueva opción "Quitar el Portal de empresa" del menú de acciones.](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="remove-data-collected-by-the-company-portal-app"></a>Eliminación de datos recopilados por la aplicación Portal de empresa  

Para quitar todos los datos que la aplicación Portal de empresa para Android almacena en el dispositivo:

- Para borrar los datos de la aplicación, pulse **Aplicaciones** > **[*nombre de la aplicación*]**  > **Borrar datos**.
- Elimine la siguiente carpeta: \storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal.

## <a name="uninstall-the-company-portal-app"></a>Desinstalación de la aplicación Portal de empresa  
Portal de empresa es una aplicación de administración de dispositivos. No se puede desinstalar mientras no se anule la inscripción del dispositivo de la administración. Una vez hecho esto, mantenga pulsado el icono de la aplicación Portal de empresa hasta que vea **Desinstalar**. Pulse **Desinstalar** para quitar la aplicación del dispositivo.  

También puede pulsar **Configuración** > **Aplicaciones** > **Portal de empresa** > **Desinstalar**.  

### <a name="remove-the-company-portal-app-as-a-device-administrator"></a>Quitar la aplicación Portal de empresa como administrador de dispositivos  
Como último recurso, puede desinstalar la aplicación del dispositivo como administrador del dispositivo.  

Si tiene un dispositivo propiedad de su empresa, su organización puede requerir que el Portal de empresa esté instalado en el dispositivo en todo momento. Si lo desinstala, podría perder acceso a los recursos protegidos de la compañía, como correo electrónico, aplicaciones, Wi-Fi o VPN, hasta que se vuelva a instalar la aplicación. Para obtener más información sobre la instalación, la actualización o la eliminación de las aplicaciones necesarias, vea [Agregar aplicaciones a Microsoft Intune](https://docs.microsoft.com/intune/apps-add#apps-that-are-added-automatically-by-intune).  

Aquí le indicamos cómo deshabilitar el Portal de empresa como administrador del dispositivo. Los nombres reales de cada configuración pueden variar en su dispositivo Android.  

**Opción 1**:  
1. Seleccione **Configuración** > **Seguridad** > **Configuración de seguridad adicional** > **Administradores de dispositivos** .  
2. Desactive la opción **Portal de empresa**.  

**Opción 2**:  
1. Seleccione **Configuración** > **Pantalla de bloqueo y seguridad** > **Otras configuraciones de seguridad** > **Aplicaciones de administración de dispositivos**.  
2. Desactive la opción **Portal de empresa**.    

¿Sigue necesitando ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
