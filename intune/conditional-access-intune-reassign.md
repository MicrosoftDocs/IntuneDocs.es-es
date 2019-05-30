---
title: Migración del acceso condicional a Azure Portal
titleSuffix: Microsoft Intune
description: Reasigne las directivas de acceso condicional que se han creado anteriormente en el Portal de Intune clásico a Azure Portal.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 301159ad-5f7e-4fcc-86c7-f72a71701ff4
ms.reviewer: chrisgree
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a197b057278ff2f32539169feccc91edbd752386
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66048972"
---
# <a name="reassign-conditional-access-policies-from-intune-classic-portal-to-the-azure-portal"></a>Reasignar directivas de acceso condicional desde el Portal de Intune clásico a Azure Portal

A partir del nuevo Azure Portal, el acceso condicional ofrece compatibilidad para varias directivas por aplicación junto con una mayor personalización. Si previamente ha creado directivas de acceso condicional en el Portal de Intune clásico, se pueden migrar a Azure Portal. 

## <a name="before-you-begin"></a>Antes de comenzar

Si está listo para moverse a Azure Portal, siga los pasos de este tema para reasignar las directivas de acceso condicional que ha creado anteriormente en el Portal de Intune clásico:

- Recopile las directivas de acceso condicional que ha creado anteriormente, de manera que conozca las opciones que necesita reasignar posteriormente.

- Siga los pasos de este tema para volver a crear estas directivas en Azure Portal.

- Deshabilite las directivas condicionales en el portal clásico de Intune después de que haya comprobado que las nuevas directivas están funcionando como se espera en Azure Portal.
<br /><br />
    - **Antes de deshabilitar** las directivas de acceso condicional en el Portal de Intune clásico, planee cómo moverá los usuarios a la nueva directiva. Existen dos enfoques:
<br /><br />
        - **Usar el mismo grupo de inclusión para aplicar las directivas creadas en Azure Portal, y crear un nuevo grupo de exención para usarse con las directivas que ha aplicado el Portal de Intune clásico**.
            - Mueva de manera gradual algunos usuarios al grupo de exención especificado en el portal clásico. Esto evita que se apliquen las directivas a las que se dirige el Portal de Intune clásico. Las directivas que se han creado y que se dirigen al mismo grupo de usuarios en Azure Portal se aplican además de las que se han aplicado en el Portal de Intune clásico. 
<br /><br />
        - **Crear un nuevo grupo que tenga como destino las directivas de acceso condicional en Azure Portal**. Si elige este enfoque, necesita realizar lo siguiente:
            - Quite de manera gradual los usuarios de los grupos de seguridad que tienen como destino directivas de acceso condicional en el Portal de Intune clásico.
            - Después de que haya confirmado que la nueva directiva está funcionando para esos usuarios, puede deshabilitarla en el Portal de Intune clásico. 
