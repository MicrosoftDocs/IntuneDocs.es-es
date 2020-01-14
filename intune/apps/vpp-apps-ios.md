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
ms.openlocfilehash: 01c95e1961871f33a3d8ed8c0b6c22502faca3a9
ms.sourcegitcommit: 8d7406b75ef0d75cc2ed03b1a5e5f74ff10b98c0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2020
ms.locfileid: "75654029"
---
# <a name="how-to-manage-ios-and-macos-apps-purchased-through-apple-volume-purchase-program-with-microsoft-intune"></a>Administración de aplicaciones de iOS y macOS compradas a través del Programa de Compras por Volumen de Apple con Microsoft Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Apple le permite comprar varias licencias de una aplicación que quiera ejecutar en la empresa en dispositivos iOS y macOS. Comprar varias copias permite administrar de manera eficaz las aplicaciones de la empresa.

Microsoft Intune le ayuda a administrar varias copias de las aplicaciones que se adquirieron a través de este programa de las siguientes maneras:

- Informes sobre la información de licencia desde la tienda de aplicaciones.
- Realizando un seguimiento de cuántas licencias ha usado.
- Le ayudamos a no instalar más copias de la aplicación que las que tiene.

Existen dos métodos que puede usar para asignar aplicaciones compradas por volumen:

## <a name="device-licensing"></a>Licencias de dispositivo

Cuando asigna una aplicación a los dispositivos, se usa una licencia de aplicación y permanece asociada con el dispositivo al que se le ha asignado.

Cuando asigna aplicaciones compradas por volumen a un dispositivo, el usuario final del dispositivo no tiene que proporcionar un id. de Apple para tener acceso a la tienda.

## <a name="user-licensing"></a>Licencias de usuario

Cuando asigna una aplicación a un usuario, se usa una licencia de aplicación para el usuario y se asocia con este. La aplicación se puede ejecutar en hasta cinco dispositivos propiedad del usuario (el límite de dispositivos lo controla Apple).

Cuando asigne una aplicación comprada por volumen a los usuarios, cada usuario final debe tener un ID de Apple válido y único para acceder al App Store.

Además, puede sincronizar, administrar y asignar los libros que haya adquirido a través de la tienda del Programa de Compras por Volumen (VPP) de Apple con Intune con dispositivos iOS. Para obtener más información, consulte [Administración de libros electrónicos de iOS comprados a través de un programa de compras por volumen](vpp-ebooks-ios.md).

## <a name="manage-volume-purchased-apps-for-ios-and-macos-devices"></a>Administración de aplicaciones compradas por volumen para dispositivos iOS y macOS

### <a name="supports-apple-volume-purchase-program-volume-purchased-apps"></a>Admite las aplicaciones compradas por volumen del Programa de Compras por Volumen de Apple

