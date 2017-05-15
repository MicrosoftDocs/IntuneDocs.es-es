---
title: "Administración de DEP de Apple para dispositivos iOS | Microsoft Docs"
description: "Implemente un perfil de inscripción que inscriba dispositivos iOS comprados a través del Programa de inscripción de dispositivos (DEP) de iOS &quot;por aire&quot; para administrar dispositivos Apple."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8ff9d9e7-eed8-416c-8508-efc20fca8578
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: c8715f96f532ee6bacda231e1147d03226ecbb48
ms.openlocfilehash: 81f5b33bc344cd6ed305d72178c7eb4cac315a13
ms.contentlocale: es-es
ms.lasthandoff: 04/26/2017


---

# <a name="enroll-corporate-owned-device-enrollment-program-ios-devices"></a>Inscripción de dispositivos iOS de la empresa del Programa de inscripción de dispositivos de Apple

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune puede implementar un perfil de inscripción que inscriba dispositivos iOS que se han adquirido a través del Programa de inscripción de dispositivos (DEP) "por aire". El paquete de inscripción puede incluir opciones de asistente de instalación para el dispositivo.

>[!NOTE]
>La inscripción DEP no se puede usar con el método del [administrador de inscripción de dispositivos](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).
>Además, si los usuarios inscriben dispositivos iOS (es decir, usan la aplicación Portal de empresa) y los números de serie de esos dispositivos se importan luego y se les asigna un perfil DEP, se anulará la inscripción del dispositivo en Intune.

## <a name="prerequisites-for-enrolling-ios-devices-by-using-apple-dep-management"></a>Requisitos previos para la inscripción de dispositivos iOS mediante la administración de DEP de Apple

- [Instalar un certificado de APNs](set-up-ios-and-mac-management-with-microsoft-intune.md)

