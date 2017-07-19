---
title: "Inscripción de dispositivos iOS: Apple Configurator y el Asistente de configuración"
titleSuffix: Intune on Azure
description: "Aprenda a usar Apple Configurator para inscribir dispositivos iOS corporativos con el Asistente de configuración."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d384cd0-b662-41e7-94f5-0c96790ab20a
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1d74fbcebfe89bbafc545d11dd6316cb602db8ee
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="enroll-ios-devices-with-apple-configurator"></a>Inscribir dispositivos iOS con Apple Configurator

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune permite la inscripción de dispositivos iOS corporativos con la herramienta [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) desde un equipo Mac. La inscripción con Apple Configurator requiere que conecte mediante USB cada dispositivo iOS a un equipo Mac para configurar la inscripción corporativa. Puede inscribir dispositivos en Intune con Apple Configurator de dos maneras:
- **Inscripción con el Asistente de configuración**: este proceso restablece el dispositivo a la configuración de fábrica, lo prepara para ejecutar el Asistente de configuración e instala las directivas de la empresa para el nuevo usuario del dispositivo. En la mayoría de los casos será necesario que la directiva aplicada al dispositivo iOS incluya afinidad de usuario para habilitar la aplicación Portal de empresa de Intune.
- **Inscripción directa**: este proceso no restablece los valores de fábrica del dispositivo e inscribe el dispositivo con una directiva predefinida. Este método está destinado a los dispositivos **sin afinidad de usuario**.

>[!NOTE]
>Este método de inscripción no se puede usar con el método del [administrador de inscripción de dispositivos](device-enrollment-manager-enroll.md).

En [Choose how to enroll iOS devices in Intune](enrollment-method-choose-ios.md) (Selección del método para inscribir dispositivos iOS en Intune), se describen otros métodos de inscripción de dispositivos iOS).

## <a name="prerequisites"></a>Requisitos previos

Complete los siguientes requisitos previos antes de configurar la inscripción de dispositivos iOS:

