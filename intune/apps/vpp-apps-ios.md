---
title: Administración de aplicaciones de Apple compradas por volumen
titleSuffix: Microsoft Intune
description: Conozca cómo puede sincronizar las aplicaciones compradas por volumen en la App Store de iOS y macOS en Microsoft Intune y luego administrar y realizar el seguimiento de su uso.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0bc511669ec8a88523581b3afbcca161d5208934
ms.sourcegitcommit: de663ef5f3e82e0d983899082a7f5b62c63f24ef
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2020
ms.locfileid: "75956198"
---
# <a name="how-to-manage-ios-and-macos-apps-purchased-through-apple-volume-purchase-program-with-microsoft-intune"></a>Administración de aplicaciones de iOS y macOS compradas a través del Programa de Compras por Volumen de Apple con Microsoft Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Apple le permite adquirir varias licencias para una aplicación que desea usar en su organización en dispositivos iOS y macOS con [Apple Business Manager](https://business.apple.com/) o [Apple School Manager](https://school.apple.com/). De este modo, puede sincronizar la información de compras por volumen con Intune y hacer el seguimiento del uso de aplicaciones compradas por volumen. La adquisición de licencias de aplicaciones le ayuda a administrar de forma eficaz las aplicaciones de su empresa y a conservar la propiedad y el control de las aplicaciones adquiridas. 

Microsoft Intune le ayuda a administrar las aplicaciones que ha adquirido a través de este programa de las maneras siguientes:

- Sincronizando los tokens de ubicación que se descargan desde Apple Business Manager.
- Haciendo un seguimiento del número de licencias que están disponibles y que se han usado para las aplicaciones adquiridas.
- Ayudándole a instalar aplicaciones hasta el número de licencias que posee.

Además, puede sincronizar, administrar y asignar los libros que haya adquirido de Apple Business Manager con Intune en dispositivos iOS. Para obtener más información, consulte [Administración de libros electrónicos de iOS comprados a través de un programa de compras por volumen](vpp-ebooks-ios.md).

## <a name="what-are-location-tokens"></a>¿Qué son los tokens de ubicación?
Los tokens de ubicación también se conocen como tokens del Programa de Compras por Volumen (VPP) de Apple. Estos tokens se usan para asignar y administrar licencias adquiridas con Apple Business Manager. Los administradores de contenido pueden adquirir y asociar licencias con tokens de ubicación para los que tienen permisos en Apple Business Manager. Estos tokens de ubicación se descargan desde Apple Business Manager y se cargan en Microsoft Intune. Microsoft Intune admite la carga de varios tokens de ubicación por inquilino. La validez de cada token es de un año.

## <a name="how-are-purchased-apps-licensed"></a>¿Cómo se concede la licencia a las aplicaciones adquiridas?
Las aplicaciones adquiridas se pueden asignar a grupos con dos tipos de licencias que Apple ofrece para dispositivos iOS y macOS.

|   | Licencias de dispositivo | Licencias de usuario |
|-----|------------------|----------------|
| **Inicio de sesión en App Store** | No es necesario. | Cada usuario final debe usar un identificador de Apple único cuando se le pida que inicie sesión en App Store. |
| **Configuración del dispositivo que bloquea el acceso a App Store** | Las aplicaciones se pueden instalar y actualizar mediante el Portal de empresa. | La invitación para unirse al VPP de Apple requiere acceso a App Store. Si ha configurado una directiva para deshabilitar App Store, las licencias de aplicaciones de VPP basadas en usuario no funcionarán. |
| **Actualización automática de la aplicación** | Tal como se configura por el administrador de Intune en la configuración del token de VPP de Apple, donde el **tipo de asignación** de la aplicación es **necesario**. <br> <br> Si el **tipo de asignación** está **disponible para los dispositivos inscritos**, las actualizaciones de aplicaciones disponibles se pueden instalar desde el Portal de empresa. | Tal y como lo configuró el usuario final en la configuración personal de App Store. El administrador de Intune no puede administrarlo. |
| **Inscripción de usuarios** | No compatible. | Compatible con identificadores de Apple administrados. |
| **Libros** | No compatible. | Compatible. |
| **Licencias en uso** | 1 licencia por dispositivo. La licencia se asocia con el dispositivo. | 1 licencia para un máximo de 5 dispositivos con el mismo identificador de Apple personal. La licencia se asocia con el usuario. <br> <br> Un usuario final asociado a un identificador de Apple personal y un identificador de Apple administrado en Intune consume 2 licencias de aplicación.|
| **Migración de licencias** | Las aplicaciones se pueden migrar silenciosamente desde una licencia de usuario a otra de dispositivo. | Las aplicaciones no se pueden migrar desde una licencia de dispositivo a otra de usuario. |

