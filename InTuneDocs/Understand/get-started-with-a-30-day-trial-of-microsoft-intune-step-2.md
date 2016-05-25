---
# required metadata

title: Agregar usuarios a la evaluación de 30 días de Microsoft Intune | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 9e40999b-46f7-447b-8974-72af82bec7ef

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Agregar usuarios a la evaluación de 30 días de Microsoft Intune
Ahora que ha configurado su cuenta, podrá usar el asistente de **Nuevos usuarios** para agregar cuentas de usuario individuales a Intune, o bien el asistente de **Agregar usuarios en masa** para agregar usuarios en masa (vea las instrucciones en esta sección).  Antes de empezar, es importante que comprenda cómo Intune administra las cuentas de administrador.

Un administrador de inquilinos usa el Centro de administración de Office 365 para agregar usuarios al **grupo Usuarios** de Microsoft Intune. Agregar usuarios al  **Grupo de usuarios** asigna licencias de suscripción de Intune a los usuarios y también es la forma de hacer que esos usuarios aparezcan en la consola de administración de Microsoft Intune.

Las cuentas de administrador de Intune no se crean en el Centro de administración de Office 365, como ocurre con las cuentas de usuario normales. En su lugar, puede asignar a los usuarios derechos administrativos, ya sean de acceso de solo lectura o bien de acceso completo, mediante la consola de administración del área de trabajo **Administración** en **Administration Management (Gestión de la administración)**. Los administradores de servicios a los que se les asigna el acceso de solo lectura no pueden cambiar la configuración de Intune, pero pueden ver los datos y ejecutar informes. Los administradores de servicios con acceso completo tienen todos los derechos administrativos disponibles.

Puede ver la información del Administrador de inquilinos mediante la consola de administración de Intune, pero no puede crear administradores de inquilinos con ella. De forma predeterminada, el propietario de la suscripción se convierte en administrador de inquilinos del servicio de Microsoft Intune y tiene acceso completo tanto al Centro de administración de Office 365 como a la consola de administración de Intune. Le recomendamos que cree como mínimo una cuenta de administrador de inquilinos adicional mediante el Centro de administración de Office 365 para poder delegar tareas y asegurarse de que no se queda bloqueado fuera de la cuenta de administrador del servicio de Intune si olvida la contraseña.

## Agregar cuentas de usuario individuales
Use los pasos siguientes para crear cuentas de usuario adicionales en el inquilino de evaluación. Recuerde que cada cuenta de usuario que agregue se contabiliza como una de las 100 licencias que obtiene como parte de la evaluación gratuita de Intune.

1.  En el [Centro de administración de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854), elija **Agregar usuarios** &gt; **Nuevo**&gt; **Usuario** para iniciar el asistente de **Nuevos usuarios**.

2.  En la página **Detalles** , rellene los campos obligatorios.

3.  En la página **Configuración** , establezca la **ubicación** del usuario.

4.  En la página **Grupo**, elija **Siguiente** para aceptar el valor predeterminado y asignar una licencia de Intune a la cuenta del usuario.

5.  En la página **Correo electrónico** , puede especificar hasta cinco direcciones de correo electrónico que recibirán notificación del nombre de usuario y la contraseña temporal de la cuenta. Use signos de punto y coma (;) para separar varias direcciones de correo electrónico. Cuando haya terminado, elija **Crear** para agregar el usuario a su suscripción.

6.  En la página **Resultados** , puede ver el nuevo nombre de cuenta y su contraseña temporal. Intune crea automáticamente la contraseña temporal.

7.  Cuando el nuevo usuario aparezca en el Centro de administración de Office 365, compruebe que el nuevo usuario se creó correctamente:

    1.  En la [consola de administración de Intune](https://manage.microsoft.com/), elija **Administrador** &gt; **Portal de empresa** y, después, desplácese a la parte inferior de la pantalla. Copie la dirección URL que se muestra en **Portal de empresa de Intune**..

    2.  Abra una nueva ventana del explorador en “modo de privacidad” (en Internet Explorer, elija **Herramientas** &gt; **Exploración de InPrivate**) o abra una nueva ventana del explorador en un dispositivo diferente y, después, vaya a la dirección URL que copió en el paso anterior. Cuando los usuarios inicien sesión por primera vez, deberán proporcionar una nueva contraseña para la cuenta.

## Agregar usuarios en masa
Para agregar usuarios en masa a Intune, use el asistente de **Agregar usuarios en masa** para cargar un archivo de valores separados por comas (CSV) que contenga los datos de usuario. En el asistente encontrará los vínculos que le permitirán descargar una plantilla en blanco y el archivo CSV de ejemplo. La primera fila del archivo CSV debe contener, en el orden correcto, cada una de las etiquetas de columna de datos de usuario. En el archivo CSV se debe incluir el **nombre de usuario** (como **juan@contoso.com**) y un **nombre para mostrar** (como **Juan Casanova**) para cada usuario.).

1.  En el [Centro de administración de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854), elija **Usuarios** &gt; **Nuevo**..

2.  Elija **Agregar en masa** para iniciar el asistente de Agregar usuarios en masa.

3.  En la página **Seleccionar archivo**, elija **Examinar** para especificar y cargar un archivo CSV existente desde su equipo. También puede descargar un archivo CSV de ejemplo o el archivo de plantilla en blanco mediante los vínculos del asistente.

4.  En la página **Comprobación**, revise los resultados y elija **Ver** para obtener más detalles.

5.  En la página **Configuración**, compruebe que el estado de inicio de sesión es **Permitido** y establezca la **ubicación**. Esta configuración se aplica a todas las cuentas de usuarios agregadas mediante el archivo CSV.

6.  En la página **Grupo**, elija **Siguiente** para aceptar los valores predeterminados y asignar una licencia para Intune a todas las cuentas de usuarios agregadas mediante el archivo CSV. De manera predeterminada, la casilla está seleccionada, lo que asigna una licencia para Intune a cada cuenta.

7.  En la página **Correo electrónico**, puede especificar hasta cinco direcciones de correo electrónico para que reciban una notificación de los nombres de usuario y contraseñas temporales que Intune crea para cada cuenta. Separe varias direcciones de correo electrónico con punto y coma (;). Elija **Crear** para agregar los usuarios a la suscripción.

8.  En la página **Resultados** puede ver los nombres de cuenta y las contraseñas temporales para cada cuenta de usuario.

Cada cuenta de usuario que ha agregado mediante importación, aparece ahora en el nodo **Usuarios** del Centro de administración de Office 365. Cuando los nuevos usuarios inicien sesión por primera vez, deberán especificar una nueva contraseña para su cuenta de usuario.

### Pasos siguientes
Enhorabuena. Acaba de completar el paso 2 del tutorial de *evaluación de Microsoft Intune*.

>[!div class="step-by-step"]

>[&larr; **Registrarse en una evaluación**](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-1.md)     [**Crear grupos** &rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md)  


<!--HONumber=May16_HO1-->