- [Un certificado push MDM de Apple](apple-mdm-push-certificate-get.md)
- Acceso físico a dispositivos iOS
- Números de serie del dispositivo (vea [cómo encontrar el número de serie de un producto Apple](https://support.apple.com//HT204308))
- Cables de conexión USB
- Equipo Mac con [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)
- [Agregar números de serie de Apple Configurator](apple-configurator-serial-numbers-add.md)

## <a name="setup-assistant-enrollment"></a>Inscripción con el asistente para la configuración

### <a name="create-an-apple-configurator-profile-for-devices"></a>Creación de un perfil de Apple Configurator para los dispositivos

Un perfil de inscripción de dispositivo define la configuración que se aplica a un grupo de dispositivos. Los siguientes pasos muestran cómo crear un perfil de inscripción de dispositivos para dispositivos iOS inscritos mediante Apple Configurator.

1. En el portal de Intune, elija **Inscripción de dispositivos** y luego **Inscripción de Apple**.
2. En **Administrar la configuración de inscripción de Apple Configurator**, seleccione **Perfiles AC**.
3. En la hoja **Perfiles de inscripción de Apple Configurator**, seleccione **Crear**.
4. En la hoja **Crear perfil de inscripción**, escriba un nombre y una descripción para el perfil.
5. En **Afinidad de usuario**, elija si los dispositivos con este perfil se inscribirán con o sin afinidad de usuario.

   - **Inscribir con afinidad de usuario**: el dispositivo se debe afiliar a un usuario durante la configuración inicial y luego se le puede permitir el acceso a los datos y al correo electrónico de la empresa. La afinidad de usuario debe configurarse para dispositivos administrados que pertenezcan a usuarios y necesiten usar el Portal de empresa para hacer uso de servicios, como instalar aplicaciones.
   - **Inscribir sin afinidad de usuario**: el dispositivo no está afiliado a ningún usuario. Utilice esta afiliación para dispositivos que realizan tareas sin tener acceso a datos de usuario local. Las aplicaciones que requieren la afiliación de un usuario no funcionarán, incluida la aplicación Portal de empresa cuando se usa para instalar aplicaciones de línea de negocio.

6. Seleccione **Crear** para guardar el perfil.

### <a name="add-apple-configurator-serial-numbers"></a>Adición de números de serie de Apple Configurator

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Siga estos pasos para agregar números de serie a Intune cuando quiera [inscribir dispositivos iOS corporativos mediante Apple Configurator con el Asistente de configuración](apple-configurator-setup-assistant-enroll-ios.md). Puede agregar números de serie de uno en uno o cargar un archivo de valores separados por comas (CSV) de números de serie. Después de agregar números de serie, puede asignarles un perfil. El perfil contiene la configuración de administración específica que quiere aplicar a los dispositivos.

En [Choose how to enroll iOS devices in Intune](enrollment-method-choose-ios.md) (Selección del método para inscribir dispositivos iOS en Intune), se describen otros métodos de inscripción de dispositivos iOS).

**Adición de números de serie de Apple Configurator a Intune**

1. Cree una lista de valores separados por comas (.csv), con dos columnas, sin un encabezado. Agregue el identificador IMEI en la columna izquierda y los detalles en la columna derecha. El número máximo actual de filas de la lista es 500. En un editor de texto, la lista .csv tiene este aspecto:

    F7TLWCLBX196,detalles de dispositivo</br>
    DLXQPCWVGHMJ,detalles de dispositivo

2. En Azure Portal, seleccione **Inscribir dispositivos** y luego elija **Inscripción de Apple**.
3. En **Administrar la configuración de inscripción de Apple Configurator**, seleccione **Números de serie de Apple Configurator**.
4. En la hoja **Números de serie de Apple Configurator**, seleccione **Agregar**.
5. En la hoja **Agregar números de serie**, seleccione un perfil para aplicar a los números de serie que se van a importar. Si va a importar un archivo con nuevos detalles que sobrescribirán los existentes, seleccione Sobrescribir detalles de identificadores existentes para que los nuevos detalles sustituyan a los existentes.
6. Desplácese hasta el archivo .csv de números de serie y seleccione **Agregar**.

### <a name="assign-a-profile-to-specific-serial-numbers"></a>Asignación de un perfil específico a números de serie

Intune permite asignar perfiles de dos sitios diferentes en el portal de Azure. Puede realizar la asignación según el perfil de Apple Configurator o por dispositivos.

#### <a name="assign-by-devices"></a>Asignación por dispositivos
1. En el portal de Intune, elija **Inscripción de dispositivos** y luego **Inscripción de Apple**.
3. En la hoja **Dispositivos de Apple Configurator**, seleccione los números de serie a los que quiere asignar un perfil y luego seleccione **Asignar perfil**.
4. En la hoja **Asignar perfil**, seleccione el perfil que quiere asignar y luego seleccione **Asignar**.

#### <a name="assign-by-profiles"></a>Asignación por perfiles
1. En el portal de Intune, elija **Inscripción de dispositivos** y luego **Inscripción de Apple**.
2. Elija **Perfiles de AC** y seleccione el perfil al que desea asignar números de serie.
3. En la hoja con nombre para el perfil, seleccione **Números de serie** > **Asignar**.
4. Seleccione los números de serie que quiere asignar al perfil y luego seleccione el botón **Asignar**.

### <a name="export-the-profile-to-ios-devices"></a>Exportación del perfil a dispositivos iOS
Después de crear el perfil y asignar números de serie, tendrá que exportar el perfil de Intune, bien como una dirección URL o como un archivo en el formato que se describe a continuación. A continuación, impórtelo manualmente en el programa Apple Configurator en un Mac, después de lo cual este programa lo implementará en los dispositivos.

1. En el portal de Intune, elija **Perfiles de inscripción de Apple Configurator** y después elija el perfil que desea exportar.
2. En la hoja del perfil, seleccione **Exportar perfil**.
3. Copie la dirección URL en [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12), con el dispositivo iOS conectado. Se cargará en Apple Configurator más tarde para definir el perfil de Intune utilizado por los dispositivos iOS.

  En el procedimiento siguiente, esta dirección URL de perfil se carga en el servicio Apple mediante la herramienta Apple Configurator para definir el perfil de Intune utilizado por dispositivos iOS.
4. Cargue esta dirección URL del perfil en el servicio Apple mediante la herramienta Apple Configurator para definir el perfil de Intune usado por dispositivos iOS.
 1.  En un equipo Mac, abra **Apple Configurator 2**. En la barra de menús, elija **Apple Configurator 2** y, después, elija **Preferencias**.
  > [!WARNING]
  > Los dispositivos se restablecerán en la configuración de fábrica durante el proceso de inscripción. Como procedimiento recomendado, restablezca el dispositivo y enciéndalo. Los dispositivos deberían estar en la pantalla **Hola** cuando conecte el dispositivo.
  2. En el panel de **preferencias**, seleccione **Servidores** y elija el símbolo más (+) para iniciar el asistente del servidor MDM. Seleccione **Siguiente**.
  3. Escriba el **nombre de host o la dirección URL** y la **dirección URL de inscripción** para el servidor MDM en el Asistente de configuración para la inscripción de dispositivos de iOS con Microsoft Intune. Para la dirección URL de inscripción, escriba la dirección URL del perfil de inscripción exportada desde Intune. Seleccione **Siguiente**.  

    Puede omitir de forma segura una advertencia que indica "no se comprueba la dirección URL del servidor". Para continuar, elija **Siguiente** hasta que finalice el asistente.
  4.  Conecte los dispositivos móviles iOS al equipo Mac con un adaptador USB.
  > [!WARNING]
  > Los dispositivos se restablecerán en la configuración de fábrica durante el proceso de inscripción. Como procedimiento recomendado, restablezca el dispositivo y enciéndalo. Los dispositivos deberían estar en la pantalla **Hola** cuando inicia el Asistente de configuración.
  5.  Elija **Preparar**. En el panel **Prepare iOS Device** (Preparar el dispositivo iOS), seleccione **Manual** y luego elija **Siguiente**.
  6. En el panel **Enroll in MDM Server** (Inscribir en servidor MDM), seleccione el nuevo servidor y elija **Siguiente**.
  7. En el panel **Supervise Devices** (Supervisar dispositivos), seleccione el nivel de supervisión y luego elija **Siguiente**.
  8. En el panel **Create an Organization** (Crear una organización), seleccione la **organización** o cree una nueva y luego elija **Siguiente**.
  9. En el panel **Configure iOS Setup Assistant** (Configurar el Asistente de configuración de iOS), elija los pasos que se presentan al usuario y, después, elija **Preparar**. Si se le solicita, autentíquese para actualizar la configuración de confianza.  
  10. Cuando el dispositivo iOS termine la preparación, desconecte el cable USB.  
6.  **Distribuir los dispositivos**.
    Los dispositivos ya están listos para la inscripción corporativa. Apague los dispositivos y distribúyalos a los usuarios. Cuando los usuarios enciendan sus dispositivos, se iniciará el Asistente de configuración.

## <a name="direct-enrollment"></a>Inscripción directa
Cuando inscribe dispositivos iOS directamente con Apple Configurator, puede inscribir un dispositivo sin adquirir su número de serie. También puede nombrar el dispositivo con fines de identificación antes de que Intune capture el nombre del dispositivo durante la inscripción. No se admite la aplicación de portal de empresa para dispositivos inscritos directamente. Esta guía supone que se usa Apple Configurator 2.0 en un equipo Mac.

1. En el portal de Intune, elija **Inscripción de dispositivos**, **Inscripción de Apple** y luego seleccione **Perfiles de AC**.
2. En la hoja **Perfiles de inscripción de Apple Configurator**, seleccione **Crear**.
3. En la hoja **Crear perfil de inscripción**, escriba un nombre y una descripción para el perfil.
4. Para **Afinidad de usuario**, elija **Inscribir sin afinidad de usuario** para garantizar que el dispositivo no está asociado a un usuario. Utilice esta afiliación para dispositivos que realizan tareas sin tener acceso a datos de usuario local. Las aplicaciones que requieren la afiliación de un usuario no funcionarán, incluida la aplicación Portal de empresa cuando se usa para instalar aplicaciones de línea de negocio.
5. Seleccione **Crear** para guardar el perfil.

### <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>Exportación del perfil como .mobileconfig a dispositivos iOS

1. En la hoja **Exportar perfil**, descargue el perfil de inscripción en [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) para insertarlo directamente como un perfil de administración en un dispositivo iOS conectado. Este método no realiza un restablecimiento de fábrica del dispositivo.
2. Prepare el dispositivo con Apple Configurator mediante los pasos siguientes.
  1. En un equipo Mac, abra Apple Configurator 2.0.
  2. Conecte el dispositivo iOS al equipo Mac con un cable USB. Cierre Fotos, iTunes y otras aplicaciones que se abren en el dispositivo cuando se detecta el dispositivo.
  3. En Apple Configurator, elija el dispositivo iOS conectado y, después, elija el botón **Agregar**. Las opciones que se pueden agregar al dispositivo aparecen en la lista desplegable. Elija **Perfiles**.
  4. Use el selector de archivos para seleccionar el archivo .mobileconfig que ha exportado desde Intune y, después, elija **Agregar**. El perfil se agrega al dispositivo. Si el dispositivo es No supervisado, la instalación requerirá la aceptación en el dispositivo.
3. Use los pasos siguientes para instalar el perfil en el dispositivo iOS. El dispositivo debe haber completado el Asistente de configuración y estar listo para usarse. Si la inscripción implica implementaciones de aplicaciones, el dispositivo debe tener un identificador de Apple configurado, porque las implementaciones de aplicaciones requerirán que disponga de un identificador de Apple con la sesión iniciada en App Store.
   1. Desbloquee el dispositivo iOS.
   2. En el cuadro de diálogo **Instalar el perfil** de **Perfil de administración**, elija **Instalar**.
   3. Proporcione la contraseña de dispositivo o el id. de Apple, si es necesario.
   4. Acepte la **advertencia** y elija **Instalar**.
   5. Acepte la **advertencia remota** y elija **Confiar**.
   6. Cuando el cuadro **Perfil instalado** confirme el perfil como Instalado, elija **Listo**.

    4. En el dispositivo iOS, abra **Configuración** y vaya a **General**  > **Administración de dispositivos** > **Perfil de administración**. Confirme que aparece la instalación del perfil y compruebe las restricciones de directivas de iOS y las aplicaciones instaladas. Las aplicaciones y las restricciones de directivas pueden tardar hasta 10 minutos en aparecer en el dispositivo.

    5. Distribuya los dispositivos. Ahora el dispositivo iOS está inscrito con Intune y administrado.


## <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>Cómo los usuarios instalan y usan el Portal de empresa en sus dispositivos

Los dispositivos configurados con afinidad de usuario pueden instalar y ejecutar la aplicación del portal de empresa para descargar aplicaciones y administrar dispositivos. Después de que los usuarios reciben sus dispositivos, deben realizar los pasos adicionales que se describen a continuación para completar el Asistente de configuración e instalar la aplicación del Portal de empresa.