- Su organización debe unirse al DEP de Apple y obtener los dispositivos a través de ese programa. Puede consultar los detalles de este proceso en:  [https://deploy.apple.com](https://deploy.apple.com). Las ventajas del programa incluyen dispositivos configurados con manos libres sin necesidad de usar un cable USB para conectar cada dispositivo a un equipo.

- Antes de poder inscribir dispositivos iOS corporativos con DEP, necesita un token de DEP de Apple. Este token permite a Intune sincronizar información sobre dispositivos corporativos que participan en DEP. También permite a Intune realizar cargas de perfiles de inscripción a Apple y asignar dispositivos a esos perfiles.

## <a name="steps-to-enroll-ios-devices-by-using-apple-dep-management"></a>Pasos para inscribir dispositivos iOS mediante la administración de DEP de Apple

En los siguientes pasos se explica cómo inscribir dispositivos iOS el "día 0" mediante la administración de DEP de Apple. Como los dispositivos se agregan y se quitan desde la organización, es probable que repita algunos de estos pasos, como agregar o quitar números de serie, tal como se describe a continuación.

### <a name="get-an-encryption-key"></a>Obtener una clave de cifrado

1. Como usuario administrativo, abra la [consola de administración de Microsoft Intune](https://manage.microsoft.com), vaya a **Administración** &gt; **Administración de dispositivos móviles** &gt; **iOS** &gt; **Programa de inscripción de dispositivos** y elija **Descargar clave de cifrado**.

2. Guarde el archivo de clave de cifrado (.pem) localmente. El archivo .pem se usa para solicitar un certificado de relación de confianza en el portal del Programa de Inscripción de Dispositivos de Apple.

![Actualizar un token del programa de inscripción de dispositivos](../media/dev-sa-ios-dep.png)

### <a name="get-a-device-enrollment-program-token"></a>Obtener un token del programa de inscripción de dispositivos

1. Vaya al [portal del Programa de inscripción de dispositivos](https://deploy.apple.com) (https://deploy.apple.com) e inicie sesión con su identificador de Apple de empresa. Este identificador de Apple debe usarse posteriormente para renovar el token de DEP.

2.  En el Portal del programa de inscripción de dispositivos, vaya a **Programa de inscripción de dispositivos** &gt; **Administrar servidores** y, después, elija **Add MDM Server** (Agregar servidor MDM).

3.  Escriba el **nombre del servidor MDM** y, después, elija **Siguiente**. El nombre del servidor es su referencia para identificar el servidor de administración de dispositivos móviles (MDM). No es el nombre ni la dirección URL del servidor de Microsoft Intune.

4.  Se abre el cuadro de diálogo **Agregar &lt;NombreDeServidor&gt;**. Elija **Elegir archivo...** para cargar el archivo .pem y, después, elija **Siguiente**.

5.  El cuadro de diálogo **Agregar &lt;NombreDeServidor&gt;** muestra el vínculo **Your Server Token** (Su token de servidor). Descargue el archivo de token de servidor (.p7m) en el equipo y, después, elija **Listo**.

   Este archivo de certificado (.p7m) se usa para establecer una relación de confianza entre los servidores de Intune y los del programa de inscripción de dispositivos de Apple.

### <a name="add-the-dep-token-to-intune"></a>Agregar el token de DEP a Intune

1. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), vaya a **Administración** &gt; **Administración de dispositivos móviles** &gt; **iOS** &gt; **Programa de inscripción de dispositivos**.

2. Elija **Cargar el token de DEP**. **Busque** el archivo de certificado (.p7m), escriba su **ID de Apple** y luego elija **Cargar**.

### <a name="add-the-corporate-device-enrollment-policy"></a>Agregar la directiva de inscripción de dispositivos corporativos

1. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), vaya a **Directiva** &gt; **Inscripción de dispositivos corporativos** y, después, elija **Agregar**.

2. En **General**, proporcione la información correspondiente en los campos **Nombre** y **Descripción**, y especifique si los dispositivos asignados al perfil tienen afinidad de usuario o pertenecen a un grupo:

   - **Solicitar afinidad de usuario**: el dispositivo se debe afiliar a un usuario durante la configuración inicial antes de que se le permita el acceso a los datos y al correo electrónico de la empresa como dicho usuario. La opción **Afinidad de usuario** debe configurarse para dispositivos administrados por DEP que pertenezcan a usuarios y necesiten usar el portal de empresa (es decir, para instalar aplicaciones). La autenticación multifactor (MFA) no funciona durante la inscripción en dispositivos DEP con afinidad de usuario. Después de la inscripción, MFA funciona según lo previsto en estos dispositivos. No se puede pedir a los nuevos usuarios que cambien la contraseña al iniciar sesión por primera vez durante la inscripción en dispositivos DEP. Además, no se puede pedir a los usuarios cuyas contraseñas han expirado que las restablezcan durante la inscripción de DEP y tienen que hacerlo desde otro dispositivo.

   > [!NOTE]
   > DEP con la afinidad de usuario requiere un punto de conexión de WS-Trust 1.3 nombreDeUsuario/Mixto para que se habilite para solicitar el token de usuario.

   - **Sin afinidad de usuario**: el dispositivo no está afiliado a ningún usuario. Use esta afiliación para dispositivos que realizan tareas sin tener acceso a datos de usuario local. Las aplicaciones que requieren la afiliación de usuario, incluida la aplicación Portal de empresa que se usa para instalar aplicaciones de línea de negocio, no funcionarán.

   También puede seleccionar la opción **Asignar dispositivos al siguiente grupo**. Elija **Seleccionar...** para elegir un grupo.

   > [!Important]
   > Las asignaciones de grupo están pasando de Intune a Azure Active Directory. Una vez que su cuenta de Intune reciba la actualización correspondiente, dejará de ver la opción **Asignar dispositivos al siguiente grupo**. [Obtenga más información](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune#changes-to-intune-group-assignments).

3. Habilite **Configure los ajustes del Programa de inscripción de dispositivos para esta directiva** para esta directiva para que admita DEP.

      ![Panel del asistente de instalación](../media/pol-sa-corp-enroll.png)

   Están disponibles las opciones siguientes para los dispositivos administrados por DEP:

   - **Departamento**: aparece cuando los usuarios pulsan **Acerca de la configuración** durante la activación
   - **Teléfono de soporte técnico**: aparece cuando el usuario hace clic en el botón **Necesito ayuda** durante la activación
   - **Modo de preparación**: se establece durante la activación y no se puede cambiar sin realizar el restablecimiento de fábrica del dispositivo:
       - **No supervisado**: funcionalidades de administración limitadas
       - **Supervisado**: permite más opciones de administración y deshabilita el bloqueo de activación de manera predeterminada
   - **Bloquear el perfil de inscripción al dispositivo**: se establece durante la activación y no se puede cambiar sin realizar un restablecimiento de fábrica
       - **Deshabilitar**: permite el perfil de administración que se va a quitar del menú **Configuración**
       - **Habilitar** (requiere **Modo de preparación** = **Supervisado**): deshabilita la opción del menú Configuración de iOS para quitar el perfil de administración
   - **Opciones del Asistente de configuración**: estas opciones opcionales se pueden configurar más adelante en el menú **Configuración** de iOS.
        - **Código de acceso**: solicitar el código de acceso durante la activación. Solicite siempre un código de acceso, a menos que el dispositivo esté protegido o tenga el acceso controlado de otra manera (es decir, modo de quiosco que restringe el dispositivo a una aplicación)
       - **Servicios de ubicación**: si está habilitado, el asistente de configuración solicita el servicio durante la activación
       - **Restaurar**: si está habilitado, el asistente de configuración solicita la copia de seguridad de iCloud durante la activación
       - **Id. de Apple**: si está habilitado, iOS solicitará a los usuarios un identificador de Apple cuando Intune intente instalar una aplicación sin un identificador. Se requiere un identificador de Apple para descargar aplicaciones del App Store de iOS, incluidas las que instala Intune.
       - **Términos y condiciones**: si está habilitado, el asistente de configuración solicita a los usuarios aceptar los términos y condiciones de Apple durante la activación
       - **Touch ID**: si está habilitado, el asistente para la configuración solicita este servicio durante la activación
       - **Apple Pay**: si está habilitado, el asistente para la configuración solicita este servicio durante la activación
       - **Zoom**: si está habilitado, el asistente para la configuración solicita este servicio durante la activación
       - **Siri**: si está habilitado, el asistente de configuración solicita este servicio durante la activación
       - **Enviar datos de diagnóstico a Apple**: si está habilitado, el asistente de configuración solicita este servicio durante la activación
   -  **Habilitar administración adicional de Apple Configurator**: establézcalo en **No permitir** para impedir la sincronización de archivos con iTunes o con la administración a través de Apple Configurator. Es una buena decisión elegir **No permitir**, exportar la configuración adicional de Apple Configurator y, después, implementarla como un perfil de configuración de iOS personalizado mediante Intune, en lugar de usar esta opción para permitir la implementación manual con o sin certificado.
       - **No permitir**: evita que el dispositivo se comunique mediante USB (deshabilita el emparejamiento)
       - **Permitir**: permite que un dispositivo se comunique a través de la conexión USB para cualquier equipo PC o Mac
       - **Requerir certificado**: permite el emparejamiento con un Mac con un certificado importado en el perfil de inscripción

### <a name="assign-the-profile-to-devices"></a>Asignar el perfil a los dispositivos

1. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), vaya a **Directiva** &gt; **Inscripción de dispositivos corporativos** y, después, elija **Asignar**.

2. Elija los dispositivos a los que quiere asignar el perfil que ha creado. Puede elegir **Todos los dispositivos** o seleccionar dispositivos específicos y después seleccionar **Agregar**.

> [!Important]
> Actualmente, Intune le permite designar un perfil de inscripción de dispositivos “predeterminado”, lo que significa que se asignan nuevos números de serie de forma automática a ese perfil predeterminado al sincronizar nuevos números de serie con el servicio DEP de Apple. Cuando el inquilino se migre al nuevo Azure Portal en un futuro próximo, ya no será posible establecer un perfil predeterminado y que los números de serie se asignen de forma automática a ese perfil. En su lugar, tendrá que asignar números de serie a un perfil concreto. [Más información](https://docs.microsoft.com/intune-azure/enroll-devices/enroll-ios-devices-using-device-enrollment-program).

### <a name="assign-dep-devices-for-management"></a>Asignar dispositivos DEP para la administración

1. Vaya al [Portal del programa de inscripción de dispositivos](https://deploy.apple.com) (https://deploy.apple.com) e inicie sesión con su identificador de Apple de empresa.

2. Vaya a **Programa de implementación** &gt; **Programa de inscripción de dispositivos** &gt; **Administrar dispositivos**.

3. Especifique cómo va a **elegir los dispositivos**, proporcione información del dispositivo y especifique los detalles de cada dispositivo, como **Número de serie**, **Número de pedido**, o seleccione **Cargar archivo CSV**.

4. Elija **Assign to Server** (Asignar al servidor), elija el &lt;NombreDeServidor&gt; especificado para Microsoft Intune y después elija **Aceptar**.

### <a name="synchronize-dep-managed-devices"></a>Sincronizar los dispositivos administrados por DEP

En este paso, los dispositivos se sincronizan con el servicio DEP de Apple y aparecen en la consola de Intune.

1. Como usuario administrativo, abra la [consola de administración de Microsoft Intune](https://manage.microsoft.com), vaya a **Administración** &gt; **Administración de dispositivos móviles** &gt; **iOS** &gt; **Programa de inscripción de dispositivos** y elija **Sincronizar ahora**. Se envía una solicitud de sincronización a Apple.

2. Para ver los dispositivos administrados por DEP después de la sincronización, en la [consola de administración de Microsoft Intune](https://manage.microsoft.com), vaya a **Grupos** &gt; **Todos los dispositivos** &gt; **Dispositivos corporativos inscritos previamente** &gt; **Mediante número de serie de iOS**. En el área de trabajo **Mediante número de serie de iOS**, la opción **Estado** de los dispositivos administrados es “Sin contacto” hasta que se encienda el dispositivo y se ejecute el Asistente de configuración para inscribirlo.

   Para cumplir con las condiciones de Apple relativas a un tráfico DEP aceptable, Intune impone las restricciones siguientes:

   - Una sincronización completa de DEP no se puede ejecutar más de una vez cada siete días. Durante una sincronización completa, Intune actualiza todos los números de serie que Apple ha asignado a Intune, independientemente de si el número de serie se ha sincronizado previamente o no. Si se intenta efectuar una sincronización completa sin que hayan pasado siete días desde la última sincronización completa, Intune solo actualizará los números de serie que aún no aparezcan en Intune.

   - Las solicitudes de sincronización tardan 10 minutos en finalizar. Durante este tiempo, o hasta que la solicitud finalice correctamente, el botón **Sincronización** está deshabilitado.

### <a name="distribute-devices-to-users"></a>Distribuir los dispositivos a los usuarios

Los dispositivos corporativos ahora pueden distribuirse a los usuarios. Los dispositivos iOS quedan inscritos para su administración mediante Intune al activarlos. El límite de dispositivos de usuario se aplica a dispositivos administrados por DEP.

>[!NOTE]
>Si un usuario intenta inscribir un dispositivo DEP, pero ha superado su límite de dispositivos, la inscripción dejará de realizarse sin avisar al usuario.

## <a name="changes-to-intune-group-assignments"></a>Cambios en las asignaciones de grupo de Intune

A partir de abril de 2017, la administración de grupos de dispositivos se moverá a Azure Active Directory. Después de la transición a los grupos de Azure Active Directory, la asignación de grupo no aparecerá en las opciones del perfil de inscripción corporativa. Como este cambio se implantará en una serie de meses, puede que no vea el cambio directamente. Después de moverse al nuevo portal, se pueden definir nuevas asignaciones de grupos de dispositivos dinámicos según el nombre del perfil de inscripción corporativa.

Durante la migración, para cada grupo de dispositivos de Intune previamente asignado mediante un perfil de inscripción de dispositivos corporativos, se creará un grupo de dispositivos dinámico correspondiente en Azure AD según el nombre del perfil de inscripción de dispositivos corporativos. Los nuevos nombres de perfil tienen el formato *EnrollmentProfile:&lt;nombre de perfil asociado&gt;*. Este proceso garantiza que los dispositivos que ya se han asignado previamente a un grupo de dispositivos se inscriban automáticamente en el grupo con la directiva y las aplicaciones implementadas.

Esta creación de grupos automática solo se produce una vez, durante la migración de grupos. Tras la migración, los administradores de Intune deben crear grupos mediante Azure Portal. Para detalles sobre cómo esto afecta a la inscripción de dispositivos corporativos iOS, consulte [Changes to Automatic Grouping for Corporate Pre-enrolled iOS Devices](https://blogs.technet.microsoft.com/intunesupport/2017/04/19/changes-to-automatic-grouping-for-corporate-pre-enrolled-ios-devices/) (Cambios en la agrupación automática de dispositivos corporativos iOS inscritos previamente).

También puede [obtener más información sobre los grupos de Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-manage-groups/).

### <a name="see-also"></a>Consulte también
[Requisitos previos para la inscripción de dispositivos](prerequisites-for-enrollment.md)

