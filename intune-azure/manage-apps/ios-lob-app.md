---
title: "Adición de aplicaciones de línea de negocio de iOS a Intune | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: aprenda a agregar aplicaciones de línea de negocio de iOS a Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 099101e8-4b22-40ac-ba19-82ba5c71944c
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 6d41adabfab178daa7f6fce3d86bc8216bf4ab29
ms.lasthandoff: 02/16/2017

---

# <a name="how-to-add-ios-line-of-business-lob-apps-to-microsoft-intune"></a>Adición de aplicaciones de línea de negocio (LOB) de iOS a Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


## <a name="step-1---specify-the-software-setup-file"></a>Paso 1: Especificación del archivo de instalación de software

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja de Intune, elija **Administrar aplicaciones**.
4. En la carga de trabajo **Mobile Apps**, elija Administrar > **Aplicaciones**.
5. Encima de la lista de aplicaciones, elija **Agregar**.
6. En la hoja **Agregar aplicación**, elija **Archivo de instalación de software**.
7. En la hoja **Seleccionar archivo de instalación**, haga clic en el botón del explorador y busque el archivo de instalación de la aplicación iOS (con la extensión .ipa) y luego haga clic en **Aceptar**.

## <a name="step-2---configure-app-information"></a>Paso 2: Configuración de la información de la aplicación

1. En la hoja **Editar aplicación**, configure la siguiente información. Cuando haya terminado, haga clic en **Aceptar**. Dependiendo de la aplicación que haya elegido, algunos de los valores de esta hoja pueden haber sido rellenados automáticamente:
    - **Nombre de la aplicación**: escriba el nombre de la aplicación tal como se mostrará en el Portal de empresa. Asegúrese de que todos los nombres de aplicación que usa son únicos. Si el mismo nombre de aplicación existe dos veces, solo se mostrará a los usuarios una de las aplicaciones en el portal de empresa.
    - **Descripción de la aplicación**: escriba una descripción de la aplicación. Se mostrará a los usuarios en el portal de empresa.
    - **Editor:** escriba el nombre del editor de la aplicación.
    - **Tipo de dispositivo aplicable**: seleccione si esta aplicación se puede instalar en dispositivos iPad, iPhone o iPod compatibles.
    - **Sistema operativo mínimo**: en la lista, elija la versión mínima del sistema operativo en la que se puede instalar la aplicación. Si la aplicación se asigna a un dispositivo con un sistema operativo anterior, no se instalará.
    - **Categoría** (opcional): seleccione una o varias de las categorías de aplicación integradas o una categoría que haya creado. Así les resultará más fácil a los usuarios encontrar la aplicación cuando exploren el portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: la aplicación se muestra de forma destacada en la página principal del Portal de empresa cuando los usuarios buscan aplicaciones.
    - **Dirección URL de información**: opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL se mostrará a los usuarios en el portal de empresa.
    - **Dirección URL de privacidad**: opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre esta aplicación. La dirección URL se mostrará a los usuarios en el portal de empresa.
    - **Desarrollador**: opcionalmente, escriba el nombre del desarrollador de la aplicación.
    - **Propietario**: opcionalmente,, escriba un nombre para el propietario de esta aplicación, por ejemplo, **departamento de Recursos Humanos**.
    - **Notas**: escriba notas que le gustaría asociar a esta aplicación.
    - **Cargar icono**: carga un icono que se asociará a la aplicación. Será el icono que se muestre con la aplicación cuando los usuarios examinen el portal de empresa.
2. Cuando haya terminado, en la hoja **Agregar aplicación**, elija **Guardar**.

La aplicación que ha creado se muestra en la lista de aplicaciones donde puede asignarla a los grupos que elija. Para obtener ayuda, consulte [Asignación de aplicaciones a grupos](/intune-azure/manage-apps/deploy-apps).
