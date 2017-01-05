## <a name="azure-active-directory-enrollment"></a>Inscripción de Azure Active Directory

Con la inscripción automática, los usuarios pueden inscribir en Intune equipos Windows 10 corporativos o personales y dispositivos Windows 10 Mobile agregando una cuenta profesional o educativa y aceptando su administración. Así de fácil. En segundo plano, el dispositivo del usuario se registra y se une a Azure Active Directory. Una vez registrado, el dispositivo se administra con Intune.

**Requisitos previos**
- Suscripción a Azure Active Directory Premium ([suscripción de prueba](http://go.microsoft.com/fwlink/?LinkID=816845))
- Suscripción a Microsoft Intune


### <a name="configure-automatic-mdm-enrollment"></a>Configurar la inscripción automática de MDM

1. En el [portal de administración de Azure](https://manage.windowsazure.com) (https://manage.windowsazure.com), vaya al nodo **Active Directory** y seleccione su directorio.

2. Haga clic en la pestaña **Aplicaciones**, donde debería ver **Microsoft Intune** en la lista de aplicaciones.

    ![Aplicaciones de Azure AD con Microsoft Intune](../media/aad-intune-app.png)

3. Haga clic en la flecha de **Microsoft Intune**. Debería ver una página que le permite configurar Microsoft Intune.

4. Haga clic en **Configurar** para empezar a configurar la inscripción automática de MDM con Microsoft Intune.

5. Especifique las direcciones URL de Intune:

  - **Dirección URL de inscripción de MDM**: use el valor predeterminado.
  - **Dirección URL de las condiciones de uso de MDM**: use el valor predeterminado. Esta dirección URL muestra las condiciones de uso de los usuarios al efectuar la inscripción de los dispositivos.
  - **Dirección URL de cumplimiento de MDM**: use el valor predeterminado. Si un dispositivo no sigue el cumplimiento, aparecerá el mensaje **Acceso denegado** con esta dirección URL. La dirección URL señala a una página que indica al usuario el motivo por el que el dispositivo no cumple la directiva y cómo puede corregir esta situación.

6.  Especifique los dispositivos de los usuarios que se deben administrar mediante Microsoft Intune. Los dispositivos Windows 10 de estos usuarios se inscribirán automáticamente para la administración con Microsoft Intune.

  - **Todos**
  - **Grupos**
  - **Ninguno**

7. Elija **Guardar**.


<!--HONumber=Jan17_HO1-->


