---
title: "Inscripción de dispositivos iOS: Apple Configurator y el Asistente de configuración"
titlesuffix: Azure portal
description: "Aprenda a usar Apple Configurator para inscribir dispositivos iOS corporativos con el Asistente de configuración."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d384cd0-b662-41e7-94f5-0c96790ab20a
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b3ed7fe610f8101d90af044a8ff3849c57146c75
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2017
---
# <a name="enroll-ios-devices-with-apple-configurator"></a>Inscribir dispositivos iOS con Apple Configurator

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune permite la inscripción de dispositivos iOS con la herramienta [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) desde un equipo Mac. La inscripción con Apple Configurator requiere que conecte mediante USB cada dispositivo iOS a un equipo Mac para configurar la inscripción corporativa. Puede inscribir dispositivos en Intune con Apple Configurator de dos maneras:
- **Inscripción con el Asistente de configuración**: restablece la configuración de fábrica del dispositivo y lo prepara para la inscripción mediante el Asistente de configuración.
- **Inscripción directa**: no restablece la configuración de fábrica del dispositivo y lo inscribe mediante la configuración de iOS. Este método solo admite dispositivos **sin afinidad de usuario**.

No se pueden usar los métodos de inscripción de Apple Configurator con el [administrador de inscripción de dispositivos](device-enrollment-manager-enroll.md).

## <a name="prerequisites"></a>Requisitos previos

- Acceso físico a dispositivos iOS
- [Configurar entidad de MDM](mdm-authority-set.md)
- [Un certificado push MDM de Apple](apple-mdm-push-certificate-get.md)
- Números de serie del dispositivo (solo inscripción mediante el Asistente de configuración)
- Cables de conexión USB
- Equipo Mac con [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)

## <a name="create-an-apple-configurator-profile-for-devices"></a>Creación de un perfil de Apple Configurator para los dispositivos

Un perfil de inscripción de dispositivo define la configuración que se aplica durante la inscripción. Esta configuración se aplica una sola vez. Siga estos pasos para crear un perfil de inscripción para inscribir dispositivos iOS con Apple Configurator.

1. Inicie sesión en Azure Portal.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. Elija **Inscripción de dispositivos** > **Inscripción de Apple**.
4. En **Administrar la configuración de inscripción de Apple Configurator**, seleccione **Perfiles de AC**.
5. En la hoja **Perfiles de inscripción de Apple Configurator**, seleccione **Crear**.
6. Escriba un **nombre** y una **descripción** para el perfil con fines administrativos. Los usuarios no ven estos detalles. Puede usar este campo de nombre para crear un grupo dinámico en Azure Active Directory. Use el nombre de perfil para definir el parámetro enrollmentProfileName para asignar dispositivos con este perfil de inscripción. Obtenga más información sobre los grupos dinámicos de Azure Active Directory.

  ![Captura de pantalla de la pantalla de creación de perfil con inscripción con la afinidad de usuario seleccionada](./media/apple-configurator-profile-create.png)

7. Especifique la **Afinidad de usuario**:
   - **Inscribir con afinidad de usuario**: el dispositivo se debe afiliar a un usuario con el Asistente de configuración y, después, se le puede permitir el acceso a los datos y al correo electrónico de la empresa. Se requiere afinidad de usuario para los dispositivos administrados que pertenecen a usuarios y que necesitan usar el Portal de empresa para hacer uso de servicios, como instalar aplicaciones.
   - **Inscribir sin afinidad de usuario**: el dispositivo no está afiliado a ningún usuario. Utilice esta afiliación para dispositivos que realizan tareas sin tener acceso a datos de usuario local. Las aplicaciones que requieren la afiliación de un usuario no funcionarán, incluida la aplicación Portal de empresa cuando se usa para instalar aplicaciones de línea de negocio. Se requiere para la inscripción directa.

6. Seleccione **Crear** para guardar el perfil.

## <a name="setup-assistant-enrollment"></a>Inscripción con el asistente para la configuración

### <a name="add-apple-configurator-serial-numbers"></a>Adición de números de serie de Apple Configurator

**Adición de números de serie de Apple Configurator a Intune**

