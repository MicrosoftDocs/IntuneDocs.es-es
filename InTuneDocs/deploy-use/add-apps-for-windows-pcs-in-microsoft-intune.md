---
title: Agregar aplicaciones para PC Windows en Microsoft Intune | Microsoft Docs
description: "Use la información de este tema para aprender a agregar aplicaciones para equipos Windows a Intune antes de implementarlas."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bc8c8be9-7f4f-4891-9224-55fc40703f0b
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 547330c05b7fbdd2981e49320c913d8109563384
ms.openlocfilehash: f8f1359ff08b67261b23a694a4f6bbbeca24fa2a


---

# <a name="add-apps-for-windows-pcs-that-run-the-intune-software-client"></a>Agregar aplicaciones para PC Windows en Microsoft Intune

Use la información de este tema para aprender a agregar aplicaciones a Intune antes de implementarlas.

> [!IMPORTANT]
> La información de este tema le servirá para agregar aplicaciones para equipos Windows administrados mediante el software cliente de Intune. Si quiere agregar aplicaciones para PC Windows inscritos y otros dispositivos móviles, vea [Agregar aplicaciones para dispositivos móviles en Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md).

Para instalar aplicaciones en equipos, estas deben poder instalarse automáticamente, sin interacción por parte del usuario. Si no es así, se producirá un error en la instalación.


## <a name="add-the-app"></a>Agregar la aplicación
En el siguiente procedimiento usará el editor de software de Intune para configurar las propiedades de la aplicación y cargarla en el espacio de almacenamiento en nube:

