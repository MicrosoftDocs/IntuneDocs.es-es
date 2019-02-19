---
title: Configuración del acceso condicional basado en dispositivos con Intune
titlesuffix: Microsoft Intune
description: Obtenga información sobre cómo crear una directiva de acceso condicional basado en dispositivos teniendo en cuenta el cumplimiento de dispositivos de Microsoft Intune y la administración de aplicaciones móviles.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/11/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 03ca9a65d5a62c75c45541b42c9b2aa5c4871a18
ms.sourcegitcommit: e0374b3ced83c8876a4f78b326869c10588a55e5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56307794"
---
# <a name="create-a-device-based-conditional-access-policy"></a>Creación de una directiva de acceso condicional basado en dispositivos

Con Intune, puede mejorar el acceso condicional en Azure Active Directory mediante la incorporación del cumplimiento de dispositivos móviles a los controles de acceso. Una vez que ha creado una directiva de cumplimiento de Intune que define los requisitos de cumplimiento para los dispositivos, puede usar el estado de cumplimiento de un dispositivo para permitir o bloquear el acceso a sus aplicaciones y servicios. Puede hacerlo mediante la creación de una directiva de acceso condicional que usa la opción **Requerir que el dispositivo esté marcado como compatible**. 

Una directiva de acceso condicional especifica la aplicación o los servicios que desea proteger, las condiciones bajo las que se puede acceder a las aplicaciones o a los servicios y los usuarios a los que se aplica la directiva. El acceso condicional es una característica prémium de Azure AD que se puede configurar en Azure Active Directory, pero también puede configurar estas mismas directivas desde el portal de Intune. 

> [!IMPORTANT]
> Antes de configurar el acceso condicional, deberá configurar las directivas de cumplimiento de dispositivos de Intune para evaluar dispositivos en función de si cumplen requisitos específicos. Consulte [Introducción a las directivas de cumplimiento de dispositivos de Intune](device-compliance-get-started.md).

## <a name="create-conditional-access-policy"></a>Crear una directiva de acceso condicional

1.  En el portal de Intune, seleccione **Acceso condicional** > **Directivas** > **Nueva directiva**.
   
    ![Creación de una directiva de acceso condicional](media/create-conditional-access-intune/create-ca.png)
 
2.  En **Asignaciones**, seleccione **Usuarios y grupos**. 
3.  En la pestaña de **Include**, identifique los usuarios o grupos a los que desea aplicar esta directiva de acceso condicional. Una vez que haya elegido a quiénes se va a incluir, puede usar la pestaña **Excluir** si no hay ningún usuario, rol o grupo que desee excluir de esta directiva.  
    - **Todos los usuarios**: seleccione esta opción para aplicar la directiva a todos los usuarios y grupos, incluidos los usuarios internos e invitados.
  
    - **Seleccionar usuarios y grupos**: seleccione esta opción y especifique una o varias de las opciones siguientes:
  
      a. **Todos los usuarios invitados**: seleccione esta opción para incluir o excluir los usuarios invitados externos (por ejemplo, socios o colaboradores externos)
       
      b. **Roles del directorio**: seleccione uno o varios roles de Azure AD para incluir o excluir usuarios que están asignados a estos roles.
      
      c. **Usuarios y grupos**: seleccione esta opción para buscar y seleccionar usuarios individuales o grupos que desee incluir o excluir.
     
       > [!TIP]  
       > Pruebe la directiva en un grupo reducido de usuarios para asegurarse de que funciona según lo previsto.
4.  Seleccione **Listo**.
5.  En **Asignaciones**, seleccione **Aplicaciones en la nube**. 
6.  En la pestaña **Incluir**, identifique las aplicaciones y los servicios que desea proteger con esta directiva de acceso condicional. Después, puede usar la pestaña **Excluir** si hay aplicaciones o servicios que desea excluir de esta directiva.
    - **Todas las aplicaciones en la nube**: seleccione esta opción para aplicar la directiva a todas las aplicaciones.
      > [!IMPORTANT]  
      > La aplicación Administración de Microsoft Azure para el acceso a Azure Portal se incluye en esta lista. Asegúrese de usar la pestaña **Excluir** pestaña aquí o en las opciones **Usuarios y grupos** para asegurarse de que usted (o los usuarios o grupos que designa) podrá iniciar sesión en Azure Portal. 

    - **Seleccionar aplicaciones**: seleccione esta opción, elija **Seleccionar** y luego use la lista de aplicaciones para buscar y seleccionar las aplicaciones o los servicios que desea proteger.
    
      ![Creación de una directiva de acceso condicional](media/create-conditional-access-intune/create-ca-select-apps.png)

