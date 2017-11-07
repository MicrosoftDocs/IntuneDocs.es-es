---
title: "Pruebas y validación de Intune"
description: "Los detalles que debe tener en cuenta cuando prueba y valida en su entorno una solución de Intune que solo está en la nube."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4f82ee0c-4bd6-4623-9b10-9249d316ccf5
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.openlocfilehash: f10b4b0e7c48e921eb92392edf95bfcfaa83db9f
ms.sourcegitcommit: 94d3d86f8ae9f82a9872384bbaae53580036a4ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2017
---
# <a name="intune-testing-and-validation"></a>Pruebas y validación de Intune

La fase de pruebas tiene lugar durante y después de la fase de implementación. Necesita cuentas, grupos y dispositivos de prueba para llevar a cabo pruebas de todos los escenarios necesarios de TI (administración) y de usuario final (caso de uso) que haya identificado anteriormente.

Le recomendamos que incorpore a su personal del departamento de soporte técnico de TI en la fase de pruebas para que se cree documentación de soporte técnico y que el personal de ese departamento se encuentre cómodo proporcionando ayuda del producto. Si un componente o un escenario no funciona basándose en los casos de uso, asegúrese de documentar los cambios necesarios e incluir la razón por la que se efectuó el cambio.

## <a name="before-you-begin"></a>Antes de comenzar

Le recomendamos que documente lo siguiente:

-   **Criterios de prueba:** identifique los bancos de pruebas en los que se van a medir.

-   **Componentes de diseño:** deben existir en al menos un criterio de prueba.

Si un componente de diseño no existe en al menos un criterio de prueba que se adapta a un requisito o escenario, plantéese si este es necesario o no. Además, asegúrese de tener los siguientes elementos:

-   **Cuentas:** cuentas de prueba que tienen una licencia de EMS y Office 365 para probar todos los escenarios de casos de uso.

-   **Dispositivos:** dispositivos de prueba que se pueden borrar o restablecer a los valores de fábrica.

-   **Componentes de integración:** todos los componentes de integración (conector de certificado, conector de servicio a servicio de Intune para Exchange hospedado y conector local de Intune para Exchange) deben estar instalados y configurados en caso necesario.

Puede que necesite efectuar cambios de diseño para contemplar problemas imprevistos. Además, todos los cambios de diseño deben estar completamente documentados con el motivo de cada cambio. Aquí se muestra un ejemplo para mostrar lo que puede ser un cambio:

<blockquote>Se da cuenta de que no cumple los requisitos del Servicio de inscripción de dispositivos de red (NDES) y se percata de que los perfiles de VPN y Wi-Fi se pueden configurar con una CA raíz que cumpla los mismos requisitos sin una implementación de NDES.</blockquote>

Puede experimentar problemas que requieran instrucciones técnicas o una solución de problemas especializada durante el proceso de validación y de pruebas. Le recomendamos que solicite ayuda a través de los canales de soporte técnico de Microsoft.

-   [Más información sobre cómo obtener soporte técnico de Intune](get-support.md)

-   [Asistencia telefónica para Microsoft Intune](/intune-classic/troubleshoot/contact-assisted-phone-support-for-microsoft-intune)

## <a name="functional-validation-testing"></a>Pruebas de validación funcional

La validación funcional consiste en probar cada componente y configuración para determinar si está funcionando correctamente. En la tabla siguiente se muestra un ejemplo de prueba de validación.

![Sección 9 tabla 1](./media/section-9-image-1-table.PNG)

## <a name="use-case-validation-testing"></a>Pruebas de validación de casos de uso

Lleve a cabo pruebas de validación de casos de uso para comprobar que los escenarios están completos y son funcionales. Existen dos tipos de escenarios de casos de uso: la administración de TI y el usuario final.

### <a name="it-admin"></a>Administración de TI

Lleve a cabo pruebas de validación de la administración de TI para validar que las acciones administrativas efectuadas en un dispositivo o usuario funcionan correctamente. A continuación se muestra un ejemplo de un escenario de validación completo de la administración de TI.

![Sección 9 tabla 2](./media/section-9-image-2-table.PNG)

### <a name="end-user"></a>Usuario final

Lleve a cabo pruebas de validación del usuario final para validar que la experiencia del usuario final es la prevista y se presenta correctamente en todas las comunicaciones de usuario. Es importante validar que la experiencia del usuario final es correcta. De no hacerlo, es posible que el ritmo de adopción sea inferior y que aumente el volumen de llamadas al departamento de soporte técnico.

![Sección 9 tabla 3](./media/section-9-image-3-table.PNG)

## <a name="next-steps"></a>Pasos siguientes

Ahora que ha probado y validado sus escenarios de casos de uso y los escenarios funcionales de Intune, está listo para la [implementación de producción de Intune](planning-guide-rollout-plan.md).

Consulte los [recursos adicionales](planning-guide-resources.md) para obtener más información y plantillas de planeación.
