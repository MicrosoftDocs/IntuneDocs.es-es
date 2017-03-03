---
title: Migrar a Intune | Microsoft Docs
description: "La migración a Intune desde su solución de administración de movilidad empresarial actual podría seguir la secuencia de pasos siguiente."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 88936b8a-7453-4410-b6db-29f636ba3e72
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 6b99854e17e00a0dd0f91fa82fd1b79d1dfe5663
ms.openlocfilehash: 43ac18d298901f24c8d6352537b285bf0108f667


---

# <a name="migrate-to-intune"></a>Migrar a Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

La migración a Intune desde su solución de administración de movilidad empresarial actual podría seguir la secuencia de pasos siguiente:

![Pasos de migración para Intune](./media/migrate-intune-steps.png)

## <a name="notify-users"></a>Notificar el cambio a los usuarios

Cuando esté convencido de que la implementación piloto de Intune cumple sus expectativas, comuníqueles a los usuarios la futura migración de sus dispositivos a Intune. Con mensajes de correo electrónico, instrucciones y [pósteres](https://gallery.technet.microsoft.com/Intune-End-User-Enrollment-3a0c9b0c?WT.mc_id=Blog_Intune_General_PCIT) puede establecer las expectativas y proporcionar detalles sobre los pasos de inscripción que los usuarios deberán seguir para no interrumpir la conectividad a las aplicaciones y los recursos de empresa. Asegúrese de que el equipo de soporte está preparado para ayudar a los usuarios en el proceso de migración.

## <a name="modify-your-existing-enterprise-mobility-management-solution"></a>Modificar la solución de administración de movilidad empresarial existente

En función de cómo planee gestionar las directivas de acceso condicional entre su solución de administración de movilidad empresarial existente e Intune, deberá deshabilitar las directivas de acceso condicional que tenga en vigor. Tiene dos opciones: deshabilitar las directivas de acceso condicional existentes, o bien definir su ámbito para que no incluyan a los usuarios y dispositivos que va a migrar a Intune.  Evite que Intune y su solución de administración de movilidad de empresa existente apliquen las directivas de acceso condicional a los mismos usuarios o dispositivos.

## <a name="enable-intune-conditional-access-policy-optional"></a>Habilitar la directiva de acceso condicional de Intune (opcional)

Si ha decidido aplicar inmediatamente las directivas de acceso condicional sin un período de gracia para la migración de dispositivos, habilite las directivas de acceso condicional de Intune en este paso.  Asegúrese de que esta decisión se ha comunicado a los usuarios y a su equipo de soporte técnico.  Si los dispositivos no están inscritos en Intune y no son compatibles con las directivas de Intune, los usuarios no podrán tener acceso a los recursos corporativos hasta que no se inscriban en Intune y los dispositivos sean compatibles con las directivas de Intune.

## <a name="unenrolling-devices-from-your-existing-enterprise-mobility-management-solution"></a>Cancelar la inscripción de los dispositivos de la solución de administración de movilidad empresarial actual

Antes de su inscripción en Intune, los dispositivos deben darse de baja de su solución de administración de movilidad empresarial existente. Nuestra recomendación es que permita que los usuarios cancelen ellos mismos la inscripción de sus dispositivos.  Siga las pautas de cancelación de inscripción facilitadas por el proveedor de soluciones para asegurarse de que los usuarios y dispositivos se quitan correctamente de la plataforma y para garantizar que el tiempo de interrupción del servicio sea mínimo.

## <a name="enrolling-devices-in-intune"></a>Inscribir dispositivos en Intune

Los usuarios que vayan a migrar deberán inscribirse de inmediato en Intune para recuperar o no perder el acceso a los recursos, el correo electrónico y las aplicaciones de la empresa. Si ha configurado el acceso condicional y los usuarios intentan conectarse al correo electrónico antes de inscribirse en Intune, el acceso se bloquea y se les da la bienvenida con un correo electrónico con instrucciones de inscripción. Este correo electrónico les sirve de guía para inscribir su dispositivo en Intune.  Los usuarios también tienen la opción de inscribirse en Intune a través de la aplicación de Portal de empresa de Intune o de forma nativa a través del sistema operativo en Windows 8.1 y Windows 10 Mobile. Vea [Qué decirles a los usuarios finales sobre el uso de Microsoft Intune](/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune) para obtener más instrucciones de inscripción por plataforma.

## <a name="configure-intune-conditional-access-optional"></a>Configurar el acceso condicional de Intune (opcional)

Si ha permitido un período de gracia para la aplicación del acceso condicional, habilite las directivas de acceso condicional de Intune para iniciar la aplicación cuando haya finalizado el período de gracia que ha comunicado a los usuarios finales. Esto requerirá inmediatamente que todos los dispositivos cumplan los requisitos de la directiva de acceso condicional de Intune.

## <a name="enroll-remaining-devices-and-users"></a>Inscribir el resto de los usuarios y dispositivos

Una vez habilitado el acceso condicional, todos los usuarios deben inscribirse en Intune y cumplir las directivas de cumplimiento de su organización para tener acceso a los recursos corporativos. Si ha migrado los usuarios en una inscripción por fases (es decir, no todos a la vez), repita los pasos anteriores hasta que todos los dispositivos y usuarios estén inscritos y administrados por Intune.

## <a name="retire-the-previous-enterprise-mobility-management-solution"></a>Retirar la solución de administración de movilidad empresarial anterior

Después de migrar todos los usuarios y dispositivos a Intune y de comprobar que las migraciones se han realizado correctamente, puede retirar la solución de administración de movilidad empresarial anterior o cancelar la suscripción del servicio. Siga las instrucciones del proveedor de la solución para asegurarse de que quita correctamente todos los requisitos innecesarios de la infraestructura y para cancelar las suscripciones o licencias.

## <a name="additional-migration-resources"></a>Recursos de migración adicionales

¿Necesita ayuda adicional con la migración a Intune? Tiene a su disposición varias opciones de ayuda experta para que su migración se realice sin problemas:

<!--- - [Microsoft Intune Onboarding](/em/solutions/fasttrack-center-benefit-for-enterprise-mobility-suite-ems)--->
- [Servicios de consultoría de Microsoft](https://www.microsoft.com/en-us/microsoftservices/default.aspx)
- [Soporte técnico y no técnico de Intune](/intune/troubleshoot/how-to-get-support-for-microsoft-intune)
- [Foro de TechNet sobre Microsoft Intune](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)

## <a name="get-a-downloadable-copy-of-this-guide"></a>Obtener una copia descargable de esta guía

Para obtener una copia descargable de toda esta guía, visite la [Galería de TechNet](https://gallery.technet.microsoft.com/Migrating-to-Intune-ea439387).



<!--HONumber=Feb17_HO3-->


