---
title: Directiva de cumplimiento de dispositivos para dispositivos Jamf
titleSuffix: Microsoft Intune
description: Use directivas de cumplimiento de Microsoft Intune con acceso condicional de Azure Active Directory para ayudar a proteger los dispositivos administrados por Jamf.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d3552eca925865eb3278b50490a6b70ee5807e2b
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502452"
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Aplicación del cumplimiento en equipos Mac administrados con Jamf Pro

Al [integrar Jamf Pro con Intune](conditional-access-integrate-jamf.md), puede usar las directivas de acceso condicional para forzar el cumplimiento en los dispositivos Mac de los requisitos de la organización.  Este artículo le ayudará en las siguientes tareas:  

- Creación de directivas de acceso condicional.
- Configuración de Jamf Pro para implementar la aplicación Portal de empresa de Intune en los dispositivos que administra con Jamf.
- Configuración de los dispositivos para que se registren en Azure AD cuando el usuario del dispositivo inicie sesión en la aplicación Portal de empresa que se inicia desde la aplicación Jamf Self Service. El registro de dispositivos establece una identidad en Azure AD que permite que las directivas de acceso condicional evalúen el dispositivo para el acceso a los recursos de la empresa.  
 
Los procedimientos descritos en este artículo requieren acceso tanto a las consolas de Intune como a las de Jamf Pro.

## <a name="set-up-device-compliance-policies-in-intune"></a>Configuración de las directivas de cumplimiento de dispositivos en Intune

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) y seleccione **Cumplimiento de dispositivo** > **Directivas**. 
2. Si usa una directiva creada anteriormente, selecciónela en la consola y vaya luego al paso siguiente de este procedimiento.  
   
   Seleccione **Crear directiva** y, a continuación, especifique los detalles de una directiva con una *Plataforma* de **macOS**. Ajuste la *Configuración* y las *Acciones en caso de incumplimiento* para que coincidan con los requisitos de su organización y a continuación, seleccione **Crear** para guardar la directiva.

3. En el panel *Información general* de las directivas, seleccione **Asignaciones**. Use las opciones disponibles para configurar los usuarios y los grupos de seguridad de Azure Active Directory (Azure AD) que reciben esta directiva. La integración de Jamf con Intune no es compatible con las directivas de cumplimiento que tienen como destino grupos de dispositivos. 

4. Al seleccionar **Guardar**, la directiva se implementa en los usuarios.  

Las directivas que se implementan se dirigen a los dispositivos que usan los usuarios asignados. Se evalúa el cumplimiento de esos dispositivos. Los dispositivos compatibles se marcan como conformes para el ajuste "*Requerir que el dispositivo esté marcado como compatible*" en Azure AD.  

> [!NOTE]
> Intune requiere que el cifrado de disco completo sea compatible.

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>Implementar la aplicación Portal de empresa para macOS en Jamf Pro

Cree una directiva en Jamf Pro para implementar el Portal de empresa de Intune. Esta directiva implementa la aplicación de Portal de empresa para que esté disponible en Jamf Self Service. Cree esta directiva antes de crear la directiva en Jamf Pro para que los usuarios registren dispositivos con Azure AD.  

Para completar el siguiente procedimiento, debe tener acceso a un dispositivo macOS y al portal de Jamf Pro. 

### <a name="to-deploy-the-company-portal-app"></a>Para implementar la aplicación Portal de empresa  

