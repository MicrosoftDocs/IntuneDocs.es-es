---
title: "Migrar directivas de acceso condicional desde el Portal de Intune clásico al nuevo Azure Portal"
titleSuffix: Intune on Azure
description: "Migrar directivas de acceso condicional desde el Portal de Intune clásico al nuevo Azure Portal"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 301159ad-5f7e-4fcc-86c7-f72a71701ff4
ms.reviewer: chrisgree
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2450a878424d8c992a43e8028ba59b7136e1d530
ms.sourcegitcommit: fd5b7aa26446d2fa92c21638cb29371e43fe169f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2017
---
# <a name="reassign-conditional-access-policies-from-intune-classic-portal-to-the-new-azure-portal"></a>Reasignar directivas de acceso condicional desde el Portal de Intune clásico al nuevo Azure Portal

A partir del nuevo Azure Portal, el acceso condicional ofrece compatibilidad para varias directivas por aplicación junto con una mayor personalización.

## <a name="before-you-begin"></a>Antes de comenzar

Si está listo para moverse al nuevo Azure Portal, puede seguir los pasos siguientes para reasignar las directivas de acceso condicional que ha creado anteriormente en el Portal de Intune clásico:

- Recopile las directivas de acceso condicional que ha creado anteriormente en el Portal de Intune clásico de manera que conozca las opciones que necesita reasignar posteriormente.

- Siga los pasos de este tema para volver a crear estas directivas en el nuevo Azure Portal.

- Deshabilite las directivas condicionales en la consola clásica de Intune una vez que haya comprobado que las nuevas directivas están funcionando como se espera en el nuevo Azure Portal.
<br /><br />
    - **Antes de deshabilitar** las directivas de acceso condicional en el Portal de Intune clásico, planee cómo moverá los usuarios a la nueva directiva. Existen dos enfoques:
<br /><br />
        - **Usar el mismo grupo de inclusión para aplicar las directivas creadas en el nuevo Azure Portal, y crear un nuevo grupo de exención para usarse con las directivas que ha aplicado el Portal de Intune clásico**.
            - Mueva de manera gradual algunos usuarios al grupo de exención especificado en el portal clásico.  Esto evita que se apliquen las directivas a las que se dirige el Portal de Intune clásico. Las directivas que se han creado y que se dirigen al mismo grupo de usuarios en el nuevo Azure Portal se aplican además de las que se han aplicado en el Portal de Intune clásico. 
<br /><br />
        - **Crear un nuevo grupo que tenga como destino las directivas de acceso condicional en el nuevo Azure Portal**. Si elige este enfoque, necesita realizar lo siguiente:
            - Quite de manera gradual los usuarios de los grupos de seguridad que tienen como destino directivas de acceso condicional en el Portal de Intune clásico.
            - Una vez que haya confirmado que la nueva directiva está funcionando para esos usuarios, puede deshabilitarla en el Portal de Intune clásico. 
