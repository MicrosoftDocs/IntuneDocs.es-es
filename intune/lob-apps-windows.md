---
title: "Adición de aplicaciones de línea de negocio de Windows a Intune | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda cómo agregar aplicaciones de línea de negocio de Windows a Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 696c8f8e72e21c792474f5e52fad9054b3dfade9
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017

---

# <a name="how-to-add-windows-line-of-business-lob-apps-to-microsoft-intune"></a>Adición de aplicaciones de línea de negocio (LOB) de Windows a Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]


## <a name="step-1---specify-the-software-setup-file"></a>Paso 1: Especificación del archivo de instalación de software

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Administrar aplicaciones**.
4. En la carga de trabajo **Mobile Apps**, elija **Administrar** > **Aplicaciones**.
5. Encima de la lista de aplicaciones, elija **Agregar**.
6. En la hoja **Agregar aplicación** y elija **Aplicación de línea de negocio**.

## <a name="step-2---configure-the-app-package-file"></a>Paso 2: Configuración del archivo de paquete de aplicaciones

1. En la hoja **Agregar aplicación**, elija el archivo de **paquete de aplicaciones**.
2. En la hoja del archivo de **paquete de aplicaciones**, elija el botón Examinar y seleccione un archivo de instalación de Windows con la extensión **.msi** (no se admiten otros tipos de archivos de instalación).
3. Cuando termine, elija **Aceptar**.


## <a name="step-3---configure-app-information"></a>Paso 3: Configuración de la información de la aplicación

1. En la hoja **Agregar aplicación**, elija el archivo de **paquete de aplicaciones**.
2. En la hoja **Información de aplicación**, configure la información siguiente. Dependiendo de la aplicación que haya elegido, algunos de los valores de esta hoja pueden haber sido rellenados automáticamente:
    - **Nombre:** escriba el nombre de la aplicación tal como se mostrará en el portal de empresa. Asegúrese de que todos los nombres de aplicación que usa son únicos. Si el mismo nombre de aplicación existe dos veces, solo se mostrará a los usuarios una de las aplicaciones en el portal de empresa.
    - **Descripción:** escriba una descripción de la aplicación. Se mostrará a los usuarios en el portal de empresa.
    - **Editor:** escriba el nombre del editor de la aplicación.
    - **Categoría**: seleccione una o más de las categorías de aplicaciones integradas, o una categoría que haya creado. Así les resultará más fácil a los usuarios encontrar la aplicación cuando exploren el portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: la aplicación se muestra de forma destacada en la página principal del Portal de empresa cuando los usuarios buscan aplicaciones.
    - **Dirección URL de información**: opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL se mostrará a los usuarios en el portal de empresa.
    - **Dirección URL de privacidad**: opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre esta aplicación. La dirección URL se mostrará a los usuarios en el portal de empresa.
    - **Argumentos de línea de comandos**: si lo desea, especifique los argumentos de línea de comandos que desea aplicar al archivo .ms, cuando se ejecuta, como **/q**.
    - **Desarrollador**: opcionalmente, escriba el nombre del desarrollador de la aplicación.
    - **Propietario**: opcionalmente,, escriba un nombre para el propietario de esta aplicación, por ejemplo, **departamento de Recursos Humanos**.
    - **Notas**: escriba notas que le gustaría asociar a esta aplicación.
    - **Logotipo**: cargue un icono que se asociará con la aplicación. Será el icono que se muestre con la aplicación cuando los usuarios examinen el portal de empresa.
3. Cuando termine, elija **Aceptar**.

## <a name="step-4---finish-up"></a>Paso 4: Finalización

1. En la hoja **Agregar aplicación**, compruebe que la información que configuró es correcta.
2. Elija **Agregar** para cargar la aplicación en Intune.

La aplicación que ha creado se muestra en la lista de aplicaciones donde puede asignarla a los grupos que elija. Para obtener ayuda, consulte [Asignación de aplicaciones a grupos](apps-deploy.md).

