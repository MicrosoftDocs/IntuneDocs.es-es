---
title: "Aplicación de directivas de cumplimiento en los dispositivos administrados por Jamf"
titlesuffix: Azure portal
description: Use el cumplimiento para ayudar a proteger los dispositivos administrados por Jamf.
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/30/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 06cc4d70b30ec92946baefbc020aa4cda28b0c88
ms.sourcegitcommit: 520eb7712625e129b781e2f2b9fe16f9b9f3d08a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2017
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Aplicación del cumplimiento en equipos Mac administrados con Jamf Pro

|Se aplica a: Intune en Azure Portal |
|--|
|¿Busca información sobre Intune en el portal clásico? [Vaya aquí](/intune/introduction-intune?toc=/intune-classic/toc.json).|
| |

|Actualmente en versión preliminar privada|
|--|
|Las características que se describen en este tema solo están disponibles para los clientes que dispongan actualmente de la versión preliminar privada. Este mensaje se eliminará cuando se haya publicado para todos los clientes.|
| |

Puede usar Azure Active Directory y las directivas de acceso condicional de Microsoft Intune garantizan que los usuarios finales son compatibles con los requisitos de la organización. Puede aplicar estas directivas en los equipos Mac que se [administran con Jamf Pro](conditional-access-integrate-jamf.md). Esto requiere acceso tanto a la consola de Intune como a la consola de Jamf Pro.

## <a name="set-up-device-compliance-policies-in-intune"></a>Configuración de las directivas de cumplimiento de dispositivos en Intune

1. Abra Microsoft Azure y, luego, navegue a **Intune** > **Cumplimiento de dispositivos** > **Directivas**. Puede crear directivas para macOS, incluida la elección de una serie de acciones (por ejemplo, el envío de correos electrónicos de advertencia) a usuarios y grupos no compatibles.
2. Busque los grupos deseados y, luego, aplíqueles las directivas.

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>Implementar la aplicación Portal de empresa para macOS en Jamf Pro

Hay dos maneras de implementar la aplicación Portal de empresa para macOS en Jamf Pro:

- Hacer que la implementación de la aplicación Portal de empresa esté disponible en Jamf Self Service, o bien,
- Como una instalación en segundo plano para que los usuarios sigan el procedimiento siguiente:

1. En un dispositivo macOS, descargue la versión actual de la [aplicación Portal de empresa para macOS](https://go.microsoft.com/fwlink/?linkid=862280).
2. Abra Jamf Pro y navegue a **Administración de equipos** > **Paquetes**.
3. Cree un paquete con la aplicación Portal de empresa para macOS y, luego, haga clic en **Guardar**.
4. Abra **Equipos** > **Directivas** y seleccione **Nuevo**.
5. Use la carga **General** para configurar opciones para la directiva. Estos valores deben ser: 
   - Desencadenador: seleccione **Inscripción completa** y **Comprobación periódica**
   - Frecuencia de ejecución: seleccione **Una vez por equipo**
6. Seleccione la carga **Paquetes** y haga clic en **Configurar**.
7. Haga clic en **Agregar** para seleccionar el paquete con la aplicación Portal de empresa.
8. Elija **Instalar** en el menú desplegable **Acción**.
9. Configure los valores del paquete.
10. Haga clic en la pestaña **Ámbito** para especificar en qué equipos se debe instalar la aplicación Portal de empresa. Haga clic en **Guardar**. La directiva ejecutará dispositivos con ámbito la próxima vez que el desencadenador seleccionado se produzca en el equipo y cumpla con los criterios establecidos en la carga **General**.

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>Crear una directiva en Jamf Pro para que los usuarios registren sus dispositivos con Azure Active Directory

> [!NOTE]
> Debe [implementar Portal de empresa](conditional-access-assign-jamf.md#require-the-company-portal-app-for-macos) para macOS antes de pasar por los pasos siguientes.  

Los usuarios finales deben iniciar la aplicación Portal de empresa a través del autoservicio de Jamf para registrar el dispositivo con Azure AD como un dispositivo administrado por Jamf Pro. Esto requerirá que los usuarios finales realicen una acción. Se recomienda [ponerse en contacto con el usuario final](end-user-educate.md) a través de correo electrónico, notificaciones de Jamf Pro o cualquier otro método para notificar a los usuarios finales que hagan clic en el botón de Jamf Self Service.

> [!WARNING]
> La aplicación Portal de empresa debe iniciarse desde Jamf Self Service para comenzar el registro de dispositivos. <br><br>Iniciar manualmente la aplicación Portal de empresa (por ejemplo, desde las carpetas Aplicaciones o Descargas) no registrará el dispositivo. Si un usuario final inicia manualmente el Portal de empresa, verá la advertencia "AccountNotOnboarded".

1. En Jamf Pro, navegue a **Equipos** > **Directivas** y cree una directiva nueva para el registro de dispositivos.
2. Configure la carga **Integración de Microsoft Intune**, incluido el desencadenador y la frecuencia de ejecución. Establezca la prioridad en **Después**.
3. Haga clic en la pestaña **Ámbito** y establezca el ámbito de la directiva en todos los dispositivos de destino.
4. Haga clic en la pestaña **Autoservicio** para hacer que la directiva esté disponible en el autoservicio de Jamf. Incluya la directiva en la categoría **Cumplimiento de dispositivos**. Haga clic en **Guardar**.

## <a name="next-steps"></a>Pasos siguientes

- [Acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Introducción al acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
