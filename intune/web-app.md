---
title: "Adición de aplicaciones web a Intune"
titleSuffix: Azure portal
description: "Obtenga información sobre cómo agregar aplicaciones web a Intune\"."
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 12/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cfa70879a460826d22eb6fab2e0d08603e567d6e
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-add-web-apps-to-microsoft-intune"></a>Agregar aplicaciones web a Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Antes de poder administrar y asignar aplicaciones a los usuarios, agregue la aplicación a Intune. Intune admite diversos tipos de aplicación, incluidas las aplicaciones web.

> [!Note]
> Las aplicaciones web no se admiten en dispositivos Android for Work.

Complete los pasos siguientes para agregar una aplicación a Intune como un acceso directo a una aplicación en la Web:

1. Inicie sesión en el portal de Azure.
2. Con **Más recursos**, busque y seleccione **Intune**.
3. En la hoja **Microsoft Intune**, seleccione **Aplicaciones móviles**.
4. En la hoja **Aplicaciones móviles** hoja, seleccione **Aplicaciones**.
5. Encima de la lista de aplicaciones, elija **Agregar**. Aparece la hoja **Agregar aplicación**.
6. En la hoja **Agregar aplicación**, seleccione el tipo **Aplicación web** en la lista desplegable **Tipo de aplicación**.
7. Seleccione la opción **Configurar** para mostrar la hoja **Información de la aplicación**.
8. En la hoja **Información de aplicación**, agregue la información siguiente:
    - **Nombre:** escriba el nombre de la aplicación tal como se mostrará en el Portal de empresa.
    - **Descripción:** escriba una descripción de la aplicación. Esta se muestra a los usuarios finales en el Portal de empresa.
    - **Publicador**: escriba el nombre del publicador de esta aplicación.
    - **Dirección URL de la aplicación**: escriba la dirección URL del sitio web que hospeda la aplicación que quiere asignar.
    - **Categoría (opcional)**: seleccione una o varias de las categorías de aplicaciones integradas o una categoría que haya creado. Así les resultará más fácil a los usuarios encontrar la aplicación cuando exploren el Portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: la aplicación se muestra de forma destacada en la página principal del Portal de empresa cuando los usuarios buscan aplicaciones.
    - **Se necesita Managed Browser para abrir este vínculo**: al asignar un vínculo a un sitio web o aplicación web para los usuarios, estos pueden abrirlo en el explorador administrado de Intune. Este explorador debe instalarse en su dispositivo.
    - **Logotipo**: cargue un logotipo que esté asociado a la aplicación. Este logotipo es el que se muestra con la aplicación cuando los usuarios examinan el Portal de empresa.
9. Cuando haya terminado, en la hoja **Agregar información**, seleccione **Aceptar**.
10. Luego, en la hoja **Agregar aplicación**, seleccione **Agregar**.

La aplicación que ha creado se muestra en la lista de aplicaciones, donde puede asignarla a los grupos que elija. Para obtener ayuda, consulte [Asignación de aplicaciones a grupos](apps-deploy.md).