---
title: "Implementar la aplicación Lookout for Work | Microsoft Intune"
description: Configure e implemente aplicaciones Lookout for Work para Android.
author: karthikaraman
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 524c4209-ad57-4d35-955e-a00d796bf858
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4a69be67c3ef9f028c77c738de5f1fcbd59a8d33
ms.openlocfilehash: 2c626cb0a36c38c7b5deeca0ff1e902018540634


---

# Configurar e implementar aplicaciones Lookout for Work
En este artículo se explica cómo configurar e implementar la aplicación Lookout for Work para los dispositivos Android e iOS.

## Android (aplicación Google Play Store)

* **Paso 1:** Cargue la aplicación Android Lookout for Work en la [consola de administrador de Microsoft Intune](https://manage.microsoft.com), tal como se describe en el tema [Agregar aplicaciones para dispositivos móviles en Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune).
>[!NOTE]
> No haga clic en el cuadro para exigir un explorador administrado.

![captura de pantalla de la página de aplicaciones de la consola de administrador de Intune con las aplicaciones Lookout for Work en la lista](../media/mtp/lookout-app-listed-intune-console.png)

* **Paso 2:** Implemente la aplicación para los usuarios. Seleccione la aplicación Lookout for Work que aparece en la pantalla anterior y luego **Administrar la implementación**.

  Debe seleccionar los mismos usuarios que ha agregado en la opción Administración de la inscripción en la consola de Lookout.  Vea el paso 3 de la sección sobre cómo [configurar la suscripción con la protección contra amenazas de dispositivo de Lookout](set-up-your-subscription-with-lookout-mtp#configure-your-subscription-with-lookout-mtp) para obtener información sobre cómo agregar grupos de usuarios a Lookout MTP.
>[!IMPORTANT]
> El Asistente para implementación de aplicaciones de Intune no es consciente de los grupos de usuarios de Azure AD y usa los de Intune en su lugar, por lo que debe crear un grupo de usuarios de Intune basado en el de Azure AD que está inscrito en la consola de Lookout, como se describe en [este](plan-your-user-and-device-groups.md) tema.

Seleccione la opción **Instalación requerida** para exigir que la aplicación Lookout se instale en el dispositivo del usuario.


## iOS (versión para empresa de la aplicación Lookout)

* **Paso 1:** Asegúrese de que la **administración de iOS** está configurada en el dispositivo. Para saber cómo configurar el dispositivo para la administración de iOS, consulte [Configurar la administración de dispositivos iOS y Mac](set-up-ios-and-mac-management-with-microsoft-intune.md).

* **Paso 2:** **Vuelva a firmar** la aplicación de iOS Lookout for Work. Lookout distribuye su aplicación Lookout for Work de iOS fuera de la tienda App Store de iOS. **Antes de distribuir la aplicación**, deberá volver a firmar la aplicación con su certificado de desarrollador empresarial de iOS. Para saber cómo volver a firmar las aplicaciones Lookout for Work de iOS, consulte [el proceso de volver a firmar de la aplicación Lookout for Work de iOS](https://personal.support.lookout.com/hc/en-us/articles/114094038714) en el sitio de Lookout.


* **Paso 3:** Habilite la autenticación de Azure Active Directory para los usuarios de iOS haciendo lo siguiente:
  1.  Inicie sesión en el [portal de administración de Azure Active Directory](https://manage.windowsazure.com) y vaya a la página de aplicación.
  2.  Agregue la **aplicación Lookout for Work de iOS** como una **aplicación de cliente nativ**.
  ![captura de pantalla del cuadro de diálogo Agregar aplicaciones que muestra la opción de aplicación de cliente nativo](../media/mtp/aad-add-app.png)

  3. Reemplace **com.lookout.enterprise.yourcompanyname** por el ID de agrupación del cliente que ha seleccionado cuando se registró el IPA.
  4.  Agregue un URI de redirección adicional: **&lt;companyportal://code/>** seguido de una versión codificada por URL del URI de redirección original.
  5.  Agregue los **permisos delegados** a la aplicación.

  Para más información, consulte [Configurar una aplicación de cliente nativo](https://azure.microsoft.com/en-us/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application).


* **Paso 4:** Cargue el archivo .ipa que ha vuelto a firmar tal como se describe en tema [Agregar aplicaciones a los dispositivos inscritos en Intune](https://docs.microsoft.com/en-us/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune). Establezca la versión mínima del sistema operativo en iOS 8.0 o posterior.

  ![captura de pantalla de la página de aplicaciones de la consola de administrador de Intune con la aplicación Lookout for Work, que se muestran en la lista de aplicaciones](../media/mtp/ios-app-uploaded-intune.png)

* **Paso 5:** Cree la directiva de configuración de la aplicación administrada, tal como se describe en el tema [Configurar aplicaciones de iOS con directivas de configuración de aplicaciones móviles en Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).

  ![captura de pantalla de la creación de un asistente para nueva directiva con la directiva de configuración de aplicación iOS 8.0 o posterior resaltada](../media/mtp/ios-app-config.png)

* **Paso 6:** **Para implementar la aplicación en los usuarios**, seleccione la aplicación Lookout for Work y elija **Administrar la implementación**.

  Debe seleccionar los mismos usuarios que ha agregado en la opción Administración de la inscripción en la consola de Lookout.  Vea el paso 3 de la sección sobre cómo [configurar la suscripción con la protección contra amenazas de dispositivo de Lookout](set-up-your-subscription-with-lookout-mtp#configure-your-subscription-with-lookout-mtp) para obtener información sobre cómo agregar grupos de usuarios a Lookout MTP.
>[!IMPORTANT]
> El Asistente para implementación de aplicaciones de Intune no es consciente de los grupos de usuarios de Azure AD y usa los de Intune en su lugar, por lo que debe crear un grupo de usuarios de Intune basado en el de Azure AD que está inscrito en la consola de Lookout, como se describe en [este](plan-your-user-and-device-groups.md) tema.

Seleccione la opción **Instalación requerida** para exigir que la aplicación Lookout se instale en el dispositivo del usuario.

## ¿Qué ocurre cuando se abre la aplicación implementada en el dispositivo?




Cuando el usuario abre Lookout for Work en el dispositivo, se le pide que active la aplicación y que seleccione la opción Iniciar sesión con Azure Active Directory. En los temas siguientes encontrará un tutorial detallado con el flujo para el usuario final:

* [Se le pide instalar Lookout for Work en un dispositivo Android](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

* [Debe solucionar una amenaza detectada por Lookout for Work en el dispositivo Android](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## Pasos siguientes
* [Habilitar la regla de protección contra amenazas móviles en la directiva de cumplimiento normativo](enable-device-threat-protection-rule-in-compliance-policy.md)



<!--HONumber=Oct16_HO2-->