<br /><br />
- Si ha configurado las opciones de la directiva de acceso condicional para que usen Exchange Active Sync (EAS) en el Portal de Intune clásico, vea las [instrucciones de este tema](#reassign-intune-device-based-conditional-access-policies-for-eas-clients) para **volver a asignar las opciones de la directiva de acceso condicional de EAS en Azure Portal**.

### <a name="to-verify-your-device-based-conditional-access-policies-in-the-intune-classic-portal"></a>Para comprobar las directivas de acceso condicional basadas en el dispositivo en el Portal de Intune clásico

1.  Vaya al [Portal de Intune clásico](https://manage.microsoft.com) e inicie sesión con sus credenciales.

2.  Pulse **Directiva** en el menú de la izquierda.

3.  Pulse **Acceso condicional** y, después, seleccione el servicio en la nube de Microsoft (por ejemplo, Exchange Online o SharePoint Online) para el que ha creado una directiva de acceso condicional.

4.  Tome nota de las opciones de acceso condicional y consúltelas cuando cree las mismas directivas de acceso condicional en Azure Portal.

### <a name="app-and-device-based-conditional-access-policies-working-together"></a>Las directivas de acceso condicional basadas en el dispositivo y la aplicación funcionan conjuntamente

La hoja **Protección de aplicaciones de Intune** en Azure Portal permite a los administradores establecer reglas condicionales basadas en la aplicación, de manera que solo las aplicaciones que admiten las directivas de protección de aplicaciones de Intune puedan tener acceso a los recursos de la empresa. Puede elegir superponer estas directivas de acceso condicional basadas en la aplicación mediante directivas de acceso condicional basadas en el dispositivo. Puede combinar las directivas condicionales basadas en la aplicación y basadas en el dispositivo (AND lógico) o puede proporcionar cualquier opción (OR lógico). Si los requisitos de la directiva de acceso condicional son para:

- Requerir un dispositivo compatible **Y** usar la aplicación aprobada.
    - Debe establecer la directiva de acceso condicional mediante la [hoja de acceso condicional de Azure Active Directory](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) y la [hoja de protección de aplicaciones de Intune](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0).
<br /><br />
- Requerir un dispositivo compatible **O** usar la aplicación aprobada.
    - Debe establecer la directiva de acceso condicional mediante el [Portal de Intune clásico](https://manage.microsoft.com) y la [hoja de protección de aplicaciones de Intune](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0).

> [!TIP] 
> En este tema se proporcionan capturas de pantalla que comparan la experiencia de usuario en el Portal de Intune clásico y en Azure Portal.

## <a name="reassign-intune-device-based-conditional-access-policies"></a>Reasignar las directivas de acceso condicional basadas en el dispositivo de Intune

1. Vaya a [Acceso condicional en Azure Portal](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) e inicie sesión con sus credenciales.

2. Pulse **Nueva directiva**.

3. Indique un nombre para la directiva.

4. En la **sección Asignaciones**, pulse **Usuarios y grupos** para dirigirse a la nueva directiva de acceso condicional.
    
    ![Imagen que compara la interfaz de usuario de grupos de usuarios entre Intune y Azure Portal](./media/reassign-ca-1.png)

    > [!IMPORTANT] 
    > La selección que hace para Azure Portal debe corresponder a la selección que ha realizado para el portal clásico. Por ejemplo, si ha seleccionado todos los usuarios en el Portal de Intune clásico, seleccione **Todos los usuarios** en Azure Portal. Además, si ha seleccionado la opción **Grupos exentos** en el Portal de Intune clásico, excluya también esos grupos seleccionados en Azure Portal.

5. Después de que haya seleccionado el grupo, haga clic en **Seleccionar** y, después, en **Listo**.

6. En la sección **Asignaciones**, pulse **Aplicaciones en la nube**.

7. En la hoja **Aplicaciones en la nube**, pulse **Seleccionar aplicaciones**.

8. Seleccione la aplicación a la que quiere aplicar la nueva directiva de acceso condicional y haga clic en **Seleccionar**.

9. Haga clic en **Listo**.

    ![Imagen de una comparación de la interfaz de usuario de aplicaciones en la nube entre los portales de Intune y Azure](./media/reassign-ca-3.png)

    > [!TIP] 
    > Si tiene varias aplicaciones con la misma directiva, considere la posibilidad de consolidarlas en una única directiva en Azure Portal.

10. En la sección **Asignaciones**, pulse **Condiciones**.

11. En la hoja **Condiciones**, pulse **Plataformas de dispositivo** y, después, seleccione las plataformas de dispositivo aplicables.

12. Cuando haya terminado de seleccionar las plataformas de dispositivo, haga clic en **Listo** dos veces.

    ![Imagen que compara la interfaz de usuario de la plataforma de dispositivo de los portales de Intune y Azure](./media/reassign-ca-4.png)

    > [!TIP] 
    > Si ha seleccionado plataformas individuales en el Portal de Intune clásico, selecciónelas en Azure Portal.

    > [!NOTE] 
    > Puede especificar opciones de cumplimiento o de unión al dominio para Windows posteriormente.

13. En la sección **Asignaciones**, pulse **Condiciones**.

14. En la hoja **Condiciones**, pulse **Aplicaciones cliente** y, después, seleccione la aplicación cliente aplicable.

15. Cuando haya terminado de seleccionar la aplicación cliente, haga clic en **Listo** dos veces.

    ![Imagen que compara la interfaz de usuario de aplicaciones cliente entre los portales de Intune y Azure](./media/reassign-ca-6.png)

16. Si ha seleccionado las opciones del explorador en el Portal de Intune clásico, seleccione **Explorador** y **Aplicaciones móviles y aplicaciones de escritorio** en Azure Portal. En caso de que no haya elegido las opciones del explorador en el Portal de Intune clásico, pulse solo **Aplicaciones móviles y aplicaciones de escritorio**. 

17. En la sección **Controles de acceso**, pulse **Conceder**.

18. En **Grant Access Controls** (Conceder controles de acceso), pulse **Requerir que el dispositivo esté marcado como compatible** y, después, haga clic en **Seleccionar**.

19. Si tiene una directiva que necesita dispositivos Windows unidos al dominio, y también permite dispositivos Windows compatibles e inscritos a Intune, pulse **Requerir dispositivo unido al dominio** y **Requerir que el dispositivo esté marcado como compatible** junto con **Requerir uno de los controles seleccionados**.

20. Si no permite dispositivos Windows compatibles e inscritos a Intune, excluya la directiva Windows de la directiva actual. Después, cree una directiva independiente con **Plataformas de dispositivo** establecido en **Windows**, incluidas las demás condiciones como se han establecido anteriormente, y pulse **Requerir dispositivo unido al dominio** en **Grant Access Controls** (Conceder controles de acceso).

21. Active la alternancia **Habilitar directiva** en la hoja de la directiva de acceso condicional **Nueva** y, después, haga clic en **Crear**.

    ![Comparar la interfaz de usuario para habilitar directivas de acceso condicional entre Intune y Azure Portal](./media/reassign-ca-11.png)

## <a name="reassign-intune-device-based-conditional-access-policies-for-eas-clients"></a>Reasignar las directivas de acceso condicional basadas en el dispositivo de Intune para clientes de EAS

Si ha configurado las opciones de Exchange Active Sync como parte de una directiva de Exchange Online en el Portal de Intune clásico, necesita crear una segunda directiva de acceso condicional en Azure Portal.

1. Vaya a [Acceso condicional en Azure Portal](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) e inicie sesión con sus credenciales.

2. Pulse **Nueva directiva**.

3. Indique un nombre para la directiva.

4. En la sección **Asignaciones**, pulse **Usuarios y grupos** para dirigirse a la nueva directiva de acceso condicional.

    ![Imagen en la que se muestra una comparación de la interfaz de usuario de grupos de usuarios entre el Portal de Intune y Azure Portal](./media/reassign-ca-12.png)

    > [!IMPORTANT] 
    > La selección que hace para Azure Portal debe corresponder a la selección que ha realizado para Azure Portal. Por ejemplo, si ha seleccionado todos los usuarios en el Portal de Intune clásico, seleccione **Todos los usuarios** en Azure Portal. Además, si ha seleccionado la opción **Grupos exentos** en el Portal de Intune clásico, excluya también esos grupos seleccionados en Azure Portal.

5. Después de que haya seleccionado el grupo, haga clic en **Seleccionar** y, después, en **Listo**.

6. En la sección **Asignaciones**, pulse **Aplicaciones en la nube**.

7. En la hoja **Aplicaciones en la nube**, haga clic en **Seleccionar aplicaciones** y pulse **Exchange Online**. Después, haga clic en **Seleccionar** y **Listo**.

    ![Imagen de una comparación de la interfaz de usuario de aplicaciones en la nube entre los portales de Intune y Azure](./media/reassign-ca-14.png)

    > [!IMPORTANT] 
    > Las directivas de acceso condicional de clientes de EAS no pueden incluir ninguna otra aplicación en la nube.

8. En la hoja **Condiciones**, pulse **Aplicaciones cliente** y, después, seleccione la aplicación cliente aplicable. Si ha decidido bloquear clientes que no admite Intune, use la opción **Aplicar directiva solo en las plataformas compatibles**.

    ![Imagen en la que se muestra una comparación de la interfaz de usuario de aplicaciones cliente entre el Portal de Intune y Azure Portal](./media/reassign-ca-15.png)

9. Cuando haya terminado de seleccionar la aplicación cliente, haga clic en **Listo** dos veces.

10. En la sección **Controles de acceso**, pulse **Conceder**.

11. En **Grant Access Controls** (Conceder controles de acceso), pulse **Requerir que el dispositivo esté marcado como compatible** y, después, haga clic en **Seleccionar**.

    ![Imagen que compara la interfaz de usuario para conceder acceso entre los portales de Intune y Azure](./media/reassign-ca-16.png)

12. Active la alternancia **Habilitar directiva** en la hoja de la directiva de acceso condicional **Nueva** y, después, haga clic en **Crear**.

    ![Comparación de la interfaz de usuario para habilitar directivas de acceso condicional entre Intune y Azure](./media/reassign-ca-17.png)

> [!NOTE]
> Si configura **Plataformas de dispositivos**, al guardar la directiva se producirá el error “No se admite la configuración de la directiva”. Exchange ActiveSync no puede identificar la plataforma que usa el dispositivo que se está conectando. Por lo tanto, no se admite la configuración de plataformas de dispositivos específicas al crear una directiva para dispositivos de Exchange ActiveSync.

## <a name="disable-conditional-access-policies-in-the-intune-classic-portal"></a>Deshabilitar directivas de acceso condicional en el Portal de Intune clásico

Después de que haya reasignado las directivas de acceso condicional en Azure Portal, es importante deshabilitar de manera gradual las directivas de acceso condicional que se han creado anteriormente en el Portal de Intune clásico. Además, puede que necesite usar el mismo grupo de seguridad para aplicar las directivas de acceso condicional que se han creado en Azure Portal.

> [!NOTE]
> Vea la sección [Antes de empezar](#before-you-begin) al principio de este tema antes de deshabilitar sus directivas de acceso condicional en el Portal de Intune clásico.

### <a name="to-disable-the-conditional-access-policies"></a>Para deshabilitar las directivas de acceso condicional

1.  Vaya al [Portal de Intune clásico](https://manage.microsoft.com) e inicie sesión con sus credenciales.

2.  Pulse **Directiva** en el menú de la izquierda.

3.  Pulse **Acceso condicional** y, después, seleccione el servicio en la nube de Microsoft (por ejemplo, Exchange Online o SharePoint Online) para el que ha creado una directiva de acceso condicional.

4.  Desactive la opción **Habilitar directiva de acceso condicional** y, después, haga clic en **Guardar**.

    ![Imagen de Deshabilitar directivas de acceso condicional en el Portal de Intune clásico](./media/reassign-ca-18.png)

## <a name="see-also"></a>Consulte también

- [Formas habituales de usar el acceso condicional con Intune](conditional-access-intune-common-ways-use.md)
- [acceso condicional basado en aplicación con Intune](app-based-conditional-access-intune.md)
- [Acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