1. Cree una lista de valores separados por comas (.csv), con dos columnas, sin un encabezado. Agregue el número de serie en la columna izquierda y los detalles en la columna derecha. El número máximo actual de filas de la lista es 500. En un editor de texto, la lista .csv tiene este aspecto:

    F7TLWCLBX196,detalles de dispositivo</br>
    DLXQPCWVGHMJ,detalles de dispositivo

   Obtenga información sobre [cómo buscar el número de serie de un dispositivo iOS](https://support.apple.com/HT204073).
2. En Intune en Azure Portal, elija **Inscripción de dispositivos** y luego **Inscripción de Apple**.
3. En **Administrar la configuración de inscripción de Apple Configurator**, seleccione **Dispositivos de Apple Configurator**.
4. Seleccione **Agregar**.
5. Seleccione un **perfil de inscripción** para aplicarlo a los números de serie que se van a importar. Si importa un archivo con detalles nuevos que sobrescriben los existentes, seleccione **Sobrescribir detalles de identificadores existentes**.
6. Desplácese hasta el archivo .csv de números de serie y seleccione **Agregar**.

### <a name="reassign-a-profile-to-device-serial-numbers"></a>Reasignación de un perfil a los números de serie de los dispositivos

Los perfiles de inscripción se asignan al importar los números de serie de iOS para la inscripción de Apple Configurator. Intune también permite asignar perfiles desde dos sitios en Azure Portal:
- **Dispositivos de Apple Configurator**
- **Perfiles de AC**

#### <a name="assign-from-apple-configurator-devices"></a>Asignación desde dispositivos de Apple Configurator
1. En Intune en Azure Portal, elija **Inscripción de dispositivos** y luego **Inscripción de Apple**.
3. En la hoja **Dispositivos de Apple Configurator**, seleccione los números de serie a los que quiere asignar un perfil y luego seleccione **Asignar perfil**.
4. En la hoja **Asignar perfil**, seleccione el **Nuevo perfil** que quiera asignar y luego seleccione **Asignar**.

#### <a name="assign-from-profiles"></a>Asignación desde perfiles
1. En Intune en Azure Portal, elija **Inscripción de dispositivos** y luego **Inscripción de Apple**.
2. Elija **Perfiles de AC** y seleccione el perfil que quiera asignar a los números de serie.
3. En la hoja del perfil, seleccione **Dispositivos asignados** y **Asignar**.
4. Filtre para buscar los números de serie del dispositivo que quiera asignar al perfil, seleccione los dispositivos y elija **Asignar**.

### <a name="export-the-profile"></a>Exportación del perfil
Después de crear el perfil y asignar números de serie, debe exportar el perfil desde Intune como una dirección URL. Después, impórtelo en Apple Configurator en un equipo Mac para su implementación en dispositivos.

1. En Intune en Azure Portal, seleccione **Inscripción de dispositivos** > Inscripción de Apple** > **Perfiles de AC** y elija el perfil que quiera exportar.
2. En la hoja del perfil, seleccione **Exportar perfil**.
3. Copie la dirección URL del perfil. Puede agregarla a Apple Configurator más tarde para definir el perfil de Intune usado por los dispositivos iOS.

  Después, importe este perfil en Apple Configurator en el procedimiento siguiente para definir el perfil de Intune usado por dispositivos iOS.

### <a name="enroll-devices-with-setup-assistant"></a>Inscripción de dispositivos con el Asistente de configuración

1.  En un equipo Mac, abra **Apple Configurator 2**. En la barra de menús, elija **Apple Configurator 2** y, después, elija **Preferencias**.
  > [!WARNING]
  > Los dispositivos se restablecen en la configuración de fábrica durante el proceso de inscripción. Como procedimiento recomendado, restablezca el dispositivo y enciéndalo. Los dispositivos deberían estar en la pantalla **Hola** cuando conecte el dispositivo.

2. En el panel de **preferencias**, seleccione **Servidores** y elija el símbolo más (+) para iniciar el asistente del servidor MDM. Seleccione **Siguiente**.
3. Escriba el **nombre de host o la dirección URL** y la **dirección URL de inscripción** para el servidor MDM en el Asistente de configuración para la inscripción de dispositivos de iOS con Microsoft Intune. Para la dirección URL de inscripción, escriba la dirección URL del perfil de inscripción exportada desde Intune. Seleccione **Siguiente**.  

  Puede omitir de forma segura una advertencia que indica "no se comprueba la dirección URL del servidor". Para continuar, elija **Siguiente** hasta que finalice el asistente.
4.  Conecte los dispositivos móviles iOS al equipo Mac con un adaptador USB.
5.  Elija **Preparar**. En el panel **Prepare iOS Device** (Preparar el dispositivo iOS), seleccione **Manual** y luego elija **Siguiente**.
6. En el panel **Enroll in MDM Server** (Inscribir en servidor MDM), seleccione el nuevo servidor y elija **Siguiente**.
7. En el panel **Supervise Devices** (Supervisar dispositivos), seleccione el nivel de supervisión y luego elija **Siguiente**.
8. En el panel **Create an Organization** (Crear una organización), seleccione la **organización** o cree una nueva y luego elija **Siguiente**.
9. En el panel **Configure iOS Setup Assistant** (Configurar el Asistente de configuración de iOS), elija los pasos que se presentan al usuario y, después, elija **Preparar**. Si se le solicita, autentíquese para actualizar la configuración de confianza.  
10. Cuando el dispositivo iOS termine la preparación, desconecte el cable USB.  

### <a name="distribute-devices"></a>Distribuir los dispositivos
Los dispositivos ya están listos para la inscripción corporativa. Apague los dispositivos y distribúyalos a los usuarios. Cuando los usuarios enciendan sus dispositivos, se iniciará el Asistente de configuración.

Una vez que los usuarios reciban sus dispositivos, deberán completar el Asistente de configuración. Los dispositivos configurados con afinidad de usuario pueden instalar y ejecutar la aplicación del Portal de empresa para descargar aplicaciones y administrar dispositivos.

## <a name="direct-enrollment"></a>Inscripción directa
Cuando inscribe dispositivos iOS directamente con Apple Configurator, puede inscribir un dispositivo sin adquirir su número de serie. También puede nombrar el dispositivo con fines de identificación antes de que Intune capture el nombre del dispositivo durante la inscripción. No se admite la aplicación de portal de empresa para dispositivos inscritos directamente. Este método no realiza un restablecimiento de fábrica del dispositivo.

Las aplicaciones que requieren la afiliación de un usuario no se pueden instalar, incluida la aplicación del Portal de empresa cuando se usa para instalar aplicaciones de línea de negocio.

### <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>Exportación del perfil como .mobileconfig a dispositivos iOS
1. Inicie sesión en Azure Portal.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Exportar perfil**, descargue el perfil de inscripción en [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) para insertarlo directamente como un perfil de administración en dispositivos iOS.
4. Prepare el dispositivo con Apple Configurator mediante los pasos siguientes.
  1. En un equipo Mac, abra Apple Configurator 2.0.
  2. Conecte el dispositivo iOS al equipo Mac con un cable USB. Cierre Fotos, iTunes y otras aplicaciones que se abren en el dispositivo cuando se detecta el dispositivo.
  3. En Apple Configurator, elija el dispositivo iOS conectado y, después, elija el botón **Agregar**. Las opciones que se pueden agregar al dispositivo aparecen en la lista desplegable. Elija **Perfiles**.
  4. Use el selector de archivos para seleccionar el archivo .mobileconfig que ha exportado desde Intune y, después, elija **Agregar**. El perfil se agrega al dispositivo. Si el dispositivo es No supervisado, la instalación requiere la aceptación en el dispositivo.
5. Use los pasos siguientes para instalar el perfil en el dispositivo iOS. El dispositivo debe haber completado el Asistente de configuración y estar listo para usarse. Si la inscripción implica implementaciones de aplicaciones, el dispositivo debe tener un identificador de Apple configurado, porque las implementaciones de aplicaciones requieren que se disponga de un identificador de Apple con la sesión iniciada en App Store.
   1. Desbloquee el dispositivo iOS.
   2. En el cuadro de diálogo **Instalar el perfil** de **Perfil de administración**, elija **Instalar**.
   3. Proporcione el código de acceso del dispositivo o el identificador de Apple, si es necesario.
   4. Acepte la **advertencia** y elija **Instalar**.
   5. Acepte la **advertencia remota** y elija **Confiar**.
   6. Cuando el cuadro **Perfil instalado** confirme el perfil como Instalado, elija **Listo**.

6. En el dispositivo iOS, abra **Configuración** y vaya a **General**  > **Administración de dispositivos** > **Perfil de administración**. Confirme que aparece la instalación del perfil y compruebe las restricciones de directivas de iOS y las aplicaciones instaladas. Las aplicaciones y las restricciones de directivas pueden tardar hasta 10 minutos en aparecer en el dispositivo.

7. Distribuya los dispositivos. Ahora el dispositivo iOS está inscrito en Intune y administrado.
