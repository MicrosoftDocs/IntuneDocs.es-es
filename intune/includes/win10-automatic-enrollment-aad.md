## <a name="enable-windows-10-automatic-enrollment"></a>Habilitar la inscripción automática de Windows 10

La inscripción automática permite que los usuarios inscriban sus dispositivos Windows 10 en Intune cuando agreguen sus cuentas profesionales a sus dispositivos de propiedad personal o cuando una sus dispositivos corporativos a la instancia de Azure Active Directory. En segundo plano, el dispositivo del usuario se registra y se une a Azure Active Directory. Una vez registrado, el dispositivo se administra con Intune.

**Requisitos previos**
- Suscripción a Azure Active Directory Premium ([suscripción de prueba](http://go.microsoft.com/fwlink/?LinkID=816845))
- Suscripción a Microsoft Intune


### <a name="configure-automatic-mdm-enrollment"></a>Configurar la inscripción automática de MDM

1. Inicie sesión en el [Portal de administración de Azure](https://portal.azure.com) (https://manage.windowsazure.com) y seleccione **Azure Active Directory**.

  ![Captura de pantalla de Azure Portal](../media/auto-enroll-azure-main.png)

2. Seleccione **Movilidad (MDM y MAM)**.

  ![Captura de pantalla de Azure Portal](../media/auto-enroll-mdm.png)

3. Seleccione **Microsoft Intune**.

  ![Captura de pantalla de Azure Portal](../media/auto-enroll-intune.png)

4. Configure **Ámbito de usuario de MDM**. Especifique los dispositivos de los usuarios que se deben administrar mediante Microsoft Intune. Los dispositivos Windows 10 de estos usuarios se inscribirán automáticamente para la administración con Microsoft Intune.

  - **Ninguno**
  - **Algunos**
  - **Todos**

   ![Captura de pantalla de Azure Portal](../media/auto-enroll-scope.png)

5. Use los valores predeterminados para las siguientes direcciones URL:
    - **URL de los términos de uso de MDM**
    - **URL de detección de MDM**
    - **URL de cumplimiento de MDM**

    > [!IMPORTANT]
    > Si un usuario es miembro de un grupo que tiene tanto la inscripción de MDM automática y MAM habilitados, y el usuario intenta unirse al área de trabajo en su dispositivo personal, entonces solo MAM está habilitado. 

6. Seleccione **Guardar**.

De forma predeterminada, la autenticación en dos fases no está habilitada para el servicio. En cambio, se recomienda la autenticación en dos fases al registrar un dispositivo. Antes de requerir la autenticación en dos fases para este servicio, debe configurar un proveedor de autenticación de dos fases en Azure Active Directory y configurar las cuentas de usuario para la autenticación multifactor. Vea [Introducción a Servidor Azure Multi-Factor Authentication](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).
