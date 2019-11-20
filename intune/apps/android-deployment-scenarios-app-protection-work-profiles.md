---
title: Directivas de protección de aplicaciones y perfiles de trabajo de Microsoft Intune (Azure) | Microsoft Docs
description: Al decidir usar directivas de protección de aplicaciones o perfiles de trabajo para dispositivos personales o BYOD de Android Enterprise en Microsoft Intune, es necesario examinar las diferencias y las ventajas o desventajas. Compare las diferencias y características que se obtienen con las directivas de protección de aplicaciones sin inscripción (APP-WE) y los perfiles de trabajo de Android Enterprise.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: d0b4f8d5124924d013e7ac131dafc947a95c7b65
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059792"
---
# <a name="application-protection-policies-and-work-profiles-on-android-enterprise-devices-in-intune"></a>Directivas de protección de aplicaciones y perfiles de trabajo en dispositivos de Android Enterprise en Intune

En muchas organizaciones, los administradores se encuentran con la dificultad de proteger los recursos y datos de diferentes dispositivos. Uno de los retos es protege los recursos de los usuarios con dispositivos personales de Android Enterprise, lo que también se conoce como Bring-Your-Own-Device (BYOD). Microsoft Intune admite dos escenarios de implementación de Android para Bring-Your-Own-Device (BYOD):

- Directivas de protección de aplicaciones sin inscripción (APP-WE)
- Perfiles de trabajo de Android Enterprise

Los escenarios de implementación de APP-WE y perfiles de trabajo de Android incluyen las siguientes características clave importantes en entornos BYOD:

1. **Protección y segregación de datos administrados por la organización**: ambas soluciones protegen los datos de la organización al aplicar controles de prevención de pérdida de datos (DLP) en datos administrados por esta. Estas protecciones impiden las pérdidas accidentales de datos protegidos, como en el caso, por ejemplo, de un usuario que los comparte por accidente con una aplicación o cuenta personal. También sirven para garantizar que un dispositivo que accede a los datos está en buen estado y no corre peligro.

2. **Privacidad del usuario final**: APP-WE y los perfiles de trabajo de Android Enterprise separan el contenido de los usuarios finales que hay en el dispositivo de los datos administrados por el administrador de administración de dispositivos móviles (MDM). En ambos escenarios, los administradores de TI aplican directivas, como la autenticación solo con PIN en aplicaciones o identidades administradas por la organización. Los administradores de TI no pueden leer ni borrar los datos que poseen o controlan los usuarios finales, ni tampoco acceder a ellos.

La decisión de elegir APP-WE o perfiles de trabajo de Android Enterprise para la implementación BYOD depende de sus requisitos y necesidades empresariales. El objetivo de este artículo es proporcionarle una orientación para ayudarle a decidir.

## <a name="about-intune-app-protection-policies"></a>Sobre las directivas de protección de aplicaciones de Intune

Las directivas de protección de aplicaciones de Intune (APP) son directivas de protección de datos dirigidas a los usuarios. Las directivas aplican protección de pérdida de datos en el nivel de aplicación. Intune APP exige que los desarrolladores de aplicaciones habiliten características de APP en las aplicaciones que creen.

Las aplicaciones individuales de Android están habilitadas para APP de varias maneras:

1. **Están integradas de forma nativa en aplicaciones propias de Microsoft**: las aplicaciones de Microsoft Office para Android y una selección de otras aplicaciones de Microsoft, vienen integradas con Intune APP. Estas aplicaciones de Office, como Word, Outlook, OneDrive, etc., no necesitan ninguna otra personalización para aplicar las directivas. Los usuarios finales pueden instalar directamente estas aplicaciones desde Google Play Store.

2. **Están integradas en aplicaciones creadas por los desarrolladores mediante el SDK de Intune**: los desarrolladores de aplicaciones pueden integrar el SDK de Intune en su código fuente y volver a compilar sus aplicaciones para admitir las características de directivas de APP.

3. **Están ajustadas mediante la herramienta de ajuste de aplicaciones de Intune**: algunos clientes compilan las aplicaciones Android (archivo .APK) sin acceso al código fuente. Sin el código fuente, los desarrolladores no pueden realizar la integración con el SDK de Intune. Sin el SDK, no pueden habilitar su aplicación para las directivas de APP. Los desarrolladores deben modificar o volver a codificar la aplicación para admitir las directivas de APP.

    Como ayuda, Intune incluye la **herramienta de ajuste de aplicaciones** para las aplicaciones Android existentes (APK), y crea una aplicación que reconoce las directivas de APP.

    Para más información sobre esta herramienta, vea [prepare line-of-business apps for app protection policies](../developer/apps-prepare-mobile-application-management.md) (Preparar aplicaciones de línea de negocio para las directivas de protección de aplicaciones).

