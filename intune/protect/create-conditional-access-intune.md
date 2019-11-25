---
title: Configuración del acceso condicional basado en dispositivos con Intune
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo crear una directiva de acceso condicional basado en dispositivos teniendo en cuenta el cumplimiento de dispositivos de Microsoft Intune y la administración de aplicaciones móviles.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fde15da898a70e9557aabb9ed7a7ae8324cfb304
ms.sourcegitcommit: 13fa1a4a478cb0e03c7f751958bc17d9dc70010d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188343"
---
# <a name="create-a-device-based-conditional-access-policy"></a>Creación de una directiva de acceso condicional basado en dispositivos

Con Intune, mejore el acceso condicional en Azure Active Directory mediante la incorporación del cumplimiento de dispositivos móviles a los controles de acceso. Con la directiva de cumplimiento de Intune que define los requisitos de cumplimiento para los dispositivos, puede usar el estado de cumplimiento de un dispositivo para permitir o bloquear el acceso a sus aplicaciones y servicios. Puede hacerlo mediante la creación de una directiva de acceso condicional que usa la opción **Requerir que el dispositivo esté marcado como compatible**.

Una directiva de acceso condicional especifica la aplicación o los servicios que desea proteger, las condiciones bajo las que se puede acceder a las aplicaciones o a los servicios y los usuarios a los que se aplica la directiva. Aunque el acceso condicional es una característica de Azure AD Premium, el nodo de acceso condicional al que se tiene acceso desde *Intune* es el mismo nodo al que se accede desde *Azure AD*.

> [!IMPORTANT]
> Antes de configurar el acceso condicional, deberá configurar las directivas de cumplimiento de dispositivos de Intune para evaluar dispositivos en función de si cumplen requisitos específicos. Consulte [Introducción a las directivas de cumplimiento de dispositivos de Intune](device-compliance-get-started.md).

## <a name="create-conditional-access-policy"></a>Creación de una directiva de acceso condicional

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Seleccione **Dispositivos** > **Acceso condicional** > **Directivas** > **Nueva directiva**.
  ![Creación de una directiva de acceso condicional](./media/create-conditional-access-intune/create-ca.png)

3. En **Asignaciones**, seleccione **Usuarios y grupos**.

4. En la pestaña **Incluir**, identifique los usuarios o grupos a los que se aplica esta directiva de acceso condicional. Una vez que haya elegido los grupos o usuarios a quien se va a incluir, use la pestaña **Excluir** si hay algún usuario, rol o grupo que desee excluir de esta directiva.

   - **Todos los usuarios**: seleccione esta opción para aplicar la directiva a todos los usuarios y grupos, incluidos los usuarios internos e invitados.

   - **Seleccionar usuarios y grupos**: seleccione esta opción y especifique una o varias de las opciones siguientes:
  
     1. **Todos los usuarios invitados**: seleccione esta opción para incluir o excluir los usuarios invitados externos (por ejemplo, socios o colaboradores externos)

     2. **Roles del directorio**: seleccione uno o varios roles de Azure AD para incluir o excluir usuarios que están asignados a estos roles.

     3. **Usuarios y grupos**: seleccione esta opción para buscar y seleccionar usuarios individuales o grupos que desee incluir o excluir.

        > [!TIP]
        > Pruebe la directiva en un grupo reducido de usuarios para asegurarse de que funciona según lo previsto.

5. Seleccione **Listo**.

6. En **Asignaciones**, seleccione **Acciones o aplicaciones en la nube**.

7. En la pestaña **Incluir**, use las opciones disponibles para identificar las aplicaciones y los servicios que desea proteger con esta directiva de acceso condicional. Después, puede usar la pestaña **Excluir** si hay aplicaciones o servicios que desea excluir de esta directiva.

   - **Todas las aplicaciones en la nube**: seleccione esta opción para aplicar la directiva a todas las aplicaciones.
     > [!IMPORTANT]
     > La aplicación Administración de Microsoft Azure para el acceso a Azure Portal se incluye en esta lista. Asegúrese de usar la pestaña **Excluir** pestaña aquí o en las opciones **Usuarios y grupos** para asegurarse de que usted (o los usuarios o grupos que designa) podrá iniciar sesión en Azure Portal. 

   - **Seleccionar aplicaciones**: seleccione esta opción, elija **Seleccionar** y luego use la lista de aplicaciones para buscar y seleccionar las aplicaciones o los servicios que desea proteger.

   Cuando esté listo, seleccione **Listo**.

