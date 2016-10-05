---
title: "Administración de DEP de Apple para dispositivos iOS | Microsoft Intune"
description: "Implemente un perfil de inscripción que inscriba dispositivos iOS adquiridos a través del programa de inscripción de dispositivos (DEP) iOS &quot;de forma inalámbrica&quot; para administrar dispositivos Apple."
keywords: 
author: NathBarn
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
ms.sourcegitcommit: e2daff5dae435df55c866adbf602f554500d50e0
ms.openlocfilehash: e898d070eb61583ff379821c9bf24f3997ae177e


---

# Inscribir dispositivos iOS de la empresa mediante el Programa de inscripción de dispositivos
Microsoft Intune puede implementar un perfil de inscripción que inscriba dispositivos iOS adquiridos a través del programa de inscripción de dispositivos (DEP) de Apple "de forma inalámbrica". El paquete de inscripción puede incluir opciones de asistente de instalación para el dispositivo. Los usuarios no pueden anular la inscripción de dispositivos inscritos a través de DEP.

## Administración de DEP de Apple para dispositivos iOS con Microsoft Intune
Para administrar dispositivos iOS de empresa con el programa de inscripción de dispositivos (DEP) de Apple, la organización debe unirse a DEP de Apple y adquirir dispositivos a través de ese programa. Puede consultar los detalles de este proceso en:  [https://deploy.apple.com](https://deploy.apple.com). Las ventajas del programa incluyen dispositivos configurados con manos libres sin necesidad de conectar cada dispositivo mediante USB a un equipo.

Para poder inscribir dispositivos iOS de empresa con DEP, necesita un token de DEP de Apple. Este token permite a Intune sincronizar información sobre dispositivos propiedad de la empresa que participan en DEP. También permite a Intune realizar cargas de perfiles de inscripción a Apple y asignar dispositivos a esos perfiles.

1.  **Empezar a administrar dispositivos iOS con Microsoft Intune** Para poder inscribir dispositivos del programa de inscripción de dispositivos (DEP) de iOS, debe habilitar la opción de administración de iOS para Intune.

2.  **Obtener una clave de cifrado** Como usuario administrativo, abra la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Administración** &gt; **Administración de dispositivos móviles** &gt; **iOS** &gt; **Programa de inscripción de dispositivos** y haga clic en **Descargar clave de cifrado**. Guarde el archivo de clave de cifrado (.pem) localmente. El archivo .pem se usa para solicitar un certificado de relación de confianza en el portal del Programa de Inscripción de Dispositivos de Apple.

      ![Actualizar un token del programa de inscripción de dispositivos](../media/dev-sa-ios-dep.png)

3.  **Obtener un token del Programa de inscripción de dispositivos** Vaya al [portal del Programa de inscripción de dispositivos](https://deploy.apple.com) (https://deploy.apple.com) e inicie sesión con su identificador de Apple de empresa. Este identificador de Apple debe usarse posteriormente para renovar el token de DEP.

    1.  En el [portal del Programa de inscripción de dispositivos](https://deploy.apple.com), vaya a **Programa de inscripción de dispositivos** &gt; **Administrar servidores** y, después, haga clic en **Agregar servidor MDM**.

    2.  Escriba el **nombre del servidor MDM** y, a continuación, haga clic en **Siguiente**. El nombre del servidor es su referencia para identificar el servidor MDM. No es el nombre o la dirección URL del servidor de Microsoft Intune.

    3.  Se abre el cuadro de diálogo **Agregar &lt;NombreDeServidor&gt;**. Haga clic en **Elegir archivo...** para cargar el archivo .pem y, a continuación, haga clic en **Siguiente**.

    4.  En el cuadro de diálogo **Agregar &lt;NombreDeServidor&gt;** muestra el vínculo **Your Server Token** (Su token de servidor). Descargue el archivo de token de servidor (.p7m) en el equipo y, a continuación, haga clic en **Listo**.

    Este archivo de certificado (.p7m) se usa para establecer una relación de confianza entre los servidores de Intune y los del Programa de Inscripción de Dispositivos de Apple.

4.  **Agregar el token de DEP a Intune** En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Administración** &gt; **Administración de dispositivos móviles** &gt; **iOS** &gt; **Programa de inscripción de dispositivos** y haga clic en **Cargar el token de DEP**. **Busque** el archivo de certificado (.p7m), escriba su **ID de Apple**y haga clic en **Cargar**.

5.  **Agregar la directiva de inscripción de dispositivos corporativos** En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Directiva** &gt; **Inscripción de dispositivos corporativos** y, después, haga clic en **Agregar**.

    Proporcione información **General**, incluidos el **Nombre** y la **Descripción**, y especifique si los dispositivos asignados al perfil tienen afinidad de usuario o pertenecen a un grupo.
      - **Solicitar afinidad de usuario**: el dispositivo se debe afiliar a un usuario durante la configuración inicial y luego se le puede permitir el acceso a los datos y al correo electrónico de la empresa como dicho usuario.  La **afinidad de usuario** debe configurarse para dispositivos administrados por DEP que pertenezcan a usuarios y necesitan usar el Portal de empresa (es decir, instalar aplicaciones). **Nota:** Los dispositivos DEP con afinidad de usuario no admiten la autenticación multifactor.
      - **Sin afinidad de usuario**: el dispositivo no está afiliado a ningún usuario. Utilice esta afiliación para dispositivos que realizan tareas sin tener acceso a datos de usuario local. Las aplicaciones que requieren la afiliación de un usuario no funcionarán, incluida la aplicación Portal de empresa cuando se usa para instalar aplicaciones de línea de negocio.

    También puede **asignar dispositivos al siguiente grupo**. Haga clic en **Seleccionar...** para elegir un grupo.

    [!INCLUDE[groups deprecated](../includes/group-deprecation.md)]

    Después, habilite **Configurar los ajustes del Programa de inscripción de dispositivos para esta directiva** para que admita DEP.

      ![Panel del asistente de configuración](../media/pol-sa-corp-enroll.png)

     Están disponibles las opciones siguientes para los dispositivos administrados por DEP:

     - **Departamento**: aparece cuando los usuarios pulsan "Acerca de la configuración" durante la activación.
     - **Teléfono de soporte técnico**: se muestra cuando el usuario hace clic en el botón **Necesito ayuda** durante la activación.
     - **Modo de preparación**: este estado se establece durante la activación y no se puede cambiar sin realizar el restablecimiento de fábrica del dispositivo:
        - **Sin supervisar**: funciones de administración limitadas.
        - **Supervisado**: permite más opciones de administración y deshabilita el bloqueo de activación de forma predeterminada.
     - **Bloquear el perfil de inscripción al dispositivo**: este estado se establece durante la activación y no se puede cambiar sin realizar un restablecimiento de fábrica.
        - **Deshabilitar**: permite quitar el perfil de administración del menú **Configuración**.
        - **Habilitar** (requiere **Modo de preparación** = **Supervisado**): deshabilita la configuración de iOS que podría permitir quitar el perfil de administración.
     - **Opciones del Asistente para la configuración**: estas configuraciones son opcionales y se pueden configurar más adelante en el menú **Configuración** de iOS.
        - **Código de acceso**: solicita el código de acceso durante la activación. Solicite siempre un código de acceso, a menos que el dispositivo esté protegido o tenga el acceso controlado de otra manera (es decir, modo de quiosco que restringe el dispositivo a una aplicación).
        - **Servicios de ubicación**: si está habilitado, el Ayudante para la configuración solicitará el servicio durante la activación.
        - **Restauración**: si está habilitado, el Ayudante para la configuración solicitará una copia de seguridad de iCloud durante la activación.
        - **Identificador de Apple**: se requiere un identificador de Apple para descargar aplicaciones del App Store de iOS, incluidas las que instala Intune. Si está habilitado, iOS solicitará a los usuarios un identificador de Apple cuando Intune intente instalar una aplicación sin un identificador.
        - **Términos y condiciones**: si está habilitado, el Asistente para la configuración solicita a los usuarios que acepten los términos y condiciones de Apple durante la activación.
        - **Touch ID**: si está habilitado, el Ayudante para la configuración solicitará este servicio durante la activación.
        - **Apple Pay**: si está habilitado, el Ayudante para la configuración solicitará este servicio durante la activación.
        - **Zoom**: si está habilitado, el Ayudante para la configuración solicitará este servicio durante la activación.
        - **Siri**: si está habilitado, el Ayudante para la configuración solicitará este servicio durante la activación.
        - **Enviar datos de diagnóstico a Apple**: si está habilitado, el Ayudante para la configuración solicitará este servicio durante la activación.
     -  **Habilitar administración adicional de Apple Configurator**: establézcalo en **No permitir** para impedir la sincronización de archivos con iTunes o con la administración a través de Apple Configurator. Microsoft recomienda que lo establezca en **No permitir**, exporte la configuración adicional de Apple Configurator y, después, la implemente como un perfil de configuración de iOS personalizado mediante Intune, en lugar de usar esta opción para permitir la implementación manual con o sin certificado.
        - **No permitir**: impide que el dispositivo se comunique a través de USB (deshabilita el emparejamiento).
        - **Permitir**: permite que el dispositivo se comunique a través de la conexión USB para cualquier PC o Mac.
        - **Requerir certificado**: permite el emparejamiento con un Mac con un certificado importado en el perfil de inscripción.

6.  **Asignar dispositivos DEP para la administración** Vaya al [portal del Programa de inscripción de dispositivos](https://deploy.apple.com) (https://deploy.apple.com) e inicie sesión con su identificador de Apple de empresa. Vaya a **Programa de implementación** &gt; **Programa de inscripción de dispositivos** &gt; **Administrar dispositivos**. Especifique cómo va a **elegir los dispositivos**, proporcione información del dispositivo y especifique los detalles de cada dispositivo, como **Número de serie**y **Número de pedido**, o seleccione **Cargar archivo CSV**. Después, seleccione **Asignar al servidor**, seleccione el &lt;NombreDeServidor&gt; especificado para Microsoft Intune y haga clic en **Aceptar**.

7.  **Sincronizar dispositivos administrados por DEP** Como usuario administrativo, abra la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Administración** &gt; **Administración de dispositivos móviles** &gt; **iOS** &gt; **Programa de inscripción de dispositivos** y haga clic en **Sincronizar ahora**. Se envía una solicitud de sincronización a Apple. Para ver los dispositivos administrados por DEP después de la sincronización, en la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Grupos** &gt; **Todos los dispositivos** &gt; **Dispositivos corporativos inscritos previamente** &gt; **Mediante número de serie de iOS**. En el área de trabajo **Mediante número de serie de iOS**, el **Estado** de los dispositivos administrados es "Sin contacto" hasta que se encienda el dispositivo y se ejecute el Asistente de configuración para inscribirlo.

    Para cumplir con las condiciones de Apple relativas a un tráfico DEP aceptable, Intune impone las restricciones siguientes:
     -  Una sincronización completa de DEP no se puede ejecutar más de una vez cada 7 días. Durante una sincronización completa, Intune actualiza todos los números de serie que Apple asignó a Intune, independientemente de si el número de serie se ha sincronizado previamente o no. Si se intenta efectuar una sincronización completa sin que hayan pasado 7 días desde la última sincronización completa, Intune solo actualizará los números de serie que aún no aparezcan en Intune.
     -  Las solicitudes de sincronización tardan 10 minutos en completarse. Durante este tiempo, o hasta que la solicitud finalice correctamente, el botón de sincronización está deshabilitado.

8.  **Distribuir los dispositivos a los usuarios** Los dispositivos corporativos pueden distribuirse ahora a los usuarios. Los dispositivos iOS quedan inscritos para su administración mediante Intune al activarlos.

## Cambios en las asignaciones de grupo de Intune

A partir de noviembre, la administración de grupos de dispositivos se moverá a Azure Active Directory. Después de la transición a los grupos de Azure Active Directory, la asignación de grupo no aparecerá en las opciones del **perfil de inscripción corporativa**. Como este cambio se implantará en una serie de meses, puede que no vea el cambio directamente. Después de moverse al nuevo portal, se pueden definir nuevas asignaciones de grupos de dispositivos dinámicos según el nombre del perfil de inscripción corporativa. Este proceso garantiza que los dispositivos previamente asignados a un grupo de dispositivos se inscriban automáticamente en el grupo con la directiva y las aplicaciones implementadas. [Más información acerca de los grupos de Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-manage-groups/)

### Consulte también
[Preparar la inscripción de dispositivos](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Sep16_HO2-->