Para ver una lista de aplicaciones habilitadas con APP, consulte [Aplicaciones administradas con un amplio conjunto de directivas de protección de aplicaciones móviles](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

## <a name="deployment-scenarios"></a>Escenarios de implementación

En esta sección se describen las importantes características de los escenarios de implementación de APP-WE y perfiles de trabajo de Android Enterprise.

### <a name="app-we"></a>APP-WE

Una implementación de APP-WE (directivas de protección de aplicaciones sin inscripción) define las directivas sobre aplicaciones, no sobre dispositivos. En este escenario, los dispositivos normalmente no están inscritos ni administrados por una entidad de MDM, como Intune. Para proteger las aplicaciones y el acceso a los datos de la organización, los administradores usan aplicaciones que se pueden administrar con APP y aplican directivas de protección de datos a estas aplicaciones.

Esta característica se aplica a:

- Android 4.4 y versiones posteriores

> [!TIP]
> Para más información, consulte [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md)

Los escenarios de APP-WE son para usuarios finales que quieren una superficie organizativa pequeña en sus dispositivos y no desean inscribirlos en MDM. Como administrador, aún debe proteger los datos. Estos dispositivos no están administrados. De modo que, las tareas y características comunes de MDM, como Wi-Fi, VPN de dispositivos y administración de certificados, no forman parte de este escenario de implementación.

### <a name="android-enterprise-work-profiles"></a>Perfiles de trabajo de Android Enterprise

Los perfiles de trabajo son el escenario de implementación principal de Android Enterprise y el único escenario dirigido en casos de uso de BYOD. El perfil de trabajo es una partición independiente que se crea en el nivel del sistema operativo Android que puede administrarse mediante Intune.

Esta característica se aplica a:

- Dispositivos Android 5.0 y versiones posteriores con Google Mobile Services

Un perfil de trabajo incluye las siguientes características:

- **Funcionalidad de MDM tradicional**: las principales funcionalidades de MDM, como la administración del ciclo de vida de las aplicaciones mediante Google Play administrado, están disponibles en cualquier escenario de Android Enterprise. Google Play administrado proporciona una experiencia sólida para instalar y actualizar aplicaciones sin la intervención del usuario. El departamento de TI también puede insertar la configuración de aplicaciones en las aplicaciones de la organización. No es necesario que los usuarios finales permitan instalaciones desde orígenes desconocidos. Otras actividades comunes de MDM disponibles con los perfiles de trabajo son la implementación de certificados, la configuración de redes Wi-Fi o VPN y la configuración de códigos de acceso de dispositivo.

- **DLP en los límites del perfil de trabajo**: al igual que en APP-WE, el departamento de TI puede aplicar directivas de protección de datos. Con un perfil de trabajo, las directivas de DLP se aplican en el nivel de perfil de trabajo, no en el nivel de aplicación. Por ejemplo, la protección contra copiar y pegar se aplica a una aplicación mediante la configuración de APP o se aplica mediante el perfil de trabajo. Cuando la aplicación se implementa en un perfil de trabajo, los administradores pueden pausar la protección contra copiar y pegar en el perfil de trabajo mediante la desactivación de esta directiva en el nivel de APP.

## <a name="tips-to-optimize-the-work-profile-experience"></a>Sugerencias para optimizar la experiencia del perfil de trabajo

### <a name="when-to-use-app-within-work-profiles"></a>Cuándo usar APP en los perfiles de trabajo

Intune APP y los perfiles de trabajo son tecnologías complementarias que se pueden usar juntas o separadas. Desde el punto de vista de la arquitectura, ambas soluciones aplican directivas en diferentes capas: APP en la capa de la aplicación individual y el perfil de trabajo en la capa de perfil. La implementación de aplicaciones administradas con una directiva de APP en una aplicación de un perfil de trabajo es un escenario válido y admitido. El uso de APP, los perfiles de trabajo o una combinación de ambos depende de los requisitos de DLP.

Las configuraciones de los perfiles de trabajo y APP se complementan entre sí al proporcionar cobertura adicional si un perfil no satisface los requisitos de protección de datos de la organización. Por ejemplo, los perfiles de trabajo no proporcionan de forma nativa controles para impedir que una aplicación se guarde en una ubicación de almacenamiento en la nube que no es de confianza. APP incluye esta característica. Puede decidir que es suficiente con la prevención de pérdida de datos que proporciona el perfil de trabajo y elegir no usar APP. O, puede que necesite las protecciones que resultan de combinar los dos métodos.

### <a name="suppress-app-policy-for-work-profiles"></a>Supresión de la directiva de APP en los perfiles de trabajo

Es posible que deba admitir usuarios que tienen varios dispositivos: dispositivos no administrados en un escenario APP-WE y dispositivos administrados con perfiles de trabajo.

Por ejemplo, exige que los usuarios escriban un PIN al abrir una aplicación de trabajo. En función del dispositivo, las características del PIN se gestionan mediante APP o el perfil de trabajo. En los dispositivos APP-WE, APP aplica el comportamiento de escribir el PIN para iniciar. En dispositivos con perfil de trabajo, puede usar un PIN de dispositivo o de perfil de trabajo aplicado por el sistema operativo. Para realizar este escenario, configure los valores de APP de forma que no se apliquen *cuando* una aplicación se implemente en un perfil de trabajo. Si no lo configura de este modo, el usuario final recibe una solicitud de PIN en el dispositivo y otra en la capa de APP.

### <a name="control-multi-identity-behavior-in-work-profiles"></a>Control del comportamiento de identidades múltiples en los perfiles de trabajo

Las aplicaciones de Office, como Outlook y OneDrive, tienen un comportamiento de "identidades múltiples". Dentro de una instancia de la aplicación, el usuario final puede agregar conexiones a varias cuentas o ubicaciones de almacenamiento en la nube distintas. Dentro de la aplicación, los datos recuperados desde estas ubicaciones pueden estar separados o combinados. Y, el usuario puede cambiar de contexto entre identidades personales (user@outlook.com) e identidades de la organización (user@contoso.com).

Al usar perfiles de trabajo, puede que quiera deshabilitar este comportamiento de identidades múltiples. Al deshabilitarlo, las instancias con distintivo de la aplicación en el perfil de trabajo solo pueden configurarse con una identidad de organización. Use la opción de configuración de aplicaciones Cuentas permitidas para permitir la compatibilidad con aplicaciones Android de Office.

Para más información, consulte [Implementación de Outlook para iOS y opciones de configuración de aplicación de Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

## <a name="when-to-use-intune-app"></a>Cuándo usar Intune APP

Hay varios escenarios de movilidad empresarial donde el uso de Intune APP es la mejor recomendación.

### <a name="older-devices-running-android-44-51-are-being-used"></a>Se usan dispositivos antiguos que ejecutan Android 4.4-5.1

Oficialmente, cualquier dispositivo Android 5.0 o versiones posteriores con Google Mobile Services admite perfiles de trabajo y es apto para administrarse de esa manera. Sin embargo, algunos dispositivos Android 5.0 y 5.1 de algunos OEM no admiten perfiles de trabajo.

Si usa versiones que no admiten perfiles de trabajo y quiere garantizar la protección frente a la pérdida de datos de la organización en los dispositivos, debe usar las características de Intune APP.

### <a name="no-mdm-no-enrollment-google-services-are-unavailable"></a>Sin MDM, sin inscripción, los servicios de Google no están disponibles

Algunos clientes no quieren ninguna forma de administración de dispositivos, lo que incluye la administración de los perfiles de trabajo, por diversos motivos:

- Motivos legales y de responsabilidad
- Para mantener la coherencia de la experiencia del usuario
- El entorno de dispositivos Android es enormemente heterogéneo
- No hay ninguna conectividad con servicios de Google, lo que es necesario para la administración de perfiles de trabajo.

Por ejemplo, los clientes de China o que tienen usuarios en este país no pueden usar la administración de dispositivos Android dado que los servicios de Google están bloqueados. En este caso, use Intune APP para DLP.

## <a name="summary"></a>Resumen

Con Intune, tiene a su disposición tanto APP-WE como perfiles de trabajo de Android Enterprise para su programa BYOD de Android. La elección de APP-WE o de perfiles de trabajo depende de sus requisitos de uso y empresariales. En resumen, use perfiles de trabajo si necesita actividades de MDM en dispositivos administrados, como la implementación de certificados, la inserción de aplicaciones, etc. Use APP-WE si no quiere o no puede administrar dispositivos, y únicamente usa aplicaciones habilitadas para Intune APP.

## <a name="next-steps"></a>Pasos siguientes
[Comience a usar directivas de protección de aplicaciones](app-protection-policy.md) o [inscriba sus dispositivos](../enrollment/android-enroll.md).
