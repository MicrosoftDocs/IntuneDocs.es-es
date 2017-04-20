## <a name="enable-windows-10-automatic-enrollment"></a>Habilitar la inscripción automática de Windows 10

Con la inscripción automática, los usuarios pueden inscribir en Intune equipos Windows 10 corporativos o personales y dispositivos Windows 10 Mobile agregando una cuenta profesional o educativa y aceptando su administración. Así de fácil. En segundo plano, el dispositivo del usuario se registra y se une a Azure Active Directory. Una vez registrado, el dispositivo se administra con Intune.

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

4. Configurar los usuarios que se inscribirán automáticamente.

  ![Captura de pantalla de Azure Portal](../media/auto-enroll-scope.png)

  Use los valores predeterminados para las siguientes direcciones URL:
  - **Inscripción de MDM**
  - **Condiciones de uso de MDM**
  - **Cumplimiento de MDM**

5. Especifique los dispositivos de los usuarios que se deben administrar mediante Microsoft Intune. Los dispositivos Windows 10 de estos usuarios se inscribirán automáticamente para la administración con Microsoft Intune.

  - **Todos**
  - **Grupos**
  - **Ninguno**

6. Seleccione **Guardar**.
