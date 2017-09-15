## <a name="enable-windows-10-automatic-enrollment"></a>Habilitar la inscripción automática de Windows 10

La inscripción automática permite a los usuarios inscribir sus dispositivos Windows 10 en Intune. Para inscribirse, los usuarios deben agregar su cuenta profesional a los dispositivos personales o conectar dispositivos corporativos a Azure Active Directory. En segundo plano, el dispositivo se registra y se une a Azure Active Directory. Una vez registrado, el dispositivo se administra con Intune.

**Requisitos previos**
- Suscripción a Azure Active Directory Premium ([suscripción de prueba](http://go.microsoft.com/fwlink/?LinkID=816845))
- Suscripción a Microsoft Intune


### <a name="configure-automatic-mdm-enrollment"></a>Configurar la inscripción automática de MDM

1. Inicie sesión en [Azure Portal](https://portal.azure.com) y seleccione **Azure Active Directory**.

  ![Captura de pantalla de Azure Portal](../media/auto-enroll-azure-main.png)

2. Seleccione **Movilidad (MDM y MAM)**.

  ![Captura de pantalla de Azure Portal](../media/auto-enroll-mdm.png)

3. Seleccione **Microsoft Intune**.

  ![Captura de pantalla de Azure Portal](../media/auto-enroll-intune.png)

4. Configure **Ámbito de usuario de MDM**. Especifique los dispositivos de los usuarios que se deben administrar mediante Microsoft Intune. Estos dispositivos Windows 10 pueden inscribirse automáticamente para la administración con Microsoft Intune.

  - **Ninguno**: inscripción automática de MDM deshabilitada
  - **Algunos** : seleccione los **Grupos** que pueden inscribir automáticamente sus dispositivos Windows 10
  - **Todos**: todos los usuarios pueden inscribir automáticamente sus dispositivos Windows 10

      > [!IMPORTANT]
      > Si tanto el **ámbito de usuario MAM** como la inscripción automática de MDM (**el ámbito de usuario MDM**) están habilitados para un grupo, solo se habilitará MAM. MAM solo se agrega para los usuarios de ese grupo al conectar su dispositivo personal con su área de trabajo. Los dispositivos no se inscriben en MDM automáticamente.

   ![Captura de pantalla de Azure Portal](../media/auto-enroll-scope.png)

5. Use los valores predeterminados para las siguientes direcciones URL:
    - **URL de los términos de uso de MDM**
    - **URL de detección de MDM**
    - **URL de cumplimiento de MDM**

6. Seleccione **Guardar**.

De forma predeterminada, la autenticación en dos fases no está habilitada para el servicio. En cambio, se recomienda la autenticación en dos fases al registrar un dispositivo. Para habilitar la autenticación en dos fases, configure un proveedor de autenticación en dos fases en Azure AD, así como las cuentas de usuario para la autenticación multifactor. Vea [Introducción a Servidor Azure Multi-Factor Authentication](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).