8. En **Asignaciones**, seleccione **Condiciones**.

   - **Riesgo de inicio de sesión**: seleccione *Sí* para usar la detección de riesgo de inicio de sesión de Azure AD Identity Protection con esta directiva y luego elija los niveles de riesgo de inicio de sesión a los que se debe aplicar la directiva.

   - **Plataformas de dispositivos**: en la pestaña **Incluir**, identifique las plataformas de dispositivos a las que desea aplicar esta directiva de acceso condicional. Use la pestaña **Excluir** para excluir plataformas de esta directiva.

   - **Ubicaciones**: En la pestaña **Incluir**, especifique si la directiva se aplica a:
     - Cualquier ubicación
     - Ubicaciones de red de confianza que están bajo el control de su departamento de TI
     - Ubicaciones de red específicas

     Use la pestaña **Excluir** para excluir ubicaciones de red de esta directiva.

   - **Aplicaciones cliente**: seleccione *Sí* para especificar si la directiva se debe aplicar a aplicaciones de explorador, a aplicaciones móviles y a clientes de escritorio.

   - **Estado del dispositivo**: la directiva de acceso condicional se aplicará a todos los estados de dispositivo a menos que elija Sí y excluya específicamente los estados Unido a Azure AD híbrido de dispositivo o Dispositivo marcado como compatible (o ambos).

     > [!TIP]
     > Si desea proteger tanto los clientes de **autenticación moderna** como los **clientes de Exchange ActiveSync**, cree dos directivas de acceso condicional independientes, una para cada tipo de cliente. Aunque Exchange ActiveSync admita autenticación moderna, la única condición que Exchange ActiveSync admite es la plataforma. Otras condiciones, incluida la autenticación multifactor, no se admiten. Para proteger eficazmente el acceso a Exchange Online desde Exchange ActiveSync, cree una directiva de acceso condicional que especifique la aplicación en la nube de Office 365 Exchange Online y la aplicación cliente Exchange ActiveSync con la directiva Aplicar solo a las plataformas admitidas seleccionadas.

9. Seleccione **Listo**.

10. En **Controles de acceso**, seleccione **Conceder**. Configure lo que ocurre en función de las condiciones que ha definido.  Puede seleccionar entre las siguientes opciones:

    - **Bloquear acceso**: se denegará el acceso a los usuarios especificados en esta directiva a las aplicaciones bajo las condiciones que haya especificado.
    - **Conceder acceso**: se concederá acceso a los usuarios especificados en esta directiva, pero puede ser necesario realizar cualquiera de las siguientes acciones adicionales:
      - **Requerir autenticación multifactor**: el usuario deberá completar los requisitos de seguridad adicionales, como una llamada de teléfono o texto.
      - **Requerir que el dispositivo esté marcado como compatible**: el dispositivo debe ser compatibles con Intune. Si el dispositivo no es compatible, se dará al usuario la opción de inscribir el dispositivo en Intune.
      - **Requerir dispositivo unido a Azure AD híbrido**: los dispositivos deben estar unidos a Azure AD híbrido.
      - **Requerir aplicación cliente aprobada**: el dispositivo debe usar estas aplicaciones cliente aprobadas. 
      - **Para varios controles**: seleccione **Requerir todos los controles seleccionados** para que se cumplan todos los requisitos cuando un dispositivo intente acceder a la aplicación.

      ![Configuración de la concesión de controles de acceso](./media/create-conditional-access-intune/create-ca-grant-access-settings.png)

11. En **Habilitar directiva**, seleccione **Activar**.

12. Seleccione **Crear**.

## <a name="next-steps"></a>Pasos siguientes

[Acceso condicional basado en aplicación con Intune](app-based-conditional-access-intune.md)

[Solución de problemas de acceso condicional de Intune](https://support.microsoft.com/help/4456106)