> [!NOTE]  
> El Portal de empresa no muestra las aplicaciones con licencia de dispositivo en los dispositivos de inscripción de usuarios, ya que solo se pueden instalar aplicaciones con licencia de usuario en dispositivos de inscripción de usuario.

## <a name="what-app-types-are-supported"></a>¿Qué tipos de aplicación se admiten?
Puede comprar y distribuir aplicaciones públicas y privadas con Apple Business Manager.
- **Aplicaciones de la Tienda**: Con Apple Business Manager, los administradores de contenido pueden comprar aplicaciones gratuitas y de pago que están disponibles en App Store.
- **Aplicaciones personalizadas:** Con Apple Business Manager, los administradores de contenido también pueden comprar aplicaciones personalizadas que estén disponibles de forma privada para su organización. Estas aplicaciones se adaptan a las necesidades específicas de su organización por parte de los desarrolladores con los que trabaja directamente. Obtenga más información sobre [cómo distribuir aplicaciones personalizadas](https://developer.apple.com/business/custom-apps/).

## <a name="prerequisites"></a>Requisitos previos
- Una cuenta de [Apple Business Manager](https://business.apple.com/) o [Apple School Manager](https://school.apple.com/) para su organización. 
- Licencias de aplicaciones adquiridas asignadas a uno o varios tokens de ubicación. 
- Tokens de ubicación descargados. 

> [!IMPORTANT]
> - Un token de ubicación solo se puede usar con una solución de administración de dispositivos a la vez. Antes de empezar a usar aplicaciones adquiridas con Intune, revoque y quite los tokens de ubicación existentes que se usan con otro proveedor de administración de dispositivos móviles (MDM). 
> - Un token de ubicación solo se admite para su uso en un inquilino de Intune a la vez. No vuelva a usar el mismo token para varios inquilinos de Intune.
> - De forma predeterminada, Intune sincroniza los tokens de ubicación con Apple dos veces al día. Puede iniciar una sincronización manual en cualquier momento desde Intune.
> - Después de importar el token de ubicación en Intune, no importe el mismo token en otra solución de administración de dispositivos. Si lo hace, podría perder la asignación de licencias y los registros de usuario.

## <a name="migrate-from-volume-purchase-program-vpp-to-apps-and-books"></a>Migración desde el Programa de Compras por Volumen (VPP) a Apps y libros
Si su organización aún no ha migrado a Apple Business Manager o Apple School Manager, consulte la [guía de Apple sobre la migración de Apps y libros](https://support.apple.com/HT208257) antes de continuar con la administración de aplicaciones adquiridas en Intune.

> [!IMPORTANT]
> - Para disfrutar de la mejor experiencia de migración, migre solo un comprador de VPP por ubicación. Si cada comprador se migra a una ubicación única, todas las licencias (asignadas y sin asignar) se moverán a Apps y libros.
> - No elimine el token de VPP heredado existente en Intune ni las aplicaciones y asignaciones asociadas al token de VPP heredado existente en Intune. Estas acciones requerirán que se vuelvan a crear todas las asignaciones de aplicaciones en Intune.

Migre el contenido y los tokens de VPP adquiridos existentes a Apps y libros en Apple Business Manager o Apple School Manager como se indica a continuación:

1. Invite a los compradores de VPP a que se unan a su organización y a que pidan a cada usuario que seleccionen una ubicación única. 
2. Asegúrese de que todos los compradores de PCV de su organización hayan completado el paso 1 antes de continuar.
3. Compruebe que todas las licencias y aplicaciones adquiridas se han migrado a Apps y libros en Apple Business Manager o Apple School Manager.
4. Descargue el nuevo token de ubicación; para ello, vaya a **Apple Business (o School) Manager** > **Ajustes** > **Apps y libros** > **My Server Tokens** (Mis tokens de servidor).
5. Actualice el token de ubicación en el Centro de administración del Administrador de puntos de conexión de Microsoft. Para ello, vaya a **Tenant administration** > **Connectors and tokens** > **Apple VPP tokens** y sincronice el token (Administración de inquilinos > Conectores y tokens > Tokens de VPP de Apple).

## <a name="upload-an-apple-vpp-or-location-token"></a>Carga de un token de VPP o de ubicación de Apple

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Seleccione **Administración de inquilinos** > **Conectores y tokens** > **Tokens de VPP de Apple**.
4. En la lista del panel de tokens del VPP, seleccione **Crear**.
5. En el panel **Crear token de VPP**, especifique la información siguiente:
    - **Archivo de token de VPP**: si aún no lo ha hecho, regístrese en Apple Business Manager o Apple School Manager. Después de registrarse, descargue el token de VPP de Apple para la cuenta y selecciónelo aquí.
    - **Id. de Apple**: escriba el identificador de Apple administrado de la cuenta asociada con el token de carga.
    - **Tomar el control del token desde otro MDM**: si establece esta opción en **sí**, el token se puede reasignar a Intune desde otra solución de MDM.
    - **Nombre de token**: un campo administrativo para establecer el nombre del token.    
    - **País o región**: seleccione el país o la región de la tienda del VPP.  Intune sincroniza las aplicaciones de VPP para todas las configuraciones regionales desde la instancia de App Store del país o la región de VPP especificada.
        > [!WARNING]  
        > Al cambiar el país o la región, se actualizarán los metadatos de las aplicaciones y la dirección URL de App Store en la siguiente sincronización con el servicio de Apple de las aplicaciones creadas con ese token. La aplicación no se actualizará si no existe en la tienda del nuevo país o región.

    - **Tipo de cuenta de VPP**: elija **Empresa** o **Educación**.
    - **Actualizaciones automáticas de la aplicación**: elija entre **activar** o **desactivar** las actualizaciones automáticas. Cuando se habilite, Intune detectará las actualizaciones de la aplicación de VPP dentro de la App Store y las insertará automáticamente en el dispositivo cuando este se registre. 
        
        > [!NOTE] 
        > Las actualizaciones automáticas de la aplicación para aplicaciones del PCV de Apple actualizarán automáticamente solo las aplicaciones implementadas con la intención de instalación **Obligatorio**. En el caso de aplicaciones implementadas con la intención de instalación **Disponible**, la actualización automática genera un mensaje de estado dirigido al administrador en el que le informa de que hay disponible una versión nueva de la aplicación. Para ver este mensaje de estado, hay que seleccionar la aplicación, seleccionar la opción Estado de instalación del dispositivo y, finalmente, consultar Detalles del estado.  

    - **Concedo permiso a Microsoft para enviar información del usuario y del dispositivo a Apple.** -Debe seleccionar **Acepto** para continuar. Para revisar qué datos envía Microsoft a Apple, consulte [Datos que Intune envía a Apple](~/protect/data-intune-sends-to-apple.md).

6. Cuando haya terminado, seleccione **Crear**. El token se muestra en el panel de la lista de tokens.

## <a name="synchronize-a-vpp-token"></a>Sincronización de un token de VPP
Puede sincronizar los nombres de aplicación, los metadatos y la información de licencia de las aplicaciones adquiridas en Intune. para ello, elija **Sincronizar** para un token seleccionado.

## <a name="assign-a-volume-purchased-app"></a>Asignación de una aplicación comprada por volumen

1. Seleccione **Aplicaciones** > **Todas las aplicaciones**.
2. En el panel de la lista de aplicaciones, elija la aplicación que quiera asignar y elija **Asignaciones**.
3. En el panel **Nombre de la aplicación** - **Asignaciones**, elija **Agregar grupo** y, en el panel **Agregar grupo**, elija un **Tipo de asignación** y los grupos de dispositivos o de usuarios de Azure AD a los que quiera asignar la aplicación.
5. Para cada grupo que ha seleccionado, pulse las opciones siguientes:
    - **Tipo**: elija si la aplicación estará **disponible** (los usuarios finales pueden instalar la aplicación desde el Portal de empresa) o será **necesaria** (la aplicación se instalará automáticamente para los usuarios finales).
    - **Tipo de licencia**: elija **Licencias de usuario** o **Licencias de dispositivo**.
6. Cuando termine, elija **Guardar**.


>[!NOTE]
>No se admite el intento de implementación disponible para grupos de dispositivos; solo se admiten grupos de usuarios. La lista de aplicaciones mostradas está asociada con un token. Si tiene una aplicación que está asociada con varios tokens de VPP, verá la misma aplicación mostrándose varias veces; una por cada token.

## <a name="end-user-prompts-for-vpp"></a>Solicitudes de VPP al usuario final

El usuario final recibirá solicitudes para que instale la aplicación de VPP en diferentes situaciones. En la tabla siguiente se explica cada condición:

| # | Escenario                                | Invitar al programa VPP de Apple                              | Solicitud de instalación de la aplicación | Solicitud del ID de Apple |
|---|--------------------------------------------------|-------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------------|
| 1 | BYOD: usuario con licencia (no dispositivo de inscripción de usuario)                             | S                                                                                               | S                                           | S                                 |
| 2 | Corp: usuario con licencia (dispositivo no supervisado)     | S                                                                                               | S                                           | S                                 |
| 3 | Corp: usuario con licencia (dispositivo supervisado)         | S                                                                                               | No                                           | S                                 |
| 4 | BYOD: dispositivo con licencia                           | No                                                                                               | S                                           | No                                 |
| 5 | Corp: dispositivo con licencia (dispositivo no supervisado)                           | No                                                                                               | S                                           | No                                 |
| 6 | Corp: dispositivo con licencia (dispositivo supervisado)                           | No                                                                                               | No                                           | No                                 |
| 7 | Pantalla completa (dispositivo supervisado): dispositivo con licencia | No                                                                                               | No                                           | No                                 |
| 8 | Pantalla completa (dispositivo supervisado): usuario con licencia   | --- | ---                                          | ---                                |

> [!Note]  
> No se recomienda asignar aplicaciones de VPP a dispositivos en modo de pantalla completa que usen licencias de usuario.

## <a name="revoking-app-licenses"></a>Revocación de las licencias de aplicación

Puede revocar todas las licencias de aplicación del Programa de Compras por Volumen (VPP) de iOS o macOS asociadas en función de un dispositivo, usuario o aplicación determinados,  pero hay algunas diferencias entre las plataformas iOS y macOS. 

|   | iOS | macOS |
|-----|------------------|----------------|
| **Eliminación de la asignación de aplicaciones** | Si quita una aplicación que estaba asignada a un usuario, Intune reclama la licencia de usuario o dispositivo y desinstala la aplicación del dispositivo. | Al quitar una aplicación que se asignó a un usuario, Intune reclama la licencia de usuario o dispositivo. La aplicación no se desinstala del dispositivo. |
| **Revocación de la licencia de la aplicación** | La revocación de una licencia de aplicación recupera la licencia de aplicación del usuario o dispositivo. Debe cambiar la asignación a **Desinstalar** para quitar la aplicación del dispositivo. | La revocación de una licencia de aplicación recupera la licencia de aplicación del usuario o dispositivo. La aplicación macOS a la que se le revocó la licencia se puede seguir usando en el dispositivo, pero no se puede actualizar hasta que se vuelva a asignar una licencia al usuario o al dispositivo. Según Apple, estas aplicaciones se quitan después de un período de gracia de 30 días. Sin embargo, Apple no proporciona un medio para que Intune quite la aplicación mediante la acción de asignación Desinstalar.

>[!NOTE]
> - Cuando un empleado abandona la empresa y deja de formar parte de los grupos de AAD, Intune reclama las licencias de aplicaciones.
> - Al asignar una aplicación comprada con la intención **Desinstalar**, Intune recupera la licencia y desinstala la aplicación.
> - Las licencias de aplicaciones no se reclaman cuando se quita un dispositivo de la administración de Intune. 

## <a name="deleting-vpp-tokens"></a>Eliminación de tokens de VPP
<!-- 820879 -->  
Puede eliminar un token del Programa de Compras por Volumen (VPP) de Apple con la consola. Esto puede resultar necesario cuando tiene instancias duplicadas de un token de VPP. Si elimina un token, también se eliminarán la asignación y las aplicaciones asociadas. En cambio, si elimina un token, no se revocan las licencias de aplicación ni se desinstalan aplicaciones. 

>[!NOTE]
>Intune no puede revocar las licencias de aplicación después de que se haya eliminado un token. 

<!-- 820870 -->  
Para revocar la licencia de todas las aplicaciones de VPP de un token de VPP determinado, primero debe revocar todas las licencias de aplicación asociadas con el token y, después, eliminar el token.

## <a name="renewing-app-licenses"></a>Renovación de licencias de aplicación

Puede renovar un token de VPP de Apple mediante la descarga de un nuevo token desde Apple Business Manager o Apple School Manager y la actualización del token existente en Intune.

## <a name="deleting-a-vpp-app"></a>Eliminación de una aplicación de VPP

En estos momentos, no se puede eliminar una aplicación VPP de iOS de Microsoft Intune.

## <a name="assigning-custom-role-permissions-for-vpp"></a>Asignación de permisos de rol personalizados para VPP

El acceso a los tokens de VPP de Apple y a las aplicaciones de VPP se puede controlar de manera independiente mediante los permisos asignados a los roles de administrador personalizados en Intune.

* Para permitir que un rol personalizado de Intune administre los tokens de VPP de Apple, en **Aplicaciones** > **Tokens de VPP de Apple**, asigne permisos para **Aplicaciones administradas**.
* Para permitir que un rol personalizado de Intune administre las aplicaciones compradas con tokens de VPP de iOS, en **Aplicaciones** > **Todas las aplicaciones**, asigne permisos para **Aplicaciones móviles**. 

## <a name="additional-information"></a>Información adicional

Apple proporciona asistencia directa para crear y renovar tokens de VPP. Para obtener más información, vea el artículo [Distribuir contenidos a usuarios con el Programa de Compras por Volumen (PCV)](https://go.microsoft.com/fwlink/?linkid=2014661) de la documentación de Apple. 

Si en el portal de Intune se indica **Assigned to external MDM** (Asignado a una MDM externa), usted (el administrador) debe quitar el token de VPP de la MDM externa antes de usar el token de VPP en Intune.

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes

### <a name="how-many-tokens-can-i-upload"></a>¿Cuántos tokens puedo cargar?
Puede cargar hasta 3000 tokens en Intune.

### <a name="how-long-does-the-portal-take-to-update-the-license-count-once-an-app-is-installed-or-removed-from-the-device"></a>¿Cuánto tarda el portal en actualizar el recuento de licencias cuando se instala una aplicación en el dispositivo o se quita de él?
La licencia debe actualizarse en unas horas tras la instalación o desinstalación de una aplicación. Tenga en cuenta que si el usuario final quita la aplicación del dispositivo, la licencia sigue asignada a ese usuario o dispositivo.

### <a name="is-it-possible-to-oversubscribe-an-app-and-if-so-in-what-circumstance"></a>¿Es posible saturar una aplicación y, si es así, en qué circunstancias?
Sí. El administrador de Intune puede saturar una aplicación. Por ejemplo, si el administrador adquiere 100 licencias de la aplicación XYZ y luego la destina a un grupo con 500 miembros. A los 100 primeros miembros (usuarios o dispositivos) se les asigna la licencia, mientras que el resto de los miembros ven un error al asignarse la licencia.


## <a name="next-steps"></a>Pasos siguientes

Consulte [Supervisión de aplicaciones](apps-monitor.md) para obtener información que le ayude a supervisar las asignaciones de aplicaciones.

Consulte [Solucionar problemas de instalación de aplicaciones](~/apps/troubleshoot-app-install.md) para obtener información sobre la solucionar problemas relacionados con la aplicación.
