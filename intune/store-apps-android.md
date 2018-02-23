---
title: "Adición de aplicaciones Android de la Tienda a Intune"
titleSuffix: Azure portal
description: "Obtenga información sobre cómo agregar aplicaciones Android de la tienda a Intune\"."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/13/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cdf00d8adc5a854f90b59c6066d6f0ab7c6ae94a
ms.sourcegitcommit: 754fcc31155b28d6910bba45419c6be745f8793e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="how-to-add-android-store-apps-to-microsoft-intune"></a>Adición de aplicaciones de la Tienda Android a Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Antes de asignar una aplicación a un dispositivo o a un grupo de usuarios, primero debe agregar la aplicación a Microsoft Intune. Los pasos siguientes permiten agregar una aplicación de la tienda Android a Intune desde Azure Portal.

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Microsoft Intune**, elija **Aplicaciones móviles**.
4. En la carga de trabajo **Aplicaciones móviles**, elija **Aplicaciones** en la sección **Administrar**.
5. Encima de la lista de aplicaciones, elija **Agregar**.
6. En la hoja **Agregar aplicación**, seleccione **Android** en los tipos **Aplicación de la Tienda** disponibles.
7. Seleccione **Configurar** para configurar la siguiente información de la aplicación. Dependiendo de la aplicación que haya elegido, algunos de los valores de esta hoja pueden haberse rellenado automáticamente:
    - **Nombre:** escriba el nombre de la aplicación tal como se mostrará en el portal de empresa. Asegúrese de que todos los nombres de aplicación que usa son únicos. Si el mismo nombre de aplicación existe dos veces, solo se mostrará a los usuarios una de las aplicaciones en el portal de empresa.
    - **Descripción:** escriba una descripción de la aplicación. Esta descripción se muestra a los usuarios en el Portal de empresa.
    - **Editor:** escriba el nombre del editor de la aplicación.
    - **Dirección URL de AppStore**: escriba la dirección URL de la tienda de aplicaciones de la aplicación que quiere crear.
    - **Versión mínima del sistema operativo**: en la lista, elija la versión mínima del sistema operativo en la que se puede instalar la aplicación. Si la aplicación se asigna a un dispositivo con un sistema operativo anterior, no se instalará.
    - **Categoría** (opcional): seleccione una o varias de las categorías de aplicación integradas o una categoría que haya creado. Así les resultará más fácil a los usuarios encontrar la aplicación cuando exploren el portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: la aplicación se muestra de forma destacada en la página principal del Portal de empresa cuando los usuarios buscan aplicaciones.
    - **Dirección URL de información** (opcional): escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL se mostrará a los usuarios en el portal de empresa.
    - **Dirección URL de privacidad** (opcional): escriba la dirección URL de un sitio web que contenga información de privacidad de esta aplicación. La dirección URL se mostrará a los usuarios en el portal de empresa.
    - **Desarrollador** (opcional): escriba el nombre del desarrollador de la aplicación.
    - **Propietario** (opcional): escriba el nombre del propietario de esta aplicación, por ejemplo, **Departamento de Recursos Humanos**.
    - **Notas** (opcional): escriba las notas que le gustaría asociar a esta aplicación.
    - **Logotipo** (opcional): cargue un icono que se asocie con la aplicación. Este icono se muestra con la aplicación cuando los usuarios examinan el portal de empresa.
8. Haga clic en **Aceptar** cuando haya terminado de configurar la información de la aplicación.
9. Haga clic en **Agregar** para agregar la aplicación.

La aplicación que ha creado se muestra en la lista de aplicaciones, donde puede asignarla a los grupos que elija. 

##<a name="next-steps"></a>Pasos siguientes

- [Asignación de aplicaciones a grupos](apps-deploy.md)