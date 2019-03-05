---
title: 'Uso de líneas de base de seguridad en Microsoft Intune: Azure | Microsoft Docs'
description: Agregue o defina configuraciones de seguridad de grupo recomendadas para proteger al usuario y los datos en dispositivos mediante Microsoft Intune para la administración de dispositivos móviles. Habilite bitlocker, configure Advanced Threat Protection para Windows Defender, controle Internet Explorer, use Smart Screen, establezca directivas de seguridad locales, requiera una contraseña, bloquee las descargas de Internet, etc.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/01/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 180a4cad27082105aa41c2bd79e6f9c05a65d162
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2019
ms.locfileid: "57238615"
---
# <a name="create-a-windows-10-security-baseline-in-intune"></a>Creación de una línea de base de seguridad de Windows 10 en Intune

Las líneas de base de seguridad son una característica en versión preliminar que está disponible para dispositivos con Windows 10 y versiones posteriores. Esta característica incluye numerosas configuraciones admitidas por Intune que puede usar para proteger a los usuarios y dispositivos. Automáticamente establece estas configuración en los valores que los equipos de seguridad recomiendan. Por ejemplo, la línea de base habilita automáticamente BitLocker, requiere automáticamente una contraseña para desbloquear un dispositivo, deshabilita automáticamente la autenticación básica, etc.

Esta característica se aplica a:

- Windows 10, versión 1809 y posteriores

> [!NOTE]
> Mientras las líneas de base de seguridad se encuentren en versión preliminar, Microsoft no recomienda el uso de perfiles en un entorno de producción, ya que dichas líneas pueden cambiar en el transcurso de la versión preliminar. Cuando las líneas de base de seguridad están disponibles con carácter general, los perfiles existentes no se convertirán a los perfiles compatibles más recientes.

El objetivo de usar las líneas de base de seguridad es proporcionar un flujo de trabajo seguro de un extremo a otro cuando trabaja con Microsoft 365. Estas son algunas de las ventajas:

- Una línea de base de seguridad incluye los procedimientos recomendados y las recomendaciones sobre la configuración que afectan a la seguridad. Intune se asocia con el mismo equipo de seguridad de Windows que crea las líneas de base de seguridad de directiva de grupo. Estas recomendaciones se basan en la orientación y en una amplia experiencia.
- Si es nuevo en Intune y no está seguro de por dónde empezar, las líneas de base de seguridad ofrecen una ventaja. Puede crear e implementar rápidamente un perfil seguro, sabiendo que ayuda a proteger los recursos y datos de su organización.
- Si actualmente usa una directiva de grupo, migrar a Intune para la administración es mucho más fácil con estas líneas de base. Estas líneas de base están integradas de forma nativa en Intune e incluyen una experiencia de administración moderna.

Las líneas de base de seguridad crean un "perfil de configuración" en Intune. Este perfil incluye todas las configuraciones en la línea de base. Después, puede aplicar o asignar este perfil a los usuarios, grupos y dispositivos.

Una vez asignado el perfil, puede supervisar dicho perfil y la línea de base. Por ejemplo, puede ver los dispositivos que coinciden con la línea de base y aquellos que no coinciden con dicha línea.

En este artículo se muestra cómo usar las líneas de base de seguridad para crear, asignar y supervisar un perfil.

