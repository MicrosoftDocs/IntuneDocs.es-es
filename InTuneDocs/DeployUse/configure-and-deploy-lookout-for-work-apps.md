---
title: "Implementar la aplicación Lookout for Work | Microsoft Intune"
description: Configure e implemente aplicaciones Lookout for Work para Android.
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 524c4209-ad57-4d35-955e-a00d796bf858
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c4d05b9ba7249e4068d21480b1c9db342277757e
ms.openlocfilehash: 687a102ccb34cb7acfaab1e8a1d4b67cb54b9e92


---

# Configurar e implementar aplicaciones Lookout for Work
En este artículo se explica cómo configurar e implementar la aplicación Lookout for Work para los dispositivos inscritos que se ejecutan en Android 4.1 o versiones posteriores.

* **Paso 1:** en la [consola de administración de Microsoft Intune](https://manage.microsoft.com), vaya a **Aplicaciones** y seleccione **Agregar aplicaciones**.   
* **Paso 2:** en la página **Instalación de software** del publicador, seleccione **Vínculo externo** y especifique la dirección URL siguiente: https://play.google.com/store/apps/details?id=com.lookout.enterprise.
>[!NOTE]
>No haga clic en el cuadro para exigir un explorador administrado.

* **Paso 3:** en la página **Descripción del software**, rellene la información siguiente:
  * **Publicador:** Lookout Mobile Security
  * **Nombre:** Lookout for Work
  * **Descripción:** Lookout ofrece la mejor protección contra amenazas móviles para proteger el dispositivo. Cuando se instala la aplicación Lookout en el dispositivo, lo protege de amenazas y avisa, tanto a usted como al administrador de la empresa, si detecta alguna.
  * **Categoría:** administración de equipos
* **Paso 4:** una vez finalizado correctamente, aparece un mensaje **La carga de datos en Microsoft Intune se completó correctamente**.

Cuando haga clic en **Aplicaciones** en la consola de administrador de Intune, ahora verá la aplicación Lookout for Work en la lista. ![captura de pantalla de la página de aplicaciones de la consola de administración de Intune con la aplicación Lookout for Work en la lista](../media/mtp/lookout-app-listed-intune-console.png)

**Para implementar la aplicación en los usuarios**, seleccione la aplicación Lookout for Work que aparece en la pantalla anterior y luego **Administrar la implementación**.

Debe seleccionar los mismos usuarios que agregó en la opción Administración de la inscripción en la consola de Lookout MTP.  Vea el paso 3 de la sección [Configurar la suscripción con Lookout MTP](set-up-your-subscription-with-lookout-mtp#configure-your-subscription-with-lookout-mtp) para obtener información sobre cómo agregar grupos de usuarios a Lookout MTP.
>[!IMPORTANT]
> El Asistente para la implementación de aplicaciones de Intune no es consciente de los grupos de usuarios de Azure AD y usa los de Intune en su lugar, por lo que debe crear un grupo de usuarios de Intune basado en el de Azure AD que está inscrito en la consola de Lookout MTP, como se describe en [este](plan-your-user-and-device-groups.md) tema.

Seleccione la opción **Instalación requerida** para exigir que la aplicación Lookout se instale en el dispositivo del usuario.


Con la opción **Instalación requerida** seleccionada para la implementación, Intune instalará la aplicación Lookout for Work en el dispositivo.   

Cuando el usuario abre Lookout for Work en el dispositivo, se le pide que active la aplicación y que seleccione la opción Iniciar sesión con Azure Active Directory. En los temas siguientes encontrará un tutorial detallado con el flujo para el usuario final:

* [Se le pide instalar Lookout for Work en un dispositivo Android](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

* [Debe solucionar una amenaza detectada por Lookout for Work en el dispositivo Android](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## Pasos siguientes
* [Habilitar la regla de protección contra amenazas móviles en la directiva de cumplimiento normativo](enable-device-threat-protection-rule-in-compliance-policy.md)



<!--HONumber=Sep16_HO3-->