Compre varias licencias para aplicaciones iOS y macOS mediante el [Programa de Compras por Volumen de Apple para empresas](https://www.apple.com/business/vpp/) o el [Programa de Compras por Volumen de Apple para educación](https://volume.itunes.apple.com/us/store). Este proceso implica configurar una cuenta de VPP de Apple en el sitio web de Apple y cargar el token de VPP de Apple en Intune.  De este modo, puede sincronizar la información de compras por volumen con Intune y hacer el seguimiento del uso de aplicaciones compradas por volumen.

### <a name="supports-business-to-business-volume-purchased-apps"></a>Admite las aplicaciones de negocio a negocio compradas por volumen.

Además, los desarrolladores de terceros también pueden distribuir aplicaciones de forma privada a miembros autorizados del Programa de Compras por Volumen para la Empresa, especificados en App Store Connect. Estos miembros pueden iniciar sesión en la tienda de aplicaciones del Programa de Compras por Volumen y comprar aplicaciones. Las aplicaciones del VPP para empresas que haya comprado el usuario final se sincronizarán con sus inquilinos de Intune.

## <a name="before-you-start"></a>Antes de empezar
Antes de empezar, necesita obtener un token de VPP de Apple y cargarlo en la cuenta de Intune. Además, debe comprender los siguientes criterios:

* Puede asociar varios tokens de VPP con la cuenta de Intune.
* Si usó anteriormente un token de PCV con otro producto, debe generar uno nuevo para usarlo con Intune.
* La validez de cada token es de un año.
* De forma predeterminada, Intune se sincroniza con el servicio PCV de Apple dos veces al día. Puede iniciar una sincronización manual en cualquier momento.
* Antes de empezar a usar el VPP de Apple con Intune, quite todas las cuentas de usuario de VPP existentes creadas con otros proveedores de administración de dispositivos móviles (MDM). Intune no sincroniza esas cuentas de usuario en Intune como medida de seguridad. Intune solo sincroniza los datos del servicio VPP de Apple que se ha creado mediante Intune.
* El Programa Perfil de inscripción de dispositivos (DEP) de Apple automatiza la inscripción de la administración de dispositivos móviles (MDM). Puede usar DEP para configurar dispositivos corporativos sin tocarlos. Puede inscribirse en el programa DEP con la misma cuenta de agente de programa que usó con el VPP de Apple. El identificador del programa de implementación de Apple es único para los programas que aparecen en el sitio web [Deployment Programmes](https://deploy.apple.com) (Programas de implementación) de Apple y no se puede usar para iniciar sesión en los servicios de Apple, como la tienda iTunes.
* Cuando asigne aplicaciones de VPP con el modelo de licencias de usuario a los usuarios o dispositivos (con la afinidad de usuario), cada usuario de Intune necesita asociarse con un único id. de Apple o una dirección de correo electrónico cuando acepte los términos y condiciones de Apple en su dispositivo.
* Asegúrese de que cuando configure un dispositivo para un nuevo usuario de Intune, lo configura con esa dirección de correo electrónico o con el Id. de Apple únicos del usuario. La dirección de correo electrónico o el id. de Apple y el usuario de Intune forman un único par y pueden usarse en hasta cinco dispositivos.
* Un token de VPP solo se admite para su uso en una cuenta de Intune a la vez. No vuelva a usar el mismo token de VPP para varios inquilinos de Intune.

>[!IMPORTANT]
>Después de importar el token de PCV en Intune, no importe el mismo token en otra solución de administración de dispositivos. Si lo hace, podría perder la asignación de licencias y los registros de usuario.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Para obtener y cargar un token de PCV de Apple

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Seleccione **Administración de inquilinos** > **Conectores y tokens** > **Tokens de VPP de Apple**.
4. En la lista del panel de tokens del VPP, seleccione **Crear**.
5. En el panel **Crear token de VPP**, especifique la información siguiente:
    - **Archivo de token de VPP**: si aún no lo ha hecho, regístrese en el Programa de compras por volumen para empresas o el Programa para educación. Después de registrarse, descargue el token de VPP de Apple para la cuenta y selecciónelo aquí.
    - **Id. de Apple**: escriba el identificador de Apple de la cuenta asociada con el programa de compras por volumen.
    - **Tomar el control del token desde otro MDM**: si establece esta opción en **sí**, el token se puede reasignar a Intune desde otro MDM.
    - **Nombre de token**: un campo administrativo para establecer el nombre del token.    
    - **País o región**: seleccione el país o la región de la tienda del VPP.  Intune sincroniza las aplicaciones de VPP para todas las configuraciones regionales desde la instancia de App Store del país o la región de VPP especificada.
        > [!WARNING]  
        > Al cambiar el país o la región, se actualizarán los metadatos de las aplicaciones y almacenarán la dirección URL en la siguiente sincronización con el servicio de Apple de las aplicaciones creadas con ese token. La aplicación no se actualizará si no existe en la tienda del nuevo país o región.

    - **Tipo de cuenta de VPP**: elija **Empresa** o **Educación**.
    - **Actualizaciones automáticas de la aplicación**: elija entre **activar** o **desactivar** las actualizaciones automáticas. Cuando se habilite, Intune detectará las actualizaciones de la aplicación de VPP dentro de la App Store y las insertará automáticamente en el dispositivo cuando este se registre. Las actualizaciones automáticas de la aplicación para aplicaciones del PCV de Apple actualizarán automáticamente solo las aplicaciones implementadas con la intención de instalación **Obligatorio**. En el caso de las aplicaciones implementadas con la intención de instalación **Disponible**, el usuario verá que la aplicación no está instalada en el Portal de empresa, aunque se haya instalado una versión anterior de la aplicación. En este caso, el usuario puede volver a instalar la aplicación con un clic en **Instalar** en la pantalla de detalles de la aplicación del Portal de empresa para instalar la versión más reciente de la aplicación. Tenga en cuenta que para los dispositivos iOS inscritos por el usuario, los usuarios finales seguirán viendo todas las aplicaciones de VPP con licencia de usuario en el Portal de empresa. 

        > [!NOTE]
        > Las actualizaciones de aplicaciones automáticas funcionan en las aplicaciones con licencia de dispositivo y usuario de iOS 11.0 y versiones posteriores o de macOS 10.12 y versiones posteriores.

    - **Concedo permiso a Microsoft para enviar información del usuario y del dispositivo a Apple.** -Debe seleccionar **Acepto** para continuar. Para revisar qué datos envía Microsoft a Apple, consulte [Datos que Intune envía a Apple](~/protect/data-intune-sends-to-apple.md).

6. Cuando haya terminado, seleccione **Crear**.

El token se muestra en el panel de la lista de tokens.

Puede sincronizar los datos que tiene Apple con Intune en cualquier momento al elegir **Sincronizar ahora**.

## <a name="to-assign-a-volume-purchased-app"></a>Para asignar una aplicación comprada por volumen

1. Seleccione **Aplicaciones** > **Todas las aplicaciones**.
2. En el panel de la lista de aplicaciones, elija la aplicación que quiera asignar y elija **Asignaciones**.
3. En el panel ***Nombre de la aplicación*** - **Asignaciones**, elija **Agregar grupo** y, en el panel **Agregar grupo**, elija un **Tipo de asignación** y los grupos de dispositivos o de usuarios de Azure AD a los que quiera asignar la aplicación.
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
| 1 | BYOD: usuario con licencia                             | S                                                                                               | S                                           | S                                 |
| 2 | Corp: usuario con licencia (dispositivo no supervisado)     | S                                                                                               | S                                           | S                                 |
| 3 | Corp: usuario con licencia (dispositivo supervisado)         | S                                                                                               | No                                           | S                                 |
| 4 | BYOD: dispositivo con licencia                           | No                                                                                               | S                                           | No                                 |
| 5 | Corp: dispositivo con licencia (dispositivo no supervisado)                           | No                                                                                               | S                                           | No                                 |
| 6 | Corp: dispositivo con licencia (dispositivo supervisado)                           | No                                                                                               | No                                           | No                                 |
| 7 | Pantalla completa (dispositivo supervisado): dispositivo con licencia | No                                                                                               | No                                           | No                                 |
| 8 | Pantalla completa (dispositivo supervisado): usuario con licencia   | --- | ---                                          | ---                                |

> [!Note]  
> No se recomienda asignar aplicaciones de VPP a dispositivos en modo de pantalla completa que usen licencias de usuario de VPP.

## <a name="revoking-app-licenses"></a>Revocación de las licencias de aplicación

Puede revocar todas las licencias de aplicación del Programa de Compras por Volumen (VPP) de iOS o macOS asociadas en función de un dispositivo, usuario o aplicación determinados,  pero hay algunas diferencias entre las plataformas iOS y macOS. 

### <a name="revoking-app-licenses-on-ios"></a>Revocación de licencias de aplicación en iOS
Puede notificar a los usuarios cuando una aplicación ya no esté asignada a ellos. Sin embargo, al revocar una licencia de aplicación no se desinstalará la aplicación VPP del dispositivo. Para desinstalar una aplicación de VPP y reclamar una licencia de aplicación asignada a un usuario o a un dispositivo, debe cambiar la acción de asignación a **Desinstalar**. Si quita una aplicación que estaba asignada a un usuario, Intune reclama la licencia de usuario o dispositivo y desinstala la aplicación del dispositivo. El número de licencias reclamadas se indicará en el nodo **Aplicaciones con licencia** en la carga de trabajo **Aplicación** de Intune. Después de haber desinstalado una aplicación de VPP y de haber reclamado la licencia de aplicación, puede decidir asignar esa licencia de aplicación a otro usuario o dispositivo.


### <a name="revoking-app-licenses-on-macos"></a>Revocación de licencias de aplicación en macOS
Sin embargo, al revocar una licencia de aplicación no se desinstala la aplicación VPP del dispositivo. Al revocar una licencia de aplicación que se asignó a un usuario, Intune reclama la licencia de usuario o dispositivo. La aplicación macOS a la que se le revocó la licencia se puede seguir usando en el dispositivo, pero no se puede actualizar hasta que se vuelva a asignar una licencia al usuario o al dispositivo. Según Apple, estas aplicaciones se quitan después de un período de gracia de 30 días. Sin embargo, Apple no proporciona un medio para que Intune quite la aplicación mediante la acción de asignación **Desinstalar**, pero sí se puede optar por asignar la licencia de la aplicación reclamada a otro usuario o dispositivo.

>[!NOTE]
>Cuando un empleado abandone la empresa y deje de formar parte de los grupos de AAD, Intune recuperará las licencias de aplicación de VPP de iOS y de macOS con licencia de usuario.

## <a name="deleting-vpp-tokens"></a>Eliminación de tokens de VPP
<!-- 820879 -->  
Puede eliminar un token del Programa de Compras por Volumen (VPP) de Apple con la consola. Esto puede resultar necesario cuando tiene instancias duplicadas de un token de VPP. Si elimina un token, también se eliminarán la asignación y las aplicaciones asociadas. En cambio, si elimina un token, no se revocan las licencias de aplicación ni se desinstalan aplicaciones. 

>[!NOTE]
>Intune no puede revocar las licencias de aplicación después de que se haya eliminado un token. 

<!-- 820870 -->  
Para revocar la licencia de todas las aplicaciones de VPP de un token de VPP determinado, primero debe revocar todas las licencias de aplicación asociadas con el token y, después, eliminar el token.

## <a name="renewing-app-licenses"></a>Renovación de licencias de aplicación

Puede renovar un token de PCV de Apple mediante la descarga de un nuevo token desde el portal del Programa de Compras por Volumen de Apple y la actualización del token existente en Intune.

## <a name="deleting-a-vpp-app"></a>Eliminación de una aplicación de VPP

En estos momentos, no se puede eliminar una aplicación VPP de iOS de Microsoft Intune.

## <a name="assigning-custom-role-permissions-for-vpp"></a>Asignación de permisos de rol personalizados para VPP

El acceso a los tokens de VPP de Apple y a las aplicaciones de VPP se puede controlar de manera independiente mediante los permisos asignados a los roles de administrador personalizados en Intune.

* Para permitir que un rol personalizado de Intune administre los tokens de VPP de Apple, en **Aplicaciones** > **Tokens de VPP de Apple**, asigne permisos para **Aplicaciones administradas**.
* Para permitir que un rol personalizado de Intune administre las aplicaciones compradas con tokens de VPP de iOS, en **Aplicaciones** > **Todas las aplicaciones**, asigne permisos para **Aplicaciones móviles**. 

## <a name="additional-information"></a>Información adicional

Si un usuario con un dispositivo válido intenta primero instalar una aplicación de VPP en un dispositivo, se le pedirá que se una al Programa de Compras por Volumen de Apple. Debe unirse para poder continuar con la instalación de la aplicación. La invitación para unirse al Programa de Compras por Volumen de Apple requiere que el usuario pueda usar la aplicación App Store en el dispositivos iOS o macOS. Si ha configurado una directiva para deshabilitar la aplicación App Store, las licencias de aplicaciones de VPP basadas en usuario no funcionan. La solución es quitar la directiva para permitir la aplicación App Store o usar licencias basadas en dispositivos.

Apple proporciona asistencia directa para crear y renovar tokens de VPP. Para obtener más información, vea el artículo [Distribuir contenidos a usuarios con el Programa de Compras por Volumen (PCV)](https://go.microsoft.com/fwlink/?linkid=2014661) de la documentación de Apple. 

Si en el portal de Intune se indica **Assigned to external MDM** (Asignado a una MDM externa), usted (el administrador) debe quitar el token de VPP de la MDM externa antes de usar el token de VPP en Intune.

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes

### <a name="how-long-does-the-portal-take-to-update-the-license-count-once-an-app-is-installed-or-removed-from-the-device"></a>¿Cuánto tarda el portal en actualizar el recuento de licencias cuando se instala una aplicación en el dispositivo o se quita de él?
La licencia debe actualizarse en unas horas tras la instalación o desinstalación de una aplicación. Tenga en cuenta que si el usuario final quita la aplicación del dispositivo, la licencia sigue asignada a ese usuario o dispositivo.

### <a name="is-it-possible-to-oversubscribe-an-app-and-if-so-in-what-circumstance"></a>¿Es posible saturar una aplicación y, si es así, en qué circunstancias?
Sí. El administrador de Intune puede saturar una aplicación. Por ejemplo, si el administrador adquiere 100 licencias de la aplicación XYZ y luego la destina a un grupo con 500 miembros. A los 100 primeros miembros (usuarios o dispositivos) se les asigna la licencia, mientras que el resto de los miembros ven un error al asignarse la licencia.

### <a name="how-frequently-does-intune-sync-vpp-tokens-with-apple"></a>¿Con qué frecuencia Intune sincroniza los tokens de VPP con Apple?
Intune sincroniza las licencias y los tokens de VPP con Apple dos veces al día. El administrador de Intune puede iniciar una sincronización manual en **Aplicaciones** > **Tokens de VPP de Apple**.

## <a name="next-steps"></a>Pasos siguientes

Consulte [Supervisión de aplicaciones](apps-monitor.md) para obtener información que le ayude a supervisar las asignaciones de aplicaciones.
