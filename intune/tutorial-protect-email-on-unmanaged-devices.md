---
title: 'Tutorial: Protección del correo electrónico de Exchange Online en dispositivos no administrados'
titleSuffix: Microsoft Intune
description: Aprenda a proteger Office 365 Exchange Online con directivas de protección de aplicaciones de Intune y acceso condicional de Azure AD.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/26/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b91e3863a23d62921f4145db4460fa07f325df98
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66040294"
---
# <a name="tutorial-protect-exchange-online-email-on-unmanaged-devices"></a>Tutorial: Protección del correo electrónico de Exchange Online en dispositivos no administrados

Obtenga información sobre el uso de directivas de protección de aplicaciones con acceso condicional para proteger Exchange Online, incluso cuando los dispositivos no están inscritos en una solución de administración de dispositivos como Intune. En este tutorial, aprenderá a: 

> [!div class="checklist"]
> * Cree una directiva de protección de aplicaciones de Intune para la aplicación Outlook. Deberá limitar lo que el usuario puede hacer con los datos de la aplicación impidiendo que pueda ejecutar "Guardar como" y restringiendo las acciones de corte, copiar y pegado. 
> * Cree directivas de acceso condicional de Azure Active Directory (Azure AD) que permitan solo a la aplicación Outlook acceder al correo electrónico de la compañía en Exchange Online. También necesita la autenticación multifactor (MFA) para los clientes de autenticación moderna, como Outlook para iOS y Android.

