---
ms.openlocfilehash: 3aadafbcf9c9208e7c87504c5459731de1e402b5
ms.sourcegitcommit: 614c4c36cfe544569db998e17e29feeaefbb7a2e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "71302594"
---
## <a name="enable-windows-10-automatic-enrollment"></a>Habilitar la inscripción automática de Windows 10

La inscripción automática permite a los usuarios inscribir sus dispositivos Windows 10 en Intune. Para inscribirse, los usuarios deben agregar su cuenta profesional a los dispositivos personales o conectar dispositivos corporativos a Azure Active Directory. En segundo plano, el dispositivo se registra y se une a Azure Active Directory. Una vez registrado, el dispositivo se administra con Intune.

**Requisitos previos**
- Suscripción a Azure Active Directory Premium ([suscripción de prueba](http://go.microsoft.com/fwlink/?LinkID=816845))
- Suscripción a Microsoft Intune


### <a name="configure-automatic-mdm-enrollment"></a>Configurar la inscripción automática de MDM

1. Inicie sesión en [Azure Portal](https://portal.azure.com) y seleccione **Azure Active Directory**.

   ![Captura de pantalla de Azure Portal](../media/auto-enroll-azure-main.png)

2. Seleccione **Movilidad (MDM y MAM)** .

   ![Captura de pantalla de Azure Portal](../media/auto-enroll-mdm.png)

3. Seleccione **Microsoft Intune**.

   ![Captura de pantalla de Azure Portal](../media/auto-enroll-intune.png)

4. Configure **Ámbito de usuario de MDM**. Especifique los dispositivos de los usuarios que se deben administrar mediante Microsoft Intune. Estos dispositivos Windows 10 pueden inscribirse automáticamente para la administración con Microsoft Intune.

   - **Ninguno**: inscripción automática de MDM deshabilitada
   - **Algunos** : seleccione los **Grupos** que pueden inscribir automáticamente sus dispositivos Windows 10
   - **Todos**: todos los usuarios pueden inscribir automáticamente sus dispositivos Windows 10

      > [!IMPORTANT]
      > En el caso de los dispositivos BYOD, el ámbito de usuario MAM tiene prioridad si el ámbito de usuario MAM y el ámbito de usuario MDM (inscripción automática de MDM) están habilitados para todos los usuarios (o los mismos grupos de usuarios). El dispositivo usará las directivas de Windows Information Protection (WIP) (si las ha configurado) en lugar de inscribirse en MDM.
      >
      > En el caso de los dispositivos corporativos, el ámbito de usuario MDM tiene prioridad si ambos ámbitos están habilitados. Los dispositivos se inscriben en MDM.

   > [!NOTE]
   > El ámbito de usuario de MDM debe establecerse en un grupo de Azure AD que contenga objetos de usuario.

   ![Captura de pantalla de Azure Portal](../media/auto-enroll-scope.png)

5. Use los valores predeterminados para las siguientes direcciones URL:
    - **URL de los términos de uso de MDM**
    - **URL de detección de MDM**
    - **URL de cumplimiento de MDM**

6. Seleccione **Guardar**.

De forma predeterminada, la autenticación en dos fases no está habilitada para el servicio. En cambio, se recomienda la autenticación en dos fases al registrar un dispositivo. Para habilitar la autenticación en dos fases, configure un proveedor de autenticación en dos fases en Azure AD, así como las cuentas de usuario para la autenticación multifactor. Vea [Introducción a Servidor Azure Multi-Factor Authentication](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).
