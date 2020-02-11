---
title: 'Inscripción de dispositivos iOS: inscripción de usuario'
titleSuffix: Microsoft Intune
description: Aprenda a configurar la inscripción de usuarios de iOS e iPadOS.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/2/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0872eef38e3ea5a70ebb64d3ae3c62069045fa97
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754645"
---
# <a name="set-up-ios-and-ipados-user-enrollment-preview"></a>Configuración de la inscripción de usuarios de iOS y iPadOS (versión preliminar)

Puede configurar Intune para inscribir dispositivos iOS y iPadOS a través del proceso de inscripción de usuario de Apple. La inscripción de usuario proporciona a los administradores un subconjunto simplificado de opciones de administración en comparación con otros métodos de inscripción.

Para obtener más información acerca de las opciones disponibles con la inscripción de usuario, consulte [Acciones admitidas en la inscripción de usuarios, contraseñas y otras opciones](ios-user-enrollment-supported-actions.md).

> [!NOTE]
> La compatibilidad con la inscripción de usuario de Apple en Intune se encuentra actualmente en versión preliminar.

## <a name="prerequisites"></a>Requisitos previos
- [Autoridad de Administración de dispositivos móviles (MDM)](../fundamentals/mdm-authority-set.md)
- [Certificado push MDM de Apple](apple-mdm-push-certificate-get.md)
- [Identificadores de Apple administrados](https://support.apple.com/guide/apple-business-manager/mdm1c9622977/web).

## <a name="create-a-user-enrollment-profile-in-intune"></a>Creación de un perfil de inscripción de usuario en Intune

Un perfil de inscripción define la configuración que se aplica a un grupo de dispositivos durante la inscripción. 

1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Dispositivos** > **iOS** > **Inscripción de iOS** > **Tipos de inscripción (vista previa)**  > **Crear perfil** > **iOS/iPadOS**. En este perfil se indicará la experiencia de inscripción que tendrán los usuarios finales de iOS y iPadOS en los dispositivos no inscritos a través de un método corporativo de Apple. Si desea realizar cambios, puede editar este perfil después de haberlo creado.

    ![Creación de un perfil de inscripción de Apple](./media/ios-user-enrollment/create-profile.png)

2. En la página **Básico**, escriba la información pertinente en **Nombre** y **Descripción** para el perfil con fines administrativos. Los usuarios no ven estos detalles. Puede usar este campo de **nombre** para crear un grupo dinámico en Azure Active Directory. Use el nombre de perfil para definir el parámetro enrollmentProfileName para asignar dispositivos con este perfil de inscripción. Obtenga más información sobre los [grupos dinámicos de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#rules-for-devices).

    ![Página de aspectos básicos](./media/ios-user-enrollment/basics-page.png)


3. Seleccione **Siguiente**.

4. En la página **Configuración**, seleccione una de estas opciones para el **Tipo de inscripción**:

    ![Página de configuración](./media/ios-user-enrollment/settings-page.png)

    - **Inscripción de dispositivos**: todos los usuarios de este perfil usarán la Inscripción de dispositivos.
    - **Inscripción de usuarios**: todos los usuarios de este perfil usarán la Inscripción de usuarios.
    - **Determinar según la opción del usuario**: todos los usuarios de este grupo tendrán la posibilidad de elegir qué tipo de inscripción usar. Cuando los usuarios inscriban sus dispositivos, verán una opción de elegir entre **Soy el propietario de este dispositivo** y **(Empresa) es el propietario de este dispositivo**. Si optan por la segunda, el dispositivo se inscribirá mediante la inscripción de dispositivos. Si el usuario elige **Soy el propietario de este dispositivo**, tendrá otra opción para proteger todo el dispositivo o solo las aplicaciones y los datos relacionados con el trabajo. La selección del usuario final de si es el propietario del dispositivo determina qué tipo de inscripción se implementa en su dispositivo. Esta opción de usuario también se refleja en el atributo Propiedad del dispositivo en Intune. Para obtener más información sobre la experiencia del usuario, consulte [Configuración del acceso de dispositivos iOS a los recursos de la empresa](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).
    
5. Seleccione **Siguiente**.

6. En la página **Asignaciones**, elija los grupos de usuarios que contienen los usuarios a los que desea asignar este perfil. Puede elegir asignar el perfil a todos los usuarios o a grupos específicos. Todos los usuarios de los grupos seleccionados usarán el tipo de inscripción elegido anteriormente. Los grupos de dispositivos no se admiten en escenarios de inscripción de usuarios porque la característica se basa en las identidades de usuario y no de dispositivos. Puede elegir asignar el perfil a todos los usuarios o a grupos específicos.

    ![Página de asignaciones](./media/ios-user-enrollment/assignments-page.png)

7. Seleccione **Siguiente**.

8. En la página de **revisión y creación**, revise las opciones seleccionadas y, a continuación, seleccione **Crear** para asignar el perfil a los usuarios.

    ![Página de asignaciones](./media/ios-user-enrollment/assignments-page.png)


## <a name="profile-priority"></a>Prioridad de perfil

Después de crear más de un perfil de tipo de inscripción, puede cambiar el orden de prioridad en el que se aplican.

1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Dispositivos** > **iOS** > **Inscripción de iOS** > **Tipos de inscripción (vista previa)** .
2. Arrastre y coloque los perfiles en la lista en el orden en el que desea que se apliquen.

En caso de que se produzcan conflictos entre los perfiles de cualquier usuario, se aplicará el perfil de mayor prioridad para el usuario.