## <a name="prerequisites"></a>Requisitos previos
  - Necesitará a un inquilino de prueba con las siguientes suscripciones para este tutorial:
    - Azure Active Directory Premium ([evaluación gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
    - Suscripción a Intune ([evaluación gratuita](free-trial-sign-up.md))
    - Suscripción de Office 365 Empresa que incluya Exchange ([evaluación gratuita](https://go.microsoft.com/fwlink/p/?LinkID=510938))

## <a name="sign-in-to-intune"></a>Iniciar sesión en Intune

Inicie sesión en [Intune](https://aka.ms/intuneportal) como administrador global o administrador de servicios de Intune. Intune se encuentra en Azure Portal, si selecciona **Todos los servicios** > **Intune**.

## <a name="create-the-app-protection-policy"></a>Creación de la directiva de protección de la aplicación
Para este tutorial, deberá configurar una directiva de protección de aplicaciones de Intune para la aplicación Outlook para aplicar protecciones en el nivel de aplicación. Solicitaremos un PIN para abrir la aplicación en un contexto de trabajo. También limitaremos el uso compartido de los datos entre aplicaciones y evitaremos que los datos de la compañía se guarden en una ubicación personal.

1.  En Intune, seleccione **Aplicaciones cliente** > **Directivas de protección de aplicaciones** > **Agregar directiva**.
2.  En **Nombre**, escriba **Prueba de directiva de aplicaciones de Outlook**.
3.  En **Descripción**, escriba **Prueba de directiva de aplicaciones de Outlook**.
4.  Seleccione **Aplicaciones**. En la lista de aplicaciones, seleccione **Outlook** y luego elija **Seleccionar**.
5.  Haga clic en **Configuración**. 
6.  En **Reubicación de datos**, para este tutorial, seleccione estas configuraciones:

    - Para **Permitir que la aplicación transfiera datos a otras aplicaciones**, seleccione **Ninguna**.
    - Para **Permitir a la aplicación recibir datos de otras aplicaciones** , seleccione **Ninguna**.
    - Para **Impedir "Guardar como"** , seleccione **Sí**.
    - Para **Restringir cortar, copiar y pegar con otras aplicaciones**, seleccione **Bloqueado**.
   
     ![Selección de la configuración de reubicación de datos de directiva de protection de la aplicación Outlook](media/tutorial-protect-email-on-unmanaged-devices/outlook-app-data-relocation.png)
    
7.  En **Acciones de acceso**, seleccione estas configuraciones para este tutorial:

    - Para **Requerir PIN para acceder**, seleccione **Sí**.
    - Para **Requerir credenciales corporativas para el acceso**, seleccione **Sí**.
    - Deje todas las demás configuraciones con sus valores predeterminados.
 
     ![Selección de acciones de acceso de la directiva de protección de la aplicación Outlook](media/tutorial-protect-email-on-unmanaged-devices/outlook-app-access-actions.png)

9.  Seleccione **Aceptar**.
10. Seleccione **Crear**.

Se crea la directiva de protección de aplicación para Outlook. Ahora puede configurar el acceso condicional para exigir a los dispositivos que usen la aplicación Outlook.

## <a name="create-conditional-access-policies"></a>Creación de directivas de acceso condicional
Ahora vamos a crear dos directivas de acceso condicional para cubrir todas las plataformas de dispositivo. La primera directiva requerirá que los clientes de autenticación moderna, como Outlook para iOS y Outlook para Android, usen la aplicación Outlook aprobada y MFA. La segunda directiva requerirá que los clientes de Exchange ActiveSync usen la aplicación Outlook aprobada. (Actualmente, Exchange Active Sync no admite condiciones distintas de la plataforma del dispositivo). Puede configurar las directivas de acceso condicional en el portal de Azure AD o en el portal de Intune. Como ya estamos en el portal de Intune, vamos a crear la directiva aquí.
### <a name="create-an-mfa-policy-for-modern-authentication-clients"></a>Creación de una directiva de MFA para los clientes de autenticación moderna
1.  En Intune, seleccione **Acceso condicional** > **Directivas** > **Nueva directiva**.
1.  En **Nombre**, escriba **Probar directiva para clientes de autenticación moderna**. 
3.  En **Asignaciones**, seleccione **Usuarios y grupos**. En la pestaña **Incluir**, seleccione **Todos los usuarios**, y luego seleccione **Listo**.

4.  En **Asignaciones**, seleccione **Aplicaciones en la nube**. Puesto que deseamos proteger el correo electrónico de Office 365 Exchange Online, lo seleccionaremos siguiendo estos pasos:
     
    1. En la pestaña **Incluir**, elija **Seleccionar aplicaciones**.
    2. Elija **Seleccionar**. 
    3. En la lista de aplicaciones, seleccione **Office 365 Exchange Online** y después elija **Seleccionar**. 
    4. Seleccione **Listo**.
  
    ![Seleccione la aplicación Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-cloud-apps.png)

5.  En **Asignaciones**, seleccione **Condiciones** > **Plataformas de dispositivo**.
     
    1. En **Configurar**, seleccione **Sí**.
    2. En la pestaña **Incluir**, seleccione **Cualquier dispositivo**.
    1. Seleccione **Listo**.
   
6.  En el panel **Condiciones**, seleccione **Aplicaciones cliente**.
     
    1. En **Configurar**, seleccione **Sí**.
    2. Seleccione **Aplicaciones móviles y clientes de escritorio** y **Clientes de autenticación moderna**.
    3. Desactive las demás casillas.
    4. Seleccione **Listo** y después vuelva a seleccionar **Listo**.
    
    ![Seleccione la aplicación Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-client-apps.png)

7.  En **Controles de acceso**, seleccione **Conceder**. 
     
    1. En el panel **Conceder**, seleccione **Conceder acceso**.
    2. Seleccione **Requerir autenticación multifactor**.
    4. Seleccione **Requerir aplicación cliente aprobada**.
    5. En **Para varios controles**, seleccione **Requerir todos los controles seleccionados**. Esta configuración garantiza que ambos requisitos que ha seleccionado se aplican cuando un dispositivo intenta acceder al correo electrónico.
    6. Elija **Seleccionar**.
     
    ![Seleccione la aplicación Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-mfa.png)

8.  En **Habilitar directiva**, seleccione **Activar**.
     
    ![Seleccione la aplicación Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/enable-policy.png)

9.  Seleccione **Crear**.

Se crea la directiva de acceso condicional para clientes de autenticación moderna. Ahora puede crear una directiva para los clientes de Exchange Active Sync.

### <a name="create-a-policy-for-exchange-active-sync-clients"></a>Creación de una directiva para los clientes de Exchange Active Sync
1.  En Intune, seleccione **Acceso condicional** > **Directivas** > **Nueva directiva**.
2.  En **Nombre**, escriba **Probar directiva para clientes de EAS**. 
3.  En **Asignaciones**, seleccione **Usuarios y grupos**. En la pestaña **Incluir**, seleccione **Todos los usuarios**, y luego seleccione **Listo**.

4.  En **Asignaciones**, seleccione **Aplicaciones en la nube**. Seleccione el correo electrónico de Office 365 Exchange Online con estos pasos:
     
    1. En la pestaña **Incluir**, elija **Seleccionar aplicaciones**.
    2. Elija **Seleccionar**. 
    3. En la lista de aplicaciones, seleccione **Office 365 Exchange Online** y después elija **Seleccionar**. 
    4. Seleccione **Listo**.

5.  En **Asignaciones**, seleccione **Condiciones** > **Plataformas de dispositivo**.
     
    1. En **Configurar**, seleccione **Sí**.
    2. En la pestaña **Incluir**, seleccione **Cualquier dispositivo** y luego seleccione **Listo**. 
    3. Vuelva a seleccionar **Listo**.

6.  En el panel **Condiciones**, seleccione **Aplicaciones cliente**.
     
    1. En **Configurar**, seleccione **Sí**.
    2. Seleccione **Aplicaciones móviles y clientes de escritorio**.
    3. Seleccione **Clientes de Exchange ActiveSync** y **Aplicar directiva solo en las plataformas compatibles** . 
    4. Desactive todas las demás casillas.
    5. Seleccione **Listo** y después vuelva a seleccionar **Listo**.
    
    ![Seleccione la aplicación Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/eas-client-apps.png)

7.  En **Controles de acceso**, seleccione **Conceder**. 
     
    1. En el panel **Conceder**, seleccione **Conceder acceso**.
    4. Seleccione **Requerir aplicación cliente aprobada**. Desactive todas las demás casillas.
    6. Elija **Seleccionar**.
     
    ![Seleccione la aplicación Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/eas-grant-access.png)

8.  En **Habilitar directiva**, seleccione **Activar**.

9.  Seleccione **Crear**.

Las directivas de protección de aplicaciones y el acceso condicional están preparados y listos para probar. 

## <a name="try-it-out"></a>Haga la prueba
Con las directivas que se han creado, los dispositivos deberán inscribirse en Intune y usar la aplicación móvil de Outlook para acceder al correo electrónico de Office 365. Para probar este escenario en un dispositivo iOS, intente iniciar sesión en Exchange Online con las credenciales de un usuario en su inquilino de prueba.
1. Para realizar pruebas en un iPhone, vaya a **Configuración** > **Contraseñas y cuentas** > **Agregar cuenta** > **Exchange** .
2. Escriba la dirección de correo electrónico de un usuario en su inquilino de prueba y después presione **Siguiente**.
3. Presione **Iniciar sesión**.
4. Escriba la contraseña del usuario de prueba y luego presione **Iniciar sesión**.
5. Aparece el mensaje **Se necesita más información**, lo que significa que se le pedirá que configure MFA. Continúe y configure un método de comprobación adicional.
6. A continuación, verá un mensaje que indica que está intentando abrir este recurso con una aplicación que no ha sido aprobada por el departamento de TI. Esto significa que se le bloqueará el uso de la aplicación de correo nativa. Cancele el inicio de sesión.
7.  Abra la aplicación Outlook y seleccione **Configuración** > **Agregar cuenta** > **Agregar una cuenta de correo electrónico**.
8. Escriba la dirección de correo electrónico de un usuario en su inquilino de prueba y después presione **Siguiente**.
9. Presione **Iniciar sesión con Office 365**. Se le pedirá que lleve a cabo una autenticación y un registro adicionales. Una vez que haya iniciado sesión, puede probar acciones como Cortar, Copiar, Pegar y "Guardar como".

## <a name="clean-up-resources"></a>Limpieza de recursos
Cuando ya no se necesiten las directivas de prueba, puede quitarlas.
1. Inicie sesión en [Intune](https://aka.ms/intuneportal) como administrador global o administrador de servicios de Intune.
2. Seleccione **Cumplimiento de dispositivos** > **Directivas**.
3. En la lista **Nombre de directiva**, seleccione el menú contextual ( **...** ) de la directiva de prueba y después seleccione **Eliminar**. Seleccione **Aceptar** para confirmar la operación.
4. Seleccione **Acceso condicional** > **Directivas**.
5. En la lista **Nombre de directiva**, seleccione el menú contextual ( **...** ) para cada una de las directivas de prueba y después seleccione **Eliminar**. Seleccione **Sí** para confirmar.

 ## <a name="next-steps"></a>Pasos siguientes 
En este tutorial, ha creado directivas de protección de aplicación para limitar lo que el usuario puede hacer con la aplicación de Outlook y ha creado directivas de acceso condicional para que los clientes de autenticación moderna usen la aplicación Outlook y MFA. Para información sobre cómo usar Intune con acceso condicional para proteger otras aplicaciones y servicios, vea [¿Qué es el acceso condicional?](conditional-access.md).
