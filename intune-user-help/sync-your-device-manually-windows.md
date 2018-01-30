---
title: Sincronizar manualmente el dispositivo Windows | Microsoft Docs
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 05/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 443c6de7-5187-4dc4-b844-6085a0c659bd
searchScope:
- User help
ROBOTS: 
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 6d3b0fb8ea462656602ee9b4e58200d3c2e755a9
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="sync-your-windows-device-manually"></a>Sincronización manual del dispositivo Windows

A veces, intentar instalar una aplicación en su dispositivo Windows puede tardar más de lo que esperaba. Si esto sucede, puede intentar sincronizar manualmente su dispositivo Windows. La sincronización puede ayudar a acelerar la instalación.

> [!Note]
> Las aplicaciones pueden tardar un tiempo en instalarse si está en una red con velocidades más lentas o grandes cantidades de dispositivos descargando contenido a la vez.

Las siguientes versiones de Windows pueden sincronizarse manualmente. Si su dispositivo está usando una versión diferente de Windows, no puede iniciar una sincronización manual.

* [Sincronizar Windows 10 Escritorio](#windows-10-desktop)
* [Sincronizar Windows 10 Mobile](#windows-10-mobile)
* [Sincronizar Windows Phone 8.1](#windows-phone-81)

## <a name="windows-10-desktop"></a>Windows 10 Escritorio
Hay más de una versión de Windows 10, así que hay dos conjuntos de pasos. Para averiguar qué pasos debe seguir, vea las capturas de pantalla y siga los pasos que se parezcan a lo que ve en el dispositivo.

1. Elija el botón **Iniciar** y, después, elija **Configuración**.

    ![El botón Iniciar](./media/win10pc-sync-1-start-button.png)

2. En la página **Configuración**, seleccione **Cuentas**.

    ![Elección de cuentas en la página de configuración](./media/win10pc-sync-2-settings-accounts.png)

3. Examine las dos pantallas siguientes y elija la que se parezca más a lo que ve en el dispositivo. Siga los pasos que tienen que ver con la pantalla que verá en el dispositivo.

    Si aparece esta pantalla, que muestra "Obtener acceso a trabajo o escuela", siga las instrucciones de [Pasos a seguir si ve acceso profesional o educativo](#steps-to-follow-if-you-see-access-work-or-school).

    ![Sincronizar los pasos que debe seguir si ve acceso profesional o educativo](./media/w10-enroll-rs1-connect-to-work-or-school.png)

    Si aparece esta pantalla, que muestra "Acceso al trabajo", siga los pasos de [Pasos que debe seguir si ve acceso profesional](#steps-to-follow-if-you-see-work-access).

    ![Elección del acceso al trabajo como tipo de cuenta](./media/win10pc-sync-3-work-access.png)

### <a name="steps-to-follow-if-you-see-access-work-or-school"></a>Pasos a seguir si ve acceso profesional o educativo

1. En la página **Cuentas**, elija **Obtener acceso a trabajo o escuela**.

    ![Elegir acceso profesional o educativo](./media/w10-enroll-rs1-connect-to-work-or-school.png)

2. Elija la cuenta profesional o educativa. Según la configuración que haya definido el equipo de soporte técnico de su empresa, podría ver dos cuentas con un aspecto similar al ejemplo siguiente. Una tiene un maletín al lado y la otra tiene el logotipo de Microsoft.

    - Si ve la cuenta con el maletín, selecciónela y busque un botón **Información** debajo de ella.
    - Si solo ve la cuenta con el logotipo de Microsoft, selecciónela y busque un botón **Información** debajo de ella.

    ![Elija el nombre de la cuenta junto al maletín o el logotipo de Microsoft](./media/win10pc-rs1-sync-info-button.png)

3. Elija el botón **Información**. Se abre un cuadro de diálogo parecido al siguiente ejemplo.

    ![Elija el nombre de la cuenta junto al maletín o el logotipo de Microsoft](./media/win10pc-rs1-sync-button.png)

4. Elija el botón **Sincronizar**. El dispositivo se sincronizará con Intune.

### <a name="steps-to-follow-if-you-see-work-access"></a>Pasos que debe seguir si ve acceso profesional

1. En la página **Cuentas**, seleccione **Acceso al trabajo**.

    ![Elección del acceso al trabajo como tipo de cuenta](./media/win10pc-sync-3-work-access.png)

2. En la sección **Enroll in to device management** (Inscribirse en la administración de dispositivos), elija el nombre de su compañía.

    ![Elección del nombre de la empresa para la administración de dispositivos](./media/win10pc-sync-4-tap-com-name.png)

3. Elija el botón **Sincronizar**.

    ![Elección del botón Sincronizar](./media/win10pc-sync-5-tap-sync.png)

   El botón se atenúa hasta que se finaliza la sincronización.

### <a name="windows-10-mobile"></a>Windows 10 Mobile
Para sincronizar manualmente el dispositivo de Windows 10 Mobile de modo que se acelere la instalación de una aplicación lenta:

   1. Vaya a **Todas las aplicaciones** > **Configuración** > **Cuentas**.

       ![Elección de cuentas en la pantalla de configuración](./media/win10m-sync-1-settings-accounts.png)

   2. Elija **Acceso al trabajo**.

       ![Elección del acceso al trabajo como tipo de cuenta](./media/win10m-sync-2-work-access.png)

   3. En **Enroll in to device management** (Inscribirse en la administración de dispositivos), elija el nombre de su empresa.

       ![Elección del nombre de la empresa para la administración de dispositivos](./media/win10m-sync-3-tap-comp-name.png)

   4. Elija el icono **Sincronizar**.

       ![Elección del icono Sincronizar](./media/win10m-sync-4-tap-sync.png)

       Aparece el mensaje "We’re synching your account" (Estamos sincronizando su cuenta) en la parte superior de la pantalla. El botón **Sincronizar** aparecerá atenuado hasta que el dispositivo finalice la sincronización.

## <a name="windows-phone-81"></a>Windows Phone 8,1
Para sincronizar manualmente el dispositivo de Windows Phone 8.1 de modo que se acelere la instalación de una aplicación lenta:

1. Vaya a **Todas las aplicaciones** > **Configuración** > **Área de trabajo**.

    ![Lista de configuración](./media/wp81-1-sync-settings-workplace.png)

2. Elija el nombre de su compañía.

    ![Elección del nombre de la empresa para la cuenta de trabajo](./media/wp81-2-sync-tap-compname.png)

3. Elija el icono **Sincronizar**.

    ![Elección del icono Sincronizar](./media/wp81-3-sync-tap-sync-button.png)

   Aparece el mensaje "We’re synching your account" (Estamos sincronizando su cuenta) en la parte superior de la pantalla hasta que el dispositivo acabe de sincronizarse.

¿Sigue necesitando ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://portal.manage.microsoft.com#HelpDeskDialog).