7.  Seleccione **Listo**.
8.  En **Asignaciones**, seleccione **Condiciones**.
    - **Riesgo de inicio de sesión**: elija Sí para usar la detección de riesgo de inicio de sesión de Azure AD Identity Protection con esta directiva y luego elija los niveles de riesgo de inicio de sesión a los que se debe aplicar la directiva.
    - **Plataformas de dispositivos**: en la pestaña **Incluir**, identifique las plataformas de dispositivos a las que desea aplicar esta directiva de acceso condicional. Use la pestaña **Excluir** para excluir plataformas de esta directiva.
    - **Ubicaciones**: en la pestaña **Incluir**, especifique si la directiva se aplica a cualquier ubicación, a ubicaciones de red de confianza que están bajo el control de su departamento de TI o a ubicaciones de red específicas. Use la pestaña **Excluir** para excluir ubicaciones de red de esta directiva. 
    - **Aplicaciones cliente**: elija **Sí** para especificar si la directiva se debe aplicar a aplicaciones de explorador, a aplicaciones móviles y a clientes de escritorio. También puede seleccionar **Clientes de autenticación moderna** (como Outlook para iOS o Outlook para Android) y **Clientes de Exchange ActiveSync**.
    - **Estado del dispositivo**: la directiva de acceso condicional se aplicará a todos los estados de dispositivo a menos que elija Sí y excluya específicamente los estados Unido a Azure AD híbrido de dispositivo o Dispositivo marcado como compatible (o ambos).
    
      ![Creación de una directiva de acceso condicional](media/create-conditional-access-intune/create-ca-device-platforms.png)

      > [!TIP]  
      > Si desea proteger tanto los clientes de **autenticación moderna** como los clientes de **Exchange ActiveSync**, cree dos directivas de acceso condicional independientes, una para cada tipo de cliente. Aunque Exchange ActiveSync admita autenticación moderna, la única condición que Exchange ActiveSync admite es la plataforma. Otras condiciones, incluida la autenticación multifactor, no se admiten. Para proteger eficazmente el acceso a Exchange Online desde Exchange ActiveSync, cree una directiva de acceso condicional que especifique la aplicación en la nube de Office 365 Exchange Online y la aplicación cliente Exchange ActiveSync con la directiva Aplicar solo a las plataformas admitidas seleccionadas.

9.  Seleccione **Listo**.
10. En **Controles de acceso**, seleccione **Conceder**. Configure lo que ocurre en función de las condiciones que ha definido.  Puede seleccionar entre las siguientes opciones:
    - **Bloquear acceso**: se denegará el acceso a los usuarios especificados en esta directiva a las aplicaciones bajo las condiciones que haya especificado.
    - **Conceder acceso**: se concederá acceso a los usuarios especificados en esta directiva, pero puede ser necesario realizar cualquiera de las siguientes acciones adicionales:
      - **Requerir autenticación multifactor**: el usuario deberá completar los requisitos de seguridad adicionales, como una llamada de teléfono o texto.
      - **Requerir que el dispositivo esté marcado como compatible**: el dispositivo debe ser compatibles con Intune. Si el dispositivo no es compatible, se dará al usuario la opción de inscribir el dispositivo en Intune. 
      - **Requerir dispositivo unido a Azure AD híbrido**: los dispositivos deben estar unidos a Azure AD híbrido.
      - **Requerir aplicación cliente aprobada**: el dispositivo debe usar estas aplicaciones cliente aprobadas. 
      - **Para varios controles**: seleccione **Requerir todos los controles seleccionados** para que se cumplan todos los requisitos anteriores cuando un dispositivo intente acceder a la aplicación.
    
      ![Configuración de la concesión de controles de acceso](media/create-conditional-access-intune/create-ca-grant-access-settings.png)
 
11. En **Habilitar directiva**, seleccione **Activar**.
     
     ![Habilitación de la directiva](media/create-conditional-access-intune/enable-policy.png)

12. Seleccione **Crear**.

## <a name="see-also"></a>Consulte también
[Acceso condicional basado en aplicación con Intune](app-based-conditional-access-intune.md)
