---
title: 'Tutorial: Protección del correo electrónico de Exchange Online en dispositivos no administrados'
titleSuffix: Microsoft Intune
description: Aprenda a proteger Office 365 Exchange Online con directivas de protección de aplicaciones de Intune y acceso condicional de Azure AD.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/21/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 810a898a3b2d1981babc231f32ed386bde37a856
ms.sourcegitcommit: ce518a5dfe62c546a77f32ef372f36efbaad473f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2019
ms.locfileid: "74465789"
---
# <a name="tutorial-protect-exchange-online-email-on-unmanaged-devices"></a>Tutorial: Protección del correo electrónico de Exchange Online en dispositivos no administrados

Obtenga información sobre el uso de directivas de protección de aplicaciones con acceso condicional para proteger Exchange Online, incluso cuando los dispositivos no están inscritos en una solución de administración de dispositivos como Intune. En este tutorial, aprenderá a:

> [!div class="checklist"]
> * Cree una directiva de protección de aplicaciones de Intune para la aplicación Outlook. Deberá limitar lo que el usuario puede hacer con los datos de la aplicación impidiendo que pueda ejecutar "Guardar como" y restringiendo las acciones de corte, copiar y pegado.
> * Cree directivas de acceso condicional de Azure Active Directory (Azure AD) que permitan solo a la aplicación Outlook acceder al correo electrónico de la empresa en Exchange Online. También necesita la autenticación multifactor (MFA) para los clientes de autenticación moderna, como Outlook para iOS y Android.

## <a name="prerequisites"></a>Requisitos previos

Necesitará a un inquilino de prueba con las siguientes suscripciones para este tutorial:

