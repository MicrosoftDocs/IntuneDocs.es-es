---
title: "Administración de DEP de Apple para dispositivos iOS | Microsoft Intune"
description: "Implemente un perfil de inscripción que inscriba dispositivos iOS adquiridos a través del Programa de inscripción de dispositivos (DEP) iOS &quot;de forma inalámbrica&quot; para administrar dispositivos Apple."
keywords: 
author: staciebarker
ms.author: stabar
manager: arob98
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8ff9d9e7-eed8-416c-8508-efc20fca8578
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: cfbf04627892dd700d2e31fabe8bca357f692d51
ms.openlocfilehash: d1e534677bf5e5098f3a3665765983305a6bac69


---

# <a name="enroll-corporate-owned-device-enrollment-program-ios-devices"></a>Inscribir dispositivos iOS de la empresa mediante el Programa de inscripción de dispositivos
Microsoft Intune puede implementar un perfil de inscripción que inscriba dispositivos iOS que se han adquirido a través del Programa de inscripción de dispositivos (DEP) de Apple "de forma inalámbrica". El paquete de inscripción puede incluir opciones de asistente de instalación para el dispositivo. Los usuarios no pueden anular la inscripción de dispositivos inscritos a través de DEP.

## <a name="apple-dep-management-for-ios-devices-with-microsoft-intune"></a>Administración de DEP de Apple para dispositivos iOS con Microsoft Intune
Para administrar dispositivos iOS corporativos con el Programa de inscripción de dispositivos (DEP) de Apple, la organización debe unirse a DEP de Apple y obtener dispositivos a través de ese programa. Puede consultar los detalles de este proceso en:  [https://deploy.apple.com](https://deploy.apple.com). Las ventajas del programa incluyen dispositivos configurados con manos libres sin necesidad de usar un cable USB para conectar cada dispositivo a un equipo.

Antes de poder inscribir dispositivos iOS corporativos con DEP, necesita un token de DEP de Apple. Este token permite a Intune sincronizar información sobre dispositivos corporativos que participan en DEP. También permite a Intune realizar cargas de perfiles de inscripción a Apple y asignar dispositivos a esos perfiles.

1.  **Empezar a administrar dispositivos iOS con Microsoft Intune**</br>
    Antes de poder inscribir dispositivos del Programa de inscripción de dispositivos (DEP) iOS, debe finalizar la habilitación de la administación iOS para Intune.

2.  **Obtener una clave de cifrado**</br>
    Como usuario administrativo, abra la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Administración** &gt; **Administración de dispositivos móviles** &gt; **iOS** &gt; **Programa de inscripción de dispositivos** y, después, elija **Descargar clave de cifrado**. Guarde el archivo de clave de cifrado (.pem) localmente. El archivo .pem se usa para solicitar un certificado de relación de confianza en el portal del Programa de Inscripción de Dispositivos de Apple.

      ![Actualizar un token del programa de inscripción de dispositivos](../media/dev-sa-ios-dep.png)

3.  **Obtener un token del programa de inscripción de dispositivos**</br>
    Vaya al [portal del Programa de inscripción de dispositivos](https://deploy.apple.com) (https://deploy.apple.com) e inicie sesión con su identificador de Apple de empresa. Este identificador de Apple debe usarse posteriormente para renovar el token de DEP.

    1.  En el [portal del Programa de inscripción de dispositivos](https://deploy.apple.com), vaya a **Programa de inscripción de dispositivos** &gt; **Administrar servidores** y, después, elija **Add MDM Server (Agregar servidor MDM)**.

    2.  Escriba el **nombre del servidor MDM** y, después, elija **Siguiente**. El nombre del servidor es su referencia para identificar el servidor de administración de dispositivos móviles (MDM). No es el nombre ni la dirección URL del servidor de Microsoft Intune.

    3.  Se abre el cuadro de diálogo **Agregar &lt;NombreDeServidor&gt;**. Elija **Elegir archivo...** para cargar el archivo .pem y, después, elija **Siguiente**.

    4.  El cuadro de diálogo **Agregar &lt;NombreDeServidor&gt;** muestra un vínculo **Your Server Token (Su token de servidor)**. Descargue el archivo de token de servidor (.p7m) en el equipo y, después, elija **Listo**.

    Este archivo de certificado (.p7m) se usa para establecer una relación de confianza entre los servidores de Intune y los del Programa de Inscripción de Dispositivos de Apple.

4.  **Agregar el token de DEP a Intune**</br>
    En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Administración** &gt; **Administración de dispositivos móviles** &gt; **iOS** &gt; **Programa de inscripción de dispositivos** y, después, elija **Cargar el token de DEP**. **Busque** el archivo de certificado (.p7m), escriba su **ID de Apple** y, después, elija **Cargar**.

5.  **Agregar la directiva de inscripción de dispositivos corporativos**</br>
    En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Directiva** &gt; **Inscripción de dispositivos corporativos** y, después, elija **Agregar**.

    Proporcione información **General**, incluidos el **Nombre** y la **Descripción**, y especifique si los dispositivos asignados al perfil tienen afinidad de usuario o pertenecen a un grupo.
      - **Solicitar afinidad de usuario**: el dispositivo se debe afiliar a un usuario durante la configuración inicial antes de que se le permita el acceso a los datos y al correo electrónico de la empresa como dicho usuario. La **afinidad de usuario** debe configurarse para dispositivos administrados por DEP que pertenezcan a usuarios y necesiten usar el portal de empresa (es decir, para instalar aplicaciones). La autenticación multifactor (MFA) no funciona durante la inscripción en dispositivos DEP con afinidad de usuario. Después de la inscripción, MFA funciona según lo previsto en estos dispositivos. 

      > [!NOTE]
      > DEP con la afinidad de usuario requiere un punto de conexión de WS-Trust 1.3 nombreDeUsuario/Mixto para que se habilite para solicitar el token de usuario.

      - **Sin afinidad de usuario**: el dispositivo no está afiliado a ningún usuario. Use esta afiliación para dispositivos que realizan tareas sin tener acceso a datos de usuario local. Las aplicaciones que requieren la afiliación de usuario, incluida la aplicación de portal de empresa que se usa para instalar aplicaciones de línea de negocio, no funcionarán.

    También puede **asignar dispositivos al siguiente grupo**. Elija **Seleccionar...** para elegir un grupo.

    [!INCLUDE[groups deprecated](../includes/group-deprecation.md)]

    Después, habilite **Configurar los ajustes del Programa de inscripción de dispositivos para esta directiva** para que admita DEP.

      ![Panel del asistente de configuración](../media/pol-sa-corp-enroll.png)

     Están disponibles las opciones siguientes para los dispositivos administrados por DEP:

     - **Departamento**: aparece cuando los usuarios pulsan **Acerca de la configuración** durante la activación.
     - **Teléfono de soporte técnico**: aparece cuando el usuario hace clic en el botón **Necesito ayuda** durante la activación.
     - **Modo de preparación**: se establece durante la activación y no se puede cambiar sin realizar el restablecimiento de fábrica del dispositivo:
        - **Sin supervisar**: funciones de administración limitadas.
        - **Supervisado**: permite más opciones de administración y deshabilita el bloqueo de activación de forma predeterminada.
     - **Bloquear el perfil de inscripción al dispositivo**: se establece durante la activación y no se puede cambiar sin realizar un restablecimiento de fábrica.
        - **Deshabilitar**: permite quitar el perfil de administración del menú **Configuración**.
        - **Habilitar** (requiere **Modo de preparación** = **Supervisado**): deshabilita la configuración de iOS que podría permitir quitar el perfil de administración.
     - **Opciones del Asistente para la configuración**: estas opciones opcionales se pueden configurar más adelante en el menú **Configuración** de iOS.
        - **Código de acceso**: solicita el código de acceso durante la activación. Solicite siempre un código de acceso, a menos que el dispositivo esté protegido o tenga el acceso controlado de otra manera (es decir, modo de quiosco que restringe el dispositivo a una aplicación).
        - **Servicios de ubicación**: si está habilitado, el Ayudante para la configuración solicitará el servicio durante la activación.
        - **Restauración**: si está habilitado, el Ayudante para la configuración solicitará una copia de seguridad de iCloud durante la activación.
        - **ID de Apple**: si está habilitado, iOS solicitará a los usuarios un identificador de Apple cuando Intune intente instalar una aplicación sin un identificador. Se requiere un identificador de Apple para descargar aplicaciones del App Store de iOS, incluidas las que instala Intune.
        - **Términos y condiciones**: si está habilitado, el Asistente para la configuración solicita a los usuarios que acepten los términos y condiciones de Apple durante la activación.
        - **Touch ID**: si está habilitado, el Ayudante para la configuración solicitará este servicio durante la activación.
        - **Apple Pay**: si está habilitado, el Ayudante para la configuración solicitará este servicio durante la activación.
        - **Zoom**: si está habilitado, el Ayudante para la configuración solicitará este servicio durante la activación.
        - **Siri**: si está habilitado, el Ayudante para la configuración solicitará este servicio durante la activación.
        - **Enviar datos de diagnóstico a Apple**: si está habilitado, el Ayudante para la configuración solicitará este servicio durante la activación.
     -  **Habilitar administración adicional de Apple Configurator**: establézcalo en **No permitir** para impedir la sincronización de archivos con iTunes o con la administración a través de Apple Configurator. Es una buena decisión elegir **No permitir**, exportar la configuración adicional de Apple Configurator y, después, implementarla como un perfil de configuración de iOS personalizado mediante Intune, en lugar de usar esta opción para permitir la implementación manual con o sin certificado.
        - **No permitir**: impide que el dispositivo se comunique a través de USB (deshabilita el emparejamiento).
        - **Permitir**: permite que un dispositivo se comunique a través de la conexión USB para cualquier equipo PC o Mac.
        - **Requerir certificado**: permite el emparejamiento con un Mac con un certificado importado en el perfil de inscripción.

6.  **Asignar dispositivos DEP para la administración** Vaya al [portal del Programa de inscripción de dispositivos](https://deploy.apple.com) (https://deploy.apple.com) e inicie sesión con su identificador de Apple de empresa. Vaya a **Programa de implementación** &gt; **Programa de inscripción de dispositivos** &gt; **Administrar dispositivos**. Especifique cómo va a **elegir los dispositivos**, proporcione información del dispositivo y especifique los detalles de cada dispositivo, como **Número de serie**y **Número de pedido**, o seleccione **Cargar archivo CSV**. Después, elija **Asignar al servidor**, elija el &lt;NombreDeServidor&gt; especificado para Microsoft Intune y elija **Aceptar**.

7.  **Sincronizar dispositivos administrados por DEP** Como usuario administrativo, abra la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Administración** &gt; **Administración de dispositivos móviles** &gt; **iOS** &gt; **Programa de inscripción de dispositivos** y, después, elija **Sincronizar ahora**. Se envía una solicitud de sincronización a Apple. Para ver los dispositivos administrados por DEP después de la sincronización, en la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Grupos** &gt; **Todos los dispositivos** &gt; **Dispositivos corporativos inscritos previamente** &gt; **Mediante número de serie de iOS**. En el área de trabajo **Mediante número de serie de iOS**, el **Estado** de los dispositivos administrados es "Sin contacto" hasta que se encienda el dispositivo y se ejecute el Asistente de configuración para inscribirlo.

    Para cumplir con las condiciones de Apple relativas a un tráfico DEP aceptable, Intune impone las restricciones siguientes:
     -  Una sincronización completa de DEP no se puede ejecutar más de una vez cada siete días. Durante una sincronización completa, Intune actualiza todos los números de serie que Apple ha asignado a Intune, independientemente de si el número de serie se ha sincronizado previamente o no. Si se intenta efectuar una sincronización completa sin que hayan pasado siete días desde la última sincronización completa, Intune solo actualizará los números de serie que aún no aparezcan en Intune.
     -  Las solicitudes de sincronización tardan 10 minutos en finalizar. Durante este tiempo, o hasta que la solicitud finalice correctamente, el botón **Sincronización** está deshabilitado.

8.  **Distribuir los dispositivos a los usuarios** Los dispositivos corporativos pueden distribuirse ahora a los usuarios. Los dispositivos iOS quedan inscritos para su administración mediante Intune al activarlos.

## <a name="changes-to-intune-group-assignments"></a>Cambios en las asignaciones de grupo de Intune

A partir de noviembre, la administración de grupos de dispositivos se moverá a Azure Active Directory. Después de la transición a los grupos de Azure Active Directory, la asignación de grupo no aparecerá en las opciones del **perfil de inscripción corporativa**. Como este cambio se implantará en una serie de meses, puede que no vea el cambio directamente. Después de moverse al nuevo portal, se pueden definir nuevas asignaciones de grupos de dispositivos dinámicos según el nombre del perfil de inscripción corporativa. Este proceso garantiza que los dispositivos que ya se han asignado previamente a un grupo de dispositivos se inscriban automáticamente en el grupo con la directiva y las aplicaciones implementadas. [Más información acerca de los grupos de Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-manage-groups/)

### <a name="see-also"></a>Consulte también
[Requisitos previos para la inscripción de dispositivos](prerequisites-for-enrollment.md)



<!--HONumber=Nov16_HO3-->