<br /><br />
- Si ha configurado las opciones de la directiva de acceso condicional para que usen Exchange Active Sync (EAS) en el Portal de Intune clásico, vea las [instrucciones de este tema](#to-reassign-intune-device-based-conditional-access-policies-for-eas-clients) para **volver a asignar las opciones de la directiva de acceso condicional de EAS en el nuevo Azure Portal**.

### <a name="to-verify-your-device-based-conditional-access-policies-in-the-intune-classic-portal"></a>Para comprobar las directivas de acceso condicional basadas en el dispositivo en el Portal de Intune clásico

1.  Vaya al [Portal de Intune clásico](https://manage.microsoft.com) e inicie sesión con sus credenciales.

2.  Pulse **Directiva** en el menú de la izquierda.

3.  Pulse **Acceso condicional**, después seleccione el servicio en la nube de Microsoft (Exchange Online, SharePoint Online, etc.) para el que ha creado una directiva de acceso condicional.

4.  Tome notas de las opciones de acceso condicional y use estas notas como referencia para crear las mismas directivas de acceso condicional en el nuevo Azure Portal.

### <a name="app-and-device-based-conditional-access-policies-working-together"></a>Las directivas de acceso condicional basadas en el dispositivo y la aplicación funcionan conjuntamente

La hoja **Protección de aplicaciones de Intune** en el nuevo Azure Portal permite a los administradores establecer reglas condicionales basadas en la aplicación, de manera que solo las aplicaciones que admiten las directivas de protección de aplicaciones de Intune puedan tener acceso a los recursos de la empresa. Puede elegir superponer estas directivas de acceso condicional basadas en la aplicación mediante directivas de acceso condicional basadas en el dispositivo. Dependiendo de si quiere combinar las directivas condicionales basadas en la aplicación y basadas en el dispositivo (AND lógico) o proporcionar una opción (OR lógico). Si los requisitos de la directiva de acceso condicional son:

- Requerir un dispositivo compatible **Y** usar la aplicación aprobada.
    - Debe establecer la directiva de acceso condicional mediante la [hoja de acceso condicional de Azure AD](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) y la [hoja de Protección de aplicaciones de Intune](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0).
<br /><br />
- Requerir un dispositivo compatible **O** usar la aplicación aprobada.
    - Debe establecer la directiva de acceso condicional mediante el [Portal de Intune clásico](https://manage.microsoft.com) y la [hoja de Protección de aplicaciones de Intune](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0).

> [!TIP] 
> En este tema se proporcionan capturas de pantalla que comparan la experiencia de usuario en el Portal de Intune clásico y en el nuevo Azure Portal.

## <a name="to-re-assign-intune-device-based-conditional-access-policies"></a>Para reasignar las directivas de acceso condicional basadas en el dispositivo de Intune

1. Vaya a [Acceso condicional en el nuevo Azure Portal](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) e inicie sesión con sus credenciales.

2. Pulse **Nueva directiva**.

3. Indique un nombre para la directiva.

4. Pulse **Usuarios y grupos** en la sección **Asignaciones** para dirigirse a la nueva directiva de acceso condicional.
    
    ![Comparación de la interfaz de usuario del grupo de usuarios entre Intune clásico y el nuevo Azure Portal](./media/reassign-ca-1.png)

    > [!IMPORTANT] 
    > Si ha seleccionado todos los usuarios en el Portal de Intune clásico, incluya Todos los usuarios. Lo mismo se aplica a los grupos. Si tiene grupos seleccionados, necesita pulsar **Seleccionar usuarios individuales y grupos** para incluir esos grupos. Además, si ha seleccionado la opción **Grupos exentos** en el Portal de Intune clásico, necesita excluir esos grupos seleccionados en el nuevo Azure Portal.

5. Después de que haya seleccionado el grupo, haga clic en **Seleccionar** y en **Listo**.

6. Pulse **Aplicaciones en la nube** en la sección **Asignaciones**.

7. En la hoja **Aplicaciones en la nube**, pulse **Seleccionar aplicaciones**.

8. Seleccione la aplicación a la que quiere aplicar la nueva directiva de acceso condicional y haga clic en **Seleccionar**.

9. Haga clic en **Listo**.

    ![Comparación de la interfaz de usuario de aplicaciones en la nube entre Intune clásico y el nuevo Azure Portal](./media/reassign-ca-3.png)

    > [!TIP] 
    > Si tiene varias aplicaciones con la misma directiva, puede considerar la posibilidad de consolidarlas en una única directiva en el nuevo Azure Portal.

10. Pulse **Condiciones** en la sección **Asignaciones**.

11. En la hoja **Condiciones**, pulse **Plataformas de dispositivo**, después seleccione las plataformas de dispositivo aplicables.

12. Una vez que haya terminado de seleccionar las plataformas de dispositivo, haga clic en **Listo** dos veces.

    ![Comparación de la interfaz de usuario de las plataformas de dispositivo entre Intune clásico y el nuevo Azure Portal](./media/reassign-ca-4.png)

    > [!TIP] 
    > Si ha seleccionado plataformas individuales en el Portal de Intune clásico, selecciónelas en el nuevo Azure Portal.

    > [!NOTE] 
    > Puede especificar opciones de cumplimiento o de unión al dominio para Windows posteriormente.

13. Pulse **Condiciones** en la sección **Asignaciones**.

14. En la hoja **Condiciones**, pulse **Aplicaciones cliente**, después seleccione la aplicación cliente aplicable.

15. Una vez que haya terminado de seleccionar la aplicación cliente, haga clic en **Listo** dos veces.

    ![Comparación de la interfaz de usuario de aplicaciones cliente entre Intune clásico y el nuevo Azure Portal](./media/reassign-ca-6.png)

16. Si ha seleccionado las opciones del explorador en el Portal de Intune clásico, seleccione **Explorador** y **Aplicaciones móviles y aplicaciones de escritorio** en el nuevo Azure Portal. En caso de que no haya elegido las opciones del explorador en el Portal de Intune clásico, pulse solo **Aplicaciones móviles y aplicaciones de escritorio**. 

17. Pulse **Conceder** en la sección **Controles de acceso**.

18. Pulse **Requerir que el dispositivo esté marcado como compatible** en **Grant Access Controls** (Conceder controles de acceso) y, después, haga clic en **Seleccionar**.

19. Si tiene una directiva que necesita dispositivos Windows unidos al dominio, y también permite dispositivos Windows compatibles e inscritos a Intune, pulse **Requerir dispositivo unido al dominio** y **Requerir que el dispositivo esté marcado como compatible** junto con **Requerir uno de los controles seleccionados**.

20. Si no permite dispositivos Windows compatibles e inscritos a Intune, excluya la directiva Windows de la directiva actual y, después, cree una directiva independiente con **Plataformas de dispositivo** establecido en **Windows**, incluidas las demás condiciones como se han establecido anteriormente, y pulse **Requerir dispositivo unido al dominio** en **Grant Access Controls** (Conceder controles de acceso).

21. Active la alternancia **Habilitar directiva** en la hoja de la directiva de acceso condicional **Nueva** y, después, haga clic en **Crear**.

    ![Habilitar la comparación de la interfaz de usuario de directivas entre Intune clásico y el nuevo Azure Portal](./media/reassign-ca-11.png)

## <a name="to-reassign-intune-device-based-conditional-access-policies-for-eas-clients"></a>Para reasignar las directivas de acceso condicional basadas en el dispositivo de Intune para clientes de EAS

Si ha configurado las opciones de Exchange Active Sync (EAS) como parte de una directiva de Exchange Online en el Portal de Intune clásico, necesita crear una segunda directiva de acceso condicional en el nuevo Azure Portal.

1. Vaya a [Acceso condicional en el nuevo Azure Portal](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) e inicie sesión con sus credenciales.

2. Pulse **Nueva directiva**.

3. Indique un nombre para la directiva.

4. Pulse **Usuarios y grupos** en la sección **Asignaciones** para dirigirse a la nueva directiva de acceso condicional.

    ![Comparación de la interfaz de usuario del grupo de usuarios entre Intune clásico y el nuevo Azure Portal](./media/reassign-ca-12.png)

    > [!IMPORTANT] 
    > Si ha seleccionado todos los usuarios en el Portal de Intune clásico, incluya Todos los usuarios. Lo mismo se aplica a los grupos. Si tiene grupos seleccionados, necesita pulsar **Seleccionar usuarios individuales y grupos** para incluir esos grupos. Además, si ha seleccionado la opción **Grupos exentos** en el Portal de Intune clásico, necesita excluir esos grupos seleccionados en el nuevo Azure Portal.

5. Después de que haya seleccionado el grupo, haga clic en **Seleccionar** y en **Listo**.

6. Pulse **Aplicaciones en la nube** en la sección **Asignaciones**.

7. En la hoja **Aplicaciones en la nube**, haga clic en **Aplicaciones seleccionadas**, pulse **Exchange Online**, haga clic en **Seleccionar** y, después, en **Listo**.

    ![Comparación de la interfaz de usuario de aplicaciones en la nube entre Intune clásico y el nuevo Azure Portal](./media/reassign-ca-14.png)

    > [!IMPORTANT] 
    > Las directivas de acceso condicional de clientes de EAS no pueden incluir ninguna otra aplicación en la nube.

8. En la hoja **Condiciones**, pulse **Aplicaciones cliente**, después seleccione la aplicación cliente aplicable. Si ha decidido bloquear clientes que no admite Intune, use la opción **Aplicar directiva solo en las plataformas compatibles**.

    ![Comparación de la interfaz de usuario de aplicaciones cliente entre Intune clásico y el nuevo Azure Portal](./media/reassign-ca-15.png)

9. Una vez que haya terminado de seleccionar la aplicación cliente, haga clic en **Listo** dos veces.

10. Pulse **Conceder** en la sección **Controles de acceso**.

11. Pulse **Requerir que el dispositivo esté marcado como compatible** en **Grant Access Controls** (Conceder controles de acceso) y, después, haga clic en **Seleccionar**.

    ![Comparación de la interfaz de usuario de concesión de acceso entre Intune clásico y el nuevo Azure Portal](./media/reassign-ca-16.png)

12. Active la alternancia **Habilitar directiva** en la hoja de la directiva de acceso condicional **Nueva** y, después, haga clic en **Crear**.

    ![Habilitar la comparación de la interfaz de usuario de directivas entre Intune clásico y el nuevo Azure Portal](./media/reassign-ca-17.png)

## <a name="disable-conditional-access-policies-in-the-intune-classic-portal"></a>Deshabilitar directivas de acceso condicional en el Portal de Intune clásico
### <a name="before-you-start"></a>Antes de empezar

Una vez que haya reasignado las directivas de acceso condicional en el nuevo Azure Portal, es importante deshabilitar de manera gradual las directivas de acceso condicional que se han creado anteriormente en el Portal de Intune clásico. Además, puede que necesite usar el mismo grupo de seguridad para aplicar las directivas de acceso condicional que se han creado en el nuevo Azure Portal.

- Vea la sección [Antes de empezar](#before-you-begin) al principio de este tema antes de deshabilitar sus directivas de acceso condicional en el Portal de Intune clásico.

### <a name="to-disable-the-conditional-access-policies"></a>Para deshabilitar las directivas de acceso condicional

1.  Vaya al [Portal de Intune clásico](https://manage.microsoft.com) e inicie sesión con sus credenciales.

2.  Pulse **Directiva** en el menú de la izquierda.

3.  Pulse **Acceso condicional**, después seleccione el servicio en la nube de Microsoft (Exchange Online, SharePoint Online, etc.) para el que ha creado una directiva de acceso condicional.

4.  Desactive la opción **Habilitar directiva de acceso condicional** y, después, haga clic en **Guardar**.

    ![Deshabilitar directivas de acceso condicional desde el Portal de Intune clásico](./media/reassign-ca-18.png)

## <a name="see-also"></a>Consulte también

- [Formas habituales de usar el acceso condicional con Intune](conditional-access-intune-common-ways-use.md)
- [Acceso condicional basado en aplicación con Intune](app-based-conditional-access-intune.md)
- [Acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)