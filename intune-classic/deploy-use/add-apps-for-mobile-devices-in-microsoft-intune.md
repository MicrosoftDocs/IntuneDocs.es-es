---
title: Agregar aplicaciones a los dispositivos inscritos
description: "Antes de que pueda implementar una aplicación, debe agregarla a Intune. Después, esta se encuentra disponible en la consola de Intune donde puede implementarla y administrarla."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/11/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5b1f1ae-f177-450a-9af9-936a02d052e3
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 98d0376ff02ea89e019fba6022de800f3ca84555
ms.contentlocale: es-es
ms.lasthandoff: 06/08/2017


---

# <a name="add-apps-for-enrolled-devices-to-intune"></a>Agregar aplicaciones a los dispositivos inscritos en Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Antes de que pueda implementar o administrar una aplicación, debe agregarla a Microsoft Intune. En este tema se muestra cómo agregar aplicaciones a los dispositivos inscritos.


> [!IMPORTANT]
> La información de este tema le servirá para agregar las aplicaciones que quiere implementar a dispositivos y PC Windows inscritos. Si quiere agregar aplicaciones para equipos PC Windows administrados con el software cliente de Intune, vea [Agregar aplicaciones para PC Windows en Microsoft Intune](add-apps-for-windows-pcs-in-microsoft-intune.md).

## <a name="add-the-app"></a>Agregar la aplicación
Use el Editor de software de Intune para configurar las propiedades de la aplicación y, si procede, cargarla en su espacio de almacenamiento en la nube. Utilice el procedimiento siguiente:

1.  En la [consola de administrador de Microsoft Intune](https://manage.microsoft.com), elija **Aplicaciones** &gt; **Agregar aplicaciones** para iniciar el Editor de software de Intune.

    > [!TIP]
    > Deberá escribir su nombre de usuario y contraseña de Intune para que se inicie el editor.

2.  En la página **Instalación de software** del editor, elija una de las siguientes opciones en **Seleccione cómo debe ponerse a disposición de los dispositivos este software**:
    - **Instalador de software** para aplicaciones con la extensión **.msi**:
        - **Seleccionar el tipo de archivo instalador de software**. Indica el tipo de software que desea implementar. Por ejemplo, si quiere instalar una aplicación iOS, elija **Paquete de aplicación para iOS (archivo &#42;.ipa)**.
        - **Especificar la ubicación de los archivos de instalación del software**. Escriba la ubicación de los archivos de instalación o elija **Examinar** para seleccionar la ubicación en una lista.
        - **Incluir archivos y subcarpetas adicionales de la misma carpeta**. Esta opción es únicamente para el tipo de archivo **Windows Installer**.<br>Cierto software que usa Windows Installer necesita los archivos auxiliares que normalmente se encuentran en la misma carpeta que los archivos de instalación. Seleccione esta opción si también desea implementar estos archivos.<br>Este tipo de instalación usa parte del espacio de almacenamiento en la nube.

  -   **Vínculo externo**, para aplicaciones que quiere crear indicando un vínculo a una tienda de aplicaciones:

        - **Especificar la dirección URL**. Especifique la dirección URL de una de las opciones siguientes:
            - La dirección URL de la tienda de aplicaciones de la aplicación que quiere implementar. Por ejemplo, si quiere implementar la aplicación Escritorio remoto de Microsoft para Android, especifique **https://play.google.com/store/apps/details?id=com.microsoft.rdc.android**.<br>Para buscar la dirección URL de la aplicación, use un motor de búsqueda para encontrar la página de almacenamiento que contiene la aplicación. Por ejemplo, para encontrar la aplicación Escritorio remoto, puede buscar **Escritorio remoto de Microsoft Android**.
            - Un sitio web. Intune implementará un icono de acceso directo al sitio del dispositivo (conocido como un clip de web).
            - Una aplicación en la web. Intune implementará un icono de acceso directo a la aplicación del dispositivo.
        - **Se necesita Managed Browser para abrir este vínculo (solo iOS y Android)**. Al implementar un vínculo a un sitio web o aplicación web para los usuarios, estos solo podrán abrirlo en el explorador administrado de Intune. Este explorador debe instalarse en su dispositivo.<br>Para obtener más detalles sobre el explorador administrado, vea [Administrar el acceso a Internet mediante directivas de explorador administrado con Microsoft Intune](manage-internet-access-using-managed-browser-policies.md).<br>Este tipo de instalación no usa el espacio de almacenamiento en la nube.

  -   **Aplicación iOS administrada de la App Store**, para aplicaciones gratuitas de iTunes Store que quiera administrar con directivas de administración de aplicaciones móviles (MAM):

        - **Especificar la dirección URL**. Especifique la dirección URL de la tienda de aplicaciones de la aplicación que quiere implementar. Por ejemplo, si quiere implementar la aplicación Carpetas de trabajo de Microsoft para iOS, especifique **https://itunes.apple.com/us/app/work-folders/id950878067?mt=8**.<br>Este tipo de instalación no usa el espacio de almacenamiento en la nube.

        Por ejemplo, si quiere implementar la aplicación Microsoft Word desde iTunes Store en los dispositivos, la página sería similar a esta:

        ![editor de software de Intune](./media/publisher-for-mobile.png)

> [!NOTE]
> Al agregar e implementar una aplicación desde un almacén, los usuarios finales deben tener una cuenta con el almacén para poder instalar la aplicación.

3.  En la página **Descripción del software**, configure las siguientes opciones:

    > [!TIP]
    > En función del tipo de instalador que use, algunos de estos valores podrían especificarse automáticamente.

    - **Publicador**. Escriba el nombre del publicador de la aplicación.
    - **Nombre**. Escriba el nombre de la aplicación tal como se mostrará en el portal de empresa.<br>Asegúrese de que todos los nombres de aplicación que usa son únicos. Si el mismo nombre de aplicación existe dos veces, solo se mostrará a los usuarios una de las aplicaciones en el portal de empresa.
    - **Descripción**. Escriba una descripción de la aplicación. Se mostrará a los usuarios en el portal de empresa.
    - **Dirección URL para información del software**. Solo está disponible si seleccionó **Instalador de software**. Opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL se mostrará a los usuarios en el portal de empresa.
    - **Dirección URL de privacidad**. Solo está disponible si seleccionó **Instalador de software**. Opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre esta aplicación. La dirección URL se mostrará a los usuarios en el portal de empresa.
    - **Categoría** (opcional). Seleccione una de las categorías de aplicaciones integradas. Así les resultará más fácil a los usuarios encontrar la aplicación cuando exploren el portal de empresa.
    - **Mostrar esta aplicación como destacada y resaltarla en el portal de empresa**. Muestra la aplicación de forma destacada en la página principal del portal de empresa cuando los usuarios buscan aplicaciones.
    - **Icono** (opcional). Cargue un icono que se asociará con la aplicación. Será el icono que se muestre con la aplicación cuando los usuarios examinen el portal de empresa.

        En este ejemplo, ha configurado una descripción de la aplicación Microsoft Word para iOS:

        ![Ejemplo de descripción del software](./media/ios-software-description.png)

4.  En la página **Requisitos**, seleccione los requisitos que deben cumplirse para que la aplicación pueda instalarse en un dispositivo. Por ejemplo, para un paquete de aplicación de iOS, puede seleccionar la versión mínima de iOS necesarios. Además, puede seleccionar el tipo de dispositivo que debe ser, como un iPhone o un iPad.

    > [!TIP]
    > La página **Requisitos** no se muestra para todos los tipos de aplicaciones.

5.  Se mostrarán más páginas del asistente si elige el tipo de archivo **Windows Installer**. Este tipo de archivo se usa al implementar software en equipos que ejecutan Windows 10 o posterior y que están inscritos con Intune.

6.  En la página **Resumen**, revise la información que especificó. Cuando esté listo, elija **Cargar**.

7.  Elija **Cerrar** para finalizar.

La aplicación se muestra en el nodo **Aplicaciones** del área de trabajo **Aplicaciones**.

## <a name="example---deploying-msi-applications-to-windows-10-devices"></a>Ejemplo: Implementar aplicaciones .msi en dispositivos Windows 10
En este vídeo de cuatro minutos, obtendrá información sobre cómo implementar las aplicaciones de Windows Installer (msi) en los dispositivos inscritos que ejecutan Windows 10.<br><br>

<iframe src="https://channel9.msdn.com/Series/How-to-Control-the-Uncontrolled/6--How-to-Deploy-MSI-Applications-to-Windows-10-Using-Intune-and-Mobile-Device-Management-MDM/player" width="640" height="360" allowFullScreen frameBorder="0"></iframe>

## <a name="next-steps"></a>Pasos siguientes

Tras crear una aplicación, el siguiente paso es implementarla. Para obtener más información, vea [Implementar aplicaciones en Microsoft Intune](deploy-apps.md).

