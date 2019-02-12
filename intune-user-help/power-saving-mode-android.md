---
title: La optimización de energía impide el acceso al correo electrónico | Microsoft Docs
description: Averigüe cómo desactivar la optimización de energía en Android para asegurarse de que recibe el correo electrónico.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/07/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ad713f18-40a9-421f-aa2b-f8c21028d57c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 98b8d4636b3f402b2b7246311e8027722fa01953
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55838130"
---
# <a name="outlook-wont-sync-managed-email-when-battery-optimization-for-android-is-turned-on"></a>Outlook no sincroniza el correo electrónico administrado si la optimización de la batería en Android está activada

> [!IMPORTANT]
> Este problema se documenta aquí porque hemos estado recibiendo numerosos informes de clientes relacionados con él. Si sigue experimentando este problema después de haber seguido estos pasos, póngase en contacto con el [equipo de soporte técnico de su empresa](https://go.microsoft.com/fwlink/?linkid=2010980) para obtener más ayuda.

La inscripción de un dispositivo en Intune le permite obtener acceso a los recursos de empresa. Uno de los recursos más comunes es el acceso al correo electrónico. Un problema que hemos detectado con el acceso al correo electrónico con Outlook para dispositivos Android es cuando la optimización de la batería está activada. La optimización de la batería se puede activar automáticamente para que el dispositivo siga encendido el máximo de tiempo posible. En este sentido, la optimización de la batería puede ayudarle en parte porque intenta detener las descargas automáticas de correo electrónico.

El equipo de Microsoft Intune está trabajando de forma activa para hallar una solución a este problema. Una manera de evitar que el dispositivo entre en modo de bajo consumo de energía consiste en asegurarse de que la batería tenga un nivel de carga de más del 30 %. A fin de que el problema no se produzca al entrar en modo de bajo consumo de energía, debe quitar el Portal de empresa y Outlook de la lista de aplicaciones que se ven afectadas por la optimización de la batería y la configuración de ahorro de energía.

Existen muchos dispositivos Android de distintos fabricantes, por lo que no podemos documentar los pasos exactos que se deben seguir con cada dispositivo. Es posible que deba llevar a cabo esta acción únicamente en la configuración del sistema o también en ciertas opciones específicas del fabricante. Aquí proporcionamos algunos ejemplos habituales sobre cómo se puede resolver este problema en dispositivos Android.

## <a name="unmodified-android-devices"></a>Dispositivos Android no modificados

Muchos fabricantes agregan modificaciones a sus dispositivos Android. Esto puede cambiar ciertas formas de interacción con el dispositivo, como los temas y las notificaciones. Por lo general, Google no efectúa estos tipos de modificaciones en sus teléfonos. Por ejemplo, en un dispositivo Google Pixel con Android 7.0 o posterior, debería seguir estos pasos para quitar estas aplicaciones de la optimización de la batería:

1. Abra **Configuración**.
2. Pulse **Batería** > **Más** > **Optimización de batería**.
3. Pulse la flecha hacia abajo y, luego, **No optimizado**.
4. Seleccione las aplicaciones del Portal de empresa y Outlook, y desactive la optimización de la batería.

## <a name="samsung-devices"></a>Dispositivos de Samsung

Para otros tipos de dispositivos Android, como los dispositivos Samsung con Android 7.0 o posterior, deberá seguir pasos diferentes para quitar las aplicaciones del Portal de empresa y Outlook de la optimización de la batería.

1. Abra **Configuración**.
2. Pulse **Menú (...)**  >  **Acceso especial** > **Optimizar uso de batería**.
3. Seleccione **Todas las aplicaciones** en la lista desplegable.
4. **Desactive** el botón de alternancia situado junto a las aplicaciones del Portal de empresa y Outlook para desactivar la optimización de la batería.

Además, si usa un dispositivo Samsung que tiene una versión anterior de Android, deberá seguir estos pasos para quitar estas aplicaciones del modo de ahorro de energía.

1. Abra **Configuración**.
2. Pulse **Mantenimiento dispositivo** > **Batería** > **Aplicaciones no supervisadas**.
3. Pulse **Añadir aplicaciones**.
4. Seleccione las aplicaciones del Portal de empresa y Outlook y, luego, pulse **Hecho**.

## <a name="oneplus-devices"></a>Dispositivos OnePlus

Otro ejemplo de una forma diferente para localizar estas opciones es a través de la búsqueda en la configuración del sistema. Por ejemplo, en un OnePlus 3 con Android 7.1.1, debe seguir estos pasos: 

1. Abra **Ajustes del sistema**. 
2. Pulse el botón **Buscar** (se parece a una lupa, situada en la parte superior derecha de la pantalla). 
3. Escriba **Optimización de batería** en la búsqueda y seleccione la opción **Optimización de batería** en la pantalla **Configuración** que aparece. 
4. Pulse **Batería** > **Optimización de batería**.
5. Seleccione las aplicaciones del Portal de empresa y Outlook y, luego, seleccione **No optimizar**. Pulse **Listo**.

<!--On a OnePlus 5 device with Android 7.1.1, you would follow these steps to remove these apps from battery optimization:
1. Open **Settings**.
2. Tap **Battery** > **Battery optimization**.
3. Select the Company Portal and Outlook apps, then select **Don’t optimize**. Tap **Done**.-->

¿Sigue necesitando ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