- Azure Active Directory Premium ([evaluación gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
- Suscripción a Intune ([evaluación gratuita](../fundamentals/free-trial-sign-up.md))
- Suscripción de Office 365 Empresa que incluya Exchange ([evaluación gratuita](https://go.microsoft.com/fwlink/p/?LinkID=510938))

## <a name="sign-in-to-intune"></a>Iniciar sesión en Intune

En este tutorial, cuando inicia sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), lo hace como [administrador global](../fundamentals/users-add.md#types-of-administrators) o [administrador de servicio](../fundamentals/users-add.md#types-of-administrators) de Intune. Si ha creado una suscripción de prueba de Intune, la cuenta con la que la haya creado es el administrador global.

## <a name="create-the-app-protection-policy"></a>Creación de la directiva de protección de la aplicación

En este tutorial, configurará una directiva de protección de aplicaciones para iOS para la aplicación Outlook a fin de colocar protecciones en el nivel de aplicación. Solicitaremos un PIN para abrir la aplicación en un contexto de trabajo. También limitaremos el uso compartido de los datos entre aplicaciones y evitaremos que los datos de la compañía se guarden en una ubicación personal.

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Seleccione **Aplicaciones** > **Directivas de protección de aplicaciones** > **Crear directiva** y seleccione **iOS/iPadOS** como plataforma.

3. En la página **Aspectos básicos**, configure las siguientes opciones:

   - **Nombre**: escriba **Prueba de directiva de aplicaciones de Outlook**.
   - **Descripción**: escriba **Prueba de directiva de aplicaciones de Outlook**.

   El valor de **Plataforma** está establecido en la opción anterior.

   Haga clic en **Siguiente** para continuar.

4. La página **Aplicaciones** permite elegir cómo se quiere aplicar esta directiva a las aplicaciones en distintos dispositivos. Configure las siguientes opciones:

   - **Destinar a todos los tipos de aplicaciones**: seleccione **No** y, después, en **Tipos de aplicaciones**, active la casilla correspondiente a **Aplicaciones en dispositivos no administrados**.
   - Haga clic en **Seleccionar aplicaciones públicas**. En la lista de aplicaciones, seleccione **Outlook** y luego elija **Seleccionar**.  Outlook aparece ahora en *Aplicaciones públicas*.

   Haga clic en **Siguiente** para continuar.

5. La página **Protección de datos** proporciona valores de configuración que determinan cómo interactúan los usuarios con los datos de las aplicaciones a las que se aplica esta directiva de protección de aplicaciones. Configure las siguientes opciones:

   Debajo de *Transferencia de datos*, configure las siguientes opciones y deje el resto en sus valores predeterminados:

   - En **Enviar datos de la organización a otras aplicaciones**, seleccione **Ninguno**.  
   - En **Recibir datos de otras aplicaciones**, seleccione **Ninguno**.  
   - En **Guardar copias de los datos de la organización**, seleccione **Bloquear**.  
   - En **Restringir cortar, copiar y pegar entre aplicaciones**, seleccione **Bloqueado**. 

   ![Selección de la configuración de reubicación de datos de directiva de protection de la aplicación Outlook](./media/tutorial-protect-email-on-unmanaged-devices/data-protection-settings.png)

   Seleccione **Siguiente** para continuar.

6. La página **Requisitos de acceso** proporciona valores de configuración que permiten configurar los requisitos de PIN y credenciales que los usuarios deben cumplir para obtener acceso a las aplicaciones en un contexto de trabajo. Configure las opciones siguientes y deje el resto en sus valores predeterminados:

   - En **PIN para acceder**, seleccione **Requerir**.
   - En **Credenciales de cuenta profesional o educativa para el acceso**, seleccione **Requerir**.

   ![Selección de acciones de acceso de la directiva de protección de la aplicación Outlook](./media/tutorial-protect-email-on-unmanaged-devices/access-requirements-settings.png)

   Seleccione **Siguiente** para continuar.

7. La página **Inicio condicional** proporciona opciones para establecer los requisitos de seguridad del inicio de sesión de la directiva de protección de aplicaciones. En este tutorial, no es necesario configurar estos valores.

   Haga clic en **Siguiente** para continuar.

8. La página **Asignaciones** permite asignar la directiva de protección de aplicaciones a grupos de usuarios. En este tutorial, no asignará esta directiva a un grupo.  
 No es necesario configurar estos valores.

   Haga clic en **Siguiente** para continuar.

9. En la página **Siguiente: Revisar + crear**, revise los valores y la configuración especificados para esta directiva de protección de aplicaciones. Haga clic en **Crear** para crear la directiva de protección de aplicaciones en Intune.

Se crea la directiva de protección de aplicación para Outlook. A continuación, puede configurar el acceso condicional para exigir a los dispositivos que usen la aplicación Outlook.

## <a name="create-conditional-access-policies"></a>Creación de directivas de acceso condicional

Ahora vamos a crear dos directivas de acceso condicional para cubrir todas las plataformas de dispositivo.  

- La primera directiva requerirá que los clientes de autenticación moderna utilicen la aplicación de Outlook y la autenticación multifactor (MFA) aprobadas. Los clientes de autenticación moderna incluyen Outlook para iOS y Outlook para Android.  

- La segunda directiva requerirá que los clientes de Exchange ActiveSync utilicen la aplicación de Outlook aprobada. (Actualmente, Exchange Active Sync no admite condiciones distintas de la plataforma del dispositivo). Puede configurar las directivas de acceso condicional en el portal de Azure AD o en el portal de Intune. Como ya estamos en el portal de Intune, vamos a crear la directiva aquí.  

### <a name="create-an-mfa-policy-for-modern-authentication-clients"></a>Creación de una directiva de MFA para los clientes de autenticación moderna  

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Seleccione **Endpoint security** (Seguridad del punto de conexión)  >  **Acceso condicional** > **Nueva directiva**.  

3. En **Nombre**, escriba **Probar directiva para clientes de autenticación moderna**.  

4. En **Asignaciones**, seleccione **Usuarios y grupos**. En la pestaña **Incluir**, seleccione **Todos los usuarios**, y luego seleccione **Listo**.

5. En **Asignaciones**, seleccione **Acciones o aplicaciones en la nube**. Puesto que deseamos proteger el correo electrónico de Office 365 Exchange Online, lo seleccionaremos siguiendo estos pasos:

   1. En la pestaña **Incluir**, elija **Seleccionar aplicaciones**.
   2. Elija **Seleccionar**.
   3. En la lista de aplicaciones, seleccione **Office 365 Exchange Online** y después elija **Seleccionar**.
   4. Seleccione **Listo** para volver al panel de directiva nueva.

   ![Seleccione la aplicación Office 365 Exchange Online](./media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-cloud-apps.png)

6. En **Asignaciones**, seleccione **Condiciones** > **Plataformas de dispositivo**.

   1. En **Configurar**, seleccione **Sí**.
   2. En la pestaña **Incluir**, seleccione **Cualquier dispositivo**.
   3. Seleccione **Listo**.

7. En el panel **Condiciones**, seleccione **Aplicaciones cliente**.

   1. En **Configurar**, seleccione **Sí**.
   2. Seleccione **Aplicaciones móviles y clientes de escritorio** y **Clientes de autenticación moderna**.
   3. Desactive las demás casillas.
   4. Seleccione **Listo** > **Listo** para volver al panel de directiva nueva.

   ![Selección de clientes y aplicaciones móviles](./media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-client-apps.png)

8. En **Controles de acceso**, seleccione **Conceder**.

   1. En el panel **Conceder**, seleccione **Conceder acceso**.
   2. Seleccione **Requerir autenticación multifactor**.
   3. Seleccione **Requerir aplicación cliente aprobada**.
   4. En **Para varios controles**, seleccione **Requerir todos los controles seleccionados**. Esta configuración garantiza que ambos requisitos que ha seleccionado se aplican cuando un dispositivo intenta acceder al correo electrónico.
   5. Elija **Seleccionar**.

   ![Selección de los controles de acceso](./media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-mfa.png)

9. En **Habilitar directiva**, seleccione **Activar** y después seleccione **Crear**.

   ![Creación de directiva](./media/tutorial-protect-email-on-unmanaged-devices/enable-policy.png)  

Se crea la directiva de acceso condicional para clientes de autenticación moderna. Ahora puede crear una directiva para los clientes de Exchange Active Sync.

### <a name="create-a-policy-for-exchange-active-sync-clients"></a>Creación de una directiva para los clientes de Exchange Active Sync

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Seleccione **Endpoint security** (Seguridad del punto de conexión)  > **Acceso condicional** > **Nueva directiva**.

3. En **Nombre**, escriba **Probar directiva para clientes de EAS**.

4. En **Asignaciones**, seleccione **Usuarios y grupos**. En la pestaña *Incluir*, seleccione **Todos los usuarios**, y luego seleccione **Listo**.

5. En **Asignaciones**, seleccione **Acciones o aplicaciones en la nube**. Seleccione el correo electrónico de Office 365 Exchange Online con estos pasos:

   1. En la pestaña *Incluir*, elija **Seleccionar aplicaciones**.
   2. Elija **Seleccionar**.
   3. En la lista *Aplicaciones*, seleccione **Office 365 Exchange Online**, después elija **Seleccionar** y, por último, **Listo**.
  
6. En **Asignaciones**, seleccione **Condiciones** > **Plataformas de dispositivo**.

   1. En **Configurar**, seleccione **Sí**.
   2. En la pestaña **Incluir**, seleccione **Cualquier dispositivo** y luego seleccione **Listo**.

7. En el panel **Condiciones**, seleccione **Aplicaciones cliente**.

   1. En **Configurar**, seleccione **Sí**.
   2. Seleccione **Aplicaciones móviles y clientes de escritorio**.
   3. Seleccione **Clientes de Exchange ActiveSync** y **Aplicar directiva solo en las plataformas compatibles** .  
   4. Desactive todas las demás casillas.  
   5. Seleccione **Listo** y después vuelva a seleccionar **Listo**.  

   ![Aplicación a plataformas compatibles](./media/tutorial-protect-email-on-unmanaged-devices/eas-client-apps.png)  

8. En **Controles de acceso**, seleccione **Conceder**.

   1. En el panel **Conceder**, seleccione **Conceder acceso**.
   2. Seleccione **Requerir aplicación cliente aprobada**. Desactive todas las demás casillas.
   3. Elija **Seleccionar**.

   ![Requerimiento de aplicación cliente aprobada](./media/tutorial-protect-email-on-unmanaged-devices/eas-grant-access.png)

9. En **Habilitar directiva**, seleccione **Activar** y después seleccione **Crear**.

Las directivas de protección de aplicaciones y el acceso condicional están preparados y listos para probar.

## <a name="try-it-out"></a>Haga la prueba

Con las directivas que se han creado, los dispositivos deberán inscribirse en Intune y usar la aplicación móvil de Outlook para acceder al correo electrónico de Office 365. Para probar este escenario en un dispositivo iOS, intente iniciar sesión en Exchange Online con las credenciales de un usuario en su inquilino de prueba.

1. Para realizar pruebas en un iPhone, vaya a **Configuración** > **Contraseñas y cuentas** > **Agregar cuenta** > **Exchange** .

2. Escriba la dirección de correo electrónico de un usuario en su inquilino de prueba y después presione **Siguiente**.  
3. Presione **Iniciar sesión**.

4. Escriba la contraseña del usuario de prueba y luego presione **Iniciar sesión**.

5. Aparece el mensaje **Se necesita más información**, lo que significa que se le pedirá que configure MFA. Continúe y configure un método de comprobación adicional.

6. Después verá un mensaje que indica que está intentando abrir este recurso con una aplicación que no ha sido aprobada por el departamento de TI. Este mensaje significa que se le bloqueará el uso de la aplicación de correo nativa. Cancele el inicio de sesión.

7. Abra la aplicación Outlook y seleccione **Configuración** > **Agregar cuenta** > **Agregar una cuenta de correo electrónico**.

8. Escriba la dirección de correo electrónico de un usuario en su inquilino de prueba y después presione **Siguiente**.

9. Presione **Iniciar sesión con Office 365**. Se le pedirá que lleve a cabo una autenticación y un registro adicionales. Una vez que haya iniciado sesión, puede probar acciones como Cortar, Copiar, Pegar y "Guardar como".

## <a name="clean-up-resources"></a>Limpieza de recursos

Cuando ya no se necesiten las directivas de prueba, puede quitarlas.

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Seleccione **Dispositivos** **Directivas de cumplimiento**.

3. En la lista **Nombre de directiva**, seleccione el menú contextual ( **...** ) de la directiva de prueba y después seleccione **Eliminar**. Seleccione **Aceptar** para confirmar la operación.

4. Seleccione **Seguridad de los puntos de conexión** > **Acceso condicional**.

5. En la lista **Nombre de directiva**, seleccione el menú contextual ( **...** ) para cada una de las directivas de prueba y después seleccione **Eliminar**. Seleccione **Sí** para confirmar.

## <a name="next-steps"></a>Pasos siguientes
En este tutorial, ha creado directivas de protección de aplicación para limitar lo que el usuario puede hacer con la aplicación de Outlook y ha creado directivas de acceso condicional para que los clientes de autenticación moderna usen la aplicación Outlook y MFA. Para información sobre cómo usar Intune con acceso condicional para proteger otras aplicaciones y servicios, consulte [¿Qué es el acceso condicional?](conditional-access.md).
