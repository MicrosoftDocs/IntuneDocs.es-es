---
title: ¿Cómo puede Microsoft Intune ayudar a mi empresa?
titleSuffix: ''
description: Problemas empresariales comunes que Microsoft Intune ayuda a resolver.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/26/2019
ms.topic: overview
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6bfab644-c1e2-4154-a254-e95b9a1d75f2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 313e4ccf0e96536b3e99edb968298e4cc3343aa1
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61513998"
---
# <a name="what-can-intune-do-for-my-company"></a>¿Cómo puede Intune ayudar a mi empresa?
Microsoft Intune es un servicio de administración de movilidad empresarial (EMM) basado en nube que ayuda a los empleados a ser productivos mientras mantiene protegidos los datos corporativos.

Intune permite:

- Administrar los dispositivos móviles que los empleados usan para tener acceso a datos de la empresa.
- Administrar las aplicaciones móviles que usa la plantilla.
- Proteger la información de la empresa al ayudar a controlar la manera en que los empleados tienen acceso a ella y la comparten.
- Garantizar que los dispositivos y las aplicaciones sean compatibles con los requisitos de seguridad de la empresa.

## <a name="common-business-problems-that-intune-helps-solve"></a>Problemas empresariales comunes que Intune ayuda a resolver

* [Proteger el correo electrónico y los datos locales para tener acceso a ellos desde un dispositivo móvil](common-scenarios.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Proteger el correo electrónico y los datos de Office 365 para tener acceso a ellos sin riesgos desde un dispositivo móvil](common-scenarios.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Distribuir teléfonos de propiedad corporativa entre los trabajadores](common-scenarios.md#issue-corporate-owned-phones-to-your-employees)
* [Ofrecer un programa "Bring Your Own Device" (BYOD) o de dispositivo personal a todos los empleados](common-scenarios.md#offer-a-bring-your-own-device-program-to-all-employees)
* [Permitir que los empleados tengan un acceso seguro a Office 365 desde un quiosco público no administrado](common-scenarios.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
* [Distribuir tabletas compartidas de uso limitado entre los trabajadores de tareas](common-scenarios.md#issue-limited-use-shared-tablets-to-your-employees)

## <a name="quickstarts"></a>Inicios rápidos

Somos conscientes de que puede ser difícil administrar dispositivos móviles. Hay muchas decisiones diferentes que deberá tomar en nombre de su empresa. Los siguientes tutoriales lo ayudarán a empezar a trabajar con Intune y a realizar algunas tareas comunes en una cantidad mínima de tiempo.

Puede seguir el orden previsto de los **inicios rápidos** usando la tabla de contenidos del lado izquierdo de esta página.

- [Probar Intune gratis](free-trial-sign-up.md): cree una suscripción gratuita para probar Intune en un entorno de prueba.    
- [Crear un usuario](quickstart-create-user.md): agregue un usuario a Intune para que pueda acceder a los recursos de la empresa en dispositivos móviles.
- [Crear un grupo](quickstart-create-group.md): organice los usuarios en grupos para administrar las directivas y las aplicaciones a las que pueden acceder con más facilidad.
- [Configurar la inscripción automática](quickstart-setup-auto-enrollment.md): configure Intune para inscribir automáticamente los dispositivos cuando determinados usuarios inicien sesión en dispositivos Windows 10.
- [Inscribir el dispositivo](quickstart-enroll-windows-device.md): asuma el rol de un usuario de Intune e inscriba su dispositivo en Intune. Luego, vuelva a Intune y confirme que el dispositivo se ha inscrito correctamente.
- [Crear una directiva de cumplimiento de dispositivos](quickstart-set-password-length-android.md): cree una directiva de cumplimiento de dispositivos y asígnele un grupo.
- [Enviar notificaciones a dispositivos no conformes](quickstart-send-notification.md): envíe una notificación por correo electrónico a los miembros de su personal que tengan dispositivos no conformes. Para ello, cree y asigne una directiva de cumplimiento.
- [Agregar y asignar una aplicación](quickstart-add-assign-app.md): agregue y asigne una aplicación cliente a los empleados de su empresa.
- [Crear y asignar una directiva de protección de aplicaciones](quickstart-create-assign-app-policy.md): cree y asigne una directiva de protección de aplicaciones a una aplicación cliente en el dispositivo de un usuario final.
- [Crear y asignar un rol personalizado](quickstart-create-custom-role.md): cree y asigne un rol personalizado con permisos específicos para un departamento de operaciones de seguridad. 
- [Crear un perfil de dispositivo de correo para iOS](quickstart-email-profile.md): cree un perfil de dispositivo de correo para dispositivos iOS.

## <a name="prerequisites"></a>Requisitos previos

Antes de comenzar, debe tener una cuenta de inquilino y administrador de Intune activada. Cree una suscripción gratuita para [probar Intune gratis](free-trial-sign-up.md) en un entorno de prueba. Los suscriptores actuales también pueden completar estas actividades en su inquilino dinámico. Estos artículos de introducción presuponen que está trabajando en dispositivos de prueba.

También necesita asegurarse de que es el administrador global de su organización para poder completar todas las tareas de Introducción.

## <a name="intune-architecture"></a>Arquitectura de Intune

Intune es el componente de Enterprise Mobility + Security (EMS) que administra aplicaciones y dispositivos móviles. Intune se integra perfectamente con otros componentes de EMS, como Azure Active Directory (Azure AD) para la identidad y el control de acceso y Azure Information Protection para la protección de datos. Al usarlo junto a Office 365, permite que los empleados sean productivos en todos sus dispositivos sin poner en peligro la información de la organización.

![Diagrama de arquitectura de alto nivel para Microsoft Intune](/intune/media/intunearchitecture.svg)

## <a name="next-steps"></a>Pasos siguientes

[Introducción a Azure](get-started-azure.md): descubra los componentes de Azure Portal, además de cómo realizar cambios en la página.

## <a name="learn-more"></a>Obtener más información

* [¿Qué es Intune?](introduction-intune.md)
* [¿Qué es Azure Portal?](what-is-intune.md)
* [Ciclos de vida de aplicaciones y dispositivos](introduction-device-app-lifecycles.md)