Las [líneas de base de seguridad de Windows](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines) son un excelente recurso para obtener más información sobre esta característica. La [administración de dispositivos móviles](https://docs.microsoft.com/windows/client-management/mdm/) (MDM) es un magnífico recurso sobre MDM y lo que puede hacer en los dispositivos Windows.

## <a name="co-managed-devices"></a>Dispositivos administrados conjuntamente

Las líneas de base de seguridad en dispositivos administrados por Intune son similares a los dispositivos administrados conjuntamente con Configuration Manager. Los dispositivos administrados conjuntamente usan System Center Configuration Manager y Microsoft Intune para administrar los dispositivos Windows 10 al mismo tiempo. Le permite conectar a la nube su inversión existente de Configuration Manager a las ventajas de Intune. La [introducción a la administración conjunta](https://docs.microsoft.com/sccm/comanage/overview) es un excelente recurso si usa Configuration Manager y también quiere las ventajas de la nube.

Cuando se usen dispositivos administrados conjuntamente, debe cambiar la carga de trabajo de la **configuración del dispositivo** (su configuración) a Intune. [Las cargas de trabajo de configuración de dispositivo](https://docs.microsoft.com/sccm/comanage/workloads#device-configuration) proporcionan más información.

## <a name="create-the-profile"></a>Creación del perfil

1. En [Azure Portal](https://portal.azure.com/), seleccione **Todos los servicios**, filtre por **Intune** > seleccione **Intune**.
2. Seleccione **Líneas base de seguridad (vista previa)**. Hay una lista de líneas de base disponibles. Aquí podrá ver las líneas de base a medida que se agregan:

    ![Ver una lista de las líneas de base de seguridad actualmente disponibles en Intune](./media/security-baselines/available-baselines.png)

3. Seleccione la línea de base que le gustaría usar > **Crear perfil**.
4. En **Básico**, escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre para el perfil de las líneas de base de seguridad. Por ejemplo, escriba `pilot Windows 10 MDM baseline - Oct 2018`.
    - **Descripción**: escriba algún texto que describa lo que hace esta línea de base. La descripción es para que introduzca cualquier texto que desee. Es opcional, pero muy recomendable.

5. Expanda **Configuración**. En la lista, verá todas las configuraciones de esta línea de base de seguridad y en qué valor se establece automáticamente. La configuración y sus valores son recomendados y los puede cambiar usted mismo.

    ![Expandir las opciones de configuración para ver todas las configuraciones de esta línea de base de seguridad en Intune](./media/security-baselines/sample-list-of-settings.png)

    Expanda algunas de las configuraciones para comprobar sus valores. Por ejemplo, expanda **Windows Defender**. Observe algunas de las configuraciones y en que están establecidas:

    ![Vea en qué valores se definen automáticamente las opciones de Windows Defender en Intune](./media/security-baselines/expand-windows-defender.png)

6. **Cree** el perfil. 
7. Seleccione **Perfiles**. El perfil se crea y se muestra en la lista. Sin embargo, no hace nada todavía. Después, asigne el perfil.

## <a name="assign-the-profile"></a>Asignar el perfil

Una vez creado el perfil, está listo para asignarlo a los usuarios, dispositivos y grupos. Una vez asignado, el perfil y su configuración se aplican a los usuarios, dispositivos y grupos que elija.

1. En Intune, seleccione **Líneas base de seguridad** > elija una línea de base > **Perfiles**.
2. Seleccione su perfil > **Asignaciones**.

    ![Seleccionar el perfil de línea de base de seguridad en Intune y hacer clic en Asignaciones para implementar el perfil](./media/security-baselines/assignments.png)

3. En la pestaña **Incluir**, agregue los grupos, usuarios o dispositivos que desee que aplique esta directiva.

    > [!TIP]
    > Tenga en cuenta que también puede **excluir** grupos. Si se aplica una directiva a **Todos los usuarios**, considere la posibilidad de excluir los grupos de administrador. En caso de que ocurra algo, usted y los administradores no desean quedar bloqueados.

4. Guarde los cambios mediante **Guardar**.

Tan pronto como guarde los cambios, el perfil se insertará en los dispositivos cuando se registren en Intune. Por lo tanto, puede ocurrir inmediatamente.

## <a name="available-security-baselines"></a>Líneas de base de seguridad disponibles  

Las líneas de base de seguridad siguientes están disponibles para su uso con Intune.
- **Versión preliminar: línea de base de seguridad MDM**
  - Versión: [Octubre de 2018](security-baseline-settings-windows.md)

## <a name="q--a"></a>Q & A

#### <a name="why-these-settings"></a>¿Por qué esta configuración?

El grupo de seguridad de Microsoft acumula muchos años de experiencia trabajando directamente con los desarrolladores de Windows y la comunidad de seguridad para crear estas recomendaciones. Las configuraciones de esta línea de base se consideran las opciones de configuración relacionadas con la seguridad más pertinentes. En cada nueva compilación de Windows, el equipo ajusta sus recomendaciones basándose en las características lanzadas recientemente.

#### <a name="is-there-a-difference-in-the-recommendations-for-windows-security-baselines-for-group-policy-vs-intune"></a>¿Hay alguna diferencia en las recomendaciones para las líneas de base de seguridad de Windows para la directiva de grupo frente a Intune?

El mismo equipo de seguridad de Microsoft eligió y organizó la configuración para cada línea de base. Intune incluye todas las configuración pertinentes en la línea de base de seguridad de Intune. Hay algunas configuraciones en la línea de base de la directiva de grupo que son específicas de un controlador de dominio local. Estas opciones se excluyen de las recomendaciones de Intune. Todas las demás configuraciones son las mismas.

#### <a name="are-the-intune-security-baselines-cis-or-nsit-compliant"></a>¿Son compatibles las líneas de base de seguridad CIS o NSIT de Intune?

Estrictamente hablando, no. El equipo de seguridad de Microsoft consulta a las organizaciones, como CIS, para recopilar sus recomendaciones. Sin embargo, no hay una asignación unívoca entre las líneas de base de Microsoft y “compatibles con CIS”.

#### <a name="what-certifications-does-microsofts-security-baselines-have"></a>¿Qué certificaciones tienen las líneas de base de seguridad de Microsoft? 

- Microsoft continúa publicando líneas de base de seguridad para directivas de grupo (GPO) y el [Security Compliance Toolkit](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10), como ha hecho durante muchos años. Muchas organizaciones usan estas líneas de base. Las recomendaciones que figuran en estas líneas de base provienen del compromiso del equipo de seguridad de Microsoft con clientes empresariales y agencias externas, incluido el Departamento de Defensa (DoD), el Instituto Nacional de Estándares y Tecnología (NIST), etc. Compartimos nuestras recomendaciones y líneas de base con estas organizaciones. Estas organizaciones también tienen sus propias recomendaciones que reflejan fielmente las recomendaciones de Microsoft. Dado que la administración de dispositivos móviles (MDM) continúa creciendo en la nube, Microsoft ha creado recomendaciones de MDM equivalentes de estas líneas de base de directivas de grupo. Estas líneas de base adicionales están integradas en Microsoft Intune e incluyen informes de cumplimiento sobre usuarios, grupos y dispositivos que siguen (o no) la línea de base.

- Muchos clientes utilizan las recomendaciones de línea de base de Intune como punto de partida y luego las personalizan para satisfacer sus demandas de TI y seguridad. La **línea de base de seguridad de MDM** de Windows 10 RS5 de Microsoft es la primera línea de base para lanzar. Esta línea de base se construye como una infraestructura genérica que permite a los clientes eventualmente importar otras líneas de base de seguridad basadas en CIS, NIST y otros estándares. Actualmente, está disponible para Windows y eventualmente incluirá iOS y Android.

- La migración de las directivas de grupo de Active Directory locales a una solución en la nube pura mediante Azure Active Directory (AD) con Microsoft Intune es una odisea. Para ayudar en este proceso, hay GPO complementarios publicados para AD híbrido y dispositivos unidos a Azure AD. Estos dispositivos pueden obtener configuraciones de MDM desde la nube (Intune) y configuraciones de directiva de grupo desde los controladores de dominio locales según sea necesario.

## <a name="next-steps"></a>Pasos siguientes
- Vea la [configuración de línea de base de seguridad de Windows](security-baseline-settings-windows.md) compatible con Intune.  
- Compruebe el estado y supervise la [línea de base y el perfil](security-baselines-monitor.md).