1.  En la [consola de administrador de Microsoft Intune](https://manage.microsoft.com), elija **Aplicaciones** &gt; **Agregar aplicaciones** para iniciar el Editor de software de Intune.

    > [!TIP]
    > Deberá escribir su nombre de usuario y contraseña de Intune para que se inicie el editor.

2.  En la página **Instalación de software** del publicador, en **Seleccione cómo debe ponerse a disposición de los dispositivos este software**, elija **Instalador de software** y, a continuación, especifique:

    - **Seleccionar el tipo de archivo instalador de software**. Indica el tipo de software que desea implementar. En el caso de un PC Windows, elija **Windows Installer**.
    - **Especificar la ubicación de los archivos de instalación del software**. Escriba la ubicación de los archivos de instalación o elija **Examinar** para seleccionar la ubicación en una lista.
    - **Incluir archivos y subcarpetas adicionales de la misma carpeta**. Algún software que usa Windows Installer requiere los archivos auxiliares. Estos deben estar ubicados en la misma carpeta que el archivo de instalación. Seleccione esta opción si también desea implementar estos archivos auxiliares.

    Por ejemplo, si quiere publicar una aplicación llamada Application.msi en Intune, la página sería similar a la siguiente: ![Página de configuración del software del publicador](./media/publisher-for-pc.png)

   Este tipo de instalación usa parte del espacio de almacenamiento en la nube.

3.  En la página **Descripción del software**, configure las siguientes opciones.

    > [!NOTE]
    > En función del archivo instalador que use, algunos de estos valores podrían especificarse automáticamente o no aparecer.

    - **Publicador**. Escriba el nombre del publicador de la aplicación.
    - **Nombre**. Escriba el nombre de la aplicación tal como se mostrará en el portal de empresa.<br />Asegúrese de que todos los nombres de aplicación que usa son únicos. Si el mismo nombre de aplicación existe dos veces, solo se mostrará a los usuarios una de las aplicaciones en el portal de empresa.
    - **Descripción**. Escriba una descripción de la aplicación. Se mostrará a los usuarios en el portal de empresa.
    - **Dirección URL para información del software** (opcional). Escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL se mostrará a los usuarios en el portal de empresa.
    - **Dirección URL de privacidad** (opcional). Escriba la dirección URL de un sitio web que contenga información de privacidad sobre esta aplicación. La dirección URL se mostrará a los usuarios en el portal de empresa.
    - **Categoría** (opcional). Seleccione una de las categorías de aplicaciones integradas. Así les resultará más fácil a los usuarios encontrar la aplicación cuando exploren el portal de empresa.
    - **Icono** (opcional). Cargue un icono que se asociará con la aplicación. Será el icono que se muestre con la aplicación cuando los usuarios examinen el portal de empresa.

4.  En la página **Requisitos**, seleccione los requisitos que deben cumplirse para que la aplicación pueda instalarse. Elija de entre las siguientes opciones:

    - **Arquitectura**. Seleccione si esta aplicación puede instalarse en un sistema operativo de 32 bits, 64 bits o en ambos.
    - **Sistema operativo**. Seleccione el sistema operativo mínimo en el que se puede instalar esta aplicación.

5.  En la página **Reglas de detección de**, puede configurar reglas para detectar si la aplicación que está configurando ya está instalada en un equipo. O bien, puede usar las reglas de detección predeterminadas para sobrescribir automáticamente las versiones de la aplicación instaladas previamente. Esta opción es para Windows Installer (solo archivos .exe).

    Las reglas que puede configurar son las siguientes:
    - **El archivo existe**. Especifique la ruta de acceso del archivo que quiere detectar. Puede buscar en **%ProgramFiles%** (busca en **Archivos de programa**\&lt;ruta de acceso&gt; y **Archivos de programa (x86)**\&lt;ruta de acceso&gt;) en el equipo o en **%SystemDrive%** (busca en la unidad raíz del equipo, normalmente la unidad C).
    - **Existe un código de producto MSI**. Elija **Examinar** para elegir el archivo de Windows Installer (.msi) que quiere detectar.
    - **Existe la clave del registro**. Especifique una clave del Registro que comience por **HKEY_LOCAL_MACHINE\**. Se busca en las rutas de acceso del Registro de 32 bits y 64 bits. Si la clave especificada existe en ambas ubicaciones, se cumple la regla de detección.

    Si la aplicación cumple alguna de las reglas que configuró, no se instalará.

6.  Únicamente para el tipo de archivo **Windows Installer** (.msi y .exe): en la página **Argumentos de la línea de comandos **, elija si quiere proporcionar argumentos de línea de comandos opcionales para el instalador.
    Intune agrega automáticamente los parámetros siguientes:
    - Para los archivos .exe, se agrega **/install**.
    - Para los archivos .msi, se agrega **/quiet**.
    Tenga en cuenta que estas opciones solo funcionarán si el creador del paquete de aplicaciones ha habilitado la funcionalidad correspondiente.

7.  Únicamente para el tipo de archivo **Windows Installer** (solo .exe): en la página **Códigos de retorno** puede agregar nuevos códigos de error que Intune interpretará cuando la aplicación se instale en un equipo Windows administrado.

    Intune usa códigos de retorno estándar de la industria de forma predeterminada para informar de una instalación correcta o incorrecta de un paquete de aplicación: **0:** (Correcto) o **3010:** (Correcto con reinicio). También puede agregar sus propios códigos de retorno a esta lista. Si especifica una lista de códigos de retorno y la instalación de la aplicación devuelve un código que no se encuentra en la lista, se interpreta como un error.

8.  En la página **Resumen**, revise la información que especificó. Cuando esté listo, elija **Cargar**.

9. Elija **Cerrar** para finalizar.

La aplicación se muestra en el nodo **Aplicaciones** del área de trabajo **Aplicaciones**.

## <a name="next-steps"></a>Pasos siguientes

Tras crear una aplicación, el siguiente paso es implementarla. Para obtener más información, vea [Implementar aplicaciones en Microsoft Intune](deploy-apps.md).

Si quiere obtener más información sobre consejos y trucos para implementar software en equipos Windows, consulte la entrada de blog [Support Tip: Best Practices for Intune Software Distribution to PC’s](https://blogs.technet.microsoft.com/intunesupport/2016/06/13/support-tip-best-practices-for-intune-software-distribution-to-pcs/) (Consejo de soporte: recomendaciones para la distribución de software de Intune en PC).



<!--HONumber=Feb17_HO3-->