1. En un dispositivo macOS, descargue pero no instale la versión actual de la [aplicación Portal de empresa para macOS](https://go.microsoft.com/fwlink/?linkid=862280). Solo necesita una copia de la aplicación para cargar la aplicación en Jamf Pro.  

2. Abra Jamf Pro y vaya a **Computer management**(Administración de equipos) > **Packages** (Paquetes).

3. Cree un paquete con la aplicación Portal de empresa para macOS y, luego, haga clic en **Guardar**.

4. Abra **Equipos** > **Directivas** y seleccione **Nuevo**.

5. Use la carga **General** para configurar opciones para la directiva. Estos valores deben ser:
   - Desencadenador: seleccione **Inscripción completa** y **Comprobación periódica**
   - Frecuencia de ejecución: seleccione **Una vez por equipo**

6. Seleccione la carga **Paquetes** y haga clic en **Configurar**.

7. Haga clic en **Agregar** para seleccionar el paquete con la aplicación Portal de empresa.

8. Elija **Instalar** en el menú desplegable **Acción**.
9. Configure los valores del paquete.

10. Haga clic en la pestaña **Ámbito** para especificar en qué equipos se debe instalar la aplicación Portal de empresa. Seleccione **Guardar**. La directiva se ejecuta en dispositivos con ámbito la próxima vez que el desencadenador seleccionado se produzca en el equipo y cumpla con los criterios establecidos en la carga **General**.

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>Crear una directiva en Jamf Pro para que los usuarios registren sus dispositivos con Azure Active Directory  

Después de [implementar el Portal de empresa](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro) para macOS a través de Jamf Pro Self Service, puede crear la directiva de Jamf Pro que registra el dispositivo de un usuario con Azure AD. 

El registro de dispositivos requiere que el usuario de un dispositivo seleccione manualmente la aplicación Portal de empresa de Intune desde dentro de Jamf Self Service. Le recomendamos que [se ponga en contacto con los usuarios finales](../fundamentals/end-user-educate.md) a través del correo electrónico, las notificaciones de Jamf Pro o cualquier otro método que use su organización para solicitarles que completen esta acción a fin de registrar sus dispositivos. 

> [!WARNING]
> El inicio manual de la aplicación Portal de empresa (por ejemplo, desde las carpetas Aplicaciones o Descargas) no registrará el dispositivo. Si el usuario de un dispositivo inicia manualmente el Portal de empresa, verá la advertencia **"AccountNotOnboarded"** .

### <a name="to-create-the-registration-policy"></a>Para crear la directiva de registro  

1. En Jamf Pro, navegue a **Computers** (Equipos) > **Policies** (Directivas) y cree una directiva nueva para el registro de dispositivos.

2. Configure la carga **Integración de Microsoft Intune**, incluido el desencadenador y la frecuencia de ejecución.

3. Haga clic en la pestaña **Scope** (Ámbito) y establezca el ámbito de la directiva en todos los dispositivos de destino.

4. Haga clic en la pestaña **Self Service** para hacer que la directiva esté disponible en Jamf Self Service. Incluya la directiva en la categoría **Cumplimiento de dispositivos**. Haga clic en **Guardar**.

## <a name="validate-intune-and-jamf-integration"></a>Validación de la integración de Intune y Jamf  

Use la consola de Jamf Pro para confirmar que la comunicación entre Jamf Pro y Microsoft Intune se realiza correctamente. 

- En Jamf Pro, vaya a **Settings**(Configuración) > **Global Management**(Administración global) > **Microsoft Intune Integration** (Integración de Microsoft Intune) y luego seleccione **Test** (Probar). 

    La consola muestra un mensaje que indica si la conexión se ha realizado correctamente o no.  

Si se produce un error en la prueba de conexión de la consola de Jamf Pro, revise la configuración de Jamf. 


## <a name="removing-a-jamf-managed-device-from-intune"></a>Eliminación de un dispositivo administrado por Jamf de Intune

Puede quitar un dispositivo administrado por Jamf de la consola de Intune si selecciona **Eliminar** en la vista **Todos los dispositivos**. La eliminación de dispositivos de forma masiva puede habilitarse si se seleccionan varios dispositivos y se hace clic en **Eliminar**.

Obtenga información sobre cómo [quitar un dispositivo administrado por Jamf en los documentos de Jamf Pro](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). También puede presentar una incidencia de soporte técnico al [soporte técnico de Jamf](https://www.jamf.com/support/) para obtener más ayuda. 

## <a name="next-steps"></a>Pasos siguientes

- [Acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Introducción al acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
