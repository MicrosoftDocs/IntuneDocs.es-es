---
title: "Adición de aplicaciones de línea de negocio de Windows Phone a Intune"
titlesuffix: Azure portal
description: "Obtenga información sobre cómo agregar aplicaciones de línea de negocio de Windows Phone a Intune\"."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/3/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a097b7b2-d01d-454b-954c-da4f3cd0ae86
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6c20414c2df5616a2616d64f88718761be8a57b0
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-add-windows-phone-line-of-business-lob-apps-to-microsoft-intune"></a>Adición de aplicaciones de línea de negocio (LOB) de Windows Phone a Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


## <a name="step-1---specify-the-software-setup-file"></a>Paso 1: Especificación del archivo de instalación de software

1. Inicie sesión en Azure Portal.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** + **Intune**.
3. En la hoja **Intune**, elija **Administrar aplicaciones**.
4. En la carga de trabajo **Mobile Apps**, elija **Administrar** > **Aplicaciones**.
5. Encima de la lista de aplicaciones, elija **Agregar**.
6. En la hoja **Agregar aplicación** y elija **Aplicación de línea de negocio**.

## <a name="step-2---configure-the-app-package-file"></a>Paso 2: Configuración del archivo de paquete de aplicaciones

1. En la hoja **Agregar aplicación**, elija el archivo de **paquete de aplicaciones**.
2. En la hoja del archivo **Paquete de aplicaciones**, elija el botón Examinar y seleccione un archivo de instalación de Windows Phone con la extensión **.xap**.
3. Cuando termine, elija **Aceptar**.


## <a name="step-3---configure-app-information"></a>Paso 3: Configuración de la información de la aplicación

1. En la hoja **Agregar aplicación**, elija el archivo de **paquete de aplicaciones**.
2. En la hoja **Información de la aplicación**, configure la información de la aplicación. Dependiendo de la aplicación que haya elegido, algunos de los valores de esta hoja pueden haber sido rellenados automáticamente:
    - **Nombre**: escriba el nombre de la aplicación tal como se muestra en el portal de empresa. Asegúrese de que todos los nombres de aplicación que usa son únicos. Si el mismo nombre de aplicación existe dos veces, solo se muestra a los usuarios una de las aplicaciones en el portal de empresa.
    - **Descripción:** escriba una descripción de la aplicación. La descripción se muestra a los usuarios en el portal de empresa.
    - **Editor:** escriba el nombre del editor de la aplicación.
    - **Categoría**: seleccione una o más de las categorías de aplicaciones integradas, o una categoría que haya creado. El uso de categorías facilita a los usuarios encontrar la aplicación cuando exploren el portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: la aplicación se muestra de forma destacada en la página principal del Portal de empresa cuando los usuarios buscan aplicaciones.
    - **Dirección URL de información**: opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Dirección URL de privacidad**: opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Desarrollador**: opcionalmente, escriba el nombre del desarrollador de la aplicación.
    - **Propietario**: opcionalmente,, escriba un nombre para el propietario de esta aplicación, por ejemplo, **departamento de Recursos Humanos**.
    - **Notas**: escriba notas que le gustaría asociar a esta aplicación.
    - **Logotipo**: cargue un icono que esté asociado a la aplicación. Este icono se muestra con la aplicación cuando los usuarios examinan el portal de empresa.
3. Cuando termine, elija **Aceptar**.

## <a name="step-4---finish-up"></a>Paso 4: Finalización

1. En la hoja **Agregar aplicación**, compruebe que ha configurado correctamente la información.
2. Elija **Agregar** para cargar la aplicación en Intune.

## <a name="next-steps"></a>Pasos siguientes

La aplicación que ha creado aparece en la lista de aplicaciones. Ahora puede asignarla a los grupos que elija. Para obtener ayuda, consulte [Asignación de aplicaciones a grupos](apps-deploy.md).

Obtenga más información sobre los métodos disponibles para supervisar las propiedades y la asignación de la aplicación. Para más información, vea [Supervisión de información de aplicación y asignaciones](apps-monitor.md).

Obtenga más información sobre el contexto de la aplicación en Intune. Para más información, vea [Información general sobre los ciclos de vida del dispositivo y la aplicación](introduction-device-app-lifecycles.md).
