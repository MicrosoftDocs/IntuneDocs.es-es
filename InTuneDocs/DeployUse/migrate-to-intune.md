---
# required metadata

title: Migrar a Intune | Microsoft Intune
description:
keywords:
author: jeffgilb
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 88936b8a-7453-4410-b6db-29f636ba3e72

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Migrar a Intune


La migración a Intune desde su solución de administración de movilidad empresarial actual podría seguir la secuencia de pasos siguiente:

![Pasos de migración para Intune](./media/migrate-intune-steps.png)

## Notificar el cambio a los usuarios

Cuando esté convencido de que la implementación piloto de Intune cumple sus expectativas, comuníqueles a los usuarios la futura migración de sus dispositivos a Intune. Con mensajes de correo electrónico, [instrucciones](http://www.microsoft.com/en-us/download/details.aspx?id=46398) y [pósteres](https://gallery.technet.microsoft.com/Intune-End-User-Enrollment-3a0c9b0c?WT.mc_id=Blog_Intune_General_PCIT), puede establecer las expectativas y proporcionar detalles sobre los pasos de inscripción que los usuarios deberán seguir para no interrumpir la conectividad a las aplicaciones y los recursos de empresa. Asegúrese de que el equipo de soporte está preparado para ayudar a los usuarios en el proceso de migración.

## Modificar la solución de administración de movilidad empresarial existente

En función de cómo planee gestionar las directivas de acceso condicional entre su solución de administración de movilidad empresarial existente e Intune, deberá deshabilitar las directivas de acceso condicional que tenga en vigor. Tiene dos opciones: deshabilitar las directivas de acceso condicional existentes, o bien definir su ámbito para que no incluyan a los usuarios y dispositivos que va a migrar a Intune.  Evite que Intune y su solución de administración de movilidad de empresa existente apliquen las directivas de acceso condicional a los mismos usuarios o dispositivos.

## Habilitar la directiva de acceso condicional de Intune (opcional)

Si ha decidido aplicar inmediatamente las directivas de acceso condicional sin un período de gracia para la migración de dispositivos, habilite las directivas de acceso condicional de Intune en este paso.  Asegúrese de que esta decisión se ha comunicado a los usuarios y a su equipo de soporte técnico.  Si los dispositivos no están inscritos en Intune y no son compatibles con las directivas de Intune, los usuarios no podrán tener acceso a los recursos corporativos hasta que no se inscriban en Intune y los dispositivos sean compatibles con las directivas de Intune.

## Cancelar la inscripción de los dispositivos de la solución de administración de movilidad empresarial actual

Antes de su inscripción en Intune, los dispositivos deben darse de baja de su solución de administración de movilidad empresarial existente. Nuestra recomendación es que permita que los usuarios cancelen ellos mismos la inscripción de sus dispositivos.  Siga las pautas de cancelación de inscripción facilitadas por el proveedor de soluciones para asegurarse de que los usuarios y dispositivos se quitan correctamente de la plataforma y para garantizar que el tiempo de interrupción del servicio sea mínimo.

## Inscribir dispositivos en Intune

Los usuarios que vayan a migrar deberán inscribirse de inmediato en Intune para recuperar o no perder el acceso a los recursos, el correo electrónico y las aplicaciones de la empresa. Si ha configurado el acceso condicional y los usuarios intentan conectarse al correo electrónico antes de inscribirse en Intune, se bloqueará el acceso y se les dará la bienvenida con un correo electrónico con instrucciones de inscripción. Este correo electrónico les servirá de guía para inscribir su dispositivo en Intune.  Los usuarios también tienen la opción de inscribirse en Intune a través de la aplicación de Portal de empresa de Intune o de forma nativa a través del sistema operativo en Windows 8.1 y Windows 10 Mobile. Consulte [Qué decirles a los usuarios finales sobre el uso de Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md) para obtener más instrucciones de inscripción por plataforma.

## Configurar el acceso condicional de Intune (opcional)

Si ha permitido un período de gracia para la aplicación del acceso condicional, habilite las directivas de acceso condicional de Intune para iniciar la aplicación cuando haya finalizado el período de gracia que ha comunicado a los usuarios finales. Esto requerirá inmediatamente que todos los dispositivos cumplan los requisitos de la directiva de acceso condicional de Intune.

## Inscribir el resto de los usuarios y dispositivos

Una vez habilitado el acceso condicional, todos los usuarios deben inscribirse en Intune y cumplir las directivas de cumplimiento de su organización para tener acceso a los recursos corporativos. Si ha migrado los usuarios en una inscripción por fases (es decir, no todos a la vez), repita los pasos anteriores hasta que todos los dispositivos y usuarios estén inscritos y administrados por Intune.

## Retirar la solución de administración de movilidad empresarial anterior

Después de migrar todos los usuarios y dispositivos a Intune y de comprobar que las migraciones se han realizado correctamente, puede retirar la solución de administración de movilidad empresarial anterior o cancelar la suscripción del servicio. Siga las instrucciones del proveedor de la solución para asegurarse de que quita correctamente todos los requisitos innecesarios de la infraestructura y para cancelar las suscripciones o licencias.

## Recursos de migración adicionales

¿Necesita ayuda adicional con la migración a Intune? Tiene a su disposición varias opciones de ayuda experta para que su migración se realice sin problemas:

<!--- - [Microsoft Intune Onboarding](/em/solutions/fasttrack-center-benefit-for-enterprise-mobility-suite-ems)--->
- [Servicios de consultoría de Microsoft](https://www.microsoft.com/en-us/microsoftservices/default.aspx)
- [Soporte técnico y no técnico de Intune](/intune/troubleshoot/how-to-get-support-for-microsoft-intune)
- [Foro de TechNet sobre Microsoft Intune](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)

## Obtener una copia descargable de esta guía

Para obtener una copia descargable de toda esta guía, visite la [Galería de TechNet](https://gallery.technet.microsoft.com/Migrating-to-Intune-ea439387)..


<!--HONumber=May16_HO1-->


