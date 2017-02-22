## <a name="set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium"></a>Configuración de la inscripción automática de Windows 10 y Windows 10 Mobile con Azure Active Directory Premium

Con la inscripción automática, los usuarios pueden inscribir en Intune equipos Windows 10 corporativos o personales y dispositivos Windows 10 Mobile agregando una cuenta profesional o educativa y aceptando su administración. Así de fácil. En segundo plano, el dispositivo del usuario se registra y se une a Azure Active Directory. Una vez registrado, el dispositivo se administra con Intune.

**Requisitos previos**
- Suscripción a Azure Active Directory Premium ([suscripción de prueba](http://go.microsoft.com/fwlink/?LinkID=816845))
- Suscripción a Microsoft Intune


### <a name="configure-automatic-mdm-enrollment"></a>Configurar la inscripción automática de MDM

1. En el [portal de administración de Azure](https://portal.azure.com) (https://manage.windowsazure.com), vaya al nodo **Active Directory** y seleccione su directorio.

2. Seleccione la pestaña **Aplicaciones**. **Microsoft Intune** aparece en la lista de aplicaciones.

    ![Aplicaciones de Azure AD con Microsoft Intune](../media/aad-intune-app.png)

3. Seleccione la flecha para **Microsoft Intune**. Se abre una página que le permite configurar Microsoft Intune.

4. Haga clic en **Configurar** para empezar a configurar la inscripción automática de MDM con Microsoft Intune.

5. Especifique las direcciones URL de Intune:

  - **Dirección URL de inscripción de MDM**: use el valor predeterminado.
  - **Dirección URL de las condiciones de uso de MDM**: use el valor predeterminado. Esta dirección URL muestra las condiciones de uso de los usuarios al efectuar la inscripción de los dispositivos.
  - **Dirección URL de cumplimiento de MDM**: use el valor predeterminado. Si un dispositivo no sigue el cumplimiento, aparecerá el mensaje **Acceso denegado** con esta dirección URL. La dirección URL señala a una página que ayuda a los usuarios a comprender el motivo por el que el dispositivo no cumple la directiva y cómo pueden corregir esta situación.

6.  Especifique los dispositivos de los usuarios que se deben administrar mediante Microsoft Intune. Los dispositivos Windows 10 de estos usuarios se inscribirán automáticamente para la administración con Microsoft Intune.

  - **Todos**
  - **Grupos**
  - **Ninguno**

7. Elija **Guardar**.


<!--HONumber=Feb17_HO2-->


